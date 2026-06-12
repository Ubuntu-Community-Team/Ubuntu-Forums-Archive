---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2012-07-21
forum: New to Ubuntu
---

### Post by amin021023 on 2012-07-21
I just wanted to install prozgui
[COLOR=Red]
encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/COLOR]

I Always suffer this error and like that

plz help me sorry if I posted wrong place

---

### Post by jmfal on 2012-07-21
Welcome to Ubuntu
I was going to type all this but its easier this way, 
Open a terminal and copy/paste this,  and press enter
```
 
sudo rm /var/lib/dpkg/info/oracle-java7-installer* sudo apt-get purge oracle-java7-installer* sudo rm /etc/apt/sources.list.d/*java* sudo apt-get update sudo add-apt-repository ppa:webupd8team/java sudo apt-get update sudo apt-get install oracle-java7-installer
```
There's alot there make sure you copy it all.

---

### Post by jmfal on 2012-07-21
I'm not sure if it copy/pasted right so here is link

[http://ubuntuforums.org/showthread.php?t=1977483](http://ubuntuforums.org/showthread.php?t=1977483)

command is in post #2

---

### Post by amin021023 on 2012-07-22
thanks for answering but still no luck with that

when I do this:  sudo rm /var/lib/dpkg/info/oracle-java7-installer

It sayes [COLOR=Red]no such file or directory[/COLOR]

what should i do?can i remove all java ect then reinstall all sweat?

---

### Post by NikTh on 2012-07-22
Hi , 
please , clarify something , is this problem related to java , or its always present , no matter what program try to install ? 

Try to install something (even java) and give the full output of terminal . 
**Put the results inside [CODE] tags , by highlighting the text and click # symbol at top of message pane.**

Thanks

---

### Post by amin021023 on 2012-07-22
this error happens always , install a program , ect...

such as installing prozgui:


```
amin@Amin-Aspire:~$ sudo apt-get install prozgui
[sudo] password for amin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  prozgui
0 upgraded, 1 newly installed, 0 to remove and 12 not upgraded.
1 not fully installed or removed.
Need to get 0 B/226 kB of archives.
After this operation, 666 kB of additional disk space will be used.
Selecting previously unselected package prozgui.
(Reading database ... 176584 files and directories currently installed.)
Unpacking prozgui (from .../prozgui_2.0.7-1ubuntu1~34~precise1_i386.deb) ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Setting up oracle-java7-installer (7u3-0~eugenesan~precise4) ...
Downloading...
--2012-07-22 15:17:44--  http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz
Resolving download.oracle.com (download.oracle.com)... 213.155.154.89, 213.155.154.112
Connecting to download.oracle.com (download.oracle.com)|213.155.154.89|:80... connected.
HTTP request sent, awaiting response... 403 Forbidden
2012-07-22 15:17:47 ERROR 403: Forbidden.

download failed
[COLOR=Red]Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up prozgui (2.0.7-1ubuntu1~34~precise1) ...
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]
amin@Amin-Aspire:~$ 

```I Think I should complete installing java or remove it all...the qustion is how?as I said I tried to reinstall java7 (following post2) but no luck....

---

### Post by amin021023 on 2012-07-22
guys i really need this to be solved so please

---

### Post by Toz on 2012-07-22
It looks like at some point you tried to install oracle-java7-installer and it didn't complete. Now every time you try to install something, it tries to complete the java 7 installation and fails.

Try removing java 7:
```
sudo apt-get remove oracle-java7-installer
```

---

### Post by amin021023 on 2012-07-22
> **Toz said:**
> It looks like at some point you tried to install oracle-java7-installer and it didn't complete. Now every time you try to install something, it tries to complete the java 7 installation and fails.

Yes I think so

Try removing java 7:
```
sudo apt-get remove oracle-java7-installer
```[/QUOTE]

I did it but again the error appeared! :

```
amin@Amin-Aspire:~$ sudo apt-get remove oracle-java7-installer
[sudo] password for amin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  oracle-java7-installer
0 upgraded, 0 newly installed, 1 to remove and 11 not upgraded.
1 not fully installed or removed.
After this operation, 82.9 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 176599 files and directories currently installed.)
Removing oracle-java7-installer ...
update-alternatives: error: unknown argument `cdrom'
dpkg: error processing oracle-java7-installer (--remove):
 subprocess installed pre-removal script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Downloading...
--2012-07-22 17:54:46--  http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz
Resolving download.oracle.com (download.oracle.com)... 208.47.254.41, 208.47.254.43
Connecting to download.oracle.com (download.oracle.com)|208.47.254.41|:80... connected.
HTTP request sent, awaiting response... 403 Forbidden
2012-07-22 17:54:59 ERROR 403: Forbidden.

download failed
[COLOR=Red]Oracle JDK 7 is NOT installed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]
amin@Amin-Aspire:~$ 

