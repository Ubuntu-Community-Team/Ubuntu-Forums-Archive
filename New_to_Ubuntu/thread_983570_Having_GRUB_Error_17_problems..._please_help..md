---
title: "Having GRUB Error 17 problems... please help."
date: 2008-11-15
forum: New to Ubuntu
---

### Post by chris_james on 2008-11-15
Hey all, I know this topic may have been discussed before, but I haven't been able to find an answer to my specific situation so I'll make it as brief as possible and hopefully someone here knows what I need to do. 

A few months ago, I decided to download Ubuntu and dual boot with XP, but I split my HD space (160 GB) 50/50 which I didn't mean to do. I meant to allot more space to XP since I had more files there and still planned on using it primarily. So in an attempt to re-partition and give XP more space, I ran Partition Magic and attempted to just format the Linux space to NTFS (I think...) which probably wasn't what I was supposed to do... but anyway, I executed the action and when my computer restarted, I got the GRUB Error 17 message. Basically, all I want to do at this point is just get Windows back up and running... I downloaded the .iso file for the Super Grub disk and burned it to CD-R and ran it on my computer.. but I don't really know much about what to do with it, it ran the diagnostic tests and so far has found no errors.. but I just want to know what I need to do in order to boot Windows back up. 

Any advice would be GREATLY appreciated, I'm kind of at a loss right now and I need to get back up and running. Also, I'm not the most computer savvy person in the world, so I guess in as plain english as possible. :) Thanks.

---

### Post by Duck2006 on 2008-11-15
Boot up the win xp installation disk chose recover and repair the mbr

in recover mode

fixmbr


reboot and you should be able to boot into windoze.

---

### Post by chris_james on 2008-11-15
Is there any way to do it if I don't have the XP Install disk? I'm not sure my computer even came with one when I got it 2+ years ago.. if not, I'm going to have to figure out a way to get my hands on one.

---

### Post by Duck2006 on 2008-11-15
You can do it from the live cd of ubuntu.

[http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)
[http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php](http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php)

---

### Post by unutbu on 2008-11-15
Here are instructions on how to use SuperGRUB disk to restore your Windows MBR:

[http://www.supergrubdisk.org/wiki/UninstallGRUB](http://www.supergrubdisk.org/wiki/UninstallGRUB)

---

### Post by chris_james on 2008-11-15
> **unutbu said:**
> Here are instructions on how to use SuperGRUB disk to restore your Windows MBR:

[http://www.supergrubdisk.org/wiki/UninstallGRUB](http://www.supergrubdisk.org/wiki/UninstallGRUB)

That worked! Thank you so much. :)

---

