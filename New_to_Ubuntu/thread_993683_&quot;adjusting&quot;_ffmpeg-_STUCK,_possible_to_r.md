---
title: "&quot;adjusting&quot; ffmpeg- STUCK, possible to ruin computer?"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by BastardNamban on 2008-11-26
I hope this can still be considered a beginner post, as I've only just began Ubuntu. Up till now, I've done alot in only a few days, and I even successfully upgraded my compiz fusion to 0.76 from 0.74, among other difficult things. I'm getting there!

BUT it seems I've picked something out of my league to tangle with, & I'm stuck. I was trying to download & convert a video using the Download Helper add-on in firefox (a scientific .flv video), when I tried to convert from .flv to .avi instead of the native .wmv. Following it's help link, I learned I had to do some stuff to adjust it. I ended up here:

[https://wiki.ubuntu.com/ffmpeg](https://wiki.ubuntu.com/ffmpeg)

I have followed it to the "Because you enabled amr..." part, and have this (excuse the length!) ```
(ME)@(Comp):~$ sudo apt-get build-dep ffmpeg
[sudo] password for (ME): 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  build-essential debhelper diffstat dpkg-dev g++ g++-4.2 gettext html2text
  intltool-debian libdc1394-13-dev libfreetype6-dev libgif-dev libgif4
  libgl1-mesa-dev libglu1-mesa-dev libglu1-xorg-dev libgsm1-dev libimlib2
  libimlib2-dev libjpeg62-dev libltdl3-dev libogg-dev libpng12-dev
  libpthread-stubs0 libpthread-stubs0-dev libraw1394-dev libsdl1.2-dev
  libstdc++6-4.2-dev libtheora-dev libtiff4-dev libtiffxx0c2 libtimedate-perl
  libvorbis-dev libx11-dev libxau-dev libxcb-xlib0-dev libxcb1-dev
  libxdmcp-dev libxext-dev mesa-common-dev patch po-debconf quilt texi2html
  x11proto-core-dev x11proto-input-dev x11proto-kb-dev x11proto-xext-dev
  xtrans-dev zlib1g-dev
0 upgraded, 50 newly installed, 0 to remove and 16 not upgraded.
Need to get 12.5MB/15.2MB of archives.
After this operation, 56.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://jp.archive.ubuntu.com hardy-updates/main libstdc++6-4.2-dev 4.2.4-1ubuntu3 [1187kB]
Get:2 http://jp.archive.ubuntu.com hardy-updates/main g++-4.2 4.2.4-1ubuntu3 [2784kB]
Get:3 http://jp.archive.ubuntu.com hardy-updates/main g++ 4:4.2.3-1ubuntu6 [1440B]
Get:4 http://jp.archive.ubuntu.com hardy/main libtimedate-perl 1.1600-9 [30.1kB]
Get:5 http://jp.archive.ubuntu.com hardy/main patch 2.5.9-4 [95.6kB]           
Get:6 http://jp.archive.ubuntu.com hardy-updates/main dpkg-dev 1.14.16.6ubuntu4 [559kB]
Get:7 http://jp.archive.ubuntu.com hardy/main build-essential 11.3ubuntu1 [7066B]
Get:8 http://jp.archive.ubuntu.com hardy/main html2text 1.3.2a-3build2 [87.6kB]
Get:9 http://jp.archive.ubuntu.com hardy/main gettext 0.17-2ubuntu1 [1978kB]   
Get:10 http://jp.archive.ubuntu.com hardy/main intltool-debian 0.35.0+20060710.1 [31.6kB]
Get:11 http://jp.archive.ubuntu.com hardy/main po-debconf 1.0.10 [232kB]       
Get:12 http://jp.archive.ubuntu.com hardy/main debhelper 6.0.4ubuntu1 [516kB]  
Get:13 http://jp.archive.ubuntu.com hardy/main diffstat 1.45-2 [21.2kB]        
Get:14 http://jp.archive.ubuntu.com hardy-updates/main libfreetype6-dev 2.3.5-1ubuntu4.8.04.1 [663kB]
Get:15 http://jp.archive.ubuntu.com hardy/main libgif4 4.1.6-4 [38.7kB]        
Get:16 http://jp.archive.ubuntu.com hardy/main libgif-dev 4.1.6-4 [42.6kB]     
Get:17 http://jp.archive.ubuntu.com hardy/main libglu1-mesa-dev 7.0.3~rc2-1ubuntu3 [258kB]
Get:18 http://jp.archive.ubuntu.com hardy-updates/main libglu1-xorg-dev 1:7.3+10ubuntu10.2 [964B]
Get:19 http://jp.archive.ubuntu.com hardy/main libgsm1-dev 1.0.12-1 [34.0kB]   
Get:20 http://jp.archive.ubuntu.com hardy/main libimlib2 1.4.0-1ubuntu1 [191kB]
Get:21 http://jp.archive.ubuntu.com hardy/main libjpeg62-dev 6b-14 [188kB]     
Get:22 http://jp.archive.ubuntu.com hardy/main libltdl3-dev 1.5.26-1ubuntu1 [370kB]
Get:23 http://jp.archive.ubuntu.com hardy-updates/main libtiffxx0c2 3.8.2-7ubuntu3.1 [5038B]
Get:24 http://jp.archive.ubuntu.com hardy-updates/main libtiff4-dev 3.8.2-7ubuntu3.1 [552kB]
Get:25 http://jp.archive.ubuntu.com hardy/main libimlib2-dev 1.4.0-1ubuntu1 [310kB]
Get:26 http://jp.archive.ubuntu.com hardy/main libogg-dev 1.1.3-3ubuntu1 [92.8kB]
Get:27 http://jp.archive.ubuntu.com hardy/main libraw1394-dev 1.3.0-2 [49.8kB] 
Get:28 http://jp.archive.ubuntu.com hardy/main libsdl1.2-dev 1.2.13-1ubuntu1 [821kB]
Get:29 http://jp.archive.ubuntu.com hardy/main libtheora-dev 1.0~beta2-2 [243kB]
Get:30 http://jp.archive.ubuntu.com hardy/main libvorbis-dev 1.2.0.dfsg-2 [455kB]
Get:31 http://jp.archive.ubuntu.com hardy/main quilt 0.46-4 [300kB]            
Get:32 http://jp.archive.ubuntu.com hardy/main texi2html 1.78-1 [345kB]        
Get:33 http://jp.archive.ubuntu.com hardy/main libdc1394-13-dev 1.1.0-5ubuntu1 [41.1kB]
Fetched 12.5MB in 31s (398kB/s)                                                
Extracting templates from packages: 100%
Selecting previously deselected package x11proto-core-dev.
(Reading database ... 101362 files and directories currently installed.)
Unpacking x11proto-core-dev (from .../x11proto-core-dev_7.0.11-1_all.deb) ...
Selecting previously deselected package libxau-dev.
Unpacking libxau-dev (from .../libxau-dev_1%3a1.0.3-2_i386.deb) ...
Selecting previously deselected package libpthread-stubs0.
Unpacking libpthread-stubs0 (from .../libpthread-stubs0_0.1-2_i386.deb) ...
Selecting previously deselected package libpthread-stubs0-dev.
Unpacking libpthread-stubs0-dev (from .../libpthread-stubs0-dev_0.1-2_i386.deb) ...
Selecting previously deselected package libxdmcp-dev.
Unpacking libxdmcp-dev (from .../libxdmcp-dev_1%3a1.0.2-2_i386.deb) ...
Selecting previously deselected package libxcb1-dev.
Unpacking libxcb1-dev (from .../libxcb1-dev_1.1-1ubuntu1_i386.deb) ...
Selecting previously deselected package libxcb-xlib0-dev.
Unpacking libxcb-xlib0-dev (from .../libxcb-xlib0-dev_1.1-1ubuntu1_i386.deb) ...
Selecting previously deselected package x11proto-input-dev.
Unpacking x11proto-input-dev (from .../x11proto-input-dev_1.4.2-1_all.deb) ...
Selecting previously deselected package x11proto-kb-dev.
Unpacking x11proto-kb-dev (from .../x11proto-kb-dev_1.0.3-2ubuntu1_all.deb) ...
Selecting previously deselected package xtrans-dev.
Unpacking xtrans-dev (from .../xtrans-dev_1.0.4-1_all.deb) ...
Selecting previously deselected package libx11-dev.
Unpacking libx11-dev (from .../libx11-dev_2%3a1.1.3-1ubuntu2ja4_i386.deb) ...
Selecting previously deselected package x11proto-xext-dev.
Unpacking x11proto-xext-dev (from .../x11proto-xext-dev_7.0.2-5ubuntu1_all.deb) ...
Selecting previously deselected package libxext-dev.
Unpacking libxext-dev (from .../libxext-dev_2%3a1.0.3-2build1_i386.deb) ...
Selecting previously deselected package libstdc++6-4.2-dev.
Unpacking libstdc++6-4.2-dev (from .../libstdc++6-4.2-dev_4.2.4-1ubuntu3_i386.deb) ...
Selecting previously deselected package g++-4.2.
Unpacking g++-4.2 (from .../g++-4.2_4.2.4-1ubuntu3_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.2.3-1ubuntu6_i386.deb) ...
Selecting previously deselected package libtimedate-perl.
Unpacking libtimedate-perl (from .../libtimedate-perl_1.1600-9_all.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.5.9-4_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.14.16.6ubuntu4_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3ubuntu1_i386.deb) ...
Selecting previously deselected package html2text.
Unpacking html2text (from .../html2text_1.3.2a-3build2_i386.deb) ...
Selecting previously deselected package gettext.
Unpacking gettext (from .../gettext_0.17-2ubuntu1_i386.deb) ...
Selecting previously deselected package intltool-debian.
Unpacking intltool-debian (from .../intltool-debian_0.35.0+20060710.1_all.deb) ...
Selecting previously deselected package po-debconf.
Unpacking po-debconf (from .../po-debconf_1.0.10_all.deb) ...
Selecting previously deselected package debhelper.
Unpacking debhelper (from .../debhelper_6.0.4ubuntu1_all.deb) ...
Selecting previously deselected package diffstat.
Unpacking diffstat (from .../diffstat_1.45-2_i386.deb) ...
Selecting previously deselected package zlib1g-dev.
Unpacking zlib1g-dev (from .../zlib1g-dev_1%3a1.2.3.3.dfsg-7ubuntu1_i386.deb) ...
Selecting previously deselected package libfreetype6-dev.
Unpacking libfreetype6-dev (from .../libfreetype6-dev_2.3.5-1ubuntu4.8.04.1_i386.deb) ...
Selecting previously deselected package libgif4.
Unpacking libgif4 (from .../libgif4_4.1.6-4_i386.deb) ...
Selecting previously deselected package libgif-dev.
Unpacking libgif-dev (from .../libgif-dev_4.1.6-4_i386.deb) ...
Selecting previously deselected package mesa-common-dev.
Unpacking mesa-common-dev (from .../mesa-common-dev_7.0.3~rc2-1ubuntu3_all.deb) ...
Selecting previously deselected package libgl1-mesa-dev.
Unpacking libgl1-mesa-dev (from .../libgl1-mesa-dev_7.0.3~rc2-1ubuntu3_all.deb) ...
Selecting previously deselected package libglu1-mesa-dev.
Unpacking libglu1-mesa-dev (from .../libglu1-mesa-dev_7.0.3~rc2-1ubuntu3_i386.deb) ...
Selecting previously deselected package libglu1-xorg-dev.
Unpacking libglu1-xorg-dev (from .../libglu1-xorg-dev_1%3a7.3+10ubuntu10.2_all.deb) ...
Selecting previously deselected package libgsm1-dev.
Unpacking libgsm1-dev (from .../libgsm1-dev_1.0.12-1_i386.deb) ...
Selecting previously deselected package libimlib2.
Unpacking libimlib2 (from .../libimlib2_1.4.0-1ubuntu1_i386.deb) ...
Selecting previously deselected package libjpeg62-dev.
Unpacking libjpeg62-dev (from .../libjpeg62-dev_6b-14_i386.deb) ...
Selecting previously deselected package libltdl3-dev.
Unpacking libltdl3-dev (from .../libltdl3-dev_1.5.26-1ubuntu1_i386.deb) ...
Selecting previously deselected package libpng12-dev.
Unpacking libpng12-dev (from .../libpng12-dev_1.2.15~beta5-3_i386.deb) ...
Selecting previously deselected package libtiffxx0c2.
Unpacking libtiffxx0c2 (from .../libtiffxx0c2_3.8.2-7ubuntu3.1_i386.deb) ...
Selecting previously deselected package libtiff4-dev.
Unpacking libtiff4-dev (from .../libtiff4-dev_3.8.2-7ubuntu3.1_i386.deb) ...
Selecting previously deselected package libimlib2-dev.
Unpacking libimlib2-dev (from .../libimlib2-dev_1.4.0-1ubuntu1_i386.deb) ...
Selecting previously deselected package libogg-dev.
Unpacking libogg-dev (from .../libogg-dev_1.1.3-3ubuntu1_i386.deb) ...
Selecting previously deselected package libraw1394-dev.
Unpacking libraw1394-dev (from .../libraw1394-dev_1.3.0-2_i386.deb) ...
Selecting previously deselected package libsdl1.2-dev.
Unpacking libsdl1.2-dev (from .../libsdl1.2-dev_1.2.13-1ubuntu1_i386.deb) ...
Selecting previously deselected package libtheora-dev.
Unpacking libtheora-dev (from .../libtheora-dev_1.0~beta2-2_i386.deb) ...
Selecting previously deselected package libvorbis-dev.
Unpacking libvorbis-dev (from .../libvorbis-dev_1.2.0.dfsg-2_i386.deb) ...
Selecting previously deselected package quilt.
Unpacking quilt (from .../archives/quilt_0.46-4_all.deb) ...
Selecting previously deselected package texi2html.
Unpacking texi2html (from .../texi2html_1.78-1_all.deb) ...
Selecting previously deselected package libdc1394-13-dev.
Unpacking libdc1394-13-dev (from .../libdc1394-13-dev_1.1.0-5ubuntu1_i386.deb) ...
Setting up x11proto-core-dev (7.0.11-1) ...
Setting up libxau-dev (1:1.0.3-2) ...
Setting up libpthread-stubs0 (0.1-2) ...
Setting up libpthread-stubs0-dev (0.1-2) ...
Setting up libxdmcp-dev (1:1.0.2-2) ...
Setting up libxcb1-dev (1.1-1ubuntu1) ...
Setting up libxcb-xlib0-dev (1.1-1ubuntu1) ...
Setting up x11proto-input-dev (1.4.2-1) ...
Setting up x11proto-kb-dev (1.0.3-2ubuntu1) ...
Setting up xtrans-dev (1.0.4-1) ...
Setting up libx11-dev (2:1.1.3-1ubuntu2ja4) ...
Setting up x11proto-xext-dev (7.0.2-5ubuntu1) ...
Setting up libxext-dev (2:1.0.3-2build1) ...
Setting up libtimedate-perl (1.1600-9) ...
Setting up patch (2.5.9-4) ...
Setting up dpkg-dev (1.14.16.6ubuntu4) ...
Setting up html2text (1.3.2a-3build2) ...

Setting up gettext (0.17-2ubuntu1) ...

Setting up intltool-debian (0.35.0+20060710.1) ...
Setting up po-debconf (1.0.10) ...

Setting up debhelper (6.0.4ubuntu1) ...
Setting up diffstat (1.45-2) ...

Setting up zlib1g-dev (1:1.2.3.3.dfsg-7ubuntu1) ...
Setting up libfreetype6-dev (2.3.5-1ubuntu4.8.04.1) ...

Setting up libgif4 (4.1.6-4) ...

Setting up libgif-dev (4.1.6-4) ...
Setting up mesa-common-dev (7.0.3~rc2-1ubuntu3) ...
Setting up libgl1-mesa-dev (7.0.3~rc2-1ubuntu3) ...
Setting up libglu1-mesa-dev (7.0.3~rc2-1ubuntu3) ...
Setting up libglu1-xorg-dev (1:7.3+10ubuntu10.2) ...
Setting up libgsm1-dev (1.0.12-1) ...
Setting up libimlib2 (1.4.0-1ubuntu1) ...

Setting up libjpeg62-dev (6b-14) ...
Setting up libltdl3-dev (1.5.26-1ubuntu1) ...
Setting up libpng12-dev (1.2.15~beta5-3) ...
Setting up libtiffxx0c2 (3.8.2-7ubuntu3.1) ...

Setting up libtiff4-dev (3.8.2-7ubuntu3.1) ...

Setting up libimlib2-dev (1.4.0-1ubuntu1) ...

Setting up libogg-dev (1.1.3-3ubuntu1) ...
Setting up libraw1394-dev (1.3.0-2) ...
Setting up libsdl1.2-dev (1.2.13-1ubuntu1) ...

Setting up libtheora-dev (1.0~beta2-2) ...
Setting up libvorbis-dev (1.2.0.dfsg-2) ...
Setting up quilt (0.46-4) ...

Setting up texi2html (1.78-1) ...

Setting up libdc1394-13-dev (1.1.0-5ubuntu1) ...
Setting up libstdc++6-4.2-dev (4.2.4-1ubuntu3) ...
Setting up g++-4.2 (4.2.4-1ubuntu3) ...
Setting up g++ (4:4.2.3-1ubuntu6) ...

Setting up build-essential (11.3ubuntu1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
W: Duplicate sources.list entry http://ppa.launchpad.net hardy/main Packages (/var/lib/apt/lists/ppa.launchpad.net_reacocard-awn_ubuntu_dists_hardy_main_binary-i386_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net hardy/main Packages (/var/lib/apt/lists/ppa.launchpad.net_reacocard-awn_ubuntu_dists_hardy_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
(ME)@(Comp):~$ sudo apt-get install liblame-dev libfaad-dev libx264-dev libfaac-dev libxvidcore4-dev liba52-0.7.4 liba52-0.7.4-dev libdts-dev checkinstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
liba52-0.7.4 is already the newest version.
liba52-0.7.4 set to manually installed.
The following NEW packages will be installed:
  checkinstall liba52-0.7.4-dev libdts-dev libfaac-dev libfaad-dev liblame-dev
  libx264-dev libxvidcore4-dev
0 upgraded, 8 newly installed, 0 to remove and 16 not upgraded.
Need to get 1385kB of archives.
After this operation, 4039kB of additional disk space will be used.
Get:1 http://jp.archive.ubuntu.com hardy/universe checkinstall 1.6.1-5ubuntu1 [116kB]
Get:2 http://jp.archive.ubuntu.com hardy/universe liba52-0.7.4-dev 0.7.4-11ubuntu1 [43.7kB]
Get:3 http://jp.archive.ubuntu.com hardy/universe libdts-dev 0.0.2-svn-2ubuntu1 [192kB]
Get:4 http://jp.archive.ubuntu.com hardy/multiverse libfaac-dev 1.26-0.1ubuntu1 [63.6kB]
Get:5 http://jp.archive.ubuntu.com hardy-updates/universe libfaad-dev 2.6.1-2ubuntu0.1 [205kB]
Get:6 http://jp.archive.ubuntu.com hardy/multiverse liblame-dev 3.97-0.0 [217kB]
Get:7 http://jp.archive.ubuntu.com hardy/multiverse libx264-dev 1:0.svn20071224-0.0ubuntu1 [289kB]
Get:8 http://jp.archive.ubuntu.com hardy/multiverse libxvidcore4-dev 2:1.1.2-0.1ubuntu3 [259kB]
Fetched 1385kB in 3s (348kB/s)           
Selecting previously deselected package checkinstall.
(Reading database ... 105420 files and directories currently installed.)
Unpacking checkinstall (from .../checkinstall_1.6.1-5ubuntu1_i386.deb) ...
Selecting previously deselected package liba52-0.7.4-dev.
Unpacking liba52-0.7.4-dev (from .../liba52-0.7.4-dev_0.7.4-11ubuntu1_i386.deb) ...
Selecting previously deselected package libdts-dev.
Unpacking libdts-dev (from .../libdts-dev_0.0.2-svn-2ubuntu1_i386.deb) ...
Selecting previously deselected package libfaac-dev.
Unpacking libfaac-dev (from .../libfaac-dev_1.26-0.1ubuntu1_i386.deb) ...
Selecting previously deselected package libfaad-dev.
Unpacking libfaad-dev (from .../libfaad-dev_2.6.1-2ubuntu0.1_i386.deb) ...
Selecting previously deselected package liblame-dev.
Unpacking liblame-dev (from .../liblame-dev_3.97-0.0_i386.deb) ...
Selecting previously deselected package libx264-dev.
Unpacking libx264-dev (from .../libx264-dev_1%3a0.svn20071224-0.0ubuntu1_i386.deb) ...
Selecting previously deselected package libxvidcore4-dev.
Unpacking libxvidcore4-dev (from .../libxvidcore4-dev_2%3a1.1.2-0.1ubuntu3_i386.deb) ...
Setting up checkinstall (1.6.1-5ubuntu1) ...
Setting up liba52-0.7.4-dev (0.7.4-11ubuntu1) ...
Setting up libdts-dev (0.0.2-svn-2ubuntu1) ...
Setting up libfaac-dev (1.26-0.1ubuntu1) ...
Setting up libfaad-dev (2.6.1-2ubuntu0.1) ...
Setting up liblame-dev (3.97-0.0) ...
Setting up libx264-dev (1:0.svn20071224-0.0ubuntu1) ...
Setting up libxvidcore4-dev (2:1.1.2-0.1ubuntu3) ...
(ME)@(Comp):~$ apt-get source ffmpeg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Need to get 2634kB of source archives.
Get:1 http://jp.archive.ubuntu.com hardy-updates/main ffmpeg 3:0.cvs20070307-5ubuntu7.1 (dsc) [1325B]
Get:2 http://jp.archive.ubuntu.com hardy-updates/main ffmpeg 3:0.cvs20070307-5ubuntu7.1 (tar) [2593kB]
Get:3 http://jp.archive.ubuntu.com hardy-updates/main ffmpeg 3:0.cvs20070307-5ubuntu7.1 (diff) [39.4kB]
Fetched 2634kB in 6s (412kB/s)                                                 
gpg: Signature made Thu Jul 24 06:36:01 2008 JST using DSA key ID 17063E6D
gpg: Can't check signature: public key not found
dpkg-source: extracting ffmpeg in ffmpeg-0.cvs20070307
dpkg-source: unpacking ffmpeg_0.cvs20070307.orig.tar.gz
dpkg-source: applying ./ffmpeg_0.cvs20070307-5ubuntu7.1.diff.gz
(ME)@(Comp):~$ cd ffmpeg-*/
(ME)@(Comp):~/ffmpeg-0.cvs20070307$ ./configure --enable-liba52 --disable-debug --enable-libfaad --enable-libfaac --enable-gpl --enable-amr_nb --enable-amr_wb --enable-x264 --enable-xvid --enable-libdts --enable-pthreads --enable-libvorbis --enable-pp --enable-libtheora --enable-libogg --enable-libgsm --disable-debug --enable-shared --prefix=/usr
install prefix            /usr
source path               /home/(ME)/ffmpeg-0.cvs20070307
C compiler                gcc
make                      make
.align is power-of-two    no
ARCH                      x86_32 (generic)
big-endian                no
MMX enabled               yes
CMOV enabled              no
CMOV is fast              no
gprof enabled             no
debug symbols             no
strip symbols             yes
optimize                  yes
static                    yes
shared                    yes
postprocessing support    yes
software scaler enabled   no
video hooking             yes
Imlib2 support            yes
FreeType support          yes
network support           yes
IPv6 support              yes
threading support         pthreads
SDL support               yes
Sun medialib support      no
AVISynth enabled          no
liba52 support            yes
liba52 dlopened           no
libdts support            yes
libfaac enabled           yes
libfaad enabled           yes
faadbin enabled           no
libgsm enabled            yes
libmp3lame enabled        no
libnut enabled            no
libogg enabled            yes
libtheora enabled         yes
libvorbis enabled         yes
x264 enabled              yes
XviD enabled              yes
zlib enabled              yes
AMR-NB float support      yes
AMR-NB fixed support      no
AMR-WB float support      yes
AMR-WB IF2 support        no
License: GPL
Creating config.mak and config.h...
(ME)@(Comp):~/ffmpeg-0.cvs20070307$ 

``` Whew, long. At the next part, it says to get the latest AMR NB & WB float versions, from the respective links, but here's the problem: On each page, there are TWO files with the same date, and unzipping both from either link shows me they seem to be the same thing (both have WB in the .doc titles, not NB)? Also, the files from BOTH pages seem to be this WB version, as all 4 latest files from both links together say "wide band" in the .doc files!

I then found this page, listing that there are "float" & "fixed point" types for BOTH NB & WB AMR. [http://www.irisa.fr/texmex/people/dufouil/ffmpegdoxy/libavcodec_2amr_8c.html](http://www.irisa.fr/texmex/people/dufouil/ffmpegdoxy/libavcodec_2amr_8c.html) How am I supposed to know which is which, which one to extract (ie: actually need, maybe both?), and where either are- since all 4 files at both 2 links seem to all be WB type SOMETHING.

I am hopelessly lost, and while I can follow the typical "magic lines of code" schpeal at this point, I am over my head! HOW, and can I continue? I need some real help here, or I'm afraid I'll break my ffmpeg codec (?) if I do anything else.

BTW, THE FORMER page is an Ubuntu WIKI? Are all things linux SUPPOSED to be this confusing? I'm half intellegent (I think!), and I have no idea what the hell is going on. I just wanted to download a video in a format I can use!

Can anyone help?

---

### Post by dhughes on 2008-11-26
I'm not really sure what to say, I use ffmpeg but when I installed it I just went to Synaptic and marked it for installation.

 FYI there is some sort of bug in the latest version of ffmpeg where it fails, I forget the error message, and I thought I saved the reason in a text file so I could remember why but I can't find the files if it exists.

  Just in case: [http://ubuntuforums.org/showthread.php?t=788047](http://ubuntuforums.org/showthread.php?t=788047)

---

### Post by BastardNamban on 2008-11-26
Thanks for the heads up. If I can finish my installation, I'll fix that too!

Anyone have any ideas? Maybe, god forbid, somewhere there is a complete working version of ffmpeg already that I could install instead? I'd rather not deal with the annoying stuff I started in the first post, but I'm still stuck halfway through!

---

### Post by Dedoimedo on 2008-11-26
Why don't you try installing ffpmeg by using sudo apt-get install ffmpeg or via Synaptic? Always go for simple solutions first.

BTW, if you need help using ffmpeg, do tell.

Dedoimedo

---

### Post by BastardNamban on 2008-11-26
According to Download helper's site ([http://www.downloadhelper.net/conversion-manual.php](http://www.downloadhelper.net/conversion-manual.php)), FFMPEG Doesn't seem to natively come able to do a lot of conversions because of legal reasons, so I followed the link where they said to compile it with more options.

So if I take your advice, would I be able to convert .flv to .avi using it, and more, or is it indeed restricted in what in comes with? I'm a bit confused. If I should just get rid of it, and get it again through Synaptic (I understand how to use that, at least), will it come with everything I need?

---

### Post by Dedoimedo on 2008-11-26
Hello,
Sure, I do it all the time. Not only that, I'm going to post a few multimedia editing tutorials in a few days, so stay tuned.
Dedoimedo

---

### Post by BastardNamban on 2008-11-26
Ok, so I found the ffmpeg-0.cvs20070307 folder under /usr/, and just deleted it. Something tells me I shouldn't have done that... I wanted a totally fresh install.

First I reinstalled it through Synaptic- but I couldn't find it. I uninstalled it through Synaptic. I went directly to terminal and did ```
sudo apt-get install ffmpeg
``` and all I got was some folder in /usr/lib/gstreamer-0.10, with a file called libgstffmpeg.so, among other things. Something tells me I F*ed up. How am I supposed to configure this to work with Download Helper in Firefox now? It only lets me set the value for ffmpeg as the original place which I already cleared!

I still have that ffmpef 0.cvs20070307 folder, along with ffmpeg_0.cvs20070307.orig.tar.gz, ffmpeg_0.cvs20070307-5ubuntu7.1.diff.gz, & ffmpeg_0.cvs20070307-5ubuntu7.1.diff.gz all in my trash bin, but if restoring those has some part in this, I can't remember all their locations, and there seems to be no restore function in linux like XP- so I have to know where I deleted it from to send it back! No restore in trash, and no undo command like CTRL+Z that I can find. On another note, I accidentally downloaded that video, in .flv, and found it plays in totem! I'm surprised- XP could never do .flv, at least not that I could find. But I still want to finish this buisness properly, to get .avi, for my Zen Vision.

So what now?

---

### Post by JohnFH on 2008-11-26
Can you post the output of the following commands?

```
sudo apt-get install ffmpeg
```
```
dpkg -l | grep ffmpeg
```
```
ffmpeg -version
```

---

### Post by BastardNamban on 2008-11-26
Sure.
```
(ME)@(COMP):~$ sudo apt-get install ffmpeg
[sudo] password for (ME): 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ffmpeg is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
(ME)@(COMP):~$ dpkg -l | grep ffmpeg
ii  ffmpeg                                     3:0.cvs20070307-5ubuntu7.1        multimedia player, server and encoder
ii  gstreamer0.10-ffmpeg                       0.10.3-6                          FFmpeg plugin for GStreamer
ii  libavcodec1d                               3:0.cvs20070307-5ubuntu7.1        ffmpeg codec library
ii  libavformat1d                              3:0.cvs20070307-5ubuntu7.1        ffmpeg file format library
ii  libavutil1d                                3:0.cvs20070307-5ubuntu7.1        ffmpeg utility library
ii  libpostproc1d                              3:0.cvs20070307-5ubuntu7.1        ffmpeg video postprocessing library
ii  libswscale1d                               3:0.cvs20070307-5ubuntu7.1        ffmpeg video scaling library
(ME)@(COMP):~$ ffmpeg -version
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 23 2008 22:38:24, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
ffmpeg      SVN-rUNKNOWN
libavutil   3212032
libavcodec  3352064
libavformat 3344896
(ME)@(COMP):~$ 

```

Does this help?

---

### Post by JohnFH on 2008-11-26
Ok thanks.  It looks as if ffmpeg is installed ok.  I'm not quite understanding the problem though.  Do you get an error trying to use it?

Try the following (and post the results):
The following command will double check that your current installation of ffmpeg supports flv files as input.  
```
ffmpeg -formats 2> /dev/null | grep flv
```

The following command will convert a .flv file to .avi file.  
```
ffmpeg -i <NameOfFlvMovieFile>.flv output.avi
```

The following command will also convert from .flv to .avi, but will give you more control over the quality.
```
ffmpeg -i <NameOfFlvMovieFile>.flv -b 1000k -ab 128k output.avi
```

-b specifies the video bitrate.
-ab specifies the audio bitrate.
ffmpeg will know to convert to avi format because of the filename output.avi.
If your .flv file is huge (unlikely since you downloaded it?) then you might want to only convert part of it to start with.  To convert part of it, use the -t option to specify the duration in seconds.

The link you gave in the first post looks quite overly complicated so I'm not surprised you felt out of your depth after only a few days in Ubuntu!  To answer your original question - no (no way in fact), it's not usually that complicated at all!  The manpage for ffmpeg may look daunting at first with all the options it has, but it's actually very helpful and you won't need to know most of the options anyway as a lot of them are specific to different codecs.  I don't think you need to compile ffmpeg and that link may be a bit misleading especially for beginners, so definitely try using the ffmpeg version you have installed now (see steps above), without any further compilation.  If that doesn't work ... well let's see if it does first ...

Hope that helps.

---

### Post by BastardNamban on 2008-11-27
Thank you! I get the feeling there is still something I don't understand, though... I tried coding the first two: ```
(ME)@(COMP):~$ ffmpeg -formats 2> /dev/null | grep flv
 DE flv             flv format
 DEVSD  flv
(ME)@(COMP):~$ ffmpeg -i <Retracting Geneva Tooth Gear>.flv output.avi
bash: Retracting: No such file or directory
(ME)@(COMP):~$ ffmpeg -i <Retracting Geneva Tooth Gear>.flv output.avi
bash: Retracting: No such file or directory
(ME)@(COMP):~$ ffmpeg -i <Retracting Geneva Tooth Gear>.flv output.avi
bash: Retracting: No such file or directory
(ME)@(COMP):~$ ffmpeg -i <Retracting_Geneva_Tooth_Gear>.flv output.avi
bash: Retracting_Geneva_Tooth_Gear: No such file or directory
(ME)@(COMP):~$ sudo ffmpeg -i <Retracting_Geneva_Tooth_Gear>.flv output.avi
bash: Retracting_Geneva_Tooth_Gear: No such file or directory
``` I'm wondering if I don't understand naming conventions? I'm doing this from terminal, because as far as I understand, ffmpeg is not an "openable" program- it's something that my computer uses to achieve an end, not a direct executable file.

I'm RELIEVED that the first link was indeed ridiculous not just to me. I'm really sorry, but it seems like I still don't seem to understand something involved in this. I guess I should just give up, at this point it's just embarrassing to keep saying "why can't I make this work", when I feel like all the reading I'm doing should have told me how to "get" it by now. Thanks.

---

### Post by JohnFH on 2008-11-27
Don't give up, you're just about there!  I should have been more clear about how to specify the filename.  If there are spaces in the filename then you need to put the filename in quotes or use an escape character before the space, so the following two commands should both work.
```
ffmpeg -i Retracting\ Geneva\ Tooth\ Gear.flv output.avi
```
```
ffmpeg -i "Retracting Geneva Tooth Gear.flv" output.avi
```
It might take a while but it will show you the progress as it converts the file.  When it's finished use a movie player to play output.avi.  Either select it from the menu or type the command in the terminal to start the movie player.  I use mplayer because I'm used to the shortcut keys it uses but have a look in the menu to see what multimedia applications you've got installed already.
```
mplayer output.avi
```
It can be a lot to take in at first because it's not something you're used to, but stick with it.  I don't think it will take you long to get used to it.
Glad I can help.

---

### Post by PocketDog on 2008-11-27
...or get [http://vixy.net](http://vixy.net) to fetch the .flv and convert it for you ;-)

---

### Post by BastardNamban on 2008-11-27
Ah, I see. I tried both, with no success :confused: ```
(ME)@(COMP):~$ ffmpeg -i Retracting\ Geneva\ Tooth\ Gear.flv output.avi
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 23 2008 22:38:24, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
Retracting Geneva Tooth Gear.flv: I/O error occured
Usually that means that input file is truncated and/or corrupted.
(ME)@(COMP):~$ ffmpeg -i "Retracting Geneva Tooth Gear.flv" output.avi
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 23 2008 22:38:24, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
Retracting Geneva Tooth Gear.flv: I/O error occured
Usually that means that input file is truncated and/or corrupted.

``` I did rename the file after I downloaded it, as it was originally something in French, of no use to me. It's a unique mechanical use of a geneva gear, and I renamed it to my language. Could that have anything to do with it?

---

### Post by JohnFH on 2008-11-27
> **BastardNamban said:**
> I did rename the file after I downloaded it, as it was originally something in French, of no use to me. It's a unique mechanical use of a geneva gear, and I renamed it to my language. Could that have anything to do with it?
What was the original name?  Are you sure it was a .flv file?  Renaming it shouldn't make a difference.  Try downloading it again if that's an option for you.

---

### Post by BastardNamban on 2008-11-28
Ok, I re-downloaded the original file, and tried the same thing- same error messages. It is indeed an .flv file, as it downloaded. I don't know why it won't convert either.

Are you sure ffmpeg is capable of doing this, without some kind of special update? I used to have a program in XP called total video converter, and that almost always worked. I wonder, since this seems like it refuses to work, could you or anyone else recommend a separate program that I can open and use to convert videos? My Zen Vision M has problems displaying things other than .avi or mpeg4, so I need to convert videos rather often:(

Edit PS: My original video download that I renamed works fine in totem, as a .flv, but the new downloaded file of the same thing, also an .flv but with the original name, doesn't play! I tried renaming that one, and got the same error both times- "An error occurred- Gstreamer encountered a general library supporting error".

Does this give a clue to anything? I am sorry I am so inept, I cannot figure out why this is giving me so much crap.

---

### Post by JohnFH on 2008-11-28
I'm not sure what the problem is with your file to be honest.

I'm certain ffmpeg can convert it.  I just downloaded a flv file and converted it to .avi and also .mpg, using ffmpeg and then play the files using mplayer, all without a problem.

Have a look at these links - maybe something in them will help.

[http://www.ubuntugeek.com/convert-flv-google-videos-to-mpg-using-ffmpeg.html]("http://www.ubuntugeek.com/convert-flv-google-videos-to-mpg-using-ffmpeg.html")

[http://blog.mypapit.net/2006/12/howto-convert-flv-youtube-google-video-files-to-avi-in-linux.html]("http://blog.mypapit.net/2006/12/howto-convert-flv-youtube-google-video-files-to-avi-in-linux.html")

---

### Post by mc4man on 2008-11-28
If it's possible can you provide a link to the flv in question?

---

### Post by cariboo on 2008-11-28
Sometimes doing things the hard way is good for you, but why not use avidemux to convert the file from .flv to .avi. I use it all the time and have never run into any problems. Avidemux is in the repositories and you can use Add/Remove Programs, Synaptic Package Manager and of course the command line to install it.

Make sure you have all the repositories checked in System-->Administration-->Software Sources, and if you plan on doing a lot of audio/video conversions, it may be worth your while to enable the Medibuntu repositories. Follow the instructions here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Make sure you scroll down and add gpg key.

Jim

---

### Post by BastardNamban on 2008-11-29
Here is a link to the video in question: Cinématique d'une dent rétractable, on this page:[http://www.tellwatch.com/media.php?menu=80](http://www.tellwatch.com/media.php?menu=80)

If you're wondering what the hell this is, it's a very specialized Parametric CAD program used exclusively in the watch industry, called TellWatch. I'm debating whether I should invest in this or not, studying to be a watchmaker.

Linux doesn't seem to have any parametric CAD programs, BTW.

PS: I agree with the hard way, most of the time, as it gives superior results. But when the hard way, or any way at all isn't working, you're screwed. I will try some of your new sugguestions, and see what happens, then report. Thank you so far everyone!

---

### Post by JohnFH on 2008-11-29
Ah, I see!  It may look like a .flv by the name but what you are getting in the browser is a php script that is playing the flv file in a flash application.

When you play one of the movies in the browser, the address is something like:
"http://www.tellwatch.com/video.php?file=dl/video/cine_chrono_jmb.flv&dl_id=35&vid_x=320&vid_y=240"

The ?file=...flv& bit is picking up the name of the flv file on the server and playing it directly so when you download it from the browser you just get the flash application.  

To get round it, add [http://www.tellwatch.com/](http://www.tellwatch.com/) to the file paramter bit in the address (ie., the ?file=...& bit) of the flash window, so in this case the full address would be:

[http://www.tellwatch.com/dl/video/cine_chrono_jmb.flv]("http://www.tellwatch.com/dl/video/cine_chrono_jmb.flv")

Now type that into the browser and save it to disk.  Now you have the proper flv file which you can easily convert using ffmpeg.

I've uploaded one of the files (converted to avi using ffmpeg) to my website:

[http://www.johnhawthorne.co.uk/cine_chrono_jmb.avi]("http://www.johnhawthorne.co.uk/cine_chrono_jmb.avi")

---

### Post by BastardNamban on 2008-11-30
I'm glad we figured this out! Unfortunately, using the link you gave did not work- I downloaded that file fine, and used the commands you gave earlier, but no good. Example:```
(ME)@(COMP):~$ ffmpeg -i cine\ chrono\ jmb.flv output.avi
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 23 2008 22:38:24, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
cine chrono jmb.flv: I/O error occured
Usually that means that input file is truncated and/or corrupted.

``` So what now? I did the same thing with the file I originally wanted, and both download ok using your naming trick, but they both gave me the same error message!

Something has got to be wrong with my ffmpeg.

---

### Post by JohnFH on 2008-11-30
Looks like you are not using the right filename.  Type 'ls' to see what files are currently there and make sure you use the same filename as listed.  In this case, use underscore (_) instead of a space.

Another good tip is to use filename completion.  In the terminal (usually at least), if you start typing a filename and you press <tab> button half way through then the filename will be completed for you if the partial name matches only one file.  If the partially typed filename matches more than one file, then pressing <tab> twice quickly will show the possible matches.  If you already know all this then tell me to shut up.  It's just that I use tab completion a lot and it would help here.

Anyway do this:
```
ls -lh *.flv
```
Hopefully you will now see the filename of the file you want to convert.  Now type this:
```
ffmpeg -i cine_chrono_jmb.flv output.avi
```
Hopefully it will now work.

---

### Post by BastardNamban on 2008-11-30
I got to hand it to ya mate, you have incredible patience to keep trying to help me! Thanks :embarrassed:

I will not tell you to shut up- I had no idea about the tab thing in terminal- that is sweet. Bad news though- the file on my desktop is named exactly that- cine_chrono_jmb.flv, no spaces- I left it in the original underscores.```
(ME)@(COMP):~$ ffmpeg -i cine_chrono_jmb.flv output.avi
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 23 2008 22:38:24, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
cine_chrono_jmb.flv: I/O error occured
Usually that means that input file is truncated and/or corrupted.
shogun@Valhalla:~$ ls -lh *.flv
ls: cannot access *.flv: No such file or directory
(ME)@(COMP):~$ ls
Desktop    Examples  Pictures  Templates  Web Articles
Documents  Music     Public    Videos
(ME)@(COMP):~$ ls -lh
total 40K
drwxr-xr-x  7 shogun shogun 4.0K 2008-12-01 02:57 Desktop
drwxr-xr-x 11 shogun shogun 4.0K 2008-11-23 21:53 Documents
lrwxrwxrwx  1 shogun shogun   26 2008-11-20 22:54 Examples -> /usr/share/example-content
drwxr-xr-x 42 shogun shogun 4.0K 2008-12-01 03:34 Music
drwxr-xr-x 29 shogun shogun  12K 2008-11-29 16:15 Pictures
drwxr-xr-x  2 shogun shogun 4.0K 2008-11-20 23:01 Public
drwxr-xr-x  2 shogun shogun 4.0K 2008-11-20 23:01 Templates
drwxr-xr-x  2 shogun shogun 4.0K 2008-12-01 01:04 Videos
drwxr-xr-x 18 shogun shogun 4.0K 2008-11-23 21:41 Web Articles

``` I cannot believe this is giving me so much !#$%, I checked the properties of each supposed now REAL .flv, and it says they are flash files. Specifically: "TYPE- Flash Video. MIME TYPE- application/x-flash-video"
Perhaps this explains it? I downloaded them using your site renaming method, and it did indeed just bring up a download prompt, instead of the site, but it looks like they still aren't .flvs. I can't explain why, I have been doing everything you said.

It may seem that I am as dumb as a stone, but I assure you, I'm not. That's why I don't understand this either. I'm ready to say F*CK FFMPEG, I don't need it, and to get some kind of stand-alone converter program I can open with a gui.:mad:](*,):-k

---

### Post by JohnFH on 2008-11-30
When you see this error:

cine_chrono_jmb.flv: I/O error occured

it means that it couldn't find that file.  The output of ls -lh does not contain the flv file so we're not in the right place.  When you download things where do they go?  Do they appear on the desktop?  If so, type this:
```
cd Desktop
ls -lh
```
Do you see the flv file now in the list?

---

### Post by BastardNamban on 2008-12-01
It shows up. ```
shogun@Valhalla:~$ cd Desktop
shogun@Valhalla:~/Desktop$ ls -lh
total 527M
-rw-r--r--  1 shogun shogun  37K 2008-12-01 06:09 Atlas Rope Ascender.jpg
drwxr-xr-x  2 shogun shogun 4.0K 2008-11-27 10:50 Beat Pharmacy - Constant Pressure (2006)
-rw-r--r--  1 shogun shogun 8.8M 2008-12-01 01:13 cine_chrono_jmb.flv
-rw-r--r--  1 shogun shogun  39K 2008-12-01 05:16 Claire Watkins Needle Sculpture 01.jpg
-rw-r--r--  1 shogun shogun  67K 2008-12-01 05:17 Claire Watkins Needle Sculpture 02.jpg
-rw-r--r--  1 shogun shogun 171M 2008-11-22 17:18 [DB]_Bleach_195_[B9E1F112].avi
-rw-r--r--  1 shogun shogun 171M 2008-11-26 21:21 [DB]_Bleach_196_[3FDE9706].avi
-rw-r--r--  1 shogun shogun 170M 2008-11-22 17:19 [DB]_Naruto_Shippuuden_085_[5962F2C8].avi
drwxr-xr-x  5 shogun shogun 4.0K 2008-12-01 22:10 Debito Hails The End Of Bush_files
-rw-r--r--  1 shogun shogun  65K 2008-12-01 22:10 Debito Hails The End Of Bush.html
-rw-r--r--  1 shogun shogun 3.1M 2008-12-01 01:18 dent retract.flv
drwxr-xr-x  2 shogun shogun 4.0K 2008-11-25 04:27 Emerald Themes
drwxr-xr-x  2 shogun shogun 4.0K 2008-11-28 01:06 Ethics & Philosophy Of Watch Restoration_files
-rw-r--r--  1 shogun shogun  17K 2008-11-28 01:06 Ethics & Philosophy Of Watch Restoration.htm
-rw-r--r--  1 shogun shogun  30K 2008-12-01 20:28 In Praise Of Idleness by Bertrand Russell.html
-rw-r--r--  1 shogun shogun 190K 2008-11-29 02:49 JSCH.jpg
drwxrwxrwx 21 shogun shogun 4.0K 2008-11-25 04:19 LINUX
-rw-r--r--  1 shogun shogun  71K 2008-12-01 05:07 Magnetic Prop Balancer.gif
drwxr-xr-x  4 shogun shogun 4.0K 2008-12-01 06:25 Magnetic Sphere Levitation_files
-rw-r--r--  1 shogun shogun 1.1K 2008-12-01 06:27 Magnetic Sphere Levitation.html
-rw-r--r--  1 shogun shogun 348K 2008-12-01 23:20 Michael Dyber Cut Smithsonian Ametrine.png
-rw-r--r--  1 shogun shogun 5.5K 2008-12-01 05:05 Mystery Motor.gif
-rw-r--r--  1 shogun shogun  37K 2008-12-01 05:01 NdFeB Magnet Sculpture.jpg
drwxr-xr-x  2 shogun shogun 4.0K 2008-12-01 05:47 Rotational Levitation With Magnets Patented_files
-rw-r--r--  1 shogun shogun 7.8K 2008-12-01 05:47 Rotational Levitation With Magnets Patented.html
-rw-r--r--  1 shogun shogun 375K 2008-12-01 23:20 Smithsonian Eye Of Horus Ametrine.png
-rw-r--r--  1 shogun shogun 292K 2008-11-26 22:05 The Pirate Bay 5 Years.jpg
-rw-r--r--  1 shogun shogun 1.6M 2008-11-30 18:23 The Public Domain- Enclosing The Commons Of The Mind by James Boyle.pdf
drwxr-xr-x  2 shogun shogun 4.0K 2008-12-01 02:57 Watch & Clock Escapements- A Complete Study_files
-rw-r--r--  1 shogun shogun 458K 2008-12-01 02:57 Watch & Clock Escapements- A Complete Study.htm
shogun@Valhalla:~/Desktop$ 

``` But using your past conversion parsing, it still REFUSES TO CONVERT.

Honestly, whatever I am doing/is missing from my system that keeps me from making this work, I've had it. It's been nearly a week. I just want to quit, say F*** IT, and find a video converter program. Doing this stuff from terminal is BEYOND ANNOYING.

And yeah, I know, I gotta clean up my desktop.

---

