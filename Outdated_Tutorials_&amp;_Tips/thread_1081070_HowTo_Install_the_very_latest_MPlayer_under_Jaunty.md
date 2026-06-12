---
title: "HowTo: Install the very latest MPlayer under Jaunty Jackalope"
date: 2009-02-26
forum: Outdated Tutorials &amp; Tips
---

### Post by andrew.46 on 2009-02-26
======================
**Introduction**
=====================

This guide demonstrates how to successfully compile the subversion MPlayer under Jaunty Jackalope. It is intended for use by *advanced users* only. If this advanced guide is really not what you are after perhaps you could try the very popular: [Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683") where Nathan will look after you.

========================
**Some Preparation**
========================

A degree of preparation is involved before actually compiling MPlayer. Steps involved are:

[LIST=1]
[*]Compiling the latest x264 libraries
[*]Compiling the latest live555 libraries
[*]Compiling the latest libopencore-amr libraries
[*]Download and install the required dev files
[/LIST]

First step is to download and compile the latest x264 libraries:

-----------------
**x264**
-----------------

Note that x264 is required so MEncoder can encode/transcode to the h264 format, MPlayer playback does not actually require these files. The x264 package included with Jaunty is a little newer than previous offerings, in fact a snapshot from December 30th, 2008, but it is still a good idea to download and compile your own. I would also *strongly* advise that all older versions of x264 are removed from your system before installing the newer version. Some software tools are required first:

```

$ sudo apt-get install build-essential checkinstall gpac libgpac-dev git-core yasm

```

On a fresh system, which is how I test this guide, this is a download of about 23 megs. The next few steps download the x264 libraries from git and then compile, package and install them:

```

$ cd $HOME
$ git clone git://git.videolan.org/x264.git
$ cd x264
$ ./configure --prefix=/usr --enable-shared
$ make
$ sudo checkinstall --fstrans=no --install=yes --pakdir "$HOME/Desktop" \
--maintainer "$USER" --pkgname=x264 --pkgversion "1:0.svn`date +%Y%m%d`-0.0ubuntu1" \
--backup=no --deldoc=yes --deldesc=yes --delspec=yes --gzman --default
$ make distclean

```

Return here from time to time to update x264 by using the command 'git up' from the source directory. Next to install the Live555 libraries:

------------------
**Live555**
------------------

Jaunty ships with quite an old version of the Live555 libraries which are required for some streaming broadcasts. The Ubuntu version in fact dates from July 25th, 2008, so we will install a much newer version:

```

$ cd $HOME
$ wget http://www.live555.com/liveMedia/public/live555-latest.tar.gz
$ tar xvf live555-latest.tar.gz
$ cd live
$ ./genMakefiles linux
$ make
$ sudo cp -r $HOME/live /usr/lib

```

Live555 is updated quite frequently so it may pay to return here from time to time to update. Simply repeat the process after removing the previous libraries at /usr/lib/live. Next to compile the latest libopencore-amr libraries:

------------------
**libopencore-amr**
------------------

The svn MPlayer has switched to Open Source amr libraries and I note that for Jaunty there is no Medibuntu package. No problems we will roll our own:

```

$ cd $HOME
$ wget http://transact.dl.sourceforge.net/project/opencore-amr/opencore-amr/0.1.2/opencore-amr-0.1.2.tar.gz
$ tar xvf opencore-amr-0.1.2.tar.gz
$  cd opencore-amr-0.1.2/
$ ./configure --prefix=/usr
$ make
$ sudo checkinstall --fstrans=no --install=yes --pakdir "$HOME/Desktop" \
--maintainer "$USER" --pkgname="libopencore-amr" --pkgversion="0.1.2"  \
--backup=no --deldoc=yes --deldesc=yes --delspec=yes --gzman --default
$ make distclean

```

Next to install the required dev files:

------------------
**The dev files**
------------------

Ubuntu is not a particularly rich compiling environment so to give MPlayer extra functionality we need to install a truckload of dev files and in fact you will be downloading about 30 megs of files on a fresh system. Load these into a terminal and then make yourself a cup of tea while they are downloading and installing:

```

$ sudo apt-get install debhelper em8300-headers gawk gettext html2text \
intltool-debian ladspa-sdk libaa1-dev libasound2-dev libatk1.0-dev libaudio-dev \
libaudio2 libaudiofile-dev libavahi-client-dev libavahi-common-dev libcaca-dev \
libcairo2-dev libcdparanoia-dev libcelt0 libdbus-1-dev libdbus-glib-1-dev libdirectfb-dev \
libdirectfb-extra libdts-dev libdv4-dev libenca-dev libenca0 libesd0-dev libexpat1-dev \
libfaac-dev libfaac0 libffado0 libfontconfig1-dev libfreebob0 libfreetype6-dev \
libfribidi-dev libggi-target-x libggi2 libggi2-dev libggimisc2 libggimisc2-dev \
libgif-dev libgii1 libgii1-dev libgii1-target-x libgl1-mesa-dev libglib2.0-dev \
libglu1-mesa-dev libgtk2.0-dev libice-dev libjack-dev libjack0 libjpeg62-dev \
liblzo-dev liblzo1 liblzo2-2 liblzo2-dev libmad0-dev libmail-sendmail-perl \
libmp3lame-dev libmp3lame0 libmpcdec-dev libmpcdec3 libncurses5-dev libogg-dev \
libopenal-dev libopenal1 libpango1.0-dev libpixman-1-dev libpng12-dev libpopt-dev \
libpthread-stubs0 libpthread-stubs0-dev libpulse-dev libpulse-mainloop-glib0 \
libsdl1.2-dev libslang2-dev libsm-dev libsmbclient-dev libspeex-dev libsvga1 \
libsvga1-dev libsys-hostname-long-perl libsysfs-dev libtheora-dev libtwolame-dev \
libtwolame0 libvorbis-dev libx11-dev libxau-dev libschroedinger-dev libstdc++5  \
libxcb-render-util0-dev libxcb-render0-dev libxcb1-dev libxcomposite-dev \
libxcursor-dev libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev \
libxi-dev libxinerama-dev libxml++2.6-2 libxrandr-dev libxrender-dev libxt-dev \
libxv-dev libxvidcore4-dev libxvmc-dev libxxf86dga-dev libxxf86vm-dev mesa-common-dev \
po-debconf sharutils x11proto-composite-dev x11proto-core-dev x11proto-damage-dev \
x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev \
x11proto-render-dev x11proto-video-dev x11proto-xext-dev x11proto-xf86dga-dev \
x11proto-xf86vidmode-dev x11proto-xinerama-dev xtrans-dev zlib1g-dev \
liboil0.3-dev libcddb2-dev

```

This concludes the preparatory work, now to start installing MPlayer itself:

======================
**Installing MPlayer**
======================

Again the actual installation of MPlayer requires a couple of steps:

[LIST=1]
[*]Install the codecs
[*]Source a font
[*]Download and compile the svn MPLayer
[/LIST]

First for the codecs:

-------------------------
**Install the codecs**
-------------------------

The following commands downloads a codec pack of about 13 megs suitable for 32bit systems, decompresses it and places it in the appropriate location:

```

$ cd $HOME
$ wget http://www.mplayerhq.hu/MPlayer/releases/codecs/all-20071007.tar.bz2
$ sudo mkdir -pv /usr/lib/codecs
$ tar xjvf all-20071007.tar.bz2
$ sudo cp -v $HOME/all-20071007/* /usr/lib/codecs

```

I am not qualified to comment too much on 64bit systems but I believe that these systems require a different quite minimal set of codecs. Unfortunately I know next to nothing about 64bit systems and their requirements but there are some 64bit users following this thread that may be able to help out.
 
But now to source a font for MPlayer:

--------------------
**Source a Font**
--------------------

Mplayer needs to know the location of a TrueType Font to show movie subtitles. This can be selected from the commandline but more traditionally a symlink is created to the font of your choice:

```

$ mkdir -v $HOME/.mplayer
$ ln -sv /usr/share/fonts/truetype/ttf-bitstream-vera/Vera.ttf ~/.mplayer/subfont.ttf

```

Feel free to choose your own font but this will certainly do to start with. Now to download and compile the svn MPlayer:

----------------------------------------
**Download and compile the svn mplayer**
----------------------------------------

Finally after all of the preparation it is time to download Mplayer from the subversion repository, compile it and use checkinstall to create a package and install it:

```

$ sudo apt-get install subversion
$ cd $HOME
$ svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer
$ cd $HOME/mplayer
$ ./configure --confdir=/etc/mplayer
$ make
$ sudo checkinstall -D --install=yes --fstrans=no --pakdir "$HOME/Desktop" \
--pkgname mplayer --backup=no --deldoc=yes --deldesc=yes --delspec=yes --default \
--pkgversion "3:1.0~svn-`grep "#define VERSION" version.h | cut -d"-" -f2`"
$ make distclean

```

If you wish this installation to register both MPlayer and MEncoder with the Ubuntu package management system consider adding *--provides "mplayer,mencoder"* to the checkinstall line. Or perhaps you have no interest in MEncoder at all, in which case add *--disable-mencoder* to your ./configure options. Lots of choices!

And there you have the cutting edge MPlayer. Return here from time to time to update your copy by using the command 'svn update' and then compiling as before. But this is of course the commandline version only, next to download the best graphical front-end for MPlayer available today:

===========================
**Downloading SMPlayer**
===========================

The default gui for MPlayer is known as gmplayer and it has been out of development for some time. Although something of a commandline guy I use SMPLayer in place of gmplayer and I would advise that you do the same. To download from the Ubuntu Repositories simply:

```
$ sudo apt-get install smplayer 
```

This will be a download of about 13 megs on a fresh system as there are some QT requirements. The developer of SMPlayer also maintains a Personal Package Archive (PPA) with a newer version of the SMPlayer, details of how to access this can be seen [here]("http://smplayer.sourceforge.net/downloads.php?tr_lang=en").

=============================
**And in conclusion.....**
=============================

And so you have successfully installed the svn MPlayer! You can check the options available for you with the following commands:

[LIST=1]
[*]**mplayer -vo help** : Video output available to mplayer
[*]**mplayer -ao help** : Audio output available to mplayer
[*]**mplayer -vc help** : Available video codecs
[*]**mplayer -ac help** : Available audio codecs
[*]**mencoder -ovc help** : Available video codecs
[*]**mencoder-oac help** : Available audio codecs 
[/LIST]

The commandline player is started with the command 'mplayer' in a Terminal window, the encoder with the command 'mencoder' while the gui SMPlayer should appear on your menu.  And remember: "Have fun!".

Andrew Strong
September 15th, 2009.

---

### Post by taavikko on 2009-02-26
Thanks for the quick-guide..

however, one thing, i would use
```
sudo apt-get build-deb mplayer mencoder
```
to satisfy the dependencies...

---

### Post by Jeroen Vernooij on 2009-02-26
Further, x264 is an encoder. If you don't plan to encode/transcode movies (only playback) it is not necessary to compile x264 at all.

[SIZE="1"]Edit: Thanks, Nullack[/SIZE]

---

### Post by Nullack on 2009-02-26
> **taavikko said:**
> Thanks for the quick-guide..

however, one thing, i would use
```
sudo apt-get build-deb mplayer mencoder
```
to satisfy the dependencies...

I use 

```
sudo apt-get build-dep mplayer-nogui mencoder
```

Plus, if you want VDPAU and you have installed the NVIDIA driver via Ubuntu's repo, you will need the NVIDIA VDPAU Dev package installed which currently isnt a build dep. If you have manually installed the driver you wont need the VPAU Dev package.

@Andrew - top stuff mate :) The codecs section doesnt mention those processes are for 32bit platforms only - the AMD64 build of Ubuntu Jaunty requires the AMD64 bit essential codecs from mplayers website. Its so great to have a powerful set of tools with mencoder and x264, all up to date with SVN. Thanks.

---

### Post by meborc on 2009-02-26
thanks, a very good howto :)

---

### Post by Nullack on 2009-02-26
You didnt use checkinstall like the guide instructs Jeroen

---

### Post by andrew.46 on 2009-02-26
Hi Jeroen,

> **Jeroen Vernooij said:**
> When I earlier compiled MPlayer from SVN, apt didn't knew it was installed: it didn't show up in Synaptic. Therefore, if you try to install SMPlayer via apt, it will install the MPlayer from the ubuntu repository, regardless if you want it or not since it is a dependency.

True but I suspect you did not notice that I have altered the package version number of MPlayer specifically for this reason. The version number I give there means that the repository version will *not* overwrite the compiled version.

> Further, x264 is an encoder. If you don't plan to encode/transcode movies (only playback) it is not necessary to compile x264 at all.

There is a special problem with x264 in that the svn MPlayer will not compile with a build number less than 59. Although the repository now hosts build 60 I have 3 good reasons for compiling x264:

[LIST=1]
[*]This future proofs the guide in case the MPlayer devs ever raise the required build number again.
[*]If people wish to also compile FFmpeg as per the FakeOutdoorsman's guide on these forums there will be no duplication or redundancy.
[*]Some will wish to encode x264/h264 with Mencoder
[/LIST]

All the best,

Andrew

---

### Post by andrew.46 on 2009-02-26
Hi meborc,

> **meborc said:**
> thanks, a very good howto :)

My pleasure :-). It is destined to actually go in the 'Tutorials' section when Jaunty is released. The forum guys decided it was better here in the meantime.

Andrew

---

### Post by andrew.46 on 2009-02-26
Hi taavikko,

> **taavikko said:**
> Thanks for the quick-guide..

however, one thing, i would use
```
sudo apt-get build-deb mplayer mencoder
```
to satisfy the dependencies...

I have used 'build-dep' as a *starter* for the dev files. I have added some in and subtracted more than a few. The svn is different to the rc2 hosted by Ubuntu in many subtle ways so usually the files need a little pruning. You will note the addition of the amr libraries, the omission of all the libdvdnav/libdvdread files, the omission of the repository Live555 libraries, omission of the libx264-65 library, addition of libschroeder-dev etc etc.

All the best,

Andrew

---

### Post by andrew.46 on 2009-02-26
Hi Nullack,

> **Nullack said:**
>  The codecs section doesnt mention those processes are for 32bit platforms only - the AMD64 build of Ubuntu Jaunty requires the AMD64 bit essential codecs from mplayers website. Its so great to have a powerful set of tools with mencoder and x264, all up to date with SVN. Thanks.

Bugger, I forgot the 64bit codecs. I will add a reference to those after this spell of night work.

Andrew

---

### Post by FakeOutdoorsman on 2009-02-26
An excellent guide as usual, Andrew.

---

### Post by andrew.46 on 2009-02-26
Hi FakeOutdoorsman,

> **FakeOutdoorsman said:**
> An excellent guide as usual, Andrew.

My thanks again to you for mentioning VirtualBox, this version of the MPlayer guide was written using it :-). 

Andrew

---

### Post by Nullack on 2009-02-27
Andrew, mate Ive got problems with x264:

(Reading database ... 115204 files and directories currently installed.)
Preparing to replace x264 1:0.svn20090224-0.0ubuntu1-1 (using .../x264_1:0.svn20090228-0.0ubuntu1-1_amd64.deb) ...
Unpacking replacement x264 ...
dpkg: error processing /home/nullack/src/x264/x264_1:0.svn20090228-0.0ubuntu1-1_amd64.deb (--install):
 trying to overwrite `/usr/lib/libx264.a', which is also in package libx264-dev
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/nullack/src/x264/x264_1:0.svn20090228-0.0ubuntu1-1_amd64.deb

It does seem to install though, so its jst the package thats not created.

---

### Post by andrew.46 on 2009-02-27
Hi Nullack,

> **Nullack said:**
> 
dpkg: error processing /home/nullack/src/x264/x264_1:0.svn20090228-0.0ubuntu1-1_amd64.deb (--install):
 trying to overwrite `/usr/lib/libx264.a', which is also in **[COLOR="Red"]package libx264-dev[/COLOR]**


I have just upgraded x264 successfully on my 'virgin' installation of Jaunty with no problems. I note the reference to libx264-dev, highlighted above. This might very well be the Ubuntu repository version on tour system? If so perhaps try removing it first and then install the git version.

All the best,

Andrew

---

### Post by andrew.46 on 2009-02-27
BTW since this guide is in temporary 'quarantine' here in the Jaunty testing section can I ask that as many as possible test it out? In particular I am keen to hear if there are any media files that MPlayer does *not* play after following this setup guide.

Thanks,

Andrew

---

### Post by Nullack on 2009-02-28
Andrew to answer your question. Theres long standing things mplayer/ffmpeg doesnt play, such as:

MS WMA Pro (personally this is the biggest gap for my uses)
MS WMVP
MS WVP2
Intel IV41
Intel IV50

Then there is decoder and demuxer bugs that are in a state of flux with SVN. Getting fixes, new bugs etcetc.

The biggest two of these for me currently in SVN is:

1. Broken VDPAU VC1
2. Broken VDPAU WMV3

---

### Post by plun on 2009-03-01
Thanks Andrew !

Works just fine......

a small humble proposal is to remove all $$$, faster "copy and paste"  :P

---

### Post by Starks on 2009-03-01
I hate how people use those symbols instead of sudo or non-sudo.

What's the rationale?

---

### Post by taavikko on 2009-03-01
> **Starks said:**
> I hate how people use those symbols instead of sudo or non-sudo.

What's the rationale?

For the experts to tell the difference when to use it...
root #
non-root $

---

### Post by Nullack on 2009-03-01
SVN has improved with working vc-1 and wmv3 vdpau playback. Though, there is a bit of green artifacting with vdpau which is probably a driver issue.

---

### Post by kvarley on 2009-03-01
Thanks, very useful thread!

---

### Post by KhaaL on 2009-03-03
Hi! I'm trying to follow this guide but i'm failing at the x264 bit... i'm sure i did some kind of goof since i'm not really familiar with compiling stuff :)


```
MMX -DARCH_X86_64 -DSYS_LINUX -fPIC -s -fomit-frame-pointer  common/set.c -MT common/set.o -MM -g0 1>> .depend;  gcc -O4 -ffast-math  -Wall -I. -DVISUALIZE=1 -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -fPIC -s -fomit-frame-pointer  common/quant.c -MT common/quant.o -MM -g0 1>> .depend;  gcc -O4 -ffast-math  -Wall -I. -DVISUALIZE=1 -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -fPIC -s -fomit-frame-pointer  common/vlc.c -MT common/vlc.o -MM -g0 1>> .depend;  gcc -O4 -ffast-math  -Wall -I. -DVISUALIZE=1 -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -fPIC -s -fomit-frame-pointer  encoder/analyse.c -MT encoder/analyse.o -MM -g0 1>> .depend;  gcc -O4 -ffast-math  -Wall -I. -DVISUALIZE=1 -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -fPIC -s -fomit-frame-pointer  encoder/me.c -MT encoder/me.o -MM -g0 1>> .depend;  gcc -O4 -ffast-math  -Wall -I. -DVISUALIZE=1 -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -fPIC -s -fomit-frame-pointer  encoder/ratecontrol.c -MT encoder/ratecontrol.o -MM -g0 1>> .depend;  gcc -O4 -ffast-math  -Wall -I. -DVISUALIZE=1 -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -fPIC -s -fomit-frame-pointer  encoder/set.c -MT encoder/set.o -MM -g0 1>> .depend;  gcc -O4 -ffast-math  -Wall -I. -DVISUALIZE=1 -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -fPIC -s -fomit-frame-pointer  encoder/macroblock.c -MT encoder/macroblock.o -MM -g0 1>> .depend;  gcc -O4 -ffast-math  -Wall -I. -DVISUALIZE=1 -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -fPIC -s -fomit-frame-pointer  encoder/cabac.c -MT encoder/cabac.o -MM -g0 1>> .depend;  gcc -O4 -ffast-math  -Wall -I. -DVISUALIZE=1 -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -fPIC -s -fomit-frame-pointer  encoder/cavlc.c -MT encoder/cavlc.o -MM -g0 1>> .depend;  gcc -O4 -ffast-math  -Wall -I. -DVISUALIZE=1 -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -fPIC -s -fomit-frame-pointer  encoder/encoder.c -MT encoder/encoder.o -MM -g0 1>> .depend;  gcc -O4 -ffast-math  -Wall -I. -DVISUALIZE=1 -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -fPIC -s -fomit-frame-pointer  common/visualize.c -MT common/visualize.o -MM -g0 1>> .depend;  gcc -O4 -ffast-math  -Wall -I. -DVISUALIZE=1 -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -fPIC -s -fomit-frame-pointer  common/display-x11.c -MT common/display-x11.o -MM -g0 1>> .depend;  gcc -O4 -ffast-math  -Wall -I. -DVISUALIZE=1 -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -fPIC -s -fomit-frame-pointer  common/x86/mc-c.c -MT common/x86/mc-c.o -MM -g0 1>> .depend;  gcc -O4 -ffast-math  -Wall -I. -DVISUALIZE=1 -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -fPIC -s -fomit-frame-pointer  common/x86/predict-c.c -MT common/x86/predict-c.o -MM -g0 1>> .depend;  gcc -O4 -ffast-math  -Wall -I. -DVISUALIZE=1 -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -fPIC -s -fomit-frame-pointer  x264.c -MT x264.o -MM -g0 1>> .depend;  gcc -O4 -ffast-math  -Wall -I. -DVISUALIZE=1 -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -fPIC -s -fomit-frame-pointer  matroska.c -MT matroska.o -MM -g0 1>> .depend;  gcc -O4 -ffast-math  -Wall -I. -DVISUALIZE=1 -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -fPIC -s -fomit-frame-pointer  muxers.c -MT muxers.o -MM -g0 1>> .depend;
gcc -O4 -ffast-math  -Wall -I. -DVISUALIZE=1 -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -fPIC -s -fomit-frame-pointer   -c -o encoder/set.o encoder/set.c
gcc -O4 -ffast-math  -Wall -I. -DVISUALIZE=1 -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -fPIC -s -fomit-frame-pointer   -c -o common/display-x11.o common/display-x11.c
common/display-x11.c:21:22: error: X11/Xlib.h: No such file or directory
common/display-x11.c:22:23: error: X11/Xutil.h: No such file or directory
common/display-x11.c:28: error: ‘ConfigureNotify’ undeclared here (not in a function)
common/display-x11.c:28: error: ‘ExposureMask’ undeclared here (not in a function)
common/display-x11.c:28: error: ‘KeyPressMask’ undeclared here (not in a function)
common/display-x11.c:28: error: ‘ButtonPressMask’ undeclared here (not in a function)
common/display-x11.c:28: error: ‘StructureNotifyMask’ undeclared here (not in a function)
common/display-x11.c:28: error: ‘ResizeRedirectMask’ undeclared here (not in a function)
common/display-x11.c:30: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
common/display-x11.c:33: error: expected specifier-qualifier-list before ‘Window’
common/display-x11.c: In function ‘disp_chkerror’:
common/display-x11.c:39: warning: implicit declaration of function ‘abort’
common/display-x11.c:39: warning: incompatible implicit declaration of built-in function ‘abort’
common/display-x11.c: In function ‘disp_init_display’:
common/display-x11.c:43: error: ‘Visual’ undeclared (first use in this function)
common/display-x11.c:43: error: (Each undeclared identifier is reported only once
common/display-x11.c:43: error: for each function it appears in.)
common/display-x11.c:43: error: ‘visual’ undeclared (first use in this function)
common/display-x11.c:48: error: ‘disp_display’ undeclared (first use in this function)
common/display-x11.c:50: warning: implicit declaration of function ‘XOpenDisplay’
common/display-x11.c:52: warning: implicit declaration of function ‘DefaultScreen’
common/display-x11.c:53: warning: implicit declaration of function ‘DefaultVisual’
common/display-x11.c:55: warning: implicit declaration of function ‘DefaultDepth’
common/display-x11.c:56: error: ‘TrueColor’ undeclared (first use in this function)
common/display-x11.c:59: error: ‘PseudoColor’ undeclared (first use in this function)
common/display-x11.c: In function ‘disp_init_window’:
common/display-x11.c:64: error: ‘XSizeHints’ undeclared (first use in this function)
common/display-x11.c:64: error: ‘shint’ undeclared (first use in this function)
common/display-x11.c:65: error: ‘XSetWindowAttributes’ undeclared (first use in this function)
common/display-x11.c:65: error: expected ‘;’ before ‘xswa’
common/display-x11.c:66: error: ‘XEvent’ undeclared (first use in this function)
common/display-x11.c:66: error: expected ‘;’ before ‘xev’
common/display-x11.c:67: error: ‘disp_display’ undeclared (first use in this function)
common/display-x11.c:68: error: ‘Visual’ undeclared (first use in this function)
common/display-x11.c:68: error: ‘visual’ undeclared (first use in this function)
common/display-x11.c:72: error: ‘Window’ undeclared (first use in this function)
common/display-x11.c:72: error: expected ‘;’ before ‘window’
common/display-x11.c:80: warning: implicit declaration of function ‘XAllocSizeHints’
common/display-x11.c:84: error: ‘PSize’ undeclared (first use in this function)
common/display-x11.c:84: error: ‘PMinSize’ undeclared (first use in this function)
common/display-x11.c:84: error: ‘PMaxSize’ undeclared (first use in this function)
common/display-x11.c:88: warning: implicit declaration of function ‘WhitePixel’
common/display-x11.c:89: warning: implicit declaration of function ‘BlackPixel’
common/display-x11.c:92: error: ‘CWColormap’ undeclared (first use in this function)
common/display-x11.c:93: error: ‘xswa’ undeclared (first use in this function)
common/display-x11.c:93: warning: implicit declaration of function ‘XCreateColormap’
common/display-x11.c:93: warning: implicit declaration of function ‘DefaultRootWindow’
common/display-x11.c:93: error: ‘AllocNone’ undeclared (first use in this function)
common/display-x11.c:97: error: ‘Always’ undeclared (first use in this function)
common/display-x11.c:99: error: ‘NorthWestGravity’ undeclared (first use in this function)
common/display-x11.c:100: error: ‘CWBackPixel’ undeclared (first use in this function)
common/display-x11.c:100: error: ‘CWBorderPixel’ undeclared (first use in this function)
common/display-x11.c:100: error: ‘CWBackingStore’ undeclared (first use in this function)
common/display-x11.c:100: error: ‘CWBackingPlanes’ undeclared (first use in this function)
common/display-x11.c:100: error: ‘CWBitGravity’ undeclared (first use in this function)
common/display-x11.c:101: error: ‘window’ undeclared (first use in this function)
common/display-x11.c:101: warning: implicit declaration of function ‘XCreateWindow’
common/display-x11.c:103: error: ‘InputOutput’ undeclared (first use in this function)
common/display-x11.c:104: error: ‘struct disp_window’ has no member named ‘window’
common/display-x11.c:106: warning: implicit declaration of function ‘XSelectInput’
common/display-x11.c:107: warning: implicit declaration of function ‘XSetStandardProperties’
common/display-x11.c:107: error: ‘None’ undeclared (first use in this function)
common/display-x11.c:108: warning: implicit declaration of function ‘XMapWindow’
common/display-x11.c:110: warning: implicit declaration of function ‘XNextEvent’
common/display-x11.c:110: error: ‘xev’ undeclared (first use in this function)
common/display-x11.c:111: error: ‘MapNotify’ undeclared (first use in this function)
common/display-x11.c:114: error: ‘struct disp_window’ has no member named ‘window’
common/display-x11.c:116: warning: implicit declaration of function ‘XResizeWindow’
common/display-x11.c:117: warning: implicit declaration of function ‘XSync’
common/display-x11.c:118: warning: implicit declaration of function ‘XFree’
common/display-x11.c: In function ‘disp_sync’:
common/display-x11.c:122: error: ‘disp_display’ undeclared (first use in this function)
common/display-x11.c: In function ‘disp_setcolor’:
common/display-x11.c:127: error: ‘GC’ undeclared (first use in this function)
common/display-x11.c:127: error: expected ‘;’ before ‘gc’
common/display-x11.c:128: error: ‘XColor’ undeclared (first use in this function)
common/display-x11.c:128: error: expected ‘;’ before ‘c_exact’
common/display-x11.c:129: error: ‘Colormap’ undeclared (first use in this function)
common/display-x11.c:129: error: expected ‘;’ before ‘cm’
common/display-x11.c:130: error: ‘Status’ undeclared (first use in this function)
common/display-x11.c:130: error: expected ‘;’ before ‘st’
common/display-x11.c:132: error: ‘disp_display’ undeclared (first use in this function)
common/display-x11.c:133: error: ‘gc’ undeclared (first use in this function)
common/display-x11.c:133: warning: implicit declaration of function ‘DefaultGC’
common/display-x11.c:134: error: ‘cm’ undeclared (first use in this function)
common/display-x11.c:134: warning: implicit declaration of function ‘DefaultColormap’
common/display-x11.c:135: error: ‘st’ undeclared (first use in this function)
common/display-x11.c:135: warning: implicit declaration of function ‘XAllocNamedColor’
common/display-x11.c:135: error: ‘c_nearest’ undeclared (first use in this function)
common/display-x11.c:135: error: ‘c_exact’ undeclared (first use in this function)
common/display-x11.c:137: warning: implicit declaration of function ‘XSetForeground’
common/display-x11.c: In function ‘disp_gray’:
common/display-x11.c:141: error: ‘Visual’ undeclared (first use in this function)
common/display-x11.c:141: error: ‘visual’ undeclared (first use in this function)
common/display-x11.c:142: error: ‘XImage’ undeclared (first use in this function)
common/display-x11.c:142: error: ‘ximage’ undeclared (first use in this function)
common/display-x11.c:149: error: ‘GC’ undeclared (first use in this function)
common/display-x11.c:149: error: expected ‘;’ before ‘gc’
common/display-x11.c:154: error: ‘disp_display’ undeclared (first use in this function)
common/display-x11.c:157: warning: implicit declaration of function ‘XCreateImage’
common/display-x11.c:157: error: ‘ZPixmap’ undeclared (first use in this function)
common/display-x11.c:160: error: ‘LSBFirst’ undeclared (first use in this function)
common/display-x11.c:163: error: ‘MSBFirst’ undeclared (first use in this function)
common/display-x11.c:173: error: ‘gc’ undeclared (first use in this function)
common/display-x11.c:177: warning: implicit declaration of function ‘XPutImage’
common/display-x11.c:177: error: ‘struct disp_window’ has no member named ‘window’
common/display-x11.c:181: error: ‘struct disp_window’ has no member named ‘window’
common/display-x11.c:183: warning: implicit declaration of function ‘XDestroyImage’
common/display-x11.c: In function ‘disp_gray_zoom’:
common/display-x11.c:198: warning: pointer targets in passing argument 2 of ‘disp_gray’ differ in signedness
common/display-x11.c:199: warning: implicit declaration of function ‘free’
common/display-x11.c:199: warning: incompatible implicit declaration of built-in function ‘free’
common/display-x11.c: In function ‘disp_point’:
common/display-x11.c:204: error: ‘GC’ undeclared (first use in this function)
common/display-x11.c:204: error: expected ‘;’ before ‘gc’
common/display-x11.c:205: error: ‘disp_display’ undeclared (first use in this function)
common/display-x11.c:206: error: ‘gc’ undeclared (first use in this function)
common/display-x11.c:207: warning: implicit declaration of function ‘XDrawPoint’
common/display-x11.c:207: error: ‘struct disp_window’ has no member named ‘window’
common/display-x11.c: In function ‘disp_line’:
common/display-x11.c:213: error: ‘GC’ undeclared (first use in this function)
common/display-x11.c:213: error: expected ‘;’ before ‘gc’
common/display-x11.c:214: error: ‘disp_display’ undeclared (first use in this function)
common/display-x11.c:215: error: ‘gc’ undeclared (first use in this function)
common/display-x11.c:216: warning: implicit declaration of function ‘XDrawLine’
common/display-x11.c:216: error: ‘struct disp_window’ has no member named ‘window’
common/display-x11.c: In function ‘disp_rect’:
common/display-x11.c:222: error: ‘GC’ undeclared (first use in this function)
common/display-x11.c:222: error: expected ‘;’ before ‘gc’
common/display-x11.c:223: error: ‘disp_display’ undeclared (first use in this function)
common/display-x11.c:225: error: ‘gc’ undeclared (first use in this function)
common/display-x11.c:226: warning: implicit declaration of function ‘XDrawRectangle’
common/display-x11.c:226: error: ‘struct disp_window’ has no member named ‘window’
make: *** [common/display-x11.o] Error 1

```

