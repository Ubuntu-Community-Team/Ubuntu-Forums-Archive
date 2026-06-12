---
title: "MY USB Doesn't Work!!!"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by zamadatix on 2008-10-27
To put it simply i need my windows to open my usb but after formatting as fat32 with gparted (whole drive) when i stick it in windows and open it through my computer windows freezes. ive tried formating from windows with the windows formatter and the hp usb format tool but neither work (they freeze) so what the heck is up with my usb (2gb dane elec) !!!!!!!

---

### Post by porchrat on 2008-10-27
Have you tried using NTFS instead?

---

### Post by scorchgeek on 2008-10-27
What about the usual default for those drives, FAT?

---

### Post by P13808 on 2008-10-27
Does it work in Linux?  If not, check the hardware.
Try a different computer.  Driver could be messed up.

---

### Post by Keen101 on 2008-10-27
most flash drives are formatted in FAT32. Some are formatted in FAT16, and some (even less) are formatted in NTFS. If you are only going to use it on Linux you could format it as ext3. I'm not sure what went wrong, but gparted Live-CD has worked for me in the past for formatting USB drives. I suppose you could try using the fdisk utility.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

