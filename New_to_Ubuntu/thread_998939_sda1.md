---
title: "sda1"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by JimHebert on 2008-12-01
How do I determine on my vista OS if the internal drive C is sda1, sda2, etc.? Where do I find that info?

---

### Post by bhadotia on 2008-12-01
> **JimHebert said:**
> How do I determine on my vista OS if the internal drive C is sda1, sda2, etc.? Where do I find that info?

I don't know about how to find that out in vista but sure can find this out in ubuntu using gparted partition editor for a graphical view of the hard disk. Type:
```
sudo apt-get install gparted
```in the terminal to install gparted and then launch it from System>Administration>Partition Editor.
Actually sda1 means scsi disk a (partition) 1- meaning it designates the partition number 1 on your first (a) scsi disk (HDD). And as Vista only install on the first primary partition of the disk your (and of everyone else)Vista is on sda1.

---

### Post by __Ryan__ on 2008-12-01
The drive letter such as the /dev/sd**a**1 is determined by boot order in BIOS.  The partition /dev/sda**1** by partition order, at least the logical (first 4) ones I believe.  So if windows is using the first partition for its C: drive then it would most likely be /dev/sda1.

In Linux you can find this out by:

```
sudo fdisk -l
```

It will show you each drive partition and its file system label.

---

### Post by mapes12 on 2008-12-01
Re: sda1
> Quote:
Originally Posted by JimHebert View Post
How do I determine on my vista OS if the internal drive C is sda1, sda2, etc.? Where do I find that info?
I don't know about how to find that out in vista but sure can find this out in ubuntu using gparted partition editor for a graphical view of the hard disk. Type:
Code:

sudo apt-get install gparted

in the terminal to install gparted and then launch it from System>Administration>Partition Editor.
Actually sda1 means scsi disk a (partition) 1- meaning it designates the partition number 1 on your first (a) scsi disk (HDD). And as Vista only install on the first primary partition of the disk your (and of everyone else)Vista is on sda1.

Not my preferred option. If you run GParted from a running system you will get strange results. Either:

1. Boot your system from a Ubu Live CD and run GParted from there.
2. Burn an iso CD from the GParted website (Google it) and boot from that

Then look for the partition labelled NTFS. That will be your windoze partition.

---

### Post by halitech on 2008-12-01
running fdisk -l seems a lot easier, even if it is in the command line :D

typically /dev/sda would be your primary master, sdb primary slave, /dev/sdc secondary master and sdd would be seconday slave. (is it okay to use the word slave on here? don't want to be politically incorrect). If you only have 1 physical hard drive you would need to look at the info from fdisk -l to know if its sda1, sda2, etc.

---

### Post by bhadotia on 2008-12-01
> **mapes12 said:**
> Re: sda1


Not my preferred option. If you run GParted from a running system you will get strange results. Either:

1. Boot your system from a Ubu Live CD and run GParted from there.
2. Burn an iso CD from the GParted website (Google it) and boot from that

Then look for the partition labelled NTFS. That will be your windoze partition.

I'm not saying that OP go and actually edit his/her partitions. He just wanted a way to find which partition is sda 1 and IMHO gparted provides a nice graphical view.
Of course, you cannot find which partition is sda1 from windows because windows uses its own naming scheme for the partitions (Drive letters: C,D,E etc.) (Therefore any graphical utility in windoze will not show which partition is sda1). Whereas the sda scheme is linux scheme for naming paritions.
Regarding, fdisk -l, though it is good  but it does not provide necessary info, only block sizes are shown.

---

### Post by halitech on 2008-12-01
actually, it will also show the system type which would give us a pretty good idea where windows is

```
daryl@debian-desktop:~$ sudo fdisk /dev/hda -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005d3c5

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          30      240943+  83  Linux
/dev/hda2              31        3069    24410767+  83  Linux
/dev/hda3            3070        3251     1461915   82  Linux swap / Solaris
/dev/hda4            3252       19457   130174695   83  Linux

```

granted I don't have windows so it doesn't show up on my system :D

---

