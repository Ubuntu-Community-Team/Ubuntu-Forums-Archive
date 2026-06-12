---
title: "Resizing my extended partition"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by sidzoo on 2008-08-22
sudo fdisk =l gives me

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = l225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              34        1408    11044687+   7  HPFS/NTFS
/dev/sda2            1409        3608    17671500   83  Linux
/dev/sda3   *        3609        4257     5213092+   c  W95 FAT32 (LBA)
/dev/sda4            4258        9730    43961872+   f  W95 Ext'd (LBA)
/dev/sda5            4258        4507     2008062   82  Linux swap / Solaris
/dev/sda6            4508        8142    29198106    7  HPFS/NTFS
/dev/sda7            8143        9729    12747546    7  HPFS/NTFS


My disk has only 9729 cylinders, but my extended partition sda4 goes up to 9730. As a result, GParted shows my hard disk as being completely unallocated. How do I resize the partition?

Thanks,
sidzoo.

---

### Post by sidzoo on 2008-08-23
No Ideas?

Thanks,
sidzoo.

---

### Post by vanadium on 2008-08-23
This seems to be an inconsistency in the partitioning causing problems for gparted. Resizing the extended partition would require to delete all logical partitions contained into them (sda5 and up) anyway. The next steps depends on what you actually want to do. If the current setup is not causing any other problems for you, then I would leave everything as is.

---

### Post by louieb on 2008-08-23
Get a [SystemRescueCd]("http://www.sysresccd.org/Main_Page") 
There a two programs that may be able to fix your partition table.
The 1st I would try is** testdisk** I might be able to detect the problem and offer to fix it. 

The other is** fdisk**  - it will write a new partition table with whatever you tell it to.  fdisk is a very powerful program for altering the partition table. It can fix the problem or it can break your system. It does not do much error checking I just does whatever you tell it to.
[HowTo: Partitioning Basics - Ubuntu Forums]("http://www.ubuntuforums.org/showthread.php?&t=282018") 
[Partitioning with fdisk]("http://tldp.org/HOWTO/Partition/fdisk_partitioning.html")

---

### Post by coffeecat on 2008-08-23
Have you got Windows XP on there, and can you copy any data you need to retain off sda6 and sda7?

Here's a suggestion. Boot into Windows and go to Control Panel > Adminstrative Tools > Computer Management > Disk Management. Does it show the partitions? If it does, you can right-click on logical partitions to delete them. I don't know whether it gives you an option to delete an extended partition once you've emptied it of logicals, but it ought to. I'm in XP at the moment and I can see all my logicals, but not the extended. It would make sense for it not to let you delete an extended before you've deleted all the logicals, but I've never tried this for myself.

If you can delete the logicals and then the extended, Gparted **may** be able to make sense of the partition table, and you'll be able to recreate the extended and logicals properly. Of course, if there's another issue in the partition table, this will get you no further.

And if you've got Vista, I don't know where the equivalent tool is. Shouldn't be too difficult to find - I would hope.

---

### Post by SkonesMickLoud on 2008-08-23
> **louieb said:**
> Get a [SystemRescueCd]("http://www.sysresccd.org/Main_Page") 
There a two programs that may be able to fix your partition table.
The 1st I would try is** testdisk** I might be able to detect the problem and offer to fix it.

^^ This will be your best bet.  However, you don't need another CD for it.  You can install it while booted into the Ubuntu LiveCD:

```
sudo aptitude install testdisk
sudo testdisk
```

Follow the on-screen prompts.  I can't quote exactly what they say, but they're pretty straightforward and it's safe to go with the defaults.  Much safer than c/fdisk.

---

