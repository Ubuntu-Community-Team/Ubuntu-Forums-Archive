---
title: "How to stream my desktop to Twitch.tv?"
date: 2014-05-06
forum: New to Ubuntu
---

### Post by bshatt1987 on 2014-05-06
Hi, so I want to stream my desktop to Twitch.tv and I've installed VLC but I can't for the life of me figure out what the heck I'm supposed to do.  
I've tried googling but all I can find is people saying something about FFMPEG and then they give some kind of shell code but I don't know what I'm supposed to do with it.  VLC has a wizard but it's not a very friendly wizard.  So does anyone know how I can do this easily?  I'm really running out of ideas.  

Edit - 
Okay, so I figured out a way to stream, not using VLC or ffmpeg, but avconv.   Having a couple problems now though, my sound on the stream is just a  lot of really loud static unless I turn off the mic input.  
And then  the biggest problem is that it streams at a rather low bitrate and has  to buffer all the time.  It starts out strong for a few seconds, but  quickly decreases to about 140-165 kbps.  Here's the code in the shell  script that I'm using if anyone has any ideas.  :o
```
#!/bin/bash
    INRES="1366x768" # input resolution
    OUTRES="1366x768"
    OFFSET="0,0"
    FPS="10" # target FPS
    QUAL="fast"  # one of the many FFMPEG preset
    STREAM_KEY="live_61624341_oJeqP61PL61i85XmHiFcxUUjQ2Dnwe"
    URL="rtmp://live.twitch.tv/app/$STREAM_KEY"
     
    avconv -f x11grab -s "$INRES" -r "$FPS" -i :0.0+$OFFSET -ab 180k \
    -f alsa -ac 2 -i pulse -vcodec libx264 -crf 30 -preset "$QUAL" -s "1366x768" \
    -vol 5000 -acodec libmp3lame -ar 44100 -threads 0 \
    -f flv "$URL"
```

---

### Post by FakeOutdoorsman on 2014-05-06
See [Encoding for streaming sites with FFmpeg](http://trac.ffmpeg.org/wiki/EncodingForStreamingSites).

Note that this guide is for ffmpeg from FFmpeg, not the fake "ffmpeg" or avconv from the Libav fork. If you want the real thing see [https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu](https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu)

---

### Post by bshatt1987 on 2014-05-06
> **FakeOutdoorsman said:**
> See [Encoding for streaming sites with FFmpeg]("http://trac.ffmpeg.org/wiki/EncodingForStreamingSites").

Note that this guide is for ffmpeg from FFmpeg, not the fake "ffmpeg" or avconv from the Libav fork. If you want the real thing see [https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu](https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu)

Okay, I compiled the real ffmpeg successfully (I think).  But when I try to run it with this code: 
```

$ ffmpeg -f alsa -ac 2 -i hw:0,0 -f x11grab -framerate 30 -video_size 1280x720 \
-i :0.0+0,0 -vcodec libx264 -preset veryfast -maxrate 1984k -bufsize 3968k \
-vf "format=yuv420p" -g 60 -acodec libmp3lame -b:a 96k -ar 44100 \
-f flv rtmp://live.twitch.tv/app/<stream key>
``` 
It tells me ```
[alsa @ 0x211af80] cannot open audio device hw:0,0 (No such file or directory)
hw:0,0: Input/output error
```

---

### Post by bshatt1987 on 2014-05-07
Okay, so I figured out a way to stream, not using ffmpeg, but avconv.   Having a couple problems now though, my sound on the stream is just a  lot of really loud static unless I turn off the mic input.  
And then  the biggest problem is that it streams at a rather low bitrate and has  to buffer all the time.  It starts out strong for a few seconds, but  quickly decreases to about 140-165 kbps.  Here's the code in the shell  script that I'm using if anyone has any ideas.  :o
```
#!/bin/bash
    INRES="1366x768" # input resolution
    OUTRES="1366x768"
    OFFSET="0,0"
    FPS="10" # target FPS
    QUAL="fast"  # one of the many FFMPEG preset
    STREAM_KEY="live_61624341_oJeqP61PL61i85XmHiFcxUUjQ2Dnwe"
    URL="rtmp://live.twitch.tv/app/$STREAM_KEY"
     
    avconv -f x11grab -s "$INRES" -r "$FPS" -i :0.0+$OFFSET -ab 180k \
    -f alsa -ac 2 -i pulse -vcodec libx264 -crf 30 -preset "$QUAL" -s "1366x768" \
    -vol 5000 -acodec libmp3lame -ar 44100 -threads 0 \
    -f flv "$URL"
```

---

### Post by FakeOutdoorsman on 2014-05-08
> **bshatt1987 said:**
> Okay, I compiled the real ffmpeg successfully (I think).  But when I try to run it with this code: 
```

$ ffmpeg -f alsa -ac 2 -i hw:0,0 -f x11grab -framerate 30 -video_size 1280x720 \
-i :0.0+0,0 -vcodec libx264 -preset veryfast -maxrate 1984k -bufsize 3968k \
-vf "format=yuv420p" -g 60 -acodec libmp3lame -b:a 96k -ar 44100 \
-f flv rtmp://live.twitch.tv/app/<stream key>
``` 
It tells me ```
[alsa @ 0x211af80] cannot open audio device hw:0,0 (No such file or directory)
hw:0,0: Input/output error
```

Please show your complete ffmpeg console output.  Are you sure "hw:0,0" is the correct input device? You can see a list of devices with "arecord -l".

---

### Post by bshatt1987 on 2014-05-08
```
ffmpeg - ffmpeg version 2.2.git Copyright (c) 2000-2014 the FFmpeg developers
  built on May  6 2014 19:38:46 with gcc 4.8 (Ubuntu 4.8.2-19ubuntu1)
  configuration: --prefix=/home/ben/ffmpeg_build --extra-cflags=-I/home/ben/ffmpeg_build/include --extra-ldflags=-L/home/ben/ffmpeg_build/lib --bindir=/home/ben/bin --extra-libs=-ldl --enable-gpl --enable-libass --enable-libfdk-aac --enable-libfreetype --enable-libmp3lame --enable-libopus --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-nonfree --enable-x11grab
  libavutil      52. 81.100 / 52. 81.100
  libavcodec     55. 60.103 / 55. 60.103
  libavformat    55. 37.102 / 55. 37.102
  libavdevice    55. 13.101 / 55. 13.101
  libavfilter     4.  5.100 /  4.  5.100
  libswscale      2.  6.100 /  2.  6.100
  libswresample   0. 18.100 /  0. 18.100
  libpostproc    52.  3.100 / 52.  3.100
Hyper fast Audio and Video encoder
usage: ffmpeg [options] [[infile options] -i infile]... {[outfile options] outfile}...
```

arecord -l:
```
**** List of CAPTURE Hardware Devices ****
card 1: Generic_1 [HD-Audio Generic], device 0: ALC269VC Analog [ALC269VC Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```

---