```

khaal@Xeraphim:~/x264$ sudo checkinstall --fstrans=no --install=yes --pakdir "$HOME/Desktop" \
> --maintainer "$USER" --pkgname=x264 --pkgversion "1:0.svn`date +%Y%m%d`-0.0ubuntu1" \
> --backup=no --deldoc=yes --deldesc=yes --delspec=yes --gzman --default

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.



*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ khaal ]
1 -  Summary: [ Package created with checkinstall 1.6.1 ]
2 -  Name:    [ x264 ]
3 -  Version: [ 1:0.svn20090303-0.0ubuntu1 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ amd64 ]
8 -  Source location: [ x264 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]
11 - Provides: [ x264 ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make...Installing with install...

========================= Installation results ===========================
gcc -O4 -ffast-math  -Wall -I. -DVISUALIZE=1 -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -fPIC -s -fomit-frame-pointer   -c -o x264.o x264.c
gcc -O4 -ffast-math  -Wall -I. -DVISUALIZE=1 -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -fPIC -s -fomit-frame-pointer   -c -o muxers.o muxers.c
gcc -O4 -ffast-math  -Wall -I. -DVISUALIZE=1 -DHAVE_MALLOC_H -DHAVE_MMX -DARCH_X86_64 -DSYS_LINUX -fPIC -s -fomit-frame-pointer   -c -o common/display-x11.o common/display-x11.c
common/display-x11.c:21:22: error: X11/Xlib.h: No such file or directory
common/display-x11.c:22:23: error: X11/Xutil.h: No such file or directory
common/display-x11.c:28: error: ‘ConfigureNotify’ undeclared here (not in a function)
common/display-x11.c:28: error: ‘ExposureMask’ undeclared here (not in a function)
common/display-x11.c:28: error: ‘KeyPressMask’ undeclared here (not in a function)
common/display-x11.c:28: error: ‘ButtonPressMask’ undeclared here (not in a function)
common/display-x11.c:28: error: ‘StructureNotifyMask’ undeclared here (not in a function)
common/display-x11.c:28: error: ‘ResizeRedirectMask’ undeclared here (not in a function)
common/display-x11.c:30: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
common/display-x11.c:33: error: expected specifier-qualifier-list before ‘Window’
common/display-x11.c: In function ‘disp_chkerror’:
common/display-x11.c:39: warning: implicit declaration of function ‘abort’
common/display-x11.c:39: warning: incompatible implicit declaration of built-in function ‘abort’
common/display-x11.c: In function ‘disp_init_display’:
common/display-x11.c:43: error: ‘Visual’ undeclared (first use in this function)
common/display-x11.c:43: error: (Each undeclared identifier is reported only once
common/display-x11.c:43: error: for each function it appears in.)
common/display-x11.c:43: error: ‘visual’ undeclared (first use in this function)
common/display-x11.c:48: error: ‘disp_display’ undeclared (first use in this function)
common/display-x11.c:50: warning: implicit declaration of function ‘XOpenDisplay’
common/display-x11.c:52: warning: implicit declaration of function ‘DefaultScreen’
common/display-x11.c:53: warning: implicit declaration of function ‘DefaultVisual’
common/display-x11.c:55: warning: implicit declaration of function ‘DefaultDepth’
common/display-x11.c:56: error: ‘TrueColor’ undeclared (first use in this function)
common/display-x11.c:59: error: ‘PseudoColor’ undeclared (first use in this function)
common/display-x11.c: In function ‘disp_init_window’:
common/display-x11.c:64: error: ‘XSizeHints’ undeclared (first use in this function)
common/display-x11.c:64: error: ‘shint’ undeclared (first use in this function)
common/display-x11.c:65: error: ‘XSetWindowAttributes’ undeclared (first use in this function)
common/display-x11.c:65: error: expected ‘;’ before ‘xswa’
common/display-x11.c:66: error: ‘XEvent’ undeclared (first use in this function)
common/display-x11.c:66: error: expected ‘;’ before ‘xev’
common/display-x11.c:67: error: ‘disp_display’ undeclared (first use in this function)
common/display-x11.c:68: error: ‘Visual’ undeclared (first use in this function)
common/display-x11.c:68: error: ‘visual’ undeclared (first use in this function)
common/display-x11.c:72: error: ‘Window’ undeclared (first use in this function)
common/display-x11.c:72: error: expected ‘;’ before ‘window’
common/display-x11.c:80: warning: implicit declaration of function ‘XAllocSizeHints’
common/display-x11.c:84: error: ‘PSize’ undeclared (first use in this function)
common/display-x11.c:84: error: ‘PMinSize’ undeclared (first use in this function)
common/display-x11.c:84: error: ‘PMaxSize’ undeclared (first use in this function)
common/display-x11.c:88: warning: implicit declaration of function ‘WhitePixel’
common/display-x11.c:89: warning: implicit declaration of function ‘BlackPixel’
common/display-x11.c:92: error: ‘CWColormap’ undeclared (first use in this function)
common/display-x11.c:93: error: ‘xswa’ undeclared (first use in this function)
common/display-x11.c:93: warning: implicit declaration of function ‘XCreateColormap’
common/display-x11.c:93: warning: implicit declaration of function ‘DefaultRootWindow’
common/display-x11.c:93: error: ‘AllocNone’ undeclared (first use in this function)
common/display-x11.c:97: error: ‘Always’ undeclared (first use in this function)
common/display-x11.c:99: error: ‘NorthWestGravity’ undeclared (first use in this function)
common/display-x11.c:100: error: ‘CWBackPixel’ undeclared (first use in this function)
common/display-x11.c:100: error: ‘CWBorderPixel’ undeclared (first use in this function)
common/display-x11.c:100: error: ‘CWBackingStore’ undeclared (first use in this function)
common/display-x11.c:100: error: ‘CWBackingPlanes’ undeclared (first use in this function)
common/display-x11.c:100: error: ‘CWBitGravity’ undeclared (first use in this function)
common/display-x11.c:101: error: ‘window’ undeclared (first use in this function)
common/display-x11.c:101: warning: implicit declaration of function ‘XCreateWindow’
common/display-x11.c:103: error: ‘InputOutput’ undeclared (first use in this function)
common/display-x11.c:104: error: ‘struct disp_window’ has no member named ‘window’
common/display-x11.c:106: warning: implicit declaration of function ‘XSelectInput’
common/display-x11.c:107: warning: implicit declaration of function ‘XSetStandardProperties’
common/display-x11.c:107: error: ‘None’ undeclared (first use in this function)
common/display-x11.c:108: warning: implicit declaration of function ‘XMapWindow’
common/display-x11.c:110: warning: implicit declaration of function ‘XNextEvent’
common/display-x11.c:110: error: ‘xev’ undeclared (first use in this function)
common/display-x11.c:111: error: ‘MapNotify’ undeclared (first use in this function)
common/display-x11.c:114: error: ‘struct disp_window’ has no member named ‘window’
common/display-x11.c:116: warning: implicit declaration of function ‘XResizeWindow’
common/display-x11.c:117: warning: implicit declaration of function ‘XSync’
common/display-x11.c:118: warning: implicit declaration of function ‘XFree’
common/display-x11.c: In function ‘disp_sync’:
common/display-x11.c:122: error: ‘disp_display’ undeclared (first use in this function)
common/display-x11.c: In function ‘disp_setcolor’:
common/display-x11.c:127: error: ‘GC’ undeclared (first use in this function)
common/display-x11.c:127: error: expected ‘;’ before ‘gc’
common/display-x11.c:128: error: ‘XColor’ undeclared (first use in this function)
common/display-x11.c:128: error: expected ‘;’ before ‘c_exact’
common/display-x11.c:129: error: ‘Colormap’ undeclared (first use in this function)
common/display-x11.c:129: error: expected ‘;’ before ‘cm’
common/display-x11.c:130: error: ‘Status’ undeclared (first use in this function)
common/display-x11.c:130: error: expected ‘;’ before ‘st’
common/display-x11.c:132: error: ‘disp_display’ undeclared (first use in this function)
common/display-x11.c:133: error: ‘gc’ undeclared (first use in this function)
common/display-x11.c:133: warning: implicit declaration of function ‘DefaultGC’
common/display-x11.c:134: error: ‘cm’ undeclared (first use in this function)
common/display-x11.c:134: warning: implicit declaration of function ‘DefaultColormap’
common/display-x11.c:135: error: ‘st’ undeclared (first use in this function)
common/display-x11.c:135: warning: implicit declaration of function ‘XAllocNamedColor’
common/display-x11.c:135: error: ‘c_nearest’ undeclared (first use in this function)
common/display-x11.c:135: error: ‘c_exact’ undeclared (first use in this function)
common/display-x11.c:137: warning: implicit declaration of function ‘XSetForeground’
common/display-x11.c: In function ‘disp_gray’:
common/display-x11.c:141: error: ‘Visual’ undeclared (first use in this function)
common/display-x11.c:141: error: ‘visual’ undeclared (first use in this function)
common/display-x11.c:142: error: ‘XImage’ undeclared (first use in this function)
common/display-x11.c:142: error: ‘ximage’ undeclared (first use in this function)
common/display-x11.c:149: error: ‘GC’ undeclared (first use in this function)
common/display-x11.c:149: error: expected ‘;’ before ‘gc’
common/display-x11.c:154: error: ‘disp_display’ undeclared (first use in this function)
common/display-x11.c:157: warning: implicit declaration of function ‘XCreateImage’
common/display-x11.c:157: error: ‘ZPixmap’ undeclared (first use in this function)
common/display-x11.c:160: error: ‘LSBFirst’ undeclared (first use in this function)
common/display-x11.c:163: error: ‘MSBFirst’ undeclared (first use in this function)
common/display-x11.c:173: error: ‘gc’ undeclared (first use in this function)
common/display-x11.c:177: warning: implicit declaration of function ‘XPutImage’
common/display-x11.c:177: error: ‘struct disp_window’ has no member named ‘window’
common/display-x11.c:181: error: ‘struct disp_window’ has no member named ‘window’
common/display-x11.c:183: warning: implicit declaration of function ‘XDestroyImage’
common/display-x11.c: In function ‘disp_gray_zoom’:
common/display-x11.c:198: warning: pointer targets in passing argument 2 of ‘disp_gray’ differ in signedness
common/display-x11.c:199: warning: implicit declaration of function ‘free’
common/display-x11.c:199: warning: incompatible implicit declaration of built-in function ‘free’
common/display-x11.c: In function ‘disp_point’:
common/display-x11.c:204: error: ‘GC’ undeclared (first use in this function)
common/display-x11.c:204: error: expected ‘;’ before ‘gc’
common/display-x11.c:205: error: ‘disp_display’ undeclared (first use in this function)
common/display-x11.c:206: error: ‘gc’ undeclared (first use in this function)
common/display-x11.c:207: warning: implicit declaration of function ‘XDrawPoint’
common/display-x11.c:207: error: ‘struct disp_window’ has no member named ‘window’
common/display-x11.c: In function ‘disp_line’:
common/display-x11.c:213: error: ‘GC’ undeclared (first use in this function)
common/display-x11.c:213: error: expected ‘;’ before ‘gc’
common/display-x11.c:214: error: ‘disp_display’ undeclared (first use in this function)
common/display-x11.c:215: error: ‘gc’ undeclared (first use in this function)
common/display-x11.c:216: warning: implicit declaration of function ‘XDrawLine’
common/display-x11.c:216: error: ‘struct disp_window’ has no member named ‘window’
common/display-x11.c: In function ‘disp_rect’:
common/display-x11.c:222: error: ‘GC’ undeclared (first use in this function)
common/display-x11.c:222: error: expected ‘;’ before ‘gc’
common/display-x11.c:223: error: ‘disp_display’ undeclared (first use in this function)
common/display-x11.c:225: error: ‘gc’ undeclared (first use in this function)
common/display-x11.c:226: warning: implicit declaration of function ‘XDrawRectangle’
common/display-x11.c:226: error: ‘struct disp_window’ has no member named ‘window’
make: *** [common/display-x11.o] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

khaal@Xeraphim:~/x264$ 

```

---

### Post by andrew.46 on 2009-03-03
Hi KhaaL,

Good news is that I have just updated x264 with no problems so there is no problem with x264 itself. A little housekeeping on your x264 files may help, try:

```
$ sudo chown -R $USER:$USER ~/x264
$ cd ~/x264
$ make clean
$ git pull
```

And then run the ./configure options / make etc as before. Hopefully this will straighten out the issue. If not delete the ~/x264 directory and all of its contents and start from scratch.

**Edit:** As I have suggested by private mail it may be required or some 64bit systems to also run this option with configure:

```
./configure --prefix=/usr --enable-shared --enable-visualize **[COLOR="Red"]--enable-pic[/COLOR]**
```

Some details of this can be [seen here]("http://www.gentoo.org/proj/en/base/amd64/howtos/index.xml?part=1&chap=3"). If can get some confirmation that this is required on 64bit systems I will add this as a footnote to the x264 section.


All the best,

Andrew

---

### Post by andrew.46 on 2009-03-04
Hi again,

On closer examination:

```
common/display-x11.c:21:22: error: X11/Xlib.h: No such file or directory
```

Try losing the --enable-visualize option, or better still installing the MPlayer -dev files first (which should install the required file).

**Edit:** Before I submerge for another spell of night work I have removed the --enable-visualize option for x264 which I suspect was always going to be more trouble than it is worth.

Andrew

---

### Post by Nullack on 2009-03-04
SVN broke some types of MPEG1/2 VDPAU playback - devs have been reported to the problem.

Also NVIDIA have resolved some VDPAU issues in their drivers which will be in the next release from NVIDIA. This apparently fixes coloured macroblock artifacting in some VC1 and AVC streams.

---

### Post by KhaaL on 2009-03-04
Thanks for the updated guide, now it compiles successfully on my 64bit system! what I did was to download the all codecs package and overwrote its files with the 3 files provided with the 64bit package. it dont seem to have vpdau enabled though but playback is incredibly much more smoother... I've just tested it quickly though, will test it more throughly later tonight. Nullack, can you direct me to the announcement of the broken vdpau in mplayer?

---

### Post by Nullack on 2009-03-04
You need the vdpau dev files installed for enabling VDPAU video out - check the output of ./configure to confirm mplayers build script is picking it up.

---

### Post by n3had on 2009-03-05
Hi everyone mencoder wasn't allowing me to continue the installation of mplayer. Everything went fine compiling, building. So i uninstalled the current mencoder version and the installation went fine mplayer is running great

But now ```
sudo dpkg --configure -a

```

gives this 

```
dpkg: dependency problems prevent configuration of devede:
 devede depends on mencoder; however:
  Package mencoder is not installed.
dpkg: error processing devede (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of acidrip:
 acidrip depends on mencoder; however:
  Package mencoder is not installed.
dpkg: error processing acidrip (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 devede
 acidrip

```

when actually mencoder is installed along with mplayer! 

thx 
nehad

EDIT: I've the uninstalled this version and back to repo as for now

thx

---

### Post by Nullack on 2009-03-05
When you compile with make, you get both mplayer and mencoder binaries.

---

### Post by andrew.46 on 2009-03-05
Hi n3had,

> **n3had said:**
> ```
Package mencoder is not installed.
```

Unfortunately ubuntu splits MPlayer into a bunch of different packages and one is Mencoder. This guide does not artificially split MPlayer in this way so there will be a packaging problem which will probably remain. It would be possible to compile *twice* disabling compilation of MPlayer and the MEncoder in turn and produce 2 packages with numbering systems to defeat the Ubuntu packaging numbers but that is all starting to get a little silly.

Sorry about that.

Andrew

---

### Post by rvm4000 on 2009-03-05
> **n3had said:**
> Hi everyone mencoder wasn't allowing me to continue the installation of mplayer. Everything went fine compiling, building. So i uninstalled the current mencoder version and the installation went fine mplayer is running great

But now ```
sudo dpkg --configure -a

```

gives this 

```
dpkg: dependency problems prevent configuration of devede:
 devede depends on mencoder; however:
  Package mencoder is not installed.
dpkg: error processing devede (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of acidrip:
 acidrip depends on mencoder; however:
  Package mencoder is not installed.
dpkg: error processing acidrip (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 devede
 acidrip

```

when actually mencoder is installed along with mplayer! 



I have never used checkinstall, but I see there's a "Provides" field. I think adding "mencoder" to it could fix the problem.

---

### Post by andrew.46 on 2009-03-05
Hi rvm,

> **rvm4000 said:**
> I have never used checkinstall, but I see there's a "Provides" field. I think adding "mencoder" to it could fix the problem. 

Thanks for that :-). Certainly seems to work on my system so I have added it to the guide.  Hopefully this will get a solid testing before Jaunty is released, I normally try to stay out of Debian/Ubuntu package management if I can help it at all!

Andrew

---

### Post by andrew.46 on 2009-03-05
Hi n3had,

> **n3had said:**
> Hi everyone mencoder wasn't allowing me to continue the installation of mplayer. Everything went fine compiling, building. So i uninstalled the current mencoder version and the installation went fine mplayer is running great

But now 

```
sudo dpkg --configure -a
```

gives this 

```
dpkg: dependency problems prevent configuration of devede:
 devede depends on mencoder; however:
  Package mencoder is not installed.
dpkg: error processing devede (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of acidrip:
 acidrip depends on mencoder; however:
  Package mencoder is not installed.
dpkg: error processing acidrip (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 devede
 acidrip

```

when actually mencoder is installed along with mplayer! 

rvm has suggested a fix which I have incorporated into the checkinstall syntax for MPlayer. If you have time could you test it out and in particular see if devede is happy?

Thanks for your trouble,

Andrew

---

### Post by n3had on 2009-03-06
```
(Reading database ... 283947 files and directories currently installed.)
Preparing to replace mplayer 2:1.0~rc2-0ubuntu19 (using .../mplayer_3:1.0~svn-1_amd64.deb) ...
Unpacking replacement mplayer ...
dpkg: error processing /home/tru3m0sl3m/mplayer/mplayer_3:1.0~svn-1_amd64.deb (--install):
 trying to overwrite `/usr/bin/mencoder', which is also in package mencoder
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Processing triggers for man-db ...
Errors were encountered while processing:
 /home/tru3m0sl3m/mplayer/mplayer_3:1.0~svn-1_amd64.deb
~
~
~
~
~
~
~
~
~
~
~
~
(END) 

```

Exactly what i got before i can bypass this by uninstalling mencoder which creates broken dependencies

peace
nehad

---

### Post by andrew.46 on 2009-03-06
Hi nehad,

> **n3had said:**
> Exactly what i got before i can bypass this by uninstalling mencoder which creates broken dependencies

Thanks for trying that for me! If you ever do a clean install of Jaunty consider installing the svn MPlayer/Mencoder *1st* and this may get around some of these problems. But on your existing system why not just compile MPlayer *without* MEncoder? Unless you are keen to do some commandline encoding with MEncoder there should be no problems. Your compiling string would then be:

```

$ cd $HOME/mplayer
$ ./configure --prefix=/usr --codecsdir=/usr/lib/codecs --confdir=/etc/mplayer \
**[COLOR="Red"]--disable-mencoder[/COLOR]**
$ make
$ sudo checkinstall -D --install=yes --fstrans=no --pakdir "$HOME/Desktop" \
--maintainer "$USER" --pkgname mplayer --pkgversion "3:1.0~svn" --backup=no \
--deldoc=yes --deldesc=yes --delspec=yes --gzman --default 
$ make clean
```

Note I have also edited the Checkinstall syntax. And this should give you access to the full MPlayer program and not disturb the older version of MEncoder that is so entwined in your package structure.

All the best,

Andrew

---

### Post by rvm4000 on 2009-03-06
If the "Provides: mencoder" is not enough, maybe adding also "Replaces: mencoder" could work (if checkinstall allows to enter a replaces field).

---

### Post by n3had on 2009-03-06
> **andrew.46 said:**
> Hi nehad,



Thanks for trying that for me! If you ever do a clean install of Jaunty consider installing the svn MPlayer/Mencoder *1st* and this may get around some of these problems. But on your existing system why not just compile MPlayer *without* MEncoder? Unless you are keen to do some commandline encoding with MEncoder there should be no problems. Your compiling string would then be:

```

$ cd $HOME/mplayer
$ ./configure --prefix=/usr --codecsdir=/usr/lib/codecs --confdir=/etc/mplayer \
**[COLOR="Red"]--disable-mencoder[/COLOR]**
$ make
$ sudo checkinstall -D --install=yes --fstrans=no --pakdir "$HOME/Desktop" \
--maintainer "$USER" --pkgname mplayer --pkgversion "3:1.0~svn" --backup=no \
--deldoc=yes --deldesc=yes --delspec=yes --gzman --default 
$ make clean
```

Note I have also edited the Checkinstall syntax. And this should give you access to the full MPlayer program and not disturb the older version of MEncoder that is so entwined in your package structure.

All the best,

Andrew

:popcorn:

```
checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.



