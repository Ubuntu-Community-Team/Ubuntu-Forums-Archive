---
title: "[SOLVED] SD Card mounts multiple times"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by kjohansen on 2008-08-21
I keep an SD card in my reader all the time, I mostly use it as a small backup for projects Im currently working on (or if I boot into windows as Readyboost memory).

But anyways the point is that each time I come out of hibernate in Ubunutu the SD card is mounted again so I end up with multiple mounts of it. The old mounts stay on my desktop but are not functional. Is there a way to keep it from mounting multiple times?

I put a script in the suspend.d folder that is:
umount /media/KINGSTON

but that does not seem to do anything. (KINGSTON is the normal name for the mount of the SD card)

thanks.

---

### Post by kjohansen on 2008-09-01
I removed the automount settings from gconf-editor for nautilus.

This way I only mount an SD card when I want it.

I hate to find threads marked solved when no one gives the solution, so I posted my own solution for reference.

---

