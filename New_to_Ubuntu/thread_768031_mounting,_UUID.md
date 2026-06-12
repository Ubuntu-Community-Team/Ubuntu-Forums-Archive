---
title: "mounting, UUID"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by krisfrajer on 2008-04-26
I have ubuntu 7 and I need to mount my new partition I created with gparted for backup purposes. It is define as /dev/hda7 with ext3 file system. I tried to mounted on /export/backup but it says I need to create a mounting point first. How can I do that?

sudo mount -t ext3 /dev/hda7 /export/backup
mount: mount point /export/backup does not exist


cristian@NARUTO:~$ sudo fdisk -l

Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12799728

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        8052    64677658+  83  Linux
/dev/hda2            8053       24321   130680742+   5  Extended
/dev/hda5           23971       24321     2819376   82  Linux swap / Solaris
/dev/hda6            8053       16298    66235932   83  Linux
/dev/hda7           16299       23970    61625308+  83  Linux

Partition table entries are not in disk order

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01ae01ae

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9728    78140128+   7  HPFS/NTFS



cristian@NARUTO:~$ more /etc/mtab
/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
/dev/hda6 /export/home ext3 rw 0 0
/dev/hdb1 /media/hdb1 fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
tmpfs /dev/shm tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0


K.

---

### Post by tamoneya on 2008-04-26
```
sudo mkdir /export/backup
```

---

### Post by krisfrajer on 2008-04-26
How can i make it a permanent mounting?
Do I need the UUID number of this new partition so to add it on the fstab file? How can I get this number? Thank you,
K.

---

### Post by tamoneya on 2008-04-26
although some people put the uuid into /etc/fstab it is not necessary.  For your partition you could add the following line to the end of fstab```
/dev/hda7 /export/backup ext3 defaults 0 0
```

---

