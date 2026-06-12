---
title: "After Nvidia install, graphics have gone beyond monitor settings"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by Starrfoxx on 2008-07-25
I installed Hardy Heron on a small partition on my wife's computer a couple of days ago.  Everything went fine with that.  I was then prompted to install the Nvidia driver to support advanced graphics.  After I rebooted, Ubuntu will switch to a screen mode that is beyond what the monitor (or perhaps it's the graphics card) is capable of.  The monitor will have a message that states "unable to sync" or something like that.  How can we switch the graphics settings so that Ubuntu will boot up correctly?

Graphics card is an Nvidia EVGA 8400gs
Installed Hardy Heron 64 bit, on a 2.7 Athlon dual core chip.

---

### Post by Troll_the_Great on 2008-07-25
Try this:
At boot up, you should have (at least) 3 options (if you don't see them, pres ESC several times when the computer boots):
Ubuntu 8.04.1 kernel 2.6.24-19 generic
Ubuntu 8.04.1 kernel 2.6.24-19 generic-recovery mode
Memtest86
Choose recovery mode and in the menu that you see choose repair X server and then normal boot.
See if this works and post the results.
Cheers!

---

