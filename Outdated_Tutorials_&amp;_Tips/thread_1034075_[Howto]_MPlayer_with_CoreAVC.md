---
title: "[Howto] MPlayer with CoreAVC"
date: 2009-01-07
forum: Outdated Tutorials &amp; Tips
---

### Post by Bachstelze on 2009-01-07
[b]===========================
Howto: MPlayer with CoreAVC
===========================[/b]
[i]This guide will work on Ubuntu 8.10 "Intrepid Ibex", 9.04 "Jaunty Jackalope" and 9.10 "Karmic Koala", both 32 and 64bit.
Although it has not been tested on previous Ubuntu releases, there is a good chance it will work with them too.
It should also work with very minimal changes in any other modern GNU/Linux distribution.

The version of CoreAVC that has been tested is 1.9.5.[/i]


[COLOR="Red"]**When you ask for help about your video not playing, plase include the FULL output from MPlayer in your post!**[/COLOR]


**What this guide *is***

This guide will explain in detail the steps needed to install and configure a build of the [MPlayer](http://www.mplayerhq.hu/) video player that will be suitable for use with the [CoreAVC](http://www.coreavc.com/) H.264 decoder, using code from the [coreavc-for-linux]("http://code.google.com/p/coreavc-for-linux/") project. The text of this document is licensed under the Simplified BSD License as used by the [FreeBSD](http://www.freebsd.org/copyright/freebsd-license.html) project (the license statement for this document can be found at the bottom thereof).


**What this guide is *not***

This guide is not a comprehensive MPlayer build guide ([another guide]("http://ubuntuforums.org/showthread.php?t=1024592") on this subject exists on these forums). It strives to be quick, simple, no-nonsense and to-the-point, and therefore will describe only the steps required to get what its title says: a build of MPlayer with CoreAVC support.

Of course, if you need to compile MPlayer with specific options, or if you desire to stick with The Ubuntu Way&#8482; and create a .deb package for your build, you are perfectly free to do so, but it is not the point of this guide to tell you how do to that and I refer you to the aforementioned one, which can very well be used in conjunction with this one.


**What is CoreAVC and why would I want to use it?**

CoreAVC is a proprietary MPEG-4 AVC (Advanced Video Coding, aka H.264) decoder. H.264 uses extremely advanced compression algorithms to achieve much better video compression than its predecessors, but with the drawback that much more processing power is needed in order to properly decode the resulting video streams.

The MPlayer video player ships with the Free libavcodec library, which provides it with H.264 decoding capabilities. However, many people experience video stuttering, frame-dropping, or even impossibility to playback H.264 streams at all with it, especially with high-definition material on older hardware. CoreAVC offers much better decoding performance than libavcodec, and therefore might be a solution for those people.

You will of course need a valid CoreAVC license key in order to be able to use it with MPlayer (there is a trial version of CoreAVC, but I could not test it myself, feel free to do it and report your results!), and I shall remind you that as per the forums rules, anyone's asking or offering CoreAVC itself and/or a CoreAVC license key will result in action being taken by the forum staff.


**Get the sources**

First, let's create a directory to work in, install the necessary build tools, and download the MPlayer sources as well as the coreavc-for-linux code. Karmic users will also need to install gcc 4.3, as the default gcc in Karmic (4.4) causes problems with MPlayer:

```
mkdir ~/mplayer-with-coreavc
cd ~/mplayer-with-coreavc
sudo apt-get install build-essential subversion pkg-config xorg-dev
sudo apt-get install gcc-4.3   # Karmic users
svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer
svn checkout http://coreavc-for-linux.googlecode.com/svn/trunk/ coreavc-for-linux

```

The next step is to install DShowServer, which is the program that will allow MPlayer to make use of CoreAVC. It is different depending on your architecture (i.e. whether you use the 32bit or 64bit version of Ubuntu).


**Patch, build and install DShowServer (i386/32bit users)**

First, we need to patch the sources to make them compatible with recent versions of MPlayer:

```
cd coreavc-for-linux
wget -qO - "http://pastebin.com/pastebin.php?dl=f7ca459d" | patch -p0
```

Then we build the [font="monospace"]dshowserver[/font] and [font="monospace"]registercodec[/font] binaries and copy them into [font="monospace"]/usr/local/bin[/font].

```
cd dshowserver
make
sudo cp dshowserver registercodec /usr/local/bin
```


**Build DShowServer statically on a 32bit system (amd64/64bit users)**

DShowServer will not compile on a 64bit system (you can try!). That means you will have to compile it statically on a 32bit system, and copy the resulting binaries onto your 64bit system. To do this, download the coreavc-for-linux sources on your 32bit system as described above (you don't need the MPlayer sources), and compile the DShowServer binaries with the [font="monospace"]STATIC[/font] flag:

```
make STATIC=1
```

Alternatively, I have a [tarball]("http://itsuki.fkraiem.org/stuff/dshowserver-ia32-r82-1.tar.bz2") containing those binaries (compiled on Karmic with coreavc-for-linux r82 and the above patch) that you can use.


**Install and register CoreAVC**

Copy the [font="monospace"]CoreAVCDecoder.ax[/font] file (located in the CoreAVC directory under Windows's "Program Files") in [font="monospace"]/usr/local/lib/win32/[/font] (create that directory if it does not exist). You can either copy this file from your existing Windows installation of CoreAVC or, if you don't have one, run the Windows installer in WINE and copy it from your WINE virtual drive.

The next step is to enter your CoreAVC license key in the registry (don't forget to replace the bogus one in the command with your real one!):

```
test -d ~/.mplayer || mkdir ~/.mplayer
registercodec -r ~/.mplayer/registry32 -k "HKLM\\Software\\CoreCodec\\CoreAVC Pro\\Serial" -v "55555-55555-CORE-55555-5555"
```

Then, to check that it's working:

**dshowserver will currently crash during this step. This is caused by a patch that fixes a playback problem, you can probably just ignore this step for now.**

```
dshowserver -c CoreAVCDecoder.ax -s 1280x720 -g 09571a4b-f1fe-4c60-9760de6d310c7c31 -b 12 -f 0x34363248 -o 0x30323449
```

If all went well, that command should return:

```
3248 -o 0x30323449
No id specified, assuming test mode
Opening device
len: 992
ProductVersion: 1.8.5
Decoder supports the following YUV formats: YUY2 UYVY YV12 I420
Decoder is capable of YUV output (flags 0x2b)
Setting fmt
Starting
Initialization is complete
```

***Note for CoreAVC 1.9 users:** CoreAVC 1.9 supports GPU decoding on nvidia graphics card using nvidia's CUVID interface. Therefore, you will see the following warning message when running the above command:*

```
Win32 LoadLibrary failed to load: nvcuvid.dll, /usr/lib/win32/nvcuvid.dll, /usr/local/lib/win32/nvcuvid.dll
```

*You can safely disregard it. The absence of the nvcuvid.dll library will not affect the normal operation of CoreAVC.*


**Patch, build and install MPlayer**

Now let's move to the MPlayer source directory and configure it:

```
cd ~/mplayer-with-coreavc/mplayer
./configure
```

Karmic users will need to configure MPlayer to use gcc 4.3 for compilation:

```
CC=gcc-4.3 ./configure
```

There are of course a lot of options to choose from here, but once again, it's outside the scope of this guide. If the configuration has completed successfully and the options look good to you, you can apply the coreavc-for-linux patch:

```
wget "http://pastebin.com/pastebin.php?dl=f1c7c15f7" -qO - | patch -p0
```

As of MPlayer r29367, the output looks like this:

```
(Stripping trailing CRs from patch.)
patching file libmpcodecs/vd.c
Hunk #1 succeeded at 25 (offset -4 lines).
Hunk #2 succeeded at 57 (offset -5 lines).
(Stripping trailing CRs from patch.)
patching file Makefile
Hunk #2 succeeded at 519 (offset 295 lines).
(Stripping trailing CRs from patch.)
patching file libmpcodecs/vd_dshowserver.c

```

Then we build and install MPlayer:

```
make
sudo make install
```

*If the build fails, it is most likely because a change in the MPlayer source code broke compatibility with coreavc-for-linux or caused some other bug. Please report in the thread and I'll update the patch accordingly.*

The last step is to copy the [font="monospace"]codecs.conf[/font] file from the MPlayer source directory in your [font="monospace"]~/.mplayer[/font] directory if you don't have one already:

```
test -f ~/.mplayer/codecs.conf || cp etc/codecs.conf ~/.mplayer
```

Finally, open your [font="monospace"]codecs.conf[/font] file in your favourite text editor, and add this text at the bottom of it:

```
videocodec coreserve
  info "CoreAVC DShow H264 decoder 1.3 for x86 - http://corecodec.org/"
  status working
  format 0x10000005
  fourcc H264,h264 H264
  fourcc X264,x264
  fourcc avc1,AVC1 AVC1
  fourcc davc,DAVC
  fourcc VSSH
  driver dshowserver
  dll "CoreAVCDecoder.ax"
  guid 0x09571a4b, 0xf1fe, 0x4c60, 0x97, 0x60, 0xde, 0x6d, 0x31, 0x0c, 0x7c, 0x31
  out YV12,IYUV,I420,YUY2
```


**Enjoy!**

To check that CoreAVC is actually working, start MPlayer like this from your terminal:

```
mplayer -vc coreserve foo.mkv
```

The [font="monospace"]-vc coreserve[/font] argument will force MPlayer to use CoreAVC (of course, make sure you're trying to play a file containing a H.264 video stream, otherwise CoreAVC won't be able to decode it, and you will not see any video).

Of course, it would be a pain to add [font="monospace"]-vc coreserve[/font] to your command line every time you want to play a video. The best way to avoid that is to open your main MPlayer config file (located at [font="monospace"]~/.mplayer/config[/font]) in your favourite text editor and add this line to it:

```
vc=coreserve,
```

*Do not* forget the trailing comma, it is very important. Now, every time you will try to play a video, MPlayer will first try to decode it with CoreAVC and, if that fails, fall back to the normal codecs.


**FAQs**

*I have the Ubuntu package for MPlayer installed. What do I do?*

Since you are building a new version of MPlayer, you probably won't need the old one anyway, and it's recommended to uninstall it in order to avoid conflicts.

That being said, it is not an absolute requirement, and you can also use the build you've done with this guide alongside your "official" version. Simply omit the [font="monospace"]sudo make install[/font] step and run the [font="monospace"]mplayer[/font] binary directly from your build directory (you can also move and/or rename it to your convenience).


*What if I want to uninstall my build?*

Simply return to your source directory and do:

```
sudo make uninstall
```

If you have deleted your source directory, here is a list of the files most commonly installed, you can safely remove them.

```
/usr/local/etc/mplayer
/usr/local/bin/mencoder
/usr/local/bin/mplayer 
/usr/local/bin/gmplayer
/usr/local/share/mplayer/skins
/usr/local/share/pixmaps/mplayer.xpm
/usr/local/share/applications/mplayer.desktop
/usr/local/share/man/man1/mplayer.1
/usr/local/share/man/man1/mencoder.1
```


*How do I upgrade to a newer version of CoreAVC?*

Simply copy the new version of the [font="monospace"]CoreAVCDecoder.ax[/font] file over your old one in [font="monospace"]/usr/local/lib/win32[/font].


**Legal stuff**

[SIZE="1"][font="monospace"]Copyright 2009 Firas Kraïem. All rights reserved.

Redistribution and use in source and compiled forms, with or
without modification, are permitted provided that the following
conditions are met:

Redistributions in source form must retain the above copyright
notice, this list of conditions and the following disclaimer.

Redistributions in compiled form must reproduce the above
copyright notice, this list of conditions and the following
disclaimer in the documentation and/or other materials provided
with the distribution.

THIS DOCUMENT IS PROVIDED BY THE AUTHOR ``AS IS'' AND ANY
EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO,
THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A
PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE AUTHOR
OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT
LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF
USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED
AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT
LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING
IN ANY WAY OUT OF THE USE OF THIS DOCUMENT, EVEN IF ADVISED OF
THE POSSIBILITY OF SUCH DAMAGE.[/font][/SIZE]

---

### Post by jpeddicord on 2009-01-08
> **HymnToLife said:**
> 
**Legal stuff**

[SIZE="1"][font="monospace"]Copyright 2009 Firas Kraïem. All rights reserved.

Redistribution and use in source and binary forms, with or
without modification, are permitted provided that the following
conditions are met:

Redistributions in source form must retain the above copyright
notice, this list of conditions and the following disclaimer.

Redistributions in binary form must reproduce the above
copyright notice, this list of conditions and the following
disclaimer in the documentation and/or other materials provided
with the distribution.

THIS DOCUMENT IS PROVIDED BY THE AUTHOR ``AS IS'' AND ANY
EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO,
THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A
PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE AUTHOR
OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT
LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF
USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED
AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT
LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING
IN ANY WAY OUT OF THE USE OF THIS DOCUMENT, EVEN IF ADVISED OF
THE POSSIBILITY OF SUCH DAMAGE.[/font][/SIZE]

Wouldn't a non-source based license make more sense, such as one of the Creative Commons licenses or the GFDL? Unless you can compile this tutorial into a binary (which would be awesome)

---

### Post by Bachstelze on 2009-01-08
> **jacobmp92 said:**
> Wouldn't a non-source based license make more sense, such as one of the Creative Commons licenses or the GFDL? Unless you can compile this tutorial into a binary (which would be awesome)

In the case of text material like this, the "source" form means a text version you can for example copy-and-paste around, and the "binary" form is everything else (for example a PDF, an ODT/DOC/RTF document, or a printed copy). I'm pretty sure the GFDL uses the same terminology.

---

### Post by Bachstelze on 2009-01-09
So no one else has anything to say? Guess I'l move it into the Tutorials section later today then.

---

### Post by Bachstelze on 2009-01-09
Bump :D

---

### Post by BrownD on 2009-01-16
First of all, great guide - it is very easy to follow and understand :)

However, having a couple problems I am hoping someone here can help me with.  It all goes perfectly, registering CoreAVC etc worked up to when i try to install mplayer.  The patch works fine, but 'make' brought up tons of errors.  

So instead, I tried using your 'source snapshot', did ./configure again, patched and 'make' - there were a lot less errors this time but for some reason I cant figure out what the problem is ;(  Heres the last few lines from make:

[http://paste.ubuntu.com/105483/plain/](http://paste.ubuntu.com/105483/plain/)

There are other 'warnings' etc that are throughout the make process as well.  Im pretty unexperienced with ubuntu and linux in general so its probably a stupid mistake on my part - but I can tell you I still get the same errors even when I dont patch mplayer, so its probably unrelated to CoreAVC.

Anyway, appreciate any advise/help, thanks ;)

Edit: Here is the full 'make' paste, if its needed at all: [http://paste.ubuntu.com/105496/](http://paste.ubuntu.com/105496/)

---

### Post by Bachstelze on 2009-01-16
BrownD's problem was caused by a bug in the mplayer source, which was fixed in the latest revision (r28344). I uploaded a new source snapshot made with that revision and updated the link.

---

### Post by ripps818 on 2009-01-18
For ease of use, you can install a dshowserver patched mplayer from RVM's PPA at [http://launchpad.net/~rvm/+archive]("http://launchpad.net/~rvm/+archive").

You can install dshowserver and registercodec by installing the dshowserver package from my PPA at [http://launchpad.net/~ripps818/+archive]("http://launchpad.net/~ripps818/+archive").

(Unfortunately, I can't figure out how to build a 64 bit package in PPA, so you'll have to follow manual instructions if you have x86_64 cpu.)

---

### Post by Cybervirem on 2009-01-18
Hi,

First, I would like to join the "congratulators" and thank for this guide !
However, i can't manage to compile whatever version i use : svn updated trunk ou source snapshot.

Though i successfully installed, registred coreAVC and patched, it always stops at the same module giving me :
> 
cc -DHAVE_AV_CONFIG_H -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -I.. -I.. -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -std=gnu99 -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -I.  -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT -I/usr/include/kde/artsc -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -D_REENTRANT   -Ilibdvdread4  -I/usr/include/freetype2 -I/usr/include   -I/usr/include/dirac   -I/usr/include/schroedinger-1.0 -I/usr/include/liboil-0.3   -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12   -Ilibdvdnav   -c -o libx264.o libx264.c

libx264.c: In function 'X264_init':
libx264.c:167: error: 'x264_param_t' has no member named 'i_bframe_adaptive'

make: *** [libavcodec/libavcodec.a] Erreur 2


Does anybody understand why ?  (I think i have all needed dev lib installed)

Thank you for hints

---

### Post by Cybervirem on 2009-01-18
i followed this thread to replace x264 libs :

[http://ubuntuforums.org/showthread.php?t=558538](http://ubuntuforums.org/showthread.php?t=558538)

pointing to this one :

[http://ubuntuforums.org/showthread.php?t=1024592](http://ubuntuforums.org/showthread.php?t=1024592)


i could get it work fine, though i got troubles with  :

o XShape extension which vanished during manipulations - i didn't have this error when i started to compile... so i couldn't enable gui :( but i works fine from man pages to keyboard :-) 
(not yet solved, ideas to obtain true gui are  welcome :-) )

o libavcodec/nellymoserenc.c in which i added a define ([http://lists.mplayerhq.hu/pipermail/mplayer-users/2008-December/075391.html](http://lists.mplayerhq.hu/pipermail/mplayer-users/2008-December/075391.html))

Anyway, very interesting topic driving throu tons of video mplaying informations ;-)

1080p coreAVC videos are read without frame dropping, and with sync sound !

i will check for such topic in french forums, and add if not.

Thank you

---

### Post by Bachstelze on 2009-01-18
The build-issue with x364 is indeed a common one, which I forgot when writing this guide, I whall update it soon (it would seem the version of the x264 library in the Ubuntu repositories is not compatible with MPlayer's latest versions, and an up-to-date one must be used instead).

About your GUI problems, you mean you can't start MPlayer with the GMPlayer GTK+ GUI? What happens if you try to run [font="monospace"]gmplayer[/font] from a terminal?

---

### Post by Cybervirem on 2009-01-19
Hi,

yes it sounds like a compat pb. 

With x264 from svn, it's ok (adding a line of code in libavcodec/nellymoserenc.c).

About graphic, i don't know what went wrong.  try after try i could configure with --enable-gui, and could compile ; 

the only way the alter XShape cap is from xorg.conf, and obviously i tried with native xorg nvidia driver and with the proprietary one... Just using the admin menu... a non deterministic automated process ;-)
Without --enable-gui, everything is ok.

---

### Post by tech0007 on 2009-01-19
Hi!  thanks for this wonderful guide.  I was able to follow it, compile mplayer and edit codecs.conf.  But whenever I run it, it shows:

```

Forced video codec: coreserve
Cannot find codec matching selected -vo and video format 0x33564D57.
Read DOCS/HTML/en/codecs.html!

```

So I get no video. Any help is appreciated.

Got this resolved!

---

### Post by Cybervirem on 2009-01-19
Hi,

if i try with a movie which doesn't use CoreAVC, i obtain "no video", all ok with coreavc encoded movies. (ffmpeg -i foo.mkv --> video : h264) 
- 
it depends only on what encoding you want to read ; with -vc coreserve : only coreavc, without -vc coreserve, it reads all other kind.

---

### Post by Bachstelze on 2009-01-19
Hmm, I should have made that clearer.

With [font="monospace"]-vc coreserve,[/font] (notice the trailing comma!), it will work for everything (it will first try to use CoreAVC, and if that fails, fall back to the normal codecs).

That means you can add

```
vc=coreserve,
```

to your mplayer.conf, and it will always use CoreAVC if possible, and fall back to the default codecs if not.

---

### Post by Cybervirem on 2009-01-19
thank you !
I will now try to configure with --enable-gui :-)

---

### Post by Bachstelze on 2009-01-19
> **Cybervirem said:**
> thank you !
I will now try to configure with --enable-gui :-)

You can also try to use smplayer instead of the GUI that ships with MPlayer. I've been told it's much more advanced and has more features, but couldn't get the time to try it yet.

---

### Post by MathSWE on 2009-01-22
Hi!

Id really like to get this to work! :)

However, my problem is that my trial serial code doesnt seem to regiser correctly, or it cant be found. I have a 64 bit CPU if that matters.

The registration process goes fine, but when it enter the command to test the registration I get:

No id specified, assuming test mode
Opening device
Called unk_IsDebuggerPresent
MSGBOX 'Serial Number Missing!' 'CoreAVC Trial Edition' (327680)
Win32 LoadLibrary failed to load: CoreAVCDecoder.ax
Warning: DS_Filter() could not open DirectShow DLL.  (DLL=CoreAVCDecoder.ax)
Failed to create DirectShow filter
Failed to open win32 codec CoreAVCDecoder.ax

How do I fix this?

Thanks in advance! //Mathias

---

### Post by Bachstelze on 2009-01-22
The serial number for the Trial version is stored in a different place in registry than for the full version, so the command to register your serial number is different. Try this:

```
rm -rf ~/.mplayer/registry32
registercodec -r ~/.mplayer/registry32 -k "HKLM\\Software\\CoreCodec\\CoreAVC Trial\\Serial" -v "55555-55555-CORE-55555-5555"
```

---

### Post by stepdown on 2009-01-24
Well, I've got it working by following your instructions, so that's very good!

Still unable to get 1080p files to play smoothly though, looks like it's a HW issue, but thanks for a great tutorial! :)

---

### Post by Bachstelze on 2009-02-19
Updated for CoreAVC 1.9 (yes, it works). I'll have to look into the GPU decoding (I don't have a compatible card at the moment), but it seems unlikely that it will work.

---

### Post by blablu on 2009-02-24
HymnToLife thanks for this great guide.

I'm having this problem:

> **tech0007 said:**
> Hi!  thanks for this wonderful guide.  I was able to follow it, compile mplayer and edit codecs.conf.  But whenever I run it, it shows:

```

Forced video codec: coreserve
Cannot find codec matching selected -vo and video format 0x33564D57.
Read DOCS/HTML/en/codecs.html!

```

So I get no video. Any help is appreciated.

Got this resolved!

But unfortunately I couldn't get this resolved! :lolflag:
Any help would be greatly appreciated. Thanks for your time.

---

### Post by Bachstelze on 2009-02-24
Most likely you are trying to play a video that is not an AVC stream. CoreAVC can only decode AVC streams, and won't work on other formats.

---

### Post by blablu on 2009-02-24
I thought that all h264 encoded videos were AVC streams.:(

---

### Post by ripps818 on 2009-02-24
Did you add the codec coreserve to your ~/.mplayer/codecs.conf? coreserve won't work just by installing the codec, dshowserver, and mplayer.

[http://code.google.com/p/coreavc-for-linux/wiki/MplayerInstallation](http://code.google.com/p/coreavc-for-linux/wiki/MplayerInstallation)

Also, remember to put "-vc coreserve**,**", notice the comma at the end, that tells mplayer to fallback to other codecs if coreserve doesn't work.

---

### Post by Bachstelze on 2009-02-24
> **blablu said:**
> I thought that all h264 encoded videos were AVC streams.:(

They are. H.264 (*not* "h264", by the way) is just another name for MPEG-4 AVC. Are you sure the video you are trying to play is H.264? The error you're getting is the one I get when I try to play a non-H.264 stream with CoreAVC.

---

### Post by blablu on 2009-02-24
solved!

My problem was that I was using /usr/bin/mplayer instead of /usr/local/bin/mplayer. 

Thanks for your help guys!

---

### Post by binbash on 2009-02-24
Very good step by step guide.I will test this on my other notebook which has some problems with x264

---

### Post by blablu on 2009-02-24
Anybody got it to work with smplayer?

for some reason it doesn't like me puttin rc=coreserve inside .mplayer/config. Though mplayer alone is fine.

thanks again for your time!

---

### Post by binbash on 2009-02-24
I am getting this error: 

```

 dshowserver -c CoreAVCDecoder.ax -s 1280x800 -g 09571a4b-f1fe-4c60-9760de6d310c7c31 -b 12 -f 0x34363248 -o 0x30323449
No id specified, assuming test mode
Opening device
Win32 LoadLibrary failed to load: CoreAVCDecoder.ax, /usr/lib/win32/CoreAVCDecoder.ax, /usr/local/lib/win32/CoreAVCDecoder.ax
Warning: DS_Filter() could not open DirectShow DLL.  (DLL=CoreAVCDecoder.ax)
Failed to create DirectShow filter
Failed to open win32 codec CoreAVCDecoder.ax

```

---

### Post by binbash on 2009-02-24
got it working, forgot to copy the file.Thanks again :)

---

### Post by binbash on 2009-02-25
OK i got everything installed  this time (on another PC) , when i open a mkv file, it says NO VIDEO

---

### Post by Cybervirem on 2009-02-27
Hi,

the comma at after "-vc coreserve,"

---

### Post by Bachstelze on 2009-02-28
> **blablu said:**
> Anybody got it to work with smplayer?

for some reason it doesn't like me puttin rc=coreserve inside .mplayer/config. Though mplayer alone is fine.

thanks again for your time!

It works fine with smplayer here. What you need to add to your config file  is:

```
vc=coreserve,
```

---

### Post by SpoZen on 2009-02-28
Thanks for the how to, but please add that you have to install yasm 0.7.2 and x264 from this guide:  [http://ubuntuforums.org/showthread.php?t=558538](http://ubuntuforums.org/showthread.php?t=558538)

Now to my problem:

I can't get mplayer to use coreavc after adding this line:

```
vc=coreserve,
```

To ~/.mplayer/codecs.conf
 
It only works if i use this command mplayer -vc coreserve.

Also is their a how to somewhere about 5.1 sound in mplayer?

---

### Post by andrew.46 on 2009-02-28
Hi SpoZen,

> **SpoZen said:**
> Thanks for the how to, but please add that you have to install yasm 0.7.2 and x264 from this guide:  [http://ubuntuforums.org/showthread.php?t=558538](http://ubuntuforums.org/showthread.php?t=558538)

h264 *decoding* comes with FFmpeg's libavcodec, as I believe HymnToLife mentions in this guide, but if you definitely want *encoding* there is a better method for installing x264 [in this thread]("http://ubuntuforums.org/showthread.php?t=1081070").

Playback can be seen:

```
andrew@skamandros~$ mplayer -vc help | grep -i 264
ffh264      ffmpeg    working   FFmpeg H.264  [h264]
ffh264vdpau ffmpeg    working   FFmpeg H.264 (VDPAU)  [h264_vdpau]
vssh264     dshow     working   VSS H.264 New  [vsshdsd.dll]
vssh264old  vfw       working   VSS H.264 Old  [vssh264.dll]
```

while encoding capability can be seen:

```
andrew@skamandros~$ mencoder -ovc help | grep -i 264
   x264     - H.264 encoding
```

Andrew

---

### Post by SpoZen on 2009-02-28
I'm not really sure what you getting at. How does this help me? The outputs doesn't tell me anything useful?


```
spozen@Luke:~$ mplayer -vc help | grep -i 264
parse error at line 4075
ffh264      ffmpeg    working   FFmpeg H.264  [h264]
ffh264vdpau ffmpeg    working   FFmpeg H.264 (VDPAU)  [h264_vdpau]

vssh264     dshow     working   VSS H.264 New  [vsshdsd.dll]
vssh264old  vfw       working   VSS H.264 Old  [vssh264.dll]
```


The guide told me to disable mencoder so i can't give you any output from that.

I mentioned x264 because when i tried to compile without it, it just throw out a bunch of errors at me.

---

### Post by andrew.46 on 2009-02-28
Hi SpoZen,

> **SpoZen said:**
> I mentioned x264 because when i tried to compile without it, it just throw out a bunch of errors at me.

My apologies I did not fully understand your question and I will admit my motivation in busting in on this thread was simply to guide you to a better installation method for x264 :-). And to mention in passing the different approaches in MPlayer to decoding and encoding h264 / x264.

Perhaps if you post the actual errors HymnToLife can guide you better? (x264 errors usually relate to an x264 build less than 59 = old Ubuntu problem.)

All the best,

Andrew

---

### Post by SpoZen on 2009-03-01
Well, there are not really any errors, i just can't get it to use CoreAVC by default. To use CoreAVC i now have to type this everytime:

```
mplayer -vc coreserve clip.mkv

```


In the guide it's stated you have to add this line to ~/.mplayer/codecs.conf:

```
vc=coreserve,
```

But this doesn't work at all, mplayer doesn't use coreAVC.
And i can't use the mplayer -vc command anymoore i only get sound.

---

### Post by Bachstelze on 2009-03-02
> **SpoZen said:**
> In the guide it's stated you have to add this line to ~/.mplayer/codecs.conf

Nope, you must add it to [font="monospace"]~/.mplayer/config[/font].

I must admit, though, that my guide doesn't make this very clear. I'm going to add a more thorough section about the different methods that can be used to actually enable CoreAVC.

---

### Post by SpoZen on 2009-03-02
This is my ~/.mplayer/config:


```
# Write your default config options here!
vc=coreserve,

```

I still can't get it to use CoreAVC, i am totally out of luck.

---

### Post by Bachstelze on 2009-03-02
Please paste what you get in your terminal.

---

### Post by SpoZen on 2009-03-03
```
spozen@Luke:~$ gmplayer 
MPlayer SVN-r28764-4.3.2 (C) 2000-2009 MPlayer Team
parse error at line 4075
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

(<unknown>:5869): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",

Playing /media/Filmer1/Filmer/21.2008.1080p.BD9.x264-REFiNED/refined-21-1080p.mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_AC3), -aid 0, -alang eng
[mkv] Track ID 3: subtitles (S_TEXT/UTF8), -sid 0, -slang eng
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1920x1080  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
SUB: Detected subtitle file format: subviewer
SUB: Read 1268 subtitles.
SUB: Added subtitle file (1): /media/Filmer1/Filmer/21.2008.1080p.BD9.x264-REFiNED/refined-21-1080p.srt
==========================================================================
Forced video codec: coreserve
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 640.0 kbit/41.67% (ratio: 80000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 1920 x 1080 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 1920x1080 => 1920x1080 Planar YV12 
A:  22.9 V:  22.0 A-V:  0.927 ct: -0.222   0/  0 54%  7% 96.6% 50 0             

           ************************************************
           **** Your system is too SLOW to play this!  ****
           ************************************************

Possible reasons, problems, workarounds:
- Most common: broken/buggy _audio_ driver
  - Try -ao sdl or use the OSS emulation of ALSA.
  - Experiment with different values for -autosync, 30 is a good start.
- Slow video output
  - Try a different -vo driver (-vo help for a list) or try -framedrop!
- Slow CPU
  - Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
    e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.
- Broken file
  - Try various combinations of -nobps -ni -forceidx -mc 0.
- Slow media (NFS/SMB mounts, DVD, VCD etc)
  - Try -cache 8192.
- Are you using -cache to play a non-interleaved AVI file?
  - Try -nocache.
Read DOCS/HTML/en/video.html for tuning/speedup tips.
If none of this helps you, read DOCS/HTML/en/bugreports.html.

A:  52.9 V:  52.1 A-V:  0.760 ct: -0.233   0/  0 73%  8% 18.7% 674 0            

MPlayer interrupted by signal 2 in module: decode video
A:  54.1 V:  52.2 A-V:  1.877 ct: -0.234   0/  0 77%  8% 18.7% 675 0            
Exiting... (Quit)

```

---

### Post by SpoZen on 2009-03-03
```
spozen@Luke:~$ gmplayer 
MPlayer SVN-r28764-4.3.2 (C) 2000-2009 MPlayer Team
parse error at line 4075
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

(<unknown>:5869): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",

Playing /media/Filmer1/Filmer/21.2008.1080p.BD9.x264-REFiNED/refined-21-1080p.mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_AC3), -aid 0, -alang eng
[mkv] Track ID 3: subtitles (S_TEXT/UTF8), -sid 0, -slang eng
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1920x1080  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
SUB: Detected subtitle file format: subviewer
SUB: Read 1268 subtitles.
SUB: Added subtitle file (1): /media/Filmer1/Filmer/21.2008.1080p.BD9.x264-REFiNED/refined-21-1080p.srt
==========================================================================
Forced video codec: coreserve
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 640.0 kbit/41.67% (ratio: 80000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 1920 x 1080 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 1920x1080 => 1920x1080 Planar YV12 
A:  22.9 V:  22.0 A-V:  0.927 ct: -0.222   0/  0 54%  7% 96.6% 50 0             

           ************************************************
           **** Your system is too SLOW to play this!  ****
           ************************************************

Possible reasons, problems, workarounds:
- Most common: broken/buggy _audio_ driver
  - Try -ao sdl or use the OSS emulation of ALSA.
  - Experiment with different values for -autosync, 30 is a good start.
- Slow video output
  - Try a different -vo driver (-vo help for a list) or try -framedrop!
- Slow CPU
  - Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
    e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.
- Broken file
  - Try various combinations of -nobps -ni -forceidx -mc 0.
- Slow media (NFS/SMB mounts, DVD, VCD etc)
  - Try -cache 8192.
- Are you using -cache to play a non-interleaved AVI file?
  - Try -nocache.
Read DOCS/HTML/en/video.html for tuning/speedup tips.
If none of this helps you, read DOCS/HTML/en/bugreports.html.

A:  52.9 V:  52.1 A-V:  0.760 ct: -0.233   0/  0 73%  8% 18.7% 674 0            

MPlayer interrupted by signal 2 in module: decode video
A:  54.1 V:  52.2 A-V:  1.877 ct: -0.234   0/  0 77%  8% 18.7% 675 0            
Exiting... (Quit)

```

It seems like it detects CoreAVC, but it uses the ffmpeg decoder instead.

---

### Post by Bachstelze on 2009-03-03
Could you please do the same thing with

```
vc=coreserve
```

in your config file (without the trailing comma), to forbid the use of any other video codec?

---

### Post by SpoZen on 2009-03-03
Ok it's working now i found out that i didn't remove vc=coreserve, from ~/.mplayer/codecs.conf


Sorry for double post and wasting your time, i hope you forgive me for my stupidity ;) 

Now i just have to fix some tearing problems and sound issues but i will google that up my self, thanks for the help!

---

### Post by dhanar_10 on 2009-03-06
Hi everyone,

My mplayer-coreavc is unable to play MP4 files downloaded from YouTube.

Is there anyone having the same problem or is it just me?  Is there any possible fix?

Thank you.

---

### Post by bcg30506 on 2009-04-10
I've followed your very useful guide to the letter and used the mplayer-checkout version from the link in your guide with the trail version of CoreAVC.  DirectShow runs fine and mplayer patched and installed fine.  The codec is setup and the config is good.  I'm trying to play an MTS file from our Canon HF10 camera which records in 1920x1080x30p AVCHD format.  If I try and run mplayer with no options I get:

$ mplayer /monolith/tmp/Canon/stream/00000.mts
MPlayer SVN-r28661-4.2.4 (C) 2000-2009 MPlayer Team
137 audio & 297 video codecs

Playing /monolith/tmp/Canon/stream/00000.mts.
TS file format detected.
VIDEO H264(pid=4113) AUDIO A52(pid=4352) NO SUBS (yet)!  PROGRAM N. 1
FPS not specified in the header or invalid, use the -fps option.
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 256.0 kbit/16.67% (ratio: 32000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   9.0 (08.9) of 2472.1 (41:12.1)  1.1% 
Exiting... (Quit)


If I then add the -fps 60 option, it then correctly detects the video stream and tries to initialize the dshowserver codec, only to crash with this:

$ mplayer -fps 60 /monolith/tmp/Canon/stream/00000.mts
MPlayer SVN-r28661-4.2.4 (C) 2000-2009 MPlayer Team
137 audio & 297 video codecs

Playing /monolith/tmp/Canon/stream/00000.mts.
TS file format detected.
VIDEO H264(pid=4113) AUDIO A52(pid=4352) NO SUBS (yet)!  PROGRAM N. 1
==========================================================================
Forced video codec: coreserve
Opening video decoder: [dshowserver] DirectShowServer video codecs


MPlayer interrupted by signal 11 in module: init_video_codec
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.

---

### Post by ubulaptop on 2009-04-10
this may sound a bit stupid, but I can not find out where the terminal is located! Can someone explain me how it is?:lolflag:

---

### Post by c-m on 2009-04-10
I get the following error:

```
carl@carl-laptop:~/mplayer-with-coreavc/coreavc-for-linux/dshowserver$ dshowserver -c CoreAVCDecoder.ax -s 1280x720 -g 09571a4b-f1fe-4c60-9760de6d310c7c31 -b 12 -f 0x34363248 -o 0x30323449
No id specified, assuming test mode
Opening device
Win32 LoadLibrary failed to load: CoreAVCDecoder.ax, /usr/lib/win32/CoreAVCDecoder.ax, /usr/local/lib/win32/CoreAVCDecoder.ax
Warning: DS_Filter() could not open DirectShow DLL.  (DLL=CoreAVCDecoder.ax)
Failed to create DirectShow filter
Failed to open win32 codec CoreAVCDecoder.ax
   
```

---

### Post by bcg30506 on 2009-04-10
SOLVED.  I had to add the demuxer=lavf option to mplayer when playing the mts files from the Canon camera.  Now they play but are no faster than with ffmpeg's decoder.  I still get "System too slow to play this" message.  Visually I can tell no difference using CoreAVC over the base mplayer from svn.

Here is my processor info:

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Celeron(R) CPU 2.53GHz
stepping        : 1
cpu MHz         : 2533.622
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni monitor ds_cpl tm2 cid cx16 xtpr
bogomips        : 5073.31
clflush size    : 64

And mtrr info:
reg00: base=0x00000000 (   0MB), size= 512MB: write-back, count=1
reg01: base=0x1c000000 ( 448MB), size=  64MB: write-combining, count=1
reg02: base=0x1bf00000 ( 447MB), size=   1MB: uncachable, count=1

Any chance of my machine playing HD video files or am I SOL without upgrading hardware?


> **bcg30506 said:**
> I've followed your very useful guide to the letter and used the mplayer-checkout version from the link in your guide with the trail version of CoreAVC.  DirectShow runs fine and mplayer patched and installed fine.  The codec is setup and the config is good.  I'm trying to play an MTS file from our Canon HF10 camera which records in 1920x1080x30p AVCHD format.  If I try and run mplayer with no options I get:

$ mplayer /monolith/tmp/Canon/stream/00000.mts
MPlayer SVN-r28661-4.2.4 (C) 2000-2009 MPlayer Team
137 audio & 297 video codecs

Playing /monolith/tmp/Canon/stream/00000.mts.
TS file format detected.
VIDEO H264(pid=4113) AUDIO A52(pid=4352) NO SUBS (yet)!  PROGRAM N. 1
FPS not specified in the header or invalid, use the -fps option.
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 256.0 kbit/16.67% (ratio: 32000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   9.0 (08.9) of 2472.1 (41:12.1)  1.1% 
Exiting... (Quit)


If I then add the -fps 60 option, it then correctly detects the video stream and tries to initialize the dshowserver codec, only to crash with this:

$ mplayer -fps 60 /monolith/tmp/Canon/stream/00000.mts
MPlayer SVN-r28661-4.2.4 (C) 2000-2009 MPlayer Team
137 audio & 297 video codecs

Playing /monolith/tmp/Canon/stream/00000.mts.
TS file format detected.
VIDEO H264(pid=4113) AUDIO A52(pid=4352) NO SUBS (yet)!  PROGRAM N. 1
==========================================================================
Forced video codec: coreserve
Opening video decoder: [dshowserver] DirectShowServer video codecs


MPlayer interrupted by signal 11 in module: init_video_codec
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.

---

### Post by acr0nym on 2009-04-18
Hi I followed your instructions to the letter and everything went fine from installing to downloading etc..

But when I try to open my .mkv file (X264) with mplayer -vc coreserv blabla.mkv 
Mplayer tells me that it cannot find the video codec.
Now I am pretty sure I followed your instructions correctly, I even double checked them. Here's what mplayer shows me:

```
MPlayer SVN-r29188-4.3.3 (C) 2000-2009 MPlayer Team
137 audio & 297 video codecs

Playing blabla.mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_AC3), -aid 0, -alang und
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1280x720  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
Can't open /dev/fb0: No such file or directory
[fbdev2] Can't open /dev/fb0: No such file or directory
VO: [v4l2] No such file or directory
vo_cvidix: No vidix driver name provided, probing available ones (-v option for details)!
[cyberblade] Error occurred during pci scan: Operation not permitted
[mach64] Error occurred during pci scan: Operation not permitted
[mga] Error occurred during pci scan: Operation not permitted
[mga] Error occurred during pci scan: Operation not permitted
[nvidia_vid] Error occurred during pci scan: Operation not permitted
[pm3] Error occurred during pci scan: Operation not permitted
[radeon] Error occurred during pci scan: Operation not permitted
[rage128] Error occurred during pci scan: Operation not permitted
[s3_vid] Error occurred during pci scan: Operation not permitted
[SiS] Error occurred during pci scan: Operation not permitted
[unichrome] Error occurred during pci scan: Operation not permitted
[VO_SUB_VIDIX] Couldn't find working VIDIX driver.
==========================================================================
Forced video codec: coreserv
Cannot find codec matching selected -vo and video format 0x31637661.
Read DOCS/HTML/en/codecs.html!
==========================================================================
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   2.9 (02.8) of 57.4 (57.4)  1.0%                                                                                                                          

MPlayer interrupted by signal 2 in module: play_audio
A:   2.9 (02.9) of 57.4 (57.4)  1.0%                                                                                                                          
Exiting... (Quit)

```

It only plays sound, whereas before it used to play the video choppy but now there isn't any video at all. I don't think this is a specific problem with .mkv files since I cannot open normal low quality avi video files either which I used to be able to do before with the standard mplayer.

I think the problem has to do with the step:

```
ls ~/.mplayer/codecs.conf || cp etc/codecs.conf ~/.mplayer
```

When I did that, terminal told me 
```
ls: cannot access /home/acr0nym/.mplayer/codecs.conf: No such file or directory
```

The 2nd time I used that command I added sudo in front of it and I didn't get any error.

Great Tut and thanks in advance for any help :)

---

### Post by Bachstelze on 2009-04-18
> **acr0nym said:**
> 
I think the problem has to do with the step:

```
ls ~/.mplayer/codecs.conf || cp etc/codecs.conf ~/.mplayer
```

When I did that, terminal told me 
```
ls: cannot access /home/acr0nym/.mplayer/codecs.conf: No such file or directory
```

The 2nd time I used that command I added sudo in front of it and I didn't get any error.

Actually the error message you get the first time is normal, that was a bit silly of me to put this in the howto, I guess I'll remove it.

Since you ran the command the second time with [font="monospace"]sudo[/font], maybe your [font="monospace"]codecs.conf[/font] file is now owned by root. What does this command output?

```
ls -l ~/.mplayer/codecs.conf
```

---

### Post by acr0nym on 2009-04-19
I just edited this post... I managed to get it working by using the snapshot you mentioned in your post. That one works great :)

Now I still do have one question, when I open a video file for example with: "mplayer blabla.extension" it plays fine I can see the audio and video getting deteced no errors whatsoever, but it doesn't open the video panel, I can hear the audio though.

Another thing...I don't want to keep using the command line. So I wanted to install SMplayer but everytime I want to install that one it tells me that it has to install mplayer as well... I'm afraid it will override my custom compiled mplayer with the coreavc codec.. So how do I install SMplayer without mplayer 

Thanks again :)

---

### Post by rvm4000 on 2009-04-19
> **acr0nym said:**
> So how do I install SMplayer without mplayer

Get the smplayer sources and compile it.

---

### Post by EnSeNiX on 2009-04-22
Hi.i've install everything correctly but when i type 
mplayer -vc coreserve movie.mkv

there's no video only sounds can anyone help?

thanks

---

### Post by gandalf_17 on 2009-04-28
Hello. I wolud like to thank the tutorial. I'm new in the Ubuntu World (I have started yesterday) and this material and this forum it's a blessing.

So, I have many troubles that I not understand, and the MPlayer doesn't work in mi computer. **So I want to follow the guide since the beginning again**, but this is a problem for me. **How to remove and dispose all I did? **

Well, I'm waiting an answer. Thank very much.

Good Bye

PD: I'm sorry for my english. I'm spanish and I can't speak it very good.

---

### Post by Bachstelze on 2009-04-28
> **EnSeNiX said:**
> Hi.i've install everything correctly but when i type 
mplayer -vc coreserve movie.mkv

there's no video only sounds can anyone help?

thanks

Please paste the output from MPlayer.


> **gandalf_17 said:**
> So, I have many troubles that I not understand, and the MPlayer doesn't work in mi computer. **So I want to follow the guide since the beginning again**, but this is a problem for me. **How to remove and dispose all I did? **


How far did you go? If you didn't run [font="monospace"]sudo make install[/font], you can just delete your source directory and start again.

---

### Post by Bachstelze on 2009-04-28
Other updates:

-> As of MPlayer r29241, the patch provided in coreavc-for-linux r82 doesn't work anymore due to changes in the MPlayer source. I made a quick and somewhat dirty (but working) patch update and updated the guide accordingly.

-> Jaunty was released. The compatibility-related text at the top of the guide was also updated accordingly.

---

### Post by Zorael on 2009-04-30
Nevermind. I found the patch in the coreavc directory after some snooping, but I also found [http://ubuntuforums.org/showthread.php?t=1049449](http://ubuntuforums.org/showthread.php?t=1049449) which uses the "official" svn repo, with which your patch worked (although patch muttered about line offsets).
> **me][QUOTE=HymnToLife said:**
> -> As of MPlayer r29241, the patch provided in coreavc-for-linux r82 doesn't work anymore due to changes in the MPlayer source. I made a quick and somewhat dirty (but working) patch update and updated the guide accordingly.
I'm trying to combine compiling mplayer for CoreAVC with compiling mplayer for multithreaded decoding (as per [http://ubuntuforums.org/showthread.php?t=1104967](http://ubuntuforums.org/showthread.php?t=1104967)). That thread uses another repo which seems to be based on an earlier revision of mplayer master, and your patch fails when I *know* I succeeded with this earlier, on another machine.

Where can I find the old patch? Alternatively, could you, by any chance, glance briefly at that (multithreaded) mplayer source code to see if your current patch could be easily modified to work?[/quote]

---

### Post by gandalf_17 on 2009-04-30
HymnToLife, I have followed the guide again and I have not any problem.

Thank very much, my friend.

Bye and "Saludos desde Galicia (España)"

---

### Post by gandalf_17 on 2009-04-30
I'm sorry but I still have a problem.

Now, I have installed the MPlayer without the GUI, and I would like to install GUI without reinstalling MPlayer. What can I do?

Thank very much,

Bye!

---

### Post by Bachstelze on 2009-04-30
> **gandalf_17 said:**
> 
Now, I have installed the MPlayer without the GUI, and I would like to install GUI without reinstalling MPlayer. What can I do?

You must download the source code for SMPlayer [here]("http://smplayer.sourceforge.net/downloads.php?tr_lang=en") and compile it. It does not require recompiling MPlayer itself

If you want to use the GTK+ GUI that comes with MPlayer, you'll have to reconfigure your source with [font="monospace"]./configure --enable-gui[/font] and then recompile and reinstall MPlayer.

---

### Post by SuperBo on 2009-05-03
I think we should config codecs.conf with following
```
videocodec coreavc
  info "CoreAVC DShow H264 decoder 1.9 for x86 - http://coreavc.com/"
  status working
  format 0x10000005
  fourcc H264,h264 ;H264
  fourcc X264,x264 ;X264
  fourcc avc1,AVC1 ;AVC1
  fourcc davc,DAVC ;DAVC
  fourcc VSSH
  driver dshowserver
  dll "CoreAVCDecoder.ax"
  guid 0x09571a4b, 0xf1fe, 0x4c60, 0x97, 0x60, 0xde, 0x6d, 0x31, 0x0c, 0x7c, 0x31
  out YV12,IYUV,I420,YUY2
```

and put it at the top of codecs.conf will make coreserver as the default codec to decode h264,x264 and avc1.

---

### Post by gandalf_17 on 2009-05-04
> **HymnToLife said:**
> If you want to use the GTK+ GUI that comes with MPlayer, you'll have to reconfigure your source with [FONT=monospace]./configure --enable-gui[/FONT] and then recompile and reinstall MPlayer.

Thanks. I have alredy done it and MPlayer works very good. But I still have a problem.

[B]When I open a DVD with MPlayer, it appears a window with the follow mensage:

[I]Error!
Seek Failed[/I][/B]

I have read that I could work the DVD with other program, but **I prefer doing it with MPlayer**. 

**What can I do?** Thanks and excuse the inconvenience

Bye!

---

### Post by charcer on 2009-05-05
Could it be possible to add support for subtitles to the guide, for example 
```
ln -s /usr/share/fonts/truetype/freefont/FreeSans.ttf ~/.mplayer/subfont.ttf
```
because matroska subs won't work otherwise

---

### Post by Bachstelze on 2009-05-05
> **charcer said:**
> Could it be possible to add support for subtitles to the guide, for example 
```
ln -s /usr/share/fonts/truetype/freefont/FreeSans.ttf ~/.mplayer/subfont.ttf
```
because matroska subs won't work otherwise

This is not a MPlayer user guide. ;)

---

### Post by umanzor on 2009-05-06
Hi Hymn. I followed your instructions and everything seemed to go fine. Unfortunately, when I try to play mkvs, I'm only getting audio. I get this message as well:

> Forced video codec: coreserve
Cannot find codec matching selected -vo and video format 0x31637661.
Read DOCS/HTML/en/codecs.html!


Any ideas?

---

### Post by Bachstelze on 2009-05-06
Did you edit [font="monospace"]codecs.conf[/font] properly? Are yu sure the video stream of your MAtroska file is H.264?

---

### Post by umanzor on 2009-05-07
> **HymnToLife said:**
> Did you edit [font="monospace"]codecs.conf[/font] properly? Are yu sure the video stream of your MAtroska file is H.264?

Hi there,

Well, given that they are 720p videos and that I can play them in Windows using MPC and I see that CoreAVC is selected under video filters (or something like that) I think I can safely assume it is H.264. Correct if I'm wrong :p.

Now, ummmmm, I'll paste the last part of my codecs.conf file.

> videocodec coreserve
  info "CoreAVC DShow H264 decoder 1.3 for x86 - http://corecodec.org/"
  status working
  format 0x10000005
  fourcc H264,h264 H264
  fourcc X264,x264
  fourcc avc1,AVC1 AVC1
  fourcc davc,DAVC
  fourcc VSSH
  driver dshowserver
  dll "CoreAVCDecoder.ax"
  guid 0x09571a4b, 0xf1fe, 0x4c60, 0x97, 0x60, 0xde, 0x6d, 0x31, 0x0c, 0x7c, 0x31
  out YV12,IYUV,I420,YUY2

Thanks for your reply!

---

### Post by Bachstelze on 2009-05-07
It seems correct. Did you run

```
dshowserver -c CoreAVCDecoder.ax -s 1280x720 -g 09571a4b-f1fe-4c60-9760de6d310c7c31 -b 12 -f 0x34363248 -o 0x30323449
```

and was the output as it should have been?

---

### Post by Absurd on 2009-05-08
I'm getting the "Cannot find codec matching selected -vo and video format 0x31637661."

I'm pretty sure that the video is H.264 and that I did everything else correctly. However, based on the parameters I see for the aforementioned dshowserver command, the options seems to be specifically for 720p videos. 
I believe the video in format 0x31637661 is 480p (NTSC dvd). How would I go about adding a dshowserver entry for that?

---

### Post by Bachstelze on 2009-05-08
> **Absurd said:**
> However, based on the parameters I see for the aforementioned dshowserver command, the options seems to be specifically for 720p videos. 

That comment is just here to test whether dshowserver and CoreAVC are working properly, it doesn't have anything to do with actual video playback. Once again, did the command output what it shuld when you ran it?

---

### Post by Absurd on 2009-05-08
yes, and I'll run it again too

```
{albert:~/.mplayer}$ dshowserver -c CoreAVCDecoder.ax -s 1280x720 -g 09571a4b-f1fe-4c60-9760de6d310c7c31 -b 12 -f 0x34363248 -o 0x30323449
No id specified, assuming test mode
Opening device
Called unk_IsDebuggerPresent
len: 992
ProductVersion: 1.9.0
Win32 LoadLibrary failed to load: nvcuvid.dll, /usr/lib/win32/nvcuvid.dll, /usr/local/lib/win32/nvcuvid.dll
Decoder supports the following YUV formats: YUY2 UYVY YV12 I420 
Decoder is capable of YUV output (flags 0x2b)
Setting fmt
Starting
Initialization is complete
{albert:~/.mplayer}$                                                 (05/08/09  8:13 AM)

```

here's my mplayer output if you don't believe me

```
{albert:~/.mplayer}$ /usr/local/bin/mplayer -vc coreserve /media/Source/movies/The.Man.Who.Knew.Too.Much.1956.DVDRip.AC3.h264-TSDC/The.Man.Who.Knew.Too.Much-TSDC.mkv
MPlayer SVN-r29274-4.3.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /media/Source/movies/The.Man.Who.Knew.Too.Much.1956.DVDRip.AC3.h264-TSDC/The.Man.Who.Knew.Too.Much-TSDC.mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_AC3), -aid 0, -alang eng
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  720x464  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Forced video codec: coreserve
Cannot find codec matching selected -vo and video format 0x31637661.
==========================================================================
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   3.4 (03.3) of 0.0 (00.0)  0.4% 

MPlayer interrupted by signal 2 in module: play_audio
A:   3.5 (03.4) of 0.0 (00.0)  0.4% 
Exiting... (Quit)
{albert:~/.mplayer}$                                                 (05/08/09  8:13 AM)

```

[edit]ok, for some reason it all works. Like, out of the blue.

suggestion to fellow nvidia users: if you use jaunty, you may want to install the nvidia-180-libvdpau-dev package before using the ./configure command before building mplayer. This will allow mplayer to compile with vdpau support; vdpau is the output plugin for CUDA decoding.

---

### Post by Master One on 2009-05-08
Awesome! Thanks for that great guide, HymnToLife, got it all working on a fresh Jaunty installation without any problems:

- CoreAVC 1.9.5 Build 6721
- MPlayer SVN r29275
- SMPlayer 0.6.7+SVN-r3014

At first I was skeptical, because of the installation going to /usr/local and having to compile SMPlayer manually as well, but that was no trouble at all. SMPlayer is so much better then the gmplayer gui, just get it from SVN as well, because the latest source tarball from the SMplayer site (v0.6.7) is broken.

Hopefully you keep that guide updated, development is going on so fast.

---

### Post by kingnebby on 2009-05-23
any way to get alsa to work?
dont have this option in my audio driver
Thanks

---

### Post by Bachstelze on 2009-05-23
> **kingnebby said:**
> any way to get alsa to work?
dont have this option in my audio driver
Thanks

You're probably missing some -dev package that is needed to compile with ALSA support. I can't help you with that, though, sorry.

---

### Post by kingnebby on 2009-05-23
> **HymnToLife said:**
> You're probably missing some -dev package that is needed to compile with ALSA support. I can't help you with that, though, sorry.

Thanks,
figured it out
during compiling
```
$sudo apt-get install build-essential subversion pkg-config xorg-dev libgtk2.0-dev libpulse-dev libasound2-dev
```

```
$cd ~/mplayer-with-coreavc/mplayer
$./configure --enable-gui --enable-alsa --enable-pulse
```

---

### Post by gandalf_17 on 2009-05-25
Hi.

I had done this how to a month ago, and mplayer works very well. But I have formatted mi PC and I have followed this tutorial again, however** mplayer works slowly now.** I have done this guide several times and I can't solved the problem. Ideas?

Thank very much

Bye!

---

### Post by xyos on 2009-05-29
tank you! it worked flawlessly

---

### Post by gandalf_17 on 2009-06-04
Hi, I have problems again :S

I have followed the guide again and when I compile, it appears this error:
[B]
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1[/B]

I have configured the program with:

./configure --enable-gui

Ideas?

Thank Very Much

Bye!

---

### Post by Bachstelze on 2009-06-04
> **gandalf_17 said:**
> Hi, I have problems again :S

I have followed the guide again and when I compile, it appears this error:
[B]
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1[/B]

I have configured the program with:

./configure --enable-gui

Ideas?

Thank Very Much

Bye!

Probably a change in mplayer that broke compatibility. I'll look into it tomorrow.

---

### Post by kingnebby on 2009-06-07
> **gandalf_17 said:**
> Hi.

I had done this how to a month ago, and mplayer works very well. But I have formatted mi PC and I have followed this tutorial again, however** mplayer works slowly now.** I have done this guide several times and I can't solved the problem. Ideas?

Thank very much

Bye!

do you have your ubuntu-restricted-extras installed?
> sudo apt-get install ubuntu-restricted-extra

---

### Post by gandalf_17 on 2009-06-07
> **kingnebby said:**
> do you have your ubuntu-restricted-extras installed?

Thanks, kingnebby, but I have solved that problem when I wrote vc=coreserve, in mi mplayer config file.

 Now, my problem is:

> 
I have followed the guide again and when I compile, it appears this error:
[B]
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1[/B]

I have configured the program with:

./configure --enable-gui

Ideas?

Thanks again for your patience.

Bye!

---

### Post by Bachstelze on 2009-06-07
> **gandalf_17 said:**
> Ideas?

Thanks again for your patience.

Bye!

I answered to that one. Please be patient, my time is not unlimited.

---

### Post by gandalf_17 on 2009-06-07
> **HymnToLife said:**
> I answered to that one. Please be patient, my time is not unlimited.

I'm sorry. I did not irritated you. 

Bye!

---

### Post by kingnebby on 2009-06-07
> **gandalf_17 said:**
> Hi, I have problems again :S

I have followed the guide again and when I compile, it appears this error:
[B]
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1[/B]

I have configured the program with:

./configure --enable-gui

Ideas?

Thank Very Much

Bye!

I would just use ./configure without --enable-gui
and install smplayer instead

---

### Post by Master One on 2009-06-07
Yes, forget the MPlayer gui, that's what SMPlayer is for.

---

### Post by sciurognathi on 2009-06-09
I received a patch error:

patching file Makefile
Hunk #2 FAILED at 224
1 out of 2 hunks FAILED -- saving rejects to file Makefile.rej

Problem solved: see [http://code.google.com/p/coreavc-for-linux/issues/detail?id=85](http://code.google.com/p/coreavc-for-linux/issues/detail?id=85)

Still another problem arrived: when I go to full screen in smplayer all is freezing and I need to reboot.

Ideas?

---

### Post by Bachstelze on 2009-06-16
Guide updated with a new patch, but it seems someone was faster than me. :p

---

### Post by swells5 on 2009-06-19
output from end of "make" (mplayer)- up until this point I thought I finally had it made.

coreavc 1.9.5 and output of dshowserver is identical to what you suggest it should be.
--
No id specified, assuming test mode
Opening device
Called unk_IsDebuggerPresent
len: 992
ProductVersion: 1.9.5
Win32 LoadLibrary failed to load: nvcuvid.dll, /usr/lib/win32/nvcuvid.dll, /usr/local/lib/win32/nvcuvid.dll
Decoder supports the following YUV formats: YUY2 UYVY YV12 I420 
Decoder is capable of YUV output (flags 0x2b)
Setting fmt
Starting
Initialization is complete
-----
copy of end of make file where it started to give errors
----
In file included from command.c:44:
stream/stream_dvd.h:6:32: error: dvdread/dvd_reader.h: No such file or directory
stream/stream_dvd.h:7:31: error: dvdread/ifo_types.h: No such file or directory
stream/stream_dvd.h:8:30: error: dvdread/ifo_read.h: No such file or directory
stream/stream_dvd.h:9:30: error: dvdread/nav_read.h: No such file or directory
In file included from command.c:44:
stream/stream_dvd.h:13: error: expected specifier-qualifier-list before 'dvd_reader_t'
make: *** [command.o] Error 1
-----
thanks for any help
steve

---

### Post by Bachstelze on 2009-06-19
You seem to be missing some files that should be in your mplayer source tree. Are you adding any extra options to [font="monospace"]./configure[/font]?

---

### Post by Master One on 2009-06-19
Made a new installation (without any extra options to ./configure) incl. SMPlayer (from svn as well) yesterday, all OK.

---

### Post by swells5 on 2009-06-19
no extra options
./configure    
only.
steve

---

### Post by Bachstelze on 2009-06-19
> **swells5 said:**
> no extra options
./configure    
only.
steve

Then I really don't know what could be wrong. Maybe having a full log of your build process might help, do:

```
cd
rm -rf mplayer-with-coreavc
script mplayerbuild.log
```

then start over. After the errors occurs, do

```
exist
```

and reply to this post with the mplayerbuild.log file as attachment.

---

### Post by sodapop_ on 2009-06-20
Hi im using the svn version of mplayer compiled with gcc 4.4.0, 
since my nvidia (NV40 [GeForce 6800]) card does not support VDPAU im trying to use CoreAVC, 
the problem is that i dont see much difference when using CoreAVC still the video specially on high motion 
scenes plays slow and looses sync with the audio. any ideas?

CPU usage : dshowserver 40%, mplayer 20%, X 15%

mplayer file.mkv -vc coreserve -ao alsa -ac hwac3 -nocorrect-pts

Matroska file format detected.
VIDEO:  [avc1]  1280x544  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Forced video codec: coreserve
Opening video decoder: [dshowserver] DirectShowServer video codecs
Opening device
len: 992
ProductVersion: 1.8.5
Decoder supports the following YUV formats: YUY2 UYVY YV12 I420 
Decoder is capable of YUV output (flags 0x2b)
Setting fmt
Starting
Initialization is complete
Dshowserver Connected to host
VDec: vo config request - 1280 x 544 (preferred colorspace: Packed YUY2)
[PP] Using codec's postprocessing, max q = 4.
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 2.35:1 - prescaling to correct movie aspect.
VO: [xv] 1280x544 => 1280x544 Planar YV12 
[VO_XV] Shared memory not supported
Reverting to normal Xv.
[VO_XV] Shared memory not supported
Reverting to normal Xv.
Found DirectShow filterSelected video codec: [coreserve] vfm: dshowserver (CoreAVC DShow H264 decoder 1.3 for x86 - [http://corecodec.org/](http://corecodec.org/))
==========================================================================
==========================================================================
Forced audio codec: hwac3
Opening audio decoder: [hwac3] AC3/DTS pass-through S/PDIF
No accelerated IMDCT transform found
hwac3: switched to AC3, 448000 bps, 48000 Hz
AUDIO: 48000 Hz, 2 ch, ac3, 448.0 kbit/29.17% (ratio: 56000->192000)
Selected audio codec: [hwac3] afm: hwac3 (AC3 through S/PDIF)
==========================================================================
AO: [alsa] 48000Hz 2ch ac3 (1 bytes per sample)
Starting playback...
....
           ************************************************
           **** Your system is too SLOW to play this!  ****
           ************************************************

Possible reasons, problems, workarounds:
- Most common: broken/buggy _audio_ driver
  - Try -ao sdl or use the OSS emulation of ALSA.
  - Experiment with different values for -autosync, 30 is a good start.
- Slow video output
  - Try a different -vo driver (-vo help for a list) or try -framedrop!
- Slow CPU
  - Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
    e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.
- Broken file
  - Try various combinations of -nobps -ni -forceidx -mc 0.
- Slow media (NFS/SMB mounts, DVD, VCD etc)
  - Try -cache 8192.
- Are you using -cache to play a non-interleaved AVI file?
  - Try -nocache.
Read DOCS/HTML/en/video.html for tuning/speedup tips.
If none of this helps you, read DOCS/HTML/en/bugreports.html.

---

### Post by Bachstelze on 2009-06-20
CoreAVC is not magical pixie dust. ;) Sometimes, videos are just too complex to decode even with it.

---

### Post by sodapop_ on 2009-06-21
i can see no difference in performance on any mkv file.

---

### Post by Bachstelze on 2009-06-21
> **sodapop_ said:**
> i can see no difference in performance on any mkv file.

Your CoreAVC installed properly, that's all I can say. If you think it sucks and want your money back, ask CoreCodec, not me...

---

### Post by jarek.uk on 2009-06-23
Hi,

I get this error when I try to run a patch. Any suggestions why?

(Stripping trailing CRs from patch.)
patching file libmpcodecs/vd.c
Hunk #1 succeeded at 25 (offset -4 lines).
Hunk #2 succeeded at 57 (offset -5 lines).
patch: **** Can't rename file libmpcodecs/vd.c to libmpcodecs/vd.c.orig : Permission denied

---

### Post by Bachstelze on 2009-06-23
> **jarek.uk said:**
> Hi,

I get this error when I try to run a patch. Any suggestions why?

(Stripping trailing CRs from patch.)
patching file libmpcodecs/vd.c
Hunk #1 succeeded at 25 (offset -4 lines).
Hunk #2 succeeded at 57 (offset -5 lines).
patch: **** Can't rename file libmpcodecs/vd.c to libmpcodecs/vd.c.orig : Permission denied

Apparently you don't have write permission to your source tree, which is why [font="monospace"]patch[/font] can't create backups of the patched files. The build should still work normally without them, though.

---

### Post by jarek.uk on 2009-06-23
I changed permission on all the files in folder to 0777 and i run it as sudo.

how can i give more permission?

In your how to, your printout shows that more files were patched after vd.c, and in my case it stops when it can't rename vd.c.

---

### Post by Bachstelze on 2009-06-23
> **jarek.uk said:**
> I changed permission on all the files in folder to 0777 and i run it as sudo.

You probably did something wrong right from the start. You should not need to change permissions for anything, and you should not run anything with sudo that is not run with sudo in the guide.

---

### Post by jarek.uk on 2009-06-23
that might be a problem... i run most of commands with sudo, just in case.

I'll do it again then.

thanks for your help.

---

### Post by rldev on 2009-08-06
Well the guide worked for me. I have using a harry Potter trailer 1080p and it runs perfectly. However I can't get smplayer to work with it properly. What is the path I should be giving smplayer and do I have to add any flags under advanced.?

I tried /usrlocal/bin/mplayer, but that gives me horrible playback. Command line playback is good.

---

### Post by rvm4000 on 2009-08-07
In smplayer 0.6.8 there's an option in preferences -> performance to enable coreavc.

---

### Post by Bachstelze on 2009-08-07
Also, you should read the guide more carefully. ;) I explain what to do when you want to start mplayer from a GUI.

---

### Post by rldev on 2009-08-07
Thanks rvm. I have it playing after I checked coreavc in smplayer. However, the performance is far worse than running mplayer from the command line. I had this same issue before running this patch, that's why I tried it. I'm not sure what variables smplayer is passing, but it is unwatchable with smplayer. Pretty good in mplayer from the command line.

I also notice and I'm sure somehow related that there is a big difference in performance when I run: 

mplayer /home/rocco/Desktop/*vidfile

as root vs user. I only get good performance running as root.

---

### Post by rvm4000 on 2009-08-07
> **rldev said:**
> Thanks rvm. I have it playing after I checked coreavc in smplayer. However, the performance is far worse than running mplayer from the command line. I had this same issue before running this patch, that's why I tried it. I'm not sure what variables smplayer is passing, but it is unwatchable with smplayer. Pretty good in mplayer from the command line.

You can see the arguments that smplayer passes to mplayer in Options -> View logs -> mplayer.

---

### Post by n3had on 2009-08-16
> **rvm4000 said:**
> You can see the arguments that smplayer passes to mplayer in Options -> View logs -> mplayer.

I've been trying to following this guide on karmic, i tried both the ppa and svn and had no installation problems

but i get this error when i try to play the file 

```
/usr/bin/mplayer -noquiet -nofs -nomouseinput -vc coreserve, -lavdopts threads=2 -sub-fuzziness 1 -identify -slave -vo xv -ao pulse -nokeepaspect -nodr -double -input nodefault-bindings:conf=/dev/null -stop-xscreensaver -wid 73400335 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/tru3m0sl3m/.config/smplayer/styles.*** -fontconfig -font DejaVu Sans -subfont-autoscale 0 -subfont-osd-scale 14 -subfont-text-scale 14 -subcp ISO-8859-1 -vid 0 -aid 0 -subpos 100 -volume 100 -cache 2000 -osdlevel  -vf-add screenshot -noslices -channels 6 -af volnorm=1,scaletempo /media/disk-2/123.mkv -loop 0

MPlayer SVN-r29325-4.4.1 (C) 2000-2009 MPlayer Team
parse error at line 347
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Terminal type `unknown' is not defined.

Playing /media/disk-2/123.mkv.

ID_VIDEO_ID=0
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
ID_AUDIO_ID=0
ID_AID_0_LANG=und
[mkv] Track ID 2: audio (A_AC3), -aid 0, -alang und
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1280x720  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
ID_FILENAME=/media/disk-2/123.mkv
ID_DEMUXER=mkv
ID_VIDEO_FORMAT=avc1
ID_VIDEO_BITRATE=0
ID_VIDEO_WIDTH=1280
ID_VIDEO_HEIGHT=720
ID_VIDEO_FPS=23.976
ID_VIDEO_ASPECT=1.7778
ID_AUDIO_FORMAT=8192
ID_AUDIO_BITRATE=0
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=6
ID_LENGTH=2487.90
ID_SEEKABLE=1
ID_CHAPTERS=0
[***] auto-open
Opening video filter: [screenshot]
[***] Init
[***] Updating font cache.
==========================================================================
Forced video codec: coreserve
Opening video decoder: [dshowserver] DirectShowServer video codecs
Opening device
Called unk_IsDebuggerPresent
len: 992
ProductVersion: 1.9.5
Win32 LoadLibrary failed to load: nvcuvid.dll, /usr/lib/win32/nvcuvid.dll, /usr/local/lib/win32/nvcuvid.dll
Decoder supports the following YUV formats: YUY2 UYVY YV12 I420 
Decoder is capable of YUV output (flags 0x2b)
Setting fmt
Starting
VDec: vo config request - 1280 x 720 (preferred colorspace: Packed YUY2)
[PP] Using codec's postprocessing, max q = 4.
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
ID_VIDEO_ASPECT=1.7778
[swscaler @ 0x33323e0]No accelerated colorspace conversion found.
[swscaler @ 0x33323e0]using unscaled yuv420p -> rgb24 special converter
VO: [xv] 1280x720 => 1280x720 Planar YV12 
Found DirectShow filterSelected video codec: [coreserve] vfm: dshowserver (CoreAVC DShow H264 decoder for x86 - http://corecodec.org/)
==========================================================================
ID_VIDEO_CODEC=coreserve
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform


MPlayer interrupted by signal 11 in module: init_audio_codec
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

### Post by Bachstelze on 2009-08-16
> **n3had said:**
> I've been trying to following this guide on karmic, i tried both the ppa and svn and had no installation problems

but i get this error when i try to play the file 


Please try without SMPlayer.

---

### Post by Nepherte on 2009-08-16
```
MPlayer SVN-r29325-4.4.1 (C) 2000-2009 MPlayer Team
....
opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform


MPlayer interrupted by signal 11 in module: init_audio_codec
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

This is a known problem when compiling mplayer with gcc 4.4.1 and liba52 support enabled. The problem was already there when compiling with gcc 4.4.0. A patch was released which fixed the issue for 4.4.0 and the problem "should" have been fixed with 4.4.1 but unfortunately it doesn't work.

You can either compile mplayer with an older gcc (remember to apply the patch for liba52 if using 4.4.0) or wait till a new fix is published.

---

### Post by penguinchrissy on 2009-08-18
My mplayer make fails with these errors
```

lcldec.c:50:18: error: zlib.h: No such file or directory
lcldec.c:70: error: expected specifier-qualifier-list before 'z_stream'
lcldec.c: In function 'zlib_decomp':
lcldec.c:131: warning: implicit declaration of function 'inflateReset'
lcldec.c:131: error: 'LclDecContext' has no member named 'zstream'
lcldec.c:132: error: 'Z_OK' undeclared (first use in this function)
lcldec.c:132: error: (Each undeclared identifier is reported only once
lcldec.c:132: error: for each function it appears in.)
lcldec.c:136: error: 'LclDecContext' has no member named 'zstream'
lcldec.c:137: error: 'LclDecContext' has no member named 'zstream'
lcldec.c:138: error: 'LclDecContext' has no member named 'zstream'
lcldec.c:139: error: 'LclDecContext' has no member named 'zstream'
lcldec.c:140: warning: implicit declaration of function 'inflate'
lcldec.c:140: error: 'LclDecContext' has no member named 'zstream'
lcldec.c:140: error: 'Z_FINISH' undeclared (first use in this function)
lcldec.c:141: error: 'Z_STREAM_END' undeclared (first use in this function)
lcldec.c:145: error: 'LclDecContext' has no member named 'zstream'
lcldec.c:147: error: 'LclDecContext' has no member named 'zstream'
lcldec.c:150: error: 'LclDecContext' has no member named 'zstream'
lcldec.c: In function 'decode_init':
lcldec.c:544: error: 'Z_NO_COMPRESSION' undeclared (first use in this function)
lcldec.c:544: error: 'Z_BEST_COMPRESSION' undeclared (first use in this function)
lcldec.c:580: error: 'LclDecContext' has no member named 'zstream'
lcldec.c:580: error: 'Z_NULL' undeclared (first use in this function)
lcldec.c:581: error: 'LclDecContext' has no member named 'zstream'
lcldec.c:582: error: 'LclDecContext' has no member named 'zstream'
lcldec.c:583: warning: implicit declaration of function 'inflateInit'
lcldec.c:583: error: 'LclDecContext' has no member named 'zstream'
lcldec.c:584: error: 'Z_OK' undeclared (first use in this function)
lcldec.c: In function 'decode_end':
lcldec.c:609: warning: implicit declaration of function 'inflateEnd'
lcldec.c:609: error: 'LclDecContext' has no member named 'zstream'
make[1]: *** [lcldec.o] Error 1
make[1]: Leaving directory `/home/dj/mplayer-with-coreavc/mplayer/libavcodec'
make: *** [libavcodec/libavcodec.a] Error 2
```

anything I can do or forgot to do that can fix/caused this?

---

### Post by Bachstelze on 2009-08-18
Install [font=monospace]zlib1g-dev[/font].

---

### Post by penguinchrissy on 2009-08-18
Thanks for help on the first problem. I didn't realize that I had my repositories from intrepid so I had to change them back in reinstall build-essentials. After doing that though I get this error that I can't decode
```

libavcodec/libavcodec.a(lcldec.o): In function `decode_frame':
lcldec.c:(.text+0x579): undefined reference to `inflateReset'
lcldec.c:(.text+0x5b9): undefined reference to `inflate'
lcldec.c:(.text+0x7bb): undefined reference to `inflateReset'
lcldec.c:(.text+0x811): undefined reference to `inflate'
lcldec.c:(.text+0x867): undefined reference to `inflateReset'
lcldec.c:(.text+0x8bf): undefined reference to `inflate'
libavcodec/libavcodec.a(lcldec.o): In function `decode_end':
lcldec.c:(.text.unlikely+0x4b): undefined reference to `inflateEnd'
libavcodec/libavcodec.a(lcldec.o): In function `decode_init':
lcldec.c:(.text.unlikely+0x363): undefined reference to `inflateInit_'
libavcodec/libavcodec.a(lclenc.o): In function `encode_frame':
lclenc.c:(.text+0x41): undefined reference to `deflateReset'
lclenc.c:(.text+0x91): undefined reference to `deflate'
lclenc.c:(.text+0xaa): undefined reference to `deflate'
libavcodec/libavcodec.a(lclenc.o): In function `encode_end':
lclenc.c:(.text.unlikely+0x23): undefined reference to `deflateEnd'
libavcodec/libavcodec.a(lclenc.o): In function `encode_init':
lclenc.c:(.text.unlikely+0x131): undefined reference to `deflateInit_'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1
```

thanks for your help.

---

### Post by regneva on 2009-09-09
> **penguinchrissy said:**
> Thanks for help on the first problem. I didn't realize that I had my repositories from intrepid so I had to change them back in reinstall build-essentials. After doing that though I get this error that I can't decode
```

libavcodec/libavcodec.a(lcldec.o): In function `decode_frame':
lcldec.c:(.text+0x579): undefined reference to `inflateReset'
lcldec.c:(.text+0x5b9): undefined reference to `inflate'
lcldec.c:(.text+0x7bb): undefined reference to `inflateReset'
lcldec.c:(.text+0x811): undefined reference to `inflate'
lcldec.c:(.text+0x867): undefined reference to `inflateReset'
lcldec.c:(.text+0x8bf): undefined reference to `inflate'
libavcodec/libavcodec.a(lcldec.o): In function `decode_end':
lcldec.c:(.text.unlikely+0x4b): undefined reference to `inflateEnd'
libavcodec/libavcodec.a(lcldec.o): In function `decode_init':
lcldec.c:(.text.unlikely+0x363): undefined reference to `inflateInit_'
libavcodec/libavcodec.a(lclenc.o): In function `encode_frame':
lclenc.c:(.text+0x41): undefined reference to `deflateReset'
lclenc.c:(.text+0x91): undefined reference to `deflate'
lclenc.c:(.text+0xaa): undefined reference to `deflate'
libavcodec/libavcodec.a(lclenc.o): In function `encode_end':
lclenc.c:(.text.unlikely+0x23): undefined reference to `deflateEnd'
libavcodec/libavcodec.a(lclenc.o): In function `encode_init':
lclenc.c:(.text.unlikely+0x131): undefined reference to `deflateInit_'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1
```

thanks for your help.

Open makefile using "gedit Makefile". There should be a line which begis with EXTRALIBS. Append " -lz -lm" to that line and try make again.

---

### Post by Bachstelze on 2009-09-09
Do not ediy your makefile. Just running

```
make clean
./configure
make
```

should be enough.

---

### Post by GraceDivine on 2009-09-19
Hello and thank you for the guide!
I just cloned the latest mplayer-mt source, and configured the source with just ./configure
After the code is generated, I tried applying the patch specified with this command:
wget [http://paste.ubuntu.com/197237/plain/](http://paste.ubuntu.com/197237/plain/) -qO - | patch -p0

Here is the output:

(Stripping trailing CRs from patch.)
patching file libmpcodecs/vd.c
Hunk #1 FAILED at 29.
Hunk #2 succeeded at 55 with fuzz 2 (offset -7 lines).
1 out of 2 hunks FAILED -- saving rejects to file libmpcodecs/vd.c.rej
(Stripping trailing CRs from patch.)
patching file Makefile
Hunk #2 succeeded at 522 (offset 298 lines).
(Stripping trailing CRs from patch.)
patching file libmpcodecs/vd_dshowserver.c

After issuing the make command, I get this shortened error:

libmpcodecs/vd.o -MD -MP -MF libmpcodecs/vd.d libmpcodecs/vd.c
libmpcodecs/vd.c:57: error: 'mpcodecs_vd_dshowserver' undeclared here (not in a function)
make: *** [libmpcodecs/vd.o] Error 1

Perhaps the mplayer svn code is not compatible with the dshow patch anymore?
Do anyone else have this problem too?

---

### Post by Bachstelze on 2009-09-19
> **GraceDivine said:**
> 
Perhaps the mplayer svn code is not compatible with the dshow patch anymore?

Works fine here with vanilla MPlayer. If you are going to use CoreAVC, you don't need ffmpeg-mt anyway.

---

### Post by GraceDivine on 2009-09-19
You are correct that it works with the latest svn (18-9-2009). Thanks for the tip!
I was just wanting to integrate CoreAVC with mplayer-mt once again, because my notebook is not that powerful, hence the need for dual-core usage. The last time I was able to build mplayer-mt with CoreAVC was back in August.  Thanks again!

---

### Post by Bachstelze on 2009-09-19
> **GraceDivine said:**
> The last time I was able to build mplayer-mt with CoreAVC was back in August.

Okay so it worked before, then. Give me a few minutes, I'll make a new patch.

---

### Post by Bachstelze on 2009-09-19
How are you getting the mplayer-mt sources? It seems to work fine here.

---

### Post by GraceDivine on 2009-09-19
From this git source:

git clone git://repo.or.cz/mplayer && cd mplayer && git checkout origin/mt && git submodule init && git submodule update

---

### Post by Bachstelze on 2009-09-19
Okay, try this one:

```
wget http://paste.ubuntu.com/274320/plain/ -qO - | patch -p0
```

---

### Post by GraceDivine on 2009-09-19
Your updated patch worked!
Thanks very much!

---

### Post by khelben1979 on 2009-09-19
If you have a powerful graphics card and a slow cpu, is it worth it? Or is it just a waste of time?

I tried CoreAVC on a Windows system last year and was impressed by the speed, but it don't feel good that you need to pay for this. I rather choose slower software which is free in this case. It would be interesting to see some bars/diagrams describing some fps from this CoreAVC.

---

### Post by Bachstelze on 2009-09-19
> **khelben1979 said:**
> If you have a powerful graphics card and a slow cpu, is it worth it? Or is it just a waste of time?

If your graphics card is a recent one by nvidia, you can try VDPAU instead. Otherwise, it absolutely doesn't matter how powerful your graphics card is, since it's the CPU that does all the decoding work.

---

### Post by khelben1979 on 2009-09-19
> **Bachstelze said:**
> If your graphics card is a recent one by nvidia, you can try VDPAU instead. Otherwise, it absolutely doesn't matter how powerful your graphics card is, since it's the CPU that does all the decoding work.

How recent? :) 
Will a nVidia Geforce7800GS do? :lolflag:

---

### Post by GraceDivine on 2009-09-19
VDPAU is great....if you own an NVIDIA card of course.
The CPU usage is extremely low, especially with the latest driver updates!
Also, NVIDIA recently released libvdpau which if ATI or Intel were smart, they would incorporate that into their proprietary code bases. 
Nonetheless, those of us stuck with AMD/ATI have to rely on coreAVC and mplayer-mt.....for now!

---

### Post by Bachstelze on 2009-09-19
> **khelben1979 said:**
> How recent? :) 
Will a nVidia Geforce7800GS do? :lolflag:

Sadly, no. You need a GeForce 8 series or above:

[http://en.wikipedia.org/wiki/VDPAU#Table_of_NVIDIA_GPUs](http://en.wikipedia.org/wiki/VDPAU#Table_of_NVIDIA_GPUs)

---

### Post by GraceDivine on 2009-09-19
khelben1979: I would much rather use free software as well!
My desktop is powerful enough to run without coreAVC + mplayer but my notebook is not.

Thanks again to Bachstelze for the help!

---

### Post by GraceDivine on 2009-10-01
It seems CoreAVC 1.9.5.0 Pro was recently released.
I'll build a package with this newer version, test it and report back soon.

---

### Post by wingsofgreed on 2009-10-08
First of all hello, i have to say that i really love the tutorials in this forum and that the yours especially have my attention.

But (there always a but) to be honest i am suffering a little because i am a newbie and when i tried to prove it appears this:

[I]htpc@htpc-desktop:~$ dshowserver -c CoreAVCDecoder.ax -s 1280x1024 -g 09571a4b-f1fe-4c60-9760de6d310c7c31 -b 12 -f 0x34363248 -o 0x30323449
No id specified, assuming test mode
Opening device
Fallo de segmentación[/I]

(failure of segmentation)

i realy apreciate if you can explain me when i made the mistaque, oh and like a said thanks i'v really enjoying my first  2 weeks a lot.:popcorn:

---

### Post by Bachstelze on 2009-10-08
We'll need more details about your configuration: version of Ubuntu, architecture (32 or 64 bit), etc.

---

### Post by kevinguillorytraining on 2009-10-09
Thanks for nice tutorial.

---

### Post by xfalcox on 2009-10-15
Hey,

Thanks A LOT for the tutorial, worked fine on my EEEPC 1000HA @ Karmic Beta UNR.

Is there a way to build a .deb to pass it to my friend?

---

### Post by GraceDivine on 2009-10-16
xfalcox, after you downloaded, patched, and configured the source code, just issue this command:

dpkg-buildpackage -rfakeroot

Or if you want to customize your ./configure , just do this:

DEB_BUILD_OPTIONS=" (your config options) fakeroot debian/rules binary

---

### Post by GraceDivine on 2009-10-16
By the way, the newer CoreAVC for windows works well with Bachstelze's code patch.

---

### Post by jafox on 2009-10-17
Using Karmic/LPIA.
1. Added repos:
rvm/mplayer
rvm/smplayer
2. Installed mplayer/smplayer from rvm ppa via apt
3. Installed dshowserver from coreavc-for-ubuntu ppa
4. Installed CoreAVC per normal instructions, registered codec.
5. added the vc=coreserve, option to my .mplayer/config file
6. mplayer -vc coreserve foo.mkv works fine, and plays well on my wimpy atom system****.


Playing with smplayer is pretty choppy though. I am trying to figure out which options smplayer is passing to mplayer that is slowing things down.

---

### Post by Master One on 2009-10-25
> **jafox said:**
> Playing with smplayer is pretty choppy though.
You have to disable the option "Allow drop of frames" (or something like that), which is enabled in SMPlayer by default.

I just did a new installation of Ubuntu 9.10-RC on a P4 2.4GHz with 1GB RAM, which should be enough for 720p playback (according to [this](http://coreavc.com/index.php?option=com_content&task=view&id=28&Itemid=1) info), installed MPlayer with CoreAVC 1.9.5 + SMPlayer, but CPU usage goes to 100%, mplayer says "Your system is too SLOW to play this", and although there are no visible distortions in the picture, audio is totally out of sync.

Is the use MPlayer with CoreAVC more demanding, than using CoreAVC on Windows? According to the requirements for 720p playback, my hardware is better than the recommended, nevertheless it's not enough.

As it was mentioned to work on an Eee PC, can an Atom N270 playback 720p material (downscaled to the display resolution of 1024x600)?

---

### Post by Bachstelze on 2009-10-25
> **Master One said:**
> 
I just did a new installation of Ubuntu 9.10-RC on a P4 2.4GHz with 1GB RAM, which should be enough for 720p playback (according to [this](http://coreavc.com/index.php?option=com_content&task=view&id=28&Itemid=1) info), installed MPlayer with CoreAVC 1.9.5 + SMPlayer, but CPU usage goes to 100%, mplayer says "Your system is too SLOW to play this", and although there are no visible distortions in the picture, audio is totally out of sync.[/code]

Does this also happen when you play your file in mplayer from the command line (not smplayer)?

[quote]As it was mentioned to work on an Eee PC, can an Atom N270 playback 720p material (downscaled to the display resolution of 1024x600)?

Yes, but remember that downscaling can increase CPU usage dramatically. Maybe that's where your problem comes from.

---

### Post by Master One on 2009-10-26
The message "Your system is too SLOW to play this" came when starting mplayer from a terminal, the effect with A/V out of sync came with both mplayer and SMPlayer (after all, SMPlayer is just a GUI frontent for mplayer).

When selecting "Allow drop of frames" A/V stayed in sync, but I had picture distortions, when there was movement in the video. When not allowing frame-drop, the picture was fine without any problems, but A/V was out of sync (jumping to another part in the video, A/V was in sync for a short time, but pretty much got lost again). Since the CPU was at 100% most of the time, with dshowserver alone more than 60% all the time, it's pretty clear, that the used P4 2.4Ghz was just not fast enough.

I did not try it on my Asus Eee PC 901GO with Atom N270 1.6Ghz yet, but I will do soon (that where the video has to be downscaled from 1280x720 to 1024x600, with my test on the P4 2.4Ghz I had it play in native resolution and 50%, but no difference there).

I already kicked the idea of using the P4 2.4GHz machine for my purpose, and I am just doing the same setup on a Dual-Core Atom 330 1.6Ghz with 2GB RAM, which is know is working fine for 720p AVC content. When finished, I'll setup my netbook the same way (additionally with the UNR package), then I can tell, if 720p AVC content can be played downscaled to 1024x600.

---

### Post by Master One on 2009-10-27
It's amazing! Playback of 720p AVC material downscaled to 1024x600 indeed works on my Asus Eee PC 901GO with its Intel Atom N270 1.6GHz (single core with hyperthreading). That's HD on the Eee! Really nice! :)

Looks like it makes full use of hyperthreading (two instances of dshowserver running, both recognized CPUs under heavy load).

Quite strange, that the Atom N270 with 3200 bogomips is doing well, whereas the P4 2.4GHz with ~ 4700 bogomips was too slow.

---

### Post by datscilly on 2009-10-30
First, thanks a lot for the guide Bachstelze. It allowed me to get more video performance out of my system than otherwise, and for that I'm grateful.   

After upgrading to karmic from jaunty, this custom build of mplayer stopped functioning (for this user) due to the shared library dependency libdirectfb-1.0.so.0 being not found. Karmic had replaced libdirectfb-1.0 by libdirectfb-1.2, and the symlink libdirectfb-1.0.so.0 is now gone and replaced with the symlink libdirectfb-1.2.so.0. Here's the error message that would be googled "libdirectfb-1.0.so.0 cannot open shared object file: No such file or directory."    

As I'm a new user and had to learn about shared library dependencies and review unix commands such as ldd and cp to fix this, I wanted to post a solution here. To restore the missing libdirectfb-1.0.so.0: 
```
cd /usr/lib sudo 
cp libdirectfb-1.2.so.0 libdirectfb-1.0.so.0
```    

(Or if creating copies of libdirectfb-1.2.so.0.7.0 is somehow bad, then  ```
cd /usr/lib sudo 
ln -s libdirectfb-1.2.so.0.7.0 libdirectfb-1.0.so.0
``` However, since I'm inexperienced I don't know if everyone has the same lib file libdirectfb-1.2.so.0.7.0.)

---

### Post by Bachstelze on 2009-10-30
Just recompile your MPlayer. ;) You'll get a new build that will depend on the new library.

---

### Post by Bachstelze on 2009-10-31
Guide updated for Karmic and CoreAVC 1.9.5.

---

### Post by Master One on 2009-10-31
That's strange. What problems is GCC 4.4 supposed to cause with compiling Mplayer?

I already made three installations of Mplayer with CoreAVC + SMplayer + SMplayer-Themes from SVN this way, all on fresh Karmic installs, and all just working fine, no problems detected so far.

---

### Post by Bachstelze on 2009-10-31
> **Master One said:**
> That's strange. What problems is GCC 4.4 supposed to cause with compiling Mplayer?

I already made three installations of Mplayer with CoreAVC + SMplayer + SMplayer-Themes from SVN this way, all on fresh Karmic installs, and all just working fine, no problems detected so far.

Google "mplayer GCC 4.4", and also see earlier posts on this thread. ;) Personally, I've had a lot of MPlayer crashes when compiling it with gcc 4.4. Of course, your mileage may vary, bur since it's not just me, I think it's better to play it safe and tell KArmic users to compile with gcc 4.3.

---

### Post by Master One on 2009-11-01
No idea, what's different here then, because I use this setup on a daily basis on three different machines, and not a single mplayer crash (yet). The only addition I made to your guide was```
aptitude build-dep mplayer smplayer
```before the mplayer ./configure.

---

### Post by TruebaseB on 2009-11-06
Thanks Bachstelze for this nice guide. :)

Hmm... I have a problem.

I followed all the steps,the MPlayer is working,but it seems that the acceleration doesn't.

Actually,i'm sure that it doesn't work because i have high cpu load when i play an hd video.

I also upgraded my gpu drivers to the latest.

I'm using the CoreAVC 1.9.5

Any idea about this problem?

Thanks.

---

### Post by Bachstelze on 2009-11-06
What are your hardware specs? The GPU drivers are irrelevant here: CoreAVC in Linux can't use the GPU like in Windows. If you want to use your GPU, have a look at VDPAU.

---

### Post by TruebaseB on 2009-11-07
Hi,

Actually i need gpu decoding,because i have a crappy cpu,which is just fine for my everyday use and some games i play on linux,but is the worst processor for 1080p video decoding (720p is running fine).

On windows with CoreAVC and Media Player Classic i have about 5-10% cpu load when i play 1080p videos,but on linux i have 100% cpu load,and the image stucks on the fast scenes.

I don't know what can i do since it's my first time i'm dealing with media players on linux,but i will try out the VDPAU.

Thanks for your response. :)

Btw my main hardware specs are:

Pentium 4 506 @ 4,5ghz
Nvidia Geforce 9800gtx
2gb Ram @ 1066mhz

---

### Post by Arup on 2009-11-07
> **TruebaseB said:**
> Hi,

Actually i need gpu decoding,because i have a crappy cpu,which is just fine for my everyday use and some games i play on linux,but is the worst processor for 1080p video decoding (720p is running fine).

On windows with CoreAVC and Media Player Classic i have about 5-10% cpu load when i play 1080p videos,but on linux i have 100% cpu load,and the image stucks on the fast scenes.

I don't know what can i do since it's my first time i'm dealing with media players on linux,but i will try out the VDPAU.

Thanks for your response. :)

Btw my main hardware specs are:

Pentium 4 506 @ 4,5ghz
Nvidia Geforce 9800gtx
2gb Ram @ 1066mhz


Even cheap 8400 nvidia would do VDPAU with ease, the 9600 would do super high rez. You need to follow instructions here and use the latest 190.42 drivers [http://ubuntuforums.org/showthread.php?t=1081070&highlight=mplayer+compile](http://ubuntuforums.org/showthread.php?t=1081070&highlight=mplayer+compile)

---

### Post by TruebaseB on 2009-11-07
Thank you,i'll do my tests later.:)

---

### Post by ClockworkMonk on 2009-11-08
Have followed the instructions as best I can, including using gcc 4.3, but make bombs out (after many, many warnings - is that normal?) with

```
libmpcodecs/vd.o:(.rodata+0x8): undefined reference to `mpcodecs_vd_dshowserver'
libvo/sub.o: In function `vo_update_text_teletext':
sub.c:(.text+0x1e07): undefined reference to `force_load_font'
sub.c:(.text+0x1e16): undefined reference to `osd_font_scale_factor'
sub.c:(.text+0x1e1c): undefined reference to `osd_font_scale_factor'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1

```

Any help welcome. 

CWM

---

### Post by wisekki on 2009-11-09
Same here with 9.10.. altough not exactly the same output as above, but something to do with fonts i guess :)

```

libvo/sub.o: In function `vo_update_text_teletext':
sub.c:(.text+0x1e07): undefined reference to `force_load_font'
sub.c:(.text+0x1e16): undefined reference to `osd_font_scale_factor'
sub.c:(.text+0x1e1c): undefined reference to `osd_font_scale_factor'
collect2: ld returned 1 exit status
make: *** [mencoder] Error 1
make: *** Waiting for unfinished jobs....
libvo/sub.o: In function `vo_update_text_teletext':
sub.c:(.text+0x1e07): undefined reference to `force_load_font'
sub.c:(.text+0x1e16): undefined reference to `osd_font_scale_factor'
sub.c:(.text+0x1e1c): undefined reference to `osd_font_scale_factor'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1

```

Any kind of help is appreciated. :)

 - Antti

---

### Post by Bachstelze on 2009-11-09
No problem here, on both 32 and 64 bits. Can you paste the **entire** output of ./configure ?

---

### Post by wisekki on 2009-11-09
Okay problem solved for me. I just installed libfreetype6, libfontconfig1 and their dev-packages. 

But for some reason mplayer plays .mkv for a few minutes and then crashes saying:
```

glibc detected *** /opt/mplayer/bin/mplayer: free(): invalid next size(fast): 0x09187448 ***
Backtrace:
/lib/tls/i686/cmov/libc.so.6[0xb72abff1] ... and so on..

Mplayer interrupted by signal 6 in module: decode_audio
```

..and this happens with every movie I have.

Is there something wrong with Karmic's audio drivers or smthng like that? Worked nicely on 9.04...

---

### Post by Bachstelze on 2009-11-09
Looks like the kind of crashes I got when building MPlayer with gcc 4.4. Did you use 4.3?

---

### Post by wisekki on 2009-11-09
Yes I did.. just like it was explained in the howto.. CC=gcc-4.3 ./configure

---

### Post by ClockworkMonk on 2009-11-09
OK - I had libfreetype6 and libfontconfig1 installed, but not their dev files. Installed said dev files, and now get a different make error - should I remove everything and start again from clean? 

For reference, this is the new make complaint:

```
libmpcodecs/vd.o:(.rodata+0x8): undefined reference to `mpcodecs_vd_dshowserver'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1

```

And, if it is still of interest, here's the ./configure output. Had to do it as root - is that right, or is that a sign of something else untoward?

```
Checking for cc version ... 4.4.1 
Detected operating system: Linux
Detected host architecture: i386
Checking for host cc ... cc 
Checking for cross compilation ... no 
Checking for CPU vendor ... GenuineIntel (6:14:8) 
Checking for CPU type ...  Genuine Intel(R) CPU           T2300  @ 1.66GHz 
Checking for kernel support of mmx ... yes 
Checking for kernel support of mmxext ... yes 
Checking for kernel support of sse ... yes 
Checking for kernel support of sse2 ... yes 
Checking for kernel support of cmov ... yes 
Checking for mtrr support ... yes 
Checking for GCC & CPU optimization abilities ... native 
Checking for byte order ... little-endian 
Checking for extern symbol prefix ...  
Checking for assembler support of -pipe option ... yes 
Checking for compiler support of named assembler arguments ... yes 
Checking for assembler (as ) ... ok 
Checking for .align is a power of two ... no 
Checking for 10 assembler operands ... yes 
Checking for ebx availability ... yes 
Checking for PIC ... no 
Checking for yasm ... no 
Checking for bswap ... yes 
Checking for Linux kernel version ... 2.6.31-14-generic, ok 
Checking for -lposix ... no 
Checking for -lm ... yes 
Checking for langinfo ... yes 
Checking for language ... messages: en - man pages: en - documentation: en 
Checking for enable sighandler ... yes 
Checking for runtime cpudetection ... no 
Checking for restrict keyword ... restrict 
Checking for __builtin_expect ... yes 
Checking for kstat ... no 
Checking for posix4 ... no 
Checking for llrint ... yes 
Checking for log2 ... yes 
Checking for lrint ... yes 
Checking for lrintf ... yes 
Checking for round ... yes 
Checking for roundf ... yes 
Checking for truncf ... yes 
Checking for mkstemp ... yes 
Checking for nanosleep ... yes 
Checking for socklib ... yes 
Checking for arpa/inet.h ... yes 
Checking for inet_pton() ... yes 
Checking for inet_aton() ... yes 
Checking for socklen_t ... yes 
Checking for closesocket() ... no 
Checking for network ... yes 
Checking for inet6 ... yes 
Checking for gethostbyname2 ... yes 
Checking for inttypes.h (required) ... yes 
Checking for int_fastXY_t in inttypes.h ... yes 
Checking for malloc.h ... yes 
Checking for memalign() ... yes 
Checking for posix_memalign() ... yes 
Checking for alloca.h ... yes 
Checking for fastmemcpy ... yes 
Checking for mman.h ... yes 
Checking for dynamic loader ... yes 
Checking for dynamic a/v plugins support ... no 
Checking for pthread ... yes (using -lpthread)
Checking for w32threads ... no (using pthread instead)
Checking for rpath ... no 
Checking for iconv ... yes 
Checking for soundcard.h ... yes (sys/soundcard.h)
Checking for sys/dvdio.h ... no 
Checking for sys/cdio.h ... no 
Checking for linux/cdrom.h ... yes 
Checking for dvd.h ... no 
Checking for termcap ... no 
Checking for termios ... yes (using sys/termios.h)
Checking for shm ... yes 
Checking for strsep() ... yes 
Checking for vsscanf() ... yes 
Checking for swab() ... yes 
Checking for POSIX select() ... yes 
Checking for audio select() ... yes 
Checking for gettimeofday() ... yes 
Checking for glob() ... yes 
Checking for setenv() ... yes 
Checking for sys/sysinfo.h ... yes 
Checking for Apple IR ... yes 
Checking for pkg-config ... yes 
Checking for Samba support (libsmbclient) ... no 
Checking for tdfxfb ... no 
Checking for s3fb ... no 
Checking for wii ... no 
Checking for tdfxvid ... no 
Checking for xvr100 ... no 
Checking for tga ... yes 
Checking for md5sum support ... yes 
Checking for yuv4mpeg support ... yes 
Checking for bl ... no 
Checking for DirectFB ... no 
Checking for X11 headers presence ... no (check if the dev(el) packages are installed)
Checking for X11 ... no (check if the dev(el) packages are installed)
Checking for Xss screensaver extensions ... no 
Checking for DPMS ... no 
Checking for Xv ... no 
Checking for XvMC ... no 
Checking for VDPAU ... no 
Checking for Xinerama ... no 
Checking for Xxf86vm ... no 
Checking for XF86keysym ... no 
Checking for DGA ... no 
Checking for 3dfx ... no 
Checking for VIDIX ... yes 
Checking for VIDIX PCI device name database ... yes 
Checking for VIDIX dhahelper support ... no 
Checking for VIDIX svgalib_helper support ... no 
Checking for /dev/mga_vid ... no 
Checking for xmga ... no 
Checking for GGI ... no 
Checking for GGI extension: libggiwmh ... no 
Checking for AA ... no 
Checking for CACA ... no 
Checking for SVGAlib ... no 
Checking for FBDev ... yes 
Checking for DVB ... no 
Checking for DVB HEAD ... yes 
Checking for OpenGL ... no 
Checking for PNG support ... no 
Checking for MNG support ... no 
Checking for JPEG support ... no 
Checking for PNM support ... yes 
Checking for GIF support ... no 
Checking for VESA support ... no 
Checking for SDL ... no 
Checking for DXR2 ... no 
Checking for DXR3/H+ ... no 
Checking for IVTV TV-Out (pre linux-2.6.24) ... no 
Checking for V4L2 MPEG Decoder ... yes 
Checking for OSS Audio ... yes 
Checking for aRts ... no 
Checking for EsounD ... no 
Checking for NAS ... no 
Checking for pulse ... no 
Checking for JACK ... no 
Checking for OpenAL ... no 
Checking for ALSA audio ... no 
Checking for Sun audio ... no 
Checking for VCD support ... yes 
Checking for dvdread ... yes (internal)
Checking for internal libdvdcss ... yes 
Checking for cdparanoia ... no 
Checking for libcdio ... no 
Checking for bitmap font support ... yes 
Checking for freetype >= 2.0.9 ... yes 
Checking for fontconfig ... yes 
Checking for SSA/*** support ... yes 
Checking for fribidi with charsets ... no 
Checking for ENCA ... no 
Checking for zlib ... yes 
Checking for bzlib ... no 
Checking for RTC ... yes 
Checking for liblzo2 support ... no 
Checking for mad support ... no 
Checking for Twolame ... no 
Checking for Toolame ... no 
Checking for OggVorbis support ... yes (internal Tremor)
Checking for libspeex (version >= 1.1 required) ... no 
Checking for OggTheora support ... no 
Checking for internal mp3lib support ... yes 
Checking for liba52 support ... yes (internal)
Checking for internal libmpeg2 support ... yes 
Checking for libdca support ... no 
Checking for libmpcdec (musepack, version >= 1.2.1 required) ... no 
Checking for FAAC support ... no (in libavcodec: no)
Checking for FAAD2 support ... yes (internal floating-point)
Checking for LADSPA plugin support ... no 
Checking for libbs2b audio filter support ... no 
Checking for Win32 codecs ... yes (using /usr/local/lib/win32)
Checking for XAnim codecs ... yes (using /usr/local/lib/win32)
Checking for RealPlayer codecs ... yes (using /usr/local/lib/win32)
Checking for QuickTime codecs ... yes 
Checking for Nemesi Streaming Media libraries ... no 
Checking for LIVE555 Streaming Media libraries ... no 
Checking for FFmpeg libavutil ... yes (static)
Checking for FFmpeg libavcodec ... yes (static)
Checking for FFmpeg libavformat ... yes (static)
Checking for FFmpeg libpostproc ... yes (static)
Checking for FFmpeg libswscale ... yes (static)
Checking for libopencore_amr narrowband ... no 
Checking for libopencore_amr wideband ... no 
Checking for libdv-0.9.5+ ... no 
Checking for Xvid ... no 
Checking for Xvid two pass plugin ... no 
Checking for x264 ... no (in libavcodec: no)
Checking for libdirac ... no 
Checking for libschroedinger ... no 
Checking for libnut ... no 
Checking for zr ... no 
Checking for libmp3lame ... no (in libavcodec: no)
Checking for mencoder ... yes 
Checking for UnRAR executable ... yes 
Checking for TV interface ... yes 
Checking for DirectShow TV interface ... no 
Checking for Video 4 Linux TV interface ... yes 
Checking for Video 4 Linux 2 TV interface ... yes 
Checking for Radio interface ... no 
Checking for Capture for Radio interface ... no 
Checking for Video 4 Linux 2 Radio interface ... no 
Checking for Video 4 Linux Radio interface ... no 
Checking for Video 4 Linux 2 MPEG PVR interface ... yes 
Checking for ftp ... yes 
Checking for vstream client ... no 
Checking for OSD menu ... no 
Checking for Subtitles sorting ... yes 
Checking for XMMS inputplugin support ... no 
Checking for GUI ... no
Checking for automatic gdb attach ... no 
Checking for compiler support for noexecstack ... yes 
Checking for joystick ... no 
Checking for lirc ... no 
Checking for lircc ... no 
Checking for DVD support (libdvdnav) ... yes (internal)
Creating config.mak
Creating config.h

Config files successfully generated by ./configure  !

  Install prefix: /usr/local
  Data directory: /usr/local/share/mplayer
  Config direct.: /usr/local/etc/mplayer

  Byte order: little-endian
  Optimizing for: native

  Languages:
    Messages/GUI: en
    Manual pages: en
    Documentation: en

  Enabled optional drivers:
    Input: dvdnav(internal) ftp pvr tv-v4l2 tv-v4l tv libdvdcss(internal) dvdread(internal) vcd dvb network 
    Codecs: libavcodec(internal) qtx real xanim win32 faad2(internal) libmpeg2(internal) liba52(internal) mp3lib(internal) tremor(internal) 
    Audio output: oss v4l2 mpegpes(dvb) 
    Video output: v4l2 pnm mpegpes(dvb) fbdev cvidix yuv4mpeg md5sum tga 

  Disabled optional drivers:
    Input: vstream radio tv-dshow live555 nemesi cddb cdda smb 
    Codecs: libschroedinger libdirac x264 xvid libdv libopencore_amrwb libopencore_amrnb faac musepack libdca libtheora speex toolame twolame libmad liblzo gif 
    Audio output: sun alsa openal jack pulse nas esd arts ivtv dxr2 sdl 
    Video output: zr zr2 ivtv dxr3 dxr2 sdl vesa gif89a jpeg png opengl svga caca aa ggi xmga mga xvidix winvidix 3dfx dga vdpau xvmc xv x11 dfbmga directfb bl xvr100 tdfx_vid wii s3fb tdfxfb 

'config.h' and 'config.mak' contain your configuration options.
Note: If you alter theses files (for instance CFLAGS) MPlayer may no longer
      compile *** DO NOT REPORT BUGS if you tweak these files ***

'make' will now compile MPlayer and 'make install' will install it.
Note: On non-Linux systems you might need to use 'gmake' instead of 'make'.

Please check mtrr settings at /proc/mtrr (see DOCS/HTML//video.html#mtrr)

Check configure.log if you wonder why an autodetection failed (make sure
development headers/packages are installed).

NOTE: The --enable-* parameters unconditionally force options on, completely
skipping autodetection. This behavior is unlike what you may be used to from
autoconf-based configure scripts that can decide to override you. This greater
level of control comes at a price. You may have to provide the correct compiler
and linker flags yourself.
If you used one of these options (except --enable-gui and similar ones that
turn on internal features) and experience a compilation or linking failure,
make sure you have passed the necessary compiler/linker flags to configure.

If you suspect a bug, please read DOCS/HTML//bugreports.html.

```

Ta!

CWM

---

### Post by Master One on 2009-11-09
Guys, how about just doing a "aptitude build-dep mplayer" before the "./configure" of mplayer-SVN? That step makes sure, that everything needed is in place. This is how I did it on 4 machines, and absolutely no problems so far, even with Karmic's default GCC 4.4.

---

### Post by wisekki on 2009-11-09
ClockworkMonk: did you use gcc 4.3? :)

Master One: thnx for the tip.. i did not even know you could use it like that :( stupid of me...

---

### Post by Bachstelze on 2009-11-10
> **ClockworkMonk said:**
> Had to do it as root - is that right, or is that a sign of something else untoward?

Definitely not right.

---

### Post by Bachstelze on 2009-11-10
> **Master One said:**
> Guys, how about just doing a "aptitude build-dep mplayer" before the "./configure" of mplayer-SVN?

Because it installs *a lot* of unnecessary things.

---

### Post by Master One on 2009-11-10
> **Bachstelze said:**
> Because it installs *a lot* of unnecessary things.
I know, but that does not really hurt, and it's definitely better then missing some dependencies (also fixes the ALSA/Pulse audio issue, which otherwise would require manual fiddling). Since that step is the only relevant difference to your guide, I suspect that one to prevent the mentioned GCC 4.4 issues as well (maybe by the use of some external components, if ./configure detects their presence?).

---

### Post by wisekki on 2009-11-10
> **Bachstelze said:**
> Because it installs *a lot* of unnecessary things.

How much unnecessary things? :) I'm using slow 3G-connection so I guess it's not an option for me :) --edit-- Okay it takes about 90MB and 22MB to download.. uh..

I know this goes beyond this guide but what kind of fiddling do I need to fix this pulse/alsa problem that I currently have?

---

### Post by Master One on 2009-11-10
The "aptitude build-dep mplayer" pulls about 50MB in, if I remember right, so it's not really tragic. ALSA/Pulse support is not compiled into mplayer, if you don't have the needed dev-packages installed, which is what "aptitude build-dep mplayer" takes care of. If you don't want to pull in all mplayer build-deps, you have to watch the output of ./configure, and install the desired missing dev-packages manually (followed by another ./configure and then make).

Bachstelze, sorry if you think this is OT and not to be covered by your guide, but in the end, more people will ask about it, or wonder, why a manual compile of mplayer is missing functionality over the mplayer from the official repos.

---

### Post by wisekki on 2009-11-10
> **Master One said:**
> ALSA/Pulse support is not compiled into mplayer, if you don't have the needed dev-packages installed, which is what "aptitude build-dep mplayer" takes care of. If you don't want to pull in all mplayer build-deps, you have to watch the output of ./configure, and install the desired missing dev-packages manually (followed by another ./configure and then make).

Well that is what I did.. I watched configure closely and installed manually every -dep package that I wanted/needed. But still my audio is very buggy and mplayer crashes. Doesn't matter if I use pulse or alsa.. :(

---

### Post by Nate53085 on 2009-11-10
I have tried this guide with 2 different computers (one jaunty, one karmic) and I can't get it to work.  On both machines coreserve tests fine, but mplayer simply outputs black and doesn't look like its playing.  An example output from mplayer: 

mplayer -ao null -vc coreserve Serenity\ -\ HD\ DVD\ Trailer.mp4 

MPlayer SVN-r29813-4.3.3 (C) 2000-2009 MPlayer Team
141 audio & 307 video codecs

Playing Serenity - HD DVD Trailer.mp4.
libavformat file format detected.
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  [H264]  1280x720  24bpp  23.976 fps  4674.1 kbps (570.6 kbyte/s)
Clip info:
 major_brand: isom
 minor_version: 1
 compatible_brands: isomavc1
 author: Universal Pictures
 title: Serenity - HD DVD Trailer
 year: 2005
==========================================================================
Forced video codec: coreserve
Opening video decoder: [dshowserver] DirectShowServer video codecs
Opening device
Called unk_IsDebuggerPresent
len: 992
ProductVersion: 1.9.5
Win32 LoadLibrary failed to load: nvcuvid.dll, /usr/lib/win32/nvcuvid.dll, /usr/local/lib/win32/nvcuvid.dll
Decoder supports the following YUV formats: YUY2 UYVY YV12 I420 
Decoder is capable of YUV output (flags 0x2b)
Setting fmt
Starting
Initialization is complete
Dshowserver Connected to host
[PP] Using codec's postprocessing, max q = 4.
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 1280x720 => 1280x720 Planar YV12 
Found DirectShow filterSelected video codec: [coreserve] vfm: dshowserver (CoreAVC DShow H264 decoder 1.3 for x86 - [http://corecodec.org/](http://corecodec.org/))
==========================================================================
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
AUDIO: 48000 Hz, 2 ch, s16le, 127.5 kbit/8.30% (ratio: 15942->192000)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [null] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...

Too many audio packets in the buffer: (4096 in 1400938 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:   0.2 V:   0.0 A-V:  0.224 ct:  0.000   0/  0 ??% ??% ??,?% 1408 0 
Destroying filter
Exiting... (End of file)
************
in-frames: 2102 out-frames: 0
************

Notice I supplied -ao null so that I could be sure there wasn't an issue with a sound card or something.

Any help would be greatly appreciated, thanks.

---

### Post by arryo on 2009-11-10
Thanks [[COLOR=#d40000]**Bachstelze**[/COLOR]]("http://ubuntuforums.org/member.php?u=51114") for your great tutorial. I managed to install successfully. But after installing SMplayer and Mplayer-mt from RVM/PPA, I no longer play mplayer from command line any more, still can play from SMPlayer though. Here the error

vobsub:mpeg_run error
no matching VOBSUB language found!
seek failed

Also when I play with smplayer, I already choose 5.1 for audio but in my receiver, it shows only 3 channels working. If I play the same file on xbmc, it shows DTS correctly

Thank you

Edited: I decided to remove everything and reinstall only mplayer with coreavc, but the same error about vobsub again

---

### Post by ClockworkMonk on 2009-11-12
> **Master One said:**
> The "aptitude build-dep mplayer" pulls about 50MB in, if I remember right, so it's not really tragic. ALSA/Pulse support is not compiled into mplayer, if you don't have the needed dev-packages installed, which is what "aptitude build-dep mplayer" takes care of. If you don't want to pull in all mplayer build-deps, you have to watch the output of ./configure, and install the desired missing dev-packages manually (followed by another ./configure and then make).

Bachstelze, sorry if you think this is OT and not to be covered by your guide, but in the end, more people will ask about it, or wonder, why a manual compile of mplayer is missing functionality over the mplayer from the official repos.

Well, I did the build-dep mplayer thang. Didn't make any difference, still getting the make error and still needs to be compiled as root, so I imagine I've got some dodgy permissions somewhere. I'll have another go at the weekend after ripping everything out and starting again from scratch. Real life still getting in the way of satisfying Linux hackery!

CWM

---

### Post by Bachstelze on 2009-11-13
> **Master One said:**
> 
Bachstelze, sorry if you think this is OT and not to be covered by your guide, but in the end, more people will ask about it, or wonder, why a manual compile of mplayer is missing functionality over the mplayer from the official repos.

I don't mind people discussing it here, but since those are features I don't use, I can't help you with them.

---

### Post by Master One on 2009-11-20
It seems, I am having a strange problem here with Mplayer SVN + CoreAVC not being able in playing MP4 files.

I just downloaded the [first episode](http://www.youtube.com/watch?v=4UVy7uUceXw) of [Riese - The Series](http://www.youtube.com/user/Riesetheseries) (which is a free webseries, means a legal download), using the Firefox plugin "DownloadHelper". There are several versions of the file available for download, I chose the [HQ22] file with .mp4 ending, which is 720p using H.264 / AVC video codec, and MPEG-4 AAC audio codec.

When I open the file in SMplayer, it seems to be starting to playback, I can hear a fraction of audio, no video, then it just quits.

When I start with mplayer on the commandline, it get to "Starting playback...", the video video opens, no video, and after some time (timeout), it just quits with the lines below the ""Starting playback...":```
$ mplayer -ao pulse 'Episode 1 - Hunt.mp4'
MPlayer SVN-r29814-4.4.1 (C) 2000-2009 MPlayer Team
141 audio & 307 video codecs
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Episode 1 - Hunt.mp4.
libavformat file format detected.
[lavf] Audio stream found, -aid 0
[lavf] Video stream found, -vid 1
VIDEO:  [H264]  1280x720  24bpp  23.976 fps  1750.4 kbps (213.7 kbyte/s)
Clip info:
 major_brand: mp42
 minor_version: 0
 compatible_brands: isomavc1mp42
Xlib:  extension "NV-GLX" missing on display ":0.0".
[vdpau] Error when calling vdp_device_create_x11: 1
==========================================================================
Forced video codec: coreserve
Opening video decoder: [dshowserver] DirectShowServer video codecs
Opening device
Called unk_IsDebuggerPresent
len: 992
ProductVersion: 1.9.5
Win32 LoadLibrary failed to load: nvcuvid.dll, /usr/lib/win32/nvcuvid.dll, /usr/local/lib/win32/nvcuvid.dll
Decoder supports the following YUV formats: YUY2 UYVY YV12 I420 
Decoder is capable of YUV output (flags 0x2b)
Setting fmt
Starting
Initialization is complete
Dshowserver Connected to host
[PP] Using codec's postprocessing, max q = 4.
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 1280x720 => 1280x720 Planar YV12 
Found DirectShow filterSelected video codec: [coreserve] vfm: dshowserver (CoreAVC DShow H264 decoder 1.3 for x86 - http://corecodec.org/)
==========================================================================
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
AUDIO: 44100 Hz, 2 ch, s16le, 119.3 kbit/8.45% (ratio: 14914->176400)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...

Too many audio packets in the buffer: (4096 in 1429060 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:   0.2 V:   0.0 A-V:  0.205 ct:  0.000   0/  0 ??% ??% ??,?% 1470 0 
Destroying filter
Exiting... (End of file)
************
in-frames: 2278 out-frames: 0
************
```
When starting with the "-nosound" option, exactly the same happens, so it gets till the line "Starting playback...", the video window opens, but no video, and nothing more happens, although it does not time out and just stays that way, till I manually abort with Strg-C, which leads to:```
Audio: no sound
Starting playback...


MPlayer interrupted by signal 2 in module: decode video
Got illegal command 0
Destroying filter??% ??% ??,?% 0 0 
Exiting... (Quit)
```
This should not have anything to do with the FAAC codec (libfaac0 is installed, as was libfaac-dev before compiling mplayer), or PulseAudio/ALSA/OSS.

Can anybody here please try to play the mentioned file with the manually compiled Mplayer from SVN with CoreAVC support?

I am quite sure, that this can not be a general problem, and maybe I am just missing something here. A search on the web did not lead to anything useful, and the downloaded .mp4 file itself is OK (can be played with Totem Video-Player, although the result is totally unacceptable here on my low-power machine due to the missing CoreAVC support).

P.S. That youtube-download is the only .mp4 file I have so far, so I don't know, if it can not play any .mp4 file, or just that one.

EDIT: Ok, the issue most likely does not have anything to do with the container format, because I just downloaded the version [HQ35] of that video in .flv format, and it results in the same problem, so can not be opened in Mplayer SVN with CoreAVC, but works fine in Totem Video-Player. Must have something to do either with the AAC audio, or the way this file is encoded/multiplexed. Somebody here using Mplayer SVN with CoreAVC please try this file.

---

### Post by Bachstelze on 2009-11-20
I could try it if I knew how to download a YouTube video. ^^;

---

### Post by Master One on 2009-11-20
Just install the "DownloadHelper" add-on in Firefox, you will then find a new button besides "Home" in the navigation-bar, visit the link in my previous post for Riese Episode 1 on youtube, the DownloadHelper button gets active, and shows you the available videos on that page. There are several different files to choose from, the one that starts with [HQ22] is the .mp4 file with 720p resolution, [HQ35] is a .flv file in SD resolution, both use the same codecs (H.264/AVC and AAC). Then it's just click and download, really pretty straight forward (just installed that add-on myself today, because obviously it should have given a better viewing result in SMplayer SVN with CoreAVC, than with these stupid webbased Flash videoplayers).

---

### Post by mc4man on 2009-11-20
> Too many audio packets in the buffer:

With a run of the mill aac stream like twhat's on your video that error could be caused by having a different version of libfaad installed from what  mplayer was built off of.

Try forcing the audio decoding to avcodec instead 

mplayer -ac ffaac -ao pulse 'Episode 1 - Hunt.mp4'


> I could try it if I knew how to download a YouTube video

if you don't wish to install anything then just open the link, switch to hd or leave at sd, pause the player if you don't want to watch.

Go about your business and a few min.'s later you can grab the file from /tmp when it's fully buffered.

---

### Post by Master One on 2009-11-21
> **mc4man said:**
> With a run of the mill aac stream like twhat's on your video that error could be caused by having a different version of libfaad installed from what  mplayer was built off of.

Try forcing the audio decoding to avcodec instead 

mplayer -ac ffaac -ao pulse 'Episode 1 - Hunt.mp4'
That looked plausible, and gave hope (although I do not recall any libfaad update since the compilation of mplayer), but did not change anything:```
$ mplayer -ac ffaac -ao pulse 'Episode 1 - Hunt.mp4'MPlayer SVN-r29814-4.4.1 (C) 2000-2009 MPlayer Team
141 audio & 307 video codecs
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Episode 1 - Hunt.mp4.
libavformat file format detected.
[lavf] Audio stream found, -aid 0
[lavf] Video stream found, -vid 1
VIDEO:  [H264]  1280x720  24bpp  23.976 fps  1750.4 kbps (213.7 kbyte/s)
Clip info:
 major_brand: mp42
 minor_version: 0
 compatible_brands: isomavc1mp42
Xlib:  extension "NV-GLX" missing on display ":0.0".
[vdpau] Error when calling vdp_device_create_x11: 1
==========================================================================
Forced video codec: coreserve
Opening video decoder: [dshowserver] DirectShowServer video codecs
Opening device
Called unk_IsDebuggerPresent
len: 992
ProductVersion: 1.9.5
Win32 LoadLibrary failed to load: nvcuvid.dll, /usr/lib/win32/nvcuvid.dll, /usr/local/lib/win32/nvcuvid.dll
Decoder supports the following YUV formats: YUY2 UYVY YV12 I420 
Decoder is capable of YUV output (flags 0x2b)
Setting fmt
Starting
Initialization is complete
Dshowserver Connected to host
[PP] Using codec's postprocessing, max q = 4.
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 1280x720 => 1280x720 Planar YV12 
Found DirectShow filterSelected video codec: [coreserve] vfm: dshowserver (CoreAVC DShow H264 decoder 1.3 for x86 - http://corecodec.org/)
==========================================================================
==========================================================================
Forced audio codec: ffaac
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 119.3 kbit/8.45% (ratio: 14914->176400)
Selected audio codec: [ffaac] afm: ffmpeg (FFmpeg AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...

.
.
. (some waiting for a timeout)
.
.

Too many audio packets in the buffer: (4096 in 1429060 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:   0.2 V:   0.0 A-V:  0.197 ct:  0.000   0/  0 ??% ??% ??,?% 1457 0 
Destroying filter
Exiting... (End of file)
************
in-frames: 2278 out-frames: 0
************
```
This has to be a different problem.

I really would like to get some feedback from others, experiencing the same problem.

> **mc4man said:**
> if you don't wish to install anything then just open the link, switch to hd or leave at sd, pause the player if you don't want to watch.

Go about your business and a few min.'s later you can grab the file from /tmp when it's fully buffered.
Cool, didn't know that, but the DownloadHelper add-on is so much more comfortable, and even supports conversion.

---

### Post by Master One on 2009-11-23
There is definitely something wrong with this Mplayer installment, I just tried with the HQ35 version of the youtube video from the [SGU Vancouver Press-Conference](http://www.youtube.com/watch?v=HgPYaROAhlc), which is 640x480 H.264/AVC, and Mplayer shows the same behavior as described above, whereas Totem Video-Player can play that file just fine. That means the issue is not just limited to the way, they encoded/muxed the Rise - The Series videos.

I guess, the problem can be seen with any .mp4 or .flv file from youtube, so please, somebody here have a look, so that I know, that others are experiencing the same issue as well, and maybe somebody knows a solution for that problem (still can't believe that Mplayer is not supposed to be able to play such files).

---

### Post by Bachstelze on 2009-11-23
It seems to be some weird interaction bug between MPlayer and CoreAVC. MPlayer plays the files fine without CoreAVC, and CoreAVC plays them fine in Windows.

---

### Post by BagRackRider on 2009-11-24
I have the exact same problem with MP4 files, however these are NOT from youtube. Would be nice if someone actually finds a fix for this.

---

### Post by Bachstelze on 2009-11-24
> **BagRackRider said:**
> I have the exact same problem with MP4 files, however these are NOT from youtube. Would be nice if someone actually finds a fix for this.

I have a ton of mp4 files that work just fine, so without more detail...

---

### Post by Nate53085 on 2009-11-24
I am running into the same problem.  I would be happy to troubleshoot and give you any information that is required to sort it out, just point me in the right direction.

This is the video I have been using for testing:

[http://www.dvdloc8.com/clip.php?movieid=8419&clipid=2](http://www.dvdloc8.com/clip.php?movieid=8419&clipid=2)

Its the serenity trailer from this website: [http://www.h264info.com/clips.html](http://www.h264info.com/clips.html)

When playing this movie I get the following:

./mplayer -vc coreserve -ao null ../../Serenity\ -\ HD\ DVD\ Trailer.mp4 

MPlayer SVN-r29813-4.3.3 (C) 2000-2009 MPlayer Team
3DNow supported but disabled
3DNowExt supported but disabled
141 audio & 307 video codecs

Playing ../../Serenity - HD DVD Trailer.mp4.
libavformat file format detected.
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  [H264]  1280x720  24bpp  23.976 fps  4674.1 kbps (570.6 kbyte/s)
Clip info:
 major_brand: isom
 minor_version: 1
 compatible_brands: isomavc1
 author: Universal Pictures
 title: Serenity - HD DVD Trailer
 year: 2005
==========================================================================
Forced video codec: coreserve
Opening video decoder: [dshowserver] DirectShowServer video codecs
Opening device
Called unk_IsDebuggerPresent
len: 992
ProductVersion: 1.9.5
Win32 LoadLibrary failed to load: nvcuvid.dll, /usr/lib/win32/nvcuvid.dll, /usr/local/lib/win32/nvcuvid.dll
Decoder supports the following YUV formats: YUY2 UYVY YV12 I420 
Decoder is capable of YUV output (flags 0x2b)
Setting fmt
Starting
Initialization is complete
Dshowserver Connected to host
[PP] Using codec's postprocessing, max q = 4.
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 1280x720 => 1280x720 Planar YV12 
Found DirectShow filterSelected video codec: [coreserve] vfm: dshowserver (CoreAVC DShow H264 decoder 1.3 for x86 - [http://corecodec.org/](http://corecodec.org/))
==========================================================================
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
AUDIO: 48000 Hz, 2 ch, s16le, 127.5 kbit/8.30% (ratio: 15942->192000)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [null] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...

Too many audio packets in the buffer: (4096 in 1400938 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:   0.2 V:   0.0 A-V:  0.224 ct:  0.000   0/  0 ??% ??% ??,?% 1420 0 
Destroying filter
Exiting... (End of file)
************
in-frames: 2102 out-frames: 0
************



Mplayer opens a window of the correct size, but no updates occur.  The screen is either black or some smear of the windows underneath it.

---

### Post by BagRackRider on 2009-11-24
> **Bachstelze said:**
> I have a ton of mp4 files that work just fine, so without more detail...


This is the info i get from MediaInfo;
Video
ID                               : 1
Format                           : AVC
Format/Info                      : Advanced Video Codec
Format profile                   : Main@L3.1
Format settings, CABAC           : Yes
Format settings, ReFrames        : 4 frames
Codec ID                         : avc1
Codec ID/Info                    : Advanced Video Coding

Audio
ID                               : 2
Format                           : AAC
Format/Info                      : Advanced Audio Codec
Format version                   : Version 4
Format profile                   : LC
Format settings, SBR             : No
Codec ID                         : 40

---

### Post by Bachstelze on 2009-11-24
The dshowserver sources need to be patched (as per [this post]("http://code.google.com/p/coreavc-for-linux/issues/detail?id=93")). Move to the dir where your coreavc-for-linux sources are, download the attached patch, and run

```
make clean
patch -p0 < DS_VideoDecoder.c.diff
make
```

Then copy the new dshowserver binary over your old one. You don't need to rebuild MPlayer.

---

### Post by Bachstelze on 2009-11-24
Reported broken files now work fine:

```
firas@kano:~$ mplayer -vc coreserve dwhelper/Episode\ 1\ -\ Hunt.flv 
MPlayer SVN-r29962-4.3.4 (C) 2000-2009 MPlayer Team
141 audio & 309 video codecs

Playing dwhelper/Episode 1 - Hunt.flv.
libavformat file format detected.
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  [H264]  854x480  0bpp  23.976 fps  1033.9 kbps (126.2 kbyte/s)
Clip info:
 duration: 543
 starttime: 0
 totalduration: 543
 width: 854
 height: 480
 videodatarate: 1010
 audiodatarate: 96
 totaldatarate: 1113
 framerate: 24
 bytelength: 75636052
 canseekontime: true
 sourcedata: B4A7D0605
 purl: 
 pmsg: 
[VO_XV] It seems there is no Xvideo support for your video card available.
[VO_XV] Run 'xvinfo' to verify its Xv support and read
[VO_XV] DOCS/HTML/en/video.html#xv!
[VO_XV] See 'mplayer -vo help' for other (non-xv) video out drivers.
[VO_XV] Try -vo x11.
==========================================================================
Forced video codec: coreserve
Opening video decoder: [dshowserver] DirectShowServer video codecs
Opening device
Called unk_IsDebuggerPresent
len: 992
ProductVersion: 1.9.5
Win32 LoadLibrary failed to load: nvcuvid.dll, /usr/lib/win32/nvcuvid.dll, /usr/local/lib/win32/nvcuvid.dll
Decoder supports the following YUV formats: YUY2 UYVY YV12 I420 
Decoder is capable of YUV output (flags 0x2b)
Setting fmt
Starting
Initialization is complete
[PP] Using codec's postprocessing, max q = 4.
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [x11] 854x480 => 854x480 Planar YV12 
Dshowserver Connected to host
[swscaler @ 0xa4f99b0]using unscaled yuv420p -> rgb32 special converter
Found DirectShow filterSelected video codec: [coreserve] vfm: dshowserver (CoreAVC DShow H264 decoder 1.3 for x86 - http://corecodec.org/)
==========================================================================
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
FAAD: compressed input bitrate missing, assuming 128kbit/s!
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
[AO OSS] audio_setup: Can't open audio device /dev/dsp: No such file or directory
DVB card number must be between 1 and 4
AO: [null] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
************  2.5 A-V:  0.001 ct: -0.017   0/  0 21% 10%  1.4% 2 0              
in-frames: 63 out-frames: 62
************
Destroying filter
Exiting... (Quit)

```

Notice the line:

```
VIDEO:  [H264]  854x480  0bpp  23.976 fps  1033.9 kbps (126.2 kbyte/s)
```

The file had a stored FOURCC value of "H264", which wasn't recognized as being H.264 by dshowserver anymore (it was really like trying to open a xvid file with CoreAVC). Files that have a FOURCC value of "avc1" were not affected.

---

### Post by Bachstelze on 2009-11-24
Guide updated, and new precompiled dshowserver and registercodec binaries for 64 bit users uploaded.

---

### Post by BagRackRider on 2009-11-24
> **Bachstelze said:**
> The dshowserver sources need to be patched (as per [this post]("http://code.google.com/p/coreavc-for-linux/issues/detail?id=93")). Move to the dir where your coreavc-for-linux sources are, download the attached patch, and run

```
make clean
patch -p0 < DS_VideoDecoder.c.diff
make
```Then copy the new dshowserver binary over your old one. You don't need to rebuild MPlayer.

Hm.. aint that patch the same as the one in the first post?
[http://paste.ubuntu.com/327178/plain/](http://paste.ubuntu.com/327178/plain/)

So I basically did the whole dshowserver step in the guide again from the begining just to make sure I got it right.
And it WORKS now... and I was pretty sure I followed the guide step by step but apperently the patch-step went wrong or I just missed it.

---

### Post by Bachstelze on 2009-11-24
> **BagRackRider said:**
> Hm.. aint that patch the same as the one in the first post?
[http://paste.ubuntu.com/327178/plain/](http://paste.ubuntu.com/327178/plain/)


Yes it is, I just updated the guide. ;) I copied the patch to the pastebin because the URL to the original is a bit long.

---

### Post by BagRackRider on 2009-11-24
Yeah, obviously you changed the guide while I was reading the forum.. ;) 
Thanks for the detective work btw.

---

### Post by Master One on 2009-11-25
Yes, that patch fixed the problem. :)

Great guidance, great result (without it, all my low-power Atom hardware would be pretty much useless, since I usually only watch 720p content).

---

### Post by quvil on 2009-11-25
When I tried to test whether codec registration had worked (dshowserver -c CoreAVCDecoder.ax -s 1280x720 ...), dshowserver crashed with an assertion:

No id specified, assuming test mode
Opening device
dshowserver: malloc.c:3074: sYSMALLOc: Assertion `(old_top == (((mbinptr) (((char *) &((av)->bins[((1) - 1) * 2])) - __builtin_offsetof (struct malloc_chunk, fd)))) && old_size == 0) || ((unsigned long) (old_size) >= (unsigned long)((((__builtin_offsetof (struct malloc_chunk, fd_nextsize))+((2 * (sizeof(size_t))) - 1)) & ~((2 * (sizeof(size_t))) - 1))) && ((old_top)->size & 0x1) && ((unsigned long)old_end & pagemask) == 0)' failed.
Aborted

Did somebody encounter something similar? 

I compiled dshowserver statically according to the instructions on a system with Atom n280 running Karmic, and tried to use it on a 64 bit system with Core 2 Duo T7250 running Jaunty.

P.S.: site hosting a tarball with precompiled binaries was unavailable, I could not check whether it would behave differently.

---

### Post by Cesaar on 2009-11-26
> **quvil said:**
> When I tried to test whether codec registration had worked (dshowserver -c CoreAVCDecoder.ax -s 1280x720 ...), dshowserver crashed with an assertion:

No id specified, assuming test mode
Opening device
dshowserver: malloc.c:3074: sYSMALLOc: Assertion `(old_top == (((mbinptr) (((char *) &((av)->bins[((1) - 1) * 2])) - __builtin_offsetof (struct malloc_chunk, fd)))) && old_size == 0) || ((unsigned long) (old_size) >= (unsigned long)((((__builtin_offsetof (struct malloc_chunk, fd_nextsize))+((2 * (sizeof(size_t))) - 1)) & ~((2 * (sizeof(size_t))) - 1))) && ((old_top)->size & 0x1) && ((unsigned long)old_end & pagemask) == 0)' failed.
Aborted

Did somebody encounter something similar? 

I compiled dshowserver statically according to the instructions on a system with Atom n280 running Karmic, and tried to use it on a 64 bit system with Core 2 Duo T7250 running Jaunty.

P.S.: site hosting a tarball with precompiled binaries was unavailable, I could not check whether it would behave differently.

Hi, I got exactly the same crash, using 32bit system also running karmic

---

### Post by quvil on 2009-11-26
Indeed there is a problem with compiling dshowserver on Karmic and using it on Jaunty: I tried to compile on some old 32 bit Red Hat, and it worked. Maybe the problem is in gcc version (4.4.1 on Karmic).

---

### Post by christian667 on 2009-11-27
Hi there!
I did the tutorial and everything looked well.
I'm running a Ubuntu Karmic machine, and used
the CoreAVC with jaunty before without any problems.
But now I have audio and the video window, but now
video :(
This is the mplayer output without audio:

```

mplayer -vc CoreAVC -ao no-audio big_buck_bunny_720p_h264.mov 
MPlayer SVN-r29969-4.4.1 (C) 2000-2009 MPlayer Team
141 audio & 309 video codecs

Playing big_buck_bunny_720p_h264.mov.
libavformat file format detected.
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  [H264]  1280x720  24bpp  25.000 fps  3945.2 kbps (481.6 kbyte/s)
Clip info:
 major_brand: qt  
 minor_version: 537199360
 compatible_brands: qt  
==========================================================================
Forced video codec: CoreAVC
Opening video decoder: [dshowserver] DirectShowServer video codecs
Opening device
Called unk_IsDebuggerPresent
len: 992
ProductVersion: 1.9.5
Decoder supports the following YUV formats: YUY2 UYVY YV12 I420 
Decoder is capable of YUV output (flags 0x2b)
Setting fmt
Starting
Initialization is complete
Dshowserver Connected to host
[PP] Using codec's postprocessing, max q = 4.
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 1280x720 => 1280x720 Planar YV12 
Found DirectShow filterSelected video codec: [CoreAVC] vfm: dshowserver (CoreAVC DShow H264 decoder 1.3 for x86 - http://corecodec.org/)
==========================================================================
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
AUDIO: 48000 Hz, 2 ch, s16le, 428.6 kbit/27.90% (ratio: 53575->192000)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
No such audio driver 'no-audio'
Could not open/initialize audio device -> no sound.
Audio: no sound
Starting playback...
V:   0.0   0/  0 ??% ??% ??,?% 0 0 
Destroying filter
Exiting... (End of file)


```

Any ideas?

---

### Post by Sölve on 2009-12-01
No, I've got GCC 4.3.4, Karmic 32 bits, Pentium 4 Processor and I get the information.
I think, this is a dshowserver or mplayer issue.

---

### Post by CorruptDNA on 2009-12-02
well everything was working fine, until i wrote make
then this error appeared.. 
> 
./version.sh `cc -dumpversion`
cc -o mplayer command.o m_property.o mixer.o mp_fifo.o mp_msg.o mplayer.o parser-mpcmd.o input/input.o libao2/ao_mpegpes.o libao2/ao_null.o libao2/ao_pcm.o libao2/audio_out.o libvo/aspect.o libvo/geometry.o libvo/spuenc.o libvo/video_out.o libvo/vo_mpegpes.o libvo/vo_null.o input/appleir.o libvo/vo_dga.o libvo/vo_fbdev.o libvo/vo_fbdev2.o libvo/gl_common.o libvo/vo_gl.o libvo/vo_gl2.o libvo/vo_jpeg.o libvo/vo_md5sum.o libao2/ao_oss.o libvo/vo_png.o libvo/vo_pnm.o libvo/vo_tga.o libvo/vo_v4l2.o libao2/ao_v4l2.o libvo/vo_cvidix.o libvo/vosub_vidix.o vidix/vidix.o vidix/drivers.o vidix/dha.o vidix/mtrr.o vidix/pci.o vidix/pci_names.o vidix/pci_dev_ids.o vidix/cyberblade_vid.o vidix/mach64_vid.o vidix/mga_vid.o vidix/mga_crtc2_vid.o vidix/nvidia_vid.o vidix/pm2_vid.o vidix/pm3_vid.o vidix/radeon_vid.o vidix/rage128_vid.o vidix/s3_vid.o vidix/sis_vid.o vidix/sis_bridge.o vidix/unichrome_vid.o libvo/vo_x11.o libvo/vo_xover.o libvo/x11_common.o libvo/vo_xv.o libvo/vo_xvidix.o libvo/vo_yuv4mpeg.o asxparser.o codec-cfg.o cpudetect.o edl.o find_sub.o fmt-conversion.o get_path.o m_config.o m_option.o m_struct.o mpcommon.o parser-cfg.o playtree.o playtreeparser.o spudec.o sub_cc.o subopt-helper.o subreader.o vobsub.o libaf/af.o libaf/af_center.o libaf/af_channels.o libaf/af_comp.o libaf/af_delay.o libaf/af_dummy.o libaf/af_equalizer.o libaf/af_extrastereo.o libaf/af_format.o libaf/af_gate.o libaf/af_hrtf.o libaf/af_karaoke.o libaf/af_pan.o libaf/af_resample.o libaf/af_scaletempo.o libaf/af_sinesuppress.o libaf/af_stats.o libaf/af_sub.o libaf/af_surround.o libaf/af_sweep.o libaf/af_tools.o libaf/af_volnorm.o libaf/af_volume.o libaf/filter.o libaf/format.o libaf/reorder_ch.o libaf/window.o libmpcodecs/ad.o libmpcodecs/ad_alaw.o libmpcodecs/ad_dk3adpcm.o libmpcodecs/ad_dvdpcm.o libmpcodecs/ad_hwmpa.o libmpcodecs/ad_imaadpcm.o libmpcodecs/ad_msadpcm.o libmpcodecs/ad_msgsm.o libmpcodecs/ad_pcm.o libmpcodecs/dec_audio.o libmpcodecs/dec_teletext.o libmpcodecs/dec_video.o libmpcodecs/img_format.o libmpcodecs/mp_image.o libmpcodecs/native/xa_gsm.o libmpcodecs/pullup.o libmpcodecs/vd.o libmpcodecs/vd_hmblck.o libmpcodecs/vd_lzo.o libmpcodecs/vd_mpegpes.o libmpcodecs/vd_mtga.o libmpcodecs/vd_null.o libmpcodecs/vd_raw.o libmpcodecs/vd_sgi.o libmpcodecs/vf.o libmpcodecs/vf_1bpp.o libmpcodecs/vf_2xsai.o libmpcodecs/vf_blackframe.o libmpcodecs/vf_boxblur.o libmpcodecs/vf_crop.o libmpcodecs/vf_cropdetect.o libmpcodecs/vf_decimate.o libmpcodecs/vf_delogo.o libmpcodecs/vf_denoise3d.o libmpcodecs/vf_detc.o libmpcodecs/vf_dint.o libmpcodecs/vf_divtc.o libmpcodecs/vf_down3dright.o libmpcodecs/vf_dsize.o libmpcodecs/vf_dvbscale.o libmpcodecs/vf_eq.o libmpcodecs/vf_eq2.o libmpcodecs/vf_expand.o libmpcodecs/vf_field.o libmpcodecs/vf_fil.o libmpcodecs/vf_filmdint.o libmpcodecs/vf_flip.o libmpcodecs/vf_format.o libmpcodecs/vf_framestep.o libmpcodecs/vf_gradfun.o libmpcodecs/vf_halfpack.o libmpcodecs/vf_harddup.o libmpcodecs/vf_hqdn3d.o libmpcodecs/vf_hue.o libmpcodecs/vf_il.o libmpcodecs/vf_ilpack.o libmpcodecs/vf_ivtc.o libmpcodecs/vf_kerndeint.o libmpcodecs/vf_mirror.o libmpcodecs/vf_noformat.o libmpcodecs/vf_noise.o libmpcodecs/vf_ow.o libmpcodecs/vf_palette.o libmpcodecs/vf_perspective.o libmpcodecs/vf_phase.o libmpcodecs/vf_pp7.o libmpcodecs/vf_pullup.o libmpcodecs/vf_rectangle.o libmpcodecs/vf_remove_logo.o libmpcodecs/vf_rgb2bgr.o libmpcodecs/vf_rgbtest.o libmpcodecs/vf_rotate.o libmpcodecs/vf_sab.o libmpcodecs/vf_scale.o libmpcodecs/vf_smartblur.o libmpcodecs/vf_softpulldown.o libmpcodecs/vf_softskip.o libmpcodecs/vf_swapuv.o libmpcodecs/vf_telecine.o libmpcodecs/vf_test.o libmpcodecs/vf_tfields.o libmpcodecs/vf_tile.o libmpcodecs/vf_tinterlace.o libmpcodecs/vf_unsharp.o libmpcodecs/vf_vo.o libmpcodecs/vf_yadif.o libmpcodecs/vf_yuvcsp.o libmpcodecs/vf_yuy2.o libmpcodecs/vf_yvu9.o libmpdemux/aac_hdr.o libmpdemux/asfheader.o libmpdemux/aviheader.o libmpdemux/aviprint.o libmpdemux/demuxer.o libmpdemux/demux_aac.o libmpdemux/demux_asf.o libmpdemux/demux_audio.o libmpdemux/demux_avi.o libmpdemux/demux_demuxers.o libmpdemux/demux_film.o libmpdemux/demux_fli.o libmpdemux/demux_lmlm4.o libmpdemux/demux_mf.o libmpdemux/demux_mkv.o libmpdemux/demux_mov.o libmpdemux/demux_mpg.o libmpdemux/demux_nsv.o libmpdemux/demux_pva.o libmpdemux/demux_rawaudio.o libmpdemux/demux_rawvideo.o libmpdemux/demux_realaud.o libmpdemux/demux_real.o libmpdemux/demux_roq.o libmpdemux/demux_smjpeg.o libmpdemux/demux_ts.o libmpdemux/demux_ty.o libmpdemux/demux_ty_osd.o libmpdemux/demux_viv.o libmpdemux/demux_vqf.o libmpdemux/demux_y4m.o libmpdemux/ebml.o libmpdemux/extension.o libmpdemux/mf.o libmpdemux/mp3_hdr.o libmpdemux/mp_taglists.o libmpdemux/mpeg_hdr.o libmpdemux/mpeg_packetizer.o libmpdemux/parse_es.o libmpdemux/parse_mp4.o libmpdemux/video.o libmpdemux/yuv4mpeg.o libmpdemux/yuv4mpeg_ratio.o libvo/osd.o libvo/sub.o osdep/getch2.o osdep/timer-linux.o stream/open.o stream/stream.o stream/stream_cue.o stream/stream_file.o stream/stream_mf.o stream/stream_null.o stream/url.o libmpcodecs/vd_dshowserver.o stream/ai_oss.o libvo/font_load.o stream/dvb_tune.o stream/stream_dvb.o stream/stream_dvdnav.o libdvdnav/dvdnav.o libdvdnav/highlight.o libdvdnav/navigation.o libdvdnav/read_cache.o libdvdnav/remap.o libdvdnav/searching.o libdvdnav/settings.o libdvdnav/vm/decoder.o libdvdnav/vm/vm.o libdvdnav/vm/vmcmd.o stream/stream_dvd.o stream/stream_dvd_common.o libdvdread4/bitreader.o libdvdread4/dvd_input.o libdvdread4/dvd_reader.o libdvdread4/dvd_udf.o libdvdread4/ifo_print.o libdvdread4/ifo_read.o libdvdread4/md5.o libdvdread4/nav_print.o libdvdread4/nav_read.o libmpcodecs/ad_faad.o libfaad2/bits.o libfaad2/cfft.o libfaad2/common.o libfaad2/decoder.o libfaad2/drc.o libfaad2/drm_dec.o libfaad2/error.o libfaad2/filtbank.o libfaad2/hcr.o libfaad2/huffman.o libfaad2/ic_predict.o libfaad2/is.o libfaad2/lt_predict.o libfaad2/mdct.o libfaad2/mp4.o libfaad2/ms.o libfaad2/output.o libfaad2/pns.o libfaad2/ps_dec.o libfaad2/ps_syntax.o libfaad2/pulse.o libfaad2/rvlc.o libfaad2/sbr_dct.o libfaad2/sbr_dec.o libfaad2/sbr_e_nf.o libfaad2/sbr_fbt.o libfaad2/sbr_hfadj.o libfaad2/sbr_hfgen.o libfaad2/sbr_huff.o libfaad2/sbr_qmf.o libfaad2/sbr_syntax.o libfaad2/sbr_tf_grid.o libfaad2/specrec.o libfaad2/ssr.o libfaad2/ssr_fb.o libfaad2/ssr_ipqf.o libfaad2/syntax.o libfaad2/tns.o libvo/aclib.o libvo/font_load_ft.o stream/stream_ftp.o libmpcodecs/vf_bmovl.o libaf/af_export.o osdep/mmap_anon.o libmpcodecs/vd_ijpg.o libmpcodecs/ad_hwac3.o libmpcodecs/ad_liba52.o liba52/crc.o liba52/resample.o liba52/bit_allocate.o liba52/bitstream.o liba52/downmix.o liba52/imdct.o liba52/parse.o libass/***.o libass/***_bitmap.o libass/***_cache.o libass/***_font.o libass/***_fontconfig.o libass/***_library.o libass/***_mp.o libass/***_render.o libass/***_utils.o libmpcodecs/vf_***.o av_opts.o libaf/af_lavcresample.o libmpcodecs/ad_ffmpeg.o libmpcodecs/vd_ffmpeg.o libmpcodecs/vf_lavc.o libmpcodecs/vf_lavcdeint.o libmpcodecs/vf_screenshot.o libaf/af_lavcac3enc.o libmpcodecs/vf_fspp.o libmpcodecs/vf_geq.o libmpcodecs/vf_mcdeint.o libmpcodecs/vf_qp.o libmpcodecs/vf_spp.o libmpcodecs/vf_uspp.o libmpdemux/demux_lavf.o stream/stream_ffmpeg.o libdvdcss/css.o libdvdcss/device.o libdvdcss/error.o libdvdcss/ioctl.o libdvdcss/libdvdcss.o libmpcodecs/vd_libmpeg2.o libmpeg2/alloc.o libmpeg2/cpu_accel.o libmpeg2/cpu_state.o libmpeg2/decode.o libmpeg2/header.o libmpeg2/idct.o libmpeg2/motion_comp.o libmpeg2/slice.o libmpeg2/idct_mmx.o libmpeg2/motion_comp_mmx.o libmpcodecs/vf_pp.o libmpdemux/demux_mng.o libmpcodecs/ad_mp3lib.o mp3lib/sr1.o mp3lib/decode_i586.o mp3lib/dct36_3dnow.o mp3lib/dct64_3dnow.o mp3lib/dct36_k7.o mp3lib/dct64_k7.o mp3lib/dct64_mmx.o mp3lib/decode_mmx.o mp3lib/dct64_sse.o stream/stream_rtsp.o stream/freesdp/common.o stream/freesdp/errorlist.o stream/freesdp/parser.o stream/librtsp/rtsp.o stream/librtsp/rtsp_rtp.o stream/librtsp/rtsp_session.o osdep/shmem.o stream/stream_netstream.o stream/asf_mmst_streaming.o stream/asf_streaming.o stream/cookies.o stream/http.o stream/network.o stream/pnm.o stream/rtp.o stream/udp.o stream/tcp.o stream/stream_rtp.o stream/stream_udp.o stream/realrtsp/asmrp.o stream/realrtsp/real.o stream/realrtsp/rmff.o stream/realrtsp/sdpplin.o stream/realrtsp/xbuffer.o libmpcodecs/vd_mpng.o stream/stream_pvr.o libmpcodecs/ad_qtaudio.o libmpcodecs/vd_qtvideo.o loader/wrapper.o libmpcodecs/ad_realaud.o libmpcodecs/vd_realvid.o stream/cache2.o tremor/bitwise.o tremor/block.o tremor/codebook.o tremor/floor0.o tremor/floor1.o tremor/framing.o tremor/info.o tremor/mapping0.o tremor/mdct.o tremor/registry.o tremor/res012.o tremor/sharedbook.o tremor/synthesis.o tremor/window.o stream/stream_tv.o stream/tv.o stream/frequencies.o stream/tvi_dummy.o stream/tvi_v4l.o stream/audio_in.o stream/tvi_v4l2.o unrar_exec.o stream/stream_vcd.o libmpcodecs/ad_libvorbis.o libmpdemux/demux_ogg.o loader/elfdll.o loader/ext.o loader/ldt_keeper.o loader/module.o loader/pe_image.o loader/pe_resource.o loader/registry.o loader/resource.o loader/win32.o libmpcodecs/ad_acm.o libmpcodecs/ad_dmo.o libmpcodecs/ad_dshow.o libmpcodecs/ad_twin.o libmpcodecs/vd_dmo.o libmpcodecs/vd_dshow.o libmpcodecs/vd_vfw.o libmpcodecs/vd_vfwex.o libmpdemux/demux_avs.o loader/afl.o loader/drv.o loader/vfl.o loader/dshow/DS_AudioDecoder.o loader/dshow/DS_Filter.o loader/dshow/DS_VideoDecoder.o loader/dshow/allocator.o loader/dshow/cmediasample.o loader/dshow/guids.o loader/dshow/inputpin.o loader/dshow/mediatype.o loader/dshow/outputpin.o loader/dmo/DMO_AudioDecoder.o loader/dmo/DMO_VideoDecoder.o loader/dmo/buffer.o loader/dmo/dmo.o loader/dmo/dmo_guids.o libmpcodecs/vd_xanim.o libavformat/libavformat.a libavcodec/libavcodec.a libavutil/libavutil.a libpostproc/libpostproc.a libswscale/libswscale.a -Wl,-z,noexecstack  -ffast-math   -lpng -lz -lmng -lz -ljpeg -lfreetype -lz -lfontconfig  -lz -lpthread -ldl -rdynamic  -lm  -lrt -lXext -lX11 -lpthread -lXss -lXv -lXinerama -lXxf86vm -lXxf86dga -lGL -ldl
vidix/pci_names.o: file not recognized: File truncated
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1


I dont know what to do afterwards, please tell me. 
Thanks.

---

### Post by Bachstelze on 2009-12-02
The patch apparently makes dshowserver crash during the "testing" phase, I will investigate as soon as I get the time.

@CorruptDNA: couldn't reproduce. Are you passing any special options to ./configure?

---

### Post by CorruptDNA on 2009-12-02
no no , its oke now.. i uninstalled the build deleted the files and redid the installation..
it got installed properly, but i cant seem to open mplayer like this.. 
mplayer -vc coreserve foo.mkv



is mplayer same as totem movie playeR?
 and can i now install smplayer normally? when i uninstalled the build and everything i also uninstalled mplayer and smplayer..
Thanks

---

### Post by Bachstelze on 2009-12-02
> **CorruptDNA said:**
> 
it got installed properly, but i cant seem to open mplayer like this.. 
mplayer -vc coreserve foo.mkv

Well, what happens when you try?

> **CorruptDNA said:**
> is mplayer same as totem movie playeR?

No.

> **CorruptDNA said:**
> and can i now install smplayer normally?

Depends what you call "normally". ;) If you compiled mplayer from source, you need to also compile smplayer.

---

### Post by CorruptDNA on 2009-12-02
> **Bachstelze said:**
> Well, what happens when you try?



No.
Playing foo.mkv.
File not found: 'foo.mkv'
Failed to open foo.mkv.



well is says no such file as foo or something
Depends what you call "normally". ;) If you compiled mplayer from source, you need to also compile smplayer.


yes, i followed your steps, and i installed mplayer from source, what do i have to do to install smplayer too?

also the config file you tell us to update is codecs.config.h  is the "h" normal??? 

also when i write this, test -f ~/.mplayer/codecs.conf || cp etc/codecs.conf ~/.mplayer
my screen went black, then my cursor appeared . it was an "x" and then it went black again for 2-3 min so i restarted my computer

<snip>
Thanks

---

### Post by Sölve on 2009-12-02
> **Bachstelze said:**
> The patch apparently makes dshowserver crash during the "testing" phase, I will investigate as soon as I get the time.

When you write a patch, we will have to recompile dshowserver? Mplayer too?
Regards.

---

### Post by Bachstelze on 2009-12-02
> **Sölve said:**
> When you write a patch, we will have to recompile dshowserver? Mplayer too?

dshowserver, yes. MPlayer, probably not.

---

### Post by Sölve on 2009-12-02
Can you tell me what is the error in the patch, which makes it impossible to validate the dshowserver work?

---

### Post by Bachstelze on 2009-12-02
> **Sölve said:**
> Can you tell me what is the error in the patch, which makes it impossible to validate the dshowserver work?

I can't, because I haven't had the time to look into it yet.

---

### Post by CorruptDNA on 2009-12-03
Thanks for the tutorial, there was no error.
I couldnt play the file because it was hd, my brother told me.. other files work perfectly..

---

### Post by Rimasto on 2009-12-04
> **quvil said:**
> When I tried to test whether codec registration had worked (dshowserver -c CoreAVCDecoder.ax -s 1280x720 ...), dshowserver crashed with an assertion:

No id specified, assuming test mode
Opening device
dshowserver: malloc.c:3074: sYSMALLOc: Assertion `(old_top == (((mbinptr) (((char *) &((av)->bins[((1) - 1) * 2])) - __builtin_offsetof (struct malloc_chunk, fd)))) && old_size == 0) || ((unsigned long) (old_size) >= (unsigned long)((((__builtin_offsetof (struct malloc_chunk, fd_nextsize))+((2 * (sizeof(size_t))) - 1)) & ~((2 * (sizeof(size_t))) - 1))) && ((old_top)->size & 0x1) && ((unsigned long)old_end & pagemask) == 0)' failed.
Aborted

Did somebody encounter something similar? 

I compiled dshowserver statically according to the instructions on a system with Atom n280 running Karmic, and tried to use it on a 64 bit system with Core 2 Duo T7250 running Jaunty.

P.S.: site hosting a tarball with precompiled binaries was unavailable, I could not check whether it would behave differently.

Well, I had the same problem, i run Ubuntu 9.10 Karmic with gcc-4.4.1, i think the problem is attributable to gcc ..... 
I solved by downloading an already compiled version of registercodec and dshowserver (i I downloaded "dshowserver-ia32-r46.tar.bz2")
You can find the latest versions @ [http://code.google.com/p/coreavc-for-linux/downloads/list ]("http://code.google.com/p/coreavc-for-linux/downloads/list").

Ps: Do not try to downgrade gcc-4.4 to gcc-4.3 or gcc-4.2. I already tried this way, but without results...

---

### Post by _El_Chojin_ on 2009-12-11
> **Rimasto said:**
> Well, I had the same problem, i run Ubuntu 9.10 Karmic with gcc-4.4.1, i think the problem is attributable to gcc ..... 
I solved by downloading an already compiled version of registercodec and dshowserver (i I downloaded "dshowserver-ia32-r46.tar.bz2")
You can find the latest versions @ [http://code.google.com/p/coreavc-for-linux/downloads/list ]("http://code.google.com/p/coreavc-for-linux/downloads/list").

Ps: Do not try to downgrade gcc-4.4 to gcc-4.3 or gcc-4.2. I already tried this way, but without results...
I have downloaded dshowserver from that website but when i use:
dshowserver -c CoreAVCDecoder.ax -s 1280x720 -g 09571a4b-f1fe-4c60-9760de6d310c7c31 -b 12 -f 0x34363248 -o 0x30323449

I continue having the same error, we need to recompile something?

---

### Post by Bachstelze on 2009-12-11
> **_El_Chojin_ said:**
> I have downloaded dshowserver from that website but when i use:
dshowserver -c CoreAVCDecoder.ax -s 1280x720 -g 09571a4b-f1fe-4c60-9760de6d310c7c31 -b 12 -f 0x34363248 -o 0x30323449

I continue having the same error, we need to recompile something?

I have given up on searching the cause of this bug. If someone with more C knowledge than me wants to look it up...

---

### Post by GraceDivine on 2009-12-12
Last night, I successfully compiled Mplayer using this guide, but on Ubuntu 9.04.
I used an older version of Dshowserver and Registercodec, and CoreAVC 1.9.5.
So it would seem that a major compilation issue exists with Karmic and GCC.
I'm not going to start a heated debate over what is better: 9.04 or 9.10, but since I like mplayer so much and it works well on 9.04, I'll stick with it for the time being.
Hopefully, GCC will be fixed on 9.10 soon, if not by 10.04.

---

### Post by Bachstelze on 2009-12-12
> **GraceDivine said:**
> Last night, I successfully compiled Mplayer using this guide, but on Ubuntu 9.04.
I used an older version of Dshowserver and Registercodec, and CoreAVC 1.9.5.

Do you mean it worked even in the "test" phase? If that's the case, can you please post the output of

```
gcc -v
```

on your Jaunty system? packages.ubuntu.com is down at the moment so I can't check which version of GCC Jaunty uses, but it's very possible that it's one of the numerous problems introduced by GCC 4.4.

---

### Post by ripps818 on 2009-12-12
The dshowserver+registercodec package I built in my coreavc ppa seems to work in Karmic. I've used a couple patches on it.
It gives me an error when I run a test from commandline, but it seems to still work fine with the mplayer in rvm's ppa.

[https://edge.launchpad.net/~ripps818/+archive/coreavc](https://edge.launchpad.net/~ripps818/+archive/coreavc)
[https://edge.launchpad.net/~rvm/+archive/mplayer](https://edge.launchpad.net/~rvm/+archive/mplayer)

---

### Post by sanktnelson on 2009-12-15
Hi all,

I also get the the 
"dshowserver: malloc.c:3074" error, and this is with the prebuilt packages from ripps ppa on 32-bit karmic. This used to work fine until maybe a few days ago, don't know what the exact timing was. I also tried some older versions of the packages from both the ppas, no luck. Any advice?

---

### Post by sanktnelson on 2009-12-15
Oh well, all the .debs failed for me, but I finally went and downloaded the prebuilt dshowserver from upstream at:

[http://coreavc-for-linux.googlecode.com/files/dshowserver-ia32-r46.tar.bz2](http://coreavc-for-linux.googlecode.com/files/dshowserver-ia32-r46.tar.bz2)

(as previously mentioned in this thread) and copied it over /usr/bin/dshowserver, and everything works fine again.

Still, would be nice if the packages worked...

---

### Post by Bachstelze on 2009-12-15
> **sanktnelson said:**
> Oh well, all the .debs failed for me, but I finally went and downloaded the prebuilt dshowserver from upstream at:

[http://coreavc-for-linux.googlecode.com/files/dshowserver-ia32-r46.tar.bz2](http://coreavc-for-linux.googlecode.com/files/dshowserver-ia32-r46.tar.bz2)

(as previously mentioned in this thread) and copied it over /usr/bin/dshowserver, and everything works fine again.

Still, would be nice if the packages worked...

Can you read MP4 or FLV files with it? This was the reason why the last patch was included, which broke the dshowserver "test".

---

### Post by GraceDivine on 2009-12-15
@[Bachstelze]("http://ubuntuforums.org/member.php?u=51114")

Here is the output from gcc -v:
Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.3.3-5ubuntu4' --with-bugurl=file:///usr/share/doc/gcc-4.3/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.3 --program-suffix=-4.3 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4)

Yes, the older dshowserver and registercodec worked even in test phase. Then again, I'm using Ubuntu 9.04.

---

### Post by jbernardo on 2009-12-16
Guys, to have it working with gcc 4.4.1 in karmic, "all" I had to do was to add the line CFLAGS+=-fno-strict-aliasing to the directshowserver Makefile (after the other CFLAGS lines), and pass "--extra-cflags=-fno-strict-aliasing" to mplayer's configure. And now coreserv works!

---

### Post by Sölve on 2009-12-18
Okay. When I try to patch DShowServer with this command:

```
cd coreavc-for-linux
wget -qO - [http://paste.ubuntu.com/327178/plain/](http://paste.ubuntu.com/327178/plain/) | patch -p0
```It gives me:

```
patch: **** Only garbage was found in the patch input.
```I have Ubuntu 9.10 32 bits and newest versions mplayer and DShowServer from SVN. What can I do?

//EDIT:

I solved my problem by copying the patch to another location on the network.

---

### Post by Master One on 2009-12-19
> **jbernardo said:**
> Guys, to have it working with gcc 4.4.1 in karmic, "all" I had to do was to add the line CFLAGS+=-fno-strict-aliasing to the directshowserver Makefile (after the other CFLAGS lines), and pass "--extra-cflags=-fno-strict-aliasing" to mplayer's configure. And now coreserv works!
Thanks for that hint, I am just updating my installation, and added the "-fno-strict-aliasing" to stick with gcc 4.4.1. The dshowserver test still gives that malloc, but I guess that does not matter, as long is it is nevertheless working. I am now recompiling mplayer and then smplayer, which may take some time on my Atom machines...

BTW They changed something on [http://paste.ubuntu.com](http://paste.ubuntu.com) which requires to login first, so fetching the patches with wget does not work any more (just open the link to paste.ubuntu.com in a browser, and save the shown plaintext manually).

Bachstelze, although the dshowserver-patch adds the h264 & H264 idents and fixes the problem with the mentioned files from youtube, I found another files there, which are causing the same problem. How to find out, what "idents" else are used in such files, to add them to the patch?

Another problem I discovered recently: My DualCore Atom 330 machine generally is powerful enough, to play all AVC 720p content using CoreAVC, nevertheless I now have some files, which are causing strange problems. Either there are partial picture distortions all the time, or the picture is not in a smooth flow, but is sometimes jerking instead, and kind of looses track in a way, that at first it looks fine, then it starts jerking and ends up with picture distortion, which go away, if I skip back and forward, but come back after a short time, making the whole file unwatchable. No idea, what's behind this, especially since most files play just fine, other don't, although they are of equal parameters (same resolution, bitrate, fps). It definitely is not a limit in CPU power, as all 4 cpus (dualcore with hyperthreading) stay way below 80% all the time. Changing settings in smplayer (like caching, threads for decoding) did not help either. Any hint?

---

### Post by Sölve on 2009-12-19
Please paste the log from the console, which will be showed when you play this file.

---

### Post by Bachstelze on 2009-12-19
> **Master One said:**
> 
Bachstelze, although the dshowserver-patch adds the h264 & H264 idents and fixes the problem with the mentioned files from youtube, I found another files there, which are causing the same problem. How to find out, what "idents" else are used in such files, to add them to the patch?

What Sölve said: paste the MPlayer output.

> **Master One said:**
> Another problem I discovered recently: My DualCore Atom 330 machine generally is powerful enough, to play all AVC 720p content using CoreAVC, nevertheless I now have some files, which are causing strange problems. Either there are partial picture distortions all the time, or the picture is not in a smooth flow, but is sometimes jerking instead, and kind of looses track in a way, that at first it looks fine, then it starts jerking and ends up with picture distortion, which go away, if I skip back and forward, but come back after a short time, making the whole file unwatchable. No idea, what's behind this, especially since most files play just fine, other don't, although they are of equal parameters (same resolution, bitrate, fps). It definitely is not a limit in CPU power, as all 4 cpus (dualcore with hyperthreading) stay way below 80% all the time. Changing settings in smplayer (like caching, threads for decoding) did not help either. Any hint?

All AVC steams are not equal in terms of processing power needed for decoding. Some encoding parameter (high number of reference frames, high bitrate, weighted P and/or B-frames, etc.) can increase the needed processing power dramativally, even if the resolution is kept constant.

---

### Post by wiiaboo on 2009-12-19
As anyone tried to see if the new CoreAVC 2.0 works out-of-the-box with patched builds of Mplayer?

---

### Post by Bachstelze on 2009-12-19
> **wiiaboo said:**
> As anyone tried to see if the new CoreAVC 2.0 works out-of-the-box with patched builds of Mplayer?

Not me, they don't have a trial version up yet.

---

### Post by wiiaboo on 2009-12-20
Also, Bachstelze, could you make a patch against [mplayer-build.git](http://repo.or.cz/w/mplayer-build.git) or maybe even [mplayer.git](http://repo.or.cz/w/mplayer.git) (the latter is linked to the former)? It's the most developed version of mplayer, with latest libass support, matroska editions, ordered chapters et al.

Or if it's the same as the latest patch, could you maybe give detailed instructions on how to compile with coreavc support? I got a free upgrade because I bought CoreAVC in the last 60 days, and I wanted to try and see if it works.

---

### Post by Bachstelze on 2009-12-20
> **wiiaboo said:**
> Also, Bachstelze, could you make a patch against [mplayer-build.git](http://repo.or.cz/w/mplayer-build.git) or maybe even [mplayer.git](http://repo.or.cz/w/mplayer.git) (the latter is linked to the former)? It's the most developed version of mplayer, with latest libass support, matroska editions, ordered chapters et al.

Or if it's the same as the latest patch, could you maybe give detailed instructions on how to compile with coreavc support? I got a free upgrade because I bought CoreAVC in the last 60 days, and I wanted to try and see if it works.

It should be the same, really. Just use git instead of svn to get the mplayer source, and try to patch them. If it doesn't work, report back, and I'll see what I can do.

---

### Post by wiiaboo on 2009-12-20
Patching Mplayer failed with vd.c.

[vd.c.ref](http://paste.ubuntu.com/343996/)

---

### Post by wiiaboo on 2009-12-20
Compiling now.
Here's the [git diff](http://paste.ubuntu.com/343997/).

---

### Post by Bachstelze on 2009-12-20
Aye, this was already asked a while ago:

[http://ubuntuforums.org/showthread.php?t=1034075&page=13#122](http://ubuntuforums.org/showthread.php?t=1034075&page=13#122)

---

### Post by wiiaboo on 2009-12-20
So it compiled like a charm, but turns out the registry information is different and even after changing the value like it shows in regedit.exe, it still doesn't recognize the key. Maybe it's some problem with CoreAVC itself?

The changes I can see by regedit are:
"CoreAVC Pro" => "CoreAVC Pro 2.x"
and
"User" entry has to be specified now, as the serials are tied to it

```
Forced video codec: coreserve
Opening video decoder: [dshowserver] DirectShowServer video codecs
Opening device
Called unk_IsDebuggerPresent
MSGBOX 'Serial Number Missing!' 'CoreAVC Professional Edition' (327680)
Win32 LoadLibrary failed to load: CoreAVCDecoder.ax
Warning: DS_Filter() could not open DirectShow DLL.  (DLL=CoreAVCDecoder.ax)
Failed to create DirectShow filter
Failed to open win32 codec CoreAVCDecoder.ax
```

Tried with:
```
registercodec -r ~/.mplayer/registry32 -k "HKLM\\Software\\CoreCodec\\CoreAVC Pro 2.x\\Serial" -v "XXXXXX-XXXXXX-XXXXXX-XXXXXX-XXXXXX"
```
and
```
registercodec -r ~/.mplayer/registry32 -k "HKLM\\Software\\CoreCodec\\CoreAVC Pro 2.x\\User" -v "wiiaboo@email.org"
```
but still didn't work.

---

### Post by wiiaboo on 2009-12-20
Sorry, double post.

---

### Post by ripps818 on 2009-12-21
I can't get coreavc 2.0 to work either.
When I try to run it in mplayer, I get "Called unk_GetModuleHandleW" repeatedly.

---

### Post by gtdaqua on 2009-12-22
> **ripps818 said:**
> I can't get coreavc 2.0 to work either.
When I try to run it in mplayer, I get "Called unk_GetModuleHandleW" repeatedly.

Same here. Tried various steps for several hours and still couldn't get CoreAVC 2.0 to work.

Edit: Finally Got it working! I did not apply the patch for dshowserver. Just checkedout the coreavc-for-linux and did a 'make' inside the dshowserver folder. The patch messes with the dshowserver. Don't apply the patch. Just 'make' it straight and copy the file to /usr/local/bin.

If you want GUI working, then use the --enable-gui switch when executing configure.

And .TS containers (x264) work with -demuxer lavf switch along with mplayer.

---

### Post by Master One on 2009-12-22
> **gtdaqua said:**
> Same here. Tried various steps for several hours and still couldn't get CoreAVC 2.0 to work.

Edit: Finally Got it working! I did not apply the patch for dshowserver. Just checkedout the coreavc-for-linux and did a 'make' inside the dshowserver folder. The patch messes with the dshowserver. Don't apply the patch. Just 'make' it straight and copy the file to /usr/local/bin.

If you want GUI working, then use the --enable-gui switch when executing configure.

And .TS containers (x264) work with -demuxer lavf switch along with mplayer.
Can you explain that in detail please?

The patch for the dshowserver only adds the "h264" and "H264" IDs, so I do not see how this can be related to the CoreAVC 2.0 update.

If one has a working setup with CoreAVC 1.9.5, what's the update process for using CoreAVC 2.0.0? Just copy the new CoreAVCDecoder.ax over, and then what registercodec command?

---

### Post by Master One on 2009-12-22
> **Master One said:**
> Another problem I discovered recently: My DualCore Atom 330 machine generally is powerful enough, to play all AVC 720p content using CoreAVC, nevertheless I now have some files, which are causing strange problems. Either there are partial picture distortions all the time, or the picture is not in a smooth flow, but is sometimes jerking instead, and kind of looses track in a way, that at first it looks fine, then it starts jerking and ends up with picture distortion, which go away, if I skip back and forward, but come back after a short time, making the whole file unwatchable. No idea, what's behind this, especially since most files play just fine, other don't, although they are of equal parameters (same resolution, bitrate, fps). It definitely is not a limit in CPU power, as all 4 cpus (dualcore with hyperthreading) stay way below 80% all the time. Changing settings in smplayer (like caching, threads for decoding) did not help either. Any hint?
Ok, note to myself: An Atom 330 machine is definitely powerful enough to handle any AVC 720p content, none of the 4 recognized CPUs ever maxes out, whatever I tried, they stayed between 50 and 80% at all times, even when the mentioned problems occured.

The second problem with picture not staying a smooth flow followed by jerking and loosing track could be solved by switching the audio device from "Pulse" back to "OSS". There seem to some serious problems with Pulse audio.

The first problem with partial picture distortions all the time (but only with certain files, others play just fine) is still there, so this has to be something else, which I was hoping the upgrade to CoreAVC 2.0.0 would fix. There are no errors in the mplayer log when these distortions show up. To show you what I mean, I have added two pictures. The first shows such typical partial picture distortions, which appear in one frameset, and a second later (next frameset) they are gone again. I don't really have a clue, how to explain this any better, but I guess it has something to do with A, B, and I-frames and decoding errors. I have tested such a problematic file on two different machines with this Ubuntu 9.10 and this CoreAVC MPlayer setup, as well as an old laptop with WinXP and MediaPlayerClassic + CoreAVC 1.9.5 installed, with exactly the same result. These distortions are not random, if the same file is played multiple times, the same distortions appear in exactly the same places every time. So this pretty much comes down to the chance, that there is something wrong with CoreCodec 1.9.5, which is why I am very much interested in upgrading to CoreAVC 2.0.0.

---

### Post by wiiaboo on 2009-12-22
I'm guessing (just guessing) that those corruptions are caused by bad decoding of WeightP enabled encodes by CoreAVC 1.9.5. It is solved in 2.0. Thus why I installed it.

Gonna try not patching dshowserver like gtdaqua said.

---

### Post by wiiaboo on 2009-12-22
Guess not.

Failed with the same error:
```

Opening device
Called unk_IsDebuggerPresent
MSGBOX 'Serial Number Missing!' 'CoreAVC Professional Edition' (327680)
Win32 LoadLibrary failed to load: CoreAVCDecoder.ax
Warning: DS_Filter() could not open DirectShow DLL.  (DLL=CoreAVCDecoder.ax)
Failed to create DirectShow filter
Failed to open win32 codec CoreAVCDecoder.ax
```

---

### Post by trapperjohn on 2009-12-23
> **Master One said:**
> Ok, note to myself: An Atom 330 machine is definitely powerful enough to handle any AVC 720p content, none of the 4 recognized CPUs ever maxes out, whatever I tried, they stayed between 50 and 80% at all times, even when the mentioned problems occured.

I have the same problem - though it only happened on one movie so far when using CoreAVC (1.9.5).

Did you try mplayer-mt (mplayer with multithreaded ffmpeg)? Might be sufficient on your system. On my Atom N270 it's nearly as fast as CoreAVC when playing 720p MKVs and it had no problem with the mentioned movie file. It's definitely a lot faster than the standard mplayer - even on my single core (but hyperthreaded) Atom.

Just add the repos from here
[https://launchpad.net/~rvm/+archive/testing](https://launchpad.net/~rvm/+archive/testing)
and here
[https://launchpad.net/~rvm/+archive/libs](https://launchpad.net/~rvm/+archive/libs)
and install it via apt.

---

### Post by wiiaboo on 2009-12-23
Can your Atom N270 run live-action 720p smoothly, with mplayer-mt?

---

### Post by Master One on 2009-12-23
Just tried it with CoreAVC 2.0.0, but I get the same result as already mentioned here:```
Forced video codec: coreserve
Opening video decoder: [dshowserver] DirectShowServer video codecs
Opening device
Called unk_IsDebuggerPresent
Called unk_GetModuleHandleW
Called unk_GetModuleHandleW
Called unk_GetModuleHandleW
.
.
.
Called unk_GetModuleHandleW
Called unk_GetModuleHandleW
Called unk_GetModuleHandleW
DirectShow filter failedVDecoder init failed :(
```
If the upgrade from 1.9.5 to 2.0.0 can not just be done by exchanging CoreAVCDecoder.ax and adding the new Serial & User lines with registercodec, I guess a new version of coreavc-for-linux is needed? Just tried "svn update", but it's still "Revision 82."

If that's the case, I really wonder, what gtdaqua has done, as he claims to have solved this problem. The dhshowserver patch really just can't be the issue.

I was so much hoping to be able to try 2.0.0 asap, because I have a few shows having these distortion problems, making it unwatchable, so I can't wait to continue watching... ;)

---

### Post by wiiaboo on 2009-12-23
betaboy from CoreCodec also says he's received 2 reports of CoreAVC working on Linux.

Still nothing here on my side, unfortunately, even after not patching dshowserver.

---

### Post by Master One on 2009-12-24
> **wiiaboo said:**
> betaboy from CoreCodec also says he's received 2 reports of CoreAVC working on Linux.
So now we just need to know, how it's done.
> **wiiaboo said:**
> Still nothing here on my side, unfortunately, even after not patching dshowserver.
As seen from your mplayer log-snippet, you are stuck at a completely different point, I guess something went wrong when you tried to add the new data with registercodec. You may want to remove your old registry32 file, and try again, but then it will lead to "Called unk_GetModuleHandleW" for sure.

As already mentioned, the dshowserver patch can not have anything to do with this issue, because it does not change anything essential for handling CoreAVCDecoder.ax, but only adds the "h264" & "H264" idents, so that these crappy mp4 files from youtube play at all.

I did not try mplayer-mt yet (never heard about that version before), if it is able to play all kind of AVC 720p files even on an Atom N270, it may be an option, but I'd still prefer to use CoreAVC, since there is no doubt, that it is easier on CPU resources (it's not only about playback, but also the files coming over the network from a SMB share).

---

### Post by trapperjohn on 2009-12-24
> **wiiaboo said:**
> Can your Atom N270 run live-action 720p smoothly, with mplayer-mt?

What do you mean with "live-action"?

For 720p movies, it depends. mplayer-mt is still a bit slower than CoreAVC and some movies with a high bitrate won't even play smooth using CoreAVC on my Atom N270. But it's a minority and only a few scenes have such a high bitrate.

But I think on a dual-core Atom 330, these issues should be gone.

edit: This is my mplayer-mt commandline
```

mplayer-mt -subfont-text-scale 3 -ao alsa:device=iec958 -ac hwdts,hwac3, -cache 8192 -vo xv -lavdopts threads=2:skiploopfilter=all:fast=1

```

I am no professional when it's about mplayer options - these are just the ones which worked best for me. Mplayer is running on an Eee Box connected to a HD TV, optical audio out, DTS/AC3 passthrough

---

### Post by wiiaboo on 2009-12-24
Live-action as in not-animation. Animation can run almost completely smooth because of the lack action compared to real-life movies, even on ffmpeg-mt.

But any real-life movie you open gets out of sync once in a few half minutes, it's kinda annoying.

---

### Post by Talix on 2009-12-24
> **Sölve said:**
> Okay. When I try to patch DShowServer with this command:

```
cd coreavc-for-linux
wget -qO - [http://paste.ubuntu.com/327178/plain/](http://paste.ubuntu.com/327178/plain/) | patch -p0
```It gives me:

```
patch: **** Only garbage was found in the patch input.
```I have Ubuntu 9.10 32 bits and newest versions mplayer and DShowServer from SVN. What can I do?

//EDIT:

I solved my problem by copying the patch to another location on the network.

Hi all, I have the exact same issue, however, his solution doesn't help me as I have no idea on how to accomplish even saving the patch...

---

### Post by Sölve on 2009-12-25
Try with this command:

```
wget -qO - [http://wklej.org/id/246249/txt](http://wklej.org/id/246249/txt) | patch -p0
```

---

### Post by Talix on 2009-12-25
> **Sölve said:**
> Try with this command:

```
wget -qO - [http://wklej.org/id/246249/txt](http://wklej.org/id/246249/txt) | patch -p0
```
ooooh, that did the job :D

thanks a lot

---

### Post by Talix on 2009-12-25
noooooo, now I get the same message with the other patch command.... the> wget [http://paste.ubuntu.com/197237/plain/](http://paste.ubuntu.com/197237/plain/) -qO - | patch -p0Is there another place for finding this too? How do you find these "mirrors"?


EDIT: ooops, sry for doublepost :s

---

### Post by Sölve on 2009-12-25
Catch:

```
wget [http://wklej.org/id/246538/txt]("http://paste.ubuntu.com/197237/plain/") -qO - | patch -p0
```You can copy the text of the patch (from paste.ubuntu.com) in a different place (with clear text output).

---

### Post by Bachstelze on 2009-12-25
Guide updated with patches on pastebin.com.

---

### Post by Talix on 2009-12-25
> **Bachstelze said:**
> Guide updated with patches on pastebin.com.
Nice of you to add the fix such a critical source of error it *after* I waited 24 hours -.-

Nah, just kiddin' :D  Anyone know *why* the original patch is "garbage"?

---

### Post by Bachstelze on 2009-12-25
> **Talix said:**
> Nice of you to add the fix such a critical source of error it *after* I waited 24 hours -.-

Nah, just kiddin' :D  Anyone know *why* the original patch is "garbage"?

It's because the Ubuntu pastebin decided it requires people to login now, so when you tried to download the text with wget, you got a nice error message instead, which [font=monospace]patch[/font] obviously didn't understand.

---

### Post by Talix on 2009-12-25
> **Bachstelze said:**
> It's because the Ubuntu pastebin decided it requires people to login now, so when you tried to download the text with wget, you got a nice error message instead, which [FONT=monospace]patch[/FONT] obviously didn't understand.
Hmm, seems a bit pointless as any eventual spammers / bandwidth bitches (I suppose it *is* because of these that they implement logins now) would obviously be able to make accounts too, thus being able to hog on... Or is their some *good* reason for it?

Anyway, thank you both for your help on the subject, I can now get back to my shows on the eeepc (well, if it works :s ) - I hate using x264 especially for all the live-action :/

---

### Post by trapperjohn on 2009-12-26
> **wiiaboo said:**
> 

But any real-life movie you open gets out of sync once in a few half minutes, it's kinda annoying.

With mplayer-mt? Not in my case.

---

### Post by Master One on 2009-12-26
trapperjohn, how about the AVC 720p episodes from [Riese - The Series](http://www.youtube.com/user/Riesetheseries) (which is a free webseries, means a legal download)? For example, here the [first episode](http://www.youtube.com/watch?v=4UVy7uUceXw), which I downloaded using the Firefox plugin "DownloadHelper". There are several versions of the file available for download, it's important to choose the [HQ22] file with .mp4 ending, which is 720p using H.264 / AVC video codec, and MPEG-4 AAC audio codec.

Do such files play on your Atom N270 machine without any problems using mplayer-mt?

On my DualCore Atom 330 setup, neither the default videoplayer of Ubuntu (Totem), nor mplayer from the Ubuntu repos or VLC can playback these files, whereas mplayer + CoreAVC can do it with not more than 50-70% CPU power, still didn't try mplayer-mt though.

Still no clue about getting CoreAVC 2.0.0 to run with this mplayer + dshowserver setup? I guess I am just not into it deep enough, I follow this thread, but I have no clue where else to look for more info on that matter.

---

### Post by Bachstelze on 2009-12-26
> **Master One said:**
> 
Still no clue about getting CoreAVC 2.0.0 to run with this mplayer + dshowserver setup? I guess I am just not into it deep enough, I follow this thread, but I have no clue where else to look for more info on that matter.

I can't do any testing without a trial version of CoreAVC 2. I'm not buying it since I now use VDPAU. BetaBoy said there would be a trial version shortly after release but we're still waiting...

---

### Post by ogooreck on 2009-12-27
> **ripps818 said:**
> I can't get coreavc 2.0 to work either.
When I try to run it in mplayer, I get "Called unk_GetModuleHandleW" repeatedly.

I get the same message.
GetModuleHandleW is not implemented in loader/win32.c. Probably that's the problem. 

[http://source.winehq.org/source/dlls/kernel32/module.c](http://source.winehq.org/source/dlls/kernel32/module.c)
[FONT=monospace][I][B]
[/B][/I][/FONT]Unicode version of GetModuleHandleA

---

### Post by Master One on 2009-12-27
Ok, getting somewhere, but this will be interesting now, since the coreavc-for-linux project on code.google.com is pretty much dead (last update to the source tree on 28th October 2008 ), someone else will have to come up with a solution.

I guess it's not as easy as just replacing mplayer-with-coreavc/coreavc-for-linux/loader/module.c and(?) mplayer-with-coreavc/mplayer/loader/module.c with [http://source.winehq.org/source/dlls/kernel32/module.c](http://source.winehq.org/source/dlls/kernel32/module.c), is it?

loader/module.c from coreavc-for-linux and mplayer are not the same, and both say "Modified for use with MPlayer" at the beginning of the file.

Are we stuck now?

Can someone please give Bachstelze the CoreAVCDecoder.ax file and a registration? ;)

The present state is quite annoying, on one hand some claim to have it working, on the other hand no info on how it's done, most likely the only one able to fix the problem (Bachstelze) can not investigate the issue due to the lack of a trial-version, I found out that I have quite some files affected by those (weighted P and/or B-frames) picture distortions, and my wife is bugging me, because we still can't watch those files... :(

---

### Post by trapperjohn on 2009-12-27
> **Master One said:**
> trapperjohn, how about the AVC 720p episodes from [Riese - The Series](http://www.youtube.com/user/Riesetheseries) (which is a free webseries, means a legal download)? For example, here the [first episode](http://www.youtube.com/watch?v=4UVy7uUceXw), which I downloaded using the Firefox plugin "DownloadHelper". There are several versions of the file available for download, it's important to choose the [HQ22] file with .mp4 ending, which is 720p using H.264 / AVC video codec, and MPEG-4 AAC audio codec.

Do such files play on your Atom N270 machine without any problems using mplayer-mt?

I tried it on my Atom netbook with mplayer-mt and the episode runs fine, no issues so far. Of course, this was on a smaller screen (1024x600). I'll try it on my TV when I'm home.

What errors do you get when running the default mplayer? What mplayer options do you use?

---

### Post by Master One on 2009-12-27
When I try to play any AVC 720p file with the default mplayer, I just get the "Your system is too slow to play this file" message, and the playback it total crap with jerking picture and out of sync audio. The sames goes for Totem videoplayer.

I use SMplayer as the frontend, and I already tried different settings for cache, number of threads, filter and output-device, but this AVC decoding inefficiency just can not be tweaked.

I don't know, can mplayer with coreavc and mplayer-mt be installed at the same time, and can SMplayer be used for both? I don't want to mess up my system just for trying out mplayer-mt.

---

### Post by Bachstelze on 2009-12-27
> **Master One said:**
> 
I don't know, can mplayer with coreavc and mplayer-mt be installed at the same time, and can SMplayer be used for both? I don't want to mess up my system just for trying out mplayer-mt.

Yes, mplayer-mt just uses multithreaded versions of the ffmpeg libraries instead of the "reguular" ones. Whether or not your ffmpeg libraries are multithreaded makes no difference as far as CoreAVC is concerned.

---

### Post by ogooreck on 2009-12-27
> **Master One said:**
> I guess it's not as easy as just replacing mplayer-with-coreavc/coreavc-for-linux/loader/module.c and(?) mplayer-with-coreavc/mplayer/loader/module.c with [http://source.winehq.org/source/dlls/kernel32/module.c](http://source.winehq.org/source/dlls/kernel32/module.c), is it?


It's not as easy.
I woked it around but now I get:

Forced video codec: coreserve
Opening video decoder: [dshowserver] DirectShowServer video codecs
Opening device
Called unk_IsDebuggerPresent
GetModuleHandleA('SHELL32.dll') => 0x132
GetModuleHandleA('ADVAPI32.dll') => 0x0
GetModuleHandleA('ole32.dll') => 0x0
GetModuleHandleA('OLEAUT32.dll') => 0x131
GetModuleHandleA('USER32.dll') => 0x0
GetModuleHandleA('VERSION.dll') => 0x0
GetModuleHandleA('COMCTL32.dll') => 0x133
GetModuleHandleA('KERNEL32.dll') => 0x120
GetModuleHandleA('GDI32.dll') => 0x0
  src: KERNEL32.DLL
  src: KERNEL32.DLL
  src: KERNEL32.DLL
  src: KERNEL32.DLL
  src: KERNEL32.DLL
  src: KERNEL32.DLL
  src: KERNEL32.DLL
  src: KERNEL32.DLL
Called unk_InitializeCriticalSectionAndSpinVirtualQuery
DirectShow filter failed

InitializeCriticalSectionAndSpinVirtualQuery ???
I give up.

---

### Post by GraceDivine on 2009-12-27
Bachstelze, could you possibly upload the old 64-bit Dshowserver and Registercodec files that you made available before the release of Karmic?  I lost all of my mplayer binaries that I previously built : (    Thanks in advance!

---

### Post by Bachstelze on 2009-12-27
[http://itsuki.fkraiem.org/stuff/dshowserver-ia32-r82.tar.bz2](http://itsuki.fkraiem.org/stuff/dshowserver-ia32-r82.tar.bz2)

---

### Post by chuckman78 on 2009-12-28
> **Master One said:**
> Ok, getting somewhere, but this will be interesting now, since the coreavc-for-linux project on code.google.com is pretty much dead (last update to the source tree on 28th October 2008 ), someone else will have to come up with a solution.

I guess it's not as easy as just replacing mplayer-with-coreavc/coreavc-for-linux/loader/module.c and(?) mplayer-with-coreavc/mplayer/loader/module.c with [http://source.winehq.org/source/dlls/kernel32/module.c](http://source.winehq.org/source/dlls/kernel32/module.c), is it?

loader/module.c from coreavc-for-linux and mplayer are not the same, and both say "Modified for use with MPlayer" at the beginning of the file.

Are we stuck now?

Can someone please give Bachstelze the CoreAVCDecoder.ax file and a registration? ;)

The present state is quite annoying, on one hand some claim to have it working, on the other hand no info on how it's done, most likely the only one able to fix the problem (Bachstelze) can not investigate the issue due to the lack of a trial-version, I found out that I have quite some files affected by those (weighted P and/or B-frames) picture distortions, and my wife is bugging me, because we still can't watch those files... :(

I am in the same situation, I think. I am watching lots of artifacts and distortion when playing lots of 720p and 1080p mkv files. I am using coreavc 1.9.5.

Also, Is there a way to configure coreavc in Ubuntu? It has some config options under windows...

Regards,

Carlos.

---

### Post by Bachstelze on 2009-12-28
> **chuckman78 said:**
> 
Also, Is there a way to configure coreavc in Ubuntu? It has some config options under windows...


They are all stored in the registry. [This page]("http://code.google.com/p/coreavc-for-linux/wiki/RegisterCoreAVC") gives more detail (scroll down a bit).

---

### Post by trapperjohn on 2009-12-28
> **trapperjohn said:**
> I tried it on my Atom netbook with mplayer-mt and the episode runs fine, no issues so far. Of course, this was on a smaller screen (1024x600). I'll try it on my TV when I'm home.



Okay, runs fine on 1280x720, too. Though it seems the file has a low bitrate (or a bad encoding) which is sometimes noticeable when watching the episode.

I tried to also open it with mplayer+CoreAVC but it doesn't even show up. After a while, mplayer just exits with an error. Does the file work for you using CoreAVC?

And yes, mplayer-mt (installed from the mentioned ppa repos) runs fine next to another mplayer because it uses its own binary as "mplayer-mt".

---

### Post by Master One on 2009-12-28
> **trapperjohn said:**
> I tried to also open it with mplayer+CoreAVC but it doesn't even show up. After a while, mplayer just exits with an error. Does the file work for you using CoreAVC?
That's what the dshowserver patch is for.

---

### Post by BagRackRider on 2009-12-28
> **ripps818 said:**
> I can't get coreavc 2.0 to work either.
When I try to run it in mplayer, I get "Called unk_GetModuleHandleW" repeatedly.

I get the unk_GetModuleHandleW message too but after a while the video plays. 
I THOUGHT it was working but i noticed it was using FFMPEG code as fallback. :(

EDIT:
I tried adding GetModuleHandleW myself but I think the wine code dshowserver uses needs updating. Just adding in GetModuleHandleW requires too much work as it is now, at least for me as I'm not skilled enough on C/C++.

---

### Post by Master One on 2009-12-29
Since there is still no solution for using CoreAVC 2.0.0 with MPlayer, I now tried mplayer-mt on my Atom 330, and it indeed does the job.

I just tested it with the options "-cache 8192 -lavdopts threads=4:skiploopfilter=all" on one of the problematic files, which causes those picture distortions when using mplayer with CoreAVC 1.9.5, and playback was just fine, no distortions and no jerking, all 4 CPUs (DualCore with HyperThreading) stay between 60% and 80% most of the time.

So as long as CoreAVC 2.0.0 can not be used, mplayer-mt is indeed a working option. :)

BTW It's easy to use SMplayer as frontend for both (mplayer with CoreAVC and mplayer-mt), by just replacing "mplayer" with "mplayer-mt" (or the other way around) in the appropriate field in Options >> General.

---

### Post by BagRackRider on 2009-12-29
Well, seems like I managed to add GetModuleHandle but I'm stuck at getting IsDebuggerPresent to return a FALSE value (i think).

This is what mplayer outputs now:

Forced video codec: coreserve
Opening video decoder: [dshowserver] DirectShowServer video codecs
Opening device
MSGBOX 'I'm sorry, this application will not run while Soft-Ice is running.' '(null)' (16)
EXIT - code 1

I can't get past that, it thinks I'm running a debugger. :(

EDIT:
Looks like they packed the CoreAVC codec with PECompact with extra options added. The previous version was also PECompact protected but they probably enabled more "anti-debugging/hacking" routines when packing the codec with PECompact this time.

EDIT2:
I think it's the GetModuleHandle code I added that caused the debug error msg to appear, I've done what I can but I give up on this. Hope someone else can  fix it.

---

### Post by ogooreck on 2009-12-31
Just a thought.
Maybe will be possible to compile dshowserver for windows (mingw for example) and run on wine ?

---

### Post by Starks on 2010-01-02
Is there any way to use CoreAVC 2.0 with mplayer-build?

---

### Post by Sölve on 2010-01-02
registercodec is no longer supported... A lot has changed in the code of dshowserver... Look at coreavc-for-linux site...

---

### Post by Starks on 2010-01-02
Almost have it working...

```
eric@kingfisher:~/mplayer/mplayer$ ./mplayer -vc coreserve ~/Videos/[gg]_Umineko_no_Naku_Koro_ni_-_23_[1F55F7E5].mkv
MPlayer UNKNOWN-4.4.2 (C) 2000-2009 MPlayer Team
134 audio & 285 video codecs
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/eric/Videos/[gg]_Umineko_no_Naku_Koro_ni_-_23_[1F55F7E5].mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC) "480p H.264", -vid 0
[mkv] Track ID 2: audio (A_AAC) "2.0 AAC", -aid 0, -alang jpn
[mkv] Track ID 3: subtitles (S_TEXT/***) "***", -sid 0, -slang eng
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  848x480  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
Xlib:  extension "NV-GLX" missing on display ":0.0".
[vdpau] Error when calling vdp_device_create_x11: 1
==========================================================================
Forced video codec: coreserve
Opening video decoder: [dshowserver] DirectShowServer video codecs
dshowserver --codec /home/eric/CoreAVCDecoder.ax --size 848x480 --guid 09571a4b-f1fe-4c60-9760de6d310c7c31 --fourc 0x31637661 --bits 12 --outfmt 0x32315659 --pid 20927 --id b779e730 --numpages 10 --port 0 &
Opening device (port is 0)
len: 992
ProductVersion: 2.0.0
fixme:thread:SetThreadIdealProcessor (0x60): stub
fixme:thread:SetThreadIdealProcessor (0x64): stub
Decoder supports the following YUV formats: YUY2 UYVY YV12 I420 
Decoder is capable of YUV output (flags 0x2b)
Setting fmt
Starting
Initialization is complete
Using semaphore based mutex
Unknown type specified: 2
DirectShow filter failedVDecoder init failed :(
Cannot find codec matching selected -vo and video format 0x31637661.
==========================================================================
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
FAAD: compressed input bitrate missing, assuming 128kbit/s!
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio) decoder)
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Il giudizio finale sta per essere emesso
A:   1.7 (01.6) of 1394.8 (23:14.7)  1.4% 

MPlayer interrupted by signal 2 in module: play_audio
A:   1.8 (01.7) of 1394.8 (23:14.7)  1.4% 
Exiting... (Quit)

```

---

### Post by ripps818 on 2010-01-02
I've started work on setting up my coreavc-for-ubuntu ppa to use fta's ppabot to update and build dshowserver and mplayer. So give me a week or two to set things up.

---

### Post by Starks on 2010-01-02
Getting closer... For any give file, only the first frame is rendering at the moment.

The coreavc-for-linux guy is working out the last few bugs with me.

---

### Post by Starks on 2010-01-03
It works. A pain in the *** to achieve, but CoreAVC 2.0 works! I'd like to thank Alan (the coreavc-for-linux guy) for all of his help.

[http://img205.imageshack.us/img205/8159/successc.png](http://img205.imageshack.us/img205/8159/successc.png)

I'll try to write a howto later.

```
eric@kingfisher:~/mplayer/mplayer$ ./mplayer -*** -vo gl:yuv=4 -ao pulse -vc coreserve "/home/eric/sample.mkv"
MPlayer UNKNOWN-4.4.2 (C) 2000-2009 MPlayer Team
141 audio & 322 video codecs
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/eric/sample.mkv
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC) "Sample", -vid 0
[mkv] Track ID 2: audio (A_VORBIS) "2.0 Vorbis", -aid 0, -alang jpn
[mkv] Track ID 3: subtitles (S_TEXT/***) "***", -sid 0, -slang eng
[mkv] Track ID 4: subtitles (S_TEXT/UTF8) "SRT", -sid 1, -slang eng
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1280x720  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
[gl] using extended formats. Use -vo gl:nomanyfmts if playback fails.
Couldn't open video filter '***'.
***: cannot add video filter
[***] Init
[***] Updating font cache
==========================================================================
Forced video codec: coreserve
Opening video decoder: [dshowserver] DirectShowServer video codecs
dshowserver --codec /home/eric/CoreAVCDecoder.ax --size 1280x720 --guid 09571a4b-f1fe-4c60-9760de6d310c7c31 --fourc 0x31637661 --bits 12 --outfmt 0x32315659 --pid 16616 --id b7829730 --numpages 10 --port 20185 &
Opening device (port is 20185)
len: 992
ProductVersion: 2.0.0
fixme:thread:SetThreadIdealProcessor (0x4c): stub
fixme:thread:SetThreadIdealProcessor (0x50): stub
Decoder supports the following YUV formats: YUY2 UYVY YV12 I420 
Decoder is capable of YUV output (flags 0x2b)
Setting fmt
Starting
Initialization is complete
Using socket based mutex
[PP] Using codec's postprocessing, max q = 4.
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [gl] 1280x720 => 1280x720 Planar YV12 
EINPROGRESS in connect() - selecting
Dshowserver Connected to host
Found DirectShow filterSelected video codec: [coreserve] vfm: dshowserver (CoreAVC DShowServer)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 0.0 kbit/0.00% (ratio: 0->192000)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
Decreasing video pts: 0.042000 < 0.292000  0/  0 ??% ??% ??,?% 0 0 
Decreasing video pts: 0.083000 < 0.292000  0/  0 ??% ??% ??,?% 0 0 
Decreasing video pts: 0.125000 < 0.292000  0/  0 ??% ??% ??,?% 0 0 
Decreasing video pts: 0.167000 < 0.292000  0/  0 ??% ??% ??,?% 0 0 
Decreasing video pts: 0.209000 < 0.292000  0/  0 ??% ??% ??,?% 1 0 
Decreasing video pts: 0.250000 < 0.292000  0/  0 ??% ??% ??,?% 2 0 

```

---

### Post by ogooreck on 2010-01-03
> **Starks said:**
> It works.


Thanks Alan !

It works here too.

My steps:

1. checkout mplayer from svn (or prepare your sources for patching)
2. checkout coreavc-for-linux
3. apply dshowserver.patch to mplayer sources
4. configure mplayer sources
5. make install mplayer
6. Install wine
7. Install coreavc on wine
8. Copy dshowserver.exe to CoreAVC install dir
9. Create a wrapper script to run dshowserver.exe - see code. Name it dshowserver and place in PATH. "Disable" old dshowserver.
10. Configure mplayer - old codecs.conf configuration just works. There are new tips how to workaround fourcc issues in README
11. Enjoy your movies

```
#!/bin/sh

DSHOWSERVEREXE="c:\\Program Files\\CoreCodec\\CoreAVC Professional Edition\\dshowserver.exe"
wine "${DSHOWSERVEREXE}" "$@"
# if you wish to run dshowserver with elevated priority comment out line above and uncomment line below
# nice -n -5 wine "${DSHOWSERVEREXE}" "$@"

```

---

### Post by BagRackRider on 2010-01-03
Sweet! I gotta try this when I get home!

But isn't there going to be a performance loss? I mean now it's using wine itself as the "middle hand" in all this.

---

### Post by Sölve on 2010-01-03
When I trying to play a mkv file with new dshowserver and fresh compiled mplayer, console throws:

```
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC) "To Aru Kagaku no Railgun - 13", -vid 0
[mkv] Track ID 2: audio (A_AAC) "AAC 2.0", -aid 0, -alang jpn
[mkv] Track ID 3: subtitles (S_TEXT/***), -sid 0, -slang eng
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1280x720  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
SUB: error recoding line.
SUB: Added subtitle file (1): /media/wszystko/Anime2/To Aru Kagaku no Railgun/[Mazui]_To_Aru_Kagaku_no_Railgun_-_13v2_[54AB9810].***
[gl] using extended formats. Use -vo gl:nomanyfmts if playback fails.
==========================================================================
Forced video codec: coreserve
Opening video decoder: [dshowserver] DirectShowServer video codecs
dshowserver --codec CoreAVCDecoder.ax --size 1280x720 --guid 09571a4b-f1fe-4c60-9760de6d310c7c31 --fourc 0x31637661 --bits 12 --outfmt 0x32315659 --pid 20012 --id b6994700 --numpages 10 --port 0 &
Opening device (port is 0)
len: 992
ProductVersion: 2.0.0
fixme:thread:SetThreadIdealProcessor (0x74): stub
fixme:thread:SetThreadIdealProcessor (0x7c): stub
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Decoder supports the following YUV formats: YUY2 UYVY YV12 I420 
Unknown type specified: 2
Decoder is capable of YUV output (flags 0x2b)
Setting fmt
Starting
Initialization is complete
Using semaphore based mutex
DirectShow filter failedVDecoder init failed :(
Cannot find codec matching selected -vo and video format 0x31637661.
==========================================================================
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
FAAD: compressed input bitrate missing, assuming 128kbit/s!
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
```The command is:
```
-vo gl:yuv=2:force-pbo:ati-hack -vc coreserve -demuxer mkv
```
And yes, I updated my codecs.conf. What can I do?

---

### Post by ogooreck on 2010-01-03
> **Sölve said:**
> When I trying to play a mkv file with new dshowserver and fresh compiled mplayer, console throws:
...
What can I do?

Check sources.
Do You have latest release r85 ? look at vd_dshowserver.c. First line should be uncommented and second commented out.

```
    ds_mpi->sem = timed_seminit(DS_SOCKET, &port, 1);
    //ds_mpi->sem = timed_seminit(DS_SEMAPHORE, id, 1);

```

---

### Post by BagRackRider on 2010-01-03
This is what happens to me after putting dshowserver.exe in system32 and running the codec test:

$ wine dshowserver.exe -c "c:\\Program Files\\CoreCodec\\CoreAVC Professional Edition\\CoreAVCDecoder.ax"  -s 1280x720 -g 09571a4b-f1fe-4c60-9760de6d310c7c31 -b 12 -f 0x34363248 -o 0x30323449 -d

No id specified, assuming test mode
Opening device (port is 0)
len: 992
ProductVersion: 2.0.0
fixme:thread:SetThreadIdealProcessor (0x6c): stub
fixme:thread:SetThreadIdealProcessor (0x70): stub
Decoder supports the following YUV formats: YUY2 UYVY YV12 I420
Decoder is capable of YUV output (flags 0x2b)
Setting fmt
Starting
Initialization is complete


But playing a file doesn't work:
$ mplayer -vc coreserve test.mkv

MPlayer SVN-r29945-4.3.4 (C) 2000-2009 MPlayer Team
141 audio & 309 video codecs

Playing test.mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_DTS), -aid 0, -alang eng
[mkv] Track ID 3: subtitles (S_TEXT/UTF8), -sid 0, -slang eng
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1280x688  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Forced video codec: coreserve
Opening video decoder: [dshowserver] DirectShowServer video codecs
nice: cannot set niceness: Permission denied
DirectShow filter failedVDecoder init failed :(
Cannot find codec matching selected -vo and video format 0x31637661.

---

### Post by BagRackRider on 2010-01-03
> **ogooreck said:**
> Check sources.
Do You have latest release r85 ? look at vd_dshowserver.c. First line should be uncommented and second commented out.

```
    ds_mpi->sem = timed_seminit(DS_SOCKET, &port, 1);
    //ds_mpi->sem = timed_seminit(DS_SEMAPHORE, id, 1);

```

Don't even have that file in the svn release I just fetched.

---

### Post by ogooreck on 2010-01-03
> **chuckman78 said:**
> I am in the same situation, I think. I am watching lots of artifacts and distortion when playing lots of 720p and 1080p mkv files. I am using coreavc 1.9.5.

Also, Is there a way to configure coreavc in Ubuntu? It has some config options under windows...

Regards,

Carlos.

You may be hit by this issue

[http://code.google.com/p/coreavc-for-linux/issues/detail?id=37&can=1](http://code.google.com/p/coreavc-for-linux/issues/detail?id=37&can=1)


with newest dshowserver release one can use configuration dialog under wine

---

### Post by ogooreck on 2010-01-03
> **BagRackRider said:**
> 
==========================================================================
Forced video codec: coreserve
Opening video decoder: [dshowserver] DirectShowServer video codecs
nice: cannot set niceness: Permission denied
DirectShow filter failedVDecoder init failed :(
Cannot find codec matching selected -vo and video format 0x31637661.

remove nice from wrapper:

```
#!/bin/sh

DSHOWSERVEREXE="c:\\Program Files\\CoreCodec\\CoreAVC Professional Edition\\dshowserver.exe"
wine "${DSHOWSERVEREXE}" "$@"

```

or modify your /etc/security/limits.conf (I think):

user - nice -20

---

### Post by ogooreck on 2010-01-03
> **BagRackRider said:**
> Don't even have that file in the svn release I just fetched.

file is created when You apply dshowserver.patch .

In mplayer sources:

libmpcodecs/vd_dshowserver.c

---

### Post by BagRackRider on 2010-01-03
Now I got the same error as Sölve. Probably because of the mplayer patch I never applied. (using the old mplayer coreavc build)

---

### Post by ogooreck on 2010-01-03
> **BagRackRider said:**
> Now I got the same error as Sölve. Probably because of the mplayer patch I never applied. (using the old mplayer coreavc build)

You need new patch it changed it is mendatory.

---

### Post by BagRackRider on 2010-01-03
I think we might have a minor issue...
This patch [http://pastebin.com/pastebin.php?dl=f7ca459d](http://pastebin.com/pastebin.php?dl=f7ca459d) ain't applied to the dshowserver sources now. Not that I can see anyway. Therefor all movies won't play.

AVC sources play fine, H264/h264 don't.

---

### Post by Sölve on 2010-01-03
Dont use this patch. Use patch from sources downloaded from SVN (coreavc-for-linux).
In coreavc-for-linux wiki are new howtos. Maybe someone can write full tutorial?

---

### Post by ogooreck on 2010-01-03
> **BagRackRider said:**
> I think we might have a minor issue...
This patch [http://pastebin.com/pastebin.php?dl=f7ca459d](http://pastebin.com/pastebin.php?dl=f7ca459d) ain't applied to the dshowserver sources now. Not that I can see anyway. Therefor all movies won't play.

AVC sources play fine, H264/h264 don't.

There is no need to apply this patch. it should be extended because it breaks avi file (h264 in avi) playing. The workaround is to change codecs.conf as described in vd_dshowserver.c source file.

---

### Post by BagRackRider on 2010-01-03
> **ogooreck said:**
> There is no need to apply this patch. it should be extended because it breaks avi file (h264 in avi) playing. The workaround is to change codecs.conf as described in vd_dshowserver.c source file.

Well, as it is now my H264 .mp4 don't play. I only get a black picture... so something must be wrong?

EDIT:
Using fourcc in this order solved my problem:
```
  fourcc H264,h264 AVC1
  fourcc X264,x264
  fourcc avc1,AVC1 AVC1
  fourcc davc,DAVC
  fourcc VSSH

```

So it's finally working. ;)

---

### Post by ogooreck on 2010-01-03
> **BagRackRider said:**
> Well, as it is now my H264 .mp4 don't play. I only get a black picture... so something must be wrong?

Did You try this in codecs.conf ?

```
videocodec coreserve
  info "CoreAVC DShow H264 decoder"
  status working
  format 0x10000005
  fourcc H264,h264 AVC1
  fourcc X264,x264
  fourcc avc1,AVC1 AVC1
  fourcc davc,DAVC
  fourcc VSSH
  driver dshowserver
  dll "CoreAVCDecoder.ax"
  guid 0x09571a4b, 0xf1fe, 0x4c60, 0x97, 0x60, 0xde, 0x6d, 0x31, 0x0c, 0x7c, 0x31
  out YV12,IYUV,I420,YUY2

```

---

### Post by Sölve on 2010-01-03
Okay. I tried a way from coreavc-for-linux wiki and I must say it really work!
I build a winelib, and I don't saw any decrease in performance.
I tried with r100.

---

### Post by AlanNisota on 2010-01-03
There were a few comments I saw here that I thought I'd respond to.
1) Using wine wil lnot affect performance in any significant way.  the number of Win32 calls is small, all the real work is done inside the Codec itself.  The Wine emulator is doing exactly the same task as the 'loader' code that was in use before and should be as efficient as well.  Now, switching from semaphores to sockets could have a performance impact, but in my tests, it was negligible.

2) Make sure to use the latest code (currently R100)

3) The wiki has been updated with the latest instructions, including proper installation instructions.  If there are issues please give me feedback and I'll try to improve it.

4) As of 2009-09-01 mplayer no longer properly will pass AVC1 headers to CoreAVC.  As noted in the source, this can be fixed via a hack to the codecs.conf file, but that may break non AVC1 streams.  altrnatively, you can comment out this in libmpdemux/mp_taglists.c:
```

    { CODEC_ID_H264,              MKTAG('H', '2', '6', '4')},
```This only affects using the lavf demuxer.  I don't know how to properly fix this issue.

5) you can now use **dshowserver -c CoreAVCDecoder.ax --config** to configure CoreAVC, but you need to install dcom98 into Wine first.

---

### Post by AlanNisota on 2010-01-03
Additionally, there should be no difference between building with winelib, or using the precompiled .exe

Using winelib allows using semaphore message passing if you are interested in playing with that, but otherwise the code should behave exactly the same.  No amount of compile-time optimizations will make a significant performance impact, so there isn't much point, unless you don't trust binaries, which is perfectly understandable

---

### Post by Sölve on 2010-01-03
Hmm, but I noticed, Wine longer loads a dshowserver than "loader".
[SIZE=1][COLOR=#000000]Can the loading time be shortened?[/COLOR][/SIZE]

---

### Post by AlanNisota on 2010-01-03
you mean the startup time?  I don't think much can be done about that.  The only thing I can think of is that you can start the wineserver manually and leave it running in the background.  I didn't notice a significant difference in startup time myself.  Once it is started, decoding should have identical performance.  You could probably try running a profiler and see what is going on.  I've never tried using one under Wine though.

---

### Post by Starks on 2010-01-03
The dcom98 overrides for CoreAVC configuration break wine. 

```
eric@kingfisher:~/coreavc/dshowserver$ dshowserver -c CoreAVCDecoder.ax  --config 
Starting wine dshowserver.exe.so 
err:module:attach_process_dlls "rpcrt4.dll" failed to initialize, aborting 
err:module:LdrInitializeThunk Main exe initialization for  L"Z:\\usr\\share\\dshowserver\\dshowserver.exe" failed, status c0000005
```

---

### Post by AlanNisota on 2010-01-03
> **Starks said:**
> The dcom98 overrides for CoreAVC configuration break wine. 

```
eric@kingfisher:~/coreavc/dshowserver$ dshowserver -c CoreAVCDecoder.ax  --config 
Starting wine dshowserver.exe.so 
err:module:attach_process_dlls "rpcrt4.dll" failed to initialize, aborting 
err:module:LdrInitializeThunk Main exe initialization for  L"Z:\\usr\\share\\dshowserver\\dshowserver.exe" failed, status c0000005
```

Is that a clean wine install?

I did (be aware that this will purge all programs installed into wine.  you can alternatively use WINEPREFIX instead)
```

rm -rf ~/.wine
wine <path to Core AVC Setup.exe>
winetricks dcom98
dshowserver -c CoreAVCDecoder.ax  --config

```

I've tried it on the latest Wine from git as well as 1.1.9 and it worked fine with both.

---

### Post by Starks on 2010-01-03
The config works after clearing my .wine, but then I can't run dshowserver without the config flag.

---

### Post by ripps818 on 2010-01-04
Awesome, I've got working dshowserver and mplayer packages running coreavc-2.0 in my Lucid staging ppa. Now all I have to do is setup up some ppabot configs so I can easily backport this work to older Ubuntu releases.

---

### Post by ogooreck on 2010-01-04
> **AlanNisota said:**
> There were a few comments I saw here that I thought I'd respond to.
1) Using wine wil lnot affect performance in any significant way.  the number of Win32 calls is small, all the real work is done inside the Codec itself.  The Wine emulator is doing exactly the same task as the 'loader' code that was in use before and should be as efficient as well.  Now, switching from semaphores to sockets could have a performance impact, but in my tests, it was negligible.

I can't see any performance loss with precompiled binary. Actually things works better now maybe because better coreavc 2.0 performance. Overall performance is better, at least on my computer.

> 3) The wiki has been updated with the latest instructions, including proper installation instructions.  If there are issues please give me feedback and I'll try to improve it.

You could mention about following issues:

1. -framdrop   
[http://code.google.com/p/coreavc-for-linux/issues/detail?id=37](http://code.google.com/p/coreavc-for-linux/issues/detail?id=37)

2. expand filter issue
[http://code.google.com/p/coreavc-for-linux/issues/detail?id=63](http://code.google.com/p/coreavc-for-linux/issues/detail?id=63)

3. 
[http://code.google.com/p/coreavc-for-linux/issues/detail?id=29](http://code.google.com/p/coreavc-for-linux/issues/detail?id=29)

Thank You once again

---

### Post by BagRackRider on 2010-01-04
Yes, the codec seems to work better here too. 

And for me, the loading times ain't really noticable. If you think they're slow, try "apt-get install preload", then run mplayer/coreavc a few times and see if it helps.

TBH, I'm quite impressed by the achivement. Good work all who were involved. ;)

---

### Post by wiiaboo on 2010-01-04
Using r100, it is indeed working with me too.

---

### Post by AlanNisota on 2010-01-04
Here is a patch (ported from ticket 37) that you can try to address the framedrop issue.  apply it after applying the directshow patch:
```

Index: libmpcodecs/vd_dshowserver.c
===================================================================
--- libmpcodecs/vd_dshowserver.c.orig    2010-01-04 08:27:18.000000000 -0800
+++ libmpcodecs/vd_dshowserver.c    2010-01-04 08:27:15.000000000 -0800
@@ -241,10 +241,6 @@
    int ret;
    if(len<=0) return NULL; // skipped frame
 
-   if(flags&3) {
-      // framedrop:
-      return NULL;
-   }
    ds_mpi->vd->cmd = VD_DECODE; //'2' is cmd for decoding
    ds_mpi->vd->pts = (uint64_t)(sh->buffered_pts[0]*1E9);
    memcpy(ds_mpi->data, data, len);
@@ -263,6 +259,10 @@
    ds_mpi->vd->buflen = len;
    timed_sempost(ds_mpi->sem);
    ret = timed_semwait(ds_mpi->sem, 10);
+   if(flags&3) {
+      // framedrop:
+      return NULL;
+   }
    //printf("len: %d, PTS (ret:%d,vd_ret:%d): %f -> %f\n", len, ret, ds_mpi->vd->ret, sh->buffered_pts[0], (double)ds_mpi->vd->pts/1E9);
    //printf("PTS (%d): %f(%d) -> %d\n", ds_mpi->vd->ret, sh->buffered_pts[0], pts-1, ds_mpi->vd->pts);
    if(ret == 1 && ds_mpi->vd->ret && ! (ds_mpi->vd->ret & (1<<31))) {

```

The reason I hadn't included it before is that it doesn't really do anything.  You are still decoding every frame, just not displaying it, so you don't really save any CPU unless you need to do software conversion from YUV to RGB.  There doesn't seem to be any way to actually not process frames other than dropping B-frames, which I'm not sure that coreAVC supports.  Anyhow let me know if the patch is better.  It certainly shouldn't be any worse than what is in the codebase today.

---

### Post by ogooreck on 2010-01-04
Thank You, I will check if it is better then using -noframedrop mplayer option. I think it is, because in my opinion it's better ignore this option then have distorted picture.

And another note on fourcc issue. Attached patch forces mplayer to select mov demuxer by default (like mkv demuxer) for files that seems to be affected by this issue. lavf demuxer can be selected with -demuxer lavf as always. I also tried to compile mplayer with --disable-demuxer=mov but this caused errors in mplayer's file type detection (it reported mp4 stream as mp3 stream).

```
--- libmpdemux/demux_lavf.c    (revision 30118)
+++ libmpdemux/demux_lavf.c    (working copy)
@@ -177,7 +177,7 @@
     "gxf",
     "nut",
     "nuv",
-    "mov,mp4,m4a,3gp,3g2,mj2",
+//    "mov,mp4,m4a,3gp,3g2,mj2",
     "mpc",
     "mpc8",
     "mxf",
```

---

### Post by Zorael on 2010-01-04
I'm about to give this another go and I'm overwhelmed by the patches and whatnot mentioned in only the last few pages.

I'm currently using the binaries from ripps818's ppa. aptitude wants to replace mplayer (2:1.0~rc3+svn20090426-1ubuntu10+coreavc1) with the version from karmic-updates, but I told it to forbid that version for the time being. 'dshowserver -c CoreAVCDecoder.ax' works nicely.
```
$ dshowserver -c CoreAVCDecoder.ax
Starting wine dshowserver.exe
No id specified, assuming test mode
Using default width  for CoreAVCDecoder.ax: 1280
Using default height for CoreAVCDecoder.ax: 720
Using default fourcc for CoreAVCDecoder.ax: 0x34363248
Using default outfmt for CoreAVCDecoder.ax: 0x30323449
Using default outbit for CoreAVCDecoder.ax: 12
Using default GUID   for CoreAVCDecoder.ax: 09571a4b-f1fe-4c60-9760de6d310c7c31
Opening device (port is 0)
len: 992
ProductVersion: 2.0.0
fixme:thread:SetThreadIdealProcessor (0x6c): stub
fixme:thread:SetThreadIdealProcessor (0x70): stub
Decoder supports the following YUV formats: YUY2 UYVY YV12 I420
Decoder is capable of YUV output (flags 0x2b)
Setting fmt
Starting
Initialization is complete
```

But when I try to play something, it fails to produce any video. (scroll down)
```
$ mplayer -vc coreserve the.usual.suspects.1995.dvd5.720p.bluray.x264.sample-hv.mkv 
MPlayer SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team                                                             
mplayer: could not connect to socket                                                                            
mplayer: No such file or directory                                                                              
Failed to open LIRC support. You will not be able to use your remote control.                                   

Playing the.usual.suspects.1995.dvd5.720p.bluray.x264.sample-hv.mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC) "The Usual Suspects", -vid 0
[mkv] Track ID 2: audio (A_DTS) "DTS 5.1", -aid 0, -alang eng         
[mkv] Will play video track 1.                                        
Matroska file format detected.                                        
VIDEO:  [avc1]  1280x544  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
open: No such file or directory                                       
[MGA] Couldn't open: /dev/mga_vid                                     
open: No such file or directory                                       
[MGA] Couldn't open: /dev/mga_vid                                     
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.                   
[VO_3DFX] Unable to open /dev/3dfx.                                   
==========================================================================
Forced video codec: coreserve                                             
Opening video decoder: [dshowserver] DirectShowServer video codecs        
Starting wine dshowserver.exe                                             
Opening device (port is 0)                                                
len: 992                                                                  
ProductVersion: 2.0.0                                                     
fixme:thread:SetThreadIdealProcessor (0x7c): stub                         
fixme:thread:SetThreadIdealProcessor (0x80): stub
Decoder supports the following YUV formats: YUY2 UYVY YV12 I420
Unknown type specified: 2
Decoder is capable of YUV output (flags 0x2b)
Setting fmt
Starting
Initialization is complete
Using semaphore based mutex
[B][COLOR="Red"]DirectShow filter failedVDecoder init failed :(
Cannot find codec matching selected -vo and video format 0x31637661.[/COLOR][/B]
Read DOCS/HTML/en/codecs.html!
==========================================================================
==========================================================================
Opening audio decoder: [libdca] DTS decoding with libdca
Stream with high frequencies VQ coding
AUDIO: 48000 Hz, 2 ch, s16le, 1536.0 kbit/100.00% (ratio: 192000->192000)
Selected audio codec: [dts] afm: libdca (DTS-libdca)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   2.3 (02.2) of 61.5 (01:01.5) 29.5%

MPlayer interrupted by signal 2 in module: key_events
A:   2.3 (02.2) of 61.5 (01:01.5) 29.3%
Exiting... (Quit)
```
The error message isn't precisely verbose.

Thinking I need to build it myself, I fail at even compiling dshowserver.
```
make[1]: Leaving directory `/home/zorael/src/mplayer/coreavc-for-linux/loader'
winegcc  -o dshowserver ../objs-winelib/server.o ../objs-winelib/timeout_sem.o ../objs-winelib/defaults.o ../objs-winelib/crc32.o ../objs-winelib/libloader.a -lm -lole32 -loleaut32 -lrt -lpthread
/usr/bin/ld: cannot find -lwine
collect2: ld returned 1 exit status
winegcc: i486-linux-gnu-gcc failed
make: *** [dshowserver] Error 2
```
Anything obvious I'm doing wrong?

**edit:** Giving it a second browse I see it's the same issue Stark describes a few pages back, but he doesn't elaborate as to how he got around it.

Running dshowserver normally (i.e. not testing CoreAVCDecoder.ax) makes it immediately crash, by the way.
```
$ dshowserver                                                                         
Starting wine dshowserver.exe                                                                                     
No id specified, assuming test mode                                                                               
wine: Unhandled page fault on read access to 0x00000000 at address 0xb74defb7 (thread 0009), starting debugger... 
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0xb74defb7).                         
Register dump:                                                                                                    
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b                                                                  
 EIP:b74defb7 ESP:0063fd58 EBP:0063fda8 EFLAGS:00010282(   - 00      - RIS1)                                      
 EAX:00000000 EBX:b75aaff4 ECX:00000001 EDX:00000000                                                              
 ESI:00000000 EDI:0063fe90                                                                                        
Stack dump:                                                                                                       
0x0063fd58:  00126ed8 00000002 00000000 0000002e                                                                  
0x0063fd68:  7edd24bb 7edf3ff4 00000001 7edfa100                                                                  
0x0063fd78:  0063fdb8 7edd2fc4 00000001 7edf1540                                                                  
0x0063fd88:  00000001 7bc41aee 00126328 001103e0                                                                  
0x0063fd98:  00000001 7bc8aff4 00000000 0063fe90                                                                  
0x0063fda8:  0063fdc8 7bc68844 00000000 0040d0f0                                                                  
Backtrace:                                                                                                        
=>1 0xb74defb7 strstr+0x17() in libc.so.6 (0x0063fda8)                                                            
  2 0x7bc68844 NTDLL_strstr+0x24() in ntdll (0x0063fdc8)                                                          
  3 0x00402458 in dshowserver (+0x2458) (0x0063fdf8)                                                              
  4 0x00401c35 in dshowserver (+0x1c35) (0x0063fea8)                                                              
  5 0x004011e9 __mingw_CRTStartup+0xd9() [/build/buildd/mingw32-runtime-3.13/build_dir/src/mingw-runtime-3.13-20070825-1/crt1.c:237] in dshowserver (0x0063fee8)                                                                    
  6 0x00401233 in dshowserver (+0x1233) (0x0063ff08)                                                              
  7 0x7b877f48 in kernel32 (+0x57f48) (0x0063ffe8)                                                                
0xb74defb7 strstr+0x17 in libc.so.6: movzbl     0x0(%edx),%eax                                                    
Modules:                                                                                                          
Module  Address                 Debug info      Name (58 modules)                                                 
PE        400000-  440000       Stabs           dshowserver                                                       
ELF     7b800000-7b93c000       Export          kernel32<elf>                                                     
  \-PE  7b820000-7b93c000       \               kernel32                                                          
ELF     7bc00000-7bca7000       Export          ntdll<elf>                                                        
  \-PE  7bc10000-7bca7000       \               ntdll                                                             
ELF     7bf00000-7bf04000       Deferred        <wine-loader>                                                     
ELF     7e556000-7e561000       Deferred        libxcursor.so.1                                                   
ELF     7e561000-7e567000       Deferred        libxfixes.so.3                                                    
ELF     7e567000-7e56b000       Deferred        libxcomposite.so.1                                                
ELF     7e56b000-7e574000       Deferred        libxrandr.so.2                                                    
ELF     7e574000-7e57e000       Deferred        libxrender.so.1                                                   
ELF     7e57e000-7e581000       Deferred        libxinerama.so.1                                                  
ELF     7e581000-7e5a2000       Deferred        imm32<elf>                                                        
  \-PE  7e590000-7e5a2000       \               imm32                                                             
ELF     7e5a2000-7e5a7000       Deferred        libxdmcp.so.6                                                     
ELF     7e5a7000-7e5c5000       Deferred        libxcb.so.1                                                       
ELF     7e5c5000-7e5c9000       Deferred        libxau.so.6                                                       
ELF     7e5c9000-7e5ce000       Deferred        libuuid.so.1                                                      
ELF     7e5ce000-7e6fd000       Deferred        libx11.so.6                                                       
ELF     7e6fd000-7e70d000       Deferred        libxext.so.6                                                      
ELF     7e70d000-7e713000       Deferred        libxxf86vm.so.1                                                   
ELF     7e713000-7e72e000       Deferred        libice.so.6                                                       
ELF     7e72e000-7e737000       Deferred        libsm.so.6                                                        
ELF     7e74e000-7e7e8000       Deferred        winex11<elf>                                                      
  \-PE  7e760000-7e7e8000       \               winex11                                                           
ELF     7e8b5000-7e8dc000       Deferred        libexpat.so.1                                                     
ELF     7e8dc000-7e909000       Deferred        libfontconfig.so.1                                                
ELF     7e909000-7e91f000       Deferred        libz.so.1                                                         
ELF     7e91f000-7e995000       Deferred        libfreetype.so.6                                                  
ELF     7e995000-7e9c2000       Deferred        ws2_32<elf>                                                       
  \-PE  7e9a0000-7e9c2000       \               ws2_32                                                            
ELF     7e9c2000-7ea68000       Deferred        oleaut32<elf>                                                     
  \-PE  7e9d0000-7ea68000       \               oleaut32                                                          
ELF     7ea68000-7ea7c000       Deferred        libresolv.so.2                                                    
ELF     7ea93000-7eab2000       Deferred        iphlpapi<elf>                                                     
  \-PE  7eaa0000-7eab2000       \               iphlpapi                                                          
ELF     7eab2000-7eb15000       Deferred        rpcrt4<elf>                                                       
  \-PE  7eac0000-7eb15000       \               rpcrt4                                                            
ELF     7eb15000-7ebb4000       Deferred        gdi32<elf>                                                        
  \-PE  7eb30000-7ebb4000       \               gdi32                                                             
ELF     7ebb4000-7ecff000       Deferred        user32<elf>                                                       
  \-PE  7ebd0000-7ecff000       \               user32                                                            
ELF     7ecff000-7eda5000       Deferred        ole32<elf>                                                        
  \-PE  7ed10000-7eda5000       \               ole32                                                             
ELF     7eda5000-7ee0f000       Deferred        msvcrt<elf>                                                       
  \-PE  7edc0000-7ee0f000       \               msvcrt                                                            
ELF     7ee0f000-7ee61000       Deferred        advapi32<elf>                                                     
  \-PE  7ee20000-7ee61000       \               advapi32                                                          
ELF     7ef8d000-7ef99000       Deferred        libnss_files.so.2                                                 
ELF     7ef99000-7efa4000       Deferred        libnss_nis.so.2                                                   
ELF     7efa4000-7efbb000       Deferred        libnsl.so.1                                                       
ELF     7efbb000-7efc3000       Deferred        libnss_compat.so.2                                                
ELF     7efc3000-7efe9000       Deferred        libm.so.6                                                         
ELF     b7467000-b746b000       Deferred        libdl.so.2                                                        
ELF     b746b000-b75af000       Export          libc.so.6                                                         
ELF     b75b0000-b75c9000       Deferred        libpthread.so.0
ELF     b75e0000-b7716000       Deferred        libwine.so.1
ELF     b7718000-b7735000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\usr\share\dshowserver\dshowserver.exe
        00000009    0 <==
0000000c
        00000013    0
        00000012    0
        0000000e    0
        0000000d    0
0000000f
        00000015    0
        00000014    0
        00000011    0
        00000010    0
Backtrace:
=>1 0xb74defb7 strstr+0x17() in libc.so.6 (0x0063fda8)
  2 0x7bc68844 NTDLL_strstr+0x24() in ntdll (0x0063fdc8)
  3 0x00402458 in dshowserver (+0x2458) (0x0063fdf8)
  4 0x00401c35 in dshowserver (+0x1c35) (0x0063fea8)
  5 0x004011e9 __mingw_CRTStartup+0xd9() [/build/buildd/mingw32-runtime-3.13/build_dir/src/mingw-runtime-3.13-20070825-1/crt1.c:237] in dshowserver (0x0063fee8)
  6 0x00401233 in dshowserver (+0x1233) (0x0063ff08)
  7 0x7b877f48 in kernel32 (+0x57f48) (0x0063ffe8)
```

---

### Post by Sölve on 2010-01-04
You must install wine-dev packet. You can do this in Synaptic. If this fail, install wine1.2-dev (this automatically remove wine packet).
//EDIT:
You can use precompiled binaries too. I recommend a clean installation of wine1.2.

---

### Post by BagRackRider on 2010-01-04
Zorael, I don't think you can run dshowserver from the commandline without a valid arg. It crashes here too if I just type dshowserver.
Have you downloaded mplayer svn and patched it with the mplayer patch in the coreavc sources directory?

---

### Post by Zorael on 2010-01-04
> **BagRackRider said:**
> Zorael, I don't think you can run dshowserver from the commandline without a valid arg. It crashes here too if I just type dshowserver.
Well, as long as it's not indicative of an error from my part. :3

> **BagRackRider said:**
> Have you downloaded mplayer svn and patched it with the mplayer patch in the coreavc sources directory?
No, I'm using binaries from ripp181's ppa. A few replies back he said he had gotten it to work with CoreAVC 2.0 on Lucid, and was working on a way to backport them to Karmic. Seeing as it doesn't work over here (again, with "DirectShow filter failedVDecoder init failed"), the next step is to try to compile dshowserver myself.

I'm still curious to know how Stark worked around it though, as his code snippet had the same error message I get.

---

### Post by Zorael on 2010-01-04
To follow up, it works after compiling dshowserver myself and replacing ripps818's package with my own files. Stuff plays now, which is a start.

I installed wine1.2 as a whole when I was to get wine-dev, but wine1.2 gets an illegal exception upon start so nothing requiring wine worked. I replaced it with normal wine packages and now I only get a screen full of backtraces (but it works).

Would you recommend I compile mplayer myself anyway and make sure to apply the patches/tweaks mentioned so far?
[list][*]libmpdemux/mp_taglists.c from [#294](http://ubuntuforums.org/showpost.php?p=8605564&postcount=294)
[*]libmpcodecs/vd_dshowserver.c from [#305](http://ubuntuforums.org/showpost.php?p=8608716&postcount=305)
[*]libmpdemux/demux_lavf.c from [#306](http://ubuntuforums.org/showpost.php?p=8609342&postcount=306)[/list]

---

### Post by BagRackRider on 2010-01-04
You have to compile mplayer yourself. I did the same mistake thinking the old mplayer I had for CoreAVC 1.9.5 would work, it doesn't.

---

### Post by ogooreck on 2010-01-05
> **Zorael said:**
> Would you recommend I compile mplayer myself anyway and make sure to apply the patches/tweaks mentioned so far?
[LIST]
[*]libmpdemux/mp_taglists.c from [#294]("http://ubuntuforums.org/showpost.php?p=8605564&postcount=294")
[*]libmpcodecs/vd_dshowserver.c from [#305]("http://ubuntuforums.org/showpost.php?p=8608716&postcount=305")
[*]libmpdemux/demux_lavf.c from [#306]("http://ubuntuforums.org/showpost.php?p=8609342&postcount=306")
[/LIST]


Use patches if You experience issues they correct. Use #294 OR #306 not both. The latter is my own invention, it works for me so far. It has effect similar to adding "-demuxer mov" on command line. It changes default mplayer's demuxer preference.

---

### Post by ripps818 on 2010-01-05
Yeah, the dshowserver in the ppa works, but the mplayer doesn't use correct patch yet. I have a working mplayer in another ppa, but my backporting software isn't working nice at the moment. I'll do some manual backports of mplayer to the ppa in the mean time.

UPDATE:
Okay, I've got some new dshowserver patched mplayer packages in the PPA. It seems to work in my Lucid machine, but I'd very much like people to test them. :)

[https://launchpad.net/~ripps818/+archive/coreavc/+packages](https://launchpad.net/~ripps818/+archive/coreavc/+packages)

---

### Post by Zorael on 2010-01-06
> **ripps818 said:**
> UPDATE:
Okay, I've got some new dshowserver patched mplayer packages in the PPA. It seems to work in my Lucid machine, but I'd very much like people to test them. :)

[https://launchpad.net/~ripps818/+archive/coreavc/+packages](https://launchpad.net/~ripps818/+archive/coreavc/+packages)
Your dshowserver package still doesn't work for me. Everything looks right but video doesn't play (see earlier post). My own compiled dshowserver does the trick, though. This is on Karmic.

(edit, no sense in making another post)
Would it be possible to combine this dshowserver-aware mplayer with ffmpeg-mt? I realize CoreAVC does its own threading, but it only plays H264/AVC files, right? And falls back to ffmpeg for the rest?

---

### Post by ripps818 on 2010-01-06
> **Zorael said:**
> Your dshowserver package still doesn't work for me. Everything looks right but video doesn't play (see earlier post). My own compiled dshowserver does the trick, though. This is on Karmic.

(edit, no sense in making another post)
Would it be possible to combine this dshowserver-aware mplayer with ffmpeg-mt? I realize CoreAVC does its own threading, but it only plays H264/AVC files, right? And falls back to ffmpeg for the rest?

First, are you using both the dshowserver and mplayer from the ppa? I didn't compile anything in dshowserver, the package uses the precompiled binaries from svn.

Second, as far as I can recall, in order to get mplayer to use multiple threads, all you need to do is add `-lavdopts threads=n` (where n is the number threads you want, I assume 1 per core of your processor).


UPDATE:
After doing some experimenting, it seems that I get the exact same problem as you when I don't specify the video output. Add '-vo xv' or '-vo gl' or whatever your preferred method is.

---

### Post by Bachstelze on 2010-01-06
*Please delete.*

---

### Post by Bachstelze on 2010-01-06
Well, the new dshowserver using WINE seems to be a giant step backwards for me. I can't get it to work on a 64bit system (not tried on a 32bit yet). Not to mention that it adds a huge dependency.

---

### Post by Zorael on 2010-01-06
> **ripps818 said:**
> First, are you using both the dshowserver and mplayer from the ppa? I didn't compile anything in dshowserver, the package uses the precompiled binaries from svn.
Yes, both packages from the ppa.
```
$ apt-cache policy mplayer-nogui dshowserver
mplayer-nogui:
  Installed: 2:1.0~rc3+svn20090426-1ubuntu10+coreavc1
  **[COLOR="Red"]Candidate: 2:1.0~rc3+svn20090426-1ubuntu10.1[/COLOR]**
  Version table:
     [B][COLOR="red"]2:1.0~rc3+svn20090426-1ubuntu10.1 0
        500 http://se.archive.ubuntu.com karmic-updates/multiverse Packages[/COLOR][/B]
 *** 2:1.0~rc3+svn20090426-1ubuntu10+coreavc1 0
        500 http://ppa.launchpad.net karmic/main Packages
        100 /var/lib/dpkg/status
     2:1.0~rc3+svn20090426-1ubuntu10 0
        500 http://se.archive.ubuntu.com karmic/multiverse Packages
dshowserver:
  Installed: 0-svn101-0ubuntu2~ripps1~karmic
  Candidate: 0-svn101-0ubuntu2~ripps1~karmic
  Version table:
 *** 0-svn101-0ubuntu2~ripps1~karmic 0
        500 http://ppa.launchpad.net karmic/main Packages
        100 /var/lib/dpkg/status
```
Note that it wants to overwrite yours with the karmic-updates/multiverse package, so I have to tell aptitude to hold it.

> **ripps818 said:**
> Second, as far as I can recall, in order to get mplayer to use multiple threads, all you need to do is add `-lavdopts threads=n` (where n is the number threads you want, I assume 1 per core of your processor).
I have an mplayer-mt package installed alongside the normal mplayer-nogui from your ppa, which I grabbed from some ppa or another a while back. rvm's? It seems to have been deleted now though, but I still have it locally installed.

With it, -lavdopts threads=n does work and I have it set up in my ~/.mplayer/config, but it doesn't work with your mplayer; it still only spawns one mplayer thread. When running with -benchmark, the performance difference is noticeable. After cutting out the irrelevant parts;
```
$ mplayer -benchmark -nosound -frames 500 -vc ffh264 -lavdopts threads=4 the.usual.suspects.1995.dvd5.720p.bluray.x264.sample-hv.mkv

**[h264 @ 0xb64ca960]Cannot parallelize deblocking type 1, decoding such frames in sequential order**

BENCHMARKs: VC:  23.428s VO:   0.810s A:   0.000s Sys:   0.243s =   24.480s
BENCHMARK%: VC: 95.7010% VO:  3.3077% A:  0.0000% Sys:  0.9914% = 100.0000%

------------------------------------------------------------

$ mplayer-mt -benchmark -nosound -frames 500 -vc ffh264 -lavdopts threads=4 the.usual.suspects.1995.dvd5.720p.bluray.x264.sample-hv.mkv

BENCHMARKs: VC:  18.482s VO:   0.652s A:   0.000s Sys:   0.305s =   19.438s
BENCHMARK%: VC: 95.0792% VO:  3.3518% A:  0.0000% Sys:  1.5690% = 100.0000%
```
Small sample but mplayer-mt does win out over mplayer consistently. CoreAVC beats both, though.

See also [this thread](http://ubuntuforums.org/showthread.php?t=1104967).

I managed to get it working once a few months back by merely copying the ffmpeg directory from the ffpmeg-mt repo in that thread and overwriting the ffmpeg I fetched from the mplayer svn (as the svn version was fresher). I remember I had to tailor the dshowserver patch a bit to make it apply properly. Then something happened in svn mplayer that broke compatibility with the ffmpeg in the ffmpeg-mt repo, and I haven't retried combining them since.

edit: Latest update to the multithreading repo was Sun Nov 15 00:40:24 2009 +0200.

---

### Post by ripps818 on 2010-01-06
*Deleted*
Chromium double posted me.

---

### Post by ripps818 on 2010-01-06
No, you're not using the latest mplayer package from the ppa. You're using the older version of mplayer that was patched for the old dshowserver. The most recent version in the ppa should be "2:1.0~rc3+svn20100105.30229-0ubuntu2~ripps1~karmic".
Make sure your sources are up to date with 'sudo apt-get update'.

---

### Post by Zorael on 2010-01-06
Ah, I see you're not updating mplayer-nogui, that's why mine isn't getting updated.

Have you applied the framedrop patch to your new package?

---

### Post by ripps818 on 2010-01-06
> **Zorael said:**
> Ah, I see you're not updating mplayer-nogui, that's why mine isn't getting updated.

Have you applied the framedrop patch to your new package?

Yeah, I'm using a modified version the mplayer package from rvm's ppa. It doesn't use mplayer-nogui.

Yes, the latest version of the dshowserver patch from svn has the framedrop fix in it. But from what I read, it doesn't actually improve the performance, it's still trying to render every frame, even if they're not being shown. It just prevents the image from getting corrupted when a frame is dropped.

---

### Post by ogooreck on 2010-01-07
> **Bachstelze said:**
> Well, the new dshowserver using WINE seems to be a giant step backwards for me. I can't get it to work on a 64bit system (not tried on a 32bit yet). Not to mention that it adds a huge dependency.

But wine is constantly updated and improved. It's easier to maintain. CoreAVC is windows app after all.

---

### Post by Zorael on 2010-01-07
I finally managed to get a mplayer with dshowserver support and ffmpeg-mt built, but in addition to me sucking at packaging dput now refuses to finish uploading it to my ppa.

I basically pulled mplayer sources from svn, deleted its debian directory and replaced it with the one from ripp818's source. Then I deleted the ffmpeg, libavcodec, libavformat and libavutil subdirectories and pulled ffmpeg-mt from git, replacing the now-deleted ffmpeg directory with it. In it were modified versions of libavcodec, libavformat and libavutil, which I merely moved to the root mplayer directory, again replacing now-deleted equavilents.

There was also a ffmpeg/mt-work/mplayer.diff patch, which I moved to debian/patches and added a mention of in 00list and series. Lastly I incremented the changelog and had a go at building.

Took a while on this netbook, especially since it was configuring it to build mencoder and the GTK gui and a whole lot of garbage I would otherwise have disabled when ./configuring, but I only realized this when I was halfway through.

**edit:** A ppa search comes up with [Hanbin Lee's ppa](https://launchpad.net/~hanbin973/+archive/ppa) containing built packages of mplayer-mt, seemingly very fresh, latest having been uploaded 2010-02-01. It doesn't seem patched to work with dshowserver though.

---

### Post by kamitsukai on 2010-01-07
I keep getting this error when typing make at the [FONT=monospace]dshowserver part...[/FONT]

```
carl@carl-laptop:~/coreavc-for-linux/dshowserver$ make
mkdir ../objs-winelib
winegcc -I../loader -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D__WINE__ -DNOAVIFILE_HEADERS -DMPLAYER -fno-omit-frame-pointer -mno-omit-leaf-frame-pointer -O2 -o ../objs-winelib/server.o -c server.c
winegcc -I../loader -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D__WINE__ -DNOAVIFILE_HEADERS -DMPLAYER -fno-omit-frame-pointer -mno-omit-leaf-frame-pointer -O2 -o ../objs-winelib/timeout_sem.o -c timeout_sem.c
winegcc -I../loader -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D__WINE__ -DNOAVIFILE_HEADERS -DMPLAYER -fno-omit-frame-pointer -mno-omit-leaf-frame-pointer -O2 -o ../objs-winelib/defaults.o -c defaults.c
winegcc -I../loader -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D__WINE__ -DNOAVIFILE_HEADERS -DMPLAYER -fno-omit-frame-pointer -mno-omit-leaf-frame-pointer -O2 -o ../objs-winelib/crc32.o -c crc32.c
make -C ../loader 
make[1]: Entering directory `/home/carl/coreavc-for-linux/loader'
winegcc -D__MINGW32__ -O2 -Icompat -Idshow -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -fno-omit-frame-pointer -mno-omit-leaf-frame-pointer -DUSE_SHARED_MEM -o ../objs-winelib/DS_Filter.o -c dshow/DS_Filter.c
winegcc -D__MINGW32__ -O2 -Icompat -Idshow -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -fno-omit-frame-pointer -mno-omit-leaf-frame-pointer -DUSE_SHARED_MEM -o ../objs-winelib/DS_VideoDecoder.o -c dshow/DS_VideoDecoder.c
winegcc -D__MINGW32__ -O2 -Icompat -Idshow -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -fno-omit-frame-pointer -mno-omit-leaf-frame-pointer -DUSE_SHARED_MEM -o ../objs-winelib/allocator.o -c dshow/allocator.c
dshow/allocator.c:117: warning: &#8216;MemAllocator_CreateAllocator&#8217; defined but not used
winegcc -D__MINGW32__ -O2 -Icompat -Idshow -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -fno-omit-frame-pointer -mno-omit-leaf-frame-pointer -DUSE_SHARED_MEM -o ../objs-winelib/mediatype.o -c dshow/mediatype.c
winegcc -D__MINGW32__ -O2 -Icompat -Idshow -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -fno-omit-frame-pointer -mno-omit-leaf-frame-pointer -DUSE_SHARED_MEM -o ../objs-winelib/cmediasample.o -c dshow/cmediasample.c
winegcc -D__MINGW32__ -O2 -Icompat -Idshow -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -fno-omit-frame-pointer -mno-omit-leaf-frame-pointer -DUSE_SHARED_MEM -o ../objs-winelib/guids.o -c dshow/guids.c
winegcc -D__MINGW32__ -O2 -Icompat -Idshow -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -fno-omit-frame-pointer -mno-omit-leaf-frame-pointer -DUSE_SHARED_MEM -o ../objs-winelib/inputpin.o -c dshow/inputpin.c
winegcc -D__MINGW32__ -O2 -Icompat -Idshow -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -fno-omit-frame-pointer -mno-omit-leaf-frame-pointer -DUSE_SHARED_MEM -o ../objs-winelib/outputpin.o -c dshow/outputpin.c
ar r ../objs-winelib/libloader.a ../objs-winelib/DS_Filter.o ../objs-winelib/DS_VideoDecoder.o ../objs-winelib/allocator.o ../objs-winelib/mediatype.o ../objs-winelib/cmediasample.o ../objs-winelib/guids.o ../objs-winelib/inputpin.o ../objs-winelib/outputpin.o
ar: creating ../objs-winelib/libloader.a
ranlib ../objs-winelib/libloader.a
make[1]: Leaving directory `/home/carl/coreavc-for-linux/loader'
winegcc  -o dshowserver ../objs-winelib/server.o ../objs-winelib/timeout_sem.o ../objs-winelib/defaults.o ../objs-winelib/crc32.o ../objs-winelib/libloader.a -lm -lole32 -loleaut32 -lrt -lpthread 
/usr/bin/ld: cannot find -lwine
collect2: ld returned 1 exit status
winegcc: i486-linux-gnu-gcc failed
make: *** [dshowserver] Error 2

```

---

### Post by Zorael on 2010-01-07
> **kamitsukai said:**
> i keep getting this error when typing make at the [font=monospace]dshowserver part...[/font]
> **sölve said:**
> you must install wine-dev packet. You can do this in synaptic. If this fail, install wine1.2-dev (this automatically remove wine packet).
//edit:
You can use precompiled binaries too. I recommend a clean installation of wine1.2.
:3

---

### Post by BagRackRider on 2010-01-07
I found out something cool, you can use coreavc-for-linux together with [ps3mediaserver]("http://code.google.com/p/ps3mediaserver/").

Since my server doesn't have a state of the art CPU (p4 2.9ghz celeron) I toyed around with the idea of getting coreavc to decode the mkv/h264 files instead of mencoders builtin codec.

It pretty much worked straight out of the box.
First I disabled deblocking/deinterlacing in coreavc codec to make sure I freed up some CPU power for mencoder. Then all I did was adding this like to PMS.conf (ps3mediaserver's config file)

```

codec_spec_script = width >= 1279 :: -vc coreserve -quality keyint=25:vqscale=2:vqmin=3 -lavdopts fast

```

And there you go, coreavc is now decoding your HD content. ;)
Just make sure mencoder is doing the transcoding for you and not ffmpeg, otherwise the above line won't work.

You can ofcourse toy around with the quality settings and ps3mediaserver's other settings but that doesn't belong in this thread.

---

### Post by AlanNisota on 2010-01-07
> **Bachstelze said:**
> Well, the new dshowserver using WINE seems to be a giant step backwards for me. I can't get it to work on a 64bit system (not tried on a 32bit yet). Not to mention that it adds a huge dependency.
I'm sorry you don't like it, but keeping CoreAVC working using the loader code required me doing a lot of assembly-level debugging for each release to figure out why things didn't work.  It was incredibly tedious and time consuming and I just don' have time.Using Wine, the only thing I need to maintain is the interface code which is pretty stable and should not need to be modified to support future versions of the codec.  The old code is still there and someone else is free to maintain it if they like.  It is only me working on this, and I'm still happily using CoreAVC 1..7.0 (with Wine), just as I have for the past year or so, so my incentive here is pretty low.

---

### Post by Zorael on 2010-01-08
> **AlanNisota said:**
> I'm sorry you don't like it, but keeping CoreAVC working using the loader code required me doing a lot of assembly-level debugging for each release to figure out why things didn't work.  It was incredibly tedious and time consuming and I just don' have time.Using Wine, the only thing I need to maintain is the interface code which is pretty stable and should not need to be modified to support future versions of the codec.  The old code is still there and someone else is free to maintain it if they like.  It is only me working on this, and I'm still happily using CoreAVC 1..7.0 (with Wine), just as I have for the past year or so, so my incentive here is pretty low.
I'm all appreciation over here, much <3 for the work.

---

### Post by freechelmi on 2010-01-11
Hi , sorry if it was already answered I did not  read the whole thread : 


I currently try to play 4 Mbps/720pH264 on a Sempron 2200 1,5 Ghz, No VPDAU.

XP+CoreAVC is doing a great Job, 98 % Cpu. 

Jaunty+ mplayer/dshowserver ripps818 PPA : Noticeable performance boost from FFMPEG But still unwatchable. 

In Both case I tried Framedrop option on mplayer and CoreAVC

My question is would Dshowserver/Wine generate such a big performance lost compared To native Use in XP ? 


Cheers

---

### Post by ripps818 on 2010-01-11
> **freechelmi said:**
> I currently try to play 4 Mbps/720pH264 on a Sempron 2200 1,5 Ghz, No VPDAU.

XP+CoreAVC is doing a great Job, 98 % Cpu. 

Jaunty+ mplayer/dshowserver ripps818 PPA : Noticeable performance boost from FFMPEG But still unwatchable. 

In Both case I tried Framedrop option on mplayer and CoreAVC

My question is would Dshowserver/Wine generate such a big performance lost compared To native Use in XP ?

Try using renice to change the priority of mplayer and dshowserver.exe to around -2. That should help a little.

I have a script, just run it after the video has started:
```
#! /bin/bash
## Increase niceness of dshowserver
DSHOW=`pidof dshowserver.exe`
MPLAY=`pidof mplayer`

sudo renice -2 -p $DSHOW
sudo renice -2 -p $MPLAY
sudo ionice -c 1 -p $DSHOW
sudo ionice -c 1 -p $MPLAY
```

---

### Post by freechelmi on 2010-01-12
Hi ripps818 ! and thanks for your PPA that save me a lot of time ! 

Actually , I started again by launching mplayer through smplayer ( Nice options windows where you can add conditionnal coreavc flag etc..) and the performance is really better ! 


for some reason, launching though cmdline made terminal and X consume a lot of CPU(15-20%) . Now dshowserver is at 70/80 % CPU and apart from some really complicated scene , it's watchable ! 

ok now I need to integrate this in XBMC :-)

---

### Post by ripps818 on 2010-01-12
Wanna know a neat trick?
Since the dshowserver in the ppa uses a wrapper script, you can inject additional things before or after loading the dshowserver.exe.

For example, this script will launch gksu, giving you the ability to change the priority of mplayer/dshowserver.exe/wineserver after the video has already started. It even works with mplayer gui's like smplayer and gnome-mplayer.
```
#!/bin/sh
echo 'Starting wine dshowserver.exe'
wine /usr/share/dshowserver/dshowserver.exe $* &
gksu echo sudo confirmed
DSHOW=`pidof dshowserver.exe`
MPLAY=`pidof mplayer`
WINE=`pidof wineserver`
sudo renice -2 -p $MPLAY
sudo renice -2 -p $WINE
sudo renice -2 -p $DSHOW
sudo ionice -c 1 -p $MPLAY
sudo ionice -c 1 -p $WINE
sudo ionice -c 1 -p $DSHOW

```

Just put the script in ~/bin/ or /usr/local/bin and it'll be run instead of the regular dshowserver script.

---

### Post by Zorael on 2010-01-12
I've been using a script that I run manually after having started a video. I've set up a wrapper script and a real script, where the wrapper calls the real one with sudo. Then I changed sudo to allow the real one to be run without providing a password.

Wrapper (/usr/local/bin/renicemplayer):
```
#!/bin/bash

sudo /usr/local/bin/renicemplayer.real
```
Real (/usr/local/bin/renicemplayer.real):
```
#!/bin/bash

# Divine pids
mplayer=$(pidof mplayer)
dshowserver=$(pidof dshowserver.exe)

# Display pids (and pad for readability)
echo
echo "mplayer pids: $mplayer"
echo "dshowserver pids: $dshowserver"
echo "-----------------------------------------"

# Renice
renice -n -10 $mplayer $dshowserver
ionice -c 1 -p $mplayer $dshowserver

# Pad for readability
echo
```
sudoers line (sunspire being my group):
```
%sunspire ALL=NOPASSWD: /usr/local/bin/renicemplayer.real
```

I'm not sure I'm catching all the threads with my renicing. **pidof dshowserver.exe** always only returns one process, while **htop** shows two of them, on my single-core hyperthreaded Atom cpu (ergo, two threads). Also, wineserver doesn't seem to be using any resources worth mentioning.

**--------------------------------------------------------------------------**

For instance, I'm currently playing a test clip.
**pidof** dshowserver.exe: **9061**
```
$ cat /proc/9061/cmdline
/usr/share/dshowserver/dshowserver.exe--codecCoreAVCDecoder.ax--size1280x544--guid09571a4b-f1fe-4c60-9760de6d310c7c31--fourc0x31637661--bits12--outfmt0x32315659--pid9058--idb5177780--numpages10--port54174
```
Seems real.

**htop** shows two dshowserver.exe processes: **9079, 9080**
```
$ cat /proc/9079/cmdline
/usr/share/dshowserver/dshowserver.exe--codecCoreAVCDecoder.ax--size1280x544--guid09571a4b-f1fe-4c60-9760de6d310c7c31--fourc0x31637661--bits12--outfmt0x32315659--pid9058--idb5177780--numpages10--port54174

$ cat /proc/9080/cmdline
/usr/share/dshowserver/dshowserver.exe--codecCoreAVCDecoder.ax--size1280x544--guid09571a4b-f1fe-4c60-9760de6d310c7c31--fourc0x31637661--bits12--outfmt0x32315659--pid9058--idb5177780--numpages10--port54174
```
They also seem real. But neither 9079 nor 9080 show up in **ps ux**. wat.

I think my ignorance is showing here. What am I not seeing?


**Addendum:** If you evoke a renicing script directly in the dshowserver script, you may need to add a **sleep** command to give wine a chance to start up. If I don't add it to mine, it fails to resolve a dshowserver.exe process (since it doesn't exist yet).
```
$ cat /usr/bin/dshowserver
#!/bin/sh
echo 'Starting wine dshowserver.exe'
wine /usr/share/dshowserver/dshowserver.exe $* &

# Give wine a chance to start properly
sleep 1
sudo /usr/local/bin/renicemplayer.real
```
And again, provided you've added that renicemplayer.real script to your sudoers file, this shouldn't ever ask for your password.

End result:
```
*[...]*

Playing /main/downloads/the.usual.suspects.1995.dvd5.720p.bluray.x264.sample-hv.mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC) "The Usual Suspects", -vid 0              
[mkv] Track ID 2: audio (A_DTS) "DTS 5.1", -aid 0, -alang eng                       
[mkv] Will play video track 1.                                                      
Matroska file format detected.                                                      
VIDEO:  [avc1]  1280x544  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)              
==========================================================================          
Forced video codec: coreserve                                                       
Opening video decoder: [dshowserver] DirectShowServer video codecs                  
dshowserver --codec CoreAVCDecoder.ax --size 1280x544 --guid 09571a4b-f1fe-4c60-9760de6d310c7c31 --fourc 0x31637661 --bits 12 --outfmt 0x32315659 --pid 9594 --id b5263780 --numpages 10 --port 17053 &                             
Starting wine dshowserver.exe                                                                                     

[COLOR="Green"][b]mplayer pids: 9594
dshowserver pids: 9597
-----------------------------------------
9594: old priority 0, new priority -10   
9597: old priority 0, new priority -10   [/b][/COLOR]

Opening device (port is 17053)
len: 992                      
ProductVersion: 2.0.0

*[...]*
```

---

### Post by ogooreck on 2010-01-12
> **freechelmi said:**
> Hi ripps818 ! and thanks for your PPA that save me a lot of time ! 

Actually , I started again by launching mplayer through smplayer ( Nice options windows where you can add conditionnal coreavc flag etc..) and the performance is really better ! 


for some reason, launching though cmdline made terminal and X consume a lot of CPU(15-20%) . Now dshowserver is at 70/80 % CPU and apart from some really complicated scene , it's watchable ! 

ok now I need to integrate this in XBMC :-)

It can be releated to vo driver, vf chain mplayer uses, etc. For best performance it is the best to avoid any colorspace conversions in video chain and use fastest vo for your system. You can compare mplayer output messages to find out what's going on. For me best results gives vo=gl:yuv=2:force-pbo and vo=xv takes second place. When using vo=xv i can see higher X cpu utilization, as you do.

---

### Post by BagRackRider on 2010-01-14
Hmm.. how do you run sudo without prompting for password?!
I mean since you have it in a script.

EDIT:
Nevermind, you can add something like this with visudo:
%foo    ALL = NOPASSWD: /usr/bin/ionice

That allows the group foo to sudo ionice without a password.

---

### Post by ripps818 on 2010-01-14
> **BagRackRider said:**
> Hmm.. how do you run sudo without prompting for password?!
I mean since you have it in a script.

EDIT:
Nevermind, you can add something like this with visudo:
%foo    ALL = NOPASSWD: /usr/bin/ionice

That allows the group foo to sudo ionice without a password.

Yes, but I wouldn't recommend doing that, because it gives too much power for someone who happens to get access to your computer to screw up things. Rather, you should have your sudoers point to a script that is saved in /usr/local/bin or somewhere else that only root can write to.

If you open nice/ionice to change higher priority without a password, you open up your computer to be crashed by some random joe who manages to get access and giving some random process -20 niceness. That can effectively freeze your computer.

EDIT:
Also, I've changed the source of mplayer in the ppa to now use the git mplayer-build. Mplayer should now be built to use better ffmpeg multi-threading.

---

### Post by Zorael on 2010-01-14
> **ripps818 said:**
> EDIT:
Also, I've changed the source of mplayer in the ppa to now use the git mplayer-build. Mplayer should now be built to use better ffmpeg multi-threading.
So future package updates will have ffmpeg-mt included? So far I've been downloading your sources, replacing the relevant libav* directories with ffmpeg-mt variants, including the patch and then building manually. Then they keep getting overwritten when you upload a new build, as I'm not completely sure how to change the package name (and binary names) to mplayer-mt. :3

Regardless, many thanks for the ppa, makes things much easier.

**edit:** Just installed **3:1.0~rc3+git20100108.7602d24-0ubuntu4~ripps3~karmic** and now **htop** shows multiple threads of mplayer when started with **-vc ffh264 -lavdopts threads=2**. Nice. :>

---

### Post by ripps818 on 2010-01-14
Actually, I think mplayer now uses built in ffmpeg-mt. If you look at the package, you'll notice that it doesn't depend on libavcodec anymore.

---

### Post by BagRackRider on 2010-01-14
> **ripps818 said:**
> Yes, but I wouldn't recommend doing that, because it gives too much power for someone who happens to get access to your computer to screw up things. Rather, you should have your sudoers point to a script that is saved in /usr/local/bin or somewhere else that only root can write to.

If you open nice/ionice to change higher priority without a password, you open up your computer to be crashed by some random joe who manages to get access and giving some random process -20 niceness. That can effectively freeze your computer.

Yeah, I know it's a risk but I think its a small one in this case. It's a personal server with few active accounts and worst case scenario is that someone figures out that ionice is open for "hacking" and then crashes the machine. Not to mention that if someone get access to the machine, this person must hack an account whose group is accepted to run ionice.

---

### Post by tpettit on 2010-01-17
I didn't get very far. I'm on a 32bit machine, running Ubuntu 9.10 Karmic Koala, and this line:
```
wget -qO - "http://pastebin.com/pastebin.php?dl=f7ca459d" | patch -p0
```

...returns this:
```
(Stripping trailing CRs from patch.)
patching file loader/dshow/DS_VideoDecoder.c
Hunk #1 FAILED at 97.
1 out of 1 hunk FAILED -- saving rejects to file loader/dshow/DS_VideoDecoder.c.rej
```

Here are the contents of the rej file using cat:
```
***************
*** 97,103 ****
        
  }
  #define is_avc(cc) (cc == mmioFOURCC('A', 'V', 'C', '1') || \
-                     cc == mmioFOURCC('a', 'v', 'c', '1'))
  char *ConvertVIHtoMPEG2VI(VIDEOINFOHEADER *vih, int *size)
  {
      struct VIDEOINFOHEADER2 {
--- 97,106 ----
        
  }
  #define is_avc(cc) (cc == mmioFOURCC('A', 'V', 'C', '1') || \
+                     cc == mmioFOURCC('a', 'v', 'c', '1') || \
+                     cc == mmioFOURCC('H', '2', '6', '4') || \
+                     cc == mmioFOURCC('h', '2', '6', '4'))
+                     
  char *ConvertVIHtoMPEG2VI(VIDEOINFOHEADER *vih, int *size)
  {
      struct VIDEOINFOHEADER2 {
```

I'm sort of new to Linux so I have no clue where to even start in order to fix this... Any help would be greatly appreciated. Thanks.

---

### Post by Master One on 2010-01-17
To be honest, I completely lost the oversight. Can someone post a summary of how to get mplayer-mt + CoreAVC 2.0.0 up and running (with the available patches and which of these are really needed)?

---

### Post by Zorael on 2010-01-17
If you really want to just "get it running", use ripps818's ppa.

If you still want to compile it yourself, perhaps to change a setting or apply a separate patch, just grab the *source* from ripps818's ppa and use checkinstall or dpkg-buildpackage to make sure it applies the patches in debian/patches.

If you want a fresher mplayer than what's available in his ppa (last update 13 hours ago), you may be able to copy the newer source into a directory containing the ppa source, making sure to not overwrite the debian directory. That way you'll be overwriting the mplayer bits while keeping the patches etc as they are.

That said, the coreavc-for-linux patch has been recently updated (by AlanNisota in this thread), so I'm not sure it needs wget/patching anymore as detailed on the first page.

---

### Post by BagRackRider on 2010-01-19
> **Zorael said:**
> That said, the coreavc-for-linux patch has been recently updated (by AlanNisota in this thread), so I'm not sure it needs wget/patching anymore as detailed on the first page.

The first page here is outdated.

---

### Post by Jason4108 on 2010-01-20
Does ripps818 mplayer-build package have ssa/*** subtitle support enabled?
Thanks

---

### Post by ripps818 on 2010-01-20
> **Jason4108 said:**
> Does ripps818 mplayer-build package have ssa/*** subtitle support enabled?
Thanks
Yes, if I have SSA/*** support enabled.

---

### Post by Jason4108 on 2010-01-20
> **ripps818 said:**
> Yes, if I have SSA/*** support enabled.

hey ripps I'm on hardy amd64 and when I try to install mencoder and mplayer from your repos I get:

  mencoder: Depends: libopencore-amrnb0 (>= 0.1.1) but it is not installable
            Depends: libopencore-amrwb0 (>= 0.1.1) but it is not installable
  mplayer: Depends: libopencore-amrnb0 (>= 0.1.1) but it is not installable
           Depends: libopencore-amrwb0 (>= 0.1.1) but it is not installable

I've been looking for the packages but I'm having trouble finding them, do you have an advice?

---

### Post by ripps818 on 2010-01-20
> **Jason4108 said:**
> hey ripps I'm on hardy amd64 and when I try to install mencoder and mplayer from your repos I get:

  mencoder: Depends: libopencore-amrnb0 (>= 0.1.1) but it is not installable
            Depends: libopencore-amrwb0 (>= 0.1.1) but it is not installable
  mplayer: Depends: libopencore-amrnb0 (>= 0.1.1) but it is not installable
           Depends: libopencore-amrwb0 (>= 0.1.1) but it is not installable

I've been looking for the packages but I'm having trouble finding them, do you have an advice?

Sorry, I forgot to move some backports from rvm's ppa into mine. I'll do that now.

---

### Post by Jason4108 on 2010-01-21
> **ripps818 said:**
> Sorry, I forgot to move some backports from rvm's ppa into mine. I'll do that now.

hmm for some reason when I use your packages I can't get ssa/*** subs to work. When using rvm's they work fine but coreavc doesn't work with those. I tried downloading your source packages to compile and when I do ./configure it says SSA/*** ... No

---

### Post by Zorael on 2010-01-21
ripps818, do you think you could add a clause to whatever script you're using to make it add the git revision and/or date to the version string?
```
$ mplayer | grep Team            # yours
MPlayer UNKNOWN-4.4.1 (C) 2000-2009 MPlayer Team

$ mplayer-alt | grep Team        # old compiled version
MPlayer SVN-r30166-4.4.1 (C) 2000-2009 MPlayer Team
```
Just a tought.

---

### Post by ripps818 on 2010-01-21
> **Jason4108 said:**
> hmm for some reason when I use your packages I can't get ssa/*** subs to work. When using rvm's they work fine but coreavc doesn't work with those. I tried downloading your source packages to compile and when I do ./configure it says SSA/*** ... No
Well, SSA/*** support is automatically enabled based on what development package it detects as being installed. I've been having trouble getting hardy amd64 to build on the ppa, but after checking the buildlogs, the last succesful build of mplayer-amd64-hardy did have SSA/*** enabled.

[https://edge.launchpad.net/~ripps818/+archive/coreavc/+files/mplayer_1.0~rc3+git20100116.180c7ca-0ubuntu2~ripps1~hardy_amd64.deb](https://edge.launchpad.net/~ripps818/+archive/coreavc/+files/mplayer_1.0~rc3+git20100116.180c7ca-0ubuntu2~ripps1~hardy_amd64.deb)

---

### Post by kub-fu on 2010-01-22
Hey Ripps, thanks a lot for your packages.

I'm running Karmic x64, and I first tried the guide on the first page, but I had the issue with CoreAVC 2.0, so I kept reading and found your repo.

Unfortunately, mplayer says:

```
Requested video codec family [coreserve] (vfm=dshowserver) not available.
Enable it at compilation.
```

I'm using both mplayer and dshowserver from your repository. Also, this is dshowservers output (same command as the guide):

**Edit:** Ok, so I got further by installing CoreAVC using wine instead of CrossOver, dumb me... Still, although dshowserver now works properly, mplayer keeps showing the same message above, and no video.

I have CoreAVCDecoder.ax in /usr/share/dshowserver

A hand please?

Thanks in advance!

---

### Post by ripps818 on 2010-01-22
> **kub-fu said:**
> 
```
Requested video codec family [coreserve] (vfm=dshowserver) not available.
Enable it at compilation.
```

Okay, first of all, it's vc= not vfm=. Dshowserver is not part of a codec family, at least not yet.

> 
```
Starting wine dshowserver.exe
err:menubuilder:WinMain unknown option -a
err:menubuilder:WinMain unknown option -r
No id specified, assuming test mode
Opening device (port is 0)
Warning: DS_Filter() could not open DirectShow DLL.  (DLL=CoreAVCDecoder.ax)
Failed to create DirectShow filter
Failed to open win32 codec CoreAVCDecoder.ax

```
I have CoreAVCDecoder.ax in /usr/share/dshowserver

You have the codec in the right place, but did you install it correctly in wine? The new dshowserver relies on the wine configuration for settings and registry, you can't just fake it like you did with the old dshowserver anymore.

---

### Post by kub-fu on 2010-01-23
Thanks for your reply. I didn't change anything in what I pasted, that's how mplayer shows it (and I did use the -vc flag not -vfm).

I did install it under wine, with my serial, and dshowserver does show "Initialization is complete", so I'm guessing it's installed correctly?

Other thoughts?

---

### Post by ripps818 on 2010-01-23
> **kub-fu said:**
> Thanks for your reply. I didn't change anything in what I pasted, that's how mplayer shows it (and I did use the -vc flag not -vfm).

I did install it under wine, with my serial, and dshowserver does show "Initialization is complete", so I'm guessing it's installed correctly?

Other thoughts?
Hmm....
This might be reaching, but do you have a custom codecs.conf in your .mplayer/ directory? Dshowserver doesn't need a custom codecs.conf for my mplayer build.

If that doesn't help, I'd file a bug on the coreavc-for-linux google project page. I'm not sure what else to do.

**UPDATE**:
Hold the phones, I've been looking closer at my buildlogs and it seems that with my latest mplayer release, amd64 packages older than lucid haven't been compiling the vd_dshowserver.c file. I don't understand why that's happening, and only with amd64. I'll have to consult some developers.

**UPDATE2**:
It seem that a series of win32 files aren't being compiled on amd64. I'm still investigating the cause.

**UPDATE3**:
Okay, I've edited my dshowserver patches to not be dependent on win32dll being enabled in the config. This should hopefully allow it to compile on x64 arches. *crosses fingers*

---

### Post by kub-fu on 2010-01-23
I do have the codecs.conf file, and I did try removing it, but the same error appears.

I eagerly wait for your updated packages, thanks a lot!

---

### Post by Zorael on 2010-01-27
Hmm, any idea what could be causing this?
```
$ mplayer out.ogv
MPlayer UNKNOWN-4.4.1 (C) 2000-2009 MPlayer Team

Playing out.ogv.
Ogg stream 0 is of an unknown type
[Ogg] stream 1: video (Theora v3.2.1), -vid 0
Ogg file format detected.
VIDEO:  [theo]  672x352  24bpp  10.000 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Forced video codec: coreserve
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[theora @ 0x88216c0]Missing extradata!


MPlayer interrupted by signal 11 in module: init_video_codec
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
```

To reproduce, try recording a screencast of a few seconds with **recordmydesktop** and then playing it with mplayer.
```
$ recordmydesktop --no-audio
$ mplayer out.ogv
```

---

### Post by ripps818 on 2010-01-28
> **Zorael said:**
> Hmm, any idea what could be causing this?
```
$ mplayer out.ogv
MPlayer UNKNOWN-4.4.1 (C) 2000-2009 MPlayer Team

Playing out.ogv.
Ogg stream 0 is of an unknown type
[Ogg] stream 1: video (Theora v3.2.1), -vid 0
Ogg file format detected.
VIDEO:  [theo]  672x352  24bpp  10.000 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Forced video codec: coreserve
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[theora @ 0x88216c0]Missing extradata!


MPlayer interrupted by signal 11 in module: init_video_codec
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
```

To reproduce, try recording a screencast of a few seconds with **recordmydesktop** and then playing it with mplayer.
```
$ recordmydesktop --no-audio
$ mplayer out.ogv
```

Well, I've managed to reproduce this. Using normal mplayer works, but if I add `-lavdopts threads=2`, than mplayer crashes. So I'm guessing that libtheora isn't multithreaded. I'll look into this, but I'm not sure what else to do.

---

### Post by ogooreck on 2010-01-29
Maybe just use -vc theora, ?

---

### Post by Zorael on 2010-01-29
> **ripps818 said:**
> Well, I've managed to reproduce this. Using normal mplayer works, but if I add `-lavdopts threads=2`, than mplayer crashes. So I'm guessing that libtheora isn't multithreaded. I'll look into this, but I'm not sure what else to do.
> **ogooreck said:**
> Maybe just use -vc theora, ?
Both limiting it to one thread and specifying -vc theora worked. I modified my ~/.mplayer/config file to prefer theora over coreserve, and now mplayer opens the file nicely without giving extra arguments.
```
ao=alsa,
lavdopts=fast=1:threads=3
vc=**theora,**coreserve,
nolirc=1
```
Thanks for the help.

---

### Post by coolme on 2010-02-01
> **ogooreck said:**
> 

```
#!/bin/sh

DSHOWSERVEREXE="c:\\Program Files\\CoreCodec\\CoreAVC Professional Edition\\dshowserver.exe"
wine "${DSHOWSERVEREXE}" "$@"
# if you wish to run dshowserver with elevated priority comment out line above and uncomment line below
# nice -n -5 wine "${DSHOWSERVEREXE}" "$@"

```
I had to make an account and say Thank You!. Have been messing around with this for some time and nothing i did worked it was driveing me insane. Tried the code and walla!! it works, THank you. Also Thank you Alan for coreavc-for-linux

---

### Post by ripps818 on 2010-02-04
Hmm...
I was about to make a post about how a properly tweaked mplayer using only ffmpeg-mt was just as fast (if not faster) than coreavc, but with the latest dshowserver patches for mplayer, It seems that coreavc wins over ffmpeg once again, ever so slightly.

I've already upload the mplayer/dshowserver with patches to the coreavc-for-ubuntu ppa already.

---

### Post by BagRackRider on 2010-02-04
Feel free to post the mplayer-mt guide (unless it's just goes through on how to add ffmpeg-mt support, because there are guides for that already).

Currently, since I switched to a P4 CPU with Hyperthreading, mplayer-mt actually does a better job than coreavc, CoreAVC seem to bug here with HT enabled... stutters madly.

---

### Post by supadid on 2010-02-27
I used rips818 PPA to download the packages (after failing first with compiling my own) and initially it didn't work due to the following message:

```
wine: cannot find '/usr/local/bin/dshowserver.exe.so'
```

I fixed this with the following:

```
sudo cp /usr/share/dshowserver/dshowserver.exe /usr/local/bin/dshowserver.exe.so

```

HD playback is now very smooth! This really is the Achilles heel in Ubuntu and Linux distributions in general at the moment I feel, playback on HD content is far too difficult for the average user to get working.

Anyway, I hope my fix above helps somebody out. :D and thanks to the OP and rips818 for his fine packages. :D

---

### Post by ripps818 on 2010-02-27
> **supadid said:**
> I used rips818 PPA to download the packages (after failing first with compiling my own) and initially it didn't work due to the following message:

```
wine: cannot find '/usr/local/bin/dshowserver.exe.so'
```

I fixed this with the following:

```
sudo cp /usr/share/dshowserver/dshowserver.exe /usr/local/bin/dshowserver.exe.so

```

HD playback is now very smooth! This really is the Achilles heel in Ubuntu and Linux distributions in general at the moment I feel, playback on HD content is far too difficult for the average user to get working.

Anyway, I hope my fix above helps somebody out. :D and thanks to the OP and rips818 for his fine packages. :D

Thanks, I try my best to make coreavc as easy as possible.

Btw, the reason you were having trouble is because you were using wine-gcc to compile dshowserver instead of mingw32. Technically, the wine-gcc should work, but I find it gives too much trouble.

---

### Post by supadid on 2010-02-27
A-ha! Thanks.

The weird thing now is, I can't seem to get CoreAVC running with smplayer, it always seems to choose ffmpeg.

When i select the coreserve codec in the video properties it only plays the audio and seems to lock up a bit, any ideas?

---

### Post by ripps818 on 2010-02-27
> **supadid said:**
> A-ha! Thanks.

The weird thing now is, I can't seem to get CoreAVC running with smplayer, it always seems to choose ffmpeg.

When i select the coreserve codec in the video properties it only plays the audio and seems to lock up a bit, any ideas?

Every once in a while, it seems that dshowserver.exe doesn't close properly. Just enter in a terminal `killall dshowserver.exe` and that should fix it.

Also, I have another idea why coreserve might be looking for a dshowserver.exe.so in /usr/local, do you have a script installed to /usr/local/bin/dshowserver?
If you installed a file there during your earlier experimenting, it will interfere with the /usr/bin/dshowserver script I install in my package.

---

### Post by supadid on 2010-02-27
Hmm, no sign of dshowserver.exe in the running processes and no sign of dshowserver.exe.so in /usr/local either.

Odd.

---

### Post by supadid on 2010-02-27
Ignore that. 

There was a dshowserver.exe.so in the /usr/local/bin and i moved it to dshowserver.exe.so.moved but smplayer still seems the same :(

---

### Post by tito_torrisi on 2010-02-27
I'm using the mplayer build from CoreAVC-for-Ubuntu ppa with SMPlayer on an Atom 330 dual core CPU.
Do I have to add the command "lavdopts=threads=2" to the advanced options for mplayer section in order to work?
And what about the in "threads for decoding" the performance tab of SMPlayer options, do I have to set it to 2 cores as well? Or JUST that?

Are there any other necessary tweaks to get the best performance? (eg. video or audio output driver)

---

### Post by blablu on 2010-03-04
Hi all,

I followed [ripps818 guide]("https://launchpad.net/~ripps818/+archive/coreavc") to the letter, the only difference being my CoreAVCDecoder.ax was in a slightly different path inside wine's folder.

Now whenever I try 
```
mplayer -vc coreserve someHDfile.mkv
```

I get only sound  (like so many people in the previews posts back in 2009  I see)

> Cannot find codec matching selected -vo and video format...

I have no codecs.conf in Ubuntu 9.10.

How can I force mplayer to use coreavc? 

Thank you for your time!

---

### Post by ripps818 on 2010-03-04
> **blablu said:**
> Hi all,
I followed [ripps818 guide]("https://launchpad.net/~ripps818/+archive/coreavc") to the letter, the only difference being my CoreAVCDecoder.ax was in a slightly different path inside wine's folder.
Now whenever I try 
```
mplayer -vc coreserve someHDfile.mkv
```
I get only sound  (like so many people in the previews posts back in 2009  I see)
I have no codecs.conf in Ubuntu 9.10.
How can I force mplayer to use coreavc? 
Thank you for your time!

Are you sure that you're playing an h.264 video? Coreavc can only play AVC/h.264 files, and not all HD videos are encoded in that. Have you tried using `-vc coreserve,` (notice the comma at the end) so that it will fallback to another codec if coreavc can't play it.

Also, I've become aware that some certain stream rips have been encoded with FLV4 and mplayer doesn't know what to do with them, using `-vc +ffvp6f` will force them to playback using the proper codec.

---

### Post by blablu on 2010-03-04
The video I tried is an AVC file.

this is exactly what I did:
1) installed coreavc with wine
2) added your ppa, installed dshowserver and updated mplayer to your version.
3) copied CoreAVCDecoder.ax to /usr/share/dshowserver
4) tried: mplayer -vc coreserve Video[720p][AVC-FLAC].mkv 

did I miss something? 

thank you very much for your reply!

---

### Post by ripps818 on 2010-03-04
> **blablu said:**
> The video I tried is an AVC file.

this is exactly what I did:
1) installed coreavc with wine
2) added your ppa, installed dshowserver and updated mplayer to your version.
3) copied CoreAVCDecoder.ax to /usr/share/dshowserver
4) tried: mplayer -vc coreserve Video[720p][AVC-FLAC].mkv 

did I miss something? 

thank you very much for your reply!
Nope, that's how it's suppose to go. Does coreserve work on other HD videos? I'm just trying to figure out whether it's the video or the your installation.

Btw, give me the entire output mplayer gives, there might be something I'm missing. Try using the -identify flag.

---

### Post by blablu on 2010-03-04
I've tried with many videos. Same thing:

> MPlayer SVN-r29748-4.4.1 (C) 2000-2009 MPlayer Team

Playing some_anime_[720p,BluRay,x264,DTS-ES].mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_DTS), -aid 0, -alang jpn
[mkv] Track ID 3: subtitles (S_TEXT/***) "***", -sid 0, -slang eng
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1280x720  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Forced video codec: coreserve
Cannot find codec matching selected -vo and video format 0x31637661.
==========================================================================
==========================================================================
Requested audio codec family [dts] (afm=libdca) not available.
Enable it at compilation.
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 1536.0 kbit/100.00% (ratio: 192000->192000)
Selected audio codec: [ffdca] afm: ffmpeg (FFmpeg DTS)
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...


Although I should mention that even whithout coreavc, your mplayer build greatly improved video playback in my machine. Thanks.

---

### Post by ripps818 on 2010-03-04
Okay, I think I know what's going on, your not using my patched mplayer packages. Let me guess, you upgraded your mplayer-nogui package. Upstream doesn't support the gmplayer gui anymore, so I renamed the nogui package to just plain mplayer. I thought I fixed this...

Okay, first uninstall mplayer-nogui:
```
sudo apt-get remove mplayer-nogui
```

Then reinstall normal mplayer from my ppa:
```
sudo apt-get install mplayer
```

And just to be sure, make sure that your mplayer version is correct run:
```
apt-cache policy mplayer
```
The installed version should something like: 3:1.0~rc3+git20100226.e28cf6c-0ubuntu1


This is probably my fault, your probably seeing remnants some old packages that used to populate the ppa. I had them all deleted, but I guess it didn't take.
I should probably create a dummy package so that mplayer-nogui will force the installation of my mplayer package.

---

### Post by blablu on 2010-03-04
removing mplayer-nogui made no difference.:cry:

mplayer version is 3:1.0~rc3+git20100226.e28cf6c-0ubuntu1~ripps1~karmic

hd playback it's not a big deal for me though. I'm just curious.

Thanks for your time.:D

---

### Post by ripps818 on 2010-03-04
hmm.... weird. The reason I said you were using an older version was because your mplayer copyright string said:
```
MPlayer SVN-r29748-4.4.1 (C) 2000-2009 MPlayer Team
```
Which isn't right, because that's the version used by ubuntu.
The version in the ppa should be something similar to this:
```
MPlayer UNKNOWN-4.4.3 (C) 2000-2010 MPlayer Team
```

Maybe you should check your system to see if you have any old binaries of mplayer in your /usr/local/bin or ~/bin that is taking precedence over the one installed by the ppa.

---

### Post by blablu on 2010-03-04
> **ripps818 said:**
> 
Maybe you should check your system to see if you have any old binaries of mplayer in your /usr/local/bin or ~/bin that is taking precedence over the one installed by the ppa.

wow man, that was it!

works like a charm...

thanks a million!:D:D:D

---

### Post by wiz_master49 on 2010-03-10
Sorry to ask such a dumb question but I just reformatted my laptop to Ubuntu and am looking to play some videos. I have mplayer installed and have installed coreavc using wine but I have no idea what to do other than that. I've read like 15 pages in this thread and my head is spinning lol so if someone could please simplify what I have to do exactly? I have the mplayer and dshowserver from [https://launchpad.net/~ripps818/+archive/coreavc](https://launchpad.net/~ripps818/+archive/coreavc) version 3.1.

Any help i appreciated. Thanks:D

---

### Post by ripps818 on 2010-03-10
> **wiz_master49 said:**
> Sorry to ask such a dumb question but I just reformatted my laptop to Ubuntu and am looking to play some videos. I have mplayer installed and have installed coreavc using wine but I have no idea what to do other than that. I've read like 15 pages in this thread and my head is spinning lol so if someone could please simplify what I have to do exactly? I have the mplayer from [https://launchpad.net/~ripps818/+archive/coreavc](https://launchpad.net/~ripps818/+archive/coreavc) version 3.1.

Any help i appreciated. Thanks:D

Easiest possible method, just ignore the previous 37 pages on this thread and just follow the directions in ppa's description.
The majority of this thread was to help people compile their own mplayer and dshowserver binaries. If your using the PPA, you don't need to worry about all of that.

---

### Post by wiz_master49 on 2010-03-10
> **ripps818 said:**
> Easiest possible method, just ignore the previous 37 pages on this thread and just follow the directions in ppa's description.
The majority of this thread was to help people compile their own mplayer and dshowserver binaries. If your using the PPA, you don't need to worry about all of that.

Alright, I got it working perfectly thank you. Just one more question, is their some way I can set mplayer to try to use coreavc if possible without having to play videos from the terminal?

---

### Post by ripps818 on 2010-03-10
> **wiz_master49 said:**
> Alright, I got it working perfectly thank you. Just one more question, is their some way I can set mplayer to try to use coreavc if possible without having to play videos from the terminal?
Yes, you just need to add an option to your ~/.mplayer/config. Below [Default] add:
vc=coreserve,

(remember to add the comma at the end, that will tell mplayer to fallback to another codec if coreavc fails)

---

### Post by wiz_master49 on 2010-03-10
> **ripps818 said:**
> Yes, you just need to add an option to your ~/.mplayer/config. Below [Default] add:
vc=coreserve,

(remember to add the comma at the end, that will tell mplayer to fallback to another codec if coreavc fails)
Below vo=xv,  or below vc=ffmpeg12, ?

Thanks for the help.

---

### Post by ripps818 on 2010-03-10
> **wiz_master49 said:**
> Below vo=xv,  or below vc=ffmpeg12, ?

Thanks for the help.
I'd replace the `vc=ffmpeg12,`.

---

### Post by joris1977 on 2010-03-11
Wow cool thanks for this thread, the ppa and the mulitthreaded playback. Really easy to set up and now I can just watch HD videos on my netbook; Atom N270 @ 1.60GH 

The atom is under heavy load but it works! 

:popcorn: 

btw SMplayer makes a real nice front end for mplayer

---

### Post by duchai on 2010-03-13
Installing CoreAVC 2.0 and DShowServer r114 works for me but whenever I run the own compiled mplayer svn r30883 with vc coreserve I get no video/black screen. I can only hear the audio. 

Mplayer from ripps818's ppa works fine though
 
but I need to install libggi-target-x{u} libggi2{u} libgii1{u} libgii1-target-x{u} liblircclient0{u} liblzo2-2{u} libsvga1{u}

The compiled mplayer from svn does not need any other libs. Is that the reason why I get no video?

---

### Post by dadou on 2010-04-10
> **ripps818 said:**
> Easiest possible method, just ignore the previous 37 pages on this thread and just follow the directions in ppa's description.
The majority of this thread was to help people compile their own mplayer and dshowserver binaries. If your using the PPA, you don't need to worry about all of that.
Hi ripps, 

I've done everything yoiu said and I can actually use the CoreAVC codec with MPlayer. As I can see, when I load a BluRay Rip of 4.8Gios @1080p, it's not laggy, at least far less than VideoLAN is so thanks for that. 
Though, I got two questions, first of all, how do I get back a GUI with MPlayer. Since your version is now the one installed through synaptic I don't have a GUI and Im forced to launch vids with the command line. Then, I would like to know if it is normal for my configuration to still have some lags playing HD contents since I got a Lenovo W500, VideoLAN should run those vids flawlessly and using a trick like this one to play it is a bit awkward (and it's not even running full load while playing with VideoLAN, Im puzzled why its laggy). 
By the way, thanks again for your effort.

---

### Post by ripps818 on 2010-04-10
Hey dadou, 
mplayer used to compile with an internal frontend called gmplayer, but that has been discontinued upstream. However, the mplayer I package should work out of the box with the myriad of other guis that are made to use mplayer. SMplayer and Gnome-Mplayer are probably the most popular.

I don't know why vlc isn't able to decode h.246 as well, but I'd wager a guess that it's because coreavc and the provided mplayer are compiled to provide much more efficient multithreaded playback. Vlc might playback better if you increase the number of threads it uses.

---

### Post by dadou on 2010-04-10
Thanks for the quick answer ;) 
> **ripps818 said:**
> Hey dadou, 
mplayer used to compile with an internal frontend called gmplayer, but that has been discontinued upstream. However, the mplayer I package should work out of the box with the myriad of other guis that are made to use mplayer. SMplayer and Gnome-Mplayer are probably the most popular.
Ok, I was just asking because previously to that upgrade to your version, MPlayer has his own GUI and was shown in the applications menu. Anyway, Im gonna install a GUI and everything would be alright. By the way, Gnome MPlayer is the same as MPlayer? Because it's laggy as it have always been, kinda like it has not been upgraded as well as the command line MPlayer. Maybe I just should reinstall it. 
(Yeah I just played the 1080p vid right now with gnome-mplayer and mplayer both in command line, totally not the same, weird uh?)
> **ripps818 said:**
> I don't know why vlc isn't able to decode h.246 as well, but I'd wager a guess that it's because coreavc and the provided mplayer are compiled to provide much more efficient multithreaded playback. Vlc might playback better if you increase the number of threads it uses.

Ok, you're maybe right about the multithreaded issue. It's bummer a machine like this suffer a laggy playback, I don't think VideoLAN was laggy running Windows. Tho it's too messy to run Windows. Let's keep it simple with MPlayer :D

---

### Post by ripps818 on 2010-04-10
> **dadou said:**
> 
Ok, I was just asking because previously to that upgrade to your version, MPlayer has his own GUI and was shown in the applications menu. Anyway, Im gonna install a GUI and everything would be alright. By the way, Gnome MPlayer is the same as MPlayer? Because it's laggy as it have always been, kinda like it has not been upgraded as well as the command line MPlayer. Maybe I just should reinstall it.

Both gnome-mplayer and smplayer are just front-ends for mplayer, there isn't too much reason there should be a performance difference between the two. You might need to play around with some of the options and Video Output. Mplayer isn't multithreaded by default, you need to tell how many threads to make by using `-lavdopts threads=n` (where n is the number of threads/cores your cpu can use). Gnome-mplayer has a place in Preferences to specify custom options. Although, if your using `-vc coreserve,` than coreavc should determine how many threads it needs to make.

Many people prefer to use smplayer in Ubuntu (even though it's designed for kde/qt) because it has a lot of robust configuration options and has support for CoreAVC by just clicking a checkbox. Although, I find it uses a few too many video filters that can reduce performance if your on a particularly slower cpu.

---

### Post by dadou on 2010-04-20
> **ripps818 said:**
> Both gnome-mplayer and smplayer are just front-ends for mplayer, there isn't too much reason there should be a performance difference between the two. You might need to play around with some of the options and Video Output. Mplayer isn't multithreaded by default, you need to tell how many threads to make by using `-lavdopts threads=n` (where n is the number of threads/cores your cpu can use). Gnome-mplayer has a place in Preferences to specify custom options. Although, if your using `-vc coreserve,` than coreavc should determine how many threads it needs to make.

Many people prefer to use smplayer in Ubuntu (even though it's designed for kde/qt) because it has a lot of robust configuration options and has support for CoreAVC by just clicking a checkbox. Although, I find it uses a few too many video filters that can reduce performance if your on a particularly slower cpu.

Hi ripps, 

Ok, I've played around with mplayer and different of its front ends those last days. As you said, gnome-mplayer and smplayer are just front ends and are giving same results, dunno why I got a laggy gnome-mplayer at this time. Anyway, now I can play HD playback flawlessly (gotta turn off pretty much every others apps in background for 1080p :D ) thanks to the coreserve codec. I hope a free one will pop up soon though. 
I switched to ext4 too, can't do any bad either... 
And by the way, I noticed the VC-1 support is not perfect as well as the dvd navigation with an iso file. 
Thanks again for your work!

---

### Post by t.alex on 2010-04-20
ripps818,

could you please tell me, what mplayer repository you use for your builds ([https://launchpad.net/~ripps818/+archive/coreavc)?](https://launchpad.net/~ripps818/+archive/coreavc)?) it's the git version from Uoti Urpala, right?

a while i thought it's that one here:
[http://repo.or.cz/w/mplayer.git/shortlog](http://repo.or.cz/w/mplayer.git/shortlog)
but according to the git tags it doesn't seem to be so.

---

### Post by ripps818 on 2010-04-26
> **t.alex said:**
> ripps818,

could you please tell me, what mplayer repository you use for your builds ([https://launchpad.net/~ripps818/+archive/coreavc)?](https://launchpad.net/~ripps818/+archive/coreavc)?) it's the git version from Uoti Urpala, right?

a while i thought it's that one here:
[http://repo.or.cz/w/mplayer.git/shortlog](http://repo.or.cz/w/mplayer.git/shortlog)
but according to the git tags it doesn't seem to be so.

Sorry It took me soo long to reply, the repository I use is called mplayer-build, I think it uses the repository you specified as a submodule. My package uses that mplayer with ffmpeg-mt included internally as another submodule.

---

### Post by djerom on 2010-04-30
Hi,

I installed yesterday the new release of Ubuntu (Lucid), then installed wine1.1.42-0ubuntu4, and your built packages of mplayer and dshowserver.

Testing the codec *CoreAVCDecoder.ax *in  /usr/share/dshowserver with your binary dshowserver returned an error :

[I]dshowserver -c CoreAVCDecoder.ax
Starting wine dshowserver.exe
No id specified, assuming test mode
Using default width  for CoreAVCDecoder.ax: 1280
Using default height for CoreAVCDecoder.ax: 720
Using default fourcc for CoreAVCDecoder.ax: 0x34363248
Using default outfmt for CoreAVCDecoder.ax: 0x30323449
Using default outbit for CoreAVCDecoder.ax: 12
Using default GUID   for CoreAVCDecoder.ax: 09571a4b-f1fe-4c60-9760de6d310c7c31
Opening device (port is 0)
Warning: DS_Filter() could not open DirectShow DLL.  (DLL=CoreAVCDecoder.ax)
Failed to create DirectShow filter
Failed to open win32 codec CoreAVCDecoder.ax[/I]

Could it be because of the Wine version ?

Thanks for all your investment.

---

### Post by ripps818 on 2010-04-30
> **djerom said:**
> Hi,

I installed yesterday the new release of Ubuntu (Lucid), then installed wine1.1.42-0ubuntu4, and your built packages of mplayer and dshowserver.

Testing the codec *CoreAVCDecoder.ax *in  /usr/share/dshowserver with your binary dshowserver returned an error :

[I]dshowserver -c CoreAVCDecoder.ax
Starting wine dshowserver.exe
No id specified, assuming test mode
Using default width  for CoreAVCDecoder.ax: 1280
Using default height for CoreAVCDecoder.ax: 720
Using default fourcc for CoreAVCDecoder.ax: 0x34363248
Using default outfmt for CoreAVCDecoder.ax: 0x30323449
Using default outbit for CoreAVCDecoder.ax: 12
Using default GUID   for CoreAVCDecoder.ax: 09571a4b-f1fe-4c60-9760de6d310c7c31
Opening device (port is 0)
Warning: DS_Filter() could not open DirectShow DLL.  (DLL=CoreAVCDecoder.ax)
Failed to create DirectShow filter
Failed to open win32 codec CoreAVCDecoder.ax[/I]

Could it be because of the Wine version ?

Thanks for all your investment.

Hmm... do you have any leftover scripts from previous coreavc attempts. The default script generated by coreavc-for-linux doesn't work with the setup I use with my dshowserver package. Check your /usr/local/bin and $HOME/bin directories to see if a different script is being run instead of the one installed in /usr/bin.

---

### Post by m45t3r on 2010-05-01
Well, rips818, you rocks:guitar:. I was trying to compile a MPlayer with CoreAVC support using the  instructions from the CoreAVC-for-Linux homepage, but it didn't work. Your PPA works like a charm for me (using a fresh install of Ubuntu 10.4, CoreAVC 2.0).

---

### Post by djerom on 2010-05-01
> **ripps818 said:**
> Hmm... do you have any leftover scripts from previous coreavc attempts. The default script generated by coreavc-for-linux doesn't work with the setup I use with my dshowserver package. Check your /usr/local/bin and $HOME/bin directories to see if a different script is being run instead of the one installed in /usr/bin.

Hello,

I was using a codec built from a Windows XP installation. Installing the codec with Wine finally worked great ! No more issue.

MPlayer and this codec rocks !

---

### Post by ripps818 on 2010-05-01
> **djerom said:**
> Hello,

I was using a codec built from a Windows XP installation. Installing the codec with Wine finally worked great ! No more issue.

MPlayer and this codec rocks !

Ah, yes. You can't just copy the codec, you have to actually install it. CoreAVC relies on user data stored in the wine windows registry to operate.

---

### Post by baleks on 2010-05-12
> **m45t3r said:**
> Well, rips818, you rocks:guitar:. I was trying to compile a MPlayer with CoreAVC support using the  instructions from the CoreAVC-for-Linux homepage, but it didn't work. Your PPA works like a charm for me (using a fresh install of Ubuntu 10.4, CoreAVC 2.0).

+1, thank you very much!!!

---

### Post by djerom on 2010-05-16
Hi rips818,

could your packages be considered as "Debian compatible packages" or are they specific to Ubuntu ? I'm asking it because I search Debian packages for installing them on a linux distribution based on Debian.

Many thanks.

---

### Post by djerom on 2010-05-16
> **djerom said:**
> Hi rips818,

could your packages be considered as "Debian compatible packages" or are they specific to Ubuntu ? I'm asking it because I search Debian packages for installing them on a linux distribution based on Debian.

Many thanks.

I guess viewing package details on your Launchpad project "CoreAVC-for-Ubuntu" gave me the answer : some .deb files are present.

---

### Post by qtzlctl on 2010-05-17
uh, I'm failing on step 1: installing CoreAVC with Wine. I've got Wine 1.1.42 (from the software center) and the installer (CoreAVC 2.0 Professional Edition.exe). It shows the installer pop-up, goes silent for 60 seconds then throws a "This application encountered a serious problem and needs to close".

Do I need to install anything to get CoreAVC to install?

*edit

Workaround for anyone who can't get past the installer pop-up:
1. Open a terminal window
2. Type "wine /installer location/"
3. When you see "err:ntdll:RtlpWaitForCriticalSection section 0x7bca27e4 "loader.c: loader_section" wait timed out in thread 001c, blocked by 0009, retrying (60 sec)" wait about 4 seconds and type CTRL+C.
4. You can now continue with the installation.

---

### Post by joris1977 on 2010-05-25
Sorry if this is off topic;

But after the success story with CoreAVC and my atom based netbook without an advanced graphic card, I was wondering if it would make sense to use CoreAVC on my desktop. On my desktop I now use Vdpau and mplayer with an Nvidia card. Works pretty well on very low cpu. Is there any advancement I could have by using CoreAVC?

---

### Post by regneva on 2010-05-25
I have installed Mplayer with coreavc. I use this to play HD mkv files. Everything works fine except once in a while the image is garbled as shown in the attached file. After a few seconds it sorts itself out. This usually happens when there is a dramatic change in the scene. This is very annoying. Anyone knows why this happens or how I can fix it? Thanks a ton!

---

### Post by nikmad on 2010-05-25
Hi,

Am a newbie, got past thru the first step of installing wine with difficulty(had the same problem described and solved a few threads back), now having difficulty in installing Dshowserver

I have listed the errors below. All greek to me :)

Any help would be much appreciated

1)

nikmad@nikmad ~/coreavc-for-linux $ cd dshowserver && make
make -C ../loader
make[1]: Entering directory `/home/nikmad/coreavc-for-linux/loader'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/nikmad/coreavc-for-linux/loader'
winegcc  -o dshowserver ../objs-winelib/server.o ../objs-winelib/timeout_sem.o ../objs-winelib/defaults.o ../objs-winelib/crc32.o ../objs-winelib/libloader.a -lm -m32 -lole32 -loleaut32 -lrt -lpthread
/usr/bin/ld: cannot find -lwine
collect2: ld returned 1 exit status
winegcc: i486-linux-gnu-gcc failed
make: *** [dshowserver] Error 2


2)
nikmad@nikmad ~/coreavc-for-linux $ cd dshowserver && make X_COMPILE=1
i586-mingw32msvc-gcc -I../loader -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D__WINE__ -DNOAVIFILE_HEADERS -DMPLAYER -fno-omit-frame-pointer -mno-omit-leaf-frame-pointer -O2 -o ../objs-mingw/server.o -c server.c
make: i586-mingw32msvc-gcc: Command not found
make: *** [../objs-mingw/server.o] Error 127

3)
nikmad@nikmad ~/coreavc-for-linux/precompiled $ sudo make install
mkdir -p /usr/local/share/dshowserver
mkdir -p /usr/local/bin
cp dshowserver.exe /usr/local/share/dshowserver/
echo "#!/bin/sh" > /usr/local/bin/dshowserver
/bin/sh: cannot create /usr/local/bin/dshowserver: Is a directory
make: *** [install] Error 2

nikmad@nikmad ~/coreavc-for-linux/precompiled $ sudo make install X_COMPILE=1
mkdir -p /usr/local/share/dshowserver
mkdir -p /usr/local/bin
cp dshowserver.exe /usr/local/share/dshowserver/
echo "#!/bin/sh" > /usr/local/bin/dshowserver
/bin/sh: cannot create /usr/local/bin/dshowserver: Is a directory
make: *** [install] Error 2


Then i tried installing it through synaptic, that seemed to work, but on testing it, getting a new error

nikmad@nikmad ~ $ dshowserver -c CoreAVCDecoder.ax
Starting wine dshowserver.exe
No id specified, assuming test mode
Using default width  for CoreAVCDecoder.ax: 1280
Using default height for CoreAVCDecoder.ax: 720
Using default fourcc for CoreAVCDecoder.ax: 0x34363248
Using default outfmt for CoreAVCDecoder.ax: 0x30323449
Using default outbit for CoreAVCDecoder.ax: 12
Using default GUID   for CoreAVCDecoder.ax: 09571a4b-f1fe-4c60-9760de6d310c7c31
Opening device (port is 0)
Warning: DS_Filter() could not open DirectShow DLL.  (DLL=CoreAVCDecoder.ax)
Failed to create DirectShow filter
Failed to open win32 codec CoreAVCDecoder.ax


Could u kindly point out what i am doing wrong.

---

### Post by ripps818 on 2010-05-25
> **nikmad said:**
> Hi,

Am a newbie, got past thru the first step of installing wine with difficulty(had the same problem described and solved a few threads back), now having difficulty in installing Dshowserver

I have listed the errors below. All greek to me :)

Any help would be much appreciated

1)

nikmad@nikmad ~/coreavc-for-linux $ cd dshowserver && make
make -C ../loader
make[1]: Entering directory `/home/nikmad/coreavc-for-linux/loader'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/nikmad/coreavc-for-linux/loader'
winegcc  -o dshowserver ../objs-winelib/server.o ../objs-winelib/timeout_sem.o ../objs-winelib/defaults.o ../objs-winelib/crc32.o ../objs-winelib/libloader.a -lm -m32 -lole32 -loleaut32 -lrt -lpthread
/usr/bin/ld: cannot find -lwine
collect2: ld returned 1 exit status
winegcc: i486-linux-gnu-gcc failed
make: *** [dshowserver] Error 2


2)
nikmad@nikmad ~/coreavc-for-linux $ cd dshowserver && make X_COMPILE=1
i586-mingw32msvc-gcc -I../loader -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D__WINE__ -DNOAVIFILE_HEADERS -DMPLAYER -fno-omit-frame-pointer -mno-omit-leaf-frame-pointer -O2 -o ../objs-mingw/server.o -c server.c
make: i586-mingw32msvc-gcc: Command not found
make: *** [../objs-mingw/server.o] Error 127

3)
nikmad@nikmad ~/coreavc-for-linux/precompiled $ sudo make install
mkdir -p /usr/local/share/dshowserver
mkdir -p /usr/local/bin
cp dshowserver.exe /usr/local/share/dshowserver/
echo "#!/bin/sh" > /usr/local/bin/dshowserver
/bin/sh: cannot create /usr/local/bin/dshowserver: Is a directory
make: *** [install] Error 2

nikmad@nikmad ~/coreavc-for-linux/precompiled $ sudo make install X_COMPILE=1
mkdir -p /usr/local/share/dshowserver
mkdir -p /usr/local/bin
cp dshowserver.exe /usr/local/share/dshowserver/
echo "#!/bin/sh" > /usr/local/bin/dshowserver
/bin/sh: cannot create /usr/local/bin/dshowserver: Is a directory
make: *** [install] Error 2


Then i tried installing it through synaptic, that seemed to work, but on testing it, getting a new error

nikmad@nikmad ~ $ dshowserver -c CoreAVCDecoder.ax
Starting wine dshowserver.exe
No id specified, assuming test mode
Using default width  for CoreAVCDecoder.ax: 1280
Using default height for CoreAVCDecoder.ax: 720
Using default fourcc for CoreAVCDecoder.ax: 0x34363248
Using default outfmt for CoreAVCDecoder.ax: 0x30323449
Using default outbit for CoreAVCDecoder.ax: 12
Using default GUID   for CoreAVCDecoder.ax: 09571a4b-f1fe-4c60-9760de6d310c7c31
Opening device (port is 0)
Warning: DS_Filter() could not open DirectShow DLL.  (DLL=CoreAVCDecoder.ax)
Failed to create DirectShow filter
Failed to open win32 codec CoreAVCDecoder.ax


Could u kindly point out what i am doing wrong.

woo... okay, let's go through these one by one.

1) Okay, it looks here that you were trying to use the default dshowserver build method. This one uses winegcc to compile the code (which is usually unreliable and buggy for me), but the main issue is that you don't have the wine-dev package installed which supplies the wine headers needed to compile dshowserver this way.
*This should be easily solved by installing the **wine-dev** package.*

2) Now this time, you tried the compile it with the X_COMPILE method (which I recommend). This method uses mingw32 to compile the code instead of winegcc. But it seems you didn't install mingw32, so it failed. 
*Easily solved by installing the **mingw32** package.*

3) Now, you were trying to install the precompiled dshowserver.exe, which is probably the easist method, and should work on most platforms. But, it seems that it was having trouble installing the execution script. I had this problem too, and I decided to bypass the problem all together by making my own script and installing it manually. 
*I don't have an easy method of fixing this aside from rewriting the Makefile.*

4) Lastly, you tried installing a package through synaptic. I'm going to assume you used my package from the CoreAVC-for-Ubuntu PPA (as I'm the only one that builds a package, as far as I know). Okay, now there could be a number of things going on here, but since you said it worked, I'm going to assume that your problem is trying to load in configuration panel for it. This probably because your wine installation is missing some necessary files, 
*you can probably fix this by using the **winetricks** script to install **dcom98***.
```
wget http://www.kegel.com/wine/winetricks
```
And then executing the script to install the component into wine.
```
sh winetricks dcom98
```

Other issues with the dshowserver package in the PPA: 
[LIST]
[*]CoreAVCDecoder.ax not being installed correctly into /usr/share/dshowserver. 
[*]Not installing CoreAVC properly into Wine so the windows registry doesn't have proper registration username and credentials. 
[*]There is still some old remnants of previous dshowserver installations messing with the dshowserver package, make sure that there isn't any dshowserver related files remaining in /usr/local.
[/LIST]

---

### Post by nikmad on 2010-05-25
> **ripps818 said:**
> woo... okay, let's go through these one by one.

1) Okay, it looks here that you were trying to use the default dshowserver build method. This one uses winegcc to compile the code (which is usually unreliable and buggy for me), but the main issue is that you don't have the wine-dev package installed which supplies the wine headers needed to compile dshowserver this way.
*This should be easily solved by installing the **wine-dev** package.*

2) Now this time, you tried the compile it with the X_COMPILE method (which I recommend). This method uses mingw32 to compile the code instead of winegcc. But it seems you didn't install mingw32, so it failed. 
*Easily solved by installing the **mingw32** package.*

3) Now, you were trying to install the precompiled dshowserver.exe, which is probably the easist method, and should work on most platforms. But, it seems that it was having trouble installing the execution script. I had this problem too, and I decided to bypass the problem all together by making my own script and installing it manually. 
*I don't have an easy method of fixing this aside from rewriting the Makefile.*

4) Lastly, you tried installing a package through synaptic. I'm going to assume you used my package from the CoreAVC-for-Ubuntu PPA (as I'm the only one that builds a package, as far as I know). Okay, now there could be a number of things going on here, but since you said it worked, I'm going to assume that your problem is trying to load in configuration panel for it. This probably because your wine installation is missing some necessary files, 
*you can probably fix this by using the **winetricks** script to install **dcom98***.
```
wget http://www.kegel.com/wine/winetricks
```And then executing the script to install the component into wine.
```
sh winetricks dcom98
```Other issues with the dshowserver package in the PPA: 
[LIST]
[*]CoreAVCDecoder.ax not being installed correctly into /usr/share/dshowserver.
[*]Not installing CoreAVC properly into Wine so the windows registry doesn't have proper registration username and credentials.
[*]There is still some old remnants of previous dshowserver installations messing with the dshowserver package, make sure that there isn't any dshowserver related files remaining in /usr/local.
[/LIST]


Thanks for the quick response. :)

1)I tried winetricks first 
it returned 

~/coreavc-for-linux/dshowserver $ sh winetricks dcom98
err:module:attach_process_dlls "rpcrt4.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\cmd.exe" failed, status c0000005
------------------------------------------------------
wine cmd.exe /c echo '%ProgramFiles%' returned empty string


2)Then i tried the mingw32 method. Installed it thru synaptic,

ran 
cd dshowserver && make X_COMPILE=1

and 
sudo make install X_COMPILE=1

it returned

sudo make install X_COMPILE=1
mkdir -p /usr/local/share/dshowserver
mkdir -p /usr/local/bin
cp dshowserver.exe /usr/local/share/dshowserver/
echo "#!/bin/sh" > /usr/local/bin/dshowserver
/bin/sh: cannot create /usr/local/bin/dshowserver: Is a directory
make: *** [install] Error 2



:(

---

### Post by ripps818 on 2010-05-26
> **nikmad said:**
> 
1)I tried winetricks first 
it returned 

~/coreavc-for-linux/dshowserver $ sh winetricks dcom98
err:module:attach_process_dlls "rpcrt4.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\cmd.exe" failed, status c0000005
------------------------------------------------------
wine cmd.exe /c echo '%ProgramFiles%' returned empty string

Grrr... stupid Wine.
After doing some google searches, I found a discussion about this in the wine-users mailing list: [http://osdir.com/ml/wine-users/2010-01/msg00757.html]("http://osdir.com/ml/wine-users/2010-01/msg00757.html")
I'm not sure this a proper fix. I'm not getting this error with 1.1.42-ubuntu4 in Ubuntu Lucid, so I'm not quite sure what to do.

> 
2)Then i tried the mingw32 method. Installed it thru synaptic,

ran 
cd dshowserver && make X_COMPILE=1

and 
sudo make install X_COMPILE=1

it returned

sudo make install X_COMPILE=1
mkdir -p /usr/local/share/dshowserver
mkdir -p /usr/local/bin
cp dshowserver.exe /usr/local/share/dshowserver/
echo "#!/bin/sh" > /usr/local/bin/dshowserver
/bin/sh: cannot create /usr/local/bin/dshowserver: Is a directory
make: *** [install] Error 2
Yeah, it's goofing when it tries to generate the dshowsever script. I bypassed this by just making my own script.
This one *might* work with the manual install of dshowserver.
*First, create an empty file named **dshowserver***
```

#!/bin/sh
echo 'Starting wine dshowserver.exe'
wine /usr/local/share/dshowserver/dshowserver.exe $*

```
Then, make the file executable
```
chmod +x dshowserver
```
and move it to /usr/local/bin.

---

### Post by nikmad on 2010-05-26
> **ripps818 said:**
> Grrr... stupid Wine.
After doing some google searches, I found a discussion about this in the wine-users mailing list: [http://osdir.com/ml/wine-users/2010-01/msg00757.html](http://osdir.com/ml/wine-users/2010-01/msg00757.html)
I'm not sure this a proper fix. I'm not getting this error with 1.1.42-ubuntu4 in Ubuntu Lucid, so I'm not quite sure what to do.


Yeah, it's goofing when it tries to generate the dshowsever script. I bypassed this by just making my own script.
This one *might* work with the manual install of dshowserver.
*First, create an empty file named **dshowserver***
```

#!/bin/sh
echo 'Starting wine dshowserver.exe'
wine /usr/local/share/dshowserver/dshowserver.exe $*

```Then, make the file executable
```
chmod +x dshowserver
```and move it to /usr/local/bin.


:) :) :popcorn:

Your manual Dshowserver worked :) . Now it opens in mplayer from the terminal. First it played only audio and not video. I went into synaptic, and forced reinstall with "version 2:1.0~rc3+svn20090426-1ubuntu16+medibuntu1". Now, it opens from terminal ( "mplayer <file path>"), and plays video with no lag .
 But there is no open using mplayer option in the file browser. I tried installing smplayer but on opening it from browser, there is again only audio, no video. A solution for this and am all set. Thank you for all your help :)

---

### Post by ripps818 on 2010-05-26
> **nikmad said:**
> Your manual Dshowserver worked :) . Now it opens in mplayer from the terminal. First it played only audio and not video. I went into synaptic, and forced reinstall with "version 2:1.0~rc3+svn20090426-1ubuntu16+medibuntu1". Now, it opens from terminal ( "mplayer <file path>"), and plays video with no lag .
 But there is no open using mplayer option in the file browser. I tried installing smplayer but on opening it from browser, there is again only audio, no video. A solution for this and am all set. Thank you for all your help :)

Umm... if your using the medibuntu mplayer, than you're probably not using dshowserver and CoreAVC. You need to patch mplayer to use dshowserver. You're probably just using FFmpeg to decode your video, which is just fine. FFmpeg has really advanced AVC decoding these days, and I only recommend using CoreAVC if your using a particularly old or slow computer.

Also, mplayer, by it's nature, is a commandline application. Don't expect it to work from a file browser, such as nautilus, without a frontend such as gnome-mplayer or smplayer.

---

### Post by zapbrannigan99 on 2010-05-28
Hey just tried following the instructions in post#1 and I'm stuck on the line:

[B]~/mplayer-with-coreavc/coreavc-for-linux$ wget -qO - "http://pastebin.com/pastebin.php?dl=f7ca459d" | patch -p0
(Stripping trailing CRs from patch.)
patching file loader/dshow/DS_VideoDecoder.c
Hunk #1 FAILED at 97.
1 out of 1 hunk FAILED -- saving rejects to file loader/dshow/DS_VideoDecoder.c.rej
patch unexpectedly ends in middle of line


[/B]Please help?

---

### Post by ripps818 on 2010-05-28
> **zapbrannigan99 said:**
> Hey just tried following the instructions in post#1 and I'm stuck on the line:

[B]~/mplayer-with-coreavc/coreavc-for-linux$ wget -qO - "http://pastebin.com/pastebin.php?dl=f7ca459d" | patch -p0
(Stripping trailing CRs from patch.)
patching file loader/dshow/DS_VideoDecoder.c
Hunk #1 FAILED at 97.
1 out of 1 hunk FAILED -- saving rejects to file loader/dshow/DS_VideoDecoder.c.rej
patch unexpectedly ends in middle of line


[/B]Please help?

Post #1 and that patch are out of date. I don't think the dshowserver source needs to be patched anymore.

---

### Post by joris1977 on 2010-05-29
> **nikmad said:**
> I tried installing smplayer but on opening it from browser, there is again only audio, no video. A solution for this and am all set. Thank you for all your help :)

To have audio with Smplayer you probably need to change 
The audio output driver. In Smplayer preferences -> general -> audio -> audio output driver. Change it from alsa to pulse. (This made my audio work)

Oh and it is possible to use Smplayer with coreavc. Under preferences -> performance -> performance -> There is a checkbox 'use coreavc if no other codec is speciefied'. You can chec the logs in Smplayer if it is using coreavc

---

### Post by speedtortoise on 2010-05-29
One of the steps failed and I cannot move on from there...

```
$ wget -qO - "http://pastebin.com/pastebin.php?dl=f7ca459d" | patch -p0
missing header for unified diff at line 154 of patch
(Stripping trailing CRs from patch.)
patching file loader/dshow/DS_VideoDecoder.c
Hunk #1 FAILED at 97.
1 out of 1 hunk FAILED -- saving rejects to file loader/dshow/DS_VideoDecoder.c.rej
patch unexpectedly ends in middle of line
```DS_VideoDecoder.c.rej contains:
```

***************
*** 97,103 ****
        
  }
  #define is_avc(cc) (cc == mmioFOURCC('A', 'V', 'C', '1') || \
-                     cc == mmioFOURCC('a', 'v', 'c', '1'))
  char *ConvertVIHtoMPEG2VI(VIDEOINFOHEADER *vih, int *size)
  {
      struct VIDEOINFOHEADER2 {
--- 97,106 ----
        
  }
  #define is_avc(cc) (cc == mmioFOURCC('A', 'V', 'C', '1') || \
+                     cc == mmioFOURCC('a', 'v', 'c', '1') || \
+                     cc == mmioFOURCC('H', '2', '6', '4') || \
+                     cc == mmioFOURCC('h', '2', '6', '4'))
+                     
  char *ConvertVIHtoMPEG2VI(VIDEOINFOHEADER *vih, int *size)
  {
      struct VIDEOINFOHEADER2 {

```

Please tell me how I can correct this. Thank you.

---

### Post by MidBSD on 2010-05-30
Will the PPA work for 64 bit systems?

Currently I'm having problems with this error when I start gnome-mplayer:

Failed to open Win32 codec CoreAVCDecoder.ax

I copied CoreAVCDecoder64.ax and CoreAVCDecoder.ax into /usr/share/dshowserver.

My ~/.mplayer/config is as follows:


[default]
vc=coreserve,
lavdopts=threads=2

[gnome-mplayer]
msglevel=all=5

---

### Post by zapbrannigan99 on 2010-05-31
> **ripps818 said:**
> Hmm...
I was about to make a post about how a properly tweaked mplayer using only ffmpeg-mt was just as fast (if not faster) than coreavc, but with the latest dshowserver patches for mplayer, It seems that coreavc wins over ffmpeg once again, ever so slightly.

I've already upload the mplayer/dshowserver with patches to the coreavc-for-ubuntu ppa already.

Hey Ripps - I found your PPA with the prebuilt mplayer packages - wish I'd seen these at the beginning, installed and they work :)

One question though - your build of mplayer crashes when I try to play anything over smb:// - any idea how to fix this?

Thanks again for the PPA though - worked first time with mplayer (had to move dshowserver.exe to the wine windows folder cause wine couldn't find it...)

---

### Post by trapperjohn on 2010-06-10
Hey there!

I had CoreAVC+mplayer running on my Atom EEE Box using the ppa on Karmic and everything was fine.

Some days ago, my harddisk crashed (:mad:) and everything was lost. I still had the old disk lying around with Jaunty and an old CoreAVC+mplayer installation.

So I made the 2-step update from Jaunty to Karmic to Lucid, added ppa sources to apt, installed dshowserver and mplayer, installed CoreAVC 2.0 with wine and copied the CoreAVCDecoder.ax to /usr/share/dshowserver

I also renamed my old local versions of dshowserver and registercodec, so they don't interfere with the new system.

So far so good.

But when I now run "dshowserver -c CoreAVCDecoder.ax" (or just try to watch a movie using CoreAVC), the following error comes up:

```

Starting wine dshowserver.exe
No id specified, assuming test mode
Using default width  for CoreAVCDecoder.ax: 1280
Using default height for CoreAVCDecoder.ax: 720
Using default fourcc for CoreAVCDecoder.ax: 0x34363248
Using default outfmt for CoreAVCDecoder.ax: 0x30323449
Using default outbit for CoreAVCDecoder.ax: 12
Using default GUID   for CoreAVCDecoder.ax: 09571a4b-f1fe-4c60-9760de6d310c7c31
Opening device (port is 0)
len: 992
ProductVersion: 2.0.0
fixme:thread:SetThreadIdealProcessor (0x64): stub
fixme:thread:SetThreadIdealProcessor (0x68): stub
err:ole:CoGetClassObject class {1e651cc0-b199-11d0-8212-00c04fc32c45} not registered
err:ole:CoGetClassObject no class object {1e651cc0-b199-11d0-8212-00c04fc32c45} could be created for context 0x1
Warning: DS_Filter() error getting IMemAllocator interface.  (DLL=CoreAVCDecoder.ax)
Failed to create DirectShow filter
Failed to open win32 codec CoreAVCDecoder.ax
```

I'm sure it finds the .ax file, because if I rename it, dshowserver makes a clear error message about the missing file.

What's going on here? Will a clear installation of Lucid help? Or is it because of the crappy Intel graphics in the Eee box in combination with changes in Lucid?

Thanks in advance, any help would be appreciated!

---

### Post by ripps818 on 2010-06-10
> **MidBSD said:**
> Will the PPA work for 64 bit systems?

Currently I'm having problems with this error when I start gnome-mplayer:

Failed to open Win32 codec CoreAVCDecoder.ax

I copied CoreAVCDecoder64.ax and CoreAVCDecoder.ax into 

/usr/share/dshowserver.

My ~/.mplayer/config is as follows:

[default]
vc=coreserve,
lavdopts=threads=2

[gnome-mplayer]
msglevel=all=5
To be honest, I don't know if it works with 64-bit. I assumed that it would just work under 32-bit mode. You could try compliling dshowserver using mingw-w64 instead of mingw32. But I'm not sure dshowserver will recognize CoreAVCDecoder64.ax. It would probably require editing mplayer's codec.conf.

I'm sorry that I haven't been able to test it, but I don't have a x64 cpu, so I can debug these kind of problems.

[QUOTE=zapbrannigan99]Hey Ripps - I found your PPA with the prebuilt mplayer packages - wish I'd seen these at the beginning, installed and they work 

One question though - your build of mplayer crashes when I try to play anything over smb:// - any idea how to fix this?

Thanks again for the PPA though - worked first time with mplayer (had to move dshowserver.exe to the wine windows folder cause wine couldn't find it...)[/QUOTE]
You might want to talk to **uau** at **#mplayer** on **irc.freenode.net**. He's the developer of the mplayer-build branch I source the packages from. He might have an idea what might be up.

[QUOTE=trapperjohn]Hey there!

I had CoreAVC+mplayer running on my Atom EEE Box using the ppa on Karmic and everything was fine.

Some days ago, my harddisk crashed () and everything was lost. I still had the old disk lying around with Jaunty and an old CoreAVC+mplayer installation.

So I made the 2-step update from Jaunty to Karmic to Lucid, added ppa sources to apt, installed dshowserver and mplayer, installed CoreAVC 2.0 with wine and copied the CoreAVCDecoder.ax to /usr/share/dshowserver

I also renamed my old local versions of dshowserver and registercodec, so they don't interfere with the new system.

So far so good.

But when I now run "dshowserver -c CoreAVCDecoder.ax" (or just try to watch a movie using CoreAVC), the following error comes up:
```
Starting wine dshowserver.exe
No id specified, assuming test mode
Using default width  for CoreAVCDecoder.ax: 1280
Using default height for CoreAVCDecoder.ax: 720
Using default fourcc for CoreAVCDecoder.ax: 0x34363248
Using default outfmt for CoreAVCDecoder.ax: 0x30323449
Using default outbit for CoreAVCDecoder.ax: 12
Using default GUID   for CoreAVCDecoder.ax: 09571a4b-f1fe-4c60-9760de6d310c7c31
Opening device (port is 0)
len: 992
ProductVersion: 2.0.0
fixme:thread:SetThreadIdealProcessor (0x64): stub
fixme:thread:SetThreadIdealProcessor (0x68): stub
err:ole:CoGetClassObject class {1e651cc0-b199-11d0-8212-00c04fc32c45} not registered
err:ole:CoGetClassObject no class object {1e651cc0-b199-11d0-8212-00c04fc32c45} could be created for context 0x1
Warning: DS_Filter() error getting IMemAllocator interface.  (DLL=CoreAVCDecoder.ax)
Failed to create DirectShow filter
Failed to open win32 codec CoreAVCDecoder.ax
```
I'm sure it finds the .ax file, because if I rename it, dshowserver makes a clear error message about the missing file.

What's going on here? Will a clear installation of Lucid help? Or is it because of the crappy Intel graphics in the Eee box in combination with changes in Lucid?

Thanks in advance, any help would be appreciated![/QUOTE]
My best guess is that it's a Wine issue. The best solution I know is to use [winetricks]("http://wiki.winehq.org/winetricks") to install **dcom98**.

---

### Post by trapperjohn on 2010-06-13
> **ripps818 said:**
> My best guess is that it's a Wine issue. The best solution I know is to use [winetricks]("http://wiki.winehq.org/winetricks") to install **dcom98**.


Nope, didn't work. The error stays the same after DICOM98 installation.

As I need to buy another harddrive anyway, I will try it again after fresh installation of Lucid. ):P

---

### Post by aviramof on 2010-06-18
Whats up with Maverick ppa why do i get partial upgrade messege?

---

### Post by ripps818 on 2010-06-18
> **aviramof said:**
> Whats up with Maverick ppa why do i get partial upgrade messege?
It's probably the the recent ffmpeg update in Maverick. My mplayer shouldn't be affected because it uses it's own statically linked ffmpeg, seperate from the installed libraries. You'll have to wait until it's fixed. 

If that's not the problem, you'll need to give me some more details, because I'm not seeing this problem. (btw, try using aptitude from the commandline. It gives alot of useful output)

---

### Post by djerom on 2010-06-19
Hi,

I'm trying to install coreavc on a Linux distro (crunchbang statler) based on Debian Squeeze.
First I've followed the procedure described on [coreavc-for-linux]("http://code.google.com/p/coreavc-for-linux/") project (code.google hosted) compiling sources. No issue.
But an error occurs when running mplayer on a video file : loop with message "Too many buffered pts".

Then I tried installing your package "dshowserver - 0-svn115-0ubuntu2~ripps1". Same error at running.

My logs:

mplayer -vo xv -vc coreserve glee.s01e09.720p.hdtv.x264-ctu.mkv 
MPlayer SVN-r31383-4.4.4 (C) 2000-2010 MPlayer Team
154 audio & 340 video codecs

Playing glee.s01e09.720p.hdtv.x264-ctu.mkv.
libavformat file format detected.
[matroska @ 0xa0893e0]Estimating duration from bitrate, this may be inaccurate
[lavf] stream 0: audio (ac3), -aid 0
[lavf] stream 1: video (h264), -vid 0
VIDEO:  [H264]  1280x720  0bpp  24.000 fps    0.0 kbps ( 0.0 kbyte/s)
SUB: Added subtitle file (1): ./glee.s01e09.720p.hdtv.x264-ctu.srt
==========================================================================
Forced video codec: coreserve
Opening video decoder: [dshowserver] DirectShowServer video codecs
[PP] Using codec's postprocessing, max q = 4.
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 1280x720 => 1280x720 Planar YV12 
dshowserver --codec CoreAVCDecoder.ax --size 1280x720 --guid 09571a4b-f1fe-4c60-9760de6d310c7c31 --fourc 0x34363248 --bits 12 --outfmt 0x32315659 --pid 2385 --id b69d9700 --numpages 10 --port 4512 &
Starting wine dshowserver.exe
Opening device (port is 4512)
len: 992
ProductVersion: 2.0.0
fixme:thread:SetThreadIdealProcessor (0x7c): stub
fixme:thread:SetThreadIdealProcessor (0x80): stub
Decoder supports the following YUV formats: YUY2 UYVY YV12 I420 
Found DirectShow filterSelected video codec: [coreserve] vfm: dshowserver (CoreAVC DShow H264 decoder x.x for x86 - [http://corecodec.org/](http://corecodec.org/))
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 448.0 kbit/29.17% (ratio: 56000->192000)
Selected audio codec: [ffac3] afm: ffmpeg (FFmpeg AC-3)
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
EINPROGRESS in connect() - selecting
Too many buffered pts
Too many buffered pts
Too many buffered pts
...

Any idea to help me ?

[]("http://code.google.com/p/coreavc-for-linux/")

---

### Post by funkwizard on 2010-06-19
3 questions :

1.  What is dshowserver?

2.  Why is dshowserver necessary?

3.  How does dshowserver interact with mplayer?

---

### Post by ripps818 on 2010-06-20
> **funkwizard said:**
> 3 questions :
1.  What is dshowserver?
Dshowserver (or rather dshowserver.exe) is a win32 program designed to simulate Windows directshow server using Windows codecs, such as CoreAVC.
> 2.  Why is dshowserver necessary?
Dshowserver is the only way to use CoreAVC with mplayer on Linux. Right now, CoreAVC is much more efficient than FFMpeg at decoding H.264/AVC video. For people with older/slower CPUs/GPUs, it might be the only way to realistically play 720p HD videos.
> 3.  How does dshowserver interact with mplayer?
Dshowserver.exe is used by Mplayer to decode the video. Dshowserver.exe is run within a wrapper script because it relies on WINE in order to operate.

If you want a more detailed description on how dshowserver works, you'd best take it up with the developer at the [coreavc-for-linux]("http://http://code.google.com/p/coreavc-for-linux/") project.

---

### Post by funkwizard on 2010-06-22
Thanks for answering those questions so thoroughly, Ripps.

I have another question :

1.  CoreAVC uses CUDA technology on Nvidia Cards (where available).  Does the coreAVC-for-linux project (using dshowserver.exe) support CUDA?

Many thanks

---

### Post by ripps818 on 2010-06-24
> **funkwizard said:**
> Thanks for answering those questions so thoroughly, Ripps.

I have another question :

1.  CoreAVC uses CUDA technology on Nvidia Cards (where available).  Does the coreAVC-for-linux project (using dshowserver.exe) support CUDA?

Many thanks
Too be honest, I'm not sure whether CoreAVC CUDA works in Linux or not. Best to contact the developer about it.
But, if you have an Nvidia card, you'd probably have an easier time just using FFMpeg with VDPAU. That would probably give you the best performance.

---

### Post by Red3 on 2010-06-26
> **djerom said:**
> 
...
Too many buffered pts
Too many buffered pts
Too many buffered pts
...


I'm also having this problem.

Very frustrating, so close to having it working.
I didn't have this problem 2 months ago when I did this on my Karmic box, now on my Lucid box it doesn't work.

I've tried using "-nocorrect-pts" and[FONT=monospace] [/FONT]"-correct-pts" to no avail.

---

### Post by DuyUn on 2010-07-03
I get pretty confused at this step: ([http://code.google.com/p/coreavc-for-linux/wiki/MplayerInstallation](http://code.google.com/p/coreavc-for-linux/wiki/MplayerInstallation))

> 3) Install patch into mplayer: 
cd <path to mplayer source code>
patch -p0 < <path to coreavc-for-linux>/mplayer/dshowserver.patch
make
make installI got mplayer source from svn://svn.mplayerhq.hu/mplayer/trunk
I cant do "make" and "make install" before ./configure. So when should I configure ? before patching or after patching ?

I'm totally newbie to Linux. I own coreavc and would like to use it for my Ubuntu ^^

P/s: I have installed mplayer via Ubuntu software center. Do I need to remove it before following this guide ?

---

### Post by annoyingrob on 2010-07-18
> **Red3 said:**
> I'm also having this problem.

Very frustrating, so close to having it working.
I didn't have this problem 2 months ago when I did this on my Karmic box, now on my Lucid box it doesn't work.

I've tried using "-nocorrect-pts" and[FONT=monospace] [/FONT]"-correct-pts" to no avail.

Me as well. Running Lucid 64 bit with CoreAVC 1.9.5. I tried a 720p .mkv file, and it played just fine, but when I tried a 1080p .ts file, I would just get the "Too many buffered pts" message repeated over and over. If I use "-nocorrect-pts", I can get the audio, but the video remains black.

---

### Post by Nixton on 2010-08-21
Hey...I feel like a real nub at the moment...I have been trying to get my mplayer to work with HD Movies. Finaly I found a step by step Howto but I seems that its outdated.

> 
**Patch, build and install DShowServer (i386/32bit users)**

First, we need to patch the sources to make them compatible with recent versions of MPlayer:
     ```

[FONT=monospace]
[/FONT]cd coreavc-for-linux[FONT=monospace]
[/FONT]wget -qO - "http://pastebin.com/pastebin.php?dl=f7ca459d" | patch -p0


```Then we build the [FONT=monospace]dshowserver[/FONT] and [FONT=monospace]registercodec[/FONT] binaries and copy them into [FONT=monospace]/usr/local/bin[/FONT].

```

cd dshowserver
make
sudo cp dshowserver registercodec /usr/local/bin
```Already this step gives me a headache.
```

nixton@nixton-1557:~/mplayer-with-coreavc/coreavc-for-linux$ wget -qO - "http://pastebin.com/pastebin.php?dl=f7ca459d" | patch -p0
(Stripping trailing CRs from patch.)
patching file loader/dshow/DS_VideoDecoder.c
Hunk #1 FAILED at 97.
1 out of 1 hunk FAILED -- saving rejects to file loader/dshow/DS_VideoDecoder.c.rej
patch unexpectedly ends in middle of line

```I already read that *[zapbrannigan99]("http://ubuntuforums.org/member.php?u=1084944")* had the same problem and that *[ripps818]("http://ubuntuforums.org/member.php?u=283653")* said that it wasn't necessary to patch it. But what does that mean. Can I just go on with the make part (which I tried but this was the outcome)

```
nixton@nixton-1557:~/mplayer-with-coreavc/coreavc-for-linux/dshowserver$ make
winegcc -I../loader -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D__WINE__ -DNOAVIFILE_HEADERS -DMPLAYER -fno-omit-frame-pointer -mno-omit-leaf-frame-pointer -O2 -o ../objs-winelib/server.o -c server.c
make: winegcc: Kommando nicht gefunden
make: *** [../objs-winelib/server.o] Fehler 127

```This is what the dshowserver directory contains.
```

nixton@nixton-1557:~/mplayer-with-coreavc/coreavc-for-linux/dshowserver$ ls -al
insgesamt 56
drwxr-xr-x  3 nixton nixton 4096 2010-08-22 03:16 .
drwxr-xr-x 11 nixton nixton 4096 2010-08-22 03:21 ..
-rw-r--r--  1 nixton nixton 3771 2010-08-22 03:16 crc32.c
-rw-r--r--  1 nixton nixton 2387 2010-08-22 03:16 defaults.c
-rw-r--r--  1 nixton nixton  229 2010-08-22 03:16 defaults.h
-rw-r--r--  1 nixton nixton 2047 2010-08-22 03:16 Makefile
-rw-r--r--  1 nixton nixton 9642 2010-08-22 03:16 server.c
drwxr-xr-x  6 nixton nixton 4096 2010-08-22 03:16 .svn
-rw-r--r--  1 nixton nixton 9872 2010-08-22 03:16 timeout_sem.c
-rw-r--r--  1 nixton nixton  279 2010-08-22 03:16 timeout_sem.h

```
I also tried chmod +x Makefile and ./Makefile but that also doesn't lead anywhere :(
So what do I have to do???

Looking forward to your help.

P.S. I am using Ubuntu 10.04 on a Intel Core i7

---

### Post by Zorael on 2010-08-22
@Nixton;

If you merely want it to Just Work I suggest adding ripp818's ppa. A simple upgrade of the **mplayer** package and an installation of the **dshowserver** one should get your mplayer sorted. Then it's just a matter of installing CoreAVC via Wine, and copying the **CoreAVCDecoder.ax** file from where the CoreAVC installer put it to **/usr/share/dshowserver/**.

```
$ sudo add-apt-repository ppa:ripps818/coravc
$ sudo aptitude update
$ sudo aptitude full-upgrade mplayer+ dshowserver+
```

---

### Post by Nixton on 2010-08-22
Thanks for your fast response. I added the repository and did the upgrade but I seem to have a problem with wine.

> Then it's just a matter of installing CoreAVC via Wine, and copying the **CoreAVCDecoder.ax** file from where the CoreAVC installer put it to **/usr/share/dshowserver/**.```

root@nixton-1557:/home/nixton/Downloads/mplayer/CoreAVC H264 Video Codec Pro v2.0.0# wine coreavc_professional_edition-setup.exe 
wine: created the configuration directory '/root/.wine'
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x33cfd4
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\system32\\gecko\\1.0.0\\wine_gecko\\components\\xpti.dat" 1 536870916 (nil) (nil) 0x1923e4 (nil)
fixme:iphlpapi:NotifyAddrChange (Handle 0xa71e8d8, overlapped 0xa71e8e0): stub
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\system32\\gecko\\1.0.0\\wine_gecko\\components\\compreg.dat" 1 536870916 (nil) (nil) 0x1f2a0fc (nil)
wine: configuration in '/root/.wine' has been updated.
err:ntdll:RtlpWaitForCriticalSection section 0x7bca27e4 "loader.c: loader_section" wait timed out in thread 0029, blocked by 0009, retrying (60 sec)
wine: Critical section 7bca27e4 wait failed at address 0x7bc34fdd (thread 0029), starting debugger...
Unhandled exception: wait failed on critical section 0x7bca27e4
err:seh:raise_exception Unhandled exception code c0000194 flags 0 addr 0x7bc34fdd
Process of pid=0008 has terminated
No process loaded, cannot execute 'echo Modules:'
Cannot get info on module while no process is loaded
No process loaded, cannot execute 'echo Threads:'
process  tid      prio (all id:s are in hex)
root@nixton-1557:/home/nixton/Downloads/mplayer/CoreAVC H264 Video Codec Pro v2.0.0# 0000000c services.exe
    00000024    0
    0000000e    0
    0000000d    0
00000011 explorer.exe
    00000012    0
00000021 winedevice.exe
    00000027    0
    00000026    0
    00000023    0
    00000022    0
You must be attached to a process to run this command.
No process loaded, cannot execute 'detach'
^C

```This is my first experience with wine (so it was freshly installed on my system). Is there something I have to add to the command or should 
```
wine app.exe
```be enough?

Greetz

EDIT:
Since you said I only need the .ax file I installed CoreAVC on a virtual machine of Win XP in a VBOX. So I now have the CoreAVCDecoder.ax in /usr/share/dshowserver....but what now??? I am really confused!

---

### Post by ShadowKyuzo on 2010-09-29
> **ogooreck said:**
> Thanks Alan !

It works here too.

My steps:

1. checkout mplayer from svn (or prepare your sources for patching)
2. checkout coreavc-for-linux
3. apply dshowserver.patch to mplayer sources
4. configure mplayer sources
5. make install mplayer
6. Install wine
7. Install coreavc on wine
8. Copy dshowserver.exe to CoreAVC install dir
9. Create a wrapper script to run dshowserver.exe - see code. Name it dshowserver and place in PATH. "Disable" old dshowserver.
10. Configure mplayer - old codecs.conf configuration just works. There are new tips how to workaround fourcc issues in README
11. Enjoy your movies

```
#!/bin/sh

DSHOWSERVEREXE="c:\\Program Files\\CoreCodec\\CoreAVC Professional Edition\\dshowserver.exe"
wine "${DSHOWSERVEREXE}" "$@"
# if you wish to run dshowserver with elevated priority comment out line above and uncomment line below
# nice -n -5 wine "${DSHOWSERVEREXE}" "$@"

```

Thanks a lot! it worked!!! With CoreAVC 2.0.0

To anyone out there trying to make it work: 
Just do exactly as ogooreck says, skipping step 3 (patch doesnt work anymore and its not needed) and it should run fine.

Now i only need to watch some 1080p movie entirely to see if im gonna experience any problems :P

Mplayer installation instructions:
[http://code.google.com/p/coreavc-for-linux/wiki/MplayerInstallation](http://code.google.com/p/coreavc-for-linux/wiki/MplayerInstallation) (ignore patch process)

Dshowserver:
[http://code.google.com/p/coreavc-for-linux/wiki/DshowserverInstall](http://code.google.com/p/coreavc-for-linux/wiki/DshowserverInstall)

hope it helps someone,
cya

---

### Post by trancephorm on 2010-10-06
..Been trying for few days now to setup CoreAVC with Mplayer first in Mint 9.0 which I like a bit more to Ubuntu 10.04.1, but after several unsuccessful attempts, finally decided to go Ubuntu 10.04.1 way, because I found this topic. Sure, I get hunk #1 failed when I try to patch, and then I saw ripps's PPA, but I'm really new to installing software from PPA.

The problem is how can I be sure mplayer is actually installed from PPA? I ask because I see the package name in PPA is mplayer-build, but when I try "sudo apt-get install mplayer-build" it says package cannot be found.

I tried "sudo add-apt-repository ppa:ripps818/coreavc" along with "sudo apt-get update" & "sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com EEB23232"

I also tried to add these lines manually to /etc/apt/sources.list:
```

deb http://ppa.launchpad.net/ripps818/coreavc/ubuntu lucid main 
deb-src http://ppa.launchpad.net/ripps818/coreavc/ubuntu lucid main

```

Do I really need to type "apt-get install mplayer"? I doubt.

I would really love to dump out Windows from my laptop that serves as a player for 1080p content. So CoreAVC is a must for me because I don't have that fancy new nVidia hardware with vdpau... etc...

With a little bit of help from the community I hope I can make this work :), still I'm wondering why multithreaded mplayer isn't installed by default in the system, that's really the essential thing.

Thanks...

---

### Post by trancephorm on 2010-10-06
Never mind... I solved it... found that post 4-5 posts above... Works! :)
The only problem remaining is that ripps's patched mplayer doesn't support audio filter (-af pan) which is supposed to downmix 5.1 audio channels to stereo, which is needed on my setup.

---

### Post by klepto on 2010-10-13
A very big thank you to whoever is running that repo.
On my little Asus 1000HE 720p video runs smooth as hell. 

Bookmarked for posterity.

---

### Post by KisGellert on 2010-10-22
can i play my ghost in the shell 2.0 DVD with coreavc?

i cant. smplayer dont work as well.

aaa@aaa:~$ mplayer dvd://1 -vc coreserve, -dvd-device /dev/scd0
...
...
==========================================================================
Forced video codec: coreserve
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffmpeg2] vfm: ffmpeg (FFmpeg MPEG-2)
==========================================================================
???:confused:

---

### Post by Zorael on 2010-10-28
> **KisGellert said:**
> can i play my ghost in the shell 2.0 DVD with coreavc?

i cant. smplayer dont work as well.
Well, it has to be h264-encoded for CoreAVC to be able to play it...

------------------------------------------------------------

I just installed Maverick on this other computer and thought I'd install CoreAVC, but I must have forgotten some step. I installed it via Wine, copied the .ax file to **/usr/lib/dshowserver/**, and now the test command works.
```
$ dshowserver -c CoreAVCDecoder.ax
Starting wine dshowserver.exe
No id specified, assuming test mode
Using default width  for CoreAVCDecoder.ax: 1280
Using default height for CoreAVCDecoder.ax: 720
Using default fourcc for CoreAVCDecoder.ax: 0x34363248
Using default outfmt for CoreAVCDecoder.ax: 0x30323449
Using default outbit for CoreAVCDecoder.ax: 12
Using default GUID   for CoreAVCDecoder.ax: 09571a4b-f1fe-4c60-9760de6d310c7c31
Opening device (port is 0)
len: 992
ProductVersion: 2.0.0
fixme:thread:SetThreadIdealProcessor (0x6c): stub
fixme:thread:SetThreadIdealProcessor (0x70): stub
Decoder supports the following YUV formats: YUY2 UYVY YV12 I420 
Decoder is capable of YUV output (flags 0x2b)
Setting fmt
Starting
Initialization is complete
```

But when I try to play anything, I get this.
```
==========================================================================
Forced video codec: coreserve
Opening video decoder: [dshowserver] DirectShowServer video codecs
[PP] Using codec's postprocessing, max q = 4.
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 1280x720 => 1280x720 Planar YV12 
dshowserver --codec CoreAVCDecoder.ax --size 1280x720 --guid 09571a4b-f1fe-4c60-9760de6d310c7c31 --fourc 0x31637661 --bits 12 --outfmt 0x32315659 --pid 14732 --id 8a78a7c0 --numpages 10 --port 37550 &
Starting wine dshowserver.exe
Opening device (port is 37550)
len: 992
ProductVersion: 2.0.0
fixme:thread:SetThreadIdealProcessor (0x74): stub
fixme:thread:SetThreadIdealProcessor (0x78): stub
Decoder supports the following YUV formats: YUY2 UYVY YV12 I420 
Found DirectShow filterSelected video codec: [coreserve] vfm: dshowserver (CoreAVC DShow H264 decoder - http://corecodec.org/)
==========================================================================
==========================================================================
EINPROGRESS in connect() - selecting
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 1536.0 kbit/100.00% (ratio: 192000->192000)
Selected audio codec: [ffdca] afm: ffmpeg (FFmpeg DTS)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
[Mixer] No hardware mixing, inserting volume filter.
Starting playback...
Got illegal command 0
Decoder is capable of YUV output (flags 0x2b)
Setting fmt
Starting
Initialization is complete
Using socket based mutex
Dshowserver Connected to host
A:   0.0 V:   0.0 A-V:  0.030 ct:  0.000   0/  0 ??% ??% ??,?% 0 0 

MPlayer interrupted by signal 13 in module: check_framedrop
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
```

I don't have any complex .mplayer/config file, so that's not causing it.

```
$ apt-cache policy mplayer dshowserver
mplayer:
  Installed: 3:1.0~rc3+git20101021.4b2f9f6-0ubuntu1~ripps1
dshowserver:
  Installed: 0-svn115-0ubuntu2~ripps1

```

---

### Post by docomo on 2010-11-19
> **Zorael said:**
> @Nixton;

If you merely want it to Just Work I suggest adding ripp818's ppa. A simple upgrade of the **mplayer** package and an installation of the **dshowserver** one should get your mplayer sorted. Then it's just a matter of installing CoreAVC via Wine, and copying the **CoreAVCDecoder.ax** file from where the CoreAVC installer put it to **/usr/share/dshowserver/**.

```
$ sudo add-apt-repository ppa:ripps818/coravc
$ sudo aptitude update
$ sudo aptitude full-upgrade mplayer+ dshowserver+
```

Thanks, that worked perfectly!

Small correction: It should be:
$ sudo add-apt-repository ppa:ripps818/coreavc

---

### Post by mulat on 2010-11-22
ppa:ripps818/coreavc working also on Mint Julia :)

---

### Post by GFUnforgiven on 2010-12-07
I installed CoreAVC just fine but there is a single file I can't seem to play anymore. The CRC matches so I'm sure its not broken and I was able to view it (with intense lag) before I installed CoreAVC.

> 
p, li { white-space: pre-wrap; } /usr/bin/mplayer -noquiet -nofs -nomouseinput -vc coreavcwindows -lavdopts threads=4 -sub-fuzziness 1 -identify -slave -vo xv, -ao pulse -nokeepaspect -nodr -double -input nodefault-bindings:conf=/dev/null -stop-xscreensaver -wid 102760803 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/unforgiven/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp enca:en:UTF-8 -vid 0 -aid 0 -subpos 100 -volume 100 -cache 5000 -ss 709 -osdlevel 0 -vf-add screenshot -slices -channels 2 -af scaletempo,equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 110 /media/server/Complete/[Coalgirls] Higashi no Eden/[Coalgirls] Higashi no Eden 01 [013B9B32].mkv
 
 MPlayer UNKNOWN-4.4.5 (C) 2000-2010 MPlayer Team
 mplayer: could not connect to socket
 mplayer: No such file or directory
 Failed to open LIRC support. You will not be able to use your remote control.
 Terminal type `unknown' is not defined.
 
 Playing /media/server/Complete/[Coalgirls] Higashi no Eden/[Coalgirls] Higashi no Eden 01 [013B9B32].mkv.
 
 Cache fill:  0.00% (0 bytes)   
 
 ID_CHAPTER_ID=0
 ID_CHAPTER_0_START=0
 ID_CHAPTER_0_END=30989
 ID_CHAPTER_0_NAME=Prologue
 ID_CHAPTER_ID=1
 ID_CHAPTER_1_START=0
 ID_CHAPTER_1_END=81039
 ID_CHAPTER_1_NAME=Opening
 ID_CHAPTER_ID=2
 ID_CHAPTER_2_START=31031
 ID_CHAPTER_2_END=1192149
 ID_CHAPTER_2_NAME=Episode
 ID_CHAPTER_ID=3
 ID_CHAPTER_3_START=0
 ID_CHAPTER_3_END=82040
 ID_CHAPTER_3_NAME=Ending
 ID_VIDEO_ID=0
 ID_VID_0_NAME=Eden of the East 01
 [mkv] Track ID 1: video (V_MPEG4/ISO/AVC) "Eden of the East 01", -vid 0
 ID_AUDIO_ID=0
 ID_AID_0_NAME=5.1 FLAC
 ID_AID_0_LANG=jpn
 [mkv] Track ID 2: audio (A_FLAC) "5.1 FLAC", -aid 0, -alang jpn
 ID_AUDIO_ID=1
 ID_AID_1_NAME=5.1 FLAC
 ID_AID_1_LANG=eng
 [mkv] Track ID 3: audio (A_FLAC) "5.1 FLAC", -aid 1, -alang eng
 ID_SUBTITLE_ID=0
 ID_SID_0_NAME=English
 ID_SID_0_LANG=eng
 [mkv] Track ID 4: subtitles (S_TEXT/***) "English", -sid 0, -slang eng
 ID_SUBTITLE_ID=1
 ID_SID_1_NAME=Songs + Signs
 ID_SID_1_LANG=eng
 [mkv] Track ID 5: subtitles (S_TEXT/***) "Songs + Signs", -sid 1, -slang eng
 [mkv] Will play video track 1.
 Detected file format: Matroska
 VIDEO:  [avc1]  1920x1080  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
 File uses ordered chapters, will build edit timeline.
 This file references data from other sources.
 Will scan other files in the same directory to find referenced sources.
 Checking file /media/server/Complete/[Coalgirls] Higashi no Eden/[Coalgirls] Higashi no Eden 02 [937F2ECC].mkv
 ID_CHAPTER_ID=0
 ID_CHAPTER_0_START=0
 ID_CHAPTER_0_END=81039
 ID_CHAPTER_0_NAME=Opening
 ID_CHAPTER_ID=1
 ID_CHAPTER_1_START=0
 ID_CHAPTER_1_END=1191148
 ID_CHAPTER_1_NAME=Episode
 ID_CHAPTER_ID=2
 ID_CHAPTER_2_START=0
 ID_CHAPTER_2_END=82040
 ID_CHAPTER_2_NAME=Ending
 ID_VIDEO_ID=0
 ID_VID_0_NAME=Eden of the East 02
 [mkv] Track ID 1: video (V_MPEG4/ISO/AVC) "Eden of the East 02", -vid 0
 ID_AUDIO_ID=0
 ID_AID_0_NAME=5.1 FLAC
 ID_AID_0_LANG=jpn
 [mkv] Track ID 2: audio (A_FLAC) "5.1 FLAC", -aid 0, -alang jpn
 ID_AUDIO_ID=1
 ID_AID_1_NAME=5.1 FLAC
 ID_AID_1_LANG=eng
 [mkv] Track ID 3: audio (A_FLAC) "5.1 FLAC", -aid 1, -alang eng
 ID_SUBTITLE_ID=0
 ID_SID_0_NAME=English
 ID_SID_0_LANG=eng
 [mkv] Track ID 4: subtitles (S_TEXT/***) "English", -sid 0, -slang eng
 ID_SUBTITLE_ID=1
 ID_SID_1_NAME=Songs + Signs
 ID_SID_1_LANG=eng
 [mkv] Track ID 5: subtitles (S_TEXT/***) "Songs + Signs", -sid 1, -slang eng
 [mkv] Will play video track 1.
 Detected file format: Matroska
 VIDEO:  [avc1]  1920x1080  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
 Checking file /media/server/Complete/[Coalgirls] Higashi no Eden/[Coalgirls] Higashi no Eden 03 [63734DEC].mkv
 ID_CHAPTER_ID=0
 ID_CHAPTER_0_START=0
 ID_CHAPTER_0_END=81039
 ID_CHAPTER_0_NAME=Opening
 ID_CHAPTER_ID=1
 ID_CHAPTER_1_START=0
 ID_CHAPTER_1_END=1191148
 ID_CHAPTER_1_NAME=Episode
 ID_CHAPTER_ID=2
 ID_CHAPTER_2_START=0
 ID_CHAPTER_2_END=82040
 ID_CHAPTER_2_NAME=Ending
 ID_VIDEO_ID=0
 ID_VID_0_NAME=Eden of the East 03
 [mkv] Track ID 1: video (V_MPEG4/ISO/AVC) "Eden of the East 03", -vid 0
 ID_AUDIO_ID=0
 ID_AID_0_NAME=5.1 FLAC
 ID_AID_0_LANG=jpn
 [mkv] Track ID 2: audio (A_FLAC) "5.1 FLAC", -aid 0, -alang jpn
 ID_AUDIO_ID=1
 ID_AID_1_NAME=5.1 FLAC
 ID_AID_1_LANG=eng
 [mkv] Track ID 3: audio (A_FLAC) "5.1 FLAC", -aid 1, -alang eng
 ID_SUBTITLE_ID=0
 ID_SID_0_NAME=English
 ID_SID_0_LANG=eng
 [mkv] Track ID 4: subtitles (S_TEXT/***) "English", -sid 0, -slang eng
 ID_SUBTITLE_ID=1
 ID_SID_1_NAME=Songs + Signs
 ID_SID_1_LANG=eng
 [mkv] Track ID 5: subtitles (S_TEXT/***) "Songs + Signs", -sid 1, -slang eng
 [mkv] Will play video track 1.
 Detected file format: Matroska
 VIDEO:  [avc1]  1920x1080  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
 Checking file /media/server/Complete/[Coalgirls] Higashi no Eden/[Coalgirls] Higashi no Eden 04 [570A5043].mkv
 ID_CHAPTER_ID=0
 ID_CHAPTER_0_START=0
 ID_CHAPTER_0_END=72406
 ID_CHAPTER_0_NAME=Prologue
 ID_CHAPTER_ID=1
 ID_CHAPTER_1_START=0
 ID_CHAPTER_1_END=81039
 ID_CHAPTER_1_NAME=Opening
 ID_CHAPTER_ID=2
 ID_CHAPTER_2_START=72447
 ID_CHAPTER_2_END=1191148
 ID_CHAPTER_2_NAME=Episode
 ID_CHAPTER_ID=3
 ID_CHAPTER_3_START=0
 ID_CHAPTER_3_END=82040
 ID_CHAPTER_3_NAME=Ending
 ID_VIDEO_ID=0
 ID_VID_0_NAME=Eden of the East 04
 [mkv] Track ID 1: video (V_MPEG4/ISO/AVC) "Eden of the East 04", -vid 0
 ID_AUDIO_ID=0
 ID_AID_0_NAME=5.1 FLAC
 ID_AID_0_LANG=jpn
 [mkv] Track ID 2: audio (A_FLAC) "5.1 FLAC", -aid 0, -alang jpn
 ID_AUDIO_ID=1
 ID_AID_1_NAME=5.1 FLAC
 ID_AID_1_LANG=eng
 [mkv] Track ID 3: audio (A_FLAC) "5.1 FLAC", -aid 1, -alang eng
 ID_SUBTITLE_ID=0
 ID_SID_0_NAME=English
 ID_SID_0_LANG=eng
 [mkv] Track ID 4: subtitles (S_TEXT/***) "English", -sid 0, -slang eng
 ID_SUBTITLE_ID=1
 ID_SID_1_NAME=Songs + Signs
 ID_SID_1_LANG=eng
 [mkv] Track ID 5: subtitles (S_TEXT/***) "Songs + Signs", -sid 1, -slang eng
 [mkv] Will play video track 1.
 Detected file format: Matroska
 VIDEO:  [avc1]  1920x1080  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
 Checking file /media/server/Complete/[Coalgirls] Higashi no Eden/[Coalgirls] Higashi no Eden 05 [307C3F38].mkv
 ID_CHAPTER_ID=0
 ID_CHAPTER_0_START=0
 ID_CHAPTER_0_END=92926
 ID_CHAPTER_0_NAME=Prologue
 ID_CHAPTER_ID=1
 ID_CHAPTER_1_START=0
 ID_CHAPTER_1_END=81039
 ID_CHAPTER_1_NAME=Opening
 ID_CHAPTER_ID=2
 ID_CHAPTER_2_START=92968
 ID_CHAPTER_2_END=1191148
 ID_CHAPTER_2_NAME=Episode
 ID_CHAPTER_ID=3
 ID_CHAPTER_3_START=0
 ID_CHAPTER_3_END=82040
 ID_CHAPTER_3_NAME=Ending
 ID_VIDEO_ID=0
 ID_VID_0_NAME=Eden of the East 05
 [mkv] Track ID 1: video (V_MPEG4/ISO/AVC) "Eden of the East 05", -vid 0
 ID_AUDIO_ID=0
 ID_AID_0_NAME=5.1 FLAC
 ID_AID_0_LANG=jpn
 [mkv] Track ID 2: audio (A_FLAC) "5.1 FLAC", -aid 0, -alang jpn
 ID_AUDIO_ID=1
 ID_AID_1_NAME=5.1 FLAC
 ID_AID_1_LANG=eng
 [mkv] Track ID 3: audio (A_FLAC) "5.1 FLAC", -aid 1, -alang eng
 ID_SUBTITLE_ID=0
 ID_SID_0_NAME=English
 ID_SID_0_LANG=eng
 [mkv] Track ID 4: subtitles (S_TEXT/***) "English", -sid 0, -slang eng
 ID_SUBTITLE_ID=1
 ID_SID_1_NAME=Songs + Signs
 ID_SID_1_LANG=eng
 [mkv] Track ID 5: subtitles (S_TEXT/***) "Songs + Signs", -sid 1, -slang eng
 [mkv] Will play video track 1.
 Detected file format: Matroska
 VIDEO:  [avc1]  1920x1080  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
 Checking file /media/server/Complete/[Coalgirls] Higashi no Eden/[Coalgirls] Higashi no Eden 06 [E756D697].mkv
 ID_CHAPTER_ID=0
 ID_CHAPTER_0_START=0
 ID_CHAPTER_0_END=85210
 ID_CHAPTER_0_NAME=Prologue
 ID_CHAPTER_ID=1
 ID_CHAPTER_1_START=0
 ID_CHAPTER_1_END=81039
 ID_CHAPTER_1_NAME=Opening
 ID_CHAPTER_ID=2
 ID_CHAPTER_2_START=85252
 ID_CHAPTER_2_END=1191148
 ID_CHAPTER_2_NAME=Episode
 ID_CHAPTER_ID=3
 ID_CHAPTER_3_START=0
 ID_CHAPTER_3_END=82040
 ID_CHAPTER_3_NAME=Ending
 ID_VIDEO_ID=0
 ID_VID_0_NAME=Eden of the East 06
 [mkv] Track ID 1: video (V_MPEG4/ISO/AVC) "Eden of the East 06", -vid 0
 ID_AUDIO_ID=0
 ID_AID_0_NAME=5.1 FLAC
 ID_AID_0_LANG=jpn
 [mkv] Track ID 2: audio (A_FLAC) "5.1 FLAC", -aid 0, -alang jpn
 ID_AUDIO_ID=1
 ID_AID_1_NAME=5.1 FLAC
 ID_AID_1_LANG=eng
 [mkv] Track ID 3: audio (A_FLAC) "5.1 FLAC", -aid 1, -alang eng
 ID_SUBTITLE_ID=0
 ID_SID_0_NAME=English
 ID_SID_0_LANG=eng
 [mkv] Track ID 4: subtitles (S_TEXT/***) "English", -sid 0, -slang eng
 ID_SUBTITLE_ID=1
 ID_SID_1_NAME=Songs + Signs
 ID_SID_1_LANG=eng
 [mkv] Track ID 5: subtitles (S_TEXT/***) "Songs + Signs", -sid 1, -slang eng
 [mkv] Will play video track 1.
 Detected file format: Matroska
 VIDEO:  [avc1]  1920x1080  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
 Checking file /media/server/Complete/[Coalgirls] Higashi no Eden/[Coalgirls] Higashi no Eden 07 [AF133BE6].mkv
 ID_CHAPTER_ID=0
 ID_CHAPTER_0_START=0
 ID_CHAPTER_0_END=74992
 ID_CHAPTER_0_NAME=Prologue
 ID_CHAPTER_ID=1
 ID_CHAPTER_1_START=0
 ID_CHAPTER_1_END=81039
 ID_CHAPTER_1_NAME=Opening
 ID_CHAPTER_ID=2
 ID_CHAPTER_2_START=75033
 ID_CHAPTER_2_END=1191148
 ID_CHAPTER_2_NAME=Episode
 ID_CHAPTER_ID=3
 ID_CHAPTER_3_START=0
 ID_CHAPTER_3_END=82040
 ID_CHAPTER_3_NAME=Ending
 ID_VIDEO_ID=0
 ID_VID_0_NAME=Eden of the East 07
 [mkv] Track ID 1: video (V_MPEG4/ISO/AVC) "Eden of the East 07", -vid 0
 ID_AUDIO_ID=0
 ID_AID_0_NAME=5.1 FLAC
 ID_AID_0_LANG=jpn
 [mkv] Track ID 2: audio (A_FLAC) "5.1 FLAC", -aid 0, -alang jpn
 ID_AUDIO_ID=1
 ID_AID_1_NAME=5.1 FLAC
 ID_AID_1_LANG=eng
 [mkv] Track ID 3: audio (A_FLAC) "5.1 FLAC", -aid 1, -alang eng
 ID_SUBTITLE_ID=0
 ID_SID_0_NAME=English
 ID_SID_0_LANG=eng
 [mkv] Track ID 4: subtitles (S_TEXT/***) "English", -sid 0, -slang eng
 ID_SUBTITLE_ID=1
 ID_SID_1_NAME=Songs + Signs
 ID_SID_1_LANG=eng
 [mkv] Track ID 5: subtitles (S_TEXT/***) "Songs + Signs", -sid 1, -slang eng
 [mkv] Will play video track 1.
 Detected file format: Matroska
 VIDEO:  [avc1]  1920x1080  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
 Checking file /media/server/Complete/[Coalgirls] Higashi no Eden/[Coalgirls] Higashi no Eden 08 [680AF98E].mkv
 ID_CHAPTER_ID=0
 ID_CHAPTER_0_START=0
 ID_CHAPTER_0_END=70529
 ID_CHAPTER_0_NAME=Prologue
 ID_CHAPTER_ID=1
 ID_CHAPTER_1_START=0
 ID_CHAPTER_1_END=81039
 ID_CHAPTER_1_NAME=Opening
 ID_CHAPTER_ID=2
 ID_CHAPTER_2_START=70569
 ID_CHAPTER_2_END=1191148
 ID_CHAPTER_2_NAME=Episode
 ID_CHAPTER_ID=3
 ID_CHAPTER_3_START=0
 ID_CHAPTER_3_END=82040
 ID_CHAPTER_3_NAME=Ending
 ID_VIDEO_ID=0
 ID_VID_0_NAME=Eden of the East 08
 [mkv] Track ID 1: video (V_MPEG4/ISO/AVC) "Eden of the East 08", -vid 0
 ID_AUDIO_ID=0
 ID_AID_0_NAME=5.1 FLAC
 ID_AID_0_LANG=jpn
 [mkv] Track ID 2: audio (A_FLAC) "5.1 FLAC", -aid 0, -alang jpn
 ID_AUDIO_ID=1
 ID_AID_1_NAME=5.1 FLAC
 ID_AID_1_LANG=eng
 [mkv] Track ID 3: audio (A_FLAC) "5.1 FLAC", -aid 1, -alang eng
 ID_SUBTITLE_ID=0
 ID_SID_0_NAME=English
 ID_SID_0_LANG=eng
 [mkv] Track ID 4: subtitles (S_TEXT/***) "English", -sid 0, -slang eng
 ID_SUBTITLE_ID=1
 ID_SID_1_NAME=Songs + Signs
 ID_SID_1_LANG=eng
 [mkv] Track ID 5: subtitles (S_TEXT/***) "Songs + Signs", -sid 1, -slang eng
 [mkv] Will play video track 1.
 Detected file format: Matroska
 VIDEO:  [avc1]  1920x1080  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
 Checking file /media/server/Complete/[Coalgirls] Higashi no Eden/[Coalgirls] Higashi no Eden 09 [CAC254FC].mkv
 ID_CHAPTER_ID=0
 ID_CHAPTER_0_START=0
 ID_CHAPTER_0_END=40499
 ID_CHAPTER_0_NAME=Prologue
 ID_CHAPTER_ID=1
 ID_CHAPTER_1_START=0
 ID_CHAPTER_1_END=81039
 ID_CHAPTER_1_NAME=Opening
 ID_CHAPTER_ID=2
 ID_CHAPTER_2_START=40540
 ID_CHAPTER_2_END=1191148
 ID_CHAPTER_2_NAME=Episode
 ID_CHAPTER_ID=3
 ID_CHAPTER_3_START=0
 ID_CHAPTER_3_END=82040
 ID_CHAPTER_3_NAME=Ending
 ID_VIDEO_ID=0
 ID_VID_0_NAME=Eden of the East 09
 [mkv] Track ID 1: video (V_MPEG4/ISO/AVC) "Eden of the East 09", -vid 0
 ID_AUDIO_ID=0
 ID_AID_0_NAME=5.1 FLAC
 ID_AID_0_LANG=jpn
 [mkv] Track ID 2: audio (A_FLAC) "5.1 FLAC", -aid 0, -alang jpn
 ID_AUDIO_ID=1
 ID_AID_1_NAME=5.1 FLAC
 ID_AID_1_LANG=eng
 [mkv] Track ID 3: audio (A_FLAC) "5.1 FLAC", -aid 1, -alang eng
 ID_SUBTITLE_ID=0
 ID_SID_0_NAME=English
 ID_SID_0_LANG=eng
 [mkv] Track ID 4: subtitles (S_TEXT/***) "English", -sid 0, -slang eng
 ID_SUBTITLE_ID=1
 ID_SID_1_NAME=Songs + Signs
 ID_SID_1_LANG=eng
 [mkv] Track ID 5: subtitles (S_TEXT/***) "Songs + Signs", -sid 1, -slang eng
 [mkv] Will play video track 1.
 Detected file format: Matroska
 VIDEO:  [avc1]  1920x1080  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
 Checking file /media/server/Complete/[Coalgirls] Higashi no Eden/[Coalgirls] Higashi no Eden 10 [08CEAF12].mkv
 ID_CHAPTER_ID=0
 ID_CHAPTER_0_START=0
 ID_CHAPTER_0_END=259217
 ID_CHAPTER_0_NAME=Prologue
 ID_CHAPTER_ID=1
 ID_CHAPTER_1_START=0
 ID_CHAPTER_1_END=81039
 ID_CHAPTER_1_NAME=Opening
 ID_CHAPTER_ID=2
 ID_CHAPTER_2_START=259259
 ID_CHAPTER_2_END=1191148
 ID_CHAPTER_2_NAME=Episode
 ID_CHAPTER_ID=3
 ID_CHAPTER_3_START=0
 ID_CHAPTER_3_END=82040
 ID_CHAPTER_3_NAME=Ending
 ID_VIDEO_ID=0
 ID_VID_0_NAME=Eden of the East 10
 [mkv] Track ID 1: video (V_MPEG4/ISO/AVC) "Eden of the East 10", -vid 0
 ID_AUDIO_ID=0
 ID_AID_0_NAME=5.1 FLAC
 ID_AID_0_LANG=jpn
 [mkv] Track ID 2: audio (A_FLAC) "5.1 FLAC", -aid 0, -alang jpn
 ID_AUDIO_ID=1
 ID_AID_1_NAME=5.1 FLAC
 ID_AID_1_LANG=eng
 [mkv] Track ID 3: audio (A_FLAC) "5.1 FLAC", -aid 1, -alang eng
 ID_SUBTITLE_ID=0
 ID_SID_0_NAME=Songs + Signs
 ID_SID_0_LANG=eng
 [mkv] Track ID 4: subtitles (S_TEXT/***) "Songs + Signs", -sid 0, -slang eng
 ID_SUBTITLE_ID=1
 ID_SID_1_NAME=English
 ID_SID_1_LANG=eng
 [mkv] Track ID 5: subtitles (S_TEXT/***) "English", -sid 1, -slang eng
 [mkv] Will play video track 1.
 Detected file format: Matroska
 VIDEO:  [avc1]  1920x1080  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
 Checking file /media/server/Complete/[Coalgirls] Higashi no Eden/[Coalgirls] Higashi no Eden 11 [D9931607].mkv
 ID_CHAPTER_ID=0
 ID_CHAPTER_0_START=0
 ID_CHAPTER_0_END=340298
 ID_CHAPTER_0_NAME=Prologue
 ID_CHAPTER_ID=1
 ID_CHAPTER_1_START=0
 ID_CHAPTER_1_END=81039
 ID_CHAPTER_1_NAME=Opening
 ID_CHAPTER_ID=2
 ID_CHAPTER_2_START=340340
 ID_CHAPTER_2_END=1191148
 ID_CHAPTER_2_NAME=Episode
 ID_CHAPTER_ID=3
 ID_CHAPTER_3_START=0
 ID_CHAPTER_3_END=82040
 ID_CHAPTER_3_NAME=Ending
 ID_VIDEO_ID=0
 ID_VID_0_NAME=Eden of the East 11
 [mkv] Track ID 1: video (V_MPEG4/ISO/AVC) "Eden of the East 11", -vid 0
 ID_AUDIO_ID=0
 ID_AID_0_NAME=5.1 FLAC
 ID_AID_0_LANG=jpn
 [mkv] Track ID 2: audio (A_FLAC) "5.1 FLAC", -aid 0, -alang jpn
 ID_AUDIO_ID=1
 ID_AID_1_NAME=5.1 FLAC
 ID_AID_1_LANG=eng
 [mkv] Track ID 3: audio (A_FLAC) "5.1 FLAC", -aid 1, -alang eng
 ID_SUBTITLE_ID=0
 ID_SID_0_NAME=English
 ID_SID_0_LANG=eng
 [mkv] Track ID 4: subtitles (S_TEXT/***) "English", -sid 0, -slang eng
 ID_SUBTITLE_ID=1
 ID_SID_1_NAME=Songs + Signs
 ID_SID_1_LANG=eng
 [mkv] Track ID 5: subtitles (S_TEXT/***) "Songs + Signs", -sid 1, -slang eng
 [mkv] Will play video track 1.
 Detected file format: Matroska
 VIDEO:  [avc1]  1920x1080  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
 Checking file /media/server/Complete/[Coalgirls] Higashi no Eden/[Coalgirls] Higashi no Eden ED [5C34AABF].mkv
 ID_VIDEO_ID=0
 ID_VID_0_NAME=Eden of the East ED
 [mkv] Track ID 1: video (V_MPEG4/ISO/AVC) "Eden of the East ED", -vid 0
 ID_AUDIO_ID=0
 ID_AID_0_NAME=5.1 FLAC
 ID_AID_0_LANG=jpn
 [mkv] Track ID 2: audio (A_FLAC) "5.1 FLAC", -aid 0, -alang jpn
 ID_AUDIO_ID=1
 ID_AID_1_NAME=5.1 FLAC
 ID_AID_1_LANG=eng
 [mkv] Track ID 3: audio (A_FLAC) "5.1 FLAC", -aid 1, -alang eng
 ID_SUBTITLE_ID=0
 ID_SID_0_NAME=English
 ID_SID_0_LANG=eng
 [mkv] Track ID 4: subtitles (S_TEXT/***) "English", -sid 0, -slang eng
 ID_SUBTITLE_ID=1
 ID_SID_1_NAME=Songs + Signs
 ID_SID_1_LANG=und
 [mkv] Track ID 5: subtitles (S_TEXT/***) "Songs + Signs", -sid 1, -slang und
 [mkv] Will play video track 1.
 Detected file format: Matroska
 VIDEO:  [avc1]  1920x1080  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
 Match for source 2: /media/server/Complete/[Coalgirls] Higashi no Eden/[Coalgirls] Higashi no Eden ED [5C34AABF].mkv
 Checking file /media/server/Complete/[Coalgirls] Higashi no Eden/[Coalgirls] Higashi no Eden OP [8366FFF0].mkv
 ID_VIDEO_ID=0
 ID_VID_0_NAME=Eden of the East OP
 [mkv] Track ID 1: video (V_MPEG4/ISO/AVC) "Eden of the East OP", -vid 0
 ID_AUDIO_ID=0
 ID_AID_0_NAME=5.1 FLAC
 ID_AID_0_LANG=jpn
 [mkv] Track ID 2: audio (A_FLAC) "5.1 FLAC", -aid 0, -alang jpn
 ID_AUDIO_ID=1
 ID_AID_1_NAME=5.1 FLAC
 ID_AID_1_LANG=eng
 [mkv] Track ID 3: audio (A_FLAC) "5.1 FLAC", -aid 1, -alang eng
 ID_SUBTITLE_ID=0
 ID_SID_0_NAME=English
 ID_SID_0_LANG=eng
 [mkv] Track ID 4: subtitles (S_TEXT/***) "English", -sid 0, -slang eng
 ID_SUBTITLE_ID=1
 ID_SID_1_NAME=Songs + Signs
 ID_SID_1_LANG=eng
 [mkv] Track ID 5: subtitles (S_TEXT/***) "Songs + Signs", -sid 1, -slang eng
 [mkv] Will play video track 1.
 Detected file format: Matroska
 VIDEO:  [avc1]  1920x1080  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
 Match for source 1: /media/server/Complete/[Coalgirls] Higashi no Eden/[Coalgirls] Higashi no Eden OP [8366FFF0].mkv
 ID_FILENAME=/media/server/Complete/[Coalgirls] Higashi no Eden/[Coalgirls] Higashi no Eden 01 [013B9B32].mkv
 ID_DEMUXER=mkv
 ID_VIDEO_FORMAT=avc1
 ID_VIDEO_BITRATE=0
 ID_VIDEO_WIDTH=1920
 ID_VIDEO_HEIGHT=1080
 ID_VIDEO_FPS=23.976
 ID_VIDEO_ASPECT=1.7778
 ID_AUDIO_FORMAT=fLaC
 ID_AUDIO_BITRATE=0
 ID_AUDIO_RATE=48000
 ID_AUDIO_NCH=6
 ID_START_TIME=0.00
 ID_LENGTH=1355.19
 ID_SEEKABLE=1
 ID_CHAPTERS=4
 [***] auto-open
 Opening video filter: [screenshot]
 ==========================================================================
 Forced video codec: coreavcwindows
 Opening video decoder: [dshow] DirectShow video codecs
 
 
 MPlayer interrupted by signal 11 in module: init_video_codec
 ID_SIGNAL=11
 - MPlayer crashed by bad usage of CPU/FPU/RAM.
   Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
   disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
 - MPlayer crashed. This shouldn't happen.
   It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
   gcc version. If you think it's MPlayer's fault, please read
   DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
   won't help unless you provide this information when reporting a possible bug.
 


Anyone can help me out?

---

### Post by ripps818 on 2010-12-07
> **GFUnforgiven said:**
> I installed CoreAVC just fine but there is a single file I can't seem to play anymore. The CRC matches so I'm sure its not broken and I was able to view it (with intense lag) before I installed CoreAVC.

Okay, according to your log your using the mplayer built-in coreavcwindows codec. To my knowledge, that only works when your using Windows. I don't think it's ever worked in Linux. This thread is devoted to patching and building a custom mplayer to use a program called dshowserver using the -vc coreserve.
I have a pre-built mplayer with dshowserver patches in my PPA.

Follow the directions at [http://launchpad.net/~ripps818/+archive/coreavc](http://launchpad.net/~ripps818/+archive/coreavc)

---

### Post by beew on 2010-12-08
Maybe I am doing something wrong, but it seems that coreAVC  uses  not less, but considerably more CPU cycles because of dshowserver.  But thanks ripps818 for the PPA, your version of mplayer does work a  lot better than the one in the repository even without coreAVC.

My mplayer configuration file doesn't  quite look like the one that was posted earlier in the thread. It looks like this

> # Write your default config options here!


[gnome-mplayer]
msglevel=all=5
vo=xv
#vc=coreserve,
ao=alsa

vf=eq2


There are no other vc option except for coreVAC which I have added and then commented out.

P.S. Why is this thread marked outdated while it is still active?

---

### Post by GFUnforgiven on 2010-12-09
> **ripps818 said:**
> Okay, according to your log your using the mplayer built-in coreavcwindows codec. To my knowledge, that only works when your using Windows. I don't think it's ever worked in Linux. This thread is devoted to patching and building a custom mplayer to use a program called dshowserver using the -vc coreserve.
I have a pre-built mplayer with dshowserver patches in my PPA.

Follow the directions at [http://launchpad.net/~ripps818/+archive/coreavc]("http://launchpad.net/%7Eripps818/+archive/coreavc")

That's strange then, it works with every other file other than this one.

EDIT: Nevermind, I unchecked the "Remember settings for all files" option and it worked. Thanks.

---

### Post by colo505 on 2010-12-21
Is CoreAVC superior to VDPAU?

---

### Post by ripps818 on 2010-12-21
> **colo505 said:**
> Is CoreAVC superior to VDPAU?
No, it's not even that much better than the default FFmpeg. It's mostly for people with old/slow computers that don't have access to vaapi/vdpau/xvmc.

---

### Post by okke on 2011-01-01
Can't seem to be able to change the settings of CoreAVC with ```
dshowserver -c CoreAVCDecoder.ax --config
``` I'm using the mplayer and dshowserver from [https://launchpad.net/~ripps818/+archive/coreavc](https://launchpad.net/~ripps818/+archive/coreavc).

---

### Post by ruegore on 2011-01-01
First of all, many many thanks to alannisota and Ripps. 720p plays decently well on my netbook and it's all thanks to you guys.

I had been using Ripps' PPA for some time now, but I recently noticed that files which use ordered chapters are now magically working. Thank you very much for this!!

Everything works well except for one thing; I can't figure out how to configure mplayer to downmix multichannel audio down to stereo. Whenever I need to playback a file with multichannel audio, I must play them from VLC, but then I lose the benefits of CoreAVC. :(

I use SMPlayer as my front end, and I make direct edits to my configuration file to get certain things working the way I want them, so I would really appreciate it if someone could explain what I must change in the config file to have mplayer downmix multichannel to stereo. Thank you!

---

### Post by trancephorm on 2011-01-02
I had the same problem with multichannel audio with some files, but it seems that it healed itself with some ripps mplayer update... be sure that you updated it.

---

### Post by ruegore on 2011-01-02
You're right! It is working now. Gosh, I wish I noticed that sooner.
Thanks again! :)

---

### Post by okke on 2011-01-04
Anyone else having problems configuring the codec using the ripps repository builds?

---

### Post by ruegore on 2011-01-05
I have no problem with the CoreCodec Configuration window. Seems to work properly with Wine.

What problem are you having?

---

### Post by okke on 2011-01-06
I can't apply the changes I make in the config dialog (apply button is disabled and if just I click OK, it doesn't save the chages).

---

### Post by Jason4108 on 2011-01-16
hey ripps I was wondering if it was possible to integrate rvm's Advanced SubStation Alpha (I can't say ".***" lol) mencoder patch ([http://smplayer.svn.sourceforge.net/viewvc/smplayer/mplayer-builds/patches/?pathrev=3495]("http://smplayer.svn.sourceforge.net/viewvc/smplayer/mplayer-builds/patches/?pathrev=3495")) into your builds. I'm using your builds with coreavc to do transcoding.

Thanks.

---

### Post by ripps818 on 2011-01-16
> **Jason4108 said:**
> hey ripps I was wondering if it was possible to integrate rvm's Advanced SubStation Alpha (I can't say ".***" lol) mencoder patch ([http://smplayer.svn.sourceforge.net/viewvc/smplayer/mplayer-builds/patches/?pathrev=3495]("http://smplayer.svn.sourceforge.net/viewvc/smplayer/mplayer-builds/patches/?pathrev=3495")) into your builds. I'm using your builds with coreavc to do transcoding.

Thanks.
The mplayer-build git source from Uoti Urpala that I use for my coreavc mplayer packages no longer supports mencoder. It hasn't been in the source since November. If there are still mencoder packages in my ppa, it's because of some old builds that haven't been cleaned out yet.

I'll see what I can do to remove them, but in the mean time, I recommend you get your mencoder package from elsewhere, as my PPA no longer supplies it.

---

### Post by Jason4108 on 2011-01-17
> **ripps818 said:**
> The mplayer-build git source from Uoti Urpala that I use for my coreavc mplayer packages no longer supports mencoder. It hasn't been in the source since November. If there are still mencoder packages in my ppa, it's because of some old builds that haven't been cleaned out yet.

I'll see what I can do to remove them, but in the mean time, I recommend you get your mencoder package from elsewhere, as my PPA no longer supplies it.

I got some mencoder builds from your ppa that allowed me to use coreavc with mencoder, if I got mencoder builds from elsewhere wouldn't coreavc not work?

---

### Post by ripps818 on 2011-01-17
> **Jason4108 said:**
> I got some mencoder builds from your ppa that allowed me to use coreavc with mencoder, if I got mencoder builds from elsewhere wouldn't coreavc not work?

You can't encode with coreavc, only decode. Dshowserver, which allows the use of coreavc, is only designed for playback. And as far as I understand the patches, it's only accessible from the decoding portion of mplayer's code. It doesn't even touch mencoder.

Are you sure it wasn't just falling back to the default ffmpeg encoders?

Coreavc is just an h.264 decoder. Conversely, you need an h.264 encoder to make videos it can playback. FFmpeg and x264 are able to encode h.264 video.

---

### Post by Jason4108 on 2011-01-17
> **ripps818 said:**
> You can't encode with coreavc, only decode. Dshowserver, which allows the use of coreavc, is only designed for playback. And as far as I understand the patches, it's only accessible from the decoding portion of mplayer's code. It doesn't even touch mencoder.

Are you sure it wasn't just falling back to the default ffmpeg encoders?

Coreavc is just an h.264 decoder. Conversely, you need an h.264 encoder to make videos it can playback. FFmpeg and x264 are able to encode h.264 video.

```
[mencoder] INFO  01:09:01.600 Starting mencoder -ss 0 -quiet test.mkv -quiet -quiet -oac lavc -of mpeg -quiet -quiet -mpegopts format=mpeg2:muxrate=500000:vbuf_size=1194:abuf_size=64 -ovc lavc -channels 2 -lavdopts debug=0:threads=2 -lavcopts autoaspect=1:vcodec=mpeg2video:acodec=ac3:abitrate=256:threads=2:keyint=1:vqscale=1:vqmin=2 -spuaa 3 -subcp cp1252 -subfont Arial -subfont-text-scale 3 -subfont-outline 2 -subfont-blur 1 -subpos 98 -aid 1 -sid 0 -quiet -quiet -ofps 24000/1001 -quiet -quiet -vc coreserve -lavdopts fast -quiet -mc 0 -noskip -af lavcresample=48000 -srate 48000 -o /tmp/javaps3media/mencoder1295255341545
[mencoder] INFO  01:09:01.615 Reading pipe: /tmp/javaps3media/mencoder1295255341545
[mencoder] DEBUG 01:09:01.615 Opening file /tmp/javaps3media/mencoder1295255341545 for reading...
[mencoder] INFO  01:09:01.820 Attaching thread: mencoder
[Thread-34] DEBUG 01:09:01.821 MEncoder UNKNOWN-4.4.3 (C) 2000-2010 MPlayer Team
[Thread-34] DEBUG 01:09:01.821 success: format: 0  data: 0x0 - 0xe52c3905
[Thread-34] DEBUG 01:09:01.821 [mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[Thread-34] DEBUG 01:09:01.821 [mkv] Track ID 2: audio (A_AAC), -aid 0, -alang jpn
[Thread-34] DEBUG 01:09:01.821 [mkv] Track ID 3: audio (A_AAC), -aid 1, -alang jpn
[Thread-34] DEBUG 01:09:01.821 [mkv] Track ID 4: subtitles (S_TEXT/***), -sid 0, -slang eng
[Thread-34] DEBUG 01:09:01.821 [mkv] Will play video track 1.
[Thread-34] DEBUG 01:09:01.821 Matroska file format detected.
[Thread-34] DEBUG 01:09:01.821 VIDEO:  [avc1]  1920x1080  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
[Thread-34] DEBUG 01:09:01.822 [V] filefmt:31  fourcc:0x31637661  size:1920x1080  fps:23.976  ftime:=0.0417
[Thread-34] DEBUG 01:09:01.822 ==========================================================================
[Thread-34] DEBUG 01:09:01.822 Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
[Thread-34] DEBUG 01:09:01.822 AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
[Thread-34] DEBUG 01:09:01.822 Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
[Thread-34] DEBUG 01:09:01.822 ==========================================================================
[Thread-34] DEBUG 01:09:01.822 PACKET SIZE: 2048 bytes, deltascr: 884
[Thread-34] DEBUG 01:09:01.822 Opening video filter: [expand osd=1]
[Thread-34] DEBUG 01:09:01.822 Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
[Thread-34] DEBUG 01:09:01.822 ==========================================================================
[Thread-34] DEBUG 01:09:01.822 Forced video codec: coreserve
[Thread-34] DEBUG 01:09:01.822 Opening video decoder: [dshowserver] DirectShowServer video codecs
[Thread-34] DEBUG 01:09:01.822 [PP] Using codec's postprocessing, max q = 4.
[Thread-34] DEBUG 01:09:01.822 Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
[Thread-34] DEBUG 01:09:01.822 videocodec: libavcodec (1920x1080 fourcc=3267706d [mpg2])
[Thread-34] DEBUG 01:09:01.822 [VE_LAVC] Using constant qscale = 1.000000 (VBR).
[Thread-34] DEBUG 01:09:01.822 Starting wine dshowserver.exe
[Timer-3] DEBUG 01:09:01.829 Buffered Space: 0 bytes / inputs: 0
[Thread-31] DEBUG 01:09:01.905 fixme:thread:SetThreadIdealProcessor (0x60): stub
[Thread-31] DEBUG 01:09:01.905 fixme:thread:SetThreadIdealProcessor (0x64): stub
[Thread-34] DEBUG 01:09:01.913 dshowserver --codec CoreAVCDecoder.ax --size 1920x1080 --guid 09571a4b-f1fe-4c60-9760de6d310c7c31 --fourc 0x31637661 --bits 12 --outfmt 0x32315659 --pid 13953 --id d3850740 --numpages 10 --port 18105 &
[Thread-34] DEBUG 01:09:01.914 Found DirectShow filterSelected video codec: [coreserve] vfm: dshowserver (CoreAVC DShow H264 decoder - http://corecodec.org/)
[Thread-34] DEBUG 01:09:01.914 ==========================================================================
[Thread-31] DEBUG 01:09:01.915 [ac3 @ 0xb5d6e0]No channel layout specified. The encoder will guess the layout, but it might be incorrect.
[Thread-31] DEBUG 01:09:01.915 Limiting audio preload to 0.4s.
[Thread-31] DEBUG 01:09:01.915 Increasing audio density to 4.
[Thread-34] DEBUG 01:09:02.286 Writing header...
[Timer-3] DEBUG 01:09:03.829 Buffered Space: 657408 bytes / inputs: 0
[Timer-3] DEBUG 01:09:05.829 Buffered Space: 4012032 bytes / inputs: 0
[New I/O server worker #1-1] DEBUG 01:09:07.700 Suspend Read: readCount=0 / writeCount=8292352
[Timer-3] DEBUG 01:09:07.830 Buffered Space: 8486912 bytes / inputs: 1
[Timer-3] DEBUG 01:09:09.829 Buffered Space: 12457984 bytes / inputs: 1
[New I/O server worker #1-1] DEBUG 01:09:10.201 Resume Read: readCount=0 / writeCount=12922880
[New I/O server worker #1-1] DEBUG 01:09:10.206 Sent to socket: Accept-Ranges: bytes
[New I/O server worker #1-1] DEBUG 01:09:10.206 Sent to socket: Connection: keep-alive
[New I/O server worker #1-1] DEBUG 01:09:10.206 Sent to socket: Content-Type: video/mpeg
[New I/O server worker #1-1] DEBUG 01:09:10.206 Sent to socket: Server: Linux-amd64-2.6.32-26-generic, UPnP/1.0, PMS/1.20.414-SB11
[New I/O server worker #1-1] DEBUG 01:09:10.587 Suspend Read: readCount=12599296 / writeCount=13598720
[New I/O server worker #1-1] DEBUG 01:09:11.088 Resume Read: readCount=12599296 / writeCount=14864384
[New I/O server worker #1-1] DEBUG 01:09:11.111 Suspend Read: readCount=13869056 / writeCount=14864384
[New I/O server worker #1-1] DEBUG 01:09:11.611 Resume Read: readCount=13869056 / writeCount=16906240
[New I/O server worker #1-1] DEBUG 01:09:11.695 Suspend Read: readCount=16146432 / writeCount=17145856
[Timer-3] DEBUG 01:09:11.830 Buffered Space: 1720320 bytes / inputs: 1
[New I/O server worker #1-1] DEBUG 01:09:12.195 Resume Read: readCount=16146432 / writeCount=19187712
[Timer-3] DEBUG 01:09:13.829 Buffered Space: 7321599 bytes / inputs: 1
[Timer-3] DEBUG 01:09:15.829 Buffered Space: 10831871 bytes / inputs: 1
[Timer-3] DEBUG 01:09:17.829 Buffered Space: 11395071 bytes / inputs: 1
[Thread-10] DEBUG 01:09:18.252 Receiving a M-SEARCH from [192.168.10.198:4491]
[Thread-10] DEBUG 01:09:18.253 Sending this reply [192.168.10.198:4491]: HTTP/1.1 200 OK<CRLF>CACHE-CONTROL: max-age=1200<CRLF>DATE: Mon, 17 Jan 2011 09:09:18 GMT<CRLF>LOCATION: http://192.168.10.182:5001/description/fetch<CRLF>SERVER: Linux-amd64-2.6.32-26-generic, UPnP/1.0, PMS/1.20.414-SB11<CRLF>ST: upnp:rootdevice<CRLF>EXT: <CRLF>USN: uuid:46d00021-c173-3e60-8baf-2c35da39de03::upnp:rootdevice<CRLF>Content-Length: 0<CRLF><CRLF>
[Thread-10] DEBUG 01:09:18.253 Receiving a M-SEARCH from [192.168.10.198:4491]
[Thread-10] DEBUG 01:09:18.253 Sending this reply [192.168.10.198:4491]: HTTP/1.1 200 OK<CRLF>CACHE-CONTROL: max-age=1200<CRLF>DATE: Mon, 17 Jan 2011 09:09:18 GMT<CRLF>LOCATION: http://192.168.10.182:5001/description/fetch<CRLF>SERVER: Linux-amd64-2.6.32-26-generic, UPnP/1.0, PMS/1.20.414-SB11<CRLF>ST: upnp:rootdevice<CRLF>EXT: <CRLF>USN: uuid:46d00021-c173-3e60-8baf-2c35da39de03::upnp:rootdevice<CRLF>Content-Length: 0<CRLF><CRLF>
[Timer-3] DEBUG 01:09:19.829 Buffered Space: 9359359 bytes / inputs: 1
[Timer-3] DEBUG 01:09:21.829 Buffered Space: 7485439 bytes / inputs: 1
[Thread-32] DEBUG 01:09:23.198 freeMemory: 46441672
[Thread-32] DEBUG 01:09:23.198 totalMemory: 122224640
[Thread-32] DEBUG 01:09:23.198 maxMemory: 715849728
[Thread-32] DEBUG 01:09:23.198 Extending buffer to 419430400
[Timer-3] DEBUG 01:09:23.829 Buffered Space: 8220671 bytes / inputs: 1
[Thread-32] DEBUG 01:09:23.834 Done extending
[Timer-3] DEBUG 01:09:25.829 Buffered Space: 12062719 bytes / inputs: 1
[Timer-3] DEBUG 01:09:27.829 Buffered Space: 16089087 bytes / inputs: 1

```

I'm transcoding, so its using coreavc for the decoding them encoding with some other codec

---

### Post by ripps818 on 2011-01-17
Now, I'm not entirely familiar with mencoder, but that does indeed look like it's using it to encode. This is news to me because I've never heard of anybody using it to encode on linux.

Regardless, it wasn't my decision to remove mencoder from mplayer-build.git. So, I can't really fix that. Besides, does encoding using coreavc carry any benefit over x264/ffmpeg?

EDIT:
just read your transcoding edit. Okay, so if that's the case than it doesn't really matter too much. Coreavc/ffmpeg give the same output, coreavc just does it a little bit faster. Using ffmpeg for the decoding portion over coreavc shouldn't change the quality of the transcode, as far as I understand it.

---

### Post by Jason4108 on 2011-01-17
oops duplicate post, the forums are super lagging for me right now, sorry about that.

---

### Post by Jason4108 on 2011-01-17
Are you sure I'm using coreavc for encoding? from my understanding mencoder must decode the input before encoding.

the server I'm using is a dual core so transcoding HD content can sometimes be a little more then the server can handle and it seems like decoding with coreavc is a little quicker.

can you please not remove the old mencoder builds form your repository? I'll try some other mencoder builds to see if there was much of a performance difference, but I may want to go back to your builds.

---

### Post by ripps818 on 2011-01-17
> **Jason4108 said:**
> Are you sure I'm using coreavc for encoding? from my understanding mencoder must decode the input before encoding.

the server I'm using is a dual core so transcoding HD content can sometimes be a little more then the server can handle and it seems like decoding with coreavc is a little quicker.

can you please not remove the old mencoder builds form your repository? I'll try some other mencoder builds to see if there was much of a performance difference, but I may want to go back to your builds.

Sorry, I already flagged the packages for deletion. You can protest to Uroti, but I don't think he wanted to have to deal with it anymore.

If you really want to use coreavc with mencoder, I recommend that you try and compile your own version. The patches should be available from the coreavc-for-linux's svn repository.

---

### Post by Jason4108 on 2011-01-17
aww :( ok I'll try to follow one of the compile guides, I've had bad luck with compiling myself before haha, thanks anyway

---

### Post by bazil.xxl on 2011-01-28
Hi,
I just install mplayer and dshowserver from [https://launchpad.net/~ripps818/+archive/coreavc]("https://launchpad.net/%7Eripps818/+archive/coreavc")

I install and copy CoreAVCDecoder.ax to /usr/share/dshowserver.

Tests past (dshowserver -c CoreAVCDecoder.ax):
```

Starting wine dshowserver.exe
No id specified, assuming test mode
Using default width  for CoreAVCDecoder.ax: 1280
Using default height for CoreAVCDecoder.ax: 720
Using default fourcc for CoreAVCDecoder.ax: 0x34363248
Using default outfmt for CoreAVCDecoder.ax: 0x30323449
Using default outbit for CoreAVCDecoder.ax: 12
Using default GUID   for CoreAVCDecoder.ax: 09571a4b-f1fe-4c60-9760de6d310c7c31
Opening device (port is 0)
len: 992
ProductVersion: 2.0.0
fixme:thread:SetThreadIdealProcessor (0x5c): stub
fixme:thread:SetThreadIdealProcessor (0x60): stub
Decoder supports the following YUV formats: YUY2 UYVY YV12 I420 
Decoder is capable of YUV output (flags 0x2b)
Setting fmt
Starting
Initialization is complete

```But when I try play some video with mplayer -vc coreserve I got this error:
```
MPlayer interrupted by signal 13 in module: uninit_vcodec
```Here is mplayer output:
```

MPlayer UNKNOWN-4.4.5 (C) 2000-2011 MPlayer Team
161 audio & 352 video codecs
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

XXXXXXXXXXXXXXXXXXXXXX.1080p.Bluray.CZ.EN.x264-CBGB.mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_DTS), -aid 0, -alang eng
[mkv] Track ID 3: audio (A_AC3), -aid 1, -alang cze
[mkv] Track ID 4: subtitles (S_TEXT/UTF8), -sid 0, -slang cze
[mkv] Track ID 5: subtitles (S_TEXT/UTF8), -sid 1, -slang slo
[mkv] Will play video track 1.
Detected file format: Matroska
VIDEO:  [avc1]  1920x816  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
[gl] using extended formats. Use -vo gl:nomanyfmts if playback fails.
==========================================================================
Forced video codec: coreserve
Opening video decoder: [dshowserver] DirectShowServer video codecs
[PP] Using codec's postprocessing, max q = 4.
Movie-Aspect is 2.35:1 - prescaling to correct movie aspect.
VO: [gl] 1920x816 => 1920x816 Planar YV12 
[ASPECT] Warning: No suitable new res found!
[ASPECT] Warning: No suitable new res found!
dshowserver --codec CoreAVCDecoder.ax --size 1920x816 --guid 09571a4b-f1fe-4c60-9760de6d310c7c31 --fourc 0x31637661 --bits 12 --outfmt 0x32315659 --pid 16267 --id fc8e97a0 --numpages 10 --port 36296 &
Starting wine dshowserver.exe
Opening device (port is 36296)
len: 992
ProductVersion: 2.0.0
fixme:thread:SetThreadIdealProcessor (0x6c): stub
fixme:thread:SetThreadIdealProcessor (0x70): stub
Decoder supports the following YUV formats: YUY2 UYVY YV12 I420 
Found DirectShow filterSelected video codec: [coreserve] vfm: dshowserver (CoreAVC DShow H264 decoder 1.3 for x86 - http://corecodec.org/)
EINPROGRESS in connect() - selecting
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 1536.0 kbit/100.00% (ratio: 192000->192000)
Selected audio codec: [ffdca] afm: ffmpeg (FFmpeg DTS)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
Got illegal command 0
Decoder is capable of YUV output (flags 0x2b)
Setting fmt
Starting
Initialization is complete
Using socket based mutex
Dshowserver Connected to host
A:   0.0 V:   0.0 A-V:  0.004 ct:  0.000   0/  0 ??% ??% ??,?% 0 0 


MPlayer interrupted by signal 13 in module: check_framedrop
A:   0.0 V:   0.0 A-V:  0.004 ct:  0.000   0/  0 ??% ??% ??,?% 0 0 


MPlayer interrupted by signal 13 in module: uninit_vcodec

```Pls can you help me?

---

### Post by comrobo on 2011-02-09
i have the same issue, mplayer worked fine with coreavc a few weeks ago but now crashes and show this log:

[HTML]

p, li { white-space: pre-wrap; } /usr/bin/mplayer -noquiet -nofs -nomouseinput -vc coreserve, -sub-fuzziness 1 -identify -slave -vo xv -ao alsa -nokeepaspect -framedrop -nodr -double -input nodefault-bindings:conf=/dev/null -stop-xscreensaver -wid 73400667 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/jo7/.config/smplayer/styles.*** -fontconfig -font Ubuntu -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -subpos 100 -volume 100 -nocache -osdlevel 0 -vf-add screenshot -slices -channels 2 -af scaletempo -softvol -softvol-max 200 /home/jo7/Videos/Cinnamon Chasers - Two hours time (Official Music Video) Rel.mp4
 
 MPlayer UNKNOWN-4.4.5 (C) 2000-2011 MPlayer Team
 mplayer: could not connect to socket
 mplayer: No such file or directory
 Failed to open LIRC support. You will not be able to use your remote control.
 Terminal type `unknown' is not defined.
 
 Playing /home/jo7/Videos/Cinnamon Chasers - Two hours time (Official Music Video) Rel.mp4.
 Detected file format: QuickTime/MPEG-4/Motion JPEG 2000 format (libavformat)
 ID_VIDEO_ID=0
 [lavf] stream 0: video (h264), -vid 0
 ID_AUDIO_ID=0
 ID_AID_0_LANG=und
 [lavf] stream 1: audio (aac), -aid 0, -alang und
 VIDEO:  [avc1]  1920x1080  24bpp  25.000 fps  2401.3 kbps (293.1 kbyte/s)
 Clip info:
  major_brand: mp42
 ID_CLIP_INFO_NAME0=major_brand
 ID_CLIP_INFO_VALUE0=mp42
  minor_version: 0
 ID_CLIP_INFO_NAME1=minor_version
 ID_CLIP_INFO_VALUE1=0
  compatible_brands: isommp42
 ID_CLIP_INFO_NAME2=compatible_brands
 ID_CLIP_INFO_VALUE2=isommp42
  creation_time: 2010-10-26 21:25:49
 ID_CLIP_INFO_NAME3=creation_time
 ID_CLIP_INFO_VALUE3=2010-10-26 21:25:49
 ID_CLIP_INFO_N=4
 ID_FILENAME=/home/jo7/Videos/Cinnamon Chasers - Two hours time (Official Music Video) Rel.mp4
 ID_DEMUXER=lavfpref
 ID_VIDEO_FORMAT=avc1
 ID_VIDEO_BITRATE=2401312
 ID_VIDEO_WIDTH=1920
 ID_VIDEO_HEIGHT=1080
 ID_VIDEO_FPS=25.000
 ID_VIDEO_ASPECT=1.7778
 ID_AUDIO_FORMAT=MP4A
 ID_AUDIO_BITRATE=128008
 ID_AUDIO_RATE=44100
 ID_AUDIO_NCH=2
 ID_START_TIME=0.00
 ID_LENGTH=244.64
 ID_SEEKABLE=1
 ID_CHAPTERS=0
 [***] auto-open
 Opening video filter: [screenshot]
 ==========================================================================
 Forced video codec: coreserve
 Opening video decoder: [dshowserver] DirectShowServer video codecs
 [PP] Using codec's postprocessing, max q = 4.
 Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
 ID_VIDEO_ASPECT=1.7778
 [swscaler @ 0x887ec80]using unscaled yuv420p -> rgb24 special converter
 VO: [xv] 1920x1080 => 1920x1080 Planar YV12 
 Starting wine dshowserver.exe
 fixme:thread:SetThreadIdealProcessor (0x64): stub
 fixme:thread:SetThreadIdealProcessor (0x68): stub
 dshowserver --codec CoreAVCDecoder.ax --size 1920x1080 --guid 09571a4b-f1fe-4c60-9760de6d310c7c31 --fourc 0x31637661 --bits 12 --outfmt 0x32315659 --pid 3611 --id b77c3730 --numpages 10 --port 9897 &
 Found DirectShow filterSelected video codec: [coreserve] vfm: dshowserver (CoreAVC DShow H264 decoder - http://corecodec.org/)
 ==========================================================================
 ID_VIDEO_CODEC=coreserve
 ==========================================================================
 Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
 AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16001->176400)
 ID_AUDIO_BITRATE=128008
 ID_AUDIO_RATE=44100
 ID_AUDIO_NCH=2
 Selected audio codec: [ffaac] afm: ffmpeg (FFmpeg AAC (MPEG-2/MPEG-4 Audio))
 ==========================================================================
 AO: [alsa] 44100Hz 2ch s16le (2 bytes per sample)
 ID_AUDIO_CODEC=ffaac
 [Mixer] No hardware mixing, inserting volume filter.
 Starting playback...
 Opening device (port is 9897)
 
 len: 992
 
 ProductVersion: 2.0.0
 
 Decoder supports the following YUV formats: YUY2 UYVY YV12 I420 
 
 Decoder is capable of YUV output (flags 0x2b)
 
 Setting fmt
 
 Starting
 
 Initialization is complete
 
 Using socket based mutex
 
 Dshowserver Connected to host
 
 EINPROGRESS in connect() - selecting
 
 Got illegal command 0
 
 
 
 
 MPlayer interrupted by signal 13 in module: check_framedrop
 ID_SIGNAL=13
 
 
 
 MPlayer interrupted by signal 13 in module: uninit_vcodec
 Destroying filterID_SIGNAL=13

[/HTML]

---

### Post by penn919 on 2011-03-24
hmm, well looks like I might as well post mine here as well...

I've recently found out about a way to use Core AVC inside ubuntu and followed the following guides to get it up and running:

[http://code.google.com/p/coreavc-for-linux/wiki/DshowserverInstall](http://code.google.com/p/coreavc-for-linux/wiki/DshowserverInstall)

[http://code.google.com/p/coreavc-for-linux/wiki/MplayerInstallation](http://code.google.com/p/coreavc-for-linux/wiki/MplayerInstallation)

There were a few peculiarities during the installation process, but I personally thought I got it right based on the rough similarities between what was described in the step-by-step guide and what I was seeing on my screen, but I guess I must of gone wrong somewhere. Hopefully someone here can help me sort it out.

As of now whenever I attempt to play a video using this:

```
mplayer -vc coreserve /media/7E04971F0496D98B/striped/"Crysis 2 The Wall Trailer (1080p).mp4"
```

I get this:

```
Warning unknown option vo_driver at line 2
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /media/7E04971F0496D98B/striped/Crysis 2 The Wall Trailer (1080p).mp4.
libavformat file format detected.
[lavf] Audio stream found, -aid 0
[lavf] Video stream found, -vid 1
VIDEO:  [avc1]  1920x1080  24bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Forced video codec: coreserve
Cannot find codec matching selected -vo and video format 0x31637661.
Read DOCS/HTML/en/codecs.html!
==========================================================================
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
FAAD: compressed input bitrate missing, assuming 128kbit/s!
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A: 126.6 (02:06.5) of 126.9 (02:06.9)  2.1% 

Exiting... (End of file)
penn@ubuntu:~$
```

I was able to hear the audio, but I didn't get any video at all. The codec of the video file is  H.264 / AVC, so it should be supported by coreavc right? Any ideas on what I could've possibly done wrong?

I really hope I can get this resolved because it'd be great if I could successfully use my core avc license in ubuntu because WMP 12 seems to do just fine playing just about any HD video format in windows 7...definitely can't say the same about any player in linux, so hopefully this can work somehow.

---

### Post by comrobo on 2011-03-25
[penn919]("http://ubuntuforums.org/member.php?u=1240405") This happened to me too, and I realized that:

if you look the video properties with mediainfo in the video section shows:

Video
ID                               : 2
Format                           : AVC
Format/Info                      : Advanced Video Codec
Format profile                   : Baseline@L3.1
......etc



Video
ID                               : 1
Format                           : AVC
Format/Info                      : Advanced Video Codec
Format profile                   : High@L3.1
......etc


and the videos with ID=1 coreserve works but with ID=2 only audio.
I recodec video with ID=2 with avidemux and H.264 / AVC (the same codec .mp4 format) and the ID turn to ID=1 and now coreserve display video and audio.

this is very strange because i had ubuntu 10.10 and coreserve works with any video and any ID (later i had the problem mencioned in my last post)

so, now i have ubuntu 11.04 and happens the ID issue.(maybe is ID there are many other parameters in video properties but i just but only noticed that)


sorry my English
Greetings
JO

---

### Post by penn919 on 2011-03-25
> **comrobo said:**
> [penn919]("http://ubuntuforums.org/member.php?u=1240405") This happened to me too, and I realized that:

if you look the video properties with mediainfo in the video section shows:

Video
ID                               : 2
Format                           : AVC
Format/Info                      : Advanced Video Codec
Format profile                   : Baseline@L3.1
......etc



Video
ID                               : 1
Format                           : AVC
Format/Info                      : Advanced Video Codec
Format profile                   : High@L3.1
......etc


and the videos with ID=1 coreserve works but with ID=2 only audio.
I recodec video with ID=2 with avidemux and H.264 / AVC (the same codec .mp4 format) and the ID turn to ID=1 and now coreserve display video and audio.

this is very strange because i had ubuntu 10.10 and coreserve works with any video and any ID (later i had the problem mencioned in my last post)

so, now i have ubuntu 11.04 and happens the ID issue.(maybe is ID there are many other parameters in video properties but i just but only noticed that)


sorry my English
Greetings
JO

I looked in my video properties, but I didn't see that info. This is all that I see:

[IMG]https://lh6.googleusercontent.com/_0oR-59-USHo/TY1TOdtj1oI/AAAAAAAAMqM/x-7dKJJ-cds/s800/mp4-video.jpg[/IMG]

Were you using a special  program?

---

### Post by comrobo on 2011-03-27
Mediainfo
 [http://mediainfo.sourceforge.net/en](http://mediainfo.sourceforge.net/en)   

here is their repository ( is available to 10.10)

 [https://launchpad.net/~shiki/+archive/mediainfo]("https://launchpad.net/%7Eshiki/+archive/mediainfo")  

Greetings.

PD: i use the windows version under wine (came with the pack necesary to run subtitle workshop), the ubuntu version is a little different,
so you must go to the "view" tab and change to txt (or html, I don't remember) view to have the same display that I showed in my last post.

---

### Post by runesvend on 2011-05-01
Hey all

Just upgraded to the current mplayer version in the PPA (3:2.0+git20110422.5079c04-0ubuntu1~ripps1) and now exiting fullscreen mode doesn't work by pressing the 'f' key.
When I have "fs=true" specified in my .mplayer/config, exiting fullscreen mode doesn't work, but if I comment out that line in my config, then mplayer starts in windowed (non-fullscreen) mode and toggling fullscreen mode on and off works fine.

Any ideas what could be wrong? The following message appears on the console every time I press 'f' when in fullscreen mode (or so it I think, since I can't actually see the terminal window when mplayer is playing video in fullscreen mode, but the more I press the 'f' key the more of these messages are present in the terminal when I exit mplayer):

```
[ASPECT] Warning: No suitable new res found!
[ASPECT] Warning: No suitable new res found!
V:   2.6   0/  0 10% 32%  0.0% 0 0 

```

EDIT: Here's the full output of mplayer:

```
rune@runescomp:~$ mplayer '/media/thesafe/Video/Test Samples/Basketball 60fps 1080p 5000kbps.mkv' 
MPlayer2 UNKNOWN (C) 2000-2011 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /media/thesafe/Video/Test Samples/Basketball 60fps 1080p 5000kbps.mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Will play video track 1.
Detected file format: Matroska
VIDEO:  [avc1]  1920x1088  24bpp  59.940 fps    0.0 kbps ( 0.0 kbyte/s)
Load subtitles in /media/thesafe/Video/Test Samples/
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
[***] auto-open
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Asking decoder to use 4 threads if supported.
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
Audio: no sound
Starting playback...
V:   0.0   0/  0 ??% ??% ??,?% 0 0 
Movie-Aspect is 1.76:1 - prescaling to correct movie aspect.
VO: [xv] 1920x1088 => 1920x1088 Planar YV12  [fs]
[ASPECT] Warning: No suitable new res found!
[ASPECT] Warning: No suitable new res found!
V:   0.9   0/  0 15% 34%  0.0% 0 0 
[ASPECT] Warning: No suitable new res found!
[ASPECT] Warning: No suitable new res found!
V:   1.4   0/  0 16% 33%  0.0% 0 0 
[ASPECT] Warning: No suitable new res found!
[ASPECT] Warning: No suitable new res found!
V:   1.5   0/  0 16% 32%  0.0% 0 0 
[ASPECT] Warning: No suitable new res found!
[ASPECT] Warning: No suitable new res found!
V:   2.0   0/  0 13% 33%  0.0% 0 0 

Exiting... (Quit)

```

And my config file is now attached

---

### Post by jsevi83 on 2011-05-07
The latest build of mplayer2 is not working with gnome-mplayer. This is what I get in the terminal:

ERROR: Unknown profile 'gnome-m'.

So it looks like a profile parsing error, notice how it looks chopped. This was not happening with svn20110422

---

### Post by ripps818 on 2011-05-07
> **jsevi83 said:**
> The latest build of mplayer2 is not working with gnome-mplayer. This is what I get in the terminal:

ERROR: Unknown profile 'gnome-m'.

So it looks like a profile parsing error, notice how it looks chopped. This was not happening with svn20110422

I noticed it too, it can easily be fixed by shortening the profiles name. But you should file a bug at mplayer2's bug tracker [http://devel.mplayer2.org/wiki/Bugs](http://devel.mplayer2.org/wiki/Bugs)

---

### Post by sysabod on 2011-05-24
> **Bachstelze said:**
> Install [FONT=monospace]zlib1g-dev[/FONT].
thanks, it really helps !

---

### Post by kamitsukai on 2011-06-16
Hi I'm on debian testing and I'm tying to patch the makefile but I get this error

```
patch -p0 < /home/carl/mplayer-with-coreavc/coreavc-for-linux/mplayer/dshowserver.patch
patching file libmpcodecs/vd.c
Hunk #1 succeeded at 40 (offset -3 lines).
Hunk #2 succeeded at 72 with fuzz 2 (offset -3 lines).
patching file Makefile
Hunk #1 succeeded at 20 with fuzz 2.
Hunk #2 FAILED at 530.
Hunk #3 FAILED at 909.
2 out of 3 hunks FAILED -- saving rejects to file Makefile.rej
patching file libmpcodecs/vd_dshowserver.c
patching file libmpcodecs/timeout_sem.c
patching file libmpcodecs/timeout_sem.h

```

there's a bug report for it and a fix but it's just that I don't understand what the guys on about:( so if someone could elaborate on what I need to do? please:KS

> Ok guys, I succeed patching makefile and vd.c files by myself by hand.
As said, the new revision change makefile command.
the patch want to place "	      libmpcodecs/vd_dshowserver.c \"
before  "              $(SRCS_COMMON-yes)"
In the new file, It might be place at the 526. You all can do it by yourselves.
And in the new /libmpcodecs/vd.c file, the ligne to add after
"  extern const vd_functions_t mpcodecs_vd_dshow;" is 
"  extern const vd_functions_t mpcodecs_vd_dshowserver;", where the patch wanted to add "extern vd_functions_t mpcodecs_vd_dshowserver;" which is now a wrong call.
Hoping all that can help you all, even to make a new correct dshowserver.patch

[http://code.google.com/p/coreavc-for-linux/issues/detail?id=110](http://code.google.com/p/coreavc-for-linux/issues/detail?id=110)

---

### Post by beew on 2011-06-16
I don't use coreavc, but just want to say Ripps' build of mplayer is superb. Works much better than other versions including the one put out by the MOTU team (actually that one doesn't even work with VDPAU in Natty) Wonder what your secrete is. :)

Thank you for the great work!


As for coreavc I don't think it really improve anything even on Computers without vdpau. Whatever cpu gain in mplayer is more than offset by running dshowserver in WINE, so in the end cpu usage is actually higher. I have tested it briefly on a few older PCs and decided that it wouldn't really worth the troubles.

---

### Post by ripps818 on 2011-06-16
> **beew said:**
> I don't use coreavc, but just want to say Ripps' build of mplayer is superb. Works much better than other versions including the one put out by the MOTU team (actually that one doesn't even work with VDPAU in Natty) Wonder what your secrete is. :)

Thank you for the great work!


As for coreavc I don't think it really improve anything even on Computers without vdpau. Whatever cpu gain in mplayer is more than offset by running dshowserver in WINE, so in the end cpu usage is actually higher. I have tested it briefly on a few older PCs and decided that it wouldn't really worth the troubles.

The secret is that it's mplayer2, Uoti Urpala's fork of mplayer. 

I've tweaked the dshowserver patches over time to keep working, but I don't think I'll take the time to fix them if they fail to patch in the future. The h.264 codec is just as good, if not better than the CoreAVC now. There's not much reason to continue keeping these builds working, especially since the Coreavc-for-Linux project seems dead now.

---

### Post by beew on 2011-06-17
> **ripps818 said:**
>  The h.264 codec is just as good, if not better than the CoreAVC now. There's not much reason to continue keeping these builds working, especially since the Coreavc-for-Linux project seems dead now.

I figured. Terminate the coreavc support by all means, but please keep the mplayer2 builds coming. Thanks again. :)

---

### Post by rdantas on 2012-01-21
Hi,

I'm a newbie in ubuntu. Every time I type 

```
cd dshowserver 
make
sudo cp dshowserver registercodec /usr/local/bin
```I get the following error:

```
/usr/bin/ld: cannot find -lwine
collect2: ld returned 1 exit status
winegcc: i686-linux-gnu-gcc failed
make: ** [dshowserver] Erro 2 

```Can anyone help me?
Thanks.

---

### Post by dmt0 on 2012-01-22
> **rdantas said:**
> Hi,

I'm a newbie in ubuntu. Every time I type 

```
cd dshowserver 
make
sudo cp dshowserver registercodec /usr/local/bin
```I get the following error:

```
/usr/bin/ld: cannot find -lwine
collect2: ld returned 1 exit status
winegcc: i686-linux-gnu-gcc failed
make: ** [dshowserver] Erro 2 

```Can anyone help me?
Thanks.


Do this:
sudo apt-get install wine

---

### Post by c-m on 2012-02-08
So what is the best way to go for a netbook - Dell Mini9 or Aspire One?

Most of my content (on the server) is 720p - the netbook really struggles with files in the MKV format. Isn't coreavc meant to be the fastest the decoder out there?

---

### Post by c-m on 2012-02-08
Confused as to which guide i should be installing. I want a full gui

This guide below seems simple, but there's no gui:
[https://launchpad.net/~ripps818/+archive/coreavc](https://launchpad.net/~ripps818/+archive/coreavc)

---

### Post by andrew.46 on 2012-02-08
> **c-m said:**
>  I want a full gui

Try installing a frontend such as SMPlayer or UMPlayer.

---

### Post by c-m on 2012-02-08
> **andrew.46 said:**
> Try installing a frontend such as SMPlayer or UMPlayer.

To work with coreavc?

---

### Post by c-m on 2012-02-09
Does this mean that mplayer used coreavc?

Either way it was far too slow. I don't understand why. A netbook should be capable of playing 720p video.


```
Forced video codec: coreserve
Opening video decoder: [dshowserver] DirectShowServer video codecs
[PP] Using codec's postprocessing, max q = 4.
Movie-Aspect is 1.84:1 - prescaling to correct movie aspect.
VO: [xv] 1280x696 => 1280x696 Planar YV12 
Colorspace details not fully supported by selected vo.
dshowserver --codec CoreAVCDecoder.ax --size 1280x696 --guid 09571a4b-f1fe-4c60-9760de6d310c7c31 --fourc 0x31637661 --bits 12 --outfmt 0x32315659 --pid 7877 --id b77609a0 --numpages 10 --port 24528 &
Starting wine dshowserver.exe
Opening device (port is 24528)
len: 996
ProductVersion: 2.5.5
fixme:thread:SetThreadIdealProcessor (0x70): stub
fixme:thread:SetThreadIdealProcessor (0x74): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x61ef3c,0x00000000), stub!
Decoder supports the following YUV formats: YUY2 UYVY YV12 I420 
Found DirectShow filterSelected video codec: [coreserve] vfm: dshowserver (CoreAVC DShow H264 decoder - http://corecodec.org/)
==========================================================================
==========================================================================
EINPROGRESS in connect() - selecting
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 1536.0 kbit/100.00% (ratio: 192000->192000)
Selected audio codec: [ffdca] afm: ffmpeg (FFmpeg DTS)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
A:   0.1 V:   0.1 A-V:  0.024 ct:  0.000   0/  0 ??% ??% ??,?% 0 0 
Decreasing video pts: 0.042000 < 0.125000
A:   0.3 V:   0.1 A-V:  0.174 ct:  0.000   0/  0 ??% ??% ??,?% 0 0 
Decreasing video pts: 0.083000 < 0.125000
A:   5.4 V:   2.0 A-V:  3.379 ct:  0.003   0/  0 84% 19% 162.1% 50 0 


           ************************************************
           **** Your system is too SLOW to play this!  ****
           ************************************************

Possible reasons, problems, workarounds:
- Most common: broken/buggy _audio_ driver
  - Try -ao sdl or use the OSS emulation of ALSA.
  - Experiment with different values for -autosync, 30 is a good start.
- Slow video output
  - Try a different -vo driver (-vo help for a list) or try -framedrop!
- Slow CPU
  - Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
    e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.
- Broken file
  - Try various combinations of -nobps -ni -forceidx -mc 0.
- Slow media (NFS/SMB mounts, DVD, VCD etc)
  - Try -cache 8192.
- Are you using -cache to play a non-interleaved AVI file?
  - Try -nocache.
Read DOCS/HTML/en/video.html for tuning/speedup tips.
If none of this helps you, read DOCS/HTML/en/bugreports.html.

Seek now V:  73.4 A-V: -0.014 ct:  0.004   0/  0 31% 10% 37.7% 1165 0 
Seek now V:  86.2 A-V:  0.121 ct:  0.002   0/  0 53% 11% 23.5% 2 0 
Seek now V: 100.9 A-V:  1.414 ct:  0.004   0/  0 38% 16% 182.2% 24 0 
Seek now V: 118.0 A-V:  0.224 ct:  0.002   0/  0 ??% ??% ??,?% 1 0 
Seek now V: 128.5 A-V:  0.349 ct:  0.002   0/  0 ??% ??% ??,?% 4 0 
Seek now V: 149.0 A-V:  0.263 ct:  0.003   0/  0 30% 15% 57.0% 18 0 
Seek now V: 161.5 A-V:  0.116 ct:  0.002   0/  0 37% 14% 78.4% 13 0 
A: 192.5 V: 185.3 A-V:  7.255 ct:  0.005   0/  0 30% 17% 315.9% 86 0 
[***] PlayResX undefined, setting to 384
Destroying filter A-V: 33.387 ct:  0.004   0/  0 29% 17% 203.8% 578 0 

Exiting... (Quit)
 
```

---

### Post by ripps818 on 2012-02-12
According to what I see, you were indeed using CoreAVC. But coreavc is slower than standard libav or ffmpeg these days anyway, so I don't see the point. The only reason it might be faster on Windows is because it can use CUDA on nvidia cards (maybe OpenCL too) for decoding.

In fact, I would assume that no netbook should be able to decode 720p, the CPU just isn't designed for that. And if it's advertised as saying it can, then it must be using some form of Graphics hardware decoding such as with Nvidia VDPAU or Intel VA-API. If the netbook doesn't support either of those options, than it was probably some other hardware decoding that isn't available to Linux that I know of.

If you want to coax a few more cpu cycles in mplayer, make sure to be using these flags:
```
-lavdopts fast:skiploopfilter=all
```

Also, depending on you graphics card and drivers, different video outputs may be faster. Try using:
```
-vo xv
-vo gl:yuv2
-vo gl:yuv=2:ati-hack:force-pbo -dr
-vo gl2
```

---

### Post by c-m on 2012-02-18
> **ripps818 said:**
> According to what I see, you were indeed using CoreAVC. But coreavc is slower than standard libav or ffmpeg these days anyway, so I don't see the point. 


I'm not sure about that, playback, although still slow, is faster when using mplayer with coreavc for me than with whatever mplayer uses as default.

When i first had my aspire one, there where plenty of youtube videos and reviews where people had enjoyed success playing 720p videos in windows with coreavc.

I'm going to buy a broadcom crystal HD card anyway, so this is just for fun.

---

### Post by footspa on 2012-03-09
An update of Mplayer2 was made available today so I proceeded to do that. Now Mplayer won't play any kind of files. 

After re-installing Mplayer2 I get the error message "Mplayer interrupted by signal 4 in module: demux_open". Initially I got the error message "Mplayer interrupted by signal 4 in module: init_video_code".

---

### Post by ripps818 on 2012-03-09
> **footspa said:**
> An update of Mplayer2 was made available today so I proceeded to do that. Now Mplayer won't play any kind of files. 

After re-installing Mplayer2 I get the error message "Mplayer interrupted by signal 4 in module: demux_open". Initially I got the error message "Mplayer interrupted by signal 4 in module: init_video_code".

The mplayer2 packages I have in my coreavc-for-ubuntu PPA seem to work fine here in 12.04 beta. All my h.264 videos work using vdpau,xv,gl. Just using the built-in libav codecs to decode the video.

From the looks of the error it's having trouble finding a codec or demuxer for  the video your trying to play. Can you give me more details about your mplayer and what files your trying to play? Where are you installing your mplayer2 from? What version of Ubuntu are you using?

If this is a CoreAVC problem, I can't help you. The coreavc-for-linux project is dead and I've been doing my best to keep the patches working despite that. But I'm not a programmer and I can't fix it if stops working.

Also, it would probably be wise to contact the mplayer2 developer, uau, at #mplayer2 on irc.ubuntu.com.

---

### Post by imsety on 2012-03-22
Hi, I just tried to install mplayer from the PPA but I got the following error:

```
sudo apt-get install mplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 mplayer : Depends: mplayer2 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

Any idea what the problem might be?

---

### Post by Zorael on 2012-03-23
```
sudo apt-get install mplayer

[...]

The following packages have unmet dependencies:
 mplayer : Depends: mplayer2 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```
I think ripps has been packaging mplayer2 for some time now and some way along the road renamed the package to reflect this. Just install **[mplayer2](apt://mplayer2)** instead.

This is a good example of where apt-get falls short while aptitude might have done the trick. When dependency errors show up aptitude will try to offer solutions (eg. "don't install mplayer, install mplayer2 instead"), often several such, whereas apt-get merely concludes it's an unresolvable dependency and exits with errors. On the other hand, apt-get seems to be better at keeping track of automatically installed packages and tags them for removal when they're no longer needed (when using autoremove).

So when you get errors like this, you may want to try the same command but with aptitude. Add the argument **-P** to force it to always ask for confirmation before proceeding. Do note that apt-get autoremove won't work well on removing automatically installed packages it didn't install itself, so extensively mixing the use of the two is not a good idea over time.

The aptitude in 12.04 is broken on multiarch platforms (like amd64) and basically only works when installing packages, else I normally recommend the use of aptitude for *everything* besides updating package lists. It still works fine in 11.10 though, so feel free.

-----

As always, *huge* thanks to you for packaging this, ripps181.

---

### Post by ShareBuntu on 2012-03-25
Any idea whether mplayer2 + CoreAVC 3.0.1 work together using the CoreAVC-for-Ubuntu method? It doesn't work for me. I've got the rvn PPA enabled for SMPlayer as well as the ripps818 one, so I'm not sure if there's a conflict.

All installs fine, there just isn't any mention of CoreAVC in the SMPlayer logs.

---

### Post by ripps818 on 2012-03-25
> **ShareBuntu said:**
> Any idea whether mplayer2 + CoreAVC 3.0.1 work together using the CoreAVC-for-Ubuntu method? It doesn't work for me. I've got the rvn PPA enabled for SMPlayer as well as the ripps818 one, so I'm not sure if there's a conflict.

All installs fine, there just isn't any mention of CoreAVC in the SMPlayer logs.

It'll probably never work. Dshowserver was made by the Coreavc-for-LInux project, and they're dead now. It would probably have to be rewritten to make it compatible, but I'm not a programmer, so unless you or someone you know wants to take up a challenge, don't expect it to ever get fixed.

---

### Post by ShareBuntu on 2012-03-25
> **ripps818 said:**
> It'll probably never work. Dshowserver was made by the Coreavc-for-LInux project, and they're dead now. It would probably have to be rewritten to make it compatible, but I'm not a programmer, so unless you or someone you know wants to take up a challenge, don't expect it to ever get fixed.

Well that's interesting news. What's the current state of affairs for video playback on Linux? Should I just stick with mplayer2 from your repository? Is there a configuration optimization guide out there somewhere?

---

### Post by ripps818 on 2012-03-25
> **ShareBuntu said:**
> Well that's interesting news. What's the current state of affairs for video playback on Linux? Should I just stick with mplayer2 from your repository? Is there a configuration optimization guide out there somewhere?

mplayer2 with it's static libav (used to be ffmpeg) is pretty good these days, I've been wanting to try some unstable optimizations. It might grab another 1-2% improvement on video decoding, but it could also make it crash on some hardware.

As for settings, always add "-lavdopts fast=1:skiploopfilter=all" for general speedup.

---

