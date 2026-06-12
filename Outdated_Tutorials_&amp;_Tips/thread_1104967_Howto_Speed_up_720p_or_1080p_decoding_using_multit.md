---
title: "Howto: Speed up 720p or 1080p decoding using multithreaded mplayer"
date: 2009-03-24
forum: Outdated Tutorials &amp; Tips
---

### Post by sammydee on 2009-03-24
Hi all

If you are like me, you may have tried to play some 720p or 1080p high definition H264 film clips on your computer and it has stuttered or lagged behind audio, making it unwatchable.

Even very fast pcs suffer from this, for example a core 2 quad Q6600 @ 2.4Ghz will struggle with some 1080p material sometimes.

There are two solutions to this problem:

[LIST=1]
[*]Use nvidia's new VDPAU acceleration architecture to speed up h264 decoding. If you have a 8xxx series or newer graphics card and use the proprietary nvidia drivers then it's a fair bet you can use this option.
[*]Use the latest multi-threaded branch of mplayer to try and speed up decoding. In my limited testing this has worked very well and gives massive speedups on dual core systems.
[/LIST]

If you have a nvidia card already, vdpau is your best bet, you can head over to [**this thread for a step by step howto**]("http://ubuntuforums.org/showthread.php?t=1037625&highlight=vdpau").

If you don't have a 8xxx series or high nvidia card, or don't want to use vdpau, the multi-threaded branch of ffmpeg is for you. I tried this on my core duo T2350@1.86Ghz laptop and I went from stuttering on 720p to perfectly smooth 1080p.

_Dependencies_

You will need to install mplayer's build dependencies and smplayer which is a nice frontend I like to use:

```
sudo apt-get build-dep mplayer && sudo aptitude install smplayer git-core
```

_Install_

Change to the src directory in your home folder. If you don't have one, create one:

```
mkdir ~/src && cd ~/src
```

Get and build the latest multi-threaded branch of mplayer:

```
git clone git://repo.or.cz/mplayer && cd mplayer && git checkout origin/mt && git submodule init && git submodule update && ./configure && make
```

The above method will not install mplayer to your system folders, so if it fails for some reason your old mplayer will work just fine. It also doesn't interfere with the package management system. You can of course install the multithreaded version to your system if you like using make install. You should be able to update the source to the latest upstream version by entering the mplayer directory and typing:

```
git pull origin mt
```

_Configure Smplayer_

Ok, the hard work is all done, now you just need to tell smplayer to use your new super fast mplayer version. Here is a list of configuration options you must change in smplayer:

[LIST]
[*]General/General tab/Select MPlayer executable: Point this to your newly compiled mplayer version, if you followed this guide to the letter it should be /home/$user/src/mplayer/mplayer
[*]General/General/Output drivers: You should make sure video is set to xv for best performance.
[*]Performance/Performance: Loop filter - enabled at first, if movie plays slowly or stutters then you can disable this to improve performance at the expense of some quality. You should be able to leave this enabled on 2Ghz+ dual core systems
[*]Advanced/Options for MPlayer/Options box: Enter the following line here:
```
-lavdopts threads=2
```
[/LIST]

That's it! Try playing a 1080p or 720p movie that your computer struggled with before. It should play perfectly well and you should be able to see that both cores are in use rather than just one as before. If your computer still struggles despite these enhancements then you can disable the loop deblocking filter in smplayer as detailed above, this should give you a large performance boost at the expense of quality.

Bear in mind the multithreaded branch of ffmpeg is still experimental so some movies might fail to play. If you don't like using the new mplayer, you can easily tell smplayer to use the old reliable single threaded one instead by entering just "mplayer" in the mplayer executable box instead the path to your newly compiled one.

Hope this helps someone!

Sam

---

### Post by purewater08 on 2009-03-25
Cool!! I've been waiting so long for this.

With fglrx driver i had to use gl2 video output to get rid of tearing.
And it eats a lot of computing power.

I had to decode videos with a 3.33GHz CPU.
Now I can do it with a 2GHz CPU, and both cores' usage at ~70% rather than 1% and 100%.

Thanks for sharing :)

---

### Post by pascal16 on 2009-03-25
Thanks, great guide. Worked perfectly but for one thing: 
```
sudo aptitude build-dep mplayer && sudo aptitude install smplayer git-core
```
should be ```
sudo **apt-get** build-dep mplayer && sudo aptitude install smplayer git-core
```
as it doesn't look like aptitude supports build-dep.

---

### Post by sammydee on 2009-03-25
Thanks pascal16, correction has been made.

