---
title: "Repeating Gstreamer audio"
date: 2008-06-19
forum: Programming Talk
---

### Post by af20001 on 2008-06-19
Hi,

I'm developing a python app that uses GStreamer (pygst) to play short audio files.

I want to be able to repeat the audio file a set number of times (number of times set by a preference), but I can't find any information on how to do this.

For example:

[PHP]for i in range(3):
     self.pipeline.set_state(gst.STATE_PLAYING)
     self.pipeline.set_state(gst.STATE_READY)
[/PHP]

doesn't repeat the audio file. I'm not expecting the solution to be as simple as that, but show this as an example that there is obviously more to it than resetting the state.

Thanks,
Andy.

---

