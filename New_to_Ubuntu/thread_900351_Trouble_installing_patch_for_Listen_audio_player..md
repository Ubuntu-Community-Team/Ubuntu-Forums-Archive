---
title: "Trouble installing patch for Listen audio player."
date: 2008-08-25
forum: New to Ubuntu
---

### Post by mjs918 on 2008-08-25
Hi, I'm new here and also extremely inexperienced with linux (only have been running Ubuntu for 2 days, but already I'm very impressed).  I have tried out a few different audio players to see if there was anything available for Ubuntu that would be comparable to iTunes.  I've been using the Listen audio player and I'm very happy with it.  However, apparently the fast forward/rewind feature does not work with v0.5.  I did though find a patch on the developers website that's supposed to fix it.  The only problem is I don't have any idea how to install it!  Their site gives me this code:



--- /usr/lib/listen/player.py   2008-06-16 00:16:36.000000000 +0200
+++ player.py   2008-07-27 12:27:36.000000000 +0200
@@ -196,7 +196,7 @@
     def on_message(self,bus,message):
         self.debug("message", message)
 
-        if message.type == gst.MESSAGE_CLOCK_PROVIDE:#gst.MESSAGE_NEW_CLOCK:
+        if (message.type == gst.MESSAGE_CLOCK_PROVIDE or message.type == gst.MESSAGE_NEW_CLOCK):
             self.clock=True
             if self.seek_pending:
                 self.seek_cb(self.seek_pending)



Any help would be appreciated!

---

### Post by neurostu on 2008-08-25
use the patch command...
```

man patch

```
will display the manual which does a pretty good job of explaining how to use the patch utility.

---

