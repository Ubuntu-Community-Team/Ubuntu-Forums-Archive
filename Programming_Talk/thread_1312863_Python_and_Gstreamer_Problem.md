---
title: "Python and Gstreamer Problem"
date: 2009-11-03
forum: Programming Talk
---

### Post by regomodo on 2009-11-03
#

---

### Post by SledgeHammer_999 on 2009-11-03
I don't know python but I think I can follow your logic. I suggest you do this in load() :
1.After you have set the file-location on file-src, you should put file-src in paused mode. After that put decoderbin in paused mode(this will emit the pad-added signal.
2.In OnDynamicPad first put the converter and the sink in paused mode. Then connect the pad to the converter src-pad.

After that it should start playing on play()

---

### Post by regomodo on 2009-11-03
#

---

### Post by SledgeHammer_999 on 2009-11-03
Dont forget that a pipeline is a gstelement itself. So I supposed you should do something like this for the file-src
```
self.filesrc.set_state(gst.STATE_PAUSED)
```

If this doesn't work, can you point me to the python-gst docs?

---

### Post by regomodo on 2009-11-03
#

---

### Post by regomodo on 2009-11-03
#

---

### Post by SledgeHammer_999 on 2009-11-03
Does the print "OnDynamicPad called!" ever get called?

---

### Post by SledgeHammer_999 on 2009-11-03
I think I spotted the actual problem. 

```
file_now = "file://%s" % fname
```

get rid of the "file://"

---

### Post by regomodo on 2009-11-03
#

---

### Post by SledgeHammer_999 on 2009-11-03
I suppose you are getting the same segfault now, with the changes I proposed right?

How about first setting the location of filesrc, then PAUSING it and then linking it to decodebin?

---

### Post by regomodo on 2009-11-04
#

---

### Post by SledgeHammer_999 on 2009-11-04
This works because you're using a mainloop as I suggested on the other thread.

I don't know how you can interact with that. I suppose you should investigate how you can connect signal handlers.(eg on pressing "p" it should call a function in your code that pauses the pipeline).

Or maybe you can create another thread(B). On thread B create the mainloop(is that possible?) and the pipeline. Use the first thread to control thread B.

---

### Post by regomodo on 2009-11-05
#

---

### Post by regomodo on 2009-11-06
#

---

### Post by SledgeHammer_999 on 2009-11-06
Well I was right for one thing: you don't need **file://** :p

Glad to hear you worked it out. (although thread_init may start a mainloop... just a guess). 

Anywayz, if you have other questions about gstreamer I may be able to help you.(I am writing my own hobby app).

---

