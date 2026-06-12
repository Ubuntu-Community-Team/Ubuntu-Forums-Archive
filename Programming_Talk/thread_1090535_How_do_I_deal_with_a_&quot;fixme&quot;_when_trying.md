---
title: "How do I deal with a &quot;fixme&quot; when trying to run a windows exe?"
date: 2009-03-08
forum: Programming Talk
---

### Post by col48 on 2009-03-08
What is the approach to 'fixing' this kind of thing?

fixme:ole:OLEPictureImpl_SaveAsFile (0x12f1a0)->(0x131f50, 0, (nil)), hacked stub.

This was attempting to run an exe (compiled VB5 code) under wine.  It is the first time I have tried to run this particular one, which uses an Access Database, although it cannot have got as far as trying to do that yet.  The superficial error (reported by a Windows-style error box) was "Error 11 - division by zero"

---

### Post by crazyfuturamanoob on 2009-03-08
Wine really can't run all windows programs, most of them are malfunctioning or don't work at all.

Or maybe it's a bug in the program you are trying to run? "Division by zero" sounds one to me.

Whenever I run any programs under wine, I get lots of fixmes, even if the program is working correctly.

---

### Post by col48 on 2009-03-09
I don't think it is likely to be a bug.  It is a prog I have been running for a long time on my W95 machine.  The first thing it does is ask the user which input file to use, but under wine it doesn't even get that far.

But my point is.... supposing the 'fixme' is fixable, how do I find out how?

---

### Post by snova on 2009-03-09
It means an API call that the program is using has not been reimplemented in Wine.

You can check the [Wine App database]("http://appdb.winehq.org/") to see if they have a workaround. But aside from that, I don't think there's anything you can do about it until it gets written, unless you want to go write it yourself...

---

