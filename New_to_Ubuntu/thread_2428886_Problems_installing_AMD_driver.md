---
title: "Problems installing AMD driver"
date: 2019-10-10
forum: New to Ubuntu
---

### Post by chris0744 on 2019-10-10
Hey folks,

I'm trying to setup Ubunto bionic (18.04.3) on laptop thats a couple of years old. It's got an AMD Radeon HD8870M inside.
Prior to this, this laptop has been running win8.1 and then win10. 2 years ago the CPU got bricked because of issues with driver updates.
Ever since I have wondered if it is the hardware that broke, or if simply the driver was corrupt (I worked on it for weeks, computer was unusable. In the end I managed to simply permanently disable the GPU to allow the laptop to function, using intel integrated graphics).

So, now I'm trying to setup Ubunto, and I want to try to get the GPU working again, however, install has been far from smooth sailing. I've tried a few different tutorials, but I always appear to be missing some dependencies, with no clue which ones really or how to install them. I'm a linux noob, first time ever installing it now and setting it up, so please be patient with me haha.

Here is the output from my latest install attempt:
```
chris@chris-laptop:~$ sudo apt-get install fglrx fglrx-amdcccle[sudo] password for chris:     
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package fglrx
E: Unable to locate package fglrx-amdcccle
chris@chris-laptop:~$ sudo sh /usr/share/ati/fglrx-uninstall.sh
sh: 0: Can't open /usr/share/ati/fglrx-uninstall.sh
chris@chris-laptop:~$ sudo apt-get remove --purge fglrx fglrx-* fglrx-amdcccle* fglrx-dev*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'fglrx-pxpress' for glob 'fglrx-*'
Note, selecting 'fglrx-updates-core' for glob 'fglrx-*'
Note, selecting 'fglrx-glx' for glob 'fglrx-*'
Package 'fglrx-updates-core' is not installed, so not removed
Package 'fglrx-glx' is not installed, so not removed
E: Unable to locate package fglrx
E: Unable to locate package fglrx-amdcccle*
E: Couldn't find any package by glob 'fglrx-amdcccle*'
E: Couldn't find any package by regex 'fglrx-amdcccle*'
E: Unable to locate package fglrx-dev*
E: Couldn't find any package by glob 'fglrx-dev*'
E: Couldn't find any package by regex 'fglrx-dev*'
chris@chris-laptop:~$ sudo dpkg-reconfigure xserver-xorg
chris@chris-laptop:~$ sudo apt-get install build-essential cdbs dh-make dkms execstack dh-modaliases fakeroot libqtgui4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
execstack is already the newest version (0.0.20131005-1).
build-essential is already the newest version (12.4ubuntu1).
fakeroot is already the newest version (1.22-2ubuntu1).
fakeroot set to manually installed.
dh-modaliases is already the newest version (1:0.5.2.3).
The following packages were automatically installed and are no longer required:
  libavutil56 libsdl2-2.0-0:i386 libstb0 libwayland-client0:i386
  libwayland-cursor0:i386 libwayland-egl1:i386 libxkbcommon0:i386 wine-stable
  wine-stable-amd64 wine-stable-i386:i386
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  dh-translations intltool jq libfile-which-perl libjq1 libmng2
  libmysqlclient20 libonig4 libqt4-dbus libqt4-declarative libqt4-network
  libqt4-script libqt4-sql libqt4-sql-mysql libqt4-xml libqt4-xmlpatterns
  libqtcore4 libqtdbus4 mysql-common python3-scour qdbus qt-at-spi qtchooser
  qtcore4-l10n scour
Suggested packages:
  devscripts menu libqt4-declarative-folderlistmodel
  libqt4-declarative-gestures libqt4-declarative-particles
  libqt4-declarative-shaders qt4-qmlviewer libqt4-dev libicu55 qt4-qtconfig
The following NEW packages will be installed:
  cdbs dh-make dh-translations dkms intltool jq libfile-which-perl libjq1
  libmng2 libmysqlclient20 libonig4 libqt4-dbus libqt4-declarative
  libqt4-network libqt4-script libqt4-sql libqt4-sql-mysql libqt4-xml
  libqt4-xmlpatterns libqtcore4 libqtdbus4 libqtgui4 mysql-common
  python3-scour qdbus qt-at-spi qtchooser qtcore4-l10n scour
0 upgraded, 29 newly installed, 0 to remove and 4 not upgraded.
Need to get 11,9 MB of archives.
After this operation, 47,1 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu bionic/universe amd64 libmng2 amd64 2.0.2-0ubuntu3 [169 kB]
Get:2 http://security.ubuntu.com/ubuntu bionic-security/main amd64 libmysqlclient20 amd64 5.7.27-0ubuntu0.18.04.1 [816 kB]
Get:3 http://archive.ubuntu.com/ubuntu bionic/universe amd64 intltool all 0.51.0-5ubuntu1 [44,6 kB]
Get:4 http://archive.ubuntu.com/ubuntu bionic/universe amd64 libonig4 amd64 6.7.0-1 [119 kB]
Get:5 http://archive.ubuntu.com/ubuntu bionic/universe amd64 libjq1 amd64 1.5+dfsg-2 [111 kB]
Get:6 http://archive.ubuntu.com/ubuntu bionic/universe amd64 jq amd64 1.5+dfsg-2 [45,6 kB]
Get:7 http://archive.ubuntu.com/ubuntu bionic/main amd64 libfile-which-perl all 1.21-1 [11,8 kB]
Get:8 http://archive.ubuntu.com/ubuntu bionic-updates/universe amd64 dh-translations all 138.18.04.1 [24,6 kB]
Get:9 http://archive.ubuntu.com/ubuntu bionic/universe amd64 python3-scour all 0.36-2 [44,8 kB]
Get:10 http://archive.ubuntu.com/ubuntu bionic/universe amd64 scour all 0.36-2 [7372 B]
Get:11 http://archive.ubuntu.com/ubuntu bionic/universe amd64 cdbs all 0.4.156ubuntu4 [45,4 kB]
Get:12 http://archive.ubuntu.com/ubuntu bionic/main amd64 dh-make all 2.201701 [31,6 kB]
Get:13 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 dkms all 2.3-3ubuntu9.5 [68,1 kB]
Get:14 http://archive.ubuntu.com/ubuntu bionic/main amd64 mysql-common all 5.8+1.0.4 [7308 B]
Get:15 http://archive.ubuntu.com/ubuntu bionic/universe amd64 qtcore4-l10n all 4:4.8.7+dfsg-7ubuntu1 [617 kB]
Get:16 http://archive.ubuntu.com/ubuntu bionic/universe amd64 libqtcore4 amd64 4:4.8.7+dfsg-7ubuntu1 [1552 kB]
Get:17 http://archive.ubuntu.com/ubuntu bionic/universe amd64 libqt4-xml amd64 4:4.8.7+dfsg-7ubuntu1 [96,1 kB]
Get:18 http://archive.ubuntu.com/ubuntu bionic/universe amd64 libqtdbus4 amd64 4:4.8.7+dfsg-7ubuntu1 [186 kB]
Get:19 http://archive.ubuntu.com/ubuntu bionic/main amd64 qtchooser amd64 64-ga1b6736-5 [24,1 kB]
Get:20 http://archive.ubuntu.com/ubuntu bionic/universe amd64 qdbus amd64 4:4.8.7+dfsg-7ubuntu1 [30,0 kB]
Get:21 http://archive.ubuntu.com/ubuntu bionic/universe amd64 libqt4-dbus amd64 4:4.8.7+dfsg-7ubuntu1 [6440 B]
Get:22 http://archive.ubuntu.com/ubuntu bionic/universe amd64 libqt4-network amd64 4:4.8.7+dfsg-7ubuntu1 [562 kB]
Get:23 http://archive.ubuntu.com/ubuntu bionic/universe amd64 libqt4-script amd64 4:4.8.7+dfsg-7ubuntu1 [815 kB]
Get:24 http://archive.ubuntu.com/ubuntu bionic/universe amd64 libqt4-sql amd64 4:4.8.7+dfsg-7ubuntu1 [98,5 kB]
Get:25 http://archive.ubuntu.com/ubuntu bionic/universe amd64 libqt4-xmlpatterns amd64 4:4.8.7+dfsg-7ubuntu1 [1091 kB]
Get:26 http://archive.ubuntu.com/ubuntu bionic/universe amd64 libqtgui4 amd64 4:4.8.7+dfsg-7ubuntu1 [4115 kB]
Get:27 http://archive.ubuntu.com/ubuntu bionic/universe amd64 libqt4-declarative amd64 4:4.8.7+dfsg-7ubuntu1 [1089 kB]
Get:28 http://archive.ubuntu.com/ubuntu bionic/universe amd64 libqt4-sql-mysql amd64 4:4.8.7+dfsg-7ubuntu1 [30,5 kB]
Get:29 http://archive.ubuntu.com/ubuntu bionic/universe amd64 qt-at-spi amd64 0.4.0-8 [58,6 kB]
Fetched 11,9 MB in 3s (3632 kB/s)   
Selecting previously unselected package libmng2:amd64.
(Reading database ... 227754 files and directories currently installed.)
Preparing to unpack .../00-libmng2_2.0.2-0ubuntu3_amd64.deb ...
Unpacking libmng2:amd64 (2.0.2-0ubuntu3) ...
Selecting previously unselected package intltool.
Preparing to unpack .../01-intltool_0.51.0-5ubuntu1_all.deb ...
Unpacking intltool (0.51.0-5ubuntu1) ...
Selecting previously unselected package libonig4:amd64.
Preparing to unpack .../02-libonig4_6.7.0-1_amd64.deb ...
Unpacking libonig4:amd64 (6.7.0-1) ...
Selecting previously unselected package libjq1:amd64.
Preparing to unpack .../03-libjq1_1.5+dfsg-2_amd64.deb ...
Unpacking libjq1:amd64 (1.5+dfsg-2) ...
Selecting previously unselected package jq.
Preparing to unpack .../04-jq_1.5+dfsg-2_amd64.deb ...
Unpacking jq (1.5+dfsg-2) ...
Selecting previously unselected package libfile-which-perl.
Preparing to unpack .../05-libfile-which-perl_1.21-1_all.deb ...
Unpacking libfile-which-perl (1.21-1) ...
Selecting previously unselected package dh-translations.
Preparing to unpack .../06-dh-translations_138.18.04.1_all.deb ...
Unpacking dh-translations (138.18.04.1) ...
Selecting previously unselected package python3-scour.
Preparing to unpack .../07-python3-scour_0.36-2_all.deb ...
Unpacking python3-scour (0.36-2) ...
Selecting previously unselected package scour.
Preparing to unpack .../08-scour_0.36-2_all.deb ...
Unpacking scour (0.36-2) ...
Selecting previously unselected package cdbs.
Preparing to unpack .../09-cdbs_0.4.156ubuntu4_all.deb ...
Unpacking cdbs (0.4.156ubuntu4) ...
Selecting previously unselected package dh-make.
Preparing to unpack .../10-dh-make_2.201701_all.deb ...
Unpacking dh-make (2.201701) ...
Selecting previously unselected package dkms.
Preparing to unpack .../11-dkms_2.3-3ubuntu9.5_all.deb ...
Unpacking dkms (2.3-3ubuntu9.5) ...
Selecting previously unselected package mysql-common.
Preparing to unpack .../12-mysql-common_5.8+1.0.4_all.deb ...
Unpacking mysql-common (5.8+1.0.4) ...
Selecting previously unselected package libmysqlclient20:amd64.
Preparing to unpack .../13-libmysqlclient20_5.7.27-0ubuntu0.18.04.1_amd64.deb ...
Unpacking libmysqlclient20:amd64 (5.7.27-0ubuntu0.18.04.1) ...
Selecting previously unselected package qtcore4-l10n.
Preparing to unpack .../14-qtcore4-l10n_4%3a4.8.7+dfsg-7ubuntu1_all.deb ...
Unpacking qtcore4-l10n (4:4.8.7+dfsg-7ubuntu1) ...
Selecting previously unselected package libqtcore4:amd64.
Preparing to unpack .../15-libqtcore4_4%3a4.8.7+dfsg-7ubuntu1_amd64.deb ...
Unpacking libqtcore4:amd64 (4:4.8.7+dfsg-7ubuntu1) ...
Selecting previously unselected package libqt4-xml:amd64.
Preparing to unpack .../16-libqt4-xml_4%3a4.8.7+dfsg-7ubuntu1_amd64.deb ...
Unpacking libqt4-xml:amd64 (4:4.8.7+dfsg-7ubuntu1) ...
Selecting previously unselected package libqtdbus4:amd64.
Preparing to unpack .../17-libqtdbus4_4%3a4.8.7+dfsg-7ubuntu1_amd64.deb ...
Unpacking libqtdbus4:amd64 (4:4.8.7+dfsg-7ubuntu1) ...
Selecting previously unselected package qtchooser.
Preparing to unpack .../18-qtchooser_64-ga1b6736-5_amd64.deb ...
Unpacking qtchooser (64-ga1b6736-5) ...
Selecting previously unselected package qdbus.
Preparing to unpack .../19-qdbus_4%3a4.8.7+dfsg-7ubuntu1_amd64.deb ...
Unpacking qdbus (4:4.8.7+dfsg-7ubuntu1) ...
Selecting previously unselected package libqt4-dbus:amd64.
Preparing to unpack .../20-libqt4-dbus_4%3a4.8.7+dfsg-7ubuntu1_amd64.deb ...
Unpacking libqt4-dbus:amd64 (4:4.8.7+dfsg-7ubuntu1) ...
Selecting previously unselected package libqt4-network:amd64.
Preparing to unpack .../21-libqt4-network_4%3a4.8.7+dfsg-7ubuntu1_amd64.deb ...
Unpacking libqt4-network:amd64 (4:4.8.7+dfsg-7ubuntu1) ...
Selecting previously unselected package libqt4-script:amd64.
Preparing to unpack .../22-libqt4-script_4%3a4.8.7+dfsg-7ubuntu1_amd64.deb ...
Unpacking libqt4-script:amd64 (4:4.8.7+dfsg-7ubuntu1) ...
Selecting previously unselected package libqt4-sql:amd64.
Preparing to unpack .../23-libqt4-sql_4%3a4.8.7+dfsg-7ubuntu1_amd64.deb ...
Unpacking libqt4-sql:amd64 (4:4.8.7+dfsg-7ubuntu1) ...
Selecting previously unselected package libqt4-xmlpatterns:amd64.
Preparing to unpack .../24-libqt4-xmlpatterns_4%3a4.8.7+dfsg-7ubuntu1_amd64.deb ...
Unpacking libqt4-xmlpatterns:amd64 (4:4.8.7+dfsg-7ubuntu1) ...
Selecting previously unselected package libqtgui4:amd64.
Preparing to unpack .../25-libqtgui4_4%3a4.8.7+dfsg-7ubuntu1_amd64.deb ...
Unpacking libqtgui4:amd64 (4:4.8.7+dfsg-7ubuntu1) ...
Selecting previously unselected package libqt4-declarative:amd64.
Preparing to unpack .../26-libqt4-declarative_4%3a4.8.7+dfsg-7ubuntu1_amd64.deb ...
Unpacking libqt4-declarative:amd64 (4:4.8.7+dfsg-7ubuntu1) ...
Selecting previously unselected package libqt4-sql-mysql:amd64.
Preparing to unpack .../27-libqt4-sql-mysql_4%3a4.8.7+dfsg-7ubuntu1_amd64.deb ...
Unpacking libqt4-sql-mysql:amd64 (4:4.8.7+dfsg-7ubuntu1) ...
Selecting previously unselected package qt-at-spi:amd64.
Preparing to unpack .../28-qt-at-spi_0.4.0-8_amd64.deb ...
Unpacking qt-at-spi:amd64 (0.4.0-8) ...
Setting up libfile-which-perl (1.21-1) ...
Setting up intltool (0.51.0-5ubuntu1) ...
Setting up qtcore4-l10n (4:4.8.7+dfsg-7ubuntu1) ...
Setting up mysql-common (5.8+1.0.4) ...
update-alternatives: using /etc/mysql/my.cnf.fallback to provide /etc/mysql/my.cnf (my.cnf) in auto mode
Setting up libonig4:amd64 (6.7.0-1) ...
Setting up qtchooser (64-ga1b6736-5) ...
Setting up python3-scour (0.36-2) ...
Setting up scour (0.36-2) ...
Setting up libmng2:amd64 (2.0.2-0ubuntu3) ...
Setting up libjq1:amd64 (1.5+dfsg-2) ...
Setting up dh-make (2.201701) ...
Setting up dkms (2.3-3ubuntu9.5) ...
Setting up libqtcore4:amd64 (4:4.8.7+dfsg-7ubuntu1) ...
Setting up libmysqlclient20:amd64 (5.7.27-0ubuntu0.18.04.1) ...
Setting up libqt4-xml:amd64 (4:4.8.7+dfsg-7ubuntu1) ...
Setting up jq (1.5+dfsg-2) ...
Setting up dh-translations (138.18.04.1) ...
Setting up libqt4-sql:amd64 (4:4.8.7+dfsg-7ubuntu1) ...
Setting up libqtdbus4:amd64 (4:4.8.7+dfsg-7ubuntu1) ...
Setting up cdbs (0.4.156ubuntu4) ...
Setting up libqt4-script:amd64 (4:4.8.7+dfsg-7ubuntu1) ...
Setting up libqt4-sql-mysql:amd64 (4:4.8.7+dfsg-7ubuntu1) ...
Setting up qdbus (4:4.8.7+dfsg-7ubuntu1) ...
Setting up libqt4-dbus:amd64 (4:4.8.7+dfsg-7ubuntu1) ...
Setting up libqt4-network:amd64 (4:4.8.7+dfsg-7ubuntu1) ...
Setting up libqt4-xmlpatterns:amd64 (4:4.8.7+dfsg-7ubuntu1) ...
Setting up libqt4-declarative:amd64 (4:4.8.7+dfsg-7ubuntu1) ...
Setting up libqtgui4:amd64 (4:4.8.7+dfsg-7ubuntu1) ...
Setting up qt-at-spi:amd64 (0.4.0-8) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
chris@chris-laptop:~$ sudo apt-get install lib32gcc1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libavutil56 libsdl2-2.0-0:i386 libstb0 libwayland-client0:i386
  libwayland-cursor0:i386 libwayland-egl1:i386 libxkbcommon0:i386 wine-stable
  wine-stable-amd64 wine-stable-i386:i386
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libc6-i386
The following NEW packages will be installed:
  lib32gcc1 libc6-i386
0 upgraded, 2 newly installed, 0 to remove and 4 not upgraded.
Need to get 2699 kB of archives.
After this operation, 12,6 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu bionic/main amd64 libc6-i386 amd64 2.27-3ubuntu1 [2651 kB]
Get:2 http://security.ubuntu.com/ubuntu bionic-security/main amd64 lib32gcc1 amd64 1:8.3.0-6ubuntu1~18.04.1 [47,9 kB]
Fetched 2699 kB in 0s (5719 kB/s)                                              
Selecting previously unselected package libc6-i386.
(Reading database ... 228214 files and directories currently installed.)
Preparing to unpack .../libc6-i386_2.27-3ubuntu1_amd64.deb ...
Unpacking libc6-i386 (2.27-3ubuntu1) ...
Replaced by files in installed package libc6:i386 (2.27-3ubuntu1) ...
Selecting previously unselected package lib32gcc1.
Preparing to unpack .../lib32gcc1_1%3a8.3.0-6ubuntu1~18.04.1_amd64.deb ...
Unpacking lib32gcc1 (1:8.3.0-6ubuntu1~18.04.1) ...
Setting up libc6-i386 (2.27-3ubuntu1) ...
Setting up lib32gcc1 (1:8.3.0-6ubuntu1~18.04.1) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
chris@chris-laptop:~$ wget --referer='http://support.amd.com/en-us/download/desktop?os=Linux+x86' http://www2.ati.com/drivers/linux/amd-catalyst-13.12-linux-x86.x86_64.zip
--2019-10-10 20:02:07--  http://www2.ati.com/drivers/linux/amd-catalyst-13.12-linux-x86.x86_64.zip
Resolving www2.ati.com (www2.ati.com)... 92.122.253.115
Connecting to www2.ati.com (www2.ati.com)|92.122.253.115|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://drivers.amd.com/drivers/linux/amd-catalyst-13.12-linux-x86.x86_64.zip [following]
--2019-10-10 20:02:07--  http://drivers.amd.com/drivers/linux/amd-catalyst-13.12-linux-x86.x86_64.zip
Resolving drivers.amd.com (drivers.amd.com)... 92.122.253.115
Reusing existing connection to www2.ati.com:80.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: https://drivers.amd.com/drivers/linux/amd-catalyst-13.12-linux-x86.x86_64.zip [following]
--2019-10-10 20:02:07--  https://drivers.amd.com/drivers/linux/amd-catalyst-13.12-linux-x86.x86_64.zip
Connecting to drivers.amd.com (drivers.amd.com)|92.122.253.115|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 160580195 (153M) [application/zip]
Saving to: ‘amd-catalyst-13.12-linux-x86.x86_64.zip’


amd-catalyst-13.12- 100%[===================>] 153,14M  2,29MB/s    in 73s     


2019-10-10 20:03:21 (2,09 MB/s) - ‘amd-catalyst-13.12-linux-x86.x86_64.zip’ saved [160580195/160580195]


chris@chris-laptop:~$ unzip amd-catalyst-13.12-linux-x86.x86_64.zipwget --referer='http://support.amd.com/en-us/download/desktop?os=Linux+x86' http://www2.ati.com/drivers/linux/amd-catalyst-13.12-linux-x86.x86_64.zip
unzip:  cannot find or open amd-catalyst-13.12-linux-x86.x86_64.zipwget, amd-catalyst-13.12-linux-x86.x86_64.zipwget.zip or amd-catalyst-13.12-linux-x86.x86_64.zipwget.ZIP.
chris@chris-laptop:~$ sudo sh amd-driver-installer-14.20-x86.x86_64.run --buildpkg Ubuntu/precise
sh: 0: Can't open amd-driver-installer-14.20-x86.x86_64.run
chris@chris-laptop:~$ wget --referer='http://support.amd.com/en-us/download/desktop?os=Linux+x86' http://www2.ati.com/drivers/linux/amd-catalyst-13.12-linux-x86.x86_64.zip
--2019-10-10 20:04:37--  http://www2.ati.com/drivers/linux/amd-catalyst-13.12-linux-x86.x86_64.zip
Resolving www2.ati.com (www2.ati.com)... 92.122.253.115
Connecting to www2.ati.com (www2.ati.com)|92.122.253.115|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://drivers.amd.com/drivers/linux/amd-catalyst-13.12-linux-x86.x86_64.zip [following]
--2019-10-10 20:04:37--  http://drivers.amd.com/drivers/linux/amd-catalyst-13.12-linux-x86.x86_64.zip
Resolving drivers.amd.com (drivers.amd.com)... 92.122.253.115
Reusing existing connection to www2.ati.com:80.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: https://drivers.amd.com/drivers/linux/amd-catalyst-13.12-linux-x86.x86_64.zip [following]
--2019-10-10 20:04:37--  https://drivers.amd.com/drivers/linux/amd-catalyst-13.12-linux-x86.x86_64.zip
Connecting to drivers.amd.com (drivers.amd.com)|92.122.253.115|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 160580195 (153M) [application/zip]
Saving to: ‘amd-catalyst-13.12-linux-x86.x86_64.zip.1’


amd-catalyst-13.12- 100%[===================>] 153,14M  5,40MB/s    in 28s     


2019-10-10 20:05:05 (5,51 MB/s) - ‘amd-catalyst-13.12-linux-x86.x86_64.zip.1’ saved [160580195/160580195]


chris@chris-laptop:~$ unzip amd-catalyst-13.12-linux-x86.x86_64.zip
Archive:  amd-catalyst-13.12-linux-x86.x86_64.zip
  inflating: amd-catalyst-13.12-linux-x86.x86_64.run  
chris@chris-laptop:~$ sudo sh amd-driver-installer-14.20-x86.x86_64.run --buildpkg Ubuntu/precise
sh: 0: Can't open amd-driver-installer-14.20-x86.x86_64.run
chris@chris-laptop:~$ sudo dpkg -i fglrx*.deb
dpkg: error: cannot access archive 'fglrx*.deb': No such file or directory
chris@chris-laptop:~$ sudo sh amd-driver-installer-14.20-x86.x86_64.run --buildpkg Ubuntu/bionic
sh: 0: Can't open amd-driver-installer-14.20-x86.x86_64.run
chris@chris-laptop:~$ sudo sh amd-catalyst-13.12-linux-x86.x86_64.run --buildpkg Ubuntu/bionic
Created directory fglrx-install.bKR0Og
Verifying archive integrity... All good.
Uncompressing AMD Catalyst(TM) Proprietary Driver-13.251...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
=====================================================================
 AMD Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================
Generating package: Ubuntu/bionic
mv: cannot stat 'dpkg-deb:': No such file or directory
Package /home/chris/dpkg-deb: has been successfully generated
mv: cannot stat 'building': No such file or directory
Package /home/chris/building has been successfully generated
mv: cannot stat 'package': No such file or directory
Package /home/chris/package has been successfully generated
mv: cannot stat "'fglrx'": No such file or directory
Package /home/chris/'fglrx' has been successfully generated
mv: cannot stat 'in': No such file or directory
Package /home/chris/in has been successfully generated
mv: cannot stat "'../fglrx_13.251-0ubuntu1_amd64.deb'.": No such file or directory
Package /home/chris/fglrx_13.251-0ubuntu1_amd64.deb'. has been successfully generated
mv: cannot stat 'dpkg-deb:': No such file or directory
Package /home/chris/dpkg-deb: has been successfully generated
mv: cannot stat 'building': No such file or directory
Package /home/chris/building has been successfully generated
mv: cannot stat 'package': No such file or directory
Package /home/chris/package has been successfully generated
mv: cannot stat "'fglrx-dev'": No such file or directory
Package /home/chris/'fglrx-dev' has been successfully generated
mv: cannot stat 'in': No such file or directory
Package /home/chris/in has been successfully generated
mv: cannot stat "'../fglrx-dev_13.251-0ubuntu1_amd64.deb'.": No such file or directory
Package /home/chris/fglrx-dev_13.251-0ubuntu1_amd64.deb'. has been successfully generated
mv: cannot stat 'dpkg-deb:': No such file or directory
Package /home/chris/dpkg-deb: has been successfully generated
mv: cannot stat 'building': No such file or directory
Package /home/chris/building has been successfully generated
mv: cannot stat 'package': No such file or directory
Package /home/chris/package has been successfully generated
mv: cannot stat "'fglrx-amdcccle'": No such file or directory
Package /home/chris/'fglrx-amdcccle' has been successfully generated
mv: cannot stat 'in': No such file or directory
Package /home/chris/in has been successfully generated
mv: cannot stat "'../fglrx-amdcccle_13.251-0ubuntu1_amd64.deb'.": No such file or directory
Package /home/chris/fglrx-amdcccle_13.251-0ubuntu1_amd64.deb'. has been successfully generated
Removing temporary directory: fglrx-install.bKR0Og
chris@chris-laptop:~$ sudo dpkg -i fglrx*.deb
dpkg: error: cannot access archive 'fglrx*.deb': No such file or directory
chris@chris-laptop:~$ sudo dpkg -i fglrx*.deb
dpkg: error: cannot access archive 'fglrx*.deb': No such file or directory
chris@chris-laptop:~$ sudo dpkg -i fglrx-amdcccle_13.251-0buntu1_amd64.deb
dpkg: error: cannot access archive 'fglrx-amdcccle_13.251-0buntu1_amd64.deb': No such file or directory
chris@chris-laptop:~$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.orig
cp: cannot stat '/etc/X11/xorg.conf': No such file or directory
chris@chris-laptop:~$ ./amd-driver-installer-15-12-x86/x86_64.run
bash: ./amd-driver-installer-15-12-x86/x86_64.run: No such file or directory
chris@chris-laptop:~$ 



```

