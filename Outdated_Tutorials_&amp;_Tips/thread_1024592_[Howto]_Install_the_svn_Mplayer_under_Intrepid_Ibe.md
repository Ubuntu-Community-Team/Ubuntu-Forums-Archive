---
title: "[Howto] Install the svn Mplayer under Intrepid Ibex"
date: 2008-12-29
forum: Outdated Tutorials &amp; Tips
---

### Post by andrew.46 on 2008-12-29
======================
**Introduction**
=====================

This guide intends to show how to successfully compile the subversion MPlayer under Intrepid Ibex with a full codec pack. It is intended for use by *advanced users* only. If this advanced guide is really not what you are after perhaps you could try the very popular: [Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683") where Nathan will look after you :-)

========================
**Some Preparation**
========================

For this guide to succeed you must ensure that you have *all* of the major Ubuntu Repositories enabled, details of enabling the Universe, Multiverse and Restricted Repositories can be found [here]("https://help.ubuntu.com/community/Repositories/Ubuntu").

Compiling, subversion and installation tools are first required and these can be downloaded from the Repositories as follows:

```
$ sudo apt-get install build-essential checkinstall subversion git-core yasm
```

Next to install the codecs:

======================
**Set up the Codecs**
======================

The codecs are the heart and soul of Mplayer and we will be downloading the 'full' pack, decompressing it and placing it in the appropriate location:

```
$ cd $HOME
$ wget ftp://ftp.mplayerhq.hu/MPlayer/releases/codecs/all-20071007.tar.bz2
$ sudo mkdir -pv /usr/local/lib/codecs
$ tar xjvf all-20071007.tar.bz2
$ sudo cp -v $HOME/all-20071007/* /usr/local/lib/codecs
```

I should mention at this time that it is this codec pack that has caused a bit of discussion concerning copyright, only use it if the laws in your country allow it. But now to source a font for Mplayer:

=============================
**Source a Font**
=============================

Mplayer needs to know the location of a TrueType Font to show movie subtitles. This can be selected from the commandline but more traditionally a symlink is created to the font of your choice:

```
$ sudo apt-get install ttf-bitstream-vera
$ mkdir -v ~/.mplayer
$ ln -sv /usr/share/fonts/truetype/ttf-bitstream-vera/Vera.ttf ~/.mplayer/subfont.ttf
```

Feel free to choose your own font but this will certainly do to start with. I suspect this font is part of a default Ubuntu installation but I include directions for its installation anyway, just to be sure!

====================================
**Install the x264 Libraries**
====================================

The version of x264 in the Ubuntu Repository is too old for MPlayer so we will need to download a copy from the x264 git repository:

```
$ cd $HOME
$ git clone git://git.videolan.org/x264.git
$ cd x264
$ ./configure --enable-shared
$ make
$ sudo checkinstall --fstrans=no --install=yes --pakdir "$HOME/Desktop" \
--maintainer "$USER" --pkgname=x264 --pkgversion "1:0.svn`date +%Y%m%d`-0.0ubuntu1" \
--backup=no --deldoc=yes --deldesc=yes --delspec=yes --gzman --default
$ make clean
```

And now to install the Live555 libraries.

====================================
**Install the Live555 Libraries**
====================================

The version of the Live555 libraries in Ubuntu (liblivemedia-dev) seems to have trouble with some of the streaming broadcasts that I routinely listen to so I always compile MPlayer against the latest upstream libraries:

```
$ cd $HOME
$ wget http://www.live555.com/liveMedia/public/live555-latest.tar.gz
$ tar xvf live555-latest.tar.gz
$ cd live
$ ./genMakefiles linux
$ make
$ sudo cp -r $HOME/live /usr/lib
```

It is a fairly primitive installation regime but it enables me to listen to my favourite broadcasts and so I think it will make your version of MPlayer a little better as well. 

And now to install the libopencore-amr libraries:


====================================
**Install the libopencore-amr Libraries**
====================================

These libraries enable amr playback for MPlayer:

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

Now for all the Development files:

====================================
**Download the 'Development' Files**
====================================

By default Ubuntu does not offer a particularly rich development environment so we need to download the required 'dev' files which are specific to Intrepid Ibex. (These files are loosely modelled on the results of the command 'sudo apt-get build-dep mplayer-nogui', I have removed some files and added others.):

```
$ sudo apt-get install em8300-headers gawk gettext html2text intltool-debian \
ladspa-sdk libaa1-dev libartsc0 libartsc0-dev libasound2-dev libatk1.0-dev libaudio-dev \
libaudio2 libaudiofile-dev libavahi-client-dev libavahi-common-dev libcaca-dev \
libcairo2-dev libcdparanoia0-dev libcucul-dev libdbus-1-dev libdbus-glib-1-dev \
libdirectfb-dev libdirectfb-extra libdts-dev libdv4-dev libenca-dev libenca0 \
libesd0-dev libexpat1-dev libfaac-dev libfaac0 libfontconfig1-dev libfreebob0 \
libfreetype6-dev libfribidi-dev libggi-target-x libggi2 libggi2-dev libggimisc2 \
libggimisc2-dev libgif-dev libgii1 libgii1-dev libgii1-target-x libgl1-mesa-dev \
libglu1-mesa-dev libglu1-xorg-dev libgtk2.0-dev libice-dev libschroedinger-dev \
libjack-dev libjack0 libjpeg62-dev liblzo-dev liblzo1 liblzo2-2 liblzo2-dev libmad0 \
libmad0-dev libmail-sendmail-perl libmp3lame-dev libmp3lame0 libmpcdec-dev libmpcdec3 \
libncurses5-dev libogg-dev libopenal-dev libopenal1 libpango1.0-dev libpixman-1-dev \
libpng12-dev libpopt-dev libpthread-stubs0 libpthread-stubs0-dev libpulse-dev \
libpulse-mainloop-glib0 libsdl1.2-dev libslang2-dev libsm-dev libsmbclient-dev \
libspeex-dev libsvga1 libsvga1-dev libsys-hostname-long-perl libsysfs-dev \
libtheora-dev libtwolame-dev libtwolame0 libvorbis-dev libx11-dev libxau-dev \
libxcb-render-util0-dev libxcb-render0-dev libxcb-xlib0-dev libxcb1-dev \
libxcomposite-dev libxcursor-dev libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev \
libxft-dev libxi-dev libxinerama-dev libxrandr-dev libxrender-dev libxt-dev libxv-dev \
libxvidcore4 libxvidcore4-dev libxvmc-dev libxvmc1 libxxf86dga-dev libxxf86vm-dev \
mesa-common-dev po-debconf sharutils x11proto-composite-dev x11proto-core-dev \
x11proto-damage-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev \
x11proto-randr-dev x11proto-render-dev x11proto-video-dev x11proto-xext-dev \
x11proto-xf86dga-dev x11proto-xf86vidmode-dev x11proto-xinerama-dev \
xtrans-dev zlib1g-dev libstdc++5 
```

This will download about 35 megs of archives from the Ubuntu and Medibuntu Repositories and will give our copy of MPlayer a huge amount of functionality. Feel free to add your own dev files to customise MPlayer to your own taste! Now to download the svn Mplayer itself:

=================================
**Download and Compile the svn mplayer**
=================================

Finally after all of the preparation it is time to download Mplayer from the subversion repository, compile it and use checkinstall to create a package and install it:

```
$ cd $HOME
$ svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer
$ cd $HOME/mplayer
$ ./configure
$ make
$ sudo checkinstall -D --install=yes --fstrans=no --pakdir "$HOME/Desktop" \
--pkgname mplayer --backup=no --deldoc=yes --deldesc=yes --delspec=yes --default \
--pkgversion "3:1.0~svn-`grep "#define VERSION" version.h | cut -d"-" -f2`"
$ make distclean
```

And there you have the cutting edge MPlayer! Return here from time to time to update your copy by using the command 'svn update' and then compiling as before. But this is of course only the commandline version, next to download the best graphical front-end for MPlayer available today:

=========================================
**Downloading SMPlayer**
=========================================

The default gui for MPlayer is known as gmplayer and it has been out of development for some time. I personally use the amazing SMPLayer in its place and I would advise that you do the same. To download from the Ubuntu Repositories simply:

```
$ sudo apt-get install smplayer 
```

Some qt dependencies are brought in with SMPlayer for a total download of about 14 megs but trust me, it is well worthwhile! If you have any trouble with SMPlayer you will find that the developer is quite active on these forums and keen to help with his product. The developer also maintains a Personal Package Archive (PPA) with a newer version of the SMPlayer, details of how to access this can be seen [here]("http://smplayer.sourceforge.net/downloads.php?tr_lang=en").

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
March 28th, 2009

---

### Post by abhilashm86 on 2008-12-29
hi andrew,i just love terminal apps,now just running moc,i had initially installed mplayer but was not much working in terminal,i removed it through 
sudo apt-get purge-- mplayer

then i started following your guide,so i ended up with this error,i din't get how to remove locks,
svn cleanup din't work for me......

abhilash@abhi:~$ svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer
svn: Working copy 'mplayer' locked
svn: run 'svn cleanup' to remove locks (type 'svn help cleanup' for details)

so the next step config file,i've been stuck,so where i need to correct the error?

---

### Post by abhilashm86 on 2008-12-29
hey now i completely removed mplayer and mencoder,is this package correct?
*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ abhilash ]
1 -  Summary: [ Package created with checkinstall 1.6.1 ]
2 -  Name:    [ mplayer ]
3 -  Version: [ 3:1.0~svn ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ mplayer ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
make: *** No rule to make target `install'.  Stop.

****  Installation failed. Aborting package creation.
why this aborting package creation?

abhilash@abhi:/$ mplayer p /media/MUSIC/Western Classical/Richard Clayderman Piano/Tango
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) D  CPU 2.66GHz (Family: 15, Model: 4, Stepping: 7)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket


i think m messed up things while removing older mplayer,if u can tell where original files and config files are present,i can remove those and proceed coz many files din't download and terminal was telling files exist!!!!!!!
will do after your reply.

---

### Post by andrew.46 on 2008-12-29
Hi abhilashm86,

Good to hear from you again :-),

> **abhilashm86 said:**
> hey now i completely removed mplayer and mencoder,is this package correct?[...]

========================= Installation results ===========================
make: *** No rule to make target `install'.  Stop.

****  Installation failed. Aborting package creation.
why this aborting package creation?

I suspect that your svn MPLayer files may not be complete, as your previous message suggested when svn was complaining of locked files:

> andrew@skamandros:~$ svn help cleanup
cleanup: Recursively clean up the working copy, removing locks, resuming
unfinished operations, etc.


You can issue this command (svn cleanup) from $HOME/mplayer or simply delete this directory and run the original MPlayer svn command which might be the easier option. Make sure you are runnig this as an unpriviledged user, I remember this was a problem with your mutt setup :-).

> abhilash@abhi:/$ mplayer p /media/MUSIC/Western Classical/Richard Clayderman Piano/Tango
**[COLOR="Red"]MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team[/COLOR]**
[...]
i think m messed up things while removing older mplayer,

It looks like your original repository MPlayer is still there :-). You might be best to delete this by searching for it in the synaptic package manager.

> if u can tell where original files and config files are present,i can remove those and proceed coz many files din't download and terminal was telling files exist!!!!!!!

This new version of the MPlayer guide is more closely integrated with the package management system of Ubuntu and you must have the Universe, Multiverse and Medibuntu repositories enabled for it to succeed. You will find links to the Ubuntu Community documentation describing how to do this in the first paragraph or so of the guide.

Don't worry too much if you already have some of the files. I deliberately reloaded Intrepid Ibex and installed MPlayer on a clean system so I would catch all dependencies. Some will have already been installed by many users or other purposes.

All the very best with this,

Andrew

---

### Post by piemaster89 on 2008-12-30
I noticed you have libglide2 in this new guide for 8.10. Is this intentional? It was previously removed since it's no longer included in the repository, right?

---

### Post by abhilashm86 on 2008-12-30
hey andrew thanks one more,i had deleted from package managers,but some hidden files were problem which i searched and removed.

i did install completely and player is working fine,but can u tell how to install additional formats of video playing options like 
Untraceable.2008.DVDRip.x264.Adz-300MB.mkv

this player din't recognise.

============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.


one more,do have any idea about using DOSBOX emulator,using it and mounting is hard........

---

### Post by mocha on 2008-12-30
Thanks for maintaining this guide.  Can I suggest that you point users to the updated PPA repository for smplayer given [here]("http://smplayer.sourceforge.net/downloads.php?tr_lang=en").  The version in Intrepid is at 0.6.1 while the latest version is 0.6.5.

Also, can you give any examples of where the live555 libs in Ubuntu give you problems with streams?  What are the symptoms of this issue?  I listen to a lot of streams as well.

---

### Post by andrew.46 on 2008-12-30
Hi piemaster,

> **piemaster89 said:**
> I noticed you have libglide2 in this new guide for 8.10. Is this intentional? It was previously removed since it's no longer included in the repository, right?

I was hoping to slip that one in quietly :-). I had a close look on a fresh install of Intrepid Ibex and I have to say that this library is in the Intrepid Ibex Universe Repository:

[http://packages.ubuntu.com/intrepid/libglide2](http://packages.ubuntu.com/intrepid/libglide2)

```
andrew@skamandros:~$ apt-cache search libglide2 | grep library
libglide2 - graphics library for 3Dfx Voodoo based cards - shared libraries
libglide2-dev - graphics library for 3Dfx Voodoo based cards - development files

```

Do you have the Universe Repositories enabled?

Andrew

---

### Post by andrew.46 on 2008-12-30
Hi abhilashm86,

> **abhilashm86 said:**
> i did install completely and player is working fine,but can u tell how to install additional formats of video playing options like 
Untraceable.2008.DVDRip.x264.Adz-300MB.mkv

this player din't recognise.

============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.

An mkv file is a matroska container usually with a variety of audio, video and subtitle elements inside. It is a little unusual that MPlayer cannot play this but it depends on what is inside the container.

MPlayer can identify elements in a file with the following synyax:

```
$ mplayer -identify -frames 0 **[COLOR="Red"]<filename>[/COLOR]**
```

ffmpeg does a better job by using:

```
$ ffmpeg -i  **[COLOR="Red"]<filename>[/COLOR]**
```

If you can post the results of either of these there should be an answer as to why MPlayer chokes on the file.

> one more,do have any idea about using DOSBOX emulator,using it and mounting is hard........

I am afraid that I have absolutely no idea about this one .... sorry!

All the best,

  Andrew

---

### Post by andrew.46 on 2008-12-30
Hi mocha:

> **mocha said:**
> Thanks for maintaining this guide.  Can I suggest that you point users to the updated PPA repository for smplayer given [here]("http://smplayer.sourceforge.net/downloads.php?tr_lang=en").  The version in Intrepid is at 0.6.1 while the latest version is 0.6.5.

There are really 2 reasons why I have deliberately chosen to use the repository version of the wonderful smplayer. Firstly I am trying to bring the guide closer to 'mainstream' ubuntu with admittedly mixed success, but for this reason I am sticking with a straight repository download not a PPA. I acknowledge of course that this is the PPA of the developer of smplayer and unlikely to be a problem. Secondly I do not know smplayer all that closely and I am not really qualified to field questions relating to either use of a PPA or even newer versions of smplayer. I will however add a note about this archive to the guide for those bolder than myself :-).

> Also, can you give any examples of where the live555 libs in Ubuntu give you problems with streams?  What are the symptoms of this issue?  I listen to a lot of streams as well.

I have found some connection issues with connections to some live streams from the ABC ClassicFM website in Australia. Once connected there was no problem but I saw improvements with compiling my own libraries and compiling MPlayer against these: connecting well almost all of the time.

The version I give in the guide is a little newer than the Intrepid version now:

[https://launchpad.net/ubuntu/intrepid/+source/liblivemedia/2008.07.25-2](https://launchpad.net/ubuntu/intrepid/+source/liblivemedia/2008.07.25-2)

so may be worth a try anyway?

All the best,

Andrew

---

### Post by mocha on 2008-12-30
> **andrew.46 said:**
> I have found some connection issues with connections to some live streams from the ABC ClassicFM website in Australia. Once connected there was no problem but I saw improvements with compiling my own libraries and compiling MPlayer against these: connecting well almost all of the time.

Interesting.  Is your problem that the RTSP stream will try to connect and then not connect unless you attempt it several times?  I occasionally see this problem when mplayer plugin trys to open an embedded RTSP stream in Firefox, but I always assumed the problem was with the stream itself.

Can I install updated live555 libs independantly without recompiling mplayer?  Will they still get used?  or do they have to be installed prior to compiling?

---

### Post by andrew.46 on 2008-12-30
Hi mocha,

> **mocha said:**
> Interesting.  Is your problem that the RTSP stream will try to connect and then not connect unless you attempt it several times?  I occasionally see this problem when mplayer plugin trys to open an embedded RTSP stream in Firefox, but I always assumed the problem was with the stream itself.

Yes this is the problem, but I have not used the MPlayer plugin so I am not sure about this one.

> Can I install updated live555 libs independantly without recompiling mplayer?  Will they still get used?  or do they have to be installed prior to compiling?

They will need to be installed prior to compiling MPlayer and should be picked up by the configure process:

```
Checking for LIVE555 Streaming Media libraries ... yes (using /usr/lib/live)
```

Details of MPlayer and Live555 can be seen [here]("http://www.live555.com/mplayer/"). You will note on this page that the current advice is to use VLC :-).

