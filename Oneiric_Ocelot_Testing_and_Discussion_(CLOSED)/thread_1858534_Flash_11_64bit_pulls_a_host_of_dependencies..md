---
title: "Flash 11 64bit pulls a host of dependencies."
date: 2011-10-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by mikewhatever on 2011-10-12
Check this out:

> 
sudo apt-get install flashplugin-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  flashplugin-downloader:i386 libasound2:i386 libasound2-plugins:i386
  libasyncns0:i386 libatk1.0-0:i386 libavahi-client3:i386
  libavahi-common-data:i386 libavahi-common3:i386 libcairo2:i386 libcups2:i386
  libcurl3:i386 libdatrie1:i386 libexpat1:i386 libflac8:i386
  libfontconfig1:i386 libfreetype6:i386 libgcrypt11:i386
  libgdk-pixbuf2.0-0:i386 libgnutls26:i386 libgpg-error0:i386
  libgssapi-krb5-2:i386 libgtk2.0-0:i386 libice6:i386 libidn11:i386
  libjack-jackd2-0:i386 libjasper1:i386 libjpeg62:i386 libjson0:i386
  libk5crypto3:i386 libkeyutils1:i386 libkrb5-3:i386 libkrb5support0:i386
  libldap-2.4-2:i386 libnspr4:i386 libnspr4-0d:i386 libnss3:i386
  libnss3-1d:i386 libogg0:i386 libpango1.0-0:i386 libpixman-1-0:i386
  libpulse0:i386 librtmp0:i386 libsamplerate0:i386 libsasl2-2:i386
  libsasl2-modules:i386 libsm6:i386 libsndfile1:i386 libspeexdsp1:i386
  libsqlite3-0:i386 libstdc++6:i386 libtasn1-3:i386 libthai0:i386
  libtiff4:i386 libvorbis0a:i386 libvorbisenc2:i386 libwrap0:i386
  libx11-6:i386 libxau6:i386 libxcb-render0:i386 libxcb-shm0:i386 libxcb1:i386
  libxcomposite1:i386 libxcursor1:i386 libxdamage1:i386 libxdmcp6:i386
  libxext6:i386 libxfixes3:i386 libxft2:i386 libxi6:i386 libxinerama1:i386
  libxrandr2:i386 libxrender1:i386 libxt6:i386 nspluginviewer:i386
  nspluginwrapper
Suggested packages:
  firefox:i386 x-ttcidfont-conf:i386 msttcorefonts:i386
  ttf-bitstream-vera:i386 ttf-dejavu:i386 ttf-xfree86-nonfree:i386 xfs:i386
  libasound2-python:i386 cups-common:i386 rng-tools:i386 gnutls-bin:i386
  krb5-doc:i386 krb5-user:i386 librsvg2-common:i386 gvfs:i386 jackd2:i386
  libjasper-runtime:i386 ttf-japanese-gothic:i386 ttf-japanese-mincho:i386
  ttf-thryomanes:i386 ttf-baekmuk:i386 ttf-arphic-gbsn00lp:i386
  ttf-arphic-bsmi00lp:i386 ttf-arphic-gkai00mp:i386 ttf-arphic-bkai00mp:i386
  libsasl2-modules-otp:i386 libsasl2-modules-ldap:i386
  libsasl2-modules-sql:i386 libsasl2-modules-gssapi-mit:i386
  libsasl2-modules-gssapi-heimdal:i386
