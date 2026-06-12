---
title: "[SOLVED] Avi. to MP4"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by otamotacon on 2008-10-11
I am trying to put videos on my little sisters Ipod. Certain videos work others don't. I'm using GTK pod.

Do i need to convert my video files to MP4 for them to work? If so how do i go about doing this?

---

### Post by SuperSonic4 on 2008-10-11
I think you do. Try ```
!/bin/bash
cd ~/dwhelper
for i in *.avi; do ffmpeg -i "$i" -avcodec copy "`echo "$i" | sed -r -e 's/(.*)\.avi$/\1.mp4/'`"; done
```

No idea if it will work, I adapted one for my own use to this. So good luck :p

make ~/dwhelper the directory in which your avi files are stored

---

### Post by otamotacon on 2008-10-11
I tried it but came up with this:
> FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 23 2008 22:38:24, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
*.avi: I/O error occured
Usually that means that input file is truncated and/or corrupted.


---

### Post by chris200x9 on 2008-10-11
you can try avidemux it has a nice GUI too :guitar:

---