Andrew

---

### Post by mocha on 2008-12-30
> **andrew.46 said:**
> Yes this is the problem, but I have not used the MPlayer plugin so I am not sure about this one.

What do you mean?  I thought that the mplayer plugin was using the mplayer that we are building here as its backend.  Is the mplayer window in a web browser using its own special mplayer?

---

### Post by andrew.46 on 2008-12-31
Hi mocha,

> **mocha said:**
> I thought that the mplayer plugin was using the mplayer that we are building here as its backend.  Is the mplayer window in a web browser using its own special mplayer?

No it is the same MPlayer that the plugin uses. I was just saying I have no experience myself in using the MPlayer plugin as I have never installed it :-). 

I would be interested to hear if you build the newer Live555 libraries and experience any difference in your use of streams.

All the best,

  Andrew

---

### Post by abhilashm86 on 2008-12-31
hey thanks for those commands,i got it,now i am playing mkv file,don't know how,yesterday it din't work!!!!!!!gud one:)

abhilash@abhi:~$ mplayer mplayer /media/SONGS/Film/*.mkv
MPlayer dev-SVN-r28208-4.2.4 (C) 2000-2008 MPlayer Team
CPU: Intel(R) Pentium(R) D  CPU 2.66GHz (Family: 15, Model: 4, Stepping: 7)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

Playing mplayer.


Playing /media/SONGS/Film/Untraceable.2008.DVDRip.x264.Adz-300MB.mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_AAC), -aid 0, -alang und
[mkv] Track ID 3: subtitles (S_TEXT/UTF8) "English Subs", -sid 0, -slang eng
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  640x264  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
FAAD: compressed input bitrate missing, assuming 128kbit/s!
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio) decoder)
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 640 x 264 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 2.42:1 - prescaling to correct movie aspect.
VO: [x11] 640x264 => 640x264 Planar YV12 
[swscaler @ 0x895d0c0]using unscaled yuv420p -> rgb32 special converter
[Mixer] No hardware mixing, inserting volume filter.  5%  1.7% 13 
  =====  PAUSE  =====

---

### Post by IronFox on 2008-12-31
great guide but i get this error with exit code 1:
mplayer -noquiet -nofs -sub-fuzziness 1 -identify -msglevel demux=6 -slave -vo xv, -zoom -nokeepaspect -framedrop -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 62914572 -monitorpixelaspect 1 -subfont-autoscale 1 -subfont-text-scale 5 -subcp ISO-8859-1 -subpos 100 -contrast 0 -brightness 0 -hue 0 -saturation 0 -nocache -osdlevel 0 -vf-add screenshot -channels 2 /home/jordan/Desktop/[gg]_Maria+Holic_-_01_[Pre-Airing]_[8AA4255B].mkv

MPlayer dev-SVN-r28216-4.3.2 (C) 2000-2008 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.80GHz (Family: 15, Model: 4, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
Unknown option on the command line: -stop-xscreensaver
Error parsing option on the command line: -stop-xscreensaver

---

### Post by andrew.46 on 2008-12-31
Hi IronFox,

> **IronFox said:**
> great guide but i get this error with exit code 1:
[...]
MPlayer dev-SVN-r28216-4.3.2 (C) 2000-2008 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.80GHz (Family: 15, Model: 4, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
[B][COLOR="Red"]Unknown option on the command line: -stop-xscreensaver
Error parsing option on the command line: -stop-xscreensaver[/COLOR][/B]

Can I ask that you try to play your file from the commandline? I am running the same svn version as you and the option works fine:

```
andrew@skamandros:~/Desktop$ **[COLOR="Red"] mplayer -stop-xscreensaver 100_0057.MOV [/COLOR]**
MPlayer dev-SVN-r28216-4.3.2 (C) 2000-2008 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz (Family: 6, Model: 15, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

Playing 100_0057.MOV.
libavformat file format detected.
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  [jpeg]  640x480  24bpp  14.991 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 comments: EASTMAN KODAK COMPANY  KODAK M853 ZOOM DIGITAL CAMERA
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffmjpeg] vfm: ffmpeg (FFmpeg MJPEG decoder)
==========================================================================
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 11025 Hz, 1 ch, u8, 0.0 kbit/0.00% (ratio: 0->11025)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
AO: [oss] 11025Hz 1ch u8 (1 bytes per sample)
Starting playback...
VDec: vo config request - 640 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 3)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 640x480 => 640x480 Planar YV12 
A:  15.0 V:  14.9 A-V:  0.018 ct: -0.027   0/  0  8%  1%  0.3% 2 0 

```

which I suspect means a question for RVM if he is around, this is probably a question related to smplayer? As a start perhaps you could un-check the following option in smplayer:

SMPlayer --> Options --> Preferences --> General --> Video --> Disable Screensaver

Andrew

---

### Post by rvm4000 on 2008-12-31
If mplayer doesn't recognize the -stop-xscreensaver option I guess it's because it hasn't been compiled correctly (missing development libraries).

---

### Post by IronFox on 2009-01-01
from the command line i get the same error:

root@jordan-laptop:/home/jordan/Desktop# mplayer -stop-xscreensaver \[gg\]_Maria+Holic_-_01_\[Pre-Airing\]_\[8AA4255B\].mkv 
MPlayer dev-SVN-r28216-4.3.2 (C) 2000-2008 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.80GHz (Family: 15, Model: 4, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
Creating config file: /root/.mplayer/config
Unknown option on the command line: -stop-xscreensaver
Error parsing option on the command line: -stop-xscreensaver

BUT when I run it from the command line with no arguments its seems to work, though im not getting a video window (should I).

and when i uncheck the disable screensaver box":

MPlayer dev-SVN-r28216-4.3.2 (C) 2000-2008 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.80GHz (Family: 15, Model: 4, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
Unknown option on the command line: -nostop-xscreensaver
Error parsing option on the command line: -nostop-xscreensaver

When I compiled the libraries I didnt get any errors.  But when I try the headers I get:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
gettext is already the newest version.
gettext set to manually installed.
html2text is already the newest version.
html2text set to manually installed.
intltool-debian is already the newest version.
intltool-debian set to manually installed.
libartsc0 is already the newest version.
libartsc0 set to manually installed.
libaudio2 is already the newest version.
libaudio2 set to manually installed.
libenca0 is already the newest version.
libenca0 set to manually installed.
libfaac0 is already the newest version.
libfaac0 set to manually installed.
libfreebob0 is already the newest version.
libfreebob0 set to manually installed.
libggi-target-x is already the newest version.
libggi-target-x set to manually installed.
libggi2 is already the newest version.
libggi2 set to manually installed.
libgii1 is already the newest version.
libgii1 set to manually installed.
libgii1-target-x is already the newest version.
libgii1-target-x set to manually installed.
libglide2 is already the newest version.
libglide2 set to manually installed.
libjack0 is already the newest version.
libjack0 set to manually installed.
liblzo2-2 is already the newest version.
liblzo2-2 set to manually installed.
libmad0 is already the newest version.
libmad0 set to manually installed.
libmail-sendmail-perl is already the newest version.
libmail-sendmail-perl set to manually installed.
libmp3lame-dev is already the newest version.
libmp3lame0 is already the newest version.
libmpcdec3 is already the newest version.
libmpcdec3 set to manually installed.
libopenal1 is already the newest version.
libopenal1 set to manually installed.
libsvga1 is already the newest version.
libsvga1 set to manually installed.
libsys-hostname-long-perl is already the newest version.
libsys-hostname-long-perl set to manually installed.
libxvidcore4 is already the newest version.
libxvidcore4 set to manually installed.
libxvmc1 is already the newest version.
libxvmc1 set to manually installed.
po-debconf is already the newest version.
po-debconf set to manually installed.
zlib1g-dev is already the newest version.
zlib1g-dev set to manually installed.
E: Couldn't find package libamrnb-dev

It seems I cant find libamrnb-dev and libamrwb-dev but all others are installed

---

### Post by andrew.46 on 2009-01-01
Hi IronFox,

I suspect that as RVM has suggested you do not have all the 'dev' libraries installed. Compounding this problem you do not have the Medibuntu Repository enabled: this is the home of the amr dev files amongst others. Can you firstly check that you have the Universe, Multiverse, Main and Restricted Repositories enabled? Details of how to go about this can be seen in the Community Docs:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Can you enable the Medibuntu Repositories as well? Details of this can be seen here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

When this is all done can you run:

```
$ sudo apt-get update && sudo apt-get upgrade
```

and following this load the entire list of dev files into the terminal and reinstall, as per the guide, and with this hopefully successful run 'svn update' and compile MPlayer again. I notice you have only given about a third of the dev files in your post, is this edited a little or did you miss some?

Hopefully these steps will rectify the problem and you can start to enjoy both MPlayer and SMPlayer :-).

All the best,

Andrew

**Edit:** BTW You are not running this all as root are you? Just logon as an unpriviledged user if this is the case and use sudo where required.

---

### Post by IronFox on 2009-01-01
im getting quite a few errors when trying to update.  When I recompile I get
```
svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer
svn: Working copy 'mplayer' locked
svn: run 'svn cleanup' to remove locks (type 'svn help cleanup' for details)
```

then when I run svn cleanup i get
```
svn cleanup
svn: '.' is not a working copy directory
```

even when I try svn update i get
```
svn update
Skipped '.'
```

EDIT:  Got it working by going to the mplayer website and downloading the snapshot instead of going through the command prompt.  Compiled it after installing _all_ of the dev headers and files.  Works great!  since i watch alot of anime thats in a variety of formats, totem gsteamer/xine wasnt working very well.  Im switched to smplayer now!

---

### Post by andrew.46 on 2009-01-01
Hi IronFox,

> **IronFox said:**
> Got it working by going to the mplayer website and downloading the snapshot instead of going through the command prompt.  Compiled it after installing _all_ of the dev headers and files.  Works great!  since i watch alot of anime thats in a variety of formats, totem gsteamer/xine wasnt working very well.  Im switched to smplayer now!

Excellent news! MPlayer is an amazing program and it richly rewards the time spent learning to use it. svn snapshot is fine but I think the svn errors you received are easily rectified. The error you received:

```
andrew@skamandros:~$ svn cleanup
svn: '.' is not a working copy directory
```

either means you are in the wrong directory or for some reason your svn materials lack the required .svn material. You can either ensure that you are in the correct directory:

```
$ cd $HOME/mplayer
$ svn cleanup
$ svn update
```

or 'cut the Gordian knot' and delete the entire directory and contents and issue the original svn command. If you are happier with the snapshots from the MPlayer website just note that there are 2 different types of snapshots from svn: one *with* the svn meta information that can be updated if you wish and one *without* which cannot be updated. This represents the difference between 'svn checkout' and 'svn export'.

Anyway good to hear you have it all running :-).

Andrew

---

### Post by mach-schnell on 2009-01-03
Somewhat recently, Nvidia has included VDPAU support for some video cards in its release of beta drivers, essentially bringing "purevideo" to linux.  In order to demonstrate its capabilities, they created a patch for mplayer to take advantage of the new api.  

I realize this is a somewhat niche application, since these drivers are both proprietary and beta.  However, can you offer any advice for applying Nvidia's patch?  It can be found at the bottom of the following page: [http://www.nvnews.net/vbulletin/showthread.php?t=123091](http://www.nvnews.net/vbulletin/showthread.php?t=123091)

If not, would you consider looking at it in the future when drivers are stable?

Either way, thanks for the excellent guide.

---

### Post by andrew.46 on 2009-01-03
Hi mach-schnell,

> **mach-schnell said:**
> Somewhat recently, Nvidia has included VDPAU support for some video cards in its release of beta drivers, essentially bringing "purevideo" to linux.  In order to demonstrate its capabilities, they created a patch for mplayer to take advantage of the new api.

I do remember an announcement by the Nvidia people on MPlayer-users but I will have to admit as a man who runs an 'on-board' video chip I glossed over it fairly quickly :-). 

> I realize this is a somewhat niche application, since these drivers are both proprietary and beta.  However, can you offer any advice for applying Nvidia's patch?  It can be found at the bottom of the following page: [http://www.nvnews.net/vbulletin/showthread.php?t=123091](http://www.nvnews.net/vbulletin/showthread.php?t=123091)

It is actually a series of patches tied together with an installation script. Of special note is that it appears to require the download of a specific MPlayer svn version: 27960 and also a specific version of ffmpeg: 15884 that is patched.

> If not, would you consider looking at it in the future when drivers are stable?

Personally I would not actually *install* it to the system but there should be no harm in running the script 'checkout-patch-build.sh', which only goes as far as 'make' and then running it from the build directory as ./mplayer, utilising the syntax suggested in the README:

```
$ cd mplayer-vdpau
$ ./mplayer -vc <VDPAU-codec-name> -vo vdpau <filename>
```

It is quite an extensive series of patches so probably will only install cleanly on these specific versions. So I would say test it out but keep your main svn MPlayer in place as well :-).

> Either way, thanks for the excellent guide.

The guide still gives me enormous pleasure to write, troubleshoot and support!

Andrew

**Edit:** Looks like there may be an implementation for vo vdpau in svn shortly so perhaps hold off for a bit?

---

### Post by napauleon on 2009-01-06
I don't know whether this is the right topic since I use Hardy Heron, but the other thread about this topic seems kinda closed, so I'll post my question here too:

First of all: a great guide for installing mplayer from svn

The only thing i cant get my head around is lirc support. When using mplayer from the package tree, lirc works fine.

However i needed some extra's for my 1080p video's (coreavc), which runs very nice now. However i can't get lirc to work with the latest svn release of mplayer (dev-SVN-r28274-4.2.4).

when I run ./configure it shows that it found a positive lookup for --enable-lirc (not for --enable-lircc) and it compiles fine when running make.
However lirc is not loaded when running mplayer. I've got all the necessary lirc packages installed i guess.

Any ideas on getting lirc to work with the svn release of mplayer?

---

### Post by andrew.46 on 2009-01-06
Hi napauleon,

I have taken the liberty of reproducing in full my reply from the 'other' guide :-).

> **napauleon said:**
> [...]when I run ./configure it shows that it found a positive lookup for --enable-lirc (not for --enable-lircc) and it compiles fine when running make. However lirc is not loaded when running mplayer. I've got all the necessary lirc packages installed i guess. Any ideas on getting lirc to work with the svn release of mplayer?

Only 2 potential problems that I can see. Firstly make sure that you *don't* try to specifically --enable-lirc in your configure options, with MPlayer the configure process is best left to find the required files itself. If you specify such an option you need also to manually locate all the header files and this is not normally required (in fact I have never had to do it).

Secondly ensure that you have the required dev files, which you may have already. If you were using Intrepid the required file would be:

```
$ sudo apt-get install liblircclient-dev
```

and it is *probably* the same under Hardy but you can check by using the following:

```
$ sudo apt-cache search lirc | grep dev 
```

This will give a few choices and probably liblircclient-dev will be one of them. You will then need to recompile. Hopefully this is all that is required, in part because that is the limit of my knowledge of lirc :-).

All the best,

Andrew

---

### Post by napauleon on 2009-01-07
thanks for the suggestions, but unfortunately it didn't help. I tried that already.
The expectation i had is that mplayer produces a message like "setting up lirc support", but that message isn't there.
But when i disable lirc, the message "Failed to open LIRC support. You will not be able to use your remote control." does pop up, so the support for lirc seems to be in order i guess.

Now i have to figure out why my remote doesn't work on mplayer...

---

### Post by andrew.46 on 2009-01-07
Hi,

> **napauleon said:**
> thanks for the suggestions, but unfortunately it didn't help. I tried that already.
The expectation i had is that mplayer produces a message like "setting up lirc support", but that message isn't there.
But when i disable lirc, the message "Failed to open LIRC support. You will not be able to use your remote control." does pop up, so the support for lirc seems to be in order i guess.

In fact I am out of ideas and my apologies for being little help to you. You have probably read the relevent docs:

[http://www.mplayerhq.hu/DOCS/HTML/en/control.html#lirc](http://www.mplayerhq.hu/DOCS/HTML/en/control.html#lirc)

and perhaps the final option is to try the MPlayer-users. This group can be a little firm with some questions and I would suggest lurking a little while if you have not already encountered the attitudes of some in this group.

All the best with this, and my apologies again,

Andrew

---

### Post by CraymelCage on 2009-01-07
Hi I just installed mplayer using this guide and I can't play any dvds.I also had this problem with installing using your other guide to (used smplayer for both guides). All smplayer does is resize and then nothing. I did get this error once

```
mplayer -noquiet -nofs -lavdopts threads=8 -sub-fuzziness 1 -identify -slave -vo xv:adaptor=1 -ao alsa -zoom -nokeepaspect -nodr -double -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 50331660 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/jonathan/.config/smplayer/styles.*** -fontconfig -font Arial -subcp ISO-8859-1 -vid 0 -aid 128 -subpos 100 -dvd-device /dev/dvd -dvdangle 1 -nocache -ss 12 -osdlevel 0 -idx -correct-pts -vf-add screenshot -slices -channels 2 -af scaletempo,equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 400 dvd://1

MPlayer dev-SVN-r28279-4.3.2 (C) 2000-2008 MPlayer Team
CPU: Intel(R) Core(TM) Duo CPU      T2450  @ 2.00GHz (Family: 6, Model: 14, Stepping: 12)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
Terminal type `unknown' is not defined.

Playing dvd://1.
ID_DVD_TITLES=29
ID_DVD_TITLE_1_CHAPTERS=24
ID_DVD_TITLE_1_ANGLES=2
ID_DVD_TITLE_2_CHAPTERS=1
ID_DVD_TITLE_2_ANGLES=1
ID_DVD_TITLE_3_CHAPTERS=3
ID_DVD_TITLE_3_ANGLES=1
ID_DVD_TITLE_4_CHAPTERS=3
ID_DVD_TITLE_4_ANGLES=1
ID_DVD_TITLE_5_CHAPTERS=2
ID_DVD_TITLE_5_ANGLES=1
ID_DVD_TITLE_6_CHAPTERS=2
ID_DVD_TITLE_6_ANGLES=1
ID_DVD_TITLE_7_CHAPTERS=1
ID_DVD_TITLE_7_ANGLES=1
ID_DVD_TITLE_8_CHAPTERS=1
ID_DVD_TITLE_8_ANGLES=1
ID_DVD_TITLE_9_CHAPTERS=1
ID_DVD_TITLE_9_ANGLES=1
ID_DVD_TITLE_10_CHAPTERS=1
ID_DVD_TITLE_10_ANGLES=1
ID_DVD_TITLE_11_CHAPTERS=6
ID_DVD_TITLE_11_ANGLES=1
ID_DVD_TITLE_12_CHAPTERS=2
ID_DVD_TITLE_12_ANGLES=1
ID_DVD_TITLE_13_CHAPTERS=2
ID_DVD_TITLE_13_ANGLES=1
ID_DVD_TITLE_14_CHAPTERS=2
ID_DVD_TITLE_14_ANGLES=1
ID_DVD_TITLE_15_CHAPTERS=2
ID_DVD_TITLE_15_ANGLES=1
ID_DVD_TITLE_16_CHAPTERS=2
ID_DVD_TITLE_16_ANGLES=1
ID_DVD_TITLE_17_CHAPTERS=2
ID_DVD_TITLE_17_ANGLES=1
ID_DVD_TITLE_18_CHAPTERS=7
ID_DVD_TITLE_18_ANGLES=1
ID_DVD_TITLE_19_CHAPTERS=1
ID_DVD_TITLE_19_ANGLES=1
ID_DVD_TITLE_20_CHAPTERS=2
ID_DVD_TITLE_20_ANGLES=1
ID_DVD_TITLE_21_CHAPTERS=2
ID_DVD_TITLE_21_ANGLES=1
ID_DVD_TITLE_22_CHAPTERS=7
ID_DVD_TITLE_22_ANGLES=1
ID_DVD_TITLE_23_CHAPTERS=1
ID_DVD_TITLE_23_ANGLES=1
ID_DVD_TITLE_24_CHAPTERS=11
ID_DVD_TITLE_24_ANGLES=1
ID_DVD_TITLE_25_CHAPTERS=15
ID_DVD_TITLE_25_ANGLES=1
ID_DVD_TITLE_26_CHAPTERS=2
ID_DVD_TITLE_26_ANGLES=1
ID_DVD_TITLE_27_CHAPTERS=1
ID_DVD_TITLE_27_ANGLES=1
ID_DVD_TITLE_28_CHAPTERS=3
ID_DVD_TITLE_28_ANGLES=1
ID_DVD_TITLE_29_CHAPTERS=3
ID_DVD_TITLE_29_ANGLES=1
ID_DVD_TITLE_1_LENGTH=7100.700
ID_DVD_TITLE_2_LENGTH=0.500
ID_DVD_TITLE_3_LENGTH=34.500
ID_DVD_TITLE_4_LENGTH=6.000
ID_DVD_TITLE_5_LENGTH=10.500
ID_DVD_TITLE_6_LENGTH=19.500
ID_DVD_TITLE_7_LENGTH=0.500
ID_DVD_TITLE_8_LENGTH=0.500
ID_DVD_TITLE_9_LENGTH=0.500
ID_DVD_TITLE_10_LENGTH=0.500
ID_DVD_TITLE_11_LENGTH=372.867
ID_DVD_TITLE_12_LENGTH=95.066
ID_DVD_TITLE_13_LENGTH=142.066
ID_DVD_TITLE_14_LENGTH=108.300
ID_DVD_TITLE_15_LENGTH=98.000
ID_DVD_TITLE_16_LENGTH=80.500
ID_DVD_TITLE_17_LENGTH=71.000
ID_DVD_TITLE_18_LENGTH=592.433
ID_DVD_TITLE_19_LENGTH=0.500
ID_DVD_TITLE_20_LENGTH=466.867
ID_DVD_TITLE_21_LENGTH=1664.834
ID_DVD_TITLE_22_LENGTH=509.500
ID_DVD_TITLE_23_LENGTH=0.500
ID_DVD_TITLE_24_LENGTH=0.500
ID_DVD_TITLE_25_LENGTH=0.500
ID_DVD_TITLE_26_LENGTH=1.000
ID_DVD_TITLE_27_LENGTH=0.500
ID_DVD_TITLE_28_LENGTH=1.000
ID_DVD_TITLE_29_LENGTH=19.200
ID_DVD_DISC_ID=1E26BBB67D6EF70FE88E3DE8CCEB7DAC
ID_DVD_VOLUME_ID=NVWONND1
There are 29 titles on this DVD.
ID_DVD_CURRENT_TITLE=1
There are 2 angles in this DVD title.
audio stream: 0 format: ac3 (stereo) language: en aid: 128.
ID_AUDIO_ID=128
ID_AID_128_LANG=en
audio stream: 1 format: ac3 (stereo) language: ja aid: 129.
ID_AUDIO_ID=129
ID_AID_129_LANG=ja
number of audio channels on disk: 2.
subtitle ( sid ): 0 language: en
ID_SUBTITLE_ID=0
ID_SID_0_LANG=en
subtitle ( sid ): 1 language: en
ID_SUBTITLE_ID=1
ID_SID_1_LANG=en
number of subtitles on disk: 2
CHAPTERS: 00:00:00,00:07:54,00:12:21,00:18:48,00:23:45,00:28:49,00:33:40,00:38:25,00:45:06,00:50:02,00:54:49,00:58:36,01:01:27,01:08:01,01:13:58,01:18:46,01:24:35,01:30:56,01:34:45,01:40:16,01:46:11,01:49:52,01:52:14,01:58:20,
ID_VIDEO_ID=0
MPEG-PS file format detected.
ID_AUDIO_ID=128
VIDEO:  MPEG2  720x480  (aspect 3)  29.970 fps  9800.0 kbps (1225.0 kbyte/s)
ID_FILENAME=dvd://1
ID_DEMUXER=mpegps
ID_VIDEO_FORMAT=0x10000002
ID_VIDEO_BITRATE=9800000
ID_VIDEO_WIDTH=720
ID_VIDEO_HEIGHT=480
ID_VIDEO_FPS=29.970
ID_VIDEO_ASPECT=0.0000
ID_AUDIO_FORMAT=8192
ID_AUDIO_BITRATE=0
ID_AUDIO_RATE=0
ID_AUDIO_NCH=0
ID_LENGTH=7100.70
ID_SEEKABLE=1
ID_CHAPTERS=24
[***] auto-open
Opening video filter: [screenshot]
[***] Init
[***] Updating font cache.
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffmpeg2] vfm: ffmpeg (FFmpeg MPEG-2)
==========================================================================
ID_VIDEO_CODEC=ffmpeg2
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
ID_AUDIO_BITRATE=192000
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=2
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [alsa] 48000Hz 2ch floatle (4 bytes per sample)
ID_AUDIO_CODEC=a52
Starting playback...
ID_AUDIO_ID=129
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
ID_VIDEO_ASPECT=1.7778
SwScaler: reducing / aligning filtersize 5 -> 4
SwScaler: reducing / aligning filtersize 5 -> 4
SwScaler: reducing / aligning filtersize 1 -> 1
SwScaler: reducing / aligning filtersize 5 -> 4
[swscaler @ 0x8a1d1e0]BICUBIC scaler, from yuv420p to rgb24 using MMX2
[swscaler @ 0x8a1d1e0]using 4-tap MMX scaler for horizontal luminance scaling
[swscaler @ 0x8a1d1e0]using 4-tap MMX scaler for horizontal chrominance scaling
[swscaler @ 0x8a1d1e0]using n-tap MMX scaler for vertical scaling (BGR)
[swscaler @ 0x8a1d1e0]720x480 -> 854x480
VO: [xv] 720x480 => 854x480 Planar YV12  [zoom]
X11 error: BadAccess during XSelectInput Call
X11 error: The 'ButtonPressMask' mask of specified window has probably already used by another appication (see man XSelectInput)
X11 error: MPlayer discards mouse control (reconfiguring)
[mpeg2video @ 0x8973a30]ac-tex damaged at 4 7
[mpeg2video @ 0x8973a30]Warning MVs not available
[mpeg2video @ 0x8973a30]concealing 1035 DC, 1035 AC, 1035 MV errors
[mpeg2video @ 0x8973a30]Missing picture start code
[mpeg2video @ 0x8973a30]Missing picture start code
[mpeg2video @ 0x8973a30]Missing picture start code
[mpeg2video @ 0x8973a30]Missing picture start code
[mpeg2video @ 0x8973a30]Missing picture start code
[mpeg2video @ 0x8973a30]Missing picture start code
[mpeg2video @ 0x8973a30]Missing picture start code
[mpeg2video @ 0x8973a30]Missing picture start code
[mpeg2video @ 0x8973a30]concealing 1035 DC, 1035 AC, 1035 MV errors
[mpeg2video @ 0x8973a30]Missing picture start code
[mpeg2video @ 0x8973a30]Missing picture start code
[mpeg2video @ 0x8973a30]Missing picture start code
[mpeg2video @ 0x8973a30]Missing picture start code
[mpeg2video @ 0x8973a30]Missing picture start code
[mpeg2video @ 0x8973a30]Missing picture start code
[mpeg2video @ 0x8973a30]Missing picture start code
[mpeg2video @ 0x8973a30]Missing picture start code
[mpeg2video @ 0x8973a30]concealing 1035 DC, 1035 AC, 1035 MV errors
[mpeg2video @ 0x8973a30]Missing picture start code
[mpeg2video @ 0x8973a30]Missing picture start code
[mpeg2video @ 0x8973a30]Missing picture start code
[mpeg2video @ 0x8973a30]Missing picture start code
[mpeg2video @ 0x8973a30]Missing picture start code
[mpeg2video @ 0x8973a30]Missing picture start code
[mpeg2video @ 0x8973a30]concealing 1035 DC, 1035 AC, 1035 MV errors
[mpeg2video @ 0x8973a30]Missing picture start code
[mpeg2video @ 0x8973a30]Missing picture start code
[mpeg2video @ 0x8973a30]Missing picture start code
[mpeg2video @ 0x8973a30]Missing picture start code
[mpeg2video @ 0x8973a30]Missing picture start code
[mpeg2video @ 0x8973a30]Missing picture start code
[mpeg2video @ 0x8973a30]Missing picture start code
[mpeg2video @ 0x8973a30]Missing picture start code
[mpeg2video @ 0x8973a30]Missing picture start code
[mpeg2video @ 0x8973a30]Missing picture start code
[mpeg2video @ 0x8973a30]Missing picture start code
[mpeg2video @ 0x8973a30]Missing picture start code
[mpeg2video @ 0x8973a30]Missing picture start code
[mpeg2video @ 0x8973a30]Missing picture start code
[mpeg2video @ 0x8973a30]Missing picture start code
[mpeg2video @ 0x8973a30]Missing picture start code
[mpeg2video @ 0x8973a30]Missing picture start code
[mpeg2video @ 0x8973a30]Missing picture start code
[mpeg2video @ 0x8973a30]Missing picture start code
[mpeg2video @ 0x8973a30]Missing picture start code
[mpeg2video @ 0x8973a30]Missing picture start code
[mpeg2video @ 0x8973a30]Missing picture start code
[mpeg2video @ 0x8973a30]Missing picture start code


MPlayer interrupted by signal 11 in module: decode video
ID_SIGNAL=11
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.

```

---

### Post by andrew.46 on 2009-01-07
Hi,

CraymelCage,

> **CraymelCage said:**
> Hi I just installed mplayer using this guide and I can't play any dvds.I also had this problem with installing using your other guide to (used smplayer for both guides). All smplayer does is resize and then nothing. I did get this error once

```

X11 error: BadAccess during XSelectInput Call
X11 error: The 'ButtonPressMask' mask of specified window has probably already used by another appication (see man XSelectInput)

```

This error has been mentioned on MPlayer-users and at least one person has associated this with the '-wid 50331660' option. Can you try without this option? Best way is to use the command line as follows:

```
$ mplayer -v dvd://1
```

I note a similar reference to this error, although not with DVD playback, that was solved differently:

[http://www.thinkdigit.com/forum/showthread.php?p=964514](http://www.thinkdigit.com/forum/showthread.php?p=964514)

I suspect that the bare commandline will play your dvd's, but I have been wrong before :-).

Andrew

---

### Post by CraymelCage on 2009-01-07
> **andrew.46 said:**
> Hi,

CraymelCage,



This error has been mentioned on MPlayer-users and at least one person has associated this with the '-wid 50331660' option. Can you try without this option? Best way is to use the command line as follows:

```
$ mplayer -v dvd://1
```

I note a similar reference to this error, although not with DVD playback, that was solved differently:

[http://www.thinkdigit.com/forum/showthread.php?p=964514](http://www.thinkdigit.com/forum/showthread.php?p=964514)

I suspect that the bare commandline will play your dvd's, but I have been wrong before :-).

Andrew

It seems to work perfect if I use the commandline perfectly. The disabling screen saver option doesn't fix it in smplayer though. It's a shame because I'd rather not go to the command line just to play dvds.

EDIT: I've also found out that the dvd is playing smplayer but the picture is black except for an occasional grey bar that appears at the top. audio is fine as well.

EDIT: Also can you clarify what '-wid 50331660' is please?

---

### Post by andrew.46 on 2009-01-08
Hi CraymelCage,

> **CraymelCage said:**
> Also can you clarify what '-wid 50331660' is please?

This is something used by smplayer:

>        -wid <window ID> (also see -guiwid) (X11, OpenGL and DirectX only)
              This  tells  MPlayer to attach to an existing window.  Useful to
              embed MPlayer in a browser (e.g. the plugger extension).

although I am not sure how the window ID is generated. Again I am afraid that I do not know how to solve this problem and unfortunately I cannot duplicate the error on my own system. Anybody else with ideas??

Andrew

---

### Post by CraymelCage on 2009-01-08
it still doesn't work when I disable mplayer being embedded in smplayer. I'll see what else I can do. Kay I got it working. I had to disable correct-pts and picture would be displayed but jumpy and strips would flash by so I had to enable software video equalizer and it runs perfect now.

EDIT: Now if only mplayer would support dvd menus it would be the perfect dvd player :P I don't know why they haven't fixed that.

---

### Post by rvm4000 on 2009-01-08
If the picture is black in smplayer, I suggest to try to disable the option "Repaint the background of the video window" in Preferences->Advanced. If that doesn' fix the problem, try another video driver in Preferences->General->Video.

---

### Post by andrew.46 on 2009-01-08
Hi CraymelCage,

> **CraymelCage said:**
> Now if only mplayer would support dvd menus it would be the perfect dvd player :P I don't know why they haven't fixed that.

Well actually MPlayer *does* support dvd menus but it is still a work in progress. Support has to be compiled in and libdvdnav is still an *exernal* library. Details can be seen in DOCS/tech/dvdnav-howto.txt of the MPlayer tarball although even that is a little out of date now that libdvdread has been incorporated from its svn site.

Andrew

---

### Post by rvm4000 on 2009-01-11
Since SVN r28291, the mplayer sources also include an internal copy of libdvdnav. So now there's no need to compile libdvdread4 and libdvdnav4 :)

---

### Post by andrew.46 on 2009-01-12
Hi rvm,

> **rvm4000 said:**
> Since SVN r28291, the mplayer sources also include an internal copy of libdvdnav. So now there's no need to compile libdvdread4 and libdvdnav4 :)

That is truly great news, I have been waiting for some time for this one! I note that it is auto-detected as well so no configure options need adjusting. I have been waiting to see this for a long time:

```
Checking for DVD support (libdvdnav) ... yes (internal)
```

Now to play with the menus :-).

Andrew

---

### Post by CraymelCage on 2009-01-15
Yes! I've also been waiting ages for this now mplayer really does do everything I want it to:KS

Edit: Kay so I compiled mplayer again and there's no playback problem but gmplayer is enabled by default now. I'm sure you know this but I think it would be good to add how to disable gmplayer since this guide is for using mplayer with smplayer.

Edit2: No, Wait. Ignore what I just wrote. I installed the default mplayer in the repositories by mistake... WOOPS!

---

### Post by Dakanya on 2009-01-16
> cpudetect.c: Assembler messages:
cpudetect.c:104: Error: bad register name `%rbx'
cpudetect.c:106: Error: bad register name `%rbx'
cpudetect.c:104: Error: bad register name `%rbx'
cpudetect.c:106: Error: bad register name `%rbx'
cpudetect.c:104: Error: bad register name `%rbx'
cpudetect.c:106: Error: bad register name `%rbx'
cpudetect.c:104: Error: bad register name `%rbx'
cpudetect.c:106: Error: bad register name `%rbx'
cpudetect.c:67: Error: suffix or operands invalid for `pushf'
cpudetect.c:72: Error: suffix or operands invalid for `popf'
cpudetect.c:73: Error: suffix or operands invalid for `pushf'
cpudetect.c:104: Error: bad register name `%rbx'
cpudetect.c:106: Error: bad register name `%rbx'
cpudetect.c:104: Error: bad register name `%rbx'
cpudetect.c:106: Error: bad register name `%rbx'
cpudetect.c:104: Error: bad register name `%rbx'
cpudetect.c:106: Error: bad register name `%rbx'
cpudetect.c:104: Error: bad register name `%rbx'
cpudetect.c:106: Error: bad register name `%rbx'
cpudetect.c:104: Error: bad register name `%rbx'
cpudetect.c:106: Error: bad register name `%rbx'
make: *** [cpudetect.o] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

I keep running into this problem trying to compile and install mplayer. Any ideas? :confused:

---

### Post by andrew.46 on 2009-01-16
Hi Dakanya,

> **Dakanya said:**
> I keep running into this problem trying to compile and install mplayer. Any ideas? :confused:

This seems to be quite a turbulent period for the svn MPlayer and I have not been able to successfully compile a revision over the last week or so. Best advice is to wait for a couple of days and try again. You can keep an eye on developments via the MPlayer-users:

[http://lists.mplayerhq.hu/pipermail/mplayer-users/](http://lists.mplayerhq.hu/pipermail/mplayer-users/)

It will be a worthwhile wait as some major developments are settling in: libdvdnav and libdvdread incorporated from their own svn homes, the new NVidia driver incorporated .....

Andrew

---

### Post by Dakanya on 2009-01-16
> **andrew.46 said:**
> Hi Dakanya,



This seems to be quite a turbulent period for the svn MPlayer and I have not been able to successfully compile a revision over the last week or so. Best advice is to wait for a couple of days and try again. You can keep an eye on developments via the MPlayer-users:

[http://lists.mplayerhq.hu/pipermail/mplayer-users/](http://lists.mplayerhq.hu/pipermail/mplayer-users/)

It will be a worthwhile wait as some major developments are settling in: libdvdnav and libdvdread incorporated from their own svn homes, the new NVidia driver incorporated .....

Andrew
Alright, thanks for the quick reply. :)

---

### Post by andrew.46 on 2009-01-16
Hi Dakanya,

> **Dakanya said:**
> Alright, thanks for the quick reply. :)

Things appear to have settled a little and I have had success with r28337. You could either try a straight 'svn up' or aim for this revision specifically from your svn tree with:

```
$ svn update -r 28337
```

and then recompile as before.

All the best,

Andrew

---

### Post by domoso on 2009-01-16
Hello Andrew. You guide is much appreciated. I've gone through it and everything works great until compile time which results in the following error:

> libvo/aclib.c:105:1: warning: "HAVE_MMX" redefined
libvo/aclib.c:100:1: warning: this is the location of the previous definition
libvo/aclib.c:106:1: warning: "HAVE_MMX2" redefined
libvo/aclib.c:101:1: warning: this is the location of the previous definition
In file included from libvo/aclib.c:108:
libvo/aclib_template.c:69:14: error: operator '&&' has no left operand
libvo/aclib_template.c:80:16: error: operator '!' has no right operand
libvo/aclib_template.c:108:14: error: #if with no expression
libvo/aclib_template.c:124:14: error: #if with no expression
libvo/aclib_template.c:347:14: error: #if with no expression
libvo/aclib_template.c:431:14: error: #if with no expression
libvo/aclib.c:168:16: error: #if with no expression
libvo/aclib.c:172:15: error: #if with no expression
libvo/aclib.c:202:16: error: #if with no expression
libvo/aclib.c:206:15: error: #if with no expression
make: *** [libvo/aclib.o] Error 1


I've been working on this off and on most of the day. However, I have only found one post concerning libvo/aclib.o error 1 using Google. It was one post asking about the error with no followup that I can find. Might you have a suggestion? I'm running an Athlon XP + 2800 but, I have no idea how to deal with the mmx issue, from what it appears.

---

### Post by andrew.46 on 2009-01-16
Hi domoso,

> **domoso said:**
> Hello Andrew. You guide is much appreciated. I've gone through it and everything works great until compile time which results in the following error:
```
libvo/aclib.c:105:1: warning: "HAVE_MMX" redefined
libvo/aclib.c:100:1: warning: this is the location of the previous definition
libvo/aclib.c:106:1: warning: "HAVE_MMX2" redefined
libvo/aclib.c:101:1: warning: this is the location of the previous definition
```

This has been rectified with [revision 28337]("http://svn.mplayerhq.hu/mplayer?view=rev&revision=28337") so I suspect if you run 'svn update' from your source tree you should be able to successfully compile.

All the best,

Andrew

---

### Post by domoso on 2009-01-16
Wow, quick replier! I'm compiling now after running svn update. Another question for you. It's a "help me help myself" question. How would I have found that out? And how is it you have your hands on the pulse of mplayer development?

Compilation successful, thanks.

---

### Post by andrew.46 on 2009-01-16
Hi domoso,

> **domoso said:**
> Wow, quick replier! I'm compiling now after running svn update. Another question for you. It's a "help me help myself" question. How would I have found that out? And how is it you have your hands on the pulse of mplayer development?

But if I tell you that you will no longer believe that I am quite so clever :-). But seriously there are 2 mailing lists that are well worth subscribing to even if only to see some of the developers fighting:

Mplayer-Users
[https://lists.mplayerhq.hu/mailman/listinfo/mplayer-users](https://lists.mplayerhq.hu/mailman/listinfo/mplayer-users)

and 

MPlayer-dev-eng -- MPlayer development
[https://lists.mplayerhq.hu/mailman/listinfo/mplayer-dev-eng](https://lists.mplayerhq.hu/mailman/listinfo/mplayer-dev-eng)

I would strongly advise lurking for a while in both of these mailing lists as perceived infractions are dealt with *very* sternly. It is also well worthwhile to keep an eye on the web interface of the svn repository:

[http://svn.mplayerhq.hu/mplayer/trunk/](http://svn.mplayerhq.hu/mplayer/trunk/)


> Compilation successful, thanks.

Excellent news!

Andrew

---

### Post by CraymelCage on 2009-01-16
Having new problems woohoo. So I just did a new install of mplayer for the dvd menus and all that jazz. Well my problem is that it doesn't play anything using smplayer and when I use the command line it only plays the audio of video files. So I'm guessing it has something to do with video output driver. But here is the strange thing. My list of video ouput drivers is seriously gimped same with my audio output drivers as well.

video options: fbdev, fbdev2, v4fl2, cvidx, mpegpes, yuv4mpeg, user defined set as xv

audio options: oss, mpegpes, v4l2, null, pcm, user defined set as alsa

and heres the log that shows up when player crashes.

```
mplayer -noquiet -nofs -lavdopts threads=8 -sub-fuzziness 1 -identify -slave -vo xv, -ao alsa, -zoom -nokeepaspect -framedrop -nodr -double -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 52428812 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/jonathan/.config/smplayer/styles.*** -fontconfig -font Arial -subcp ISO-8859-1 -subpos 100 -volume 40 -dvd-device /dev/dvd -dvdangle 1 -cache 100000 -osdlevel 0 -nocorrect-pts -vf-add eq2,hue -vf-add screenshot -slices -channels 2 -af scaletempo,equalizer=0:0:0:0:0:0:0:0:0:0 dvd://1

MPlayer dev-SVN-r28337-4.3.2 (C) 2000-2009 MPlayer Team
CPU: Intel(R) Core(TM) Duo CPU      T2450  @ 2.00GHz (Family: 6, Model: 14, Stepping: 12)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
Unknown option on the command line: -stop-xscreensaver
Error parsing option on the command line: -stop-xscreensaver
ID_EXIT=NONE

```

I don't know what to do... I r sad:(

EDIT: Ok so I just uninstalled smplayer 6.6 and installed 6.1 from the repositories and the problem still persists but if you look for the video and audio output driver lists you wont be able to find them because they're just not there... At all! there's not even text that says video or audio output drivers. I don't think any of them are actually installed at this point... Second opinion?

---

### Post by andrew.46 on 2009-01-16
Hi CraymelCage,

It sounds like a bad compile as both the current MPlayer and SMPlayer *should* be working perfectly. 

Pivotal to any compiling effort in Ubuntu is the 'dev' files so can I suggest you pick up the entire list of dev files given in the guide and plant them in a terminal to download with 'sudo apt-get install'. Download any required files and if you could report any errors back here that would be great; these errors may show where there is a problem.

Once this is accomplished completely remove the svn material by deleting $HOME/mplayer and all its subdirectories and again run:

```
$ cd $HOME
$ svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer
$ cd $HOME/mplayer
$ ./configure
$ make
$ sudo checkinstall -D --install=yes --fstrans=no --pakdir "$HOME/Desktop" \
--maintainer "$USER" --pkgname mplayer --pkgversion "3:1.0~svn" \
--backup=no --deldoc=yes --deldesc=yes --delspec=yes --gzman --default
$ make clean
```

This is as much as I do on my own Ubuntu system and if there are no errors given by the terminal you should have a perfectly running svn MPlayer + SMPlayer.

All the best with this,

Andrew

---

### Post by CraymelCage on 2009-01-16
this is what I get when I try to install those dev files.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libaudio2 is already the newest version.
libaudio2 set to manually installed.
libfaac0 is already the newest version.
libfreebob0 is already the newest version.
libjack0 is already the newest version.
liblzo2-2 is already the newest version.
libmad0 is already the newest version.
libmp3lame0 is already the newest version.
libmpcdec3 is already the newest version.
libopenal1 is already the newest version.
libopenal1 set to manually installed.
libxvidcore4 is already the newest version.
E: Couldn't find package libamrnb-dev

```

and this is all the things that are disabled when I compile mplayer

```
 Disabled optional drivers:
    Input: vstream radio tv-teletext tv-dshow nemesi cddb cdda smb 
    Codecs: libschroedinger libdirac xvid libdv libamr_wb libamr_nb faac musepack libdca libtheora speex toolame twolame libmad liblzo gif 
    Audio output: sun alsa openal jack pulse nas esd arts ivtv dxr2 sdl 
    Video output: zr zr2 ivtv dxr3 dxr2 sdl vesa gif89a jpeg png svga caca aa ggi xmga mga xvidix winvidix opengl 3dfx dga xvmc xv x11 dfbmga directfb bl xvr100 tdfx_vid wii s3fb tdfxfb 
```

yup they're not installing.

---

### Post by andrew.46 on 2009-01-17
Hi CraymelCage,

Well that is actually good news because it is now clear why your copy of the svn MPlayer is failing: you have not been able to compile against all of the required dev files.

> **CraymelCage said:**
> this is what I get when I try to install those dev files.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libaudio2 is already the newest version.
libaudio2 set to manually installed.
libfaac0 is already the newest version.
libfreebob0 is already the newest version.
libjack0 is already the newest version.
liblzo2-2 is already the newest version.
libmad0 is already the newest version.
libmp3lame0 is already the newest version.
libmpcdec3 is already the newest version.
libopenal1 is already the newest version.
libopenal1 set to manually installed.
libxvidcore4 is already the newest version.
E: Couldn't find package libamrnb-dev

```

There are 2 things to note here:

[LIST=1]
[*]**E: Couldn't find package libamrnb-dev** This file is located in the Medibuntu repository and it should be well worth your while to [add this repository to your list]("https://help.ubuntu.com/community/Medibuntu").
[*]**The number of dev files is too low**. The dev files you quote above are only about a tenth of the requirements to compile MPlayer. I give the full list below:
[/LIST]

```
sudo apt-get install em8300-headers gawk gettext html2text intltool-debian \
ladspa-sdk libaa1-dev libartsc0 libartsc0-dev libasound2-dev libatk1.0-dev libaudio-dev \
libaudio2 libaudiofile-dev libavahi-client-dev libavahi-common-dev libcaca-dev \
libcairo2-dev libcdparanoia0-dev libcucul-dev libdbus-1-dev libdbus-glib-1-dev \
libdirectfb-dev libdirectfb-extra libdts-dev libdv4-dev libenca-dev libenca0 \
libesd0-dev libexpat1-dev libfaac-dev libfaac0 libfontconfig1-dev libfreebob0 \
libfreetype6-dev libfribidi-dev libggi-target-x libggi2 libggi2-dev libggimisc2 \
libggimisc2-dev libgif-dev libgii1 libgii1-dev libgii1-target-x libgl1-mesa-dev \
libglib2.0-dev libglide2 libglu1-mesa-dev libglu1-xorg-dev libgtk2.0-dev libice-dev \
libjack-dev libjack0 libjpeg62-dev liblzo-dev liblzo1 liblzo2-2 liblzo2-dev libmad0 \
libmad0-dev libmail-sendmail-perl libmp3lame-dev libmp3lame0 libmpcdec-dev libmpcdec3 \
libncurses5-dev libogg-dev libopenal-dev libopenal1 libpango1.0-dev libpixman-1-dev \
libpng12-dev libpopt-dev libpthread-stubs0 libpthread-stubs0-dev libpulse-dev \
libpulse-mainloop-glib0 libsdl1.2-dev libslang2-dev libsm-dev libsmbclient-dev \
libspeex-dev libsvga1 libsvga1-dev libsys-hostname-long-perl libsysfs-dev \
libtheora-dev libtwolame-dev libtwolame0 libvorbis-dev libx11-dev libxau-dev \
libxcb-render-util0-dev libxcb-render0-dev libxcb-xlib0-dev libxcb1-dev \
libxcomposite-dev libxcursor-dev libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev \
libxft-dev libxi-dev libxinerama-dev libxrandr-dev libxrender-dev libxt-dev libxv-dev \
libxvidcore4 libxvidcore4-dev libxvmc-dev libxvmc1 libxxf86dga-dev libxxf86vm-dev \
mesa-common-dev po-debconf sharutils x11proto-composite-dev x11proto-core-dev \
x11proto-damage-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev \
x11proto-randr-dev x11proto-render-dev x11proto-video-dev x11proto-xext-dev \
x11proto-xf86dga-dev x11proto-xf86vidmode-dev x11proto-xinerama-dev \
xtrans-dev zlib1g-dev libamrnb-dev libamrwb-dev libschroedinger-dev
```

You can see all the dev files that have been missed in your compile.

> and this is all the things that are disabled when I compile mplayer

```
 Disabled optional drivers:
    Input: vstream radio tv-teletext tv-dshow nemesi cddb cdda smb 
    Codecs: libschroedinger libdirac xvid libdv libamr_wb libamr_nb faac musepack libdca libtheora speex toolame twolame libmad liblzo gif 
    Audio output: sun alsa openal jack pulse nas esd arts ivtv dxr2 sdl 
    Video output: zr zr2 ivtv dxr3 dxr2 sdl vesa gif89a jpeg png svga caca aa ggi xmga mga xvidix winvidix opengl 3dfx dga xvmc xv x11 dfbmga directfb bl xvr100 tdfx_vid wii s3fb tdfxfb 
```

yup they're not installing.

Yes, you have missed out on basic stuff like xv and x11 video. What you should see on configure is:

```
  Enabled optional drivers:
    Input: dvdnav(internal) ftp pvr tv-teletext tv-v4l2 tv-v4l tv live555 cddb cdda libdvdcss(internal) dvdread(internal) vcd dvb smb network 
    Codecs: libschroedinger x264 xvid libdv libamr_wb libamr_nb libavcodec(internal) qtx real xanim win32 faad2(internal) faac musepack libdca libmpeg2(internal) liba52(internal) mp3lib(internal) libtheora speex tremor(internal) twolame libmad liblzo gif 
    Audio output: alsa openal jack pulse nas esd arts oss v4l2 sdl mpegpes(dvb) 
    Video output: v4l2 dxr3 sdl gif89a pnm jpeg png mpegpes(dvb) fbdev svga caca aa ggi xvidix cvidix opengl dga xv x11 xover dfbmga directfb yuv4mpeg md5sum tga 

  Disabled optional drivers:
    Input: vstream radio tv-dshow nemesi 
    Codecs: libdirac toolame 
    Audio output: sun ivtv dxr2 
    Video output: zr zr2 ivtv dxr2 vesa xmga mga winvidix 3dfx xvmc bl xvr100 tdfx_vid wii s3fb tdfxfb 
```

If you can get these dev files installed you should be right.

All the best,

Andrew

---

### Post by mocha on 2009-01-26
andrew,

Do you know of any way to search for changes in each svn revision?  [http://svn.mplayerhq.hu/mplayer/trunk/]("http://svn.mplayerhq.hu/mplayer/trunk/") doesn't seem to be searchable even with Google.

---

### Post by phenest on 2009-01-26
Excellent! Worked fine for me first time. Except for 2 minor things:

1. 3 packages I couldn't install:
libglide2 libamrnb-dev libamrwb-dev (are they important?)

2. The x264 package wouldn't install because I already had libx264-dev installed which I using for compiling svn's of Avidemux. Probably doesn't matter either way

Any chance you can remove those $ signs from your code sections. Then the whole code section can be copied and pasted into a terminal instead of one line at a time. Just a thought.

Also, why has Canonical got the out dated version 1.0rc2 in the repos? Why has no one replaced it with a later version. It does need replacing, badly.

---

### Post by andrew.46 on 2009-01-27
Hi mocha,

> **mocha said:**
> Do you know of any way to search for changes in each svn revision?  [http://svn.mplayerhq.hu/mplayer/trunk/]("http://svn.mplayerhq.hu/mplayer/trunk/") doesn't seem to be searchable even with Google.

Unfortunately I am not aware of any other way for the newer revisions that ploughing through that address. If you know the specific file that has changed you can of course see the revision history for that file. For example changes to libdvdcss.h can be seen:

[http://svn.mplayerhq.hu/mplayer/trunk/libdvdcss/libdvdcss.h?view=log](http://svn.mplayerhq.hu/mplayer/trunk/libdvdcss/libdvdcss.h?view=log)

Andrew

---

### Post by andrew.46 on 2009-01-27
Hi phenest,

> **phenest said:**
> Excellent! Worked fine for me first time. Except for 2 minor things:

1. 3 packages I couldn't install:
libglide2 libamrnb-dev libamrwb-dev (are they important?)

These packages are for playback and encoding of amr sound which can be found in some mobile phones. Should not be a big drama if you do not actually wish it but it simply means that you do not have the Medibuntu repository enabled.

> 2. The x264 package wouldn't install because I already had libx264-dev installed which I using for compiling svn's of Avidemux. Probably doesn't matter either way

I have a deep suspicion that when compiling Avidemux a newer x264 library would be an advantage and this is the one in the x264 git repository. But my knowledge of Avidemux is zero :-). Actually you are a little lucky there as compilation of MPlayer usually fails in the presence of the Ubuntu x264 ... It is a good point to remember that the git x264 libraries are really only for *encoding*, decoding comes from the pieces of FFmpeg that MPlayer borrows.

> Any chance you can remove those $ signs from your code sections. Then the whole code section can be copied and pasted into a terminal instead of one line at a time. Just a thought.

There are 2 reasons I use these. Firstly to illustrate a seperate comman and secondly it is an old habit from another Linux distro I use that differentiates a command for an ordinary user as '$' and root as '#'. Not relevant to Ubuntu so much as a root account is discouraged. I will thinl about this one for the next version of this guide.

> Also, why has Canonical got the out dated version 1.0rc2 in the repos? Why has no one replaced it with a later version. It does need replacing, badly.

Not only outdated but partly crippled and split up as well :-). Debian / Ubuntu will not ship a full, recent version for 2 reasons, as I understand it,:

[LIST=1]
[*]There is a perceived potential legal problem with some of the codecs
[*]A 'release' version is preferred, despite MPlayer rarely producing such a version.
[/LIST]

All the best,

Andrew

---

### Post by mocha on 2009-01-27
I was hoping to to able to search the svn changes because I just purchased a new video card that supports VDPAU H264 decoding using the GPU, so I'm kind of getting excited about support in mplayer for it.  I was going to wait to upgrade until it is mainstreamed into the svn versions.

---

### Post by Pitboss on 2009-02-14
Thank you for your topic. Now I really enjoy playing movies, and I like smplayer very much.

EDIT: I have a question. I think that this is a problem with the new fglrx driver but anyway, every 5 minutes mplayer, respectively the smplayer freezes for a second or two and continues normally. I don't know neither what causes this nor how to fix it. So I'll appreciate any help, because it's pretty annoying.

---

### Post by psychok9 on 2009-02-16
**libglide2** now is named **libglide3** on intrepid repository :)

ATM I can't access to [http://svn.mplayerhq.hu](http://svn.mplayerhq.hu), I hope come back soon... :o

---

### Post by andrew.46 on 2009-02-17
Hi Pitboss,

> **Pitboss said:**
> I have a question. I think that this is a problem with the new fglrx driver but anyway, every 5 minutes mplayer, respectively the smplayer freezes for a second or two and continues normally. I don't know neither what causes this nor how to fix it. So I'll appreciate any help, because it's pretty annoying.

Hmmm.... my knowledge of this driver is absolutely zero unfortunately. It might be handy to be running with the -v option when this happens (verbose). But does this freeze happen with other applications?

Andrew

---

### Post by andrew.46 on 2009-02-17
Hi psychok9,

> **psychok9 said:**
> **libglide2** now is named **libglide3** on intrepid repository :)

Curse this renegade libglide demon that is always popping up :-).


> ATM I can't access to [http://svn.mplayerhq.hu](http://svn.mplayerhq.hu), I hope come back soon... :o

It is working at the moment for me. Should be busy soon with the new version due very shortly.

Andrew

---

### Post by psychok9 on 2009-02-17
Thank you :)
Now it work.
I've tried to compile mplayer for use with/in SMPlayer, but I've discovered that have a "in" stand alone mplayer (28403).
Can I compile smplayer and mplayer for use together with last svn and custom version?

Thank you again ;)

---

### Post by andrew.46 on 2009-02-18
Hi psychok9,

> **psychok9 said:**
> I've tried to compile mplayer for use with/in SMPlayer, but I've discovered that have a "in" stand alone mplayer (28403).
Can I compile smplayer and mplayer for use together with last svn and custom version?

I have no idea :-). SMplayer will tell you which version of MPlayer it is actually using in Help ---> About ----> Info. I suspect that yu would be better to have only one version of MPlayer on your system unless there is a special reason?

Andrew

---

### Post by psychok9 on 2009-02-18
Very strange.
I've many problems with vdpau enabled, but with it disabled I've similar problems:
```
nvironment/libBasicUsageEnvironment.a                     -lncurses -lsmbclient -lpng -lz -lmng -lz -ljpeg -lungif -lasound -ldl -lpthread -lcdda_interface -lcdda_paranoia -lfreetype -lz -lfontconfig  -L/usr/lib -lfribidi -lenca -lz -llzo2 -lmad -lspeex -ltheora -logg   -ldts -lmpcdec  -lstdc++ -lamrnb -lamrwb -ldv -lxvidcore -lm -lschroedinger-1.0 -lpthread -loil-0.3 -lm -lrt   -lpthread -ldl -rdynamic -L/usr/lib -L/usr/lib -L/usr/lib  -lm   
libavcodec/libavcodec.a(fft.o): In function `ff_fft_init':
fft.c:(.text.unlikely+0x2b7): undefined reference to `ff_imdct_calc_3dn2'
fft.c:(.text.unlikely+0x2bf): undefined reference to `ff_imdct_half_3dn2'
fft.c:(.text.unlikely+0x2c7): undefined reference to `ff_fft_calc_3dn2'
fft.c:(.text.unlikely+0x2e1): undefined reference to `ff_imdct_calc_3dn'
fft.c:(.text.unlikely+0x2e9): undefined reference to `ff_imdct_half_3dn'
fft.c:(.text.unlikely+0x2f1): undefined reference to `ff_fft_calc_3dn'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1

```
:cry: :cry:
I'm posting on nVidia forums for vdpau problems, but this seem to be a problem with mplayer source/ubuntu compiler.
The vdpau problem spawn also in a virtual jaunty fresh machine.

---

### Post by andrew.46 on 2009-02-18
Hi psychok9,

> **psychok9 said:**
> Very strange.
I've many problems with vdpau enabled, but with it disabled I've similar problems:
[...]
I'm posting on nVidia forums for vdpau problems, but this seem to be a problem with mplayer source/ubuntu compiler.
The vdpau problem spawn also in a virtual jaunty fresh machine.

Unfortunately the svn MPlayer is temporarily broken:

[http://lists.mplayerhq.hu/pipermail/mplayer-users/2009-February/075993.html](http://lists.mplayerhq.hu/pipermail/mplayer-users/2009-February/075993.html)

Best advice is to wait a day or so. If you are keen you can regress libavcodec and libavformat but that has always seemed to much like hard work to me :-).

Andrew

---

### Post by andrew.46 on 2009-02-19
Hi,

Things have settle a little although I believe the release has been pushed back a little so could be more instability to come. The following version compiled or me:

```

andrew@skamandros~$ mplayer | head -n 1
MPlayer SVN-r28672-4.2.4 (C) 2000-2009 MPlayer Team

```

Andrew

---

### Post by mc4man on 2009-02-20
Things seem to have been squared up as far as building on ubuntu, at least with r28672.
The other issue that had arisen in r286xx (*at least here in 8.10*) is having Xvmc enabled would break the compile. 
Again that seems to have been resolved by having that option moved from auto detect to disabled so having libxvmc-dev installed isn't an issue. (if it was going to be

---

### Post by yther on 2009-02-20
I built r28672 last night without problems.  I only tested on three videos to make sure it worked, but it did just fine!  Then I got adventurous and decided to try building the latest VDPAU-enabled patch from NVIDIA... ha, ha, it blew up while the patch script was running.  :P  Oh well, no big deal.

Thanks, Andrew, for this little guide... and BTW, **libglide2** has been replaced with **libglide3**, resulting in an error if folks just paste your stuff in.  I don't have a 3DFX card so I don't care, but some might.  ;)  Also, in your live555 section, you download one file but the next line has them extracting a different one.  Again, no big deal because I have a few brain cells and tab-completion.  Too bad **checkinstall** doesn't work for that package so things could be tidier.

I think I'll go and remove my other media players now!

---

### Post by andrew.46 on 2009-02-20
Hi yther,

> **yther said:**
> I built r28672 last night without problems.  I only tested on three videos to make sure it worked, but it did just fine!  Then I got adventurous and decided to try building the latest VDPAU-enabled patch from NVIDIA... ha, ha, it blew up while the patch script was running.  :P  Oh well, no big deal.

I am pretty sure vdpau will eventually come 'out of the box' with MPlayer and this should ease the pain somewhat :-).

> Thanks, Andrew, for this little guide... and BTW, **libglide2** has been replaced with **libglide3**, resulting in an error if folks just paste your stuff in.  I don't have a 3DFX card so I don't care, but some might.  ;) 

This is pulled in as part of another package so I have removed libglide completely and left the Debian rules to sort it out.

> Also, in your live555 section, you download one file but the next line has them extracting a different one.  Again, no big deal because I have a few brain cells and tab-completion.  Too bad **checkinstall** doesn't work for that package so things could be tidier

That was me doing a half-arsed job changing the links a while back :-). Thanks for noticing and posting this. I have shifted to the so-called 'latest' version as this link will always work. Probably this installation could be scripted and tidied up a little...

> I think I'll go and remove my other media players now!

Well don't be too hasty! I also run the latest vlc if only for testing  some files that don't seem to run all that well with MPlayer. Mind you what is really missing from these forums is a decent guide to compiling the latest vlc, it is quite a difficult one and I have only managed to compile it on another linux distro.

All the best,

Andrew

---

### Post by yther on 2009-02-21
> **andrew.46 said:**
> I am pretty sure vdpau will eventually come 'out of the box' with MPlayer and this should ease the pain somewhat :-).

...

Well don't be too hasty! I also run the latest vlc if only for testing  some files that don't seem to run all that well with MPlayer. Mind you what is really missing from these forums is a decent guide to compiling the latest vlc, it is quite a difficult one and I have only managed to compile it on another linux distro.

Sometimes figuring out how to get stuff to build is fun, but tonight I decided not to bother with the experimental patches and whatnot.  I grabbed the VDPAU-enabled **mplayer** from the repository of a certain "[JYA]("http://www.avenard.org/media/Home.html")," updated my video drivers and restarted, and I now have perfect video at the expense of fancy desktop effects.  >_<  Oh well, the only person I was impressing with those was myself.  I'd rather have clear video with no tearing than wobbly windows.

(To anyone reading this for informational purposes, the tearing only happens on my DVI monitor.  On the other one that uses an analog signal, it looks fine, so if you are not using a digital video cable you probably don't have to worry about this *particular* issue.)

:KS  I am glad NVIDIA is (finally) bringing this technology to us Linux users, and I hope that one day soon they will even manage to get this stuff to play nicely with X11 compositing.  :KS

---

### Post by rvm4000 on 2009-02-21
There's a interesing news in the [mplayer homepage](http://www.mplayerhq.hu/design7/news.html):

> 
2009-02-20, Friday :: Video Acceleration and You 
posted by Compn 

There are several ways to speed up the playback of 1080 H.264 files in MPlayer. 

First is to use the newly added VDPAU output. It allows the newer NVidia video cards to decode the video without using much CPU. It is in SVN MPlayer, you can find known bugs and report bugs HERE. (Linux only) 

Second is to use MPlayer with the experimental multithreaded FFmpeg-mt branch, which allows you to use multiple cores/CPU. (all OS and CPU supported) 

To Install, copy and paste this line:
git clone git://repo.or.cz/mplayer && cd mplayer && git checkout origin/mt && git submodule init && git submodule update && ./configure && make && make install 
To enable threading run mplayer -lavdopts threads=N file.mkv where N is the number of threads you want to use. 

A Windows build of MPlayer using FFmpeg-mt can be found at [http://kovensky.project357.com](http://kovensky.project357.com). 

Third is to use the multithreaded CoreAVC codec with the CoreAVC-for-linux project. The CoreAVC decoder costs $15 USD. (Linux (and Windows with this PATCH)) 

FFmpeg has also added some optimizations from the x264 project. To fully utilize these you will need to make sure a recent version of YASM is installed and detected by the latest SVN MPlayer when compiling. 
Using -lavdopts skiploopfilter=all:fast=1 will cause artifacts, but may allow you to play larger files in realtime. 

There is also a rejected PATCH which adds support for the new multithreaded binary VC-1/WMV3 codec.

---

### Post by andrew.46 on 2009-02-21
Hi,

It is indeed a very exciting time to be around MPlayer, even if only as an end-user, more exciting I suspect if you are involved in the development of such software as SMPlayer :-).

I hope that any future versions of this guide, and I suspect that this Intrepid version may be *my* last, will attempt to incorporate some of these newer strategies for h264 playback. Perhaps also directions for the installation of *newer* versions of SMPlayer, for creating the html docs in multi-page and single page, for scripting updates to x264 and MPlayer, fine-tuning the installation of the Live555 libraries, creation of formal Debian packages etc etc. 

Very exciting times!

Andrew

---

### Post by Nullack on 2009-02-21
Andrew any news on the Jaunty dependencies?

Currently Im using the build dep defaults.

Perhaps if you could please explain what your mods are?

Also I note that youve got the 32bit codecs in your install which AFAIK doesnt work on 64bit platforms.

---

### Post by andrew.46 on 2009-02-21
Hi Nullack,

Well I will admit that I am still tossing up my future with this guide. Courtesy of a small push from a colleague on these forums I am experimenting with VirtualBox to run Ubuntu and possibly continue this guide. I am torn a little both ways, Ubuntu is not my primary distro...

I suspect however that the dependencies will not change that much. I have had a quick look at the Jaunty files and there is some good and some not so good. The x264 library has been updated but it would be better to continue with the git 264, not the least because this fits in with the FFmpeg + x264 guide on these forums. The Live555 libraries remain a little old and would be better placed from upstream as before. If you are running build-dep you do not read libdvdcss / libdvdread / libdvdnav as the svn MPlayer comes with these.

If all works out and I can organise myself (and get VirtualBox running properly!) I would be thinking of writing the Jaunty guide with the release of the beta. Unless of course someone beats me to it, I do not have a monopoly on the subject :-). 

I don't run 64 bit so I guess the guide reflects this, I have no plans for incorporating a section for 64 I'm afraid. As for modifications it is all a little primitive I am afraid :-). I usually run build-dep to see what the Ubuntu dev people use and pick out the ones I want. Apps like x264 and Live555 I know I need to install from upstream so this is done. Medibuntu is added in as they keep the amr dev libraries. If there is a particular type of media file I want MPlayer to be able to play I run:

```
$ apt-cache search mymedia | grep dev
```

download the file and run configure again. This has to be done on a clean, freshly installed system though otherwise Mlayer will pick up the cruft on a busy system. Then test and test again. I keep an ear on MPlayer-users and MPlayer-dev-eng for updates and an ear on problems with MPlayer on these forums. See how easy it all is :-)

Andrew

**Edit:** VirtualBox all sorted, not the easiest piece of software to compile and set up! Screenshot attached for anybody interested, host is Slackware.

---

### Post by Nullack on 2009-02-22
Many thanks Andrew

All the 64bit Ubuntu changes that are needed is to download the AMD64 linux codecs instead of the 32 bit package your guide calls for. That wouldnt be a big change to your guide :)

I went with build-dep defaults and then added the NVIDIA vdpau dev package to ensure I can go with vdpau output. I then needed to tweak the codecs to use:

ffvc1vdpau
ffwmv3vdpau
ffh264vdpau

On anoher topic the one thing I dont like about the smplayer front end is how it remembers the videos played in a database - is it possible to turn this off so it has no memory of what has been played in the past?

---

### Post by andrew.46 on 2009-02-22
Hi Nullack,

> **Nullack said:**
> 
All the 64bit Ubuntu changes that are needed is to download the AMD64 linux codecs instead of the 32 bit package your guide calls for. That wouldnt be a big change to your guide :)

But I guess I really only write up what I have knowledge of and can test as well. If questions were asked specific to 64bit MPlayer I would have no answers and no real method to test. The guide of course is meant to only be a start and a guide, not the full picture by any means.

> I went with build-dep defaults and then added the NVIDIA vdpau dev package to ensure I can go with vdpau output. I then needed to tweak the codecs to use:

ffvc1vdpau
ffwmv3vdpau
ffh264vdpau

In the midst of all the vdpau excitement I sometimes wish I had more than one of those Intel Integrated Graphics Controllers on my computer :-).

> On anoher topic the one thing I dont like about the smplayer front end is how it remembers the videos played in a database - is it possible to turn this off so it has no memory of what has been played in the past?

I have had a look and unfortunately I cannot see an option for this, but I will admit that I am no SMPlayer expert. RVM?

Andrew

---

### Post by rvm4000 on 2009-02-22
> **Nullack said:**
> On anoher topic the one thing I dont like about the smplayer front end is how it remembers the videos played in a database - is it possible to turn this off so it has no memory of what has been played in the past?

Disable the option "Remember settings for all files" (Preferences -> General). 

Or if you don't want the "Recents files" menu to appear, go to Preferences -> Interface and set max. items for recent files to 0.

---

### Post by Nullack on 2009-02-22
Thanks

---

### Post by Nullack on 2009-02-24
Andrew about the 64bit codec thing, I understand your position :) Why not simply have a caveat its for 32bit, and perhaps link to my previous post, as I know it works having a 64bit Jaunty install myself :)

---

### Post by andrew.46 on 2009-02-24
Hi Nullack,

> **Nullack said:**
> Andrew about the 64bit codec thing, I understand your position :) Why not simply have a caveat its for 32bit, and perhaps link to my previous post, as I know it works having a 64bit Jaunty install myself :)

I shall make the appropriate note in the next incarnation of this guide, if all goes well!

Andrew

---

### Post by Nullack on 2009-02-24
This is going really great for me. VDPAU is buggy, but it has so much promise! Ive been doing some bug reports to NVIDIA on issues with it. Can I suggest the next time you ammend the guide Andrew to consider some possible questions and answers in the guide? Like, helping users understand why this is done, its benefits etcetc.

Say perhaps something like:

Q: Whats wrong with the default ubuntu movie player?

A: The default Totem movie player, together with the default gstreamer backend are conveniently separated into different codec categories that allows distributors to easily comply with multimedia legal issues. Totem with the gstreamer backend has a more advanced architecture than mplayer, which provides great potential.

The present reality is though that there are problems, such as:

* Lacking robust gstreamer DVD navigation
* No gstreamer based GPU acceleration
* Lacking video capabilities such as an advanced gstreamer deinterlace filter

Q: Why should I use mplayer?

A: Mplayer uses a static library to ffmpeg, which uses the famous libavcodec library to provide a huge library of different decoders and demuxers that are well regarded for robustness.

Mplayer has advanced video out capabilities, which allows various output methods to be chosen including GPU accelerated output.

Q: Why should I compile my own mplayer?

A: The mplayer build process uniquely optimises the resulting binaries for your specific system. It will be compiled using specific compiler optimisations unique to you. It gives you the very best performance possible.

Mplayer and the statically linked ffmpeg libraries are fast moving projects that tend not to conduct releases on a regular basis. Having the latest SVN build, and keeping up to date regularly, is the best way to ensure you have the latest fixes and enhancements. The developers strive to maintain a buildable SVN codebase.

---

### Post by andrew.46 on 2009-02-25
Hi Nullack,

> **Nullack said:**
> Can I suggest the next time you ammend the guide Andrew to consider some possible questions and answers in the guide? Like, helping users understand why this is done, its benefits etcetc.

My aim in presenting this guide on these forums is simply to give another option for those looking for decent multimedia playback under Ubuntu. I prefer to leave it to the individual to decide the benefits or otherwise of the material presented and also leave them to explore other media players under their *own* guidance. Just presenting one choice, there are others... 

Still waiting for a decent guide to compiling an svn vlc to appear on these forums!

Andrew

---

### Post by Nullack on 2009-02-25
Nvidias new 180.35 driver,,,,,,drum roll,,,,,now features amongst other things:

VDPAU now supports VC-1/WMV acceleration on all GPUs supported by VDPAU

Yay :popcorn:

---

### Post by jeremyjjbrown on 2009-02-26
Thanks for the great info on compiling svn Mplayer. I was able to install and use Mplayer according to directions. I was hoping it would solve my problem.

I've used a win XP version of Mplayer to play HD .mkv's for several years with very few issues. But I have been unable to get Ubuntu to play HD .mkv's on the same hardware with viewable performance. The playback is stuttery, even in 720p. Switching Mplayer to x11 overlay helps greatly but the picture is still not smooth. Any ideas on what to do would be greatly appreciated.

---

### Post by andrew.46 on 2009-02-26
Hi jeremyjjbrown,

> **jeremyjjbrown said:**
> Thanks for the great info on compiling svn Mplayer. I was able to install and use Mplayer according to directions. I was hoping it would solve my problem.

Glad to hear that the guide ran smoothly for you :-).

> I've used a win XP version of Mplayer to play HD .mkv's for several years with very few issues. But I have been unable to get Ubuntu to play HD .mkv's on the same hardware with viewable performance. The playback is stuttery, even in 720p. Switching Mplayer to x11 overlay helps greatly but the picture is still not smooth. Any ideas on what to do would be greatly appreciated.

It would be interesting to see what was actually in these mkv files. The problem you describe sounds like h264 video. Are you keen enough to try the FakeOutdoorsman's [HOWTO: Install and use the latest FFmpeg and x264]("http://ubuntuforums.org/showthread.php?t=786095")? This will give you a cutting edge FFmpeg that you can run:

```
ffmpeg -i myfile.mkv
```

to properly identify the streams as well as give you software that can easily manipulate the files to make them a little more playable.

Conventionally the '-framedrop' option is also used with MPlayer as a shorter term solution. Try:

```
mplayer -framedrop myfile.mkv
```

and see if this makes any difference?

Andrew

---

### Post by jeremyjjbrown on 2009-02-26
Hi Andrew,

Thanks for your reply.

The files I am using are .h264 ~1500 Kbps 1280x720 in a .mkv container. I have almost a TB of video that runs great on my XP HTPC. I don't think I need to re-encode it, or have the time to do that. But thanks for the FFmpeg link. That will be a huge help if I can complete my switch to Ubuntu.

I tried:

```
mplayer -framedrop myfile.mkv
```

I lost vsnyc almost completely. I am honestly shocked at this. I can play flawless 720p .mkv on a Pentium 4 in XP with a crap-tastic ATI x300 after a 30 second install. Ubuntu can't handle it on a 2.4 core duo with a x1600.

Any other ideas would be appreciated.

---

### Post by rvm4000 on 2009-02-26
> **jeremyjjbrown said:**
> I lost vsnyc almost completely. I am honestly shocked at this. I can play flawless 720p .mkv on a Pentium 4 in XP with a crap-tastic ATI x300 after a 30 second install. Ubuntu can't handle it on a 2.4 core duo with a x1600.

There are several ways to try to improve performance.

First be sure you use xv as video output, it's the fastest.

mplayer -vo xv ...

You can also try the option *-lavdopts skiploopfilter=all* although that could decrease image quality.

Another possibility is to compile mplayer with the experimental multithreaded FFmpeg, as explained [here](http://www.mplayerhq.hu/design7/news.html).

---

### Post by andrew.46 on 2009-02-27
Hi jeremyjjbrown,

> **jeremyjjbrown said:**
> 
I tried:
```
mplayer -framedrop myfile.mkv
```
I lost vsnyc almost completely. I am honestly shocked at this. I can play flawless 720p .mkv on a Pentium 4 in XP with a crap-tastic ATI x300 after a 30 second install. Ubuntu can't handle it on a 2.4 core duo with a x1600.

I suspect that my advice to you is a good example of why I should not post to these forums while doing night shift :-). The framedrop option is actually more properly intended to skip frames to help maintain sync on slower systems:

> 
 -framedrop  (also  see  -hardframedrop,  experimental  without  -nocorrect-pts)
              Skip displaying some frames to maintain A/V sync  on  slow  sys-
              tems.   Video  filters  are  not applied to such frames.  For B-
              frames even decoding is skipped completely.


Maybe I should stick a little 'night-shift' icon next to such posts :-). RVM's advice is much more solid.

Andrew

---

### Post by jeremyjjbrown on 2009-02-27
> **andrew.46 said:**
> 

I suspect that my advice to you is a good example of why I should not post to these forums while doing night shift :-). 

Andrew

No worries. I'm looking at this whole things as a learning experience. So far I've mucked up xorg.conf twice and as a result learned to use the shell command line and nano to undo my improprieties. 

As I should have suspected x264, mplayer and vlc player are not the cause of the video flicks and tears, neither is Ubuntu. It is an incompatibility between fglrx and compix-fusion. If I turn off all visual affects the video issues are abated, and the picture is fantastic. Too bad, I like compiz and I have all radeon video cards. I'm willing to bet if fglrx was open source I wouldn't be fighting this problem.

Thanks again for the advice!

---

### Post by ajunsum on 2009-03-09
great! thanks!!

---

### Post by Antioch on 2009-03-14
Andrew. Your guide worked well. I was compiling this new version of mplayer to get access to working vc-1 (wvc-1) decoders, and the compiled version of mplayer runs them fine.

I installed smplayer as you suggested, but this old smplayer doesnt seem to "map" to the new mplayer. I can run "mplayer file.name" at the command line and it works fine, but trying to play the file in smplayer results in it not knowing the codec (the same behavior as for the stock intrepid mplayer build).

How can I fix this?

---

### Post by rvm4000 on 2009-03-14
In Preferences -> General there's an option to select the mplayer executable (in case you have two mplayers installed on different paths).

---

### Post by EnSeNiX on 2009-04-19
I'm have errors during compiling mplayer.it's keep on giving me this errors.can anyone help me out?
thanks you
By the way i'm using Jaunty.

make: *** No rule to make target `libavformat/*/*.[chS]', needed by `libavformat/libavformat.a'.  Stop.

