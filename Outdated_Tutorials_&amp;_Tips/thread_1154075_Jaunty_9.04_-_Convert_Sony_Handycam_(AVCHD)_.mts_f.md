---
title: "Jaunty 9.04 - Convert Sony Handycam (AVCHD) .mts files to x264"
date: 2009-05-09
forum: Outdated Tutorials &amp; Tips
---

### Post by budluva04 on 2009-05-09
Here is the tutorial I wrote on my site....now i'm writing it here, sorry, didn't know I could just post a link. Enjoy.

ORIGINAL [http://blog.thefrozencanuck.ca/?p=12]("http://blog.thefrozencanuck.ca/?p=12")

I have a Sony Handycam HDR-XR100 and it's my first videocamera, and it takes great HD video, but I couldn't get it to play on my Xbox 360, or my computer, as the video the camera outputs is interlaced and in .MTS format. So I'll tell you how I figured out how to convert the .MTS files to .MP4 that will playback fine on your PC or Xbox 360. I found alot of information from this [post]("http://ubuntuforums.org/showthread.php?t=786095"), thanks to the author.

I will be using Ubuntu Jaunty 9.04 and FFMPEG for this tutorial. First we need to compile FFMPEG with x264 support.

**1) Make sure any previous installations of ffmpeg and x264 are removed.**
```
sudo apt-get purge ffmpeg x264 libx264-dev
```

**2) Download packages and install**
```
sudo apt-get update
sudo apt-get install build-essential subversion git-core checkinstall yasm texi2html libfaac-dev libfaad-dev libmp3lame-dev libtheora-dev libxvidcore4-dev
```

**3) Download the latest version of x264 from GIT, then compile**
```
cd ~
git clone git://git.videolan.org/x264.git
cd x264
./configure
make
sudo checkinstall --fstrans=no --install=yes --pkgname=x264 --pkgversion "1:0.svn`date +%Y%m%d`-0.0ubuntu1" --default

```
**4) Download the latest version of FFMpeg from SVN, then compile**
```
cd ~
svn checkout svn://svn.ffmpeg.org/ffmpeg/trunk ffmpeg
cd ffmpeg
./configure --enable-gpl --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab
make
sudo checkinstall --fstrans=no --install=yes --pkgname=ffmpeg --pkgversion "3:0.svn`date +%Y%m%d`-12ubuntu3" --default
```

**5) Convert your .MTS to .MP4 (Single Pass)**
```
ffmpeg -i INPUT.MTS -acodec libfaac -ab 128k -ac 2 -vcodec libx264 -vpre hq -crf 22 -threads 0 -deinterlace OUTPUT.MP4
```

Change your INPUT and OUTPUT, and you can play around with the ffmpeg preset's (-vpre) the availabe presets are default, normal, hq, and max.

***** NOTE FOR XBOX 360 PLAYBACK *****
Playback requires the Audio stream be 2 Channel AAC (-ac 2)

To remove all packages and the changes made to your system from my how-to...
```
sudo apt-get purge x264 ffmpeg build-essential yasm subversion git-core checkinstall texi2html libfaac-dev libfaad-dev libmp3lame-dev libtheora-dev libxvidcore4-dev

```
Thanks, have fun with your videos. Don't be afraid to play around with the setting's either. And please feel free to post you comments/suggestions, thanks...until next time!

---

### Post by jpeddicord on 2009-05-11
Moved; please see the criteria for tutorials & tips inclusion:
[http://ubuntuforums.org/showthread.php?t=677396](http://ubuntuforums.org/showthread.php?t=677396)

Thanks!

---

### Post by budluva04 on 2009-06-15
can someone move this or copy this thread to the how-to section?

---

### Post by budluva04 on 2009-06-16
bump...still looking for someone to copy this thread to the howto section

---

### Post by jpeddicord on 2009-06-16
> **budluva04 said:**
> bump...still looking for someone to copy this thread to the howto section

Done!

---

### Post by FakeOutdoorsman on 2009-06-16
Most of this tutorial is a copy and paste from:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

Not a complaint (it's nice to see people finding my tutorial useful), but hopefully the author of this tutorial will be able to keep up with the very active FFmpeg development.  Installation and usage options change often.

---

### Post by andrew.46 on 2009-06-17
Hi budluva04,

Nice work. But perhaps an acknowledgment of some of the sources that you drew your guide from would not be out of place?

All the best,

Andrew

---

### Post by budluva04 on 2009-06-17
> on your PC or Xbox 360. I found alot of information from this post, thanks to the author.

I did SORRY!!! eeek i forgot the href! i'm sorry, fixed now, sorry to piss anyone off :(

---

