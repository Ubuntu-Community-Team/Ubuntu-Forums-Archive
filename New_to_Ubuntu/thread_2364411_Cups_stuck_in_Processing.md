---
title: "Cups stuck in Processing"
date: 2017-06-22
forum: New to Ubuntu
---

### Post by schmitta on 2017-06-22
My print job to a parallel connected printer (yes it is connected/powered on/enabled and working) has been stuck in processing for 6 minutes.

The sys printer setting says it is enabled .

I tried:    lp -i 225 -H resume

but it did not help. Linux needs a simpler print job processor that does not break.

as I don't know where to start and do not really understand CUPS Any help would be greatly appreciated.

---

### Post by yancek on 2017-06-23
Have you tried printing to it from a terminal as you may see a message on screen if it fails which could help resolve the problem.  lpr /path/tofile

CUPS has been around for many years and is used successfully by millions so I doubt that is the problem.  Have you read the documentation?  What make/model/age is the printer?

---

### Post by schmitta on 2017-06-23
Thanks YANCEK I will try that!

---

