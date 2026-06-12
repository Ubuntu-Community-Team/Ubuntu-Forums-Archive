---
title: "[Python] usb device detection (deamon style)"
date: 2009-04-08
forum: Programming Talk
---

### Post by Kegusa on 2009-04-08
Was sitting browsing the web for the various music players for linux out there with a decent iPod support. Seems like there's always a downside with most of the music players regarding the syncing.

IDEA: It should be possible to make a deamon or just a simple script that detects if there's and iPod connected (lsusb check) and even identify the correct iPod (via sysinfo on the iPod itself). Then regardless of what musicplayer you use you can then launch rsync for automatic syncing with the desired directories? 

I'm not the best py-programmer, but have made some simple deamons already (love my kitchen-timer script) using this simple Python method described [here.]("http://code.activestate.com/recipes/278731/")

IS there a good way to detect the system calls when USB devices are detected and what libs? 

Anyone with thougths about this?

---

### Post by xilix on 2009-10-28
I would be interested in the same thing.

---