---

### Post by sammydee on 2009-04-03
Added method for updating to latest source via git.

---

### Post by c-shadow on 2009-04-07
Thanks for the great guide :)
Now i can watch 1080p without stuttering, even with loop filter enabled. 
It would be nice to see what other dependencies (dev packages) mplayer requires at compile time. configure also gives some list od disabled optional output drivers.
Also, smplayer doesn't seem to recognize this version of mplayer, it asks on first start. 
Had to delete the smplayer config files and start from scratch since some things didn't work: subtitles, xv video output,...now it appears to work fine.
Problem: newest version pulled from git doesn't compile:
```

libao2/ao_jack.o: In function `reset':
ao_jack.c:(.text+0x1c6): undefined reference to `av_fifo_reset'
libao2/ao_jack.o: In function `init':
ao_jack.c:(.text+0x2ef): undefined reference to `av_fifo_alloc'
libao2/ao_jack.o: In function `uninit':
ao_jack.c:(.text+0x8ff): undefined reference to `av_fifo_reset'
libao2/ao_sdl.o: In function `reset':
ao_sdl.c:(.text+0x118): undefined reference to `av_fifo_reset'
libao2/ao_sdl.o: In function `init':
ao_sdl.c:(.text+0x14a): undefined reference to `av_fifo_alloc'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1

```
Any ideas abut that?

---

### Post by chapterthree on 2009-04-12
**Thanks!** (Where did the 'Thank' button go?)

Ubuntu Intrepid 8.10 64-bit
Intel E8400 Core 2 Duo 3.0GHz
Nvidia 6600GT
2x2GB DDR2

On this rig I was able to play 720p content without any issues using VLC, but playing 1080p content had extreme stutter and delay (unwatchable).

The instructions mentioned in this thread have significantly improved the playback of 1080p content.  Now viewing 1080p content (using SMplayer) is almost perfect, no more stuttering or delay, but I am seeing some artifacts, which I need to troubleshoot independently, but the instructions mentioned here got me 98% of the way there (on an under-capacity card no less).  I've only tried 1 media source so far, and I haven't tried with the loop filter disabled yet.

