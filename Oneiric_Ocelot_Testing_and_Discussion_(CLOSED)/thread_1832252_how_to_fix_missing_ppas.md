---
title: "how to fix missing ppas?"
date: 2011-08-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ventrical on 2011-08-24
I tried an  apt-get  for distribution and here is the following:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  console-terminus
The following NEW packages will be installed:
  python-wnck
The following packages will be upgraded:
  accountsservice aptdaemon aptdaemon-data compiz compiz-core compiz-gnome
  compiz-plugins compiz-plugins-default compiz-plugins-main
  compiz-plugins-main-default compizconfig-backend-gconf
  compizconfig-settings-manager console-setup cups cups-bsd cups-client
  cups-common cups-ppdc deja-dup empathy empathy-common foo2zjs gcalctool
  gedit gedit-common gir1.2-notify-0.7 gnome-screensaver gnome-tweak-tool
  gstreamer0.10-gconf gstreamer0.10-plugins-bad gstreamer0.10-plugins-good
  gstreamer0.10-pulseaudio gvfs gvfs-backends gvfs-fuse gwibber
  gwibber-service gwibber-service-facebook gwibber-service-identica
  gwibber-service-twitter hpijs hplip hplip-cups hplip-data ibus-table
  ifupdown jockey-common jockey-gtk keyboard-configuration klibc-utils
  language-pack-en language-pack-gnome-en libaccountsservice0 libcaca0
  libcompizconfig0 libcups2 libcupscgi1 libcupsdriver1 libcupsimage2
  libcupsmime1 libcupsppdc1 libdecoration0 libenchant1c2a libgudev-1.0-0
  libgwibber-gtk2 libgwibber2 libhpmud0 libklibc liblightdm-gobject-1-0
  libmono-cairo4.0-cil libmono-corlib4.0-cil libmono-csharp4.0-cil
  libmono-i18n-west4.0-cil libmono-i18n4.0-cil libmono-posix4.0-cil
  libmono-security4.0-cil libmono-sharpzip4.84-cil
  libmono-system-configuration4.0-cil libmono-system-core4.0-cil
  libmono-system-drawing4.0-cil libmono-system-security4.0-cil
  libmono-system-xml4.0-cil libmono-system4.0-cil libnotify-bin libnotify4
  libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core
  libreoffice-draw libreoffice-emailmerge libreoffice-gnome libreoffice-gtk
  libreoffice-help-en-us libreoffice-impress libreoffice-math
  libreoffice-style-human libreoffice-writer libsane-hpaio libudev0 lightdm
  lightdm-gtk-greeter linux-firmware linux-headers-3.0.0-9
  linux-headers-3.0.0-9-generic linux-image-3.0.0-9-generic linux-libc-dev
  mono-4.0-gac mono-gac mono-runtime nautilus-sendto-empathy nautilus-share
  policykit-1-gnome pxljr python-aptdaemon python-aptdaemon-gtk
  python-aptdaemon.gtk3widgets python-aptdaemon.gtkwidgets python-compizconfig
  python-uno rastertosag-gdi simple-scan splix ttf-opensymbol udev
  unity-greeter uno-libs3 ure
128 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 178 MB of archives.
After this operation, 442 kB disk space will be freed.
Do you want to continue [Y/n]? y
Err [http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/](http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/) oneiric/main compiz-plugins-main i386 1:0.9.5.92-0ubuntu2~ppa2
  404  Not Found
Err [http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/](http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/) oneiric/main compiz-plugins i386 1:0.9.5.92+bzr2791-0ubuntu0~ppa2
  404  Not Found
Err [http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/](http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/) oneiric/main compiz-gnome i386 1:0.9.5.92+bzr2791-0ubuntu0~ppa2
  404  Not Found
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main keyboard-configuration all 1.57ubuntu25 [377 kB]
Err [http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/](http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/) oneiric/main compiz-plugins-default i386 1:0.9.5.92+bzr2791-0ubuntu0~ppa2
  404  Not Found
Err [http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/](http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/) oneiric/main compiz-plugins-main-default i386 1:0.9.5.92-0ubuntu2~ppa2
  404  Not Found
Err [http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/](http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/) oneiric/main compiz-core i386 1:0.9.5.92+bzr2791-0ubuntu0~ppa2
  404  Not Found
Err [http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/](http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/) oneiric/main libcompizconfig0 i386 1:0.9.5.92-0ubuntu2
  404  Not Found
