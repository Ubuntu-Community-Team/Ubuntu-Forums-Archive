---
title: "[SOLVED] Which drive to install Ubuntu on"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by a.v.l on 2008-06-22
I in need advice on which drive to install Ubuntu on in my Acer 7720 laptop. When I insert the installation disk and press install I get to the partition window where I have to choose either a guided, manual of use one of the two hard drives on this laptop. This is where my problem starts, I'm cannot identify the hard drive I should use for Ubuntu and my concern is that I will end up removing Vista which I don't want to do at the moment. Can someone help please?

---

### Post by bodhi.zazen on 2008-06-22
See this link :

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=282018") 

You can see your partitions if you start gparted, it is in the system menu

Or open a terminal and enter :
```
sudo fdisk -l
```

---

### Post by Nikitas350 on 2008-06-22
You have to resize a partition and make two others. One in ext3 format and one swap. For the ext3 set the mountpoint to /. Then you can continue the installation...

---

### Post by a.v.l on 2008-06-22
> **bodhi.zazen said:**
> See this link :

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=282018") 

You can see your partitions if you start gparted, it is in the system menu

Or open a terminal and enter :
```
sudo fdisk -l
```

Thanks this is the result which di I install Ubuntu on please?

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeb4de1f0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1402    11261533+  27  Unknown
/dev/sda2   *        1403       15918   116592640    6  FAT16
/dev/sda3           15918       30402   116342784    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeb4de1f1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS
ubuntu@ubuntu:~$

---

### Post by sayakb on 2008-06-22
/dev/sda1 seems like a free partition. You can resize it to make out a **swap partition** equiv to the size of your RAM, a 10GB **/ partition** (ext3 fs) and rest of the space a **/home** (ext3 fs)

---

### Post by bodhi.zazen on 2008-06-22
Looks like windows is on your first hard drive, sda

So you would want to install on sbd.

If you wish you can select "use entire hard drive" and Ubuntu will do the rest. **This will destroy any data on the second hard drive**.

If you have data on the second hard drive you wish to keep you can either move it to the first hard drive or resize your partition with gparted.

You should defragement the hard drive first (b4 you resize it) and of course back up your data.

You resize with gparted : [Gparted Documentation](http://gparted.sourceforge.net/documentation.php)

The other option is to learn about partitioning first so that you can manually partition your hard drive. This second option is not necessary, but obviously it helps a great deal.

Just be sure to back up your data b4 you install. Although rare, a mistake or error will result in data loss.

---

### Post by sharks on 2008-06-22
Use Gparted to partition ur drive. use / as mountpoint.

---

### Post by a.v.l on 2008-06-22
Thanks everyone I have Ubuntu installed as a dual boot now.

---

