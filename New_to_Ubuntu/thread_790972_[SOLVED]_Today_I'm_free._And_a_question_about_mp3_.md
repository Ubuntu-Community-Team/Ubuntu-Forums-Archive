---
title: "[SOLVED] Today I'm free. And a question about mp3 to ogg conversion. and webcam mic h"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by Mjölner on 2008-05-11
Hi all. Well today I'm free! :)

I was reinstalling cause I wanted to use the 64bit distro, And I thought.... What the hell do I need my xp dual boot for? 
And the answer was. Nothing! So I did it :) Cold turkey for me :)    

I want to say a big THANKYOU to all involved in Ubuntu and GNU/Linux for all the work you have put in (more than I can fathom) and a great user experience, with everything just working out the box. 
I had to install proprietary drivers for grafix and mp3 support, but that's it! 

Perhaps someone can suggest a program to convert my mp3's to ogg (my "portable digital audio player" ;)  supports it which is great) 

One other thing..........   Can the mic on my usb webcam (logitech quickcam) work with Ubuntu?

---

### Post by spiderbatdad on 2008-05-11
ffmpeg is reliable and flexible. It is a command line tool. You can get it from synaptic. Running:  man ffmpeg  will provide you with the manual pages, also there is a good deal of info you can google regarding ffmpeg. For mp3's you will also want the lame & lame-extras packages.
An example of ffmpeg conversion is to cd into the directory containing the files, for example, mp3 on your Desktop:```
cd Desktop
ffmpeg -i your_file.mp3 your_file.ogg

```

[http://snippets.dzone.com/user/dirtyaffairs](http://snippets.dzone.com/user/dirtyaffairs)

---

### Post by mmb1 on 2008-05-11
I reccomend "sound converter" for converting your mp3s, and congrats on your freedom!

---

### Post by Mjölner on 2008-05-11
Hi,

Thanks for your fast help

Installed what u suggested. I took a quick look at the man pages and then attempted...
but to no avail.
The mp3 file plays, and it is at the bitrate that I used.
This is what I got out.

****@ubuntu:~/Desktop$ ffmpeg -i 04 Deine Tränen.mp3 -ab 320k 04 Deine Tränen.ogg
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 12 2008 15:36:03, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu4)
04: I/O error occured
Usually that means that input file is truncated and/or corrupted.
****@ubuntu:~/Desktop$

Will look into the other program too.

Thanks again

---

### Post by spiderbatdad on 2008-05-11
Should have mentioned, file names that contain spaces require "quotes." try:
```
ffmpeg -i "04 Deine Tränen.mp3" -ab 320k "04 Deine Tränen.ogg"
```

---

### Post by Mjölner on 2008-05-11
Thanks for that. It worked. but with audio not perfect. It's like a small echo/doubling effect :(

Do you know what it might be?

It didn't happen with  "sound converter", but the highest GUI bit rate is 256k, and I've got a feeling(!? imagined?) I'm loosing something.

---

### Post by spiderbatdad on 2008-05-11
not sure. try with out the -ab 320k flag. Googling should turn up some good tips to ffmpeg. My usage is pretty basic. I convert a little bit of AV. And usually ogg to mp3, or avi to mp4

---

### Post by Mjölner on 2008-05-11
Thanks. I'll look into it.

Will let u know what I find out :)

Thor

---

### Post by Mjölner on 2008-05-24
This it a reply to make this thread a solved thread. Although, technically, all my questions have not been answered. I have reached some conclusions, although some may be incorrect. This would be due to my newbie self.

Conversion between mp3 and ogg is of course lossy, and they use different compression/conversion algorithms, therefore the quality *will* degrade.

But I found that "oggconvert" in the repositories, did a fantastic job of conversion (at its highest quality setting) without noticeable loss to the "original" mp3. It converts up to 499kbs! so a 3minute file at 320kbs was 7 meg is now 499kbs and 9 meg.
I think that for all my CD imports from now on I will use flac, and then convert to ogg when I want the audio on my "portable digital audio player".

wasn't able to find out why, when I was using the terminal, I got such strange audio peculiarities.

Mjölner

---

