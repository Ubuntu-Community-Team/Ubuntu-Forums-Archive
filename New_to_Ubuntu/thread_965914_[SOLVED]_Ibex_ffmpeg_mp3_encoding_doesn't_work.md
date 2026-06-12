---
title: "[SOLVED] Ibex ffmpeg mp3 encoding doesn't work"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by whitethorn on 2008-10-31
Hi,

I recently installed ffmpeg from the medibuntu repository, I'm assuming encoding mp3 should work but it doesn't. Whenever I try running the command with 

```
ffmpeg --acodec mp3
```
```
ffmpeg --acodec libmp3lame
``` (I think that's how it's called) 

I get an error saying > Unknown encoder.  I'm pretty sure I've installed the encoder.  I installed a bunch of libraries and lame. Any ideas why it doesn't work?  I could always try compiling it myself, but it kinda beats the purpose of using the medibuntu repository.

---

### Post by mc4man on 2008-11-01
> but it kinda beats the purpose of using the medibuntu repository
I don't believe there is a ffmpeg in medibuntu for ibex, and the ubuntu version is neutered. 
Here's a fairly straightforward guide to building ect. if needed and thread for info, help.

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by cariboo on 2008-11-01
Either  that or just install lame to convert to mp3

Jim

---

### Post by mc4man on 2008-11-01
There is also an 'in between' thing that one could do. If you've no real need for the latest ffmpeg and libav*'s and just want a better ffmpeg to go along with your existing libav*'s this is fairly easy. (will be compatible with the regular or unstripped libav*'s which must be installed for other apps anyway.

The hardest part would be making sure you have all the libs and -devs you'll need installed. Absolutely don't depend on apt-get build-dep ffmpeg.

Basically just download the ubuntu ffmpeg source and build off of command of
```
fakeroot debian/rules binary
```
This will build a complete set of libav*'s and ffmpeg .deb's (17 packages) though all you'll want is the ffmpeg deb.

Before running comm. on the source just browse to the debian folder, open the confflags file and make some changes, enable what you want supported, edit a few lines, remove a couple of lines and run the above command.

Then just install the ffmpeg deb (if and when medibuntu releases you can upgrade your libav*'s and ffmpeg.

Ex. (enabled most of the basic stuff 
> doug@doug-desktop:~$ ffmpeg -i heroes.wav -acodec libmp3lame -ab 192k heroes.mp3
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --enable-libxvid --enable-libmp3lame --enable-libfaac --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-nonfree --enable-libamr-nb --enable-libamr-wb --enable-libx264 --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Nov  1 2008 01:27:35, gcc: 4.3.2
Input #0, wav, from 'heroes.wav':
  Duration: 00:04:33.6, bitrate: 2304 kb/s
    Stream #0.0: Audio: pcm_s24le, 48000 Hz, stereo, 2304 kb/s
Output #0, mp3, to 'heroes.mp3':
    Stream #0.0: Audio: libmp3lame, 48000 Hz, stereo, 192 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=    6415kB time=273.7 bitrate= 192.0kbits/s  video:0kB audio:6415kB global headers:0kB muxing overhead 0.000472%


if you need help with confflags i can offer advice though I'm sure others would know more or better.

---

### Post by jahst on 2008-11-17
This worked for me!



[https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/296922](https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/296922)

 Lionel Le Folgoc  wrote on 2008-11-11:  (permalink)

Hi,

Thanks for your bug report.
To have mp3 encoding, you need to install the 'libavcodec-unstripped-51' package, and pass '-acodec libmp3lame' instead of '-acodec mp3' in your command line.

---

### Post by FakeOutdoorsman on 2008-11-17
Ibex can use the "unstripped" codecs and such with ffmpeg to allow mp3, aac, xvid, etc.  Just to make this easy:
```
sudo apt-get purge ffmpeg
sudo apt-get update
sudo apt-get install libavcodec-unstripped-51 libavdevice-unstripped-52 libavformat-unstripped-52 libavutil-unstripped-49 libpostproc-unstripped-51 libswscale-unstripped-0 ffmpeg
```

---

### Post by Nyken on 2009-10-15
Dead on. Perfect fix. Thanks for the posts!

---

