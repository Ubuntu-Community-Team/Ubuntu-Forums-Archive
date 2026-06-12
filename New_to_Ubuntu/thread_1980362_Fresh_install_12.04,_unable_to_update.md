---
title: "Fresh install 12.04, unable to update"
date: 2012-05-15
forum: New to Ubuntu
---

### Post by fisheater on 2012-05-15
Hi,

I just did a fresh instal of 12.04, then ran

```
sudo apt-get upgrade; sudo apt-get update; sudo apt-get distribution
```

it did not instal the updates

When I tried the software center to update and watch the progress bar -> nearly all the updates fail.

I have tried to change to source for the files in software sources, with no luck. Even reinstalled the OS, no luck.

Suggestions?

TY 

FE

---

### Post by Peripheral Visionary on 2012-05-15
You installed the latest version and then tried to upGRADE instead of upDATE.

A freshly installed Ubuntu will update itself automatically immediately after installation. Or you may also have taken the option when you installed it from the LiveCD to download and install the updates *during* the installation.

Do nothing! You're all set.

---

### Post by mörgæs on 2012-05-15
And for later maintenance: Run

```
sudo apt-get update
```

before

```
sudo apt-get upgrade
```

---

### Post by lolpenguin on 2012-05-15
> **fisheater said:**
> Hi,

I just did a fresh instal of 12.04, then ran

```
sudo apt-get upgrade; sudo apt-get update; sudo apt-get distribution
```

it did not instal the updates

When I tried the software center to update and watch the progress bar -> nearly all the updates fail.

I have tried to change to source for the files in software sources, with no luck. Even reinstalled the OS, no luck.

Suggestions?

TY 

FE

There is no such thing as ```
apt-get distribution
```
You may be looking for ```
apt-get dist-upgrade
```

---

### Post by garvinrick4 on 2012-05-15
Do not know if you have all repositories open in Software Sources.

---

### Post by fisheater on 2012-05-16
Thanks for all you insight, here is a summary of events:

1. I have selected all the radio boxes suggested by garvinrick4
2. I have corrected my apt-get update, apt-get upgrade
3. I have tried to change my servers from a few in Canada to a few in the US

But if I am reading this output correctly, it is not getting the files.

