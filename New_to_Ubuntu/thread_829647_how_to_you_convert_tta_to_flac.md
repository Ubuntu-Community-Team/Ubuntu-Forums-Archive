---
title: "how to you convert tta to flac"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by zerobinary on 2008-06-15
how to you convert tta to flac?

---

### Post by dnns123 on 2008-06-15
Try Sound Converter from the add/remove. I'm not sure if .tta is supported though...

---

### Post by akraievoy on 2011-02-03
Ubuntu 10.10 with most of medibuntu packages installed:
[LIST]
[*] FYI: rhythmbox did not play the .tta files till the moment I've installed gstreamer0.10-plugins-bad and gstreamer0.10-ffmpeg
[*] soundconverter (tta->mp3) worked for me just fine, so I guess it should as well do (tta->flac)
[*] FYI: audacity (open/export attempt) failed saying that "Audacity recognized the type of file. Importers supposedly supporting this format are 'ffmpeg-compatible files', but none of them understood file format". More or less helpful message, but soundconverter did the job anyway, so...
[/LIST]

---

### Post by vinnywright on 2011-02-03
ffmpeg dose handle this file type so winff should do what you want if you nead a GUI or just use ffmpeg on the CLI

VINNY

---

### Post by andrew.46 on 2011-02-05
There is a nice sample here:

```
wget http://samples.mplayerhq.hu/A-codecs/lossless/luckynight.tta
```

and simple enough to convert to flac:

```

andrew@skamandros~/Desktop$ **[COLOR="Red"]ffmpeg -i luckynight.tta -ab 800k luckynight.flac[/COLOR]**
FFmpeg version git-d33ed7b, Copyright (c) 2000-2011 the FFmpeg developers
  built on Jan 30 2011 19:58:08 with gcc 4.5.2
  configuration: --prefix=/usr --mandir=/usr/man --enable-postproc --enable-avfilter --enable-pthreads --enable-shared --disable-static --disable-ffserver --enable-libvorbis --enable-libmp3lame --enable-libx264 --enable-libfaac --enable-zlib --enable-nonfree --enable-gpl
  libavutil    50. 36. 0 / 50. 36. 0
  libavcore     0. 16. 1 /  0. 16. 1
  libavcodec   52.108. 0 / 52.108. 0
  libavformat  52. 94. 0 / 52. 94. 0
  libavdevice  52.  2. 3 / 52.  2. 3
  libavfilter   1. 74. 0 /  1. 74. 0
  libswscale    0. 12. 0 /  0. 12. 0
  libpostproc  51.  2. 0 / 51.  2. 0
Input #0, tta, from 'luckynight.tta':
  Metadata:
    title           : Lucky Night
    artist          : Jody Marie Gnant
    album           : Treasure Quest Soundtrack
    date            : 1995
    comment         : 1-minute .tta sample song
    track           : 9
    genre           : Soundtrack
  Duration: 00:01:00.48, start: 0.000000, bitrate: 872 kb/s
    Stream #0.0: Audio: tta, 44100 Hz, 2 channels, s16
Output #0, flac, to 'luckynight.flac':
  Metadata:
    title           : Lucky Night
    artist          : Jody Marie Gnant
    album           : Treasure Quest Soundtrack
    date            : 1995
    comment         : 1-minute .tta sample song
    TRACKNUMBER     : 9
    genre           : Soundtrack
    encoder         : Lavf52.94.0
    Stream #0.0: Audio: flac, 44100 Hz, 2 channels, s16, 800 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
Error while decoding stream #0.0te= 869.5kbits/s    
size=    6502kB time=60.50 bitrate= 880.4kbits/s    
video:0kB audio:6494kB global headers:0kB muxing overhead 0.126625%

```

My apologies to all for necroposting :)

Andrew

---

### Post by akraievoy on 2011-02-13
> **andrew.46 said:**
> ```
... -ab 800k ...
```
Oh, but why did you reduce the bitrate? I guess this option should be omitted.
Let me try a file with that and without that option, just to be sure...

UPD: oh, it looks like it does not change anything, at least files are the same size!

Thanks for your example, and don't mind that necroposting thing...

---

