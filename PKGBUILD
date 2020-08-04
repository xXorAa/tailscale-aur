# Maintainer: David Anderson <dave@natulte.net>

pkgname="tailscale"
_version="0.100.0-153"
pkgver="0.100.0_153"
pkgrel="1"
pkgdesc="A mesh VPN that makes it easy to connect your devices, wherever they are."
arch=("x86_64" "aarch64")
url="https://tailscale.com"
license=("MIT")
depends=("glibc")
backup=("etc/default/tailscaled")
source_x86_64=("$pkgname-$pkgver.tgz::https://pkgs.tailscale.com/stable/tailscale_${_version}_amd64.tgz")
source_aarch64=("$pkgname-$pkgver.tgz::https://pkgs.tailscale.com/stable/tailscale_${_version}_arm64.tgz")
sha256sums_x86_64=('020d9c384c557ea7e2aba3f667ebb7ecb86eac442e2a393a9b14f02d487df29c')
sha256sums_aarch64=('ca6f109e8d6ab659c0323062406c153440d37d0ed475201d98b32569e38333ce')
install="tailscale.install"

package() {
  case $CARCH in
  x86_64)
    cd tailscale_${_version}_amd64
    ;;
  aarch64)
    cd tailscale_${_version}_arm64
    ;;
  esac

  mkdir -p "$pkgdir/usr/bin" "$pkgdir/etc/default" "$pkgdir/usr/lib/systemd/system"
  install -m755 tailscale tailscaled "$pkgdir/usr/bin"
  install -m644 systemd/tailscaled.defaults "$pkgdir/etc/default/tailscaled"
  install -m644 systemd/tailscaled.service "$pkgdir/usr/lib/systemd/system"
}
