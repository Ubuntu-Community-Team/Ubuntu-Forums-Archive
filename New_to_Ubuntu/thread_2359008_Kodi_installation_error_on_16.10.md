---
title: "Kodi installation error on 16.10"
date: 2017-04-19
forum: New to Ubuntu
---

### Post by anbu-s on 2017-04-19
I tried to install kodi on my new ubuntu install 16.10. I got the following error msg

my PPA - sudo add-apt-repository ppa:team-xbmc/ppa
```

sudo apt-get install kodi
[sudo] password for anbu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fonts-roboto-hinted javascript-common kodi-data kodi-visualization-spectrum
  libavfilter6 libavresample3 libcec3 libcrossguid0 libjs-iscroll libjs-jquery
  libpostproc54 librubberband2v5 libsdl2-2.0-0 libsndio6.1
  linux-headers-4.8.0-41 linux-headers-4.8.0-41-generic
  linux-image-4.8.0-41-generic linux-image-extra-4.8.0-41-generic
  linux-signed-image-4.8.0-41-generic
Use 'sudo apt autoremove' to remove them.
Suggested packages:
  kodi-pvr-mythtv kodi-pvr-vuplus kodi-pvr-vdr-vnsi kodi-pvr-njoy
  kodi-pvr-nextpvr kodi-pvr-mediaportal-tvserver kodi-pvr-tvheadend-hts
  kodi-pvr-dvbviewer kodi-pvr-argustv kodi-pvr-iptvsimple
  kodi-audioencoder-vorbis kodi-audioencoder-flac kodi-audioencoder-lame
Recommended packages:
  libva-intel-vaapi-driver
The following NEW packages will be installed:
  kodi
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
Need to get 0 B/20.1 MB of archives.
After this operation, 37.1 MB of additional disk space will be used.
(Reading database ... 236346 files and directories currently installed.)
Preparing to unpack .../kodi_2%3a17.1~git20170320.2031-final-0yakkety_all.deb ...
Unpacking kodi (2:17.1~git20170320.2031-final-0yakkety) ...
dpkg: error processing archive /var/cache/apt/archives/kodi_2%3a17.1~git20170320.2031-final-0yakkety_all.deb (--unpack):
 trying to overwrite '/usr/share/icons/hicolor/128x128/apps/kodi.png', which is also in package kodi-data 16.1+dfsg1-2
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kodi_2%3a17.1~git20170320.2031-final-0yakkety_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any help would be appreciated

---

### Post by deadflowr on 2017-04-20
The fix is shown in the output.
> The following packages were automatically installed and are no longer required:
  fonts-roboto-hinted javascript-common **kodi-data** kodi-visualization-spectrum
  libavfilter6 libavresample3 libcec3 libcrossguid0 libjs-iscroll libjs-jquery
  libpostproc54 librubberband2v5 libsdl2-2.0-0 libsndio6.1
  linux-headers-4.8.0-41 linux-headers-4.8.0-41-generic
  linux-image-4.8.0-41-generic linux-image-extra-4.8.0-41-generic
  linux-signed-image-4.8.0-41-generic
Use 'sudo apt autoremove' to remove them.
you have kodi-data already installed, but it conflicts with kodi from the xbmc ppa, which shows in the error:
> dpkg: error processing archive /var/cache/apt/archives/kodi_2%3a17.1~git20170320.2031-final-0yakkety_all.deb (--unpack):
 trying to overwrite '/usr/share/icons/hicolor/128x128/apps/kodi.png', which is also in package **kodi-data **16.1+dfsg1-2
Basically, try running the autoremove command, and then try installing the ppa kodi.
or just remove kodi-data.

---

### Post by russkyca on 2017-04-21
It won't update in Ubuntu 17.04 Zesty either.   Looks like a lot of problems when trying to use Ubuntu with this software.

---

