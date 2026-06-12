---
title: "Installation woes"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by Grolber on 2008-08-06
I've been trying to get Ubuntu 8.0.4 installed on my machine over the last couple of nights with no joy.

I downloaded the iso of the live cd and burnt and verified it ok.
I can boot from it, but it only gets so far into the install before coming up with a busy box prompt - initramfs ata3, comreset failed errno=16.

After a bit of digging, I booted the live version, got Ubuntu up and running and then tried to use the installer there - but it can't see the hard drive I'm trying to install to.

I have four HDs, the main drive (SATA) which has windows, a pair of mirrored SATA drives and a single IDE (with 2 partitions) - which is where I'm trying to install to. The IDE drive didn't show up in the installer (although my i-pod did!).

Then I tried to use Wubi - which could see the partition on the IDE drive I wanted to use, downloaded ok, setup, put a Ubuntu entry into my boot options. But when I choose that entry - it drops me downto a Grub prompt.

I figure it's getting confused by the number of drives and partitions I have - but I'm not exactly certain what I need to do next.


G.

---

### Post by ugm6hr on 2008-08-06
> **Grolber said:**
> After a bit of digging, I booted the live version, got Ubuntu up and running and then tried to use the installer there - but it can't see the hard drive I'm trying to install to.

I have four HDs, the main drive (SATA) which has windows, a pair of mirrored SATA drives and a single IDE (with 2 partitions) - which is where I'm trying to install to. The IDE drive didn't show up in the installer (although my i-pod did!).

Let's see if we can find it...

Boot the LiveCD
Applications-> Accessories-> Terminal
```
fdisk -l
```
copy / paste the output here.  Can you identify the IDE in the list?

Another way is to find it in System-> Administration-> Partition Editor (aka GParted)

If Ubuntu can see the HD, we should be able to find a way to install to it.

---

### Post by DJH10 on 2008-08-06
I had a similar problem,i have 3 hd's,1 IDE,2 SATA.I was trying to install Ubuntu on the IDE but had issues,in the end i just unplugged both SATA hd's and left the IDE one plugged in.Installed without a problem after that and then i just plugged the 2 SATA hd's back in and everything is working fine

---

### Post by Grolber on 2008-08-06
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc11bc11b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4462    35840983+   7  HPFS/NTFS
/dev/sda2            4463        4984     4192965    f  W95 Ext'd (LBA)
/dev/sda3            4985        8808    30716280    7  HPFS/NTFS
/dev/sda4            8809       14593    46468012+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xff2c89bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19581   157284351    7  HPFS/NTFS
/dev/sdb2           19582       23497    31455270    7  HPFS/NTFS
/dev/sdb3           23498       30024    52428127+   7  HPFS/NTFS
/dev/sdb4           30025       38913    71400892+   7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xff2c89bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19581   157284351    7  HPFS/NTFS
/dev/sdc2           19582       23497    31455270    7  HPFS/NTFS
/dev/sdc3           23498       30024    52428127+   7  HPFS/NTFS
/dev/sdc4           30025       38913    71400892+   7  HPFS/NTFS
ubuntu@ubuntu:~$ 

Doesn't look right...
First drive is 120Gb SATA and is the boot disk
Drives 2 & 3 are 320GB SATA mirrored (supposed to be HW RAID !)
Drive 4 is IDE - 160GB with around 40Gb being the slice I want to install on. It looks like it can't see past the mirror set (which it sees as separate drives ... hmmmmm).

G.

---

