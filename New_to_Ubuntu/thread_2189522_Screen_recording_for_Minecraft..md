---
title: "Screen recording for Minecraft."
date: 2013-11-22
forum: New to Ubuntu
---

### Post by swordm-1993 on 2013-11-22
Hey, I'm a new user when it comes to linux and Ubuntu and I had previously been using Windows seven and Debut Video Capture for making videos (Audio included) for my Minecraft sessions. However after switching over I've found that Debut doesn't really work even with WINE. The same goes for RecordMyDesktop, The video was rather crappy and its "Records only active parts of screen" Thing left dead bits over part of the video. Is there anything out there that does a fair and easy job of recording Audio and video for Ubuntu/Linux and if so would you be willing to help me install it? 

Thanks in advance
~Sword

---

### Post by stinkeye on 2013-11-22
Try vokoscreen.
```
sudo add-apt-repository ppa:vokoscreen-dev/vokoscreen
sudo apt-get update
sudo apt-get install vokoscreen
```

---

### Post by swordm-1993 on 2013-11-23
Alright, so I downloaded it as you said and whenever I press start it kind of shuffles across "Start, stop, and pause" (the highlighted button I mean) real quick once and stops. When I try Window mode it keeps doing that repeatedly until I hit stop or pause and then it give me "[vokoscreen] ffmpeg has crashed on (insert time and day, ex Saturday, 09:29)"

I also tried changing the codec, the file type, and the player all with the same results.

---

### Post by philinux on 2013-11-23
> **swordm-1993 said:**
> Alright, so I downloaded it as you said and whenever I press start it kind of shuffles across "Start, stop, and pause" (the highlighted button I mean) real quick once and stops. When I try Window mode it keeps doing that repeatedly until I hit stop or pause and then it give me "[vokoscreen] ffmpeg has crashed on (insert time and day, ex Saturday, 09:29)"

I also tried changing the codec, the file type, and the player all with the same results.

VLC works a treat for screen recording.

---

### Post by swordm-1993 on 2013-11-23
O.o how would one use a media player to record their screen?

---

### Post by philinux on 2013-11-23
> **swordm-1993 said:**
> O.o how would one use a media player to record.

[http://www.howtogeek.com/120202/](http://www.howtogeek.com/120202/)

Increase frame rate to suit.

---

