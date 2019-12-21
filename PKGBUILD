# Maintainer: Thibaut Sautereau (thithib) <thibaut at sautereau dot fr>

pkgname=netctl-wg
pkgver=1.20
pkgrel=1
pkgdesc='Profile based systemd network management, with WireGuard support'
url='https://projects.archlinux.org/netctl.git/'
license=('GPL')
depends=('coreutils' 'iproute2' 'resolvconf' 'systemd>=233')
makedepends=('pkg-config' 'asciidoc' 'git')
optdepends=('dialog: for the menu based wifi assistant'
            'dhclient: for DHCP support (or dhcpcd)'
            'dhcpcd: for DHCP support (or dhclient)'
            'wpa_supplicant: for wireless networking support'
            'ifplugd: for automatic wired connections through netctl-ifplugd'
            'ppp: for PPP connections'
            'openvswitch: for Open vSwitch connections'
            'wireguard-tools: for WireGuard connections'
           )
conflicts=('netctl')
install=netctl.install
source=('git+https://github.com/thithib/netctl#branch=wireguard?signed')
arch=('any')
md5sums=('SKIP')
validpgpkeys=('CFA6AF15E5C74149FC1D8C086D1655C14CE1C13E'  # Florian Pritz
              'B663151724E4C3D82C250F4369E7F43252C4F70A')  # Thibaut Sautereau

package() {
  cd "${pkgname%-wg}"
  make DESTDIR="$pkgdir" install

  # Shell Completion
  install -D -m644 contrib/bash-completion "$pkgdir/usr/share/bash-completion/completions/netctl"
  ln -s netctl "$pkgdir/usr/share/bash-completion/completions/netctl-auto"
  ln -s netctl "$pkgdir/usr/share/bash-completion/completions/wifi-menu"
  install -D -m644 contrib/zsh-completion "$pkgdir/usr/share/zsh/site-functions/_netctl"
}
