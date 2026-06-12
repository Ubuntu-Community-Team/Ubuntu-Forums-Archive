---
title: "Mounting SATA vfat drive"
date: 2006-04-03
forum: Outdated Tutorials &amp; Tips
---

### Post by nebc on 2006-04-03
I know there are threads on this but so far they have not completly done the trick.

I have a dual boot currently configured across 2 SATA drives.  One 160GB hard drive is home to Ubuntu (/dev/sdb) where the other hardrive has a 80GB ntfs partition for windows and an 80GB vfat partition that I would like both ubuntu and windows to see.

This is the contents of /etc/fstab:

/dev/sdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda2       /media/sda2     vfat    auto,rw,user 0 0
/dev/sdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

I added the /dev/sda2 line and I'm pretty darn sure that it is the correct partition.  However, after rebooting I cannot get access to it.  When I ls media I get:

cdrom/   cdrom0/  cdrom1/  floppy/  floppy0/

Suspiciously I only have 2 CD drives (1 is DVD I suppose).  At any suggestions?  If you need more information just ask and I will happily provide.

Cheers.

---

