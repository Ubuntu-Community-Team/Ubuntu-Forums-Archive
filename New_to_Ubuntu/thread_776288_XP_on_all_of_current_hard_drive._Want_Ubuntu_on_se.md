---
title: "XP on all of current hard drive. Want Ubuntu on second, new hardrive. Possible?"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by dan-buntu on 2008-04-30
Hi. I tried searching for this seemingly common situation, but the myriad results are just confusing me. So...

Starting simply:

I have have Windows XP Home on _all_ of C:

I want to keep it there but have the option of booting to ubuntu (ubuntustudio) on a second hard drive (or at least a partition that resides on a second hard drive).

Is this possible without having to "shrink?" or tamper with the XP (NTFS) partition (all of C: )?

---

### Post by yamawho on 2008-04-30
Yes it can be done.
There are many threads on this topic.
Here is one of the latest ones ...
[http://ubuntuforums.org/showthread.php?t=773145](http://ubuntuforums.org/showthread.php?t=773145)

---

### Post by anewguy on 2008-04-30
Yes - that's how I run.  Windows on 1 drive, Ubuntu on another.  To do this, just go through the normal installation process until it gets to the disk partitioning.  At this point you'll need to tell it manual config, then when the partitioner itself runs you will need select only the drive you want to put Ubuntu on.  It will give you a grub menu when you boot so you can select Windows or Ubuntu.  :)

---

### Post by dan-buntu on 2008-04-30
Thanks so much for the quick friendly replies! I can feel the love :)

So, just tell the installer to install it on the second drive? Where does GRUB load from? (I just want to if ANYTHING will be installed on C: and whether or not that means messing with the XP partition)

Edit:

Also, If i get say, a 120 Gb hd, and want to keep 60G for windows, and use the rest for ubuntu, should I create the partition for windows first and leave the rest unformatted for ubuntu to format? (if it works that way)

---

### Post by kansasnoob on 2008-04-30
I did it this way most recently:

[http://www.cypherhackz.net/archives/2007/12/25/how-to-dual-boot-ubuntu-and-winxp-using-two-hard-drives/](http://www.cypherhackz.net/archives/2007/12/25/how-to-dual-boot-ubuntu-and-winxp-using-two-hard-drives/)

I really do like this better because it does not mess with the windows MBR. That way I could actually remove either hard drive completely and still have a bootable machine.

---

