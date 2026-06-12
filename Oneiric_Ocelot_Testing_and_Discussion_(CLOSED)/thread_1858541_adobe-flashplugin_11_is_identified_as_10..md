---
title: "adobe-flashplugin 11 is identified as 10."
date: 2011-10-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by mikewhatever on 2011-10-12
In Oneiric 64bit, if you search for Flash in the Software Center, all it shows is Flash 10.


Check this out:

> apt-cache search adobe-flashplugin
adobe-flashplugin - **Adobe Flash Player plugin version 10**


> 
apt-cache show adobe-flashplugin
Package: adobe-flashplugin
Priority: optional
Section: web
Installed-Size: 18512
Maintainer: DL-Flash Player Ubuntu <FlashPlayerUbuntu@adobe.com>
Architecture: amd64
**Version: 11.0.1.152-0oneiric1**
Recommends: adobe-flash-properties-gtk (= 11.0.1.152-0oneiric1) | adobe-flash-properties-kde (= 11.0.1.152-0oneiric1)
Replaces: flashplugin (<< 6)
Suggests: firefox, konqueror-nsplugins, x-ttcidfont-conf, msttcorefonts, ttf-bitstream-vera | ttf-dejavu, ttf-xfree86-nonfree, xfs (>= 1:1.0.1-5), libnspr4-0d, libnss3-1d
Provides: flashplugin-nonfree
Depends: wget, fontconfig, libatk1.0-0 (>= 1.12.4), libc6 (>= 2.4), libcairo2 (>= 1.2.4), libfontconfig1 (>= 2.8.0), libfreetype6 (>= 2.2.1), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.12.0), libgtk2.0-0 (>= 2.14.0), libpango1.0-0 (>= 1.14.0), libx11-6, libxext6, libxt6
Conflicts: flashplayer-mozilla, flashplugin (<< 6), flashplugin-installer, xfs (<< 1:1.0.1-5)
**Filename: pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.0.1.152-0oneiric1_amd64.deb**
Size: 6705108
MD5sum: e8677fce390ec7b4f9cc893af8b01ff8
SHA1: 365b997a3f5c73933db9805e17d98d45b2d7acb3
**Description: Adobe Flash Player plugin version 10**
 This package will download the Flash Player from Adobe. It is a
 Netscape/Mozilla type plugin. Any browser based on Netscape or Mozilla can use
 the Flash plugin. This package officially supports the following browsers:
 .
 Firefox 2.x, Firefox 3.x, SeaMonkey 1.11
Npp-File: libflashplayer.so
Npp-Mimetype: application/x-shockwave-flash
Npp-Applications: ec8030f7-c20a-464f-9b0e-13a3a9e97384, 92650c4d-4b8e-4d2a-b7eb-24ecf4f6b63a, aa5ca914-c309-495d-91cf-3141bbb04115
Npp-Description: Adobe Flash Plugin ([http://www.adobe.com](http://www.adobe.com))
Npp-Name: Adobe Flash Plugin



In fact, the package installs flash 11.0.1.152, but the description is wrong.
I've tried filing a bug report, but it failed saying "not a genuine ubuntu package".

OK, done. [https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/872995](https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/872995)

---

### Post by linuxman94 on 2011-10-12
This is a duplicate of bug #872710.  Marked as such

---

### Post by linuxman94 on 2011-10-12
Fixed the bug, but i can't upload it

---