---

### Post by andrew.46 on 2009-04-19
Hi EnSeNix,

> **EnSeNiX said:**
> I'm have errors during compiling mplayer.it's keep on giving me this errors.can anyone help me out?
thanks you
By the way i'm using Jaunty.

make: *** No rule to make target `libavformat/*/*.[chS]', needed by `libavformat/libavformat.a'.  Stop.

Unfortunately at the moment compilation is broken. The best strategy is to wait a day or so and try again. BTW if you are using Jaunty there is a newer guide:

HowTo: Install the very latest MPlayer under Jaunty Jackalope 
[http://ubuntuforums.org/showthread.php?t=1081070](http://ubuntuforums.org/showthread.php?t=1081070)

All the best,

Andrew

---

### Post by mc4man on 2009-04-20
Maybe it's a jaunty thing (or gcc 4.3.3 ?), builds fine on 8.10
> doug@doug-desktop:~$ mplayer
MPlayer SVN-r29204-4.3.2 (C) 2000-2009 MPlayer Team

Was actually looking more at the wmapro patch and some build inconsistencies involving it and happened to use the latest svn instead of a -r

---

### Post by andrew.46 on 2009-04-20
Hi mc4man,

> **mc4man said:**
> Maybe it's a jaunty thing (or gcc 4.3.3 ?), builds fine on 8.10

```
doug@doug-desktop:~$ mplayer
MPlayer SVN-r29204-4.3.2 (C) 2000-2009 MPlayer Team 
```



Good to 'see' you again :-). To tell the truth the few revisions before 29204 failed for me on a non-Ubuntu distro as well. Back on track now with this revision though.

