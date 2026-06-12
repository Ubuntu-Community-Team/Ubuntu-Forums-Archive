---
title: "mpeg-4 and kino"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by todaymueller on 2008-11-08
I have just bought a sanyo video camera .[ vpc-ca65 ] It uses mpeg-4 and a USB connector .
I cannot get kino to import any of the video I have taken .
Are there any other video editing programs that would work ?
Or can anybody tell me how to get kino to work ?
I can get the video clips to play on VLC but I really need a video editing program that supports mpeg-4 or a program that converts mpeg-4 to DV .
I have tried ffmpeg but can not get it to work .
This is what I get ;


john@john-desktop:~$ ffmpeg -i original.mov -target pal-dv new.dv
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
libavutil version: 1d.49.3.0
libavcodec version: 1d.51.38.0
libavformat version: 1d.51.10.0
built on Jul 23 2008 22:38:24, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
original.mov: I/O error occured
Usually that means that input file is truncated and/or corrupted.
john@john-desktop:~$

---

### Post by FakeOutdoorsman on 2008-11-08
Everytime I've encountered this error my input file was corrupted or screwy.  Did you try re-importing it?

---

