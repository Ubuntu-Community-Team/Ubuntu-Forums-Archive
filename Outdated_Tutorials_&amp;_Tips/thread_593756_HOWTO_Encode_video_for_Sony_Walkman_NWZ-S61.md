---
title: "HOWTO: Encode video for Sony Walkman NWZ-S61"
date: 2007-10-27
forum: Outdated Tutorials &amp; Tips
---

### Post by 3rdalbum on 2007-10-27
The Sony Walkman NWZ-S61 series MP3 players are awesome for Linux use - they can be loaded with music through simple drag 'n' drop in any operating system. These little beauties support video too, but with slightly different specifications to the iPods and the PSP, so programs that work for those two devices will not create the right files for your MP3 player.

First, you need a recent version of FFMPEG. The one in the Gutsy repos is probably alright (not tried it). If you are running Feisty or earlier distributions, you need to visit the FFMPEG website and install the latest version from SVN:

[SIZE="3"]Install FFMPEG from SVN[/SIZE]
1. install development packages and svn itself:
```
sudo apt-get install svn build-essential liba52-dev libxvid-dev libvorbis-dev libogg-dev libtheora-dev libfaac-dev libfaad-dev faac libx264-dev liblame-dev
```

2. Create a directory to be used for holding source code:
```
cd
mkdir sources
cd sources

```

3. "Check out" the latest source code from FFMPEG:
```
svn checkout svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg
```

4. Compile it:
```

cd ffmpeg
./configure --enable-gpl --enable-pp --enable-swscaler --enable-liba52 --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libogg --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid
make
sudo make install

```

[SIZE="3"]Manual Encoding Method[/SIZE]

FFMpeg on the command-line isn't so hard to use. In fact, it's rather easy once you know what values to plug into the program! (it took me 4 days to figure out what values my Walkman would accept). For the weak at heart, I have put together a GUI program, but here's the idea.

1. Prepare your source material - download it from Youtube or rip a DVD into .vob.

2. Put this into the command-line:
```
ffmpeg -i <inputfile> -b 567k -s 320x240 -vcodec mpeg4 -ab 220k -ar 44100 -ac 2 -acodec libfaac output.mp4
```

Substituting <inputfile> for your input file, and output.mp4 for the filename you want for the video. Make sure it ends in .mp4 though.

3. Copy the encoded file to /media/WALKMAN/VIDEO or wherever your Walkman is mounted.

[SIZE="3"]The GUI method - BlackLight[/SIZE] ###This howto concerns Blacklight 0.1 - please go to [http://sourceforge.net/projects/blacklight]("http://sourceforge.net/projects/blacklight") and get the latest Blacklight.

This program will get some polish in the coming weeks, but for now here's a simple frontend for the whole operation.

1. You will need to pull down some packages to run BlackLight:

```
sudo apt-get install python-pythoncard zenity faac
```

2. If not already connected, connect your Walkman to the computer (and mount it).

3. Run Blacklight by setting blacklight.py to be executable in the usual way, and then double-clicking on it and selecting "Run".

3. Click "Browse..." and select the video file or VOB that you want to convert.

4. Click "Convert", and then wait a while. On a reasonably modern computer, the encoding performance will be better than 1x.

5. BlackLight will send the encoded video file directly to your Walkman.


--------------
Possible problems:

P. The audio stutters on the Walkman, but not on the computer.

S. Your FFMPEG is too old. Compile the latest version from SVN. Don't worry, the SVN versions are so stable, all distributions include whatever the latest SVN was at time of freeze!

P. When using the manual method, FFMPEG complains that it can't find the "libfaac" codec.

S. Sometimes, FFMPEG refers to codecs by slightly different names depending on its version. In the command, change "libfaac" to "aac" and this should work.

P. Something else has gone wrong.

S. Please reply to this topic with as much information as possible. I'll try and help as best as I can!

EDIT: Added link to Sourceforge site, also added an extra parameter to the ffmpeg command so it works on more DVD rip files.

---

