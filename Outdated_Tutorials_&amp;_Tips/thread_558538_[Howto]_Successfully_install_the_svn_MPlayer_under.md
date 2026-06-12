---
title: "[Howto] Successfully install the svn MPlayer under Hardy Heron"
date: 2007-09-24
forum: Outdated Tutorials &amp; Tips
---

### Post by andrew.46 on 2007-09-24
This guide shows how to successfully compile a *fully featured* svn MPlayer and MEncoder with *all* of the codecs and with the Graphical User Interface (GUI) SMPlayer. It is designed to work with Ubuntu Hardy Heron LTS and will be supported by myself until the 'end-of-life' of Hardy in April 2011 courtesy of my new best friend VirtualBox.  

==========================================
** Some 'External' Libraries ... **
===========================================

There are a few libraries that are important to have installed *before* compiling the svn MPlayer and I give the details here for installing x264, Live555 and libopencore-amr:

-----------------
**x264 ...**
-----------------

The MPlayer developers advise that current x264 sources should be used with the svn MPlayer and details follow for compiling both a of yasm newer than that found in the Ubuntu repository and the git x264. But first to assemble some compiling software and a few vital utilities:

```

$ sudo apt-get install build-essential checkinstall subversion git-core

```

and then to install yasm which is required for optimising the x264 build:

```

$ cd $HOME
$ wget http://www.tortall.net/projects/yasm/releases/yasm-0.8.0.tar.gz
$ tar xzvf yasm-0.80.tar.gz
$ cd yasm-0.8.0
$ ./configure
$ make
$ sudo checkinstall -D --pkgname=yasm --fstrans=no --pakdir "$HOME/Desktop" \
--maintainer "$USER" --pkgversion "0.8.0" --backup=no \
--deldoc=yes --deldesc=yes --delspec=yes --default
$ make distclean

```

and now to install the x264 libraries from git:

```

$ sudo apt-get purge x264 libx264-dev
$ cd $HOME
$ git clone git://git.videolan.org/x264.git
$ cd x264
$ ./configure --prefix=/usr --enable-shared
$ make
$ sudo checkinstall -D --pkgname=x264 --fstrans=no --pakdir "$HOME/Desktop" \
--maintainer "$USER" --pkgversion "1:0.svn`date +%Y%m%d`-0.0ubuntu1" --backup=no \
--deldoc=yes --deldesc=yes --delspec=yes --default
$ make distclean

```

Next to install the Live555 libraries:

-------------------
**Live555 ...**
-------------------

Live555 is a vital library if you ever intend to access streaming radio or television broadcasts:

```

$ cd $HOME
$ wget http://www.live555.com/liveMedia/public/live555-latest.tar.gz
$ tar xvf live555-latest.tar.gz
$ cd live
$ ./genMakefiles linux
$ make
$ sudo cp -r $HOME/live /usr/lib
$ make clean

```

This library is updated quite frequently so you may like to return here at some stage and pick up a newer version? Next to install the libopencore-amr libraries:

-------------------
**libopencore-amr ...**
-------------------

These libraries are required to give the svn MPlayer the ability to playback files with amr sound:

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

With this preparation complete it is time now to setup the codecs:

======================
**Set up the Codecs ...**
======================

MPlayer has the ability to use and external library of codecs to playback some media files. Conveniently Medibuntu holds these files and I would suggest that you now read over the following page to understand the implications of utilising this repository which is *not* part of Ubuntu:

Medibuntu - Community Ubuntu Documentation
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

The actual syntax to add the repository (taken directly from the page above) is as follows:

```

sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
 --output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update

```

Once the repository is in place users of a 32bit system will need to run the following:

```
$ sudo apt-get install w32codecs
```

while users of a 64bit system will need to run the following instead:

```
$ sudo apt-get install w64codecs
```

=============================
**Source a Font**
=============================

Mplayer needs to know the location of a TrueType Font to show movie subtitles. (As you probably know this can be activated with the 'j' key.) This can be selected from the commandline but more traditionally a symlink is created to the font of your choice:

```

$ mkdir -v $HOME/.mplayer
$ ln -sv /usr/share/fonts/truetype/ttf-bitstream-vera/Vera.ttf ~/.mplayer/subfont.ttf

```

Feel free to choose your own font but this will certainly do to start with.

====================================
**Download the 'Development' Files**
====================================

By default Ubuntu does not offer a particularly rich development environment so we need to download the required 'dev' files plus a few extra programs. Do not be alarmed if the repository suggests other files as well, or informs you that you already have some of this impressive list. And certainly feel free to add your own!

```

$ sudo apt-get install comerr-dev ladspa-sdk libaa1-dev libarts1c2a libarts1-dev \
libartsc0 libartsc0-dev libasound2-dev libaudio2 libaudio-dev libaudiofile-dev \
libavahi-client-dev libavahi-common-dev libcaca-dev libcairo-directfb2 \
libcairo-directfb2-dev libcdio-dev libcdparanoia0-dev libcucul-dev libcupsys2-dev \
libdbus-1-dev libdirectfb-dev libdirectfb-extra libdts-dev libdv4-dev libenca0 \
libenca-dev libesd0-dev libfaac0 libfaac-dev libfreebob0 libfribidi-dev \
libgcrypt11-dev libggi2 libggi2-dev libggiwmh0 libggiwmh0-dev libgii1 libgii1-dev \
libgii1-target-x libgl1-mesa-dev libglu1-mesa-dev libgnutls-dev libgnutlsxx13 \
libgpg-error-dev libgtk2.0-dev libgtk-directfb-2.0-0 libgtk-directfb-2.0-dev \
libjack0 libjack-dev libjpeg62-dev libkadm55 libkrb5-dev libladspa-ocaml \
libladspa-ocaml-dev liblame0 liblame-dev liblcms1-dev libstdc++5 \
liblzo2-dev libmad0 libmad0-dev libmng-dev libmpcdec3 libamrnb3 libamrwb3 \
libmpcdec-dev libncurses5-dev libogg-dev libopenal-dev libopencdk10-dev \
libpng12-dev libpopt-dev libpulse-browse0 libpulse-dev libpulse-mainloop-glib0 \
libqt3-headers libqt3-mt libqt3-mt-dev libsdl1.2-dev libslang2-dev libsmbclient-dev \
libsmpeg0 libsmpeg-dev libspeex-dev libsvga1 libsvga1-dev libsysfs-dev libtasn1-3-dev \
libtheora-dev libtwolame0 libtwolame-dev libungif4-dev libungif4g libvorbis-dev \
libx11-dev libxcb-shm0 libxcb-shm0-dev libxcb-xv0 \
libxcb-xv0-dev libxcb-xvmc0 libxcb-xvmc0-dev libxext-dev libxi-dev libxinerama-dev \
libxmu-dev libxmu-headers libxss-dev libxt-dev libxv-dev libxvidcore4 libxvidcore4-dev \
libxvmc1 libxvmc-dev libxxf86dga-dev libxxf86vm-dev mesa-common-dev ocaml-base-nox \
ocaml-findlib ocaml-interp ocaml-nox qt3-dev-tools x11proto-core-dev \
x11proto-scrnsaver-dev x11proto-video-dev x11proto-xf86dga-dev \
x11proto-xf86vidmode-dev zlib1g-dev zlib1g-dev

```

=================================
**Download and Compile the svn mplayer**
=================================

Finally after all of the preparation it is time to download MPlayer from the subversion repository:

```

$ cd $HOME
$ svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer
$ cd $HOME/mplayer
$ ./configure --confdir=/etc/mplayer
$ make
$ sudo checkinstall -D --install=yes --fstrans=no --pakdir "$HOME/Desktop" \
--pkgname mplayer --backup=no --deldoc=yes --deldesc=yes --delspec=yes --default \
--pkgversion "3:1.0~svn-`grep "#define VERSION" version.h | cut -d"-" -f2`" \
--provides "mplayer,mencoder"
$ make distclean

```

This of course has only installed the commandline MPlayer, now to install the GUI SMPlayer:

===========================
**Downloading SMPlayer ... **
===========================

The default gui for MPlayer is known as gmplayer and it has been out of development for some time. I personally use the SMPLayer in its place and I would advise that you do the same. The versions of SMplayer in both the main repository and the repository backports are a little dated so I would suggest using a copy from a PPA generously maintained by the developer of SMPlayer. Add the following to your /etc/apt/sources.list:

```

deb http://ppa.launchpad.net/rvm/smplayer/ubuntu hardy main 
deb-src http://ppa.launchpad.net/rvm/smplayer/ubuntu hardy main

```

If you feel that you can trust rvm and his packages, as I do, you can also install the OpenPGP key for this PPA:

```

$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com E4A4F4F4

```

and then simply run:

```

$ sudo apt-get update && sudo apt-get upgrade
$ sudo apt-get install smplayer

```

It is a little bit of futzing around but well worth the trouble taken and you will then be using a version of SMPlayer that will work well with the cutting edge MPlayer.

=============================
**And in conclusion.....**
=============================

And so you have successfully installed the svn MPlayer! You can check the options available for you with the following commands:

[LIST=1]
[*]**mplayer -vo help** : Video output available to mplayer
[*]**mplayer -ao help** : Audio output available to mplayer
[*]**mplayer -vc help** : Available video codecs
[*]**mplayer -ac help** : Available audio codecs 
[*]**mencoder -ovc help** : Video encoding available to mencoder
[*]**mencoder -oac help** : Audio encoding available to mencoder
[/LIST]

Start both from the command line, the player with the command **mplayer** and the movie encoder with **mencoder**. The gui SMPlayer should appear on your menu.  And remember: "Have fun!".

Andrew Strong
November 11th, 2009

---

### Post by tribble222 on 2007-09-26
Thanks for the guide!

When installing all the dev's I had to change the 0.9-22 to 0.9-25 in all cases.  Also it didn't like me doing libglu-dev because it's part of the libglu-mesa-dev metapackage or something.

---

### Post by andrew.46 on 2007-09-26
Hi,

Thanks for the message:

> **tribble222 said:**
> Thanks for the guide!

When installing all the dev's I had to change the 0.9-22 to 0.9-25 in all cases.  Also it didn't like me doing libglu-dev because it's part of the libglu-mesa-dev metapackage or something.

 There is a slight problem with specifying all these dev packages: they vary from one version of ubuntu to another. I am planning on setting up a Gutsy set of dev files and then labelling the walkthough: "Gutsy Gibbon: svn + etc etc"

 Everything else worked out ok though?

                 Andrew

---

### Post by tribble222 on 2007-09-26
> **andrew.46 said:**
> Hi,

 Everything else worked out ok though?



Actually, I'm having a problem compiling it now.  I seem to have some problem with libavformat.

I get:

libavformat/libavformat.a(allformats.o): In function `av_register_all':
allformats.c:(.text+0xf3): undefined reference to `avisynth_demuxer'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1


Edit: I compiled ffmpeg from source and now mplayer compiles great with your instructions

Edit2: But I don't get any video, just greenish stuff...

Edit3: I just had to specify -vo.  Now everything works perfectly!

---

### Post by jrmink on 2007-09-26
Does Not Work With Ubuntu Fiesty Fawn 7

---

### Post by andrew.46 on 2007-09-26
Hi,

 Sorry you had so much trouble,

> **tribble222 said:**
> Actually, I'm having a problem compiling it now.  I seem to have some problem with libavformat.

I get:

libavformat/libavformat.a(allformats.o): In function `av_register_all':
allformats.c:(.text+0xf3): undefined reference to `avisynth_demuxer'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1


Edit: I compiled ffmpeg from source and now mplayer compiles great with your instructions

Edit2: But I don't get any video, just greenish stuff...

Edit3: I just had to specify -vo.  Now everything works perfectly!

 Oddly enough you should not have to compile ffmpeg apart from the svn package, but if it has worked for you ....

 You should have a choice of -vo. Run the following in a terminal:

```
 mplayer -vo help
```

 and all available options will be seen. If you want a default one start up a ~/ .mplayer/config and place it in there.

  ALl the best,

     Andrew

PS I have mplayer running on gutsy, but reasonably extensive changes in the required dev files. I shall change everything when Gutsy is officially released

---

### Post by tribble222 on 2007-09-26
> **andrew.46 said:**
> Hi,

 Sorry you had so much trouble,



 Oddly enough you should not have to compile ffmpeg apart from the svn package, but if it has worked for you ....


Yes, I found out later that ffmpeg compiles with mplayer so I'm not sure how installing ffmpeg helped.

Thanks for the tip with the config file!

---

### Post by andrew.46 on 2007-09-27
Hi,

 Good to see a satisfied customer:

> **tribble222 said:**
> Yes, I found out later that ffmpeg compiles with mplayer so I'm not sure how installing ffmpeg helped.

Thanks for the tip with the config file!

 There is a system one somewhere as well. Search for mplayer.conf which should get you started. I probably should add that to the guide but you really have to stop somewhere :-)

 Beta of the Gutsy version is here:

[http://people.aapt.net.au/~adjlstrong/ftgws.html](http://people.aapt.net.au/~adjlstrong/ftgws.html)

 I have left out checkinstall, jazzed up the directory selection and changed all the devs. The radio business won't be appearing on the forums though :-)

           Andrew

---

### Post by xieu90 on 2007-09-27
how do I know if my computer has GTK or not ?

  Checking for GTK+ version ... GTK-2 devel packages were not found, trying GTK 1.2
Checking for GTK version ... 
Error: The GUI requires GTK devel packages (which were not found).

Check "configure.log" if you do not understand why it failed.



how can I install that one ?

---

### Post by andrew.46 on 2007-09-27
Hi,

Saw your message:

> **xieu90 said:**
> how do I know if my computer has GTK or not ?
  Checking for GTK+ version ... GTK-2 devel packages were not found, trying GTK 1.2
Checking for GTK version ... 
Error: The GUI requires GTK devel packages (which were not found).
Check "configure.log" if you do not understand why it failed.
how can I install that one ?

 Looks like you are missing libgtk2.0-dev which you can install with apt-get.

 A broader issue is a miscalculation that I have made in the differences between *versions *of Ubuntu. What I am working on is a small rewrite of this guide that will target only *one* version: Gutsy Gibbon, This will make installation and troubleshooting easier.

 Really the major difference will be the dev packages. The use of svn, setting up of skins etc will remain unchanged.

                    Andrew

---

### Post by tribble222 on 2007-09-27
> **xieu90 said:**
> how do I know if my computer has GTK or not ?

  Checking for GTK+ version ... GTK-2 devel packages were not found, trying GTK 1.2
Checking for GTK version ... 
Error: The GUI requires GTK devel packages (which were not found).

Check "configure.log" if you do not understand why it failed.



how can I install that one ?

The GTK-2 dev package is called libgtk2.0-dev I believe.  So running "sudo apt-get install libgtk2.0-dev should install it.

---

### Post by tribble222 on 2007-09-27
> **andrew.46 said:**
> Hi,
 A broader issue is a miscalculation that I have made in the differences between *versions *of Ubuntu. What I am working on is a small rewrite of this guide that will target only *one* version: Gutsy Gibbon, This will make installation and troubleshooting easier.

 Really the major difference will be the dev packages. The use of svn, setting up of skins etc will remain unchanged.

                    Andrew

Why not have a list of dev packages for a few versions of Ubuntu?  I can confirm that the following works in Feisty:

```
sudo apt-get install liblame-dev libdvdread3-dev libdvdnav-dev libogg-dev \
libvorbis-dev libxv-dev libtheora-dev libpng12-dev libmpcdec-dev \
libcdparanoia0-dev libxinerama-dev x11proto-xinerama-dev libjpeg62-dev \
libgdk-pixbuf-dev libfreetype6-dev libexpat1-dev libfontconfig1-dev \
libcaca-dev libfaac-dev libmp4v2-dev libaa1-dev libavcodec-dev \
libavifile-0.7-dev libsdl1.2-dev libesd0-dev libfaad2-dev libice-dev \
libmatroska-dev libmad0-dev libmp4v2-dev libmikmod2-dev libpostproc-dev \
libspeex-dev libxvidcore4-dev libxvidcore4 avifile-xvid-plugin \
avifile-divx-plugin ladspa-sdk libsvga1-dev libsvga1 libungif4-dev \
libungif4g libenca-dev libdfb++-0.9-25 libdfb++-dev libdirectfb-0.9-25 \
libdirectfb-dev libavformat-dev libfame-0.9 libfame-dev zlib1g-dev \
liblivemedia-dev libfribidi-dev libdvdnav4 libdvdplay0 libasound2-dev \
libdv4-dev libpopt-dev zlib1g-dev xlibs-dev libflac++-dev libflac-dev \
liboggflac++-dev liboggflac-dev toolame ttf-bitstream-vera \
libdbus-glib-1-dev libx264-dev libggi2-dev libxvmc-dev libxxf86vm-dev \
libxxf86dga-dev libfontconfig-dev libartsc0-dev \
libglu1-mesa-dev libdts-dev libdvdread-dev libdv-dev \
libpng12-dev libsmbclient-dev gawk sharutils libaudiofile-dev liblzo-dev \
libc6-dev libggimisc2 libggimisc2-dev libggiwmh0 libggiwmh0-dev \
libatk1.0-dev libcairo2-dev libgtk2.0-dev libpango1.0-dev \
libxcursor-dev libxfixes-dev x11proto-fixes-dev liba52-0.7.4-dev
```

---

### Post by andrew.46 on 2007-09-28
Hi,

 Thanks for your message:

> **tribble222 said:**
> Why not have a list of dev packages for a few versions of Ubuntu?  I can confirm that the following works in Feisty [...]:

 I guess because my aim was to establish a guide that I could troubleshoot, answer questions on, be reasonably authoritative on and continue to develop. To do this with complex software like mplayer and  with the limited time available to me it would make sense to focus on *one* version of ubuntu.only. And as gusty is coming into its own....

 Mind you as you have posted the dev files that work with Feisty this has now gone on permanent record in these forums and will be a resource for those who use Feisty.

   All the best,

        Andrew

---

### Post by andrew.46 on 2007-09-28
Hi,

 Well hopefully this will not put too many people out but I have changed the guide a little to reflect Gutsy Gibbons needs. Specifically this will mean that the dev files *will need to be adjusted* for Dapper, Edgy and Feisty.

 As I have mentioned before this gives me the chance to focus specifically on one version of the guide rather than troubleshooting a few different versions.

 Sorry if anybody is put out by this. Note that a version of the dev files for Feisty has already been posted in this thread. Plus of course experimentation with different libraris / dev files will alter and extend mplayer's capabilities. I am hoping that this guide will only be a start.

 BTW if you are not familiar with svn I probably should mention that you can open a Terminal window in the directory of the mplayer source code and run:

```
svn update
```

to retrieve updated files from the svn repository rather than download the full thing again. And of course run the command:

```
make clean
```

before reconfiguring. To uninstall mplayer run the following command from the mplayer source code directory,:

```
sudo make uninstall
```

How cool is that!!!

              Andrew

---

### Post by shirilover on 2007-09-29
> **andrew.46 said:**
> 
```
$ tar xjvf all-20061022.tar.bz2
$ sudo mkdir -v /usr/local/lib/codecs
$ sudo cp -v $HOME/Desktop/all-20061022/*.* /usr/local/lib/codecs
```

The above can be shortened to:
```

mkdir -v /usr/local/lib/codecs
sudo tar -xjvf all-20061012.tar.bz2 -C /usr/local/lib/codecs

```

The switch --codecsdir is not needed if you place the codecs in either /usr/lib/codecs or /usr/local/lib/codecs.

I usually compile x264 from svn as well before building mplayer.

If you happen to be using compiz, the patch attached here -> [http://lists.freedesktop.org/archives/compiz/2007-July/002494.html](http://lists.freedesktop.org/archives/compiz/2007-July/002494.html)
will help video playback using -vo xv.

Also, if you would like to create a deb package you can do the following (needs fakeroot and dpkg-dev):
```

cd  /path/to/mplayer-svn/source
DEB_BUILD_OPTIONS="--enable-gui --enable-largefiles --enable-xvmc" fakeroot debian/rules binary

```

---

### Post by andrew.46 on 2007-09-29
Hi,

 Thanks very much for your comments and suggestions:

> **shirilover said:**
> The above can be shortened to:
```
mkdir -v /usr/local/lib/codecs
sudo tar -xjvf all-20061012.tar.bz2 -C /usr/local/lib/codecs
``` 

 I love this and have added it to the guide.

> The switch --codecsdir is not needed if you place the codecs in either /usr/lib/codecs or /usr/local/lib/codecs.

 I have also specified a reasonably redundant --prefix=/usr/local in the configure options. I have been a little overly pedantic to ensure that those who do not have a lot of experience with svn / compiling etc should be very unlikely to come to grief.

> I usually compile x264 from svn as well before building mplayer.

 This sounds fascinating and I will investigate it for my *own* copy of mplayer. I suspect it goes a little beyond this little guide though :-)

> If you happen to be using compiz, the patch attached here -> [http://lists.freedesktop.org/archives/compiz/2007-July/002494.html](http://lists.freedesktop.org/archives/compiz/2007-July/002494.html)
will help video playback using -vo xv.

 Don't use compiz myself and I have a deep-seated suspicion about all eye-candy (retires briefly to put on asbestos suit).

> Also, if you would like to create a deb package you can do the following (needs fakeroot and dpkg-dev):
```
cd  /path/to/mplayer-svn/source
DEB_BUILD_OPTIONS="--enable-gui --enable-largefiles --enable-xvmc" fakeroot debian/rules binary

```

 Thanks for this information and all the other suggestions. I appreciate the time and effort you have put into your post. 

                 Andrew

---

### Post by Gouz on 2007-09-29
Hey all.

I tried to install the mplayer and when I used sudo mkdir -v /usr/local/lib/codecs

I got an out put: mkdir: cannot create directory `/usr/local/lib/codecs': File exists
do you know why?
And yes I have root rights. in case you wander

---

### Post by tribble222 on 2007-09-29
> **Gouz said:**
> Hey all.

I tried to install the mplayer and when I used sudo mkdir -v /usr/local/lib/codecs

I got an out put: mkdir: cannot create directory `/usr/local/lib/codecs': File exists
do you know why?


That's okay -- it existed already for me too.  In my case because I had already installed mplayer before.  Just ignore it and move on to the next step and you'll be fine.

---

### Post by Gouz on 2007-09-29
ok I think I did it, but I can't install a skin, I go confused from the code in the first page cause of the $ and then HOME isnt it /home/ the directory?

---

### Post by tribble222 on 2007-09-29
> **Gouz said:**
> ok I think I did it, but I can't install a skin, I go confused from the code in the first page cause of the $ and then HOME isnt it /home/ the directory?

When you type $home into the terminal it will act as your home directory.  If you login name is gouz, then your home directory is /home/gouz/

---

### Post by Gouz on 2007-09-29
ok what I get from cp -v $HOME/Desktop/Blue/*.* $HOME/.mplayer/skins/default
which as I can understand it is one command (correct me if I am wrong)
is: cp: target `/home/rosi/.mplayer/skins/default' is not a directory (where rosi is my log in name)

And so I can add a skin on the mplayer is it not that what this command does?

---

### Post by andrew.46 on 2007-09-30
Hi,

 Saw you in a bit of a pickle:

> **Gouz said:**
> ok what I get from cp -v $HOME/Desktop/Blue/*.* $HOME/.mplayer/skins/default
which as I can understand it is one command (correct me if I am wrong)
is: cp: target `/home/rosi/.mplayer/skins/default' is not a directory (where rosi is my log in name)

And so I can add a skin on the mplayer is it not that what this command does?

 That is *exactly* what this command does. gmplayer looks in a few places for the default skin and I selected this one for the walkthrough.

 Sounds like the required directory might not be there. Try this:

```
$ cd
$ mkdir -pv .mplayer/skins/default
$ cp -Rv /home/rosi/Desktop/Blue/* /home/rosi/.mplayer/skins/default
```

 And this should copy the contents of the Blue folder into the required directory.

 I use $HOME rather than /home/username so people do not have to remember to substitute 'username' for their *own* username :-)

 Try the following and it will make sense:

```
echo $HOME
```

 All the very best with this, if you are down to the skin you must be almost there!

           Andrew

---

### Post by synd7 on 2007-09-30
Thanks for the guide andrew and also to shirilover for the packaging info.

The only problem is my gmplayer wont start:
```
$ gmplayer
MPlayer dev-SVN-r24673-4.1.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.00GHz (Family: 15, Model: 2, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
/usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf doesn't look like a bitmap font description, ignoring.
Cannot load bitmap font: /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
[skin] file ( /usr/share/mplayer/skins/default/skin ) not found.
Skin not found (default).

```

I've copied the skin data to the folder. Is there any other info that need to go into a config file or something?

---

### Post by andrew.46 on 2007-09-30
Hi,

 Sounds like you are almost there. Just 2 small steps have gone awry:

> **synd7 said:**
> Thanks for the guide andrew and also to shirilover for the packaging info.

The only problem is my gmplayer wont start:
```
 [...]

/usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf doesn't look like a bitmap font description, ignoring.
Cannot load bitmap font: /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
[skin] file ( /usr/share/mplayer/skins/default/skin ) not found.
Skin not found (default).

```

I've copied the skin data to the folder. Is there any other info that need to go into a config file or something?

 You need to get a font configured for the On Screen Display and put the skin where gmplayer can find it. There are many ways to do this but my guide aims to make it straightfoward. Although I seem to have confused you a little :)

**For the OSN Font**

gmplayer needs to have a font specified for subtitles and the on-screen-display. There are several ways to do this, easiest way is to copy a decent font to the ~/.mplayer folder and give it a different name. Try this:


```
$ mkdir -v  $HOME/.mplayer
$ sudo apt-get install ttf-bitstream-vera
$ sudo cp -v /usr/share/fonts/truetype/ttf-bitstream-vera/Vera.ttf ~/.mplayer/subfont.ttf
```

This is a fairly crude way of doing it, a symlink would be better but I am trying to keep a complex subject simple. That should take care of the OSD error.

**For the skin**

gmplayer needs a skin to run and this does not come *with* the package, in fact the GUI is actually looked down at by some. The trick is to create the relevant folders and place a full skin pack in them* in the right location*.

So:

```
$ cd $HOME
$ mkdir -pv .mplayer/skins/default
$ cd $HOME/Desktop
$ wget http://www.mplayerhq.hu/MPlayer/skins/Blue-1.7.tar.bz2
$ tar xjvf Blue-1.7.tar.bz2 
$ cp -Rv $HOME/Desktop/Blue/* $HOME/.mplayer/skins/default
```

 And this should complete your setup. As you explore a bit more you will see that you can have many skins and chose from them, in fact I believe that there is a skin 'browser' in gmplayer.
 All the -v settings are for 'verbose' which should tell you if something is going wrong. Post the errors if there are any and they should be fixable.

 Let me know how you go?

       Andrew

---

### Post by Gouz on 2007-09-30
Hey thanks for the info there were help full and everything worked until the command  gmplayer..

Then I got the following 
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
Warning unknown option vo_dxr3_device at line 6
[skin] file ( /usr/local/share/mplayer/skins/default/skin ) not found.
Skin not found (default).

I know that the rest of those commands that you send me worked cause I read all the log and I found that everything was copied and the file for the skin was made. *shrugs*

---

### Post by andrew.46 on 2007-09-30
Hi,

 Looks like a problem that can be solved:

> **Gouz said:**
> Hey thanks for the info there were help full and everything worked until the command  gmplayer..

Then I got the following 
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
Warning unknown option vo_dxr3_device at line 6
[skin] file ( /usr/local/share/mplayer/skins/default/skin ) not found.
Skin not found (default).

I know that the rest of those commands that you send me worked cause I read all the log and I found that everything was copied and the file for the skin was made. *shrugs*

It is my suspicion that the skin is not placed correctly. Could you post the results of the following, the first reloads you locate database and the second looks for the exact location of one of the Blue skin files:

```
$ sudo updatedb
$ locate subblue.png
```

As for the error:

> Warning unknown option vo_dxr3_device at line 6

I presume that you have written an ~/.mplayer/config file that has an error?

 Anyway please post the results of the locate command and then I suspect we can get gmplayer going.

                  Andrew

---

### Post by Gouz on 2007-09-30
rosi@rosi:~$ sudo updatedb
Password:
rosi@rosi:~$ locate subblue.png
/home/rosi/.mplayer/skins/default/subblue.png
/home/rosi/Blue/subblue.png
/home/rosi/Desktop/Blue/subblue.png

now that i see it, I think because I have 3 they may conflict with each other. I don't know *shrugs*


for the error no, I just run gmplayer and I got the error (and all the above message)

---

### Post by andrew.46 on 2007-09-30
Hi,

 I have found the solution:


> **Gouz said:**
> rosi@rosi:~$ sudo updatedb
Password:
rosi@rosi:~$ locate subblue.png
/home/rosi/.mplayer/skins/default/subblue.png
/home/rosi/Blue/subblue.png
/home/rosi/Desktop/Blue/subblue.png

now that i see it, I think because I have 3 they may conflict with each other. I don't know *shrugs*


for the error no, I just run gmplayer and I got the error (and all the above message)

 The syntax that I gave before to install the skin was a little sloppy for  which you have my apologies. Can I suggest that you delete the *contents* of your /home/rosi/.mplayer/skins/default directory but not the *actual* directory.  And then run the following:

```
$ cp -Rv $HOME/Desktop/Blue/* $HOME/.mplayer/skins/default
```

 And again my apologies for the sloppy syntax of the guide that has now been corrected.  Hopefully you will be looking at the glorious blue mplayer skin shortly :-)

                  Andrew

---

### Post by Gouz on 2007-09-30
how do i do that, I know just 

sudo rm -i

which will delete the file that I will name after the -i

and the rm -r that will remove all the directory.

even better how can I delete everything so i can reinstall them from the start step by step.

---

### Post by Gouz on 2007-09-30
BTW it worked perfectly only with one video for the rest I get an error: Fail to open :(

ok here is what happens, if I right click on a video file and say open with mplayer it can't be open if I brows the file from right click on the skin and say open file then brows it and open it is works...

But the image is not good at all it is too bright and the subs are not that good, if I change to X11 from Xv it fixes the color of the image and the subs. few subs are misplaced and there is to big space between them and the image is small even in full screen the image is like normal size.

any ideas?

---

### Post by andrew.46 on 2007-09-30
Hi,

 Good to see that you are persisting:

> **Gouz said:**
> BTW it worked perfectly only with one video for the rest I get an error: Fail to open :(

ok here is what happens, if I right click on a video file and say open with mplayer it can't be open if I brows the file from right click on the skin and say open file then brows it and open it is works...

But the image is not good at all it is too bright and the subs are not that good, if I change to X11 from Xv it fixes the color of the image and the subs. few subs are misplaced and there is to big space between them and the image is small even in full screen the image is like normal size.

any ideas?

 It is sometimes a struggle to get things just right but it will be worthwhile in the end. Have a look at what video output is available to you:

```
mplayer -vo help
```

 and have a play with these. The one that works best can be selected as default in an ~/.mplayer/conf file or selected on the command line as you have already found.

 Subtitles go a little beyond the scope of my walkthrough which is designed to get you up and going rather than move through the program itself. But if you use the gui you will see a section under preferences marked 'Subtitles and OSD' which will get you started. For the command line you would normally load all your preferences into a configuration file in ~./mplayer. You should find many 'recipes' online to experiment with.

 But otherwise the program is up and running with gui and on screen display + access to all codecs?

                  Andrew

---

### Post by csulok on 2007-09-30
hey

first of all thank you for the guide.

i came here to ask for some advice, halfway through the make install (actually checkinstall but i dont think that counts) i'm getting an error, that i can't resolve, not with google, not with this forum.

```

install -m 755 -s mplayer /usr/local/bin
strip: could not create temporary file to hold stripped copy of '/usr/local/bin/mplayer'
install: strip failed
make: *** [install-mplayer] Error 1

****  Installation failed. Aborting package creation.

```

these are the last couple of lines. what could i have done wrong? how do i resolve this issue?

---

### Post by Gouz on 2007-09-30
Hey, sorry for posting all this an stuff.

It is up and running all the videos that I have tried to run. The only thing is that  I can't drug and drop and I can't do a -right click open with-
And I think that the mplayer may choke with few videos, at least the older version that I was using was choking with something that can have big resolution (1024x786) and higher I will check that tomorrow and I will try to use what you posted and I will keep the topic updated with everything I found.

Btw mplayer has some great skins :P
I have tried most of them, it is easy to change them when you get the hung of it :P

Thanks for the help! *G*


Edit to csulok : Hey have you tried to pass the huge post(commands for the codecs) all at once or one by one?
If you have tried all at one try with few every time It worked for me with 3 line per time just don't forget the "sudo apt-get intall" before passing the first line and then copy past the rest ;)

---

### Post by andrew.46 on 2007-09-30
Hi,

 Saw your message:

> **csulok said:**
> hey

first of all thank you for the guide.

i came here to ask for some advice, halfway through the make install (actually checkinstall but i dont think that counts) i'm getting an error, that i can't resolve, not with google, not with this forum.

```

install -m 755 -s mplayer /usr/local/bin
strip: could not create temporary file to hold stripped copy of '/usr/local/bin/mplayer'
install: strip failed
make: *** [install-mplayer] Error 1

****  Installation failed. Aborting package creation.

```

these are the last couple of lines. what could i have done wrong? how do i resolve this issue?

 Hmmm... not sure about that one. I presume that this follows from:

```
$ make
$ sudo checkinstall -D
```

 Try without checkinstall, as 'package creation' would probably refer to the creation of the deb package by checkinstall. So just try the usual:

```
$ make
$ sudo make install
```

and this may be enough to get you out of trouble. I took checkinstall out of the guide because of *other* error messages with deb creation. And actually stopped using it myself at all.

         Andrew

---

### Post by csulok on 2007-10-01
thanks for the reply andrew

i wanted to make an easily removable and if needed reinstallable package by creating a deb

although you were right and with make install it didn't have a problem, i'd still prefer an easily removable solution..

---

### Post by andrew.46 on 2007-10-01
Hi,

 Read your comments about checkinstall:

> **csulok said:**
> thanks for the reply andrew

i wanted to make an easily removable and if needed reinstallable package by creating a deb

although you were right and with make install it didn't have a problem, i'd still prefer an easily removable solution..

 I agree with you completely, and checkinstall will do a great job. But better written software, like mplayer, has the ability to uninstall from the source code. To uninstall the mplayer program go to the source directory of mplayer and type:

```
$ sudo make uninstall
```

 and the program is gone. If you read the fine print of checkinstall you will see that it was produced for those programs that *don't* have this facility built in. Checkinstall by creating a deb and installing from it also places mplayer in the packet management system which is pointless in *this* case as it is extremely unlikely that Ubuntu will ever present the svn version of mplayer in its repository.

 Don't misunderstand me, I have checkinstall on my system and I use it for some software but for mplayer I do not. Mind you I have actually used checkinstall with the svn mplayer quite successfully in the past. If you want to try again just try changing options 2 and 3 in the deb creation section. From memory section 2 by default has a space that checkinstall does not like and section 3 needs a number.

 Otherwise all is working well with mplayer?

                Andrew

---

### Post by taisao on 2007-10-01
my smplayer doesn't work after installing the svn version of mplayer, where is the mplayer executeble found?
--

oke, it's in /usr/local/bin/

the old one is in /usr/bin/

so smplayer works now, how can I delete/remove the old mplayer version? Or just leave it like that?

---

### Post by andrew.46 on 2007-10-01
Hi,

 Glad you resolved your issue:

> **taisao said:**
>  [....]  how can I delete/remove the old mplayer version? Or just leave it like that?

To uninstall the mplayer program go to the source directory of mplayer and type:

```
$ sudo make uninstall
```

and the program is gone. But is smplayer a front-end for mplayer? In which case I assume you will need a copy of mplayer on your system either repository or compiled.

 Regards,

   Andrew

---

### Post by TheMono on 2007-10-01
Yes, smplayer packages depend on either mplayer or mplayer-nogui.

---

### Post by andrew.46 on 2007-10-01
Hi,

 Thanks for that:

> **TheMono said:**
> Yes, smplayer packages depend on either mplayer or mplayer-nogui.

 I have a small confession: although I am a huge fan of mplayer if I watch a dvd on a computer (rarely) I tend to use vlc :-) The gui gmplayer is a little primitive for my taste, I guess that is where a program like smplayer steps in.

                Andrew

---

### Post by taisao on 2007-10-02
> **andrew.46 said:**
> Hi,

 Glad you resolved your issue:



To uninstall the mplayer program go to the source directory of mplayer and type:

```
$ sudo make uninstall
```

and the program is gone. But is smplayer a front-end for mplayer? In which case I assume you will need a copy of mplayer on your system either repository or compiled.

 Regards,

   Andrew

uhm, but there is 2x mplayer on my kubuntu :confused:

one executeable is in /usr/local/bin/
 (MPlayer dev-SVN-r24680-4.1.2 (C) <- installed with the howto)

the other is in /usr/bin/ (which is MPlayer 2:1.0~rc1-0ubuntu9.1 (C) <- this one is installed with apt-get)

anyway, I think I just leave it like that, it works anyway.

---

### Post by andrew.46 on 2007-10-02
Hi,

 Hmmm.... mplayer x 2:

> **taisao said:**
> uhm, but there is 2x mplayer on my kubuntu :confused: one executeable is in /usr/local/bin/
 (MPlayer dev-SVN-r24680-4.1.2 (C) <- installed with the howto)
the other is in /usr/bin/ (which is MPlayer 2:1.0~rc1-0ubuntu9.1 (C) <- this one is installed with apt-get) anyway, I think I just leave it like that, it works anyway.

 That's something you don't see every day :-) Certainly this validates my caution in specifying --prefix=/usr/local (which is the default) in the guide that avoids one version overwriting the other.

 I guess this means that the repository version will uninstall with:

```
$ sudo apt-get remove mplayer
```

 while the svn version will uninstall with:

```
$ sudo make uninstall
```

 from the source directory.

               Andrew

---

### Post by NZ-Wanderer on 2007-10-02
Hi there...

I seem to have a problem when it comes to pasting that really HUGE list of files to get...

I get the following:

Reading package lists... Done
Building dependency tree
Reading state information... Done
libartsc0 is already the newest version.
libflac++6 is already the newest version.
liblzo2-2 is already the newest version.
libmpcdec3 is already the newest version.
libungif4g is already the newest version.
libxvmc1 is already the newest version.
ttf-bitstream-vera is already the newest version.
ttf-bitstream-vera set to manual installed.
Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libexpat1-dev: Depends: libexpat1 (= 1.95.8-4) but 1.95.8-4ubuntu1 is to be installed
E: Broken packages
simplicity@Kubuntu:~/source$         

I checked apept and it told me that libexpat1 1.95.8-4ubuntu1 is already installed, and when I tried to use adept to install the dev file it would not let me

Please help :) :)

---

### Post by andrew.46 on 2007-10-02
Hi,

 In fact it is a truly *huge* list of files:

> **NZ-Wanderer said:**
> Hi there...
I seem to have a problem when it comes to pasting that really HUGE list of files to get...
I get the following:

[...]
Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libexpat1-dev: Depends: libexpat1 (= 1.95.8-4) but 1.95.8-4ubuntu1 is to be installed
E: Broken packages     
I checked apept and it told me that libexpat1 1.95.8-4ubuntu1 is already installed, and when I tried to use adept to install the dev file it would not let me
Please help :) :)

  All is not lost :-) As long as there is only a couple of dev files missing from this 50 megs collection I suspect that you will be ok to continue with the configure process. Have a look at the output of ./configure and it will tell you what is missing and what is included.

 The collection of libs and devs has been put together (by me!) to grab as much functionality as possible from mplayer, not all of it would be used by all users. For example did you see all the libungif material? This enables mplayer to output frames of a movie in gif format: multiple stills. So if you did not load all the libungif dev files you would not have access to this feature.

 See what I mean? The files are not* all* mandatory. My advice is to continue, check what configure says and you will probably be ok.

 Actually I just dug this out of the official docs. It illustrates perfectly the trial and error nature of compiling the program:

> STEP2: Configuring MPlayer
~~~~~~~~~~~~~~~~~~~~~~~~~~

MPlayer can be adapted to all kinds of needs and hardware environments. Run

  ./configure

to configure MPlayer with the default options. GUI support has to be enabled
separately, run

  ./configure --enable-gui

if you want to use the GUI.

If something does not work as expected, try

  ./configure --help

to see the available options and select what you need.

The configure script prints a summary of enabled and disabled options. If you
have something installed that configure fails to detect, check the file
configure.log for errors and reasons for the failure. Repeat this step until
you are satisfied with the enabled feature set.

 The rest of this doc can be read at: [http://www.mplayerhq.hu/DOCS/README](http://www.mplayerhq.hu/DOCS/README)


          Andrew

---

### Post by jmrichky on 2007-10-04
The guide worked perfect for me.  It has played every file I have thrown at flawlessly.  Note that since I am using the 64-bit version of Ubuntu, I needed to:
```
$ wget http://www.mplayerhq.hu/MPlayer/releases/codecs/essential-amd64-20061203.tar.bz2
```
Instead of:
```
$ wget http://www.mplayerhq.hu/MPlayer/releases/codecs/all-20061022.tar.bz2
```

I do have one question though.  How can I get mplayer to play embedded video in Firefox?  When I try to install the plugin through apt, it wants to install mplayer from the repos as well.  I am afraid it will replace the shiny new version that I just built.

---

### Post by andrew.46 on 2007-10-04
Hi,

 You echo my own question:

> **jmrichky said:**
> I do have one question though.  How can I get mplayer to play embedded video in Firefox?  When I try to install the plugin through apt, it wants to install mplayer from the repos as well.  I am afraid it will replace the shiny new version that I just built.

 I am a little puzzled with this one too and have been racking my brains for a solution. Any ideas anybody else?

 Good to hear it all worked well for you though. I had no idea that there were different codecs for 64bit: you live and learn :-)

                 Andrew

---

### Post by shirilover on 2007-10-04
> **jmrichky said:**
> I do have one question though.  How can I get mplayer to play embedded video in Firefox?  When I try to install the plugin through apt, it wants to install mplayer from the repos as well.  I am afraid it will replace the shiny new version that I just built.

You can also build mplayerplug-in as well.
The latest version 3.4.5 works well for me.

I'm going to assume you have already successfully built mplayer.
First, we need to grab the source.
```

wget http://internap.dl.sourceforge.net/sourceforge/mplayerplug-in/mplayerplug-in-3.45.tar.gz
tar -xzvf mplayerplug-in-3.45.tar.gz
cd mplayerplug-in

```

Also, we need the firefox development files
```

sudo apt-get install firefox-dev libnss-dev libnspr-dev

```

Now, we can build the plugin.
```

./configure
make
make install

```
make install will install the plugin to your firefox profile directory, usually ~/.mozilla/plugins. If you wish to make them globally available, use sudo make install instead.

---

### Post by andrew.46 on 2007-10-04
Hi,

 I tried that several times before:

> **shirilover said:**
> You can also build mplayerplug-in as well.
The latest version 3.4.5 works well for me.


and for the life of me I could never compile it :-) For Gutsy:
```

sudo apt-get install firefox-dev libnss3-dev libnspr4-dev
```

 Wish I could get it going!!

          Andrew

---

### Post by jmrichky on 2007-10-04
I just figured out to get the embedded video in firefox with t he mplayer built from your guide.  First you must go to the mplayer source directory and "sudo make uninstall" then (in the same directory) "sudo checkinstall" and finally "sudo apt-get mozilla-mplayer".  Hope this helps.

---

### Post by owcarnia on 2007-10-04
I did what your guide said and still have no gui. ubuntu says:
> 
MPlayer 1.0rc1-4.1.2 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm)  (Family: 6, Model: 8, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE
Usage:   mplayer [options] [url|path/]filename

Basic options: (complete list in the man page)



and then the options... No gui errors for me :/ And since there still was na mozilla plugin I did what jmrichy said and  command 'checkinstall' is not found and 'apt-get mozilla-mplayer' is inapropriate somehow. The funny thing is that synaptic finds no installed mplayer packages at all. Is it normal?

---

### Post by jmrichky on 2007-10-04
> [COLOR="Red"]MPlayer 1.0rc1-4.1.2 (C) 2000-2006 MPlayer Team[/COLOR]
CPU: AMD Athlon(tm) (Family: 6, Model: 8, Stepping: 1)
CPUflags: MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE
Usage: mplayer [options] [url|path/]filename
It appears that you have an older version of mplayer (1.0rc1-4.1.2).  It should look like this:
> [COLOR="Lime"]MPlayer dev-SVN-r24698-4.1.3 (C) 2000-2007 MPlayer Team[/COLOR]
CPU: AMD Athlon(tm) 64 Processor 3200+ (Family: 15, Model: 15, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE SSE

---

### Post by owcarnia on 2007-10-04
well i've downloaded it yesterday from mplayers webpage :P And what about this whole gui stuff ? I've seen on the forum that normally gui problems are somehow indicated.

---

### Post by jmrichky on 2007-10-04
> well i've downloaded it yesterday from mplayers webpage :P And what about this whole gui stuff ? I've seen on the forum that normally gui problems are somehow indicated.

Are you using Gutsy?  Does MPlayer show up in Applications>Sound&Video on the menu?  Did you try "gmplayer" instead of "mplayer" in the console?  With my limited knowledge, I would have no idea why your version of mplayer does not display the same as mine if you followed the guide exactly.  If I were you, I would remove mplayer altogether and start the guide again.  Just remember to use "sudo checkinstall" in the place of "sudo make install" if you want to install the plug-in for Firefox.  Again, I am relatively new to Linux but this did work for me.  There may be a better way to get the plug-in to work.

---

### Post by andrew.46 on 2007-10-05
Hi,

 Saw a small bit of confusion here:

> **owcarnia said:**
> well i've downloaded it yesterday from mplayers webpage :P And what about this whole gui stuff ? I've seen on the forum that normally gui problems are somehow indicated.

 I suspect that you have actually installed 'MPlayer v1.0rc1 source' from the mplayer web site. This is fine, although the svn version is newer. Hopefully you installed the codecs pack first?

 To run the gui you will also need to install a skin.

                  Andrew

---

### Post by owcarnia on 2007-10-06
Ok. So there were some problems with downloading lib's I guees. Now I stick strictly to your guide installing the svn version and there's another problem. While configuring I got problem at the end:

> Error: The GUI requires libavcodec with PNG support (needs zlib).
Check "configure.log" if you do not understand why it failed.

 Nothing interesting in log though. Still searching for some solution on discussion lists.

And that's what happens when I try 'make' anyway :

> ############################################################
####### Please run ./configure again - it's changed! #######
############################################################
./version.sh `cc -dumpversion`
cc -I./libavcodec -I./libavformat -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -I. -I./libavutil -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=athlon-xp -mtune=athlon-xp -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DHAVE_CONFIG_H -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT     -c -o mplayer.o mplayer.c
libvo/font_load.h:97: warning: 'render_one_glyph' defined but not used
libvo/font_load.h:98: warning: 'kerning' defined but not used
mplayer.c: In function 'playing_audio_pts':
mplayer.c:1602: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions,
see <URL:file:///usr/share/doc/gcc-4.1/README.Bugs>.
Preprocessed source stored into /tmp/ccEmL47g.out file, please attach this to your bugreport.
make: *** [mplayer.o] Error 1


---

### Post by andrew.46 on 2007-10-10
Hi,

 Most gratifying to see that this guide has almost 2,000 views! Might be a good time to point out that a new release version has just come out. Anybody who is interested more in stability than cutting edge has three choices in ascending order of excitement:

[LIST=1]
[*]Ubuntu repository mplayer
[*]Release version from mplayer site
[*]svn mplayer
[/LIST]

 The gap between svn and release version should be a little tighter right now.

                   Andrew

---

### Post by owcarnia on 2007-10-10
damn there is no way this can work. I installed checkinstall for better view of things done during installation, and after installing mplayer it doesnt work. Ubuntu says that 'gmplayer' is not installed and inputing 'mplayer' gives "Segmentation fault (core dumped)" error.

Uninstalling it completely (with make uninstall and apt-get remove) and reinstalling didn't fix the issue. Also installation through synaptic isn't the right way :/

---

### Post by andrew.46 on 2007-10-10
Hi,

 Sorry to hear you are having this trouble:

> **owcarnia said:**
> damn there is no way this can work. I installed checkinstall for better view of things done during installation, and after installing mplayer it doesnt work. Ubuntu says that 'gmplayer' is not installed and inputing 'mplayer' gives "Segmentation fault (core dumped)" error.

Uninstalling it completely (with make uninstall and apt-get remove) and reinstalling didn't fix the issue. Also installation through synaptic isn't the right way :/

If this svn mplayer is giving you a lot of trouble it is not the end of the world to use the repository version:

```
sudo apt-get install mplayer
```

 This will give you a functioning mplayer, gmplayer and many of the codecs.

                Andrew

---

### Post by owcarnia on 2007-10-11
Ha yeah I tried this also but still get 'Segmentation fault (core dumped)" :/ Guess I have to wait for edgy or at least new kernel.

---

### Post by andrew.46 on 2007-10-11
Hi,

> **owcarnia said:**
> Ha yeah I tried this also but still get 'Segmentation fault (core dumped)" :/ Guess I have to wait for edgy or at least new kernel.

 hmmm.... edgy? You mean Gutsy?

              Andrew

---

### Post by owcarnia on 2007-10-11
> **owcarnia said:**
> Ha yeah I tried this also but still get 'Segmentation fault (core dumped)" :/ Guess I have to wait for edgy or at least new kernel.

Yeah Gutsy,sry.

---

### Post by Frijolie on 2007-10-15
Thanks for this awesome guide. It was amazing that I was able to compile anything, and from svn to boot! I did have to tweak it a little myself after all was compiled and installed, I had to:

```

 sudo cp -R $HOME/.mplayer/skins/default/clearplayer /usr/local/share/mplayer/skins

```

to get my gmplayer to recognize my skin. However, this still hasn't fixed my problem of navigating DVD menus. Hmm...

Also I'm getting this error:

```
 
[mpeg2video @ 0x892f5b0]ac-tex damaged at 25 9
[mpeg2video @ 0x892f5b0]Warning MVs not available
[mpeg2video @ 0x892f5b0]concealing 945 DC, 945 AC, 945 MV errors

```

and a pop-up in the GUI that says "Warning: MVs are not available"

How do I fix this one?

---

### Post by gav616 on 2007-10-18
was just trying your guide...

am i alriight using the newer codecs? [http://www.mplayerhq.hu/MPlayer/releases/codecs/all-20071007.tar.bz2](http://www.mplayerhq.hu/MPlayer/releases/codecs/all-20071007.tar.bz2)

---

### Post by andrew.46 on 2007-10-18
Hi,

 Thanks for that tip:

> **gav616 said:**
> was just trying your guide...
am i alriight using the newer codecs? [http://www.mplayerhq.hu/MPlayer/releases/codecs/all-20071007.tar.bz2](http://www.mplayerhq.hu/MPlayer/releases/codecs/all-20071007.tar.bz2)

You certainly are! These must have come out with mplayer rc 2. I have adjusted the guide to match this. Plus downloaded and installed them myself.

 Thanks!

     Andrew

---

### Post by dlpfmVfH on 2007-10-19
I'm running gutsy right now, but can't get mplayer to compile...

it gives error with the ivtv part. I tried disable it with --disable-ivtv but that didn't work.

how did you bypass/solve this problem??

---

### Post by andrew.46 on 2007-10-19
Hi,

 Saw your message:

> **aboe said:**
> I'm running gutsy right now, but can't get mplayer to compile...

it gives error with the ivtv part. I tried disable it with --disable-ivtv but that didn't work.

how did you bypass/solve this problem??

 I suspect that you must have a fancy mpeg decoder board on your system? From the manual:

> Player  supports  a  wide range of video and audio output drivers.  It works with X11, Xv, DGA, OpenGL, SVGAlib, fbdev,  AAlib,  libcaca,  DirectFB,  Quartz, Mac OS X CoreVideo, but you can also use GGI, SDL (and all their drivers), VESA (on every VESA-compatible card,  even  without X11),  some  low-level card-specific drivers (for Matrox, 3dfx and ATI) and some hardware MPEG decoder boards, such as the Siemens  DVB, ** Hauppauge PVR (IVTV)**, DXR2 and DXR3/Hollywood+.  Most of them support software or hardware scaling, so you can enjoy movies in fullscreen mode.

 I am not familiar with this hardware or the techiniques to run it with mplayer I am afraid :confused:

                          Andrew

---

### Post by foureight84 on 2007-10-20
wait, so how do i compile the firefox plugin from svn? also, this is an awesome guide. works like a charm. awesome work from everyone who contributed.

edit: i noticed that after a clean install of gusty, the codecs are not installed so divx, and etc media files do not have thumbnails. how do i go about getting thumbnails to work? would i install the w32codec and other codec packs?

---

### Post by foureight84 on 2007-10-20
for anyone using compiz and you're getting blank video. then do the following:

**go into preference, and change the video driver to: **
```
X11 (XImage/Shm) 
```

then **gedit ~/.mplayer/config** and add:
```
zoom=yes
```

this should allow full video playback in compiz without the blue screen when moving the movie around.

---

### Post by mocha on 2007-10-20
I noticed that this guide was updated for Gutsy.  How does it differ from Feisty?  For those of us with nvidia cards too scared to upgrade..  :(  Thanks!

---

### Post by andrew.46 on 2007-10-20
Hi,

Saw your message concerning Feisty:

> **mocha said:**
> I noticed that this guide was updated for Gutsy.  How does it differ from Feisty?  For those of us with nvidia cards too scared to upgrade..  :(  Thanks!

I decided to focus on a specific version as it gets a little too complex to describe different strategies for different versions of Ubuntu. However the basic setup is *exactly* the same but the listing of libraries and dev files will be different. If you scroll back a few messages you will see that somebody has posted a list of Feisty dev files / libraries.

I have not tried this list myself as I do not run feisty, actually I no longer run Gutsy either but that is another story :-)

           Andrew

---

### Post by mocha on 2007-10-20
I just complied and installed, no problems.  I was mainly interested in compiling for the sake of mencoder.  Thanks for the guide!

Now I have for video encoding:

```

Available codecs:
   copy     - frame copy, without re-encoding. Doesn't work with filters.
   frameno  - special audio-only file for 3-pass encoding, see DOCS.
   raw      - uncompressed video. Use fourcc option to set format explicitly.
   lavc     - libavcodec codecs - best quality!
   vfw      - VfW DLLs, read DOCS/HTML/en/encoding-guide.html.
   qtvideo  - QuickTime DLLs, currently only SVQ1/3 are supported.
   libdv    - DV encoding with libdv v0.9.5
   xvid     - XviD encoding
   x264     - H.264 encoding

```

and for audio encoding:

```
Available codecs:
   copy     - frame copy, without re-encoding (useful for AC3)
   pcm      - uncompressed PCM audio
   mp3lame  - cbr/abr/vbr MP3 using libmp3lame
   lavc     - FFmpeg audio encoder (MP2, AC3, ...)
   twolame  - Twolame MP2 audio encoder
   faac     - FAAC AAC audio encoder

```

Twolame was my main concern, now I got it!

---

### Post by andrew.46 on 2007-10-20
Hi,

 Good to see a satisfied customer:

> **mocha said:**
> I just complied and installed, no problems.  I was mainly interested in compiling for the sake of mencoder.  Thanks for the guide!

Now I have for video encoding:

```

Available codecs:
   copy     - frame copy, without re-encoding. Doesn't work with filters.
   frameno  - special audio-only file for 3-pass encoding, see DOCS.
   raw      - uncompressed video. Use fourcc option to set format explicitly.
   lavc     - libavcodec codecs - best quality!
   vfw      - VfW DLLs, read DOCS/HTML/en/encoding-guide.html.
   qtvideo  - QuickTime DLLs, currently only SVQ1/3 are supported.
   libdv    - DV encoding with libdv v0.9.5
   xvid     - XviD encoding
   x264     - H.264 encoding

```

and for audio encoding:

```
Available codecs:
   copy     - frame copy, without re-encoding (useful for AC3)
   pcm      - uncompressed PCM audio
   mp3lame  - cbr/abr/vbr MP3 using libmp3lame
   lavc     - FFmpeg audio encoder (MP2, AC3, ...)
   twolame  - Twolame MP2 audio encoder
   faac     - FAAC AAC audio encoder

```

Twolame was my main concern, now I got it!

 mencoder still remains a dark mystery for me. The few times I have used it I have copied and pasted other people's instructions :-)

 For H.264 encoding I understand that the mplayer people advise the svn H.264 encoder:

[http://www.mplayerhq.hu/DOCS/HTML/en/video-codecs.html](http://www.mplayerhq.hu/DOCS/HTML/en/video-codecs.html)

 Something I have not investigated myself but if you are a keen encoder ...:

svn co svn://svn.videolan.org/x264/trunk x264

              Andrew

---

### Post by mocha on 2007-10-20
Another bonus of compiling this svn mplayer is my FLV files can now be rewound and fast forwarded!  Yay!!

---

### Post by porphiron on 2007-10-22
Thanks for the tutorial!, it worked a treat.

I it installed ok, but am having a problem getting applications to recognise that mplayer / mencoder are installed, for example k9copy (which i use alot) just keeps trying to install the stock version that comes with gutsy, even though mencoder / mplayer are there, I've checked aptitude and theres nothing there to say that mplayer/mencoder are installed......


cheers!

Porph

---

### Post by andrew.46 on 2007-10-22
Hi,

 Glad my walkthough was useful to you:

> **porphiron said:**
> Thanks for the tutorial!, it worked a treat.

I it installed ok, but am having a problem getting applications to recognise that mplayer / mencoder are installed, for example k9copy (which i use alot) just keeps trying to install the stock version that comes with gutsy, even though mencoder / mplayer are there, I've checked aptitude and theres nothing there to say that mplayer/mencoder are installed......
cheers!

Porph

 Installing in this way goes outside the ubuntu package management system. The solution is to locate mplayer in synaptic and use the 'lock version' option. I would give more detailed directions but my dark secret is that I no longer run ubuntu :(. Can someone post the exact instructions?

                       Andrew

---

### Post by porphiron on 2007-10-22
Ta! for the reply,

Have mamanged to lock the version of mplayer by using checkinstall, then looking it up in aptitude, instead of make install, but only mplayer looked liked it had been "installed" not mencoder, is there any way of doing a separate ./configure and make for mencoder?? then i could simply do a checkinstall for that and everything would be fine??


Porph!

---

### Post by andrew.46 on 2007-10-22
Hi,

 Glad to see that you silently corrected my 'senior moment' :

> **porphiron said:**
> Ta! for the reply,

Have mamanged to lock the version of mplayer by using checkinstall, then looking it up in aptitude, instead of make install, but only mplayer looked liked it had been "installed" not mencoder, is there any way of doing a separate ./configure and make for mencoder?? then i could simply do a checkinstall for that and everything would be fine??Porph!

 Of course checkinstall will put the mplayer install back into the ubuntu package management system and *then* you can lock the version.

 Looks like you can install mencoder without mplayer although I have never done this:

```
Optional features:
  --disable-mencoder     disable MEncoder (A/V encoder) compilation [enable]
  --disable-mplayer      disable MPlayer compilation [enable]
  --enable-gui           enable GMPlayer compilation (GTK+ GUI) [disable]

```

 These and many other options are found by typing ./configure --help in the mplayer source code directory. I am not so sure that this will help though but I am sure there is room there for several hours of mucking around :)

               Andrew

---

### Post by Sunnz on 2007-10-23
Just wondering, why use the SVN version? If you only want some compile option not turned on by default by the Ubuntu team + CPU optimisation, why not just use the source from launchpad.net?

I just did that and it worked out pretty well... I even did a `sudo aptitude hold mplayer` so it doesn't "upgrade" it when I install other things like gnome-mplayer.

---

### Post by andrew.46 on 2007-10-23
Hi,

 Thanks for your comments:

> **Sunnz said:**
> Just wondering, why use the SVN version? If you only want some compile option not turned on by default by the Ubuntu team + CPU optimisation, why not just use the source from launchpad.net?

I just did that and it worked out pretty well... I even did a `sudo aptitude hold mplayer` so it doesn't "upgrade" it when I install other things like gnome-mplayer.

 Using the svn mplayer is certainly a *choice*, and one that is available for everybody to make. As I see it there are 3 choices:

[LIST=1]
[*]Use the Ubuntu repository version.This is the safest option and will give you an mplayer that has been expertly crafted to fit in with Ubuntu. Certain choices will have already been made for you, some codecs added but not others, but it will be a safe, solid bit of software that will be automatically updated by the Ubuntu team if a newer version is produced for Ubuntu.
[*]Use the source code for the latest Release Candidate. This can be downloaded from the mplayer web site and represents a "polished" version of mplayer. This is a tempting option as MPlayer v1.0rc2 has only recently been released. You have to download a skin + codecs yourself and decide on your own compile time options as well as ensuring that dependancies are satisfied.
[*]Use the svn mplayer. This is what my guide describes and it delivers features that have not made it into either of the 2 versions. If a new feature has been added yesterday, you have it today by utilising "svn update". Always carrying the *possibility* of instability in the case of mplayer it delivers performance often better that either of the 2 options with a stability that I personally have never seen in question. There are some very clever people out there and the svn mplayer allows you to share the product of their labours. 
[/LIST]

It is of course all about choice and any of the 3 above will deliver you a decent copy of mplayer, it depends how involved you want to get. BTW when  you say "lanchpad.net" do you mean [https://code.launchpad.net/mplayer??](https://code.launchpad.net/mplayer??)

            Andrew

---

### Post by ephman on 2007-10-23
> **foureight84 said:**
> for anyone using compiz and you're getting blank video. then do the following:

**go into preference, and change the video driver to: **
```
X11 (XImage/Shm) 
```

then **gedit ~/.mplayer/config** and add:
```
zoom=yes
```

this should allow full video playback in compiz without the blue screen when moving the movie around.

hey thanks,

good news is that i can now play a video full screen... bad new, runs way too slow...  any idea how to speed it up??  am i the only person with this issue, did a little hunting and can't find the answer.  i have an ati x300, not the heaviest video card, but should be able to run the video full speed.  any help would be greatly appreciated.

thanks for the bandwidth,

ephman

---

### Post by Sunnz on 2007-10-24
> **andrew.46 said:**
>  Using the svn mplayer is certainly a *choice*, and one that is available for everybody to make. As I see it there are 3 choices:

[LIST=1]
[*]Use the Ubuntu repository version.This is the safest option and will give you an mplayer that has been expertly crafted to fit in with Ubuntu. Certain choices will have already been made for you, some codecs added but not others, but it will be a safe, solid bit of software that will be automatically updated by the Ubuntu team if a newer version is produced for Ubuntu.
[*]Use the source code for the latest Release Candidate. This can be downloaded from the mplayer web site and represents a "polished" version of mplayer. This is a tempting option as MPlayer v1.0rc2 has only recently been released. You have to download a skin + codecs yourself and decide on your own compile time options as well as ensuring that dependancies are satisfied.
[*]Use the svn mplayer. This is what my guide describes and it delivers features that have not made it into either of the 2 versions. If a new feature has been added yesterday, you have it today by utilising "svn update". Always carrying the *possibility* of instability in the case of mplayer it delivers performance often better that either of the 2 options with a stability that I personally have never seen in question. There are some very clever people out there and the svn mplayer allows you to share the product of their labours. 
[/LIST]

It is of course all about choice and any of the 3 above will deliver you a decent copy of mplayer, it depends how involved you want to get. **BTW when  you say "lanchpad.net" do you mean [https://code.launchpad.net/mplayer??](https://code.launchpad.net/mplayer??)**

            Andrew

Yea, that would be the source used to build the mplayer in (1), or am I missing something?

Precisely, I really meant this one: [https://code.launchpad.net/~ubuntu-dev/mplayer/ubuntu](https://code.launchpad.net/~ubuntu-dev/mplayer/ubuntu) "MPlayer for Ubuntu".

---

### Post by andrew.46 on 2007-10-24
Hi,

Now I see:

> **Sunnz said:**
> Yea, that would be the source used to build the mplayer in (1), or am I missing something?

Precisely, I really meant this one: [https://code.launchpad.net/~ubuntu-dev/mplayer/ubuntu](https://code.launchpad.net/~ubuntu-dev/mplayer/ubuntu) "MPlayer for Ubuntu".

 I think that this source represents an in-between stage for Ubuntu. The _actual_ source is found here:

[http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)

 which no doubt the Ubuntu devs  start with and modify to produce the repositiory version. I have never used this 'in-between' version; I have used the Repository version via apt-get, compiled the latest release candidate and settled on the svn mplayer. But if this version works for you go for it :-)

          Andrew

---

### Post by rvm4000 on 2007-10-24
> **ephman said:**
> good news is that i can now play a video full screen... bad new, runs way too slow...  any idea how to speed it up??  am i the only person with this issue, did a little hunting and can't find the answer.  i have an ati x300, not the heaviest video card, but should be able to run the video full speed.  any help would be greatly appreciated.

x11 is much slower than xv.

---

### Post by andrew.46 on 2007-10-24
Hi,

 Excellent point:

> **rvm4000 said:**
> x11 is much slower than xv.

 Perhaps try full screen with xv:

```
$ mplayer -vo xv -fs filename.mpg
```

   Andrew

---

### Post by ephman on 2007-10-24
> **andrew.46 said:**
> Hi,

 Excellent point:



 Perhaps try full screen with xv:

```
$ mplayer -vo xv -fs filename.mpg
```

   Andrew

hi,

thanks for your help, so appreciated.  ok here's what i noticed, when i switch to xv and go to full screen all i get is a blank screen.  here's the thing i noticed.  i have a sneaky feeling xgl has something to do with it.  just noticed that when i enable xgl is when i have this 'slow full screen' issue.  googled around a bit and found i'm not the only person with this issue.  so i took their suggestion of using gl2, so i tried it and the strangest thing was that my machine autologged me off. so i tried it again, and i got logged off again.  so i think xgl has something to do with this issue of having a slow video at full screen.  any other suggestions??

thanks for your bandwidth,

ephman

---

### Post by andrew.46 on 2007-10-26
Wooooo hooooo!!!

  5,000 views! I cannot believe my little guide is so popular!!  Do I get a T-shirt or something?

         Andrew

---

### Post by lordViN on 2007-10-26
Andrew.46 Great guide, thanks

I'm having problems with the mplayer, It doesn't work very well on the graphic interface, when I try to open within xfce. It only works when I drag & drop files to the gui but not if I doble click or rigjht click open with "mplayer".

and one more question, where is the mplayer source directory, is there where I need to do "make uninstall" for uninstalling the svn version right?   is in "/usr/local/bin",  or is in the same directory where it was compiled  "/home/user/mplayer"

---

### Post by loko on 2007-10-27
> **csulok said:**
> hey

first of all thank you for the guide.

i came here to ask for some advice, halfway through the make install (actually checkinstall but i dont think that counts) i'm getting an error, that i can't resolve, not with google, not with this forum.

```

install -m 755 -s mplayer /usr/local/bin
strip: could not create temporary file to hold stripped copy of '/usr/local/bin/mplayer'
install: strip failed
make: *** [install-mplayer] Error 1

****  Installation failed. Aborting package creation.

```

these are the last couple of lines. what could i have done wrong? how do i resolve this issue?

Hello, today i got the same error while installing cheese.

For you, and anybody elsa having this error: 

/usr/local/bin does not exist

so create it first, then it will work

(sudo mkdir /usr/local/bin and sudo chmod 755 /usr/local/bin)

---

### Post by andrew.46 on 2007-10-29
Hi,

 Good to see a fellow xfce user:

> **lordViN said:**
> Andrew.46 Great guide, thanks
I'm having problems with the mplayer, It doesn't work very well on the graphic interface, when I try to open within xfce. It only works when I drag & drop files to the gui but not if I doble click or rigjht click open with "mplayer". 

Hmmm...  I suspect that this might be a  problem with your setup rather than an mplayer problem. I use xfce myself with no such problem. What is the error message you receive?


> and one more question, where is the mplayer source directory, is there where I need to do "make uninstall" for uninstalling the svn version right?   is in "/usr/local/bin",  or is in the same directory where it was compiled  "/home/user/mplayer"

The directory will be the one you unpacked and compiled the archive in. In this walkthrough I have nominated $HOME/Desktop/mplayer but this is an arbitrary choice and you may have chosen a different location?

 Don't forget you can update mplayer easily now by entering the command:

```
$ svn update
```

in this directory also and then recompiling. The mplayer svn repository is *always* busy :-)

 All the very best!!

      Andrew

---

### Post by lordViN on 2007-10-30
thanks for your help, 

the message I receive is "Failed to open the file xxxx" but it only happens with some files. 

about updating you wrote:

> Don't forget you can update mplayer easily now by entering the command:

Code:

$ svn update

in this directory also and then recompiling. The mplayer svn repository is always busy


After updating using the "svn update", it's necessary to do a new ./configure, and then "make" and "sudo make install" again? and also I need to a "sudo make uninstall" before all that right?  

so probably if I'm right the order for updating is: 

```
$ sudo make uninstall
$ svn update
$ make clean
$ ./configure \
--prefix=/usr/local \
--enable-largefiles \
--enable-gui \
--codecsdir=/usr/local/lib/codecs
$ make
$ sudo make install

```
I'm right?

---

### Post by andrew.46 on 2007-10-30
Hi,

 Sounds like you have the idea:

> **lordViN said:**
> After updating using the "svn update", it's necessary to do a new ./configure, and then "make" and "sudo make install" again? and also I need to a "sudo make uninstall" before all that right?  

so probably if I'm right the order for updating is: 

```
$ sudo make uninstall
$ svn update
$ make clean
$ ./configure \
--prefix=/usr/local \
--enable-largefiles \
--enable-gui \
--codecsdir=/usr/local/lib/codecs
$ make
$ sudo make install

```
I'm right?

I would tend to run make clean at the very beginning but it really makes no difference :-)

 A small secret of this walkthrough is that 2 of the ./configure options are not absolutely necessary:  --prefix=/usr/local  and  --codecsdir=/usr/local/lib/codecs. I have included these to minimise potential problems of installation and to demonstrate how easily such things can be altered.

 The default installation directory is /usr/local so this does not really *have* to be specified, but if you select a different location *this* is the line to be altered.

 The ./configure process will find the codecs directory without it necessarily being specified in the manner that I have in the walkthrough but it is so important that mplayer find the codecs that I put this line in to be *totally sure*.

 So in reality you could as easily run as follows:

```
$ sudo make clean
$ sudo make uninstall
$ svn update
$ ./configure --enable-largefiles --enable-gui 
$ make
$ sudo make install

```

with the same end result.

 I trust you are having a great time with this amazing program!

                  Andrew

---

### Post by cf1709 on 2007-10-31
Hi, I'm a complete newbie in MPlayer. I tried to play an audio file and I heard nothing. I looked at the terminal and this came out:

```
MPlayer dev-SVN-r24909-4.1.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Celeron(R) CPU 2.80GHz (Family: 15, Model: 4, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
xscreensaver_disable: Could not find XScreenSaver window.

Playing /home/cf1709/Videos/Clannad OP_ED/OST/01 - Megumeru ~cuckool mix 2007~.mp3.
Audio file file format detected.
Clip info:
 Title: Megumeru ~cuckool mix 2007~
 Artist: eufonius
 Album: Megumeru ~cuckool mix 2007~
 Year: 2007
 Comment: #NIPPONSEI @ IRC.RIZON.NET
 Track: 1
 Genre: Anime
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 320.0 kbit/22.68% (ratio: 40000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
[AO ESD] esd_open_sound failed: No such file or directory
Could not open/initialize audio device -> no sound.
Audio: no sound
Video: no video
```

EDIT: Please disregard this concern of mine. I just got it fixed by choosing drivers. Thanks anyway for this info.

---

### Post by andrew.46 on 2007-10-31
Hi,

 Not such a noob that couldn't fix your own problem :-)

> **cf1709 said:**
> 

```
MPlayer dev-SVN-r24909-4.1.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Celeron(R) CPU 2.80GHz (Family: 15, Model: 4, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
[...]
[AO ESD] esd_open_sound failed: No such file or directory
Could not open/initialize audio device -> no sound.

```

EDIT: Please disregard this concern of mine. I just got it fixed by choosing drivers. Thanks anyway for this info.

In fact as you found mplayer couldn't find esd sound driver. You can specify the successful sound device in your ~/.mplayer/config file which will make it the default rather than specifying it on the command line each time.

All the best!

   Andrew

---

### Post by andrew.46 on 2007-10-31
Hi,

 I  am not sure if people are interested in mplayer beyond its ability to read multiple audio and video formats? I have done a little work with some of its *other* features:

[http://people.aapt.net.au/~adjlstrong/ftgws.html](http://people.aapt.net.au/~adjlstrong/ftgws.html)
[http://people.aapt.net.au/~adjlstrong/iRiverX20.html](http://people.aapt.net.au/~adjlstrong/iRiverX20.html)

 I would love to hear what uses others are putting the svn mplayer to. It is a lot of work to put the program together in this way, is the program working for* you* now?

           Andrew

PS The ftgws.html page contains a Slackware version of this walkthrough, the more interesting material is after this :-)

---

### Post by gav616 on 2007-11-01
on the 
```
sudo make install
```

you could do a 

```
sudo checkinstall
```

helpful in managing cvs's through synaptic :)

also andrew.46;

i would like to see you add that svn update section to your lovely guide;
[http://ubuntuforums.org/showpost.php?p=3668385&postcount=91](http://ubuntuforums.org/showpost.php?p=3668385&postcount=91)

---

### Post by garybrlow on 2007-11-01
Nice how to. :) I have compiled Mplayer rc2 SVN as stated in the howto and everything went fine. (\\:D/ Yay!) Everything works as it should except that when playing files with blank spaces in the filename it lets out an error saying it can not play the file because it can not be found. If you rename the file removing the blank spaces it plays fine. The same thing happens if the file is located in a directory with blank spaces even if the filename is without blank spaces. This behavior should not be happening but it is. My System specs are Celeron 2.0 Ghz, 256MB RAM, Geforce FX5200, using Xubuntu Gutsy with Compiz-Fusion. Anybody having the same problem? :confused:

---

### Post by dabotsonline on 2007-11-01
So, if we wanted to use CoreAVC with coreavc-for-linux (does v1.6 work?) instead of libavcodec, and following thse instructions: [http://code.google.com/p/coreavc-for-linux/wiki/MplayerInstallation](http://code.google.com/p/coreavc-for-linux/wiki/MplayerInstallation) , would we follow this sequence after having downloaded the mplayer source code, and downloaded, compiled and installed x264:

```

$ svn checkout http://coreavc-for-linux.googlecode.com/svn/trunk/ coreavc-for-linux 
$ cd coreavc-for-linux
$ ./mplayer/build_patch.pl $HOME/Desktop/mplayer > mplayerfull.patch
$ cd $HOME/Desktop/mplayer
$ patch -p0 < $HOME/Desktop/mplayer/mplayerfull.patch
``` directly before doing 
```

$ ./configure \
--prefix=/usr/local \
--enable-largefiles \
--enable-gui \
--codecsdir=/usr/local/lib/codecs
$ make 
$ sudo make install
$ cp loader/registercodec /usr/local/bin/

```

and then update codecs.conf ?

---

### Post by andrew.46 on 2007-11-01
Hi,

 Glad my guide has helped you:

> **garybrlow said:**
> [...]Everything works as it should except that when playing files with blank spaces in the filename it lets out an error saying it can not play the file because it can not be found. If you rename the file removing the blank spaces it plays fine. The same thing happens if the file is located in a directory with blank spaces even if the filename is without blank spaces. This behavior should not be happening but it is. [...]

 This behaviour is quite normal for Linux, space in filenames and directories is something to be avoided at all costs unless you want to write and elaborate series of escapes for every file and directory you have. Some of the gui tools shield you from this which shows one of the many drawbacks of gui tools.

Try quotation marks around filnames with spaces: "filename wirh spaces.txt" for example. 

                   Andrew

---

### Post by kaambiz on 2007-11-02
works perfect. that's awsome. thanks man.

---

### Post by andrew.46 on 2007-11-02
Hi:
> **kaambiz said:**
> works perfect. that's awsome. thanks man.

 My pleasure :-)

           Andrew

---

### Post by thepaulmorris on 2007-11-03
Hello all! I am having some serious problems with mPlayer and streaming all internet radio stations!!! First and foremost I am running Gutsy. I followed the installation instructions to the 'T" on the first page of this post and my first wall that I hit is when I do ./configure I receive the following

[INDENT]./configure
Detected operating system: Linux
Detected host architecture: i386
Checking for cc version ... 4.1.3, ok 
Checking for host cc ... cc 
Checking for cross compilation ... yes 
Checking for CPU vendor ... AuthenticAMD (15:72:2) 
Checking for CPU type ...  AMD Turion(tm) 64 X2 Mobile Technology TL-50 
Checking for kernel support of mmx ... failed 
It seems that your kernel does not correctly support mmx.
To use mmx extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of mmxext ... failed 
It seems that your kernel does not correctly support mmxext.
To use mmxext extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of 3dnow ... failed 
It seems that your kernel does not correctly support 3dnow.
To use 3dnow extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of 3dnowext ... failed 
It seems that your kernel does not correctly support 3dnowext.
To use 3dnowext extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of sse ... failed 
It seems that your kernel does not correctly support sse.
To use sse extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of sse2 ... failed 
It seems that your kernel does not correctly support sse2.
To use sse2 extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of cmov ... failed 
It seems that your kernel does not correctly support cmov.
To use cmov extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for mtrr support ... yes 
Checking for GCC & CPU optimization abilities ... CPU optimization disabled. CPU not recognized or your compiler is too old. 
error 
Checking for assembler support of -pipe option ... no 
Checking for compiler support of named assembler arguments ... yes 
Checking for assembler (as ) ... ok 
Checking for .align is a power of two ... no 
Checking for Linux kernel version ... 2.6.22-14-generic, ok 
Checking for -lposix ... no 
Checking for -lm ... no 
Checking for langinfo ... no 
Checking for language ... using en (man pages: en ) 
Checking for enable sighandler ... yes 
Checking for runtime cpudetection ... no 
Checking for restrict keyword ... none 
Checking for __builtin_expect ... no 
Checking for kstat ... no 
Checking for posix4 ... no 
Checking for lrintf ... no 
Checking for mkstemp ... no 
Checking for nanosleep ... no 
Checking for socklib ... no 
Checking for inet_pton() ... no (trying inet_aton next)
Checking for inet_aton() ... no (network support disabled)
Checking for network ... no 
Checking for inttypes.h (required) ... no 
Checking for bitypes.h (inttypes.h predecessor) ... 
Error: Cannot find header either inttypes.h or bitypes.h. There is no chance for compilation to succeed.

Check "configure.log" if you do not understand why it failed.[/INDENT]

I checked the configure.log and I am not familiar enough with the Linux language yet to fully understand what the issue is. So what I did (out of frustration) I ignored the error message above and continued on with the installation. I can get MPlayer to open both from Applications and from Terminal, the skin works and all.  Now I have the MediaConnectivity plug-in installed for Firefox and it is setup to have gmplayer be the player for all file types. When I click what should be an internet radio station, lets take NPR for example I receive the following error:

Failed to open icy-url:[http://www.shoutcast.com](http://www.shoutcast.com).  When trying to open a sirius channel, MPlayer opens and I receive a similar error. I installed all of the codecs per the instructions on page 1. 

Prior to this installation attempt I installed MPLayer from Synaptic and I was still unable to play any internet radio streams, all other forms of sound work, videos, CD's systems sounds, etc. Except for streaming video and radio. I am wondering if the issue I am having getting streaming media to work is related to the same issue I am having with Sipie. If anyone isnt familiar with Sipie (ignore the last sentence) Sipie works perfectly except for sound!! This all is very frustrating!! To the point that I am considering re-imaging my laptop and I really don't want to!! Anyone that could possibly help it would be greatly appreciated!!!


Thank You,

Paul

**EDIT**
*I ran mplayer from terminal using the command mplayer (stream location) and this worked. When I ran the command gmplayer (stream location) I still receive the errors stated above. So I guess this can be a temporary stopgap but any insight would be appreciated on the issues I am having.*

---

### Post by andrew.46 on 2007-11-04
Hi Paul,

 Sorry to hear you are having such trouble:

> **thepaulmorris said:**
> Hello all! I am having some serious problems with mPlayer and streaming all internet radio stations!!! First and foremost I am running Gutsy. I followed the installation instructions to the 'T" on the first page of this post and my first wall that I hit is when I do ./configure I receive the following [....]

 You might be best to uninstall mplayer by changing to the source directory and issuing this command:

```
$ sudo make uninstall
$ make clean
```

 My only thought is that perhaps there is an AMD 64 problem. The faqs speak of this:

[http://www.mplayerhq.hu/DOCS/HTML/en/faq.html#id2552970](http://www.mplayerhq.hu/DOCS/HTML/en/faq.html#id2552970)

 But I am afraid that my experience with the AMD 64 chip and compiling mplayer is zero :confused: You could try the directions on the faqs but I am not in a position to test them myself to guarantee their effectiveness or suitability for your particular AMD chip.

 An alternative is to post on the Mplayer Users list:

[http://lists.mplayerhq.hu/mailman/listinfo/mplayer-users](http://lists.mplayerhq.hu/mailman/listinfo/mplayer-users)

 Be aware some of the users can be a little terse but the information gained there is almost always worthwhile.

 Sorry I cannot be much more help than this!

                    Andrew

---

### Post by episodic on 2007-11-04
Everything works fine but this. It does not seem to install a plugin that firefox sees at all. Can you advise?

> **shirilover said:**
> You can also build mplayerplug-in as well.
The latest version 3.4.5 works well for me.

I'm going to assume you have already successfully built mplayer.
First, we need to grab the source.
```

wget http://internap.dl.sourceforge.net/sourceforge/mplayerplug-in/mplayerplug-in-3.45.tar.gz
tar -xzvf mplayerplug-in-3.45.tar.gz
cd mplayerplug-in

```

Also, we need the firefox development files
```

sudo apt-get install firefox-dev libnss-dev libnspr-dev

```

Now, we can build the plugin.
```

./configure
make
make install

```
make install will install the plugin to your firefox profile directory, usually ~/.mozilla/plugins. If you wish to make them globally available, use sudo make install instead.

---

### Post by andrew.46 on 2007-11-05
Hi,

 Glad that you have successfully installed the svn mplayer:

> **episodic said:**
> Everything works fine but this. It does not seem to install a plugin that firefox sees at all. Can you advise?

 but unfortunately I have no experience with this plugin and in fact I have never installed it. Your quote is from someone else I suspect who has volunteered this information?

                   Andrew

---

### Post by hype on 2007-11-25
Hey, 
i'm getting this error a few seconds after "make";

```

command.c:1001: warning: passing argument 2 of 'set_video_colors' discards qualifiers from pointer target type
command.c:1008: warning: passing argument 2 of 'get_video_colors' discards qualifiers from pointer target type
command.c:1017: warning: passing argument 2 of 'set_video_colors' discards qualifiers from pointer target type
command.c: In function 'mp_property_sub_source':
command.c:1393: error: 'MSGTR_SubSourceFile' undeclared (first use in this function)
command.c:1393: error: (Each undeclared identifier is reported only once
command.c:1393: error: for each function it appears in.)
command.c:1396: error: 'MSGTR_SubSourceVobsub' undeclared (first use in this function)
command.c:1399: error: 'MSGTR_SubSourceDemux' undeclared (first use in this function)
command.c: At top level:
command.c:2015: error: 'MSGTR_SubSourceStatus' undeclared here (not in a function)
make: *** [command.o] Erreur 1

```

Should i just wait for some mplayer svn updates? :p

---

### Post by ildfroe on 2007-11-25
Hi,
I get the same error :-(

Edit:

It works now :-) I guess the mplayer-guys fixed the bug.:)
Update your source folder and make again.
```
cd mplayer
svn update
make
sudo make install
```

Or use sudo checkinstall to build a .deb package. Go to synaptic and lock the version, and then you can install the mozilla plugin from the repos.

---

### Post by andrew.46 on 2007-12-10
Hi,

 Wooo hooo!!! Almost 10,000 views of this walkthrough!!  I am hoping for an Ubuntu T-shirt or a coffee mug when it hits the big 10,000 :-)

Hopefully a lot of people have just sailed through it with great success, I know there have been some with problems; it is a difficult bit of software to compile from source.

           Andrew

---

### Post by andrew.46 on 2007-12-10
Hi,

 Glad it sorted itself out:

> **ildfroe said:**
>  It works now :-) I guess the mplayer-guys fixed the bug.:)
[...] use sudo checkinstall to build a .deb package. Go to synaptic and lock the version, and then you can install the mozilla plugin from the repos.

 I thought for some time about using checkinstall in this walkthrough, particularly when I saw that the mozilla plugin wanted to drag in the repository mplayer with it.

But checkinstall introduced a few potential problems with it that I was not keen to troubleshoot. I reasoned eventually that anybody cluey enough to run through a walkthrough that involved svn and compiling from source could make their own way with checkinstall :)

But perhaps if anyone writes a similar guide for Hardy Heron checkinstall might feature as it ties mplayer back into the Ubuntu package management system.

        Andrew

---

### Post by tachibana on 2007-12-28
Thank you, thank you, thank you so much!!!!!!

---

### Post by andrew.46 on 2007-12-28
Hi:

> **tachibana said:**
> Thank you, thank you, thank you so much!!!!!!

And thank you for your message :-)

       Andrew

---

### Post by Shakey_Jake33 on 2008-01-06
Apologies if this has been answered, but I'm assuming we just follow the process in the guide every time a new SVN build is released?

Does this process also give us the newest ffmpeg build?  Sorry if that's an obvious question.

I've just come over from Windows, and I know a bit about setting up Directshow codecs, been using ffdshow-tryouts for most uses for the past 2 years, obviously that's based on ffmpeg (usually the latest SVN).

---

### Post by andrew.46 on 2008-01-06
Hi,

 Thanks for your message:

> **Shakey_Jake33 said:**
> Apologies if this has been answered, but I'm assuming we just follow the process in the guide every time a new SVN build is released?

The good news is that only part of the process needs to be repeated. If you change to the directory that holds the source code and issue the command:

```
svn update
```you only then need to repeat the actual compile process. You will find it hard to keep up with the svn process as the updates roll in every day, almost without exception. Just keep a record of the revision number as sometimes a revision will break mplayer. If this is the case the following syntax will return the successful version:

```
svn checkout -r <revision> svn://svn.mplayerhq.hu/mplayer/trunk mplayer
```where <revision> represents the "safe" version (without the angle brackets).

>  Does this process also give us the newest ffmpeg build?  Sorry if that's an obvious question.The svn mplayer imports the most recent ffmpeg build. If you watch the svn process you will see this happening, watch for 'importing into livavcodec' etc

>  I've just come over from Windows, and I know a bit about setting up Directshow codecs, been using ffdshow-tryouts for most uses for the past 2 years, obviously that's based on ffmpeg (usually the latest SVN).The 2007 codec pack requires nothing more that to placed in the appropriate directory and sourced by mplayer. However my knowledge of Directshow codecs is simply that mplayer uses them successfully :-)

I wish you all the best with the svn mplayer. Subversion itself has a wealth of options that are well worth exploring if you have an interest.

 Regards,

   Andrew Strong

---

### Post by pritamps on 2008-01-07
Thanks for your guide! It worked like a charm. I was reading as I was "make"ing, so I uninstalled the mplayer that I had, used checkinstall and them compiled the plugin too!

Thanks!!

I'm just waiting for the day when we can rewind and fast-forward divx videos in linux :)

> **andrew.46 said:**
> **Introduction**

This guide intends to show how to successfully compile a *fully featured* svn mplayer with *all* the codecs and with the GUI player gmplayer. It is designed for the Ubuntu distro Gutsy Gibbon but will work with Dapper, Edgy or Feisty with adjustments to the required dev files, but this is not covered in this 'Howto'. Mplayer is a bit of a difficult one to compile so first make yourself a cup of tea and then get your keyboard ready!!

**Note**: *Downloading mplayer using subversion means that you will get the very latest version of this amazing software with all the latest features. But it also exposes you to the newest bugs and problems. If you value safety and stability in your system rather than access to cutting edge versions use the Ubuntu Repository mplayer instead.*

**First of the Downloads**

Still with me? Firstly install subversion + compiling tools and then download the svn mplayer plus the full codec pack:

```
$ sudo apt-get install build-essential subversion 
$ cd Desktop
$ svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer
$ wget http://www.mplayerhq.hu/MPlayer/releases/codecs/all-20071007.tar.bz2
```So far so good? Next to decompress the codec package and copy all them to the appropriate location. Make sure you are still on the Desktop and:

```
$ sudo mkdir -v /usr/local/lib/codecs
$ tar xjvf all-20071007.tar.bz2
$ sudo cp -v all-20071007/* /usr/local/lib/codecs
```**All the *dev* files**

Next comes quite a large download of development files, about 50 megs. These are required so that when mplayer is compiled you will pick up a huge amount of functionality. Don't be surprised if more are suggested, or if you already have some on your system.

 **Note:** *These dev files are specific to Gutsy Gibbon, there will be different requirements, not covered in this guide, for Feisty, Edgy and Dapper.*

```
$ sudo apt-get install avifile-divx-plugin avifile-xvid-plugin gawk \
libxcursor-dev ladspa-sdk liba52-0.7.4 liba52-0.7.4-dev libaa1-dev libartsc0 \
libartsc0-dev libasound2-dev libatk1.0-dev libaudiofile-dev libavcodec1d libavcodec-dev \
libavformat1d libavformat-dev libavifile-0.7c2 libavifile-0.7-dev libavutil1d \
libavutil-dev libcaca-dev libcairo2-dev libcdparanoia0-dev libcucul-dev libdv4-dev \
libdirectfb-dev libdirectfb-extra libdbus-1-dev libdbus-glib-1-dev libdc1394-13 \
libdc1394-13-dev libdfb++-0.9-25 libdfb++-dev libdts-dev libdvdnav4 libdvdnav-dev \
libdvdread3 libdvdread-dev libebml0 libebml-dev libenca0 libenca-dev libesd0-dev \
libexpat1-dev libfaac0 libfaac-dev libfaad2-0 libfaad2-dev libfame-0.9 libfame-dev \
libflac++6 libflac-dev libflac++-dev libfontconfig1-dev libfontenc-dev libfreetype6-dev \
libfribidi-dev libgdk-pixbuf2 libgdk-pixbuf-dev libgii1 libgii1-dev libgii1-target-x \
libgl1-mesa-dev libglib1.2 libglib1.2-dev libglib2.0-dev libglu1-mesa-dev \
libglu1-xorg-dev libgsm1 libgsm1-dev libgtk1.2 libgtk1.2-common libgtk1.2-dev \
libgtk2.0-dev libice-dev libggi2 libggi2-dev libggimisc2 libggimisc2-dev libggiwmh0 \
libggiwmh0-dev libjpeg62-dev liblame0 liblame-dev liblivemedia-dev liblzo1 liblzo-dev \
liblzo2-2 liblzo2-dev libmad0 libmad0-dev libmatroska0 libmatroska-dev libmikmod2 \
libmikmod2-dev libmp4v2-0 libmp4v2-dev libmpcdec3 libmpcdec-dev libncurses5-dev \
libogg-dev libpango1.0-dev libpng12-dev libpopt-dev libpostproc1d libpostproc-dev \
libraw1394-dev libsdl1.2-dev libslang2-dev libsmbclient-dev libsm-dev libspeex-dev \
libsvga1 libsvga1-dev libsysfs-dev libtheora-dev libungif4-dev libungif4g \
libvorbis-dev libx11-dev libx264-54 libx264-dev libxau-dev libxcomposite-dev \
libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev libxfont-dev libxft-dev \
libxi-dev libxinerama-dev libxrandr-dev libxrender-dev libxsharp-dev libxv-dev \
libxvidcore4 libxvidcore4-dev libxvmc1 libxvmc-dev libxxf86dga-dev libxxf86vm-dev \
mesa-common-dev pnet-interpreter sharutils toolame ttf-bitstream-vera \
x11proto-composite-dev x11proto-core-dev x11proto-damage-dev \
x11proto-fixes-dev x11proto-fonts-dev x11proto-input-dev x11proto-kb-dev \
x11proto-randr-dev x11proto-render-dev x11proto-video-dev x11proto-xext-dev \
x11proto-xf86dga-dev x11proto-xf86vidmode-dev x11proto-xinerama-dev \
xlibs-static-dev xtrans-dev zlib1g-dev
```[B]

Optional Step: H264[/B]

If you are keen to use [H.264 encoding]("http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-x264.html") at some stage you would be best to also compile the latest x264 source code *before* compiling mplayer. To do this the following commands will log you onto the Videolan x264 subversion repository, download the source code and compile it:

```
$ cd Desktop
$ svn co svn://svn.videolan.org/x264/trunk x264
$ cd x264
$ ./configure
$ make
$ sudo make install
```mplayer will pick this up automatically during its configure process and H.264 encoding will then be available to you. Remember this is an optional step and mplayer will run quite happily without it. As well it is a step that that can be added in at a later stage as long as you follow the sequence:[LIST=1]
[*]Compile and install H.264 source code
[*]Compile and install mplayer source code[/LIST]**Installation**

The next task is to compile the svn mplayer, setup a font for the OSD and organise a skin for the GUI:

```
$ cd $HOME/Desktop/mplayer
$ ./configure \
--prefix=/usr/local \
--enable-largefiles \
--enable-gui \
--codecsdir=/usr/local/lib/codecs
$ make 
$ sudo make install
```The next step is to place a symbolic link to a font for the OSD (On Screen Display) and subtitles. At the same time we will create the directory structure for the mplayer skin:

```
$ cd $HOME
$ mkdir -pv .mplayer/skins/default
$ ln -sv /usr/share/fonts/truetype/ttf-bitstream-vera/Vera.ttf ~/.mplayer/subfont.ttf
```And finally to set up a skin for the GUI. Can I say that I rarely use the GUI but in the spirit of generosity, Gentle Reader, I have included the directions on this page for a basic skin and access to gmplayer, the GUI version of mplayer. So, you now need to download a skin, decompress it and then place it in the appropriate directory:

```
$ cd Desktop
$ wget http://www.mplayerhq.hu/MPlayer/skins/Blue-1.7.tar.bz2
$ tar xjvf Blue-1.7.tar.bz2 
$ cp -Rv $HOME/Desktop/Blue/* $HOME/.mplayer/skins/default
```And you have successfully installed the svn mplayer! You can check the options available for you with the following commands:[LIST=1]
[*]**mplayer -vo help** : Video output available to mplayer
[*]**mplayer -ao help** : Audio output available to mplayer
[*]**mencoder -ovc help** : Video encoding available to mencoder
[*]**mencoder -oac help** : Audio encoding available to mencoder[/LIST]Start both from the command line, the CLI version with the command **mplayer**, the GUI with **gmplayer** and the movie encoder with **mencoder**. And remember: "Have fun!".

  Andrew

---

### Post by andrew.46 on 2008-01-07
Hi,

 Thanks for your message:

> **pritamps said:**
> Thanks for your guide! It worked like a charm. I was reading as I was "make"ing, so I uninstalled the mplayer that I had, used checkinstall and them compiled the plugin too!

Glad it all worked well! There have been a few problems with some versions of the svn mplayer over the New Year I noticed, but all fixed within 24 hours. It is always a good idea to subscribe to the mplayer-users list as well just to keep on top of any problems:

[http://lists.mplayerhq.hu/mailman/listinfo/mplayer-users](http://lists.mplayerhq.hu/mailman/listinfo/mplayer-users)

> I'm just waiting for the day when we can rewind and fast-forward divx videos in linux :)Hmmm.... I will take your word for that as I temporarily don't have any mpeg4 / Divx movies to hand. Do the following keys not work:

>  <-  or  ->       seek backward/forward 10 seconds
 down or up       seek backward/forward  1 minute
 pgdown or pgup   seek backward/forward 10 minutesAll the best,

   Andrew

---

### Post by pritamps on 2008-01-07
They work when I download the video, but not when the video is embedded on a site. 

Thanks for the tip about the mplayer list. I will subscribe to it!

-Pritam

---

### Post by Shakey_Jake33 on 2008-01-07
> **andrew.46 said:**
> Hi,

 Thanks for your message:



The good news is that only part of the process needs to be repeated. If you change to the directory that holds the source code and issue the command:

```
svn update
```you only then need to repeat the actual compile process. You will find it hard to keep up with the svn process as the updates roll in every day, almost without exception. Just keep a record of the revision number as sometimes a revision will break mplayer. If this is the case the following syntax will return the successful version:

```
svn checkout -r <revision> svn://svn.mplayerhq.hu/mplayer/trunk mplayer
```where <revision> represents the "safe" version (without the angle brackets).

The svn mplayer imports the most recent ffmpeg build. If you watch the svn process you will see this happening, watch for 'importing into livavcodec' etc

The 2007 codec pack requires nothing more that to placed in the appropriate directory and sourced by mplayer. However my knowledge of Directshow codecs is simply that mplayer uses them successfully :-)

I wish you all the best with the svn mplayer. Subversion itself has a wealth of options that are well worth exploring if you have an interest.

 Regards,

   Andrew Strong

Sounds good, thanks :)

One other quick thing, I prefer to use smplayer as a frontend... if I install smplayer, would it be using these new SVN files, or it's own mplayer build?  I mainly prefer smplayer for the superior deinterlace options.

---

### Post by andrew.46 on 2008-01-07
Hi,

> **pritamps said:**
> They work when I download the video, but not when the video is embedded on a site. 

In that case unfortunately you will have to chase up the mplayer plugin and I do not know a great deal about it, although I do have it installed on my system.

I note a mailing list for the mplayer pluhin at:

[https://lists.sourceforge.net/lists/listinfo/mplayerplug-in-devel](https://lists.sourceforge.net/lists/listinfo/mplayerplug-in-devel)

All the best with mplayer though, it is an amazing program.

    Andrew

---

### Post by andrew.46 on 2008-01-07
Hi again!

> **Shakey_Jake33 said:**
> Sounds good, thanks :)

One other quick thing, I prefer to use smplayer as a frontend... if I install smplayer, would it be using these new SVN files, or it's own mplayer build?  I mainly prefer smplayer for the superior deinterlace options.

I have heard a lot about smplayer but never tried it, mostly because the tru power of mplayer is in the command line. Hence the rather poor gui that comes with mplayer :-)

But I downloaded the tarball just to investigate and I found the following in the FAQs:

> **23) What version of MPlayer is recommended?**

SMPlayer requires at least MPlayer 1.0rc1. It hasn't been tested with older releases, and it uses some options only available from 1.0rc1, like -vf screenshot or --***..
If you use an older version and see that something doesn't work as it should, before reporting a bug I suggest to update MPlayer.

Anyway I recommend to use a svn MPlayer. There are several things that have been improved from version 1.0rc1. For instance now you can change the audio language in avi files, seeking works better in flv and ogm (and maybe other formats). One thing that has really been improved is the SSA/*** library for subtitles.

In the [MPlayer download page]("http://www.mplayerhq.hu/design7/dload.html") you can get a svn tar.bz2 ready to compile. And compiling it is very easy (in linux, I mean...)So I guess you should be right with both svn mplayer and smplayer. I will admit the gui on the website looks *very* nice :-)

   Andrew

PS For some anti-swearing reason the forum is disguising the letters a s s in the quoted material!!!

---

### Post by Shakey_Jake33 on 2008-01-07
Just to let you know, smplayer *can* be used with the SVN, but the deb version and repository automatically grabs the version of mplayer from the repository.  Synaptic doesn't actually seem to realise mplayer has been installed, so it assumes it's not and tries to grab it from repository (old rc1!).  Had to remove mplayer and start again.

So I grabbed the tar from the smplayer page and compiled it using the instructions (my first ever compile woo!), and all works great!  I feel rather pleased with myself =P

Hah, experienced Linux users say command line is best - I'm sure I'll learn one day why!  I just like smplayer because I can right-click->deinterlace at will.

---

### Post by mrdustinf on 2008-01-07
Im not sure if anyone else is having this problem or not. Im trying to install Mplayer using your walkthrough but Im installing it on the PS3 with Gutsy. 

When it trys to install the dev files you have listed the first one gives an error
E: Couldn't find package avifile-divx-plugin

Im very new to linux so any help will be appreciated. Thanks alot.

---

### Post by Shakey_Jake33 on 2008-01-07
I'd imagine it would not work, as the PS3 would require specific PowerPC builds.

But there is a guide on here about installing a custom PS3 mplayer build [http://linux.yes.nu/PS3Ubuntu/](http://linux.yes.nu/PS3Ubuntu/)

---

### Post by andrew.46 on 2008-01-07
Hi,

Took me a while to realise that you meant Play Station 3 :-) Obviously I am a little behind the times as I had no idea a Linux distro could be placed on such a machine!

> **mrdustinf said:**
> Im not sure if anyone else is having this problem or not. Im trying to install Mplayer using your walkthrough but Im installing it on the PS3 with Gutsy. 

When it trys to install the dev files you have listed the first one gives an error
E: Couldn't find package avifile-divx-plugin

Im very new to linux so any help will be appreciated. Thanks alot.

Nevertheless the [avifile-divx-plugin]("http://packages.ubuntu.com/gutsy/libs/avifile-divx-plugin") does exist, but you will have to enable the multiverse repositories. From the following page:

[http://packages.ubuntu.com/gutsy/allpackages](http://packages.ubuntu.com/gutsy/allpackages)

> **[avifile-divx-plugin]("http://packages.ubuntu.com/gutsy/libs/avifile-divx-plugin")** (1:0.7.47.20070718-1ubuntu2) [multiverse]
Divx4Linux video de/encoding plugin for libavifile

Best place to look at changing your sources list is:

[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

Good luck with the PS3 thing :-)

     Andrew

---

### Post by Shakey_Jake33 on 2008-01-08
Linux is supported on PS3 completely officially, endorsed by Sony, no modification needed :)  Just install from CDR.  Unfortunately it runs in some kind of hypervisor mode with limited access to the hardware, hence the ps3-modified versions of certain files found in the link I posted.  Even then, it only just about manages standard definition files :(

---

### Post by andrew.46 on 2008-01-09
Hi!

Wooooooo hoooooooooooooo!!!! 12,000 views!!!!! What about a free Ubuntu T-shirt *and* a coffee mug????!!!!!

      Andrew

---

### Post by andrew.46 on 2008-01-15
Hi,

 If anybody is interested I have rejoined the Ubuntu ranks with a dual boot Slackware / Ubuntu system and high on the agenda is a reworked version of this 'Howto' for Hardy Heron when it comes out.

I have in mind roughly the same format but differences will be:[LIST=1]
[*]Different -dev files of course
[*]Installation of some extra 'skins' + description of skin browser
[*]Addition of checkinstall in the installation
[*]Description of version locking to prevent Repository 'updating'
[*]Anything anybody suggests in the next month or two :-)[/LIST]Andrew

---

### Post by hype on 2008-01-15
Hey, first thanks for great post.
I'm just having a little issue since some weeks now installing mplayer 1.0 rc2.

I just used ./configure --enable-largefiles --enable-gui , make goes fine, but after installing, my side buttons (mouse 6 and 7) wont control volume anymore.
I tried editing the inputrc file, as advised on mplayer's mailing list but without succes.

Just wondering if anyone here had the same issue?

Note: i used svn mplayer.

---

### Post by csulok on 2008-01-15
hey

lately i've been having problems compiling mplayer, after updating from the svn

```
./configure --enable-gui --enable-largefiles
```

returns:

```
Detected operating system: Linux
Detected host architecture: i386
Checking for cc version ... 4.1.3, ok 
Checking for host cc ... cc 
Checking for cross compilation ... yes 
Checking for CPU vendor ... GenuineIntel (6:15:6) 
Checking for CPU type ...  Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz 
Checking for kernel support of mmx ... failed 
It seems that your kernel does not correctly support mmx.
To use mmx extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of mmxext ... failed 
It seems that your kernel does not correctly support mmxext.
To use mmxext extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of sse ... failed 
It seems that your kernel does not correctly support sse.
To use sse extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of sse2 ... failed 
It seems that your kernel does not correctly support sse2.
To use sse2 extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of ssse3 ... failed 
It seems that your kernel does not correctly support ssse3.
To use ssse3 extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of cmov ... failed 
It seems that your kernel does not correctly support cmov.
To use cmov extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for mtrr support ... yes 
Checking for GCC & CPU optimization abilities ... CPU optimization disabled. CPU not recognized or your compiler is too old. 
error 
Checking for assembler support of -pipe option ... no 
Checking for compiler support of named assembler arguments ... yes 
Checking for assembler (as ) ... ok 
Checking for .align is a power of two ... no 
Checking for Linux kernel version ... 2.6.22-14-generic, ok 
Checking for -lposix ... no 
Checking for -lm ... no 
Checking for langinfo ... no 
Checking for language ... using en (man pages: en ) 
Checking for enable sighandler ... yes 
Checking for runtime cpudetection ... no 
Checking for restrict keyword ... none 
Checking for __builtin_expect ... no 
Checking for kstat ... no 
Checking for posix4 ... no 
Checking for llrint ... no 
Checking for lrint ... no 
Checking for lrintf ... no 
Checking for round ... no 
Checking for roundf ... no 
Checking for mkstemp ... no 
Checking for nanosleep ... no 
Checking for socklib ... no 
Checking for inet_pton() ... no (trying inet_aton next)
Checking for inet_aton() ... no (network support disabled)
Checking for network ... no 
Checking for inttypes.h (required) ... no 
Checking for bitypes.h (inttypes.h predecessor) ... 
Error: Cannot find header either inttypes.h or bitypes.h. There is no chance for compilation to succeed.

Check "configure.log" if you do not understand why it failed.

```

Any ideas as to what causes the problem and how I can fix it?

PS: I'm using the official kernel packages

---

### Post by andrew.46 on 2008-01-15
Hi,

Sorry to see that you are having a little trouble:

> **csulok said:**
> hey
lately i've been having problems compiling mplayer, after updating from the svn


I will have to admit it does *not* sound like a specifically svn problem. There are 2 things you could try:

[LIST=1]
[*]Try to backtrack to the last successful svn version that you used. To do this simply add -R <revision number> to the svn command.
[*]Try to compile the mplayer rc2 instead.[/LIST]Mplayer rc2 can be found at:

[http://www3.mplayerhq.hu/MPlayer/releases/MPlayer-1.0rc2.tar.bz2](http://www3.mplayerhq.hu/MPlayer/releases/MPlayer-1.0rc2.tar.bz2)

  All the best,

   Andrew

---

### Post by shirilover on 2008-01-16
In case you have wondered why checking for dvdnav has resulted in no, it is because mplayer now depends on the libdvdnav source maintained by the MPlayer project.

First remove the old version od libdvdnav:
```

sudo apt-get remove libdvdnav4

```
Then, we will compile and install the newer version, at least until the Ubuntu developers decide to start using the new source files:
```

svn co svn://svn.mplayerhq.hu/dvdnav/trunk/libdvdnav libdvdnav
cd libdvdnav
./autogen.sh --enable-static --enable-shared --prefix=/usr
make
sudo make install

```
Then proceed with compiling mplayer-svn.
For those of you that are using checkinstall to create a deb file of mplayer, you should instead use:
```

fakeroot debian/rules binary

```

---

### Post by csulok on 2008-01-19
> **andrew.46 said:**
> Hi,

Sorry to see that you are having a little trouble:



I will have to admit it does *not* sound like a specifically svn problem. There are 2 things you could try:

[LIST=1]
[*]Try to backtrack to the last successful svn version that you used. To do this simply add -R <revision number> to the svn command.
[*]Try to compile the mplayer rc2 instead.[/LIST]Mplayer rc2 can be found at:

[http://www3.mplayerhq.hu/MPlayer/releases/MPlayer-1.0rc2.tar.bz2](http://www3.mplayerhq.hu/MPlayer/releases/MPlayer-1.0rc2.tar.bz2)

  All the best,

   Andrew

I can't compile the 1.0rc2 build, I get the exact same messages.
I can't compile revision 25426 either, exact same message, even though i successfully compiled it on december 16th and i'm using that package right now.

It has nothing to do with mplayer i'm afraid. there was an ubuntu kernel update during my xmas holiday, that upgraded the kernel from 2.6.22-13 to 2.6.22-14. i suspect this to be the cause (the error messages state something similar too), but i can't downgrade to confirm it :/

---

### Post by andrew.46 on 2008-01-19
Hi,

 If a kernel update is the problem:

> **csulok said:**
> 
It has nothing to do with mplayer i'm afraid. there was an ubuntu kernel update during my xmas holiday, that upgraded the kernel from 2.6.22-13 to 2.6.22-14. i suspect this to be the cause (the error messages state something similar too), but i can't downgrade to confirm it :/

you actually can either temporarily or permanently use the older kernel. Depending how Grub is set on your system press 'Esc' when you see the Grub menu on the initial bootup and select the older kernel.

If this is the problem you can change the boot order by editing /boot/grub/menu.lst.

            Andrew

---

### Post by jocheem67 on 2008-01-20
Well , I' ve been struggling bigtime with the whole thing:

I really want the mozilla-mplayer and smplayer working. As stated before smplayer really wants to install the ubuntu-deb of mplayer, resulting in two mplayers ( usr/bin and usr/local/bin ) ....hmmm...not that pretty...
mozilla-mplayer also tries to force a secondary mplayer onto your system.

Well I used the advice to use checkinstall, so i ended up with the command

[HTML]sudo checkinstall && sudo make install[/HTML]

This resulted in a .deb and in the fact that mplayer is now registered with synaptic..there I just locked the mplayer I compiled and voila smplayer and mozilla-mplayer no longer nag about mplayer needed to be installed. Just fooled the two of them....

A nice little dirty trick...

thanks for the howto and this trick by ?? somewhere in this thread!

---

### Post by andrew.46 on 2008-01-20
Hi,

 Glad you finally managed to install mplayer to your satisfaction:

> **jocheem67 said:**
> Well , I' ve been struggling bigtime with the whole thing: [...]

Well I used the advice to use checkinstall, so i ended up with the command

[html]sudo checkinstall && sudo make install[/html]This resulted in a .deb and in the fact that mplayer is now registered with synaptic..there I just locked the mplayer I compiled and voila smplayer and mozilla-mplayer no longer nag about mplayer needed to be installed. Just fooled the two of them....


I will be writing a similar howto for Hardy Heron and I suspect that checkinstall will feaure. I am not such a big fan of the program but many people have asked for it. Your syntax was a little wayward though, should be:
```
$ ./configure
$ make
$ sudo checkinstall -D
```

with the usual ./configure options added in. The -D option for Checkinstall specifies a debian package, checkinstall can also produce an rmp and tgz package.

All the best with mplayer!

            Andrew

---

### Post by aBitLater on 2008-01-20
Thanks for this post.

I can't seem to get mplayer compiled.  After, "./configure --prefix=/usr/local --enable-largefiles --enable-gui --codecsdir=/usr/local/lib/codec", I do "make" and this is what I get.. errors.

Any ideas?

Thanks

> 
./version.sh `cc -dumpversion`
cc -I./libavcodec -I./libavformat -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -I. -I./libavutil -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DHAVE_CONFIG_H -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT -I/usr/include/kde/artsc -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/freetype2 -I/usr/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12     -c -o mplayer.o mplayer.c
In file included from mplayer.c:807:
cfg-mplayer.h:352: warning: initialization discards qualifiers from pointer target type
In file included from cfg-mplayer.h:358,
                 from mplayer.c:807:
cfg-common.h:11: warning: initialization discards qualifiers from pointer target type
cfg-common.h:145: warning: initialization discards qualifiers from pointer target type
cfg-common.h:152: warning: initialization discards qualifiers from pointer target type
cfg-common.h:157: warning: initialization discards qualifiers from pointer target type
cfg-common.h:161: warning: initialization discards qualifiers from pointer target type
cfg-common.h:163: warning: initialization discards qualifiers from pointer target type
cfg-common.h:204: warning: initialization discards qualifiers from pointer target type
cfg-common.h:229: warning: initialization discards qualifiers from pointer target type
cfg-common.h:252: warning: initialization discards qualifiers from pointer target type
cfg-common.h:255: warning: initialization discards qualifiers from pointer target type
cfg-common.h:258: warning: initialization discards qualifiers from pointer target type
In file included from mplayer.c:807:
cfg-mplayer.h:367: warning: initialization discards qualifiers from pointer target type
mplayer.c: In function 'reinit_video_chain':
mplayer.c:2018: warning: passing argument 1 of 'vf_open_plugin' from incompatible pointer type
mplayer.c: In function 'main':
mplayer.c:2747: warning: passing argument 2 of 'guiGetEvent' from incompatible pointer type
cc -I./libavcodec -I./libavformat -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -I. -I./libavutil -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DHAVE_CONFIG_H -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT -I/usr/include/kde/artsc -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/freetype2 -I/usr/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12     -c -o vobsub.o vobsub.c
make -C libvo libvo.a
make[1]: Entering directory `/home/brianphillips/Desktop/mplayer/libvo'
cc -I../libavcodec -I../libavformat -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -I.. -I../libavutil -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DHAVE_CONFIG_H -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT -I/usr/include/kde/artsc -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/freetype2 -I/usr/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12     -c -o vo_ivtv.o vo_ivtv.c
vo_ivtv.c: In function 'ivtv_reset':
vo_ivtv.c:79: error: storage size of 'sd' isn't known
vo_ivtv.c:80: error: storage size of 'sd1' isn't known
vo_ivtv.c:84: error: 'IVTV_STOP_FL_HIDE_FRAME' undeclared (first use in this function)
vo_ivtv.c:84: error: (Each undeclared identifier is reported only once
vo_ivtv.c:84: error: for each function it appears in.)
vo_ivtv.c:87: error: 'IVTV_IOC_STOP_DECODE' undeclared (first use in this function)
vo_ivtv.c:97: error: 'IVTV_IOC_START_DECODE' undeclared (first use in this function)
vo_ivtv.c:80: warning: unused variable 'sd1'
vo_ivtv.c:79: warning: unused variable 'sd'
vo_ivtv.c: In function 'flip_page':
vo_ivtv.c:243: warning: passing argument 6 of 'send_mpeg_pes_packet' from incompatible pointer type
make[1]: *** [vo_ivtv.o] Error 1
make[1]: Leaving directory `/home/brianphillips/Desktop/mplayer/libvo'
make: *** [libvo/libvo.a] Error 2



---

### Post by andrew.46 on 2008-01-20
Hi,

 Sorry you are having some trouble:

> **aBitLater said:**
> Thanks for this post.

I can't seem to get mplayer compiled.  After, "./configure --prefix=/usr/local --enable-largefiles --enable-gui --codecsdir=/usr/local/lib/codec", I do "make" and this is what I get.. errors.

Any ideas?
Thanks

Try to add the following to ./configure:

```
--disable-ivtv
```and hopefully this will allow you to build a working copy of mplayer but without the use of whatever capture card you have. So full options would be:


```
$ ./configure \
--prefix=/usr/local \
--disable-ivtv \
--enable-largefiles \
--enable-gui \
--codecsdir=/usr/local/lib/codecs
$ make 
$ sudo make install
```I note that 'largefiles' is enabled by default now, not sure when that changed :-)

   Hope that helps,

    Andrew

---

### Post by jocheem67 on 2008-01-21
Hi there:


[HTML]./configure --enable-gui --codecsdir=/usr/local/lib/codecs
make
sudo checkinstall && sudo make install[/HTML]

That' s how I did it, created a deb...very nice:)

Nevertheless the mplayer gui is very crappy, smplayer is the better bet I think, and it' s a bit of a shame that it takes a workaround to get it installed when mplayer is self-compiled...even more when the smplayer developer states that one should use the svn mplayers....

---

### Post by aBitLater on 2008-01-21
thank you for your help.  

I am actually trying to get TV on Ubuntu... I'm a newbie, and I thought I had to install MPlayer to watch it.  I've installed ivtv from the package manager, but I don't know anything about it... how to configure, use, etc.  My tv card is Hauppauge WinTV PVR 150 (PCI card).  

Is there no other way?  Will --disable-ivtv make it so I can't watch tv on my computer?


EDIT1:
I ./configure with --disable-ivtv and after a very long time all appears to be good, then I get this at the end:
```
libvo/libvo.a(video_out.o):(.rodata+0x34): undefined reference to `video_out_ivtv'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1

```

EDIT2:
I also wanted to say that I have an ATI Radeon 9700 Pro graphics card, with the proprietary driver - I don't know if this affects anything.  My tuner card (PCI Card) is Hauppauge WinTV PVR 150

> **andrew.46 said:**
> Hi,

 Sorry you are having some trouble:



Try to add the following to ./configure:

```
--disable-ivtv
```and hopefully this will allow you to build a working copy of mplayer but without the use of whatever capture card you have. So full options would be:


```
$ ./configure \
--prefix=/usr/local \
--disable-ivtv \
--enable-largefiles \
--enable-gui \
--codecsdir=/usr/local/lib/codecs
$ make 
$ sudo make install
```I note that 'largefiles' is enabled by default now, not sure when that changed :-)

   Hope that helps,

    Andrew

---

### Post by andrew.46 on 2008-01-21
Hi again!,

 I am afraid that my expertise on TV an Ubuntu is absolutely zero and in fact the searching I have done on the subject seems to show that it is a little difficult to actually get TV running well on Ubuntu.

The setting --disable-ivtv will only stop playback of television with *mplayer* not with other software on your computer and I suspect that you may simply have needed to have run the command 'make clean' without the '' before recompiling. My apologies for not mentioning this previously

Can I suggest a few things?

1. Have a good long trawl through some specialty sites such as: [http://ivtv.writeme.ch/tiki-index.php](http://ivtv.writeme.ch/tiki-index.php) to get a bit more background on TV and Linux. I believe they have a mailing list as well which might be worth the time and effort.

2. Forget about mplayer for watching TV for the moment, although I suspect that all you are missing is some header files. Have a look at a few 'watching tv on linux' sites and see if there are some less difficult way of accomplishing your aim. I found an interesting one at:

[http://www.linux.com/feature/34790](http://www.linux.com/feature/34790)

which also describes some of the *other* tv software for linux. The page is a little aged but I am sure there are more recent pages out there.

3. Return after a while to the svn mplayer and try again, hopefully with the correct header files in place and a greater knowledge of IVTV (my apologies again for knowing next to nothing on the subject.)  Mplayer apparently offers great TV viewing. options wich can be seen on the online documantation at:

[http://www.mplayerhq.hu/DOCS/HTML/en/tv-input.html](http://www.mplayerhq.hu/DOCS/HTML/en/tv-input.html)

It makes it all sound quite interesting :-)

  All the very best,

      Andrew

---

### Post by csulok on 2008-01-22
> **andrew.46 said:**
> Hi,

 If a kernel update is the problem:



you actually can either temporarily or permanently use the older kernel. Depending how Grub is set on your system press 'Esc' when you see the Grub menu on the initial bootup and select the older kernel.

If this is the problem you can change the boot order by editing /boot/grub/menu.lst.

            Andrew
the old kernels aren't installed, so they are not in the grub menu, but that's not the problem, i can easily install them.

the problem is that i can't reboot due to various circumstances for another 2 weeks.

---

### Post by jocko on 2008-01-22
> **andrew.46 said:**
> I will be writing a similar howto for Hardy Heron and I suspect that checkinstall will feaure. I am not such a big fan of the program but many people have asked for it. Your syntax was a little wayward though, should be:
```
$ ./configure
$ make
$ sudo checkinstall -D
```with the usual ./configure options added in. The -D option for Checkinstall specifies a debian package, checkinstall can also produce an rmp and tgz package.

[SIZE=3][COLOR=Blue]Thanks for an excellent howto.[/COLOR][/SIZE] I have a little suggestion for improving it:
Why use checkinstall (or make install), when the mplayer source already contains the necessary instructions to build a **real** debian package?

Simply run this command instead of 'make install' or 'checkinstall' (first install fakeroot and dpkg-dev):
```
DEB_BUILD_OPTIONS="--prefix=/usr/local --enable-gui --enable-largefiles --codecsdir=/usr/local/lib/codecs" fakeroot debian/rules binary
```This will produce a **real** debian package, with proper dependencies and correct version numbering (=no conflicts with the repos, as the svn version is newer). 

Also, as pulseaudio will be default in hardy (and many already use it in gutsy), you may need to add libpulse-dev (plus fakeroot and dpkg-dev) to the dev-packages.

---

### Post by andrew.46 on 2008-01-22
Hi,

 Thanks for your message:

> **jocko said:**
> [SIZE=3][COLOR=Blue]Thanks for an excellent howto.[/COLOR][/SIZE] I have a little suggestion for improving it:
Why use checkinstall (or make install), when the mplayer source already contains the necessary instructions to build a **real** debian package?
[...] Also, as pulseaudio will be default in hardy (and many already use it in gutsy), you may need to add libpulse-dev (plus fakeroot and dpkg-dev) to the dev-packages.

Excellent suggestions! I shall certainly add this.

         Andrew

---

### Post by iulianhoratiu on 2008-01-23
Thank you . Really worked and not hard to do . Great tutorial !

---

### Post by andrew.46 on 2008-01-23
Hi,

 Thanks for your kind words:
> **iulianhoratiu said:**
> Thank you . Really worked and not hard to do . Great tutorial !

It is totally my pleasure! 

     Andrew

---

### Post by andrew.46 on 2008-01-25
Hi shirilover,

I have been poring over older posts and reread yours:

> **shirilover said:**
> 
Also, if you would like to create a deb package you can do the following (needs fakeroot and dpkg-dev):
```

cd  /path/to/mplayer-svn/source
DEB_BUILD_OPTIONS="--enable-gui --enable-largefiles --enable-xvmc" fakeroot debian/rules binary

```

I have done this at home and it certainly represents an answer for those who have had trouble with the repository threatening to overwrite their svn mplayer. I am not such a fan of checkinstall plus this method  is just plain cool :-)

Rather than change this walkthrough which has had some traffic indeed I am incorporating it into a Hardy Heron version of installing the svn mplayer.

Do you have any other suggestions for the future walkthrough?

    Andrew

---

### Post by jocko on 2008-01-25
> **andrew.46 said:**
> Hi shirilover,

I have been poring over older posts and reread yours:



I have done this at home and it certainly represents an answer for those who have had trouble with the repository threatening to overwrite their svn mplayer. I am not such a fan of checkinstall plus this method  is just plain cool :-)

Rather than change this walkthrough which has had some traffic indeed I am incorporating it into a Hardy Heron version of installing the svn mplayer.

Do you have any other suggestions for the future walkthrough?

    Andrew
I noticed after my previous post (yes, I got the idea from shirilover's post) that the version number is set in the file "changelog" in the debian subdirectory, so if the number in that file is in a different format than the repo version, synaptic may try to upgrade it.
This may be something to include in your upcoming hardy tutorial.

As an example:
The current version in the gutsy backports repo is [COLOR=Red]2:[/COLOR][COLOR=Blue]1.0[/COLOR]~rc2-0ubuntu1, while the version number in the current svn is simply "[COLOR=Blue]1.0[/COLOR]svn".
That would make it look like the svn version (major version [COLOR=Blue]1[/COLOR]) is older than the repo version (major version [COLOR=Red]2[/COLOR], although really [COLOR=Blue]1[/COLOR]).
The solution is to change the version number in the latest entry in mplayer/debian/changelog to a higher value, like [COLOR=Red]3:[/COLOR][COLOR=Blue]1.0[/COLOR]svn.

So change the first line in the file from this:
```
mplayer ([COLOR=Blue]1.0[/COLOR]svn) unstable; urgency=low
```To this:
```
mplayer ([COLOR=Red]3:[/COLOR][COLOR=Blue]1.0[/COLOR]svn) unstable; urgency=low

```

---

### Post by andrew.46 on 2008-01-25
Hi,

 Thanks for this. In fact the Ubuntu repository keeps trying to change mplayer when installed as a Debian package:

> **jocko said:**
> I noticed after my previous post (yes, I got the idea from shirilover's post) that the version number is set in the file "changelog" in the debian subdirectory, so if the number in that file is in a different format than the repo version, synaptic may try to upgrade it.
This may be something to include in your upcoming hardy tutorial.


It may be a little sad but I have half written the Hardy version already, even though there are months until the release, and I suspect changing the source code 'changelog' might be better that describing package 'locking'. I just need to find the most user friendly method of doing this.

I suspect that shirilover would do a better job at this than me. His / her knowledge of mplayer exceeds mine somewhat.

           Andrew

---

### Post by andrew.46 on 2008-01-25
Hi,

 Thanks for this. In fact the Ubuntu repository keeps trying to change mplayer when installed as a Debian package:

> **jocko said:**
> I noticed after my previous post (yes, I got the idea from shirilover's post) that the version number is set in the file "changelog" in the debian subdirectory, so if the number in that file is in a different format than the repo version, synaptic may try to upgrade it.
This may be something to include in your upcoming hardy tutorial.


It may be a little sad but I have half written the Hardy version already, even though there are months until the release, and I suspect changing the source code 'changelog' might be better that describing package 'locking'.

BTW I will eliminate many of the configure options:

```
--prefix=/usr/local  --enable-largefiles --codecsdir=/usr/local/lib/codecs
```

Large files is now a default, the prefix was always redundant and the codecs directory is found by the configure process in this location anyway. Which really only leaves: --enable-gui.

I suspect that shirilover would do a better job at this than me. His / her knowledge of mplayer exceeds mine somewhat.

           Andrew

---

### Post by andrew.46 on 2008-01-25
Hi,

 Worked a little on your idea:

> **jocko said:**
> 
So change the first line in the file from this:
```
mplayer ([COLOR=Blue]1.0[/COLOR]svn) unstable; urgency=low
```To this:
```
mplayer ([COLOR=Red]3:[/COLOR][COLOR=Blue]1.0[/COLOR]svn) unstable; urgency=low

```

and hopefully there are some sed experts here, but I came up with:

```
sed -i_bak 's/1\.0svn/3\:1\.0svn/' debian/changelog
```

which seems to do the trick, as well as saving a backup for the paranoid :- ) Any thoughts?

      Andrew

---

### Post by jocko on 2008-01-26
> **andrew.46 said:**
> Hi,

 Worked a little on your idea:



and hopefully there are some sed experts here, but I came up with:

```
sed -i_bak 's/1\.0svn/3\:1\.0svn/' debian/changelog
```which seems to do the trick, as well as saving a backup for the paranoid :- ) Any thoughts?

      Andrew

If it works, it's perfect. It's nice to be able to copy/paste a command instead of having to manually edit a file.

---

### Post by andrew.46 on 2008-01-26
Hi,

Yes it seems to work fine:

> **jocko said:**
> If it works, it's perfect. It's nice to be able to copy/paste a command instead of having to manually edit a file.

But I have a dislike for such relatively ugly hacks so FWIW I have filed bug reports with mplayer-users and launchpad although I am not so sure that either side will be prepared to change anything:

[https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/186230](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/186230)
[http://lists.mplayerhq.hu/pipermail/mplayer-users/2008-January/071488.html](http://lists.mplayerhq.hu/pipermail/mplayer-users/2008-January/071488.html)

Nice if something were definitively fixed though.

     Andrew

---

### Post by Maverynthia on 2008-01-28
I'm getting this error:
The GUI requires libavcodec with PNG support (needs zlib).

Someone else also had the error but no one posted a fix so..I ask again...

---

### Post by andrew.46 on 2008-01-28
Hi,

 A repository search reveals a few possible candidates that could solve your problem:

> **Maverynthia said:**
> I'm getting this error:
The GUI requires libavcodec with PNG support (needs zlib).

Someone else also had the error but no one posted a fix so..I ask again...

Definitely the first 2, and possibly the last 2 as well:

```
$ sudo apt-get install zlib1g-dev zlib1g zlibc zlib-bin 
```

Please let me know if this solves the problem,

     Andrew

---

### Post by andrew.46 on 2008-01-31
Hi all,

 I have done a pretty major rewrite of the Howto, not sure if this sabotages a lot of the replies / discussions etc but it is a done thing now. 

Left a placeholder for Hardy Heron which should just require a rework of the -dev files although this is no small task. Added the Debian install that a few people were after and generally tidied up. Should cover Feisty / Gutsy / Hardy after April which will hopefully mean this 'Howto' could have a life-expectancy of many years.

Let me know if I have made any typos / errors etc,

          Andrew

---

### Post by jocheem67 on 2008-02-02
You're doing an impressive job!

Maybe you could add something like how to update mplayer through subversion?? It's possible isn't it?
Or does that require recompiling the whole thing every time, cause that might be a bridge too far.

---

### Post by GamingMazter on 2008-02-02
Thanks. Thats me all set!

---

### Post by andrew.46 on 2008-02-02
Hi,

  Glad you liked the walkthrough:

> **jocheem67 said:**
> You're doing an impressive job!

Maybe you could add something like how to update mplayer through subversion?? It's possible isn't it?
Or does that require recompiling the whole thing every time, cause that might be a bridge too far.

You may have missed the recent rewrite where I have mentiond this, it is in the section marked 'Download the svn mplayer'. But just for the record the technique is quite simple. Simply change to the directory that contains the source code and type:

```
$ svn update
```

and the source code will be updated to the latest version. But then, as you mention, the code must be compiled again which is definitely a long job on my poor old computer :-)

 All the best,

   Andrew

---

### Post by marin.r on 2008-02-02
Hello there,
I see this is THE mplayer thread in the forum :) First of all - the guide is really easy and got me a fresh mplayer in no time.
But my problem persists - I had it with the packaged version too - everything works SUPER FINE from the command line, but when I use the GUI frontend with same video and audio output (xv and alsa) and everything else default - an error keeps popping up, cpu usage 100% , the error says ALSA Cannot open PCM 0,0 or something very similar.
I fail to find any more advanced configurations... why alsa opens everything really well from the command line and doesn't from GUI mplayer?
Thanks in advance,

---

### Post by l0b0 on 2008-02-03
Thanks for a great guide! I've had a couple problems though:

First, I had to
```
$ sudo apt-get install debhelper
```
to be able to run ```
$ DEB_BUILD_OPTIONS [...]
```

Second, I keep getting tons of error messages when playing anything - Here's some sample output:
```
$ gmplayer test.mp3 
MPlayer dev-SVN-r25952-4.1.3 (C) 2000-2008 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
/usr/share/fonts/truetype/ttf-gentium/GenAR102.ttf doesn't look like a bitmap font description, ignoring.
Cannot load bitmap font: /usr/share/fonts/truetype/ttf-gentium/GenAR102.ttf
[GUI] Adding video filter: pp

Playing /path/test.mp3.
Cache fill:  0.00% (0 bytes)   
Audio file file format detected.
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 320.0 kbit/22.68% (ratio: 40000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [alsa] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
[AO_ALSA] Mixer attach default error: Invalid argument
Starting playback...
[AO_ALSA] Mixer attach default error: Invalid argument
[AO_ALSA] Mixer attach default error: Invalid argument
```

The "Invalid argument" errors go on like that, while the CPU usage tops out. The contents actually play, but MPlayer is unusable because of all the error pop-ups.

---

### Post by andrew.46 on 2008-02-03
Hi,

 Sorry to hear you are having some trouble:

> **l0b0 said:**
> Thanks for a great guide! I've had a couple problems though:

First, I had to
```
$ sudo apt-get install debhelper
```
to be able to run ```
$ DEB_BUILD_OPTIONS [...]
```


I have added this to the initial install downloads, thanks for pointing this one out.

> Second, I keep getting tons of error messages when playing anything - Here's some sample output:
```
$ gmplayer test.mp3 
MPlayer dev-SVN-r25952-4.1.3 (C) 2000-2008 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
/usr/share/fonts/truetype/ttf-gentium/GenAR102.ttf doesn't look like a bitmap font description, ignoring.
Cannot load bitmap font: /usr/share/fonts/truetype/ttf-gentium/GenAR102.ttf
[GUI] Adding video filter: pp

Playing /path/test.mp3.
Cache fill:  0.00% (0 bytes)   
Audio file file format detected.
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 320.0 kbit/22.68% (ratio: 40000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [alsa] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
[AO_ALSA] Mixer attach default error: Invalid argument
Starting playback...
[AO_ALSA] Mixer attach default error: Invalid argument
[AO_ALSA] Mixer attach default error: Invalid argument
```

The "Invalid argument" errors go on like that, while the CPU usage tops out. The contents actually play, but MPlayer is unusable because of all the error pop-ups.

Looks like 2 problems. Firstly you need to select another font for the OSD as there seems to be some trouble with your existing one. Easiest way is:

```
$ sudo apt-get install ttf-bitstream-vera
$ ln -sv /usr/share/fonts/truetype/ttf-bitstream-vera/Vera.ttf ~/.mplayer/subfont.ttf
```

The other looks like an audio out problem. Have a look at what is available to you:

```
$ mplayer -ao help
```

Then try one of these. For example:

```
$ mplayer -ao oss <filename>
$ mplayer -ao esd <filename>
```

If this is a solution it can be written into a startup configuration file to make it the default audio output.

Please post back if this is a solution.

     Andrew

---

### Post by l0b0 on 2008-02-04
> **andrew.46 said:**
> Looks like 2 problems. Firstly you need to select another font for the OSD as there seems to be some trouble with your existing one. Easiest way is:

```
$ sudo apt-get install ttf-bitstream-vera
$ ln -sv /usr/share/fonts/truetype/ttf-bitstream-vera/Vera.ttf ~/.mplayer/subfont.ttf
```

This is already done:
```
$ sudo apt-get install ttf-bitstream-vera
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ttf-bitstream-vera is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

$ ln -sv /usr/share/fonts/truetype/ttf-bitstream-vera/Vera.ttf ~/.mplayer/subfont.ttf
create symbolic link `.../.mplayer/subfont.ttf' to `/usr/share/fonts/truetype/ttf-bitstream-vera/Vera.ttf'
ln: creating symbolic link `.../.mplayer/subfont.ttf' to `/usr/share/fonts/truetype/ttf-bitstream-vera/Vera.ttf': File exists
```

> **andrew.46 said:**
> The other looks like an audio out problem. Have a look at what is available to you:

```
$ mplayer -ao help
```

Then try one of these. For example:

```
$ mplayer -ao oss <filename>
$ mplayer -ao esd <filename>
```

If this is a solution it can be written into a startup configuration file to make it the default audio output.

Please post back if this is a solution.
It's only **g**mplayer that has this problem. mplayer works fine without the GUI.

---

### Post by marin.r on 2008-02-05
About the font problem in mplayer frontend - the font path is hardcoded in the configuration, so you should change it, I had this one too.
It's frontend config related, same as my issue described above.

---

### Post by sib217 on 2008-02-05
Does this work the same way for PS3?  I have installed Ubuntu but couldn't get DVD's or Blu Ray's to play.  I was hoping this would work on PS3.  I think you need something like libdvdcss to play movies.  I wasn't sure if these codes did the same thing.
Thanks!

---

### Post by andrew.46 on 2008-02-05
Hi,

I am not so sure that this guide will help you:

> **sib217 said:**
> Does this work the same way for PS3?  I have installed Ubuntu but couldn't get DVD's or Blu Ray's to play.  I was hoping this would work on PS3.  I think you need something like libdvdcss to play movies.  I wasn't sure if these codes did the same thing.
Thanks!

There is room on these forums for a guide to Ubuntu on the PS3 but as yet I have not seen one. My experience with the PS3 I am afraid is absolutely zero.

As for dvds, mplayer will play dvds but it is probably not an ideal viewer for these. I would use vlc myself and I am sure there are others. But it is probably not a good idea to go through the toil of installing the subversion mplayer to simply watch a dvd. (And it definitely does not play Blu Ray (?) movies.

 Sorry to be the bearer of bad news,

    Andrew

---

### Post by mangurt on 2008-02-05
Thanks for posting this guide, but I am having a problem with mplayer.

Attached is a screenshot of the error I get when I try to open a file.

What I am trying to do is open an file via right click, and then open with mplayer.  No matter what file I try to open, I get this error.
Any help would be greatly appreciated.

---

### Post by andrew.46 on 2008-02-05
Hi,

 Sorry to hear you are having a little trouble:

> **mangurt said:**
> Thanks for posting this guide, but I am having a problem with mplayer.

Attached is a screenshot of the error I get when I try to open a file.

What I am trying to do is open an file via right click, and then open with mplayer.  No matter what file I try to open, I get this error.
Any help would be greatly appreciated.

Does the file open with the command line player?

                Andrew

---

### Post by mangurt on 2008-02-05
Hmm....I am rather new to the whole mplayer thing, so I don't really know how to open the file via command line.

---

### Post by andrew.46 on 2008-02-06
Hi again!

No problems:

> **mangurt said:**
> Hmm....I am rather new to the whole mplayer thing, so I don't really know how to open the file via command line.

But can I suggest something?  If you are keen to open movie files on a right click the svn mplayer may not actually be what you *really* need. It will certainly do this but you might be better served by the program vlc:

```
$ sudo apt-get install vlc
```

Don't uninstall mplayer, the 2 programs can live together quite easily, and come back to mplayer in the near future.  To test the command line with mplayer (if you are still keen) you would open a terminal and type:

```
$ mplayer <path-to-file> <filename>
```

This would simply confirm if mplayer is able to play this avi file.

             Andrew

---

### Post by mangurt on 2008-02-06
I really appreciate all the assistance.
I do use VLC, but I heard mplayer is absolutely incredible.  VLC works very well, but I would still like to get mplayer working.

Here's what I got when I tried going the command route:

ed@ed-desktop:~$ mplayer /home/ed/Videos/Nip_Tuck - 5x11 - Kyle Ainge nip_tuck.avi
MPlayer dev-SVN-r25957-4.1.3 (C) 2000-2008 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3400+ (Family: 15, Model: 4, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE SSE2

Playing /home/ed/Videos/Nip_Tuck.
File not found: '/home/ed/Videos/Nip_Tuck'
Failed to open /home/ed/Videos/Nip_Tuck.


Playing -.
Reading from stdin...

I don't know if I got this right or now.  The major reason why I want to get mplayer working is I read on the v4l-dvb mailing list that mplayer is a geat way to use a tv tuner card to watch TV.  I have a card that is finally working in linux, but I cannot seem to get a program up and running to watch tv.

Again, thanks for your help.

---

### Post by andrew.46 on 2008-02-06
Hi again,

 My apologies, I did not realise your enthusiasm for the program:

> **mangurt said:**
> I really appreciate all the assistance.
I do use VLC, but I heard mplayer is absolutely incredible.  VLC works very well, but I would still like to get mplayer working..

Good news: I have managed to duplicate your problem! The problem is that your filenames have spaces in them, which to tell the truth is a minor Linux sin, and gmplayer does not understand them.

To test this make a copy of any of your files and rename it say from:

Nip and Tuck.avi

to

Nip_and_Tuck.avi

and I think it should work. I will be very pleased for you if this works!!

As regards the tv thing bear in mind that you will have to re-compile with the addition of some television -dev files. If you have compiled from my guide tv capture was not included.

 Please let me know if this has been any help to you.

              Andrew

---

### Post by mangurt on 2008-02-06
Thanks for this information.  I am currently at work (and away from my system), but I will try this when I get home tonight.

I used mplayer on my children's computer (I installed PSlinuxOS on their system because they needed something that really resembled windoze) and thought it was better than VLC.  I have some problems with VLC playing .mkv files, but using mplayer on that system had no problem at all.

I will post my results when I get home.

---

### Post by andrew.46 on 2008-02-06
Hi,

A final thought:

> **mangurt said:**
> Thanks for this information.  I am currently at work (and away from my system), but I will try this when I get home tonight.
.

Of course the path should not have spaces either, perhaps transfer the files to your Desktop? (You can 'escape' the spaces as well, but not having them at all is the best answer).

               Andrew

---

### Post by mangurt on 2008-02-06
Whoo Hooo!!!  Success!  I can play the file via command!!!!  Now I know that it works.  If I could only get the GUI working.....and get mplayer to show the file in full screen...but it's working!!:guitar::guitar::guitar:

---

### Post by andrew.46 on 2008-02-06
Hi,

Congratulations:

> **mangurt said:**
> Whoo Hooo!!!  Success!  I can play the file via command!!!!  Now I know that it works.  If I could only get the GUI working.....and get mplayer to show the file in full screen...but it's working!!:guitar::guitar::guitar:

What a feeling :-) The gmplayer is simply choking on the spaces in your path and filename, this should be easily fixed.

As for full screen, welcome to the commandline!! Imagine a file called test.avi on the Desktop:

```
$ cd Desktop
$ mplayer -fs test.avi
```

How easy is that? What about playing it in full screen, playing it 3 times, playing it at half speed, and scaling the sound to the same speed:

```
$ cd Desktop
$ mplayer -fs -loop 3 -speed .5 -af scaletempo test.avi
```

This is why the command line is king with mplayer.

                Andrew

---

### Post by mangurt on 2008-02-06
> **andrew.46 said:**
> Hi,

Congratulations:



What a feeling :-) The gmplayer is simply choking on the spaces in your path and filename, this should be easily fixed.

As for full screen, welcome to the commandline!! Imagine a file called test.avi on the Desktop:

```
$ cd Desktop
$ mplayer -fs test.avi
```

How easy is that? What about playing it in full screen, playing it 3 times, playing it at half speed, and scaling the sound to the same speed:

```
$ cd Desktop
$ mplayer -fs -loop 3 -speed .5 -af scaletempo test.avi
```

This is why the command line is king with mplayer.

                Andrew

Thanks for the assistance, but I am still not getting the entire avi to show in full screen, and that is what I would like to do.  (See attached)

---

### Post by andrew.46 on 2008-02-06
Hi,

 The answer is in fact in that screen capture:

> **mangurt said:**
> Thanks for the assistance, but I am still not getting the entire avi to show in full screen, and that is what I would like to do.  (See attached)

See the bit that says: VO : [x11] ? This means Video Output x11 which usually cannot go full screen. For some reason your default is probably x11. Run:

```
$ mplayer -vo help
```

and this will tell you what video output is available to you. xv should be available to you so run:

```
$ mplayer -vo xv -fs filename.avi
```

If all is well with this you can alter the defaults by creating the file ~/.mplayer/config and placing the following:

```
vo = xv
```  

    Andrew

---

### Post by rvm4000 on 2008-02-06
With x11 you have to use also **-zoom** (but for best performance use -vo xv).

---

### Post by mangurt on 2008-02-06
Hmm...Ok, i did the mplayer -vo help and this is what I got

MPlayer dev-SVN-r25957-4.1.3 (C) 2000-2008 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3400+ (Family: 15, Model: 4, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE SSE2
Available video output drivers:
        x11     X11 ( XImage/Shm )
        xover   General X11 driver for overlay capable video output drivers
        gl      X11 (OpenGL)
        gl2     X11 (OpenGL) - multiple textures version
        sdl     SDL YUV/RGB/BGR renderer (SDL v1.1.7+ only!)
        fbdev   Framebuffer Device
        fbdev2  Framebuffer Device
        v4l2    V4L2 MPEG Video Decoder Output
        xvidix  X11 (VIDIX)
        cvidix  console VIDIX
        null    Null video output
        mpegpes Mpeg-PES to DVB card
        yuv4mpeg        yuv4mpeg output for mjpegtools
        tga     Targa output
        pnm     PPM/PGM/PGMYUV file
        md5sum  md5sum of each frame


I did not see the vo=xv, so with I typed in the file, I did not get any video :/
I know I am really, really close..

Again, thanks for all the hlep :)

---

### Post by rvm4000 on 2008-02-07
I think you need a development library (which name I don't remember right now) to compile mplayer with xv support.

Anyway, the -zoom option will allow the video to be resized when using x11. So **mplayer -zoom -fs ..**. should display the video in fullscreen.

---

### Post by mangurt on 2008-02-07
Sweet!  I got the full screen with the -zoom function!!!

Thanks for all the help!

Time to sit back and watch some movies I have backed up :popcorn:

---

### Post by andrew.46 on 2008-02-07
Hi,

 You live and learn, I have never heard of the zoom function:
> **mangurt said:**
> Sweet!  I got the full screen with the -zoom function!!!
Thanks for all the help!
Time to sit back and watch some movies I have backed up :popcorn:

You should really have access to xv through. To find the relevant dev file for your branch of Ubuntu you can try:

```
$ apt-cache search xv | grep dev
```

and download and install a likely candidate. Then run ./configure and see if you have picked up xv as a VO. When I run this command on Hardy I get:

> 
andrew@ilium:~$ apt-cache search xv | grep dev
libmpeg4ip-dev - end-to-end system to explore streaming multimedia
libogmrip-dev - Application for ripping and encoding DVD - development files
libxvidcore4-dev - High quality ISO MPEG4 codec library -- development files
libwings-dev - Window Maker's own widget set
xviewg-dev - XView development tools
xvmount - Small graphical utility for mounting devices by users
libxcb-xv0-dev - X C Binding, xv extension, development files
libxcb-xvmc0-dev - X C Binding, xvmc extension, development files
libxv-dev - X11 Video extension library (development headers)
libxvmc-dev - X11 Video extension library (development headers)
libxxf86vm-dev - X11 XFree86 video mode extension library (development headers)
x11proto-video-dev - X11 Video extension wire protocol

and I would download libxv-dev. Thats how simple it all is :-)

      Andrew

---

### Post by mangurt on 2008-02-07
Hmmm....Ok, forgive me for my newness with linux, but how would I go about downloading what version I need?
sudo apt-get whatever?

Would I have to recompile then?

Just wondering..
Thanks again

---

### Post by andrew.46 on 2008-02-07
Hi again!

> **mangurt said:**
> Hmmm....Ok, forgive me for my newness with linux, but how would I go about downloading what version I need?
sudo apt-get whatever?

Would I have to recompile then?


If the file was libxv-dev.you would:

```
$ sudo apt-get install libxv-dev
```

You would then change to the directory that holds the mplayer source files and update that and run ./configure:

```
$ cd $HOME/Desktop/mplayer
$ sudo make clean
$ svn update
$ ./configure --enable-gui --enable-menu
```

At the bottom of the output on the screen you will see a section something like this:

> 
  Enabled optional drivers:
    Input: ftp pvr tv-teletext tv-v4l2 tv-v4l tv cddb cdda libdvdcss(internal) dvdread(internal) vcd dvb smb network 
    Codecs: x264 xvid libavcodec qtx real xanim win32 faad2 faac libmpeg2 liba52 mp3lib libtheora tremor(internal) libmad liblzo gif 
    Audio output: alsa esd arts oss sdl mpegpes(dvb) 
    Video output: sdl gif89a pnm jpeg png mpegpes(dvb) fbdev svga caca aa xvidix cvidix opengl dga **[COLOR="Red"]xv[/COLOR]** x11 xover md5sum tga 


Not neatly outlined in red of course, that is my own addition :-) If xv Video Out is there then run:

```
$ make
$ sudo make install
```

If not, hunt for another -dev file.

         Andrew

---

### Post by mangurt on 2008-02-07
Ok, some success...and some failure.

The success, I got the vo thing working.  The failure, I have no audio.  I had audio before, but now I don't, and the sad thing is I don't know what I did to lose the audio portion...

Any ideas?

---

### Post by andrew.46 on 2008-02-07
Hi,

 I hope you are still having fun!

> **mangurt said:**
> Ok, some success...and some failure.

The success, I got the vo thing working.  The failure, I have no audio.  I had audio before, but now I don't, and the sad thing is I don't know what I did to lose the audio portion...

Any ideas?

You can see the audio options available to you by running:

```
$ mplayer -ao help
```

and you should see a list similar to this:

> Available audio output drivers:
        oss     OSS/ioctl audio output
        alsa    ALSA-0.9.x-1.x audio output
        arts    aRts audio output
        esd     EsounD audio output
        sdl     SDLlib audio output
        mpegpes DVB audio output
        null    Null audio output
        pcm     RAW PCM/WAVE file writer audio output


and then you can test via the command line:

```
$ mplayer -ao alsa moviefile.avi
```

and if you desire you can make a new default by placing ao = oss in your $HOME/.mplayer/config file.

             Andrew

---

### Post by mangurt on 2008-02-08
This is what I got from doing mplayer -ao help

ed@ed-desktop:~$ mplayer -ao help
MPlayer dev-SVN-r25957-4.1.3 (C) 2000-2008 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3400+ (Family: 15, Model: 4, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE SSE2
Available audio output drivers:
        oss     OSS/ioctl audio output
        sdl     SDLlib audio output
        mpegpes DVB audio output
        v4l2    V4L2 MPEG Audio Decoder output
        null    Null audio output
        pcm     RAW PCM/WAVE file writer audio output

ed@ed-desktop:~$ 



Still sorta lost on what to do now..

---

### Post by andrew.46 on 2008-02-09
Hi,

 Are you *sure* that you are still having fun?

> **mangurt said:**
> This is what I got from doing mplayer -ao help

ed@ed-desktop:~$ mplayer -ao help
MPlayer dev-SVN-r25957-4.1.3 (C) 2000-2008 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3400+ (Family: 15, Model: 4, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE SSE2
Available audio output drivers:
        oss     OSS/ioctl audio output
        sdl     SDLlib audio output
        mpegpes DVB audio output
        v4l2    V4L2 MPEG Audio Decoder output
        null    Null audio output
        pcm     RAW PCM/WAVE file writer audio output

ed@ed-desktop:~$ 
Still sorta lost on what to do now..

Have you tried:

```
$ mplayer -ao oss movifile.avi
```

I am a bit at a loss to see that you do not have alsa and xv running and I hope it does not have something to do with the 64 bit athlon you seem to be running?

        Andrew

---

### Post by mangurt on 2008-02-09
> **andrew.46 said:**
> Hi,

 Are you *sure* that you are still having fun?




I am still having fun trying to get this to work :)  Some people describe fun one way, I like to figure things out....

As for having an atholon 64, that should not make a difference....sound was working when I posted success before....

I tried the mplayer -ao oss moviefile.avi and I still got no sound.  I know the file does work, because I tried the file with VLC and it was fine....

I am open for any other suggestions...

Thanks again.

---

### Post by andrew.46 on 2008-02-09
Hi again!

 Well it all sounds a little odd:
> **mangurt said:**
> I am open for any other suggestions...


Perhaps it is time to uninstall and reinstall the svn mplayer? Not the codecs and skins but the svn source code, there are some directions for upgrading the svn source on the revamped opening page, and then recompile. Make sure to run 'make clean' on the source first.

         Andrew

---

### Post by penC on 2008-02-09
Thanks for the guide. It worked like a charm with Gutsy.

BR,

  penC

---

### Post by andrew.46 on 2008-02-09
Hi,

 Thanks for your message:

> **penC said:**
> Thanks for the guide. It worked like a charm with Gutsy.
BR,
  enC

It is totally my pleasure, and I am *very* pleased to hear you had no problems :-)

     Andrew

---

### Post by webbie180 on 2008-02-13
I am a gusty user.  How do I get the channel list for sopcast and nslive in gmlive?  Thanks.

---

### Post by andrew.46 on 2008-02-13
Hi again!

I have finally found the solution to this problem:

> **mangurt said:**
> Thanks for posting this guide, but I am having a problem with mplayer.
What I am trying to do is open an file via right click, and then open with mplayer.  No matter what file I try to open, I get this error.
Any help would be greatly appreciated.

It turns out to be a problem with the desktop settings for Gmplayer in combination with spaces in filenames. To resolve:

======================================
**To Resolve "Cannot open file error" with Gmplayer**
=====================================

There is a problem with Gmplayer at the moment that prevents it from playing movie files directly from Nautilus or from right click on the file itself. This occurs if there is a space in the filename or the path to the filename. There is an easy solution:

Press Alt-F2 and then:

```
$ gksudo gedit /usr/local/share/applications/mplayer.desktop
```

You will see a line that says:
```

Exec=gmplayer %U
```

Change this to:

```
Exec=gmplayer %F
```

or perhaps more correctly:

```
Exec=gmplayer
```

Save the changes and exit. All should be well now :-)

================================

Please tell me if this resolves the issue for you,

      Andrew

---

### Post by andrew.46 on 2008-02-17
Hi,

For those who are interested I include the method for enabling dvd menus in the svn mplayer. This is not appearing in the main 'Howto' as the implementation of libdvdnav in mplayer is still in its very early stages and I am a little wary of offering support for such early beta efforts. Nevertheless the following works quite well on my system:

==================================
**Emabling DVD Navigation in the svn Mplayer**
==================================

1. Download and install libdvdread and libdvdcss

2.Download the svn libdvdnav source:

```
$ svn co svn://svn.mplayerhq.hu/dvdnav/trunk/libdvdnav libdvdnav
```

and compile / install it:

```
$ cd libdvdnav
$ ./autogen.sh
$ ./configure
$ make
$ make install
```

3. Add the following option when compiling the svn mplayer:

```
$ ./configure --disable-dvdread-internal
```

and compile as usual.

4. Add the following to ~/.mplayer/config:

```
mouse-movements=yes
```

5. Use the following to see the navigation menu for the movie:

```
$ mplayer dvdnav://
```

6. Navigation can be from the mouse or with the num pad keys:

>  (The  following  keys are only valid if you compiled with dvdnav
 support: They are used to navigate the menus.)

    keypad 8  Select button up.
    keypad 2  Select button down.
    keypad 4  Select button left.
    keypad 6  Select button right.
    keypad 5  Return to main menu.
    keypad 7  Return to nearest menu (the order of preference  is:  chapter->title->root).
    keypad ENTER Confirm choice.

And there you have it. When and if libdvdnav is better integrated with mplayer I will add it to the main 'Howto' section.

      Andrew

---

### Post by andrew.46 on 2008-02-17
Hi,

 I am afraid that I cannot help you with this:

> **webbie180 said:**
> I am a gusty user.  How do I get the channel list for sopcast and nslive in gmlive?  Thanks.

as I have absolutely no knowledge or experience of this. Anybody here who can help out?

            Andrew

---

### Post by andrew.46 on 2008-02-21
Hi,
Again I publish a little 'add-on' to my 'Howto' this tims a few lines that describe how to add amr widwband and narrow band support for mplayer.

===============================================
**'Howto' add amr support to your svn mplayer**
===============================================

This mini 'howto' describes the method to add amr support to your svn mplayer installation and is written especially for the father of 'the laughing girl'.

**1. amr narrow band:**

```
 
$ cd $HOME/Desktop
$ wget http://ftp.penguin.cz/pub/users/utx/amr/amrnb-7.0.0.0.tar.bz2
$ tar xjvf amrnb-7.0.0.0.tar.bz2
$ cd amrnb-7.0.0.0
$ wget http://www.3gpp.org/ftp/Specs/archive/26_series/26.104/26104-700.zip
$ ./configure  --enable-shared --disable-static
$ make
$ sudo make install

```

**2. amr wide band:**

```

$ cd $HOME/Desktop
$ wget http://ftp.penguin.cz/pub/users/utx/amr/amrwb-7.0.0.2.tar.bz2
$ tar xjvf amrwb-7.0.0.2.tar.bz2
$ cd amrwb-7.0.0.2
$ wget http://www.3gpp.org/ftp/Specs/archive/26_series/26.204/26204-700.zip
$ ./configure  --enable-shared --disable-static
$ make
$ sudo make install 

```

With both installed you now need to recompile the svn mplayer source code. Mplayer will automatically pick up the amr libraries and allow their use in Mplayer. Don't forget to run:

```
$ sudo make clean
```

before recompiling. And all the best to the father of 'the laughing girl'!!

    Andrew

---

### Post by miguelitu on 2008-02-24
hey, andrew, great work! im very thankful!

just tried your how-to to add the amr support, but got this error:

gmplayer: error while loading shared libraries: libamrnb.so.3: cannot open shared object file: No such file or directory

in the ./configure process, both amr were finded, and the file is ther at /usr/lib

any thoughts??

thanks!

---

### Post by andrew.46 on 2008-02-24
Hi,

 Glad you liked the work!

> **miguelitu said:**
>  just tried your how-to to add the amr support, but got this error:
gmplayer: error while loading shared libraries: libamrnb.so.3: cannot open shared object file: No such file or directory
in the ./configure process, both amr were finded, and the file is ther at /usr/lib

If the file is there but cannot be accessed you probably do *not* have a "shared library" installation, just make sure that you ran:

```
$ ./configure  --enable-shared --disable-static
```

for both files. Can you run through the amr bit again ensuring this is the case? Possibly you caught a very early post of mine which omitted these directions, if so my apologies :-)

   Andrew

---

### Post by miguelitu on 2008-02-24
Yes, ive compiled just the way you described..

I added the --prefix=usr as described in this [URL="http://ubuntuforums.org/showthread.php?t=491885"]thread[/URL ] and now it works! strange...

but im having other trouble here. ive been using your guide to compile the svn, and were able to play some rmvb files pretty well, but recently i did a fresh install of ubuntu on my PC, compiled mplayer again and im getting this error when i try to play the same rmvb files:

Opening video decoder: [realvid] RealVideo decoder
Error: /usr/local/lib/codecs/drvc.so: wrong ELF class: ELFCLASS32
ERROR: Could not open required DirectShow codec drvc.so.
Read the RealVideo section of the DOCS!
VDecoder init failed :(
Opening video decoder: [realvid] RealVideo decoder
ERROR: Could not open required DirectShow codec drvc.dll.
Read the RealVideo section of the DOCS!
VDecoder init failed :(
Opening video decoder: [realvid] RealVideo decoder
Error: /usr/local/lib/codecs/drv4.so.6.0: wrong ELF class: ELFCLASS32
ERROR: Could not open required DirectShow codec drv4.so.6.0.
Read the RealVideo section of the DOCS!
VDecoder init failed :(
Opening video decoder: [realvid] RealVideo decoder
ERROR: Could not open required DirectShow codec drv43260.dll.
Read the RealVideo section of the DOCS!
VDecoder init failed :(
Opening video decoder: [realvid] RealVideo decoder
Error: /usr/local/lib/codecs/drvc.bundle/Contents/MacOS/drvc: cannot open shared object file: No such file or directory
ERROR: Could not open required DirectShow codec drvc.bundle/Contents/MacOS/drvc.
Read the RealVideo section of the DOCS!
VDecoder init failed :(
Cannot find codec matching selected -vo and video format 0x30345652.
Read DOCS/HTML/en/codecs.html!

i cant figure out... all codecs are there, i even tried to download the realplayer ones from the codecs directory, but still getting nothing.

any clues?

thanks a lot.

---

### Post by andrew.46 on 2008-02-24
Hi,

 Glad to hear that the amr codecs eventually worked out:

> **miguelitu said:**
> Yes, ive compiled just the way you described..

I added the --prefix=usr as described in this [URL="http://ubuntuforums.org/showthread.php?t=491885"]thread[/URL ] and now it works! strange... 

Does not sound quite right but if it works .....

> but im having other trouble here. ive been using your guide to compile the svn, and were able to play some rmvb files pretty well, but recently i did a fresh install of ubuntu on my PC, compiled mplayer again and im getting this error when i try to play the same rmvb files:

Opening video decoder: [realvid] RealVideo decoder
Error: /usr/local/lib/codecs/drvc.so: wrong ELF class: ELFCLASS32
ERROR: Could not open required DirectShow codec drvc.so.
Read the RealVideo section of the DOCS!
VDecoder init failed  .......

Multiple codec errors. Hmmmm..... I have not seen this type of file before, do you have a copy that you could post online somewhere? I would be curious to see if my own copy of mplayer could play it.

Do you definitely have the *full* codec pack? The ones at:

[http://www.mplayerhq.hu/MPlayer/releases/codecs/all-20071007.tar.bz2]("http://www.mplayerhq.hu/MPlayer/releases/codecs/all-20071007.tar.bz2") 

   Andrew

---

### Post by andrew.46 on 2008-02-25
Hi again:

> **miguelitu said:**
> i cant figure out... all codecs are there, i even tried to download the realplayer ones from the codecs directory, but still getting nothing.


You should have the following in your codecs directory:

```

andrew@ilium/usr/local/lib/codecs$ ls
AvidQTAVUICodec.qtx          cook.so.6.0   l3codeca.acm    rt32dcmp.dll  vp31vfw.dll
BeHereiVideo.qtx             ctadp32.acm   l3codecx.ax     scg726.acm    vp4vfw.dll
CLRVIDDC.DLL                 ddnt.so.6.0   lhacm.acm       sipr.so.6.0   vp5vfw.dll
CtWbJpg.DLL                  divx.dll      lsvxdec.dll     sp5x_32.dll   vp6vfw.dll
DECVW_32.DLL                 divx_c32.ax   m3jp2k32.dll    tm20dec.ax    vp7vfw.dll
LCMW2.dll                    divxa32.acm   m3jpeg32.dll    tokf.so.6.0   vssh264.dll
LCODCCMW2E.dll               divxc32.dll   m3jpegdec.ax    tokr.so.6.0   vssh264core.dll
LCodcCMP.dll                 divxdec.ax    mcdvd_32.dll    tsccvid.dll   vssh264dec.dll
QuickTime.qts                dnet.so.6.0   mcmjpg32.dll    tsd32.dll     vsshdsd.dll
QuickTimeEssentials.qtx      drv2.so.6.0   mi-sc4.acm      tssoft32.acm  vsslight.dll
QuickTimeInternetExtras.qtx  drv3.so.6.0   mpg4c32.dll     tvqdec.dll    vsswlt.dll
README                       drv4.so.6.0   mpg4ds32.ax     ubv263d+.ax   wma9dmod.dll
VDODEC32.dll                 drvc.so       msadp32.acm     ubvmp4d.dll   wmadmod.dll
ViVD2.dll                    dspr.so.6.0   msg711.acm      ultimo.dll    wmsdmod.dll
acelpdec.ax                  frapsvid.dll  msgsm32.acm     vdowave.drv   wmspdmod.dll
alf2cd.acm                   huffyuv.dll   msh261.drv      vgpix32d.dll  wmv8ds32.ax
aslcodec_dshow.dll           i263_32.drv   msms001.vwp     vid_3ivX.xa   wmv9dmod.dll
aslcodec_vfw.dll             iac25_32.ax   msnaudio.acm    vid_cvid.xa   wmvadvd.dll
asusasv2.dll                 iccvid.dll    msrle32.dll     vid_cyuv.xa   wmvdmod.dll
asusasvd.dll                 icmw_32.dll   msscds32.ax     vid_h261.xa   wmvds32.ax
ativcr2.dll                  imaadp32.acm  msvidc32.dll    vid_h263.xa   wnvplay1.dll
atrac3.acm                   imc32.acm     mvoiced.vwp     vid_iv32.xa   wnvwinx.dll
atrc.so.6.0                  ir32_32.dll   nsrt2432.acm    vid_iv41.xa   wvc1dmod.dll
avimszh.dll                  ir41_32.dll   pclepim1.dll    vid_iv50.xa   xanlib.dll
avizlib.dll                  ir50_32.dll   qdv.dll         vivog723.acm  zmbv.dll
clrviddd.dll                 ivvideo.dll   qpeg32.dll      vmnc.dll
cook.so                      jp2avi.dll    qtmlClient.dll  voxmsdec.ax

```

This represents the full codec pack: all-20071007.tar.bz2

            Andrew

---

### Post by dotancohen on 2008-02-25
> **andrew.46 said:**
> This mini 'howto' describes the method to add amr support to your svn mplayer installation and is written especially for the father of 'the laughing girl'.

Thank you very much, Andrew. Yes, I am the happy father of 'the laughing girl' and I appreciate your guidance very much. The HowTo was not only easy to perform, but also explained why each step was necessary. That is great as it becomes a learning tool as well. I cannot thank you enough. Great job, and I'm off to Google more material of yours.

---

### Post by andrew.46 on 2008-02-25
Hi,

 Good to hear from you again and I am very glad that the walkthrough worked for you:

> **dotancohen said:**
> Thank you very much, Andrew. Yes, I am the happy father of 'the laughing girl' and I appreciate your guidance very much. The HowTo was not only easy to perform, but also explained why each step was necessary. That is great as it becomes a learning tool as well. I cannot thank you enough. Great job, and I'm off to Google more material of yours.

I have my own 'laughing girl' as I mentioned before but young Hannah is my first grand-daughter. So when I heard your own girl laughing ...

            Andrew

---

### Post by janfsd on 2008-03-01
Nice guide. Btw, is anybody having problems with the latest svn in gutsy?
It compiles fine, mplayer runs ok, the only problem is with gmplayer. I get this error:
```
MPlayer dev-SVN-r26139-4.1.3 (C) 2000-2008 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ (Family: 15, Model: 43, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE SSE2
*** glibc detected *** gmplayer: malloc(): memory corruption (fast): 0x08b68c88 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb6becc42]
/lib/tls/i686/cmov/libc.so.6(__libc_malloc+0x90)[0xb6bedfc0]
/usr/lib/libglib-2.0.so.0(g_malloc+0x36)[0xb72a6af6]
/usr/lib/libglib-2.0.so.0(g_strdup+0x39)[0xb72bec19]
/usr/lib/libgobject-2.0.so.0(g_signal_newv+0x7b)[0xb734e9fb]
/usr/lib/libgobject-2.0.so.0(g_signal_new_valist+0x6c)[0xb734f5cc]
/usr/lib/libgobject-2.0.so.0(g_signal_new+0x7c)[0xb734f68c]
/usr/lib/libgtk-x11-2.0.so.0[0xb75a1fa2]
/usr/lib/libgobject-2.0.so.0(g_type_class_ref+0x381)[0xb735ad41]
/usr/lib/libgobject-2.0.so.0(g_object_newv+0x98a)[0xb734129a]
/usr/lib/libgobject-2.0.so.0(g_object_new_valist+0x21f)[0xb734178f]
/usr/lib/libgobject-2.0.so.0(g_object_new+0x40)[0xb7341940]
/usr/lib/libgtk-x11-2.0.so.0(gtk_accel_group_new+0x27)[0xb75a1ed7]
gmplayer(create_MessageBox+0xc)[0x813fb0c]
======= Memory map: ========
08048000-08929000 r-xp 00000000 08:13 683681     /usr/local/bin/mplayer
08929000-0894d000 rw-p 008e0000 08:13 683681     /usr/local/bin/mplayer
0894d000-08b8d000 rw-p 0894d000 00:00 0          [heap]
b59a0000-b5b7b000 rw-p b59a0000 00:00 0 
b5c00000-b5c21000 rw-p b5c00000 00:00 0 
b5c21000-b5d00000 ---p b5c21000 00:00 0 
b5d8f000-b5dbd000 rw-p b5d8f000 00:00 0 
b5dfc000-b5e5c000 rw-s 00000000 00:09 145784847  /SYSV00000000 (deleted)
b5e5c000-b5e65000 r-xp 00000000 08:13 1105449    /lib/tls/i686/cmov/libnss_files-2.6.1.so
b5e65000-b5e67000 rw-p 00008000 08:13 1105449    /lib/tls/i686/cmov/libnss_files-2.6.1.so
b5e67000-b5e6f000 r-xp 00000000 08:13 1105451    /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b5e6f000-b5e71000 rw-p 00007000 08:13 1105451    /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b5e71000-b5e78000 r-xp 00000000 08:13 1105447    /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b5e78000-b5e7a000 rw-p 00006000 08:13 1105447    /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b5e7e000-b5e84000 r-xp 00000000 08:13 715691     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b5e84000-b5e85000 rw-p 00005000 08:13 715691     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b5e85000-b5e97000 r-xp 00000000 08:13 716248     /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b5e97000-b5e98000 rw-p 00012000 08:13 716248     /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b5e98000-b5e99000 rw-p b5e98000 00:00 0 
b5e99000-b5ea0000 r--s 00000000 08:13 683312     /usr/lib/gconv/gconv-modules.cache
b5ea0000-b5edf000 r--p 00000000 08:13 716459     /usr/lib/locale/en_US.utf8/LC_CTYPE
b5edf000-b5f3e000 rw-p b5edf000 00:00 0 
b5f3e000-b5f53000 r-xp 00000000 08:13 651532     /usr/lib/libICE.so.6.3.0
b5f53000-b5f55000 rw-p 00014000 08:13 651532     /usr/lib/libICE.so.6.3.0
b5f55000-b5f57000 rw-p b5f55000 00:00 0 
b5f57000-b5f5e000 r-xp 00000000 08:13 651550     /usr/lib/libSM.so.6.0.0
b5f5e000-b5f5f000 rw-p 00006000 08:13 651550     /usr/lib/libSM.so.6.0.0
b5f5f000-b5f7d000 r-xp 00000000 08:13 651762     /usr/lib/libexpat.so.1.0.0
b5f7d000-b5f7f000 rw-p 0001e000 08:13 651762     /usr/lib/libexpat.so.1.0.0
b5f7f000-b5fac000 r-xp 00000000 08:13 653551     /usr/lib/libpangoft2-1.0.so.0.1800.3
b5fac000-b5fad000 rw-p 0002c000 08:13 653551     /usr/lib/libpangoft2-1.0.so.0.1800.3
b5fad000-b5fae000 rw-p b5fad000 00:00 0 
b5fae000-b6053000 r-xp 00000000 08:13 660209     /usr/lib/libmp4v2.so.0.0.0
b6053000-b6058000 rw-p 000a4000 08:13 660209     /usr/lib/libmp4v2.so.0.0.0
b6058000-b60a5000 r-xp 00000000 08:13 651601     /usr/lib/libXt.so.6.0.0
b60a5000-b60a9000 rw-p 0004c000 08:13 651601     /usr/lib/libXt.so.6.0.0
b60a9000-b60be000 r-xp 00000000 08:13 661075     /usr/lib/libaudio.so.2.4
b60be000-b60bf000 rw-p 00014000 08:13 661075     /usr/lib/libaudio.so.2.4
b60bf000-b60c6000 r-xp 00000000 08:13 1105456    /lib/tls/i686/cmov/librt-2.6.1.so
b60c6000-b60c8000 rw-p 00006000 08:13 1105456    /lib/tls/i686/cmov/librt-2.6.1.so
b60c8000-b60cc000 r-xp 00000000 08:13 651966     /usr/lib/libgthread-2.0.so.0.1400.1
b60cc000-b60cd000 rw-p 00003000 08:13 651966     /usr/lib/libgthread-2.0.so.0.1400.1
b60cd000-b60ce000 rw-p b60cd000 00:00 0 
b60ce000-b60d3000 r-xp 00000000 08:13 661073     /usr/lib/libartsc.so.0.0.0
b60d3000-b60d4000 rw-p 00004000 08:13 661073     /usr/lib/libartsc.so.0.0.0
b60d4000-b60d9000 r-xp 00000000 08:13 651918     /usr/lib/libgpm.so.1.19.6
b60d9000-b60da000 rw-p 00004000 08:13 651918     /usr/lib/libgpm.so.1.19.6
b60da000-b60e2000 r-xp 00000000 08:13 652286     /usr/li

```
I tried several options and tried several times, and always the same thing. It isn't only the last one, before it I got the same problem.

---

### Post by andrew.46 on 2008-03-02
Hi,

 Sorry to hear you are having trouble:

> **janfsd said:**
> Nice guide. Btw, is anybody having problems with the latest svn in gutsy?
It compiles fine, mplayer runs ok, the only problem is with gmplayer. I get this error:
```
MPlayer dev-SVN-r26139-4.1.3 (C) 2000-2008 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ (Family: 15, Model: 43, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE SSE2
*** glibc detected *** gmplayer: malloc(): memory corruption (fast): .

I can suggest a few things:

1. Post all of these details to mplayer-users and see if this is actually an *mplayer* problem.

2. While hopefully waiting for an answer from the mplayer users try backtracking to a 'safe' version. Revision 26096 is working fine for me:

[CODE]$ svn checkout -r 26096  svn://svn.mplayerhq.hu/mplayer/trunk mplayer
```

or perhaps go back a little further?

3. Have a trawl through: [http://svn.mplayerhq.hu/mplayer?view=rev](http://svn.mplayerhq.hu/mplayer?view=rev) and look for any evidence :-)

 Hopefully the issue will be resolved with a combination of the above 3?

    Andrew

---

### Post by janfsd on 2008-03-02
Thanks for the answer. But the problem is still on that revision. I am trying now to rollback serveral revision and to check. However I have a question do you use that revision on gutsy?
Btw, it seems I am not the only one with this problem:
[http://forum.ubuntu.org.cn/viewtopic.php?p=642172&sid=fdbdae599fb0d2d348fd2c3b2209a421](http://forum.ubuntu.org.cn/viewtopic.php?p=642172&sid=fdbdae599fb0d2d348fd2c3b2209a421)

EDIT: Tried several revisions, but the problem persists, I just posted the issue in the mailing list.

EDIT: after debugging, I found out the problem, it was a skin problem, and after checking several skins, it seems that with some of them it crashes. Well this happened with the skin 'Ater'. The problem was with the pos.png file of the skin, by replacing it with other, the skin works.

---

### Post by andrew.46 on 2008-03-02
Hi,

Glad to see that you have found the problem:

> **janfsd said:**
> Thanks for the answer. But the problem is still on that revision. I am trying now to rollback serveral revision and to check. However I have a question do you use that revision on gutsy?

In fact you have caught me out there :-) That is the revision I use on my *Slackware* partition, my apologies. The version I have on my Hardy Heron partition turns out to be a little older: MPlayer dev-SVN-r25959-4.2.3 and this version does not have the error that you are experiencing.

> Btw, it seems I am not the only one with this problem:
[http://forum.ubuntu.org.cn/viewtopic.php?p=642172&sid=fdbdae599fb0d2d348fd2c3b2209a421](http://forum.ubuntu.org.cn/viewtopic.php?p=642172&sid=fdbdae599fb0d2d348fd2c3b2209a421) 

Now that is a bit scary! I had no idea that my guide had such a wide audience!

> EDIT: Tried several revisions, but the problem persists, I just posted the issue in the mailing list.

Yes I saw that and hopefully a suitably skilled person will have a look at the problem. The mplayers-users people as you may know get a little irascible at times and I believe sometimes view the gui mplayer as an inconvenience. BTW when you said that the error generated a report automagically have you used:

```
  --enable-debug=3 \ 
 --enable-crash-debug  
```

in your compile options? This is something I have meant to use myself but have never really done :-)

>  EDIT: after debugging, I found out the problem, it was a skin problem, and after checking several skins, it seems that with some of them it crashes. Well this happened with the skin 'Ater'. The problem was with the pos.png file of the skin, by replacing it with other, the skin works.

Fascinating. So either a problem with the skins or with mplayer's handling of the skins or both. Did you find a skin that needed no alteration? I will alter the skin I have put in the guide until the svn version addresses the problem.

  All the best,

    Andrew

---

### Post by janfsd on 2008-03-02
> **andrew.46 said:**
> 
In fact you have caught me out there :-) That is the revision I use on my *Slackware* partition, my apologies. The version I have on my Hardy Heron partition turns out to be a little older: MPlayer dev-SVN-r25959-4.2.3 and this version does not have the error that you are experiencing. 
Well, at that time I was trying to see if it was a system specific issue, or some library problem. I spent a lot of time compiling several svn until I use the debugger and it was pointing to the file pos.png in particular. So I changed the skin and it worked :)

> Yes I saw that and hopefully a suitably skilled person will have a look at the problem. The mplayers-users people as you may know get a little irascible at times and I believe sometimes view the gui mplayer as an inconvenience. 
Probably, but somebody already replied in the mailing list :D
> BTW when you said that the error generated a report automagically have you used:

```
  --enable-debug=3 \ 
 --enable-crash-debug  
```

in your compile options? This is something I have meant to use myself but have never really done :-)
No, I didn't use that. The bt and the memory map where geneterated automatically in the output.

> 
Fascinating. So either a problem with the skins or with mplayer's handling of the skins or both. Did you find a skin that needed no alteration? I will alter the skin I have put in the guide until the svn version addresses the problem.

The skin in your guide is ok, it doesn't need to be changed. The skins affected that I know are: Ater, Terminator3 and Bluecurve. With each one, it crashes differently. For instance, for the skin Ater, the crash its caused because of pos.png (I think some transparencies problem) For the other, maybe the same file, however I didn't check.

Again, nice guide, I hope you keep maintaining it, unlike the other mplayer guides that are too old... And thanks for your help.

---

### Post by mangurt on 2008-03-03
Great thread Andrew!!

I finally have mplayer up and running, but I would like to tackle another part of this player.

I would like to be able to watch TV via mplayer.  I have a card that works via drivers from v4l-dvb, and the card works with TVviewer, but this program only works with analog, and I would like to view digital streams.  Looking at the mplayer page, it states that I need to create a channel file, but I am completely clueless on how to do this.

Does anyone use mplayer to watch TV?  Any help would be greatly appreciated!

---

### Post by andrew.46 on 2008-03-06
Hi,

Woooooooooooooo hoooooooooooooooooooooo!!!!!!!  

Can someone congratulate me? I have managed [to write a patch]("http://svn.mplayerhq.hu/mplayer?view=rev&revision=26181") that has been included in the svn mplayer source code!!!!!!!!!

It actually really only has relevance to my* other* distro but I am incredibly excited to see my work in such a great program.

Woooooooooooooo hoooooooooooooooooooooo!!!!!!! 


     Andrew

---

### Post by shirilover on 2008-03-06
> **mangurt said:**
> Great thread Andrew!!
Does anyone use mplayer to watch TV?  Any help would be greatly appreciated!

I don't have a TV tuner, but have you tried using the -tvscan autostart switch from the command line. It should output a list of values to be used with -tv channels=. You may also want to try -tv chanlist=.

Then, to watch TV, use mplayer tv://<channel num>

---

### Post by janfsd on 2008-03-06
> **andrew.46 said:**
> Hi,

Woooooooooooooo hoooooooooooooooooooooo!!!!!!!  

Can someone congratulate me? I have managed [to write a patch]("http://svn.mplayerhq.hu/mplayer?view=rev&revision=26181") that has been included in the svn mplayer source code!!!!!!!!!

It actually really only has relevance to my* other* distro but I am incredibly excited to see my work in such a great program.

Woooooooooooooo hoooooooooooooooooooooo!!!!!!! 


     Andrew
Nice to hear that, congratulations. ;)

---

### Post by mangurt on 2008-03-07
> **shirilover said:**
> I don't have a TV tuner, but have you tried using the -tvscan autostart switch from the command line. It should output a list of values to be used with -tv channels=. You may also want to try -tv chanlist=.

Then, to watch TV, use mplayer tv://<channel num>

No, I have not tried that yet!  Great suggestion!!  I will try that when I get home tonight!

---

### Post by andrew.46 on 2008-03-08
Hi,

 Am I the only one who cannot changer chapters while playing a DVD using gmplayer? This is with MPlayer dev-SVN-r26196-4.1.2 but with mplayer for at least the last 100 revision numbers.

 The program will generate a segmentation fault and crash on my system. I would be interested to hear if anyone can narrow down the actual revision that caused the damage.

           Andrew

---

### Post by SoulSmasher on 2008-03-09
is there any way i can use ffmpeg (preferly compiling from source or svn) with this? i compiled with guide at wiki, but i can't see in filters..(only xv, gl gl2 etc...)  i wanna watch .mkv HD movies which are encoded with x264. xv works ok if you don't make a resize but with resize, it sucks.. and gl's performance is soo bad :(

i used to use ffdshow in windows and it all was fine

how can i use it with mplayer, do i have to add something while compiling?

thanks for any advices :)

---

### Post by andrew.46 on 2008-03-09
Hi:


> **SoulSmasher said:**
> is there any way i can use ffmpeg (preferly compiling from source or svn) with this? i compiled with guide at wiki, but i can't see in filters..(only xv, gl gl2 etc...)  i wanna watch .mkv HD movies which are encoded with x264. xv works ok if you don't make a resize but with resize, it sucks.. and gl's performance is soo bad :(

i used to use ffdshow in windows and it all was fine

how can i use it with mplayer, do i have to add something while compiling?

thanks for any advices :)

I have hopefullyanswered your query in reasonable detail here:

[http://ubuntuforums.org/showpost.php?p=4485020&postcount=8](http://ubuntuforums.org/showpost.php?p=4485020&postcount=8)

in another thread.

               Andrew

---

### Post by fnx.lv on 2008-03-21
I just want to thank your for this post/tutorial. I have been using this guide every single time I reinstall ubuntu and it never fails.  Makes linux life a whole lot easier.  Thank you!

---

### Post by andrew.46 on 2008-03-21
Hi,

 Thanks for your kind message:

> **fnx.lv said:**
> I just want to thank your for this post/tutorial. I have been using this guide every single time I reinstall ubuntu and it never fails.  Makes linux life a whole lot easier.  Thank you!

 I am very glad this guide has been useful to you. I have drifted a little away from Ubuntu lately and will probably not update the guide past Hardy Heron but it still gives me a warm feeling to see the viewing numbers climbing steadily :-)

      Andrew

---

### Post by andrew.46 on 2008-03-31
Hi,

 It has been a while since this post, but there is some good news:

> **mangurt said:**
> Thanks for posting this guide, but I am having a problem with mplayer. [...] What I am trying to do is open an file via right click, and then open with mplayer.  No matter what file I try to open, I get this error.
Any help would be greatly appreciated.

 This problem has finally been resolved in the current svn of mplayer. I take more than a little pride in fact that it is [my patch]("http://svn.mplayerhq.hu/mplayer?view=rev&revision=26306") that has made the change.

 All the best,

   Andrew

---

### Post by xfroggy on 2008-04-13
Hi guys. Anyone could give me  a hint, since I'm running out of ideas on my own. After a few times of recompiling, I don't get 'gmplayer' only mplayer. I already tried w/ --enable-gui, --enable-gui --enable-menu, probably few other combinations as well, but somehow it never compiles gmplayer.

---

### Post by andrew.46 on 2008-04-13
Hi,

 Sorry to hear you are having some trouble:

> **xfroggy said:**
> Hi guys. Anyone could give me  a hint, since I'm running out of ideas on my own. After a few times of recompiling, I don't get 'gmplayer' only mplayer. I already tried w/ --enable-gui, --enable-gui --enable-menu, probably few other combinations as well, but somehow it never compiles gmplayer.

 Can you post the screen of information that appears after:

```
$ ./configure --enable-gui
```

You probably should be aware as well that the gmplayer is not the greatest gui ever seen and debate rages periodically amongst the mplayer devs about whether to abandon it or not. But we should be able to get it running anyway :-)

  Andrew

---

### Post by xfroggy on 2008-04-13
here's the output: [http://paste2.org/p/20381](http://paste2.org/p/20381)

> You probably should be aware as well that the gmplayer is not the greatest gui ever seen and debate rages periodically amongst the mplayer devs about whether to abandon it or not. But we should be able to get it running anyway 

Yea, its far from greatest, but every linux player is missing that *something*, so I usually end up switching between totem, mplayer, and xine depending on the task. If people would stop using those crippled wmv files, than totem would be great. :-k

---

### Post by andrew.46 on 2008-04-13
Hi,

 Very odd:

> **xfroggy said:**
> here's the output: [http://paste2.org/p/20381](http://paste2.org/p/20381)

 This seems to indicate you have correctly enabled the gui with the required X11 libraries in place. Do you get an error message when you press Alt-F2 and type in 'gmplayer' ?(without the '' of course).

    Andrew

---

### Post by xfroggy on 2008-04-13
ha I got used to it. If anything to go wrong, I'm always the first in line lol

yea I get an error w/ alt+f2

```
Could not open location 'file:///gmplayer'
The location or file could not be found.

```

```
xfroggy@brokenb0x:~/mplayer$ gmplayer
bash: /usr/bin/gmplayer: No such file or directory

```

lol I always end up being a minority w/ my errors :)

---

### Post by janfsd on 2008-04-13
Try to run gmplayer from the source and see the output. I suppose you need to create a symlink before, in the folder of the source do::
```
ln -s mplayer gmplayer
./gmplayer

```

---

### Post by xfroggy on 2008-04-13
thanks for the help! Yea making symlink 'gmplayer' worked, had to found out the hard way as i didn't see it mention nowhere :S

Funny though because in DOCS it says I have to execute the binary 'gmplayer' lol...

> 
You can build it by specifying --enable-gui during ./configure. Then, to turn on GUI mode, you have to execute the gmplayer binary.

---

### Post by janfsd on 2008-04-13
I suppose that one of the latest svn got something wrong with creating the symlink. That's why it didn't work. Btw, I can suggest Smplayer, I think it's the greatest gui for mplayer.

---

### Post by xfroggy on 2008-04-13
wow I can't believe I didn't came across SMplayer till now! It's pretty much everything I been looking so far. thanx guys for the help :D

---

### Post by SoulSmasher on 2008-04-26
works perfect on hardy, as gutsy :) thanks again for the great guide

ps: yep, up to me, smplayer is the best mplayer gui so far

---

### Post by andrew.46 on 2008-04-26
Hi:

> **SoulSmasher said:**
> works perfect on hardy, as gutsy :) thanks again for the great guide

Thanks for that! I have invested a huge amount of time in this guide but I am glad that it seems to have provided a lot of people with acces to a program that can be a little to compile under most linux distros.

I have not personally tried smplayer but I think the time has almost come to abandon gmplayer on my personal setup and smplayer is getting all the publicity...

       Andrew

---

### Post by janfsd on 2008-04-28
Maybe you could add, howto install mplayer plugin for firefox. I prefer it more than the totem one. And even better is the gecko-mplayer plugin, it is by the same author and unlike the mplayer-plugin it is actively developed. The catch is that you need to install with it gnome-mplayer. But it works great, it opens everything in the browser.

---

### Post by andrew.46 on 2008-05-07
======================================================
Howto: Compile the svn mplayer against the latest x264
======================================================

A little bit extra for this svn mplayer guide if anyone is interested? If you wish to compile mplayer against the very latest release of x264 to optimise *encoding* you will need to follow these steps *before* compiling the svn mplayer:

First download a few utilities that may or may not already be on your system:

```
$ sudo apt-get install  build-essential xmlto git-core gpac libgpac-dev libgpac0.4.4 
```

Next download and compile the assembler required for optimal x264 compilation. I could not get x264 to recognise the repository offerings in any shape or form so I suggest that you compile your own as I did:

```
$ cd $HOME
$ wget http://www.tortall.net/projects/yasm/releases/yasm-0.7.0.tar.gz
$ tar xvf yasm-0.7.0.tar.gz
$ cd yasm-0.7.0
$ make
$ sudo make install
$ make clean
```

Next to download the x264 source code from the videolan git repository, the svn repository now being only a memory. First uninstall the repository x264 dev file that was used previously when compiling the svn mplayer and then download, compile and install the x264 source code:

```
$ cd $HOME
$ sudo apt-get remove libx264-dev 
$ git clone git://git.videolan.org/x264.git
$ cd x264
$ ./configure --enable-shared --enable-pthread --enable-mp4-output
$ make
$ sudo make install
$ make clean
```

And finally compile the svn mplayer as before and the new x264 libraries should be picked up automagically. How easy is that! I would suggest the following steps as well so that when you wish to update x264 it can be done very simply. First set up an alias:

```
$ git config --global alias.up "pull --rebase"
```

and then you can update from the x264 directory as follows:

```
$ git up
```

Further details about how to manipulate the videolan git repository can be found at: [http://wiki.videolan.org/Git](http://wiki.videolan.org/Git)

Don't forget that x264 can be used as standalone program as well. Simply run x264 --help to see the options available. And remember: Have Fun!

   Andrew

---

### Post by unlotto on 2008-05-08
> **andrew.46 said:**
> ======================================================
Howto: Compile the svn mplayer against the latest x264
======================================================

Andrew

Hey there Andrew. I haven't read all pages of this forum post, so I don't know if it has been mentioned before. I'd like to add that x264  is a [_library for encoding h264_]("http://en.wikipedia.org/wiki/X264"), and so has no effect on the decoding performance (playback) of, for example, 1080p mkv files with h264 video.

Maybe it would be a good idea to mention this in your #1 post or the x264 post.

Just to add, the codec responsible for decoding of h264 in mplayer is from ffmpeg. It's called ffh264. 

Before I go too much off topic I just want to mention; if people are after a performance increase of said codec, I would suggest trying playback with ```
mplayer -lavdopts fast:threads=2
``` (if dual core). If the machine just can't playback smoothly one need to look at mplayer + coreavc, which I wrote briefly about [_here_]("http://www.utilitybox.org/mplayer_h264_linux.php") in case someone is interested. It is not a howto.

---

### Post by gillza on 2008-05-11
Hi all,

I have compiled and installed mplayer+gui twice using this guide before. Both times successfully. Today while installing I got a little snag. After installation, tried to run **gmplayer** and got:

The program 'gmplayer' is currently not installed.

It looks like gmplayer is not created during "make" (or i might be wrong). Tried searching for gmplayer and found only a header file.
--enable-gui was specified during configuration. I wonder if anyone encountered the same problem and how you solved it?

Thank you.

---

### Post by andrew.46 on 2008-05-11
Hi,

Glad this guide has been useful to you. It scares me a little that it has now hit 30,000 views :). I still wonder if I will get a free Ubuntu T-shirt at this number?

You have encountered the turbulence that is surrounding the svn mplayer with some substantial reworking of the config / makefile setup:


> **gillza said:**
> 
I have compiled and installed mplayer+gui twice using this guide before. Both times successfully. Today while installing I got a little snag. After installation, tried to run **gmplayer** and got:

The program 'gmplayer' is currently not installed.

It looks like gmplayer is not created during "make" (or i might be wrong). Tried searching for gmplayer and found only a header file.
--enable-gui was specified during configuration. I wonder if anyone encountered the same problem and how you solved it?


I will admit to not having installed the gmplayer for a while but I can certainly confirm the problem you have experienced when I compiled with this enabled. The easiest way to enable gmplayer *at the moment* seems to be to add the line "sudo make install-gui" after the usual install. So:

```
$ cd $HOME/Desktop/mplayer
$ ./configure --enable-gui --enable-menu
$ make 
$ sudo make install
$ sudo make install-gui
$ sudo make clean
```

and this certainly worked on my own system. I have not added this to the walkthrough as I am not sure if this a temporary glitch or a permanent change. I have queried mplayer-users on this issue at:

[http://lists.mplayerhq.hu/pipermail/mplayer-users/2008-May/073015.html](http://lists.mplayerhq.hu/pipermail/mplayer-users/2008-May/073015.html)

     Andrew

---

### Post by gillza on 2008-05-11
> **andrew.46 said:**
> Hi,

Glad this guide has been useful to you. It scares me a little that it has now hit 30,000 views :). I still wonder if I will get a free Ubuntu T-shirt at this number?


I think you definitely deserve a t-shirt!!! Not only for this howto but for your prompt responses as well! 


```
$ cd $HOME/Desktop/mplayer
$ ./configure --enable-gui --enable-menu
$ make 
$ sudo make install
$ sudo make install-gui
$ sudo make clean
```

**This has worked!!! Thank you very much!**

> 
I have not added this to the walkthrough as I am not sure if this a temporary glitch or a permanent change. I have queried mplayer-users on this issue at:

[http://lists.mplayerhq.hu/pipermail/mplayer-users/2008-May/073015.html](http://lists.mplayerhq.hu/pipermail/mplayer-users/2008-May/073015.html)

     Andrew

Let's hope that this is just a temporary problem. I wonder though, how did you find out about **make install-gui** I have searched and not found anything about it... i wonder if i missed it somehow..

Anyway, thank you very much! I'm off to enjoy freshly downloaded anime watching it through mplayer :))

---

### Post by andrew.46 on 2008-05-11
> **gillza said:**
> I think you definitely deserve a t-shirt!!! Not only for this howto but for your prompt responses as well! 

I was only kidding about the T-shirt of course, I get a huge amount of enjoyment out of this walkthrough and tinkering with mplayer.

> Let's hope that this is just a temporary problem. I wonder though, how did you find out about **make install-gui** I have searched and not found anything about it... i wonder if i missed it somehow..

I found the solution on the mplayer-users list by searching their archives:

[http://archives.free.net.ph/list/mplayer-users.en.html](http://archives.free.net.ph/list/mplayer-users.en.html)

Usually if there is a problem in the current svn their will be a discussion there and this is true in this case. Unfortunately things move a little slowly with the gui as there is a lack of enthusiasm for its development so we will see if it will be rectified. The problem is in the makefile I suspect and this could be easily patched but that makefile is huge ...

But good news that it is all running again for you!

         Andrew

---

### Post by andrew.46 on 2008-05-12
Well it may be very temporary as it turns out:

> **gillza said:**
> Let's hope that this is just a temporary problem.

I spent some time looking at the makefile where there had been an obvious blockage and I believe I have found the error. Line 641 reads:
```

INSTALL_TARGETS-$(GUI)      += install-gui
```

while it should actually be:

```
INSTALL_TARGETS-$(GUI_GTK)  += install-gui
```

I have [submitted a patch]("http://lists.mplayerhq.hu/pipermail/mplayer-dev-eng/2008-May/057424.html") and with any luck it will be applied, the problem will be fixed and the glory will be mine :-)

```
Index: Makefile
===================================================================
--- Makefile	(revision 26746)
+++ Makefile	(working copy)
@@ -638,7 +638,7 @@
 
 INSTALL_TARGETS-$(MPLAYER)  += install-mplayer  install-mplayer-man
 INSTALL_TARGETS-$(MENCODER) += install-mencoder install-mplayer-man
-INSTALL_TARGETS-$(GUI)      += install-gui
+INSTALL_TARGETS-$(GUI_GTK)  += install-gui
 INSTALL_TARGETS             += $(INSTALL_TARGETS-yes)
 
 DIRS =  . \
```

Looks like this error occurred in Revision 26398 on April 11th where this change was overlooked.

    Andrew

---

### Post by andrew.46 on 2008-05-13
Hi again!

Time to congratulate me:

> **gillza said:**
> 
Let's hope that this is just a temporary problem.

My patch has been applied and the problem rectified:

[http://svn.mplayerhq.hu/mplayer?view=rev&revision=26754](http://svn.mplayerhq.hu/mplayer?view=rev&revision=26754)

Woooooooooo hooooooooooooooooo!!!!!

         Andrew

---

### Post by 12barz on 2008-05-13
Couldn't resist doing it, even though a Noob.  Thanks.  Now for the Noob question.  Do I need to leave all the files on my desktop?  Obviously the tar's can be deleted.  Anything else?  Would it hurt to move whatever must remain?  Where do people usually keep them?

---

### Post by andrew.46 on 2008-05-14
Hope it all worked well?

> **12barz said:**
> Couldn't resist doing it, even though a Noob.  Thanks.  Now for the Noob question.  Do I need to leave all the files on my desktop?  Obviously the tar's can be deleted.  Anything else?  Would it hurt to move whatever must remain?  Where do people usually keep them?

This is a housekeeping issue really. I keep all my downloaded source code in subdirectories under $HOME/source. The svn mplayer source code is special too as you can navigate to its directory and update all the code by running:

```
$ svn update
```

Different people will do this in different ways I guess. The choice I made to base everything on the Desktop was arbitrary.

     Andrew

---

### Post by SilverSword on 2008-05-18
Hi,

not sure if this has been posted before, but:

I've compiled it and it all runs and opens, but before video playback, I get:
ERROR: Could not open required DirectShow codec drvc.dll
DirectShow in Ubuntu? :S


and after playback, I get:
Fatal error: MPlayer interrupted by signal 11 in module: decode video
Fatal error: Mplayer has crashed by bad usage of CPU/FPU/RAM. Recompile MPlayer with --enable-debug and make 'gdb' backtrace and dissassembly. Details in DOCS/html/en/bugreports_what.html#bugreports_crash.

Then I get an 'Mplayer Crashed' message.

Any idea of what I didn't do or what I did wrong?

Thanks.

---

### Post by andrew.46 on 2008-05-18
Hi,

Sorry to hear that you are having trouble:

> **SilverSword said:**
> 
I've compiled it and it all runs and opens, but before video playback, I get:
ERROR: Could not open required DirectShow codec drvc.dll
DirectShow in Ubuntu? :S

Can you confirm that you have all the codecs in place as follows:

```
andrew@ilium/usr/local/lib/codecs$ ls
AvidQTAVUICodec.qtx          cook.so.6.0   l3codeca.acm    rt32dcmp.dll  vp31vfw.dll
BeHereiVideo.qtx             ctadp32.acm   l3codecx.ax     scg726.acm    vp4vfw.dll
CLRVIDDC.DLL                 ddnt.so.6.0   lhacm.acm       sipr.so.6.0   vp5vfw.dll
CtWbJpg.DLL                  divx.dll      lsvxdec.dll     sp5x_32.dll   vp6vfw.dll
DECVW_32.DLL                 divx_c32.ax   m3jp2k32.dll    tm20dec.ax    vp7vfw.dll
LCMW2.dll                    divxa32.acm   m3jpeg32.dll    tokf.so.6.0   vssh264.dll
LCODCCMW2E.dll               divxc32.dll   m3jpegdec.ax    tokr.so.6.0   vssh264core.dll
LCodcCMP.dll                 divxdec.ax    mcdvd_32.dll    tsccvid.dll   vssh264dec.dll
QuickTime.qts                dnet.so.6.0   mcmjpg32.dll    tsd32.dll     vsshdsd.dll
QuickTimeEssentials.qtx      drv2.so.6.0   mi-sc4.acm      tssoft32.acm  vsslight.dll
QuickTimeInternetExtras.qtx  drv3.so.6.0   mpg4c32.dll     tvqdec.dll    vsswlt.dll
README                       drv4.so.6.0   mpg4ds32.ax     ubv263d+.ax   wma9dmod.dll
VDODEC32.dll                 drvc.so       msadp32.acm     ubvmp4d.dll   wmadmod.dll
ViVD2.dll                    dspr.so.6.0   msg711.acm      ultimo.dll    wmsdmod.dll
acelpdec.ax                  frapsvid.dll  msgsm32.acm     vdowave.drv   wmspdmod.dll
alf2cd.acm                   huffyuv.dll   msh261.drv      vgpix32d.dll  wmv8ds32.ax
aslcodec_dshow.dll           i263_32.drv   msms001.vwp     vid_3ivX.xa   wmv9dmod.dll
aslcodec_vfw.dll             iac25_32.ax   msnaudio.acm    vid_cvid.xa   wmvadvd.dll
asusasv2.dll                 iccvid.dll    msrle32.dll     vid_cyuv.xa   wmvdmod.dll
asusasvd.dll                 icmw_32.dll   msscds32.ax     vid_h261.xa   wmvds32.ax
ativcr2.dll                  imaadp32.acm  msvidc32.dll    vid_h263.xa   wnvplay1.dll
atrac3.acm                   imc32.acm     mvoiced.vwp     vid_iv32.xa   wnvwinx.dll
atrc.so.6.0                  ir32_32.dll   nsrt2432.acm    vid_iv41.xa   wvc1dmod.dll
avimszh.dll                  ir41_32.dll   pclepim1.dll    vid_iv50.xa   xanlib.dll
avizlib.dll                  ir50_32.dll   qdv.dll         vivog723.acm  zmbv.dll
clrviddd.dll                 ivvideo.dll   qpeg32.dll      vmnc.dll
cook.so                      jp2avi.dll    qtmlClient.dll  voxmsdec.ax
```

     Andrew

---

### Post by SilverSword on 2008-05-19
```
acelpdec.ax          l3codeca.acm                 ubv263d+.ax
alf2cd.acm           l3codecx.ax                  ubvmp4d.dll
aslcodec_dshow.dll   LCMW2.dll                    ultimo.dll
aslcodec_vfw.dll     LCodcCMP.dll                 VDODEC32.dll
asusasv2.dll         LCODCCMW2E.dll               vdowave.drv
asusasvd.dll         lhacm.acm                    vgpix32d.dll
ativcr2.dll          lsvxdec.dll                  vid_3ivX.xa
atrac3.acm           m3jp2k32.dll                 vid_cvid.xa
atrc.so.6.0          m3jpeg32.dll                 vid_cyuv.xa
AvidQTAVUICodec.qtx  m3jpegdec.ax                 vid_h261.xa
avimszh.dll          mcdvd_32.dll                 vid_h263.xa
avizlib.dll          mcmjpg32.dll                 vid_iv32.xa
BeHereiVideo.qtx     mi-sc4.acm                   vid_iv41.xa
CLRVIDDC.DLL         mpg4c32.dll                  vid_iv50.xa
clrviddd.dll         mpg4ds32.ax                  ViVD2.dll
cook.so              msadp32.acm                  vivog723.acm
cook.so.6.0          msg711.acm                   vmnc.dll
ctadp32.acm          msgsm32.acm                  voxmsdec.ax
CtWbJpg.DLL          msh261.drv                   vp31vfw.dll
ddnt.so.6.0          msms001.vwp                  vp4vfw.dll
DECVW_32.DLL         msnaudio.acm                 vp5vfw.dll
divxa32.acm          msrle32.dll                  vp6vfw.dll
divx_c32.ax          msscds32.ax                  vp7vfw.dll
divxc32.dll          msvidc32.dll                 vssh264core.dll
divxdec.ax           mvoiced.vwp                  vssh264dec.dll
divx.dll             nsrt2432.acm                 vssh264.dll
dnet.so.6.0          pclepim1.dll                 vsshdsd.dll
drv2.so.6.0          qdv.dll                      vsslight.dll
drv3.so.6.0          qpeg32.dll                   vsswlt.dll
drv4.so.6.0          qtmlClient.dll               wma9dmod.dll
drvc.so              QuickTimeEssentials.qtx      wmadmod.dll
dspr.so.6.0          QuickTimeInternetExtras.qtx  wmsdmod.dll
frapsvid.dll         QuickTime.qts                wmspdmod.dll
huffyuv.dll          README                       wmv8ds32.ax
i263_32.drv          rt32dcmp.dll                 wmv9dmod.dll
iac25_32.ax          scg726.acm                   wmvadvd.dll
iccvid.dll           sipr.so.6.0                  wmvdmod.dll
icmw_32.dll          sp5x_32.dll                  wmvds32.ax
imaadp32.acm         tm20dec.ax                   wnvplay1.dll
imc32.acm            tokf.so.6.0                  wnvwinx.dll
ir32_32.dll          tokr.so.6.0                  wvc1dmod.dll
ir41_32.dll          tsccvid.dll                  xanlib.dll
ir50_32.dll          tsd32.dll                    zmbv.dll
ivvideo.dll          tssoft32.acm
jp2avi.dll           tvqdec.dll
```

Checked that through a few times, from what I can see they're all there.

---

### Post by andrew.46 on 2008-05-19
Hi again:

> **SilverSword said:**
> Checked that through a few times, from what I can see they're all there.

Well that should eliminate a problem with the codecs, although just be sure that you have installed the following codec pack:

```
$ wget http://www.mplayerhq.hu/MPlayer/releases/codecs/all-20071007.tar.bz2
```

and they are all placed in /usr/local/lib/codecs and mplayer has been compiled against *these* codecs.

Can I ask what the output of the following is:

```
$ mplayer | head -n 4
```

and this one:

```
$ mplayer -vc help | grep realvid
```

and finally can you post a link to the file or files that are giving the trouble and a full quote of your command line and the subsequent error message?

    Andrew

---

### Post by andrew.46 on 2008-05-22
Oh well perhaps all is well now? The codecs command should reveal:

```
andrew@ilium~$ mplayer -vc help | grep realvid
rv3040      realvid   working   Linux RealPlayer 10 RV30/40 decoder  [drvc.so]
[COLOR="Red"]**rv3040win   realvid   working   Win32 RealPlayer 10 RV30/40 decoder  [drvc.dll]**[/COLOR]
rv40        realvid   working   Linux RealPlayer 9 RV40 decoder  [drv4.so.6.0]
rv40win     realvid   working   Win32 RealPlayer 9 RV40 decoder  [drv43260.dll]
rv40mac     realvid   working   Mac OS X RealPlayer 9 RV40 decoder  [drvc.bundle/Contents/MacOS/drvc]
rv30        realvid   working   Linux RealPlayer 8 RV30 decoder  [drv3.so.6.0]
rv30win     realvid   working   Win32 RealPlayer 8 RV30 decoder  [drv33260.dll]
rv30mac     realvid   working   Mac OS X RealPlayer 9 RV30 decoder  [drvc.bundle/Contents/MacOS/drvc]
rv20        realvid   working   Linux RealPlayer 8 RV20 decoder  [drv2.so.6.0]
rv20winrp10 realvid   working   Win32 RealPlayer 10 RV20 decoder  [drv2.dll]

rv20win     realvid   working   Win32 RealPlayer 8 RV20 decoder  [drv23260.dll]
rv20mac     realvid   working   Mac OS X RealPlayer 9 RV20 decoder  [drv2.bundle/Contents/MacOS/drv2]
```

And you will see the relevant codec there.

             Andrew

---

### Post by ajw107 on 2008-05-27
Hi

I'm sorry to bother you, but I've just used your wonderful tutorial to compile mplayer.  Unfortunately I was wanting to do so to add support for LCDproc, but was unable to figure out how to enable this.  Do you know if this is even possible?

---

### Post by andrew.46 on 2008-05-27
Hi,

Glad the tutorial was useful for you:

> **ajw107 said:**
> I'm sorry to bother you, but I've just used your wonderful tutorial to compile mplayer.  Unfortunately I was wanting to do so to add support for LCDproc, but was unable to figure out how to enable this.  Do you know if this is even possible?

Unfortunately I believe that there is nothing that can be done from the mplayer side of things in the manner of a plugin that will enable support for LCDproc. The only info that I could find was for lcd-stuff which I see from another post that does not meet your needs.

Have you tried chasing this up on the [LCDProc mailing list]("http://lcdproc.org/mail.php3")? The only info there at the moment seems to relate to lcd-stuff.

    Andrew

---

### Post by ajw107 on 2008-05-28
Hi Andrew

Thank you for your very quick reply.  Unfortunately (on my system at least) lcd-stuff and mythlcdserver really don;t seem to like each other very much and stop each other from working.  I have not tired the mailing list thought (although I have searched it), but I think I will try that next, thank you again for everything you've done.

On a side note I;ve also been able to enable dvd navigation (with menus) on mplayer with either the number pad keys or the mouse, if anyone would be interested I can add this.  There are a few tutorials on the net, but I know they did not go quite to plan, and you had to copy the shared libraries to the right place.

---

### Post by andrew.46 on 2008-05-28
Hi!

> **ajw107 said:**
> Unfortunately (on my system at least) lcd-stuff and mythlcdserver really don;t seem to like each other very much and stop each other from working.  I have not tired the mailing list thought (although I have searched it), but I think I will try that next, thank you again for everything you've done.

I wish you all the best with this. There does not seem to be a lot of information on this subject out there at the moment.

> On a side note I;ve also been able to enable dvd navigation (with menus) on mplayer with either the number pad keys or the mouse, if anyone would be interested I can add this.  There are a few tutorials on the net, but I know they did not go quite to plan, and you had to copy the shared libraries to the right place.

Actually buried away in the responses to this tutorial is a smaller 'Howto' on exactly this subject:

[http://ubuntuforums.org/showpost.php?p=4351097&postcount=193](http://ubuntuforums.org/showpost.php?p=4351097&postcount=193)

I have not added it to the main section as at that time the libdvdnav project was very much in beta stage. I note that recently this has changed and a lot of work has been done. Is the information on that page similar to the method that you have used yourself?

     Andrew

---

### Post by ajw107 on 2008-05-29
Wow, a very impressive how-to, that is almost exactly what I was going to put.  The only two things I would add is if you get a lot of erros about static librardies (libdvdnav.so.4, etc) just go to the root directory:
cd /
then do a:
sudo find -name <name of file in error>
to find out where it is, and then:
sudo cp <location of file> /usr/local/lib/

To get it to work with lirc you make the config file:
config = dvdnav X
where x is:
1 for Up
2 for Down
3 for Left
4 for Right
5 for Menu
6 for Select

To change subtitles:
config = sub_select
To change audio:
config = switch_audio
To change chapter:
config = seek_chapter +1 #(forward)
config = seek_chapter -1 #(back)


Right, now fingers crossed that I get a reply from the list (and about my annoying hvr-4000 to, but that's a whole other thread)!

---

### Post by andrew.46 on 2008-05-29
Hi:

> **ajw107 said:**
> Wow, a very impressive how-to, that is almost exactly what I was going to put.  

To tell the truth I am not going to include libdvdnav in this 'howo' as I believe, perhaps incorrectly, that the code is still in very early development and there are too many potential problems with different versions of libdvdread*. So I will hold off until dvd navigation is included in the svn mplayer source code and this is a very long way away as there is resistance to its inclusion.

In the meantime why don't you publish and support an independent thread in 'Tutorials and Tips' devoted to dvd navigation with the svn mplayer? There would be keen interest in this I suspect and lots of support questions as well :-). I would then edit out my own mini Howto on the subject and link to your more fully feautured one.

         Andrew

---

### Post by andrew.46 on 2008-06-07
Hmmmmm.... there is a little movement on incorporating libdvdnav into the svn mplayer code. The following thread looks very promising:

[http://lists.mplayerhq.hu/pipermail/mplayer-dev-eng/2008-June/057762.html](http://lists.mplayerhq.hu/pipermail/mplayer-dev-eng/2008-June/057762.html)

So perhaps hold off writing a guide that may very well be obsolete soon!

            Andrew

---

### Post by ForksHolder on 2008-06-13
Great HowTo, Thank you :)

Little note,
In Codecs + Skin howto, you may clean the tar.gz file.

In the end put rm all-20071007.tar.bz2 for the Codecs and rm Blue-1.7.tar.bz2 for the skin.

Thanks again ^.-

---

### Post by dotancohen on 2008-06-17
> **ForksHolder said:**
> In the end put rm all-20071007.tar.bz2 for the Codecs and rm Blue-1.7.tar.bz2 for the skin.

I find it ironic that you suggest the inclusion of rm, but your sig warns users NOT to perform rm commands.

In other news, when I get to the step of building from SVN, the process fails with this output:

```
  -I/usr/include/freetype2 -I/usr/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1     -c -o adxenc.o adxenc.c
cc -DHAVE_AV_CONFIG_H -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_ISOC9X_SOURCE -I.. -I.. -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DHAVE_CONFIG_H -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT -I/usr/include/kde/artsc -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  -D_REENTRANT    -I/usr/include/freetype2 -I/usr/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1     -c -o g726.o g726.c
cc -DHAVE_AV_CONFIG_H -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_ISOC9X_SOURCE -I.. -I.. -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DHAVE_CONFIG_H -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT -I/usr/include/kde/artsc -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  -D_REENTRANT    -I/usr/include/freetype2 -I/usr/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1     -c -o libamr.o libamr.c
libamr.c:80:30: error: amrnb/interf_dec.h: No such file or directory
libamr.c:81:30: error: amrnb/interf_enc.h: No such file or directory
libamr.c:93: error: field 'mode' has incomplete type
libamr.c: In function 'getBitrateMode':
libamr.c:100: error: 'MR475' undeclared (first use in this function)
libamr.c:100: error: (Each undeclared identifier is reported only once
libamr.c:100: error: for each function it appears in.)
libamr.c:101: error: 'MR515' undeclared (first use in this function)
libamr.c:102: error: 'MR59' undeclared (first use in this function)
libamr.c:103: error: 'MR67' undeclared (first use in this function)
libamr.c:104: error: 'MR74' undeclared (first use in this function)
libamr.c:105: error: 'MR795' undeclared (first use in this function)
libamr.c:106: error: 'MR102' undeclared (first use in this function)
libamr.c:107: error: 'MR122' undeclared (first use in this function)
libamr.c:115: warning: return makes integer from pointer without a cast
libamr.c: At top level:
libamr.c:699: warning: initialization from incompatible pointer type
make[1]: *** [libamr.o] Error 1
make[1]: Leaving directory `/home/hardy2/Desktop/mplayer/libavcodec'
make: *** [libavcodec/libavcodec.a] Error 2
hardy2@hardy2-laptop:~$

```

I am running Kubuntu 8.04 (Hardy) and of course I had installed the prerequisite files for Hardy as specified in the f1rst p0st. Other than the default repos, I have Mediabuntu configured as well. Thanks in advance for help compiling.

---

### Post by andrew.46 on 2008-06-17
Hi,

Sorry to see you are having a little trouble:

> **dotancohen said:**
> I find it ironic that you suggest the inclusion of rm, but your sig warns users NOT to perform rm commands.

Well rm is a useful command but something of a sensitive one on the forums at the moment, However I believe in these cases the tarballs are best kept to one side as backup files for possible reinstalls. Depends on your personal preferences really.


> In other news, when I get to the step of building from SVN, the process fails with this output:

```
 
[...]
libamr.c:80:30: error: amrnb/interf_dec.h: No such file or directory
libamr.c:81:30: error: amrnb/interf_enc.h: No such file or directory
[...]

```

I suspect that the error could be with your installation of the amr libraries. On my Ubuntu system the following exist:

```
/usr/local/include/amrnb/interf_rom.h
/usr/local/include/amrnb/interf_dec.h
/usr/local/include/amrnb/interf_enc.h
```


You have 2 choices really:

[LIST=1]
[*]**Reinstall the amr libraries**: How did you install these before? You might like to try Appendix 3 of the walkthrough which has worked well on my own system.
[*]**Compile without them** : If you don't want to access amr files with mplayer simply use the following configure line: ./configure --disable-libamr_nb --disable-libamr_wb 
[/LIST]

A common problem with installing the amr libraries is that they are not available as shared libraries so watch the ./configure line with these. In the Appendix I have carefully specified 
```

$ ./configure  --enable-shared --disable-static
```

For exactly this reason. Please let me know if either of these options help you out.

All the very best,

   Andrew

PS I just recognised the name: the father of the laughing girl!!! Good to hear from you again.

---

### Post by dotancohen on 2008-06-17
> **andrew.46 said:**
> PS I just recognised the name: the father of the laughing girl!!! Good to hear from you again.

Thank, Andrew. We now have another laugher on the way, I'll let you know if it is a boy or a girl near the end of October! We wish that your granddaughter will soon be an older sister as well!

It turns out that I was in fact not compiling Narrow Band. I had written a script to download and compile AMR wide, AMR narrow, OSD fonts, Mplayer SVN, skin, codecs, and update apt-get. As I am new to scripting I had a mistake in the compilation part. I was in fact using the flags that you mention, or at least, that was my intention. I would post the script here but it's hacky and full of bugs.

By the way, what is the purpose of downloading the [http://www.3gpp.org/ftp/Specs/archive/26_series/26.204/26204-700.zip](http://www.3gpp.org/ftp/Specs/archive/26_series/26.204/26204-700.zip) file in the AMR builds?

Thanks, Andrew, and I think it's great that you stay so active in this thread.

---

### Post by andrew.46 on 2008-06-17
Hi:

> **dotancohen said:**
> Thank, Andrew. We now have another laugher on the way, I'll let you know if it is a boy or a girl near the end of October! We wish that your granddaughter will soon be an older sister as well!

Congratulations and I hope all goes well. I suspect that I will be the grandfather of only one for quite some time yet but I guess we will see :-).

> It turns out that I was in fact not compiling Narrow Band. I had written a script to download and compile AMR wide, AMR narrow, OSD fonts, Mplayer SVN, skin, codecs, and update apt-get. As I am new to scripting I had a mistake in the compilation part. I was in fact using the flags that you mention, or at least, that was my intention. I would post the script here but it's hacky and full of bugs.

That makes sense with the completely missing file. I have a similar script that I use for slackware which I tinker with constantly. Actually slackware has some 'official' scripts that do this, perhaps you could have a look at:

[http://slackbuilds.org/repository/12.1/multimedia/MPlayer/](http://slackbuilds.org/repository/12.1/multimedia/MPlayer/)

although it does not deal with svn and 'dev' files do not exist in slackware, nevertheless there is some very clever scripting there.


> By the way, what is the purpose of downloading the [http://www.3gpp.org/ftp/Specs/archive/26_series/26.204/26204-700.zip](http://www.3gpp.org/ftp/Specs/archive/26_series/26.204/26204-700.zip) file in the AMR builds?

This is the actual 3GPP source code and I gather there can be some 'legal' issues with using it. So the gentleman who packages the nice install routine has distanced himself a little from downloading it and made it the responsibility of the end-user. The details are here, near the end of the page:

[http://www.penguin.cz/~utx/amr](http://www.penguin.cz/~utx/amr)

> Thanks, Andrew, and I think it's great that you stay so active in this thread.

My pleasure. This thread constantly prods me into learning more about MPlayer :-)

   Andrew

---

### Post by Nullack on 2008-06-24
Thanks very much Andrew :)

Question, is the compile optimised for my CPU? is the flags 100% for my setup following your guide?

Cheers

---

### Post by andrew.46 on 2008-06-24
Hi Nullack,

> **Nullack said:**
> Question, is the compile optimised for my CPU? is the flags 100% for my setup following your guide?

MPlayer is a little different from most programs to compile in that the developers actively *discourage* setting options to optimise performance on a particular machine. In fact if you try to get some help from mplayer-users while using your own custom flags you will get no help. They can be a little hostile at times :-).

So the short answer is yes to both, the compile process should find the correct settings for your computer automagically. Often messing with the settings manually can be a little counter-productive but if you wish to alter the settings nobody will stop you :-). Have a look at the results of ./configure --help from the mplayer directory and you will see many, many settings that can be set manually but are usually not. 

A couple of interesting ones in there:

[LIST=1]
[*]**--enable-runtime-cpudetection** This is required if you are producing binaries for use on other machines. In our setting this usually means using the fakeroot debian/rules binary method.
[*]**--enable-debug=3** This is required if you need to submit a bug report to mplayer-users
[*]**--disable-dvdread-internal** This is required if you wish to use libdvdread.
[/LIST]

But the scary stuff that you are after is at the bottom under "Advanced Options:".

 All the best,

   Andrew

---

### Post by Nullack on 2008-06-25
Many thanks Andrew, top stuff mate.

mplayer: error while loading shared libraries: libx264.so.60: cannot open shared object file: No such file or directory

So Im trying to do the x264 as well. Ive done this twice to be sure of my process. I did the git update to get the latest x264, compiled it, cleaned it, then did svn update, compiled it and cleaned it as well.

As you can see mplayer wont run.I tried googling but I didnt find relevance except:

[http://mailman.videolan.org/pipermail/x264-devel/2008-June/004607.html](http://mailman.videolan.org/pipermail/x264-devel/2008-June/004607.html)

---

### Post by Nullack on 2008-06-25
I have some feedback about gmplayer:

1. It looks bad, jagged edges on the skin
2. I dont like the file open dialogue. It has one click instead of two click activation and the window is generally clumsy
3. The ff and rw buttons do not cue they skip
4. The cue back and forward buttons do nothing

Overall, its crap. Sorry but it is. I like how mplayer has good resource use and wide codec support. Command line mplayer is fine.

The fix? Well really there is two prime time mplayer front ends. SMplayer is QT, which I wont use. The Gnome GTK goodness is provided by gnome-mplayer. Heres some info:

[http://kdekorte.googlepages.com/gnomemplayer](http://kdekorte.googlepages.com/gnomemplayer)

Info on nailer for thumbnails:

[http://dekorte.homeip.net/download/nailer/](http://dekorte.homeip.net/download/nailer/)

Info on getting rid of Totem:

[http://kdekorte.googlepages.com/article1](http://kdekorte.googlepages.com/article1)

Andrew can I please encourage you to consider providing the option in your excellent how to with using gnome-mplayers front end. Changes to instructions:

just ./configure for mplayer configure
rm-rf $HOME/.mplayer/skins
rm -rf $HOME/.mplayer/gui*

cd home
sudo apt-get install libdbus-glib-1-dev libgconf2-dev
svn checkout [http://gnome-mplayer.googlecode.com/svn/trunk/](http://gnome-mplayer.googlecode.com/svn/trunk/) gnome-mplayer-read-only
cd gnome-mplayer-read-only/
./configure
make
sudo make install
sudo make clean

The dev version in svn works great :)

---

### Post by andrew.46 on 2008-06-25
Hi,

Sorry to hear you are having some trouble:

> **Nullack said:**
> mplayer: error while loading shared libraries: libx264.so.60: cannot open shared object file: No such file or directory

I get the same error and regression of mplayer does not change the issue. I suspect a compiler problem with Ubuntu, I have identical setup with a slackware system and not this trouble. Hmmmmmm .... anybody else have this problem?

    Andrew

---

### Post by andrew.46 on 2008-06-25
Hi again!

> **Nullack said:**
> I have some feedback about gmplayer:

1. It looks bad, jagged edges on the skin
2. I dont like the file open dialogue. It has one click instead of two click activation and the window is generally clumsy
3. The ff and rw buttons do not cue they skip
4. The cue back and forward buttons do nothing

Overall, its crap. Sorry but it is. I like how mplayer has good resource use and wide codec support. Command line mplayer is fine.

I agree with you completely about the gmplayer. It is an ugly piece of work and stacks up badly against many of the gui media players available.

>  The fix? Well really there is two prime time mplayer front ends. SMplayer is QT, which I wont use. The Gnome GTK goodness is provided by gnome-mplayer. Heres some info:

[http://kdekorte.googlepages.com/gnomemplayer](http://kdekorte.googlepages.com/gnomemplayer)

Info on nailer for thumbnails:

[http://dekorte.homeip.net/download/nailer/](http://dekorte.homeip.net/download/nailer/)

Info on getting rid of Totem:

[http://kdekorte.googlepages.com/article1](http://kdekorte.googlepages.com/article1)

Andrew can I please encourage you to consider providing the option in your excellent how to with using gnome-mplayers front end. 

Well this walkthrough is really only intended to get people started on the svn pathway with mplayer. So it only really provides the basics and even with this it provides me with more than a little work to look after :-)

Can I suggest that you publish a guide yourself that investigates guis for mplayer? I am sure you will have a large audience as it is universally acknowledged that gmplayer is not that good.

On my own system I only install gmplayer to test this guie and answer any questions about it. Otherwise no gui at all.

   Andrew

---

### Post by Nullack on 2008-06-25
Ok mate, Ill do a gnome-mplayer how to and link to yours

---

### Post by janfsd on 2008-06-25
Why not Smplayer too? Now there is a gtkstyle qt4 theme, that looks really well in a Gnome desktop. And cleanlooks theme looks good too. Imho Smplayer is the best gui available for mplayer. Gnome-mplayer is too... simple... Another thing that I don't like from it, is that when watching a movie in full screen, when you use the seek bar, then the movie position goes up.

---

### Post by andrew.46 on 2008-06-25
Hi again!

> **Nullack said:**
> Ok mate, Ill do a gnome-mplayer how to and link to yours

Sounds great. I am still battling with that x264 error message. I have posted [a query to the mplayer-users]("http://lists.mplayerhq.hu/pipermail/mplayer-users/2008-June/073520.html") and hopefully there will be resolution of this problem. Running the bleeding edge can be a bit of a pain sometines :-).

   Andrew

---

### Post by andrew.46 on 2008-06-25
Hi!

> **Nullack said:**
> Ok mate, Ill do a gnome-mplayer how to and link to yours

Bless the mplayer-users. Looks like mplayer has a little trouble with the location of the x264 shared library and simply needs --prefix=/usr for mplayer to recognise it correctly. I have changed the guide to reflect this and the correct configure option for x264 is now:
```

$ ./configure --prefix=/usr --enable-shared \
--enable-pthread --enable-mp4-output
```

I changed the amr codecs info as well although I have not had a similar problem with this.

   Andrew

---

### Post by Nullack on 2008-06-26
Great news Andrew.

Q: Why yasm? Sorry if this is a basic question, doesnt gcc handle assembler? I googled and it looks like gcc handles it?

Q: The latest release of yasm is 0.7.1 - Im going to use that

BTW your how to for yasm is missing ./configure and Intrepid has yasm 0.7.0 in packages

---

### Post by andrew.46 on 2008-06-26
Hi again!

> **Nullack said:**
> 
Q: Why yasm? Sorry if this is a basic question, doesnt gcc handle assembler? I googled and it looks like gcc handles it? 

For the simple reason that ./configure for x264 complains without it :-). I believe that is not an absolute requirement and I have seen people run speed tests with and without yasm that shows not too much difference. 

> Q: The latest release of yasm is 0.7.1 - Im going to use that

Let me know how you go with it, I will have a look at the changelog for yasm and see if there is a good reason to change the guide. I usually try to hold back from point upgrades at least for a while :-).

> BTW your how to for yasm is missing ./configure and Intrepid has yasm 0.7.0 in packages

Oops! The missing configure appeared to have migrated down to the x264 section below which for a glorious day or so has sported *two* configures :-). All fixed now thanks for the warning. Yasm is also in the Hardy repos but there are no 'dev' files and simple installation of the available files drew a blank from the x264 configure so I chose to compile rather than battle further.

Hopefully you have a working svn mplayer now + the latest x264 for encoding?

   Andrew

---

### Post by Nullack on 2008-06-26
> **janfsd said:**
> Why not Smplayer too? Now there is a gtkstyle qt4 theme, that looks really well in a Gnome desktop. And cleanlooks theme looks good too. Imho Smplayer is the best gui available for mplayer. Gnome-mplayer is too... simple... Another thing that I don't like from it, is that when watching a movie in full screen, when you use the seek bar, then the movie position goes up.

Because Smplayer still needs KDE middleware to work and I want to keep my install nice, clean and light.

---

### Post by Nullack on 2008-06-26
> **andrew.46 said:**
> Let me know how you go with it, I will have a look at the changelog for yasm and see if there is a good reason to change the guide. I usually try to hold back from point upgrades at least for a while :-).Hopefully you have a working svn mplayer now + the latest x264 for encoding?

yes sir :) Its all working great:

MPlayer dev-SVN-r27137-4.3.1 (C) 2000-2008 MPlayer Team - cool :popcorn: Yasm 7.1 compiles x264 fine. Im using the latest source for gnome-player (revision 700)

With you git alias I made it git update so its consistent with SVN. i.e.

git config --global alias.update "pull --rebase"

Im thinking about the gnome-mplayer guide Im doing. Im not too sure about our technique of not creating deb packages and installing them that way. I think it might be better to use deb packages so the dependencies can be properly handled. Also, we could then create deb packages and share them with other users so they dont have the hassle of compilation. Just an idea :)

---

### Post by andrew.46 on 2008-06-26
Hi Nullack:

> **Nullack said:**
> yes sir :) Its all working great:

MPlayer dev-SVN-r27137-4.3.1 (C) 2000-2008 MPlayer Team - cool :popcorn: Yasm 7.1 compiles x264 fine. Im using the latest source for gnome-player (revision 700)

With you git alias I made it git update so its consistent with SVN. i.e.

git config --global alias.update "pull --rebase"

Sounds great! I am glad to see you making a few changes as well, it would be a sad old world if everybody just blindly followed this guide without thinking.

> Im thinking about the gnome-mplayer guide Im doing. Im not too sure about our technique of not creating deb packages and installing them that way. I think it might be better to use deb packages so the dependencies can be properly handled. Also, we could then create deb packages and share them with other users so they dont have the hassle of compilation. Just an idea :)

I worked a little with the Debian package idea and gave up in disgust so perhaps you might have more patience. You probably have seen the [relevant area of the manual]("http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html#debian"). There is a bit of a gotcha with the naming system that [I explored a while ago]("http://ubuntuforums.org/showpost.php?p=4206950&postcount=148"). The naming scheme of the debian changelog gives a lower value than the repository naming scheme. 

This was only one of the reasons I gave up on this, but then I don't like checkinstall either :-).

   Andrew

---

### Post by Nullack on 2008-06-26
Yeah mate Im not liking checkinstall now that Im trying to use it either. I added my x264 deb then update manager is trying to install its older version.

I think what is really needed is someone in the MOTU group to take on doing x264, mplayer and gnome-player builds. Preferably every week or more regularly. Especially given the dev releases are mostly stable and wont have regressions elsewhere on a system.

That way there is no added PPA hassles for other users.

---

### Post by rvm4000 on 2008-06-26
> **Nullack said:**
> Because Smplayer still needs KDE middleware to work and I want to keep my install nice, clean and light.

SMPlayer does NOT need or require anything related to KDE. Just the Qt 4 libs.

---

### Post by Nullack on 2008-06-26
> **rvm4000 said:**
> SMPlayer does NOT need or require anything related to KDE. Just the Qt 4 libs.

I count eleven Qt lib files as dependencies in synaptic for SMplayer.

What is the effect of these being installed? Im just trying to properly understand :)

---

### Post by rvm4000 on 2008-06-27
On Qt3 everything was in only one big library. Now in Qt4 they split it in several libs (libqt4-core, libqt4-gui...) so they are more packages, but I think that's better because apps will depend only on what they use.

I don't know about the smplayer package in synaptic, but [smplayer_0.6.1-SVN-r1505_amd64.deb](ftp://ftp.berlios.de/pub/smplayer/ubuntu/smplayer_0.6.1-SVN-r1505_amd64.deb) for instance, depends only on two qt libraries:

> 
 Depends: libc6 (>= 2.2.5), libgcc1 (>= 1:4.1.1-21), **libqt4-core** (>= 4.3.4), **libqt4-gui** (>= 4.3.4), libstdc++6 (>= 4.1.1-21), mplayer | mplayer-nogui

Of course libqt4-core and libqt4-gui have other depencies but they are normal libraries (like fontconfig, freetype) which probably are used by gnome apps too.

And as you can see there's no dependency at all on any KDE package.

---

### Post by Nullack on 2008-06-27
Thanks for explaining that. SMplayer looks to be nicely features.

With these Qt libraries do I assume right that the practical impact of running Qt libraries on gnome is the amount of memory they consume? Not a big deal if so. Is there any other impact?

EDIT: I decided to install SMPlayer, and its awesome! It has very good integration to mplayer, especially filters, and does everything I need. This is the sort of front end to mplayer that shows its power in a GUI.

---

### Post by andrew.46 on 2008-06-29
Hi rvm4000:

> **rvm4000 said:**
> On Qt3 everything was in only one big library. Now in Qt4 they split it in several libs (libqt4-core, libqt4-gui...) so they are more packages, but I think that's better because apps will depend only on what they use.

You may be interested to know that smplayer now has a [slackware 12.1 installation script]("http://slackbuilds.org/repository/12.1/multimedia/smplayer/") available at slackbuilds.org. In typical slackware fashion this requires compilation of the entire 100meg qt4 source package and my 'main' computer is blowing a little smoke working on this one :-). I look forward to trying out smplayer properly I am ashamed to admit for the first time.

   Andrew

---

### Post by andrew.46 on 2008-06-29
Hi Nullack:

> **Nullack said:**
> I decided to install SMPlayer, and its awesome! It has very good integration to mplayer, especially filters, and does everything I need. This is the sort of front end to mplayer that shows its power in a GUI.

Have you read the [mplayer web site]("http://www.mplayerhq.hu/design7/dload.html") where gmplayer is given the thumbs down by the developers:

> Here you can find everything needed to get MPlayer up and running. The recommended way to install MPlayer is to compile from source. Look at the unofficial packages  section of our projects page if you do not wish to compile from source and/or are looking for packages that may be more tightly integrated with your platform. You might also want to check out the other frontends  since there is no further development and limited bug fixing for the included graphical user interface.

Pretty clear message?

    Andrew

---

### Post by pokipoki08 on 2008-07-01
SVN fixes x264 1080p playback issues but DVD or VOB files are not working well now.

Video and audio playback jumps regularly. I've tried mplayer, gmplayer and smplayer. The VOB used to play without problems.

Please help. Thanks.

```
$ mplayer vts_01_1.vob 
MPlayer dev-SVN-r27181-4.2.3 (C) 2000-2008 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

Playing vts_01_1.vob.
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 3)  29.970 fps  9800.0 kbps (1225.0 kbyte/s)
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
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 448.0 kbit/29.17% (ratio: 56000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 854x480 Planar YV12 
No bind found for key 'MOUSE_BTN0'.                         8% 0 0 
[COLOR="Red"]a52: CRC check failed!  0.039 ct:  0.059 248/248  5%  0%  1.0% 0 0 
a52: CRC check failed!  0.109 ct:  0.001 249/249 ??% ??% ??,?% 0 0 
a52: CRC check failed!  
a52: CRC check failed!  0.002 ct:  0.077 996/996  6%  0%  1.0% 4 0 
a52: error at resampling
a52: CRC check failed!  0.013 ct:  0.311 1272/1272  6%  0%  1.0% 4 0 
a52: error at resampling
[mpeg2video @ 0x88c5090]ac-tex damaged at 32 17284  6%  0%  1.2% 4 0 
[mpeg2video @ 0x88c5090]ac-tex damaged at 0 22
[mpeg2video @ 0x88c5090]ac-tex damaged at 0 23
[mpeg2video @ 0x88c5090]ac-tex damaged at 0 24
[mpeg2video @ 0x88c5090]ac-tex damaged at 0 25
[mpeg2video @ 0x88c5090]ac-tex damaged at 0 26
[mpeg2video @ 0x88c5090]ac-tex damaged at 0 27
[mpeg2video @ 0x88c5090]ac-tex damaged at 0 28
[mpeg2video @ 0x88c5090]ac-tex damaged at 0 29
[mpeg2video @ 0x88c5090]Warning MVs not available
[mpeg2video @ 0x88c5090]concealing 585 DC, 585 AC, 585 MV errors[/COLOR]

```

---

### Post by pokipoki08 on 2008-07-02
Problem is fixed now. It was due to DVD disc errors.
Thanks.

---

### Post by andrew.46 on 2008-07-02
Hi:

> **pokipoki08 said:**
> Problem is fixed now. It was due to DVD disc errors.
Thanks.

Well, glad I could be of assistance :-).

    Andrew

---

### Post by Nullack on 2008-07-03
Well Ive settled on smplayer as the front end. Just to check, Andrew are you ok with me doing a guide for smplayer / mplayer considering you said you want to stick with your command line how to?

---

### Post by andrew.46 on 2008-07-03
Hi Nullack,

> **Nullack said:**
> Well Ive settled on smplayer as the front end. Just to check, Andrew are you ok with me doing a guide for smplayer / mplayer considering you said you want to stick with your command line how to?

I would be flattered if this guide provided a starting point for your work :-). Feel free to utilise whatever portion of this guide that you need in your own work.

  Andrew

---

### Post by Nullack on 2008-07-09
Hi Andrew. Im working through some issues before posting my guide. One of these is that there is an issue with your howto that I have come across. On AMD64, your steps about copying the win32 codecs do not work. Ive since rm -rf that dir. No 32bit codecs are of any use on a 64bit system. Im now trying to figure out how to compile mplayer support for the 0x162 audio format.

EDIT: Also, I think mplayer defaults to this path for win32 codecs:

win32codecsdir=/usr/lib/win32

---

### Post by andrew.46 on 2008-07-09
Hi Nullack:

> **Nullack said:**
> Hi Andrew. Im working through some issues before posting my guide. One of these is that there is an issue with your howto that I have come across. On AMD64, your steps about copying the win32 codecs do not work. Ive since rm -rf that dir. No 32bit codecs are of any use on a 64bit system. Im now trying to figure out how to compile mplayer support for the 0x162 audio format.

EDIT: Also, I think mplayer defaults to this path for win32 codecs:

win32codecsdir=/usr/lib/win32


Unfortunately I have no experience with amd64 although I note a small pack of codecs on the mplayer site marked [amd 64]("http://www.mplayerhq.hu/MPlayer/releases/codecs/essential-amd64-20071007.tar.bz2"). The codecs directory can be set at compile time:

```
--codecsdir=DIR        directory for binary codecs [LIBDIR/codecs]

```

  Andrew

---

### Post by Nullack on 2008-07-10
Thanks again Andrew

Can I please recommend that you add a notice in your how to that the codecs section works for 32 bit Ubuntu. On AMD64, if you use the smaller 64bit mplayer codec archive it works, but it only adds a fraction of the 32 bit codecs.

Of note, its missing windows media audo pro decoding which is a key audio format in modern wmv content. I havent been able to find a wma pro decoder for linux.

Also I have been fiddling around with no success on libdvdnav. I dont like how mplayer is missing the functionality for dvd menus. I had a moment of blashphemy by installing vlc but as soon as I saw how much of a performance hog it is, I went back to mplayer and purged vlc.

With mplayer you get march and mtune equal to native which leads to total optimisation with the GCC compiler (I see the build runs on -O4 in gcc). FFmpeg is fast as it is, and with all these optimised binaries out of gcc mplayer is the fastest player out there.

---

### Post by andrew.46 on 2008-07-11
Hi Nullack:

> **Nullack said:**
> 
Also I have been fiddling around with no success on libdvdnav. I dont like how mplayer is missing the functionality for dvd menus. I had a moment of blashphemy by installing vlc but as soon as I saw how much of a performance hog it is, I went back to mplayer and purged vlc.


I will admit that I quite like vlc and have used it often, particularly in its windows incarnation. For libdvdnav have you had a look at the documents in the svn mplayer source code:

```
/DOCS/tech/dvdnav-howto.txt
```

This looks fairly comprehensive and should get you started. There is a mailing list for libdvdnav that is well worth joining just to see what is happening, I think involvement is mostly for libdvdnav developers, but I lurk there and nobody complains :-)

   Andrew

---

### Post by Nullack on 2008-07-11
Thanks

The mplayer how to for dvdnav is mostly useless unfortunately.

sudo apt-get install libdvdnav-dev
didnt work! so much for the easy option

Some strangeness going on about libdvdnav:

[http://lists.mplayerhq.hu/pipermail/dvdnav-discuss/2008-June/000588.html](http://lists.mplayerhq.hu/pipermail/dvdnav-discuss/2008-June/000588.html)

"> It's very possible that there's build issues. Nico just split
> libdvdread into its own repo and copied the build setup from
> libdvdnav."

So now I have to go the SVN route for libdvdread and libdvdnav...........

sudo apt-get install autoconf automake gettext libtool

svn co svn://svn.mplayerhq.hu/dvdnav/trunk/libdvdread libdvdread
cd libdvdread
./configure2
make
sudo make install
sudo make clean


svn co svn://svn.mplayerhq.hu/dvdnav/trunk/libdvdnav libdvdnav
cd libdvdnav
./autogen.sh && ./configure
make
sudo make install
sudo make clean

cd to mplayer
svn update mplayer
./configure --disable-dvdread-internal
note that dvdread and libdvdnav is configured to yes
make
sudo make install
sudo make clean

mplayer svn at 27266, ffmpeg svn at 14173, libdvdread svn at 1109, libdvdnav svn at 1109.

And after doing all this mplayer wont run:

mplayer: error while loading shared libraries: libdvdread.so.4: cannot open shared object file: No such file or directory

---

### Post by andrew.46 on 2008-07-11
Hi Nullack,

Well, I managed to get a working copy of libdvdnav going with mplayer but I would not really recommend it for the casual user. The successful steps for the most part mirror the advice in the source code directions.

First dispose of old copies of libdvdread and libdvdnav, ***[COLOR="Red"]being aware that this may break other applications that use these files[/COLOR]***: 
```
$ sudo rm -rf /usr/lib/libdvdnav* /usr/lib/libdvdread* /usr/include/dvdnav* \
         /usr/include/dvdread* /usr/local/lib/libdvdnav* \
         /usr/local/lib/libdvdread* /usr/local/include/dvdnav* \
         /usr/local/include/dvdread* /usr/bin/dvdnav-config \
         /usr/local/bin/dvdnav-config
```

Download libdvdread, note the use of --prefix=/usr, this bypasses an Ubuntu  default for *not* finding shared libraries in /usr/local/lib:

```
$ cd $HOME
$ svn co svn://svn.mplayerhq.hu/dvdnav/trunk/libdvdread libdvdread
$ cd libdvdread
$ ./configure2 --prefix=/usr && make
$ sudo make install
$ sudo make clean
```

And then the same idea with libdvdnav and --prefix=/usr:

```
$ cd $HOME
$ svn co svn://svn.mplayerhq.hu/dvdnav/trunk/libdvdnav libdvdnav
$ cd libdvdnav
$ ./configure2 --prefix=/usr && make
$ sudo make install
```

And the suggested configure option for the mplayer source files:

```
$ cd mplayer
$ ./configure --disable-dvdread-internal
$ make
$ sudo make install
```

And all appears well with DVD navigation:

```
$ mplayer dvdnav:// -nocache
```

Certainly showed the menu for The Matrix :-). I suggest try again with the --prefix==/usr and mplayer should find the shared libraries. I am still *not* using libdvdnav on my own setup as I am waiting patiently for it to be incorporated into the mplayer svn code. More importantly I suspect *very strongly* that removing old copies of libdvdread and libdvdnav will break other installed applications on an Ubuntu system.

     Andrew

---

### Post by Nullack on 2008-07-12
Your a blessing Andrew. So many thanks :)

Using ./configure2 --prefix=/usr for libdvdnav doesnt work on the make"

 gcc -DHAVE_CONFIG_H -I. -I../.. -I../.. -DDVDNAV_COMPILE -I/usr/local/include -I../../src -O3 -Wall -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -MT decoder.lo -MD -MP -MF .deps/decoder.Tpo -c decoder.c  -fPIC -DPIC -o .libs/decoder.o
In file included from decoder.c:27:
../../config.h:2:21: error: version.h: No such file or directory
make[3]: *** [decoder.lo] Error 1

Encrypted dvds didnt work and the medibuntu repo doesnt appear to have intrepid binaries yet so I had to compile libdvdcss. Anyway its now all working by:

```
sudo apt-get install autoconf automake gettext libtool

sudo rm -rf /usr/lib/libdvdnav* /usr/lib/libdvdread* /usr/include/dvdnav* \
         /usr/include/dvdread* /usr/local/lib/libdvdnav* \
         /usr/local/lib/libdvdread* /usr/local/include/dvdnav* \
         /usr/local/include/dvdread* /usr/bin/dvdnav-config \
         /usr/local/bin/dvdnav-config

cd ~/src
wget http://download.videolan.org/pub/libdvdcss/1.2.9/libdvdcss-1.2.9.tar.bz2
tar -xvjf libdvdcss-1.2.9.tar.bz2
cd libdvdcss-1.2.9/
./configure --prefix=/usr
make
sudo make install
sudo make clean

cd ~/src
svn co svn://svn.mplayerhq.hu/dvdnav/trunk/libdvdread libdvdread
cd libdvdread
./configure2 --prefix=/usr --with-libdvdcss
make
sudo make install
sudo make clean

cd ~/src
svn co svn://svn.mplayerhq.hu/dvdnav/trunk/libdvdnav libdvdnav
cd libdvdnav
./autogen.sh --prefix=/usr && ./configure --prefix=/usr
make
sudo make install
sudo make clean

cd ~/src/mplayer
./configure --disable-dvdread-internal (note that dvdread and libdvdnav is configured to yes)
make
sudo make install
sudo make clean
```

Im executing with mouse enabled to allow for dvd mouse navigation:

```
mplayer dvdnav:// -nocache -mouse-movements
```

Only problem is that the included docos dont seem to indicate how I can use the mouse or other method to go back to the menu while playing content.

---

### Post by andrew.46 on 2008-07-12
Hi,

Glad it is working for you although I can see a few differences in your setup from my own trial of libdvdnav :-). For the mouse you could add the following to ~/.mplayer/config:

```
mouse-movements=yes
```

For my own part it all looks a little too hard :-). All the best with wrestling with the menus!

   Andrew

---

### Post by Nullack on 2008-07-12
Andrew Im pleased to report YASM 0.7.1 is in the Intrepid repos and it compiles x264 out of the box very nicely.

---

### Post by andrew.46 on 2008-07-12
Hi Nullack:

> **Nullack said:**
> Andrew Im pleased to report YASM 0.7.1 is in the Intrepid repos and it compiles x264 out of the box very nicely.

Just by wild coincidence I have just finished downloading Intrepid Ibex alpha 2 and I will be wiping my Hardy Heron installation today :-).

   Andrew

---

### Post by Nullack on 2008-07-13
To share some new developments:

Keypad 5 is return to menu, keypad 8 is up, keypad 2 is down. This is working perfectly for me. libdvdnav and libdvdread appear to be under pretty good regular development.

The dvdnav devs have made some cvs changes that allows for configure2 to be used now without needing to use autoconf etcetc. So my amended instructions are:

```
sudo apt-get install gettext libtool

sudo rm -rf /usr/lib/libdvdnav* /usr/lib/libdvdread* /usr/include/dvdnav* \
         /usr/include/dvdread* /usr/local/lib/libdvdnav* \
         /usr/local/lib/libdvdread* /usr/local/include/dvdnav* \
         /usr/local/include/dvdread* /usr/bin/dvdnav-config \
         /usr/local/bin/dvdnav-config

cd ~/src
sudo apt-get remove libx264-dev 
git clone git://git.videolan.org/x264.git
cd x264
./configure --prefix=/usr --enable-shared --enable-pthread --enable-mp4-output
make
sudo make install
sudo make clean

cd ~/src
wget http://download.videolan.org/pub/libdvdcss/1.2.9/libdvdcss-1.2.9.tar.bz2
tar -xvjf libdvdcss-1.2.9.tar.bz2
cd libdvdcss-1.2.9/
./configure --prefix=/usr
make
sudo make install
sudo make clean

cd ~/src
svn co svn://svn.mplayerhq.hu/dvdnav/trunk/libdvdread libdvdread
cd libdvdread
./configure2 --prefix=/usr --with-libdvdcss
make
sudo make install
sudo make clean

cd ~/src
svn co svn://svn.mplayerhq.hu/dvdnav/trunk/libdvdnav libdvdnav
cd libdvdnav
./configure2 --prefix=/usr
make
sudo make install
sudo make clean

cd ~/src/mplayer
./configure --disable-dvdread-internal (note that dvdread and libdvdnav is configured to yes)
make
sudo make install
sudo make clean
```

Im executing with mouse enabled to allow for dvd mouse navigation:

```
mplayer dvdnav:// -nocache -mouse-movements
```

---

### Post by ForksHolder on 2008-07-13
Awesome HOWTO! Thank you very much!

---

### Post by andrew.46 on 2008-07-13
Hi Nullack,

 I am glad to see you working away at it! I am sure by now you appreciate the work that goes into a walkthrough of this complexity :-).

 Myself, I am fading away a little from Ubuntu and probably these forums. I have been predominantly a slackware user or some time now and having finally solved some bugs with wireless on the laptop I was running Hardy and Intrepid on it is now running slackware 12.1 beautifully.

 I will continue to keep an eye on my various walkthroughs. 

   Andrew

---

### Post by andrew.46 on 2008-07-14
Hi Nullack:

> **Nullack said:**
> To share some new developments

Even newer developments on the horizon as finally there is some definitive talk of incorporating libdvdnav and libdvdread into the svn mplayer tree:

[http://lists.mplayerhq.hu/pipermail/mplayer-dev-eng/2008-July/058079.html](http://lists.mplayerhq.hu/pipermail/mplayer-dev-eng/2008-July/058079.html)

Perhaps you should hold off a definitive guide until this is settled? This is the development that I have been waiting for myself where all the different components are available in one go :-).

   Andrew

---

### Post by Nullack on 2008-07-15
Yeah I will hang loose for a bit since it would be such a big change to the way the setup is done. Im monitoring the various ffmpeg/dvdnav/mplayer lists too. The mplayer lists could do with an Ubuntu type code of conduct on it :) Bit of a rough environment that doesnt help participation in my view.

Ive gone back to using gnome-mplayer as my preferred front end. My reasons are:

1. Excellent dvd menu support unlike smplayer
2. Better privacy than smplayer out of the box
3. Lighter, no qt libs, no sqllite etcetc

Im testing -O3 march=native mtune=native gcc compiles on the front end all seems good so far.

---

### Post by andrew.46 on 2008-07-23
With deep regret I write here that I will no longer be updating this guide, a guide that I have heartily enjoyed researching, writing and supporting. It is true of all such guides that it is the creator and maintainer of the guide who *learns* more than anybody else, and this has been my experience. I wish everybody all the best with the amazing svn mplayer through Intrepid Ibex and beyond!

Andrew Strong
July 23rd, 2008

---

### Post by mocha on 2008-07-29
I'd appreciate if someone could give me a hand with x264 and compiling mplayer and ffmpeg.  I downloaded x264 from the git repository and it complied fine.  Then I downloaded svn mplayer and compiled it with some options including --enable-x264.  Running make errors out with something about libx264.

The same thing happens with ffmpeg svn, only on newer versions like 14xxx and up.  Older version such as 13060 which I'm running now were able to be complied with the libx264 from the Ubuntu repository or the git version.  However, if I compile the git x264 and then complie ffmpeg, when I try to encode a video with vcodec libx264 I get an error about not specifying ratecontrol.  On the other hand, if I compile ffmpeg svn with only the Ubuntu libx264 installed, when I encode using the exact same ffmpeg command line parameters it works ok.

In summary:  Was there some change to newer versions of ffmpeg in regards to libx264?  Also, why does svn mplayer not want to compile with the Ubuntu libx264?  Thanks for any comments.

---

### Post by andrew.46 on 2008-07-29
Hi,

> **mocha said:**
> I'd appreciate if someone could give me a hand with x264 and compiling mplayer and ffmpeg.  I downloaded x264 from the git repository and it complied fine.  Then I downloaded svn mplayer and compiled it with some options including --enable-x264.  Running make errors out with something about libx264.

There have been some changes. For mplayer you will need to remove the ubuntu dev file for x264, install the git x264 and then commpile.

The mplayer build system is a little different from most, you actually should *not* specify --enable-x264. Just let configure find all the x264 files itself.

   Andrew

---

### Post by mocha on 2008-07-30
Andrew,

Thanks for the response.  For the moment to keep my system going I had to revert to older svns of mplayer and ffmpeg and use the Ubuntu libx264.  When I have time later I'll do fresh pulls of everything and try again.  I think I just happened to update on a day when there was a regression in x264.

Also, I don't think the libx264 from Ubuntu needs to be uninstalled.  The compiled x264 goes into /usr/local/lib,  Ubuntu's libx264 is in /usr/lib.  mplayer and ffmpeg will pick up the files from /usr/local/lib first if they exist.

---

### Post by andrew.46 on 2008-07-30
Hi,

Glad to hear that at least your system is up an running :-)

> **mocha said:**
> 
Also, I don't think the libx264 from Ubuntu needs to be uninstalled.  The compiled x264 goes into /usr/local/lib,  Ubuntu's libx264 is in /usr/lib.  mplayer and ffmpeg will pick up the files from /usr/local/lib first if they exist.

Well there is a story there. On many people's Ubuntu systems there seems to be a problem with libraries in /usr/local/lib and so for the most part in the guide that I wrote I eventually specified --prefix=/usr as the easiest way around this. Along with this is the problem that the svn mplayer will not build against anything less than build 59 of x264. You will in fact see the following in the ./configure script:

```
echocheck "x264"
if test "$_x264" = auto ; then
  cat > $TMPC << EOF
#include <inttypes.h>
#include <x264.h>
#if X264_BUILD < 59
#error We do not support old versions of x264. Get the latest from SVN.
#endif
```

This was the reasoning behind advising people to lose the Ubuntu x264 when installing the git x264 and the svn mplayer.

Unfortunately I am not in a position to recheck much of this, including the version of x264 offered by Ubuntu as I no longer run Ubuntu and I am in fact slowly retiring from these forums.

    Andrew

---

### Post by mocha on 2008-07-30
Andrew,  I appreciate you responding.  Thanks for this guide and best wishes with your new distro.

---

### Post by Nullack on 2008-08-04
Yes all the best Andrew :) I noticed ffmpeg has been getting alot of love with AVC and Matroska, plus the ogg / theora seeking bug was fixed :) Mplayer just keeps getting better and better.

---

### Post by mangurt on 2008-08-06
Greetings,
I recently did a fresh install for ubuntu, and now I am trying to follow this guide to get mplayer working.  Things went pretty well until I got to the portion to make.

Here's there error I got:

Error: The GUI requires libavcodec with PNG support (needs zlib).

Check "configure.log" if you do not understand why it failed.
ed@ed-desktop:~/mplayer$ make
Makefile:22: config.mak: No such file or directory
make: *** osdep/: Is a directory.  Stop.
ed@ed-desktop:~/mplayer$ 

Any ideas?
Thanks

---

### Post by andrew.46 on 2008-08-06
Hi:

> **mangurt said:**
> 
Error: The GUI requires libavcodec with PNG support (needs zlib).


In general the first compilation error tells the greatest truth and following that the errors have less meaning :-). In this case I suspect that you need the so-called '-dev' library of zlib. Ubuntu / Debian splits the original source so that by default the header files are *not* installed, which is actually something of a pain.

I do not have access to an Ubuntu system at the moment but to find the appropriate dev file try:

```
$ apt-cache search zlib | grep dev
```

and then install the suggested file and re-compile. This will hopefully get you out of trouble :-).

  Andrew

---

### Post by mangurt on 2008-08-06
> **andrew.46 said:**
> Hi:



In general the first compilation error tells the greatest truth and following that the errors have less meaning :-). In this case I suspect that you need the so-called '-dev' library of zlib. Ubuntu / Debian splits the original source so that by default the header files are *not* installed, which is actually something of a pain.

I do not have access to an Ubuntu system at the moment but to find the appropriate dev file try:

```
$ apt-cache search zlib | grep dev
```

and then install the suggested file and re-compile. This will hopefully get you out of trouble :-).

  Andrew

Ok, I did the first part, and downloaded just about everything except the 64bit build.  Went to recompile and got this error.

Error: X11 support required for GUI compilation.

Check "configure.log" if you do not understand why it failed.
ed@ed-desktop:~/mplayer$ make
Makefile:22: config.mak: No such file or directory
make: *** osdep/: Is a directory.  Stop.
ed@ed-desktop:~/mplayer$ 

Grrr.....part of me wants to start over....but I am so darn close...

---

### Post by andrew.46 on 2008-08-07
Hi again!

> **mangurt said:**
> Error: X11 support required for GUI compilation.

Did you manage to install the huge list of dev files in the walkthrough? The x11 dev files were definitely in there and this would allow compiling of the gui. Try copying the entire list and dropping it into a terminal window again, this should should give x11 support and all the other features.

   Andrew

---

### Post by mangurt on 2008-08-07
Andrew,
Copied the whole list again, and now got this error.

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libspeex-dev: Depends: libspeex1 (= 1.1.12-3ubuntu0.8.04.1) but 1.2~beta2-2~feisty.3670 is to be installed
E: Broken packages

Thanks

---

### Post by andrew.46 on 2008-08-07
Hi MG,

The root of the problem is that to install MPlayer with full functionality you need all of the dev packages. Broken packages, repository problems etc point to more of a system problem which you must rectify first.

   Andrew

---

### Post by Enshin on 2008-08-10
Just say thanks.

I had trouble with DVD playing with mplayer.
Just installing the codecs proved enough.

Working like a sharm.

Bye.

---

### Post by maxim99 on 2008-08-20
I have a quick question. From what I can see there is no relation to the codecs that are downloaded and placed in a directory, and the compiling of mplayer. Am I to understand this correctly the the configure process finds all of the codecs that were downloaded and placed in a particular directory, and then enables their use since it found them?

Also would I be able to prepare the mplayer that I compile myself into a debian package and place it on a computer that has not had these things (those gotten through apt-get) downloaded, and through dependancies download them automatically? I believe that the codecs would have to be downloaded and installed seperatly. I simply don't know enough about compiling of applications to even make assumtions.

By the way fatastic document you've written up there, truly a work to be proud of! It has helped me out greatly, and I really do appreciate it.

---

### Post by andrew.46 on 2008-08-21
Hi maxim,

Thanks for your message:

> **maxim99 said:**
> I have a quick question. From what I can see there is no relation to the codecs that are downloaded and placed in a directory, and the compiling of mplayer. Am I to understand this correctly the the configure process finds all of the codecs that were downloaded and placed in a particular directory, and then enables their use since it found them?

Exactly! The directions I gave are for the default location of the codecs and the mplayer configure script will find then there. This can be varied with the configure option:

```
$ ./configure --codecsdir=/the/path/I/want/
```

> Also would I be able to prepare the mplayer that I compile myself into a debian package and place it on a computer that has not had these things (those gotten through apt-get) downloaded, and through dependancies download them automatically? I believe that the codecs would have to be downloaded and installed seperatly. I simply don't know enough about compiling of applications to even make assumtions.

Creating a debian package is not covered in the guide but there is specific information available to do it:

[http://www.mplayerhq.hu/DOCS/HTML/en/linux.html#debian](http://www.mplayerhq.hu/DOCS/HTML/en/linux.html#debian)

Unfortunately I have had very little experience with this technique and in fact no longer run either Debian or Ubuntu :(.

> By the way fatastic document you've written up there, truly a work to be proud of! It has helped me out greatly, and I really do appreciate it.

I am glad the guide has been useful to you! I no longer maintain it I am afraid although I still try to answer email concerning it. 

All the best,

  Andrew

---

### Post by gillza on 2008-08-23
Hi Andrew,

I am a linux newbie and was following this thread as it was very helpful to me. You pointed out that you are no longer using Ubuntu. I am curious for which distro have you settled?

Thanks

P.S. Sorry for asking about it here, but it would not let me send you a private message.

---

### Post by andrew.46 on 2008-08-23
Hi gillza:

> **gillza said:**
> I am a linux newbie and was following this thread as it was very helpful to me. You pointed out that you are no longer using Ubuntu. I am curious for which distro have you settled?

The thing that held me mostly to Ubuntu was the community which for the most part seems *not* to be found in most distros. I have been using Slackware for a fair while now and I am very happy with it, I was dual-booting for a while but it started getting a little silly :-). I will miss writing the mplayer guide though but I am sure someone will step in there, the principles usually don't change but the details always will.

 All the best,

  Andrew

---

### Post by stanjr on 2008-10-01
I've been able to completely compile both x264 and mplayer via the instructions here within Hardy Heron 64-bit quite happily if I don't use --enable-avis-input during the configure step when compiling x264.  avis support doesn't get picked up automagically if I don't use that.  I get this during configure:> stanjr@stanjr-desktop:~/Programs/build/x264$ ./configure --enable-shared --enable-avis-input
Platform:   X86_64
System:     LINUX
asm:        yes
avis input: yes
mp4 output: yes
pthread:    yes
gtk:        no
debug:      no
gprof:      no
PIC:        yes
shared:     yes
visualize:  noBut, then when I try to make, I get this:> ...[a bunch of make stuff left out]...
yasm -f elf -m amd64 -DPIC -DARCH_X86_64 -Icommon/x86/ -o common/x86/cabac-a.o common/x86/cabac-a.asm yasm -f elf -m amd64 -DPIC -DARCH_X86_64 -Icommon/x86/ -o common/x86/dct-a.o common/x86/dct-a.asm yasm -f elf -m amd64 -DPIC -DARCH_X86_64 -Icommon/x86/ -o common/x86/deblock-a.o common/x86/deblock-a.asm yasm -f elf -m amd64 -DPIC -DARCH_X86_64 -Icommon/x86/ -o common/x86/mc-a.o common/x86/mc-a.asm yasm -f elf -m amd64 -DPIC -DARCH_X86_64 -Icommon/x86/ -o common/x86/mc-a2.o common/x86/mc-a2.asm yasm -f elf -m amd64 -DPIC -DARCH_X86_64 -Icommon/x86/ -o common/x86/pixel-a.o common/x86/pixel-a.asm yasm -f elf -m amd64 -DPIC -DARCH_X86_64 -Icommon/x86/ -o common/x86/predict-a.o common/x86/predict-a.asm yasm -f elf -m amd64 -DPIC -DARCH_X86_64 -Icommon/x86/ -o common/x86/quant-a.o common/x86/quant-a.asm yasm -f elf -m amd64 -DPIC -DARCH_X86_64 -Icommon/x86/ -o common/x86/sad-a.o common/x86/sad-a.asm yasm -f elf -m amd64 -DPIC -DARCH_X86_64 -Icommon/x86/ -o common/x86/cpu-64.o common/x86/cpu-64.asm yasm -f elf -m amd64 -DPIC -DARCH_X86_64 -Icommon/x86/ -o common/x86/dct-64.o common/x86/dct-64.asm gcc -shared -o libx264.so.64 common/mc.o common/predict.o common/pixel.o common/macroblock.o common/frame.o common/dct.o common/cpu.o common/cabac.o common/common.o common/mdate.o common/set.o common/quant.o common/vlc.o encoder/analyse.o encoder/me.o encoder/ratecontrol.o encoder/set.o encoder/macroblock.o encoder/cabac.o encoder/cavlc.o encoder/encoder.o common/x86/mc-c.o common/x86/predict-c.o common/x86/cabac-a.o common/x86/dct-a.o common/x86/deblock-a.o common/x86/mc-a.o common/x86/mc-a2.o common/x86/pixel-a.o common/x86/predict-a.o common/x86/quant-a.o common/x86/sad-a.o common/x86/cpu-64.o common/x86/dct-64.o
-Wl,-soname,libx264.so.64 -lm -lpthread -lgpac_static -lvfw32 -s
[b]/usr/bin/ld: cannot find -lvfw32
collect2: ld returned 1 exit status
make: *** [libx264.so.64] Error 1[/b]This only happens after I've used --enable-avis-input during configure.  I thought maybe I needed some kind of w32 codecs, so I installed the win32 codecs for amd64 via Synaptic, but still the same error.  What am I doing wrong to compile x264 with avis support?  x264 compiles fine if I don't enable it.

---

### Post by andrew.46 on 2008-10-01
Hi stanjr:

> **stanjr said:**
>  What am I doing wrong to compile x264 with avis support?  x264 compiles fine if I don't enable it.

As far as I know, and I cannot claim to be an expert avisynth is not yet available to Linux.

   Andrew

---

### Post by stanjr on 2008-10-04
It's not.  I thought that I had to compile x264 with avis input support to be able to use avisynth via wine, but I don't.

---

### Post by stanjr on 2008-10-04
I'm now having a different problem.  I've configured the lastest x264 (r999) with --prefix=/usr --enable-shared and it compiled and installed fine.  Then, I configured the latest mplayer (r27711) with --prefix=/usr --enable-gui --enable-menu, but it didn't compile fine.  I get this near the end of make:> libmpdemux/demuxer.o: In function `demux_pattern_3':
demuxer.c: (.text+0x35e2): undefined reference to `unlikely'
libmpdemux/demux_mpg.o: In function `demux_mpg_gxf_fill_buffer':
demux_mpg.c: (.text+0x1056): undefined reference to `unlikely'
libmpdemux/parse_es.o: In function `read_video_packet':
parse_es.c: (.text+0xee): undefined reference to `likely'
parse_es.c: (.text+0x13c): undefined reference to `unlikely'
libmpdemux/parse_es.o: In function `sync_video_packet':
parse_es.c: (.text+0x1d8 ): undefined reference to `likely'
parse_es.c: (.text+0x230): undefined reference to `unlikely'
libmpdemux/video.o: In function `video_read_frame':
video.c: (.text+0x16f): undefined reference to `likely'
video.c: (.text+0xb40): undefined reference to `unlikely'
libmpcodecs/ad_hwac3.o: In function `ac3dts_fillbuff':
ad_hwac3.c: (.text+0x369): undefined reference to `likely'
ad_hwac3.c: (.text+0x544): undefined reference to `unlikely'
libmpcodecs/ad_liba52.o: In function `a52_fillbuff':
ad_liba52.c: (.text+0x1ae): undefined reference to `likely'
ad_liba52.c: (.text+0x2bf): undefined reference to `unlikely'
libmpcodecs/ad_libdca.o: In function `dts_sync':
ad_libdca.c: (.text+0xb5): undefined reference to `likely'
ad_libdca.c: (.text+0x13e): undefined reference to `unlikely'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1What's going on?

EDIT: Whatever it was, they got it fixed in r27718!

---

### Post by andrew.46 on 2008-10-12
Hi,

Clean out time for this guide. The Feisty Fawn dev files are off the main page but I include them here for reference:

```
$ sudo apt-get install avifile-divx-plugin avifile-xvid-plugin gawk \
ladspa-sdk liba52-0.7.4-dev libaa1-dev libartsc0-dev libasound2-dev \
libatk1.0-dev libaudiofile-dev libavcodec-dev libavformat-dev libavifile-0.7-dev \
libc6-dev libcaca-dev libcairo2-dev libcdparanoia0-dev libdbus-glib-1-dev \
libdfb++-0.9-25 libdfb++-dev libdirectfb-0.9-25 libdirectfb-dev libdts-dev \
libdv-dev libdv4-dev libdvdnav-dev libdvdnav4 libdvdplay0 libdvdread-dev \
libdvdread3-dev libenca-dev libesd0-dev libexpat1-dev libfaac-dev libfaad2-dev \
libfame-0.9 libfame-dev libflac++-dev libflac-dev libfontconfig-dev \
libfontconfig1-dev libfreetype6-dev libfribidi-dev libgdk-pixbuf-dev \
libggi2-dev libggimisc2 libggimisc2-dev libggiwmh0 libggiwmh0-dev \
libglu1-mesa-dev libgtk2.0-dev libice-dev libjpeg62-dev liblame-dev \
liblivemedia-dev liblzo-dev libmad0-dev libmatroska-dev libmikmod2-dev \
libmp4v2-dev libmp4v2-dev libmpcdec-dev libogg-dev liboggflac++-dev \
liboggflac-dev libpango1.0-dev libpng12-dev libpng12-dev libpopt-dev \
libpostproc-dev libsdl1.2-dev libsmbclient-dev libspeex-dev libsvga1 \
libsvga1-dev libtheora-dev libungif4-dev libungif4g libvorbis-dev libx264-dev \
libxcursor-dev libxfixes-dev libxinerama-dev libxv-dev libxvidcore4 libxvidcore4-dev \
libxvmc-dev libxxf86dga-dev libxxf86vm-dev sharutils toolame ttf-bitstream-vera \
x11proto-fixes-dev x11proto-xinerama-dev xlibs-dev zlib1g-dev zlib1g-dev
```

 Andrew

---

### Post by Frijolie on 2008-10-12
Thanks for updating to include Intrepid. I was getting this famous line at compile:

> 
Error: X11 support required for GUI compilation.


so with the update let's see if it's fixed. I'm holding my breath and crossing my fingers.

almost there...almost there...Stay on target! Stay on target! I got past the compilation! Hurray! Thanks!

---

### Post by andrew.46 on 2008-10-12
Hi:

> **Frijolie said:**
>  I got past the compilation! Hurray! Thanks!

Glad to hear that it all worked out :-)

  Andrew

---

### Post by Frijolie on 2008-10-13
Hmmm....now all I got is an icon in my menu. When it's clicked nothing happens. I can run everything CLI but the GUI part isn't working. I've downloaded the Blue skin and set up the link but it's not working. Any suggestions?

After goofing around with it a little more...I've got it to come up with a GUI error message: 
```

[skin] file ( /usr/local/share/mplayer/skins/default/skin ) not readable.

```

I've got three different directories where mplayer stuff is installed. I think I've got stuff mixed up in different directories.

```

$HOME/mplayer (where i downloaded via svn)
$HOME/.mplayer (where I loaded the skins and fonts
/usr/local/share/mplayer/skins... (the directory that it's looking for)

```

could this be the cause?

---

### Post by andrew.46 on 2008-10-14
Hi Frijolie,

Sounds like mplayer cannot find the skin. There are in fact several different ways to set this but the easiest way is perhaps the one suggested in the guide:

```
$ cd $HOME
$ mkdir -pv $HOME/.mplayer/skins/default
$ wget http://www.mplayerhq.hu/MPlayer/skins/Blue-1.7.tar.bz2
$ tar xjvf Blue-1.7.tar.bz2 
$ cp -Rv $HOME/Blue/* $HOME/.mplayer/skins/default
```

Mplayer will easily find the skin there and all should be well. The html docs tell the full story and also demonstrate how to use different directories:

> As MPlayer doesn't have a skin included, you have to download one if you want to use the GUI. See the download page. It should be extracted to the usual system-wide directory ($PREFIX/share/mplayer/skins), or to $HOME/.mplayer/skins. MPlayer by default looks in these directories for a directory named default, but you can use the -skin newskin option, or the skin=newskin config file directive to use the skin in the */skins/newskin directory. 

Hope this helps?

  Andrew

---

### Post by mocha on 2008-10-16
Andrew, nice to see you are back to maintaining this guide!  There is a similar thread in the forums about compiling the latest x264 and ffmpeg. 

[http://ubuntuforums.com/showthread.php?786095](http://ubuntuforums.com/showthread.php?786095)

In that thread they mentioned that compiling x264 with --enable-shared, pthread, and mp4-output are no longer necessary or only useful if using the standalone x264 encoder.  I thought you might want to have a look at that.  Thanks again.

---

### Post by andrew.46 on 2008-10-16
Hi mocha:

> **mocha said:**
> Andrew, nice to see you are back to maintaining this guide!  There is a similar thread in the forums about compiling the latest x264 and ffmpeg. 

[http://ubuntuforums.com/showthread.php?786095](http://ubuntuforums.com/showthread.php?786095) 


Great thread, looks like FakeOutdoorsman knows his stuff with both x264 and ffmpeg. Something borked the address:

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)


> In that thread they mentioned that compiling x264 with --enable-shared, pthread, and mp4-output are no longer necessary or only useful if using the standalone x264 encoder.  I thought you might want to have a look at that.  Thanks again.

To tell the truth this guide is so comprehensive I think it would make more sense for me to consider dropping the x264 section of my guide and include a link to this guide. I will have a closer look on the weekend. Thanks for the heads-up!

  Andrew

---

### Post by andrew.46 on 2008-10-16
Well, after some consideration I have removed the details that relate to compiling the x264 libraries and I will direct queries about this library to the FakeOutdoorsman's guide:

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

To keep up to date with the MPlayer guide on the Ubuntu Forums I spend a great deal of time using MPlayer and Mencoder, researching guides online as well as reading the mailing lists MPlayer-Users and MPlayer-dev-eng. This takes some time and when I see someone devoting similar energy and time to ffmpeg and x264 I see no point in duplicating this excellent work and in fact I do not even have the available time for this :-).

So my strong suggestion would be if you are considering *encoding* video with x264 and mencoder to use the git x264 as outlined in the FakeOutdoorsman's guide. For simple playback the use of Ubuntu's libx264-dev should be sufficient, *as long as this version is sufficiently modern for the MPlayer ./configure process*.

  Andrew

---

### Post by Argentino on 2008-10-17
Hello, first of all I want to thank you for this very useful guide and how simple it is to fallow.

I am having a problem installing one of the libgtk files. I tried in the console but I get the same error message as if I do it on the SPM. According to Synaptic, the file that is requesting to be installed first is already installed.

Can you please help me, I have attached the screen shot.

Thank you in advanced

[[IMG]http://img337.imageshack.us/img337/8526/screenub5.th.jpg[/IMG]](http://img337.imageshack.us/my.php?image=screenub5.jpg)[[IMG]http://img337.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

### Post by andrew.46 on 2008-10-17
Hi Argentino:

> **Argentino said:**
> 
I am having a problem installing one of the libgtk files. I tried in the console but I get the same error message as if I do it on the SPM. According to Synaptic, the file that is requesting to be installed first is already installed.

This might be a problem as the gtk files are essential for building the gui gmplayer but not needed for the command line version. I could not quite see if you have any version of libgtk2.0dev installed, so run the install and see if it fails and asks for gtk libraries.

Have a look at your system and see if something like the following exists (this is the tree fro libgtk2.0-dev in Intrepid Ibex):

```
/.
/usr
/usr/bin
/usr/bin/dh_gtkmodules
/usr/bin/gdk-pixbuf-csource
/usr/bin/gtk-builder-convert
/usr/include
/usr/include/gtk-2.0
/usr/include/gtk-2.0/gdk-pixbuf
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf.h
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-transform.h
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-io.h
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-animation.h
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-simple-anim.h
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-loader.h
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-enum-types.h
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-marshal.h
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-features.h
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixdata.h
/usr/include/gtk-2.0/gdk
/usr/include/gtk-2.0/gdk/gdkx.h
/usr/include/gtk-2.0/gdk/gdk.h
/usr/include/gtk-2.0/gdk/gdkapplaunchcontext.h
/usr/include/gtk-2.0/gdk/gdkcairo.h
/usr/include/gtk-2.0/gdk/gdkcolor.h
/usr/include/gtk-2.0/gdk/gdkcursor.h
/usr/include/gtk-2.0/gdk/gdkdisplay.h
/usr/include/gtk-2.0/gdk/gdkdisplaymanager.h
/usr/include/gtk-2.0/gdk/gdkdnd.h
/usr/include/gtk-2.0/gdk/gdkdrawable.h
/usr/include/gtk-2.0/gdk/gdkevents.h
/usr/include/gtk-2.0/gdk/gdkfont.h
/usr/include/gtk-2.0/gdk/gdkgc.h
/usr/include/gtk-2.0/gdk/gdki18n.h
/usr/include/gtk-2.0/gdk/gdkimage.h
/usr/include/gtk-2.0/gdk/gdkinput.h
/usr/include/gtk-2.0/gdk/gdkkeys.h
/usr/include/gtk-2.0/gdk/gdkkeysyms.h
/usr/include/gtk-2.0/gdk/gdkpango.h
/usr/include/gtk-2.0/gdk/gdkpixbuf.h
/usr/include/gtk-2.0/gdk/gdkpixmap.h
/usr/include/gtk-2.0/gdk/gdkprivate.h
/usr/include/gtk-2.0/gdk/gdkproperty.h
/usr/include/gtk-2.0/gdk/gdkregion.h
/usr/include/gtk-2.0/gdk/gdkrgb.h
/usr/include/gtk-2.0/gdk/gdkscreen.h
/usr/include/gtk-2.0/gdk/gdkselection.h
/usr/include/gtk-2.0/gdk/gdkspawn.h
/usr/include/gtk-2.0/gdk/gdktestutils.h
/usr/include/gtk-2.0/gdk/gdktypes.h
/usr/include/gtk-2.0/gdk/gdkvisual.h
/usr/include/gtk-2.0/gdk/gdkwindow.h
/usr/include/gtk-2.0/gdk/gdkenumtypes.h
/usr/include/gtk-2.0/gtk
/usr/include/gtk-2.0/gtk/gtk.h
/usr/include/gtk-2.0/gtk/gtkaboutdialog.h
/usr/include/gtk-2.0/gtk/gtkaccelgroup.h
/usr/include/gtk-2.0/gtk/gtkaccellabel.h
/usr/include/gtk-2.0/gtk/gtkaccelmap.h
/usr/include/gtk-2.0/gtk/gtkaccessible.h
/usr/include/gtk-2.0/gtk/gtkaction.h
/usr/include/gtk-2.0/gtk/gtkactiongroup.h
/usr/include/gtk-2.0/gtk/gtkadjustment.h
/usr/include/gtk-2.0/gtk/gtkalignment.h
/usr/include/gtk-2.0/gtk/gtkarrow.h
/usr/include/gtk-2.0/gtk/gtkaspectframe.h
/usr/include/gtk-2.0/gtk/gtkassistant.h
/usr/include/gtk-2.0/gtk/gtkbbox.h
/usr/include/gtk-2.0/gtk/gtkbin.h
/usr/include/gtk-2.0/gtk/gtkbindings.h
/usr/include/gtk-2.0/gtk/gtkbox.h
/usr/include/gtk-2.0/gtk/gtkbuilder.h
/usr/include/gtk-2.0/gtk/gtkbuildable.h
/usr/include/gtk-2.0/gtk/gtkbutton.h
/usr/include/gtk-2.0/gtk/gtkcalendar.h
/usr/include/gtk-2.0/gtk/gtkcelleditable.h
/usr/include/gtk-2.0/gtk/gtkcelllayout.h
/usr/include/gtk-2.0/gtk/gtkcellrenderer.h
/usr/include/gtk-2.0/gtk/gtkcellrendereraccel.h
/usr/include/gtk-2.0/gtk/gtkcellrenderercombo.h
/usr/include/gtk-2.0/gtk/gtkcellrendererpixbuf.h
/usr/include/gtk-2.0/gtk/gtkcellrendererprogress.h
/usr/include/gtk-2.0/gtk/gtkcellrendererspin.h
/usr/include/gtk-2.0/gtk/gtkcellrenderertext.h
/usr/include/gtk-2.0/gtk/gtkcellrenderertoggle.h
/usr/include/gtk-2.0/gtk/gtkcellview.h
/usr/include/gtk-2.0/gtk/gtkcheckbutton.h
/usr/include/gtk-2.0/gtk/gtkcheckmenuitem.h
/usr/include/gtk-2.0/gtk/gtkclipboard.h
/usr/include/gtk-2.0/gtk/gtkcolorbutton.h
/usr/include/gtk-2.0/gtk/gtkcolorsel.h
/usr/include/gtk-2.0/gtk/gtkcolorseldialog.h
/usr/include/gtk-2.0/gtk/gtkcombobox.h
/usr/include/gtk-2.0/gtk/gtkcomboboxentry.h
/usr/include/gtk-2.0/gtk/gtkcontainer.h
/usr/include/gtk-2.0/gtk/gtkcurve.h
/usr/include/gtk-2.0/gtk/gtkdebug.h
/usr/include/gtk-2.0/gtk/gtkdialog.h
/usr/include/gtk-2.0/gtk/gtkdnd.h
/usr/include/gtk-2.0/gtk/gtkdrawingarea.h
/usr/include/gtk-2.0/gtk/gtkeditable.h
/usr/include/gtk-2.0/gtk/gtkentry.h
/usr/include/gtk-2.0/gtk/gtkentrycompletion.h
/usr/include/gtk-2.0/gtk/gtkenums.h
/usr/include/gtk-2.0/gtk/gtkeventbox.h
/usr/include/gtk-2.0/gtk/gtkexpander.h
/usr/include/gtk-2.0/gtk/gtkfilechooser.h
/usr/include/gtk-2.0/gtk/gtkfilechooserbutton.h
/usr/include/gtk-2.0/gtk/gtkfilechooserdialog.h
/usr/include/gtk-2.0/gtk/gtkfilechooserwidget.h
/usr/include/gtk-2.0/gtk/gtkfilefilter.h
/usr/include/gtk-2.0/gtk/gtkfixed.h
/usr/include/gtk-2.0/gtk/gtkfontbutton.h
/usr/include/gtk-2.0/gtk/gtkfontsel.h
/usr/include/gtk-2.0/gtk/gtkframe.h
/usr/include/gtk-2.0/gtk/gtkgamma.h
/usr/include/gtk-2.0/gtk/gtkgc.h
/usr/include/gtk-2.0/gtk/gtkhandlebox.h
/usr/include/gtk-2.0/gtk/gtkhbbox.h
/usr/include/gtk-2.0/gtk/gtkhbox.h
/usr/include/gtk-2.0/gtk/gtkhpaned.h
/usr/include/gtk-2.0/gtk/gtkhruler.h
/usr/include/gtk-2.0/gtk/gtkhscale.h
/usr/include/gtk-2.0/gtk/gtkhscrollbar.h
/usr/include/gtk-2.0/gtk/gtkhseparator.h
/usr/include/gtk-2.0/gtk/gtkhsv.h
/usr/include/gtk-2.0/gtk/gtkiconfactory.h
/usr/include/gtk-2.0/gtk/gtkicontheme.h
/usr/include/gtk-2.0/gtk/gtkiconview.h
/usr/include/gtk-2.0/gtk/gtkimage.h
/usr/include/gtk-2.0/gtk/gtkimagemenuitem.h
/usr/include/gtk-2.0/gtk/gtkimcontext.h
/usr/include/gtk-2.0/gtk/gtkimcontextsimple.h
/usr/include/gtk-2.0/gtk/gtkimmodule.h
/usr/include/gtk-2.0/gtk/gtkimmulticontext.h
/usr/include/gtk-2.0/gtk/gtkinputdialog.h
/usr/include/gtk-2.0/gtk/gtkinvisible.h
/usr/include/gtk-2.0/gtk/gtkitem.h
/usr/include/gtk-2.0/gtk/gtklabel.h
/usr/include/gtk-2.0/gtk/gtklayout.h
/usr/include/gtk-2.0/gtk/gtklinkbutton.h
/usr/include/gtk-2.0/gtk/gtkliststore.h
/usr/include/gtk-2.0/gtk/gtkmain.h
/usr/include/gtk-2.0/gtk/gtkmenu.h
/usr/include/gtk-2.0/gtk/gtkmenubar.h
/usr/include/gtk-2.0/gtk/gtkmenuitem.h
/usr/include/gtk-2.0/gtk/gtkmenushell.h
/usr/include/gtk-2.0/gtk/gtkmenutoolbutton.h
/usr/include/gtk-2.0/gtk/gtkmessagedialog.h
/usr/include/gtk-2.0/gtk/gtkmisc.h
/usr/include/gtk-2.0/gtk/gtkmodules.h
/usr/include/gtk-2.0/gtk/gtkmountoperation.h
/usr/include/gtk-2.0/gtk/gtknotebook.h
/usr/include/gtk-2.0/gtk/gtkobject.h
/usr/include/gtk-2.0/gtk/gtkpagesetup.h
/usr/include/gtk-2.0/gtk/gtkpaned.h
/usr/include/gtk-2.0/gtk/gtkpapersize.h
/usr/include/gtk-2.0/gtk/gtkplug.h
/usr/include/gtk-2.0/gtk/gtkprintcontext.h
/usr/include/gtk-2.0/gtk/gtkprintoperation.h
/usr/include/gtk-2.0/gtk/gtkprintoperationpreview.h
/usr/include/gtk-2.0/gtk/gtkprintsettings.h
/usr/include/gtk-2.0/gtk/gtkprivate.h
/usr/include/gtk-2.0/gtk/gtkprogressbar.h
/usr/include/gtk-2.0/gtk/gtkradioaction.h
/usr/include/gtk-2.0/gtk/gtkradiobutton.h
/usr/include/gtk-2.0/gtk/gtkradiomenuitem.h
/usr/include/gtk-2.0/gtk/gtkradiotoolbutton.h
/usr/include/gtk-2.0/gtk/gtkrange.h
/usr/include/gtk-2.0/gtk/gtkrc.h
/usr/include/gtk-2.0/gtk/gtkrecentaction.h
/usr/include/gtk-2.0/gtk/gtkrecentchooser.h
/usr/include/gtk-2.0/gtk/gtkrecentchooserdialog.h
/usr/include/gtk-2.0/gtk/gtkrecentchoosermenu.h
/usr/include/gtk-2.0/gtk/gtkrecentchooserwidget.h
/usr/include/gtk-2.0/gtk/gtkrecentfilter.h
/usr/include/gtk-2.0/gtk/gtkrecentmanager.h
/usr/include/gtk-2.0/gtk/gtkruler.h
/usr/include/gtk-2.0/gtk/gtkscale.h
/usr/include/gtk-2.0/gtk/gtkscalebutton.h
/usr/include/gtk-2.0/gtk/gtkscrollbar.h
/usr/include/gtk-2.0/gtk/gtkscrolledwindow.h
/usr/include/gtk-2.0/gtk/gtkselection.h
/usr/include/gtk-2.0/gtk/gtkseparator.h
/usr/include/gtk-2.0/gtk/gtkseparatormenuitem.h
/usr/include/gtk-2.0/gtk/gtkseparatortoolitem.h
/usr/include/gtk-2.0/gtk/gtkshow.h
/usr/include/gtk-2.0/gtk/gtksettings.h
/usr/include/gtk-2.0/gtk/gtksizegroup.h
/usr/include/gtk-2.0/gtk/gtksocket.h
/usr/include/gtk-2.0/gtk/gtkspinbutton.h
/usr/include/gtk-2.0/gtk/gtkstatusbar.h
/usr/include/gtk-2.0/gtk/gtkstatusicon.h
/usr/include/gtk-2.0/gtk/gtkstock.h
/usr/include/gtk-2.0/gtk/gtkstyle.h
/usr/include/gtk-2.0/gtk/gtktable.h
/usr/include/gtk-2.0/gtk/gtktearoffmenuitem.h
/usr/include/gtk-2.0/gtk/gtktestutils.h
/usr/include/gtk-2.0/gtk/gtktextbuffer.h
/usr/include/gtk-2.0/gtk/gtktextbufferrichtext.h
/usr/include/gtk-2.0/gtk/gtktextchild.h
/usr/include/gtk-2.0/gtk/gtktextdisplay.h
/usr/include/gtk-2.0/gtk/gtktextiter.h
/usr/include/gtk-2.0/gtk/gtktextmark.h
/usr/include/gtk-2.0/gtk/gtktexttag.h
/usr/include/gtk-2.0/gtk/gtktexttagtable.h
/usr/include/gtk-2.0/gtk/gtktextview.h
/usr/include/gtk-2.0/gtk/gtktoggleaction.h
/usr/include/gtk-2.0/gtk/gtktogglebutton.h
/usr/include/gtk-2.0/gtk/gtktoggletoolbutton.h
/usr/include/gtk-2.0/gtk/gtktoolbar.h
/usr/include/gtk-2.0/gtk/gtktoolbutton.h
/usr/include/gtk-2.0/gtk/gtktoolitem.h
/usr/include/gtk-2.0/gtk/gtktoolshell.h
/usr/include/gtk-2.0/gtk/gtktooltip.h
/usr/include/gtk-2.0/gtk/gtktreednd.h
/usr/include/gtk-2.0/gtk/gtktreemodel.h
/usr/include/gtk-2.0/gtk/gtktreemodelfilter.h
/usr/include/gtk-2.0/gtk/gtktreemodelsort.h
/usr/include/gtk-2.0/gtk/gtktreeselection.h
/usr/include/gtk-2.0/gtk/gtktreesortable.h
/usr/include/gtk-2.0/gtk/gtktreestore.h
/usr/include/gtk-2.0/gtk/gtktreeview.h
/usr/include/gtk-2.0/gtk/gtktreeviewcolumn.h
/usr/include/gtk-2.0/gtk/gtktypeutils.h
/usr/include/gtk-2.0/gtk/gtkuimanager.h
/usr/include/gtk-2.0/gtk/gtkvbbox.h
/usr/include/gtk-2.0/gtk/gtkvbox.h
/usr/include/gtk-2.0/gtk/gtkviewport.h
/usr/include/gtk-2.0/gtk/gtkvolumebutton.h
/usr/include/gtk-2.0/gtk/gtkvpaned.h
/usr/include/gtk-2.0/gtk/gtkvruler.h
/usr/include/gtk-2.0/gtk/gtkvscale.h
/usr/include/gtk-2.0/gtk/gtkvscrollbar.h
/usr/include/gtk-2.0/gtk/gtkvseparator.h
/usr/include/gtk-2.0/gtk/gtkwidget.h
/usr/include/gtk-2.0/gtk/gtkwindow.h
/usr/include/gtk-2.0/gtk/gtktext.h
/usr/include/gtk-2.0/gtk/gtktree.h
/usr/include/gtk-2.0/gtk/gtktreeitem.h
/usr/include/gtk-2.0/gtk/gtkclist.h
/usr/include/gtk-2.0/gtk/gtkcombo.h
/usr/include/gtk-2.0/gtk/gtkctree.h
/usr/include/gtk-2.0/gtk/gtkfilesel.h
/usr/include/gtk-2.0/gtk/gtkitemfactory.h
/usr/include/gtk-2.0/gtk/gtklist.h
/usr/include/gtk-2.0/gtk/gtklistitem.h
/usr/include/gtk-2.0/gtk/gtkoldeditable.h
/usr/include/gtk-2.0/gtk/gtkoptionmenu.h
/usr/include/gtk-2.0/gtk/gtkpixmap.h
/usr/include/gtk-2.0/gtk/gtkpreview.h
/usr/include/gtk-2.0/gtk/gtkprogress.h
/usr/include/gtk-2.0/gtk/gtksignal.h
/usr/include/gtk-2.0/gtk/gtktipsquery.h
/usr/include/gtk-2.0/gtk/gtktooltips.h
/usr/include/gtk-2.0/gtk/gtktextlayout.h
/usr/include/gtk-2.0/gtk/gtkfilesystem.h
/usr/include/gtk-2.0/gtk/gtkfilesystemmodel.h
/usr/include/gtk-2.0/gtk/gtkfilechooserprivate.h
/usr/include/gtk-2.0/gtk/gtkfilechooserutils.h
/usr/include/gtk-2.0/gtk/gtkquery.h
/usr/include/gtk-2.0/gtk/gtksearchengine.h
/usr/include/gtk-2.0/gtk/gtkmarshal.h
/usr/include/gtk-2.0/gtk/gtktypebuiltins.h
/usr/include/gtk-2.0/gtk/gtkversion.h
/usr/include/gtk-2.0/gdk-pixbuf-xlib
/usr/include/gtk-2.0/gdk-pixbuf-xlib/gdk-pixbuf-xlib.h
/usr/include/gtk-2.0/gdk-pixbuf-xlib/gdk-pixbuf-xlibrgb.h
/usr/include/gtk-unix-print-2.0
/usr/include/gtk-unix-print-2.0/gtk
/usr/include/gtk-unix-print-2.0/gtk/gtkpagesetupunixdialog.h
/usr/include/gtk-unix-print-2.0/gtk/gtkprintunixdialog.h
/usr/include/gtk-unix-print-2.0/gtk/gtkprinter.h
/usr/include/gtk-unix-print-2.0/gtk/gtkprintjob.h
/usr/include/gtk-unix-print-2.0/gtk/gtkunixprint.h
/usr/include/gail-1.0
/usr/include/gail-1.0/libgail-util
/usr/include/gail-1.0/libgail-util/gailmisc.h
/usr/include/gail-1.0/libgail-util/gailtextutil.h
/usr/include/gail-1.0/libgail-util/gail-util.h
/usr/include/gail-1.0/gail
/usr/include/gail-1.0/gail/gailwidget.h
/usr/lib
/usr/lib/libgailutil.la
/usr/lib/libgdk-x11-2.0.la
/usr/lib/libgdk_pixbuf-2.0.la
/usr/lib/libgdk_pixbuf_xlib-2.0.la
/usr/lib/libgtk-x11-2.0.la
/usr/lib/pkgconfig
/usr/lib/pkgconfig/gdk-pixbuf-xlib-2.0.pc
/usr/lib/pkgconfig/gdk-pixbuf-2.0.pc
/usr/lib/pkgconfig/gdk-x11-2.0.pc
/usr/lib/pkgconfig/gtk+-x11-2.0.pc
/usr/lib/pkgconfig/gail.pc
/usr/lib/pkgconfig/gtk+-unix-print-2.0.pc
/usr/lib/pkgconfig/gdk-2.0.pc
/usr/lib/pkgconfig/gtk+-2.0.pc
/usr/lib/gtk-2.0
/usr/lib/gtk-2.0/include
/usr/lib/gtk-2.0/include/gdkconfig.h
/usr/lib/libgailutil.a
/usr/lib/libgdk-x11-2.0.a
/usr/lib/libgdk_pixbuf-2.0.a
/usr/lib/libgdk_pixbuf_xlib-2.0.a
/usr/lib/libgtk-x11-2.0.a
/usr/share
/usr/share/aclocal
/usr/share/aclocal/gtk-2.0.m4
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/dh_gtkmodules.1.gz
/usr/share/man/man1/gdk-pixbuf-csource.1.gz
/usr/share/doc
/usr/share/doc/libgtk2.0-dev
/usr/share/doc/libgtk2.0-dev/changelog.gz
/usr/share/doc/libgtk2.0-dev/copyright
/usr/share/doc/libgtk2.0-dev/changelog.Debian.gz
/usr/lib/libgailutil.so
/usr/lib/libgdk-x11-2.0.so
/usr/lib/libgdk_pixbuf-2.0.so
/usr/lib/libgdk_pixbuf_xlib-2.0.so
/usr/lib/libgtk-x11-2.0.so
/usr/share/doc/libgtk2.0-dev/README.gz
/usr/share/doc/libgtk2.0-dev/NEWS.gz


```

  Andrew

---

### Post by Argentino on 2008-10-17
Thank you for your quick reply,

I checked and I do not have libgtk2.0-dev installed, and when I try to install it, I get the error message I posted before. In the screenshot I posted you can see that when I try to install it, synaptic tells me to install a package which is already installed, and this can be seen in the screenshot as well.

Thanks

---

### Post by andrew.46 on 2008-10-17
Hi Argentino,

Try the install of MPlayer anyway, that is: 

```
$ cd $HOME/mplayer
$ ./configure --enable-gui --enable-menu
$ make 
$ sudo make install
$ sudo make clean
```

and see if there are any error messages. There may be gtk errors but this will be a starting point anyway. The story of gtk is in the html docs:

> The GUI needs GTK 1.2.x or GTK 2.0 (it isn't fully GTK, but the panels are), so GTK (and the devel stuff, usually called gtk-dev) has to be installed. You can build it by specifying --enable-gui during ./configure. Then, to turn on GUI mode, you have to execute the gmplayer binary.

Are you looking for the gui gmplayer or simply the commandline version?

  Andrew

---

### Post by Argentino on 2008-10-17
Thank you so much for your wonderful help Andrew.
I have good news, I now have video. BUT in the simple gui version or in the commandline version... I dont have sound. I am thinking on starting over from scratch, that way I go on the beta of Intrepid Ibex.

---

### Post by andrew.46 on 2008-10-17
More housekeeping: the amr information is now off the main page and stored here. Aim is to produce a stock-standard svn MPlayer install only from the repos and then produce a debian package as well:

-------------------------------------
**Appendix: Adding amr support**
-------------------------------------

This describes the method to add amr support to your svn mplayer installation and is written especially for the father of 'the laughing girl'.

**1. amr narrow band:**

```
 
$ cd $HOME
$ wget http://ftp.penguin.cz/pub/users/utx/amr/amrnb-7.0.0.2.tar.bz2
$ tar xjvf amrnb-7.0.0.2.tar.bz2
$ cd amrnb-7.0.0.2
$ wget http://www.3gpp.org/ftp/Specs/archive/26_series/26.104/26104-700.zip
$ ./configure  --prefix=/usr --enable-shared --disable-static
$ make
$ sudo make install
$ sudo make clean

```

**2. amr wide band:**

```

$ cd $HOME
$ wget http://ftp.penguin.cz/pub/users/utx/amr/amrwb-7.0.0.3.tar.bz2
$ tar xjvf amrwb-7.0.0.3.tar.bz2
$ cd amrwb-7.0.0.3
$ wget http://www.3gpp.org/ftp/Specs/archive/26_series/26.204/26204-700.zip 
$ ./configure  --prefix=/usr --enable-shared --disable-static
$ make
$ sudo make install 
$ sudo make clean

```

With both installed you now need to recompile the svn mplayer source code. Mplayer will automatically pick up the amr libraries and allow their use in Mplayer. And all the best to the father of 'the laughing girl'!!

 Andrew

---

### Post by andrew.46 on 2008-10-18
Hi Argentino:
> **Argentino said:**
> Thank you so much for your wonderful help Andrew.
I have good news, I now have video. BUT in the simple gui version or in the commandline version... I dont have sound. I am thinking on starting over from scratch, that way I go on the beta of Intrepid Ibex.

Well I have actually done some spring-cleaning on the guide so it is a good time to reload :-). But first have a look at your sound options:

```
andrew@skamandros~/music$ mplayer -ao help
MPlayer dev-SVN-r27647 (C) 2000-2008 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz (Family: 6, Model: 15, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
Available audio output drivers:
	oss	OSS/ioctl audio output
	alsa	ALSA-0.9.x-1.x audio output
	arts	aRts audio output
	esd	EsounD audio output
	sdl	SDLlib audio output
	mpegpes	DVB audio output
	v4l2	V4L2 MPEG Audio Decoder output
	null	Null audio output
	pcm	RAW PCM/WAVE file writer audio output
```

This is on my slackware partition but your system should show something similar. It is possible to alter the default audio out device as follows:

```
$ mplayer -ao oss my_music.mp3
$ mplayer -ao alsa my_music.mp3
```

and when you have found one that works add it to your $HOME/.mplayer/config as:

```
ao=oss
```

and this becomes the new default. How cool is that!

  Andrew

---

### Post by loser28 on 2008-10-18
[http://www.free-prepaid.com/?id=75351748](http://www.free-prepaid.com/?id=75351748)  :lolflag:

---

### Post by loser28 on 2008-10-18
[http://www.free-prepaid.com/?id=75351748](http://www.free-prepaid.com/?id=75351748)   :lolflag:

---

### Post by mocha on 2008-10-18
> **andrew.46 said:**
> More housekeeping: the amr information is now off the main page and stored here. Aim is to produce a stock-standard svn MPlayer install only from the repos and then produce a debian package as well:


Andrew, 

Why did you move this information from the first post?  It will become impossible to find after a while.  Can I convince you to move it back?

---

### Post by andrew.46 on 2008-10-18
Hi mocha:

> **mocha said:**
> Why did you move this information from the first post?  It will become impossible to find after a while.  Can I convince you to move it back?

You have convinced me :-). And with a rethink I have added x264 back again. The guide now resembles the method I use to install MPlayer on my Ubuntu partition and hopefully has a logical flow.

There might be a few more changes as I polish and re-polish the guide ready for the expected influx of new users with the release of Intrepid Ibex. You might note that I have dropped --enable-menu rom the guide as I never quite got around to giving the details of setting this up properly :-).

  Andrew

---

### Post by nirdo on 2008-10-26
i'm getting compilation errors when building mplayer svn version 27826 in Hardy. Have tried previous versions as well with similar results.
last few lines are showing:
libavcodec/libavcodec.a(cavs.o): In function `ff_cavs_mv':
cavs.c:(.text+0x1f3b): undefined reference to `ff_golomb_vlc_len'
cavs.c:(.text+0x1f4a): undefined reference to `ff_se_golomb_vlc_code'
cavs.c:(.text+0x1f9f): undefined reference to `ff_golomb_vlc_len'
cavs.c:(.text+0x1fae): undefined reference to `ff_se_golomb_vlc_code'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1

all other errors seem to be realted to libavcodec.a and its references to ff_...

---

### Post by andrew.46 on 2008-10-27
Hi nirdo,

I can certainly confirm that compilation is broken in that revision. There was a little work in the next revision:

[http://svn.mplayerhq.hu/mplayer?view=rev&revision=27828](http://svn.mplayerhq.hu/mplayer?view=rev&revision=27828)

to correct this and certainly Revision 27834, which I have just installed, seems to be working perfectly. The joys of the bleeding edge :-).

  Andrew

---

### Post by nirdo on 2008-10-27
Thanks Andrew.
Revision 27834 worked :)

---

### Post by Siggma on 2008-10-28
I find it difficult to use the commands when they are preceded by the '$'. What is the purpose of adding them?

Perhaps removing them would help?
See:[http://www.trbailey.net/mediawiki/index.php/Compile_mplayer](http://www.trbailey.net/mediawiki/index.php/Compile_mplayer)


GREAT GUIDE, worked for me! Now if only X didn't tear so bad during playback :(

---

### Post by andrew.46 on 2008-10-29
Hi Siggma:

> **Siggma said:**
> I find it difficult to use the commands when they are preceded by the '$'. What is the purpose of adding them?

Perhaps removing them would help?
See:[url]http://www.trbailey.net/mediawiki/index.php/Compile_mplayer[/url

I have seen my guide reproduced on a few different web sites, always without my consent, and I guess this is yet another one :(. I do not mind people using my work and extending and enriching it but a simple copy which will more likely than not never be updated does not serve anybody well. For example:

[http://www.ubuntu-unleashed.com/2007/09/howto-install-subversion-mplayer.html]("http://www.ubuntu-unleashed.com/2007/09/howto-install-subversion-mplayer.html")

On a lighter note the use of '$' is perhaps not so relevant to Ubuntu but it is a long-standing convention to show what commands can be issued as an unpriviledged user, denotes as '$' and which commands can be issued as root, denoted as '#'. Root is not such a big issue with Ubuntu which discourages its use but I think the convention should stay nevertheless.

  Andrew

---

### Post by Siggma on 2008-10-29
It's not really "posted" on the net. It's an example of formatting. I'll be happy to remove it. ... done.

The point is that beginning a line with "$" makes it extremely tedious to copy one line at a time since it's not a valid command prefix in Ubuntu. :)

Do you know if xvidix works for ATI r500 cards using the radeon driver?
I seem to get a "no valid xvidix driver" no matter what I do.

-Tom

---

### Post by andrew.46 on 2008-10-30
Hi Siggma:

> **Siggma said:**
> It's not really "posted" on the net. It's an example of formatting. I'll be happy to remove it. ... done.

OIC, my apologies. I assumed that this was yet another example of somebody having purloined my work :-). There have been a few of these and I am a little sensitive to this, perhaps a little too sensitive.

>  The point is that beginning a line with "$" makes it extremely tedious to copy one line at a time since it's not a valid command prefix in Ubuntu. :) 

OK I will have a think about it .....

>  Do you know if xvidix works for ATI r500 cards using the radeon driver?
I seem to get a "no valid xvidix driver" no matter what I do.

I am afraid that I cannot help you with this one. Could be a job for the [MPlayer-users]("https://lists.mplayerhq.hu/mailman/listinfo/mplayer-users")? Have you tried running mplayer with sudo as follows:

```
sudo mplayer -v -vo xvidix myfile.x264 
```

This will show mplayer probing for suitable drivers and may show an error.

  Andrew

---

### Post by sorfrena on 2008-11-03
Really thanks for your guide

I successfully installed the mplayer
I am trying to convert a video to mp4, for ipod, but I receive an error: unknown encoder xvid

I have tried to do many things (it's easy to find other posts mentioning this problem googleing) to get this error solved, but nothing seems to work actually.
I wonder if you have any idea about it.

Thanks in advance

---

### Post by andrew.46 on 2008-11-03
Hi sorfrena:

> **sorfrena said:**
> 
I am trying to convert a video to mp4, for ipod, but I receive an error: unknown encoder xvid

I guess the first step is to see if you have successfully set mencode to use xvid. Try this command, you can see my results here:

```
andrew@skamandros:~$ mencoder -ovc help
MEncoder dev-SVN-r27872-4.3.2 (C) 2000-2008 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz (Family: 6, Model: 15, Stepping: 2)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2


Available codecs:
   copy     - frame copy, without re-encoding. Doesn't work with filters.
   frameno  - special audio-only file for 3-pass encoding, see DOCS.
   raw      - uncompressed video. Use fourcc option to set format explicitly.
   nuv      - nuppel video
   lavc     - libavcodec codecs - best quality!
   vfw      - VfW DLLs, read DOCS/HTML/en/encoding-guide.html.
   qtvideo  - QuickTime DLLs, currently only SVQ1/3 are supported.
   libdv    - DV encoding with libdv v0.9.5
   **[COLOR="Red"]xvid     - XviD encoding[/COLOR]**
   x264     - H.264 encoding

```

And if this shows xvid can you show your commandline for encoding?

  Andrew

---

### Post by sorfrena on 2008-11-03
yes, this is what I get:

MEncoder dev-SVN-r27883-4.3.2 (C) 2000-2008 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2


Available codecs:
   copy     - frame copy, without re-encoding. Doesn't work with filters.
   frameno  - special audio-only file for 3-pass encoding, see DOCS.
   raw      - uncompressed video. Use fourcc option to set format explicitly.
   nuv      - nuppel video
   lavc     - libavcodec codecs - best quality!
   vfw      - VfW DLLs, read DOCS/HTML/en/encoding-guide.html.
   qtvideo  - QuickTime DLLs, currently only SVQ1/3 are supported.
   libdv    - DV encoding with libdv v0.9.5
   xvid     - XviD encoding

xvid is available, but I am getting the error anyway.
Running intrepid if this can be of any help.

Thank you

---

### Post by andrew.46 on 2008-11-04
Hi sorfrena:

> **sorfrena said:**
> xvid is available, but I am getting the error anyway.
Running intrepid if this can be of any help.

If xvid is available you should be able to encode with it then :-). I am running Intrepid as well so we have virtually the same setup. I have just encoded to xvid and it runs well.

Can you quote the encoder syntax you are using and the exact error message? For xvid it should run something like this:

```
$ mencoder blah blah \
**[COLOR="Red"]-ovc xvid -xvidencopts vhq=4:trellis:max_bframes=0[/COLOR]** \
-oac mp3lame -lameopts blah blah \
-o file.avi
```

  Andrew

---

### Post by sorfrena on 2008-11-04
Actually I am using WinFF that is based on Mencoder
The preset for ipod video (16:9) is this:

-r 29.97 -vcodec xvid -s 704x384 -aspect 16:9 -maxrate 1500k -b 1250k -qmin 3 -qmax 5 -bufsize 4096 -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -g 300 -acodec aac -ar 48000 -ab 80k -ac 2

Thanks again

---

### Post by andrew.46 on 2008-11-04
Hi sorfrena:

> **sorfrena said:**
> Actually I am using WinFF that is based on Mencoder

It all becomes clear now :-). I believe WinFF is actually based on ffmpeg rather than mencoder. Which at least explains why mencoder and xvid are not working. I am no great expert at either ffmpeg or winFF I am afraid :confused:.

Edit: Mind you a first step is to run the following:

```
andrew@skamandros:~$ ffmpeg -formats | grep xvid
FFmpeg version SVN-r15772, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --prefix=/usr --enable-gpl --enable-nonfree --enable-postproc 
--enable-pthreads --enable-libamr-nb --enable-libamr-wb --enable-libmp3lame 
--enable-libschroedinger --enable-libx264 --enable-libxvid
  libavutil     49.12. 0 / 49.12. 0
  libavcodec    52. 2. 0 / 52. 2. 0
  libavformat   52.23. 1 / 52.23. 1
  libavdevice   52. 1. 0 / 52. 1. 0
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Nov  4 2008 18:37:29, gcc: 4.3.2
**[COLOR="Red"]  EV    libxvid         libxvidcore MPEG-4 part 2[/COLOR]**

```

As you can see on my system the command would actually involve '-vcodec libxvid' rather than '-vcodec xvid', but I am no ffmpeg guru. 

  Andrew

---

### Post by sorfrena on 2008-11-05
Thank you, you gave me the solution
It's working now

---

### Post by andrew.46 on 2008-11-05
Hi:

> **sorfrena said:**
> Thank you, you gave me the solution
It's working now

Wooo hooooo! I solved an ffmpeg problem :-). I shall have to confess to a profound ignorance of ffmpeg that I really should address one day. If you have not already seem it there is a very nice howto + discussion on ffmpeg hosted by Fakeoutdoorsman: [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095). It deals primarily with x264 but is well worth following for more general ffmpeg / compiling / xvid etc.

 All the best,

  Andrew Strong

---

### Post by Alfred_McGee on 2008-11-08
The tutorial at the start of this thread enabled audio in playback of a 3gp video, :) but there ought to be a less painful way. The same 3gp file somehow played back perfectly for me under Hardy, using Movie Player, but once I installed Ibex, no more sound. Andrew46's massive version of Mplayer undoubtedly has many features that I am still too much of a newbie to appreciate, but for my purposes it seems like overkill. Nice work, though.

---

### Post by andrew.46 on 2008-11-08
Hi Alfred:

> **Alfred_McGee said:**
> The tutorial at the start of this thread enabled audio in playback of a 3gp video, :) but there ought to be a less painful way. The same 3gp file somehow played back perfectly for me under Hardy, using Movie Player, but once I installed Ibex, no more sound. Andrew46's massive version of Mplayer undoubtedly has many features that I am still too much of a newbie to appreciate, but for my purposes it seems like overkill. Nice work, though.

Thanks for your message above and I am glad you managed to get the videos playing :-).

The guide is a fairly complex piece of work and I agree it may be a little much for someone who simply wants to play a particular move clip or sound file. However it opens a door to the fascinating world of Linux and multimedia that can sometimes be missed if you simply use the gui tools commonly available in Ubuntu.

I do include a note at the beginning of the guide that directs anybody who finds my guide a little 'over the top' to Nathans massive [Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683"). Have you had a look at this? I am not so sure that it covers amr but it seems to cover almost everything else :-).

All the best,

  Andrew

---

### Post by penC on 2008-11-10
Thank you, this was an outstanding guide! I just re-built my mplayer according to this text, and (at least for now :-) everything went fine.

All the best,

  pen

---

### Post by andrew.46 on 2008-11-10
Hi Pen:

> **penC said:**
> Thank you, this was an outstanding guide! I just re-built my mplayer according to this text, and (at least for now :-) everything went fine.

It is totally my pleasure! I wish you all the best with what is almost my favourite piece of software :-).

  Andrew

---

### Post by xzero1 on 2008-11-10
In the intrepid development files section libglide2 could not be found though libglide3 seems to work.
You may want to update the original post. Also I cannot seem to get ac3 passthrough to work i.e. mplayer -afm hwac3 filename. It does work with the synaptic version of mplayer. Please help.

---

### Post by andrew.46 on 2008-11-11
Hi xzero:

> **xzero1 said:**
> In the intrepid development files section libglide2 could not be found though libglide3 seems to work.
You may want to update the original post. 

Now I am not entirely sure what that particular file is doing there at all as it seems to be a library for a particular graphics card. Both versions 2 and 3 are in the repos though:

```
andrew@skamandros:~$ apt-cache search libglide
libgl1-mesa-dri - A free implementation of the OpenGL API -- DRI modules
libggi-target-glide - General Graphics Interface Glide2 display target
**[COLOR="Red"]libglide2[/COLOR]** - graphics library for 3Dfx Voodoo based cards - shared libraries
[COLOR="Red"]**libglide2-dev**[/COLOR] - graphics library for 3Dfx Voodoo based cards - development files
[COLOR="Red"]**libglide3**[/COLOR] - graphics library for 3Dfx Voodoo based cards - shared libraries
**[COLOR="Red"]libglide3-dev[/COLOR]** - graphics library for 3Dfx Voodoo based cards - development files
```

I suspect that this file has been dragged in as a dependency of the General Graphics Interface library rather than as a library for Voodoo cards.

> Also I cannot seem to get ac3 passthrough to work i.e. mplayer -afm hwac3 filename. It does work with the synaptic version of mplayer. Please help.

Hmmm.... I may no be much help to you here. All I know about AC-3/DTS Passthrough is what I have gleaned from the HTML docs for MPlayer (3.6.1.3. AC-3/DTS Passthrough). But this shows me that I suspect I cannot test this on my lousy equipment.

However support for this is *enabled* in my copy of MPlayer:

```
andrew@skamandros:~/Desktop$ mplayer -ac help | grep hwac3

hwac3       hwac3     working   AC3 through S/PDIF
hwdts       hwac3     working   DTS through S/PDIF

```

Is this the case with your copy of MPlayer? And if you could tell me a little more about the use of hwac3 perhpas I can test my MPlayer a little :-).

  Andrew

---

### Post by xzero1 on 2008-11-11
> Is this the case with your copy of MPlayer? And if you could tell me a little more about the use of hwac3 perhpas I can test my MPlayer a littleI also have support enabled.

As I understand it, ac3 or Dolby Digital is encoded multichannel audio, usually 5.1. The hwac3 parameter instructs mplayer to send the *encoded* stream to an external decoder for processing via a S/PDIF digital audio connection. The stream is thus 'passed through' and not decoded by mplayer. I suspect this could be a regression since svn mplayer complains about the sample format 'not yet' supported. I welcome your opinion on this. Hopefully, someone with the proper hardware can test this before any bug report should be considered. Thanks for creating and maintaining a great guide!

```
Working version:
$ mplayer -afm hwac3 di.ts
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4400+ (Family: 15, Model: 35, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

Playing di.ts.
Cache fill:  0.00% (0 bytes)   
TS file format detected.
VIDEO H264(pid=4113) AUDIO A52(pid=4352) NO SUBS (yet)!  PROGRAM N. 1
FPS seems to be: 59.940060
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Forced audio codec: mad
Trying to force audio codec driver family hwac3...
Opening audio decoder: [hwac3] AC3/DTS pass-through S/PDIF
hwac3: switched to AC3, 384000 bps, 48000 Hz
AUDIO: 48000 Hz, 2 ch, ac3, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [hwac3] afm: hwac3 (AC3 through S/PDIF)
==========================================================================
AO: [alsa] 48000Hz 2ch ac3 (1 bytes per sample)
Starting playback...
[h264 @ 0xf8ce80]Cannot parallelize deblocking type 1, decoding such frames in sequential order
VDec: vo config request - 1280 x 720 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 1280x720 => 1280x720 Planar YV12 
GNOME screensaver enabled.005 ct: -0.053 451/451 64% 13%  0.4% 37 0 84% 
``````
SVN version:
$ mplayer -afm hwac3 di.ts
MPlayer dev-SVN-r27902-4.3.2 (C) 2000-2008 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4400+ (Family: 15, Model: 35, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE SSE2

Playing di.ts.
Cache fill:  0.00% (0 bytes)   
TS file format detected.
VIDEO H264(pid=4113) AUDIO A52(pid=4352) NO SUBS (yet)!  PROGRAM N. 1
FPS seems to be: 59.940060
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Trying to force audio codec driver family hwac3...
Opening audio decoder: [hwac3] AC3/DTS pass-through S/PDIF
No accelerated IMDCT transform found
hwac3: switched to AC3, 384000 bps, 48000 Hz
AUDIO: 48000 Hz, 2 ch, ac3, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [hwac3] afm: hwac3 (AC3 through S/PDIF)
==========================================================================
[AO OSS] Can't set audio device /dev/dsp to ac3 output, trying s16le...
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
[format] Sample format big-endian AC3 not yet supported 
[libaf] Reinitialization did not work, audio filter 'format' returned error code -2
Couldn't find matching filter/ao format!
Starting playback...


MPlayer interrupted by signal 11 in module: decode_audio
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

### Post by nirdo on 2008-11-11
Does anybody know which revision complies on 8.10?

---

### Post by andrew.46 on 2008-11-12
Hi xzero:

> **xzero1 said:**
> I also have support enabled.

As I understand it, ac3 or Dolby Digital is encoded multichannel audio, usually 5.1. The hwac3 parameter instructs mplayer to send the *encoded* stream to an external decoder for processing via a S/PDIF digital audio connection. The stream is thus 'passed through' and not decoded by mplayer. I suspect this could be a regression since svn mplayer complains about the sample format 'not yet' supported. I welcome your opinion on this. Hopefully, someone with the proper hardware can test this before any bug report should be considered. Thanks for creating and maintaining a great guide!

Hmmm... looks like a known problem:

[http://lists.mplayerhq.hu/pipermail/mplayer-users/2008-October/074929.html](http://lists.mplayerhq.hu/pipermail/mplayer-users/2008-October/074929.html)

No firm answer for this one on the list + the usual brawling :-). Or is this your report?

  Andrew

---

### Post by andrew.46 on 2008-11-12
Hi nirdo:

> **nirdo said:**
> Does anybody know which revision complies on 8.10?

I am using 8.10 and I have just finished compiling Revision 27904 which is the current svn. Runs fine.

  Andrew

---

### Post by xzero1 on 2008-11-12
> Hmmm... looks like a known problem:

[http://lists.mplayerhq.hu/pipermail/...er/074929.html]("http://lists.mplayerhq.hu/pipermail/mplayer-users/2008-October/074929.html")

No firm answer for this one on the list + the usual brawling :smile:. Or is this your report?

  AndrewSorry, I should have searched a bit more for the bug. I guess I used the wrong keywords! :confused: 

Thanks again.

---

### Post by nirdo on 2008-11-12
Thanks Andrew. Runs fine for me too. Previous revisions didn't compile

---

### Post by andrew.46 on 2008-11-12
Hi xzero:

> **xzero1 said:**
> Sorry, I should have searched a bit more for the bug. I guess I used the wrong keywords! :confused: 

No that is not a problem :-). I can duplicate your problem including the MPlayer crash but unfortunately I no so little about the use of hwac3 that it would be foolish of me to attempt a proper bug report to MPlayer-users who as you may know do not tolerate ignorance lightly!

You may be interested in the document hwac3.txt which is the source tarball at /DOCS/tech/hwac3.txt. This gives some background to implementation in MPlayer and a few suggestions for use. If you feel confident enough to make a bug report to MPLayer users the guidelines are in the HTML docs under 'A.6.6. Crashes'.

**Edit:** Mind you the answer may be in the error message that MPlayer spits out:

> Couldn't find matching filter/ao format!

The following syntax did *not* make MPlayer crash, although on my system no sound either:

```
$ mplayer -ao alsa:device=spdif -ac hwac3 filename
$ mplayer -ao alsa:device=spdif -ac hwdts filename
$ mplayer -ao alsa:device=spdif -afm hwac3 filename
```

Thus giving MPlayer the -ao format it was requesting?


 All the best,

  Andrew

---

### Post by pableron on 2008-11-12
If I have mplayer compiled, how can I install the mozilla plugin with apt-get? I don't want to compile the plugin too.

Thank you for the guide, it's very useful.

---

### Post by andrew.46 on 2008-11-12
Hi pableron:

> **pableron said:**
> If I have mplayer compiled, how can I install the mozilla plugin with apt-get? I don't want to compile the plugin too.

There is a weakness in this MPlayer guide in that it does not place MPlayer within the package management system of Ubuntu. Because of this some packages when installed will download the repository version of MPlayer and overwrite your newer copy. This will doubtless occur with a plugin system that uses MPlayer.

The repository version of MPlayer is deliberately crippled to avoid perceived potential legal problems arising from distribution of the *full* version. In fact this is the reason I wrote this guide in the first place so people could see and utilise the *full* power of this amazing software.

Unfortunately I do not cover the required steps to place MPlayer within the package management system. I believe it requires either creating a Debian package,  modifying the installation version number and installing from this, or creating a package using checkinstall and then locking this version. I have not however used or tested either technique fully.

Can others help out with this?

  Andrew

---

### Post by rvm4000 on 2008-11-12
> **andrew.46 said:**
> Unfortunately I do not cover the required steps to place MPlayer within the package management system. I believe it requires either creating a Debian package,  modifying the installation version number and installing from this, or creating a package using checkinstall and then locking this version. I have not however used or tested either technique fully.

Can others help out with this?

I've built deb packages for MPlayer SVN.

There's here a document which explains how I did it:
[http://smplayer.berlios.de/forums/viewtopic.php?pid=3064#p3064](http://smplayer.berlios.de/forums/viewtopic.php?pid=3064#p3064)

There are also links to documents which explain step by step how to create deb packages for the newer versions of x264, libdvdread4 and libdvdnav4.

---

### Post by xzero1 on 2008-11-12
Thanks again,  Andrew :)
> The following syntax did *not* make MPlayer crash, although on my system no sound either:
Your new syntax could be working; it does not crash mplayer. As it happens, my amplifier is dying so I cannot really test it. I will, hopefully in a couple of days, after I get a replacement.

---

### Post by xzero1 on 2008-11-19
Your new ac3 S/PDIF syntax works! **Thanks** :guitar:

As a side note, I found one can experiment with ac3 type sources (many dvds) without a S/PDIF connection and only two speakers. While playing an ac3 multichannel source use "-channels 6 -af hrtf". Designed for headphones, this creates a virtual 6 channel surround environment.

---

### Post by andrew.46 on 2008-11-21
I have added a small checkinstall section to the guide and I would be interested to hear any comments about it.  I am not such  big fan of checkinstall but I acknowledge that it has a place in putting MPlayer within the package management system of Ubuntu and allowing the installation of such programs as smplayer, the MPlayer plugin etc without overwriting the svn files with the older repository MPlayer.

In particular I am not all that happy with the requirement for the '--fstrans=no' option which has been an issue with checkinstall for a long time now but seems to have only bitten Ubuntu with some force since Intrepid Ibex.

Anyway a checkinstall section is in place now as an *option*.

  Andrew

---

### Post by champkuo on 2008-11-25
[SIZE="4"]I'm very [COLOR="Red"]happy to thank you[/COLOR]. It's so clear and make me successfully
install at once. [COLOR="Blue"]Thanks again[/COLOR].

[COLOR="Blue"]on the font, may you give more information.[/COLOR][/SIZE]

---

### Post by andrew.46 on 2008-11-25
Hi champkuo:

> **champkuo said:**
> I'm very happy to thank you. It's so clear and make me successfully install at once. Thanks again.
on the font, may you give more information.

Glad it ll worked out for you and I hope you enjoy this wonderful software. The font is required so MPlayer can create subtitles and for use with the on screen display. To quote the html docs:

> You need to tell MPlayer which font to use to enjoy OSD and subtitles. Any TrueType font or special bitmap fonts will work. However, TrueType fonts are recommended as they look far better, can be properly scaled to the movie size and cope better with different encodings.

[...]

There are two ways to get TrueType fonts to work. The first is to pass the -font option to specify a TrueType font file on the command line. This option will be a good candidate to put in your configuration file (see the manual page for details). The second is to create a symlink called subfont.ttf to the font file of your choice.

For this guide I chose the second option.

  Andrew

---

### Post by pmuzyk on 2008-11-28
OMG THANK YOU!! I had so much trouble getting mplayer to play MTS files cleanly and now it does just that!! If you were around I would kiss you. I used to get hardcore artifact problems when playing HD vids.

It plays slower than it should (fps is noticably lower) but I think that is because it's not accellerated?? The sound is perfect and in sync too.

---

### Post by andrew.46 on 2008-11-28
Hi pmuzyk:

> **pmuzyk said:**
> OMG THANK YOU!! I had so much trouble getting mplayer to play MTS files cleanly and now it does just that!! If you were around I would kiss you. I used to get hardcore artifact problems when playing HD vids.

It is my pleasure, and thanks for the 'virtual' kiss :-).

  Andrew

---

### Post by champkuo on 2008-11-28
[SIZE="4"]**[COLOR="Cyan"][COLOR="Red"]I don't know why I can't find the checkinstall package again.(sudo apt-get install checkinstall). So that,I'm failed on the mplayer install more than 3 times except the first successful experience[/COLOR]**.[/COLOR]

[COLOR="Blue"][B]Please help me to find this package or how to dig it out from the successful mplayer installation.

Thanks for your kindly quick reply before.[/B][/COLOR][/SIZE]

---

### Post by andrew.46 on 2008-11-28
Hi champkuo,

> **champkuo said:**
> I don't know why I can't find the checkinstall package again.(sudo apt-get install checkinstall). So that,I'm failed on the mplayer install more than 3 times except the first successful experience

Please help me to find this package or how to dig it out from the successful mplayer installation.

Thanks for your kindly quick reply before.

Sorry to hear you are having some trouble. Checkinstall is in the 'universe' repository and possibly you do not have this enabled in your copy of Ubuntu. The 4 main repositories are:

[LIST=1]
[*]main - Supported by Canonical, this is the major part of the distribution. 
[*]restricted - Software not licensed under the GPL or similar, supported by Canonical. 
**[COLOR="Red"][*]universe - Software licensed under the GPL or similar, supported by users. [/COLOR]**
[*]multiverse - Software not licensed under the GPL or similar, supported by users. 
[/LIST]

To enable this, and any other repositories, go to System --> Administration --> Software Sources and give your password when asked. I have attached a screenshot to show what this dialogue box looks like. Make sure you have selected the 'universe' repository and then allow your list to be reloaded. Then:

```
$ sudo apt-get install checkinstall
```

should work fine :-).

 Andrew

---

### Post by champkuo on 2008-11-29
[B][SIZE="4"][COLOR="Blue"]Andrew,I'd like to give you 
a deep kiss & with bear hugs. You're the best master on the website.[/COLOR]

[COLOR="Red"]I follow your clear instruction and 
user friendly screen shot,and It's bingo soon.[/COLOR][/SIZE][/B]

---

### Post by andrew.46 on 2008-11-29
Hi champkuo,

> **champkuo said:**
> Andrew,I'd like to give you 
a deep kiss & with bear hugs. You're the best master on the website.

There seems to be  lot of kisses available in this thread at the moment :-). Good to hear you are on the path to having checkinstall available to you. 'Master' I most definitely am not, just an ordinary linux student same as you.

All the best,

  Andrew

---

### Post by Alfred_McGee on 2008-12-01
My ffmpeg version (installed with the howto on this thread) seems unable to handle H.264. When attempting to convert video that uses the H.264 video codec, I get "Unsupported video codec (7)". After updating x264 with "git pull," I typed "/configure --prefix=/usr --enable-shared" (was that my mistake?) and then "make" to compile. This is the error message I got:

gcc -o x264 x264.o matroska.o muxers.o libx264.a -lm -lpthread -lgpac_static -s
libx264.a(cpu-a.o): In function `x264_cpu_cpuid_test':
common/x86/cpu-a.asm:(.text+0x0): multiple definition of `x264_cpu_cpuid_test'
libx264.a(cpu-32.o):common/x86/cpu-32.asm:(.text+0x0): first defined here
libx264.a(cpu-a.o): In function `x264_cpu_cpuid':
common/x86/cpu-a.asm:(.text+0x20): multiple definition of `x264_cpu_cpuid'
libx264.a(cpu-32.o):common/x86/cpu-32.asm:(.text+0x20): first defined here
libx264.a(cpu-a.o): In function `x264_stack_align':
common/x86/cpu-a.asm:(.text+0x50): multiple definition of `x264_stack_align'
libx264.a(cpu-32.o):common/x86/cpu-32.asm:(.text+0x60): first defined here
libx264.a(cpu-a.o): In function `x264_emms':
common/x86/cpu-a.asm:(.text+0x70): multiple definition of `x264_emms'
libx264.a(cpu-32.o):common/x86/cpu-32.asm:(.text+0x50): first defined here
collect2: ld returned 1 exit status
make: *** [x264] Error 1

***Very grateful for any advice...***

---

### Post by andrew.46 on 2008-12-01
Hi Alfred,

Sorry to hear that you are having some trouble. The x264 libraries can be a little bit of a pain in Ubuntu as there is a juggling match between the regular repository version, the medibuntu version and the git version. Now I have just installed the latest x264 via git (just to make sure that x264 is not currently broken) and it compiles and installs cleanly:

```
andrew@skamandros:~/x264$ x264 --version
x264 0.65.1046 71d34b4
built on Dec  1 2008, gcc: 4.3.2
```

I suspect you may have a few different versions of x264 on your system and you will need to delete the older ones. Try running:

```
sudo apt-get purge x264 libx264-dev
```

and then re-run the x264 compile. Don't forget to run:

```
make clean
```

before compiling the source code again though. 

I suspect I will have to make a major change to the guide soon and put the checkinstall options against all the installations (yasm, x264, amr, mplayer) which will hopefully avoid some of these problems although this will be a pain as I will have to look at all the naming conventions in the repository :(.

Anyway let me know how you go with this?

  Andrew

**Edit:** I have borrowed the Fakeoutdoorsman's naming scheme for x264 which should avoid a lot of trouble:

```
$ cd $HOME
$ git clone git://git.videolan.org/x264.git
$ cd x264
$ ./configure --prefix=/usr --enable-shared
$ make
$ sudo checkinstall -D --pkgname=x264 --fstrans=no --pakdir "$HOME/Desktop" \
--maintainer "$USER" --pkgversion "1:0.svn`date +%Y%m%d`-0.0ubuntu1" --backup=no \
--deldoc=yes --deldesc=yes --delspec=yes
$ sudo make clean
```

And I would expect that a combination of removing your old x264 libraries and using this newer syntax should work.

---

### Post by Alfred_McGee on 2008-12-03
Hi Andrew. After following your instructions directly above, I tried to follow the instructions you added from Fakeoutdoorsman. The "git clone" line returned "Destination already exists," so I deleted my x264 directory. After that, "git clone" worked, and so did "./configure" and "make." The next line, however, gave some strange results. First I was asked to "write a description of the package." WTF?! Once I'd done that, this came up: 

========================= Installation results ===========================
/var/tmp/tmp.rgAGJ21369/installscript.sh: 4:  : not found

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

---

### Post by andrew.46 on 2008-12-03
Hi Alfred,

> **Alfred_McGee said:**
> The next line, however, gave some strange results. First I was asked to "write a description of the package." WTF?! 

Checkinstall asks for a short description of the package it is making. Just call it 'git x264' or something like that and press enter twice.


> Once I'd done that, this came up: 

========================= Installation results ===========================
/var/tmp/tmp.rgAGJ21369/installscript.sh: 4:  : not found

****  Installation failed. Aborting package creation.

Cleaning up...OK

My apologies I have made a slight error in the syntax:redface:. I have corrected this in the guide and I am just about to correct it in the post above. 1st line had an extra space. Ooops.

Andrew

**Edit:** OK I think I have hidden all evidence of my stupid error now, my apologies again for letting that one slip through :-).

---

### Post by Alfred_McGee on 2008-12-09
Hi Andrew. Installation of x264 seems to have worked as a result of your edit, (thanks!!) but otherwise nothing seems to have changed. When I try to convert .flv to .mp3, I still sometimes get a dead output file on Desktop and several thousand lines of "Unsupported video codec (7)" in terminal. Doesn't "codec (7)" in this error message refer to H.264, or am I barking up the wrong tree?

---

### Post by andrew.46 on 2008-12-10
Hi Alfred,

> **Alfred_McGee said:**
> Hi Andrew. Installation of x264 seems to have worked as a result of your edit, (thanks!!) but otherwise nothing seems to have changed. When I try to convert .flv to .mp3, I still sometimes get a dead output file on Desktop and several thousand lines of "Unsupported video codec (7)" in terminal. Doesn't "codec (7)" in this error message refer to H.264, or am I barking up the wrong tree?

Now this rings a bell, are these youtube videos? If so there has been a change in youtube recently that has sparked this error message for a few people. Have a look at some of the posts in this thread:

[http://ubuntuforums.org/showthread.php?t=997639](http://ubuntuforums.org/showthread.php?t=997639)

and you will see a mention of this problem a little firther down the page. I note that the fakeoutdoorsman has no problem with a self-compiled ffmpeg.

Can I ask for a link to one of these flv files that is causing trouble and an exact copy of the command line that you are using? This way I can test with both mencoder and ffmpeg and hopefully isolate the problem.

All the best,

  ANdrew

---

### Post by Alfred_McGee on 2008-12-10
Thanks for the very relevant link, Andrew. Playing H.264 flvs has only been a problem with VLC media player. Movieplayer or Mplayer work perfectly. File conversion is the problem.

EDIT: Went to FakeOutdoorsman's thread for self-compiling ffmpeg. Still no conversion of H.264 flvs, but the "Unsupported video codec (7)" message no longer appears. Instead, this:

~$ ffmpeg -i  'Desktop/t.flv' -vn -ac 2 -acodec copy  -y   'Desktop/t.mp3'
FFmpeg version SVN-r16043, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264
  libavutil     49.12. 0 / 49.12. 0
  libavcodec    52. 6. 1 / 52. 6. 1
  libavformat   52.23. 1 / 52.23. 1
  libavdevice   52. 1. 0 / 52. 1. 0
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Dec 10 2008 12:14:34, gcc: 4.3.2

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 29.92 (359/12)
Input #0, flv, from 'Desktop/t.flv':
  Duration: 00:04:24.49, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: h264, yuv420p, 320x214 [PAR 1:1 DAR 160:107], 29.92 tb(r)
    Stream #0.1: Audio: aac, 22050 Hz, stereo, s16
Output #0, mp3, to 'Desktop/tyrant.mp3':
    Stream #0.0: Audio: libfaac, 22050 Hz, stereo, s16
Stream mapping:
  Stream #0.1 -> #0.0
Press [q] to stop encoding
size=    2526kB time=264.94 bitrate=  78.1kbits/s    
video:0kB audio:2526kB global headers:0kB muxing overhead 0.001237%

***The mp3 file produced this way does not play. "Could not determine type of stream," says Totem. 

***Using the above command on an flv file with a codec other than H.264 still works perfectly, however:

~$ ffmpeg -i  'Desktop/a.flv' -vn -ac 2 -acodec copy  -y   'Desktop/a.mp3'
FFmpeg version SVN-r16043, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264
  libavutil     49.12. 0 / 49.12. 0
  libavcodec    52. 6. 1 / 52. 6. 1
  libavformat   52.23. 1 / 52.23. 1
  libavdevice   52. 1. 0 / 52. 1. 0
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Dec 10 2008 12:14:34, gcc: 4.3.2

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 29.92 (359/12)
Input #0, flv, from 'Desktop/a.flv':
  Duration: 00:04:30.31, start: 0.000000, bitrate: 80 kb/s
    Stream #0.0: Video: flv, yuv420p, 320x239, 29.92 tb(r)
    Stream #0.1: Audio: mp3, 22050 Hz, mono, s16, 80 kb/s
Output #0, mp3, to 'Desktop/a.mp3':
    Stream #0.0: Audio: libmp3lame, 22050 Hz, mono, s16, 80 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
Press [q] to stop encoding
size=    2250kB time=270.34 bitrate=  68.2kbits/s    
video:0kB audio:2250kB global headers:0kB muxing overhead 0.001389%

***Any ideas?

---

### Post by FakeOutdoorsman on 2008-12-10
> **Alfred_McGee said:**
> ...

~$ ffmpeg -i  'Desktop/t.flv' -vn -ac 2 -acodec copy  -y   'Desktop/t.mp3'

    Stream #0.0: Video: h264, yuv420p, 320x214 [PAR 1:1 DAR 160:107], 29.92 tb(r)
    Stream #0.1: Audio: aac, 22050 Hz, stereo, s16
Output #0, mp3, to 'Desktop/tyrant.mp3':
    Stream #0.0: Audio: libfaac, 22050 Hz, stereo, s16

***The mp3 file produced this way does not play. "Could not determine type of stream," says Totem.
This command is telling ffmpeg to copy the audio stream into a mp3 container, however the file contains aac audio.  This should do it (you may want to use the -ab option to give an audio bitrate):
```
ffmpeg -i ~/Desktop/t.flv t.mp3
```
> 
***Using the above command on an flv file with a codec other than H.264 still works perfectly, however:

~$ ffmpeg -i  'Desktop/a.flv' -vn -ac 2 -acodec copy  -y   'Desktop/a.mp3'

  Duration: 00:04:30.31, start: 0.000000, bitrate: 80 kb/s
    Stream #0.0: Video: flv, yuv420p, 320x239, 29.92 tb(r)
    Stream #0.1: Audio: mp3, 22050 Hz, mono, s16, 80 kb/s
Output #0, mp3, to 'Desktop/a.mp3':
    Stream #0.0: Audio: libmp3lame, 22050 Hz, mono, s16, 80 kb/s

***Any ideas?

This one works fine because the flv already contains mp3 audio so using 'acodec copy' should work as expected.

---

### Post by Alfred_McGee on 2008-12-10
Thanks, FakeOutdoorsman, that did the trick.:guitar: 

On a slightly different topic, following your howto for a self-compiled ffmpeg seems to have disabled the deluxe version of Mplayer that I installed from the howto at the beginning of this thread. Having ffmpeg now able to handle H.264 is probably worth the price of losing the ability to play 3gp video with sound (the only use for which I've depended on Mplayer so far), but it would be even better not to have to make that trade-off. I have a feeling that Andrew's installation of Mplayer can do a lot of stuff that I don't even know about yet.

---

### Post by FakeOutdoorsman on 2008-12-10
> **Alfred_McGee said:**
> Thanks, FakeOutdoorsman, that did the trick.:guitar: 

On a slightly different topic, following your howto for a self-compiled ffmpeg seems to have disabled the deluxe version of Mplayer that I installed from the howto at the beginning of this thread. Having ffmpeg now able to handle H.264 is probably worth the price of losing the ability to play 3gp video with sound (the only use for which I've depended on Mplayer so far), but it would be even better not to have to make that trade-off. I have a feeling that Andrew's installation of Mplayer can do a lot of stuff that I don't even know about yet.
If you open mplayer from a terminal and try to play something does it give an error message after you followed my guide?  It may have something to do with my guide's lack of adding "--enable-shared" to the x264 compilation configuration.  I keep going back and forth on the enable-shared option, but I'll probably just add it and leave it this time.

---

### Post by Alfred_McGee on 2008-12-10
Looks like you're right about the problem with your home-brewed ffmpeg, FakeOutdoorsman. Here's what I got when I tried to run mplayer:

$mplayer /Desktop/test.3gp
mplayer: error while loading shared libraries: libx264.so.65: cannot open shared object file: No such file or directory

Oh- about the -ab setting that you mentioned: the default value seems to work perfectly. Just for future reference, do you have any idea what it is?

---

### Post by FakeOutdoorsman on 2008-12-10
> **Alfred_McGee said:**
> Looks like you're right about the problem with your home-brewed ffmpeg, FakeOutdoorsman. Here's what I got when I tried to run mplayer:

$mplayer /Desktop/test.3gp
mplayer: error while loading shared libraries: libx264.so.65: cannot open shared object file: No such file or directory
Remove x264:
```
sudo apt-get purge x264
cd ~/x264
make distclean
```
Then recompile it following Andrew's instructions.
> Oh- about the -ab setting that you mentioned: the default value seems to work perfectly. Just for future reference, do you have any idea what it is?
Default audio bitrate for ffmpeg is 64 kb/s.  If that is too low you can change it: -ab 128k or -ab 192k or any other number.  If you use "acodec copy" you won't need to declare a bitrate.

---

### Post by andrew.46 on 2008-12-10
Hi Alfred,

You certainly get a copy of ffmpeg when you install the svn MPlayer but the downside is often that the MPlayer encoder Mencoder can be a little limited at times in manipulating and converting files. For this reason I keep a copy of both at hand. 

If you are interested in amr and have compiled according to the instructions in my guide you can of course compile ffmpeg against these libraries as I have done myself:

```
andrew@skamandros:~$ ffmpeg -formats | grep amr
FFmpeg version SVN-r16010, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --prefix=/usr --enable-gpl --enable-nonfree --enable-postproc 
--enable-pthreads --enable-libamr-nb --enable-libamr-wb 
--enable-libmp3lame --enable-libschroedinger --enable-libx264 
--enable-libxvid --enable-libfaac
  libavutil     49.12. 0 / 49.12. 0
  libavcodec    52. 6. 0 / 52. 6. 0
  libavformat   52.23. 1 / 52.23. 1
  libavdevice   52. 1. 0 / 52. 1. 0
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Dec  6 2008 09:19:26, gcc: 4.3.2
 DE amr             3GPP AMR file format
 DEA    libamr_nb       libamr-nb Adaptive Multi-Rate (AMR) Narrow-Band
 DEA    libamr_wb       libamr-wb Adaptive Multi-Rate (AMR) Wide-Band

```

All the best,

  Andrew

---

### Post by Alfred_McGee on 2008-12-11
Hi Andrew. Your post raises many questions in my fragile little newbie mind, and that's a good thing, but at the moment, now that I've got H.264 support, and got svn Mplayer working again, there's nothing urgent. I did compile Mplayer according to your instructions at the start of this thread. I don't know how much the libraries you now mention would add to what I have, but here's how it looks right now:

$ ffmpeg -formats | grep amr
FFmpeg version SVN-r16043, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264
  libavutil     49.12. 0 / 49.12. 0
  libavcodec    52. 6. 1 / 52. 6. 1
  libavformat   52.23. 1 / 52.23. 1
  libavdevice   52. 1. 0 / 52. 1. 0
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Dec 10 2008 12:14:34, gcc: 4.3.2
 DE amr             3GPP AMR file format

---

### Post by andrew.46 on 2008-12-11
Hi Alfred,

> **Alfred_McGee said:**
> Hi Andrew. Your post raises many questions in my fragile little newbie mind, and that's a good thing, but at the moment, now that I've got H.264 support, and got svn Mplayer working again, there's nothing urgent. 

I am not so sure that you can call yourself a newbie any more since you have successfully compiled 2 fairly difficult programs from source :-).

> I did compile Mplayer according to your instructions at the start of this thread. I don't know how much the libraries you now mention would add to what I have, but here's how it looks right now:

$ ffmpeg -formats | grep amr
FFmpeg version SVN-r16043, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264
  libavutil     49.12. 0 / 49.12. 0
  libavcodec    52. 6. 1 / 52. 6. 1
  libavformat   52.23. 1 / 52.23. 1
  libavdevice   52. 1. 0 / 52. 1. 0
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Dec 10 2008 12:14:34, gcc: 4.3.2
 DE amr             3GPP AMR file format

Since you have already installed the amr libraries for MPlayer just add the following two options to your ffmpeg ./configure next time you update:

```
--enable-libamr-wb --enable-libamr-nb
```

You may very well be prompted to add --enable-nonfree as well.

All the best,

  Andrew

---

### Post by gardara on 2008-12-11
I'm trying to set up x264 but I'm getting this:

```
 trying to overwrite `/usr/include/x264.h', which is also in package libx264-dev
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/gardar/x264/x264_1:0.svn20081212-0.0ubuntu1-1_i386.deb

```

Edit: nvm, I uninstalled libx264-dev and then it worked!


Edit2: Another thing I came across

```
libdca-dev: Conflicts: libdts-dev but 0.0.2-svn-2ubuntu1 is to be installed
```
any ideas what's wrong?

---

### Post by andrew.46 on 2008-12-12
Hi,

Thanks for your message:

> **gardara said:**
> Edit: nvm, I uninstalled libx264-dev and then it worked!

I have added a step to specify this action *before* installing x264 from git, something I should have done a while ago :-).

> Edit2: Another thing I came across

```
libdca-dev: Conflicts: libdts-dev but 0.0.2-svn-2ubuntu1 is to be installed
```
any ideas what's wrong?

Yes, I have taken out libdca temporarily but this should represent a newer version of libdts so it should really be the other way. Have a look at:

[http://lists.mplayerhq.hu/pipermail/mplayer-users/2007-April/066635.html](http://lists.mplayerhq.hu/pipermail/mplayer-users/2007-April/066635.html)

I shall have to have a closer look at this over the weekend and see what MPlayer is picking up in the configure process. Thanks for that!

All the best,

  Andrew

---

### Post by mad_max0204 on 2008-12-12
There is no libglide2 available for ibex. Change that to libglide3 so people dont get errors when copy pasting :)

---

### Post by andrew.46 on 2008-12-13
Hi mad_max,

> **mad_max0204 said:**
> There is no libglide2 available for ibex. Change that to libglide3 so people dont get errors when copy pasting :)

That particular file is dragged in as a dependency of another file and I now forget exactly which one :-). All curses on the debian system of packaging!

However the file is available under Intrepid Ibex, I have just installed this version from scratch and on a clean install:

```
andrew@skamandros:~$ apt-cache search libglide2 
libggi-target-glide - General Graphics Interface Glide2 display target
libglide2 - graphics library for 3Dfx Voodoo based cards - shared libraries
libglide2-dev - graphics library for 3Dfx Voodoo based cards - development files

```

BTW I only just now appreciated how easy this guide makes a reinstall of the svn mplayer, having used it for exactly this purpose! Coming up to 70,000 views soon: still waiting or a free T-shirt :-)

  Andrew

---

### Post by costre on 2008-12-14
I tried to install mplayer using this guide about six months ago. I was quite new to Ubuntu back then, and I remember something went wrong. I gave it a new go today, and I realized the same thing happened.

Using VLC, all I have to do to activate 5.1 surround sound is to click audio -> audio device -> 5.1_Surround

Using Mplayer, it's absolutely impossible. It's bad enough I have to enter the preferences, go to the audio tab and mess around with drop down menus. When done, the video starts to freeze, the audio starts to studder, and/or error messages appear once every frame. The quality and messages seem to differ a bit dependent on exactly what I select in the audio menu. 

So, all in all, it seems it's back to VLC for me, yet again. No complaints though, I like VLC :)

The only thing VLC is a bit bad at is 1080p video. It has a tendency to freeze or lag behind during heavy scenes. Not all the time, but it happens once in a while. 

Is there a quick fix, like dual graphics cards, or faster CPU? Intel vs AMD perhaps? Or should it be possible to play fluently if I mess around with codecs? 

AFAIK there are HTPC's claiming to play 1080p using weaker hardware than I am using ...

---

### Post by psychok9 on 2008-12-15
How can I enable all standard audio output and options? Source file of alsa, pulse, etc are request? Can you help me? Thank you.

My os is Ubuntu 8.10 x86_64 (Q6600 cpu).

---

### Post by andrew.46 on 2008-12-16
Hi,

Most audio outputs should be enabled in the guide, this is done by downloading and compiling against the appropriate -dev files. To see what is available to you try:

**For MPlayer:**

```
andrew@skamandros:~$ mplayer -ao help
MPlayer dev-SVN-r28145-4.3.2 (C) 2000-2008 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz (Family: 6, Model: 15, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
Available audio output drivers:
	oss	OSS/ioctl audio output
	alsa	ALSA-0.9.x-1.x audio output
	arts	aRts audio output
	esd	EsounD audio output
	pulse	PulseAudio audio output
	jack	JACK audio output
	nas	NAS audio output
	sdl	SDLlib audio output
	openal	OpenAL audio output
	mpegpes	DVB audio output
	v4l2	V4L2 MPEG Audio Decoder output
	null	Null audio output
	pcm	RAW PCM/WAVE file writer audio output

```

**For Mencoder:**

```
andrew@skamandros:~$ mencoder -oac help
MEncoder dev-SVN-r28145-4.3.2 (C) 2000-2008 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz (Family: 6, Model: 15, Stepping: 2)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2


Available codecs:
   copy     - frame copy, without re-encoding (useful for AC3)
   pcm      - uncompressed PCM audio
   mp3lame  - cbr/abr/vbr MP3 using libmp3lame
   lavc     - FFmpeg audio encoder (MP2, AC3, ...)
   twolame  - Twolame MP2 audio encoder
   faac     - FAAC AAC audio encoder

```

All the best,

  Andrew

---

### Post by andrew.46 on 2008-12-18
Hi,

I have some reasonably radical plans for this guide when Jaunty Jackalope comes into beta on March 26th 2009. The highlights are:

[LIST=1]
[*]This version of the guide ended and Jaunty Jackalope will have its own individual guide and thread. It is becoming a little unwieldy trying to juggle different Ubuntu releases on the same page.
[*]I will no longer include the X -dev files and build the gmplayer. I will advocate the smplayer instead. Development of the gmplayer has been abandoned and many faults remain. smplayer is actively developed and IMHO is a fine piece of work.
[*]amr compiling will be omitted. Not many people use it and I am trying to cut out a little complexity.
[*]I will add details for installing the mplayer plugin. This gives MPlayer a presence in the browser and has been requested a few times.
[/LIST]

I am keen to get some feedback on these plans and any suggestions for improvements in other areas. I will install the Jaunty Jackalope beta when it comes out and test the new guide, so it will be in place early April = plenty of time for suggestions :-).

Andrew

---

### Post by piemaster89 on 2008-12-18
I followed this installation almost step by step on a clean install of 8.10 except for the installation of libglide2 package. It is currently unavailable from the Ubuntu repository. libglide2-dev is available but I installed libglide3 instead. I doubt this is the source of the problem but it just might be.

I am also having the same problems as costre. Videos have an error message on almost every frame and it is impossible to watch anything. 

At the moment, my workaround is to use VLC :(

---

### Post by andrew.46 on 2008-12-18
Hi,

Sorry this guide has caused you trouble!

> **piemaster89 said:**
> I followed this installation almost step by step on a clean install of 8.10 except for the installation of libglide2 package. It is currently unavailable from the Ubuntu repository. libglide2-dev is available but I installed libglide3 instead. I doubt this is the source of the problem but it just might be.

I am not sure about this phantom libglide but I suspect that it has to go as too many people are mentioning problems with it. Tomorrow I shall remove it from my own system, recompile and see if anything is broken :-).

> I am also having the same problems as costre. Videos have an error message on almost every frame and it is impossible to watch anything. 

At the moment, my workaround is to use VLC :(

VLC is a great program and I am glad you have a backup while there is a problem with MPlayer. Can you do me a favour, can you play a movie that is giving you trouble from the commandline using the syntax:

```
mplayer -v [COLOR="Red"]**mymovie**[/COLOR]
```

Obviously substituting your own file for 'mymovie'. Copy and paste the entire output including the command into a message here on the forum and there may be a hint there.

All the best,

  Andrew

---

### Post by andrew.46 on 2008-12-18
Hi,

I have adjusted the dev files for Intrepid Ibex and re-compiled without any problems. Unless these files are used elsewhere on your system you can remove:

```
$ sudo apt-get remove libggi-target-x libggi2 libggi2-dev libggimisc2 \
libggimisc2-dev libggiwmh0 libggiwmh0-dev libggiwmh0-target-x libglide2
```

and recompiled. All is well on my system with MPlayer, hopefully on yours as well :-).

Andrew

---

### Post by piemaster89 on 2008-12-18
> **andrew.46 said:**
> Hi,

Sorry this guide has caused you trouble!



I am not sure about this phantom libglide but I suspect that it has to go as too many people are mentioning problems with it. Tomorrow I shall remove it from my own system, recompile and see if anything is broken :-).



VLC is a great program and I am glad you have a backup while there is a problem with MPlayer. Can you do me a favour, can you play a movie that is giving you trouble from the commandline using the syntax:

```
mplayer -v [COLOR="Red"]**mymovie**[/COLOR]
```


Hmm, so running it from the command line works great on avi files but right clicking doesn't work and I have no way of changing subtitles or audio stream or any of that good stuff on mkv files.

```

wilson@GIR:~/Dropbox$ mplayer -v \[Doremi-OTOME\].Mai-Otome.0.S.ifr.03.\[D7B4F17F\].avi 
MPlayer dev-SVN-r28162-4.3.2 (C) 2000-2008 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz (Family: 6, Model: 15, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
get_path('codecs.conf') -> '/home/wilson/.mplayer/codecs.conf'
Reading /home/wilson/.mplayer/codecs.conf: Can't open '/home/wilson/.mplayer/codecs.conf': No such file or directory
Reading /usr/local/etc/mplayer/codecs.conf: Can't open '/usr/local/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
Configuration: --enable-gui
CommandLine: '-v' '[Doremi-OTOME].Mai-Otome.0.S.ifr.03.[D7B4F17F].avi'
init_freetype
get_path('font/font.desc') -> '/home/wilson/.mplayer/font/font.desc'
font: can't open file: /home/wilson/.mplayer/font/font.desc
font: can't open file: /usr/local/share/mplayer/font/font.desc
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/wilson/.mplayer/fonts'
Using nanosleep() timing
get_path('input.conf') -> '/home/wilson/.mplayer/input.conf'
Can't open input config file /home/wilson/.mplayer/input.conf: No such file or directory
Can't open input config file /usr/local/etc/mplayer/input.conf: No such file or directory
Falling back on default (hardcoded) input config
get_path('[Doremi-OTOME].Mai-Otome.0.S.ifr.03.[D7B4F17F].avi.conf') -> '/home/wilson/.mplayer/[Doremi-OTOME].Mai-Otome.0.S.ifr.03.[D7B4F17F].avi.conf'

Playing [Doremi-OTOME].Mai-Otome.0.S.ifr.03.[D7B4F17F].avi.
get_path('sub/') -> '/home/wilson/.mplayer/sub/'
[file] File size is 230959104 bytes
STREAM: [file] [Doremi-OTOME].Mai-Otome.0.S.ifr.03.[D7B4F17F].avi
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
LAVF_check: AVI format
AVI file format detected.
list_end=0x2292
======= AVI Header =======
us/frame: 41708  (fps=23.976)
max bytes/sec: 0
padding: 0
MainAVIHeader.dwFlags: (272) HAS_INDEX IS_INTERLEAVED
frames  total: 39097   initial: 0
streams: 2
Suggested BufferSize: 0
Size:  848 x 480
==========================
list_end=0x10F4
==> Found video stream: 0
[aviheader] Video stream found, -vid 0
====== STREAM Header =====
Type: vids   FCC: xvid (64697678)
Flags: 0
Priority: 0   Language: 0
InitialFrames: 0
Rate: 10000000/417083 = 23.976
Start: 0   Len: 39097
Suggested BufferSize: 73684
Quality 10000
Sample size: 0
==========================
Found 'bih', 40 bytes of 40
======= VIDEO Format ======
  biSize 40
  biWidth 848
  biHeight 480
  biPlanes 1
  biBitCount 24
  biCompression 1145656920='XVID'
  biSizeImage 2442240
===========================
Regenerating keyframe table for MPEG-4 video.
list_end=0x2186
==> Found audio stream: 1
[aviheader] Audio stream found, -aid 1
====== STREAM Header =====
Type: auds   FCC:  (0)
Flags: 0
Priority: 0   Language: 0
InitialFrames: 1
Rate: 16000/1 = 16000.000
Start: 0   Len: 26090266
Suggested BufferSize: 8000
Quality -1
Sample size: 1
==========================
Found 'wf', 30 bytes of 18
======= WAVE Format =======
Format Tag: 85 (0x55)
Channels: 2
Samplerate: 44100
avg byte/sec: 16000
Block align: 1
bits/sample: 0
cbSize: 12
mp3.wID=1
mp3.fdwFlags=0x0
mp3.nBlockSize=418
mp3.nFramesPerBlock=1
mp3.nCodecDelay=0
==========================================================================
list_end=0x2292
AVI: dmlh found (size=248) (total_frames=39097)
list_end=0x22D2
hdr=Software  size=44
Software  : VirtualDubMod 1.5.10.2 (build 2540/release)
list_end=0xDB10B80
Found movie at 0x280C - 0xDB10B80
Reading INDEX block, 78183 chunks for 39097 frames (fpos=229706632).
AVI index offset: 0x2808 (movi=0x280C idx0=0x4 idx1=0x1F4C)
Auto-selected AVI audio ID = 1
Auto-selected AVI video ID = 0
AVI: Searching for audio stream (id:1)
AVI video size=202928302 (39097) audio size=26090266 (26090266)
VIDEO:  [XVID]  848x480  24bpp  23.976 fps  995.6 kbps (121.5 kbyte/s)
Auto-selected AVI audio ID = 1
[V] filefmt:3  fourcc:0x44495658  size:848x480  fps:23.976  ftime:=0.0417
Clip info:
 Software: VirtualDubMod 1.5.10.2 (build 2540/release)
get_path('sub/') -> '/home/wilson/.mplayer/sub/'
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
[xv common] Maximum source image dimensions: 1920x1088
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
INFO: libavcodec init OK!
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
dec_audio: Allocating 4608 + 65536 = 70144 bytes for output buffer.
mp3lib: using SSE optimized decore!
MP3lib: init layer2&3 finished, tables done
MPEG 1.0, Layer III, 44100 Hz 128 kbit Stereo, BPF: 417
Channels: 2, copyright: No, original: Yes, CRC: No, emphasis: 0
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
Building audio filter chain for 44100Hz/2ch/s16le -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 44100Hz/2ch/s16le
[dummy] Was reinitialized: 44100Hz/2ch/s16le
Trying every known audio driver...
ao2: 44100 Hz  2 chans  s16le
audio_setup: using '/dev/dsp' dsp device
audio_setup: using '/dev/mixer' mixer device
audio_setup: using 'pcm' mixer device
[AO OSS] audio_setup: Can't open audio device /dev/dsp: Device or resource busy
alsa-init: requested format: 44100 Hz, 2 channels, 9
alsa-init: using ALSA 1.0.17a
alsa-init: setup for 1/2 channel(s)
alsa-init: using device default
alsa-init: pcm opened in blocking mode
alsa-init: chunksize set to 1024
alsa-init: fragcount=16
alsa-init: got buffersize=65536
alsa-init: got period size 1024
alsa: 44100 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 44100Hz 2ch s16le (2 bytes per sample)
AO: Description: ALSA-0.9.x-1.x audio output
AO: Author: Alex Beregszaszi, Zsolt Barat <joy@streamminister.de>
AO: Comment: under developement
Building audio filter chain for 44100Hz/2ch/s16le -> 44100Hz/2ch/s16le...
[dummy] Was reinitialized: 44100Hz/2ch/s16le
[dummy] Was reinitialized: 44100Hz/2ch/s16le
Starting playback...
Increasing filtered audio buffer size from 0 to 65536
[mpeg4 @ 0xd05220]Invalid and inefficient vfw-avi packed B frames detected
[ffmpeg] aspect_ratio: 1.766667
VDec: vo config request - 848 x 480 (preferred colorspace: Planar YV12)
Trying filter chain: vo
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.77:1 - prescaling to correct movie aspect.
VO Config (848x480->848x480,flags=0,'MPlayer',0x32315659)
VO: [xv] 848x480 => 848x480 Planar YV12 
VO: Description: X11/Xv
VO: Author: Gerd Knorr <kraxel@goldbach.in-berlin.de> and others
Xvideo image format: 0x32595559 (YUY2) packed
Xvideo image format: 0x32315659 (YV12) planar
Xvideo image format: 0x30323449 (I420) planar
Xvideo image format: 0x59565955 (UYVY) packed
Xvideo image format: 0x434d5658 (XVMC) planar
using Xvideo port 68 for hw scaling
[xv] dx: 0 dy: 0 dw: 848 dh: 480
*** [vo] Allocating (slices) mp_image_t, 848x480x12bpp YUV planar, 610560 bytes
XXX initial  v_pts=0.000  a_pos=8000 (0.500)   1 ??% ??% ??,?% 0 0 
*** [vo] Allocating (slices) mp_image_t, 848x480x12bpp YUV planar, 610560 bytes
get_path('subfont.ttf') -> '/home/wilson/.mplayer/subfont.ttf'
Unicode font: 255 glyphs.
get_path('subfont.ttf') -> '/home/wilson/.mplayer/subfont.ttf'
Unicode font: 255 glyphs.

```

Also, regarding the extra packages that you are now removing, should I try to remove them now?

Thanks for all your help!


EDIT: I did a little more testing and I think the trouble arises when the GUI is enabled.

```

$ mplayer -gui -v Chuck.S01E03.Chuck.Versus.The.Tango.avi 
MPlayer dev-SVN-r28162-4.3.2 (C) 2000-2008 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz (Family: 6, Model: 15, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
The -gui option will only work as the first command line argument.

Playing /media/Fat Nigger/TV/Chuck Season 1/Chuck.S01E03.Chuck.Versus.The.Tango.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  624x352  24bpp  23.976 fps  1009.3 kbps (123.2 kbyte/s)
Clip info:
 Software: cant touch this
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
[AO OSS] audio_setup: Can't open audio device /dev/dsp: Device or resource busy
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
[AO_ALSA] Unable to find simple control 'PCM',0.
Starting playback...
VDec: vo config request - 624 x 352 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.77:1 - prescaling to correct movie aspect.
VO: [xv] 624x352 => 624x352 Planar YV12 
[AO_ALSA] Unable to find simple control 'PCM',0. ??% ??% ??,?% 1 0              
[AO_ALSA] Unable to find simple control 'PCM',0. ??% ??% ??,?% 2 0              
[AO_ALSA] Unable to find simple control 'PCM',0. ??% ??% ??,?% 3 0              
[AO_ALSA] Unable to find simple control 'PCM',0. ??% ??% ??,?% 3 0              
[AO_ALSA] Unable to find simple control 'PCM',0. ??% ??% ??,?% 4 0              
[AO_ALSA] Unable to find simple control 'PCM',0. ??% ??% ??,?% 4 0              
[AO_ALSA] Unable to find simple control 'PCM',0. ??% ??% ??,?% 4 0              
[AO_ALSA] Unable to find simple control 'PCM',0. ??% ??% ??,?% 4 0              
[AO_ALSA] Unable to find simple control 'PCM',0. ??% ??% ??,?% 4 0              
[AO_ALSA] Unable to find simple control 'PCM',0. ??% ??% ??,?% 4 0              
[AO_ALSA] Unable to find simple control 'PCM',0. ??% ??% ??,?% 4 0              
[AO_ALSA] Unable to find simple control 'PCM',0. ??% ??% ??,?% 4 0

```

It just continues like this for every error.

---

### Post by andrew.46 on 2008-12-18
Hi piemaster,

I would not worry about the extra packages as I suspect this is peripheral to your trouble with MPlayer. It is excellent news that that the commandline player works and it seems that the gui is the problem. The gmplayer has been almost completely abandoned by the MPlayer developers and will be also by this guide when Jaunty Jackalope comes along.

Can I suggest that if you have not already done so you recompile using the checkinstall syntax I have suggested:

```
$ cd $HOME/mplayer
$ make clean
$ svn update
$ ./configure --enable-gui
$ make
$  sudo checkinstall -D --install=yes --fstrans=no --pakdir "$HOME/Desktop" \
--maintainer "$USER" --pkgname mplayer --pkgversion "3:1.0~svn" \
--backup=no --deldoc=yes --deldesc=yes --delspec=yes --gzman
$ make clean
```

In the next version of this guide the '--enable-gui' option will be gone, you might try this if you want or perhaps leave it in place for the moment. The checkinstall syntax I suggest means that the repository will never overwrite your svn MPlayer with its older one.

Then simply install smplayer from the repository:

```
$ sudo apt-get install smplayer
```

smplayer is a little *more* than a simple front-end but it certainly uses the MPlayer engine and incorporates it into a beautiful and easily used gui. There will be some qt dependencies but the download will not be excessive. (smplayer + MPlayer is my own setup and it works well.)

Then again run your video, having first crossed your fingers :-).

  Andrew

---

### Post by piemaster89 on 2008-12-18
Andrew,

Thanks a lot. I have smplayer installed now and the videos run correctly. However, I still have a few minor problems. Sometimes the video doesn't update when I use the seek bar. Additionally, the softsubs don't display in the correct font, just a generic font from the player. I realize that I can pick a font in the preferences but the video file has styled subs.

These are minor issues that I can live with even if they go unsolved. I look forward to your next guide for Jaunty :)

---

### Post by gardara on 2008-12-18
Is there a special reason why you choose gmplayer rather than smplayer?
In my option, smplayer is much nicer...
Maby adding instructions of getting svn smplayer into the guide is a good idea?
It's actually not hard, just skip the skin and "enable gui" steps and then catch smplayer svn and compile it.

---

### Post by andrew.46 on 2008-12-18
Hi gardara,

> **gardara said:**
> Is there a special reason why you choose gmplayer rather than smplayer?
In my option, smplayer is much nicer...

I agree. This guide was originally written over a year ago and at that time I wanted to demonstrate how to install the 'complete' MPlayer package. Now I am a little more experienced and have read the mplayer-users list for some time I realise that this goal was perhaps a little foolish and even misconceived.

>  Maby adding instructions of getting svn smplayer into the guide is a good idea?
It's actually not hard, just skip the skin and "enable gui" steps and then catch smplayer svn and compile it.

I do not intend adding to this guide after the beta release of Jaunty and in fact at that time I will write a new guide that omits skin and gmplayer completely and adds in the smplayer. I had not really considered using the svn smplayer but rather the repository version. That would of course not stop anyone who wanted to write a guide for compiling the svn smplayer :-).

All the best,

  Andrew

---

### Post by pedja_portugalac on 2008-12-24
Andrew Thank You very much.

Yesterday I didn't sleep much because of problems installing svn mplayer from source. This morning following your howto, on interpid, I installed it in 30 minutes and now I have the latest mplayer. This is the best howto I have found about svn mplayer compilation and it should be in official media page. 

Thanks ones again and Mary Christmas to You

---

### Post by andrew.46 on 2008-12-24
Hi pedja,

Thanks for your kind post,

> **pedja_portugalac said:**
> Yesterday I didn't sleep much because of problems installing svn mplayer from source. This morning following your howto, on interpid, I installed it in 30 minutes and now I have the latest mplayer. This is the best howto I have found about svn mplayer compilation and it should be in official media page. 

Thanks again! The guide has kept me busy for a year or so now and I am looking forward to writing a brand new version for Jaunty when it comes. This guide will however never make it to 'official' status as it installs codecs that are not officially sanctioned by Ubuntu as well as installing libdvdcss which is not officially recognised by Ubuntu. Such a guide as mine definitely has a place but perhaps not an *official* place :-).

> Thanks ones again and Mary Christmas to You

And a Merry Christmas or you and your family as well, and best wishes for the New Year.

All the best,

Andrew

---

### Post by andrew.46 on 2008-12-29
Hi,

I have put a new version of the guide in place for Intrepid Ibex:

[Howto] Install the svn Mplayer under Intrepid Ibex
[http://ubuntuforums.org/showthread.php?t=1024592](http://ubuntuforums.org/showthread.php?t=1024592)

The new guide is considerably improved on the current effort. It integrates all the installed software under the package management system, utilises the Medibuntu Repository for the first time, deals with manually installing the newest Live555 libraries and has abandoned the gmplayer for SMPlayer.

Look forward to seeing you there !!

All the best,

Andrew Strong

---

### Post by napauleon on 2009-01-06
First of all: a great guide for installing mplayer from svn :D

The only thing i cant get my head around is lirc support. When using mplayer from the package tree, lirc works fine.

However i needed some extra's for my 1080p video's (coreavc), which runs very nice now. However i can't get lirc to work with the latest svn release of mplayer (dev-SVN-r28274-4.2.4).

when I run ./configure it shows that it found a positive lookup for --enable-lirc (not for --enable-lircc) and it compiles fine when running make.
However lirc is not loaded when running mplayer. I've got all the necessary lirc packages installed i guess.

Any ideas on getting lirc to work with the svn release of mplayer?

---

### Post by andrew.46 on 2009-01-06
Hi napauleon,

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

### Post by andrew.46 on 2009-03-26
Hi,

Well, a major rewrite, new title and a change of focus to this guide. I am running Hardy on VirtualBox now and quite prepared to support the guide until 2011. Gutsy has gone I am afraid and with the impending '-end-of-life' it might be a good idea to move on from it anyway :-). Any problems with the new version of this guide please leave me a note. On my new Hardy install it is all running beautifully!

Andrew

---

### Post by Roanoke on 2009-03-28
I got an error during mplayer compilation.
```

(Reading database ... 206459 files and directories currently installed.)
Preparing to replace mplayer 2:1.0~rc2-0ubuntu17 (using .../mplayer_3:1.0~svn-1_i386.deb) ...
Unpacking replacement mplayer ...
dpkg: error processing /home/roanoke/mplayer/mplayer_3:1.0~svn-1_i386.deb (--install):
 trying to overwrite `/usr/bin/mencoder', which is also in package mencoder
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/roanoke/mplayer/mplayer_3:1.0~svn-1_i386.deb

```

---

### Post by andrew.46 on 2009-03-28
Hi Roanoke,

> **Roanoke said:**
> I got an error during mplayer compilation.
```

(Reading database ... 206459 files and directories currently installed.)
Preparing to replace mplayer 2:1.0~rc2-0ubuntu17 (using .../mplayer_3:1.0~svn-1_i386.deb) ...
Unpacking replacement mplayer ...
dpkg: error processing /home/roanoke/mplayer/mplayer_3:1.0~svn-1_i386.deb (--install):
 trying to overwrite `/usr/bin/mencoder', which is also in package mencoder
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/roanoke/mplayer/mplayer_3:1.0~svn-1_i386.deb

```

This is a problem that I have not come to grips with yet. Ubuntu splits MPlayer into a few pieces and then installs them separately while my guide does not. A short term solution is to compile the svn MPlayer *without* Mencoder by adding the following to the configure string:

```
--disable-mencoder
```

I suspect that the repository Mencoder has been installed for the benefit of some other ripping / transcoding program. Doing it this way will be the safest and you will still get to use the latest MPlayer :-).

Andrew

---

### Post by mocha on 2009-03-28
This is the same problem on Intrepid as you mentioned andrew.46  What I do is first uninstall mencoder from the repo, then compile mplayer/mencoder.  Then you can allow whatever other package that needs mencoder as a dependancy to install it from the repo.  The repo version goes into /usr/bin but your compiled version is already in /usr/local/bin, so it will always take precedence.

---

### Post by Roanoke on 2009-03-28
Yes, that worked, thank you :)

---

### Post by andrew.46 on 2009-03-28
Hi mocha,

> **mocha said:**
> This is the same problem on Intrepid as you mentioned andrew.46  What I do is first uninstall mencoder from the repo, then compile mplayer/mencoder.  Then you can allow whatever other package that needs mencoder as a dependancy to install it from the repo.  The repo version goes into /usr/bin but your compiled version is already in /usr/local/bin, so it will always take precedence.

Thanks for that. I have removed the --prefix setting which was causing some of the trouble.

Andrew

---

### Post by white_hat on 2009-05-01
Hi all!
I've just compiled latest mplayer with multi-threaded h.264 support. It's easier then in this guide, just:
```

1. $ sudo apt-get install build-essential checkinstall subversion git-core libgpac-dev yasm
2. $sudo apt-get build-dep mplayer mencoder
3. $ git clone git://repo.or.cz/mplayer && cd mplayer && git checkout origin/mt && git submodule init && git submodule update && ./configure && make && sudo make install 
```That's all! Now 1080 movies can be smoothly played on my 1.3Ghz c2d without dropped frames :guitar:

$mplayer -benchmark -lavdopts threads=2 somemovie.mkv

---

### Post by logos34 on 2009-05-26
> **jmrichky said:**
> The guide worked perfect for me.  It has played every file I have thrown at flawlessly.  Note that since I am using the 64-bit version of Ubuntu, I needed to:
```
$ wget http://www.mplayerhq.hu/MPlayer/releases/codecs/essential-amd64-20061203.tar.bz2
```
Instead of:
```
$ wget http://www.mplayerhq.hu/MPlayer/releases/codecs/all-20061022.tar.bz2
```

I do have one question though.  How can I get mplayer to play embedded video in Firefox?  When I try to install the plugin through apt, it wants to install mplayer from the repos as well.  I am afraid it will replace the shiny new version that I just built.



> **andrew.46 said:**
> Hi,

 You echo my own question:


 I am a little puzzled with this one too and have been racking my brains for a solution. Any ideas anybody else?

 Good to hear it all worked well for you though. I had no idea that there were different codecs for 64bit: you live and learn :-)

                 Andrew

I too need to install on x64 Hardy (mainly for wmv3+wmapro support), but I don't want to screw up embedded audio and video in Firefox.  Has this issue been resolved?

(and, yes, I saw post #368.  Still not clear on workaround)

Right now for wmv3+wmapro soundtrack I'm using 

> ffplay -fs video.wmv

nice full screen + audio track, but pretty spartan (no menu options).  Would be nice to get one of the fully-featured players to work

---

### Post by andrew.46 on 2009-05-26
Hi logos34,

> **logos34 said:**
> I too need to install on x64 Hardy (mainly for wmv3+wmapro support), but I don't want to screw up embedded audio and video in Firefox.  Has this issue been resolved?

I feel a little bit bad about 64 bit MPlayer, vdpau, FFmpeg-MT and a few others as I only really write guides for technology that I am *personally* using and none of these will be featuring in my computer world in the near future. Hopefully there will be some 64 bit users out there with some experience with this issue?

All the best,

Andrew

---

### Post by logos34 on 2009-05-26
> **andrew.46 said:**
> I feel a little bit bad about 64 bit MPlayer, vdpau, FFmpeg-MT and a few others as I only really write guides for technology that I am *personally* using and none of these will be featuring in my computer world in the near future. Hopefully there will be some 64 bit users out there with some experience with this issue?

hey, can't cover everything! Your guide has helped a lot of people as far as it goes...I suspect I'll have to compile the mplayerplug-in as well...but I've already got a head start on the ffmpeg-related stuff (+ x264, etc)...mc4man mentioned something in another mplayer thread about a patch for x64, I'll have to pm him about that.  Stumbling around in the dark for a way to get this all to work on x64...it's really amazing that it's so hard to get video+audio support for wmv3/wmapro!

thanks


**Update:**

How I got mine to work on x64 8.04 Heron:

Used **--disable-mencoder** option.  I found it much easier to simply go with the standalone Medibuntu mencoder, which several dvd rip apps have as a dependency.  

Added **wma pro** audio codec support following mc4man's invaluable instructions [here]("http://ubuntuforums.org/showpost.php?p=7351561&postcount=22").

I'm using skins instead of smplayer or gmplayer gui, so I needed to use the **--enable-gui** configure option AND copy my old skins from /usr/share/mplayer/skins/ to /usr/**local**/share/mplayer/skins before it would *even launch*.

in short,

> ./configure --enable-gui --disable-mencoder --codecsdir=/usr/lib/codecs --confdir=/etc/mplayer

The stock **mozilla-mplayer** FF plugin works fine with my SVN mplayer build on 64-bit Swiftweasel browser (2.0.0.1.4).  Thought I might have to compile that too.

Development packages/build-deps: put in a combination of those Andrew.46 listed on the first page, plus others that another x64 user posted somewhere else in this thread, plus the output of apt-get build-dep mplayer. Overkill, I'm sure, but it worked.

---

### Post by whozai_min on 2009-05-30
hello...i cannot play any video in smplayer..i also got this error msg

Warning unknown option stop-xscreensaver at line 129
Unknown option on the command line:-stop-xscreensaver

how should i do..

sorry if my english bad

---

### Post by andrew.46 on 2009-05-30
Hi whozai_min,

> **whozai_min said:**
> hello...i cannot play any video in smplayer..i also got this error msg

```
Warning unknown option stop-xscreensaver at line 129
Unknown option on the command line:-stop-xscreensaver
```


Do you get the same error message from the commandline:

```
mplayer myfile.avi
```

Could you run the command above, substituting 'myfile.avi' for your own file and post the full terminal output here?

Andrew

---

### Post by logos34 on 2009-05-30
Is there a way to fix this:

> mplayer music2/Trio\ Beyond/Saudades\ \(Disc\ 1\)/02\ -\ As\ One.ogg 

mplayer: could not connect to socket
mplayer: No such file or directory

the file begins playback fine, but why the error mess.?

---

### Post by whozai_min on 2009-05-30
**from the terminal**

root@whozai-laptop:/media/ZIEOS# mplayer bess.avi
Warning unknown option stop-xscreensaver at line 129
MPlayer SVN-r29330-4.2.4 (C) 2000-2009 MPlayer Team

Playing bess.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
AVI: ODML: Building ODML index (2 superindexchunks).
VIDEO:  [xvid]  208x156  0bpp  29.970 fps  216.3 kbps (26.4 kbyte/s)
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Forced audio codec: mad
Requested audio codec family [mad] (afm=libmad) not available.
Enable it at compilation.
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 16000 Hz, 2 ch, s16le, 32.0 kbit/6.25% (ratio: 4000->64000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
No such audio driver 'pulse'
No such audio driver 'alsa'
AO: [oss] 16000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A: 357.5 (05:57.4) of 2818.6 (46:58.5)  3.3%                                                                                 

Exiting... (End of file)

**from smplayer**

/usr/local/bin/mplayer -noquiet -nofs -nomouseinput -sub-fuzziness 1 -identify -slave -vo xv, -ao alsa, -nokeepaspect -framedrop -nodr -double -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 50331662 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/whozai/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -subpos 100 -volume 40 -cache 2000 -osdlevel 0 -vf-add screenshot -slices -channels 2 -af scaletempo,equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 110 /media/ZIEOS/bess.avi

Warning unknown option stop-xscreensaver at line 129
Unknown option on the command line: -stop-xscreensaver
Error parsing option on the command line: -stop-xscreensaver
MPlayer SVN-r29330-4.2.4 (C) 2000-2009 MPlayer Team
ID_EXIT=NONE

did i do something wrong during installation?

---

### Post by mc4man on 2009-05-31
> but why the error mess.

It's not an error per se, just means mplayer was compiled with lirc support and whem mplayer was/is started the daemon wasn't running (ie. could not connect to socket

If you don't want to see it, next time you build mplayer remove liblircclient-dev first or find the appropriate config option to disable

(unless you have some plans/means to use it (lirc

---

### Post by logos34 on 2009-05-31
ok, thanx for info..no, don't need lirc support

---

### Post by rvm4000 on 2009-05-31
> **whozai_min said:**
> **from the terminal**

root@whozai-laptop:/media/ZIEOS# mplayer bess.avi
Warning unknown option stop-xscreensaver at line 129
MPlayer SVN-r29330-4.2.4 (C) 2000-2009 MPlayer Team

Playing bess.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
AVI: ODML: Building ODML index (2 superindexchunks).
VIDEO:  [xvid]  208x156  0bpp  29.970 fps  216.3 kbps (26.4 kbyte/s)
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Forced audio codec: mad
Requested audio codec family [mad] (afm=libmad) not available.
Enable it at compilation.
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 16000 Hz, 2 ch, s16le, 32.0 kbit/6.25% (ratio: 4000->64000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
No such audio driver 'pulse'
No such audio driver 'alsa'
AO: [oss] 16000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A: 357.5 (05:57.4) of 2818.6 (46:58.5)  3.3%                                                                                 

Exiting... (End of file)

**from smplayer**

/usr/local/bin/mplayer -noquiet -nofs -nomouseinput -sub-fuzziness 1 -identify -slave -vo xv, -ao alsa, -nokeepaspect -framedrop -nodr -double -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 50331662 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/whozai/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -subpos 100 -volume 40 -cache 2000 -osdlevel 0 -vf-add screenshot -slices -channels 2 -af scaletempo,equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 110 /media/ZIEOS/bess.avi

Warning unknown option stop-xscreensaver at line 129
Unknown option on the command line: -stop-xscreensaver
Error parsing option on the command line: -stop-xscreensaver
MPlayer SVN-r29330-4.2.4 (C) 2000-2009 MPlayer Team
ID_EXIT=NONE

did i do something wrong during installation?

Probably you fail to install some development packages.

What does ./configure say?

---

### Post by whozai_min on 2009-05-31
my problem solved... i download smplayer and mplayer from getdeb.net and install it..and now i can watch the video..

is there any disadvantage using this method?.. i follow the tutorial and skip at mplyer and  smplayer from the tutorial..

---

### Post by andrew.46 on 2009-05-31
Hi whozai,

> **whozai_min said:**
> my problem solved... i download smplayer and mplayer from getdeb.net and install it..and now i can watch the video..

Glad you have resolved your issue. Probably an older version of SMPlayer on getdeb but as long as it works for you :-).

Andrew

---

### Post by CD Baric on 2009-06-01
Thanks so much for your informative guide and ongoing follow up.

I now have mplayer_3:1.0~svn-r29333-1_amd64 running on Jaunty AMD64 on my twin core AMD 7750 CPU with 4 gigs memory.

I was unable to support ARTs but it was a small price to pay.

I am also a Slackware user - 12.2 current! I am planning on a trial of Slack64.

Slackware was my first Linux - I made my first commercial installation in 1995 - faxserver for a dozen W95 desktops.

Thanks again for your help and guidance.

CD Baric

---

### Post by andrew.46 on 2009-06-01
Hi CD Baric,

> **CD Baric said:**
> Thanks so much for your informative guide and ongoing follow up.

I now have mplayer_3:1.0~svn-r29333-1_amd64 running on Jaunty AMD64 on my twin core AMD 7750 CPU with 4 gigs memory.

Excellent news, although I feel somewhat overshadowed by your hardware :-). You realise that there is a Jaunty version for this guide? No matter if you have manged to get it all installed.

> I am also a Slackware user - 12.2 current! I am planning on a trial of Slack64.

I never really had the bandwidth or the inclination to run -current but I am more that happy with the release version 12.2 and I guess 13.0 will be out soon enough. Did you notice that MPlayer has actually become a part of -current with the [Tue May 19 15:36:49 CDT 2009 changes]("ftp://ftp.slackware.com/pub/slackware/slackware-current/ChangeLog.txt") and looks like it is being kept up to date as well! BTW while you are there search the page for 'Andrew Strong' and you will see my single greatest claim to fame :-).

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

### Post by andrew.46 on 2009-09-14
In a small demonstration that this Hardy Heron guide is *still *well-supported I have added in a small section to enable amr playback with the svn MPlayer. Works well on my system but please let me know if there are any problems...

Andrew

---

### Post by pedja_portugalac on 2009-11-08
Hi Andrew

There's no need to compile yasm package because there's already latest version in synaptic repository. I am trying to get this work on Karmic. See you later.

---

### Post by andrew.46 on 2009-11-09
Hi Pedja,

> **pedja_portugalac said:**
> There's no need to compile yasm package because there's already latest version in synaptic repository. I am trying to get this work on Karmic. See you later.

I will admit that I don't have a copy of Hardy installed at the moment so I take your word for this :). As for Karmic:

Howto: Utilise the svn MPlayer to Improve Karmic Koala's 'mplayer-nogui' Package
[http://ubuntuforums.org/showthread.php?t=1305181](http://ubuntuforums.org/showthread.php?t=1305181)

All the best,

Andrew

---

### Post by FakeOutdoorsman on 2009-11-09
> **andrew.46 said:**
> Hi Pedja,



I will admit that I don't have a copy of Hardy installed at the moment so I take your word for this :). As for Karmic:

Howto: Utilise the svn MPlayer to Improve Karmic Koala's 'mplayer-nogui' Package
[http://ubuntuforums.org/showthread.php?t=1305181](http://ubuntuforums.org/showthread.php?t=1305181)

All the best,

Andrew

I think that taking the few minutes to compile a recent yasm is worth the effort in return for a large list of bug fixes and feature additions compared to the repository yasm.

I just noticed that the guide is installing yasm 0.7.2, but the latest release is 0.8.0.  I subscribed to the super low volume [yasm-announce](http://www.tortall.net/projects/yasm/wiki/MailingList) mailing list to keep up with the occasional yasm release.

---

### Post by andrew.46 on 2009-11-09
Hi Fakeoutdoorsman,

> **FakeOutdoorsman said:**
> I just noticed that the guide is installing yasm 0.7.2, but the latest release is 0.8.0.  I subscribed to the super low volume [yasm-announce](http://www.tortall.net/projects/yasm/wiki/MailingList) mailing list to keep up with the occasional yasm release.

Looks like I need to reinstall Hardy this weekend :).

Andrew

---

### Post by mc4man on 2009-11-09
Just to clarify, the yasm available in hardy is an old 0.5.0-2 ver. so instr. to upgrade are valid

[http://packages.ubuntu.com/en/hardy/yasm](http://packages.ubuntu.com/en/hardy/yasm)

(noting though that there are no install deps preventing the install of a yasm package from more recent releases on hardy, ect.
[http://packages.ubuntu.com/en/karmic/yasm](http://packages.ubuntu.com/en/karmic/yasm)

---

### Post by rvm4000 on 2009-11-09
I'm using Hardy on my laptop and indeed it's necessary to update yasm, at least to version 0.7.

But you don't need to compile it, you can find yasm 0.7.1 (for Hardy and Intrepid) in this PPA:

[https://launchpad.net/~rvm/+archive/libs](https://launchpad.net/~rvm/+archive/libs)

That PPA also includes some libraries that help to compile mplayer on Hardy, Intrepid, Jaunty and Karmic.

---

### Post by pedja_portugalac on 2009-11-09
> **andrew.46 said:**
> Hi Pedja,



I will admit that I don't have a copy of Hardy installed at the moment so I take your word for this :). As for Karmic:

Howto: Utilise the svn MPlayer to Improve Karmic Koala's 'mplayer-nogui' Package
[http://ubuntuforums.org/showthread.php?t=1305181](http://ubuntuforums.org/showthread.php?t=1305181)

All the best,

Andrew

Hahahaha ;) . I was trying to install svn mplayer using 2 of yours howtos but also mplayer official documentation. Utilise the svn MPlayer to Improve Karmic Koala's 'mplayer-nogui' and the old one for Hardy but with GUI. At this moment I know lil-bit more about compiling packages and it wasn't problem to make my own svn-mplayer with GUI and mencoder enabled. The only thing now is that I don't like the GUI anymore :lolflag:. It doesn't support full range of possibilities offered by svn-mplayer. Foe example, I was trying to watch a movie with 5.1 surround sound. Smplayer played that movie only if I chose simple stereo, otherwise no sound at all. But when I start mplayer from terminal: mplayer -channels 6 <movie name> it plays like a charm. I think I'll keep on using nogui. Thanks for that tread to. Now, it wouldn't be linux if we don't get into other problems as soon as we solve some of them :D, I can't get it play TV over dvb-t pinnacle nano stick. I was trying for a week to get it work using so many packages but the only one with which was able to show some channels was the vlc. Again it couldn't save channels.conf and I had to scan every time I restart vlc :mad:. Mplayer command: mplayer dvb:// gives nothing even if I have saved channels.conf produced by w_scan in .mplayer directory. Anyway, I know I have to keep on trying to find solution and would like to say thank you, ones again, for all the good howto-s you have made and shared with community.

All the best, cheers from Brussels ;)

---

### Post by andrew.46 on 2009-11-10
Hi pedja,

> **pedja_portugalac said:**
> At this moment I know lil-bit more about compiling packages and it wasn't problem to make my own svn-mplayer with GUI and mencoder enabled. 

It certainly sounds like you have moved beyond these guides which I find immensely gratifying :). The guides in their various forms were only ever meant to furnish a *starting* point from which people could explore their own interests with media playback. 

Andrew

---

### Post by andrew.46 on 2009-11-10
Well I have undertaken a spring-clean of this guide after a new installation of Hardy on VirtualBox. I cannot believe that I wrote this guide over 2 years ago but this perhaps explains a few little anomalies that I have silently corrected :). Larger changes are placement of the release version of libopencore-amr and use of a different SMPlayer PPA. And of course a new gratuitous screenshot, Slackware 13 now resting quietly in the background as the host system. As usual please point out any errors...

All the best,

Andrew

---

### Post by iRounak on 2009-11-20
This has become a really long thread. I am not sure whether the first post is still good for Karmic Koala.  Can someone confirm it? Is there an easy way to install mplayer? (I have it installed with get-apt but I cannot see the video (I hear only audio). Smplayer shows the video but it still has codec problems)

---

### Post by andrew.46 on 2009-11-20
Hi iRounak,

> **iRounak said:**
> This has become a really long thread. I am not sure whether the first post is still good for Karmic Koala.  Can someone confirm it? 

The guide is only really suited to Hardy Heron. However there is another guide that has been specifically written for Karmic Koala:

Howto: Utilise the svn MPlayer to Improve Karmic Koala's 'mplayer-nogui' Package
[http://ubuntuforums.org/showthread.php?t=1305181](http://ubuntuforums.org/showthread.php?t=1305181)


> Is there an easy way to install mplayer? (I have it installed with get-apt but I cannot see the video (I hear only audio). Smplayer shows the video but it still has codec problems)

The easiest way to install MPlayer under Karmic is from the Ubuntu repository as you have done. If there are a few problems there a better version is available from the PPA provided by RVM. If you are interested in troubleshooting you existing copy of MPlayer could you run a file as follows:

```
mplayer -v myfile.avi

```
and post the full commandline + terminal output here?

All the best,

Andrew

---

### Post by iRounak on 2009-11-20
Thanks for the prompt response.
When i open the video file in mplayer (by right-clicking on the file and then selecting "play with mplayer", i get an error:
Error opening/initialising video_out (-vo) device

But when I used the command you gave, 
mplayer -v file.avi
it played properly.

So how to get fix the problem?

---

### Post by andrew.46 on 2009-11-20
Hi iRoounak,

> **iRounak said:**
> When i open the video file in mplayer (by right-clicking on the file and then selecting "play with mplayer", i get an error:
Error opening/initialising video_out (-vo) device

But when I used the command you gave, 

```
mplayer -v file.avi
```

it played properly.

I wonder if you have several copies of MPlayer on your system? The option on right click should have been 'Open with..... SMPlayer', as the attached screenshot demonstrates. Can I ask which copy of MPlayer you are using? Perhaps try the following command which will demonstrate if there is more than one:

```
sudo find /usr -iname 'mplayer'
```

All the best,

Andrew

---

### Post by iRounak on 2009-11-23
sorry for the delay in reply. I am still out on a vacation. I will post back when I get to "my" system.

---

### Post by iRounak on 2009-11-24
> **andrew.46 said:**
> Hi iRoounak,



I wonder if you have several copies of MPlayer on your system? The option on right click should have been 'Open with..... SMPlayer', as the attached screenshot demonstrates. Can I ask which copy of MPlayer you are using? Perhaps try the following command which will demonstrate if there is more than one:

```
sudo find /usr -iname 'mplayer'
```All the best,

Andrew

The result of the command is as follows:
/usr/share/menu/mplayer
/usr/share/doc/mplayer
/usr/share/mplayer
/usr/bin/mplayer
/usr/lib/mime/packages/mplayer


When I right-click, I get:
Enqueue in SMplayer
Mplayer media player
SMplayer
VLC

I just noticed that I don't get any errors if I use SMplayer.

---

### Post by andrew.46 on 2009-11-24
Hi iRounak,

> **iRounak said:**
> When I right-click, I get:
```
Enqueue in SMplayer
Mplayer media player
SMplayer
VLC
```

I just noticed that I don't get any errors if I use SMplayer.

Looks like the problem is with the default gui for MPlayer which is gmplayer. I would suggest you avoid gmplayer as it has not been developed for a while and debate continues amongst the developers about whether it should be abandoned or not. And if SMPlayer is playing your files well enough I suspect the problem is solved?

I will admit that I am getting a little lost though, is this the repository MPlayer from Karmic that you have installed?

All the best,

Andrew

---

### Post by iRounak on 2009-11-24
> I will admit that I am getting a little lost though, is this the repository MPlayer from Karmic that you have installed?
This is the problem really. I am not exactly sure what I did to get mplayer working.. Basically, I did not know that non-gui mplayer came along with Karmic. I installed mplayer first from Ubuntu Software Centre. Then I ran the command apt-get install mplayer. It would be better if I first remove mplayer completely and then use this:
Howto: Utilise the svn MPlayer to Improve Karmic Koala's 'mplayer-nogui' Package
[http://ubuntuforums.org/showthread.php?t=1305181](http://ubuntuforums.org/showthread.php?t=1305181)

How should I completely remove mplayer from my system?

---

### Post by mc4man on 2009-11-24
wrong thread (again

---

### Post by iRounak on 2009-11-24
posted in the correct thread now:
[http://ubuntuforums.org/showpost.php?p=8381682&postcount=85](http://ubuntuforums.org/showpost.php?p=8381682&postcount=85)

---

### Post by mc4man on 2009-11-25
> posted in the correct thread now:

> wrong thread (again 

@ iRounak
I was actually referring to myself, the again part was from something the other day. ( though possibly you were in the wrong thread also...

---

### Post by andrew.46 on 2009-11-25
OK so now I'm confused too :).

Andrew

---

### Post by fukc on 2009-12-20
I wonder how much time should be spend on this? 2-3 hr maybe? Just exactly the same time to install MacOS is required. Compare installation of the full OS with a freaking codec compilation...

Poor Linux, it's a toy to kill time. 

--
Roman

---

### Post by andrew.46 on 2009-12-20
Hi fukc,

> **fukc said:**
> I wonder how much time should be spend on this? 2-3 hr maybe?

If your computer has reasonable processing power it should take about 30 minutes...

Andrew

---

### Post by talsemgeest on 2009-12-20
> **fukc said:**
> I wonder how much time should be spend on this? 2-3 hr maybe? Just exactly the same time to install MacOS is required. Compare installation of the full OS with a freaking codec compilation...

Poor Linux, it's a toy to kill time. 

--
Roman
Compilation will always take more time than installing a binary. If you were to factor in the amount of time that it took for MacOS to compile at Apple, you would be looking at considerably longer than compiling mencoder ;)

Also, if the wait is too long you can always install the version from the Ubuntu repositories, which may only take seconds, depending on your PC and internet connection.

---

### Post by Linuxforall on 2009-12-20
On my dual quad core with make -j8 command it takes less than ten minutes with all 8 cores in action. The only time it takes is the download of the necessary files.

If you don't wish to compile, there is the basic medibuntu option as well as latest option offered via ppa from Brandon Snider and RVM who is also the creator of the excellent SMPLAYER.

At least Linux offers me the means to compile latest x264 and ffmpeg along with a universal player. In Windows I have to depend on Klite to come out with the latest updates, thankfully they are pretty much frequent for now so in all, not bad for a toy distro ;)

---

### Post by NewtownGuy on 2009-12-20
RE: mplayer: error while loading shared libraries: libcucul.so.0: cannot open shared object file: No such file or directory

I can't get past this missing file when I try to run mplayer from the command line. I've searched for an answer that I can understand, but I don't see one. I'm not up to doing a compile, I just want to apt-get install mplayer and have it work. I'm sympathetic with the person who said, in effect, there's too much geekiness in Ubuntu, because I sure can't understand some of the replies that assume the user is a guru instead of a mortal.

I'm running 8.04.1 LTS. I've done apt-get update. I have universe and multiverse enabled in the apt source list. I've run apt-get install mplayer several times now to see if somehow, magically, the missing libcucul.so.0 would appear, but no luck. There aren't any errors when I run apt-get install mplayer.

How can I fix this ?

Thank you.

-- NewtownGuy

---

### Post by andrew.46 on 2009-12-21
Hi NewtownGuy,

> **NewtownGuy said:**
> RE: mplayer: error while loading shared libraries: libcucul.so.0: cannot open shared object file: No such file or directory

I can't get past this missing file when I try to run mplayer from the command line. I've searched for an answer that I can understand, but I don't see one. 

It does seem a little odd as normally when you install the repository MPlayer it will drag all the required dependencies with it. Perhaps a first step would be to install the following:

```
sudo apt-get install libcucul0 libcucul-dev
```

and this might get you out of trouble?

> I'm not up to doing a compile, I just want to apt-get install mplayer and have it work. I'm sympathetic with the person who said, in effect, there's too much geekiness in Ubuntu, because I sure can't understand some of the replies that assume the user is a guru instead of a mortal.

Not everybody wants to compile :).

Andrew

---

### Post by FakeOutdoorsman on 2009-12-24
This has been a popular guide: 104,167 views.  Good work, Andrew.

---

### Post by andrew.46 on 2009-12-25
Hi Fakeoutdoorsman,

> **FakeOutdoorsman said:**
> This has been a popular guide: 104,167 views.  Good work, Andrew.

Thanks! It pales a little compared to a certain guide that deals with FFmpeg :).

Andrew

---

### Post by wijit on 2010-01-17
I've followed Andrew's on Karmic. Unfortunately, I've got:
wijit@rmutk-wijit:~$ mplayer Record000.amr
MPlayer SVN-r30364-4.4.1 (C) 2000-2009 MPlayer Team

Playing Record000.amr.
Seek failed
libavformat file format detected.
LAVF_header: av_open_input_stream() failed


Exiting... (End of file)

Would you teach us to do it on Karmic Koala:popcorn:?

---

### Post by mc4man on 2010-01-17
I'm gathering you may have followed this guide (hardy) on a karmic install?

If so see here ( you  should un-install the mplayer you just built and either clean the mplayer source ( make distclean @  the mplayer source  prompt) and then follow the guide or better yet maybe just start fresh.

unless something has changed you probably should use this as a configure (see last page or so or maybe Andrew has some idea's
./configure --confdir=/etc/mplayer


[http://ubuntuforums.org/showthread.php?t=1305181](http://ubuntuforums.org/showthread.php?t=1305181)

---

### Post by clint0n on 2010-03-01
libarts1c2a is not in the repos for me? anyone unable to download some of the dev files? i tried chicago and main server too.

---

### Post by andrew.46 on 2010-03-01
Hi clint0n,

> **clint0n said:**
> libarts1c2a is not in the repos for me? anyone unable to download some of the dev files? i tried chicago and main server too.

I must confess that I no longer have Hardy running but I can see this package on the package browser here:

[http://packages.ubuntu.com/hardy/libarts1c2a](http://packages.ubuntu.com/hardy/libarts1c2a)

Andrew

---

### Post by mc4man on 2010-03-01
@ clint0n
I'm wondering if you're running hardy (8.04), if I had to guess I'd think not.
If not, some other  mplayer build guides

[jaunty (9.04]("http://ubuntuforums.org/showthread.php?t=1081070&highlight=andrew.46+jaunty+mplayer")

[karmic (9.10]("http://ubuntuforums.org/showthread.php?t=1305181")

---

### Post by clint0n on 2010-03-01
bleh. haha!~ i didn't even notice the guide was for hardy, sorry about that. I have karmic. thanks for the links mc4man and thanks for the guide andrew you are a pro.

---

### Post by community nerd on 2010-08-04
thanks alot all seemed to do fine

---

### Post by gillza on 2010-08-04
> **andrew.46 said:**
> Hi fukc,



If your computer has reasonable processing power it should take about 30 minutes...

Andrew

2Ghz Core 2 Duo, 2 gb ram, 5400rpm hdd, fresh ubuntu, install is less than 30 minutes :) 

Thanks Andrew for the great guide!

---

### Post by andrew.46 on 2010-08-04
Hi gillza,

> **gillza said:**
> 2Ghz Core 2 Duo, 2 gb ram, 5400rpm hdd, fresh ubuntu, install is less than 30 minutes :) 

Thanks Andrew for the great guide!

I will admit that I have not looked at this version of my MPlayer guides for a long time so I am glad it still works ok :). For those who have moved to Lucid Lynx there is a shinier guide here:

Howto: Build the svn MPlayer under the latest release version of Ubuntu
[http://ubuntuforums.org/showthread.php?t=1542240](http://ubuntuforums.org/showthread.php?t=1542240)

All the best,

Andrew

---

