---
title: "mencoder, recording in an edit friendly format?"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by linkmaster03 on 2008-06-12
Currently I use my webcam with mencoder to record, and it saves as FFmpeg MPEG-4. I cannot edit this with Open Movie Editor, and the owner of that program says it's not good to edit. How can I record in a more friendly format with mencoder? Currently, I use this:

```
mencoder tv:// -tv driver=v4l:width=320:height=240:device=/dev/video0:forceaudio:adevice=/dev/dsp1 -ovc lavc -oac mp3lame -lameopts cbr:br=64:mode=3 -o ~/Desktop/webcam.avi

```

---

### Post by wolfen69 on 2008-06-12
you could always change the format(after recording) with winff.

---

### Post by linkmaster03 on 2008-06-12
It can't find any of the codecs and I'd rather it be recorded directly into the format rather than converting it.

---

### Post by niteshifter on 2008-06-12
Hi,

```
mencoder -ovc help
```

will show you what codecs are available to mencoder. Pick something other than lavc, raw is always an option - but that's going to make for some huge files.

---

### Post by hypocratus on 2008-06-16
You can specify a different codec with lavc. I used the following option:
-lavcopts vcodec=mpeg2video 
The only problem with that is it will be in an avi container.

---

