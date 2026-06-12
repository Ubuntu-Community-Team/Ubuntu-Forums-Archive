---
title: "harddrive back up"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by Geir102 on 2008-09-14
hi is there any way to back up a harddrive? Like in a iso file to late restore it. The drive is only 10GB

---

### Post by R_T_H on 2008-09-14
Search for "back up" in Synaptics. That might provide some useful programs :)

---

### Post by k33bz on 2008-09-14
or if you want to go the hardware route you can go to this link:

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2329300&Sku=M501-1220]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2329300&Sku=M501-1220")

---

### Post by Geir102 on 2008-09-14
I've heard of a command "dd" any one know anything about that? I've put the hard drive in an ubuntubox but it wont mount. I find it in windows but not ubuntu. Any one know how to fix it? There is windows ME on it

---

### Post by scorp123 on 2008-09-14
"How to backup your stuff UNIX-style:"

[http://www.linuxmint.com/forum/viewtopic.php?f=42&t=3969&start=0&st=0&sk=t&sd=a](http://www.linuxmint.com/forum/viewtopic.php?f=42&t=3969&start=0&st=0&sk=t&sd=a)

---

### Post by scorp123 on 2008-09-14
> **Geir102 said:**
> I've heard of a command "dd"  You did read the manual of "dd" and you understand that tampering with "dd" could lead to data loss especially if you don't know WTH you're doing? Yes? If not you might want to read the manual: ```
man dd
```

And making backups with "dd" is not a good idea as you will be copying the disk 1:1 including empty space. It's a very inefficient method.

> **Geir102 said:**
>  I've put the hard drive in an ubuntubox but it wont mount. I find it in windows but not ubuntu. Please explain in more details what you did and why. You put what harddrive where?? What for? And please supply the output of these commands: ```
sudo fdisk -l
mount
cat /etc/fstab
```

---

### Post by louieb on 2008-09-14
A couple of things for you to look at.

partimage available on the  [SystemRescueCd]("http://www.sysresccd.org/Main_Page")  - yes its in the repository too I just prefer using the System rescue CD. [Howto: Backup with Partimage - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=287522") 

And [Clonezilla]("http://www.clonezilla.org/")  pretty nice I've seen it combined with other programs Such as GParted, partimage, SystemRescueCD and super grub on one CD

---

### Post by robert shearer on 2008-09-14
Is this a hard drive that's in addition to the one with your Ubuntu install on it (ie a drive with user data) or is it your complete Ubuntu install on a small drive?

If the latter then these links are worth a look.
 
[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)
[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

if the former then ignore this post.

---

### Post by Geir102 on 2008-09-15
tanks for all the response:) First scorp123 heres the results:

$ sudo fdisk -l

Disk /dev/sda: 20.4 GB, 20418772480 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1971    15832026    7  HPFS/NTFS
/dev/sda2            1972        2002      249007+  82  Linux swap / Solaris
/dev/sda3            2003        2482     3855600   83  Linux

Disk /dev/sdb: 10.2 GB, 10240274432 bytes
255 heads, 63 sectors/track, 1244 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         447     3590496    b  W95 FAT32
/dev/sdb2             448        1244     6401902+   f  W95 Ext'd (LBA)
/dev/sdb5             448        1244     6401871    b  W95 FAT32

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    7  HPFS/NTFS

***************************

$ mount
/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-17-generic/volatile type tmpfs (rw)
/dev/disk/by-uuid/BC4CB7ED4CB7A116 on /media/sda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdc1 on /media/disk type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

***********

$ cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda3 :
UUID=447fe302-b2f2-480b-804c-a3d0cd96a886 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda1 :
UUID=BC4CB7ED4CB7A116 /media/sda1 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sdb1 :
UUID=7E88F11488F0CC21 /media/sdb1 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sda2 :
UUID=84b5fcd7-6abf-4eca-9687-c38ecbd9df49 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

---

### Post by Geir102 on 2008-09-15
so what I'm trying to do is: I have a harddirve whit Windows ME on C:. I have plugde that into a box with ubuntu allready installd. So the one i want to back up is a seperate hard drive. I want to make an image of that partition.

If forexsampel I wood be abel to make a back up of the c: partition that i coud run in some virtual machine like wmware that wood be great.

---

### Post by Geir102 on 2008-09-15
Ok i fixed the mounting problem. Only the back up again

---