*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ tru3m0sl3m ]
1 -  Summary: [ Package created with checkinstall 1.6.1 ]
2 -  Name:    [ mplayer ]
3 -  Version: [ 3:1.0~svn ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ amd64 ]
8 -  Source location: [ mplayer ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]
11 - Provides: [ mplayer ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make...Installing with install...

========================= Installation results ===========================
install -d /usr/bin /etc/mplayer /usr/lib
install -m 755 -s mplayer /usr/bin
install -d /usr/share/man/man1
install -m 644 DOCS/man/en/mplayer.1 /usr/share/man/man1/

======================== Installation successful ==========================

Copying documentation directory...
./
./LICENSE
./AUTHORS
./README
./Changelog
grep: /var/tmp/tmp.xolSbZmvcr/newfile: No such file or directory

Copying files to the temporary directory...OK

Stripping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package...OK

Installing Debian package...OK

Transferring package to /home/tru3m0sl3m/Desktop...OK

Erasing temporary files...OK

Deleting temp dir...OK


**********************************************************************

 Done. The new package has been installed and saved to

 /home/tru3m0sl3m/Desktop/mplayer_3:1.0~svn-1_amd64.deb

 You can remove it from your system anytime using: 

      dpkg -r mplayer

**********************************************************************

```


I've got one more query yesterday after uninstalling mencoder and installing the latest build i had copied /usr/bin/mencoder to desktop and reverted back to mplayer/mencoder of repo and then i copied mencoder(of this build) back to /usr/bin/ ...

NO Broken dependencies and latest mencoder (I forgot to do the same with mplayer) but by this weird workaround (newbie here) would i have the latest builds??

---

### Post by andrew.46 on 2009-03-06
Hi rvm,

> **rvm4000 said:**
> If the "Provides: mencoder" is not enough, maybe adding also "Replaces: mencoder" could work (if checkinstall allows to enter a replaces field).

I could not see this option in checkinstall unfortunately but I could certainly see the limits of checkinstall approaching. Perhaps it would be better for n3had to utilise your PPA where I suspect your MPlayer deb would fit in better with the Ubuntu package management?

Andrew

---

### Post by andrew.46 on 2009-03-06
Hi n3had,

> **n3had said:**
> I've got one more query yesterday after uninstalling mencoder and installing the latest build i had copied /usr/bin/mencoder to desktop and reverted back to mplayer/mencoder of repo and then i copied mencoder(of this build) back to /usr/bin/ ...

NO Broken dependencies and latest mencoder (I forgot to do the same with mplayer) but by this weird workaround (newbie here) would i have the latest builds??

I am afraid that in installing the svn MPlayer + showing considerable athleticism in attempting to bypass the Ubuntu package management + running an alpha release of a Linux distro you are officially no longer a n00b :-).

But as I have mentioned in a previous post I forgot that rvm has a nice [PPA with a 'proper' Debian installataion]("https://launchpad.net/~rvm/+archive/ppa") which while considerably less exciting than rolling your own MPlayer should get around the problem in a less hackish way.

Which brings me back to my own doubts about the future of this guide, particularly when I see with some horror the intricacies of a package management system, a system that has no equivalent in my primary distro, and when I see that rvm has a better arrangement in place anyway. But looks like the Jaunty version is in place anyway which leave me to ruminate darkly about the need for this guide in Ubuntu for another few months....

Andrew

---

### Post by Nullack on 2009-03-06
I hope you keep at it mate. Reasons to compile your own:

1. No waiting to get the latest svn build
2. Having complete control of the ./configure - such as ensuring vdpau output is compiled in
3. The march=native and mtune=native compiler flags provides the best possible performance for your specific system rather than a dumbed down generic compile.
4. It has geek cred

---

### Post by andrew.46 on 2009-03-07
Hi andrew :-)

> **andrew.46 said:**
> 
There is a special problem with x264 in that the svn MPlayer will not compile with a build number less than 59. Although the repository now hosts build 60 I have 3 good reasons for compiling x264:

[LIST=1]
[*]This future proofs the guide in case the MPlayer devs ever raise the required build number again.
[...]
[/LIST]


Interestingly enough the MPlayer devs have raised the bar again to build 65:

[http://svn.mplayerhq.hu/mplayer?view=rev&revision=28869](http://svn.mplayerhq.hu/mplayer?view=rev&revision=28869)

And of course looks like Jaunty is going to ship with build 65, not 60 as I mentioned before.

Andrew

---

### Post by Nullack on 2009-03-09
Mplayer is moving ahead. Todays compile is working on VDPAU for AVC, VC1, WMV2 and MPEG1/2. The NVIDIA 180.37 drivers have important fixes for GPU acceleration. Now we just need fixes for:


* Working motion adaptive temporal deinterlacer unlike the crappy simple one implemented currently
* MS WMA Pro decoding - this has been coming for ages and not delivered despite GSOC work on it


And I'll be really impressed if libavcodec ever gets a decoding feature for:

MS WMVP
MS WVP2
Intel IV41
Intel IV50

---

### Post by plun on 2009-03-10
> **Nullack said:**
> Mplayer is moving ahead. Todays compile is working on VDPAU for AVC, VC1, WMV2 and MPEG1/2. The NVIDIA 180.37 drivers have important fixes for GPU acceleration. 


Yup and I am impressed...:D

I saw your other thread and downloaded the demo from nearest file-sharing network....**Samsung.Demo.Oceanic.Life.x264.1080p.40Mbps.mkv**, 430MB

Wow !!!... some CPU fluctuations but overall perfect..:D

[[img]http://ubuntu-pics.de/thumb/10807/snapshot24_qWrzcK.png[/img]](http://ubuntu-pics.de/bild/10807/snapshot24_qWrzcK.png)

(8600GT, 180.37, latest mplayer-SMPlayer as GUI>VDPAU as output)

---

### Post by Nullack on 2009-03-10
Yes my friend :)

There is the power of VDPAU

In that file, you have AVC encoding, and to make matters extreme, its 1920x1080 at a bitrate of 40mbps!!

My old test system with its boat anchor AMD Sempron single core does it without breaking a sweat about 15% cpu utilisation. On the other hand my quad core corei7 system without vdpau cant do it........

---

### Post by Nullack on 2009-03-12
Just a heads up for a cool vdpinfo utility:

[http://www.nvnews.net/vbulletin/showthread.php?t=124978&highlight=vdpinfo](http://www.nvnews.net/vbulletin/showthread.php?t=124978&highlight=vdpinfo)

It queries the VDPAU capabilities of your system.

Heres my output as an example:

display: :0.0   screen: 0
API version: 0
Information string: Unknown

Video surface:

name   width height types
-------------------------------------------
420     4096  4096  NV12 YV12 
422     4096  4096  UYVY YUYV 

Decoder capabilities:

name          level macbs width height
------------------------------------
MPEG1             0  8192  2048  2048
MPEG2_SIMPLE      3  8192  2048  2048
MPEG2_MAIN        3  8192  2048  2048
H264_MAIN        41  8192  2048  2048
H264_HIGH        41  8192  2048  2048
VC1_SIMPLE        1  8190  2048  2048
VC1_MAIN          2  8190  2048  2048
VC1_ADVANCED      4  8190  2048  2048

Output surface:

name              width height nat types
----------------------------------------------------
B8G8R8A8          8192  8192    y  Y8U8V8A8 V8U8Y8A8 
R10G10B10A2       8192  8192    y  Y8U8V8A8 V8U8Y8A8 

Bitmap surface:

name              width height
------------------------------
B8G8R8A8          8192  8192
R8G8B8A8          8192  8192
R10G10B10A2       8192  8192
B10G10R10A2       8192  8192
A8                8192  8192

Video mixer:

feature name                    sup
------------------------------------
DEINTERLACE_TEMPORAL             y
DEINTERLACE_TEMPORAL_SPATIAL     y
INVERSE_TELECINE                 y
NOISE_REDUCTION                  y
SHARPNESS                        y
LUMA_KEY                         y

parameter name                  sup      min      max
-----------------------------------------------------
VIDEO_SURFACE_WIDTH              y         1     4096
VIDEO_SURFACE_HEIGHT             y         1     4096
CHROMA_TYPE                      y  
LAYERS                           y         0        4

attribute name                  sup      min      max
-----------------------------------------------------
BACKGROUND_COLOR                 y  
CSC_MATRIX                       y  
NOISE_REDUCTION_LEVEL            y      0.00     1.00
SHARPNESS_LEVEL                  y     -1.00     1.00
LUMA_KEY_MIN_LUMA                y  
LUMA_KEY_MAX_LUMA                y

---

### Post by Zorael on 2009-03-12
I'm trying to combine this guide with [this CoreAVC for Linux guide](http://ubuntuforums.org/showthread.php?t=1034075), since I have an MSI Wind, which can't play 720p content without CoreAVC.

Everything looks good so far, but I can't manage to pull mplayer from svn.
```
zorael@tleilax:~/coreavc$ svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer
svn: Can't connect to host 'svn.mplayerhq.hu': Connection timed out

zorael@tleilax:~/coreavc$ ping svn.mplayerhq.hu
PING svn.mplayerhq.hu (213.144.138.186) 56(84) bytes of data.
*<endless wait>*
^C
--- svn.mplayerhq.hu ping statistics ---
187 packets transmitted, 0 received, 100% packet loss, time 186745ms

zorael@tleilax:~/coreavc$ sudo tracert svn.mplayerhq.hu              
traceroute to svn.mplayerhq.hu (213.144.138.186), 30 hops max, 60 byte packets
 1  mail1.telia.com (10.0.0.1)  1.734 ms  3.275 ms  4.270 ms                  
 2  gw3-no27.tbcn.telia.com (81.232.154.1)  13.606 ms  14.607 ms  15.376 ms   
 3  s-bb2-link.telia.net (80.91.254.182)  30.601 ms  31.382 ms  32.341 ms     
 4  s-b1-link.telia.net (80.91.252.125)  33.408 ms  33.893 ms  34.980 ms      
 5  level3-117311-s-b3.telia.net (213.248.78.110)  35.688 ms  36.667 ms *     
 6  ae-5-5.ebr1.Dusseldorf1.Level3.net (4.69.140.198)  65.550 ms  53.023 ms  53.835 ms
 7  ae-2-2.ebr2.Frankfurt1.Level3.net (4.69.132.138)  51.758 ms  50.490 ms  51.122 ms 
 8  ae-7-7.car2.Zurich1.Level3.net (4.69.133.238)  57.129 ms * *                      
 9  ae-11-11.car1.Zurich1.Level3.net (4.69.133.233)  60.212 ms  59.159 ms  61.118 ms  
10  INIT-SEVEN.car1.Zurich1.Level3.net (213.242.67.54)  58.238 ms  67.164 ms  69.529 ms
11  r1zur2.core.init7.net (77.109.128.242)  57.740 ms  58.604 ms  60.766 ms
12  r1zba1.core.init7.net (77.109.128.206)  61.402 ms  62.151 ms  64.575 ms
13  r1zba1.ce.init7.net (77.109.128.178)  65.333 ms  66.064 ms  56.994 ms
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *
```
Any mirrors? :<

---

### Post by andrew.46 on 2009-03-12
Hi Zorael,

> **Zorael said:**
>  I can't manage to pull mplayer from svn.

Hmmm.... neither can I at the moment. Browsing via web is down also. I guess we just have to wait....

Andrew

---

### Post by Siggma on 2009-03-15
No quotes but I do have a question.

I've avoided using Linux until the horrible video tearing with ATI drivers is under control. Seems that milestone is being reached with the release of Jaunty. However, the alpha 6 dist is still quite green and quite slow, even incomplete. I need something more stable. So I installed Intrepid and upgraded to the xserver-xorg package from Jaunty to get the tear free video. It works OK, finally. Now I need to be able to use my game pad in Mplayer and something as simple as compiling mplayer becomes a nightmare. Apparently there are some big changes in the libc6,  libxi-dev and a few other packages that prevent me from satisfying compile requirements. 

I just want to be able to add joystick support. Can I compile mplayer on my debian 5.0 server and expect it to run under Jaunty?

-siggma

---

### Post by andrew.46 on 2009-03-15
Hi Siggma,

I am afraid that I have no answer for what sounds like a fairly complex compilation problem. I hope that perhaps others may have some insight into this problem.

Apologies,

Andrew

---

### Post by Siggma on 2009-03-15
> **andrew.46 said:**
> Hi Siggma,

I am afraid that I have no answer for what sounds like a fairly complex compilation problem. I hope that perhaps others may have some insight into this problem.

Apologies,

Andrew

NO biggie, mixing Jaunty and Intrepid repos is the problem. I'll just have to load a virtual copy of Intrepid to compile it I suppose. Thanks for the response and all the time and effort you've put into writing this and other threads.
-Tom

---

### Post by Nullack on 2009-03-15
Andrew I saw that the mplayer devs recommend using make distclean, especially before reporting any bugs.

---

### Post by andrew.46 on 2009-03-16
Hi Nullack,

> **Nullack said:**
> Andrew I saw that the mplayer devs recommend using make distclean, especially before reporting any bugs.

I think I saw that post with [Mr Hoyos on another forum]("http://www.nvnews.net/vbulletin/showthread.php?t=130079") :-). It is not perfect but I have tagged 'make distclean' on the *end* of the initial compilation. It starts getting messy if I also give 'svn up' instructions with 'make distclean' added in and I guess this way the svn tree should always be pretty clean.

I have a strong suspicion as well that many people use this guide to get a once off copy of MPlayer and never actually update this copy, which is fine as they have what they came for after all.

I was tossing up about the whole mencoder-x264 business before as x264 is a pain under Ubuntu and I am firmly convinced that encoding x264 is better with FFmpeg anyway. The option I was considering was:

```
$ ./configure --disable-mencoder --disable-x264 
```

which leaves h264 playback in place and rids MPlayer of an encoder that is not all that widely used. Plus means an end to all the compilation problems / package management issues with MPlayer under Ubuntu. But in the end I decided to present a 'vanilla' MPlayer install with MEncoder and x264 encoding available. 

I have no regrets about dumping gmplayer though :-).
  
Andrew

---

### Post by Nullack on 2009-03-16
Thanks mate

Um, does ffmpeg have an AVC encoder or does it use x264?

---

### Post by andrew.46 on 2009-03-16
Hi Nullack,

Easiest way is to run ./configure with no options on a fresh FFmpeg svn tree and you will see:

```

Enabled encoders:
ac3			mp2			pcm_u32be
adpcm_adx		mpeg1video		pcm_u32le
adpcm_g726		mpeg2video		pcm_u8
adpcm_ima_qt		mpeg4			pcm_zork
adpcm_ima_wav		msmpeg4v1		pgm
adpcm_ms		msmpeg4v2		pgmyuv
adpcm_swf		msmpeg4v3		png
adpcm_yamaha		nellymoser		ppm
alac			pam			qtrle
asv1			pbm			rawvideo
asv2			pcm_alaw		roq
bmp			pcm_f32be		roq_dpcm
dnxhd			pcm_f32le		rv10
dvbsub			pcm_f64be		rv20
dvdsub			pcm_f64le		sgi
dvvideo			pcm_mulaw		snow
ffv1			pcm_s16be		sonic
ffvhuff			pcm_s16le		sonic_ls
flac			pcm_s24be		svq1
flashsv			pcm_s24daud		targa
flv			pcm_s24le		tiff
gif			pcm_s32be		vorbis
h261			pcm_s32le		wmav1
h263			pcm_s8			wmav2
h263p			pcm_u16be		wmv1
huffyuv			pcm_u16le		wmv2
jpegls			pcm_u24be		zlib
ljpeg			pcm_u24le		zmbv
mjpeg

```

Now if someone could tell me what the hell pcm_zork is?

Andrew

---

### Post by Nullack on 2009-03-16
lol, maybe some bizzare format from the zork games?

I dont see an ffmpeg avc encoder from that list.

---

### Post by andrew.46 on 2009-03-16
Hi Nullack,

> **Nullack said:**
> I dont see an ffmpeg avc encoder from that list.

Exactly, you will see it appear when you compile against x264. But note the decoders available on a bare svn FFmpeg:

```

Enabled decoders:
aac			flashsv			pcm_u16le
aasc			flic			pcm_u24be
adpcm_4xm		flv			pcm_u24le
adpcm_adx		fourxm			pcm_u32be
adpcm_ct		fraps			pcm_u32le
adpcm_ea		gif			pcm_u8
adpcm_ea_maxis_xa	h261			pcm_zork
adpcm_ea_r1		h263			pcx
adpcm_ea_r2		h263i			png
adpcm_ea_r3		**[COLOR="Red"]h264[/COLOR]**			ptx
adpcm_ea_xas		huffyuv			qcelp
adpcm_g726		idcin			qdm2
adpcm_ima_amv		imc			qdraw
adpcm_ima_dk3		indeo2			qpeg
adpcm_ima_dk4		indeo3			qtrle
adpcm_ima_ea_eacs	interplay_dpcm		ra_144
adpcm_ima_ea_sead	interplay_video		ra_288
adpcm_ima_iss		jpegls			rawvideo
adpcm_ima_qt		kmvc			rl2
adpcm_ima_smjpeg	loco			roq
adpcm_ima_wav		mace3			roq_dpcm
adpcm_ima_ws		mace6			rpza
adpcm_ms		mdec			rv10
adpcm_sbpro_2		mimic			rv20
adpcm_sbpro_3		mjpeg			rv30
adpcm_sbpro_4		mjpegb			rv40
adpcm_swf		mlp			sgi
adpcm_thp		mmvideo			shorten
adpcm_xa		motionpixels		smackaud
adpcm_yamaha		mp1			smacker
alac			mp2			smc
amv			mp3			snow
ape			mp3adu			sol_dpcm
asv1			mp3on4			sonic
asv2			mpc7			sp5x
atrac3			mpc8			sunrast
avs			mpeg1video		svq1
bethsoftvid		mpeg2video		svq3
bfi			mpeg4			targa
bmp			mpeg_xvmc		theora
c93			mpegvideo		thp
cavs			msmpeg4v1		tiertexseqvideo
cinepak			msmpeg4v2		tiff
cljr			msmpeg4v3		truemotion1
cook			msrle			truemotion2
cscd			msvideo1		truespeech
cyuv			mszh			tscc
dca			nellymoser		tta
dnxhd			nuv			txd
dsicinaudio		pcm_alaw		ulti
dsicinvideo		pcm_dvd			vb
dvbsub			pcm_f32be		vc1
dvdsub			pcm_f32le		vcr1
dvvideo			pcm_f64be		vmdaudio
dxa			pcm_f64le		vmdvideo
eacmv			pcm_mulaw		vmnc
eatgq			pcm_s16be		vorbis
eatgv			pcm_s16le		vp3
eatqi			pcm_s16le_planar	vp5
eightbps		pcm_s24be		vp6
eightsvx_exp		pcm_s24daud		vp6a
eightsvx_fib		pcm_s24le		vp6f
escape124		pcm_s32be		vqa
ffv1			pcm_s32le		wavpack
ffvhuff			pcm_s8			wmav1
flac			pcm_u16be		wmav2
wmv1			ws_snd1			xsub
wmv2			xan_dpcm		zlib
wmv3			xan_wc3			zmbv
wnv1			xl

```

Same for muxers / demuxers : h264 is enabled in a bare-bones FFmpeg install. Hence in MPlayer you will have h264 decoding even if you pass --disable-x264 to MPlayer. (Not sure about the libavcodec option for x264 that seems to have appeared at some time: --disable-x264-lavc )

Andrew

---

### Post by Nullack on 2009-03-16
So Im confused as to what you mean mate by saying that encoding avd in ffmpeg is better?

I've now ditched the idea of using binary codecs for 64bit mplayer builds. I went through all the codec files and its only for realplayer. Since the codecs were done way back in 2007, ffmpeg has native realplayer support anyway. Realplayer technology is crap anyway. My ./configure is now:

./configure --prefix=/usr --confdir=/etc/mplayer

Theres also some great things coming. The wmapro decoder code is coming along and might soon be committed to ffmpeg. Also, some work is going on with vdpau deinterlacing and hopefully into the future we will get temporal spation deinterlacing accelerated on the GPU.....

Really, gstreamer and totem is crap in comparison to mplayer. Totem bugs go on for way too long without being fixed, such as the broken seeking in multi audio stream containers. And there is no deinterlacer at all. By statically linking ffmpeg and dvdnav into mplayer you have an easy way of keeping the significant players of multimedia on linux up to date in one swoop.

---

### Post by andrew.46 on 2009-03-17
Hi Nullack,

> **Nullack said:**
> So Im confused as to what you mean mate by saying that encoding avd in ffmpeg is better?

My apologies, I have had a bad week at work and as usual I have spoken less than clearly :-). I have found that FFmpeg is a better application than MEncoder for encoding *anything*. The syntax is much more intuitive to my mind, the program is better maintained, the presets make life so much easier and the FFmpeg guys have paid me big bucks to publicly support their product.

OK so maybe that last bit is not true :-).  Which program do you prefer yourself for media encoding / transcoding?

Andrew

---

### Post by Nullack on 2009-03-17
Its all good Andrew :)

I use a combination of x264, mencoder and ffmpeg.

---

### Post by Bakon Jarser on 2009-03-19
Thanks for the guide.  Didn't run into any problems compiling.  SMPlayer has an annoying bug though.  Every time the controls are displayed or disappear the desktop flashes for half a second.  I'm using the version in the repositories.  Maybe I'll check out the PPA and see if it's any better.

---

### Post by Nullack on 2009-03-19
Another great achievement by mplayer! Now they have added temporal spatial deinterlacing accelerated in hardware using VDPAU! Go mplayer :popcorn:

---

### Post by andrew.46 on 2009-03-19
Hi Bakon,

> **Bakon Jarser said:**
> Thanks for the guide.  Didn't run into any problems compiling.  SMPlayer has an annoying bug though.  Every time the controls are displayed or disappear the desktop flashes for half a second.  I'm using the version in the repositories.  Maybe I'll check out the PPA and see if it's any better.

Glad it all worked for you. The SMPlayer problem sounds a little odd, I cannot duplicate it here using the repository SMPlayer. So I am not sure about that one...

Andrew

---

### Post by rvm4000 on 2009-03-19
> **Bakon Jarser said:**
> Thanks for the guide.  Didn't run into any problems compiling.  SMPlayer has an annoying bug though.  Every time the controls are displayed or disappear the desktop flashes for half a second.  I'm using the version in the repositories.  Maybe I'll check out the PPA and see if it's any better.

If you mean the control that appears in fullscreen when the mouse is moved to the bottom of the screen, maybe this option may help: Preferences -> Interface -> Floating control -> Bypass window manager.

---

### Post by Bakon Jarser on 2009-03-19
> **rvm4000 said:**
> If you mean the control that appears in fullscreen when the mouse is moved to the bottom of the screen, maybe this option may help: Preferences -> Interface -> Floating control -> Bypass window manager.

It was already checked.  Unchecking it causes the controls to not display at all.

---

### Post by rvm4000 on 2009-03-19
> **Bakon Jarser said:**
> Unchecking it causes the controls to not display at all.

:-O

Are you using KDE-4?

---

### Post by Bakon Jarser on 2009-03-19
gnome 2.26
nvidia driver 180.37
geforce 6150se

Just to clarify, it flashes the desktop image, not the panels or any other open windows.  Turning off compiz fixes the problem.

---

### Post by Bakon Jarser on 2009-03-20
Looks like this might be a bug with compiz or gnome.  Flash player does the same thing when exiting full screen mode.

---

### Post by mgsfan on 2009-03-20
updated to the latest svn and compiled and I'm getting this error..make: *** [libswscale/libswscale.a] Error 2

previous svn updated and compiled fine before todays

---

### Post by andrew.46 on 2009-03-20
Hi mgsfan,

> **mgsfan said:**
> updated to the latest svn and compiled and I'm getting this error..make: *** [libswscale/libswscale.a] Error 2

Or more completely:

```

swscale.c: In function 'sws_getContext':
swscale.c:2777: error: 'CONFIG_SWSCALE_ALPHA' undeclared (first use in this function)
swscale.c: In function 'sws_freeContext':
swscale.c:3338: error: 'CONFIG_SWSCALE_ALPHA' undeclared (first use in this function)
swscale.c: In function 'sws_getCachedContext':
swscale.c:3390: warning: assignment discards qualifiers from pointer target type
make[1]: *** [swscale.o] Error 1
make[1]: Leaving directory `/tmp/mplayer/libswscale'
make: *** [libswscale/libswscale.a] Error 2
root@skamandros/home/andrew/source/mplayer# 

```

which I suspect means that MPlayer compilation is broken for a little while. It is something of a PITA as well that web browsing of the svn is turned off at the moment as well.

Andrew

---

### Post by Nullack on 2009-03-20
The devs try to keep svn buildable and robust - like all complex software it doesnt work out that way all the time. Sometimes its just a mastter of synching a few hours later to svn again, if not, ping them on IRC about it.

---

### Post by andrew.46 on 2009-03-21
Hi,

Compilation error corrected in 29019:

```

andrew@skamandros~/source/mplayer/mplayer$ svn -r 29019 log
------------------------------------------------------------------------
r29019 | diego | 2009-03-21 20:18:36 +1100 (Sat, 21 Mar 2009) | 2 lines

Add CONFIG_SWSCALE_ALPHA and HAVE_VIRTUALALLOC config.h #defines for FFmpeg.

------------------------------------------------------------------------

```

Andrew

---

### Post by psychok9 on 2009-03-21
moved sorry

---

### Post by andrew.46 on 2009-03-21
Hi psychok9,

> **psychok9 said:**
> moved sorry

It is a great sign that there seem to be several actively maintained MPlayer threads at the moment, leading to some confusion :-). Still waiting however for someone to write and maintain a guide for using MPlayer with the [experimental multithreaded FFmpeg-mt branch]("http://gitorious.org/projects/ffmpeg/repos/ffmpeg-mt").
[B]
Edit:[/B] I am of course an idiot:

