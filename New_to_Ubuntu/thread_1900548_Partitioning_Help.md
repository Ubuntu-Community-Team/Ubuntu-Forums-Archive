---
title: "Partitioning Help"
date: 2011-12-26
forum: New to Ubuntu
---

### Post by Giraffemonster on 2011-12-26
Hello, I used to have a dual-boot system with Xubuntu 11.10 and Windows XP, then I deleted that partition. I have a 40GB Maxtor hard drive, and the Windows partition took up 20GB. I'm looking for a way to add that 20GB of unallocated space to my Linux partition.

The output of fdisk -l reads as follows:

```
Disk /dev/sda: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78156288 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e0b47

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2        39018494    78155775    19568641    5  Extended
/dev/sda5   *    39018496    73965567    17473536   83  Linux
/dev/sda6        73967616    78155775     2094080   82  Linux swap / Solaris

```

Is there any way for me to end up with a primary partition of Xubuntu (Which would be resized to format all the free space), and the swap with no extended partition without having to reformat my hard drive?

---

### Post by wolfen69 on 2011-12-26
[https://help.ubuntu.com/community/HowtoPartition/ResizingPartition](https://help.ubuntu.com/community/HowtoPartition/ResizingPartition)

You can use a Gparted live cd for this.

---

### Post by khelben1979 on 2011-12-26
When it comes to the partition which you used for Windows XP. I would advise you to format that partition with the EXT3 or EXT4 filesystem so you better can use it for your Linux system for extra storage, you can split it in several partitions and add them to your current partitions if necessary.

To my knowledge, you cannot resize that partition to make it work with the other partitions (correct me if I'm wrong), since the location is on the beginning of the hard disc and not in between the other partitions.

Making backup, then reinstall for a new Ubuntu system would be the easiest thing to do, and to recommend in my opinion.

---

### Post by Giraffemonster on 2011-12-26
> **khelben1979 said:**
> When it comes to the partition which you used for Windows XP. I would advise you to format that partition with the EXT3 or EXT4 filesystem so you better can use it for your Linux system for extra storage, you can split it in several partitions and add them to your current partitions if necessary.

To my knowledge, you cannot resize that partition to make it work with the other partitions (correct me if I'm wrong), since the location is on the beginning of the hard disc and not in between the other partitions.

Making backup, then reinstall for a new Ubuntu system would be the easiest thing to do, and to recommend in my opinion.

I've decided just to do your first suggestion, formatting the unallocated space to an ext4 partition. Thanks anyway.

---

