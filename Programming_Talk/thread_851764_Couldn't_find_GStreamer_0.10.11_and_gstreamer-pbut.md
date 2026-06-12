---
title: "Couldn't find GStreamer 0.10.11 and gstreamer-pbutils"
date: 2008-07-07
forum: Programming Talk
---

### Post by yinglcs2 on 2008-07-07
Can you pleas what libraries I need to install in order to resolve this 
'configure' error:

configure: error: Couldn't find GStreamer 0.10.11 and gstreamer-pbutils 
0.10.15.

From the package manager, I already have:
gstreamer0.10-alsa
gstreamer0.10-ffmpeg
libstreamer0.10-0
libstreamer0.10-dev

Thank you.

---

### Post by mclaud2000 on 2008-07-26
It's called libgstreamer-plugins-base0.10-dev You can find it in synaptic.

---

### Post by flerchjj on 2009-02-23
Thank you from me as well. I didn't see it in synaptics package manager, but an apt-get install worked perfectly and now this error is resolved.:D

---

