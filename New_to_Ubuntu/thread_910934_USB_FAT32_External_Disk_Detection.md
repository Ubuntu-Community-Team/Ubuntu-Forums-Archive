---
title: "USB FAT32 External Disk Detection"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by nitinwagale on 2008-09-05
Dear Friends,
              First of all thanks to all who give their time for solving problems.

I have now shifted from Windows XP to Ubuntu 8.04. I am new to Linux. I have a small problem. The USB External Drive is not detected on my system. 

The details of my system are as follows :

Processor   : AMD Athlon 64 X2 Dual-Core 4000+
Motherboard : ASUS M2N8-VMX (Nvidia GeForce 6100 nForce 430)
RAM         : DDR-II 2048 Mb (533 Mhz)
Hard Disk   : Seagate SATA 160 GB
DVD Drive   : MoserBaer Liteon
Monitor     : IBM E74 Colour Monitor

I have installed Ubuntu 8.04 (AMD 64 bit Version) using a live cd.

Reading some of the posts and help files, I was able to get disk information. The output is posted below.

**nitin@nitin-desktop:~$ sudo fdisk -l**

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf673f673

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       18752   150625408+  83  Linux
/dev/sda2           18753       19457     5662912+   5  Extended
/dev/sda5           18753       19457     5662881   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40007761408 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0b4015f2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4864    39070048+   c  W95 FAT32 (LBA)

**nitin@nitin-desktop:~$ sudo fdisk /dev/sdb1**

The number of cylinders for this disk is set to 4863.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

I have a flash (pen) drive of 512 Mb which is detected but the bigger one FAT32 External Disk (40 Mb) is not detected.

I had a small encounter with Ubuntu 7 earlier, but it was not a good experience. I had a dual-boot system, Windows XP and Ubuntu 7. Due to some foolishness by me I was not able to access Ubuntu. I could not recover my thesis data and lost six months.

Now, I am not able to transfer the data on a External Disk to Ubuntu 8.04. I guess this does not mean that Linux doesn't suit me or I ma not for Linux.

I shall appreciate if any solution is given to solve my problem. One more request, please give the solution in a simple way.

Once again thanks to all for taking the time to read this.

Regards,

Nitin !

---

### Post by kpkeerthi on 2008-09-05
You could try mounting the disk manually. 

1. Connect your disk and wait for a few seconds.
2. Make sure **fdisk -l** is able to list the partition /dev/sdb1.
3. Create a folder where you want the partition mounted:
```
sudo mkdir /media/MyThesis
```
4. Mount the parition:
```
mount -t vfat -o iocharset=utf8,umask=000 /dev/sdb1 /media/MyThesis
```

You should see a shortcut on your desktop. Post back the errors if any.

---

