---
title: "Update.Video Problem"
date: 2013-01-26
forum: New to Ubuntu
---

### Post by DarthSidious on 2013-01-26
My 12.10 system was working great until I installed the updates that were available on Fri January 18th.
Once I rebooted, my video was shot, I couldn't see anything.  I was able to hit Alt-F2 (boot into safemode or something) and the system worked until I rebooted.  This has happened before with Ubuntu 11.xx but they fixed it with with 12.xx.  With 11.xx, I use to have to edit the grub file but inserting the line "nomodeset".  The grub file for 12.xx looks different and I don't know where to put the line "nomodeset".  Can someone please tell  me, or perhaps suggest another solution.  Thank in advance for your help, I have been running Win 7 and its just killing me.




Computer Specs

Dell XPS8300
8GB DDR3 SDRAM at 1333MHz - 4x2GB
XPS 8300 Intel Core i7-2600 processor(8MB Cache, 3.4GHz)
AMD Radeon HD 6450 1GB DDR3

---

### Post by bogan on 2013-01-26
Hi!, **DarthSidious**,

Try first entering 'nomodeset' after 'quiet splash' by highlighting the ubuntu entry in grub menu, and pressing 'e' to get into edit mode. Scroll down to the 'Linux boot' line and across to "ro". Then enter the option and press 'Ctrl+x' to boot.

To make it permanent:```
 gksudo gedit /etc/default/grub 
```and add 'nomodeset' to the GRUB_COMMANDLINE_LINUX_DEFAULT line, and Save.

[http://ubuntuforums.org/showthread.php?t=1613132&page=10](http://ubuntuforums.org/showthread.php?t=1613132&page=10)

Chao!, **bogan**.

---

### Post by DarthSidious on 2013-01-26
Thanks!!  It worked!!

Darth Sidious

---

