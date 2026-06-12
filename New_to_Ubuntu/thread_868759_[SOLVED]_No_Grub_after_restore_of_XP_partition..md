---
title: "[SOLVED] No Grub after restore of XP partition."
date: 2008-07-24
forum: New to Ubuntu
---

### Post by mingle on 2008-07-24
Hi,

I recently did a restore of my XP partition (from a Ghost images backup) and after the successful restore, my box now boots straight into XP, rather than showing the Grub boot menu.

So it seems that the MBR has been overwritten and whacked Grub...

My Ubuntu partition is still there and appears to be fine (when I boot from the Ubuntu LiveCD and have a look at it).

How do I get Grub installed and running again?

I've had a look around the forums and can't see anything that details exactly what I need to do to sort out this problem.

Any help or comments appreciated, as ever!

Cheers

Mike.

---

### Post by oliviacond on 2008-07-24
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by mingle on 2008-07-24
@oliviacond,

Many thanks! The SuperGrub floppy did the trick!

I guess my search was too specific! :-)

Cheers,

Mike.

---

### Post by sharks on 2008-07-24
try SuperGrubDisk.

---

