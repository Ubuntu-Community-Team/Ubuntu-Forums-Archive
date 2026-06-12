---
title: "Webcam: take one snapshot with mencoder"
date: 2012-02-04
forum: New to Ubuntu
---

### Post by honeybear on 2012-02-04
Hi, I would like to one snapshot with mencoder as png using mencoder.

my command for video is regular,
```
mencoder tv:// -tv driver=v4l2:device=/dev/video0:forceaudio:adevice=/dev/dsp2 -ovc lavc -oac mp3lame -lameopts cbr:br=64:mode=3 -o ~/mywebcam.avi
```

How can it be for making a single png please using mencoder? Thanks

---

