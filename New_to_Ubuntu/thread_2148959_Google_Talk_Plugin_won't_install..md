---
title: "Google Talk Plugin won't install."
date: 2013-05-27
forum: New to Ubuntu
---

### Post by daneandrewlam on 2013-05-27
Hello everyone, hoping you might be able to help. Getting this error message when trying to install Google Talk plugin update:

The package system is broken

The following packages have unmet dependencies:


linux-image-extra-3.5.0-28-generic: Depends: linux-image-3.5.0-28-generic but it is not installed
linux-image-extra-3.5.0-30-generic: Depends: linux-image-3.5.0-30-generic but it is not installed
linux-image-generic: Depends: linux-image-3.5.0-28-generic but it is not installed

Any tips would be most welcome :)

---

### Post by newb85 on 2013-05-27
What is the output of
```
sudo apt-get -fs upgrade
```

(This won't make changes.  The -s option means "simulate".)

---

### Post by daneandrewlam on 2013-05-27
> **newb85 said:**
> What is the output of
```
sudo apt-get -fs upgrade
```

(This won't make changes.  The -s option means "simulate".)

Quite a big output, sorry for the lenth:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following NEW packages will be installed
  linux-image-3.5.0-28-generic linux-image-3.5.0-30-generic
  linux-image-3.5.0-31-generic linux-image-extra-3.5.0-31-generic
The following packages will be upgraded:
  accountsservice alsa-utils apparmor bamfdaemon ffmpeg firefox
  firefox-globalmenu firefox-gnome-support firefox-locale-en
  flashplugin-installer google-talkplugin icedtea-7-jre-jamvm icedtea-7-plugin
  icedtea-netx icedtea-netx-common iptables isc-dhcp-client isc-dhcp-common
  libaccountsservice0 libasound2 libasound2:i386 libav-tools
  libavcodec-extra-53 libavdevice53 libavfilter2 libavformat-extra-53
  libavutil-extra-51 libbamf3-0 libcurl3 libcurl3-gnutls libcurl3-nss
  libdrm-intel1 libdrm-intel1:i386 libdrm-nouveau1a libdrm-nouveau2
  libdrm-nouveau2:i386 libdrm-radeon1 libdrm-radeon1:i386 libdrm2 libdrm2:i386
  libgl1-mesa-dri libgl1-mesa-dri:i386 libgl1-mesa-glx libgl1-mesa-glx:i386
  libglapi-mesa libglapi-mesa:i386 libjack-jackd2-0 libjack-jackd2-0:i386
  libkms1 libmysqlclient18:i386 libpoppler-glib8 libpoppler28
  libpostproc-extra-52 libssl1.0.0 libssl1.0.0:i386 libswscale-extra-2
  libtiff5 libtiff5:i386 libufe-xidgetter0 libxatracker1 libxslt1.1
  libxslt1.1:i386 linux-image-generic linux-libc-dev multiarch-support
  mysql-common openjdk-7-jre openjdk-7-jre-headless openjdk-7-jre-lib openssl
  poppler-utils rsyslog spotify-client spotify-client-qt telepathy-idle
  thunderbird thunderbird-globalmenu thunderbird-gnome-support
  thunderbird-locale-en thunderbird-locale-en-us wine-compholio:i386 xdiagnose
  xserver-common xserver-xorg-core xserver-xorg-video-intel xul-ext-unity
86 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Inst linux-image-3.5.0-28-generic (3.5.0-28.48 Ubuntu:12.10/quantal-updates [amd64]) [linux-image-extra-3.5.0-30-generic:amd64 ]
Inst linux-image-3.5.0-30-generic (3.5.0-30.51 Ubuntu:12.10/quantal-updates [amd64])
Inst linux-image-3.5.0-31-generic (3.5.0-31.52 Ubuntu:12.10/quantal-updates [amd64])
Inst linux-image-extra-3.5.0-31-generic (3.5.0-31.52 Ubuntu:12.10/quantal-updates [amd64])
Inst linux-image-generic [3.5.0.28.44] (3.5.0.31.47 Ubuntu:12.10/quantal-updates [amd64])
Inst libssl1.0.0 [1.0.1c-3ubuntu2.3] (1.0.1c-3ubuntu2.4 Ubuntu:12.10/quantal-updates [amd64]) [libssl1.0.0:amd64 on libssl1.0.0:i386] [libssl1.0.0:i386 on libssl1.0.0:amd64] [libssl1.0.0:i386 ]
Inst libssl1.0.0:i386 [1.0.1c-3ubuntu2.3] (1.0.1c-3ubuntu2.4 Ubuntu:12.10/quantal-updates [i386])
Conf libssl1.0.0 (1.0.1c-3ubuntu2.4 Ubuntu:12.10/quantal-updates [amd64])
Conf libssl1.0.0:i386 (1.0.1c-3ubuntu2.4 Ubuntu:12.10/quantal-updates [i386])
Inst libdrm2 [2.4.39-0ubuntu1] (2.4.43-0ubuntu0.1 Ubuntu:12.10/quantal-updates [amd64]) [libdrm2:amd64 on libdrm2:i386] [libdrm2:i386 on libdrm2:amd64] [libdrm2:i386 ]
Inst libdrm2:i386 [2.4.39-0ubuntu1] (2.4.43-0ubuntu0.1 Ubuntu:12.10/quantal-updates [i386])
Conf libdrm2 (2.4.43-0ubuntu0.1 Ubuntu:12.10/quantal-updates [amd64])
Conf libdrm2:i386 (2.4.43-0ubuntu0.1 Ubuntu:12.10/quantal-updates [i386])
Inst libdrm-nouveau1a [2.4.39-0ubuntu1] (2.4.43-0ubuntu0.1 Ubuntu:12.10/quantal-updates [amd64])
Inst libdrm-radeon1 [2.4.39-0ubuntu1] (2.4.43-0ubuntu0.1 Ubuntu:12.10/quantal-updates [amd64]) [libdrm-radeon1:amd64 on libdrm-radeon1:i386] [libdrm-radeon1:i386 on libdrm-radeon1:amd64] [libdrm-radeon1:i386 ]
Inst libdrm-radeon1:i386 [2.4.39-0ubuntu1] (2.4.43-0ubuntu0.1 Ubuntu:12.10/quantal-updates [i386])
Conf libdrm-radeon1 (2.4.43-0ubuntu0.1 Ubuntu:12.10/quantal-updates [amd64])
Conf libdrm-radeon1:i386 (2.4.43-0ubuntu0.1 Ubuntu:12.10/quantal-updates [i386])
Inst libkms1 [2.4.39-0ubuntu1] (2.4.43-0ubuntu0.1 Ubuntu:12.10/quantal-updates [amd64])
Inst apparmor [2.8.0-0ubuntu5] (2.8.0-0ubuntu5.1 Ubuntu:12.10/quantal-updates [amd64])
Inst libcurl3-gnutls [7.27.0-1ubuntu1.1] (7.27.0-1ubuntu1.2 Ubuntu:12.10/quantal-updates [amd64])
Inst libasound2 [1.0.25-3ubuntu3] (1.0.25-3ubuntu3.1 Ubuntu:12.10/quantal-updates [amd64]) [libasound2:amd64 on libasound2:i386] [libasound2:i386 on libasound2:amd64] [libasound2:i386 ]
Inst libasound2:i386 [1.0.25-3ubuntu3] (1.0.25-3ubuntu3.1 Ubuntu:12.10/quantal-updates [i386])
Conf libasound2 (1.0.25-3ubuntu3.1 Ubuntu:12.10/quantal-updates [amd64])
Conf libasound2:i386 (1.0.25-3ubuntu3.1 Ubuntu:12.10/quantal-updates [i386])
Inst libavutil-extra-51 [6:0.8.5ubuntu0.12.10.1] (6:0.8.6ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [amd64])
Inst libavcodec-extra-53 [6:0.8.5ubuntu0.12.10.1] (6:0.8.6ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [amd64])
Inst libavformat-extra-53 [6:0.8.5ubuntu0.12.10.1] (6:0.8.6ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [amd64])
Inst libjack-jackd2-0 [1.9.8~dfsg.4+20120529git007cdc37-2ubuntu1] (1.9.8~dfsg.4+20120529git007cdc37-2ubuntu2 Ubuntu:12.10/quantal-updates [amd64]) [libjack-jackd2-0:amd64 on libjack-jackd2-0:i386] [libjack-jackd2-0:i386 on libjack-jackd2-0:amd64] [libjack-jackd2-0:i386 ]
Inst libjack-jackd2-0:i386 [1.9.8~dfsg.4+20120529git007cdc37-2ubuntu1] (1.9.8~dfsg.4+20120529git007cdc37-2ubuntu2 Ubuntu:12.10/quantal-updates [i386])
Conf libjack-jackd2-0 (1.9.8~dfsg.4+20120529git007cdc37-2ubuntu2 Ubuntu:12.10/quantal-updates [amd64])
Conf libjack-jackd2-0:i386 (1.9.8~dfsg.4+20120529git007cdc37-2ubuntu2 Ubuntu:12.10/quantal-updates [i386])
Inst libavdevice53 [6:0.8.5-0ubuntu0.12.10.1] (6:0.8.6-0ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [amd64])
Inst libswscale-extra-2 [6:0.8.5ubuntu0.12.10.1] (6:0.8.6ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [amd64])
Inst libavfilter2 [6:0.8.5-0ubuntu0.12.10.1] (6:0.8.6-0ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [amd64])
Inst libpostproc-extra-52 [6:0.8.5ubuntu0.12.10.1] (6:0.8.6ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [amd64])
Inst libav-tools [6:0.8.5-0ubuntu0.12.10.1] (6:0.8.6-0ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [amd64])
Inst libbamf3-0 [0.3.4-0ubuntu1] (0.3.6-0ubuntu2 Ubuntu:12.10/quantal-updates [amd64]) []
Inst bamfdaemon [0.3.4-0ubuntu1] (0.3.6-0ubuntu2 Ubuntu:12.10/quantal-updates [amd64])
Inst libcurl3 [7.27.0-1ubuntu1.1] (7.27.0-1ubuntu1.2 Ubuntu:12.10/quantal-updates [amd64])
Inst libcurl3-nss [7.27.0-1ubuntu1.1] (7.27.0-1ubuntu1.2 Ubuntu:12.10/quantal-updates [amd64])
Inst libdrm-intel1 [2.4.39-0ubuntu1] (2.4.43-0ubuntu0.1 Ubuntu:12.10/quantal-updates [amd64]) [libdrm-intel1:amd64 on libdrm-intel1:i386] [libdrm-intel1:i386 on libdrm-intel1:amd64] [libdrm-intel1:i386 ]
Inst libdrm-intel1:i386 [2.4.39-0ubuntu1] (2.4.43-0ubuntu0.1 Ubuntu:12.10/quantal-updates [i386])
Conf libdrm-intel1 (2.4.43-0ubuntu0.1 Ubuntu:12.10/quantal-updates [amd64])
Conf libdrm-intel1:i386 (2.4.43-0ubuntu0.1 Ubuntu:12.10/quantal-updates [i386])
Inst libdrm-nouveau2 [2.4.39-0ubuntu1] (2.4.43-0ubuntu0.1 Ubuntu:12.10/quantal-updates [amd64]) [libdrm-nouveau2:amd64 on libdrm-nouveau2:i386] [libdrm-nouveau2:i386 on libdrm-nouveau2:amd64] [libdrm-nouveau2:i386 ]
Inst libdrm-nouveau2:i386 [2.4.39-0ubuntu1] (2.4.43-0ubuntu0.1 Ubuntu:12.10/quantal-updates [i386])
Conf libdrm-nouveau2 (2.4.43-0ubuntu0.1 Ubuntu:12.10/quantal-updates [amd64])
Conf libdrm-nouveau2:i386 (2.4.43-0ubuntu0.1 Ubuntu:12.10/quantal-updates [i386])
Inst xserver-common [2:1.13.0-0ubuntu6.1] (2:1.13.0-0ubuntu6.2 Ubuntu:12.10/quantal-updates [all])
Inst libgl1-mesa-dri [9.0.2-0ubuntu0.1] (9.0.3-0ubuntu0.1 Ubuntu:12.10/quantal-updates [amd64]) [libgl1-mesa-dri:amd64 on libgl1-mesa-dri:i386] [libgl1-mesa-dri:i386 on libgl1-mesa-dri:amd64] [libgl1-mesa-dri:i386 ]
Inst libgl1-mesa-dri:i386 [9.0.2-0ubuntu0.1] (9.0.3-0ubuntu0.1 Ubuntu:12.10/quantal-updates [i386])
Conf libgl1-mesa-dri (9.0.3-0ubuntu0.1 Ubuntu:12.10/quantal-updates [amd64])
Conf libgl1-mesa-dri:i386 (9.0.3-0ubuntu0.1 Ubuntu:12.10/quantal-updates [i386])
Inst xserver-xorg-core [2:1.13.0-0ubuntu6.1] (2:1.13.0-0ubuntu6.2 Ubuntu:12.10/quantal-updates [amd64])
Inst libgl1-mesa-glx [9.0.2-0ubuntu0.1] (9.0.3-0ubuntu0.1 Ubuntu:12.10/quantal-updates [amd64]) [libgl1-mesa-glx:amd64 on libgl1-mesa-glx:i386] [libgl1-mesa-glx:i386 on libgl1-mesa-glx:amd64] [libgl1-mesa-glx:i386 ]
Inst libgl1-mesa-glx:i386 [9.0.2-0ubuntu0.1] (9.0.3-0ubuntu0.1 Ubuntu:12.10/quantal-updates [i386]) []
Inst libglapi-mesa:i386 [9.0.2-0ubuntu0.1] (9.0.3-0ubuntu0.1 Ubuntu:12.10/quantal-updates [i386]) [libglapi-mesa:amd64 on libglapi-mesa:i386] [libglapi-mesa:i386 on libglapi-mesa:amd64] [libglapi-mesa:amd64 ]
Inst libglapi-mesa [9.0.2-0ubuntu0.1] (9.0.3-0ubuntu0.1 Ubuntu:12.10/quantal-updates [amd64])
Conf libglapi-mesa (9.0.3-0ubuntu0.1 Ubuntu:12.10/quantal-updates [amd64])
Conf libglapi-mesa:i386 (9.0.3-0ubuntu0.1 Ubuntu:12.10/quantal-updates [i386])
Conf libgl1-mesa-glx (9.0.3-0ubuntu0.1 Ubuntu:12.10/quantal-updates [amd64])
Conf libgl1-mesa-glx:i386 (9.0.3-0ubuntu0.1 Ubuntu:12.10/quantal-updates [i386])
Inst mysql-common [5.5.29-0ubuntu0.12.10.1] (5.5.31-0ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [all])
Inst libmysqlclient18:i386 [5.5.29-0ubuntu0.12.10.1] (5.5.31-0ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [i386])
Inst libtiff5 [4.0.2-1ubuntu2.1] (4.0.2-1ubuntu2.2 Ubuntu:12.10/quantal-updates [amd64]) [libtiff5:amd64 on libtiff5:i386] [libtiff5:i386 on libtiff5:amd64] [libtiff5:i386 ]
Inst libtiff5:i386 [4.0.2-1ubuntu2.1] (4.0.2-1ubuntu2.2 Ubuntu:12.10/quantal-updates [i386])
Conf libtiff5 (4.0.2-1ubuntu2.2 Ubuntu:12.10/quantal-updates [amd64])
Conf libtiff5:i386 (4.0.2-1ubuntu2.2 Ubuntu:12.10/quantal-updates [i386])
Inst libpoppler28 [0.20.4-0ubuntu1.1] (0.20.4-0ubuntu1.2 Ubuntu:12.10/quantal-updates [amd64])
Inst libpoppler-glib8 [0.20.4-0ubuntu1.1] (0.20.4-0ubuntu1.2 Ubuntu:12.10/quantal-updates [amd64])
Inst libxatracker1 [9.0.2-0ubuntu0.1] (9.0.3-0ubuntu0.1 Ubuntu:12.10/quantal-updates [amd64])
Inst libxslt1.1 [1.1.26-14] (1.1.26-14ubuntu0.1 Ubuntu:12.10/quantal-updates [amd64]) [libxslt1.1:amd64 on libxslt1.1:i386] [libxslt1.1:i386 on libxslt1.1:amd64] [libxslt1.1:i386 ]
Inst libxslt1.1:i386 [1.1.26-14] (1.1.26-14ubuntu0.1 Ubuntu:12.10/quantal-updates [i386])
Conf libxslt1.1 (1.1.26-14ubuntu0.1 Ubuntu:12.10/quantal-updates [amd64])
Conf libxslt1.1:i386 (1.1.26-14ubuntu0.1 Ubuntu:12.10/quantal-updates [i386])
Inst openjdk-7-jre [7u15-2.3.7-0ubuntu1~12.10.1] (7u21-2.3.9-0ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [amd64]) []
Inst icedtea-7-jre-jamvm [7u15-2.3.7-0ubuntu1~12.10.1] (7u21-2.3.9-0ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [amd64]) []
Inst openjdk-7-jre-headless [7u15-2.3.7-0ubuntu1~12.10.1] (7u21-2.3.9-0ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [amd64]) []
Inst openjdk-7-jre-lib [7u15-2.3.7-0ubuntu1~12.10.1] (7u21-2.3.9-0ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [all])
Inst wine-compholio:i386 [1.5.29~quantal] (1.5.30~quantal compholio:12.10/quantal [i386])
Inst multiarch-support [2.15-0ubuntu20] (2.15-0ubuntu20.1 Ubuntu:12.10/quantal-updates [amd64])
Conf multiarch-support (2.15-0ubuntu20.1 Ubuntu:12.10/quantal-updates [amd64])
Inst isc-dhcp-client [4.2.4-1ubuntu10.1] (4.2.4-1ubuntu10.3 Ubuntu:12.10/quantal-updates [amd64]) []
Inst isc-dhcp-common [4.2.4-1ubuntu10.1] (4.2.4-1ubuntu10.3 Ubuntu:12.10/quantal-updates [amd64])
Inst rsyslog [5.8.6-1ubuntu9.1] (5.8.6-1ubuntu9.2 Ubuntu:12.10/quantal-updates [amd64])
Inst accountsservice [0.6.21-6ubuntu5] (0.6.21-6ubuntu5.1 Ubuntu:12.10/quantal-updates [amd64]) []
Inst libaccountsservice0 [0.6.21-6ubuntu5] (0.6.21-6ubuntu5.1 Ubuntu:12.10/quantal-updates [amd64])
Inst iptables [1.4.12-2ubuntu2.1] (1.4.12-2ubuntu2.2 Ubuntu:12.10/quantal-updates [amd64])
Inst openssl [1.0.1c-3ubuntu2.3] (1.0.1c-3ubuntu2.4 Ubuntu:12.10/quantal-updates [amd64])
Inst alsa-utils [1.0.25-3ubuntu2] (1.0.25-3ubuntu2.2 Ubuntu:12.10/quantal-updates [amd64])
Inst ffmpeg [6:0.8.5-0ubuntu0.12.10.1] (6:0.8.6-0ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [amd64])
Inst firefox-globalmenu [19.0.2+build1-0ubuntu0.12.10.1] (21.0+build2-0ubuntu0.12.10.2 Ubuntu:12.10/quantal-updates [amd64]) []
Inst firefox [19.0.2+build1-0ubuntu0.12.10.1] (21.0+build2-0ubuntu0.12.10.2 Ubuntu:12.10/quantal-updates [amd64])
Inst firefox-gnome-support [19.0.2+build1-0ubuntu0.12.10.1] (21.0+build2-0ubuntu0.12.10.2 Ubuntu:12.10/quantal-updates [amd64])
Inst firefox-locale-en [19.0.2+build1-0ubuntu0.12.10.1] (21.0+build2-0ubuntu0.12.10.2 Ubuntu:12.10/quantal-updates [amd64])
Inst flashplugin-installer [11.2.202.275ubuntu0.12.10.1] (11.2.202.285ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [amd64])
Inst google-talkplugin [3.16.0.0-1] (3.19.1.0-1 Google:1.0/stable [amd64])
Inst xul-ext-unity [2.4.4-0ubuntu0.1] (2.4.4-0ubuntu0.2 Ubuntu:12.10/quantal-updates [all]) []
Inst libufe-xidgetter0 [2.4.4-0ubuntu0.1] (2.4.4-0ubuntu0.2 Ubuntu:12.10/quantal-updates [amd64])
Inst linux-libc-dev [3.5.0-26.42] (3.5.0-31.52 Ubuntu:12.10/quantal-updates [amd64])
Inst poppler-utils [0.20.4-0ubuntu1.1] (0.20.4-0ubuntu1.2 Ubuntu:12.10/quantal-updates [amd64])
Inst telepathy-idle [0.1.12-1] (0.1.12-1ubuntu0.1 Ubuntu:12.10/quantal-updates [amd64])
Inst thunderbird-globalmenu [17.0.4+build1-0ubuntu0.12.10.1] (17.0.6+build1-0ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [amd64]) []
Inst thunderbird-locale-en [1:17.0.4+build1-0ubuntu0.12.10.1] (1:17.0.6+build1-0ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [amd64]) []
Inst thunderbird [17.0.4+build1-0ubuntu0.12.10.1] (17.0.6+build1-0ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [amd64]) [thunderbird-gnome-support:amd64 ]
Inst thunderbird-gnome-support [17.0.4+build1-0ubuntu0.12.10.1] (17.0.6+build1-0ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [amd64])
Inst thunderbird-locale-en-us [1:17.0.4+build1-0ubuntu0.12.10.1] (1:17.0.6+build1-0ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [all])
Inst xdiagnose [3.2.2] (3.2.4 Ubuntu:12.10/quantal-updates [all])
Inst xserver-xorg-video-intel [2:2.20.9-0ubuntu2] (2:2.20.9-0ubuntu2.1 Ubuntu:12.10/quantal-updates [amd64])
Inst icedtea-netx-common [1.3-1ubuntu1.1] (1.3.2-1ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [all])
Inst icedtea-7-plugin [1.3-1ubuntu1.1] (1.3.2-1ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [amd64]) []
Inst icedtea-netx [1.3-1ubuntu1.1] (1.3.2-1ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [amd64])
Inst spotify-client [1:0.8.4.103.g9cb177b.260-1] (1:0.9.0.133.gd18ed58.259-1 Spotify Public Repository:0.4/stable [amd64])
Inst spotify-client-qt [1:0.8.4.103.g9cb177b.260-1] (1:0.9.0.133.gd18ed58.259-1 Spotify Public Repository:0.4/stable [all])
Conf initramfs-tools (0.103ubuntu0.2 Ubuntu:12.10/quantal [all])
Conf linux-image-extra-3.5.0-26-generic (3.5.0-26.42 Ubuntu:12.10/quantal-updates [amd64])
Conf linux-image-3.5.0-28-generic (3.5.0-28.48 Ubuntu:12.10/quantal-updates [amd64])
Conf linux-image-extra-3.5.0-28-generic (3.5.0-28.48 Ubuntu:12.10/quantal-updates [amd64])
Conf linux-image-3.5.0-30-generic (3.5.0-30.51 Ubuntu:12.10/quantal-updates [amd64])
Conf linux-image-extra-3.5.0-30-generic (3.5.0-30.51 Ubuntu:12.10/quantal-updates [amd64])
Conf linux-image-3.5.0-31-generic (3.5.0-31.52 Ubuntu:12.10/quantal-updates [amd64])
Conf linux-image-extra-3.5.0-31-generic (3.5.0-31.52 Ubuntu:12.10/quantal-updates [amd64])
Conf linux-image-generic (3.5.0.31.47 Ubuntu:12.10/quantal-updates [amd64])
Conf libdrm-nouveau1a (2.4.43-0ubuntu0.1 Ubuntu:12.10/quantal-updates [amd64])
Conf libkms1 (2.4.43-0ubuntu0.1 Ubuntu:12.10/quantal-updates [amd64])
Conf apparmor (2.8.0-0ubuntu5.1 Ubuntu:12.10/quantal-updates [amd64])
Conf libcurl3-gnutls (7.27.0-1ubuntu1.2 Ubuntu:12.10/quantal-updates [amd64])
Conf libavutil-extra-51 (6:0.8.6ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [amd64])
Conf libavcodec-extra-53 (6:0.8.6ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [amd64])
Conf libavformat-extra-53 (6:0.8.6ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [amd64])
Conf libavdevice53 (6:0.8.6-0ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [amd64])
Conf libswscale-extra-2 (6:0.8.6ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [amd64])
Conf libavfilter2 (6:0.8.6-0ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [amd64])
Conf libpostproc-extra-52 (6:0.8.6ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [amd64])
Conf libav-tools (6:0.8.6-0ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [amd64])
Conf bamfdaemon (0.3.6-0ubuntu2 Ubuntu:12.10/quantal-updates [amd64])
Conf libbamf3-0 (0.3.6-0ubuntu2 Ubuntu:12.10/quantal-updates [amd64])
Conf libcurl3 (7.27.0-1ubuntu1.2 Ubuntu:12.10/quantal-updates [amd64])
Conf libcurl3-nss (7.27.0-1ubuntu1.2 Ubuntu:12.10/quantal-updates [amd64])
Conf xserver-common (2:1.13.0-0ubuntu6.2 Ubuntu:12.10/quantal-updates [all])
Conf xserver-xorg-core (2:1.13.0-0ubuntu6.2 Ubuntu:12.10/quantal-updates [amd64])
Conf mysql-common (5.5.31-0ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [all])
Conf libmysqlclient18:i386 (5.5.31-0ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [i386])
Conf libpoppler28 (0.20.4-0ubuntu1.2 Ubuntu:12.10/quantal-updates [amd64])
Conf libpoppler-glib8 (0.20.4-0ubuntu1.2 Ubuntu:12.10/quantal-updates [amd64])
Conf libxatracker1 (9.0.3-0ubuntu0.1 Ubuntu:12.10/quantal-updates [amd64])
Conf openjdk-7-jre-headless (7u21-2.3.9-0ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [amd64])
Conf openjdk-7-jre-lib (7u21-2.3.9-0ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [all])
Conf openjdk-7-jre (7u21-2.3.9-0ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [amd64])
Conf icedtea-7-jre-jamvm (7u21-2.3.9-0ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [amd64])
Conf wine-compholio:i386 (1.5.30~quantal compholio:12.10/quantal [i386])
Conf isc-dhcp-common (4.2.4-1ubuntu10.3 Ubuntu:12.10/quantal-updates [amd64])
Conf isc-dhcp-client (4.2.4-1ubuntu10.3 Ubuntu:12.10/quantal-updates [amd64])
Conf rsyslog (5.8.6-1ubuntu9.2 Ubuntu:12.10/quantal-updates [amd64])
Conf libaccountsservice0 (0.6.21-6ubuntu5.1 Ubuntu:12.10/quantal-updates [amd64])
Conf accountsservice (0.6.21-6ubuntu5.1 Ubuntu:12.10/quantal-updates [amd64])
Conf iptables (1.4.12-2ubuntu2.2 Ubuntu:12.10/quantal-updates [amd64])
Conf openssl (1.0.1c-3ubuntu2.4 Ubuntu:12.10/quantal-updates [amd64])
Conf alsa-utils (1.0.25-3ubuntu2.2 Ubuntu:12.10/quantal-updates [amd64])
Conf ffmpeg (6:0.8.6-0ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [amd64])
Conf firefox (21.0+build2-0ubuntu0.12.10.2 Ubuntu:12.10/quantal-updates [amd64])
Conf firefox-globalmenu (21.0+build2-0ubuntu0.12.10.2 Ubuntu:12.10/quantal-updates [amd64])
Conf firefox-gnome-support (21.0+build2-0ubuntu0.12.10.2 Ubuntu:12.10/quantal-updates [amd64])
Conf firefox-locale-en (21.0+build2-0ubuntu0.12.10.2 Ubuntu:12.10/quantal-updates [amd64])
Conf flashplugin-installer (11.2.202.285ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [amd64])
Conf google-talkplugin (3.19.1.0-1 Google:1.0/stable [amd64])
Conf libufe-xidgetter0 (2.4.4-0ubuntu0.2 Ubuntu:12.10/quantal-updates [amd64])
Conf xul-ext-unity (2.4.4-0ubuntu0.2 Ubuntu:12.10/quantal-updates [all])
Conf linux-libc-dev (3.5.0-31.52 Ubuntu:12.10/quantal-updates [amd64])
Conf poppler-utils (0.20.4-0ubuntu1.2 Ubuntu:12.10/quantal-updates [amd64])
Conf telepathy-idle (0.1.12-1ubuntu0.1 Ubuntu:12.10/quantal-updates [amd64])
Conf thunderbird (17.0.6+build1-0ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [amd64])
Conf thunderbird-globalmenu (17.0.6+build1-0ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [amd64])
Conf thunderbird-locale-en (1:17.0.6+build1-0ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [amd64])
Conf thunderbird-gnome-support (17.0.6+build1-0ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [amd64])
Conf thunderbird-locale-en-us (1:17.0.6+build1-0ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [all])
Conf xdiagnose (3.2.4 Ubuntu:12.10/quantal-updates [all])
Conf xserver-xorg-video-intel (2:2.20.9-0ubuntu2.1 Ubuntu:12.10/quantal-updates [amd64])
Conf icedtea-netx-common (1.3.2-1ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [all])
Conf icedtea-netx (1.3.2-1ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [amd64])
Conf icedtea-7-plugin (1.3.2-1ubuntu0.12.10.1 Ubuntu:12.10/quantal-updates [amd64])
Conf spotify-client (1:0.9.0.133.gd18ed58.259-1 Spotify Public Repository:0.4/stable [amd64])
Conf spotify-client-qt (1:0.9.0.133.gd18ed58.259-1 Spotify Public Repository:0.4/stable [all])

---

### Post by newb85 on 2013-05-27
It looks like the solution to the broken package system is simply to install those four linux-image packages listed at the top.  You could do this with

```
sudo apt-get install linux-image-3.5.0-28-generic linux-image-3.5.0-30-generic linux-image-3.5.0-31-generic linux-image-extra-3.5.0-31-generic
```

Also, it looks like it's been a while since you've updated your system.  I would recommend you do that as well.

```
sudo apt-get upgrade
```

---

