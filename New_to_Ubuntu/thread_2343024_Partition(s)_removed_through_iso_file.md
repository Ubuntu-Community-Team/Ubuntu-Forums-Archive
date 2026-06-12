---
title: "Partition(s) removed through iso file"
date: 2016-11-12
forum: New to Ubuntu
---

### Post by whynot on 2016-11-12
Hi
I had Ubuntu 16.04 x64 and windows 7 pro x32 desktop system. Yesterday I wanted to mount a iso file as a driver under Unity desktop drive list menu you know that gnome software you could also able to mount or recover iso files. I think I removed my partitions with that software interface.Is there anyway to get back partitions and files?Now my system doesn't even boot up and doesn't detect any systems.
Thanks.

---

### Post by yancek on 2016-11-12
I believe you will need to be a lot more specific about what you did and what your intentions were.  Mounting an iso in itself isn't going to delete partitions or render your system unbootable.  More details needed if you want help.

---

### Post by whynot on 2016-11-12
I created a new Ubuntu Live CD.And I booted with that.
I think I messed up my system with the gnome-disk-utility software.
```

sudo fdisk -l
Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1        738023424 1465143295  727119872 346.7G  7 HPFS/NTFS/exFAT
/dev/sda2                0 1851878407 1851878408   883G 39 Plan 9
/dev/sda3          6581877 1841684869 1835102993   875G 65 Novell Netware 386
/dev/sda4       1769238633 1769922263     683631 333.8M 65 Novell Netware 386

Device         Start       End   Sectors   Size Type
/dev/sdb1         40    409639    409600   200M EFI System
/dev/sdb2     411648 619721604 619309957 295.3G Microsoft basic data
/dev/sdb3  619722752 623628287   3905536   1.9G Linux swap
/dev/sdb4  623628288 976771071 353142784 168.4G Linux filesystem

Partition table entries are not in disk order.
```
Thanks.

---

### Post by oldfred on 2016-11-12
Did you do something like a MBR to gpt conversion or something else?

You partition table for sda, looks like the partition tables are corrupted. 
Plan 9 or Netware 386 are probably the result of random data in partition table.

I might see what testdisk says. If you changed partitions a lot testdisk finds many old versions and you have to select the correct combination of partitions that was you last configuration. And no overlaps. Best to have documented partitions before hand. Do you have anything like a Boot-Repair summary report, copy of fdisk or parted output anywhere in backups?

       Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

