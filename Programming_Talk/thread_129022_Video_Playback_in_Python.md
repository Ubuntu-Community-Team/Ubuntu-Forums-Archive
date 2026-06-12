---
title: "Video Playback in Python"
date: 2006-02-12
forum: Programming Talk
---

### Post by noob_Lance on 2006-02-12
Hey, I want to make a small simple yet effective program that will play videos using python. Anyone know anything about this except for pyMedia? pymedia dosnt work... there own sample code gives errors about there own product :p

~Lance

---

### Post by ow50 on 2006-02-12
GStreamer Python Bindings
[http://gstreamer.freedesktop.org/modules/gst-python.html](http://gstreamer.freedesktop.org/modules/gst-python.html)

I haven't tried it myself. At least it should be easy, but is it mature enough and properly documented, that I don't know.

---

### Post by nszabolcs on 2006-02-13
[http://www.pymedia.org](http://www.pymedia.org) for codecs (~ffmpeg binding)
[http://www.pygame.org](http://www.pygame.org) for displaying the video (SDL binding)
Edit: oops, now i see you don't want pymedia, sorry (are you trying the latest code?)

---

