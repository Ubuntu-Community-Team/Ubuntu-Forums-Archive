---
title: "Serious dual-boot issue. &quot;sudo grub&quot; doesn't work!"
date: 2010-04-10
forum: Outdated Tutorials &amp; Tips
---

### Post by lockalidiot on 2010-04-10
So, i have followed this tutorial:
[http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999)

Everything went fine until i got to the point where I am supposed to re-install grub. I can't get it done, cause when I type in to terminal "sudo grub" it tells me that "command not found"... What to do?

---

### Post by drs305 on 2010-04-10
Are you sure you are using Grub legacy and not Grub 2? ("grub-install -v" will give you the version you are running. Grub 2 is 1.96 or higher). The note near the beginning of the thread says it won't work in Karmic and to go to page 14. Did you do this?

In either case, this is a good guide on restoring either Windows or Ubuntu if you lose one after installing the other.
[How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by lockalidiot on 2010-04-12
Apparently not... I feel like a total idiot. I got the thing to work now. Thank you!

---

