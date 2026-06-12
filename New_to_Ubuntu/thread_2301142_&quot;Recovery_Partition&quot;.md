---
title: "&quot;Recovery Partition&quot;"
date: 2015-10-31
forum: New to Ubuntu
---

### Post by yellowcrash10 on 2015-10-31
Hello! I'm not really new to Ubuntu, but I'm not sure where else to put this, and I can't find a way to search for it correctly.
Anyway, is it possible to copy the Ubuntu installation disc to a partition on my computer so that when I do something to make Ubuntu stop working (say, accidentally force-deleting a system directory because I didn't read what I was typing (I've definitely learned my lesson now ;))), I can just boot to this "recovery partition" and reinstall the OS without digging for my Ubuntu DVD/USB? There will inevitably be a time when I break my computer and am without my other gear, and something like this would be extremely useful. The partition would be read-only like the DVD and would appear in the GRUB menu on startup. Can this be done?

---

### Post by coffeecat on 2015-10-31
You can boot directly from an ISO file stored on the hard drive if you add entries to grub's menu. You could put the ISO file in a separate partition if you wish, and it doesn't have to be a conventional recovery type partition. Two useful links for you:

[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)

[http://www.howtogeek.com/196933/how-to-boot-linux-iso-images-directly-from-your-hard-drive/](http://www.howtogeek.com/196933/how-to-boot-linux-iso-images-directly-from-your-hard-drive/)

I doubt you'd be able to reinstall your main system if you use the grml-rescueboot method in the first link as the ISO would be in the partition you are trying to install to. Also - your intention won't work if you need to boot the ISO because the filesystem in the root partition (or boot if you have a separate boot partition) of your main system has become corrupted. Part of the grub files are in the /boot folder of your main system.

Although being able to boot from an ISO file is useful, I suggest the only way of reliably having a way of booting into a live session is to have a live USB or DVD available,

---

### Post by yancek on 2015-10-31
You could also use a small flash drive and just have a boot partition on it to boot the Ubuntu iso on a HD partition.  If you're new to Linux, other options might be easier.

---

