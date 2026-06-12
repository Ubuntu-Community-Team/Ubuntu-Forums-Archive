---
title: "Mounting of drive partition is not happening"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by drao on 2008-05-16
HI all,

Mine is dual boot PC one Xp and other is ubuntu. I have C: to F: partitions of 20 Gb  each. On F partition, i reserved 10Gb for Ubuntu. I installed ubuntu7.10 on that part of F and i edited /etc/fstab file to detect my xp drive partitions also whenever it boots so that i can use them in linux also. Now i upgraded to 8.04 recently, now fstab contains drive partition mounting details. But whenever i open my xp drive partition in ubuntu, it not showing up any folders inside the partition. Showing it is any empty partition. 

Thanks in advance

---

### Post by hermes0710 on 2008-05-16
Can you post your /etc/fstab?
Also open a terminal and try to manually mount your xp partition. What error do you get?

---

### Post by drao on 2008-05-18
drao@Dhanu:~$ sudo mount
/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/scd0 on /media/Matrix,Ter1,Maha type iso9660 (ro,nosuid,nodev,uhelper=hal,uid=1000,utf8)
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/scd0 on /media/Matrix,Ter1,Maha type iso9660 (ro,nosuid,nodev,uhelper=hal,uid=1000,utf8)
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
drao@Dhanu:~$ 

and fstab fle contains::

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=6fae0d0a-15fa-4794-b6b7-167b709a5992 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda8
UUID=ff1fe62b-1b36-4701-a0c7-0084d71b9c64 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/hda5      /mnt/media  auto rw,user,auto,exec 0 0
/dev/hda7     /mnt/software auto rw,user,auto,exec 0 0
/dev/hda5      /mnt/dhanu  auto rw,user,auto,exec 0 0
/dev/hda1      /mnt/win auto rw,user,auto,exec 0 0

---

### Post by hyper_ch on 2008-05-18
(1) use **[noparse]```

```[/noparse]** tags about output stuff that you post.... makes things a lot easier to read
(2) also post content of
```

sudo fdisk -l

```

---

### Post by drao on 2008-05-18
fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x671f671f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+   c  W95 FAT32 (LBA)
/dev/sda2            2433        8658    50010345    f  W95 Ext'd (LBA)
/dev/sda3            8659        9729     8602807+  83  Linux
/dev/sda5            2433        4864    19535008+   b  W95 FAT32
/dev/sda6            4865        7296    19535008+   b  W95 FAT32
/dev/sda7            7297        8604    10506478+   b  W95 FAT32
/dev/sda8            8605        8658      433723+  82  Linux swap / Solaris

Disk /dev/sdb: 2051 MB, 2051014656 bytes
33 heads, 63 sectors/track, 1926 cylinders
Units = cylinders of 2079 * 512 = 1064448 bytes
Disk identifier: 0xba6f73f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1927     2002928    b  W95 FAT32

---

### Post by volkswagner on 2008-05-18
Your fstab and fdisk -l don't agree. hda vs. sda?

---

### Post by drao on 2008-05-18
Thanks. I didnt noticed it. Now am able to access the partitions.


But i have a doubt, because of upgrade, name has changed or what might be the reason. I used same fstab file before up gradation and i was able to access drive partitions.

---

