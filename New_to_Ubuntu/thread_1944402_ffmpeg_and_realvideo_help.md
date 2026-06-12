---
title: "ffmpeg and realvideo help"
date: 2012-03-21
forum: New to Ubuntu
---

### Post by ginestre on 2012-03-21
There must be a simple way to use ffmpeg (or some other animal) to save a realvideo video to my PC? I need to salvage some old archived video material from the web,but it's in realvideo format and my knowledge doesn't reach that far.

---

### Post by Linux_junkie on 2012-03-21
Not too sure if it supports realvideo format but have you tried Pitivi to encode to another format?

---

### Post by SeijiSensei on 2012-03-21
I'm not sure I entirely understand your question.

Can you download the files in Real format but cannot view them?  Or are they streams that you need to capture on a local machine?

I'm pretty sure ffmpeg and mplayer/mencoder include codecs for Real Media in the libavcodec library.  Have you tried simply running:

```
ffmpeg -i file.rm file.mp4
```

or similar commands?  How about "mplayer file.rm"?  Does that display the file on-screen?

Capturing streams is more complicated depending on  whether they are protected with DRM scheme.

---

### Post by kazztan0325 on 2012-03-21
Hi ginestre,

I guess maybe you would be able to refer this thread:
**"RM file to AVI or XVID converter"**
[http://ubuntuforums.org/showthread.php?t=854205]("http://ubuntuforums.org/showthread.php?t=854205")

Hope this helps.

---

