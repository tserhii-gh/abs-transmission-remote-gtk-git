# Maintainer: Serhii Tsynailo <serhii.tsynailo@gmail.com>
# Previous Maintainer: TingPing tingping@tingping.se

pkgname=transmission-remote-gtk-git
pkgver=1.6.0
pkgrel=1
pkgdesc='A remote interface to the Transmission BitTorrent client'
arch=('x86_64')
url='https://github.com/transmission-remote-gtk/transmission-remote-gtk'
license=('GPL')
options=('!libtool')
depends=('gtk3' 'curl' 'libproxy' 'geoip')
makedepends=('git' 'meson' 'desktop-file-utils' 'perl')
provides=('transmission-remote-gtk')
conflicts=('transmission-remote-gtk')
source=('git+https://github.com/tserhii-gh/transmission-remote-gtk.git')
sha512sums=('SKIP')
_gitname='transmission-remote-gtk'

pkgver() {
  cd "$_gitname"

  git describe --tags | sed 's/\([^-]*-g\)/r\1/;s/-/./g'
}

prepare() {
  mkdir -p build
  meson setup build "$_gitname" --prefix=/usr
}

build() {
  meson compile -C build
}

package() {
  meson install -C build --destdir="$pkgdir"
}