```
 sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic-pae linux-headers-generic-pae linux-image-generic-pae
The following packages will be upgraded:
  apport apport-gtk at-spi2-core compiz compiz-core compiz-gnome
  compiz-plugins-default dmsetup evolution-data-server
  evolution-data-server-common firefox firefox-globalmenu
  firefox-gnome-support firefox-locale-en fonts-opensymbol gdb
  gir1.2-atspi-2.0 gir1.2-unity-5.0 glib-networking glib-networking-common
  glib-networking-services gnome-control-center gnome-control-center-data
  gnome-games-data gnome-orca gnome-settings-daemon gnome-sudoku gnomine
  gwibber gwibber-service gwibber-service-facebook gwibber-service-identica
  gwibber-service-twitter hdparm indicator-sound language-pack-en
  language-pack-en-base language-pack-gnome-en language-pack-gnome-en-base
  libatspi2.0-0 libcamel-1.2-29 libdecoration0 libdevmapper-event1.02.1
  libdevmapper1.02.1 libebackend-1.2-1 libebook-1.2-12 libecal-1.2-10
  libedata-book-1.2-11 libedata-cal-1.2-13 libedataserver-1.2-15
  libedataserverui-3.0-1 libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa
  libglu1-mesa libgnome-control-center1 libgwibber-gtk2 libgwibber2
  liblvm2app2.2 libnm-glib-vpn1 libnm-glib4 libnm-util2 libnux-2.0-0
  libnux-2.0-common liborbit2 libqt4-dbus libqt4-declarative libqt4-network
  libqt4-opengl libqt4-script libqt4-sql libqt4-sql-sqlite libqt4-svg
  libqt4-xml libqt4-xmlpatterns libqtbamf1 libqtcore4 libqtgui4
  libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core
  libreoffice-draw libreoffice-emailmerge libreoffice-gnome libreoffice-gtk
  libreoffice-help-en-us libreoffice-impress libreoffice-math
  libreoffice-style-human libreoffice-style-tango libreoffice-writer
  libsasl2-2 libsasl2-modules libsmbclient libssl1.0.0 libtasn1-3
  libunity-2d-private0 libunity-core-5.0-5 libunity9 libutouch-geis1
  libwbclient0 libxatracker1 libzeitgeist-1.0-1 linux-libc-dev mahjongg
  network-manager nux-tools openssl python-apport python-problem-report
  python-software-properties python-ubuntu-sso-client python-uno
  python-zeitgeist qdbus remmina remmina-common remmina-plugin-rdp
  remmina-plugin-vnc resolvconf samba-common samba-common-bin sessioninstaller
  simple-scan smbclient software-center software-properties-common
  software-properties-gtk sudo thunderbird thunderbird-globalmenu
  thunderbird-gnome-support ubuntu-docs ubuntu-sso-client
  ubuntu-sso-client-gtk unity unity-2d unity-2d-common unity-2d-panel
  unity-2d-shell unity-2d-spread unity-common unity-greeter
  unity-lens-applications unity-lens-music unity-scope-musicstores
  unity-services uno-libs3 update-manager update-manager-core upstart ure
  vim-common vim-tiny vino xserver-common xserver-xorg-core
  xserver-xorg-input-synaptics xul-ext-ubufox zeitgeist zeitgeist-core zenity
  zenity-common
164 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 129 MB/200 MB of archives.
After this operation, 4,973 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://ubuntu.cs.utah.edu/ubuntu/ precise-proposed/main libgl1-mesa-dri i386 8.0.2-0ubuntu3.1 [3,041 kB]
Err http://ubuntu.cs.utah.edu/ubuntu/ precise-proposed/main libgl1-mesa-glx i386 8.0.2-0ubuntu3.1
  400  Invalid header received from client
Get:2 http://ubuntu.cs.utah.edu/ubuntu/ precise-proposed/main libglapi-mesa i386 8.0.2-0ubuntu3.1 [20.9 kB]
Err http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main liborbit2 i386 1:2.14.19-0.1ubuntu1
  400  Invalid header received from client
Get:3 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main libqt4-svg i386 4:4.8.1-0ubuntu4.1 [139 kB]
Get:4 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main libqt4-opengl i386 4:4.8.1-0ubuntu4.1 [301 kB]
Get:5 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main libqtgui4 i386 4:4.8.1-0ubuntu4.1 [4,124 kB]
Get:6 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main libqt4-declarative i386 4:4.8.1-0ubuntu4.1 [1,087 kB]
Get:7 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main libqt4-xmlpatterns i386 4:4.8.1-0ubuntu4.1 [1,057 kB]
Get:8 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main libqt4-network i386 4:4.8.1-0ubuntu4.1 [556 kB]
Get:9 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main libqt4-script i386 4:4.8.1-0ubuntu4.1 [800 kB]
Get:10 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main libqt4-sql-sqlite i386 4:4.8.1-0ubuntu4.1 [23.0 kB]
Get:11 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main libqt4-sql i386 4:4.8.1-0ubuntu4.1 [99.9 kB]
Get:12 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main qdbus i386 4:4.8.1-0ubuntu4.1 [28.9 kB]
Get:13 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main libqt4-dbus i386 4:4.8.1-0ubuntu4.1 [185 kB]
Get:14 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main libqt4-xml i386 4:4.8.1-0ubuntu4.1 [92.8 kB]
Get:15 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main libqtcore4 i386 4:4.8.1-0ubuntu4.1 [2,061 kB]
Get:16 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main uno-libs3 i386 3.5.3-0ubuntu1 [591 kB]
Get:17 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main libreoffice-writer i386 1:3.5.3-0ubuntu1 [7,654 kB]
Get:18 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main libreoffice-calc i386 1:3.5.3-0ubuntu1 [6,284 kB]
Get:19 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main libreoffice-base-core i386 1:3.5.3-0ubuntu1 [823 kB]
Get:20 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main libreoffice-impress i386 1:3.5.3-0ubuntu1 [657 kB]
Get:21 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main libreoffice-draw i386 1:3.5.3-0ubuntu1 [3,170 kB]
Get:22 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main libreoffice-gtk i386 1:3.5.3-0ubuntu1 [224 kB]
Get:23 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main libreoffice-gnome i386 1:3.5.3-0ubuntu1 [83.8 kB]
Get:24 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main python-uno i386 1:3.5.3-0ubuntu1 [155 kB]
Get:25 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main libreoffice-common all 1:3.5.3-0ubuntu1 [20.9 MB]
Get:26 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main libreoffice-core i386 1:3.5.3-0ubuntu1 [37.2 MB]
Get:27 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main fonts-opensymbol all 2:102.2+LibO3.5.3-0ubuntu1 [140 kB]
Get:28 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main libreoffice-style-human all 1:3.5.3-0ubuntu1 [2,072 kB]
Get:29 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main libreoffice-style-tango all 1:3.5.3-0ubuntu1 [1,861 kB]
Get:30 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main libwbclient0 i386 2:3.6.3-2ubuntu2.1 [30.5 kB]
Get:31 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main libsmbclient i386 2:3.6.3-2ubuntu2.1 [2,135 kB]
Get:32 http://ubuntu.cs.utah.edu/ubuntu/ precise-proposed/main libxatracker1 i386 8.0.2-0ubuntu3.1 [353 kB]
Get:33 http://ubuntu.cs.utah.edu/ubuntu/ precise-proposed/main linux-image-3.2.0-24-generic-pae i386 3.2.0-24.38 [38.1 MB]
Get:34 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main libnm-util2 i386 0.9.4.0-0ubuntu4 [136 kB]
Get:35 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main libnm-glib4 i386 0.9.4.0-0ubuntu4 [85.5 kB]
Get:36 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main network-manager i386 0.9.4.0-0ubuntu4 [528 kB]
Get:37 http://ubuntu.cs.utah.edu/ubuntu/ precise-proposed/main ubuntu-docs all 12.04.5 [1,449 kB]
Get:38 http://ubuntu.cs.utah.edu/ubuntu/ precise-proposed/main libglu1-mesa i386 8.0.2-0ubuntu3.1 [165 kB]
Get:39 http://ubuntu.cs.utah.edu/ubuntu/ precise-proposed/main libutouch-geis1 i386 2.2.9-0ubuntu3 [75.8 kB]
Get:40 http://ubuntu.cs.utah.edu/ubuntu/ precise-proposed/main ubuntu-sso-client-gtk all 3.0.0-0ubuntu2 [14.8 kB]
Get:41 http://ubuntu.cs.utah.edu/ubuntu/ precise-proposed/main ubuntu-sso-client all 3.0.0-0ubuntu2 [3,062 B]
Get:42 http://ubuntu.cs.utah.edu/ubuntu/ precise-proposed/main python-ubuntu-sso-client all 3.0.0-0ubuntu2 [55.5 kB]
Get:43 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main libdevmapper1.02.1 i386 2:1.02.48-4ubuntu7.1 [67.6 kB]
Get:44 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main dmsetup i386 2:1.02.48-4ubuntu7.1 [37.1 kB]
Get:45 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main sudo i386 1.8.3p1-1ubuntu3.1 [281 kB]
Get:46 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main vim-tiny i386 2:7.3.429-2ubuntu2.1 [380 kB]
Get:47 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main vim-common i386 2:7.3.429-2ubuntu2.1 [85.8 kB]
Get:48 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main hdparm i386 9.37-0ubuntu3.1 [92.3 kB]
Get:49 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main openssl i386 1.0.1-4ubuntu5 [519 kB]
Get:50 http://ubuntu.cs.utah.edu/ubuntu/ precise-proposed/main update-manager-core i386 1:0.156.14.2 [181 kB]
Get:51 http://ubuntu.cs.utah.edu/ubuntu/ precise-proposed/main update-manager all 1:0.156.14.2 [607 kB]
Get:52 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main python-problem-report all 2.0.1-0ubuntu7 [9,550 B]
Get:53 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main python-apport all 2.0.1-0ubuntu7 [78.2 kB]
Get:54 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main apport all 2.0.1-0ubuntu7 [141 kB]
Get:55 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main apport-gtk all 2.0.1-0ubuntu7 [9,306 B]
Get:56 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main at-spi2-core i386 2.4.1-0ubuntu0.1 [43.9 kB]
Get:57 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main libunity9 i386 5.12.0-0ubuntu1 [161 kB]
Get:58 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main libnux-2.0-0 i386 2.12.0-0ubuntu1 [908 kB]
Get:59 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main libnux-2.0-common all 2.12.0-0ubuntu1 [63.8 kB]
Get:60 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main compiz-gnome i386 1:0.9.7.8-0ubuntu1 [301 kB]
Get:61 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main compiz-plugins-default i386 1:0.9.7.8-0ubuntu1 [667 kB]
Get:62 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main compiz-core i386 1:0.9.7.8-0ubuntu1 [369 kB]
Get:63 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main unity i386 5.12-0ubuntu1 [1,279 kB]
Get:64 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main libunity-core-5.0-5 i386 5.12-0ubuntu1 [234 kB]
Get:65 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main unity-services i386 5.12-0ubuntu1 [37.0 kB]
Get:66 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main unity-common all 5.12-0ubuntu1 [149 kB]
Get:67 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main nux-tools i386 2.12.0-0ubuntu1 [11.8 kB]
Get:68 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main libdecoration0 i386 1:0.9.7.8-0ubuntu1 [38.3 kB]
Get:69 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main compiz all 1:0.9.7.8-0ubuntu1 [3,290 B]
Get:70 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main libedataserver-1.2-15 i386 3.2.3-0ubuntu7 [183 kB]
Get:71 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main evolution-data-server i386 3.2.3-0ubuntu7 [519 kB]
Get:72 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main libcamel-1.2-29 i386 3.2.3-0ubuntu7 [446 kB]
Get:73 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main libebackend-1.2-1 i386 3.2.3-0ubuntu7 [18.0 kB]
Get:74 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main libebook-1.2-12 i386 3.2.3-0ubuntu7 [105 kB]
Get:75 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main libecal-1.2-10 i386 3.2.3-0ubuntu7 [145 kB]
Get:76 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main libedata-book-1.2-11 i386 3.2.3-0ubuntu7 [73.9 kB]
Get:77 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main libedata-cal-1.2-13 i386 3.2.3-0ubuntu7 [91.4 kB]
Get:78 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main evolution-data-server-common all 3.2.3-0ubuntu7 [90.1 kB]
Get:79 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main firefox-globalmenu i386 12.0+build1-0ubuntu0.12.04.1 [48.5 kB]
Get:80 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main firefox i386 12.0+build1-0ubuntu0.12.04.1 [18.3 MB]
Get:81 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main firefox-gnome-support i386 12.0+build1-0ubuntu0.12.04.1 [9,268 B]
Get:82 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main firefox-locale-en i386 12.0+build1-0ubuntu0.12.04.1 [423 kB]
Get:83 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main gdb i386 7.4-2012.04-0ubuntu2 [2,116 kB]
Get:84 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main gir1.2-atspi-2.0 i386 2.4.1-0ubuntu0.1 [16.1 kB]
Get:85 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main gir1.2-unity-5.0 i386 5.12.0-0ubuntu1 [9,898 B]
Get:86 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main glib-networking-services i386 2.32.1-1ubuntu1 [11.9 kB]
Get:87 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main glib-networking i386 2.32.1-1ubuntu1 [51.3 kB]
Get:88 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main glib-networking-common all 2.32.1-1ubuntu1 [5,978 B]
Get:89 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main gnome-control-center-data all 1:3.4.1-0ubuntu2 [1,121 kB]
Get:90 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main libgnome-control-center1 i386 1:3.4.1-0ubuntu2 [80.0 kB]
Get:91 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main gnome-control-center i386 1:3.4.1-0ubuntu2 [660 kB]
Get:92 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main mahjongg i386 1:3.4.1-0ubuntu2 [2,333 kB]
Get:93 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main gnomine i386 1:3.4.1-0ubuntu2 [416 kB]
Get:94 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main gnome-sudoku all 1:3.4.1-0ubuntu2 [765 kB]
Get:95 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main gnome-games-data all 1:3.4.1-0ubuntu2 [106 kB]
Get:96 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main linux-generic-pae i386 3.2.0.24.26 [1,718 B]
Get:97 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main linux-image-generic-pae i386 3.2.0.24.26 [2,528 B]
Get:98 http://ubuntu.cs.utah.edu/ubuntu/ precise-proposed/main linux-headers-3.2.0-24 all 3.2.0-24.38 [11.7 MB]
Get:99 http://ubuntu.cs.utah.edu/ubuntu/ precise-proposed/main linux-headers-3.2.0-24-generic-pae i386 3.2.0-24.38 [955 kB]
Get:100 http://ubuntu.cs.utah.edu/ubuntu/ precise-updates/main linux-headers-generic-pae i386 3.2.0.24.26 [2,528 B]
Fetched 194 MB in 3min 41s (878 kB/s)                                          
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/m/mesa/libgl1-mesa-glx_8.0.2-0ubuntu3.1_i386.deb 400  Invalid header received from client
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/o/orbit2/liborbit2_2.14.19-0.1ubuntu1_i386.deb 400  Invalid header received from client
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/q/qt4-x11/libqt4-opengl_4.8.1-0ubuntu4.1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/q/qt4-x11/libqtgui4_4.8.1-0ubuntu4.1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/q/qt4-x11/libqt4-declarative_4.8.1-0ubuntu4.1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/q/qt4-x11/libqt4-xmlpatterns_4.8.1-0ubuntu4.1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/q/qt4-x11/libqt4-network_4.8.1-0ubuntu4.1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/q/qt4-x11/libqt4-script_4.8.1-0ubuntu4.1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/q/qt4-x11/libqt4-sql-sqlite_4.8.1-0ubuntu4.1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/q/qt4-x11/libqt4-sql_4.8.1-0ubuntu4.1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/q/qt4-x11/qdbus_4.8.1-0ubuntu4.1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/q/qt4-x11/libqt4-dbus_4.8.1-0ubuntu4.1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/q/qt4-x11/libqt4-xml_4.8.1-0ubuntu4.1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/q/qt4-x11/libqtcore4_4.8.1-0ubuntu4.1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/libr/libreoffice/uno-libs3_3.5.3-0ubuntu1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/libr/libreoffice/libreoffice-writer_3.5.3-0ubuntu1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/libr/libreoffice/libreoffice-calc_3.5.3-0ubuntu1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/libr/libreoffice/libreoffice-base-core_3.5.3-0ubuntu1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/libr/libreoffice/libreoffice-impress_3.5.3-0ubuntu1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/libr/libreoffice/libreoffice-draw_3.5.3-0ubuntu1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/libr/libreoffice/libreoffice-gtk_3.5.3-0ubuntu1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/libr/libreoffice/libreoffice-gnome_3.5.3-0ubuntu1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/libr/libreoffice/python-uno_3.5.3-0ubuntu1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/libr/libreoffice/libreoffice-common_3.5.3-0ubuntu1_all.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/libr/libreoffice/libreoffice-core_3.5.3-0ubuntu1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/libr/libreoffice/fonts-opensymbol_102.2+LibO3.5.3-0ubuntu1_all.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/libr/libreoffice/libreoffice-style-human_3.5.3-0ubuntu1_all.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/libr/libreoffice/libreoffice-style-tango_3.5.3-0ubuntu1_all.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/s/samba/libwbclient0_3.6.3-2ubuntu2.1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/s/samba/libsmbclient_3.6.3-2ubuntu2.1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/m/mesa/libxatracker1_8.0.2-0ubuntu3.1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/l/linux/linux-image-3.2.0-24-generic-pae_3.2.0-24.38_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/n/network-manager/libnm-util2_0.9.4.0-0ubuntu4_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/n/network-manager/libnm-glib4_0.9.4.0-0ubuntu4_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/n/network-manager/network-manager_0.9.4.0-0ubuntu4_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/u/ubuntu-docs/ubuntu-docs_12.04.5_all.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/m/mesa/libglu1-mesa_8.0.2-0ubuntu3.1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/u/utouch-geis/libutouch-geis1_2.2.9-0ubuntu3_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/u/ubuntu-sso-client/ubuntu-sso-client-gtk_3.0.0-0ubuntu2_all.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/u/ubuntu-sso-client/ubuntu-sso-client_3.0.0-0ubuntu2_all.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/u/ubuntu-sso-client/python-ubuntu-sso-client_3.0.0-0ubuntu2_all.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/l/lvm2/libdevmapper1.02.1_1.02.48-4ubuntu7.1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/l/lvm2/dmsetup_1.02.48-4ubuntu7.1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/s/sudo/sudo_1.8.3p1-1ubuntu3.1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/v/vim/vim-tiny_7.3.429-2ubuntu2.1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/v/vim/vim-common_7.3.429-2ubuntu2.1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/h/hdparm/hdparm_9.37-0ubuntu3.1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/o/openssl/openssl_1.0.1-4ubuntu5_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/u/update-manager/update-manager-core_0.156.14.2_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/u/update-manager/update-manager_0.156.14.2_all.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/a/apport/python-problem-report_2.0.1-0ubuntu7_all.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/a/apport/python-apport_2.0.1-0ubuntu7_all.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/a/apport/apport_2.0.1-0ubuntu7_all.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/a/apport/apport-gtk_2.0.1-0ubuntu7_all.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/a/at-spi2-core/at-spi2-core_2.4.1-0ubuntu0.1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/libu/libunity/libunity9_5.12.0-0ubuntu1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/n/nux/libnux-2.0-0_2.12.0-0ubuntu1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/n/nux/libnux-2.0-common_2.12.0-0ubuntu1_all.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/c/compiz/compiz-gnome_0.9.7.8-0ubuntu1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/c/compiz/compiz-plugins-default_0.9.7.8-0ubuntu1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/c/compiz/compiz-core_0.9.7.8-0ubuntu1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/u/unity/unity_5.12-0ubuntu1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/u/unity/libunity-core-5.0-5_5.12-0ubuntu1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/u/unity/unity-services_5.12-0ubuntu1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/u/unity/unity-common_5.12-0ubuntu1_all.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/n/nux/nux-tools_2.12.0-0ubuntu1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/c/compiz/libdecoration0_0.9.7.8-0ubuntu1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/c/compiz/compiz_0.9.7.8-0ubuntu1_all.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/e/evolution-data-server/libedataserver-1.2-15_3.2.3-0ubuntu7_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/e/evolution-data-server/evolution-data-server_3.2.3-0ubuntu7_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/e/evolution-data-server/libcamel-1.2-29_3.2.3-0ubuntu7_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/e/evolution-data-server/libebackend-1.2-1_3.2.3-0ubuntu7_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/e/evolution-data-server/libebook-1.2-12_3.2.3-0ubuntu7_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/e/evolution-data-server/libecal-1.2-10_3.2.3-0ubuntu7_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/e/evolution-data-server/libedata-book-1.2-11_3.2.3-0ubuntu7_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/e/evolution-data-server/libedata-cal-1.2-13_3.2.3-0ubuntu7_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/e/evolution-data-server/evolution-data-server-common_3.2.3-0ubuntu7_all.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/f/firefox/firefox-globalmenu_12.0+build1-0ubuntu0.12.04.1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/f/firefox/firefox_12.0+build1-0ubuntu0.12.04.1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/f/firefox/firefox-gnome-support_12.0+build1-0ubuntu0.12.04.1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/f/firefox/firefox-locale-en_12.0+build1-0ubuntu0.12.04.1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/g/gdb/gdb_7.4-2012.04-0ubuntu2_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/a/at-spi2-core/gir1.2-atspi-2.0_2.4.1-0ubuntu0.1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/libu/libunity/gir1.2-unity-5.0_5.12.0-0ubuntu1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/g/glib-networking/glib-networking-services_2.32.1-1ubuntu1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/g/glib-networking/glib-networking_2.32.1-1ubuntu1_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/g/glib-networking/glib-networking-common_2.32.1-1ubuntu1_all.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/g/gnome-control-center/gnome-control-center-data_3.4.1-0ubuntu2_all.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/g/gnome-control-center/libgnome-control-center1_3.4.1-0ubuntu2_i386.deb Size mismatch
Failed to fetch http://ubuntu.cs.utah.edu/ubuntu/pool/main/g/gnome-control-center/gnome-control-center_3.4.1-0ubuntu2_i386.deb Size mismatch
E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing.

```

