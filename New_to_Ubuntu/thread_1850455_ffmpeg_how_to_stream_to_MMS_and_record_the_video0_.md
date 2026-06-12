---
title: "ffmpeg: how to stream to MMS:// and record the video0 at the same time?"
date: 2011-09-26
forum: New to Ubuntu
---

### Post by frenchn00b on 2011-09-26
Hello,

I would like to know whether this could be possible? 

I use for the moment: 

```

ffmpeg  -r 5 -s 640x480 -f video4linux2 -i /dev/video0  -itsoffset -5 http://localhost:8090/feed1.ffm


```

thank you!!

---

