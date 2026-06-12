---
title: "Reinstall Firmware on a USB"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by arashiko28 on 2008-11-23
I have a 32GB USB memory stick, and my sister unplugged it while still working. The data got corrupted, but I have a backup. Now, the problem is that even though the drive is 32GB, only takes 1GB, after this, the data gets corrupted. I already checked with CRTL+H, there are no hidden trash folders, I tried to format it, on Ubuntu is impossible, the option is blocked with qtparted and with windows, even if says that it has been successfully formatted, after 1GB, the files are corrupted.

To make it clearer, I can copy 32GB into it, but only what was included in the first GB will be useful, all the rest is somehow corrupted.

There is a way to find and reinstall the USB firmware and to recover all of my usable space? If is not possible the 32GB at least 16 or whatever can be done?[-o<[-o<

---

### Post by ieee488 on 2008-11-23
[http://www.quickonlinetips.com/archives/2005/08/fix-format-usb-flash-drives/](http://www.quickonlinetips.com/archives/2005/08/fix-format-usb-flash-drives/)

---

### Post by The Cog on 2008-11-23
I think I would try to re-format it like this first. Plug it in adn find out which device it is. **sudo fdisk -l** will show you what drives are there, or assuming it mounted when you plugged it in, **df -h** will list the mounted partitions. On my system, it normally mounts as /dev/sdb1.

Once you are sure you know which partition it is, try to reformat it like this (using the right device name of course:
> sudo umount /dev/sdb1
sudo mkfs.vfat -F 32 /dev/sdb1
sudo sync

---

### Post by arashiko28 on 2008-11-23
I already did all those things. It's not precisely re-format, what I need is to re install the firmware, because it's corrupted.

---

### Post by The Cog on 2008-11-24
To the best of my knowledge, they don't have "firmware". My next step up from reformatting the partition would be to wipe the partition table and then repartition and reformat. I don't _think_ this will do any permanent damage - I did it once to one of my sticks.
Overwrite the partition table and first half-meg:
**sudo dd if=/dev/zero of=/dev/sdb bs=512 count=1024**
Then use gparted to partition and format.

---

### Post by arashiko28 on 2008-11-26
That would make available my 32GB's back?

---

### Post by The Cog on 2008-11-27
I have no idea. It depends what's wrong. But it is the next think that I would try. If that doesn't work, I think the stick is beyond repair because I can't think of anything else to do.

---