Err [http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/](http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/) oneiric/main libdecoration0 i386 1:0.9.5.92+bzr2791-0ubuntu0~ppa2
  404  Not Found
Err [http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/](http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/) oneiric/main compizconfig-backend-gconf i386 1:0.9.5.92
  404  Not Found
Err [http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/](http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/) oneiric/main compiz all 1:0.9.5.92+bzr2791-0ubuntu0~ppa2
  404  Not Found
Err [http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/](http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/) oneiric/main python-compizconfig i386 1:0.9.5.92
  404  Not Found
Err [http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/](http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/) oneiric/main compizconfig-settings-manager all 1:0.9.5.92
  404  Not Found
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main console-setup all 1.57ubuntu25 [1,128 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libudev0 i386 173-0ubuntu3 [34.7 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main language-pack-en all 1:11.10+20110818 [291 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main language-pack-gnome-en all 1:11.10+20110818 [703 kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libcups2 i386 1.5.0-5 [176 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libcupscgi1 i386 1.5.0-5 [32.7 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libcupsdriver1 i386 1.5.0-5 [22.4 kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libcupsimage2 i386 1.5.0-5 [54.0 kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libcupsmime1 i386 1.5.0-5 [16.0 kB]
Get:11 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libcupsppdc1 i386 1.5.0-5 [55.4 kB]
Get:12 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libgudev-1.0-0 i386 1:173-0ubuntu3 [14.7 kB]
Get:13 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main lightdm i386 0.9.3-0ubuntu6 [86.4 kB]
Get:14 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main linux-image-3.0.0-9-generic i386 3.0.0-9.13 [36.3 MB]
Get:15 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main ure i386 3.4.1-4ubuntu1 [2,013 kB]
Get:16 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main uno-libs3 i386 3.4.1-4ubuntu1 [626 kB]
Get:17 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main ifupdown i386 0.7~alpha5.1ubuntu3 [46.8 kB]
Get:18 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main klibc-utils i386 1.5.22-1ubuntu2 [157 kB]
Get:19 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libklibc i386 1.5.22-1ubuntu2 [45.1 kB]
Get:20 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main foo2zjs i386 20110811dfsg-1ubuntu1 [1,447 kB]
Get:21 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main udev i386 173-0ubuntu3 [365 kB]
Get:22 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main accountsservice i386 0.6.13-1ubuntu4 [37.3 kB]
Get:23 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libaccountsservice0 i386 0.6.13-1ubuntu4 [28.5 kB]
Get:24 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main cups-common all 1.5.0-5 [713 kB]
Get:25 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main cups-bsd i386 1.5.0-5 [45.3 kB]
Get:26 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main cups-client i386 1.5.0-5 [632 kB]
Get:27 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main cups-ppdc i386 1.5.0-5 [31.3 kB]
Get:28 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main cups i386 1.5.0-5 [1,991 kB]
Get:29 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libnotify4 i386 0.7.3-2 [19.0 kB]
Get:30 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main deja-dup i386 19.90-0ubuntu1 [830 kB]
Get:31 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libenchant1c2a i386 1.6.0-3 [85.9 kB]
Get:32 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main nautilus-sendto-empathy i386 3.1.5.1-1ubuntu1 [558 kB]
Get:33 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main empathy i386 3.1.5.1-1ubuntu1 [2,220 kB]
Get:34 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main empathy-common all 3.1.5.1-1ubuntu1 [423 kB]
Get:35 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main gcalctool i386 6.1.5-0ubuntu1 [232 kB]
Get:36 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main gedit-common all 3.1.4-0ubuntu1 [159 kB]
Get:37 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main gedit i386 3.1.4-0ubuntu1 [540 kB]
Get:38 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main gir1.2-notify-0.7 i386 0.7.3-2 [3,708 B]
Get:39 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main gnome-screensaver i386 3.1.5-0ubuntu1 [102 kB]
Get:40 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/universe gnome-tweak-tool all 3.1.0-0ubuntu1 [67.1 kB]
Get:41 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main gstreamer0.10-gconf i386 0.10.30-1ubuntu6 [63.9 kB]
Get:42 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libcaca0 i386 0.99.beta17-2ubuntu1 [249 kB]
Get:43 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main gstreamer0.10-plugins-good i386 0.10.30-1ubuntu6 [1,933 kB]
Get:44 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/universe gstreamer0.10-plugins-bad i386 0.10.22-2ubuntu4 [1,690 kB]
Get:45 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main gstreamer0.10-pulseaudio i386 0.10.30-1ubuntu6 [90.0 kB]
Get:46 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main gvfs-fuse i386 1.9.3-0ubuntu1 [15.4 kB]
Get:47 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main gvfs i386 1.9.3-0ubuntu1 [334 kB]
Get:48 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main gvfs-backends i386 1.9.3-0ubuntu1 [287 kB]
Get:49 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main python-wnck i386 2.32.0-0ubuntu5 [45.0 kB]
Get:50 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main gwibber i386 3.1.5.1-0ubuntu1 [230 kB]
Get:51 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main gwibber-service all 3.1.5.1-0ubuntu1 [50.1 kB]
Get:52 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libgwibber2 i386 3.1.5.1-0ubuntu1 [68.6 kB]
Get:53 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libgwibber-gtk2 i386 3.1.5.1-0ubuntu1 [55.1 kB]
Get:54 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main gwibber-service-facebook all 3.1.5.1-0ubuntu1 [8,504 B]
Get:55 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main gwibber-service-identica all 3.1.5.1-0ubuntu1 [9,438 B]
Get:56 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main gwibber-service-twitter all 3.1.5.1-0ubuntu1 [9,560 B]
Get:57 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main hplip i386 3.11.7-0ubuntu4 [85.6 kB]
Get:58 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libsane-hpaio i386 3.11.7-0ubuntu4 [126 kB]
Get:59 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main hplip-data all 3.11.7-0ubuntu4 [7,350 kB]
Get:60 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main hplip-cups i386 3.11.7-0ubuntu4 [297 kB]
Get:61 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main hpijs i386 3.11.7-0ubuntu4 [362 kB]
Get:62 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libhpmud0 i386 3.11.7-0ubuntu4 [116 kB]
Get:63 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main ibus-table all 1.3.0.20100621-3ubuntu1 [208 kB]
Get:64 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main policykit-1-gnome i386 0.101-2ubuntu5 [27.5 kB]
Get:65 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main jockey-gtk all 0.9.4-0ubuntu2 [8,992 B]
Get:66 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main jockey-common all 0.9.4-0ubuntu2 [126 kB]
Get:67 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main liblightdm-gobject-1-0 i386 0.9.3-0ubuntu6 [30.7 kB]
Get:68 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libmono-system-xml4.0-cil all 2.10.4-3 [445 kB]
Get:69 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libmono-system-security4.0-cil all 2.10.4-3 [61.3 kB]
Get:70 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libmono-system-configuration4.0-cil all 2.10.4-3 [58.9 kB]
Get:71 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libmono-system4.0-cil all 2.10.4-3 [664 kB]
Get:72 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libmono-security4.0-cil all 2.10.4-3 [131 kB]
Get:73 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main mono-runtime i386 2.10.4-3 [1,521 kB]
Get:74 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main mono-gac all 2.10.4-3 [14.0 kB]
Get:75 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main mono-4.0-gac all 2.10.4-3 [19.8 kB]
Get:76 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libmono-corlib4.0-cil all 2.10.4-3 [1,007 kB]
Get:77 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libmono-cairo4.0-cil all 2.10.4-3 [35.2 kB]
Get:78 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libmono-posix4.0-cil all 2.10.4-3 [84.2 kB]
Get:79 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libmono-system-core4.0-cil all 2.10.4-3 [285 kB]
Get:80 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libmono-csharp4.0-cil all 2.10.4-3 [415 kB]
Get:81 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libmono-i18n4.0-cil all 2.10.4-3 [19.7 kB]
Get:82 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libmono-i18n-west4.0-cil all 2.10.4-3 [32.9 kB]
Get:83 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libmono-sharpzip4.84-cil all 2.10.4-3 [70.7 kB]
Get:84 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libmono-system-drawing4.0-cil all 2.10.4-3 [172 kB]
Get:85 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libnotify-bin i386 0.7.3-2 [7,100 B]
Get:86 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libreoffice-impress i386 1:3.4.1-4ubuntu1 [503 kB]
Get:87 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libreoffice-draw i386 1:3.4.1-4ubuntu1 [2,235 kB]
Get:88 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libreoffice-gtk i386 1:3.4.1-4ubuntu1 [159 kB]
Get:89 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libreoffice-gnome i386 1:3.4.1-4ubuntu1 [50.7 kB]
Get:90 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libreoffice-writer i386 1:3.4.1-4ubuntu1 [6,512 kB]
Get:91 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main python-uno i386 1:3.4.1-4ubuntu1 [169 kB]
Get:92 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main ttf-opensymbol all 2:2.4.3+LibO3.4.1-4ubuntu1 [110 kB]
Get:93 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libreoffice-math i386 1:3.4.1-4ubuntu1 [292 kB]
Get:94 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libreoffice-style-human all 1:3.4.1-4ubuntu1 [1,861 kB]
Get:95 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libreoffice-common all 1:3.4.1-4ubuntu1 [16.9 MB]
Get:96 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libreoffice-calc i386 1:3.4.1-4ubuntu1 [4,505 kB]
Get:97 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libreoffice-base-core i386 1:3.4.1-4ubuntu1 [625 kB]
Get:98 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libreoffice-core i386 1:3.4.1-4ubuntu1 [27.0 MB]
Get:99 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libreoffice-emailmerge all 1:3.4.1-4ubuntu1 [5,850 B]
Get:100 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main libreoffice-help-en-us all 1:3.4.1-4ubuntu1 [6,043 kB]
Get:101 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/universe lightdm-gtk-greeter i386 0.9.3-0ubuntu6 [24.0 kB]
Get:102 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main linux-firmware all 1.60 [21.4 MB]
Get:103 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main linux-headers-3.0.0-9 all 3.0.0-9.13 [11.1 MB]
Get:104 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main linux-headers-3.0.0-9-generic i386 3.0.0-9.13 [829 kB]
Get:105 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main linux-libc-dev i386 3.0.0-9.13 [805 kB]
Get:106 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main nautilus-share i386 0.7.3-1 [23.5 kB]
Get:107 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main pxljr i386 1.3-0ubuntu2 [58.0 kB]
Get:108 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main rastertosag-gdi all 0.1-0ubuntu3 [8,666 B]
Get:109 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main simple-scan i386 3.1.3-0ubuntu1 [114 kB]
Get:110 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main splix i386 2.0.0+20110720-0ubuntu2 [60.6 kB]
Get:111 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main unity-greeter i386 0.0.2-0ubuntu4 [30.1 kB]
Get:112 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main aptdaemon-data all 0.43+bzr674-0ubuntu1 [162 kB]
Get:113 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main python-aptdaemon-gtk all 0.43+bzr674-0ubuntu1 [1,666 B]
Get:114 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main python-aptdaemon.gtk3widgets all 0.43+bzr674-0ubuntu1 [14.2 kB]
Get:115 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main python-aptdaemon.gtkwidgets all 0.43+bzr674-0ubuntu1 [13.9 kB]
Get:116 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main aptdaemon all 0.43+bzr674-0ubuntu1 [14.0 kB]
Get:117 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main python-aptdaemon all 0.43+bzr674-0ubuntu1 [71.1 kB]
Fetched 173 MB in 11min 28s (252 kB/s)                                         
Failed to fetch [http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/pool/main/c/compiz-plugins-main/compiz-plugins-main_0.9.5.92-0ubuntu2~ppa2_i386.deb]("http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/pool/main/c/compiz-plugins-main/compiz-plugins-main_0.9.5.92-0ubuntu2%7Eppa2_i386.deb")  404  Not Found
Failed to fetch [http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/pool/main/c/compiz/compiz-plugins_0.9.5.92+bzr2791-0ubuntu0~ppa2_i386.deb]("http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/pool/main/c/compiz/compiz-plugins_0.9.5.92+bzr2791-0ubuntu0%7Eppa2_i386.deb")  404  Not Found
Failed to fetch [http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/pool/main/c/compiz/compiz-gnome_0.9.5.92+bzr2791-0ubuntu0~ppa2_i386.deb]("http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/pool/main/c/compiz/compiz-gnome_0.9.5.92+bzr2791-0ubuntu0%7Eppa2_i386.deb")  404  Not Found
Failed to fetch [http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/pool/main/c/compiz/compiz-plugins-default_0.9.5.92+bzr2791-0ubuntu0~ppa2_i386.deb]("http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/pool/main/c/compiz/compiz-plugins-default_0.9.5.92+bzr2791-0ubuntu0%7Eppa2_i386.deb")  404  Not Found
Failed to fetch [http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/pool/main/c/compiz-plugins-main/compiz-plugins-main-default_0.9.5.92-0ubuntu2~ppa2_i386.deb]("http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/pool/main/c/compiz-plugins-main/compiz-plugins-main-default_0.9.5.92-0ubuntu2%7Eppa2_i386.deb")  404  Not Found
Failed to fetch [http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/pool/main/c/compiz/compiz-core_0.9.5.92+bzr2791-0ubuntu0~ppa2_i386.deb]("http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/pool/main/c/compiz/compiz-core_0.9.5.92+bzr2791-0ubuntu0%7Eppa2_i386.deb")  404  Not Found
Failed to fetch [http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/pool/main/libc/libcompizconfig/libcompizconfig0_0.9.5.92-0ubuntu2_i386.deb](http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/pool/main/libc/libcompizconfig/libcompizconfig0_0.9.5.92-0ubuntu2_i386.deb)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/pool/main/c/compiz/libdecoration0_0.9.5.92+bzr2791-0ubuntu0~ppa2_i386.deb]("http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/pool/main/c/compiz/libdecoration0_0.9.5.92+bzr2791-0ubuntu0%7Eppa2_i386.deb")  404  Not Found
Failed to fetch [http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/pool/main/c/compizconfig-backend-gconf/compizconfig-backend-gconf_0.9.5.92_i386.deb](http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/pool/main/c/compizconfig-backend-gconf/compizconfig-backend-gconf_0.9.5.92_i386.deb)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/pool/main/c/compiz/compiz_0.9.5.92+bzr2791-0ubuntu0~ppa2_all.deb]("http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/pool/main/c/compiz/compiz_0.9.5.92+bzr2791-0ubuntu0%7Eppa2_all.deb")  404  Not Found
Failed to fetch [http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/pool/main/c/compizconfig-python/python-compizconfig_0.9.5.92_i386.deb](http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/pool/main/c/compizconfig-python/python-compizconfig_0.9.5.92_i386.deb)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/pool/main/c/compizconfig-settings-manager/compizconfig-settings-manager_0.9.5.92_all.deb](http://ppa.launchpad.net/unity-team/compiz-testing/ubuntu/pool/main/c/compizconfig-settings-manager/compizconfig-settings-manager_0.9.5.92_all.deb)  404  Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
d-ME051:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
-ME051:~$ sudo -i
-ME051:~# 
pswd: command not found
root@-ME051:~# apt-get update
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg          
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]            
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg [316 B]           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                         
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release [9,754 B]             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric InRelease                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports InRelease
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release.gpg [198 B]                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                              
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources [893 B]          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release.gpg                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release.gpg                 
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages [1,573 B]            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages       
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release [39.8 kB]                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release            
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Sources [874 kB]      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Sources [5,308 B]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Sources [4,723 kB]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Sources [153 kB]        
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main i386 Packages [1,580 kB]      
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted i386 Packages [9,002 B] 
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe i386 Packages [6,459 kB]  
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse i386 Packages [181 kB]  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main i386 Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main i386 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main TranslationIndex                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse TranslationIndex           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted TranslationIndex           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main TranslationIndex         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe TranslationIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main TranslationIndex       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe TranslationIndex   
Fetched 14.0 MB in 1min 11s (196 kB/s)                                         
Reading package lists... Done
root@d-ME051:~# --fix-missing?
--fix-missing?: command not found
root@-ME051:~# apt-get --fix-missing
apt 0.8.16~exp5ubuntu6 for i386 compiled on Aug 17 2011 09:57:30
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   autoremove - Remove automatically all unused packages
   purge - Remove packages and config files
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies
   changelog - Download and display the changelog for the given package
   download - Download the binary package into the current directory

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to correct a system with broken dependencies in place
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.
root@-ME051:~# --fix-missing
--fix-missing: command not found
root@-ME051:~#
```

---

### Post by lkjoel on 2011-08-24
Try this command:
```
sudo apt-get update --fix-missing

```

---

### Post by jbicha on 2011-08-24
> **lkjoel said:**
> Try this command:]

No, that command does something totally different.

Go into Software Sources. Switch to the Other Software tab. Click Edit on one of your PPA sources. Many PPA creators don't bother updating their listed distributions for oneiric so you need to put natty or whatever for the distribution line.

Really though you need to go the PPA's webpage to verify what distribution is supported. When you're there, click the "Published in:" dropdown to see which are supported.

Generally, you can still use packages built for older releases although there are exceptions. Unity in Oneiric uses GTK3 so I don't think old "indicator" status menus work in Oneiric for instance.

---

### Post by meborc on 2011-08-25
you can also just go into your /etc/apt/sources.list and /etc/apt/sources.list.d/* and start commenting out the lines that conflict

---

### Post by Framli on 2011-08-25
I have this bash script to check every release supported by PPA in your sources. You need to "apt-get curl zenity" before running it.

---