Andrew

---

### Post by mc4man on 2009-04-20
For any of the intrepid amd_64 users that want to enable wma3 (pro) on their mplayer build there is a link to the patch in the jaunty thread

[http://ubuntuforums.org/showthread.php?t=1081070&page=10](http://ubuntuforums.org/showthread.php?t=1081070&page=10)  (94)

It may or may not cause the build to fail, but does work perfectly.

(( While I don't have 64 bit install, a week ago  as a favor to a couple of people  I built two 64 bit patched mplayer packages using a live 64 bit cd. They built and work perfectly.
Then while considering switching to 64 bit a day ago I attempted to build a more suitable package for my hardware and it failed miserably while building wma3dec.0 (wma3dec.c))

Long story short I still can't figure why it built right a week ago and is a bit of a problem now.
Anyway I 'problem solved' a solution but probably there is a *proper* fix. (if indeed this isn't just a local issue.
If anyone needs a "workaround' will gladly share my 'solution'

So while i was at it i built a patched ffmpeg itself, though i can't see any real advantage/use there yet.

Interesting how it handles it though (32 bit install

> doug@doug-desktop:~/Desktop/ff3/wmapro/ffmpeg$ ./ffplay ~/wma3.wma
FFplay version SVN-r18617, Copyright (c) 2003-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid --enable-libvorbis
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.27. 0 / 52.27. 0
  libavformat   52.32. 0 / 52.32. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 18 2009 22:02:43, gcc: 4.3.2
[wmapro @ 0xa667ba0][18] [0] [3] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [e0] [0] [0] [0] 
[wmapro @ 0xa667ba0] ed sample bit depth = 16
[wmapro @ 0xa667ba0] ed decode flags = e0
[wmapro @ 0xa667ba0] samples per frame = 2048
[wmapro @ 0xa667ba0] log2 frame size = 18
[wmapro @ 0xa667ba0] max num subframes = 16
[wmapro @ 0xa667ba0] len prefix = 1
[wmapro @ 0xa667ba0] num channels = 2
[wmapro @ 0xa667ba0] lossless = 0


And mplayer (32 bit here but as mentioned works great on 64 bit install

doug@doug-desktop:~$ mplayer  1.wmv -channels 6
MPlayer SVN-r29188-4.3.2 (C) 2000-2009 MPlayer Team
Playing 1.wmv.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [WMV3]  640x384  24bpp  1000.000 fps  1240.0 kbps (151.4 kbyte/s)
==========================================================================
Opening video decoder: [dmo] DMO video codecs
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
Decoder supports the following formats: YV12 YUY2 UYVY YVYU RGB8 RGB555 RGB565 RGB24 RGB32 
Decoder is capable of YUV output (flags 0x1b)
VDec: vo config request - 640 x 384 (preferred colorspace: Packed YUY2)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 640x384 => 640x384 Planar YV12 
Selected video codec: [wmv9dmo] vfm: dmo (Windows Media Video 9 DMO)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
[wmapro @ 0x9ddb220][18] [0] [3f] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [e0] [0] [0] [0] 
[wmapro @ 0x9ddb220] ed sample bit depth = 16
[wmapro @ 0x9ddb220] ed decode flags = e0
[wmapro @ 0x9ddb220] samples per frame = 2048
[wmapro @ 0x9ddb220] log2 frame size = 17
[wmapro @ 0x9ddb220] max num subframes = 16
[wmapro @ 0x9ddb220] len prefix = 1
[wmapro @ 0x9ddb220] num channels = 6
[wmapro @ 0x9ddb220] lossless = 0
AUDIO: 48000 Hz, 6 ch, s16le, 254.5 kbit/5.52% (ratio: 31809->576000)
Selected audio codec: [ffwmapro] afm: ffmpeg (FFmpeg WMA Pro audio)
======================================================================

Edit: easy 'fix' here
[http://ubuntuforums.org/showthread.php?p=7123598#post7123598](http://ubuntuforums.org/showthread.php?p=7123598#post7123598)

or open to suggestions

---

### Post by Jive Turkey on 2009-05-01
Thanks, that worked great for me.  I did it on Jaunty x64, there were acouple of packages not found by apt but I adapted by instead running:```
sudo apt-get install em8300-headers gawk gettext html2text intltool-debian \
ladspa-sdk libaa1-dev libasound2-dev libatk1.0-dev libaudio-dev \
libaudio2 libaudiofile-dev libavahi-client-dev libavahi-common-dev libcaca-dev \
libcairo2-dev libcdparanoia0-dev libcucul-dev libdbus-1-dev libdbus-glib-1-dev \
libdirectfb-dev libdirectfb-extra libdts-dev libdv4-dev libenca-dev libenca0 \
libesd0-dev libexpat1-dev libfaac-dev libfaac0 libfontconfig1-dev libfreebob0 \
libfreetype6-dev libfribidi-dev libggi-target-x libggi2 libggi2-dev libggimisc2 \
libggimisc2-dev libgif-dev libgii1 libgii1-dev libgii1-target-x libgl1-mesa-dev \
libglu1-mesa-dev libglu1-xorg-dev libgtk2.0-dev libice-dev libschroedinger-dev \
libjack-dev libjack0 libjpeg62-dev liblzo-dev liblzo1 liblzo2-2 liblzo2-dev libmad0 \
libmad0-dev libmail-sendmail-perl libmp3lame-dev libmp3lame0 libmpcdec-dev libmpcdec3 \
libncurses5-dev libogg-dev libopenal-dev libopenal1 libpango1.0-dev libpixman-1-dev \
libpng12-dev libpopt-dev libpthread-stubs0 libpthread-stubs0-dev libpulse-dev \
libpulse-mainloop-glib0 libsdl1.2-dev libslang2-dev libsm-dev libsmbclient-dev \
libspeex-dev libsvga1 libsvga1-dev libsys-hostname-long-perl libsysfs-dev \
libtheora-dev libtwolame-dev libtwolame0 libvorbis-dev libx11-dev libxau-dev \
libxcb-render-util0-dev libxcb-render0-dev libxcb1-dev \
libxcomposite-dev libxcursor-dev libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev \
libxft-dev libxi-dev libxinerama-dev libxrandr-dev libxrender-dev libxt-dev libxv-dev \
libxvidcore4 libxvidcore4-dev libxvmc-dev libxvmc1 libxxf86dga-dev libxxf86vm-dev \
mesa-common-dev po-debconf sharutils x11proto-composite-dev x11proto-core-dev \
x11proto-damage-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev \
x11proto-randr-dev x11proto-render-dev x11proto-video-dev x11proto-xext-dev \
x11proto-xf86dga-dev x11proto-xf86vidmode-dev x11proto-xinerama-dev \
xtrans-dev zlib1g-dev libamrnb-dev libamrwb-dev libstdc++5
```

I dont recall which ones I had to omit, sorry.  Then I ran:```
sudo apt-get build-dep mplayer
``` just to be safe and it pulled down a few more.

---

### Post by andrew.46 on 2009-05-01
Hi Jive Turkey,

Glad you you got it all running. Mind you it would have perhaps been a little easier on you if you had followed the [Jaunty version of this guide]("http://ubuntuforums.org/showthread.php?t=1081070") :-).

All the best,

Andrew

---

### Post by andrew.46 on 2009-05-14
Hi,

Perhaps some who have gone to the trouble of installing the svn MPlayer might be interested in a new guide I have written:

Top 10 Tricks and Tips for the svn MPlayer
[http://ubuntuforums.org/showthread.php?t=1154431](http://ubuntuforums.org/showthread.php?t=1154431)

I would be very happy to receive some feedback on this new page, I always consider any guide I write a 'work in progress' often steered along by user feedback :-).

All the best,

Andrew

---

### Post by jfca283 on 2009-05-20
thanks 
it works now and was easy to build...

---

### Post by andrew.46 on 2009-05-21
Hi jfca283,

> **jfca283 said:**
> thanks 
it works now and was easy to build...

It is my pleasure! I wish you all the best with this great software.

Andrew

---

### Post by ticket on 2009-05-25
As a nervous user, I am wondering what the effect would be on other packages when installing mplayer, using the package method described in this excellent thread.

I am on Intrepid 8.1

What would happen if Ubuntu released new mplayer package(s)?  Do they replace the ones installed by this guide, or are they automatically blocked somehow?  If they are blocked, won't this stop the upgrade of other dependent packages? (e.g I use the firefox mplayer plug-in - which mplayer will it use?)

I have managed to compile mplayer (and ffpmeg) inside my home directory and manually substituted the built binaries (mplayer, ffmpeg, ffplay, ffstream) into /usr/bin.  This seems to work, but I wonder what the effect is of not also substituting the new .so libraries into /usr/lib.

I guess I can replace the binaries (and libs) in /usr/bin (and /usr/lib) by building using the configure option  --prefix=/usr  and using "sudo make install"  I thought this would cause the least interference with the Ubuntu package system, as no package is changed.  But could this break other apps that rely on using older libs? (say OpenMovieEditor?)  Clearly if I did this, the changes would be undone by an official package upgrade, but then I could decide if the upgrade was worth keeping. If not, it's simply another "sudo make install" to overwrite the package upgrade.

So, is it safe to build mplayer & ffmpeg using the non-package way (sudo make install) - will it cause problems for other installed apps, and will firefox mplayer plug-in get to work with the new mplayer?

If I use the package method, what are the issues with that?

Golly, so many questions ...

---

### Post by andrew.46 on 2009-05-26
Hi ticket,

> **ticket said:**
> As a nervous user, I am wondering what the effect would be on other packages when installing mplayer, using the package method described in this excellent thread.

For the most part I have attempted to bring the installation close to the Ubuntu package management system although a closer approach to this would be the creation of a Debian package, but I am not such a great fan of Debian packages so I suspect this will not happen :-). Some have reported problems with MEncoder in particular but I believe there is no such problem with MPlayer itself. The x264 issue is a bit of a pain though...


> What would happen if Ubuntu released new mplayer package(s)?  Do they replace the ones installed by this guide, or are they automatically blocked somehow?  If they are blocked, won't this stop the upgrade of other dependent packages? (e.g I use the firefox mplayer plug-in - which mplayer will it use?)

With the naming convention that I have used a new Ubuntu version of MPlayer would *not* register as a new version on your system. However I believe that Ubuntu / Debian are *very* unlikely to release a new version in the near future and the subversion MPlayer will *always* be more modern than any repository version.


> I have managed to compile mplayer (and ffpmeg) inside my home directory and manually substituted the built binaries (mplayer, ffmpeg, ffplay, ffstream) into /usr/bin.  This seems to work, but I wonder what the effect is of not also substituting the new .so libraries into /usr/lib.

I guess I can replace the binaries (and libs) in /usr/bin (and /usr/lib) by building using the configure option  --prefix=/usr  and using "sudo make install"  I thought this would cause the least interference with the Ubuntu package system, as no package is changed.  But could this break other apps that rely on using older libs? (say OpenMovieEditor?)  Clearly if I did this, the changes would be undone by an official package upgrade, but then I could decide if the upgrade was worth keeping. If not, it's simply another "sudo make install" to overwrite the package upgrade.

Quite frankly most of these ideas sound like too much work to me :-). I suspect you would be best to either allow an installation to /usr/local and experiment a little to see if other software is happy with this.

> So, is it safe to build mplayer & ffmpeg using the non-package way (sudo make install) - will it cause problems for other installed apps, and will firefox mplayer plug-in get to work with the new mplayer?

If I use the package method, what are the issues with that?

I believe that it is always better to integrate with the package management system. If you are a little concerned I would recommend you try the proper [Debian package of MPlayer put together by RVM]("https://launchpad.net/~rvm/+archive/mplayer") and this would integrate more tightly with the rest of your system.

Hope this helps?

Andrew

---

### Post by ticket on 2009-05-26
Thanks Andrew!

> With the naming convention that I have used a new Ubuntu version of MPlayer would not register as a new version on your system.

To clarify, what would happen if Ubuntu did a release?  Would the release not appear at all in Synaptic? If it did appear, what would stop it overwriting an installation?

> I believe that it is always better to integrate with the package management system.

I tend to agree, but maybe the slowness in the Ubuntu package updates is just to ensure that it doesn't break any other installed apps? 

I'm still learning here, so is it the case that a proper deb package would install binaries and .so's and that removing it would restore the bins and .so's that were overwritten?  

If so, that is an important difference between an install via 

"./configure --prefix=/usr  ..." and 
"./configure --prefix=/usr/local ..."  (the default)

So using --prefix=/usr, I assume I would not be able to sensibly undo the install. I presume a "make clean" would simply delete the binaries and .so's, requiring the user to reinstall the relevant packages.  Have I understood this right?  

The reason for my caution is I once tried installing a deb package from the Avenard repo (for latest nVidia drivers) but when trying to remove it, it messed up a few items (mplayer went, for example). I was able to recover, though, by re-doing some installs.

On another subject, I recall reading on one of these forums that someone managed to get smooth replay of 1280 x 720 h264 video on a 1.3GHz machine. That's really impressive - I have a 1.5GHz dell with a PCI 6200 but at that resolution, although I get a smooth playback, it is in s-l-o-w motion - so the sound quickly goes out of sync. This was using a fresh mplayer build (but I didn't do a build of the x264). Wish I knew how that poster managed to get that performance.

---

### Post by andrew.46 on 2009-05-26
Hi ticket,

> **ticket said:**
> 
To clarify, what would happen if Ubuntu did a release?  Would the release not appear at all in Synaptic? If it did appear, what would stop it overwriting an installation?

If Ubuntu did a release I suspect that the naming system used would still allow the svn MPlayer installed by this guide to be seen as a 'newer' version. In this guide this is seen in the checkinstall syntax '--pkgversion "3:1.0~svn-......'. If the Ubuntu devs changed the naming cnvention radically there is a possibility that the svn MPlayer package rom this guide would be overwritten. But it is my self-appointed role to keep an eye out for this sort of event :-).

> [..] maybe the slowness in the Ubuntu package updates is just to ensure that it doesn't break any other installed apps? 

In general yes but MPlayer is a special case, hence this guide. MPlayer release versions are few and far between, the last *official* version was released in 2007 and this is the one served up to Ubuntu users. There are moves afoot at MPlayer to release another version soon (rc3) but there is no guarantee that Karmic Koala will pick this up in time and certainly no guarantee that backports will make it to Intrepid.

> I'm still learning here, so is it the case that a proper deb package would install binaries and .so's and that removing it would restore the bins and .so's that were overwritten?  

If so, that is an important difference between an install via 

"./configure --prefix=/usr  ..." and 
"./configure --prefix=/usr/local ..."  (the default)

Unfortunately I am not entirely clear on that one as my knowledge of real debian packages is more than a little limited.

> ...I presume a "make clean" would simply delete the binaries and .so's, requiring the user to reinstall the relevant packages.  Have I understood this right?  

Not quite, 'make clean' simple cleans up some aspects of the source code tree itself and has no effect on actual 'installation'. You do not use the following logical step in the chain which is 'sudo make install'? I noted this before when you described manually placing files after compilation. MPlayer has the ability to run 'sudo make uninstall' from the source code tree if you decide not to use checkinstall / deb.

> The reason for my caution is I once tried installing a deb package from the Avenard repo (for latest nVidia drivers) but when trying to remove it, it messed up a few items (mplayer went, for example). I was able to recover, though, by re-doing some installs.

I understand your caution completely :-).


