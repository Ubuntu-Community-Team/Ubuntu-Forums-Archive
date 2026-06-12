---
title: "installing from source"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by BetterSense on 2008-11-26
I tried to use dvd::rip to encode a DVD and it wouldn't let me grab subtitles because it said I needed something for transcode, plus it encoded with xvid even though I said to use h.264. So I checked and the versions of transcode and dvd::rip I have installed are older than the current stable releases. I figured getting the latest and greatest was probably the first place to start.

So I went to transcode's website and downloaded the tarball.
I extracted it.
I cd'd to it
I ran ./configure and it complains like so:

```
...

...lots of stuff...

libdv                          no
libquicktime                   no
lzo                            no
a52                            no
libmpeg3                       no
libxml2                        no
mjpegtools                     no
sdl                            no
libfame                        no
imagemagick                    no
libjpeg                        no
bsdav                          no
iconv                          yes

ERROR: requirement failed: cannot link against libavcodec
libavcodec can be found in the following packages:
  FFmpeg  http://www.ffmpeg.org/

ERROR: requirement failed: cannot compile mpeg2dec/mpeg2.h
mpeg2dec/mpeg2.h can be found in the following packages:
  mpeg2dec  http://libmpeg2.sourceforge.net/

ERROR: requirement failed: cannot link against libmpeg2
libmpeg2 can be found in the following packages:
  mpeg2dec  http://libmpeg2.sourceforge.net/

ERROR: option '--enable-lame' failed: cannot link against libmp3lame
libmp3lame can be found in the following packages:
  lame  http://www.mp3dev.org/

ERROR: option '--enable-libdvdread' failed: cannot link against libdvdread
libdvdread can be found in the following packages:
  libdvdread  http://www.dtek.chalmers.se/groups/dvd/downloads.shtml

ERROR: option '--enable-libjpeg' failed: cannot compile jpeglib.h
jpeglib.h can be found in the following packages:
  jpeg  ftp://ftp.uu.net/graphics/jpeg/

ERROR: option '--enable-libjpeg' failed: cannot link against libjpeg
libjpeg can be found in the following packages:
  jpeg  ftp://ftp.uu.net/graphics/jpeg/


Please see the INSTALL file in the top directory of the
transcode sources for more information about building
transcode with this configure script.

chaz@brutus:/media/JBWELD/transcode-1.0.6$ sudo apt-get install ffmpeg
Reading package lists... Done
Building dependency tree
Reading state information... Done
ffmpeg is already the newest version.
ffmpeg set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 238 not upgraded.

```

---

### Post by halitech on 2008-11-26
chances are, its going to complain because the versions that the newer version of transcode was compiled against was the newer versions of the dependencies.

second
> 0 upgraded, 0 newly installed, 0 to remove and [color="red"]238 not upgraded.[/color]

you may want to do your updates

---

### Post by oldos2er on 2008-11-26
Those are dependencies needed for transcode to compile properly. You should be able to find and install them from Synaptic Package Manager.

---

### Post by BetterSense on 2008-11-26
> Those are dependencies needed for transcode to compile properly. You should be able to find and install them from Synaptic Package Manager.

I tried to apt-get some of them, and in one case it said it was already the newest version, and in another case (libavcodec I think) it said could not find package. I'll try with synaptic later. I'm also running updates.

---

### Post by jemate18 on 2008-11-26
a lot of dependency problems......


:)

---

### Post by aeiah on 2008-11-26
if you have no luck you could try different software, like acidrip for example.

---

### Post by BetterSense on 2008-11-26
You know it's very curious that k9copy has never ever worked for me. I tried it last year some time when I first started using ubuntu and it totally ran, appeared as if it was going to work, but just didn't. I tried it just yesterday, fresh install from the hardy repos and it still....beautiful gui, very easy to use, let you choose all kinds of cropping your video, choosing audio options, and appeared as if it was going to work, then just didn't. No output. Basically, the inverse of mplayer.

---

### Post by mc4man on 2008-11-26
In many cases what your missing is the -dev packages of what's listed.

You could go a long way to getting what you need by running (including basic build tools

```
sudo apt-get build-dep transcode
```

---

### Post by BetterSense on 2008-11-26
cool I ran that and it's downloading a bunch of stuff.

---

### Post by BetterSense on 2008-11-26
Well it's still giving me problems, but acidrip seems to work fine as long as I want xvid, and I don't my subtitles being on by default.

---

### Post by mc4man on 2008-11-26
If your on 8.04 it's a little tricky to build - 1.06 built fine, the latest branch didn't.

If your on 8.10 there is a way to install the latest ver. 1.07 from debian-multimedia (similar to medibuntu for ubuntu.

It's not without some risk due to having to install newer versions of about a dozen libs. I did it to see and because I have no attachment to my 8.10 install. (or 8.10 in general

Here's the configure I ended up using with 1.06 (no postproc though

> ./configure --prefix=/usr --enable-freetype2 --enable-avifile  --enable-ogg  --enable-vorbis --enable-theora --enable-pvm3 --enable-libquicktime --enable-lzo --enable-a52 --enable-libmpeg3 --enable-mjpegtools --enable-imagemagick  --enable-libjpeg  --enable-libfame --enable-libdv --enable-libxml2 


and for v 1.07 on hardy needed a new build of ffmpeg to compile off of and to enable postproc (built ffmpeg in home

> ./configure  --prefix=/usr --enable-libmpeg3 --enable-text --enable-v4l --enable-libfame --disable-libfametest --enable-ogg --enable-mjpegtools --enable-lzo --enable-gtk --enable-imagemagick --enable-theora --enable-libquicktime --enable-libdv --enable-libxml2 --enable-vorbis --enable-a52 --enable-pvm3 --enable-netstream  --enable-sdl --enable-freetype2 --enable-avifile --enable-a52-default-decoder --enable-libpostproc --enable-libmpeg3 --enable-nuv --enable-oss --with-libavcodec-includes=/home/doug/ffmpeg --with-libpostproc-includes=/home/doug/ffmpeg --with-libpostproc-libs=/home/doug/ffmpeg 


works fine 
 > transcode -i /dev/dvd -x dvd -T 2,3 -a 1 -y wav -m track3.wav
transcode v1.0.7 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg, 2004-2008 Transcode Team


Your probably better off leaving well enough alone, though if it want to try post your errors

---

### Post by BetterSense on 2008-11-27
Ya I'll just leave well enough alone, the reason I rolled back to hardy is that intrepid kept giving me trouble. Plus, I'm through upgrading anything. Everytime I run an upgrade something breaks. That's why I hadn't been upgrading, until someone in this thread reminded me to, and then now as soon as I upgraded my k3b is broken, as detailed in this thread.

[http://ubuntuforums.org/showthread.php?p=6260458#post6260458]("http://ubuntuforums.org/showthread.php?p=6260458#post6260458")

---