```

sounds this error is not getting of me:confused:

---

### Post by Toz on 2012-07-22
Here is one way to try to fix this:

```
gksudo gedit /var/lib/dpkg/info/oracle-java7-installer.postinst
```
...and towards the beginning of the file after the line:
> set -e
...add:
```
exit 0
```
...so it looks like this:
```

# Not fully internationalized, including japanese man pages

set -e
[COLOR="Red"]exit 0[/COLOR]
VER='0.6alpha'

case $(uname -m) in
```

Save the file and again run:
```
sudo dpkg --configure -a 
sudo apt-get remove oracle-java7-installer
sudo apt-get autoclean
```

---

### Post by NikTh on 2012-07-22
Hi , 
[SIZE=3]**and IF**[/SIZE] the above solution not work , open a terminal and **Please Copy-paste** these commands (for more accuracy) to your terminal . (One at time . One line = One command)
```
sudo apt-get purge $(dpkg -l | awk '/^rc/ { print $2 }')
sudo apt-get clean && sudo apt-get autoclean
sudo dpkg --configure -a 
sudo apt-get install -f
```Give the results back here. 

Thanks

---

### Post by amin021023 on 2012-07-22
YEAHHHH!!!!! Finaly it worked now all is fine...thank you guys! kiss... kiss... kiss

---

### Post by NikTh on 2012-07-22
> **amin021023 said:**
> YEAHHHH!!!!! Finaly it worked now all is fine...thank you guys! kiss... kiss... kiss

Hi ,
Glad it worked. 

You can mark **thread as solved** , from **thread tools**. 

Thanks

---

### Post by amin021023 on 2012-07-29
ohhh guys! the error is still stands...I was thinking it got fixed but....I did all you told me...please help me guys!

```
[SIZE=1]amin@Amin-Aspire:~$ sudo apt-get install git-core gnupg flex bison gperf build-essential \
>   zip curl libc6-dev libncurses5-dev:i386 x11proto-core-dev \
>   libx11-dev:i386 libreadline6-dev:i386 libgl1-mesa-glx:i386 \
>   libgl1-mesa-dev g++-multilib mingw32 openjdk-6-jdk tofrodos \
>   python-markdown libxml2-utils xsltproc zlib1g-dev:i386
[sudo] password for amin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
git-core is already the newest version.
gnupg is already the newest version.
libc6-dev is already the newest version.
zip is already the newest version.
libgl1-mesa-glx is already the newest version.
The following extra packages will be installed:
  dpkg-dev fakeroot g++ g++-4.6 g++-4.6-multilib gcc-4.6-multilib gcc-multilib
  lib64gcc1 lib64gomp1 lib64quadmath0 lib64stdc++6 libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libbison-dev libc6-amd64
  libc6-dev-amd64 libdpkg-perl libdrm-dev libfl-dev libice-dev libkms1
  libpthread-stubs0 libpthread-stubs0-dev libsm-dev libstdc++6-4.6-dev
  libtimedate-perl libtinfo-dev libx11-doc libxau-dev libxcb1-dev libxdmcp-dev
  libxext-dev libxt-dev m4 mesa-common-dev mingw32-binutils mingw32-runtime
  x11proto-input-dev x11proto-kb-dev x11proto-xext-dev xorg-sgml-doctools
  xtrans-dev
Suggested packages:
  bison-doc debian-keyring gcc-4.6-doc libstdc++6-4.6-dbg lib64stdc++6-4.6-dbg
  lib64mudflap0 ncurses-doc libstdc++6-4.6-doc libxcb-doc gcc-doc cpp-doc
  openjdk-6-demo openjdk-6-source visualvm
