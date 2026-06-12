---
title: "HOWTO: Compile the latest VLC (0.8.6)"
date: 2006-12-22
forum: Outdated Tutorials &amp; Tips
---

### Post by lucis on 2006-12-22
How to install the latest VLC release (0.8.6). [VLC](http://www.videolan.org/vlc/) is a multimedia player that I prefer over Ubuntu's default Totem for various reasons. VLC's support for DVDs, for example, seems to be a lot more complete than Totem's. Edgy's repo contains 0.8.6, but it's an earlier snapshot rather than the final release. This has only been tested on Edgy. I don't see why it wouldn't work on Dapper, so don't be afraid to try. 

This is my first guide and I am relatively new to Linux and software compilation. If you spot any mistakes, please point them out. 

**Edit: Instructions for compiling and installing the VLC Mozilla/Firefox plugin below.**

First let's download the VLC source and extract it into our home directory.

```
wget http://downloads.videolan.org/pub/videolan/vlc/0.8.6/vlc-0.8.6.tar.bz2
tar xvf vlc-0.8.6.tar.bz2
```

Next make sure you have the Multiverse and Universe repos enabled. We need to satisfy a *few* dependencies. ;)

```
sudo apt-get install libwxgtk2.6-dev libdvbpsi4-dev libmpeg2-4-dev libmpeg3-dev libmad0-dev libasound2-dev libesd0-dev x11proto-video-dev libdvdnav-dev liba52-0.7.4-dev libflac-dev libfreetype6-dev libid3tag0-dev libogg-dev libpng12-dev libspeex-dev libtheora-dev libvorbis-dev libxml2-dev zlib1g-dev build-essential automake1.9 libtool libx11-dev libdvdread-dev libdvdplay0-dev libdvdnav-dev libdvdcss2 libfaad2-dev libebml-dev libmatroska-dev libmp4v2-dev libpostproc-dev libavformat-dev ffmpeg libavcodec-dev libvcdinfo-dev libdts-dev libslp-dev gettext liblivemedia-dev libsdl1.2-dev libdv4-dev libnotify-dev libcdio-dev libavc1394-dev libcddb2-dev
```

Now get a quick cup of tea while all of these install

Back? Good. Next we'll compile VLC. :D

Let's change to the VLC source directory

```
cd vlc-0.8.6
```

And run the configure script

```

./configure --prefix=/usr/local --enable-libtool --enable-dvdread --enable-vcdx  --enable-faad --enable-real --enable-flac --enable-realrtsp --enable-snapshot --enable-live555 --enable-dv --enable-theora --enable-esd 

```

The "--prefix=/usr/local" option will install VLC in /usr/local. I prefer having my compiled apps put here just so there is no confusion between the repo's version and the newer version. 

Now run ```
make
```

When compiling is finished, type ```
sudo make install
``` which will install the binaries. Remember that VLC was installed in /usr/local, so if you run VLC from your Applications menu you will be running the old version (assuming you had VLC already installed) . You will have to run ```
/usr/local/bin/wxvlc
``` to run your version. You can edit VLC's menu entry to point at your binary rather than Ubuntu's. 

**[SIZE="3"]If you want to compile and install the VLC Mozilla/Firefox plugin:[/SIZE]**

Add mozilla-dev to the needed dependencies. 

```
sudo apt-get install mozilla-dev
```

And add --enable-mozilla to the configure options

```
./configure --prefix=/usr/local --enable-libtool --enable-dvdread --enable-vcdx  --enable-faad --enable-real --enable-flac --enable-realrtsp --enable-snapshot --enable-live555 --enable-dv --enable-theora --enable-esd --enable-mozilla
```

Compile normally. Next, link the plugin library to your Mozilla/Firefox plugins directory:

```
sudo ln -s /usr/local/lib/mozilla/plugins/*.* /usr/lib/firefox/plugins
```

Contributing users:
seelk
cor2y