The following NEW packages will be installed:
  flashplugin-downloader:i386 flashplugin-installer libasound2:i386
  libasound2-plugins:i386 libasyncns0:i386 libatk1.0-0:i386
  libavahi-client3:i386 libavahi-common-data:i386 libavahi-common3:i386
  libcairo2:i386 libcups2:i386 libcurl3:i386 libdatrie1:i386 libexpat1:i386
  libflac8:i386 libfontconfig1:i386 libfreetype6:i386 libgcrypt11:i386
  libgdk-pixbuf2.0-0:i386 libgnutls26:i386 libgpg-error0:i386
  libgssapi-krb5-2:i386 libgtk2.0-0:i386 libice6:i386 libidn11:i386
  libjack-jackd2-0:i386 libjasper1:i386 libjpeg62:i386 libjson0:i386
  libk5crypto3:i386 libkeyutils1:i386 libkrb5-3:i386 libkrb5support0:i386
  libldap-2.4-2:i386 libnspr4:i386 libnspr4-0d:i386 libnss3:i386
  libnss3-1d:i386 libogg0:i386 libpango1.0-0:i386 libpixman-1-0:i386
  libpulse0:i386 librtmp0:i386 libsamplerate0:i386 libsasl2-2:i386
  libsasl2-modules:i386 libsm6:i386 libsndfile1:i386 libspeexdsp1:i386
  libsqlite3-0:i386 libstdc++6:i386 libtasn1-3:i386 libthai0:i386
  libtiff4:i386 libvorbis0a:i386 libvorbisenc2:i386 libwrap0:i386
  libx11-6:i386 libxau6:i386 libxcb-render0:i386 libxcb-shm0:i386 libxcb1:i386
  libxcomposite1:i386 libxcursor1:i386 libxdamage1:i386 libxdmcp6:i386
  libxext6:i386 libxfixes3:i386 libxft2:i386 libxi6:i386 libxinerama1:i386
  libxrandr2:i386 libxrender1:i386 libxt6:i386 nspluginviewer:i386
  nspluginwrapper
0 upgraded, **76 newly installed**, 0 to remove and 0 not upgraded.
Need to get 0 B/13.5 MB of archives.
After this operation, 39.3 MB of additional disk space will be used.
Do you want to continue [Y/n]? 



The package info:

> 
apt-cache show flashplugin-installer
Package: flashplugin-installer
Priority: optional
Section: multiverse/web
Installed-Size: 52
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Bart Martens <bartm@knars.be>
Architecture: amd64
Source: flashplugin-nonfree
Version: 11.0.1.152ubuntu1
Depends: flashplugin-downloader (>= 11.0.1.152ubuntu1), nspluginwrapper
**Filename: pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_11.0.1.152ubuntu1_amd64.deb**
Size: 4314
MD5sum: 75cb1d8e373d69053747ad662eaabf59
SHA1: a911c508a6a71464dc948087fcc314d5502f3518
SHA256: 86691f34aa14074bfb4964e672b99282a96596d1346d441ab825ed429112da44
Description-en: Adobe Flash Player plugin installer
 This is a metapackage that should be used on amd64 to properly install the
 nspluginwrapper dependency.
Homepage: [http://wiki.ubuntu.com/FlashPlayer9](http://wiki.ubuntu.com/FlashPlayer9)
Description-md5: cd2955532df8699ec24af7052e752e5c
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu



---

### Post by Harry33 on 2011-10-12
That is not the native 64-bit flash plugin.

The correct one is in the partner repos right now.
It does not pull in anything from i386 nor nspluginwrapper.
See the package adobe-flashplugin
Here:
[https://launchpad.net/ubuntu/oneiric/amd64/adobe-flashplugin/11.0.1.152-0oneiric1](https://launchpad.net/ubuntu/oneiric/amd64/adobe-flashplugin/11.0.1.152-0oneiric1)

> 
**Depends on:**
fontconfig
libatk1.0-0 (>= 1.12.4)
libc6 (>= 2.4)
libcairo2 (>= 1.2.4)
libfontconfig1 (>= 2.8.0)
libfreetype6 (>= 2.2.1)
libgdk-pixbuf2.0-0 (>= 2.22.0)
libglib2.0-0 (>= 2.12.0)
libgtk2.0-0 (>= 2.14.0)
libpango1.0-0 (>= 1.14.0)
libx11-6
libxext6
libxt6
wget


---

