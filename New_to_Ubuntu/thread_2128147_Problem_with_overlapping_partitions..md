---
title: "Problem with overlapping partitions."
date: 2013-03-22
forum: New to Ubuntu
---

### Post by Guruprasad on 2013-03-22
I had dual boot Ubuntu and WINXP. I had to reinstall WinXP. After that Ubuntu on live USB is not recognising any partitions.

Gparted shows the whole disk as unallocated and error warning "cannot have overlapping partitions".

sudo fdisk -l gives
```
ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000b020a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
Partition 1 does not start on physical sector boundary.
/dev/sda2            5100       10199    40960000   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/sda3           11219       60801   398269985+   5  Extended
Partition 3 does not start on physical sector boundary.
/dev/sda4           21418       31616    81920000   83  Linux
Partition 4 does not end on cylinder boundary.
/dev/sda5           11219       13651    19529728   83  Linux
/dev/sda6           13651       21417    62386176   83  Linux
/dev/sda7           31617       41815    81920000   83  Linux
/dev/sda8           41815       52014    81920000   83  Linux
/dev/sda9           52015       60801    70581546    7  HPFS/NTFS
Partition 9 does not start on physical sector boundary.

Disk /dev/sdb: 8178 MB, 8178892800 bytes
252 heads, 62 sectors/track, 1022 cylinders
Units = cylinders of 15624 * 512 = 7999488 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00038494

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1022     7983833    c  W95 FAT32 (LBA)
```

Can anyone help me getting my partitions back?

Thanks in advance.

---

### Post by oldfred on 2013-03-23
By definition sda4 is a primary partition and only logical partitions starting at sda5 and up can be in the extended partition. 

But you have sda4 in between sda6 & sda7 by sectors whch violates the rules. Fortunately no partitions actually overlap as that can cause major data corruption.

But how did you get this?

Fixparts may work. It says it does not work on overlapping partitions, but may work in your case. But partition numbers may get changed. If you are mounting partitions by device like /dev/sda7 not UUID you may have to edit fstab and reinstall grub.

       First backup partition table, and copy to some other device.
sudo sfdisk -d /dev/sda > parts_sda.txt

      
 Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