> On another subject, I recall reading on one of these forums that someone managed to get smooth replay of 1280 x 720 h264 video on a 1.3GHz machine. That's really impressive - I have a 1.5GHz dell with a PCI 6200 but at that resolution, although I get a smooth playback, it is in s-l-o-w motion - so the sound quickly goes out of sync. This was using a fresh mplayer build (but I didn't do a build of the x264). Wish I knew how that poster managed to get that performance.

You do not need to build x264 if you only wish to playback h264 videos as FFmpeg has native decoders, x264 allows encoding with MEncoder. I suspect that when I write a guide for Karmic and the svn MPLayer x264 compilation + Mencoder will not feature at all. Playback of h264 in this way sounds like a version of MPLayer with vdpau capabilities and a decent NVidia card. I do not cover this in my guide but there are others that do:

HOWTO: Nvidia Driver + VDPAU + Smplayer +Mplayer
[http://ubuntuforums.org/showthread.php?t=1037625](http://ubuntuforums.org/showthread.php?t=1037625)

All the best,

Andrew

---

### Post by mc4man on 2009-05-26
> I'm still learning here, so is it the case that a proper deb package would install binaries and .so's and that removing it would restore the bins and .so's that were overwritten?


Maybe this can clear that up a bit for you.
While there is absolutely no great reason to do so I almost always build mplayer as a 'proper' debian package set. (mplayer, mencoder, docs

If I wanted to install a new. higher versioned deb than I'd just click on it and the package manager would install it. (over current

If I wanted to use a lesser versioned  deb than I'd have to remove the current mplayer package first, (thru synaptic or apt-get), then install the older .deb

Removing a package does only that - remove, it doesn't 'restore' the previous one or a repo one from your sources.

Whether you install to /usr or /usr/local doesn't make much difference, you should though avoid having the same app installed to both. ( I'm 99% sure that /usr/local takes preference over /usr, so while it's possible to have installs of same app in both, seems like poor practice

---

### Post by ticket on 2009-05-29
> **mc4man said:**
> 
Whether you install to /usr or /usr/local doesn't make much difference, you should though avoid having the same app installed to both. ( I'm 99% sure that /usr/local takes preference over /usr, so while it's possible to have installs of same app in both, seems like poor practice

I think there must be some difference. In my installation, /usr/lib is crammed with stuff, whereas /usr/local/lib is nearly empty (it has just got the frei0r video effects plug-ins). 

Seems official packages install into /usr/lib and /usr/bin, while manually built packages are usually configured to install into /usr/local/lib  and /usr/local/bin.  Currently, my /usr/local/bin is empty.   

So if people compile and make install using /usr/local, does that install a binary into /usr/local/bin? 

Presumably /usr/local/bin is in the search path for running binaries, so is /usr/bin or /usr/local/bin searched first?

Apologies if all this simply amounts to a re-statement of what you posted!

---

### Post by mocha on 2009-05-29
/usr/local/bin always has higher priority.  I tend to compile a lot of stuff on my ubuntu systems that isn't available in the repo or very old or buggy versions are in the repos.  You don't have to make deb packages or worry about uninstalling the repo version.  Just configure and install stuff into /usr/local and you're good.  If you question where an executable is being run from just do a "which xxxx" and it will give you the path to the executable.  Ubuntu's package manager can continue updating the repo version of a package to it's heart's content, it won't touch your /usr/local install.  For example, I do this with packages such as ffmpeg, mplayer/mencoder, ntfs-3g, mythtv, and so forth.  I also have the repo version of some of these packages installed as well only because they are dependancies of other programs.  I only need to rebuild my stuff when there are major kernel updates or distro updates.

---

### Post by ticket on 2009-05-30
I just tried installing the deb packages from the rvm ppa repository.  I only did this as it included debs for the newer nVidia drivers (185.12)

It all works, but I hit a snag. The mozilla-mplayer plug-in for firefox is no longer working properly (either no video, or can only get it by going to full screen).  

Is it the case that the mozilla plug-in package is statically built using older mplayer versions?   What about the newer gnome-mplayer-plugin? (I think I meant gecko-mediaplayer)

Anyway, does anyone know what is the best way of getting firefox plugins to use the latest mplayer technology?

Do I have to build my own plug-in?

---

### Post by andrew.46 on 2009-05-30
Hi ticket,

> **ticket said:**
> I just tried installing the deb packages from the rvm ppa repository.  I only did this as it included debs for the newer nVidia drivers (185.12)

You might be better to start a new thread for this as I am sure that rvm will enthusiastically support his PPA. But hopefully he will see your post here anyway :-).

> It all works, but I hit a snag. The mozilla-mplayer plug-in for firefox is no longer working properly (either no video, or can only get it by going to full screen).  

Is it the case that the mozilla plug-in package is statically built using older mplayer versions?   What about the newer gnome-mplayer-plugin? (I think I meant gecko-mediaplayer)

I use the mozilla plugin with no problem but I will admit to doing this on *another* distro so I cannot absolutely guarantee this with ubuntu. The gecko-mediaplayer I have not used but with any luck someone else on this thread can advise.

Sorry to be of so little help,

Andrew

---

### Post by ticket on 2009-05-30
Well, I removed mozilla-mplayer and installed gecko-mediaplayer.  Now any video I play through firefox appears in the player window as a tiny icon-sized video in the top left hand corner.  The rest of the player window is black.  Sound comes through ok.

I then tried manually replacing the rvm-installed mplayer binary in /usr/bin with the various mplayer binaries I had lying around (the one I built via this guide, and the original unbuntu deb) but this made no difference - behaviour was the same,  

Used on their own, the mplayer binaries are ok. Except that the rvm one sometimes needed prodding with the space bar to get going.

I am fairly sure I had the gecko-mediaplayer working in the past, so I think it is an issue with the way things have been installed. Whatever is upsetting mozilla-mplayer is probably also upsetting gecko-media player.

EDIT: I have found that gnome-mplayer has exactly the same symptoms as gecko-mediaplayer, so the problem is nothing to do with firefox plug-ins, but the way mplayer has integrated with gnome.

Could it be that I have ffmpeg installed in /usr/local/bin and /usr/bin?
(as already pointed out, the ffmpeg I built in /usr/local/bin should take preference if it is used).

The only other thing changed is the nVidia driver.

Maybe custom repos weren't such a good idea, and classic "./configure. make, sudo make install" are better?

---

### Post by andrew.46 on 2009-05-31
Hi ticket,

I would suggest clearing your system of *all* the Mplayer related files and starting from scratch :-). I suspect you may have a variety of installations in place as well as configuration files and a clean start might be the best bet.

