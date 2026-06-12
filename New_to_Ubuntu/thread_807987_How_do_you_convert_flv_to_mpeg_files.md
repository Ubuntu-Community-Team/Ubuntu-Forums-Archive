---
title: "How do you convert flv to mpeg files?"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by giordun on 2008-05-26
Topic Title :)

---

### Post by dRock1286 on 2008-05-26
avidemux ->available in the repositories

---

### Post by sica07 on 2008-05-26
I use ffmpeg:

[I] $ sudo apt-get install ffmpeg

 $ ffmpeg -i video.flv -ab 56 -ar 22050 -b 500  -s 320x240 video.mpg[/I]

where: 
-ab  audio bitrate (default=64kbps)
-ar  audio samplerate (default=44100hz)
-b    video bitrate (default=2000kbps)
-s    display size (default=160×128px)

---

### Post by giordun on 2008-05-26
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 12 2008 14:31:53, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu4)
jokes.flv: I/O error occured
Usually that means that input file is truncated and/or corrupted.

---

### Post by giordun on 2008-05-26
> **dRock1286 said:**
> avidemux ->available in the repositories

How do you do it with avidemux?

---

### Post by sica07 on 2008-05-27
$sudo apt-get install avidemux
Start avidemux. 
Open video file, select 'auto' menu and choose which format you want (in this case, mpeg), click save that's it.

---

### Post by billgoldberg on 2008-05-27
The easy way:

either this:
[http://linuxowns.wordpress.com/2008/05/07/pytube-media-converter/](http://linuxowns.wordpress.com/2008/05/07/pytube-media-converter/)

or this:
[http://linuxowns.wordpress.com/2008/01/08/ubuntu-video-converter/](http://linuxowns.wordpress.com/2008/01/08/ubuntu-video-converter/)

---

