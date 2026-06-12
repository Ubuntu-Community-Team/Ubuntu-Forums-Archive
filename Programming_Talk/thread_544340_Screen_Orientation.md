---
title: "Screen Orientation"
date: 2007-09-06
forum: Programming Talk
---

### Post by speed_123 on 2007-09-06
Hi frnds,

I am currently working on screen orientation using GTK+. Already Xrendr is available but i want to implement it using gtk.Kindly throw some light on this issue.

---

### Post by Awalton on 2007-09-06
So uhh, what exactly are you trying to accomplish? Using an app to tell RandR to turn the screen? If so, then this is what you're looking for: [http://keithp.com/~keithp/talks/randr/protocol.txt](http://keithp.com/~keithp/talks/randr/protocol.txt) (and it really has more to do with X programming than GTK+). 

It sure would be nice if this functionality was exposed through GDK at some point in the future though (especially as future portable devices will want to use this quite a bit). Something like gdk_screen_[get/set]_rotation(), gdk_screen_[get/set]_reflect(), would be nice. I guess you could always file a bug report saying all of this, though.

---

