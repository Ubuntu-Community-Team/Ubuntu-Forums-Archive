---
title: "Uninstalling Question"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by brandon89 on 2008-10-08
Ok, I just followed this thread:
[http://ubuntuforums.org/showthread.php?t=113630](http://ubuntuforums.org/showthread.php?t=113630)

to delete the ubuntu partition but i was unable to merge the free space with my current partition.

here's what it showed in the boot program i was told to use after i deleted the linux partitions.

MBR Entry 0 Partition 163397MB HPFS/NTFS
MBR Entry 2 Partition 64840MB  Extended
------      Volume    64840MB  Free Space
HP_Recovery Partition 10226MB  HPFS/NTFS

I tried resizing the MBR Entry 0, but it won't let me increase size so should i try to resize the MBR Entry 2/what exactly is the MBR Entry 2?.

---

### Post by bumanie on 2008-10-08
To merge the partitions you firstly need to get rid of the extended partition. If using gparted, the extended partition it is the blue colored rectangle. Delete that (right click on the rectangle and choose delete) and then you will be able to 'join/merge' all unallocated space.

---

