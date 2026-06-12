---
title: "Gstreamer pipeline problems"
date: 2008-12-16
forum: Programming Talk
---

### Post by fm232 on 2008-12-16
using python I've got a gstreamer pipeline going with a v4l2src and outputting to an xvimagesink, with a queue and some other plugins in the middle (like videocrop) which works fine; the problem is that when I try to pause the pipeline using pipline.set_state(gst.STATE_PAUSED) the whole application crashes (as in it just stops working until linux times out and allows me to kill it). I've got absolutely no idea why it does this. Has anyone got any ideas? (I've also tried gst.STATE_READY and STATE_NULL, which also crash it)


Thanks in advance

---

### Post by SledgeHammer_999 on 2008-12-16
Just out of curiosity: make another "test" pipeline with "filesrc" which plays an ogg file and test if it can be paused.
If the test pipeline can be paused then either an element in your original pipeline causes a problem or you don't handle correclty v4lsrc(since it is a live stream)...

Don't know for sure...

---

### Post by fm232 on 2008-12-16
hmm, it seems to pause fine if I use a filesrc. It must be something to do with using a constantly streaming source

---

### Post by SledgeHammer_999 on 2008-12-16
I think with this kind of source you can't "pause" the stream. You just stop it(STATE_NULL).
Maybe ask in gstreamer's IRC channel... Almost always the is someone who can help you. More info-->Freenode #gstreamer  ([http://gstreamer.freedesktop.org/dev/](http://gstreamer.freedesktop.org/dev/))

---

