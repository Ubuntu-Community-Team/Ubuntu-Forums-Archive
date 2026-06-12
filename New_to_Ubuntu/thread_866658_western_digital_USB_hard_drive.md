---
title: "western digital USB hard drive"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by ianbrown75 on 2008-07-22
Hard to explain here. I have had trouble in the past with this hard drive. Now I am using gparted to try to reformat. but this is the message I get,
Error: File system was not cleanly unmounted!  You should run e2fsck.  Modifying an unclean file system could cause severe corruption.
ian@ian-desktop:~$ sudo qtparted
Error: File system was not cleanly unmounted!  You should run e2fsck.  Modifying an unclean file system could cause severe corruption.
Error: Could not detect file system.
Error: File system was not cleanly unmounted!  You should run e2fsck.  Modifying an unclean file system could cause severe corruption.
Error: Could not detect file system.
Error: Could not detect file system.
Error: File system was not cleanly unmounted!  You should run e2fsck.  Modifying an unclean file system could cause severe corruption.
Error: Could not detect file system.


Could you help me just reformat it

---

### Post by jordanmthomas on 2008-07-22
Couldn't you just use mke2fs manually?

---

### Post by ramjet_1953 on 2008-07-22
When you remove the drive, do you right-click on it's icon on your desktop and choose the unmount option?

If you don't do this and just unplug it, all sorts of problems can arise, including the symptoms you have mentioned.

Regards,
Roger :cool:

---

### Post by xe1ufo on 2008-08-21
I had my external Western Digital 230-Gig hard drive working fine under Ubuntu 7.10. Then I upgraded to 8.10 and no matter what, I cannot mount it when connected to the USB port.

BUT: The drive also has a FireWire port. I plugged in the FireWire cable made to go from the video camera to the laptop, and it worked instantly. It is also much faster then USB.

---

### Post by cybrsaylr on 2008-08-22
> **ramjet_1953 said:**
> When you remove the drive, do you right-click on it's icon on your desktop and choose the unmount option?

If you don't do this and just unplug it, all sorts of problems can arise, including the symptoms you have mentioned.

Regards,
Roger :cool:

I had the same problem on my dual boot system with an Ext HDD.
It seems it didn't matter in Windows but if I didn't 'safely remove the hardware' in Windows as recommended, it would not mount on Ubuntu. Now I always 'safely remove it' and have no more problems in either OS.

---

### Post by Chevelle on 2008-08-22
> **cybrsaylr said:**
> I had the same problem on my dual boot system with an Ext HDD.
It seems it didn't matter in Windows but if I didn't 'safely remove the hardware' in Windows as recommended, it would not mount on Ubuntu. Now I always 'safely remove it' and have no more problems in either OS.

Same here. If you have Windows, just boot into Windows with the hard drive connected and use 'safely remove' on the hard drive. It should work fine in Ubuntu afterwards.

---

