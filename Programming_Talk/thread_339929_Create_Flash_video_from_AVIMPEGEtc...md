---
title: "Create Flash video from AVI/MPEG/Etc.."
date: 2007-01-16
forum: Programming Talk
---

### Post by kaptainlange on 2007-01-16
I recently got a Wii, and it comes with a web browser and flash player.  A fun web project I thought would be to allow a way to browse my video collection and also watch the videos.  Question is, are there any libraries that allow for conversion of regular video to SWF.  Language doesn't really matter, though it'd be preferable if PHP could do it.

I've found libming, however I'm not exactly sure if this is what I want.  Does the GPL flash version allow this sort of thing?

---

### Post by tpg on 2007-01-16
I'm not sure about programming libraries, but might mencoder be able to write flash video files? Also try
```
 ffmpeg -i INPUT.avi OUTPUT.flv 
```
(you'll obviously need ffmpeg and appropriate codecs installed) Hope this helps!

---

### Post by kaptainlange on 2007-01-16
I think that this will do me just fine, thank you very much.

---

### Post by Turtle.net on 2007-10-28
Any progress on your project ?
I would love to be able to watch my videos on my TV through the Wii ...

---

### Post by kaptainlange on 2007-10-29
Ah, nope.  I did have success with what was recommended here, but after I had made a really simply flash streamer someone had pointed out to me that other projects had already fulfilled this need.  So didn't want to reinvent the wheel.

Here is one example:
[http://www.redkawa.com/mediacenters/wiimediacenterx/](http://www.redkawa.com/mediacenters/wiimediacenterx/)

---

### Post by Turtle.net on 2007-10-29
I tried this one, but the quality of the video is really horrible and th sound is even worse....

---

### Post by xphelanx on 2007-11-02
I've tried this as well, but I can only get it to work with certain videos. I am starting to get discouraged. I'll keep looking and report back.

---

