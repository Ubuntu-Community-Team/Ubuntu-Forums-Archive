---
title: "Home-made package always seems to need upgrading"
date: 2011-01-13
forum: Packaging and Compiling Programs
---

### Post by peteispo on 2011-01-13
I have made a private package which rolls up a web application to be distributed internally within my company across a bunch of virtual machines (all running 10.04 LTS server edition)

I have my own internal mirror (gigabyte.justcroft.com) for the lucid main and restricted, to cut down on net access for  updates. On the same server as the mirror I made another repository for my private packages. On the VMs I set up the sources.list to point at the mirror and this additional repository. The source.list entry for the private repository is:

```
deb http://gigabyte.justcroft.com/developatwork/ubuntu ./
```That all seems to be working - system updates come from the mirror fine, and I can install my private package from the repository onto the VM.

However, the private package is always marked as having an upgrade available, even immediately after upgrading it.
Another curious thing is that apt-get claims that 1084Mb (yes, megabytes) will be freed when I install the update, although the package itself is just under 2Mb.

I'm pretty new to .deb packaging, so I have probably set something wrong in the control file:

```

Package: developatwork
Version: 1.06
Section: web
Priority: optional
Architecture: all
Essential: no
Depends: acpid, apache2, libapache2-mod-php5, apache2-mpm-prefork, apache2-utils, build-essential, fakeroot, libc-dev-bin, libfontconfig1, libicu42, libltdl7, liblzma1, libssl-dev, openssh-server, php-pear, php5-dev, php5-gd, php5-xsl, rcconf, shtool, ssl-cert, subversion, tcpd
Filename: ./developatwork-1.06.deb
Size: 1900258
Installed-Size: 7350578
MD5sum: 633fd0a79d4764c77ccad4d3008d66c5
Maintainer: Peter Ford (DevelopAtWork Packager) <pete@developatwork.com>
Provides: developatwork
Description: The DevelopAtWork web application
 This package is not for general use

```

Any suggestions?

---

### Post by gmargo on 2011-01-13
I'm guessing it's the filename of the .deb package.  You've used "developatwork-1.06.deb", but if you look at other .deb files the naming standard is 

package _ version _ arch .deb  (those are underscores)

so I think the name of your package should be "developatwork_1.06_all.deb"

But as I said, merely a guess.  I can't seem to find where the filename format is defined.

---

### Post by mc4man on 2011-01-13
the filename entry is using ./ for some reason
(also not sure why you have that entry
What does your debian/changelog show?

---

