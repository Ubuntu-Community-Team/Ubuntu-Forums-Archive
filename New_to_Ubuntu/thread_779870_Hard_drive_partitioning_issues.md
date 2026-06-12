---
title: "Hard drive partitioning issues"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by ajita on 2008-05-03
Hey all, Im completely new to linux and would like some advice on getting started here. I have windows XP and Ubuntu installed on a 250 Gig drive. I installed ubuntu (before partitioning the hard drive) and then partitioned it with gparted into a 40Gig Ntfs type, 10 Gig FAT32 type and the rest as ext2. Now my problem is that I dont know which partition Ubuntu is in. Is there any way for me to find out? GParted lists the ntfs partition as the /boot,/host. Also, when I tries to import my backup files from an external drive I get a message saying there is only 10 GIGs of space on my drive. Is Ubunto actually on the ntfs partition? How do I resolve this problem? How do I get Ubuntu to the ext2 partition and transfer my backed up files over? 
I've finally gotten the courage to leave windows and am really interested in the philosophy of open source, but Im finally stuck and really really need some help. I would appreciate if someone could guide me through this step by step. I am a total newbie at this and am eternally grateful for any help,
Thanks,
Ajita

---

### Post by kirios on 2008-05-03
Type **sudo fdisk -l** in a terminal (Applications > Accessories > Terminal) and post the output here.

---

### Post by Thingymebob on 2008-05-03
in a terminal type :
```
sudo mount -l
```
the output should read
```
/dev/hda1 on / type ext2.....
```
if you linux is on the ext2 partition 
(hda1 might be different depends on your partition order)

the important thing is that / is on the ext2 Filesystem.

---

### Post by ajita on 2008-05-03
> **kirios said:**
> Type **sudo fdisk -l** in a terminal (Applications > Accessories > Terminal) and post the output here.
Hey Kirios, here it is:

fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

---

### Post by kirios on 2008-05-03
It's **fdisk -l** (as in london) ... you seem to have typed in fdisk -1 (as in 123). 

Please post the output of **mount** as well. 

> **ajita said:**
> Hey Kirios, here it is:

fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version

---

### Post by Stefanie on 2008-05-03
you should type ```
sudo fdisk -l
``` . the last character is the letter "l", not the number one.

---

### Post by ajita on 2008-05-03
Thanks a lot. I typed in the correct command now and here is the output:

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xab48ab48

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6448    51793528+   7  HPFS/NTFS
/dev/sda2            7947       24321   131532187+  83  Linux
/dev/sda3            6449        7946    12032685    b  W95 FAT32

Partition table entries are not in disk order

---

### Post by ajita on 2008-05-03
Here is the output for sudo mount -l

/host/ubuntu/disks/root.disk on / type ext3 (rw,errors=remount-ro) []
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
/host/ubuntu/disks/boot on /boot type none (rw,bind)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/ajita/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ajita)
/dev/sda2 on /media/disk type ext2 (rw,nosuid,nodev,uhelper=hal) []

Thanks a lot!

---

### Post by Thingymebob on 2008-05-04
So you installed with wubi, your ubuntu install will be using your windows ntfs partition. To get it to its own dedicated partition you need to use LVPM [(http://lubi.sourceforge.net/lvpm.html)]("http://lubi.sourceforge.net/lvpm.html"). 

This will guide you through converting your wubi install to a standard ubuntu install. This will also mean that the add/remove Ubuntu in windows will probably no longer work.

---

### Post by kirios on 2008-05-04
Ubuntu is on the ntfs partition, so you must have used Wubi to install. You can either keep things as they are and use /media/disk (the large ext2 partition) for your files OR reinstall Ubuntu the conventional way by booting from the CD/DVD and installing to an ext3 partition. 

EDIT: Just noticed *Thingymebob*'s post, linking to [http://lubi.sourceforge.net/lvpm.html]("http://lubi.sourceforge.net/lvpm.html") which suggests that "*once the install has been completed, you may remove the original Wubi installation*" - so you have a 3rd option now. :-)

---

### Post by ajita on 2008-05-04
Thanks a bunch guys, that was a lot of help.

---

### Post by ajita on 2008-05-04
I have it installed and running well. Appreciate all the help, this community is great, thanks!

---