I would recommend rvm's package as it is closely integrated with Ubuntu and he plans on keeping this package up to date while I am wavering on future plans for this guide.

All the best,

Andrew

---

### Post by rvm4000 on 2009-05-31
I don't know if it's related or not to the problem that *ticket* is having, but I installed ubuntu 9.04 a couple of days ago in virtualbox (I'm still using kubuntu 8.04 in my machine) and realized that mplayer freezes if using alsa. It works ok with oss or pulse. (It also works ok with alsa if pulseaudio is removed).

So I'd suggest *ticket* to edit ~/.mplayer/config and change the audio output to see if that makes any difference.
```

ao=oss

```

---

### Post by ticket on 2009-06-05
Thanks Andrew & rvm for the suggestions.

Here's what I ended up doing:
I un-installed all of the packages that were installed from the rvm repo.  This also took out mplayer, some mplayer dependencies (like tovid) and the nVidia driver packages. 

I then disabled the rvm repo and installed the 180 nVidia drivers from the standard Ubuntu repos.  However, the drivers were not showing up in the Hardware Drivers menu, so fingers crossed I did a reboot and all was well - the standard 180 drivers were installed.

I then re-built the mplayer app from svn, and did a "sudo make install" rather than create a deb package.  The mplayer and gmplayer binaries duely appeared in /usr/local/bin and they worked fine.  

Now I wanted to install mozilla-mplayer in order to get firefox to use mplayer for embedded videos. So I installed mozilla-mplayer as a deb package from the standard repos. This of course pulled in the stock mplayer as well - but not to worry, the mplayer in /usr/local/bin still takes preference.  

Unfortunately the mozilla-mplayer has problems.  I have been testing it on the Apple Trailers website [http://www.apple.com/trailers/](http://www.apple.com/trailers/)
This has lots of nice embedded movs.  When trying to view these, the mplayer plug-in appears, does some buffering then stops. I am left with a grey rectangle. Sometimes, by right-clicking on the grey rectangle and selecting full-screen, I can get a perfect full screen playback of the movie, so it can work if prodded the right way. Returning from full screen, the movie continues to play, but the gui controls are gone. 

Similar things happen with other streaming web sites. Clearly something is not right with the gui integration. I tried substituting the /usr/local/bin mplayer with the old original ubuntu mplayer and couldn't get the movie to play at all. This is all so weird.  I may have to go back to using the totem mozilla plug-in if I can't get the mplayer one to work.  

I'll have a go later at using the gecko one, to see if that's any better.
Btw, using oss makes no difference. I am also using vo=xv.

My mplayer build config options were:
--enable-gui --enable-menu --enable-xvmc --disable-smbfile

I have attached the configure.log if it helps. But I suspect the problem isn't with mplayer, but with some other system / gnome configuration issue.

---

### Post by andrew.46 on 2009-06-05
Hi ticket,

I have no solution for some of the things you mention so forgive me if I just place a few comments :-).

> **ticket said:**
> 
I un-installed all of the packages that were installed from the rvm repo.  This also took out mplayer, some mplayer dependencies (like tovid) and the nVidia driver packages. 

I then disabled the rvm repo and installed the 180 nVidia drivers from the standard Ubuntu repos.  However, the drivers were not showing up in the Hardware Drivers menu, so fingers crossed I did a reboot and all was well - the standard 180 drivers were installed.

In a sign that I am far removed from the frontline of technology I have to admit that my computer does not have an NVidia card so I have never had to tussle with these drivers and their setup, in particular with seting MPlayer with vdpau. I would not underestimate the value of RVM's package however as it is maintained pretty close to the cutting edge of the svn MPlayer, I believe it is tracking svn rc3 at the moment? Not sure about this one...

> I then re-built the mplayer app from svn, and did a "sudo make install" rather than create a deb package.  The mplayer and gmplayer binaries duely appeared in /usr/local/bin and they worked fine. 

If I were you I would not put too much faith in the gmplayer as development has been abandoned and last time I used it there were many mysterious error messages. I believe the standard message from the MPlayer devs is to use a 3rd party frontend rather than the gmplayer. I am at heart a CLI sort of guy but I certainly believe if you wish to use a gui SMPlayer is the way to go.
 
> Now I wanted to install mozilla-mplayer in order to get firefox to use mplayer for embedded videos. So I installed mozilla-mplayer as a deb package from the standard repos. This of course pulled in the stock mplayer as well - but not to worry, the mplayer in /usr/local/bin still takes preference.  

Unfortunately the mozilla-mplayer has problems.  I have been testing it on the Apple Trailers website [http://www.apple.com/trailers/](http://www.apple.com/trailers/)
This has lots of nice embedded movs.  When trying to view these, the mplayer plug-in appears, does some buffering then stops. I am left with a grey rectangle. Sometimes, by right-clicking on the grey rectangle and selecting full-screen, I can get a perfect full screen playback of the movie, so it can work if prodded the right way. Returning from full screen, the movie continues to play, but the gui controls are gone.

There are a few things that I am not entirely keen about with Ubuntu and one is the package management / dependency tracking system which can often be such a PITA if you wan to do something a little different. Buried deep in this rambling message where nobody will read it I can tell you that my primary distro is Slackware and these dependency problems simply *do not exist* there. I have attached a screenshot that shows one of the Apple trailers running flawlessly with the svn MPlayer under slackware 12.2 and the plugin: it *can* be done :-).

Anyway sorry I have no definitive answer here, just a fair bit of rambling! I still suspect that the best combination for you will be rvm's PPA MPlayer + SMPlayer but it sounds like you have the capabilities to thrash out a decent solution that will work for you and your own setup :-).

All the best,

Andrew

---

### Post by rvm4000 on 2009-06-06
It works for me too in kubuntu hardy, using mplayer 2:1.0~rc3svn29325 and mozilla-mplayer 3.50-1ubuntu2.1.

[[img]http://f.imagehost.org/t/0020/trailer2.jpg[/img]](http://f.imagehost.org/view/0020/trailer2)

Although most of the trailers in that page ask me to install the quicktime plugin.

[[img]http://f.imagehost.org/t/0777/trailer3.jpg[/img]](http://f.imagehost.org/view/0777/trailer3)

:confused:

I also tested on ubuntu 9.04 and things are more complicated. Firefox uses totem-plugin for those videos, if I uninstall it, then firefox segfaults when trying to play any of those videos. And konqueror uses kmplayer to play the videos, I don't know how to change it...

---

### Post by ticket on 2009-06-06
Andrew, thanks for the hints.  Your mozilla-mplayer clearly works fine in your flavour of Unix!  I know I used to be able to do this with the standard packages in Ubuntu, but as we know, they couldn't play all possible streams, hence the need to build mplayer from svn.  

My nVidia card (6200) doesn't support vdpau, which is a pity because that is the way to offload all of the video work onto the graphics card and should allow playback of HD videos with low cpu usage.

):P rvm, you need to install the package mozilla-mplayer to stop the apple trailer site from saying you need a quicktime plug-in. [edit: it may also be how your firefox prefs are set - checkout firefox:Edit->Preferences] [edit2: I also have the package libquicktime1 installed] I found it best to only install one flavour of mozilla media player plugin.  Others (not a complete list) are:
  gecko-mediaplayer
  totem-mozilla
  mozilla-plugin-vlc
These fight amongst themselves to play video streams, so for now only install mozilla-mplayer and uninstall any others.

I'd be interested to see how you get on!

---

### Post by ticket on 2009-06-06
On a whim, I cleaned and re-built mplayer, this time omitting the --enable-gui option.   Alas, I get exactly the same behaviour as before with mozilla-mplayer.

Can't seem to trace this problem down.  Maybe try gecko-mplayer next.

---

### Post by ticket on 2009-06-06
Good news at last. 
 
I removed mozilla-mplayer and installed gecko-mediaplayer  (gecko-mediaplayer uses gnome-mplayer and mplayer). 

Now everything works (see screen shot). :popcorn:
I am not using any custom deb packages - just stuff installed into /usr/local/bin and /usr/local/lib

I can't explain why mozilla-mplayer had such problems - maybe it just doesn't get along with ubuntu and newer mplayer builds.  Also, I can't explain why gecko-mediaplayer didn't get on with rvm's repo.

I had also compiled and installed a new version of gnome-mplayer from source, upgrading ubuntu's version 0.7.0 to 0.9.5.  I am fairly sure this wasn't what helped though.

This has been a good learning experience, thanks to Andrew and the  posters on this forum. Here is what I have learned:

1. 
You can install software by compiling from source, using:
./configure <options>
make
sudo make install

2.
The configure options can be listed using: 
./configure --help

3. 
You can remove the installation using:
sudo make uninstall

4.
By default, using the above, the binaries and libs are stored in usr/local/bin and usr/local/lib.  These directories take precedence over /usr/bin and /usr/lib, which are the places where the stock Unbuntu packages ultimately install their stuff.

5. 
If a new ubuntu deb comes out promising the earth, simply install it as normal.  To make it active, just do a "sudo make uninstall" to remove the custom binaries. If the deb doesn't deliver, do a "sudo make install" and you're set to go again.

It is interesting what Andrew says about Slackware.  I had a quick look at it, but it is too 'raw' for me - I like the gui stuff too much!  I am not sure how it manages software dependencies any better than other distributions - maybe by better quality control?

---

### Post by andrew.46 on 2009-06-06
Hi ticket,

God to see that you have got things sorted out!

> **ticket said:**
> It is interesting what Andrew says about Slackware.  I had a quick look at it, but it is too 'raw' for me - I like the gui stuff too much!  I am not sure how it manages software dependencies any better than other distributions - maybe by better quality control?

Just a moment of frustration speaking out there, I am still enjoying Ubuntu and will for a long time to come :-). Slackware does not manage dependencies at all, this is left to the user to control. It is a system that works well, simply requires a little research before installing software.

All the best,

Andrew

---

### Post by andrew.46 on 2009-07-11
Hi,

Looks like support for the external, non-free amr libraries has been removed from libavcodec so for the moment there will be no amr playback for MPlayer. Consequently I have removed the amr / Medibuntu sections of the guide.

FFmpeg now features support for opencore-amr so hopefully support for this will be added to MPlayer soon. When this happens I shall add the details to this guide.

All the best,

Andrew

---

### Post by brandon88tube on 2009-07-13
Not to be a jerk or anything, but can't you just make a deb package or something as I really don't have to time to do all of this. I need a quick way I don't really have to think all that much.

---

### Post by andrew.46 on 2009-07-14
Hi brandon,

> **brandon88tube said:**
> Not to be a jerk or anything, but can't you just make a deb package or something as I really don't have to time to do all of this. I need a quick way I don't really have to think all that much.

That is a fair question. The short answer is that others have already done this work:

[https://launchpad.net/~rvm/+archive/ppa](https://launchpad.net/~rvm/+archive/ppa)

All the best,

Andrew

---

### Post by jfca283 on 2009-09-01
if i have the last nvidia drivers, how do i get mplayer-svn with vdpau support in order to watch h264 files?
i'm used to compile mplayer-svn with this how-to...
do i need another dev library?
thanks

---

### Post by andrew.46 on 2009-09-01
Hi jfca283,

> **jfca283 said:**
> if i have the last nvidia drivers, how do i get mplayer-svn with vdpau support in order to watch h264 files?
i'm used to compile mplayer-svn with this how-to...
do i need another dev library?

vdpau is one of the reasons I am getting out of the svn MPlayer business :-). Unfortunately I know next to nothing about it, for the most part because I do not have the hardware to test it. There are a couple of threads that might help, the first that comes to mind is this one:

HOWTO: Nvidia Driver + VDPAU + Smplayer +Mplayer
[http://ubuntuforums.org/showthread.php?t=1037625](http://ubuntuforums.org/showthread.php?t=1037625)

Bear in mind that the MPlayer you have compiled from this guide *will* playback h264 files, all vdpau is about is offloading much of the processing onto an appropriate nvidia graphics card.

All the best,

Andrew

---

### Post by jfca283 on 2009-09-01
oh...
i don't know
i find the method mention by you a little bit complicated
your way is so simple
thanks

---

### Post by andrew.46 on 2009-09-02
Hi jfca,

> **jfca283 said:**
> 
i find the method mention by you a little bit complicated
your way is so simple

My apologies but my knowledge of vdpau is almost nonexistent :(. But this certainly looks promising:

Nvidia Vdpau Team PPA
[https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)

Andrew

---

### Post by jfca283 on 2009-09-13
i have one doubt...
i saw a howto on this forum using
ffmpg-mit or something like that wich enabled multheading...
your tutorial includes that?

---

### Post by andrew.46 on 2009-09-13
Hi jfca283,

> **jfca283 said:**
> i saw a howto on this forum using ffmpg-mit or something like that wich enabled multheading... your tutorial includes that?

There are several recent advances with MPlayer that I do* not *cover in this guide including FFmpeg-MT, Core-AVC and vdpau. I believe that all of these have decent guides elsewhere on these forums so you have a choice to make :).

Andrew

---

### Post by andrew.46 on 2009-09-14
I have added in a small section that details how the new libopencore-amr libraries can be added to allow playback of files with amr sound. Please let me know if there are any problems...

Andrew

---

### Post by helpdeskdan on 2009-10-10
Ah, nuts!  Any suggestions?  Any help greatly appreciated.  

make[1]: Entering directory `/home/dan/mplayer/libavformat'
make[1]: *** No rule to make target `rtp_internal.h', needed by `allformats.o'.  Stop.
make[1]: Leaving directory `/home/dan/mplayer/libavformat'
make: *** [libavformat/libavformat.a] Error 2
dan@dan-desktop:~/mplayer$

---

### Post by andrew.46 on 2009-10-10
Hi helpdesk,

> **helpdeskdan said:**
> Ah, nuts!  Any suggestions?  Any help greatly appreciated.

Try the following:
```

$ cd /home/dan/mplayer
$ make distclean
$ svn up
```

and then recompile starting from *./configure*. Hopefully this will get you restarted :).

Andrew

---

### Post by helpdeskdan on 2009-10-10
Thank you kindly for your reply!  I didn't know you had Jaunty instructions.  They look about the same. 

I found you had another page here for jaunty:
[http://ubuntuforums.org/showthread.php?t=1081070](http://ubuntuforums.org/showthread.php?t=1081070)

I made distclean on everything (x264 and amr weren't working) and removed my current x264 libraries which were not letting me install.   This seems to have worked, Thanks!  On to mplayer-plugin!

---

### Post by andrew.46 on 2009-10-10
Hi helpdesk,

> **helpdeskdan said:**
> I made distclean on everything (x264 and amr weren't working) and removed my current x264 libraries which were not letting me install.   This seems to have worked, Thanks!  On to mplayer-plugin!

Great news! I have corrected a small issue with libopencore-amr by adding *--prefix=/usr* to the ./configure string as a default Ubuntu installation sometimes has problems with libraries in /usr/local.

All the best,

Andrew

---

### Post by helpdeskdan on 2009-10-11
Thank you very much, Andrew!  You're continual guidance is huge help to those of us who continually battle with dependency and compile problems!

---

### Post by andrew.46 on 2009-10-12
Hi helpdeskdan,

> **helpdeskdan said:**
> Thank you very much, Andrew!  You're continual guidance is huge help to those of us who continually battle with dependency and compile problems!

It is my pleasure :). 

Andrew

---

### Post by andrew.46 on 2009-11-10
Hi,

Not sure how many Intrepid users are still around but I have updated this guide to include the release version of the amr libraries anyway :).

Andrew

---

### Post by FakeOutdoorsman on 2009-11-11
> **andrew.46 said:**
> Hi,

Not sure how many Intrepid users are still around but I have updated this guide to include the release version of the amr libraries anyway :).

Andrew

I pointed this guide out to someone on #ffmpeg today.  Still useful!

---

### Post by lisati on 2010-05-05
Thread "retired" (closed) at request of OP

---