Suggestions?

TY

---

### Post by mörgæs on 2012-05-16
Have you read the last line of the output?

---

### Post by fisheater on 2012-05-16
Thanks again for your insight. I did try the commands on the last line, with no effect. I tried to update via terminal and via the GUI.

Here are the commands:

```

sudo apt-get update --fix-missing
(tried sudo apt-get upgrade --fix-missing)
apt-get --fix-missing 
sudo apt-get upgrade
```

Here are some screenshots - things seem to fail after a partial download. I have tried over wifi, different LAN cables and ports.

TY for your brain power!

FE

---

### Post by fisheater on 2012-05-18
Update: Unable to get 12.04 to update/upgrade despite all the suggestions, sudo, and reading.

Downgraded to 11.10, works. So the work around at the moment is to stay with 11.10.

Thanks for you help. Will check back in 6 months or so.

FE!

---

### Post by fisheater on 2012-05-21
Update 2:

I had another crack at this, it was an interesting problem to work out.

In short. Reinstalled fresh download of 12.04

1. Deactivated privoxy.
2. Set my laptop MAC as DMZ via my router.
3. Rebooted everything.
4. Updated without an issue.
- without all the steps, it would not work.

Hope that helps someone.

Keep up the good work ubuntu!

FE

---

### Post by mörgæs on 2012-05-21
Good, then please mark the thread 'solved'.

---

