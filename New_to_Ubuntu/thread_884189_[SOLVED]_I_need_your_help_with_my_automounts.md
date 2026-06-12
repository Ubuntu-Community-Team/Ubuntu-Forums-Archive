---
title: "[SOLVED] I need your help with my automounts"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by arbitrage1 on 2008-08-08
So Ive followed this thread
[http://ubuntuforums.org/showthread.php?t=871881](http://ubuntuforums.org/showthread.php?t=871881)

and this thread
[http://ubuntuforums.org/showthread.php?t=802699](http://ubuntuforums.org/showthread.php?t=802699)

but I can not get my partitions to automount. If you could take a look at my setup and make a suggestion I would appreciate it.


```
sudo fdisk -l
```
RESULTS IN:
```

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41172ba5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4678    37576003+  83  Linux
/dev/sda2            4679        4865     1502077+   5  Extended
/dev/sda5            4679        4865     1502046   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13b73ad8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       12157    97651071    7  HPFS/NTFS
/dev/sdb2           12158       19456    58629217+   f  W95 Ext'd (LBA)
/dev/sdb5           12158       14589    19535008+   b  W95 FAT32
/dev/sdb6           14590       17021    19535008+   7  HPFS/NTFS
/dev/sdb7           17022       19456    19559106    b  W95 FAT32


```




```

sudo blkid /dev/sdb1
sudo blkid /dev/sdb5
```
RESULTS IN:

```

/dev/sdb1: UUID="A61CA49C1CA468CF" LABEL="Downloads" TYPE="ntfs" 
/dev/sdb5: LABEL="MUSIC" UUID="78A4-BC5C" TYPE="vfat" 

```




```

sudo cat /etc/fstab

```
RESULTS IN
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ad97d156-32e2-4520-82a7-ce424aaa25c8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=efe84f21-55f4-4848-9216-73e7e4f1fc3d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# /dev/sdb1
UUID=A61CA49C1CA468CF /media/downloads ntfs defaults,umask=007,gid=46,noatime 0 0
# /dev/sdb5
UUID=78A4-BC5C /media/music vfat defaults,umask=007,gid=46 0 0 

```


I restart and nothing gets automounted. Please help, where am I going wrong?

---

### Post by sisco311 on 2008-08-08
did you create the mount points:
```
sudo mkdir /media/downloads
sudo mkdir /media/music
```

post the output from:
```
sudo mount -a
```and
```
mount
```

---

### Post by spiderbatdad on 2008-08-08
The only thing that jumps out at me is, you have labels for sdb1 and sdb5 Music and Downloads, but fstab has music and downloads...these are different. have you specifically created the mount points?

---

### Post by arbitrage1 on 2008-08-08
> **sisco311 said:**
> did you create the mount points:
```
sudo mkdir /media/downloads
sudo mkdir /media/music
```

Yes I did create the above directories before restarting...


sudo mount -a GIVES NO OUTPUT

```
mount
```
RESULTS IN:
```
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/pavan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=pavan)


```

---

### Post by arbitrage1 on 2008-08-08
> **spiderbatdad said:**
> The only thing that jumps out at me is, you have labels for sdb1 and sdb5 Music and Downloads, but fstab has music and downloads...these are different. have you specifically created the mount points?

Solved. That was it. The labels had capitalized letters and my mkdir statements didnt. Im coming from windows where capitalization doesnt matter. 
Thanks sisco311, spiderbatdad

---

### Post by sisco311 on 2008-08-08
deleted:)

---

