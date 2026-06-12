---
title: "convert flv to mpeg"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by dineshs on 2008-11-27
Using the following command I tried to convert an flv to mpeg , but the converted stream has no sound .please help

ffmpeg -i video.flv -ab 56 -ar 22050 -b 500  -s 320x240 video.mpg

---

### Post by dineshs on 2008-11-28
experts please help

---

### Post by alwayshere on 2008-11-28
theres an online app 
 [www.vixy.net](www.vixy.net)


 that should sort ya out

---

### Post by dineshs on 2008-11-28
thank you

---

### Post by FakeOutdoorsman on 2008-11-29
> **dineshs said:**
> Using the following command I tried to convert an flv to mpeg , but the converted stream has no sound .please help

ffmpeg -i video.flv -ab 56 -ar 22050 -b 500  -s 320x240 video.mpg

FFmpeg says: > The bitrate parameters are set too low. It takes bits/s as argument, not kbits/s.  Just add "k" to your bitrates:
```
ffmpeg -i video.flv -ab 56k -ar 22050 -b 500k -s 320x240 video.mpg
```

---

