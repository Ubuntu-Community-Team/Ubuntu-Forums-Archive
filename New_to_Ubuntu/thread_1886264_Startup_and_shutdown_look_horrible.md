---
title: "Startup and shutdown look horrible"
date: 2011-11-24
forum: New to Ubuntu
---

### Post by Foobarz on 2011-11-24
Ok so here is my startup sequence
I customized it with Super boot manager 

BIOS Screen
Beautiful burg bootloader
*Some text crap about disable irq and vesa error
*Screen goes into a seizure
Beautiful plymouth loading screen
Plymouth animation freezes, mouse appears, panel appears, ready to work

Shutdown sequence: 
*Some random text about stopping processes
plymouth loading screen
shutdown

Ok, so how do I make sure that the items in asterick do not occur?

---

### Post by Sealbhach on 2011-11-24
Look in the system log and run dmesg and see if you can get some information on what is happening. You might be better off asking on the SBM forums, if they have a forum.

.

---

