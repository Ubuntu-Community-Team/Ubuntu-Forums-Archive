---
title: "Mounting problems"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by blue_shift on 2008-08-02
I have an external HDD connected by USB. It has two partitions: one (larger) FAT32 partition, and one (smaller) encrypted ext3 partition. I am having some trouble mounting the encrypted partition, but I think it's just a simple fstab thing I'm doing wrong.

```
Disk /dev/sde: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       13951   112061376    c  W95 FAT32 (LBA)
/dev/sde2           13952       14593     5156865   83  Linux

```

Now if I try to mount the encrypted partition: ```
Method "Mount" with signature "ssas" on interface "org.freedesktop.Hal.Device.Volume" doesn't exist
```

Some of my attempt:```
alex@af-desktop:~$ mount /dev/sdb1
mount: according to mtab, /dev/sdb1 is already mounted on /media/Passport
mount failed
alex@af-desktop:~$ umount /dev/sdb1
/sbin/umount.hal: /dev/sdb1 is not recognized by hal
alex@af-desktop:~$ cat /etc/mtab
/dev/sda6 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-19-generic/volatile tmpfs rw 0 0
/dev/sdb1 /media/Passport vfat rw,nosuid,nodev,noatime,uhelper=hal,flush,uid=1000,utf8,shortname=lower 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
alex@af-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=6ebb54a5-9bba-41c4-b32d-35802d1f0435 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=c7a18e8d-f6f6-4598-9d9e-a655b58eb28e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1 /media/Passport vfat rw,nosuid,nodev,noatime,uhelper=hal,flush,uid=1000,utf8,shortname=lower 0 0

```

Confusingly, the device is listed as /dev/sde1 and /dev/sde2, but originally was sdb1 and 2. It seems every time it tries to mount, it is gaining a letter. Also, the mountpoint of /dev/sde1 is now /media/WD Passport1 rather than just /media/WD Passport, which is the default.

```
alex@af-desktop:~$ cd /media
alex@af-desktop:/media$ ls
cdrom  cdrom0  disk  Passport  WD  WD Passport  WD Passport-1

```

I'm guessing I just need to write something in /etc/mtab, but I don't know how to / what to do.

Thanks.

---

### Post by Pro-reason on 2008-08-03
Unless the device has the option "user" in its /etc/fstab entry, you always need to run "mount" with "sudo".

---

### Post by blue_shift on 2008-08-03
Good point. Thanks.

I pretty much worked it out. In the end I deleted some unused folders in the /media directory, wrote some new entries into fstab and used the command
```
sudo mke2fs -j /dev/mapper/name -L label
```
In the context of this tutorial: [http://ubuntu-tutorials.com/2007/08/17/7-steps-to-an-encrypted-partition-local-or-removable-disk/]("http://ubuntu-tutorials.com/2007/08/17/7-steps-to-an-encrypted-partition-local-or-removable-disk/")

---