HOWTO: Compiling mplayer with multi-core decoding support
[http://ubuntuforums.org/showthread.php?t=1049449](http://ubuntuforums.org/showthread.php?t=1049449)

Can't even blame night shift for forgetting that I have already seen and posted on this thread :-)

Andrew

---

### Post by Nullack on 2009-03-21
Andrew, video decoding is far more suitable to GPU acceleration than multi core CPU decoding. While people are free to do whatever they want, the best path is for the community to focus on GPU acceleration in guides.

---

### Post by andrew.46 on 2009-03-22
Hi Nullack,

> **Nullack said:**
> Andrew, video decoding is far more suitable to GPU acceleration than multi core CPU decoding. While people are free to do whatever they want, the best path is for the community to focus on GPU acceleration in guides.

I would have to cordially disagree for several reasons. Firstly not everybody actually *has* a suitable video board that will benefit from the recent advances made by nvidia and MPlayer, I know that I fall into that category myself. 

Secondly I think it is a great thing that advances in video decoding should happen on *multiple* fronts and if Ubuntu can be involved in this process, even if only as end-users, all the better. Plus this reinforces the Linux idea of *choice* and if such a choice can be found on these forums again all the better.


Mind you none of this will have any effect on *this* guide which I suspect will remain focused on producing a more 'middle of the road' version of MPlayer. Which I will have to admit fits in pretty much with my own usage of MPlayer.

Andrew

**Edit:** I am of course an idiot as I mentioned a couple of posts back:

HOWTO: Compiling mplayer with multi-core decoding support
[http://ubuntuforums.org/showthread.php?t=1049449](http://ubuntuforums.org/showthread.php?t=1049449)

---

### Post by Nullack on 2009-03-22
Yes mate, I understand your reasons. Simply, it wont ever work as well as GPU acceleration and in some cases with more complex video codecs it wont work at all, but as you say, thats choice. The architecture of multi core cpu decoding for video is inherently flawed for the task until we get a massive number of cpu cores onto a cpu chip.

When it comes to cost - the cost of a single core cpu and a VDPAU compatible gpu card is comparable / in some cases cheaper than a dual or quad core more advanced cpu with one of the more crappy integrated video chips. I know which combination will decode 1920x1080 high profile AVC with spatial temporal deinterlacing with next to no cpu utilisation :)

---

### Post by Nullack on 2009-03-22
Folks a small bit of info on VDPAU gpu accelerated deinterlacing. These are the available deinterlacing options:

deint=<0&#8722;4>
	
Chooses the deinterlacer (default: 0). All modes > 0 respect &#8722;field&#8722;dominance.
NOTE: Values > 2 delay the video output by one frame.
	
0 - No deinterlacing.

1 - Show only first field, similar to &#8722;vf field.
	
2 - Bob deinterlacing, similar to &#8722;vf tfields=1.
	
3 - Motion adaptive temporal deinterlacing. May lead to A/V desync with slow video hardware and/or high resolution.** This is the default if "D" is used to enable deinterlacing.**
	
4 - Motion adaptive temporal deinterlacing with edge-guided spatial interpolation. Needs fast video hardware.

So an example of the syntax could be:

mplayer -vo vdpau:deint=4 -vc ffmpeg12vdpau MPEGIO3MBPS30sec.mpg 

The list of VDPAU supported codecs is:

mplayer -vo vdpau -vc ffmpeg12vdpau

mplayer -vo vdpau -vc ffh264vdpau

mplayer -vo vdpau -vc ffwmv3vdpau

mplayer -vo vdpau -vc ffvc1vdpau

For in order:

mpeg1 and mpeg 2, AVC/H.264, wmv3, VC-1

---

### Post by hype on 2009-03-22
VDPAU works quite good.
I also particularly enjoy fonts in Mplayer latetly.
Looks really sharp.

---

### Post by ktp on 2009-03-22
If you don't want to build, then you can find builds on this PPA
[https://launchpad.net/~rvm4000/+archive/ppa](https://launchpad.net/~rvm4000/+archive/ppa)

---

### Post by Nullack on 2009-03-23
Keep in mind if you use someone elses binary you loose the cpu specific optimisations that come from march=native and mtune=native in the compile. Additionally, your configure options maybe different to the person who compiled it. e.g. Schrodinger encoding or vdpau vo.

What are people doing with their mplayer.conf file in the /etc/mplayer dir?

Heres mine as an example:

```
# mplayer config file version 0.1 23/03/09
#

# global setup

vo=vdpau
ao=pulse
nolirc=true
nojoystick=true

# DVD navigation

[protocol.dvdnav]
profile-desc="profile for dvdnav:// streams"
mouse-movements=yes
nocache=yes

```

---

### Post by andrew.46 on 2009-03-26
Hi,

It may be of little interest to Jaunty users but I have spent a little time reorganizing my MPlayer guides on these forums. Courtesy of a push in the right direction by FakeOutdoorsman I am now running Hardy Heron, Intrepid Ibex and Jaunty Jackalope in VirtualBox and I have just finished a little spring cleaning of the 3 guides I now aim to support until their official 'end-of-life' dates:

[Howto] Successfully install the svn MPlayer under Hardy Heron
[http://ubuntuforums.org/showthread.php?t=558538](http://ubuntuforums.org/showthread.php?t=558538)

[Howto] Install the svn Mplayer under Intrepid Ibex
[http://ubuntuforums.org/showthread.php?t=1024592](http://ubuntuforums.org/showthread.php?t=1024592)

HowTo: Install the very latest MPlayer under Jaunty Jackalope
[http://ubuntuforums.org/showthread.php?t=1081070](http://ubuntuforums.org/showthread.php?t=1081070) 

Just needs a final spring-clean of each guide, which I shall undertake over the next few weeks, and following the release of Jaunty a move to the tutorial section of the forums for the Jaunty guide.

And I think that will do me for the svn MPlayer under Ubuntu in terms of disk space for virtual machines and time needed on the forums for support/tinkering of/with the guides. My apologies to the Karmic Koala :-).

Now for that guide I would like to write on 'find'....

Andrew

---

### Post by NorQue on 2009-03-30
Thanks a lot for the guide, andrew. Works great for me.

I have one problem, though: in every .mkv i have that has embedded SSA/*** subtitles (which, by coincidence, are pretty much all of them ;) ) I can't switch off subtitles anymore. Usually this works with mplayer by pressing 'v' during playback, but not anymore. Presing 'v' now only adds another layer of subtitles over the already shown one. Anyone has a hint on what I'm doing wrong?

TiA :)

EDIT:
Looks like we're not supposed to use that other abbreviation for subtitles in sub station alpha format. :P

EDIT #2:
Okay, looks like they're gone when I disable them via smplayer GUI, but then they can't be switched on when I'm launching mplayer via command-line. Better than nothing, I suppose. :)

---

### Post by andrew.46 on 2009-03-30
Hi NorQue,

> **NorQue said:**
> Thanks a lot for the guide, andrew. Works great for me.

Great news, especially since I cannot get Jaunty beta running in VirtualBox at the moment and cannot test any Jaunty related problems :-).

> I have one problem, though: in every .mkv i have that has embedded SSA/*** subtitles (which, by coincidence, are pretty much all of them ;) ) I can't switch off subtitles anymore. Usually this works with mplayer by pressing 'v' during playback, but not anymore. Presing 'v' now only adds another layer of subtitles over the already shown one. Anyone has a hint on what I'm doing wrong?

My knowledge of subtitles and MPlayer is next to zero but I have used the following file:

[http://samples.mplayerhq.hu/Matroska/mewmew/mewmew-vorbis-ssa.mkv](http://samples.mplayerhq.hu/Matroska/mewmew/mewmew-vorbis-ssa.mkv)

and using this file I can turn the subtitles on and off using the 'v' key and cycle through the available subtitles using the 'j' key, all from the commandline. Can you test this file?

I am using the following:

```
andrew@skamandros~$ mplayer | head -n 1
MPlayer SVN-r29078-4.2.4 (C) 2000-2009 MPlayer Team
```

and I attach a couple of screenshots of the crazy Japanese anime with subtitles on and off.

All the best,

Andrew

---

### Post by NorQue on 2009-03-31
Strange. Today I can't replicate that issue, neither with your file, nor with my own. Yesterday *every single time* the SSA rendered subtitles were displayed when they were switched on in smplayer, no chance to turn them off when run from comand line. Today it woks like a charm. Sorry for bothering you, seems like all that was needed was a reboot (or some sleep, or me excessively swearing, no idea...). Best to file it under "Layer 8 problem".

---

### Post by forcecore on 2009-03-31
sometimes mplayer wont close and stays on processes, i do not know this too is that sound hissing sometimes caused by mplayer or alsa (i use smplayer always for GUI)

i have fresh complete mplayer offline .deb-s too

---

### Post by andrew.46 on 2009-04-01
Hi forecore,

> **forcecore said:**
> sometimes mplayer wont close and stays on processes, i do not know this too is that sound hissing sometimes caused by mplayer or alsa (i use smplayer always for GUI)

i have fresh complete mplayer offline .deb-s too

I am afraid that I cannot reproduce your problem and I am not sure how to troubleshoot this issue. Apologies!

Andrew

---

### Post by psychok9 on 2009-04-02
Today i've got this problem:
```
make[1]: Entering directory `/home/gianluca/auto/mplayer/libavcodec'
cc -DHAVE_AV_CONFIG_H -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -I.. -I.. -Wundef -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -std=gnu99 -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -I.  -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT   -D_REENTRANT   -Ilibdvdread4  -I/usr/include/freetype2 -I/usr/include   -I/usr/include/schroedinger-1.0 -I/usr/include/liboil-0.3   -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -c -o allcodecs.o allcodecs.c
allcodecs.c: In function 'avcodec_register_all':
allcodecs.c:57: error: 'CONFIG_H263_VAAPI_HWACCEL' undeclared (first use in this function)
allcodecs.c:57: error: (Each undeclared identifier is reported only once
allcodecs.c:57: error: for each function it appears in.)
allcodecs.c:58: error: 'CONFIG_MPEG2_VAAPI_HWACCEL' undeclared (first use in this function)
allcodecs.c:59: error: 'CONFIG_MPEG4_VAAPI_HWACCEL' undeclared (first use in this function)
make[1]: *** [allcodecs.o] Error 1
make[1]: Leaving directory `/home/gianluca/auto/mplayer/libavcodec'
make: *** [libavcodec/libavcodec.a] Error 2

```

I hope next release can fix it :)
I've tried "./configure --codecsdir=/usr/lib/codecs --confdir=/etc/mplayer --disable-vdpau" without change/success.

---

### Post by andrew.46 on 2009-04-02
Hi psychik9,

> **psychok9 said:**
> Today i've got this problem

I missed that one but revision 29134 compiled ok for me. Perhaps this fixed the problem:

```

andrew@skamandros~/source/mplayer/mplayer$ svn log -r 29130
------------------------------------------------------------------------
r29130 | cehoyos | 2009-04-03 05:38:15 +1100 (Fri, 03 Apr 2009) | 1 line

Fix compilation with libavcodec's HWACCEL.
------------------------------------------------------------------------

```

I wish the web interface for the MPlayer svn would come back up!!

Andrew

---

### Post by psychok9 on 2009-04-02
> **andrew.46 said:**
> Hi psychik9,



I missed that one but revision 29134 compiled ok for me. Perhaps this fixed the problem:

```

andrew@skamandros~/source/mplayer/mplayer$ svn log -r 29130
------------------------------------------------------------------------
r29130 | cehoyos | 2009-04-03 05:38:15 +1100 (Fri, 03 Apr 2009) | 1 line

Fix compilation with libavcodec's HWACCEL.
------------------------------------------------------------------------

```

I wish the web interface for the MPlayer svn would come back up!!

Andrew

I'll try it tomorrow, very thank you andrew ;)

---

### Post by ajunsum on 2009-04-03
thanks! worked 100%!

---

### Post by andrew.46 on 2009-04-03
Hi ajunsum,

> **ajunsum said:**
> thanks! worked 100%!

Excellent news :-). I hope that the majority of people sail through this guide with no problem, most only post when there is a problem I suspect. Anyway all the best with your new copy of MPlayer and MEncoder!

Andrew

---

### Post by psychok9 on 2009-04-06
Your guide is perfect! Thank you for your work!
The old bug is fixed :)

You know if last svn mplayer, support multithread decoding? I've found a guide for get ffmpeg-mt libraries, but I can't understand the difference with main mplayer/ffmpeg.

---

### Post by andrew.46 on 2009-04-07
Hi psychok9,

> **psychok9 said:**
> Your guide is perfect! Thank you for your work!


Well, it is not perfect but I think it is definitely ready for the release of Jaunty Jackalope. It has been good to have a little preparation time before everybody installs the release version and then thinks 'Hmmm.... now to install MPlayer.....'

> You know if last svn mplayer, support multithread decoding? I've found a guide for get ffmpeg-mt libraries, but I can't understand the difference with main mplayer/ffmpeg.

I believe that the stock version (=this guide) supports limited multiple threads within a single process for MPEG-1/2 and H.264 only (-lavdopts threads=n where 'n' can be 1-8). I gather the FFmpeg-MT project greatly extends this but I have not used this and have no great knowledge of the project except that it exists :-). Just be aware that if you use FFmpeg-MT you will be even closer to the bleeding edge than this guide takes you.

I believe also that decoding by hardware cards is what you should really be looking at and vdpau is the flavour of the month. In a sure demonstration that I am losing touch with modern developments I don't have such a card and have not experimented with this. Oh well.....

All the best,

Andrew

---

### Post by Nullack on 2009-04-07
So, your using the SVN mplayer and the static links to the SVN FFMPEG libraries that mplayer pulls in. But you lack WMA Pro decoding. Here's the solution :KS:popcorn::guitar::p;)

```

cd ~/src/mplayer
svn checkout svn://svn.ffmpeg.org/soc/wmapro wmapro
cp wmapro/wma* libavcodec
patch -p0 <wmapro/audioframesize.patch
patch -p0 <wmapro/mplayer.patch
patch -p0 <wmapro/wmapro_ffmpeg.patch

```

This summer of code google project works well. Havent found any bugs so far.

---

### Post by andrew.46 on 2009-04-08
Hi Nullack,

> **Nullack said:**
> So, your using the SVN mplayer and the static links to the SVN FFMPEG libraries that mplayer pulls in. But you lack WMA Pro decoding. Here's the solution :KS:popcorn::guitar::p;)[...]

Great news Nullack. I see that work has been going on this one for many months now and a quick peek at FFmpeg-soc shows that work is still continuing:

[http://lists.mplayerhq.hu/pipermail/ffmpeg-soc/2009-April/thread.html](http://lists.mplayerhq.hu/pipermail/ffmpeg-soc/2009-April/thread.html)

I can see that you have a taste for the bleeding edge :-).

All the best,

Andrew

---

### Post by Nullack on 2009-04-09
Yes my friend it is bleeding edge but its proving to be quite robust actually.

If we look at the recent commits into SVN, we find that its doxygen related fluff and some bike shedding relating to putting c functions into different areas. This is the same sort of fluff that goes on in many commits for the main ffmpeg branch.

---

### Post by c-m on 2009-04-11
this worked for me in 8.10 but does not install in Jaunty 9.04 

```
carl@carl-laptop:~$ sudo checkinstall -D --install=yes --fstrans=no --pakdir "$HOME/Desktop" \
> --pkgname mplayer --backup=no --deldoc=yes --deldesc=yes --delspec=yes --default \
> --pkgversion "3:1.0~svn-`grep "#define VERSION" version.h | cut -d"-" -f2`"
grep: version.h: No such file or directory

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

*** No known documentation files were found. The new package 
*** won't include a documentation directory.

*****************************************
**** Debian package creation selected ***
*****************************************

*** Warning: The package version "3:1.0~svn-" is not a
*** Warning: debian policy compliant one. Please specify an alternate one

This package will be built according to these values: 

0 -  Maintainer: [ root@carl-laptop ]
1 -  Summary: [ Package created with checkinstall 1.6.1 ]
2 -  Name:    [ mplayer ]
3 -  Version: [ 0 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ carl ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]
11 - Provides: [ mplayer ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make...Installing with install...

========================= Installation results ===========================
make: *** No rule to make target `install'.  Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.
     
```

can anyone help? At the moment i have nothing that can play movie files

---

### Post by andrew.46 on 2009-04-11
Hi c-m,

For some reason the file version.h, which is generated during make by version.sh, has not been detected:

> **c-m said:**
> this worked for me in 8.10 but does not install in Jaunty 9.04 
```
carl@carl-laptop:~$ sudo checkinstall -D --install=yes --fstrans=no --pakdir "$HOME/Desktop" \
> --pkgname mplayer --backup=no --deldoc=yes --deldesc=yes --delspec=yes --default \
> --pkgversion "3:1.0~svn-`grep "#define VERSION" version.h | cut -d"-" -f2`"
**[COLOR="Red"]grep: version.h: No such file or directory[/COLOR]**

```

There could be a few reasons that this file is not generated but I have a strong suspicion that you may not have been in the right location when you issued the command. If you have followed the guide exactly your source files should be in $HOME/mplayer while your prompt:

```
carl@carl-laptop:~$
```

looks like $HOME. This is more than likely the problem. Have a look at this section of the guide:
```

$ sudo apt-get install subversion
**[COLOR="Red"]$ cd $HOME[/COLOR]**
$ svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer
**[COLOR="Red"]$ cd $HOME/mplayer[/COLOR]**
$ ./configure --codecsdir=/usr/lib/codecs --confdir=/etc/mplayer
$ make
$ sudo checkinstall -D --install=yes --fstrans=no --pakdir "$HOME/Desktop" \
--pkgname mplayer --backup=no --deldoc=yes --deldesc=yes --delspec=yes --default \
--pkgversion "3:1.0~svn-`grep "#define VERSION" version.h | cut -d"-" -f2`"
$ make distclean
```

and you can see where the navigation lies (in red). If this does not resolve the problem could you run a simple search:

```
find $HOME -iname 'version.h'
```

and this might help.

Andrew

---

### Post by Nullack on 2009-04-12
SVN is borked due to a bad ffmpeg mmx commit. Hopefully it will be fixed soon.

---

### Post by andrew.46 on 2009-04-12
Revision: 29175 still broken .......

Andrew

**Edit:** r29176 is right to go :-).

---

### Post by Nullack on 2009-04-14
Andrew I am trying to fix a problem. The issue is its somewhat impractical to have to manually setup a link to every user's home directory for the TTF font. I'm using a global configuration file to make the mplayer experience consistent across all users in /etc/mplayer/mplayer.conf:

```

# mplayer config file version 0.2 15/04/09
#

# global setup

vo=vdpau
ao=pulse
nolirc=true
nojoystick=true
font=/usr/share/fonts/truetype/ttf-bitstream-vera/Vera.ttf

# DVD navigation

[protocol.dvdnav]
profile-desc="profile for dvdnav:// streams"
mouse-movements=yes
nocache=yes
```

Even though I have the font correctly defined mplayer spits out:

```
MPlayer SVN-r29180-4.3.3 (C) 2000-2009 MPlayer Team
/usr/share/fonts/truetype/ttf-bitstream-vera/Vera.ttf doesn't look like a bitmap font description, ignoring.
Cannot load bitmap font: /usr/share/fonts/truetype/ttf-bitstream-vera/Vera.ttf
```

Thanks for any help :)

---

### Post by andrew.46 on 2009-04-15
Hi Nullack,

> **Nullack said:**
> Andrew I am trying to fix a problem. The issue is its somewhat impractical to have to manually setup a link to every user's home directory for the TTF font. I'm using a global configuration file to make the mplayer experience consistent across all users in /etc/mplayer/mplayer.conf:

```
font=/usr/share/fonts/truetype/ttf-bitstream-vera/Vera.ttf
```


You could try:

```
sudo ln -s /usr/share/fonts/truetype/ttf-bitstream-vera/Vera.ttf /etc/mplayer/subfont.ttf
```

Not quite what you were after but it should work as well.

All the best,

Andrew

---

### Post by Nullack on 2009-04-15
Thanks mate. Thats a good suggestion. I gave it a go, I can confirm the /etc/mplayer dir has the subfont in it now. I took out the mplayer.conf font= line so that it did not interfere with the new font.

However mplayer isnt happy:

```
MPlayer SVN-r29180-4.3.3 (C) 2000-2009 MPlayer Team

Playing 1Video_2Audio_2SUBs(timed text streams).mp4.
libavformat file format detected.
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
[lavf] Audio stream found, -aid 2
[lavf] Subtitle stream found, -sid 0
[lavf] Subtitle stream found, -sid 1
VIDEO:  [mp4v]  688x320  24bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
FAAD: compressed input bitrate missing, assuming 128kbit/s!
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
[pulse] working around probably broken pause functionality,
        see http://www.pulseaudio.org/ticket/440
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 688 x 320 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 2.15:1 - prescaling to correct movie aspect.
VO: [vdpau] 688x320 => 688x320 Planar YV12 
New_Face failed. Maybe the font path is wrong.
Please supply the text font file (~/.mplayer/subfont.ttf).
subtitle font: load_sub_face failed.
New_Face failed. Maybe the font path is wrong.
Please supply the text font file (~/.mplayer/subfont.ttf).
subtitle font: load_sub_face failed.
```

What Im after is a way to fix the problem of having to setup a font for every user that has and possibly might be added to my system. I want to globally apply the font so any future users are fine.

---

### Post by andrew.46 on 2009-04-15
Hi Nullack,

Hmmm... that *should* have worked. I am out of ideas, perhaps the mplayer-users might help out with this one?

Andrew

---

### Post by andrew.46 on 2009-04-16
Hi again Nullack,

I am an idiot and please feel free to remind me of the time I gave wrong advice. The path for the system font should in fact be:

```
$PREFIX/share/mplayer/subfont.ttf
```

So if you did *not* specify $PREFIX in your compiling you will need to create the appropriate directory and place the link there:

```

$ sudo mkdir -pv /usr/local/share/mplayer
$ sudo ln -s /usr/share/fonts/truetype/ttf-bitstream-vera/Vera.ttf /usr/local/share/mplayer/subfont.ttf
```

If you specified './configure --prefix=/usr' you will need to drop the 'local' bit from the commands of course. I tested this on Jaunty and it works. My apologies for misleading you there, my only excuse is that I am learning as well :-).

All the best,

Andrew

---

### Post by bapoumba on 2009-04-17
Moved to T&T.

---

### Post by andrew.46 on 2009-04-17
Hi bapoumba,

> **bapoumba said:**
> Moved to T&T.

Thank you very much or your trouble,

Andrew

---

### Post by sephiroth135 on 2009-04-19
Just to help others, the current latest release r29203 won't compile. The latest version that compiled for me was r29190. I'm using a freshly installed Ubuntu Jaunty RC amd64.

By the time someone reads this message it maybe fixed since from when I noticed the error (r29198 ) to when I found the latest that worked (r29190 ), the latest release had become r29203.

Just change the svn line to:
svn checkout -r 29190 svn://svn.mplayerhq.hu/mplayer/trunk mplayer

for now if you are having the compile issues with the latest.

---

### Post by andrew.46 on 2009-04-19
Hi sephiroth135,

> **sephiroth135 said:**
> Just to help others, the current latest release r29203 won't compile. The latest version that compiled for me was r29190. I'm using a freshly installed Ubuntu Jaunty RC amd64.

Thanks for the warning :-). Looks like the web interface for the svn repository is going to be down for some time. Those who like to have a look at the change logs to track fixes for broken compilation might find a use for a quick and dirty script I whipped up that will give the log files for the last 6 revisions:

```

[.......]

```

**Edit:** Once again I am an idiot. See next post...

Andrew

---

### Post by andrew.46 on 2009-04-19
Hi,

Or rather than the previous ornate script:

```
svn log -l 6 svn://svn.mplayerhq.hu/mplayer/trunk
```

Sigh...........

Andrew

---

### Post by dot2kode on 2009-04-20
@andrew.46

Followed your tutorial and everything worked perfectly...Thanks alot for taking the time and putting this up...Exactly what Linux needs is user's that put these tutorials together and help answer questions people have...I ran through it on a virtualbox Jaunty rc1 with no problems and did it on my 'real' jaunty install...Thanks again!! \\:D/

p.s. I'll revert to an older session and do video of your tutorial...Installed some of the 'record my desktop' software and need something to actually record ;)

BTW I played .mkv 720 and 1080's just fine and of course .avi's

---

### Post by andrew.46 on 2009-04-21
Hi dot2kode,

> **dot2kode said:**
> 
Followed your tutorial and everything worked perfectly...Thanks alot for taking the time and putting this up...Exactly what Linux needs is user's that put these tutorials together and help answer questions people have...I ran through it on a virtualbox Jaunty rc1 with no problems and did it on my 'real' jaunty install...Thanks again!! \\:D/

I am glad to hear that it all ran well. I sometimes forget that for the most part people get through this guide with no problems, mostly people post if they have problems. So thanks for taking the time to report success :-).

> p.s. I'll revert to an older session and do video of your tutorial...Installed some of the 'record my desktop' software and need something to actually record ;)

Don't be too alarmed when you find that this software produces theora video amd vorbis sound wrapped in an ogg media container :-).

All the very best,

Andrew

---

### Post by NorQue on 2009-04-21
Lately mplayer doesn't seem to want to take Video via standard input anymore. I used to play .rar'ed Videos via unrar and piping output to mplayer, but since a few days this produces only repeated messages like that:
```
user@comp:~/Downloads/videos/videodir$ unrar p -inul video.rar|mplayer -
MPlayer SVN-r29218-4.3.3 (C) 2000-2009 MPlayer Team

Playing -.
Reading from stdin...
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
[...]
Exiting... (End of file)
```Unluckily I forgot to note which SVN Version this first happened with, but with the one from [three weeks ago](http://ubuntuforums.org/showpost.php?p=6984357&postcount=82) it still worked.

Is that a mplayer bug or did I do something stupid somewhere? Any input? What should I do if it's a bug? There a, umh, guide for filing bug reports?

---

### Post by rvm4000 on 2009-04-21
> **NorQue said:**
> What should I do if it's a bug? There a, umh, guide for filing bug reports?

[http://www.mplayerhq.hu/DOCS/HTML/en/bugreports.html](http://www.mplayerhq.hu/DOCS/HTML/en/bugreports.html)

---

### Post by andrew.46 on 2009-04-21
Hi NorQue,

> **NorQue said:**
> Lately mplayer doesn't seem to want to take Video via standard input anymore. I used to play .rar'ed Videos via unrar and piping output to mplayer, 

I can confirm this problem with the current svn. RVM has given you the details for a full bug report but it would be useful if you are serious about getting a good bug report to do some regression testing:

[http://www.mplayerhq.hu/DOCS/HTML/en/bugreports_regression_test.html](http://www.mplayerhq.hu/DOCS/HTML/en/bugreports_regression_test.html)

If you can isolate the *exact* update that killed this functionality it should be a trivial matter to repair it. If you can write the patch yourself all the better :-).

Can I suggest if you go ahead with this that you spend a little time lurking on MPlayer-users and the developer mailing list *before* posting? The developers are busy, highly focussed people and often have little tolerance for those who broke unwritten and written rules of posting.

All the best,

Andrew

---

### Post by andrew.46 on 2009-04-21
Hi again NorQue!

Looks like for some clips MPlayer needs a cache setting if you are going to pipe in this way. I have had success doing this, see attached screenshot, so try a setting like:

```
$ unrar p -inul video.rar | mplayer -cache 2048 -
```

and I would be surprised if this did not work.

All the best,

Andrew

---

### Post by NorQue on 2009-04-22
Yepp, that cache setting did the trick, thanks a lot! :)

Still, I'm wondering why it worked so long without it, I've been using that command (in a nautilus script for easier accesability) for more than a year now.

---

### Post by andrew.46 on 2009-04-22
Hi NorQue,

> **NorQue said:**
> Yepp, that cache setting did the trick, thanks a lot! :)

Still, I'm wondering why it worked so long without it, I've been using that command (in a nautilus script for easier accesability) for more than a year now.

Glad that helped. It is a great example of at least part of the reason that I write this and other guides: I did not know that unrar existed before your post so I have learnt something very useful from your question :-). But somebody much more clever than me would have to work out what has changed to make MPlayer need some cache in this way...

All the very best,

Andrew

---

### Post by Nullack on 2009-04-25
Andrew thanks very much for the fix :) You sir are no idiot, your a generous and caring individual that is a true example of Ubuntu's spirit.

Putting the font in a global area IMHO is better as it makes the config correct for all users out of the box.

Seems mplayer SVN is having some problems at the moment:

```
nullack@PPP:~/src/mplayer$ svn update
svn: Unknown hostname 'svn.mplayerhq.hu'
```

---

### Post by andrew.46 on 2009-04-25
Hi Nullack,

> **Nullack said:**
> Andrew thanks very much for the fix :) You sir are no idiot, your a generous and caring individual that is a true example of Ubuntu's spirit.

Thanks for your kind words. It is perhaps just as well that you did not witness my 3 hour session of abusing Jaunty, Ubuntu, Canonical and Mark Shuttleworth in turn as I struggled to get mouse integration working with VirualBox and Jaunty guest :-).

All the very best,

Andrew

---

### Post by mc4man on 2009-04-25
> on 64bit systems but I believe that these systems require another set of codecs that can be downloaded here

Just a little aside on those codecs linked
There are only 3 .so's in the pack, all I believe related to real audio or video

There is an additional 6 .so's available but only in the mplayer-extras-codecs......x86_64.rpm

Again I believe they're all ra and rm related, as to their value I don't know.

If desired, with the package 'rpm' installed they can be dl'ed and extracted with archive manager
screen shows the add. .so's

---

### Post by Nullack on 2009-04-25
mc4man Im on x64. Have a look through the thread history for discussion.

Basically, you dont need any binary codecs for x64. FFMPEG has cook in it, which works and has recently gotten updates in the ffmpeg SVN if you look at the changelog. Mplayer pulls in many ffmpeg libraries as a static lib during the build process.

Only thing thats really missing is WMA Pro decoder support but I provide a way to compile the google summer of code ffmpeg/mplayer patches to do this with.

---

### Post by mc4man on 2009-04-26
> Basically, you dont need any binary codecs for x64

I would absolutely agree, was just commenting on the part of the how to that mentioned adding them (I always considered them somewhat worthless

> Only thing thats really missing is WMA Pro decoder support

Yeah I've done that thanks to your post mentioning the patch, works very well.

(solely commenting on the patch in** 8.10)**
  
- about 10 days ago I built some users a patched mplayer debian package set and the build sailed thru, mplayer built, installed and works fine, both here and for the 2 people i was building for

Then several days ago tried  again with a build geared more for myself and kept encountering an error(s) during the compile with wma3dec.o.(wma3dec.c

The basis for the errors was the lack of a bitstream.h (basically nowhere to be found

From wma3dec.c in wmapro
> #include "avcodec.h"
#include "bitstream.h"
#include "wma3.h"
#undef NDEBUG
#include <assert.h>


While of no probable value also tried patching ffmpeg itself, both a svn, a couple of -r's and using the checkout.sh contained in the wmapro folder.
Exact same build failure

A workaround is shown here, both mplayer and ffmpeg compile with the patch and perform as expected, any comments, or other solutions would be welcome

[http://ubuntuforums.org/showthread.php?p=7123598#post7123598](http://ubuntuforums.org/showthread.php?p=7123598#post7123598)

(noting I haven't retried since then with later versions than shown




I do think it would be nice if wmal is someday included

---

### Post by paxmark1 on 2009-05-05
Hi, I don't ask for help that often.

I am tracking via svn ffmpeg and mplayer.  Using this guide as my start I ./configure make and sudo make install awhile back and mplayer (but not smplayer) works well and acesses ffmpeg.  This is the best I have ever seen mplayer on any of my machines.  I will never go back to the stock version.  This with a 64 bit processor and onboard intel GPU

I am not able to "make" either ffmpeg or mplayer for the updates.

Consistently for over a week of trying I get for a borked make

No rule to make target `libavcodec/bitstream.h', needed by `libavformat/mpegtsenc.o'.  Stop.    this is for both ffmpeg and mplayer.  

I have in /usr/local/lib/codec the all-20071007 and essential-amd-20071007 and no others

bitstream.h is located in /usr/local/gpac/bitstream.h

Any help would be appreciated,  peace,  mark

at the end.  

I compile ffmpeg with --enable-gpl and --enable-nonfree

I have googled a bit but not luck.

---

### Post by FakeOutdoorsman on 2009-05-05
Did you uninstall FFmpeg and MPlayer, *make distclean*, and then update?  The following guide has a section dedicated to updating your SVN FFmpeg installation:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by paxmark1 on 2009-05-05
make distclean was my missing step.  Thanks.  I haven't compiled much since I gave Mandrake-driva the boot.  

I didn't have a problem not having mplayer listed in apt , but I am impressed with checkinstall.  Thanks much  mark

---

### Post by andrew.46 on 2009-05-12
Hi,

Perhaps some who have used this guide might be interested in a new guide I have posted to the forums:

Top 10 Tricks and Tips for the svn MPlayer
[http://ubuntuforums.org/showthread.php?t=1154431](http://ubuntuforums.org/showthread.php?t=1154431)

All the best,

Andrew

---

### Post by andrew.46 on 2009-05-13
Hi,

Wooooooo hoooooooooooooooo!!!!

Re: Tutorial of the Week
[http://ubuntuforums.org/showpost.php?p=7264867&postcount=52](http://ubuntuforums.org/showpost.php?p=7264867&postcount=52)

Andrew

---

### Post by Dakanya on 2009-05-16
I have some folders in my home directory and I was wondering if it was safe to erase them or if they are actually the installed directories for mplayer. /all-20071007/ /x264/ /live/

---

### Post by andrew.46 on 2009-05-16
Hi Dakanya,

> **Dakanya said:**
> I have some folders in my home directory and I was wondering if it was safe to erase them or if they are actually the installed directories for mplayer. /all-20071007/ /x264/ /live/

If you have followed the guide to the letter and *installed* all of these the folders and their contents can then safely be deleted. You may wish to keep the x264 folder however as this can be updated at any time by issuing the command:

```
git pull
```

from the folder and re-compiling as demonstrated in the guide. This will keep you up to date with x264 development; mind you this library is used only for *encoding*, if you are only interested in *playback *I would not worry too much about updating at all.

In fact if the karmic koala version of this guide takes off I suspect that x264 and MEncoder may not even be included, FFmpeg in my mind is a *much* superior encoder / transcoder and I suspect most are using this guide for playback with MPlayer itself.

All the best,

Andrew

---

### Post by Nullack on 2009-05-16
Congrats of the award with your howto Andrew :)

Mplayer SVN isnt happy at the moment due to whats seems to be ffmpeg:

```
mpeg12.c: At top level:
mpeg12.c:608: error: static declaration of 'mpeg1_decode_block_intra' follows non-static declaration
mpeg12.c:323: note: previous implicit declaration of 'mpeg1_decode_block_intra' was here
make[1]: *** [mpeg12.o] Error 1
make[1]: Leaving directory `/home/nullack/src/mplayer/libavcodec'
make: *** [libavcodec/libavcodec.a] Error 2
```

---

### Post by andrew.46 on 2009-05-17
Hi Nullack,

> **Nullack said:**
> Congrats of the award with your howto Andrew :)

Thanks! This has given me the needed kick to produce another guide for MPlayer and Karmic Koala. I am contemplating a few changes that I would be interested in your thoughts on:

[LIST=1]
[*]Omitting x264 encoding + MEncoder completely by passing '--disable-mencoder --disable-x264'. A bit controversial perhaps?
[*]Adding in the generation of the html docs (again)
[*]Adding in a sample $HOME/.mplayer/config
[*]Draw the codecs from Medibuntu instead of directly from MPlayer site
[/LIST]

> Mplayer SVN isnt happy at the moment due to whats seems to be ffmpeg:

```
[...]make: *** [libavcodec/libavcodec.a] Error 2
```

Thanks for the heads up, I will hold off updating for a day or 2 :-).

Andrew

---

### Post by gitpik on 2009-05-17
Hello, much obliged for the guide! 

However I'm also running into the compile error that nullack has mentioned above. Could someone direct me to a way to get an older version to compile? still new to compiling and svn/git.

---

### Post by mc4man on 2009-05-17
Instead of 
svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer
use this format
svn checkout -rxxxxx svn://svn.mplayerhq.hu/mplayer/trunk mplayer

so if tonights was 29311 go a number or so back


Ex. 4 back
```
svn checkout -r29307 svn://svn.mplayerhq.hu/mplayer/trunk mplayer
```

Andrew had a neat way to check the changes x number of -r's back. I'm sorry to have forgotten it (hint

---

### Post by andrew.46 on 2009-05-17
Hi mc4man,

> **mc4man said:**
> Andrew had a neat way to check the changes x number of -r's back. I'm sorry to have forgotten it (hint

Yes, not my finest moment I am afraid :-). I spent a considerable amount of time writing a *script* to present the svn logs for a set number of revisions and then discovered that svn itself can do this with no problems!

The syntax for viewing the last 6 changes for example:

```

andrew@skamandros~/source/mplayer/mplayer$ **[COLOR="Red"]svn log -l 6[/COLOR]**
------------------------------------------------------------------------
r29310 | diego | 2009-05-16 09:17:25 +1000 (Sat, 16 May 2009) | 2 lines

Add missing path to find invocation for tags/TAGS creation.

------------------------------------------------------------------------
r29309 | diego | 2009-05-16 08:24:12 +1000 (Sat, 16 May 2009) | 4 lines

Simplify find invocation in tags/TAGS generation command:
- Drop '-print', which is the default for find.
- Drop unnecessary invocation of find in a subshell.

------------------------------------------------------------------------
r29308 | bircoph | 2009-05-14 05:44:44 +1000 (Thu, 14 May 2009) | 3 lines

Revert whitespace removal for win-related code, because lack of ^M at
linebreaks may cause problems in win.

------------------------------------------------------------------------
r29307 | bircoph | 2009-05-14 04:42:38 +1000 (Thu, 14 May 2009) | 4 lines

Restore old license file after whitspace removal in previous commit.
Legal stuff is very fragile and shouldn't be changed, even for
whitespace cosmetics.

------------------------------------------------------------------------
r29306 | bircoph | 2009-05-14 01:22:13 +1000 (Thu, 14 May 2009) | 4 lines

Remove all kind of trailing whitespaces from all MPlayer's files.
This affects all kind of spaces (' ',^I,^M,^L,...): actually
[:space:] regex character set.

------------------------------------------------------------------------
r29305 | diego | 2009-05-13 12:58:57 +1000 (Wed, 13 May 2009) | 2 lines

whitespace cosmetics: Remove all trailing whitespace.

------------------------------------------------------------------------
andrew@skamandros~/source/mplayer/mplayer$ 

```

All the best,

Andrew

---

### Post by andrew.46 on 2009-05-17
Hi gitpick,

> **gitpik said:**
> Hello, much obliged for the guide! 

It is my pleasure :-).

> However I'm also running into the compile error that nullack has mentioned above. Could someone direct me to a way to get an older version to compile? still new to compiling and svn/git.

I have just successfully compiled r23911 so everything must be back on track again.

All the best,

Andrew

---

### Post by gitpik on 2009-05-17
> **mc4man said:**
> 
svn checkout -rxxxxx svn://svn.mplayerhq.hu/mplayer/trunk mplayer


Thank you both for getting back to me so fast that's exactly what I needed. Although for some reason I tried every build back to 29307 and none would compile for me last night. This morning I tried again with 29311 on andrews recommendation and everything worked great! :D I did poke around the man page for svn last night a little. Would this do something similar?

```
svn update -rxxxxx

```

As a side note does anybody have any idea why the new electricsheep would refuse to run with this version of mplayer?

---

### Post by kthxbai2u on 2009-05-18
Great tutorial, thanks!

---

### Post by andrew.46 on 2009-05-18
Hi gitpik,

> **gitpik said:**
> I did poke around the man page for svn last night a little. Would this do something similar?

```
svn update -rxxxxx
```


Both commands have this option. If you are a little new to svn (or even if you are an old hand!) you can have a look at the available options by running: svn help <subcommand>. So to see the options for 'update':

```
svn help update
```

and the same for 'checkout', 'log', 'update' etc.

> As a side note does anybody have any idea why the new electricsheep would refuse to run with this version of mplayer?

You have got me there :-). What on earth is, or are, electricsheep?

Andrew

---

### Post by andrew.46 on 2009-05-18
Hi kthxbai2u,

> **kthxbai2u said:**
> Great tutorial, thanks!

My pleasure, I hope you enjoy this great software :-).

Andrew

---

### Post by mc4man on 2009-05-18
> What on earth is, or are, electricsheep?

It's actually kinda interesting idea, remembered ck.ing out last year

[http://electricsheep.org/tour/](http://electricsheep.org/tour/)

---

### Post by andrew.46 on 2009-05-21
Hi Nullack,

> **Nullack said:**
> 
```

cd ~/src/mplayer
svn checkout svn://svn.ffmpeg.org/soc/wmapro wmapro
cp wmapro/wma* libavcodec
patch -p0 <wmapro/audioframesize.patch
patch -p0 <wmapro/mplayer.patch
patch -p0 <wmapro/wmapro_ffmpeg.patch

```

It has taken a little prodding on these forums and a pointer from the MPlayer-users but I have finally taken your advice and installed the wmapro work from SOC. You of course were right: it works brilliantly!

Only slight modification I made is copying the files a little differently:

```
cp -v wmapro/wma3dec.c wmapro/wma3data.h wmapro/wma3.h libavcodec
```

It is a minor niggle but copying as 'wm*' also copies wmapro_ffmpeg.patch, this makes no difference but I am a little anal at times :-).

Playing [a demo file]("http://samples.mplayerhq.hu/A-codecs/WMA9/wmapro/WMVHDsplash.wmv") now gives:

```

andrew@skamandros~/samples$ mplayer WMVHDsplash.wmv 
MPlayer SVN-r29318-4.2.4 (C) 2000-2009 MPlayer Team

Playing WMVHDsplash.wmv.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [WMV3]  1280x720  24bpp  1000.000 fps  6500.0 kbps (793.5 kbyte/s)
==========================================================================
Opening video decoder: [dmo] DMO video codecs
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
Decoder supports the following formats: YV12 YUY2 UYVY YVYU RGB8 RGB555 RGB565 RGB24 RGB32 
Decoder is capable of YUV output (flags 0x1b)
VDec: vo config request - 1280 x 720 (preferred colorspace: Packed YUY2)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 1280x720 => 1280x720 Planar YV12 
Selected video codec: [wmv9dmo] vfm: dmo (Windows Media Video 9 DMO)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
[wmapro @ 0x8f576f0][18] [0] [3f] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [e0] [0] [0] [0] 
[wmapro @ 0x8f576f0] ed sample bit depth = 16
[wmapro @ 0x8f576f0] ed decode flags = e0
[wmapro @ 0x8f576f0] samples per frame = 2048
[wmapro @ 0x8f576f0] log2 frame size = 17
[wmapro @ 0x8f576f0] max num subframes = 16
[wmapro @ 0x8f576f0] len prefix = 1
[wmapro @ 0x8f576f0] num channels = 6
[wmapro @ 0x8f576f0] lossless = 0
AUDIO: 48000 Hz, 6 ch, s16le, 384.0 kbit/8.33% (ratio: 48000->576000)
**[COLOR="Red"]Selected audio codec: [ffwmapro] afm: ffmpeg (FFmpeg WMA Pro audio)[/COLOR]**
==========================================================================
AO: [oss] 48000Hz 6ch s16le (2 bytes per sample)
Starting playback...
[wmapro @ 0x8f576f0]input buffer to small413/413 24%  4%  1.8% 0 0 
A:  22.9 V:  22.9 A-V:  0.004 ct:  0.086 479/479 23%  4%  1.8% 0 0 

Exiting... (End of file)

```

I am not sure if this belongs in the Jaunty guide but I might consider adding it in this weekend as I am rewriting some sections based on advice from Carl Eugene you may have seen in MPlayer-users. Exciting times indeed for MPlayer :-).

Andrew

---

### Post by mc4man on 2009-05-21
The one thing I've noticed (and others have confirmed ) is that at times lately (last couple of weeks) the current svn of ffmpeg, when used with the current svn of wmapro will result in 3  possibilities
1. it succeeds 
2 it fails with numerous wma3dec.c (wma3dec.o) errors (then adding bitstream.h to libavcodec allows build to succeed
3. it fails with a simple error and won't compile "libavcodec/wma3dec.c:315: error: too many arguments to function &#8216;ff_mdct_init&#8217;"

right now ffmpeg revision 18839 and wmapro -r 4283 will build perfectly ( whether in mplayer or ffmpeg itself
and also the latest -r 18892

( I do a quick ck. using wmapro's checkout.sh to see if it will build

---

### Post by andrew.46 on 2009-05-21
Hi mc4man,

> **mc4man said:**
> right now ffmpeg revision 18839 and wmapro -r 4283 will build perfectly

Sounds a little 'bleeding edge' for this guide perhaps :-). I guess the question is *when* will ffwmapro join FFmpeg proper?

Andrew

---

### Post by Nullack on 2009-05-21
IMHO ffmpeg should hurry up and merge the wmapro decoder code. Its been ages and most of the SVN changes are fluff rather than core changes.

---

### Post by mc4man on 2009-05-21
> Sounds a little 'bleeding edge' for this guide perhaps 

Maybe so, though it's almost always worked for me 

The wmapro -r's (going back a little ways, seem to be the same, it's just 'some' ffmpeg -r's have an issue

The one that caused an issue the other day for someone was ffmpeg -r 18875, tonights -r 18892 works fine. 

(the quick test only takes a few minutes or so, doesn't seem suitable for a guide though

Edit: the bitstream.h thing was resolved apparently some -r's back, so the patch should work virtually all the time


> 
< #include "bitstream.h"
---
> #include "get_bits.h"

the hang up would be an errant ffmpeg -r and it seems that **mplayer always uses the latest ffmpeg svn **when you checkout an mplayer svn. (good thing or not ...?

Edit: it's sorta a viable alternate dual install, a patched ffmpeg and patched mplayer, getting the wwmapro, mplayer sources at the same time.
If a .checkout.sh, configure and make works for ffmpeg, then it will work for mplayer, if not then it won't.

The easiest immediate solution would be to replace (replace, not merge,) the 5 ffmpeg dir.'s in mplayer with those from an earlier ffmpeg -r, most likely just a couple back. (I say that's the 'sorta' part

---

### Post by andrew.46 on 2009-05-22
Hi mc4man,

> **mc4man said:**
>  it seems that **mplayer always uses the latest ffmpeg svn **when you checkout an mplayer svn. (good thing or not ...?

I think it is often a cautious thing to avoid updating MPlayer *immediately* after a sync with the FFmpeg libraries :-).

Andrew

---

### Post by penC on 2009-05-23
Thank you for a very good tutorial!

  pen

---

### Post by andrew.46 on 2009-05-23
Hi pen,

> **penC said:**
> Thank you for a very good tutorial!

It is my pleasure, I am glad it all worked out for you :-).

Andrew

---

### Post by aidanb on 2009-05-25
Thank you for this guide!  It was very useful, I'm glad someone linked it to me because I'd wasted hours trying to get mplayer to work when I hadn't installed all that stuff previously.  Great guide with plenty of detail but perfectly clear.

---

### Post by andrew.46 on 2009-05-26
Hi aidanb,

> **aidanb said:**
> Thank you for this guide!  It was very useful, I'm glad someone linked it to me because I'd wasted hours trying to get mplayer to work when I hadn't installed all that stuff previously.  Great guide with plenty of detail but perfectly clear.

My pleasure :-). Just saw [your post]("http://ubuntuforums.org/showthread.php?t=1169440") regarding MPlayer problems, good to see you found your way here, with some resolution as well. Your -vo command should be a little healthier now:

```

andrew@skamandros~$ mplayer -vo help
MPlayer SVN-r29318-4.2.4 (C) 2000-2009 MPlayer Team
Available video output drivers:
	xv	X11/Xv
	x11	X11 ( XImage/Shm )
	xover	General X11 driver for overlay capable video output drivers
	gl	X11 (OpenGL)
	gl2	X11 (OpenGL) - multiple textures version
	dga	DGA ( Direct Graphic Access V2.0 )
	sdl	SDL YUV/RGB/BGR renderer (SDL v1.1.7+ only!)
	fbdev	Framebuffer Device
	fbdev2	Framebuffer Device
	svga	SVGAlib
	aa	AAlib
	caca	libcaca
	v4l2	V4L2 MPEG Video Decoder Output
	xvidix	X11 (VIDIX)
	cvidix	console VIDIX
	null	Null video output
	mpegpes	MPEG-PES to DVB card
	yuv4mpeg	yuv4mpeg output for mjpegtools
	png	PNG file
	jpeg	JPEG file
	gif89a	animated GIF output
	tga	Targa output
	pnm	PPM/PGM/PGMYUV file
	md5sum	md5sum of each frame

```

If you are keen on the commandline side of MPlayer you might be interested in dipping into a little 'companion' site I wrote recently:

Top 10 Tricks and Tips for the svn MPlayer
[http://ubuntuforums.org/showthread.php?t=1154431](http://ubuntuforums.org/showthread.php?t=1154431)

All the best,

Andrew

---

### Post by tehownt on 2009-05-27
Ok so for the vdpau-capable folks out there, here is the rest of the tutorial:

Based on the first post, do every step except the one named "x264" up until you arrive to the command "sudo apt-get install subversion", do run that command but do nothing more thereafter. Then:

(In a temporary folder)

**1) Get vdpau files from nvidia**
```
wget ftp://download.nvidia.com/XFree86/vdpau/include/vdpau/vdpau.h
wget ftp://download.nvidia.com/XFree86/vdpau/include/vdpau/vdpau_x11.h
```
**2) Put them in /usr/include/vdpau**
```
sudo mkdir /usr/include/vdpau
sudo mv ./vdpau*.h /usr/include/vdpau/
```
**3) Checkout mplayer**
```
svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer
```
**4) Create vdpau folder in mplayer folder and link to the downloaded files**
```
cd mplayer
ln -s /usr/include/vdpau/ vdpau
```
**5) Configure the build to include vdpau and disable x264 (this means that the x264 install step from the original guide can and should be skipped)**
```
./configure --disable-x264-lavc --disable-x264 --enable-vdpau --enable-menu --prefix=/usr
```

Check that vdpau is present in the video output modes.

**6) Build mplayer**
```
make
```
If make breaks, check the top error, it usually is because you lack a file. 
Try and run :
```
aptitude build-depends mplayer
```

**7) Install mplayer**
```
sudo make install
```
This will install the executable in /usr/bin/, make sure that your "mplayer" command points to the right binary using the command 
```
which mplayer
```
(Some might point to /bin/mplayer).

**OP, if you care, you can add this to your post in order to make it easier to find everything.**

---

### Post by andrew.46 on 2009-05-28
Hi tehownt,

> **tehownt said:**
> OP, if you care, you can add this to your post in order to make it easier to find everything.

Thanks for making this available and for doing all the research :-). I am aware that the lack of a vdpau section weakens my guide substantially but I am only really prepared to place information in the guide that I can personally test *and* support. Probably yet another sign I should retire from the MPlayer guide business soon.....

A few points though:

[LIST=1]
[*]You specify '--enable-vdpau' in your ./configure line. This is normally discouraged in compiling the svn MPlayer and it is usually best to leave MPlayer autodetection to find the required libraries. Is there a special reason you have used it here?
[*]You specify '--enable-menu' which I admit I dropped from this guide some time ago as work on the osd menu dies a while back. Is it needed?
[*]'aptitude build-depends mplayer' This one can cause a little trouble as it brings in a host of unnecessary files including the relatively aged libx264-dev which can cause compiling trouble as well as many files that the svn MPLayer will not use (libdvdread-dev amongst others). I tried this approach a while ago and it was just too messy :-).
[*]I don't understand this one '--disable-x264-lavc --disable-x264'?
[/LIST]

Thanks for taking the time to make this post!

Andrew

---

### Post by tehownt on 2009-05-28
> **andrew.46 said:**
> Hi tehownt,
I am only really prepared to place information in the guide that I can personally test *and* support.

That's OK, though I think this guide really is worth going in a wiki so that everyone can test and support it... :)

As for your questions:

[LIST=1]
[*]It already happened to me in the past that the autodetection wasn't working fine with vdpau capabilities. Since adding this flag forces it and doesn't cause trouble otherwise, I find it's not a bad idea.

[*]This is to make sure that the OSD is available, if it's not needed anymore in order to have the OSD it might just be removed.

[*]The command should not be necessary (as I tried to put it), it's just meant to "help" if someone has some build problems, true it can bring up some unnecessary files. I might have never hit the libx264-dev problems since I disable it.

[*]Not using x264 is meant to avoid conflicts when the compilation had troubles finding the right libx264.so (from nv forums), this was present in the previous build scripts from nvidia.
[/LIST]

One thing I haven't done though, is describe how to make smplayer remember the -vo vdpau option (I'm not really a regular smplayer user).

One other thing that I haven't investigated (but I'm sure there's some info on nv forums), using the -vc ffh264vdpau,ffmpeg12vdpau,ffvc1vdpau,ffwmv3vdpau option when playing videos can give you some performance issues on slower systems (8xxxxM for instance). Thus I'm using no -vc switch which uses the ffh264 codec instead.

Thank you for the input, your guide is very, very useful ;)

---

### Post by CD Baric on 2009-06-02
Thanks Andrew - found it (Jaunty svm MPlayer).

I will take some time to read it through.

I used to run Slackware almost entirely in command line mode - wasn't a big of any GUIs (W3.1*, W95, W98, X11). I just lost too much work to crashes and lockups.

Linux command line was ROCK SOLID! And by ROCK SOLID, I mean the only problems I had were hardware related - hard to blame MS but at least all the builtin safety systems Linux/Unix had it was rare to lose much work.

As for my AMD dual core CPU and 4 gig of memory, that was the result of a recent upgrade. I replaced my main desktop box after almost 5 years of loyal service (AMD Athlon 2800+ with 1 gig of memory). It is literally wearing out so will be relegated to file server work (fresh 1 Gig HDs and fresh sticks of memory - yes they do wear out from heating/cooling cycles).

Just to let you know the AMD 7750s are pretty cheap right now but I recommend the AMD Phenom II X2 550 Black Edition because you can literally unlock the other two cores giving you four 3.1GHz cores, all with 512KB of active L2 cache and sharing 6MB of L3, just like a high end Phenom II X4 950 - expect to pay less than $90 this Summer.

[http://www.theinquirer.net/inquirer/news/1184444/phenom-ii-x2-550-black-edition-surprise](http://www.theinquirer.net/inquirer/news/1184444/phenom-ii-x2-550-black-edition-surprise)

Did I mention that it is an overclocking animal?

I will keep in touch as regards building and running multiple thread MPlayer.

Best regards,

CD Baric

---

### Post by andrew.46 on 2009-06-02
Hi CD Baric,

> **CD Baric said:**
> Thanks Andrew - found it (Jaunty svm MPlayer).

I will take some time to read it through.

Oops.... perhaps a link would have made things a little easier :-).

> Just to let you know the AMD 7750s are pretty cheap right now but I recommend the AMD Phenom II X2 550 Black Edition because you can literally unlock the other two cores giving you four 3.1GHz cores, all with 512KB of active L2 cache and sharing 6MB of L3, just like a high end Phenom II X4 950 - expect to pay less than $90 this Summer.

At the risk of provoking a little laughter I will reveal that my own personal speed-beast is a Dell Latitude D520 laptop with onboard video and sound :-). I picked it up for $500 AUS second hand from ebay a year or so ago...

> I will keep in touch as regards building and running multiple thread MPlayer.

I believe there is a thread somewhere on these forums that discusses that very thing, I am not sure what the state of play is with FFmpeg-MT at the moment.

All the best,

Andrew

---

### Post by shane2peru on 2009-06-02
Thanks this worked for me on 64bit.  

Shane

---

### Post by andrew.46 on 2009-06-02
Hi shane,

> **shane2peru said:**
> Thanks this worked for me on 64bit.  

Great news, 64bit is a bit of a grey area for me and for this guide :-).

Andrew

---

### Post by Malart on 2009-06-03
when i try to download the bunch of dev files, it tells me that libglu1-mesa-dev needs libglu1-mesa (= 7.4-0ubuntu3) but 7.4-1ubuntu3.1 is installed


i realize this is probably not the thread to ask this in... but i just installed Jaunty today and this is the first how-to ive been through since i did

i used Hardy before, and couldnt get it to work there either... so i'm a bit of a noob, but im wondering what to do about this, so if someone could point me in the right direction, that'd be great.


**********************************-EDIT-************************************

Actually thats not true. I had to patch my kernel to get my nvidia drivers to work


**********************************-EDIT2-***********************************

And now I've screwed a whole bunch of stuff up i think by trying to remove the offending library
I re-installed what i could, but im running into more issues

---

### Post by andrew.46 on 2009-06-03
Hi Malart,

> **Malart said:**
> when i try to download the bunch of dev files, it tells me that libglu1-mesa-dev needs libglu1-mesa (= 7.4-0ubuntu3) but 7.4-1ubuntu3.1 is installed

This package certainly does require this version:

```

andrew@skamandros:~$ apt-cache showpkg libglu1-mesa-dev
Package: libglu1-mesa-dev
Versions: 
7.4-0ubuntu3 (/var/lib/apt/lists/mirror.3fl.net.au_ubuntu_dists_jaunty_main_binary-i386_Packages) (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/apt/lists/mirror.3fl.net.au_ubuntu_dists_jaunty_main_binary-i386_Packages
                  MD5: ad4abc00598914886fe45aaf594d30f5


Reverse Depends: 
  libvtk5-dev,libglu1-mesa-dev
  libvibrant6-dev,libglu1-mesa-dev
  liboglappth-dev,libglu1-mesa-dev
  libgtkglext1-dev,libglu1-mesa-dev
  libgtkada2-dev,libglu1-mesa-dev
  libglc-dev,libglu1-mesa-dev
  libftgl-dev,libglu1-mesa-dev
  libcm-dev,libglu1-mesa-dev
  libsdl1.2-dev,libglu1-mesa-dev
  libqt4-opengl-dev,libglu1-mesa-dev
  libqt4-dev,libglu1-mesa-dev
  libqt3-mt-dev,libglu1-mesa-dev
  libglu1-xorg-dev,libglu1-mesa-dev
  libglew1.5-dev,libglu1-mesa-dev
  libfltk1.1-dev,libglu1-mesa-dev
Dependencies: 
**[COLOR="Purple"]7.4-0ubuntu3 - libglu1-mesa (5 7.4-0ubuntu3)[/COLOR]** libgl1-mesa-dev (16 (null)) libgl-dev (0 (null)) dpkg (2 1.14.12ubuntu3) mesa-glide2-dev (3 5.0.0-1) mesag-dev (3 5.0.0-1) mesag3+ggi-dev (3 5.0.0-1) xlibmesa-dev (0 (null)) libglu-dev (0 (null)) 
Provides: 
7.4-0ubuntu3 - xlibmesa-glu-dev libglu-dev 
Reverse Provides:

```

and I have a suspicion that your sources.list may very well be a little misconfigured. Could you post:

```
cat /etc/apt/sources.list
```

although this is moving a little beyond the scope of this little guide :-).

Andrew

---

### Post by Malart on 2009-06-03
just a moment, i had to reinstall jaunty... ill post in about 20 minutes

---

### Post by andrew.46 on 2009-06-03
Hi Malart,

> **Malart said:**
> just a moment, i had to reinstall jaunty... ill post in about 20 minutes

Well it was in the back of my mind that your system sounded a little broken but it is considered bad form to recommend a reinstall so I am glad you made the decision yourself :-). The guide should work well on a fresh install as I have tested it in this way several times without failure.

All the best with the reinstall!!

Andrew

---

### Post by Malart on 2009-06-03
well i may still have problems because i have to update and patch my kernel in order to get my graphics card to work


ill go through the tut again and if i have the same problem, i will post my sources list

********EDIT*********

good news is i saved the patched kernels, so i dont have to wait an hour

---

### Post by shane2peru on 2009-06-03
> **andrew.46 said:**
> Hi shane,



Great news, 64bit is a bit of a grey area for me and for this guide :-).

Andrew

Andrew,

that is funny 64bit is a bit grey for me too. :)  I use it, but I really don't know a lot about it.  I just downloaded what you had mentioned, and copied it to /usr/lib/codecs  <-- course I had to make that directory.  Seems to work fine I guess.  I tried looking it up on Google to find out the correct method I didn't see anything particular.  If I ever find anything more out about it I will let you know.  It seems to be working though.  I'm using mencoder (part of mplayer) to record some old camcorder stuff to dvd.  Thanks for keeping up the guide!

Shane

---

### Post by mc4man on 2009-06-03
A small point concerning vdpau (in the context of this thread - jaunty)

This is available and would be auto detected by mplayer
[http://packages.ubuntu.com/jaunty/nvidia-180-libvdpau-dev](http://packages.ubuntu.com/jaunty/nvidia-180-libvdpau-dev)

or if one is using a ppa to get updated nvidia drivers then would be available there also.(matching the ppa's version #

If you only copy the headers with no .pc (/usr/lib/pkgconfig or /usr/local/lib/pkgconfig then it's possible mplayer will miss

Seems better to me to keep all your nvidia related installs on the same version


@ Malart
make sure you have jaunty-updates and jaunty-security enabled as sources, then run a sudo apt-get update before trying to dl the mplayer deps.
(System -> Admin -> Software Sources -> Updates tab

7.4-1ubuntu3.1 is the jaunty-updates version, 7.4-0ubuntu3 was/is the orig. release ver.

---

### Post by Malart on 2009-06-04
thanks for the help, i got it working now no problem

i also compiled it with multi threading support... gonna test it on some 720p movies later, as i had absolutely no luck watching them in vista without MAJOR A/V lag

thanks again

:p:p:p:p:p:p

---

### Post by Malart on 2009-06-04
The 720p official trailer for the Dark Knight works PERFECTLY


hopefully itll do just as good with full movies

---

### Post by Nullack on 2009-06-04
Why do all the fiddling with vdpau patches when the SVN source is the official development tree? I have done extensive tests on VDPAU across various driver releases and find it very excellent. It also includes post processing acceleration rather than just decode acceleration. I also dont see why disabling x264, which is an AVC encoder, has anything to do with AVC decoding. IMHO all you need is SVN and the NVIDIA VDPAU driver components.

As for AMD64, again IMHO all you need is SVN. Who want to run binary decoders when ffmpeg does it anyway. I certainly dont. RV30

---

### Post by andrew.46 on 2009-06-04
Hi shane,

> **shane2peru said:**
> that is funny 64bit is a bit grey for me too. :)  I use it, but I really don't know a lot about it.  I just downloaded what you had mentioned, and copied it to /usr/lib/codecs  <-- course I had to make that directory.  Seems to work fine I guess.  I tried looking it up on Google to find out the correct method I didn't see anything particular.  If I ever find anything more out about it I will let you know.  It seems to be working though.  I'm using mencoder (part of mplayer) to record some old camcorder stuff to dvd.  Thanks for keeping up the guide!

Glad it has all worked out for you :-). The 64bit codec pack from MPlayer is in fact not something to lose to much sleep over as it only includes a handful of codecs:

```

andrew@skamandros~/Desktop$ tar tjf essential-amd64-20071007.tar.bz2 
essential-amd64-20071007/
[B][COLOR="Purple"]essential-amd64-20071007/cook.so
essential-amd64-20071007/drvc.so
essential-amd64-20071007/sipr.so[/COLOR][/B]
essential-amd64-20071007/README

```

I will admit to being a retired fan of MEncoder as I have moved my allegiance to FFmpeg courtesy of the FakeOutdoorsman's guides :-).

All the best,

Andrew

---

### Post by andrew.46 on 2009-06-04
Hi Malart,

> **Malart said:**
> thanks for the help, i got it working now no problem

i also compiled it with multi threading support... gonna test it on some 720p movies later, as i had absolutely no luck watching them in vista without MAJOR A/V lag

Great news :-). You are a braver man than me I have not ventured down the FFmpeg-MT path as yet, perhaps one day...

Andrew

---

### Post by shane2peru on 2009-06-06
> **andrew.46 said:**
> Hi shane,



Glad it has all worked out for you :-). The 64bit codec pack from MPlayer is in fact not something to lose to much sleep over as it only includes a handful of codecs:

```

andrew@skamandros~/Desktop$ tar tjf essential-amd64-20071007.tar.bz2 
essential-amd64-20071007/
[B][COLOR="Purple"]essential-amd64-20071007/cook.so
essential-amd64-20071007/drvc.so
essential-amd64-20071007/sipr.so[/COLOR][/B]
essential-amd64-20071007/README

```

I will admit to being a retired fan of MEncoder as I have moved my allegiance to FFmpeg courtesy of the FakeOutdoorsman's guides :-).

All the best,

Andrew

Really, is FFmpeg along the same lines as MEncoder?  I too updated my FFmpeg also.  I was wondering if anyone knows if I should have grabbed the 32bit codecs?  Thanks for the how to.

Shane

---

### Post by andrew.46 on 2009-06-06
Hi shane,

> **shane2peru said:**
> Really, is FFmpeg along the same lines as MEncoder?  I too updated my FFmpeg also.  I was wondering if anyone knows if I should have grabbed the 32bit codecs?  Thanks for the how to.

I have found the syntax of FFmpeg to be much more intuitive than that of MEncoder and I have always had better results with FFmpeg. As well FFmpeg development is usually white-hot, take a look at the FFmpeg-dev mailing list one day and you will see what I mean while I suspect it has been a while between MEncoder changes. I would be interested to hear what others think?

Unfortunately I have no knowledge of using the 32bit codecs on a 64bit system. I guess the good news is that the codecs are becoming less necessary as FFmpeg slowly produces native replacements, wmapro being an excellent and recent example.

All the best,

Andrew

---

### Post by andrew.46 on 2009-06-10
Hi,

Finally it has happened and Karmic Koala will get a decent copy of MPlayer:

Package: mplayer (2:1.0~rc3+svn20090426-1ubuntu2) [multiverse] 
[http://packages.ubuntu.com/karmic/mplayer](http://packages.ubuntu.com/karmic/mplayer)

This leads to the odd situation that for the moment the repository version is actually a little newer that the Medibuntu version although I note that the repository version will have some libavcodec amputations, removed mpc support and a few little odd things.

Certainly though this marks my retirement from the svn MPlayer guide business, these guides were only ever intended to provide an avenue for Ubuntu users to get a reasonably new version of MPlayer in face of the ancient version in the repositories. It looks as if this will no longer be the case, particularly if svn updates are backported, although I will personally continue to use svn of course :-).

All the best,

Andrew

---

### Post by BetterSense on 2009-06-11
In the meantime, I followed the first post of this guide to install mplayer on my Jaunty. I had the repo version but it sucked so I used 'sudo apt-get remove mplayer', then followed the guide. 

Everything went fine except it doesn't actually work. Now I have an amd64 mplayer .deb on my desktop, but trying to play a video returns 
> 
bash: /usr/bin/mplayer: No such file or directory


I tried running 

```
dpkg -i Desktop/mplayer_3\:1.0~svn-r29352-1_amd64.deb 
```

but this is what I get:
```

chaz@brutus:~/bin$ sudo !!
sudo dpkg -i mplayer_3\:1.0~svn-r29352-1_amd64.deb 
(Reading database ... 146885 files and directories currently installed.)
Preparing to replace mplayer 3:1.0~svn-r29352-1 (using mplayer_3:1.0~svn-r29352-1_amd64.deb) ...
Unpacking replacement mplayer ...
Setting up mplayer (3:1.0~svn-r29352-1) ...
Processing triggers for man-db ...
chaz@brutus:~/bin$ 

```

and it still doesn't work.

Clearly I'm missing something important here.

---

### Post by rvm4000 on 2009-06-11
What does *dpkg --contents Desktop/mplayer_3\:1.0~svn-r29352-1_amd64.deb* say?

---

### Post by shane2peru on 2009-06-11
> **BetterSense said:**
> In the meantime, I followed the first post of this guide to install mplayer on my Jaunty. I had the repo version but it sucked so I used 'sudo apt-get remove mplayer', then followed the guide. 

Everything went fine except it doesn't actually work. Now I have an amd64 mplayer .deb on my desktop, but trying to play a video returns 


I tried running 

```
dpkg -i Desktop/mplayer_3\:1.0~svn-r29352-1_amd64.deb 
```

but this is what I get:
```

chaz@brutus:~/bin$ sudo !!
sudo dpkg -i mplayer_3\:1.0~svn-r29352-1_amd64.deb 
(Reading database ... 146885 files and directories currently installed.)
Preparing to replace mplayer 3:1.0~svn-r29352-1 (using mplayer_3:1.0~svn-r29352-1_amd64.deb) ...
Unpacking replacement mplayer ...
Setting up mplayer (3:1.0~svn-r29352-1) ...
Processing triggers for man-db ...
chaz@brutus:~/bin$ 

```

and it still doesn't work.

Clearly I'm missing something important here.

It is probably installed however the 'common'  location is somewhat changed.  In the terminal type:
```

which mplayer

```

If it returns something like this:
```

/usr/local/bin/mplayer

```
Then you probably just need to make a link like this:

```

sudo ln -s /usr/local/bin/mplayer /usr/bin/mplayer 

```
That will create a soft link to the 'normal' place that Ubuntu expects it to be at.

If you don't get the above response, please post what you did get.

Shane

---

### Post by BetterSense on 2009-06-11
I created the symlink and it works now. It was in /usr/local/bin


Mplayer works now but it still fails to play the video I am trying to play, and the video I hoped compiling the svn would fix. VLC does play the video, and xine plays it without sound. It's an animated movie from the '80s. I do not know what kind of file it is since VLC doesn't have nice verbosity like mplayer. I suppose I must be missing a codec. 

I can play this video with VLC and it's not a big deal but if VLC can do it and mplayer can't there must be something missing from my configuration; maybe a 64 bit thing.

---

### Post by shane2peru on 2009-06-11
More than likely it is codec you are missing.  As a fellow 64bit user I went ahead and downloaded the codecs suggested for the 32bit and untarred it also to the location they mentioned.  It hasn't hurt thus far, and if it does cause a problem I reckon I can just delete the codecs, and only put the 64bit ones in there.  You could give that a try.  It is worth a shot.  Let us know if that helps.

Shane

---

### Post by Arup on 2009-06-11
> **andrew.46 said:**
> Hi,

Finally it has happened and Karmic Koala will get a decent copy of MPlayer:

Package: mplayer (2:1.0~rc3+svn20090426-1ubuntu2) [multiverse] 
[http://packages.ubuntu.com/karmic/mplayer](http://packages.ubuntu.com/karmic/mplayer)

This leads to the odd situation that for the moment the repository version is actually a little newer that the Medibuntu version although I note that the repository version will have some libavcodec amputations, removed mpc support and a few little odd things.

Certainly though this marks my retirement from the svn MPlayer guide business, these guides were only ever intended to provide an avenue for Ubuntu users to get a reasonably new version of MPlayer in face of the ancient version in the repositories. It looks as if this will no longer be the case, particularly if svn updates are backported, although I will personally continue to use svn of course :-).

All the best,

Andrew


Thanks for all your great help, I used your tip in Hardy and Jaunty and benefited from using the latest FFMPEG and x264 as well as mplayer. For Gnome I suggest the excellent gnome mplayer which is in the repos or one could compile it from the source as I have done.

---

### Post by andrew.46 on 2009-06-11
Hi Arup,

> **Arup said:**
> Thanks for all your great help, I used your tip in Hardy and Jaunty and benefited from using the latest FFMPEG and x264 as well as mplayer. For Gnome I suggest the excellent gnome mplayer which is in the repos or one could compile it from the source as I have done.

It has been a huge amount of fun and I am glad you have profited by my playing around with this great software :-). I will admit that I have only ever used the Gnome MPlayer briefly a long time ago and I will have to revisit it soon.

Andrew

---

### Post by BetterSense on 2009-06-11
> More than likely it is codec you are missing. As a fellow 64bit user I went ahead and downloaded the codecs suggested for the 32bit and untarred it also to the location they mentioned. It hasn't hurt thus far, and if it does cause a problem I reckon I can just delete the codecs, and only put the 64bit ones in there. You could give that a try. It is worth a shot. Let us know if that helps.


I had already done that. It seems weird to me that I have like several dozen .dll and so on files from the 32bit codecs, but only a handful of them from the 64bit download, and they are like .so files?

---

### Post by rvm4000 on 2009-06-11
AFAIK, the 32bit codecs won't work with a 64bit mplayer (although it's possible to compile mplayer in 32bit mode [1]).

The 64bit codec package provides only a few codecs (I think for rmvb mainly).

[1] [http://www.mplayerhq.hu/DOCS/HTML/en/faq.html#id2994563](http://www.mplayerhq.hu/DOCS/HTML/en/faq.html#id2994563)

---

### Post by andrew.46 on 2009-06-11
Hi rvm4000,

> **rvm4000 said:**
> AFAIK, the 32bit codecs won't work with a 64bit mplayer 

And I believe the drive from FFmpeg/MPlayer is increasingly to fashion and work with *native* decoders/encoders rather than develop support for *external* codecs. Development of ffwmapro is a recent example.

Andrew

---

### Post by andrew.46 on 2009-06-15
Hi,

An interesting thread on MPlayer-dev-eng that shows that perhaps the days of the gmplayer are indeed numbered:

[http://lists.mplayerhq.hu/pipermail/mplayer-dev-eng/2009-June/061706.html](http://lists.mplayerhq.hu/pipermail/mplayer-dev-eng/2009-June/061706.html)

Good to see SMPlayer getting the nod :-).

Andrew

---

### Post by shane2peru on 2009-06-15
> **rvm4000 said:**
> AFAIK, the 32bit codecs won't work with a 64bit mplayer (although it's possible to compile mplayer in 32bit mode [1]).

The 64bit codec package provides only a few codecs (I think for rmvb mainly).

[1] [http://www.mplayerhq.hu/DOCS/HTML/en/faq.html#id2994563](http://www.mplayerhq.hu/DOCS/HTML/en/faq.html#id2994563)

hmm, so I guess I don't need all those 32bit codecs.  I guess I could delete them.  I only use it basically for capturing video from my tvcard.  Of course I'm not sure which GUI apps are frontends for mplayer/mencoder, I use DEVEDE, DVDStyler, and Kdenlive and seem to have a good amount of things I can export to.  I have tinkered with several others, but those seem to be the ones most used.  Either way I have mplayer and ffmpeg newest versions installed, and don't 'seem' to be lacking codecs. :)    

Shane

---

### Post by andrew.46 on 2009-07-11
Hi,

Looks like support for the external, non-free amr libraries has been removed from libavcodec so for the moment there will be no amr playback for MPlayer. Consequently I have removed the amr / Medibuntu sections of the guide.

FFmpeg now features support for opencore-amr so hopefully support for this will be added to MPlayer soon. When this happens I shall add the details to this guide.

All the best,

Andrew

---

### Post by stanjr on 2009-07-17
What is compiling x264 with the --fprofile option about?  What is it good for, is it worth it, and how do you do it?

Thanks for any input!

---

### Post by andrew.46 on 2009-07-17
Hi stanjr,

> **stanjr said:**
> What is compiling x264 with the --fprofile option about?  What is it good for, is it worth it, and how do you do it?

If you are talking about gcc options I am afraid I have absolutely no idea :-). Sorry, perhaps others will have more of an idea?

Andrew

---

### Post by hissyfut on 2009-07-28
what exactly is mp4 output? Does this mean something else than being able to output an mp4 file?

This does seems to turn on mp4 output:

./configure --prefix=/usr --enable-shared --enable-visualize --enable-pic

mp4 output: yes

---

### Post by andrew.46 on 2009-07-28
Hi hissyfut,

> **hissyfut said:**
> what exactly is mp4 output? Does this mean something else than being able to output an mp4 file?

I believe this refers to the possibilities when using x264 itself from the commandline, rather than when x264 is utilised by MEncoder or FFmpeg. Have a look at your own copy as follows:

```

andrew@skamandros~$ **[COLOR="Red"]x264 --help | head -n 11[/COLOR]**
x264 core:68 r1185 2956905
Syntax: x264 [options] -o outfile infile [widthxheight]

Infile can be raw YUV 4:2:0 (in which case resolution is required),
  or YUV4MPEG 4:2:0 (*.y4m),
  or AVI or Avisynth if compiled with AVIS support (no).
**[COLOR="Red"]Outfile type is selected by filename:[/COLOR]**
 .264 -> Raw bytestream
 .mkv -> Matroska
 .mp4 -> MP4 if compiled with GPAC support (no)


```

There has been a problem for some time with with gpac and x264 as can be seen in my own configuration above.

Andrew

---

### Post by hissyfut on 2009-07-28
> **andrew.46 said:**
> Hi hissyfut,



I believe this refers to the possibilities when using x264 itself from the commandline, rather than when x264 is utilised by MEncoder or FFmpeg. Have a look at your own copy as follows:

```

andrew@skamandros~$ **[COLOR="Red"]x264 --help | head -n 11[/COLOR]**
x264 core:68 r1185 2956905
Syntax: x264 [options] -o outfile infile [widthxheight]

Infile can be raw YUV 4:2:0 (in which case resolution is required),
  or YUV4MPEG 4:2:0 (*.y4m),
  or AVI or Avisynth if compiled with AVIS support (no).
**[COLOR="Red"]Outfile type is selected by filename:[/COLOR]**
 .264 -> Raw bytestream
 .mkv -> Matroska
 .mp4 -> MP4 if compiled with GPAC support (no)


```

There has been a problem for some time with with gpac and x264 as can be seen in my own configuration above.

Andrew

Does this mean that this would be compiling an mp4 encoder to not be able to output to an mp4 container if used on the commandline? If so, how would this be beneficial?

Btw: same output except for yes, which brought in new gpac and new cmake into the mix...

---

### Post by andrew.46 on 2009-07-28
Hi hissyfut,

> **hissyfut said:**
> Does this mean that this would be compiling an mp4 encoder to not be able to output to an mp4 container if used on the commandline? 

Well I guess x264 is not an '*mp4 encoder*' as such :-). It is rather a free library for encoding H264/AVC video streams. The section here:

```
Outfile type is selected by filename:
 .264 -> Raw bytestream
 .mkv -> Matroska
 .mp4 -> MP4 if compiled with GPAC support (no)
```

is simply referring to the capabilities of x264 when used *directly* from the commandline in the following fashion:

```
x264 -o outfile infile 
```

Do you plan on using x264 in this way? If so I am afraid that I have no experience in this technique and perhaps others will weigh in with some advice...

All the best,

Andrew

---

### Post by hissyfut on 2009-07-29
> **andrew.46 said:**
> Hi hissyfut,



Well I guess x264 is not an '*mp4 encoder*' as such :-). It is rather a free library for encoding H264/AVC video streams. The section here:

```
Outfile type is selected by filename:
 .264 -> Raw bytestream
 .mkv -> Matroska
 .mp4 -> MP4 if compiled with GPAC support (no)
```

is simply referring to the capabilities of x264 when used *directly* from the commandline in the following fashion:

```
x264 -o outfile infile 
```

Do you plan on using x264 in this way? If so I am afraid that I have no experience in this technique and perhaps others will weigh in with some advice...

All the best,

Andrew

Thanks for your help, Andrew. I've read somewhere that using
x264 on the commandline is the best way to encode such a stream/file. And thanks for the correction about it not being an 'mp4 encoder'.

---

### Post by andrew.46 on 2009-07-29
Hi hissyfut,

> **hissyfut said:**
> I've read somewhere that using x264 on the commandline is the best way to encode such a stream/file. 

Unfortunately I will be of no use to you with this. Perhaps the Doom Forums or #x264 on Freenode?

> And thanks for the correction about it not being an 'mp4 encoder'.

Oops, did I sound a little picky there?

All the best,

Andrew

---

### Post by stansford on 2009-07-30
Andrew,

I wonder if you can help. I am trying to record real audio files using  the standard jaunty mplayer from the repsoitory. My syntax is:

$ mplayer -playlist 2009_29_thu_03.ram -vc null -vo null -cache 1000 -ao pcm:fast:waveheader:file=womans-hour.wav

The .ram file resides on my hard disk and I have no trouble recording this for about 15 of the 60 minutes playing time, but then it bombs out. The screen output is shown below:


$ mplayer -playlist 2009_29_thu_03.ram -vc null -vo null -cache 1000 -ao pcm:fast:waveheader:file=womans-hour.wav
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz (Family: 6, Model: 23, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing rtsp://rmv8.bbc.net.uk/radio4/womanshour/womanshour_20090723.ra?start=59.5&end=988.8&BBC-UID=342a07e15c738619425f7285510f510b0537fcba6030813424bf1496639a49ea&SSO2-UID=.
Resolving rmv8.bbc.net.uk for AF_INET6...
Couldn't resolve name for AF_INET6: rmv8.bbc.net.uk
Resolving rmv8.bbc.net.uk for AF_INET...
Connecting to server rmv8.bbc.net.uk[212.58.252.7]: 554...
Cache size set to 1000 KBytes
Cache fill: 19.20% (196608 bytes)   
REAL file format detected.
Stream description: audio/x-pn-multirate-realaudio logical stream
Stream mimetype: audio/x-pn-realaudio
[real] Audio stream found, -aid 0
Clip info:
 name: - 23 07 2009
 copyright: British Broadcasting Corporation Copyright 2009, all rights reserved.
==========================================================================
Forced audio codec: mad
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 44.1 kbit/3.12% (ratio: 5512->176400)
Selected audio codec: [ffcook] afm: ffmpeg (FFmpeg COOK audio decoder)
==========================================================================
[AO PCM] File: womans-hour.wav (WAVE)
PCM: Samplerate: 44100Hz Channels: Stereo Format s16le
[AO PCM] Info: Faster dumping is achieved with -vc null -vo null -ao pcm:fast
[AO PCM] Info: To write WAVE files use -ao pcm:waveheader (default).
AO: [pcm] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
realrtsp: Stream EOF detected(58:30.0) 96.6% 0% 
A: 990.1 (16:30.0) of 3510.0 (58:30.0) 96.6% 0% 

Exiting... (End of file)

I have tried increasing the cache but that didn't make it any better.
Could this premature exiting be due to the limited codecs available with the standard mplayer in the jaunty repos? 
If not, do you have any idea how I can fix this or is it a case of building mplayer from source as you suggest.
Alternatively are there any prebuilt .debs that are available for the complete mplayer?

Any help appreciated. Thanks

---

### Post by rvm4000 on 2009-07-30
> **stansford said:**
> Alternatively are there any prebuilt .debs that are available for the complete mplayer?

You can find a recent version of mplayer here:
[https://launchpad.net/~rvm/+archive/testing](https://launchpad.net/~rvm/+archive/testing)

---

### Post by andrew.46 on 2009-07-30
Hi stansford,

> **stansford said:**
> I wonder if you can help. I am trying to record real audio files using  the standard jaunty mplayer from the repsoitory. My syntax is:

```
$ mplayer -playlist 2009_29_thu_03.ram -vc null -vo null -cache 1000 -ao pcm:fast:waveheader:file=womans-hour.wav
```



As this is not a live stream there is a slightly different syntax that might work a little better:

```
mplayer -cache 2048 -bandwidth 1000000 rtsp://rmv8.bbc.net.uk/radio4/womanshour/womanshour_20090723.ra -vc null -vo null -ao pcm:fast:waveheader:file=womanshour_20090723.wav
```

I have run this and the full program downloaded in about 10 minutes, you might achieve better speed depending on your available bandwidth.

> Could this premature exiting be due to the limited codecs available with the standard mplayer in the jaunty repos? 

The MPlayer available to Jaunty and earlier is quite old now, interesingly this has at least in part been addressed in Karmic. Personally I would run a newer version, particularly if some problems have been found. But it might be well worthwhile attempting the syntax I have suggested with the repository MPlayer.

> Alternatively are there any prebuilt .debs that are available for the complete mplayer?

RVM has a PPA that would probably be your best bet :-).

All the best,

Andrew

---

### Post by stansford on 2009-07-31
> **rvm4000 said:**
> You can find a recent version of mplayer here:
[https://launchpad.net/~rvm/+archive/testing](https://launchpad.net/~rvm/+archive/testing)

Thanks for the link I'll check it out.

---

### Post by stansford on 2009-07-31
> **andrew.46 said:**
> Hi stansford,



As this is not a live stream there is a slightly different syntax that might work a little better:

```
mplayer -cache 2048 -bandwidth 1000000 rtsp://rmv8.bbc.net.uk/radio4/womanshour/womanshour_20090723.ra -vc null -vo null -ao pcm:fast:waveheader:file=womanshour_20090723.wav
```

I have run this and the full program downloaded in about 10 minutes, you might achieve better speed depending on your available bandwidth.

 

The MPlayer available to Jaunty and earlier is quite old now, interesingly this has at least in part been addressed in Karmic. Personally I would run a newer version, particularly if some problems have been found. But it might be well worthwhile attempting the syntax I have suggested with the repository MPlayer.



RVM has a PPA that would probably be your best bet :-).

All the best,

Andrew

Andrew,
Thanks very much for the help. I'll give the new syntax you suggested a go and see what happens. From looking at it I see you are using the bandwidth parameter, what does that do?

As you said you downloaded the program in 10 minutes, does using this parameter speed up the download? I thought that you could only download in real time?? Ie a 60 min prog took 60 mins to download?

On the RVM front I am looking at the link that rvm4000 gave in his post above. Can I download the .deb and just install it or do I need to first uninstall the version that is currently installed? 

Thanks for your help.

---

### Post by stansford on 2009-07-31
> **andrew.46 said:**
> Hi stansford,



As this is not a live stream there is a slightly different syntax that might work a little better:

```
mplayer -cache 2048 -bandwidth 1000000 rtsp://rmv8.bbc.net.uk/radio4/womanshour/womanshour_20090723.ra -vc null -vo null -ao pcm:fast:waveheader:file=womanshour_20090723.wav
```

I have run this and the full program downloaded in about 10 minutes, you might achieve better speed depending on your available bandwidth.

 

The MPlayer available to Jaunty and earlier is quite old now, interesingly this has at least in part been addressed in Karmic. Personally I would run a newer version, particularly if some problems have been found. But it might be well worthwhile attempting the syntax I have suggested with the repository MPlayer.



RVM has a PPA that would probably be your best bet :-).

All the best,

Andrew

Hi Andrew,

OK I tried your amendments and I got the same result although quicker!
- It downloaded the first 16 minutes and then bombed out. I also tried with the version from the ppa and this yielded the same result.

However, I have been successful in downloading by using the dumpstream method and then converting the stream.dump file to wav afterwards.

I'd be grateful though if you have any futher ideas/thoughts on why I don't seem to be able to grab more than 16/60 minutes using the original one pass method.

My version of mplayer is now:

MPlayer SVN-r29139-4.3.3 (C) 2000-2009 MPlayer Team


thanks

---

### Post by andrew.46 on 2009-07-31
Hi stansford,

> **stansford said:**
> I'd be grateful though if you have any futher ideas/thoughts on why I don't seem to be able to grab more than 16/60 minutes using the original one pass method.

Since you and I have both used a modern version of MPlayer and the same syntax I suspect that you have a network problem rather than an MPlayer/stream problem. (As my own efforts were completely successful).

As for the *-bandwidth* option the man pages simply say that it allows faster cache filling and stream dumping by setting a maximum delivery bandwidth. From a practical point of view it certainly allows very fast download of *some* streams.

Andrew

---

### Post by stansford on 2009-08-02
> **andrew.46 said:**
> Hi stansford,



Since you and I have both used a modern version of MPlayer and the same syntax I suspect that you have a network problem rather than an MPlayer/stream problem. (As my own efforts were completely successful).

As for the *-bandwidth* option the man pages simply say that it allows faster cache filling and stream dumping by setting a maximum delivery bandwidth. From a practical point of view it certainly allows very fast download of *some* streams.

Andrew

Andrew,

You are probably right about the network problem. I am shortly to move to a different provider so I shall try again then and see whether it improves.

Many thanks for your help in sorting this.

---

### Post by stansford on 2009-08-02
> **andrew.46 said:**
> Hi stansford,



Since you and I have both used a modern version of MPlayer and the same syntax I suspect that you have a network problem rather than an MPlayer/stream problem. (As my own efforts were completely successful).

As for the *-bandwidth* option the man pages simply say that it allows faster cache filling and stream dumping by setting a maximum delivery bandwidth. From a practical point of view it certainly allows very fast download of *some* streams.

Andrew

Andrew,

For infor: - further to my last post, I've just tried the original syntax you suggested on my laptop after a clean installation of the latest mplayer and it downloaded fully - all 58 mins very quickly!
Previously this laptop didn't have mplayer installed so I must conclude it must be something to do with the repo mplayer or something else I've installed on my other pc.

At least I know now!

---

### Post by andrew.46 on 2009-08-02
Hi stansford,

> **stansford said:**
> Previously this laptop didn't have mplayer installed so I must conclude it must be something to do with the repo mplayer or something else I've installed on my other pc.

Good to hear you have some success :-). The repository MPlayer is more than a little dated, although I have not heard too many reports of dropped streams. Should be much more interesting when Karmic Koala arrives as it is bringing with it a much more modern MPlayer. I plan on sticking with the svn MPlayer myself, once you start with it you pretty much get hooked :-).

Andrew

---

### Post by stansford on 2009-08-02
> **andrew.46 said:**
> Hi stansford,



Good to hear you have some success :-). The repository MPlayer is more than a little dated, although I have not heard too many reports of dropped streams. Should be much more interesting when Karmic Koala arrives as it is bringing with it a much more modern MPlayer. I plan on sticking with the svn MPlayer myself, once you start with it you pretty much get hooked :-).

Andrew

Well I suppose it all depends what you need it for...but I would tend to  agree. Now that I know how to get and use the latest, there's not much reason to go back to an older version.......

---

### Post by Arup on 2009-08-03
Features like VDPAU and other enhancements are onlyu implemented in the latest mplayer and not the one in the repo.

---

### Post by andrew.46 on 2009-08-04
Hi,

I have added a section that deals with installing the opencore-amr libraries so that once again the svn MPlayer in this guide can play amr/3gp files. Please let me know if there are any problems with the new section.

Andrew

---

### Post by Arup on 2009-08-04
Typing make gives error /usr/bin/ld: wrapper.o: relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
wrapper.o: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[1]: *** [libopencore-amrnb.so.0.1.1] Error 1
make[1]: Leaving directory `/home/arup/opencore-amr/amrnb'
make: *** [all] Error 2

---

### Post by andrew.46 on 2009-08-04
Hi Arup,

> **Arup said:**
> Typing make gives 

```
error /usr/bin/ld: wrapper.o: relocation R_X86_64_32 against 
`a local symbol' can not be used when making a shared object; 
recompile with -fPIC
wrapper.o: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[1]: *** [libopencore-amrnb.so.0.1.1] Error 1
make[1]: Leaving directory `/home/arup/opencore-amr/amrnb'
make: *** [all] Error 2
```


Hmmmm.... looks like it is still very much early days for libopencore-amr :-). I notice that there have been some major changes in the git repository over the last little while. Are you happy to try the newer version? Delete the old version and try the following:

```
$ git clone --depth=1 git://opencore-amr.git.sourceforge.net/gitroot/opencore-amr 
$ cd opencore-amr
$ ./configure
$ make
$ sudo checkinstall --fstrans=no --install=yes --pakdir "$HOME/Desktop" \
--maintainer "$USER" --pkgname="opencore-amr" --pkgversion "0.1.2" \
--backup=no --deldoc=yes --deldesc=yes --delspec=yes --gzman --default
$ make clean
```

This also worked on my system but MPlayer had trouble finding the amrwb libraries.

Thanks for your trouble,

Andrew
[B]
Edit:[/B] Hmmm..... are you using a 64bit installation?

---

### Post by mc4man on 2009-08-04
If having contined issues you should then build these off of the included debian rules (or edit CXXFLAGS in makefiles, easier to do a .debs

**This is just a quick look, will review after work**

To do so just cd to the opencore-amr dir

Before building go into  opencore-amr/amrnb and opencore-amr/amrwb folders.
There will be a makefile in each, you need to edit line 13  and remove /local

Ex.
orig. just remove what's in red
> # Just set OC_BASE to the opencore root, or set AMR_BASE directly to
# a detached gsm_amr directory
OC_BASE = ../opencore
AMR_BASE = $(OC_BASE)/codecs_v2/audio/gsm_amr

# To compile as C instead of C++, define BUILD_AS_C
ifneq (, $(BUILD_AS_C))
    CXX = $(CC)
    CXXFLAGS += -x c -std=c99
endif

ifeq (, $(PREFIX))
    PREFIX = /usr[COLOR="Red"]/local[/COLOR]

Do that for both makefiles, save and then at the /opencore-amr prompt run for 32 bit
```
fakeroot debian/rules binary
```

For  64 bit or  slightly better for 32 also
```
sudo apt-get install devscripts
```

Then at the /opencore-amr prompt run
```
debuild -us -uc
```

above command produces screen

Haven't had a chance to try a 64 bit install, if fPIC is needed then debuild will use with no further makefile edits than described.
From build log 
> make[1]: Entering directory `/home/doug/Desktop/arm5/opencore-amr'
make -C amrnb BUILD_AS_C=1
make[2]: Entering directory `/home/doug/Desktop/arm5/opencore-amr/amrnb'
cc -Wall -g -fPIC -DPIC  -O2 -x c -std=c99 -I../oscl -I../opencore/codecs_v2/audio/gsm_amr/amr_nb/dec/src -I../opencore/codecs_v2/audio/gsm_amr/amr_nb/common/include -I../opencore/codecs_v2/audio/gsm_amr/amr_nb/dec/include -I../opencore/codecs_v2/audio/gsm_amr/common/dec/include -I../opencore/codecs_v2/audio/gsm_amr/amr_nb/enc/src  -c -o wrapper.o wrapper.cpp
ect.,ect.

---

### Post by Arup on 2009-08-04
> **andrew.46 said:**
> Hi Arup,



Hmmmm.... looks like it is still very much early days for libopencore-amr :-). I notice that there have been some major changes in the git repository over the last little while. Are you happy to try the newer version? Delete the old version and try the following:

```
$ git clone --depth=1 git://opencore-amr.git.sourceforge.net/gitroot/opencore-amr 
$ cd opencore-amr
$ ./configure
$ make
$ sudo checkinstall --fstrans=no --install=yes --pakdir "$HOME/Desktop" \
--maintainer "$USER" --pkgname="opencore-amr" --pkgversion "0.1.2" \
--backup=no --deldoc=yes --deldesc=yes --delspec=yes --gzman --default
$ make clean
```

This also worked on my system but MPlayer had trouble finding the amrwb libraries.

Thanks for your trouble,

Andrew
[B]
Edit:[/B] Hmmm..... are you using a 64bit installation?

Andrew,

Thanks for the response, yes I am using x64 Jaunty. Your latest instructions worked out well and open-amr was installed without any hitch on my Jaunty x64.

---

### Post by andrew.46 on 2009-08-05
Hi Arup,

> **Arup said:**
> Thanks for the response, yes I am using x64 Jaunty. Your latest instructions worked out well and open-amr was installed without any hitch on my Jaunty x64.

Good to hear :-). It might be well worthwhile though building formal debian packages as mc4man has suggested, it is a major flaw in most of the guides that I have written that I do not use such packaging....

All the best,

Andrew

**Edit:** Mind you my own experiments with the git libopencore-amr include a failure to build it properly with FFmpeg and MPlayer so I would not class myself as any sort of authority :-).

---

### Post by Arup on 2009-08-05
> **andrew.46 said:**
> Hi Arup,



Good to hear :-). It might be well worthwhile though building formal debian packages as mc4man has suggested, it is a major flaw in most of the guides that I have written that I do not use such packaging....

All the best,

Andrew

**Edit:** Mind you my own experiments with the git libopencore-amr include a failure to build it properly with FFmpeg and MPlayer so I would not class myself as any sort of authority :-).

I just build the open amr, I already have mplayer installed via your instructions. Do you think I should rebuild mplayer again?

---

### Post by andrew.46 on 2009-08-05
Hi Arup,

> **Arup said:**
> I just build the open amr, I already have mplayer installed via your instructions. Do you think I should rebuild mplayer again?

You can interrogate your copy of MPlayer as follows:

```

andrew@skamandros~$ **[COLOR="Red"]mplayer -ac help | grep amr[/COLOR]**

ffamrnb     ffmpeg    working   AMR Narrowband  [libopencore_amrnb]
ffamrwb     ffmpeg    working   AMR Wideband  [libopencore_amrwb]

```

and if you don't see the amr libraries as above you *will* need to rebuild MPlayer. I am still only having success with the release version but I am upgrading my host distro shortly and I suspect the upgrade will heal a few problems.

Mind you when you hear the sound quality of most amr tracks you would wonder why all the effort :-).

All the best,

Andrew

---

### Post by Arup on 2009-08-05
```
ffamrnb     ffmpeg    working   AMR Narrowband  [libopencore_amrnb]
ffamrwb     ffmpeg    working   AMR Wideband  [libopencore_amrwb]

```

Thanks Andrew, this is what I get so I guess its working fine thanks to you.

---

### Post by andrew.46 on 2009-08-06
Hi Arup,

> **Arup said:**
> Thanks Andrew, this is what I get so I guess its working fine thanks to you.

Great news :-). I have parked a 3gp file on my personal website that I encoded with FFmpeg using h263 video and libopencore-amr so if you want to test your installation and Rammstein is your taste try this one:

```
wget http://www.andrews-corner.org/samples/Rammstein_Du_Hast.3gp
```

All the best,

Andrew

---

### Post by Arup on 2009-08-06
> **andrew.46 said:**
> Hi Arup,



Great news :-). I have parked a 3gp file on my personal website that I encoded with FFmpeg using h263 video and libopencore-amr so if you want to test your installation and Rammstein is your taste try this one:

```
wget http://www.andrews-corner.org/samples/Rammstein_Du_Hast.3gp
```

All the best,

Andrew


Works fine on my mplayer compiled thanks to you.

---

### Post by andrew.46 on 2009-08-08
Hi,

Exasperatingly enough the release version of libopencore-amr has vanished from SourceForge and combined with a few problems with the git version has given me enough reason to remove the information from this guide as well :(.

Andrew

---

### Post by andrew.46 on 2009-08-19
Hi,

A patch has surfaced that allows FFmpeg and MPlayer to compile properly with the libopencore-amr libraries:

[http://lists.mplayerhq.hu/pipermail/ffmpeg-user/2009-August/021677.html](http://lists.mplayerhq.hu/pipermail/ffmpeg-user/2009-August/021677.html)

This works well on my system for both FFmpeg and MPlayer but confirms my view that there is a bit more 'settling in' to go with amr and MPlayer.

Andrew

---

### Post by andrew.46 on 2009-09-05
Hi,

For those who have perhaps not already heard the svn MPlayer now has the ability to natively playback wmapro files using ffwmapro. Test your own copy with [WMVHDsplash.wmv]("http://samples.mplayerhq.hu/A-codecs/WMA9/wmapro/WMVHDsplash.wmv") which should play with default settings as follows:

```

andrew@skamandros~/samples$ mplayer WMVHDsplash.wmv 
MPlayer SVN-r29649-4.3.3 (C) 2000-2009 MPlayer Team

Playing WMVHDsplash.wmv.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [WMV3]  1280x720  24bpp  1000.000 fps  6500.0 kbps (793.5 kbyte/s)
==========================================================================
Opening video decoder: [dmo] DMO video codecs
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
Decoder supports the following formats: YV12 YUY2 UYVY YVYU RGB8 RGB555 RGB565 RGB24 RGB32 
Decoder is capable of YUV output (flags 0x1b)
VDec: vo config request - 1280 x 720 (preferred colorspace: Packed YUY2)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 1280x720 => 1280x720 Planar YV12 
Selected video codec: [wmv9dmo] vfm: dmo (Windows Media Video 9 DMO)
==========================================================================
==========================================================================
[B][COLOR="Red"]Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 6 ch, floatle, 384.0 kbit/4.17% (ratio: 48000->1152000)
Selected audio codec: [ffwmapro] afm: ffmpeg (WMA Pro audio (FFmpeg))[/COLOR][/B]
==========================================================================
AO: [oss] 48000Hz 6ch s16le (2 bytes per sample)
Starting playback...
A:  22.9 V:  22.9 A-V:  0.002 ct:  0.040 479/479 36%  4%  3.1% 0 0 

Exiting... (End of file)

```

Huge news!

Andrew

---

### Post by macey on 2009-09-07
Andrew, I am about to embark on this install but my system is far from a 'new' install.
You say "I would also strongly advise that all older versions of x264 are removed..."

How do I do this?
Thanks in anticipation.
Richard

---

### Post by andrew.46 on 2009-09-07
Hi macey,

> **macey said:**
> You say "I would also strongly advise that all older versions of x264 are removed..."

```
sudo apt-get remove x264 libx264-dev
```

will accomplish this. I will admit however that I have been re-thinking this strategy of late as the x264 libraries are only used by MEncoder for h264 conversion, MPlayer has its own decoder in libavcodec. So an alternative, if you do not wish to use Mencoder at all is to omit *all* the x264 compilation and alter the configure string to:

```
./configure --disable-x264 --disable-mencoder
```

and the rest of the guide holds true although you will be loading a few dev files of use only to MEncoder. And dare I say it an even easier option is to go with the current flow in Ubuntu thinking and use the excellent PPA for MPlayer put together by RVM, although you miss out on all the fun or rolling your own :-).

Andrew

---

### Post by gardara on 2009-09-10
Just tried upgrading my x264 and now I'm getting this error:

/usr/local/bin/mplayer: error while loading shared libraries: libx264.so.67: cannot open shared object file: No such file or directory

---

### Post by andrew.46 on 2009-09-10
Hi gardara,

> **gardara said:**
> Just tried upgrading my x264 and now I'm getting this error:

/usr/local/bin/mplayer: error while loading shared libraries: libx264.so.67: cannot open shared object file: No such file or directory

I suspect if you run the following search you will get a similar result to me:

```

**[COLOR="Red"]sudo find /usr -name 'libx264.so.*'[/COLOR]**
/usr/lib/libx264.so.75

```

and you will note that MPlayer is looking for an *older* version, presumably the one you had on your system when you compiled MPlayer. The easiest way to rectiy this problem is to go to your MPlayer source files and run:

```
svn up
```

and subsequently recompile. This should rectify the problem...

Andrew

---

### Post by gardara on 2009-09-11
> **andrew.46 said:**
> Hi gardara,



I suspect if you run the following search you will get a similar result to me:

```

**[COLOR="Red"]sudo find /usr -name 'libx264.so.*'[/COLOR]**
/usr/lib/libx264.so.75

```

and you will note that MPlayer is looking for an *older* version, presumably the one you had on your system when you compiled MPlayer. The easiest way to rectiy this problem is to go to your MPlayer source files and run:

```
svn up
```

and subsequently recompile. This should rectify the problem...

Andrew


That seems to have fixed the problem, cheers!


But however updating x264 and mplayer hasn't fixed my problem like I hoped it would.
The thing is that I recently got a bigger monitor (24") and when I play x264 .mkv files I keep getting some really annyoing horizontal lines in the picture. I think they were there on the smaller monitor but I just didn't notice them.
It's usually a single line in the middle or close to the top or bottom of the video. And mostly occurs in action scenes.
I have not been able to capture a screenshot of this, because when I pause the picture the line disappears.

This does not happen with totem, but happens with smplayer+mplayer.

Any ideas?

---

### Post by andrew.46 on 2009-09-11
Hi gardara,

> **gardara said:**
> That seems to have fixed the problem, cheers!

Excellent news :)

> The thing is that I recently got a bigger monitor (24") and when I play x264 .mkv files I keep getting some really annyoing horizontal lines in the picture. I think they were there on the smaller monitor but I just didn't notice them.
It's usually a single line in the middle or close to the top or bottom of the video. And mostly occurs in action scenes.

Unfortunately x264 is an encoder not a decoder and thus will have no effect on playback.

> I have not been able to capture a screenshot of this, because when I pause the picture the line disappears.

There is a way to capture your screen using MPlayer. Simply run your file as:

```
mplayer -vf screenshot **[COLOR="Red"]myfile.mkv[/COLOR]**
```

and press the 's' key at the appropriate time and MPlayer saves a single screenshot in your working directory.

> This does not happen with totem, but happens with smplayer+mplayer.

Now this I am not so sure about. Certainly if you have an NVidia card you should be using vdpau which is unfortunately something I have no experience with. Otherwise yoou could experiment with the video out settings. Available settings can be seen:

```

andrew@skamandros~$ **[COLOR="Red"]mplayer -vo help[/COLOR]**
MPlayer SVN-r29665-4.3.3 (C) 2000-2009 MPlayer Team
Available video output drivers:
	xv	X11/Xv
	x11	X11 ( XImage/Shm )
	xover	General X11 driver for overlay capable video output drivers
	gl	X11 (OpenGL)
	gl2	X11 (OpenGL) - multiple textures version
	dga	DGA ( Direct Graphic Access V2.0 )
	sdl	SDL YUV/RGB/BGR renderer (SDL v1.1.7+ only!)
	fbdev	Framebuffer Device
	fbdev2	Framebuffer Device
	svga	SVGAlib
	aa	AAlib
	caca	libcaca
	v4l2	V4L2 MPEG Video Decoder Output
	xvidix	X11 (VIDIX)
	cvidix	console VIDIX
	null	Null video output
	mpegpes	MPEG-PES to DVB card
	yuv4mpeg	yuv4mpeg output for mjpegtools
	png	PNG file
	jpeg	JPEG file
	gif89a	animated GIF output
	tga	Targa output
	pnm	PPM/PGM/PGMYUV file
	md5sum	md5sum of each frame


```

You would then try for example:
```

mplayer -vo x11 [COLOR="Red"]**myfile.mkv**[/COLOR]
```

And experiment a little with some of the others. Otherwise I am afraid I am a little lost for ideas :(.

All the best,

Andrew

---

### Post by mc4man on 2009-09-11
@ gardara
What you may want to try is to enable vsync wherever possible.

I have nvidia and while it was only slight 'tearing', while watching Quantum of Solace finally couldn't ignore it anymore. (the chase scene in chapter3 is a good test scene.

I took the 'kitchen sink' approach, so for a nvidia card 

Enabled Sync to VBlank for both  x server xvideo and opengl in nvidia setting (opened nvidia settings as root though I don't think that matters

In compiz (Advanced Desktop Effects Settings) under the General settings -> Display settings also enabled Sync to VBlank

Under the 'general tab unchecked the "Unredirect Fullscreen Windows" box

Now that scene plays flawlessly ( as does all other video

---

### Post by andrew.46 on 2009-09-14
In part of a last minute tidy-up of this guide I have added in details for the new libopencore-amr libraries which appear to have stabilised a little. I shall add in the details of generating the html docs shortly and then finally this guide will be complete, ready to be abandoned by all those rushing to Karmic :).

Andrew

---

### Post by gardara on 2009-09-15
> **mc4man said:**
> @ gardara
What you may want to try is to enable vsync wherever possible.

I have nvidia and while it was only slight 'tearing', while watching Quantum of Solace finally couldn't ignore it anymore. (the chase scene in chapter3 is a good test scene.

I took the 'kitchen sink' approach, so for a nvidia card 

Enabled Sync to VBlank for both  x server xvideo and opengl in nvidia setting (opened nvidia settings as root though I don't think that matters

In compiz (Advanced Desktop Effects Settings) under the General settings -> Display settings also enabled Sync to VBlank

Under the 'general tab unchecked the "Unredirect Fullscreen Windows" box

Now that scene plays flawlessly ( as does all other video

Thanks for the reply.

I enabled Sync to VBlank for everything I could in nvidia-settings. 

But I couldn't do anything under Display settings, it just asked me to use the nvidia tool.

This hasn't changed anything and I have found out that this happens both with x264 and xvid videos, and happens in totem too (not like I thought).


I have tried vdpau, xv and opengl video outputs and it happens in all of them.

So it seems like it's my graphics card fault but not mplayer's. I'm sorry if I'm going off topic here but if anyone else has been experiencing this and has some more tips, I'd be glad to hear about them.

Btw, I'm using nvidia driver 190.32 and have a 512mb geforce 9500m GS

---

### Post by mc4man on 2009-09-15
Sorry it didn't help you though not understanding this
> But I couldn't do anything under Display settings, it just asked me to use the nvidia tool.

Are you looking in CompizConfig Settings Manager? ( in the general options for the unredirect and general options -> display for the sync

Otherwise noticed this thread though what it's related to has never been an issue here with 2 desktops and a laptop all with nvidia ( though I always open nvidia settings as root whether needed or not
```
sudo nvidia-settings
```


[http://ubuntuforums.org/showthread.php?t=1266564](http://ubuntuforums.org/showthread.php?t=1266564)

---

### Post by Adamsz on 2009-09-15
hello... i already have mplayer and smplayer up running perfectly...and now i just notice that libopencore amr for playing several file just added again... so how i gonna add this or update my mplayer...or i have to start all over again..sorry if there any grammar mistake..


huhuhuhuhuhuhuhuhuhuhuhuhu


i solved my problem...

---

### Post by cor2y on 2009-09-23
The Latest svn version of mplayer SVN-r29705 is broken , it nolonger handles x264, video playback via vdpau or anything else, gives an error about mismatched codecs and  instead it looks for the CoreAVC codecs 
```

Matroska file format detected.
VIDEO:  [avc1]  720x480  24bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[h264 @ 0x8975b00]codec type or id mismatches
Could not open codec.
VDecoder init failed :(
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[h264_vdpau @ 0x8975b00]codec type or id mismatches
Could not open codec.
VDecoder init failed :(
Opening video decoder: [dshow] DirectShow video codecs
Win32 LoadLibrary failed to load: CoreAVCDecoder.ax, /usr/lib/codecs/CoreAVCDecoder.ax, /usr/lib/win32/CoreAVCDecoder.ax, /usr/local/lib/win32/CoreAVCDecoder.ax
Warning: DS_Filter() could not open DirectShow DLL.  (DLL=CoreAVCDecoder.ax)
Failed to create DirectShow filter
ERROR: Could not open required DirectShow codec CoreAVCDecoder.ax.
You need to upgrade/install the binary codecs package.
Go to http://www.mplayerhq.hu/dload.html
VDecoder init failed :(
Cannot find codec matching selected -vo and video format 0x31637661.
```
This was with and without vdpau enabled.

---

### Post by andrew.46 on 2009-09-23
Hi Adamsz,

> **Adamsz said:**
> hello... i already have mplayer and smplayer up running perfectly...and now i just notice that libopencore amr for playing several file just added again... so how i gonna add this or update my mplayer...or i have to start all over again..sorry if there any grammar mistake..
i solved my problem...

My apologies I did not receive email notification of your post. I have in fact added libopencore-amr information again. Mind you I added the git information and I have just noticed that there is a release version in place now :(. amr is one of those funny things, it is a little difficult to put in place and when you actually playback a few files with amr you might think: 'I made all that effort for that tinny sound???'. Anyway I shall leave the git info in place for the moment, you only really need to add it in and recompile if you think you might bump into one of these files...

All the best,

Andrew

---

### Post by andrew.46 on 2009-09-23
Hi cor2y,

> **cor2y said:**
> The Latest svn version of mplayer SVN-r29705 is broken , it nolonger handles x264, video playback via vdpau or anything else, gives an error about mismatched codecs and  instead it looks for the CoreAVC codecs 

It looks there has been a flurry of activity with FFmpeg, MPlayer and x264 and I gather x264 changed the rules, followed by FFmpeg, who temporarily broke their decoder while accommodating the changes, and then MPlayer also broke ... Interesting as well that the MPlayer/MEncoder ./configure has raised the bar again with the x264 version:

```

#include <x264.h>
**[COLOR="Red"]#if X264_BUILD < 76[/COLOR]**
#error We do not support old versions of x264. Get the latest from git.
#endif

```

which will mean a few people, myself included, will be scrabbling to update their copy of x264. This has been coasting along at build 75 for some time now. This might cause a little trouble on Karmic for those who wish to compile their own...

As for the CoreAVC mention, I believe that when a codec fails there is a cascade where MPlayer looks for other possibilities, hence the search for the CoreAVC libraries. Good news is that I have just recompiled MPlayer with r29712 and h264 playback is fine on my system, so hopefully this will be the case on your own as well. I have not tested MEncoder encoding with x264 but hopefully this will be back on track as well...

Andrew

---

### Post by cor2y on 2009-09-23
Glad to see an update was pushed out.
I started to panic when i saw vdpau and ffh264 suddenly stopped working when i updated mplayer this afternoon, but a quick visit to the mplayer channel on freenode explained r29705 was broken.
x264 was updated via git before i did mplayer.

---

### Post by andrew.46 on 2009-09-23
Hi cor2y,

> **cor2y said:**
> Glad to see an update was pushed out.
I started to panic when i saw vdpau and ffh264 suddenly stopped working when i updated mplayer this afternoon, but a quick visit to the mplayer channel on freenode explained r29705 was broken.
x264 was updated via git before i did mplayer.

Mind you before I realised that Karmic has a half-decent copy of MPlayer in the repository I was going to do the next version of this guide *without* MEncoder and x264, I am not convinced that so many people actually use MEncoder and most are simply after decent h264 playback...

Andrew

---

### Post by cor2y on 2009-09-23
i do require mencoder and an updated version of that and x264 because i use h264enc interactive script that requires mencoder/mplayer and x264 be uptodate and not the standard old stable ubuntu versions.
[http://h264enc.sourceforge.net/](http://h264enc.sourceforge.net/)
But for most people for just playback i guess its not a requirement.

---

### Post by andrew.46 on 2009-09-23
Hi cor2y,

> **cor2y said:**
> i do require mencoder and an updated version of that and x264 because i use h264enc interactive script that requires mencoder/mplayer and x264 be uptodate and not the standard old stable ubuntu versions.

That script has come up a few times recently, I was a little staggered when I downloaded it and found that the script has 9,471 lines!

Andrew

---

### Post by mc4man on 2009-09-24
> This might cause a little trouble on Karmic for those who wish to compile their own...

I have karmic now, but am resisting the temptation to modify till it hit's rc, though couldn't help putting  new ffmpeg, mplayer and vlc 1.02 packages in place. (there is quite an irony about vlc 1.02, wmapro and karmic

once karmic releases I'd think rvm would supply a 76 libx264 on his ppa and deb's could be available elsewhere.

Just did a quick set off of the current git though i think it's best to leave out of karmic for the moment

---

### Post by andrew.46 on 2009-09-24
Hi mc4man,

> **mc4man said:**
> once karmic releases I'd think rvm would supply a 76 libx264 on his ppa and deb's could be available elsewhere.

I am sure such packages will be available and I realise that PPAs seem to be all the go these days but I will have to admit to still being a big fan of people 'rolling their own' MPlayer, FFmpeg Transcode and the like. I suspect this is a minority view and so many people just want to get the software running without too much though about it, but the benefits of getting more involved in building your own versions of multimedia software are, as you know, quite considerable. 

Hmmm... when did I become such a dinosaur :).

Andrew

---

### Post by mc4man on 2009-09-24
> but the benefits of getting more involved in building your own versions of multimedia software are, as you know, quite considerable.
I totally agree, there's a lot that can learned about an app just by building it, or even failing at building it. ( possibly failures and or issues can be even more educational or 'eye-opening'

---

### Post by cor2y on 2009-09-24
Me too i like compiling my own software, it teaches you the use of the terminal and syntax.
What i have yet to learn though is how to correctly compile into a deb package so there arent clashes in synaptic, for example x264 and libx264 , checkinstall is the quick way of doing it but sometimes some apps via synaptic require the dev and library headers and dont see it in synaptic if you installed x264 using checkinstall, i'll have to get on learning how to build proper deb packages when i have time.

---

### Post by tomrickards on 2009-09-24
I have been messing with multithreaded mencoder and ffmpeg all afternoon trying to get it to work, I have ended up in this thread.  Trying to get PS3 media server working on 9.04 64 bit, i finally have tsmuxer working, but mencoder is giving me this:

[Thread-87] DEBUG 16:58:45.584 Stream with high frequencies VQ coding
[Thread-87] DEBUG 16:58:45.584 [ac3 @ 0x1ff67e0]codec type or id mismatches
[Thread-87] DEBUG 16:58:45.584 Couldn't open codec ac3, br=640.
[mencoder] DEBUG 16:58:45.585 EOF
[mencoder] TRACE 16:58:45.585 Process mencoder has a return code of 1!

Is this related to the issues you mention?

PS.  I should mention I have been installing via:
git clone git://gitorious.org/ffmpeg/ffmpeg-mt.git
svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer
git clone git://git.videolan.org/x264.git

and using the codecs from ffmpeg-mt in mplayer, then make and make install on each.

---

### Post by FakeOutdoorsman on 2009-09-24
> **cor2y said:**
> Me too i like compiling my own software, it teaches you the use of the terminal and syntax.
What i have yet to learn though is how to correctly compile into a deb package so there arent clashes in synaptic, for example x264 and libx264 , checkinstall is the quick way of doing it but sometimes some apps via synaptic require the dev and library headers and dont see it in synaptic if you installed x264 using checkinstall, i'll have to get on learning how to build proper deb packages when i have time.

I don't see any packages that depend on libx264-dev.  I don't recall ever encountering any packages from the repo that require a *-dev besides other *-dev.

---

### Post by cor2y on 2009-09-25
My MIstake i meant plain libx264
The Non Linear Editors in particular like open movieeditor cinelerra , kdenlive etc.

---

### Post by AndrewSimoes on 2009-09-25
Hi Andrew,
Thanks for your guide; it was super.

One problem I am experiencing  is with mencoder while using lavc.

when typing the following code:

mencoder -idx "California Dreamin'" -oac copy -ovc lavc -o cd.avi

I am getting this error:

videocodec: libavcodec (320x240 fourcc=34504d46 [FMP4])
[mpeg4 @ 0x9f84bd0]codec type or id mismatches
Could not open codec.
FATAL: Cannot initialize video driver.
VDec: vo config request - 320 x 240 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
videocodec: libavcodec (320x240 fourcc=34504d46 [FMP4])
Could not open codec.
FATAL: Cannot initialize video driver.

I am using Jaunty. Any idea what the problem is? Help would be much appreciated.

---

### Post by andrew.46 on 2009-09-25
Hi Andrew,

> **AndrewSimoes said:**
> 
```

videocodec: libavcodec (320x240 fourcc=34504d46 [FMP4])
[mpeg4 @ 0x9f84bd0]codec type or id mismatches
Could not open codec.
```


This is broken on my system as well with an identical error. By default MEncoder encodes with mpeg4 (fourcc FMP4) when no other codec is specified with *-ovc lavc* and in this case it is failing. On further testing I notice that most of the libavcodec encoders are broken as well :). Can I ask what revision you are using? I am using:

```
andrew@skamandros~$ **[COLOR="Red"]mplayer | head -n 1[/COLOR]**
MPlayer SVN-r29714-4.3.3 (C) 2000-2009 MPlayer Team
```

If we have both compiled recently it may be a matter of either waiting a day or 2, posting to MPlayer-users or going back a few revisions...

**Edit:** In a sure indication of how patient I actually am I have [posted to MPlayer-users]("http://lists.mplayerhq.hu/pipermail/mplayer-users/2009-September/077866.html") with this odd error. Hopefully I will not get my head bitten off :).

Andrew

---

### Post by andrew.46 on 2009-09-25
Hi tom,

> **tomrickards said:**
> I have been messing with multithreaded mencoder and ffmpeg all afternoon trying to get it to work, I have ended up in this thread.

I am afraid that I will be no help to you with this one, I tend to use FFmpeg rather than MEncoder and yours is a fairly modified MEncoder at that. Hopefully somebody will have an answer?

Andrew

---

### Post by cor2y on 2009-09-25
tomrickards what version of mplayer did you compile?
I have the multicore support on another pc that doesnt have a nvidia card so it cant use vdpau and i ran into to problems with mplayer not being able to playback when updated to SVN-r29705  because that release was broken, try the previous version of that or update to SVN-r29712.
The codec mismatch id error for mencoder seems similar to the one i got in mplayer when trying to playback H.264 encoded media.
So it could be the problem.

---

### Post by AndrewSimoes on 2009-09-25
Hey Andrew ,
It's fixed under the last release.
Thanks for the help :)

---

### Post by andrew.46 on 2009-09-25
Hi Andrew,

> **AndrewSimoes said:**
> It's fixed under the last release. Thanks for the help :)

Excellent news! I am just about to svn up and check it out...

Andrew

---

### Post by andrew.46 on 2009-09-26
Hi mc4man,

> **mc4man said:**
> I have karmic now, but am resisting the temptation to modify till it hit's rc, though couldn't help putting  new ffmpeg, mplayer and vlc 1.02 packages in place.

There seems to be a bit of a problem with gcc 4.4.1 and compiling the svn MPlayer with pretty regular crashes on playback of most mkv files. Looks like a stand-off between the gcc devs and MPlayer at the moment. I experienced this crash on Karmic + MPlayer and it could be reproduced over and over on several mkv files.

Andrew

---

### Post by Nepherte on 2009-09-26
Just apply this patch:
```
--- mplayer/configure.old	2009-04-16 12:02:10.000000000 +0200
+++ mplayer/configure	2009-05-22 15:23:38.000000000 +0200
@@ -6410,6 +6410,7 @@
 def_liba52='#undef CONFIG_LIBA52'
 def_liba52_internal="#undef CONFIG_LIBA52_INTERNAL"
 if test "$_liba52_internal" = yes ; then
+	test "$cc_vendor" = gnu && test "$cc_version" = 4.4.1 && CFLAGS=$(echo $CFLAGS|sed "s/ *-O4 */ -O2 /")
   _liba52=yes
   def_liba52_internal="#define CONFIG_LIBA52_INTERNAL 1"
   _res_comment="internal"
```

---

### Post by andrew.46 on 2009-09-26
Hi Nepherte,

> **Nepherte said:**
> Just apply this patch...

I remember seeing that one proposed [a while back]("http://lists.mplayerhq.hu/pipermail/mplayer-dev-eng/2009-May/061538.html") but I gather it was not applied. Seems a pity as it gets around an awkward issue but I gather the MPlayer developers are going to wait for gcc to be fixed instead .... Meanwhile anybody who compiles MPlayer on Karmic, and is not aware of this hack, will have problems.

Andrew

---

### Post by Nepherte on 2009-09-26
MPlayer had the same issue with gcc 4.4.0 and they indeed decided it was up to gcc to fix the problem. If I remember correctly, they indeed included some sort of patch in 4.4.1. But apparantly, it isn't working. Highly inconvenient.

---

### Post by gardara on 2009-10-05
How about the CoreAVC codec, any reason why it isn't in the manual?

[http://code.google.com/p/coreavc-for-linux/](http://code.google.com/p/coreavc-for-linux/)

---

### Post by andrew.46 on 2009-10-05
Hi gardara,

> **gardara said:**
> How about the CoreAVC codec, any reason why it isn't in the manual?

I guess this guide aims to present the *basics* of compiling and installing the subversion MPlayer under Jaunty. With this under your belt it is more than possible to explore things like CoreAVC, but I only cover that I have personal experience with I'm afraid.

Andrew

---

### Post by mc4man on 2009-10-05
> How about the CoreAVC codec
you may wish to look [here]("http://ubuntuforums.org/showthread.php?t=1034075")

---

### Post by stanjr on 2009-10-07
I have made a bash script for everyone.  I hope it is helpful in getting done what this thread is for.  PLEASE comment and approve upon where necessary!  [here]("http://pastebin.com/f20cc46cb") is a link to the pastebin site that I have posted it.  Here it is in "code" form:
```
###########
#         #
# GENERAL #
#         #
###########

sudo apt-get update # TYPE Y FOR ANY QUESTIONS
sudo apt-get upgrade # TYPE Y FOR ANY QUESTIONS
sudo apt-get autoremove # TYPE Y FOR ANY QUESTIONS

################################################################################
# THE NEXT TWO MKDIR CODE LINES BELOW SHOULD BE UNCOMMENTED IF FIRST TIME RUN. #
# CHANGE WHERE YOU WANT STUFF TO GO WHERE YOU WANT IT, STILL COMMENT BACK OUT  #
# ON SUBSEQUENT RUNS.  (CHANGE THE /Programs/build and /Programs/current       #
# TO WHAT YOU WISH THEM TO BE, BUT STILL COMMENT OUT THE MKDIR LINES           #
# AFTER FIRST RUN).  ALL LINES SUBSEQUENT TO THE EXPORT LINES SHOULD ALL BE    #
# COMMENTED OUT TOO....BUT ONLY BEFORE INITIAL RUN.                            #
################################################################################

#mkdir $HOME/Programs/build
#mkdir $HOME/Programs/current

export BUILD=$HOME/Programs/build
export CURRENT=$HOME/Programs/current

cd $BUILD

#git clone git://git.sv.gnu.org/automake.git
#mv automake automake_GIT-PULLsvn co http://www.tortall.net/svn/yasm/trunk/yasm yasm_SVN-UPDATE
#git clone --depth=1 git://opencore-amr.git.sourceforge.net/gitroot/opencore-amr/opencore-amr
#mv opencore-amr opencore-amr_GIT-PULL
#git clone git://git.videolan.org/x264.git
#mv x264 x264_GIT-PULL
#svn checkout svn://svn.ffmpeg.org/ffmpeg/trunk ffmpeg_SVN-UPDATE
#svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer_SVN-UPDATE
#wget http://www.live555.com/liveMedia/public/live555-latest.tar.gz
#tar xvf live555-latest.tar.gz
#mv live live_LIVE555-CODECS
#wget http://www.mplayerhq.hu/MPlayer/releases/codecs/all-20071007.tar.bz2
#tar xjvf all-20071007.tar.bz2
#mv all-20071007 all-20071007_MPLAYER-CODECS
#svn co http://www.tortall.net/svn/yasm/trunk/yasm yasm_SVN-UPDATE
#git clone git://git.sv.gnu.org/automake.git
#mv automake automake_GIT-PULL
#rm -R *.bz2 *.gz


#####################################################
#                                                   #
# DEV FILES NEEDED                                  #
#                                                   #
# (The files are per what was "needed"              #
# from the VERY helpful resource at                 # 
# http://ubuntuforums.org/showthread.php?t=1081070) #
# ...last updated as far as I know on 9/15/09       #
# This can be proabably commented out after         #
# inital run...                                     #
#                                                   #
#####################################################

#sudo apt-get install build-essential checkinstall gpac libgpac-dev git-core debhelper em8300-headers gawk gettext html2text intltool-debian ladspa-sdk libaa1-dev libasound2-dev libatk1.0-dev libaudio-dev libaudio2 libaudiofile-dev libavahi-client-dev libavahi-common-dev libcaca-dev libcairo2-dev libcdparanoia-dev libcelt0 libdbus-1-dev libdbus-glib-1-dev libdirectfb-dev libdirectfb-extra libdts-dev libdv4-dev libenca-dev libenca0 libesd0-dev libexpat1-dev libfaac-dev libfaac0 libffado0 libfontconfig1-dev libfreebob0 libfreetype6-dev libfribidi-dev libggi-target-x libggi2 libggi2-dev libggimisc2 libggimisc2-dev libgif-dev libgii1 libgii1-dev libgii1-target-x libgl1-mesa-dev libglib2.0-dev libglu1-mesa-dev libgtk2.0-dev libice-dev libjack-dev libjack0 libjpeg62-dev liblzo-dev liblzo1 liblzo2-2 liblzo2-dev libmad0-dev libmail-sendmail-perl libmp3lame-dev libmp3lame0 libmpcdec-dev libmpcdec3 libncurses5-dev libogg-dev libopenal-dev libopenal1 libpango1.0-dev libpixman-1-dev libpng12-dev libpopt-dev libpthread-stubs0 libpthread-stubs0-dev libpulse-dev libpulse-mainloop-glib0 libsdl1.2-dev libslang2-dev libsm-dev libsmbclient-dev libspeex-dev libsvga1 libsvga1-dev libsys-hostname-long-perl libsysfs-dev libtheora-dev libtwolame-dev libtwolame0 libvorbis-dev libx11-dev libxau-dev libschroedinger-dev libstdc++5 libxcb-render-util0-dev libxcb-render0-dev libxcb1-dev libxcomposite-dev libxcursor-dev libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxml++2.6-2 libxrandr-dev libxrender-dev libxt-dev libxv-dev libxvidcore4-dev libxvmc-dev libxxf86dga-dev libxxf86vm-dev mesa-common-dev po-debconf sharutils x11proto-composite-dev x11proto-core-dev x11proto-damage-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-render-dev x11proto-video-dev x11proto-xext-dev x11proto-xf86dga-dev x11proto-xf86vidmode-dev x11proto-xinerama-dev xtrans-dev zlib1g-dev liboil0.3-dev libcddb2-dev

##########################################################################################
#                                                                                        #
# If starting from scratch, you only need to install Live555 and the "codecs" once.      #
# So, comment the lines below if you have already done this and don't want to do it      #
# again.  AKA, if this is the first time you have run this script, leave the code as is, #
# NOT THE ACTUAL COMMENT LINES!!!  I am not going to give a lesson on what is "code"     #
# and what is a "comment."  Make sure to recomment out the code lines after having done  #
# this part once, and are going to run it again for upkeeping purposes or something,     #
# else you are wasting your time.  Nothing bad can happen, but you are                   #
# WASTING YOUR TIME.  If you want your "build" directory different than what I've used,  #
# then make it so.  You should be able to figure that out for yourself.                  #
#                                                                                        #
# I'LL PUT NOTES ABOVE COMMENT-OUTTABLE CODE IF THIS IS A SECOND-OR-MORE-RUN-THANG.      #
#                                                                                        #
# I add sudo ldconfigs pretty much at the end of everything, that usually helps solve    #
# a lot of problems that pop up, at least it did for me, and it can't hurt to just       #
# put it in, just in case...                                                             #
#                                                                                        #
# I am not fully ***-holic.                                                              #
#                                                                                        #
##########################################################################################

##################################################################################
#                                                                                #
# INSTALL THE CODECS                                                             #
#                                                                                #
# (I don't know when something newer than this will be made, but at the time of  #
# this writing (10/9/09), this is the latest).  THIS CAN PROBABLY BE COMMENTED   #
# OUT AFTER INITIAL RUN, but I just leave it for whatever reason.  (When will a  #
# git or svn be created for this?)                                               # 
#                                                                                #
##################################################################################

#sudo mkdir -pv /usr/lib/codecs
#sudo cp -v $BUILD/all-20071007_MPLAYER-CODECS/* /usr/lib/codecs
#sudo ldconfig

##################################################################################
#                                                                                #
# INSTALL THE LIVE555 CODECS                                                     #
#                                                                                #
# (I don't know when something newer than this will be made, but at the time of  #
# this writing (10/9/09), this is the latest).  THIS CAN PROBABLY BE COMMENTED   #
# OUT AFTER INITIAL RUN, but I just leave it for whatever reason.  (When will a  #
# git or svn be creater for this?)                                               #
#                                                                                #
##################################################################################

#cd $BUILD/live_LIVE555-CODECS
#./genMakefiles linux
#make --jobs=6
#sudo cp -r $BUILD/live_LIVE555-CODECS /usr/lib
#sudo ldconfig

#######################################################################
#                                                                     #
# INSTALL THE SOURCE FONT                                             #
#                                                                     # 
# (The font can be whatever you like, I actually like Liberation Sans #
# which was already on my system, peruse your fonts and see what      #  
# suits your fancy as a font, then pick it, putting in the path       #
# and name path as needed.)  THIS CAN PROBABLY BE COMMENTED OUT AFTER #
# INITIAL RUN, but I leave it for whatever reason.                    #
#                                                                     #
#######################################################################

#mkdir -v $HOME/.mplayer
#ln -sv /usr/share/fonts/truetype/ttf-liberation/LiberationSan-Bold/ttf $HOME/.mplayer/subfont.ttf
#sudo ldconfig

#################################################################
#                                                               #
# COMPILE AUTOMAKE                                              #
#                                                               #
# (I like to be up on the cuttin' edge                          #
# of my automake)                                               #
# (doesn't create a .deb file in $CURRENT)                      #
# (Could someone tell me how to get this done, per how          #
# it's done in the x264 and mplayer steps below?)               #
#                                                               #
#################################################################

cd $BUILD/automake_GIT-PULL
git pull
./bootstrap
./configure CFLAGS=-O3
make --jobs=6
sudo make install
sudo ldconfig
make distclean

#################################################################
#                                                               #
# COMPILE YASM                                                  #
#                                                               #
# (I like to be up on the cuttin' edge of                       #
# my yasm)                                                      #
# (doesn't create a .deb file in $CURRENT) #
# (Could someone tell me how to get this done, per how          #
# it's done in the x264 and mplayer steps below?)               #
#                                                               #
#################################################################

cd $BUILD/yasm_SVN-UPDATE
svn update
./autogen.sh
./configure CFLAGS=-O3
make --jobs=6
sudo make install
sudo ldconfig
make distclean

###########################
#                         # 
# COMPILE LIBOPENCORE-AMR #
#                         #  
###########################

cd $BUILD/opencore-amr_GIT-PULL
git pull
autoreconf -vfi
./configure CFLAGS=-O3
make --jobs=6
sudo checkinstall --fstrans=no --install=yes --pakdir=$CURRENT --maintainer=$USER --pkgname="libopencore-amr" --pkgversion="`date +%Y%m%d`" --backup=no --deldoc=yes --deldesc=yes --delspec=yes --gzman --default
sudo ldconfig
make distclean

################
#              # 
# COMPILE X264 #
#              #
################

cd $BUILD/x264_GIT-PULL
git pull
./configure --prefix=/usr --enable-shared --extra-cflags=-O3
make --jobs=6
sudo checkinstall --fstrans=no --install=yes --pakdir=$CURRENT --maintainer=$USER --pkgname=x264 --pkgversion="1:0.svn`date +%Y%m%d`-0.0ubuntu1" --backup=no --deldoc=yes --deldesc=yes --delspec=yes --gzman --default
sudo ldconfig
make distclean

###############################################################
#                                                             #
# COMPILE FFMPEG                                              #
#                                                             #
# This is probably not necessary, but I compile it for my     #
# own reasons to that it is up-to-date with the x264 that     #
# I just finished compiling...                                #
#                                                             #
# The enables given here were the only ones I could get       #
# to work on my system.  Check out your ./configure --help    #
# to find out all you can try to enable.                      #
# (doesn't create .deb file in $CURRENT) #
# (Could someone tell me how to get this done, per how        #
# it's done in the x264 and mplayer steps below?)             #
#                                                             #
###############################################################

cd $BUILD/ffmpeg_SVN-UPDATE
svn update
./configure --enable-shared --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-avfilter --enable-avfilter-lavf --enable-pthreads --enable-x11grab --enable-gray --enable-runtime-cpudetect --enable-bzlib --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libdc1394 --enable-libdirac --enable-libfaac --enable-libfaad --enable-libgsm --enable-libmp3lame --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-zlib --extra-cflags=-O3
make --jobs=6
sudo make install
sudo ldconfig
make distclean

###################
#                 #
# COMPILE MPLAYER #
#                 #
###################

cd $BUILD/mplayer_SVN-UPDATE
svn update
./configure --codecsdir=/usr/lib/codecs --confdir=/etc/mplayer --enable-gui --extra-cflags=-O3
make --jobs=6
sudo checkinstall -D --install=yes --fstrans=no --pakdir=$CURRENT --pkgname=mplayer --pkgversion="3:1.0~svn-`grep "#define VERSION" version.h | cut -d"-" -f2`" --backup=no --deldoc=yes --deldesc=yes --delspec=yes --default --provides="mplayer,mencoder"
sudo ldconfig
make distclean
```

---

### Post by helpdeskdan on 2009-10-10
Has anybody had any lucky compiling gecko-mediaplayer from svn?  Is there a howto somewhere?  I believe there is a patch to fix apple trailers which I wish to try.

---

### Post by helpdeskdan on 2009-10-11
Never mind!  It worked out of the box!

sudo apt-get install gnome-mplayer
./configure
make
checkinstall

Can watch the Apple trailers again:
[http://www.apple.com/trailers/](http://www.apple.com/trailers/)

---

### Post by kwokyinc on 2009-10-12
Hi Andrew.46 , 

I followed your guide and installed the latest smplayer from the developer's repository. Mplayer (SVN-r29770-4.3.3) works okay stand alone. But smplayer (0.6.8 (SVN r3213)) won't play any file and gave an error of "MPlayer was compiled without fontconfig support". Any idea what went wrong?

Edits: I unchecked the "freetype support" under the "subtitle" tab and smplayer now works ok.

---

### Post by piousp on 2009-10-14
Are you gonna 'upgrade' this guide for karmic? Or the guide will work with karmic? Thanks in advance

---

### Post by andrew.46 on 2009-10-14
Hi piousp,

> **piousp said:**
> Are you gonna 'upgrade' this guide for karmic? Or the guide will work with karmic? 

For quite some time it was my intention to no longer create these MPlayer guides following Jaunty Jackalope in particular since the repository MPlayer has improved dramatically under Karmic. However I have produced a slightly altered guide for the svn MPlayer under Karmic and there is a version on these forums at the moment that is for testing purposes:

Can a few people test a Karmic installation guide for the svn MPlayer?
[http://ubuntuforums.org/showthread.php?t=1280543](http://ubuntuforums.org/showthread.php?t=1280543)

It would be great if you could test it :). A few differences in the aim of this guide...

Andrew

---

### Post by piousp on 2009-10-18
> **andrew.46 said:**
> Hi piousp,



For quite some time it was my intention to no longer create these MPlayer guides following Jaunty Jackalope in particular since the repository MPlayer has improved dramatically under Karmic. However I have produced a slightly altered guide for the svn MPlayer under Karmic and there is a version on these forums at the moment that is for testing purposes:

Can a few people test a Karmic installation guide for the svn MPlayer?
[http://ubuntuforums.org/showthread.php?t=1280543](http://ubuntuforums.org/showthread.php?t=1280543)

It would be great if you could test it :). A few differences in the aim of this guide...

Andrew


Nice nice nice!!! :KS
I'll try your guide on Karmic beta tomorrow!
Thanks for all your efforts!

---

### Post by gardara on 2009-10-30
> **andrew.46 said:**
> Hi piousp,



For quite some time it was my intention to no longer create these MPlayer guides following Jaunty Jackalope in particular since the repository MPlayer has improved dramatically under Karmic. However I have produced a slightly altered guide for the svn MPlayer under Karmic and there is a version on these forums at the moment that is for testing purposes:

Can a few people test a Karmic installation guide for the svn MPlayer?
[http://ubuntuforums.org/showthread.php?t=1280543](http://ubuntuforums.org/showthread.php?t=1280543)

It would be great if you could test it :). A few differences in the aim of this guide...

Andrew

Awesome! I'll check it out!

---

### Post by andrew.46 on 2009-10-30
Hi gardara,

> **gardara said:**
> Awesome! I'll check it out!

That thread has been closed, as have all the Karmic testing threads. But I have submitted the guide to 'Tutorials & Tips' where hopefully it will pop up shortly after moderation.

Andrew

---

### Post by piousp on 2009-10-31
> **andrew.46 said:**
> Hi gardara,



That thread has been closed, as have all the Karmic testing threads. But I have submitted the guide to 'Tutorials & Tips' where hopefully it will pop up shortly after moderation.

Andrew

Hey Andrew, can you give me the new thread for your guide in karmic?
At long last, i'm gonna test VDPAU!
Thanks again!

---

### Post by andrew.46 on 2009-10-31
Hi piousp,

> **piousp said:**
> Hey Andrew, can you give me the new thread for your guide in karmic?
At long last, i'm gonna test VDPAU!

Still waiting for the guide to appear. These guides have to be submitted for moderation and this all depends on how busy the moderators are, but hopefully soon :).

I have actually removed the vdpau info from the guide as I am not qualified to write about vdpau in any authoritative fashion. But it should be a simple matter of adding the required NVidia drivers +/- vdpau package and then MPlayer should automagically pick up the files and allow *-vo vdpau*.

Andrew

---

### Post by piousp on 2009-11-01
> **andrew.46 said:**
> Hi piousp,



Still waiting for the guide to appear. These guides have to be submitted for moderation and this all depends on how busy the moderators are, but hopefully soon :).

I have actually removed the vdpau info from the guide as I am not qualified to write about vdpau in any authoritative fashion. But it should be a simple matter of adding the required NVidia drivers +/- vdpau package and then MPlayer should automagically pick up the files and allow *-vo vdpau*.

Andrew

Hi Andrew,
can you post the link to the new guide right here please?
Kudos to you

---

### Post by andrew.46 on 2009-11-02
Hi piousp,

> **piousp said:**
> can you post the link to the new guide right here please?

Howto: Utilise the svn MPlayer to Improve Karmic Koala's 'mplayer-nogui' Package
[http://ubuntuforums.org/showthread.php?t=1305181](http://ubuntuforums.org/showthread.php?t=1305181)

BTW I have added in the repository vdpau -dev package after some pressure :).

Andrew

---

### Post by piousp on 2009-11-02
> **andrew.46 said:**
> Hi piousp,



Howto: Utilise the svn MPlayer to Improve Karmic Koala's 'mplayer-nogui' Package
[http://ubuntuforums.org/showthread.php?t=1305181](http://ubuntuforums.org/showthread.php?t=1305181)

BTW I have added in the repository vdpau -dev package after some pressure :).

Andrew

Hi Andrew,
you have my thanks for all your efforts! :KS

---

### Post by andrew.46 on 2009-11-10
Hi,

For the benefit of any Jaunty users starting out on this guide I have just now included the release version of the libopencore-amr libraries.

All the best,

Andrew

---

### Post by motorhead_1 on 2010-03-08
can anybody halp with this MSS2 problem? 
I've installed these codecs following [this]("http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-904-jaunty.html") but it seems that I still cannot play those MSS2 ....

[https://launchpad.net/~rvm/+archive/mplayer]("https://launchpad.net/%7Ervm/+archive/mplayer")

---

### Post by andrew.46 on 2010-03-08
Hi motorhead_1,

I have replied in some detail on [the other thread]("http://ubuntuforums.org/showthread.php?t=1414115") but the missing piece of the puzzle is: are you running 64 bit or 32 bit? To play this file you need access to the w32codecs from Medibuntu...

All the best,

Andrew

---

### Post by motorhead_1 on 2010-03-08
Hello Andrew, 
I'm running 32 bit, so technically how do I work it out? I've the medibuntu repositories and in the last lines you can see this [https://launchpad.net/~rvm/+archive/mplayer]("https://launchpad.net/%7Ervm/+archive/mplayer")
however I'm not quite sure of what I'm doing

```
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://it.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://it.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://it.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://it.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://it.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://it.archive.ubuntu.com/ubuntu/ karmic universe
deb http://it.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://it.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://it.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://it.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://it.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://it.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://it.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://it.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse
deb http://packages.medibuntu.org/ karmic free non-free
deb-src http://packages.medibuntu.org/ karmic free non-free

# Per risolvere il problema di Chrome
deb http://ppa.launchpad.net/setack/stuff/ubuntu karmic main

#Virtualbox
deb http://download.virtualbox.org/virtualbox/debian karmic non-free
deb http://www.mendeley.com/repositories/xUbuntu_9.04 /

#MPlayer packages for Ubuntu.
deb http://ppa.launchpad.net/rvm/mplayer/ubuntu karmic main 
deb-src http://ppa.launchpad.net/rvm/mplayer/ubuntu karmic main 
```

---

### Post by andrew.46 on 2010-03-08
Hi Motorhead,

Looks like you have it all mostly in place :). If I were you I would add in [rvm's SMPlayer PPA]("https://launchpad.net/~rvm/+archive/smplayer"):

```
$ sudo add-apt-repository ppa:rvm/smplayer
```

and then run:

```
$ sudo apt-get update && sudo apt-get upgrade
$ sudo apt-get install smplayer mplayer w32codecs
```

and I would be very surprised if you could not play your problem file... BTW I have given directions for Karmic with the PPA although you have inadvertently posted your question in a thread devoted to Jaunty :).

All the best,

Andrew

---

### Post by motorhead_1 on 2010-03-08
ooops my mistake for Jaunty posting, I'm of course running Karmic. thanks! I guess something went wrong anyhow:

```
daitarn@daitarn-laptop:~$ **sudo add-apt-repository ppa:rvm/smplayer**
[sudo] password for daitarn: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv E23A3C5344AE497C2FEE7B0BA7E13D78E4A4F4F4
gpg: requesting key E4A4F4F4 from hkp server keyserver.ubuntu.com
gpg: key E4A4F4F4: public key "Launchpad PPA named smplayer for rvm" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
daitarn@daitarn-laptop:~$ **sudo apt-get update && sudo apt-get upgrade**
Hit http://it.archive.ubuntu.com karmic Release.gpg
Hit http://packages.medibuntu.org karmic Release.gpg                           
Ign http://packages.medibuntu.org karmic/free Translation-en_US                
Get:1 http://dl.google.com stable Release.gpg [189B]                           
Ign http://dl.google.com stable/main Translation-en_US                         
Get:2 http://ppa.launchpad.net karmic Release.gpg [307B]                       
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Get:3 http://archive.canonical.com karmic Release.gpg [189B]                   
Ign http://archive.canonical.com karmic/partner Translation-en_US              
Ign http://packages.medibuntu.org karmic/non-free Translation-en_US            
Hit http://packages.medibuntu.org jaunty Release.gpg                           
Ign http://packages.medibuntu.org jaunty/free Translation-en_US                
Ign http://packages.medibuntu.org jaunty/non-free Translation-en_US            
Hit http://security.ubuntu.com karmic-security Release.gpg                     
Hit http://packages.medibuntu.org karmic Release                               
Ign http://security.ubuntu.com karmic-security/main Translation-en_US          
Ign http://www.mendeley.com  Release.gpg                                       
Ign http://it.archive.ubuntu.com karmic/main Translation-en_US                 
Get:4 http://dl.google.com stable Release [2,540B]                             
Get:5 http://ppa.launchpad.net karmic Release.gpg [307B]                       
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Get:6 http://ppa.launchpad.net karmic Release.gpg [307B]                       
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Hit http://packages.medibuntu.org jaunty Release                               
Get:7 http://archive.canonical.com karmic Release [9,347B]                     
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US    
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US      
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US    
Hit http://security.ubuntu.com karmic-security Release                         
Get:8 http://ppa.launchpad.net karmic Release [66.0kB]                         
Ign http://it.archive.ubuntu.com karmic/restricted Translation-en_US           
Get:9 http://ppa.launchpad.net karmic Release [66.0kB]                         
Get:10 http://ppa.launchpad.net karmic Release [66.0kB]                        
Ign http://www.mendeley.com  Translation-en_US                                 
Hit http://download.virtualbox.org karmic Release.gpg                          
Ign http://download.virtualbox.org karmic/non-free Translation-en_US           
Hit http://packages.medibuntu.org karmic/free Packages                         
Ign http://ppa.launchpad.net karmic Release                                    
Ign http://ppa.launchpad.net karmic Release                                    
Get:11 http://dl.google.com stable/main Packages [914B]                        
Ign http://it.archive.ubuntu.com karmic/universe Translation-en_US             
Hit http://packages.medibuntu.org karmic/non-free Packages                     
Hit http://packages.medibuntu.org karmic/free Sources                          
Hit http://packages.medibuntu.org karmic/non-free Sources                      
Hit http://packages.medibuntu.org jaunty/free Packages                         
Hit http://security.ubuntu.com karmic-security/main Packages                   
Ign http://it.archive.ubuntu.com karmic/multiverse Translation-en_US           
Get:12 http://archive.canonical.com karmic/partner Packages [4,184B]           
Ign http://www.mendeley.com  Release                                           
Hit http://packages.medibuntu.org jaunty/non-free Packages                     
Hit http://download.virtualbox.org karmic Release                              
Hit http://security.ubuntu.com karmic-security/restricted Packages             
Hit http://ppa.launchpad.net karmic Release                                    
Hit http://security.ubuntu.com karmic-security/main Sources                    
Hit http://security.ubuntu.com karmic-security/restricted Sources              
Hit http://security.ubuntu.com karmic-security/universe Packages               
Get:13 http://it.archive.ubuntu.com karmic-updates Release.gpg [189B]          
Get:14 http://archive.canonical.com karmic/partner Sources [1,725B]            
Hit http://ppa.launchpad.net karmic/main Packages                              
Hit http://ppa.launchpad.net karmic/main Packages                              
Hit http://ppa.launchpad.net karmic/main Sources                               
Hit http://security.ubuntu.com karmic-security/universe Sources                
Hit http://security.ubuntu.com karmic-security/multiverse Packages             
Hit http://security.ubuntu.com karmic-security/multiverse Sources              
Ign http://it.archive.ubuntu.com karmic-updates/main Translation-en_US         
Ign http://www.mendeley.com  Packages                                          
Get:15 http://ppa.launchpad.net karmic/main Packages [1,017B]                  
Ign http://it.archive.ubuntu.com karmic-updates/restricted Translation-en_US   
Hit http://ppa.launchpad.net karmic/main Packages                              
Hit http://download.virtualbox.org karmic/non-free Packages                    
Ign http://it.archive.ubuntu.com karmic-updates/universe Translation-en_US     
Ign http://www.mendeley.com  Packages                                          
Ign http://it.archive.ubuntu.com karmic-updates/multiverse Translation-en_US   
Hit http://it.archive.ubuntu.com karmic Release                                
Hit http://www.mendeley.com  Packages                                          
Get:16 http://it.archive.ubuntu.com karmic-updates Release [44.1kB]            
Hit http://it.archive.ubuntu.com karmic/main Packages                          
Hit http://it.archive.ubuntu.com karmic/restricted Packages
Hit http://it.archive.ubuntu.com karmic/main Sources      
Hit http://it.archive.ubuntu.com karmic/restricted Sources
Hit http://it.archive.ubuntu.com karmic/universe Packages 
Hit http://it.archive.ubuntu.com karmic/universe Sources  
Hit http://it.archive.ubuntu.com karmic/multiverse Packages
Hit http://it.archive.ubuntu.com karmic/multiverse Sources
Get:17 http://it.archive.ubuntu.com karmic-updates/main Packages [186kB]
Get:18 http://it.archive.ubuntu.com karmic-updates/restricted Packages [14B]   
Get:19 http://it.archive.ubuntu.com karmic-updates/main Sources [54.7kB]       
Get:20 http://it.archive.ubuntu.com karmic-updates/restricted Sources [14B]    
Get:21 http://it.archive.ubuntu.com karmic-updates/universe Packages [109kB]
Get:22 http://it.archive.ubuntu.com karmic-updates/universe Sources [26.9kB]   
Get:23 http://it.archive.ubuntu.com karmic-updates/multiverse Packages [7,369B]
Get:24 http://it.archive.ubuntu.com karmic-updates/multiverse Sources [4,025B] 
Fetched 519kB in 4s (120kB/s)                             
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C28F899060FD0E97
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 015A66E603E02400
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  mplayer
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
daitarn@daitarn-laptop:~$ **sudo apt-get install smplayer mplayer w32codecs**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
w32codecs is already the newest version.
The following extra packages will be installed:
  libggi-target-x libggi2 libgii1 libgii1-target-x libopencore-amrnb0
  libopencore-amrwb0 smplayer-themes
Suggested packages:
  libggi-target-emu libggi-target-monotext libggimisc2 mplayer-doc
The following packages will be REMOVED:
  mplayer-nogui
The following NEW packages will be installed:
  libggi-target-x libggi2 libgii1 libgii1-target-x libopencore-amrnb0
  libopencore-amrwb0 smplayer smplayer-themes
The following packages will be upgraded:
  mplayer
1 upgraded, 8 newly installed, 1 to remove and 0 not upgraded.
Need to get 10.0MB of archives.
After this operation, 18.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  mplayer
Install these packages without verification [y/N]? y
Get:1 http://it.archive.ubuntu.com karmic/universe libgii1 1:1.0.2-4 [289kB]
Get:2 http://ppa.launchpad.net karmic/main mplayer 2:1.0~rc3+svn20090904-0karmic5 [5,149kB]
Get:3 http://it.archive.ubuntu.com karmic/universe libggi2 1:2.2.2-3ubuntu1 [361kB]
Get:4 http://it.archive.ubuntu.com karmic/universe libopencore-amrnb0 0.1.2-1 [90.1kB]
Get:5 http://it.archive.ubuntu.com karmic/universe libopencore-amrwb0 0.1.2-1 [46.9kB]
Get:6 http://it.archive.ubuntu.com karmic/universe libgii1-target-x 1:1.0.2-4 [86.1kB]
Get:7 http://it.archive.ubuntu.com karmic/universe libggi-target-x 1:2.2.2-3ubuntu1 [163kB]
Get:8 http://ppa.launchpad.net karmic/main smplayer 0.6.9-1~karmic1 [1,627kB]                                                                               
Get:9 http://ppa.launchpad.net karmic/main smplayer-themes 0.1.20-1~karmic1 [2,238kB]                                                                       
Fetched 10.0MB in 21s (463kB/s)                                                                                                                             
Selecting previously deselected package libgii1.
(Reading database ... 232305 files and directories currently installed.)
Unpacking libgii1 (from .../libgii1_1%3a1.0.2-4_i386.deb) ...
Selecting previously deselected package libggi2.
Unpacking libggi2 (from .../libggi2_1%3a2.2.2-3ubuntu1_i386.deb) ...
Selecting previously deselected package libopencore-amrnb0.
Unpacking libopencore-amrnb0 (from .../libopencore-amrnb0_0.1.2-1_i386.deb) ...
Selecting previously deselected package libopencore-amrwb0.
Unpacking libopencore-amrwb0 (from .../libopencore-amrwb0_0.1.2-1_i386.deb) ...
Processing triggers for man-db ...
dpkg: mplayer-nogui: dependency problems, but removing anyway as you requested:
 mplayer depends on mplayer-nogui; however:
  Package mplayer-nogui is to be removed.
(Reading database ... 232575 files and directories currently installed.)
Removing mplayer-nogui ...
Processing triggers for man-db ...
(Reading database ... 232557 files and directories currently installed.)
Preparing to replace mplayer 2:1.0~rc3+svn20090426-1ubuntu10.1 (using .../mplayer_2%3a1.0~rc3+svn20090904-0karmic5_i386.deb) ...
Unpacking replacement mplayer ...
Selecting previously deselected package smplayer.
Unpacking smplayer (from .../smplayer_0.6.9-1~karmic1_i386.deb) ...
Selecting previously deselected package libgii1-target-x.
Unpacking libgii1-target-x (from .../libgii1-target-x_1%3a1.0.2-4_i386.deb) ...
Selecting previously deselected package libggi-target-x.
Unpacking libggi-target-x (from .../libggi-target-x_1%3a2.2.2-3ubuntu1_i386.deb) ...
Selecting previously deselected package smplayer-themes.
Unpacking smplayer-themes (from .../smplayer-themes_0.1.20-1~karmic1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Setting up libgii1 (1:1.0.2-4) ...

Setting up libggi2 (1:2.2.2-3ubuntu1) ...

Setting up libopencore-amrnb0 (0.1.2-1) ...

Setting up libopencore-amrwb0 (0.1.2-1) ...

Setting up mplayer (2:1.0~rc3+svn20090904-0karmic5) ...
Installing new version of config file /etc/mplayer/mplayer.conf ...
Installing new version of config file /etc/mplayer/menu.conf ...
Installing new version of config file /etc/mplayer/input.conf ...

Setting up smplayer (0.6.9-1~karmic1) ...

Setting up libgii1-target-x (1:1.0.2-4) ...
Setting up libggi-target-x (1:2.2.2-3ubuntu1) ...
Setting up smplayer-themes (0.1.20-1~karmic1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
daitarn@daitarn-laptop:~$ 

```[[IMG]http://img695.imageshack.us/img695/225/screenshotiwa.th.png[/IMG]]("http://img695.imageshack.us/i/screenshotiwa.png/")

---

### Post by andrew.46 on 2010-03-08
Hi motorhead_1,

Almost there :). I would suggest that you use *SMPlayer* to view your video and if the -vo error persists change the Video Out device in the SMPlayer preferences:

Options --> Preferences --> General --> Video --> Output Driver

to something like x11 for example. You could also run this file from the commandline as follows:

```
$ cd Desktop
$ mplayer -v scalping.wmv
```

and post the full terminal output here and this should give a clear idea of what is going on in terms of codecs used and video and audio out devices...

Andrew

---

### Post by motorhead_1 on 2010-03-08
I've run your commands and at the end the video started perfectly in MPlayer. strange, isn't ? don't know why I can't run it by right click and open with MPlayer...

```
daitarn@daitarn-laptop:~$ cd Desktop
daitarn@daitarn-laptop:~/Desktop$ mplayer -v scalping.wmv
MPlayer SVN-r29643-Ubuntu-RVM (C) 2000-2009 MPlayer Team
CPU vendor name: GenuineIntel  max cpuid level: 2
CPU: Intel(R) Pentium(R) M processor 1.73GHz (Family: 6, Model: 13, Stepping: 8)
extended cpuid-level: 8
extended cache-info: 134242368
Detected cache-line size is 64 bytes
Testing OS support for SSE... yes.
Tests of OS support for SSE passed.
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNowExt: 0 SSE: 1 SSE2: 1 SSSE3: 0
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/daitarn/.mplayer/codecs.conf'
Reading /home/daitarn/.mplayer/codecs.conf: Can't open '/home/daitarn/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
Configuration: --enable-runtime-cpudetection --target=i586-linux --prefix=/usr --confdir=/etc/mplayer --mandir=/usr/share/man --win32codecsdir=/usr/lib/win32 --disable-libdvdcss-internal --enable-xvmc --enable-menu --cc=gcc-4.3 --enable-gui --enable-mencoder
CommandLine: '-v' 'scalping.wmv'
init_freetype
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/daitarn/.mplayer/fonts'
Using nanosleep() timing
get_path('input.conf') -> '/home/daitarn/.mplayer/input.conf'
Can't open input config file /home/daitarn/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 90 binds
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
get_path('scalping.wmv.conf') -> '/home/daitarn/.mplayer/scalping.wmv.conf'

Playing scalping.wmv.
get_path('sub/') -> '/home/daitarn/.mplayer/sub/'
[file] File size is 10051693 bytes
STREAM: [file] scalping.wmv
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
LAVF_check: ASF format
Checking for YUV4MPEG2
ASF file format detected.
stream type: guid_video_stream
stream concealment: unknown guid 0057fb20-555b-cf11-a8fd00805f5c442b
type: 879 bytes,  stream: 0 bytes  ID: 1
unk1: 0  unk2: 12A4AC
FILEPOS=0x8F0
==> Found video stream: 1
[asfheader] Video stream found, -vid 1
======= VIDEO Format ======
  biSize 868
  biWidth 1476
  biHeight 900
  biPlanes 1
  biBitCount 24
  biCompression 844321613='MSS2'
  biSizeImage 0
Unknown extra header dump: [0] [0] [3] [3c] [0] [0] [0] [2] [0] [0] [0] [1] [0] [0] [5] [c4] [0] [0] [3] [84] [0] [0] [5] [c4] [0] [0] [3] [84] [41] [70] [0] [0] [0] [3] [d0] [90] [0] [0] [0] [0] [40] [40] [0] [0] [40] [40] [0] [1] [0] [0] [0] [9] [0] [0] [0] [0] [0] [0] [1] [0] [0] [0] [0] [0] [0] [40] [0] [0] [80] [0] [0] [c0] [0] [0] [ff] [0] [40] [0] [0] [40] [40] [0] [40] [80] [0] [40] [c0] [0] [40] [ff] [0] [80] [0] [0] [80] [40] [0] [80] [80] [0] [80] [c0] [0] [80] [ff] [0] [c0] [0] [0] [c0] [40] [0] [c0] [80] [0] [c0] [c0] [0] [c0] [ff] [0] [ff] [0] [0] [ff] [40] [0] [ff] [80] [0] [ff] [c0] [0] [ff] [ff] [40] [0] [0] [40] [0] [40] [40] [0] [80] [40] [0] [c0] [40] [0] [ff] [40] [40] [0] [40] [40] [40] [40] [40] [80] [40] [40] [c0] [40] [40] [ff] [40] [80] [0] [40] [80] [40] [40] [80] [80] [40] [80] [c0] [40] [80] [ff] [40] [c0] [0] [40] [c0] [40] [40] [c0] [80] [40] [c0] [c0] [40] [c0] [ff] [40] [ff] [0] [40] [ff] [40] [40] [ff] [80] [40] [ff] [c0] [40] [ff] [ff] [80] [0] [0] [80] [0] [40] [80] [0] [80] [80] [0] [c0] [80] [0] [ff] [80] [40] [0] [80] [40] [40] [80] [40] [80] [80] [40] [c0] [80] [40] [ff] [80] [80] [0] [80] [80] [40] [80] [80] [80] [80] [80] [c0] [80] [80] [ff] [80] [c0] [0] [80] [c0] [40] [80] [c0] [80] [80] [c0] [c0] [80] [c0] [ff] [80] [ff] [0] [80] [ff] [40] [80] [ff] [80] [80] [ff] [c0] [80] [ff] [ff] [c0] [0] [0] [c0] [0] [40] [c0] [0] [80] [c0] [0] [c0] [c0] [0] [ff] [c0] [40] [0] [c0] [40] [40] [c0] [40] [80] [c0] [40] [c0] [c0] [40] [ff] [c0] [80] [0] [c0] [80] [40] [c0] [80] [80] [c0] [80] [c0] [c0] [80] [ff] [c0] [c0] [0] [c0] [c0] [40] [c0] [c0] [80] [c0] [c0] [c0] [c0] [c0] [ff] [c0] [ff] [0] [c0] [ff] [40] [c0] [ff] [80] [c0] [ff] [c0] [c0] [ff] [ff] [ff] [0] [0] [ff] [0] [40] [ff] [0] [80] [ff] [0] [c0] [ff] [0] [ff] [ff] [40] [0] [ff] [40] [40] [ff] [40] [80] [ff] [40] [c0] [ff] [40] [ff] [ff] [80] [0] [ff] [80] [40] [ff] [80] [80] [ff] [80] [c0] [ff] [80] [ff] [ff] [c0] [0] [ff] [c0] [40] [ff] [c0] [80] [ff] [c0] [c0] [ff] [c0] [ff] [ff] [ff] [0] [ff] [ff] [40] [ff] [ff] [80] [ff] [ff] [c0] [ff] [ff] [ff] [0] [20] [0] [0] [20] [40] [0] [20] [80] [0] [60] [0] [0] [60] [40] [0] [60] [80] [20] [0] [0] [20] [0] [40] [20] [0] [80] [20] [20] [0] [20] [20] [40] [20] [20] [80] [20] [40] [0] [20] [40] [40] [20] [40] [80] [20] [60] [0] [20] [60] [40] [20] [60] [80] [20] [80] [40] [20] [80] [80] [40] [20] [0] [40] [20] [40] [40] [20] [80] [40] [60] [0] [40] [60] [40] [40] [60] [80] [40] [60] [c0] [40] [a0] [40] [40] [a0] [80] [40] [a0] [c0] [60] [0] [0] [60] [0] [40] [60] [20] [0] [60] [20] [40] [60] [20] [80] [60] [40] [0] [60] [40] [40] [60] [40] [80] [60] [40] [c0] [60] [60] [0] [60] [60] [40] [60] [60] [80] [60] [60] [c0] [60] [80] [0] [60] [80] [40] [60] [80] [80] [60] [80] [c0] [60] [a0] [40] [60] [a0] [80] [60] [a0] [c0] [60] [c0] [80] [60] [c0] [c0] [80] [20] [0] [80] [20] [40] [80] [20] [80] [80] [60] [0] [80] [60] [40] [80] [60] [80] [80] [60] [c0] [80] [a0] [40] [80] [a0] [80] [80] [a0] [c0] [80] [a0] [ff] [80] [e0] [80] [80] [e0] [c0] [80] [e0] [ff] [a0] [40] [40] [a0] [40] [80] [a0] [60] [40] [a0] [60] [80] [a0] [60] [c0] [a0] [80] [40] [a0] [80] [80] [a0] [80] [c0] [a0] [80] [ff] [a0] [a0] [40] [a0] [a0] [80] [a0] [a0] [c0] [a0] [a0] [ff] [a0] [c0] [40] [a0] [c0] [80] [a0] [c0] [c0] [a0] [c0] [ff] [a0] [e0] [80] [a0] [e0] [c0] [a0] [e0] [ff] [a0] [ff] [c0] [a0] [ff] [ff] [c0] [60] [40] [c0] [60] [80] [c0] [60] [c0] [c0] [a0] [40] [c0] [a0] [80] [c0] [a0] [c0] [c0] [a0] [ff] [c0] [e0] [80] [c0] [e0] [c0] [c0] [e0] [ff] [e0] [80] [80] [e0] [80] [c0] [e0] [a0] [80] [e0] [a0] [c0] [e0] [a0] [ff] [e0] [c0] [80] [e0] [c0] [c0] [e0] [c0] [ff] [e0] [e0] [80] [e0] [e0] [c0] [e0] [e0] [ff] [e0] [ff] [80] [e0] [ff] [c0] [e0] [ff] [ff] [ff] [a0] [80] [ff] [a0] [c0] [ff] [a0] [ff] [ff] [e0] [80] [ff] [e0] [c0] [ff] [e0] [ff] [20] [20] [20] [60] [60] [60] [a0] [a0] [a0] [e0] [e0] [e0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] 
===========================
ASF: packets: 6953  flags: 2  max_packet_size: 1444  min_packet_size: 1444  max_bitrate: 260068  preroll: 3000
============ ASF Stream group == START ===
 stream count=[0x1][1]
   stream id=[0x1][1]
   max bitrate=[0x3f7e4][260068]
============ ASF Stream group == END ===
Found movie at 0xCB1 - 0x993FF5
ASF: 0 audio and 1 video streams found
Auto-selected ASF video ID = 1
VIDEO:  [MSS2]  1476x900  24bpp  1000.000 fps  250.0 kbps (30.5 kbyte/s)
[V] filefmt:6  fourcc:0x3253534D  size:1476x900  fps:1000.000  ftime:=0.0010
get_path('sub/') -> '/home/daitarn/.mplayer/sub/'
X11 opening display: :0.0
vo: X11 color mask:  FFFFFF  (R:FF0000 G:FF00 B:FF)
vo: X11 running at 1280x800 with depth 24 and 32 bpp (":0.0" => local display)
[x11] Detected wm supports NetWM.
[x11] Detected wm supports FULLSCREEN state.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Current fstype setting honours FULLSCREEN ABOVE BELOW X atoms
[VO_XV] Using Xv Adapter #0 (Intel(R) Textured Video)
[xv common] Drawing no colorkey.
[xv common] Maximum source image dimensions: 2048x2048
==========================================================================
Opening video decoder: [dmo] DMO video codecs
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
Decoder supports the following formats: RGB8 RGB555 RGB565 RGB24 RGB32 
VDec: vo config request - 1476 x 900 (preferred colorspace: Packed YUY2)
Trying filter chain: vo
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
SwScale params: -1 x -1 (-1=no scaling)
Trying filter chain: scale vo
VDec: using BGRA as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO Config (1476x900->1476x900,flags=0,'MPlayer',0x42475220)
[swscaler @ 0xa507ce0]BICUBIC scaler, from rgb32 to yuv420p using MMX2
REQ: flags=0x437  req=0x0  
VO: [xv] 1476x900 => 1476x900 Planar YV12 
VO: Description: X11/Xv
VO: Author: Gerd Knorr <kraxel@goldbach.in-berlin.de> and others
Xvideo image format: 0x32595559 (YUY2) packed
Xvideo image format: 0x32315659 (YV12) planar
Xvideo image format: 0x30323449 (I420) planar
Xvideo image format: 0x59565955 (UYVY) packed
Xvideo image format: 0x434d5658 (XVMC) planar
using Xvideo port 80 for hw scaling
INFO: Win32/DMO video codec init OK.
Selected video codec: [wmsdmod] vfm: dmo (Windows Media Screen Codec 2)
==========================================================================
Audio: no sound
Freeing 0 unused audio chunks.
Starting playback...

avg. framerate: 15 fps             
*** [scale] Allocating mp_image_t, 1476x900x32bpp BGR packed, 5313600 bytes
*** [vo] Allocating mp_image_t, 1488x900x12bpp YUV planar, 2008800 bytes
Unicode font: 5025 glyphs.
Unicode font: 5025 glyphs.
Uninit video: dmo44% 51%  0.0% 0 0 
vo: uninit ...

Exiting... (Quit)
daitarn@daitarn-laptop:~/Desktop$ 

```

---

### Post by andrew.46 on 2010-03-08
Hi motorhead,

> **motorhead_1 said:**
> I've run your commands and at the end the video started perfectly in MPlayer. strange, isn't ? don't know why I can't run it by right click and open with MPlayer...

Great news :). Have you opened the file with SMPlayer and then adjusted the Video Out device in the preferences? This should hopefully complete the circle and give you access to a modern MPlayer and a great gui for it as well...

Andrew

---

### Post by motorhead_1 on 2010-03-09
Hi! 
I'm actually stuck in compiling SMPlayer. from the .txt file:

```
1) How to make a deb package 
---------------------------- 
Be sure you have installed the following packages: libqt4-dev, zlib1g-dev, 
fakeroot, build-essential, devscripts, debhelper and g++. 
```Done

```
Now run ./create_deb.sh 
 
```daitarn@daitarn-laptop:~$ /home/daitarn/smplayer-0.6.9/create_deb.sh
cp: cannot stat `debian-rvm/changelog-orig': No such file or directory
/home/daitarn/smplayer-0.6.9/create_deb.sh: 6: ./get_svn_revision.sh: not found
rm: cannot remove `build-stamp': No such file or directory
rm: cannot remove `src/smplayer': No such file or directory
/usr/bin/fakeroot: line 176: debian/rules: No such file or directory
/usr/bin/fakeroot: line 176: debian/rules: No such file or directory
dh_clean: cannot read debian/control: No such file or directory

rm: cannot remove `debian-rvm/changelog': No such file or directory


what's wrong? I'm quite a newbie in these kind of things :redface:

```

2) How to make a rpm package 
---------------------------- 
Run rpmbuild -tb smplayer-0.6.x.tar.bz2 
You'll find the rpm pachage under /usr/src/packages/RPMS/i586/ 
 
Take a look at this document to know how to create a rpm from the SVN sources: 
http://smplayer.berlios.de/forums/viewtopic.php?id=188 
 
 
3) Generic compilation 
---------------------- 
You need at least Qt 4.3 to compile smplayer. It won't work with an older 
version. 
 
Be sure you have installed the Qt 4 development package. Its name maybe 
qt4-devel, libqt4-dev or similar.  
 
Uncompress the source code, open a console and enter in the  
smplayer-0.6.x directory. 
 
Type "make".  
 
If everything is ok now you can install it with "make install". 
That will install smplayer in /usr/local. 
 
If "make" fails, it's probably because the Qt 3 qmake has been used instead of 
the Qt 4 one. It seems that some distros have renamed that tool to qmake-qt4.  
Others may have installed in another directory. 
Look at the contents of the qt4-devel package (or whatever its name is) and 
find out where it is. 
 
Now type something like this (just examples): 
make QMAKE=qmake-qt4 
or 
make QMAKE=/usr/share/qt4/bin/qmake 
 
 
4) Changing installation path 
----------------------------- 
By default smplayer will be installed in /usr/local. You can change it by 
using PREFIX and DESTDIR. 
 
Examples: 
make PREFIX=/usr 
make PREFIX=/usr install 
 
That would install smplayer under /usr. 
 
DESTDIR will be useful for package maintainers. 
 
make PREFIX=/usr 
make PREFIX=/usr DESTDIR=/tmp/ install 
 
That would compile smplayer for /usr but in fact it will be installed in 
/tmp/usr/ 
```

---

### Post by mc4man on 2010-03-09
If you added the ppa then just install smplayer as suggested - sudo apt-get install smplayer

Rvm's 'create_deb.sh's' are actually very interesting little scripts and do work well, though I'm not sure of any advantage for the smplayer one.
(used to use the mplayer one, with a few changes to the rules file worked quite well, though haven't used in many months

If you wish to use or try this method for smplayer then **you are at the wrong terminal prompt. **

Simply download the smplayer source (smplayer-0.6.9.tar.bz) extract it and then in a terminal cd to the extracted source (smplayer-0.6.9

Then run the command and all should be well

Ex.of prompt
> doug@doug-laptop:~/Downloads/smplayer-0.6.9$ ./create_deb.sh

---

### Post by motorhead_1 on 2010-03-09
I've followed the first and easiest way sudo apt-get install smplayer and I'm now watching the video with SMPlayer :D

---

### Post by andrew.46 on 2010-03-09
Hi motorhead,

> **motorhead_1 said:**
> I've followed the first and easiest way sudo apt-get install smplayer and I'm now watching the video with SMPlayer :D

I am glad that you have had the patience to pursue this matter, the result should be very worthwhile :).

Andrew

---

### Post by motorhead_1 on 2010-03-09
thanks again! :D

---

### Post by lykeion on 2010-03-16
Hi
I still use Jaunty and have been following this guide successfully a couple of times earlier. 
Thanks Andrew for this great guide :-)

But when I tried it today (using latest mplayer from svn, rev 30913) I got a error compiling mplayer, 
and since I'm no compilation guru I turn to this thread for some help on why I can't compile.
 
Here's some info
OS: Ubuntu 9.04 Jaunty
Graphics driver: nvidia-glx-195.36-15
...
(I can provide more info if needed)

Attached is a text file of last 100 or so lines of the compile output 
(where it starts to complain about undefined references for libavcodec.a (I think), and finally ends with an exit 1)

Thankful for any help...

PS I've tried to disable x264 and also disable mencoder altogether but to no success.

---

### Post by andrew.46 on 2010-03-16
Hi lykeon,

> **lykeion said:**
> I still use Jaunty and have been following this guide successfully a couple of times earlier. 
Thanks Andrew for this great guide :-)

It is my pleasure :). I will admit that I have been working with MPlayer and Ubuntu for a little too long now and I seem to have little else to contribute in this field but it is nice to have made a contribution...

> But when I tried it today (using latest mplayer from svn, rev 30913) I got a error compiling mplayer

I get the same error and have for a day or so I suspect the best bet is to wait another day or so. If the situation is not rectified perhaps a trip to #mplayer might be worthwhile but usually the fault is rectified quickly...

All the best,

Andrew

---

### Post by andrew.46 on 2010-03-17
Hi lykeion,

Compilation succeeds again:

```

andrew@skamandros~/source/mplayer$ mplayer | head -n 1
MPlayer SVN-r30916-4.3.3 (C) 2000-2010 MPlayer Team

```

Andrew

---

### Post by Nisal on 2010-03-17
thanks usefull in4 :)

---

### Post by lykeion on 2010-03-18
> **andrew.46 said:**
> Hi lykeion,

Compilation succeeds again

...

Andrew

Yes, now it works for me too :-)

Thanks Andrew for the quick response.

---

### Post by motorhead_1 on 2010-04-06
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net]("http://ppa.launchpad.net/") karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C28F899060FD0E97
W: GPG error: [http://ppa.launchpad.net]("http://ppa.launchpad.net/") karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 015A66E603E02400

Doeas anyone know what are the keys to be added for those repositories?

---

### Post by LONDES on 2010-06-01
How do I fix this?
```
~/mplayer$ sudo checkinstall -D --install=yes --fstrans=no --pakdir "$HOME/Desktop" --pkgname mplayer --backup=no --deldoc=yes --deldesc=yes --delspec=yes --default --pkgversion "3:1.0~svn-`grep "#define VERSION" version.h | cut -d"-" -f2`"

[CENTER]-snipped-[/CENTER]
========================= Installation results ===========================
cc -MD -MP -Wstrict-prototypes -Wmissing-prototypes -Wundef -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -std=gnu99 -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -Ilibdvdread4 -I.  -D_REENTRANT -I/usr/include/directfb -I/usr/include/     -D_REENTRANT    -I/usr/include/freetype2    -c -o libmpcodecs/vf_geq.o libmpcodecs/vf_geq.c
libmpcodecs/vf_geq.c: In function 'vf_open':
libmpcodecs/vf_geq.c:175: warning: initialization from incompatible pointer type
libmpcodecs/vf_geq.c:176: warning: initialization from incompatible pointer type
libmpcodecs/vf_geq.c:177: warning: initialization from incompatible pointer type
libmpcodecs/vf_geq.c:178: warning: initialization from incompatible pointer type
libmpcodecs/vf_geq.c:181: warning: passing argument 1 of 'ff_parse_expr' from incompatible pointer type
libmpcodecs/vf_geq.c:181: warning: passing argument 2 of 'ff_parse_expr' from incompatible pointer type
libmpcodecs/vf_geq.c:181: warning: passing argument 5 of 'ff_parse_expr' from incompatible pointer type
libmpcodecs/vf_geq.c:181: warning: passing argument 6 of 'ff_parse_expr' from incompatible pointer type
libmpcodecs/vf_geq.c:181: warning: passing argument 8 of 'ff_parse_expr' makes integer from pointer without a cast
libmpcodecs/vf_geq.c:181: error: too few arguments to function 'ff_parse_expr'
make: *** [libmpcodecs/vf_geq.o] Error 1

****  Installation failed. Aborting package creation.
```

---

### Post by cry8wolf9 on 2010-11-09
im having a problem installing the **libopencore-amr  **i keep getting this

```

(Reading database ... 250987 files and directories currently installed.)
Unpacking libopencore-amr (from .../libopencore-amr_0.1.2-1_i386.deb) ...
dpkg: error processing /home/kyle/opencore-amr-0.1.2/libopencore-amr_0.1.2-1_i386.deb (--install):
 trying to overwrite '/usr/lib/libopencore-amrwb.so.0.0.2', which is also in package libopencore-amrwb0 0.1.2-1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/kyle/opencore-amr-0.1.2/libopencore-amr_0.1.2-1_i386.deb
/var/tmp/tmp.2I9AJ7bNPI/dpkginstall.log (END) 


```

---

### Post by mc4man on 2010-11-09
> installing the libopencore-amr i keep getting this
libopencore-amr is already installed (note this how-to is for jaunty

either remove what's installed (search libopencore in synaptic), or don't bother with w/ compiling, installing the opencore libs

In that case just  search libopencore and install the -dev package.

If you're using lucid you may find this more appropriate - (it's based on maverick but should still  be okay for lucid

[http://ubuntuforums.org/showthread.php?t=1542240](http://ubuntuforums.org/showthread.php?t=1542240)

Start w/ the build-deps again, if somethings not found then it may just be a slight name change, so note it, remove from command and run the build-deps again.

---

### Post by cry8wolf9 on 2010-11-09
i am actually using Maverick Meerkat now i dont see libopencore-amr unless libopencore-amrnb-dev or libopencore-amrwb-dev is the same thing?

---

### Post by mc4man on 2010-11-09
> i am actually using Maverick Meerkat 
Well then just follow the other how-to in above link, should work out fine. Pick up at the 2nd code box( installing build-deps)
If you look closely at the command you'll see this in it
> libopencore-amrnb-dev libopencore-amrwb-dev 

---

