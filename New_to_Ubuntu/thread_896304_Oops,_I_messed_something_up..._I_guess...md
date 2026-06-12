---
title: "Oops, I messed something up... I guess.."
date: 2008-08-21
forum: New to Ubuntu
---

### Post by Sspankyy on 2008-08-21
OK,
  I recently upgraded my ram, and am running out of space on my hdd <4 os's, go figure>, so I decided to resize my SWAP partition because it almost always has 0 usage.  
  So I resized it down a bit, leaving about 500 megs in it, but now Ubuntu will not boot, I get a Grub error 17, and "file not found" when I try to boot.   

    Any help would be appreciated.

Edit:  It also says something like "filesystem type unknown", and "partition type 0x82"
not sure if that will help...

---

### Post by bitninja on 2008-08-21
Try taking a look at these pages:

[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)
[http://www.iknowkungfoo.com/blog/index.cfm/2008/6/16/Stupid-solution-for-Grub-error-17](http://www.iknowkungfoo.com/blog/index.cfm/2008/6/16/Stupid-solution-for-Grub-error-17)

Hopefully one of those helps!

---

### Post by Sspankyy on 2008-08-21
I already checked my bios stuff, and nothing else is plugged in.. but thanks for the try..

---

### Post by bitninja on 2008-08-21
What partition type is your Ubuntu partition? Ext3, ext2?

---

### Post by Sspankyy on 2008-08-21
It is ext3

---

### Post by bitninja on 2008-08-21
Okay, use fdisk to look up what partition type your Ubuntu partition is reading as. (Use a Live CD of some sort). If it isn't ID 83, then use fdisk to change it to 83. I had this problem once, that's probably the culprit.

Source:
[http://www.win.tue.nl/~aeb/partitions/partition_types-1.html](http://www.win.tue.nl/~aeb/partitions/partition_types-1.html)

---

### Post by mcduck on 2008-08-22
If you also resized your system partition, it's UUID has changed and you need to edit /boot/grub/menu.lst and /etc/fstab to use the new UUID for the partition.

You most likely also need to do thei for the swap in /etc/fstab.

Use theb "blkid"-command to get the correct UUIDs.

---

