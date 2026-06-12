---
title: "Gstreamer opengl examples"
date: 2015-04-01
forum: Programming Talk
---

### Post by xors on 2015-04-01
I don't know what to do. I need to render opengl frame. Trying to run and example

gst-launch-1.0 -v videotestsrc ! "video/x-raw-rgb" ! glupload ! gstgldownload ! "video/x-raw-rgb" ! ximagesink

or

gst-launch-0.10 -v videotestsrc ! "video/x-raw-rgb" ! glupload ! gstgldownload ! "video/x-raw-rgb" ! ximagesink

It says only:
 WARNING: erroneous pipeline: no element "glupload"

I've compiled and installed gst-plugins-gl... Nothing helps.

---

### Post by ethan26 on 2015-04-04
I am a noob what is open gl or Gstreamer

---

