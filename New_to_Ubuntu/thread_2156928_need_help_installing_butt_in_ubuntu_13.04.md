---
title: "need help installing butt in ubuntu 13.04"
date: 2013-06-23
forum: New to Ubuntu
---

### Post by attyd on 2013-06-23
hi i tried installing BUTT referring this link [http://www.omgubuntu.co.uk/2010/09/broadcast-on-icecastshoutcast-using-butt](http://www.omgubuntu.co.uk/2010/09/broadcast-on-icecastshoutcast-using-butt)

but im sure im doing something wrong. PORTAUDIO is not getting installed . 

im extremely new to ubuntu. please help.  attaching the log here.





jack@jack-desktop:~$```
 cd / butt-0.1.12-linux-bin
jack@jack-desktop:/$ sudo apt-get install libmp3lame0 libvorbis-dev portaudio libfltk-dev 
[sudo] password for jack: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libfltk-dev is a virtual package provided by:
  libfltk1.3-dev 1.3.0-9
  libfltk1.1-dev 1.1.10-14ubuntu1
You should explicitly select one to install.

E: Unable to locate package portaudio
E: Package 'libfltk-dev' has no installation candidate
jack@jack-desktop:/$ ./configure && make
bash: ./configure: No such file or directory
jack@jack-desktop:/$ apt-get libfltk1.1-dev 1.1.10-14ubuntu1
E: Invalid operation libfltk1.1-dev
jack@jack-desktop:/$ apt-get libfltk1.3-dev 1.3.0-9
E: Invalid operation libfltk1.3-dev
jack@jack-desktop:/$ apt-get portaudio
E: Invalid operation portaudio
jack@jack-desktop:/$ sudo apt-get install libmp3lame0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libmp3lame0 is already the newest version.
libmp3lame0 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jack@jack-desktop:/$ sudo apt-get install libvorbis-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libogg-dev
The following NEW packages will be installed:
  libogg-dev libvorbis-dev
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 562 kB of archives.
After this operation, 4,292 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) raring/main libogg-dev amd64 1.3.0-4 [87.9 kB]
Get:2 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) raring/main libvorbis-dev amd64 1.3.2-1.3 [474 kB]
Fetched 562 kB in 8s (63.9 kB/s)                                                 
Selecting previously unselected package libogg-dev:amd64.
(Reading database ... 187636 files and directories currently installed.)
Unpacking libogg-dev:amd64 (from .../libogg-dev_1.3.0-4_amd64.deb) ...
Selecting previously unselected package libvorbis-dev:amd64.
Unpacking libvorbis-dev:amd64 (from .../libvorbis-dev_1.3.2-1.3_amd64.deb) ...
Processing triggers for doc-base ...
Processing 1 added doc-base file...
Setting up libogg-dev:amd64 (1.3.0-4) ...
Setting up libvorbis-dev:amd64 (1.3.2-1.3) ...
jack@jack-desktop:/$ sudo apt-get install portaudio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package portaudio
jack@jack-desktop:/$ sudo apt-get install portaudio libfltk-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libfltk-dev is a virtual package provided by:
  libfltk1.3-dev 1.3.0-9
  libfltk1.1-dev 1.1.10-14ubuntu1
You should explicitly select one to install.

E: Unable to locate package portaudio
E: Package 'libfltk-dev' has no installation candidate
jack@jack-desktop:/$ sudo apt-get install libfltk1.1-dev 1.1.10-14ubuntu1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package 1.1.10-14ubuntu1
E: Couldn't find any package by regex '1.1.10-14ubuntu1'
jack@jack-desktop:/$ sudo apt-get install libfltk1.3-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  fltk1.3-doc fluid libdrm-dev libfltk-cairo1.3 libfltk-forms1.3 libfltk-gl1.3
  libfltk-images1.3 libfltk1.3 libgl1-mesa-dev libglu1-mesa-dev libkms1
  libpthread-stubs0 libpthread-stubs0-dev libx11-dev libx11-doc libx11-xcb-dev
  libxau-dev libxcb-dri2-0-dev libxcb-glx0-dev libxcb1-dev libxdamage-dev
  libxdmcp-dev libxext-dev libxfixes-dev libxxf86vm-dev mesa-common-dev
  x11proto-core-dev x11proto-damage-dev x11proto-dri2-dev x11proto-fixes-dev
  x11proto-gl-dev x11proto-input-dev x11proto-kb-dev x11proto-xext-dev
  x11proto-xf86vidmode-dev xorg-sgml-doctools xtrans-dev
Suggested packages:
  libcairo2-dev libjpeg-dev libpng-dev libxft-dev libxinerama-dev zlib1g-dev
  libz-dev libxcb-doc libxext-doc
The following NEW packages will be installed:
  fltk1.3-doc fluid libdrm-dev libfltk-cairo1.3 libfltk-forms1.3 libfltk-gl1.3
  libfltk-images1.3 libfltk1.3 libfltk1.3-dev libgl1-mesa-dev libglu1-mesa-dev
  libkms1 libpthread-stubs0 libpthread-stubs0-dev libx11-dev libx11-doc
  libx11-xcb-dev libxau-dev libxcb-dri2-0-dev libxcb-glx0-dev libxcb1-dev
  libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev libxxf86vm-dev
  mesa-common-dev x11proto-core-dev x11proto-damage-dev x11proto-dri2-dev
  x11proto-fixes-dev x11proto-gl-dev x11proto-input-dev x11proto-kb-dev
  x11proto-xext-dev x11proto-xf86vidmode-dev xorg-sgml-doctools xtrans-dev
0 upgraded, 38 newly installed, 0 to remove and 0 not upgraded.
Need to get 18.1 MB of archives.
After this operation, 70.5 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) raring/universe libfltk1.3 amd64 1.3.0-9 [677 kB]
Get:2 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) raring/universe libfltk-cairo1.3 amd64 1.3.0-9 [7,060 B]
Get:3 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) raring/universe libfltk-forms1.3 amd64 1.3.0-9 [15.0 kB]
Get:4 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) raring/universe libfltk-gl1.3 amd64 1.3.0-9 [47.2 kB]
Get:5 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) raring/universe libfltk-images1.3 amd64 1.3.0-9 [29.2 kB]
Get:6 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) raring/main libkms1 amd64 2.4.43-0ubuntu1 [9,208 B]
Get:7 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) raring/main xorg-sgml-doctools all 1:1.10-1 [12.0 kB]
Get:8 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) raring/main x11proto-core-dev all 7.0.23-1 [744 kB]
Get:9 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) raring/main libxau-dev amd64 1:1.0.7-1 [10.2 kB]
Get:10 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) raring/main libxdmcp-dev amd64 1:1.1.1-1 [26.9 kB]
Get:11 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) raring/main x11proto-input-dev all 2.2.99.1-0ubuntu1 [139 kB]
Get:12 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) raring/main x11proto-kb-dev all 1.0.6-2 [269 kB]
Get:13 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) raring/main xtrans-dev all 1.2.7-1 [84.3 kB]
Get:14 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) raring/main libpthread-stubs0 amd64 0.3-3 [3,258 B]
Get:15 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) raring/main libpthread-stubs0-dev amd64 0.3-3 [2,866 B]
Get:16 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) raring-updates/main libxcb1-dev amd64 1.8.1-2ubuntu2.1 [82.6 kB]
Get:17 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) raring-updates/main libx11-dev amd64 2:1.5.0-1ubuntu1.1 [911 kB]
Get:18 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) raring/main libdrm-dev amd64 2.4.43-0ubuntu1 [208 kB]
Get:19 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) raring-updates/main mesa-common-dev amd64 9.1.3-0ubuntu0.3 [272 kB]
Get:20 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) raring-updates/main libx11-xcb-dev amd64 2:1.5.0-1ubuntu1.1 [11.1 kB]
Get:21 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) raring-updates/main libxcb-dri2-0-dev amd64 1.8.1-2ubuntu2.1 [10.2 kB]
Get:22 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) raring-updates/main libxcb-glx0-dev amd64 1.8.1-2ubuntu2.1 [43.7 kB]
Get:23 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) raring/main x11proto-xext-dev all 7.2.1-1 [265 kB]
Get:24 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) raring/main x11proto-fixes-dev all 1:5.0-2ubuntu1 [15.5 kB]
Get:25 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) raring-updates/main libxfixes-dev amd64 1:5.0-4ubuntu5.13.04.1 [14.0 kB]
Get:26 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) raring/main x11proto-damage-dev all 1:1.2.1-2 [8,286 B]
Get:27 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) raring/main libxdamage-dev amd64 1:1.1.3-2build2 [5,516 B]
Get:28 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) raring-updates/main libxext-dev amd64 2:1.3.1-2ubuntu0.13.04.1 [92.1 kB]
Get:29 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) raring/main x11proto-xf86vidmode-dev all 2.3.1-2 [6,116 B]
Get:30 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) raring-updates/main libxxf86vm-dev amd64 1:1.1.2-1ubuntu0.13.04.1 [14.7 kB]
Get:31 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) raring/main x11proto-dri2-dev all 2.8-1 [12.6 kB]
Get:32 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) raring/main x11proto-gl-dev all 1.4.16-1 [22.3 kB]
Get:33 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) raring-updates/main libgl1-mesa-dev amd64 9.1.3-0ubuntu0.3 [5,166 B]
Get:34 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) raring/universe fltk1.3-doc all 1.3.0-9 [9,892 kB]
Get:35 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) raring/universe fluid amd64 1.3.0-9 [235 kB]
Get:36 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) raring/universe libfltk1.3-dev amd64 1.3.0-9 [1,131 kB]
Get:37 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) raring/main libglu1-mesa-dev amd64 9.0.0-0ubuntu1 [314 kB]
Get:38 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) raring-updates/main libx11-doc all 2:1.5.0-1ubuntu1.1 [2,448 kB]
Fetched 18.1 MB in 2min 52s (105 kB/s)                                           
Extracting templates from packages: 100%
Selecting previously unselected package libfltk1.3:amd64.
(Reading database ... 187897 files and directories currently installed.)
Unpacking libfltk1.3:amd64 (from .../libfltk1.3_1.3.0-9_amd64.deb) ...
Selecting previously unselected package libfltk-cairo1.3:amd64.
Unpacking libfltk-cairo1.3:amd64 (from .../libfltk-cairo1.3_1.3.0-9_amd64.deb) ...
Selecting previously unselected package libfltk-forms1.3:amd64.
Unpacking libfltk-forms1.3:amd64 (from .../libfltk-forms1.3_1.3.0-9_amd64.deb) ...
Selecting previously unselected package libfltk-gl1.3:amd64.
Unpacking libfltk-gl1.3:amd64 (from .../libfltk-gl1.3_1.3.0-9_amd64.deb) ...
Selecting previously unselected package libfltk-images1.3:amd64.
Unpacking libfltk-images1.3:amd64 (from .../libfltk-images1.3_1.3.0-9_amd64.deb) ...
Selecting previously unselected package libkms1:amd64.
Unpacking libkms1:amd64 (from .../libkms1_2.4.43-0ubuntu1_amd64.deb) ...
Selecting previously unselected package xorg-sgml-doctools.
Unpacking xorg-sgml-doctools (from .../xorg-sgml-doctools_1%3a1.10-1_all.deb) ...
Selecting previously unselected package x11proto-core-dev.
Unpacking x11proto-core-dev (from .../x11proto-core-dev_7.0.23-1_all.deb) ...
Selecting previously unselected package libxau-dev:amd64.
Unpacking libxau-dev:amd64 (from .../libxau-dev_1%3a1.0.7-1_amd64.deb) ...
Selecting previously unselected package libxdmcp-dev:amd64.
Unpacking libxdmcp-dev:amd64 (from .../libxdmcp-dev_1%3a1.1.1-1_amd64.deb) ...
Selecting previously unselected package x11proto-input-dev.
Unpacking x11proto-input-dev (from .../x11proto-input-dev_2.2.99.1-0ubuntu1_all.deb) ...
Selecting previously unselected package x11proto-kb-dev.
Unpacking x11proto-kb-dev (from .../x11proto-kb-dev_1.0.6-2_all.deb) ...
Selecting previously unselected package xtrans-dev.
Unpacking xtrans-dev (from .../xtrans-dev_1.2.7-1_all.deb) ...
Selecting previously unselected package libpthread-stubs0:amd64.
Unpacking libpthread-stubs0:amd64 (from .../libpthread-stubs0_0.3-3_amd64.deb) ...
Selecting previously unselected package libpthread-stubs0-dev:amd64.
Unpacking libpthread-stubs0-dev:amd64 (from .../libpthread-stubs0-dev_0.3-3_amd64.deb) ...
Selecting previously unselected package libxcb1-dev:amd64.
Unpacking libxcb1-dev:amd64 (from .../libxcb1-dev_1.8.1-2ubuntu2.1_amd64.deb) ...
Selecting previously unselected package libx11-dev:amd64.
Unpacking libx11-dev:amd64 (from .../libx11-dev_2%3a1.5.0-1ubuntu1.1_amd64.deb) ...
Selecting previously unselected package libdrm-dev.
Unpacking libdrm-dev (from .../libdrm-dev_2.4.43-0ubuntu1_amd64.deb) ...
Selecting previously unselected package mesa-common-dev.
Unpacking mesa-common-dev (from .../mesa-common-dev_9.1.3-0ubuntu0.3_amd64.deb) ...
Selecting previously unselected package libx11-xcb-dev.
Unpacking libx11-xcb-dev (from .../libx11-xcb-dev_2%3a1.5.0-1ubuntu1.1_amd64.deb) ...
Selecting previously unselected package libxcb-dri2-0-dev:amd64.
Unpacking libxcb-dri2-0-dev:amd64 (from .../libxcb-dri2-0-dev_1.8.1-2ubuntu2.1_amd64.deb) ...
Selecting previously unselected package libxcb-glx0-dev:amd64.
Unpacking libxcb-glx0-dev:amd64 (from .../libxcb-glx0-dev_1.8.1-2ubuntu2.1_amd64.deb) ...
Selecting previously unselected package x11proto-xext-dev.
Unpacking x11proto-xext-dev (from .../x11proto-xext-dev_7.2.1-1_all.deb) ...
Selecting previously unselected package x11proto-fixes-dev.
Unpacking x11proto-fixes-dev (from .../x11proto-fixes-dev_1%3a5.0-2ubuntu1_all.deb) ...
Selecting previously unselected package libxfixes-dev.
Unpacking libxfixes-dev (from .../libxfixes-dev_1%3a5.0-4ubuntu5.13.04.1_amd64.deb) ...
Selecting previously unselected package x11proto-damage-dev.
Unpacking x11proto-damage-dev (from .../x11proto-damage-dev_1%3a1.2.1-2_all.deb) ...
Selecting previously unselected package libxdamage-dev.
Unpacking libxdamage-dev (from .../libxdamage-dev_1%3a1.1.3-2build2_amd64.deb) ...
Selecting previously unselected package libxext-dev:amd64.
Unpacking libxext-dev:amd64 (from .../libxext-dev_2%3a1.3.1-2ubuntu0.13.04.1_amd64.deb) ...
Selecting previously unselected package x11proto-xf86vidmode-dev.
Unpacking x11proto-xf86vidmode-dev (from .../x11proto-xf86vidmode-dev_2.3.1-2_all.deb) ...
Selecting previously unselected package libxxf86vm-dev.
Unpacking libxxf86vm-dev (from .../libxxf86vm-dev_1%3a1.1.2-1ubuntu0.13.04.1_amd64.deb) ...
Selecting previously unselected package x11proto-dri2-dev.
Unpacking x11proto-dri2-dev (from .../x11proto-dri2-dev_2.8-1_all.deb) ...
Selecting previously unselected package x11proto-gl-dev.
Unpacking x11proto-gl-dev (from .../x11proto-gl-dev_1.4.16-1_all.deb) ...
Selecting previously unselected package libgl1-mesa-dev.
Unpacking libgl1-mesa-dev (from .../libgl1-mesa-dev_9.1.3-0ubuntu0.3_amd64.deb) ...
Selecting previously unselected package fltk1.3-doc.
Unpacking fltk1.3-doc (from .../fltk1.3-doc_1.3.0-9_all.deb) ...
Selecting previously unselected package fluid.
Unpacking fluid (from .../fluid_1.3.0-9_amd64.deb) ...
Selecting previously unselected package libfltk1.3-dev.
Unpacking libfltk1.3-dev (from .../libfltk1.3-dev_1.3.0-9_amd64.deb) ...
Selecting previously unselected package libglu1-mesa-dev.
Unpacking libglu1-mesa-dev (from .../libglu1-mesa-dev_9.0.0-0ubuntu1_amd64.deb) ...
Selecting previously unselected package libx11-doc.
Unpacking libx11-doc (from .../libx11-doc_2%3a1.5.0-1ubuntu1.1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 1 added doc-base file...
Processing triggers for hicolor-icon-theme ...
Processing triggers for menu ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Setting up libfltk1.3:amd64 (1.3.0-9) ...
Setting up libfltk-cairo1.3:amd64 (1.3.0-9) ...
Setting up libfltk-forms1.3:amd64 (1.3.0-9) ...
Setting up libfltk-gl1.3:amd64 (1.3.0-9) ...
Setting up libfltk-images1.3:amd64 (1.3.0-9) ...
Setting up libkms1:amd64 (2.4.43-0ubuntu1) ...
Setting up xorg-sgml-doctools (1:1.10-1) ...
Setting up x11proto-core-dev (7.0.23-1) ...
Setting up libxau-dev:amd64 (1:1.0.7-1) ...
Setting up libxdmcp-dev:amd64 (1:1.1.1-1) ...
Setting up x11proto-input-dev (2.2.99.1-0ubuntu1) ...
Setting up x11proto-kb-dev (1.0.6-2) ...
Setting up xtrans-dev (1.2.7-1) ...
Setting up libpthread-stubs0:amd64 (0.3-3) ...
Setting up libpthread-stubs0-dev:amd64 (0.3-3) ...
Setting up libxcb1-dev:amd64 (1.8.1-2ubuntu2.1) ...
Setting up libx11-dev:amd64 (2:1.5.0-1ubuntu1.1) ...
Setting up libdrm-dev (2.4.43-0ubuntu1) ...
Setting up mesa-common-dev (9.1.3-0ubuntu0.3) ...
Setting up libx11-xcb-dev (2:1.5.0-1ubuntu1.1) ...
Setting up libxcb-dri2-0-dev:amd64 (1.8.1-2ubuntu2.1) ...
Setting up libxcb-glx0-dev:amd64 (1.8.1-2ubuntu2.1) ...
Setting up x11proto-xext-dev (7.2.1-1) ...
Setting up x11proto-fixes-dev (1:5.0-2ubuntu1) ...
Setting up libxfixes-dev (1:5.0-4ubuntu5.13.04.1) ...
Setting up x11proto-damage-dev (1:1.2.1-2) ...
Setting up libxdamage-dev (1:1.1.3-2build2) ...
Setting up libxext-dev:amd64 (2:1.3.1-2ubuntu0.13.04.1) ...
Setting up x11proto-xf86vidmode-dev (2.3.1-2) ...
Setting up libxxf86vm-dev (1:1.1.2-1ubuntu0.13.04.1) ...
Setting up x11proto-dri2-dev (2.8-1) ...
Setting up x11proto-gl-dev (1.4.16-1) ...
Setting up libgl1-mesa-dev (9.1.3-0ubuntu0.3) ...
Setting up fltk1.3-doc (1.3.0-9) ...
Setting up fluid (1.3.0-9) ...
Setting up libfltk1.3-dev (1.3.0-9) ...
Setting up libglu1-mesa-dev (9.0.0-0ubuntu1) ...
Setting up libx11-doc (2:1.5.0-1ubuntu1.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
jack@jack-desktop:/$ ./configure && make
bash: ./configure: No such file or directory
jack@jack-desktop:/$ ./configure && make
bash: ./configure: No such file or directory
jack@jack-desktop:/$ sudo make install
make: *** No rule to make target `install'.  Stop.
jack@jack-desktop:/$ /configure && make
bash: /configure: No such file or directory
jack@jack-desktop:/$ ./configure & make
[1] 19546
bash: ./configure: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
[1]+  Exit 127                ./configure
jack@jack-desktop:/$ sudo make install
make: *** No rule to make target `install'.  Stop.
jack@jack-desktop:/$ sudo apt-get install libmp3lame0 libvorbis-dev portaudio libfltk-dev 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libfltk-dev is a virtual package provided by:
  libfltk1.3-dev 1.3.0-9
  libfltk1.1-dev 1.1.10-14ubuntu1
You should explicitly select one to install.

E: Unable to locate package portaudio
E: Package 'libfltk-dev' has no installation candidate
jack@jack-desktop:/$ sudo apt-get install portaudio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package portaudio
jack@jack-desktop:/$ sudo apt-get install butt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package butt
jack@jack-desktop:/$ deb [http://ppa.launchpad.net/ys/radio-battletoads/ubuntu](http://ppa.launchpad.net/ys/radio-battletoads/ubuntu)
No command 'deb' found, did you mean:
 Command 'dab' from package 'bsdgames' (universe)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dwb' from package 'dwb' (universe)
 Command 'xdeb' from package 'xdeb' (universe)
 Command 'debc' from package 'devscripts' (main)
 Command 'debi' from package 'devscripts' (main)
deb: command not found
jack@jack-desktop:/$ deb-src [http://ppa.launchpad.net/ys/radio-battletoads/ubuntu](http://ppa.launchpad.net/ys/radio-battletoads/ubuntu)
deb-src: command not found
jack@jack-desktop:/$ / cd desktop/butt
bash: /: Is a directory
jack@jack-desktop:/$ ./configure
bash: ./configure: No such file or directory
jack@jack-desktop:/$
```

---

### Post by wildmanne39 on 2013-06-23
Hi, did you try it like this?
```
sudo add-apt-repository ppa:ys/radio-battletoads && sudo apt-get update && sudo apt-get install butt
```
This worked for me, I have to run it in the terminal.
Thanks

---

### Post by attyd on 2013-06-23
thnaks for this man... i tried,  it went smooth until the following...     W: Failed to fetch [http://ppa.launchpad.net/ys/radio-battletoads/ubuntu/dists/raring/main/binary-amd64/Packages](http://ppa.launchpad.net/ys/radio-battletoads/ubuntu/dists/raring/main/binary-amd64/Packages)  404  Not Found  W: Failed to fetch [http://ppa.launchpad.net/ys/radio-battletoads/ubuntu/dists/raring/main/binary-i386/Packages](http://ppa.launchpad.net/ys/radio-battletoads/ubuntu/dists/raring/main/binary-i386/Packages)  404  Not Found  E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by claracc on 2013-06-24
It seems that radio battletoads ppa are for quantal or precise ubuntu but no for raring yet?:

[https://launchpad.net/~ys/+archive/radio-battletoads/+packages](https://launchpad.net/~ys/+archive/radio-battletoads/+packages)

---

