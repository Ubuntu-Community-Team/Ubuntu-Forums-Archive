---
title: "Video for Ipods"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by bernie51 on 2008-09-27
Hi!

I've been trying to convert .avi files into .mp4 files in order to play video on my Ipod. I believe I converted the files correctly. (I used Avidemux.) However I can't move them onto my Ipod. I've been trying to use Gtkpod to do this. Any suggestions? I'm very new to Ubuntu. Thanks!

---

### Post by Xiong Chiamiov on 2008-09-28
Does gtkpod give you an error?  If so, what is it specifically?

Be aware that .avi is a container format, meaning that there can be any video (and audio) codec inside.  If the inside video is already in H264, then you should be able to just rename the extension from .avi to .mp4.

---

### Post by RequinB4 on 2008-09-28
[https://help.ubuntu.com/community/iPodVideoEncoding](https://help.ubuntu.com/community/iPodVideoEncoding)

Worked perfectly for me

---

### Post by doorknob60 on 2008-09-28
Use WinFF, I use it for converting videos for my Sansa e260 (Rockboxed), it has loads of presets and a nice GUI thats's easy to use. [http://code.google.com/p/winff/](http://code.google.com/p/winff/) There's debs for 64 bit (AMD64/x86_64) and 32 bit (i386/x86). (for 64 bit you have to click "Show All" in the featured downloads). If it doesn't convert the right type of video you want, try installing Medibuntu's version of FFmpeg: [http://packages.medibuntu.org/hardy/ffmpeg.html](http://packages.medibuntu.org/hardy/ffmpeg.html) It supports more formats which might be needed.

---

