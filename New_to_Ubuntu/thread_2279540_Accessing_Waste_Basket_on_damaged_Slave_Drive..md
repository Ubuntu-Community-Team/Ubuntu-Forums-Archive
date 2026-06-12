---
title: "Accessing Waste Basket on damaged Slave Drive."
date: 2015-05-24
forum: New to Ubuntu
---

### Post by charmingnathan2 on 2015-05-24
Hello,

I'm not entirely sure that I  should be posting this here, it maybe more appropriate to post it to the  CentOS Forum, but one has to start somewhere, so here goes!

My  main P.C. runs CentOS 6.5, I have a secondary Hard Drive that I wish to  slave up, BUT firstly it is damaged to the point that it won't boot up  on its own, and secondly it has (an albeit damaged) installation of  Ubuntu Jaunty Jalope installed - it could be Karmic Koala, but to be  honest it's so long since I've been able to access the drive, I can't  remember!

I wish to rescue some pictures from the Waste Basket.

I  am able to access the drive through mounting through the G.U.I. but as  the Waste Basket is stored within the .local folder, I need to be able  to access it as root, but have had no success in doing so (from Terminal):

```
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe769d696

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2450    19679593+  83  Linux
/dev/sda2            4866        9729    39070080    5  Extended
/dev/sda5            4866        9541    37559938+  83  Linux
/dev/sda6            9542        9729     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40036678144 bytes
255 heads, 63 sectors/track, 4867 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00089425

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          64      512000   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sdb2              64        4868    38584320   8e  Linux LVM

Disk /dev/mapper/vg_nathandesktop-lv_root: 37.4 GB, 37392220160 bytes
255 heads, 63 sectors/track, 4546 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/vg_nathandesktop-lv_swap: 2113 MB, 2113929216 bytes
255 heads, 63 sectors/track, 257 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

[root@nathan-desktop ~]# mount /dev/sdb2/slavedrive  /mnt/sdb2/slavedrive
mount: you must specify the filesystem type
[root@nathan-desktop ~]# mount /dev/sdb2/  /mnt/sdb2/slavedrive
mount: mount point /mnt/sdb2/slavedrive does not exist
```

I'd very much appreciate your help.

Thanks.

---

### Post by tgalati4 on 2015-05-24
On 14.04 Trash is located:

> tgalati4@Mint17 ~/.local/share/Trash/files $ ls
14_540ca_filled.pdf        9781461439080-c1.pdf  libraries.2                   Pecos.jpg         SHT15.zip         SHT1x_Old
2014_1040.pdf              cd4013b-mil.pdf       libraries.3                   ReadSHT1xValues   SHT1x             Thermistor_50K.pdf
2014_540_Filled.pdf        f1040.pdf             Master_bath_calculations.pdf  sht15demo.ino     SHT1x.h
3552_affidavit_signed.pdf  libraries             mozilla.pdf                   SHT15Sparkmaster  SHT1x-master.zip


If you can mount the drive, you should be able to:

```
cd
cd .local/share/Trash/files
```

Modify the command to reflect your actual mount location.  It's probably something like /media/charmingnathan2/home/charmingnathan2/.local/share/Trash/files.

If you want to recover jpegs, then install *testdisk* and use *photorec* to recover your photos.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by charmingnathan2 on 2015-05-24
Thanks very much tgalati4.

I did actually manage to mount the correct drive, which was where the issue was, eventually, and located the Trash /files in the place you said it would be in.

However, the pictures I thought would be there, weren't.

If I wiped CentOS 6.5 and installed Ubuntu, so it became a Ubuntu to Ubuntu setup, I presume this wouldn't make any difference, i.e. Ubuntu wouldn't see any files that CentOS wouldn't?

Cheers.

---

### Post by Vladlenin5000 on 2015-05-24
> **charmingnathan2 said:**
> Ubuntu wouldn't see any files that CentOS wouldn't?

No, it wouldn't.
What you need was already mentioned in the first reply.

---

### Post by charmingnathan2 on 2015-05-24
Thanks for the reply Vladlenin5000.

Point taken! I have downloaded testdisk and installed photorec which is, I hope, currently scanning the faulty Hard Drive.

As a side issue, I note within testdisk itself there in an option to write a new Master Boot Record.

Baring in mind the drive is damaged, it was originally configured to work with another Hard Drive that booted into XP, that drive no longer works.

If I were to chose the option to write a new M.B.R., what are the chances the original Ubuntu drive would be bootable again?

It should be noted that while I had it mounted under CentOS I ran badblocks on the drive.

Thanks for your help.

---

### Post by tgalati4 on 2015-05-24
It's hard to say what would happen.  Recover your photos first with *photorec*.  Once you have recovered as much as you can, then you can consider trying to fix the partition table (and MBR) with *testdisk* to make it bootable.  If you have multiple partitions with WinXP and Centos, then there is a fair chance that you can fix the drive and get both operating systems working again.

When you ran *badblocks* under Centos did you find any bad blocks?

Install *smartmontools* and report the SMART status of the drive:

```
sudo apt-get install smartmontools
sudo smartctl -a /dev/sde
```

Your drive designation can be found with:

```
sudo fdisk -l
```

---

### Post by charmingnathan2 on 2015-05-25
Thanks for your reply tgalati4.

Badblocks found so many errors it crashed my system (which also currently runs CentOS) three times and I had to re-boot!

With regards to repairing the M.B.R. and partition table, it ain't as simple as that!

I had Ubuntu and XP installed across TWO Hard Drives, so in effect, when the boot options came up, selecting Ubuntu sent you to one Hard Drive, XP to the other.

The drive XP was installed on had a power failure, though I understand it's possible to potentially repair this by replacing the S.M.A.R.T. card.

So I'm not sure how possible it is to, essentially, repair half an M.B.R., assuming it was saved between both the drives...?!

---

### Post by tgalati4 on 2015-05-25
If *badblocks* crashed, then that would indicate serious problems with the disk drive.  File recovery may be difficult.  If you read through the GRUB documentation, you can set up GRUB on one or both drives and you can add entries at the bottom of the GRUB list to point to the other drive.  This is handy if one drive crashes, then you can simply jump to the other drive and still boot correctly.  You can try to repair the MBR on the WinXP drive, but I would remove the Ubuntu/Centos drive so it doesn't get touched.

Regarding missing files, if you have enough bad blocks, then the drive runs out of places to reallocate bad sectors and you loose data very quickly.

---