The following NEW packages will be installed:
  bison build-essential curl dpkg-dev fakeroot flex g++ g++-4.6
  g++-4.6-multilib g++-multilib gcc-4.6-multilib gcc-multilib gperf lib64gcc1
  lib64gomp1 lib64quadmath0 lib64stdc++6 libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libbison-dev libc6-amd64
  libc6-dev-amd64 libdpkg-perl libdrm-dev libfl-dev libgl1-mesa-dev libice-dev
  libkms1 libncurses5-dev libpthread-stubs0 libpthread-stubs0-dev
  libreadline6-dev libsm-dev libstdc++6-4.6-dev libtimedate-perl libtinfo-dev
  libx11-dev libx11-doc libxau-dev libxcb1-dev libxdmcp-dev libxext-dev
  libxml2-utils libxt-dev m4 mesa-common-dev mingw32 mingw32-binutils
  mingw32-runtime openjdk-6-jdk python-markdown tofrodos x11proto-core-dev
  x11proto-input-dev x11proto-kb-dev x11proto-xext-dev xorg-sgml-doctools
  xsltproc xtrans-dev zlib1g-dev
0 upgraded, 61 newly installed, 0 to remove and 54 not upgraded.
1 not fully installed or removed.
Need to get 57.6 MB/73.4 MB of archives.
After this operation, 268 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://ir.archive.ubuntu.com/ubuntu/ precise/main m4 i386 1.4.16-2ubuntu1 [195 kB]
Get:2 http://ir.archive.ubuntu.com/ubuntu/ precise/main libfl-dev i386 2.5.35-10ubuntu3 [19.2 kB]
Get:3 http://ir.archive.ubuntu.com/ubuntu/ precise/main flex i386 2.5.35-10ubuntu3 [216 kB]
Get:4 http://ir.archive.ubuntu.com/ubuntu/ precise/main libc6-amd64 i386 2.15-0ubuntu10 [4,470 kB]
Get:5 http://ir.archive.ubuntu.com/ubuntu/ precise/main libc6-dev-amd64 i386 2.15-0ubuntu10 [2,470 kB]
Get:6 http://ir.archive.ubuntu.com/ubuntu/ precise/main lib64gcc1 i386 1:4.6.3-1ubuntu5 [42.4 kB]
Get:7 http://ir.archive.ubuntu.com/ubuntu/ precise/main lib64gomp1 i386 4.6.3-1ubuntu5 [25.3 kB]
Get:8 http://ir.archive.ubuntu.com/ubuntu/ precise/main lib64quadmath0 i386 4.6.3-1ubuntu5 [126 kB]
Get:9 http://ir.archive.ubuntu.com/ubuntu/ precise/main gcc-4.6-multilib i386 4.6.3-1ubuntu5 [2,357 kB]
Get:10 http://ir.archive.ubuntu.com/ubuntu/ precise/main gcc-multilib i386 4:4.6.3-1ubuntu5 [1,150 B]
Get:11 http://ir.archive.ubuntu.com/ubuntu/ precise/main libkms1 i386 2.4.32-1ubuntu1 [9,692 B]
Get:12 http://ir.archive.ubuntu.com/ubuntu/ precise/main libbison-dev i386 1:2.5.dfsg-2.1 [33.2 kB]
Get:13 http://ir.archive.ubuntu.com/ubuntu/ precise/main bison i386 1:2.5.dfsg-2.1 [275 kB]
Get:14 http://ir.archive.ubuntu.com/ubuntu/ precise/main libstdc++6-4.6-dev i386 4.6.3-1ubuntu5 [1,643 kB]
Get:15 http://ir.archive.ubuntu.com/ubuntu/ precise/main g++-4.6 i386 4.6.3-1ubuntu5 [6,745 kB]
Get:16 http://ir.archive.ubuntu.com/ubuntu/ precise/main g++ i386 4:4.6.3-1ubuntu5 [1,444 B]
Get:17 http://ir.archive.ubuntu.com/ubuntu/ precise/main libtimedate-perl all 1.2000-1 [41.6 kB]
Get:18 http://ir.archive.ubuntu.com/ubuntu/ precise/main libdpkg-perl all 1.16.1.2ubuntu7 [181 kB]
Get:19 http://ir.archive.ubuntu.com/ubuntu/ precise/main dpkg-dev all 1.16.1.2ubuntu7 [468 kB]
Get:20 http://ir.archive.ubuntu.com/ubuntu/ precise/main build-essential i386 11.5ubuntu2 [5,974 B]
Get:21 http://ir.archive.ubuntu.com/ubuntu/ precise/main curl i386 7.22.0-3ubuntu4 [137 kB]
Get:22 http://ir.archive.ubuntu.com/ubuntu/ precise/main fakeroot i386 1.18.2-1 [87.9 kB]
Get:23 http://ir.archive.ubuntu.com/ubuntu/ precise/main lib64stdc++6 i386 4.6.3-1ubuntu5 [320 kB]
Get:24 http://ir.archive.ubuntu.com/ubuntu/ precise/main g++-4.6-multilib i386 4.6.3-1ubuntu5 [1,041 kB]
Get:25 http://ir.archive.ubuntu.com/ubuntu/ precise/main g++-multilib i386 4:4.6.3-1ubuntu5 [874 B]
Get:26 http://ir.archive.ubuntu.com/ubuntu/ precise/main gperf i386 3.0.3-1ubuntu1 [94.8 kB]
Get:27 http://ir.archive.ubuntu.com/ubuntu/ precise/main libalgorithm-diff-perl all 1.19.02-2 [50.7 kB]
Get:28 http://ir.archive.ubuntu.com/ubuntu/ precise/main libalgorithm-diff-xs-perl i386 0.04-2build2 [12.9 kB]
Get:29 http://ir.archive.ubuntu.com/ubuntu/ precise/main libalgorithm-merge-perl all 0.08-2 [12.7 kB]
Get:30 http://ir.archive.ubuntu.com/ubuntu/ precise/main libdrm-dev i386 2.4.32-1ubuntu1 [178 kB]
Get:31 http://ir.archive.ubuntu.com/ubuntu/ precise/main libtinfo-dev i386 5.9-4 [93.5 kB]
Get:32 http://ir.archive.ubuntu.com/ubuntu/ precise/main libncurses5-dev i386 5.9-4 [218 kB]
Get:33 http://ir.archive.ubuntu.com/ubuntu/ precise/main libreadline6-dev i386 6.2-8 [249 kB]
Get:34 http://ir.archive.ubuntu.com/ubuntu/ precise/main x11proto-xext-dev all 7.2.0-3 [253 kB]
Get:35 http://ir.archive.ubuntu.com/ubuntu/ precise/main libxext-dev i386 2:1.3.0-3build1 [150 kB]
Get:36 http://ir.archive.ubuntu.com/ubuntu/ precise-updates/main libxml2-utils i386 2.7.8.dfsg-5.1ubuntu4.1 [38.0 kB]
Get:37 http://ir.archive.ubuntu.com/ubuntu/ precise-updates/main mesa-common-dev i386 8.0.2-0ubuntu3.1 [242 kB]
Get:38 http://ir.archive.ubuntu.com/ubuntu/ precise/universe mingw32-binutils i386 2.20-0.2 [12.0 MB]
Get:39 http://ir.archive.ubuntu.com/ubuntu/ precise/universe mingw32-runtime all 3.15.2-0ubuntu1 [2,084 kB]
Get:40 http://ir.archive.ubuntu.com/ubuntu/ precise/universe mingw32 i386 4.2.1.dfsg-2ubuntu1 [20.7 MB]
Get:41 http://ir.archive.ubuntu.com/ubuntu/ precise/universe python-markdown all 2.1.1-1 [56.1 kB]
Get:42 http://ir.archive.ubuntu.com/ubuntu/ precise/main tofrodos i386 1.7.9.debian.1-1 [20.8 kB]
Get:43 http://ir.archive.ubuntu.com/ubuntu/ precise/main xsltproc i386 1.1.26-8ubuntu1 [14.4 kB]
Get:44 http://ir.archive.ubuntu.com/ubuntu/ precise/main zlib1g-dev i386 1:1.2.3.4.dfsg-3ubuntu4 [162 kB]
Get:45 http://ir.archive.ubuntu.com/ubuntu/ precise-updates/main libgl1-mesa-dev i386 8.0.2-0ubuntu3.1 [5,000 B]
Fetched 57.6 MB in 20min 19s (47.2 kB/s)                                       
Extracting templates from packages: 100%
Selecting previously unselected package m4.
(Reading database ... 176670 files and directories currently installed.)
Unpacking m4 (from .../m4_1.4.16-2ubuntu1_i386.deb) ...
Selecting previously unselected package libfl-dev.
Unpacking libfl-dev (from .../libfl-dev_2.5.35-10ubuntu3_i386.deb) ...
Selecting previously unselected package flex.
Unpacking flex (from .../flex_2.5.35-10ubuntu3_i386.deb) ...
Selecting previously unselected package libc6-amd64.
Unpacking libc6-amd64 (from .../libc6-amd64_2.15-0ubuntu10_i386.deb) ...
Selecting previously unselected package libc6-dev-amd64.
Unpacking libc6-dev-amd64 (from .../libc6-dev-amd64_2.15-0ubuntu10_i386.deb) ...
Selecting previously unselected package lib64gcc1.
Unpacking lib64gcc1 (from .../lib64gcc1_1%3a4.6.3-1ubuntu5_i386.deb) ...
Selecting previously unselected package lib64gomp1.
Unpacking lib64gomp1 (from .../lib64gomp1_4.6.3-1ubuntu5_i386.deb) ...
Selecting previously unselected package lib64quadmath0.
Unpacking lib64quadmath0 (from .../lib64quadmath0_4.6.3-1ubuntu5_i386.deb) ...
Selecting previously unselected package gcc-4.6-multilib.
Unpacking gcc-4.6-multilib (from .../gcc-4.6-multilib_4.6.3-1ubuntu5_i386.deb) ...
Selecting previously unselected package gcc-multilib.
Unpacking gcc-multilib (from .../gcc-multilib_4%3a4.6.3-1ubuntu5_i386.deb) ...
Selecting previously unselected package libkms1.
Unpacking libkms1 (from .../libkms1_2.4.32-1ubuntu1_i386.deb) ...
Selecting previously unselected package libbison-dev.
Unpacking libbison-dev (from .../libbison-dev_1%3a2.5.dfsg-2.1_i386.deb) ...
Selecting previously unselected package bison.
Unpacking bison (from .../bison_1%3a2.5.dfsg-2.1_i386.deb) ...
Selecting previously unselected package libstdc++6-4.6-dev.
Unpacking libstdc++6-4.6-dev (from .../libstdc++6-4.6-dev_4.6.3-1ubuntu5_i386.deb) ...
Selecting previously unselected package g++-4.6.
Unpacking g++-4.6 (from .../g++-4.6_4.6.3-1ubuntu5_i386.deb) ...
Selecting previously unselected package g++.
Unpacking g++ (from .../g++_4%3a4.6.3-1ubuntu5_i386.deb) ...
Selecting previously unselected package libtimedate-perl.
Unpacking libtimedate-perl (from .../libtimedate-perl_1.2000-1_all.deb) ...
Selecting previously unselected package libdpkg-perl.
Unpacking libdpkg-perl (from .../libdpkg-perl_1.16.1.2ubuntu7_all.deb) ...
Selecting previously unselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.16.1.2ubuntu7_all.deb) ...
Selecting previously unselected package build-essential.
Unpacking build-essential (from .../build-essential_11.5ubuntu2_i386.deb) ...
Selecting previously unselected package curl.
Unpacking curl (from .../curl_7.22.0-3ubuntu4_i386.deb) ...
Selecting previously unselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.18.2-1_i386.deb) ...
Selecting previously unselected package lib64stdc++6.
Unpacking lib64stdc++6 (from .../lib64stdc++6_4.6.3-1ubuntu5_i386.deb) ...
Selecting previously unselected package g++-4.6-multilib.
Unpacking g++-4.6-multilib (from .../g++-4.6-multilib_4.6.3-1ubuntu5_i386.deb) ...
Selecting previously unselected package g++-multilib.
Unpacking g++-multilib (from .../g++-multilib_4%3a4.6.3-1ubuntu5_i386.deb) ...
Selecting previously unselected package gperf.
Unpacking gperf (from .../gperf_3.0.3-1ubuntu1_i386.deb) ...
Selecting previously unselected package libalgorithm-diff-perl.
Unpacking libalgorithm-diff-perl (from .../libalgorithm-diff-perl_1.19.02-2_all.deb) ...
Selecting previously unselected package libalgorithm-diff-xs-perl.
Unpacking libalgorithm-diff-xs-perl (from .../libalgorithm-diff-xs-perl_0.04-2build2_i386.deb) ...
Selecting previously unselected package libalgorithm-merge-perl.
Unpacking libalgorithm-merge-perl (from .../libalgorithm-merge-perl_0.08-2_all.deb) ...
Selecting previously unselected package libdrm-dev.
Unpacking libdrm-dev (from .../libdrm-dev_2.4.32-1ubuntu1_i386.deb) ...
Selecting previously unselected package xorg-sgml-doctools.
Unpacking xorg-sgml-doctools (from .../xorg-sgml-doctools_1%3a1.10-1_all.deb) ...
Selecting previously unselected package x11proto-core-dev.
Unpacking x11proto-core-dev (from .../x11proto-core-dev_7.0.22-1_all.deb) ...
Selecting previously unselected package libice-dev.
Unpacking libice-dev (from .../libice-dev_2%3a1.0.7-2build1_i386.deb) ...
Selecting previously unselected package libtinfo-dev.
Unpacking libtinfo-dev (from .../libtinfo-dev_5.9-4_i386.deb) ...
Selecting previously unselected package libncurses5-dev.
Unpacking libncurses5-dev (from .../libncurses5-dev_5.9-4_i386.deb) ...
Selecting previously unselected package libpthread-stubs0.
Unpacking libpthread-stubs0 (from .../libpthread-stubs0_0.3-3_i386.deb) ...
Selecting previously unselected package libpthread-stubs0-dev.
Unpacking libpthread-stubs0-dev (from .../libpthread-stubs0-dev_0.3-3_i386.deb) ...
Selecting previously unselected package libreadline6-dev.
Unpacking libreadline6-dev (from .../libreadline6-dev_6.2-8_i386.deb) ...
Selecting previously unselected package libsm-dev.
Unpacking libsm-dev (from .../libsm-dev_2%3a1.2.0-2build1_i386.deb) ...
Selecting previously unselected package libxau-dev.
Unpacking libxau-dev (from .../libxau-dev_1%3a1.0.6-4_i386.deb) ...
Selecting previously unselected package libxdmcp-dev.
Unpacking libxdmcp-dev (from .../libxdmcp-dev_1%3a1.1.0-4_i386.deb) ...
Selecting previously unselected package x11proto-input-dev.
Unpacking x11proto-input-dev (from .../x11proto-input-dev_2.1.99.6-1_all.deb) ...
Selecting previously unselected package x11proto-kb-dev.
Unpacking x11proto-kb-dev (from .../x11proto-kb-dev_1.0.5-2_all.deb) ...
Selecting previously unselected package xtrans-dev.
Unpacking xtrans-dev (from .../xtrans-dev_1.2.6-2_all.deb) ...
Selecting previously unselected package libxcb1-dev.
Unpacking libxcb1-dev (from .../libxcb1-dev_1.8.1-1_i386.deb) ...
Selecting previously unselected package libx11-dev.
Unpacking libx11-dev (from .../libx11-dev_2%3a1.4.99.1-0ubuntu2_i386.deb) ...
Selecting previously unselected package libx11-doc.
Unpacking libx11-doc (from .../libx11-doc_2%3a1.4.99.1-0ubuntu2_all.deb) ...
Selecting previously unselected package x11proto-xext-dev.
Unpacking x11proto-xext-dev (from .../x11proto-xext-dev_7.2.0-3_all.deb) ...
Selecting previously unselected package libxext-dev.
Unpacking libxext-dev (from .../libxext-dev_2%3a1.3.0-3build1_i386.deb) ...
Selecting previously unselected package libxml2-utils.
Unpacking libxml2-utils (from .../libxml2-utils_2.7.8.dfsg-5.1ubuntu4.1_i386.deb) ...
Selecting previously unselected package libxt-dev.
Unpacking libxt-dev (from .../libxt-dev_1%3a1.1.1-2build1_i386.deb) ...
Selecting previously unselected package mesa-common-dev.
Unpacking mesa-common-dev (from .../mesa-common-dev_8.0.2-0ubuntu3.1_i386.deb) ...
Selecting previously unselected package mingw32-binutils.
Unpacking mingw32-binutils (from .../mingw32-binutils_2.20-0.2_i386.deb) ...
Selecting previously unselected package mingw32-runtime.
Unpacking mingw32-runtime (from .../mingw32-runtime_3.15.2-0ubuntu1_all.deb) ...
Selecting previously unselected package mingw32.
Unpacking mingw32 (from .../mingw32_4.2.1.dfsg-2ubuntu1_i386.deb) ...
Selecting previously unselected package python-markdown.
Unpacking python-markdown (from .../python-markdown_2.1.1-1_all.deb) ...
Selecting previously unselected package tofrodos.
Unpacking tofrodos (from .../tofrodos_1.7.9.debian.1-1_i386.deb) ...
Selecting previously unselected package xsltproc.
Unpacking xsltproc (from .../xsltproc_1.1.26-8ubuntu1_i386.deb) ...
Selecting previously unselected package zlib1g-dev.
Unpacking zlib1g-dev (from .../zlib1g-dev_1%3a1.2.3.4.dfsg-3ubuntu4_i386.deb) ...
Selecting previously unselected package libgl1-mesa-dev.
Unpacking libgl1-mesa-dev (from .../libgl1-mesa-dev_8.0.2-0ubuntu3.1_i386.deb) ...
Selecting previously unselected package openjdk-6-jdk.
Unpacking openjdk-6-jdk (from .../openjdk-6-jdk_6b24-1.11.3-1ubuntu0.12.04.1_i386.deb) ...
Processing triggers for install-info ...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 1 added doc-base file...
Setting up oracle-java7-installer (7u5-0~webupd8~5) ...
Removing outdated cached downloads...
Downloading cookie...
--2012-07-29 11:33:56--  http://launchpadlibrarian.net/98645053/cookie.txt
Resolving launchpadlibrarian.net (launchpadlibrarian.net)... 91.189.89.229, 91.189.89.228
Connecting to launchpadlibrarian.net (launchpadlibrarian.net)|91.189.89.229|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1053 (1.0K) [text/plain]
Saving to: `./cookie.txt'

     0K                                                      100% 5.77M=0s

2012-07-29 11:33:58 (5.77 MB/s) - `./cookie.txt' saved [1053/1053]

