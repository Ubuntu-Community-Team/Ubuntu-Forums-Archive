---
title: "stream rippers, how do they work?"
date: 2009-01-11
forum: Programming Talk
---

### Post by TreeFinger on 2009-01-11
how do applications that rip music off of internet radio stations work?

---

### Post by slavik on 2009-01-11
it's a player that instead of sending the data to the audio subsystem, saves it to a file.

---

### Post by TreeFinger on 2009-01-12
> **slavik said:**
> it's a player that instead of sending the data to the audio subsystem, saves it to a file.


This interests me. Where can I start to write my own program to do this?

---

### Post by SledgeHammer_999 on 2009-01-12
Hmmm the easier method IMO is gstreamer. Just construct a pipeline that plays a radiostation but the final "elemant/plugin" in the pipeline(preferably before any decoding takes place) should write to disc and NOT send data to the audio system. Take a look at "filesink" element.

---

### Post by lswb on 2009-01-12
> **TreeFinger said:**
> This interests me. Where can I start to write my own program to do this?

You could take a look at the code for an open source program like streamripper at 

[http://streamripper.sourceforge.net/](http://streamripper.sourceforge.net/)

---

