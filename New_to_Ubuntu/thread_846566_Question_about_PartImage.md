---
title: "Question about PartImage"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by nkri on 2008-07-01
Hey, everyone.

I just got an external hard drive (500GB Seagate Freeagent), and I want to back up my Windows XP and Ubuntu partitions onto it.  I am not worried about making the image files, but about restoring them, and this is where my question comes up:

Will restoring an image to either my Windows or Ubuntu partitions change anything having to do with my MBR and/or GRUB, i.e., will I still be able to boot into both?

This is the output of fdisk -l, if anyone needs it:
```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe52de52d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5708    45849478+   7  HPFS/NTFS
/dev/sda2           11481       12160     5462100   1c  Hidden W95 FAT32 (LBA)
/dev/sda3            5709       11238    44419725   83  Linux
/dev/sda4           11239       11480     1943865    5  Extended
/dev/sda5           11239       11480     1943833+  82  Linux swap / Solaris

Partition table entries are not in disk order
```

Thanks!
-nkri

---

### Post by logos34 on 2008-07-01
Everything will be ok as long as you restore to the original partitions/locations.  So, for instance, if you restore the image of linux root to sda3, there shouldn't be a problem since Grub on the MBR (master boot record) will still be looking for menu.lst in /boot/grub on sda3

Same with windows, but remember that ntfs support in partimage is still officially 'experimental,' so there is a chance it won't boot after restore

---

### Post by nkri on 2008-07-01
Great, thanks!  Just what I want to hear!  I had been wondering about the NTFS thing (I've heard mixed reviews), but it doesn't matter to me very much, as I only use it for a couple of programs for school.

Thanks for the help!
-nkri

---