With 1080p content mplayer seems to hover in the 30-50% CPU range, and Xorg is 70%+ CPU (which I'm starting to wonder if the high Xorg CPU usage is not normal, and hence further troubleshooting).

I was planning on stepping up to a 9800/260 soon anyway (to run a yet-to-be-purchased HDTV), but the instructions here should tide me over for a while (on my measly 22" Widescreen LCD monitor at 1680x1050).

Thanks again!

---

### Post by SOME1 on 2009-04-12
thanks for the howto, but I cant install it: 
when I am running the command
```
git clone git://repo.or.cz/mplayer
```
after few seconds its start to download I get 
> 
fatal: The remote end hung up unexpectedly.
fatal: early EOF
fatal: index-pack failed


please help. 
thanks.

---

### Post by sammydee on 2009-04-13
Seeing as this is an experimental branch of mplayer, it is likely to be fairly buggy and sometimes even fail to compile.

SOME1:

It looks as though the site is just down temporarily.

Sam

---

### Post by sammydee on 2009-04-13
> **chapterthree said:**
> With 1080p content mplayer seems to hover in the 30-50% CPU range, and Xorg is 70%+ CPU (which I'm starting to wonder if the high Xorg CPU usage is not normal, and hence further troubleshooting).

Are you definately using xv? If compiz is enabled, are you definately using direct rendering (not indirect rendering)?

Sam

---

### Post by SOME1 on 2009-04-13
well, that's what I thought when I tried to download one week ago, so yesterday I tried again and I got exactly the same. 
I tried to download now from work and it's looks ok. 

strange. 

thanks any way ;)

---

### Post by commandant_gogo on 2009-04-13
Hi in "mplayer" folder i only have the following file:
-mplayer.c
-mplayer.d
-mplayer.h
-mplayer.o

But none of them is launching mplayer...

---

### Post by maxclimber1w on 2009-04-14
Hey! Thanks for the guide, I am really looking forward to this functionality.

But when I try to play a file, it fails with an error 1 message. This is the log. Any ideas?

```
/home/max/src/mplayer/mplayer -noquiet -nofs -sub-fuzziness 1 -identify -msglevel demux=6 -slave -vo xv -zoom -nokeepaspect -framedrop -input conf=/usr/share/smplayer/input.conf -nostop-xscreensaver -wid 71303180 -monitorpixelaspect 1 -subfont-autoscale 1 -subfont-text-scale 5 -subcp ISO-8859-1 -subpos 100 -contrast 0 -brightness 0 -hue 0 -saturation 0 -nocache -osdlevel 0 -vf-add screenshot -channels 2 -af scaletempo -lavdopts threads=2 /home/max/Downloads/video.mkv

Unknown option on the command line: -nostop-xscreensaver
Error parsing option on the command line: -nostop-xscreensaver
MPlayer UNKNOWN-4.3.2 (C) 2000-2009 MPlayer Team
ID_EXIT=NONE
```

---

### Post by Cresho on 2009-04-14
movie players plays my 720p or 1080p just fine.

You need a powerfull cpu.  GPU acceleration is not available.

2gb ddr800
amd athlon 6400 black edition on a 32 bit system.

---

### Post by Pitabred on 2009-04-15
> **SOME1 said:**
> thanks for the howto, but I cant install it: 
when I am running the command
```
git clone git://repo.or.cz/mplayer
```
after few seconds its start to download I get 



please help. 
thanks.

Just try it again. That's just what happens when the server times out.

---

### Post by maxclimber1w on 2009-04-16
I could really use some help here, this was working fine with the proprietary ATI driver but it broke my X.org pretty quickly.

> **maxclimber1w said:**
> Hey! Thanks for the guide, I am really looking forward to this functionality.

But when I try to play a file, it fails with an error 1 message. This is the log. Any ideas?

```
/home/max/src/mplayer/mplayer -noquiet -nofs -sub-fuzziness 1 -identify -msglevel demux=6 -slave -vo xv -zoom -nokeepaspect -framedrop -input conf=/usr/share/smplayer/input.conf -nostop-xscreensaver -wid 71303180 -monitorpixelaspect 1 -subfont-autoscale 1 -subfont-text-scale 5 -subcp ISO-8859-1 -subpos 100 -contrast 0 -brightness 0 -hue 0 -saturation 0 -nocache -osdlevel 0 -vf-add screenshot -channels 2 -af scaletempo -lavdopts threads=2 /home/max/Downloads/video.mkv

Unknown option on the command line: -nostop-xscreensaver
Error parsing option on the command line: -nostop-xscreensaver
MPlayer UNKNOWN-4.3.2 (C) 2000-2009 MPlayer Team
ID_EXIT=NONE
```

---

### Post by andrew.46 on 2009-04-16
Hi maxclimber1w,

> **maxclimber1w said:**
> 
```
Unknown option on the command line: -nostop-xscreensaver
Error parsing option on the command line: -nostop-xscreensaver
MPlayer UNKNOWN-4.3.2 (C) 2000-2009 MPlayer Team
ID_EXIT=NONE

```

The command -nostop-xscreensaver works on my svn MPlayer, although I do not use the FFmpeg-mt additions. Combined with the 'UNKNOWN' in your MPlayer string I suspect that you might need to reload the dependencies as per sammydee's guide, svn up and recompile. Possibly your install of MPlayer is incomplete.

All the best,

Andrew

---

### Post by rldev on 2009-08-03
This did not work for me. It made my performance worse. Hard to believe.

---

### Post by szr4321 on 2010-03-11
Updated instructions can be found here: [http://lglinux.blogspot.com/2010/03/multi-threaded-mplayer-for-faster-720p.html](http://lglinux.blogspot.com/2010/03/multi-threaded-mplayer-for-faster-720p.html)

---

### Post by costre on 2010-03-12
Well well, here we go again ...
Every time I reinstall Ubuntu I try to get a media player that works better than VLC.

I download, compile and install a crapload of different codecs, updates, graphics drivers, tweaks and customized/homemade software. In the end I haven't got any positive results, and VLC has more often than not got messed up in the process.

All of a sudden I get a blue bar in the top of the video frame, the hue turns to **** and I have to manually adjust it, the video output turns black after I return from a preferences window and I have to restart the playback software, in the end I can't get descent framerates in hardly any media player, and on top of it all I don't know how to reverse any of these changes!

When will I learn to just settle for a plain download of VLC? :)

(going for a complete reinstall of ubuntu tomorrow, the system feels like a complete mess when these procedures go on long enough ..)

---

### Post by sammydee on 2010-03-20
An update: Since I wrote this guide, vdpau has proven itself to be a mature, reliable and practical way of playing high definition videos on linux machines.

By far the easiest way to get pain free video playback in linux is just to buy a nvidia card. You can pick up a 9400 or something for only about £30, it's totally worth it.

---