### Post by johnonfire on 2007-10-31
I tried the command line method to convert an .avi file to mp4 for my new NWZ using both "libfaac" and "aac" for -acodec and it returns the line unknown codec.  I'm running a newly upgraded Gutsy and downloaded ffmpeg today.  Your instructions seem to be specific to .vob files.  Do you need to change something to convert an avi to mp4?

I also tried using blacklight as a gui alternative.  It didn't seem to like my using an avi either.

---

### Post by 3rdalbum on 2007-11-29
Sorry for the lateness of my reply; this thread got super-buried so quickly I thought it had never been approved.

What codecs do the AVI use? Do any other video files work with either the command-line or with Blacklight? And when you say that you downloaded ffmpeg, did you get it from their SVN server, or from the Gutsy repos?

I'm not sure, but it's possible that the Ubuntu version of ffmpeg has not been compiled with aac support. You can be sure by going to the command-line and typing:

```
ffmpeg -formats | grep "aac"
```

Please raise a bug at the Sourceforge site: [http://sourceforge.net/projects/blacklight]("http://sourceforge.net/projects/blacklight") and we'll see if we can work this problem out. The code I posted should work with any file, not just a DVD rip (.vob). It should work with any file that ffmpeg recognises!

---

### Post by mlkv on 2007-12-27
Hi all, I just tried this tutorial and here's a quick update if you're running Gutsy (or maybe is just like this on any Ubuntu version and it's just that a few packet names are changed).

You should use:

subversion in place of svn
libxvidcore4-dev in place of libxvid-dev
libfaad2-dev in place of libfaad-dev

So the first, major sudo apt-get install (point 1.) becomes:

```
sudo apt-get install subversion build-essential liba52-dev libxvidcore4-dev libvorbis-dev libogg-dev libtheora-dev libfaac-dev libfaad2-dev faac libx264-dev liblame-dev
```

Then there's one thing you can't do when you ./configure (point 4.), because --enable-libogg isn't recognised as a valid option. I've tried

```
./configure --help
```

And it looks like that's no longer a viable option? I simply wiped that option away from the command line since I figured that --enable-libvorbis should have been enough (I'm totally ignorant in this subject though). I had checked if I had the libogg-dev packet install but indeed I had it already. I can't really tell what's going on here, sorry. Anyway, everything else was still ok and the encoding was perfect: the video on which I tried (a .flv downloaded at random from youtube) looked and sounded great on my NWZ A818.

Thanks for the helpful tutorial. :)

---

