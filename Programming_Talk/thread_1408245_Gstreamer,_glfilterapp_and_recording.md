---
title: "Gstreamer, glfilterapp and recording"
date: 2010-02-16
forum: Programming Talk
---

### Post by Eirel on 2010-02-16
Hi guys.

Here's my matter: I've been trying since several days to encode an opengl/gstreamer context in an ogg files. For this, I use glupload, glfilterapp (to modify the drawing function), glupload, and the encoding pipe (theoraenc, vorbisenc, oggmux and filesink). 
My pipeline looks like:
gst-launch \
\
videotestsrc ! ffmpegcolorspace ! "video/x-raw-rgb" ! glupload ! glfilterapp ! gldownload ! theoraenc ! oggmux ! filesink location="Whyyy.ogg"

But I don't understand why, it doesn't works. If I change everything since theoraenc to an ximagesink, the result is well displayed on the screen, but the recording doesn't work. And I really need to be able to do this...

Has someone ever try to do something like that?

---

### Post by SledgeHammer_999 on 2010-02-16
When you run that pipeline through gst-launch does it output some warnings/errors in the terminal? If yes, please post them here.

---

### Post by Eirel on 2010-02-16
Well I've actually found the answer, sorry not to answer before...
Actually, it seems that I need to cast the output video to x-raw-yuv format before I can record it.

---