Downloading Oracle Java 7...
--2012-07-29 11:33:58--  http://download.oracle.com/otn-pub/java/jdk/7u5-b05/jdk-7u5-linux-i586.tar.gz
Resolving download.oracle.com (download.oracle.com)... 77.67.28.32, 77.67.28.50
Connecting to download.oracle.com (download.oracle.com)|77.67.28.32|:80... connected.
HTTP request sent, awaiting response... 403 Forbidden
2012-07-29 11:33:59 ERROR 403: Forbidden.

download failed
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Setting up m4 (1.4.16-2ubuntu1) ...
Setting up libfl-dev (2.5.35-10ubuntu3) ...
Setting up flex (2.5.35-10ubuntu3) ...
Setting up libc6-amd64 (2.15-0ubuntu10) ...
Setting up libc6-dev-amd64 (2.15-0ubuntu10) ...
Setting up lib64gcc1 (1:4.6.3-1ubuntu5) ...
Setting up lib64gomp1 (4.6.3-1ubuntu5) ...
Setting up lib64quadmath0 (4.6.3-1ubuntu5) ...
Setting up gcc-4.6-multilib (4.6.3-1ubuntu5) ...
Setting up gcc-multilib (4:4.6.3-1ubuntu5) ...
Setting up libkms1 (2.4.32-1ubuntu1) ...
Setting up libbison-dev (1:2.5.dfsg-2.1) ...
Setting up bison (1:2.5.dfsg-2.1) ...
update-alternatives: using /usr/bin/bison.yacc to provide /usr/bin/yacc (yacc) in auto mode.
Setting up libtimedate-perl (1.2000-1) ...
Setting up libdpkg-perl (1.16.1.2ubuntu7) ...
Setting up dpkg-dev (1.16.1.2ubuntu7) ...
Setting up curl (7.22.0-3ubuntu4) ...
Setting up fakeroot (1.18.2-1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.
Setting up lib64stdc++6 (4.6.3-1ubuntu5) ...
Setting up gperf (3.0.3-1ubuntu1) ...
Ignoring install-info called from maintainer script
The package gperf should be rebuilt with new debhelper to get trigger support
Setting up libalgorithm-diff-perl (1.19.02-2) ...
Setting up libalgorithm-diff-xs-perl (0.04-2build2) ...
Setting up libalgorithm-merge-perl (0.08-2) ...
Setting up libdrm-dev (2.4.32-1ubuntu1) ...
Setting up xorg-sgml-doctools (1:1.10-1) ...
Setting up x11proto-core-dev (7.0.22-1) ...
Setting up libice-dev (2:1.0.7-2build1) ...
Setting up libtinfo-dev (5.9-4) ...
Setting up libncurses5-dev (5.9-4) ...
Setting up libpthread-stubs0 (0.3-3) ...
Setting up libpthread-stubs0-dev (0.3-3) ...
Setting up libreadline6-dev (6.2-8) ...
Setting up libsm-dev (2:1.2.0-2build1) ...
Setting up libxau-dev (1:1.0.6-4) ...
Setting up libxdmcp-dev (1:1.1.0-4) ...
Setting up x11proto-input-dev (2.1.99.6-1) ...
Setting up x11proto-kb-dev (1.0.5-2) ...
Setting up xtrans-dev (1.2.6-2) ...
Setting up libxcb1-dev (1.8.1-1) ...
Setting up libx11-dev (2:1.4.99.1-0ubuntu2) ...
Setting up libx11-doc (2:1.4.99.1-0ubuntu2) ...
Setting up x11proto-xext-dev (7.2.0-3) ...
Setting up libxext-dev (2:1.3.0-3build1) ...
Setting up libxml2-utils (2.7.8.dfsg-5.1ubuntu4.1) ...
Setting up libxt-dev (1:1.1.1-2build1) ...
Setting up mesa-common-dev (8.0.2-0ubuntu3.1) ...
Setting up mingw32-binutils (2.20-0.2) ...
Setting up mingw32-runtime (3.15.2-0ubuntu1) ...
Setting up mingw32 (4.2.1.dfsg-2ubuntu1) ...
Setting up python-markdown (2.1.1-1) ...
Setting up tofrodos (1.7.9.debian.1-1) ...
Setting up xsltproc (1.1.26-8ubuntu1) ...
Setting up zlib1g-dev (1:1.2.3.4.dfsg-3ubuntu4) ...
Setting up libgl1-mesa-dev (8.0.2-0ubuntu3.1) ...
Setting up openjdk-6-jdk (6b24-1.11.3-1ubuntu0.12.04.1) ...
update-alternatives: using /usr/lib/jvm/java-6-openjdk-i386/bin/appletviewer to provide /usr/bin/appletviewer (appletviewer) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk-i386/bin/extcheck to provide /usr/bin/extcheck (extcheck) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk-i386/bin/idlj to provide /usr/bin/idlj (idlj) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk-i386/bin/jar to provide /usr/bin/jar (jar) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk-i386/bin/jarsigner to provide /usr/bin/jarsigner (jarsigner) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk-i386/bin/javac to provide /usr/bin/javac (javac) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk-i386/bin/javadoc to provide /usr/bin/javadoc (javadoc) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk-i386/bin/javah to provide /usr/bin/javah (javah) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk-i386/bin/javap to provide /usr/bin/javap (javap) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk-i386/bin/jconsole to provide /usr/bin/jconsole (jconsole) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk-i386/bin/jdb to provide /usr/bin/jdb (jdb) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk-i386/bin/jhat to provide /usr/bin/jhat (jhat) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk-i386/bin/jinfo to provide /usr/bin/jinfo (jinfo) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk-i386/bin/jmap to provide /usr/bin/jmap (jmap) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk-i386/bin/jps to provide /usr/bin/jps (jps) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk-i386/bin/jrunscript to provide /usr/bin/jrunscript (jrunscript) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk-i386/bin/jsadebugd to provide /usr/bin/jsadebugd (jsadebugd) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk-i386/bin/jstack to provide /usr/bin/jstack (jstack) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk-i386/bin/jstat to provide /usr/bin/jstat (jstat) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk-i386/bin/jstatd to provide /usr/bin/jstatd (jstatd) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk-i386/bin/native2ascii to provide /usr/bin/native2ascii (native2ascii) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk-i386/bin/rmic to provide /usr/bin/rmic (rmic) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk-i386/bin/schemagen to provide /usr/bin/schemagen (schemagen) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk-i386/bin/serialver to provide /usr/bin/serialver (serialver) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk-i386/bin/wsgen to provide /usr/bin/wsgen (wsgen) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk-i386/bin/wsimport to provide /usr/bin/wsimport (wsimport) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk-i386/bin/xjc to provide /usr/bin/xjc (xjc) in auto mode.
Setting up g++-4.6 (4.6.3-1ubuntu5) ...
Setting up g++ (4:4.6.3-1ubuntu5) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode.
Setting up build-essential (11.5ubuntu2) ...
Setting up g++-4.6-multilib (4.6.3-1ubuntu5) ...
Setting up g++-multilib (4:4.6.3-1ubuntu5) ...
Setting up libstdc++6-4.6-dev (4.6.3-1ubuntu5) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
[COLOR=Red][B][SIZE=3]Errors were encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/SIZE][/B][/COLOR][/SIZE]
```

---

### Post by raja.genupula on 2012-07-29
[http://ubuntuforums.org/showthread.php?t=2029147](http://ubuntuforums.org/showthread.php?t=2029147)

---

