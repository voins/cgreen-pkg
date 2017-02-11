# Maintainer: Alexey Voinov <alexey.v.voinov@gmail.com>
pkgname=cgreen-git
pkgver=1.0.0.r252.5d9bc5a
pkgrel=1
pkgdesc="A modern, portable, cross-language unit testing and mocking framework for C and C++"
arch=('x86_64' 'i686')
url="https://github.com/cgreen-devs/cgreen"
license=('custom:ISC')
groups=()
depends=('glibc')
makedepends=('git')
provides=('cgreen')
conflicts=('cgreen')
replaces=()
backup=()
options=()
install=
source=('git+https://github.com/cgreen-devs/cgreen/')
noextract=()
md5sums=('SKIP')

pkgver() {
	cd "$srcdir/cgreen"
	printf "%s" "$(git describe --tags | sed 's/\([^-]*-\)g/r\1/;s/-/./g')"
}

build() {
	cd "$srcdir/cgreen"
        mkdir build
        cd build
        cmake -DCMAKE_INSTALL_PREFIX:PATH="/usr" ..
        make
}

check() {
	cd "$srcdir/cgreen/build"
	make test
}

package() {
	cd "$srcdir/cgreen/build"
	make DESTDIR="$pkgdir/" install
        install -D -m644 ../LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}
