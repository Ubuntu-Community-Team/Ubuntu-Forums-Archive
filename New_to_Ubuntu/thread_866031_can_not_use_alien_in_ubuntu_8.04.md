---
title: "can not use alien in ubuntu 8.04"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by AceDip on 2008-07-21
When i try to convert a .rpm file to .deb with alien 

```
sudo alien -k Winamp.rpm

sh: rpm: not found
Error executing "LANG=C rpm -qp --queryformat %{NAME} Winamp.rpm": at /usr/local/share/perl/5.8.8/Alien/Package.pm line 482.
```

Kindly help me using Alien properly and the reason behind this weird error..

---

### Post by Potatoj316 on 2008-07-21
I havent really ever used Alien but these are some possible problems I thought of.  1. are you in the directory containing that file.  2. Is that file actually an rpm, not just with the .rpm extension.  3. are you using the -k correctly

---

### Post by scorp123 on 2008-07-21
"rpm" should be automatically installed if you installed "alien" correctly via the packet manager (e.g. "apt-get install" command or "Synaptic").

So my guess is you installed "alien" manually and not the clean way via the repos?

```
> apt-cache show alien
Package: alien
Priority: optional
Section: admin
Installed-Size: 276
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Joey Hess <joeyh@debian.org>
Architecture: all
Version: 8.68
**[COLOR="Red"]Depends:[/COLOR]** debhelper (>= 3), perl (>= 5.6.0-16), **[COLOR="Red"]rpm[/COLOR]** [COLOR="Red"]**(>= 2.4.4-2)**[/COLOR], dpkg-dev, make, cpio
Suggests: patch, bzip2, lsb-rpm, lintian
Filename: pool/main/a/alien/alien_8.68_all.deb
Size: 104134
MD5sum: 0f748555af026112a378428208d47249
SHA1: 960c235fc0ce0d5174a9892778cbca1eeccad535
SHA256: 11cbfc189d270d99be1be676581eecc928f1b61c77a947237f2ef193fb39829a
Description: install non-native packages with dpkg
 Alien allows you to convert LSB, Red Hat, Stampede and Slackware Packages
 into Debian packages, which can be installed with dpkg.
 .
 It can also generate packages of any of the other formats.
 .
 This is a tool only suitable for binary packages.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
```

---

### Post by dfreer on 2008-07-21
Check this thread out: [http://forums.winamp.com/showthread.php?threadid=249591](http://forums.winamp.com/showthread.php?threadid=249591)

Basically, the only linux version of winamp was an alpha release of winamp 3, and even on RPM based distros people had problems installing it. Recommendation? Install either XMMS, Amarok, Audacious, Songbird, or try running winamp in wine, but don't expect it to work fully.

IMO, installing from source or a .deb is a far bettter solution than using Alien.

---