References:
[http://nanocrew.net/2005/09/01/compiling-vlc/](http://nanocrew.net/2005/09/01/compiling-vlc/)
[http://ubuntuforums.org/showthread.php&t=319421&highlight=compiling+vlc](http://ubuntuforums.org/showthread.php&t=319421&highlight=compiling+vlc)
[http://developers.videolan.org/vlc/index.html](http://developers.videolan.org/vlc/index.html)

---

### Post by zorglab on 2006-12-26
Very nice howto. Compiling it now. ;)

May I just suggest to use ```
sudo checkinstall
``` instead of ```
sudo make install
``` (assuming you have installed the package "checkinstall" from universe). This will create a (quick and dirty) debian package which makes it easy to uninstall afterwards with the standard apt tools (apt-get, dpkg, synaptic, ...).

---

### Post by lucis on 2006-12-26
> **zorglab said:**
> Very nice howto. Compiling it now. ;)

May I just suggest to use ```
sudo checkinstall
``` instead of ```
sudo make install
``` (assuming you have installed the package "checkinstall" from universe). This will create a (quick and dirty) debian package which makes it easy to uninstall afterwards with the standard apt tools (apt-get, dpkg, synaptic, ...).

I've used checkinstall before and I agree on its benefits. I didn't include it in the howto though because VLC is being installed into /usr/local, which would be separate from the repository's version. If a user ever wanted to go back to the repo's VLC, they can still run it with no problems since the repo's binaries weren't modified. Likewise if they ever wanted to replace their compiled binary with a newer version they could just install the new version into /usr/local and it would overwrite the previous one. Checkinstall has lots of benefits but it's so easy to modify the installation I didn't bother with it. :)

---

### Post by NTolerance on 2006-12-26
I heard something about a backport being available.  Is that true?  If so, which is the preferred method?

---

### Post by cor2y on 2006-12-26
thanks for the how to but i have to ask is there anything else we need to enable wmv/wma/flv (flash video) playback?

Edit:
Just compile it no problems there.
However video playback for wmv and flv were not compiled in although the audio part is there.

---

### Post by lucis on 2006-12-26
> **cor2y said:**
> thanks for the how to but i have to ask is there anything else we need to enable wmv/wma/flv (flash video) playback?

I tried to include just about everything you could possibly ever want to play in the configuration. As far as I know, ffmpeg/libav* takes care of Windows Media codecs. Windows Media plays on my compile, haven't tried flv though.

---

### Post by seelk on 2006-12-26
Is there a VLC plugin for Firefox?

---

### Post by lucis on 2006-12-26
> **seelk said:**
> Is there a VLC plugin for Firefox?

Yep. :) You can install the one from the Universe repository with

```
sudo apt-get install mozilla-plugin-vlc
```

---

### Post by seelk on 2006-12-26
> **lucis said:**
> Yep. :) You can install the one from the Universe repository with

```
sudo apt-get install mozilla-plugin-vlc
```