I've just tried following this tutorial: [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Removing_Catalyst.2Ffglrx) but I ended up getting the results stated above (I also first went through the section on how to remove files from previous attempts, in that same guide).

Any help would be very much appreciated! It'd mean a lot to me to get the gpu running again after a few years of getting headaches trying to fix it in windows. 

Cheers,

---

### Post by QIII on 2019-10-10
fglrx is long dead.  You won't be able to install it.

Currently, the open source Radeon drive or the open source AMDGPU driver is automatically installed (depending on whether the hardware is supported) when Ubuntu is installed.  This may, however, be subverted in hybrid systems like yours.

From your BIOS/EFI, are you able to set the preferred GPU to dedicated?

---

### Post by ajgreeny on 2019-10-10
I'm sorry but the fglrx driver has been deprecated in Ubuntu 18.04 so you may have to make do with the open source radeon drivers.

Some cards use the AMDGPU driver but not, I suspect the HD8870M that you have.

See [https://ubuntuforums.org/showthread.php?t=2418832](https://ubuntuforums.org/showthread.php?t=2418832) for more possibly helpful info.

[COLOR="#FF0000"]EDIT:[/COLOR]
Beaten to it by QIII.

---

### Post by oldrocker99 on 2019-10-11
For a couple of years, people have been saying that the open source Radeon drivers are superior to the old fglrx drivers. 

This is no great surprise. ATI, to their great credit, has worked closely with developers, including providing complete chip information, and the radeon drivers, like the open-source Intel drivers, are the best drivers. Only nVidia's proprietary drivers are superior to the open-source Nouveau drivers.

---

### Post by twily2018 on 2019-10-18
Just use the drivers that comes with ubuntu. It's likely you don't even need to install a driver as it already comes with Ubuntu.

---

### Post by mikewhatever on 2019-10-18
> **oldrocker99 said:**
> For a couple of years, people have been saying that the open source Radeon drivers are superior to the old fglrx drivers. 

This is no great surprise. ATI, to their great credit, has worked closely with developers, including providing complete chip information, and the radeon drivers, like the open-source Intel drivers, are the best drivers. Only nVidia's proprietary drivers are superior to the open-source Nouveau drivers.

IMHO, this is not the case. Radeon is not superior to fglrx.
The radeon driver still lacks support for OpenGL 4.2 for cards like Radeon 5xxx from 2012, and in 2019, it is safe to assume, it is unlikely to ever catch up. Radeon is also not particularly great with adaptive power management on notebooks, and lacks similar to fglrx's config utility. The radeon driver is stable enough to use, because there no other option, but it is in no way superior.

---

