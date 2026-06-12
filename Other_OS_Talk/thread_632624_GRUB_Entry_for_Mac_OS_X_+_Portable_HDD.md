---
title: "GRUB Entry for Mac OS X + Portable HDD"
date: 2007-12-05
forum: Other OS Talk
---

### Post by Guardian-Mage on 2007-12-05
Ok, I have installed ToH Mac OS X x86 onto a portable hdd(250gb). I Installed it to the 25 gb hfs+ partition which is also the first partition on the disk. In Ubuntu my Portable HDD shows up as sda, and my Mac partition shows up as sda1. The install went fine, all of the data is there, but grub will not boot it. My BIOS is capable of booting from USB. GRUB is on my internal HDD and boots Windows/Ubuntu fine. 

My Mac OS X Entry

title Mac OS X 10.5
root (sd0,0)
makeactive 
chainloader +1
boot

GRUB returns Error 23: Error parsing number, what is wrong?

---

### Post by smartboyathome on 2007-12-05
You can't boot to another hard drive from the current one. The other one has to be able to boot from USB (I don't think mac can).

---

### Post by meierfra on 2007-12-05
I don't have any experience with Mac's, but I do know that "root (sd0,0)" will not work. Try "root (hd1,0)" instead.

---

### Post by hanzomon4 on 2007-12-06
> **meierfra said:**
> I don't have any experience with Mac's, but I do know that "root (sd0,0)" will not work. Try "root (hd1,0)" instead.

Edited: I was wrong it is "root (hd1,0)", grub looks at the drive/partition it's installed on as hd0,0. So if grub is installed on your main drive hd1,0 is your usb drive 1st partition. If you still are having problems make sure that the boot partition for OSX is in fact the first partition of the usb drive.

---

