---
title: "Changing device of Linux swap"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by sy88 on 2008-05-02
Hi, first of all, I'd like to say that my Ubuntu install is working fine.  However, Is there a way to switch my Linux swap from /dev/sdb5 to /dev/sdb4?  Here is my sudo fdisk -l```
stanley@Saber-chan:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0b1d6226

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       59525   375736252+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc754c754

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3824    30716248+  83  Linux
/dev/sdb2            3825       60045   451595182+   7  HPFS/NTFS
/dev/sdb3           60046       60801     6072570    5  Extended
/dev/sdb5           60046       60801     6072538+  82  Linux swap / Solaris

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001    7  HPFS/NTFS

```

---

### Post by glennric on 2008-05-02
Since you don't have a /dev/sdb4 it should be doable.  Try the following:
```
sudo swapoff /dev/sdb5
sudo mkswap /dev/sdb4
sudo swapon /dev/sdb4
```
You will then have to modify the file /etc/fstab to point to the new UUID of the swap partition.  This can be found by typing "ls -al /dev/disk/by-uuid".
If you hibernate or suspend you will probably need to also put the new UUID in the file  /etc/initramfs-tools/conf.d/resume and do "sudo update-initramfs -u".

If you need more details ask.

Edit:  I am missing a step.  You need to delete the swap partition after doing the swapoff.  I am not sure how to do this from the command line, although it is not hard to do with gparted (Partition Editor), as well as create the swap partition.

---

### Post by glennric on 2008-05-02
Okay, so I don't think my directions were very good so here goes again.  Open gparted, select the drive sdb.  Then select sdb5, right click, and select swapoff.  Then delete the partition.  Then create a new partition as linux swap.  It should now be /dev/sdb4.  Then fix fstab and the other file I suggested before.  

There much easier.

---

### Post by sy88 on 2008-05-03
> **glennric said:**
> Okay, so I don't think my directions were very good so here goes again.  Open gparted, select the drive sdb.  Then select sdb5, right click, and select swapoff.  Then delete the partition.  Then create a new partition as linux swap.  It should now be /dev/sdb4.  Then fix fstab and the other file I suggested before.  

There much easier.

Thanks for replying. I tried using GParted to delete and then recreate my linux swap, but it still stays on /dev/sdb5.

I looked more into fdisk on sdb: ```
stanley@Saber-chan:~$ sudo fdisk /dev/sdb

The number of cylinders for this disk is set to 60801.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): x

Expert command (m for help): p

Disk /dev/sdb: 255 heads, 63 sectors, 60801 cylinders

Nr AF  Hd Sec  Cyl  Hd Sec  Cyl     Start      Size ID
 1 80   1   1    0 254  63 1023         63   61432497 83
 2 00 254  63 1023 254  63 1023   61432560  903190365 07
 3 00 254  63 1023 254  63 1023  964622925   12145140 05
 4 00   0   0    0   0   0    0          0          0 00
 5 00 254  63 1023 254  63 1023         63   12145077 82

```

It seems sdb4 exists but is just blank??  Does it need to be deleted?

---

### Post by sy88 on 2008-05-03
I solved it.  My Linux swap was actually a logical partition under the extended partition /dev/sdb3.  Deleting my linux swap and reformatting /dev/sdb3 as a primary partition fixed it.

---