### Post by primorec on 2008-02-07
> **mlkv said:**
> Hi all, I just tried this tutorial and here's a quick update if you're running Gutsy (or maybe is just like this on any Ubuntu version and it's just that a few packet names are changed).

You should use:

subversion in place of svn
libxvidcore4-dev in place of libxvid-dev
libfaad2-dev in place of libfaad-dev



You saved my day    THANKS !!!!!!!!!!!!

Igor

---

### Post by descentspb on 2008-02-12
Thanks to you, mate, and to some iPod-guide-writers, and some searching, I've made a similar guide, showing how to encode into **H.264** [http://ubuntuforums.org/showthread.php?t=693867]("http://ubuntuforums.org/showthread.php?t=693867")

---

### Post by planejason on 2008-07-27
More updates (Hardy Heron):

libfaad2-dev is back to libfaad-dev in Hardy for whatever reason

and

--enable-pp has changed to --enable-postproc
--enable-swscaler has changed to --enable-swscale
 in the latest svn version of ffmpeg

Awsome how to by the way.

Edit:  well I spoke too soon.  the version of x264 that ships with Hardy is too old for the new version of ffmpeg so you will also have to get the source for and build the x264 codec if you want that enabled.  See this post

[http://ubuntuforums.org/showthread.php?t=786095&highlight=libx264](http://ubuntuforums.org/showthread.php?t=786095&highlight=libx264)

for details.   Sleep...Who needs sleep?

---

### Post by 3rdalbum on 2008-07-27
Thanks so much for keeping this thread up-to-date! I'm not running Hardy on my main computer so I haven't been keeping track of dependencies and bugs; that, and I've been just using the Medibuntu version of ffmpeg rather than building my own :-)

If you use the Blacklight program, you need to make one change to the source for it to run on Hardy. In the source, wherever it's got a file path, change it from "VIDEOS" to "Videos". I noticed this a while back and was going to roll it in with a bunch of fixes, but I've been sidetracked and that version never got released.

---

### Post by eoalvarez on 2008-08-26
I have down the previous step 1-4 with the alterations and downloaded black light from the link said. 

Unfortunately I get this

Could not encode your video. Please check that you have libfaac and libmp4v2-0 installed. If you compiled FFMPEG from source, you should check your configure-time options

I have libfaac and libmp4v2 installed.....

What could be happening?

I tried manually also and got this error

FFmpeg version SVN-r14974, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-nonfree
  libavutil     49.10. 0 / 49.10. 0
  libavcodec    51.69. 0 / 51.69. 0
  libavformat   52.21. 0 / 52.21. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  built on Aug 26 2008 18:18:19, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
Input #0, mpeg, from '/home/ouicho/Desktop/56-form-chensi.mpg':
  Duration: 00:05:40.96, start: 0.213333, bitrate: 614 kb/s
    Stream #0.0[0x1e0]: Video: mpeg1video, yuv420p, 320x240 [PAR 1:1 DAR 4:3], 104857 kb/s, 30.00 tb(r)
    Stream #0.1[0x1c0]: Audio: mp2, 32000 Hz, mono, s16, 32 kb/s
Unknown encoder 'libfaac'

i have libfaac and libfaac dev installed....

---

### Post by SlowerLearner on 2009-02-15
I've just happened upon this post and taken a quick look, so forgive me if I'm repeating info above,  I have just encoded video for a Sony Watchman today, on Intrepid, using FFMPEG.  The command I have used is:

ffmpeg -i xxxx.avi -acodec libfaac -ab 128kb -vcodec mpeg4 -b 1200kb -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -s 320x180 -title X xxxx.mp4

which I took from this website:

&#65279;[http://www.catswhocode.com/blog/19-ffmpeg-commands-for-all-needs](http://www.catswhocode.com/blog/19-ffmpeg-commands-for-all-needs)

The original command line suggested at the website above uses audio aac, which returned the error you have (but for aac instead of libfaac).  I guess you could try aac and/or some of the links from that site.

---

### Post by aircooledbusnut on 2009-11-29
when I convert video, not matter which way I have tried.  It does not show on my walkman.  I have a sample video on the walkman which is .wmv

any ideas

Thanks

---

### Post by cong06 on 2010-06-11
I'm in lucid, and having the "aac" problem:
```

isaac@phaff:~$ ffmpeg -i Desktop/04_Shindig.avi -b 567k -s 320x240 -vcodec mpeg4 -ab 220k -ar 44100 -ac 2 -acodec libfaac output.mp4
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 23.98 (65535/2733) -> 23.98 (2997/125)
Input #0, avi, from 'Desktop/04_Shindig.avi':
  Duration: 00:43:59.40, start: 0.000000, bitrate: 740 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 544x304 [PAR 1:1 DAR 34:19], 23.98 tbr, 23.98 tbn, 23.98 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 112 kb/s
Unknown encoder 'libfaac'

```
same error if I use "aac"

checking for compatability...
```

isaac@phaff:~$ ffmpeg -formats | grep aac
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3
 D  aac             raw ADTS AAC
 D A    aac             Advanced Audio Coding

```

maybe I'm just missing the right package for aac libraries?
libfaad2 is already installed, and I didn't compile.


Edit: So I've confirmed that you do in fact have to compile it to get the "--enable-nonfree" option in there.
Recompiling fixed it. (and caused other problems, see next post)

---

### Post by cong06 on 2010-06-14
I realize now that the Sony Walkman NWZ-E345 is different from the NWZ-S61.

It seems E345 needs wmv wma codecs, which I haven't managed to install/configure properly.
Any ideas with my model?

---

