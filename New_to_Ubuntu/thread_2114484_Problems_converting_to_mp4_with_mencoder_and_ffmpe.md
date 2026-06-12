---
title: "Problems converting to mp4 with mencoder and ffmpeg"
date: 2013-02-10
forum: New to Ubuntu
---

### Post by Johann-1.0 on 2013-02-10
Hello guys.

This time I request some help because I'm trying to convert some avi files into mp4, but once i do it with mencoder, ubuntu cannot play the mp4 file (although i can play other mp4). It doesn't play ONLY the mp4 files a made with mencoder.
On the other hand, when I try to use ffmpeg, it says "Unsupported codec for output stream #0.1", not allowing me to convert them.

What should I do right now?

In previous releases of Ubuntu I did this kind of conversions so easily with no problems, what's wrong this time?

I'm using Ubuntu 10.04

Please, give me a solution as easy as you can, like apt-get install whatever, etc ;)

---

### Post by linuxsyst on 2013-02-10
The command for mencoder is ```

mencoder (input).avi -o (output).mp4 -oac copy -ovc lavc -lavcopts vcodec=mpeg1video -of mpeg

```
Then test it with ```
mplayer (filename).mp4
```
 
And the command for ffmpeg is ```
ffmpeg -i (input).avi -acodec libfaac -b:a 128k -vcodec mpeg4 -b:v 1200k -flags +aic+mv4 (output).mp4
```
If you want to know how it works here:
[COLOR=#dc322f]```
[COLOR=#000000]-acodec libfaac[/COLOR]
```[/COLOR]This uses the faac codec to encode the audio to aac.
```
-b:a 128k and -b:v 1200k
```These are the audio and video (respectively) bitrates of 128kb and 1200kb
```
-flags +aic+mv4
```
mv4 - Affects: Encoding, Video
use four motion vector by macroblock (mpeg4)
aic - 
Affects: Encoding, Video
h263 advanced intra coding / mpeg4 ac prediction

---

### Post by Johann-1.0 on 2013-02-10
Thank you very much..but it's not working yet. I think the problem is related to some codecs restriction or anything, because I used the same commands as you do.
Thank you again for trying to help

---

### Post by linuxsyst on 2013-02-10
What application did you open it with?
Edit: Ok I probably know what the problem is... Add the Motumedia repository ```
sudo add-apt-repository ppa:motumedia/mplayer-daily
```
And install - ```
sudo apt-get install x264
```
Or you can do this...
```
git clone --depth 1 
git://git.videolan.org/x264.git
cd x264
./configure --enable-static
make
sudo checkinstall --pkgname=x264 --pkgversion="3:$(./version.sh | \
  awk -F'[" ]' '/POINT/{print $4"+git"$5}')" --backup=no --deldoc=yes \
  --fstrans=no --default

```

---

### Post by Johann-1.0 on 2013-02-10
Still the same: Unsupported codec.

I can play other mp4 files, but not those I created with ffmpeg, neither on my computer nor my cellphone.

---

### Post by glennric on 2013-02-10
The x264 package is in the ubuntu universe repository.  There is no need to enable a third party repository for it.

Also, installing the x264 encoder package will not help at all with the mencoder and ffmpeg commands posted above because they do not use the x264 codec.

What player are you trying to use to play the files back on your computer?  Also, what operating system does your phone have on it?

---

### Post by glennric on 2013-02-10
Try the following modified ffmpeg command and see if it works better for you.
```

avconv -i (input).avi -strict experimental -acodec aac -b:a 128k -vcodec mpeg4 -b:v 1200k -flags +aic+mv4 (output).mp4

```

Not that ffmpeg is deprecated and avconv is its replacement.  That command may not help, but the libfaac encoder codec is not available in the default ubuntu packages for avconv.  The aac encoder is, but you have to enable experimental standards to use it.

---

### Post by Johann-1.0 on 2013-02-10
Thank you very much. I use mplayer to play the files. My Ubuntu is 10.04 64bit.

I tried your modified command and still no success with it.
I tried installing avconv and could be read "Couldn't find package avconv".

I think the problem is not related to my cell, because I can play mp4 files on it. My computer also is able to play mp4 files...the only files my computer doesn't play are those I've created with mencoder or ffmpeg. 

I read in another post one command that worked fine...mencoder <input.avi> -of mpeg -ovc lavc -lavcopts vcodec=mpeg1video -oac copy -o <output.mpg>

but, as you may see, it's not in mp4 format, so I can't play it on my cellphone...but I ran this command and later played the file in my computer and everything was ok.

Thank you for your help...any other suggestions for me?

---

### Post by andrew.46 on 2013-02-11
> **Johann-1.0 said:**
> 
On the other hand, when I try to use ffmpeg, it says "Unsupported codec for output stream #0.1", not allowing me to convert them.

[...]

I'm using Ubuntu 10.04


Perhaps if you are using Lucid Lynx 10.04 you could run the following:

```
sudo apt-get install ffmpeg **[COLOR="Red"]libavcodec-extra-52[/COLOR]**
```

and then run your conversion as previously but copy and paste the entire terminal output into a forum post. This will give a few hints as to what is going on...

---

### Post by andrew.46 on 2013-02-11
> **glennric said:**
> Note that ffmpeg is deprecated and avconv is its replacement. 

FFmpeg development is actually thriving at the moment as is development of the fork avconv. The 'deprecated' message was yet another arrow fired in a highly regrettable war :(.

---

### Post by FakeOutdoorsman on 2013-02-11
> **andrew.46 said:**
> The 'deprecated' message was yet another arrow fired in a highly regrettable war :(.

The misleading 'not being developed anymore' and 'deprecated' messages probably caused more user confusion than anything else resulting from the fork. So much time has been dedicated to explaining the situation by various users, contributors, and developers of ffmpeg. Instead of working on a certain new guide for the [FFmpeg Wiki](https://ffmpeg.org/trac/ffmpeg/wiki) my FFmpeg time today has been distracted by discussing this yet again...and this is the [s]second[/s] third instance today.

For anyone looking for more info:
[list]
[*][Who can tell me the difference and relation between ffmpeg, libav, and avconv](http://stackoverflow.com/a/9477756)
[*][The FFmpeg/Libav situation](http://blog.pkh.me/p/13-the-ffmpeg-libav-situation.html)
[/list]

---

### Post by Paddy Landau on 2013-02-11
FakeOutdoorsman, I've just read your post and the links you referred to.

Wow. It seems surreal!

Something that confused me: is the [FONT=Lucida Console]ffmpeg[/FONT] on Ubuntu actually [FONT=Lucida Console]ffmpeg[/FONT], or is it something else that has been renamed as [FONT=Lucida Console]ffmpeg[/FONT]? Why would Ubuntu take sides and add the "deprecated" message, or have I misunderstood?

I presume that it is actually OK to continue to use [FONT=Lucida Console]ffmpeg[/FONT], and ignore the "deprecated" message?

Bearing in mind [my errors with avconv]("http://ubuntuforums.org/showthread.php?t=2114514"), I presume that I should cease to use [FONT=Lucida Console]avconv[/FONT]. Or should I rather raise a bug against it to the [FONT=Lucida Console]avconv[/FONT] team?

What about [bug #939863]("https://bugs.launchpad.net/ubuntu/+source/libav/+bug/939863"): it seems to me that this message should be removed altogether?

---

### Post by Johann-1.0 on 2013-02-11
> **andrew.46 said:**
> Perhaps if you are using Lucid Lynx 10.04 you could run the following:

```
sudo apt-get install ffmpeg **[COLOR="Red"]libavcodec-extra-52[/COLOR]**
```

and then run your conversion as previously but copy and paste the entire terminal output into a forum post. This will give a few hints as to what is going on...
Thank you...I had already done that but again, no success :(

Here is the error message if anyone finds it useful:

```
Forzadeldestino1-1.avi

FFmpeg version SVN-r0.5.9-4:0.5.9-0ubuntu0.10.04.3, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.9-0ubuntu0.10.04.3 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Jan 24 2013 19:42:59, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 30000.00 (30000/1) -> 29.97 (30000/1001)
Input #0, avi, from 'Forzadeldestino1-1.avi':
  Duration: 00:26:17.59, start: 0.000000, bitrate: 2364 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 480x360 [PAR 1:1 DAR 4:3], 29.97 tbr, 29.97 tbn, 30k tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 112 kb/s
File 'Forzadeldestino1-1.mp4' already exists. Overwrite ? [y/N] y
Output #0, mp4, to 'Forzadeldestino1-1.mp4':
    Stream #0.0: Video: mpeg4, yuv420p, 480x360 [PAR 1:1 DAR 4:3], q=2-31, 200 kb/s, 90k tbn, 29.97 tbc
    Stream #0.1: Audio: 0x0000, 48000 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec for output stream #0.1

```

---

### Post by Paddy Landau on 2013-02-11
Shot in the dark here, but have you installed the [ubuntu-restricted-extras]("apt:ubuntu-restricted-extras") package?

---

### Post by Johann-1.0 on 2013-02-11
> **Paddy Landau said:**
> Shot in the dark here, but have you installed the [ubuntu-restricted-extras]("apt:ubuntu-restricted-extras") package?

Yes Paddy, I have already installed that package ;)

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

```

---

### Post by SeijiSensei on 2013-02-11
> Stream #0.1: Audio: 0x0000, 48000 Hz, stereo, s16, 64 kb/s
Unsupported codec for output stream #0.1

The problem is the audio codec.  Why not just use mp3 which is what the original is encoded with?  I believe you just use "-acodec libmp3lame", but since I don't use ffmpeg, I may be wrong.

---

### Post by andrew.46 on 2013-02-11
> **Johann-1.0 said:**
> Here is the error message if anyone finds it useful:

```
Forzadeldestino1-1.avi

FFmpeg version SVN-r0.5.9-4:0.5.9-0ubuntu0.10.04.3, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.9-0ubuntu0.10.04.3 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Jan 24 2013 19:42:59, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 30000.00 (30000/1) -> 29.97 (30000/1001)
Input #0, avi, from 'Forzadeldestino1-1.avi':
  Duration: 00:26:17.59, start: 0.000000, bitrate: 2364 kb/s
[B][COLOR="Red"]    Stream #0.0: Video: mpeg4, yuv420p, 480x360 [PAR 1:1 DAR 4:3], 29.97 tbr, 29.97 tbn, 30k tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 112 kb/s[/COLOR][/B]
File 'Forzadeldestino1-1.mp4' already exists. Overwrite ? [y/N] y
Output #0, mp4, to 'Forzadeldestino1-1.mp4':
    Stream #0.0: Video: mpeg4, yuv420p, 480x360 [PAR 1:1 DAR 4:3], q=2-31, 200 kb/s, 90k tbn, 29.97 tbc
    Stream #0.1: Audio: 0x0000, 48000 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec for output stream #0.1

```

For this particular stream you can simply copy both video and audio codecs into a new container. This is an old version of FFmpeg so I am not entirely sure of the syntax but try:

```

ffmpeg -i Forzadeldestino1-1.avi \
          -acodec copy -vcodec copy \
          Forzadeldestino1-1.mp4

```

The error suggests that you do not have the capability to *encode* with libmp3lame but you can still *copy*...

---

### Post by FakeOutdoorsman on 2013-02-11
> **Paddy Landau said:**
> Something that confused me: is the [FONT=Lucida Console]ffmpeg[/FONT] on Ubuntu actually [FONT=Lucida Console]ffmpeg[/FONT], or is it something else that has been renamed as [FONT=Lucida Console]ffmpeg[/FONT]?
It is not ffmpeg (the program) from FFmpeg (the project). It is a remnant from the libav fork before they renamed their temporary ffmpeg to avconv.

> **Paddy Landau said:**
> Why would Ubuntu take sides and add the "deprecated" message, or have I misunderstood?
The Debian/Ubuntu ffmpeg maintainer took sides with the fork and decided to switch Ubuntu to libav. The misleading ["deprecated" message was added]( https://bugs.launchpad.net/ubuntu/+source/libav/+bug/939863) to silence Ubuntu users who didn't like the original "This program is not developed anymore" message, but the ambiguity was allowed to stay.

> **Paddy Landau said:**
> I presume that it is actually OK to continue to use [FONT=Lucida Console]ffmpeg[/FONT], and ignore the "deprecated" message?
libav users should use avconv instead of the libav version of ffmpeg.

> **Paddy Landau said:**
> What about [bug #939863]("https://bugs.launchpad.net/ubuntu/+source/libav/+bug/939863"): it seems to me that this message should be removed altogether?
The "fix" to this bug was unsatisfactory and reasoning behind it makes me feel that, for this distro, a good user experience is less important than petty politics.

---

### Post by Johann-1.0 on 2013-02-11
> **andrew.46 said:**
> For this particular stream you can simply copy both video and audio codecs into a new container. This is an old version of FFmpeg so I am not entirely sure of the syntax but try:

```

ffmpeg -i Forzadeldestino1-1.avi \
          -acodec copy -vcodec copy \
          Forzadeldestino1-1.mp4

```

The error suggests that you do not have the capability to *encode* with libmp3lame but you can still *copy*...


Thank you very much for your answer, it was very helpful. At first, it appears to work, because now I can play those generated mp4 files on my desktop (let me expain again, I could play every mp4 file but not those I created with ffmpeg). Now, I can play it on my desktop but still I'm not able to play it on my cell phone. Again, my cell phone only has problems with these mp4 files, but it can play other mp4files. Any other suggestion?
Anothe question: does anybody know the command to convert the files to 3gp? You know, if mp4 is giving me problems, let's give 3gp a try.
How can I be able to encode with libmp3lame?

Thank you very much for your time guys.

---

### Post by andrew.46 on 2013-02-12
> **Johann-1.0 said:**
>  Now, I can play it on my desktop but still I'm not able to play it on my cell phone. Again, my cell phone only has problems with these mp4 files, but it can play other mp4files. Any other suggestion?

Mobile phones can be a little picky about codecs unfortunately. Grab one or two of the files that work and run FFmpeg across them:
```

ffmpeg -i input.mp4
```

and post the terminal output here. Of course replace the name 'input.mp4' with the name of your own file.

---

### Post by Johann-1.0 on 2013-02-12
> **andrew.46 said:**
> Mobile phones can be a little picky about codecs unfortunately. Grab one or two of the files that work and run FFmpeg across them:
```

ffmpeg -i input.mp4
```

and post the terminal output here. Of course replace the name 'input.mp4' with the name of your own file.

Done, this is what appears in prompt:

```
ffmpeg -i Forzadeldestino1-1.mp4 
FFmpeg version SVN-r0.5.9-4:0.5.9-0ubuntu0.10.04.3, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.9-0ubuntu0.10.04.3 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Jan 24 2013 19:42:59, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 30000.00 (30000/1) -> 29.97 (30000/1001)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'Forzadeldestino1-1.mp4':
  Duration: 00:26:17.59, start: 0.000000, bitrate: 2355 kb/s
    Stream #0.0(und): Video: mpeg4, yuv420p, 480x360 [PAR 1:1 DAR 4:3], 29.97 tbr, 29.97 tbn, 30k tbc
    Stream #0.1(und): Audio: mp3, 48000 Hz, stereo, s16, 112 kb/s
At least one output file must be specified

```

Note: if this is helpful, I used acidrip to rip my DVD's to my computer in an .avi format...in acidrip could be read "codec: mp3lame".

---

### Post by andrew.46 on 2013-02-12
I am sorry I actually meant files that played on your phone, sorry for the confusion!

---

### Post by Johann-1.0 on 2013-02-12
> **andrew.46 said:**
> I am sorry I actually meant files that played on your phone, sorry for the confusion!
Well, I can't use ffmpeg on my cell phone, but I read "File Format not supported"..but trust me, it has nothing to do with the cellphone, because it plays mp4 and 3gp files well...the only files it can't play are those i created with ffmpeg.

---

### Post by FakeOutdoorsman on 2013-02-12
It has everything to do with the phone. If you find a video that works on the phone, and copy it to your computer, you can obtain the details of the file with ffmpeg. This information can be used to create a video that may work on the phone.

---

### Post by andrew.46 on 2013-02-12
> **Johann-1.0 said:**
> Well, I can't use ffmpeg on my cell phone, but I read "File Format not supported"..but trust me, it has nothing to do with the cellphone, because it plays mp4 and 3gp files well...the only files it can't play are those i created with ffmpeg.

As FakeOutdoorsman has mentioned you need to get one of the successful video files from your phone to your computer, can you hook in a usb cable and drag one across or bluetooth one across? The mp4 container can hold many different codecs and your phone has an aversion to some of these or perhaps to some small setting within an otherwise acceptable codec...

---

### Post by Paddy Landau on 2013-02-12
> **FakeOutdoorsman said:**
> libav users should use avconv instead of the libav version of ffmpeg.
Thank you for your replies, FakeOutdoorsman.

I see on the [ffmpeg download page]("http://www.ffmpeg.org/download.html"):
> FFmpeg Ubuntu packages for Precise, Oneiric, Natty, Maverick, and Lucid (amd64, i386) are available at [Jon Severinsson's FFmpeg PPA]("https://launchpad.net/~jon-severinsson/+archive/ffmpeg").Is it sufficient for me to add that PPA and update ffmpeg that way? Or will there be conflicts with Ubuntu?

---

### Post by Johann-1.0 on 2013-02-12
Ooooooooooook, sorry for the misunderstanding.

Here is the prompt message:

```

ffmpeg -i gutenacht.3gp 
FFmpeg version SVN-r0.5.9-4:0.5.9-0ubuntu0.10.04.3, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.9-0ubuntu0.10.04.3 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Jan 24 2013 19:42:59, gcc: 4.4.3
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'gutenacht.3gp':
  Duration: 00:05:42.75, start: 0.000000, bitrate: 84 kb/s
    Stream #0.0(und): Audio: aac, 22050 Hz, mono, s16
    Stream #0.1(und): Video: mpeg4, yuv420p, 176x144 [PAR 1:1 DAR 11:9], 12 tbr, 12 tbn, 12 tbc
At least one output file must be specified

```

This video works great...but is in 3gp...so it could be good to try with 3gp instead of mp4 with ffmpeg.

In fact, I'm observing that only 3gp videos play ok...in mp4 files only works the sound, not the images. How can I convert to 3gp instead in ffmpeg?

---

### Post by evilsoup on 2013-02-12
To use 3gp, simply use .3gp instead of .mp4 for your output.

---

### Post by Johann-1.0 on 2013-02-12
> **evilsoup said:**
> To use 3gp, simply use .3gp instead of .mp4 for your output.

It doesn't work :(

```
Forzadeldestino1-1.avi

convertirarchivos: 29: -acodec: not found
FFmpeg version SVN-r0.5.9-4:0.5.9-0ubuntu0.10.04.3, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.9-0ubuntu0.10.04.3 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Jan 24 2013 19:42:59, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 30000.00 (30000/1) -> 29.97 (30000/1001)
Input #0, avi, from 'Forzadeldestino1-1.avi':
  Duration: 00:26:17.59, start: 0.000000, bitrate: 2364 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 480x360 [PAR 1:1 DAR 4:3], 29.97 tbr, 29.97 tbn, 30k tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 112 kb/s
Output #0, 3gp, to 'Forzadeldestino1-1.3gp':
    Stream #0.0: Video: h263, yuv420p, 480x360 [PAR 1:1 DAR 4:3], q=2-31, 200 kb/s, 90k tbn, 29.97 tbc
    Stream #0.1: Audio: 0x0000, 48000 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[h263 @ 0x1206100]The specified picture size of 480x360 is not valid for the H.263 codec.
Valid sizes are 128x96, 176x144, 352x288, 704x576, and 1408x1152. Try H.263+.
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height

```

---

### Post by evilsoup on 2013-02-12
I would recommend upgrading to a more up-to-date version of fmpeg, according to your terminal your version is from 2009! [this PPA](https://launchpad.net/~jon-severinsson/+archive/ffmpeg) is a good one. I think that what I am about to write will not work on the version you have at the moment.

Once you've done that, the following command *should* create an output file with the same parameters to your 3gp file that works on your phone:

```

##  convert 16:9 video
ffmpeg -i input.avi -map 0:a -map 0:v -filter:v 'scale=176:-1,pad=176:144:(ow-iw)/2:(oh-ih)/2' \
-c:v mpeg4 -q:v 4 -c:a aac -b:a 96k -ac 1 -ar 22050 -strict experimental output.3gp

##  convert 4:3 video
ffmpeg -i input.avi -map 0:a -map 0:v -filter:v 'scale=-1:144,pad=176:144:(ow-iw)/2:(oh-ih)/2' \
-c:v mpeg4 -q:v 4 -c:a aac -b:a 96k -ac 1 -ar 22050 -strict experimental output.3gp

```

The scale video filter... well, scales the video down - the 16:9 does so width-wise, scaling the height to keep in ratio with the width, and the 4:3 one does it height-wise. This is then fed to the pad, which puts the scaled video over the centre of a black box with a size of 176x144.

-ac 1 -ar 22050 makes the audio mono and gives it a sample rate of 22050 Hz. These are probably not strictly necessary. -map 0:a -map 0:v tells ffmpeg to make the audio be the first stream (stream 0) and the video be after the audio. Again, probably not necessary. The rest of the options are standard ffmpeg encoder things.

---

### Post by andrew.46 on 2013-02-12
Another small thing to consider is that sometimes phones and phone-like devices will baulk at FFmpeg's ffourcc for mpeg4 encoding so perhaps add:

```

-vtag XVID

```

in the video section...

---

### Post by Johann-1.0 on 2013-02-12
> **evilsoup said:**
> I would recommend upgrading to a more up-to-date version of fmpeg, according to your terminal your version is from 2009! [this PPA](https://launchpad.net/~jon-severinsson/+archive/ffmpeg) is a good one. I think that what I am about to write will not work on the version you have at the moment.

Once you've done that, the following command *should* create an output file with the same parameters to your 3gp file that works on your phone:

```

##  convert 16:9 video
ffmpeg -i input.avi -map 0:a -map 0:v -filter:v 'scale=176:-1,pad=176:144:(ow-iw)/2:(oh-ih)/2' \
-c:v mpeg4 -q:v 4 -c:a aac -b:a 96k -ac 1 -ar 22050 -strict experimental output.3gp

##  convert 4:3 video
ffmpeg -i input.avi -map 0:a -map 0:v -filter:v 'scale=-1:144,pad=176:144:(ow-iw)/2:(oh-ih)/2' \
-c:v mpeg4 -q:v 4 -c:a aac -b:a 96k -ac 1 -ar 22050 -strict experimental output.3gp

```

The scale video filter... well, scales the video down - the 16:9 does so width-wise, scaling the height to keep in ratio with the width, and the 4:3 one does it height-wise. This is then fed to the pad, which puts the scaled video over the centre of a black box with a size of 176x144.

-ac 1 -ar 22050 makes the audio mono and gives it a sample rate of 22050 Hz. These are probably not strictly necessary. -map 0:a -map 0:v tells ffmpeg to make the audio be the first stream (stream 0) and the video be after the audio. Again, probably not necessary. The rest of the options are standard ffmpeg encoder things.

Thank you very much man...for your time and your explanation. I will try it. And all of you guys...I will try and if it works, I'll let you know.

---

