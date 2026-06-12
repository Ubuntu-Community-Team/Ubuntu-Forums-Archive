---
title: "record audio from youtube with audacity"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by ontherooftop on 2008-07-21
I have tried recording tracks from you tube on audacity and 
I recorded it and it seems to say check input output and something
else in configuration can someone help me step by step to record 
audio( I dont have a mic)  record audio from my soundcard on my computer
and make a audio or mp3 file from it , Thanks. first time trying audacity.

---

### Post by ice60 on 2008-07-21
did you try looking at youtube? i watched the first 20 seconds or so of this one and it looks like he's doing what you want!
[http://www.youtube.com/watch?v=f9_pSLG0LZQ](http://www.youtube.com/watch?v=f9_pSLG0LZQ)

there are online services that will extract the mp3 for you too, like 
[http://vixy.net/](http://vixy.net/)
[http://www.listentoyoutube.com/](http://www.listentoyoutube.com/)

---

### Post by stmiller on 2008-07-22
It is possible in Linux to record internally from one source to another. No need for a mic and static noise. The software that does this is jack. Install qjackctl for a gui.

---

### Post by jpkotta on 2008-07-22
The flash player will download the videos to /tmp.  They're named randomly, e.g. FlashDlna4t.  You can play them with mplayer (and others I would suppose).  If you can play them, there is a way to extract the audio.  You can do it with avidemux, I just tried.  The one I tried used mp3 for the audio (avidemux will tell you this).

---

### Post by heiNey on 2008-08-07
i just tried this and avidemux says it cant open the file

---

### Post by eightmillion on 2008-08-07
You can use mplayer to dump the audio:
> mplayer -dumpaudio input.flv -dumpfile output.mp3

---

### Post by heiNey on 2008-08-07
cool that worked..thanks...is there a way to specify a bitrate?  it comes out at 64kbps...or is that the best that youtube videos can be encoded at?

---

### Post by eightmillion on 2008-08-07
Generally the audio from youtube videos is low bitrate. You can dump and reencode at the same time with ffmpeg although I don't think it provides any real quality differences.
> ffmpeg -i input.flv -ab 128 -ar 44100 output.mp3

---