Is that the latest 0.8.6 plugin (if there's such a thing)?

---

### Post by lucis on 2006-12-26
> **seelk said:**
> Is that the latest 0.8.6 plugin (if there's such a thing)?

No, in Edgy that's the earlier snapshot. I didn't think about compiling the Moz plugin as well but I may add details on that now that you mention it.

---

### Post by seelk on 2006-12-26
> **lucis said:**
> No, in Edgy that's the earlier snapshot. I didn't think about compiling the Moz plugin as well but I may add details on that now that you mention it.

That'll be nice because I'm looking for an MPlayer replacement (including the plugin).

---

### Post by lucis on 2006-12-26
I added information on building the Moz plugin. :)

> **cor2y said:**
> thanks for the how to but i have to ask is there anything else we need to enable wmv/wma/flv (flash video) playback?

Edit:
Just compile it no problems there.
However video playback for wmv and flv were not compiled in although the audio part is there.

:( I don't know how to fix it. WMV works for me, but then again I'm not running on a clean install and I could have installed a library you didn't.

---

### Post by seelk on 2006-12-26
> **lucis said:**
> I tried to include just about everything you could possibly ever want to play in the configuration. As far as I know, ffmpeg/libav* takes care of Windows Media codecs. Windows Media plays on my compile, haven't tried flv though.

I already have the w32codecs installed...  do I need to uninstall them before following this guide?

---

### Post by lucis on 2006-12-26
> **seelk said:**
> I already have the w32codecs installed...  do I need to uninstall them before following this guide?

I don't know. I don't *think* so... I'm sorry I can't be of more support, I'm new at this :(

---

### Post by cor2y on 2006-12-26
i tried a clean build (removed vlc and all the dev fully) this time i was able to build and install by pointing to an svn build of ffmpeg i did.
I got mp4, x264, xvid ,mpeg1,dvd, mpeg2, mov, playback when it came to the wmv3 and flv same problem no video output but audio.
funny thing there is video and audio playback in ffplay so it should have worked i'm probably missing something.

---

### Post by kliljedahl on 2006-12-31
I'm a real newbie ( less than two weeks) so please bear with me. I get the message "E: Type 'sudo' is not known on line 1 in source list /etc/apt/sources.list
E: The list of sources could not be read." when I type in (actually copy  and paste) "sudo apt-get install libwxgtk2.6-dev libdvbpsi4-dev libmpeg2-4-dev libmpeg3-dev libmad0-dev libasound2-dev libesd0-dev x11proto-video-dev libdvdnav-dev liba52-0.7.4-dev libflac-dev libfreetype6-dev libid3tag0-dev libogg-dev libpng12-dev libspeex-dev libtheora-dev libvorbis-dev libxml2-dev zlib1g-dev build-essential automake1.9 libtool libx11-dev libdvdread-dev libdvdplay0-dev libdvdnav-dev libdvdcss2 libfaad2-dev libebml-dev libmatroska-dev libmp4v2-dev libpostproc-dev libavformat-dev ffmpeg libavcodec-dev libvcdinfo-dev libdts-dev libslp-dev gettext liblivemedia-dev libsdl1.2-dev libdv4-dev libnotify-dev libcdio-dev libavc1394-dev libcddb2-dev" 

I would like to get the VLC up and running since Totem won't play anything and I used VLC in Windoze and really like it.

---

### Post by lucis on 2006-12-31
> **kliljedahl said:**
> I'm a real newbie ( less than two weeks) so please bear with me. I get the message "E: Type 'sudo' is not known on line 1 in source list /etc/apt/sources.list
E: The list of sources could not be read." when I type in (actually copy  and paste) "sudo apt-get install libwxgtk2.6-dev libdvbpsi4-dev libmpeg2-4-dev libmpeg3-dev libmad0-dev libasound2-dev libesd0-dev x11proto-video-dev libdvdnav-dev liba52-0.7.4-dev libflac-dev libfreetype6-dev libid3tag0-dev libogg-dev libpng12-dev libspeex-dev libtheora-dev libvorbis-dev libxml2-dev zlib1g-dev build-essential automake1.9 libtool libx11-dev libdvdread-dev libdvdplay0-dev libdvdnav-dev libdvdcss2 libfaad2-dev libebml-dev libmatroska-dev libmp4v2-dev libpostproc-dev libavformat-dev ffmpeg libavcodec-dev libvcdinfo-dev libdts-dev libslp-dev gettext liblivemedia-dev libsdl1.2-dev libdv4-dev libnotify-dev libcdio-dev libavc1394-dev libcddb2-dev" 

I would like to get the VLC up and running since Totem won't play anything and I used VLC in Windoze and really like it.

Are you entering anything else besides that command? It sounds like you typed "sudo apt-get sudo apt-get <all of the dependencies>".

---

### Post by kliljedahl on 2006-12-31
That's exactly how it was put in. Copied and pasted from the first post. Of course, none of the later ones work either since that failed.

---

### Post by lucis on 2006-12-31
> **kliljedahl said:**
> That's exactly how it was put in. Copied and pasted from the first post. Of course, none of the later ones work either since that failed.


I don't know, maybe someone else can help. Sorry. :(

---

### Post by kliljedahl on 2007-01-01
Is there something I need to first add to the /etc/apt/sources.list? That's a root only edit. If there is, how would I do that? Thanks for your patience.

---

### Post by kd7swh on 2007-01-15
I am building 0.8.6a and was getting a strange error, something to the effect of: 
> python... doc/Makefile.in could not create.
One of the strangest things I have seen while trying to compile vlc. 
Anyway I think it way have been a problem with the package. I tried the tar.gz instead of the tar.bz2 and it is making now.

I too pointed to my ffmpeg svn, so I hope all goes well with the extra codecs. :)

---

### Post by michu on 2007-01-15
Hey, i got at the end this message

> checking libraw1394/raw1394.h usability... no
checking libraw1394/raw1394.h presence... no
checking for libraw1394/raw1394.h... no
configure: error: cannot find libraw1394 headers


 when i started this :

>  ./configure .....   

What have i to do ?

Thanks michu

---

### Post by LuftFan on 2007-01-22
Hello

I'm using this howto to install vlc.  Once I do this:

sudo apt-get install libwxgtk2.6-dev libdvbpsi4-dev libmpeg2-4-dev libmpeg3-dev libmad0-dev libasound2-dev libesd0-dev x11proto-video-dev libdvdnav-dev liba52-0.7.4-dev libflac-dev libfreetype6-dev libid3tag0-dev libogg-dev libpng12-dev libspeex-dev libtheora-dev libvorbis-dev libxml2-dev zlib1g-dev build-essential automake1.9 libtool libx11-dev libdvdread-dev libdvdplay0-dev libdvdnav-dev libdvdcss2 libfaad2-dev libebml-dev libmatroska-dev libmp4v2-dev libpostproc-dev libavformat-dev ffmpeg libavcodec-dev libvcdinfo-dev libdts-dev libslp-dev gettext liblivemedia-dev libsdl1.2-dev libdv4-dev libnotify-dev libcdio-dev libavc1394-dev libcddb2-dev

I get 
Reading package lists...
Building dependency tree...
Reading state information...

and then the error message :

E: Couldn't find package libwxgtk2.6-dev

Can someone help me here - I thought following the howto will be problem free.

I'm on 6.10 32-bit.

Thanks

LuftFan

---

### Post by Didjit on 2007-01-23
Not sure if anybody has seen this. If you are on i386, there is a repo for the backport of Feisty's VLC.

[http://home.eng.iastate.edu/~superm1/dists/edgy/vlc-0.8.6/](http://home.eng.iastate.edu/~superm1/dists/edgy/vlc-0.8.6/)

Didjit

---

### Post by willwarner on 2007-02-21
> **cor2y said:**
> i tried a clean build (removed vlc and all the dev fully) this time i was able to build and install by pointing to an svn build of ffmpeg i did.
I got mp4, x264, xvid ,mpeg1,dvd, mpeg2, mov, playback when it came to the wmv3 and flv same problem no video output but audio.
funny thing there is video and audio playback in ffplay so it should have worked i'm probably missing something.

I just got the exact same problem. Fresh install on Dapper Drake, and a wmv plays audio but not video. Running it from the command line allows me to see the error:
```
$/usr/local/bin/wxvlc
VLC media player 0.8.6 Janus
[00000544] main decoder error: no suitable decoder module for fourcc `WMV3'.
VLC probably does not support this sound or video format.
```

Oddly, trying to run it in totem gives the error "Video codec 'MS WMV 9 (win32)' is not handled." That was why I thought it was WMV9 and went from VLC 0.8.4 to 0.8.6.

"ffmpeg -i file.wmv file.mpg" produces this:
```
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --extra-cflags=-fomit-frame-pointer -DRUNTIME_CPUDETECT --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
  built on Nov 24 2005 10:19:02, gcc: 4.0.3 20051121 (prerelease) (Ubuntu 4.0.2-4ubuntu3)
[wmv3 @ 0x8336308]This decoder is not supposed to produce picture. Dont report this as a bug!
[wmv3 @ 0x8336308]Profile 1:
frmrtq_postproc=7, bitrtq_postproc=12
LoopFilter=0, MultiRes=0, FastUVMV=0, Extended MV=0
Rangered=0, VSTransform=0, Overlap=1, SyncMarker=0
DQuant=1, Quantizer mode=0, Max B frames=0

Seems that stream 1 comes from film source: 1000.00 (1000/1) -> 30.00 (30/1)
Input #0, asf, from '/home/james/Video 7.wmv':
  Duration: 00:01:59.4, start: 2.000000, bitrate: 883 kb/s
  Stream #0.0: Audio: wmav2, 44100 Hz, stereo, 96 kb/s
  Stream #0.1: Video: wmv3, yuv420p, 640x480, 1000.00 fps
Output #0, mpeg, to '7.mpg':
  Stream #0.0: Video: mpeg1video, yuv420p, 640x480, 30.00 fps, q=2-31, 200 kb/s
  Stream #0.1: Audio: mp2, 44100 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.0 -> #0.1
[wmv3 @ 0x8336308]This decoder is not supposed to produce picture. Dont report this as a bug!
[wmv3 @ 0x8336308]Profile 1:
frmrtq_postproc=7, bitrtq_postproc=12
LoopFilter=0, MultiRes=0, FastUVMV=0, Extended MV=0
Rangered=0, VSTransform=0, Overlap=1, SyncMarker=0
DQuant=1, Quantizer mode=0, Max B frames=0
Press [q] to stop encoding
[wmv3 @ 0x8336308]concealing 1200 DC, 1200 AC, 1200 MV errors
[wmv3 @ 0x8336308]VOP DQuant info
[wmv3 @ 0x8336308]concealing 1200 DC, 1200 AC, 1200 MV errors
Segmentation fault
```

"This decoder is not supposed to produce picture" ? OK, but how /do/ I produce picture from such a file? I've googled around, but haven't yet found the solution. ffplay produces very similar errors, and also fails.

Anyone have any idea why ffmpeg isn't showing it, alone or with VLC 0.8.6? Or whether there's another video player I could put on ubuntu that would play the video? Thanks!

---

### Post by willwarner on 2007-02-21
Ah, found a fix! Installed Xine and libxine, and the w32codecs as described in [http://ubuntuforums.org/showthread.php?t=362046](http://ubuntuforums.org/showthread.php?t=362046) , and the wmv plays in xine. I'm still a VLC loyalist, though, because its UI is MUCH better. :D

---

### Post by caffienda on 2007-02-25
During the "make" step, I was getting this message through the compiling, here is a part that I managed to copy from the terminal:

:GetNodePtr(const long unsigned int&) const':
/usr/include/wx-2.6/wx/image.h:123:[COLOR="Red"] warning: dereferencing type-punned pointer will break strict-aliasing rules[/COLOR]

does this "warning" mean anything?

---

### Post by Ob1 on 2007-02-25
Does anyone know a solution for the panel(s) showing in full screen mode?

---

### Post by ubu-for on 2007-03-09
> **lucis said:**
> First let's download the VLC source and extract it into our home directory.

```
wget http://downloads.videolan.org/pub/videolan/vlc/0.8.6/vlc-0.8.6.tar.bz2
tar xvf vlc-0.8.6.tar.bz2
```

Next make sure you have the Multiverse and Universe repos enabled. We need to satisfy a *few* dependencies. ;)

```
sudo apt-get install libwxgtk2.6-dev libdvbpsi4-dev libmpeg2-4-dev libmpeg3-dev libmad0-dev libasound2-dev libesd0-dev x11proto-video-dev libdvdnav-dev liba52-0.7.4-dev libflac-dev libfreetype6-dev libid3tag0-dev libogg-dev libpng12-dev libspeex-dev libtheora-dev libvorbis-dev libxml2-dev zlib1g-dev build-essential automake1.9 libtool libx11-dev libdvdread-dev libdvdplay0-dev libdvdnav-dev libdvdcss2 libfaad2-dev libebml-dev libmatroska-dev libmp4v2-dev libpostproc-dev libavformat-dev ffmpeg libavcodec-dev libvcdinfo-dev libdts-dev libslp-dev gettext liblivemedia-dev libsdl1.2-dev libdv4-dev libnotify-dev libcdio-dev libavc1394-dev libcddb2-dev
```

Now get a quick cup of tea while all of these install

Back? Good. Next we'll compile VLC. :D

Let's change to the VLC source directory

```
cd vlc-0.8.6
```

And run the configure script

```

./configure --prefix=/usr/local --enable-libtool --enable-dvdread --enable-vcdx  --enable-faad --enable-real --enable-flac --enable-realrtsp --enable-snapshot --enable-live555 --enable-dv --enable-theora --enable-esd 

```

The "--prefix=/usr/local" option will install VLC in /usr/local. I prefer having my compiled apps put here just so there is no confusion between the repo's version and the newer version. 

Now run ```
make
```

When compiling is finished, type ```
sudo make install
``` which will install the binaries. Remember that VLC was installed in /usr/local, so if you run VLC from your Applications menu you will be running the old version (assuming you had VLC already installed) . You will have to run ```
/usr/local/bin/wxvlc
``` to run your version. You can edit VLC's menu entry to point at your binary rather than Ubuntu's.

Your guide works for [VLC 0.9.0](http://ubuntuforums.org/showthread.php?t=380303), too! :D

---

### Post by ubu-for on 2007-03-11
> **lucis said:**
> Remember that VLC was installed in /usr/local, so if you run VLC from your Applications menu you will be running the old version (assuming you had VLC already installed) . You will have to run ```
/usr/local/bin/wxvlc
``` to run your version.

Everytime I compile VLC with your guide, the new version replaces the old one.

```
$ wxvlc
VLC media player 0.8.6a Janus
```

How can I change that? I would like to install VLC 0.8.6a and 0.9.0.

THX!

---

### Post by Hugo64 on 2007-11-15
Hello,
I can build VLC from the source, but see the problem, trying to  open rtp stream:
./vlc -vvv udp:@:1234
It seems that VLC executable that I built from source can't load 'ts' demuxer module:
I don't see this problem with binary distribution installed from 'Synaptic Package Manager'. Any idea what the problem might be?

Thank you ,

[00000535] main input debug: creating statistics handler
[00000535] main input debug: `udp:@:1234' gives access `udp' demux `' path `@:1234'
[00000535] main input debug: creating demux: access='udp' demux='' path='@:1234'
[00000537] main demuxer debug: looking for access_demux module: 0 candidates
[00000537] main demuxer warning: no access_demux module matched "udp"
[00000535] main input debug: creating access 'udp' path='@:1234'
[00000538] main access debug: looking for access2 module: 6 candidates
[00000538] access_udp access debug: opening server=:0 local=:1234
[00000538] main access debug: net: connecting to '[]:0@[]:1234'
[00000538] main access debug: looking for network module: 1 candidate
[00000538] main access debug: using network module "ipv6"
[00000538] main access debug: removing module "ipv6"
[00000538] main access debug: using access2 module "access_udp"
[00000539] main private debug: pre buffering
[00000538] access_udp access debug: detected TS over RTP
[00000538] access_udp access debug: RTP: prebuffered 17 packets
[00000535] main input debug: creating demux: access='udp' demux='ts' path='@:1234'
[00000540] main demuxer debug: looking for demux2 module: 0 candidates
[00000540] main demuxer error: no demux2 module matched "ts"
[00000535] main input error: no suitable demux module for `udp/ts://@:1234'

---

### Post by SuperBo on 2008-03-16
When I type make, there is a error:
```
demux.c:38:25: error: avformat.h: No such file or directory
In file included from demux.c:41:
ffmpeg.h:44: error: expected declaration specifiers or ‘...’ before ‘AVCodecContext’
ffmpeg.h:44: error: expected declaration specifiers or ‘...’ before ‘AVCodec’
ffmpeg.h:50: error: expected declaration specifiers or ‘...’ before ‘AVCodecContext’
ffmpeg.h:50: error: expected declaration specifiers or ‘...’ before ‘AVCodec’
ffmpeg.h:85: error: expected declaration specifiers or ‘...’ before ‘AVFrame’
make[6]: *** [libffmpeg_plugin_la-demux.lo] Error 1
make[6]: Leaving directory `/home/superbo/vlc-0.8.6e/modules/codec/ffmpeg'
make[5]: *** [all-modules] Error 1
make[5]: Leaving directory `/home/superbo/vlc-0.8.6e/modules/codec/ffmpeg'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/superbo/vlc-0.8.6e/modules/codec'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/superbo/vlc-0.8.6e/modules/codec'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/superbo/vlc-0.8.6e/modules'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/superbo/vlc-0.8.6e'
make: *** [all] Error 2
```
How can i fix this error, please help me.

---

