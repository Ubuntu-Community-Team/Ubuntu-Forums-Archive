---
title: "Python and Gstreamer"
date: 2010-04-24
forum: Programming Talk
---

### Post by Shady3D on 2010-04-24
hi, I'm creating a streaming application, using GStreamer with TCP pipeline, and i implemented start, pause, and stop.

but the problem is, that i can't seek, i tried to change the playback value from the server side, then i tried on the client side, and Finally tried to change the value on both at the same time, but in all cases it doesn't work. and I even tried to pause the playback then continue but nothing happens.

I'm having this problem with the seek and the volume. Any help please, I searched everywhere but i couldn't find anything that worked.

this is the code that i use for seeking
```
self.pipeline.seek_simple(gst.FORMAT_TIME, gst.SEEK_FLAG_FLUSH, time)
```

---

