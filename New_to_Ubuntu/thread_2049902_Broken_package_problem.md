---
title: "Broken package problem?"
date: 2012-08-29
forum: New to Ubuntu
---

### Post by JayArtist on 2012-08-29
Hi guys!

I appear to have an issue with a broken package. I'm using 12.04 LTS on an MSI netbook and every time I install a new package I get this error:

Setting up isc-dhcp-server (4.1.ESV-R4-0ubuntu5.2) ... 
start: Job failed to start 
invoke-rc.d: initscript isc-dhcp-server, action "start" failed. 
dpkg: error processing isc-dhcp-server (--configure): 
 subprocess installed post-installation script returned error exit status 1 
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of dhcp3-server: 
 dhcp3-server depends on isc-dhcp-server; however: 
  Package isc-dhcp-server is not configured yet. 
dpkg: error processing dhcp3-server (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already
Setting up computer-janitor (2.1.0-0ubuntu8) ... 
Setting up computer-janitor-gtk (2.1.0-0ubuntu8) ... 
Errors were encountered while processing: 
 isc-dhcp-server 
 dhcp3-server 
Setting up isc-dhcp-server (4.1.ESV-R4-0ubuntu5.2) ... 
start: Job failed to start 
invoke-rc.d: initscript isc-dhcp-server, action "start" failed. 
dpkg: error processing isc-dhcp-server (--configure): 
 subprocess installed post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of dhcp3-server: 
 dhcp3-server depends on isc-dhcp-server; however: 
  Package isc-dhcp-server is not configured yet. 
dpkg: error processing dhcp3-server (--configure): 
 dependency problems - leaving unconfigured 

The software that I install works fine, but I just don't like it when something obviously isn't running 100%, so  I thought I ask if anyone knows how to fix it.

I'm relatively new to Linux/Ubuntu so please go easy please ;)

Thanks in advance!

Jay.

---

### Post by josephmills on 2012-08-29
Could you post back 
```
apt-cache show  isc-dhcp-server 
```
and
```
apt-cache policy isc-dhcp-server
```
thanks

---

### Post by JayArtist on 2012-08-29
Sure ;)

Package: isc-dhcp-server
Priority: optional
Section: net
Installed-Size: 1012
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian ISC DHCP maintainers <pkg-dhcp-devel@lists.alioth.debian.org>
Architecture: i386
Source: isc-dhcp
Version: 4.1.ESV-R4-0ubuntu5.2
Replaces: dhcp3-server
Provides: dhcp3-server
Depends: debianutils (>= 2.8.2), isc-dhcp-common (= 4.1.ESV-R4-0ubuntu5.2), lsb-base, adduser, libc6 (>= 2.15), libcap2 (>= 2.10), debconf (>= 0.5) | debconf-2.0, upstart-job
Suggests: isc-dhcp-server-ldap, apparmor
Conflicts: dhcp
Filename: pool/main/i/isc-dhcp/isc-dhcp-server_4.1.ESV-R4-0ubuntu5.2_i386.deb
Size: 426984
MD5sum: 41ccc59548c3f1a79ee933ca76c7b588
SHA1: ddaf5ad9129d0cac34bbb5a1b80125fea46f3edd
SHA256: 332bf3771e69fa5ffd550b4e9f45ae4476e681ad5a8923fb53b00db541638c15
Description-en: ISC DHCP server for automatic IP address assignment
 This is the server from the Internet Software Consortium's implementation of
 DHCP. For more information, visit [http://www.isc.org](http://www.isc.org).
 .
 Dynamic Host Configuration Protocol (DHCP) is a protocol like BOOTP
 (actually dhcpd includes much of the functionality of bootpd). It
 gives client machines "leases" for IP addresses and can
 automatically set their network configuration.
 .
 This server can handle multiple ethernet interfaces.
Description-md5: 4f5d533c02fa72751acbaefe5e28258d
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu
Supported: 5y

Package: isc-dhcp-server
Priority: optional
Section: net
Installed-Size: 1011
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian ISC DHCP maintainers <pkg-dhcp-devel@lists.alioth.debian.org>
Architecture: i386
Source: isc-dhcp
Version: 4.1.ESV-R4-0ubuntu5
Replaces: dhcp3-server
Provides: dhcp3-server
Depends: debianutils (>= 2.8.2), isc-dhcp-common (= 4.1.ESV-R4-0ubuntu5), lsb-base, adduser, libc6 (>= 2.15), libcap2 (>= 2.10), debconf (>= 0.5) | debconf-2.0, upstart-job
Suggests: isc-dhcp-server-ldap, apparmor
Conflicts: dhcp
Filename: pool/main/i/isc-dhcp/isc-dhcp-server_4.1.ESV-R4-0ubuntu5_i386.deb
Size: 425878
MD5sum: a67db1dcf98d5f6eb845e7f5d30ab4a5
SHA1: 0e88314efd01ff241f7c7930aec8aece114a5b0f
SHA256: 33c170b2f4604c42b5b9f3ec556b852fb3bd3f31e8ce8bc8ed15e564bb7c000a
Description-en: ISC DHCP server for automatic IP address assignment
 This is the server from the Internet Software Consortium's implementation of
 DHCP. For more information, visit [http://www.isc.org](http://www.isc.org).
 .
 Dynamic Host Configuration Protocol (DHCP) is a protocol like BOOTP
 (actually dhcpd includes much of the functionality of bootpd). It
 gives client machines "leases" for IP addresses and can
 automatically set their network configuration.
 .
 This server can handle multiple ethernet interfaces.
Description-md5: 4f5d533c02fa72751acbaefe5e28258d
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu
Supported: 5y


isc-dhcp-server:
  Installed: 4.1.ESV-R4-0ubuntu5.2
  Candidate: 4.1.ESV-R4-0ubuntu5.2
  Version table:
 *** 4.1.ESV-R4-0ubuntu5.2 0
        500 [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) precise-updates/main i386 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main i386 Packages
        100 /var/lib/dpkg/status
     4.1.ESV-R4-0ubuntu5 0
        500 [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) precise/main i386 Packages

---

### Post by josephmills on 2012-08-29
Not sure to be honest but I would try to remove that then re-install. isc-dhcp-server that is

---

