---
title: "noobie Fstab automount error"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by tomasinho on 2008-05-22
Hello, I am really new here and hoping someone can save me!
I was trying to get a partition to automount using sudo gedit /etc/fstab. I have also fiddled with the settings through "Storage device manager"

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sda1
UUID=4ccd1ed5-6b6a-4366-814a-e92740877766  /              ext3         relatime,errors=remount-ro  0  1  
# /dev/sda2
UUID=ddab3ed9-1afc-4e25-9350-d4716122789f  none           swap         sw                          0  0  

/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sda3                                  /media/sda3    ntfs         defaults                    0  0  
/dev/sdb4                                  /media/sdb4    vfat         users                       0  0

is what fstab shows, i have two hard drives. it should be like this:
hd1
Ubuntu drive     ext3
swap drive       swap
XP drive         NTFS
hd2
Shared files     VFAT

Any help would be great!

---

### Post by TeoBigusGeekus on 2008-05-22
Please post us the output of 
```
sudo fdisk -l
```
(-L)
and
```
mount
```

---

### Post by spiderbatdad on 2008-05-22
sda is one drive
sdb is the other.
So it looks like your ntfs is set for partition3 of HD1 right  now.

---

### Post by Inxsible on 2008-05-22
You don't list exactly what the problem is. Can you not access your shared drive or the XP partition?


Also, your second drive (sdb) is listed as sdb4. Do you have 3 additional partitions before it which are simply not listed in fstab (Mind you...that is not  a problem is you do actually have 3 additional partitions)

Please post output of sudo fdisk -l as mentioned before and we can help you better

---

### Post by tomasinho on 2008-05-22
The problem is sdb4 will not let me create or edit files. It appears to be read-only. Yes this is a dualboot ubuntu/xp. Thx for your help.


[CENTER][/CENTER]Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6079    48829536   83  Linux
/dev/sda2            6080        6141      498015   82  Linux swap / Solaris
/dev/sda3   *        6142       12220    48829567+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa743beb3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb4           35306       60801   204796620    b  W95 FAT32

---

### Post by tomasinho on 2008-05-22
this is the "mount" output.

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
/dev/sda3 on /media/sda3 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/tom/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tom)
/dev/sdb4 on /media/sdb4 type vfat (rw,noexec,nosuid,nodev)

---

### Post by TeoBigusGeekus on 2008-05-22
```
/dev/sda3 /media/sda3 ntfs defaults 0 0 
/dev/sdb4 /media/sdb4 vfat users 0 0
```

Comment out these lines and add these after them

```
#/dev/sda3 /media/sda3 ntfs defaults 0 0 
#/dev/sdb4 /media/sdb4 vfat users 0 0
/dev/sda3     /media/sda3     ntfs     relatime     0     2
/dev/sda4     /media/sdb4     vfat     relatime     0     2
```
Reboot and post us what happened.

---

### Post by tomasinho on 2008-05-22
This worked to the extent that the NTFS drive automounted, and the Fat-drive was read+write. However it did not automount.

What does relatime do?

Thanks for your help again!

---

### Post by TeoBigusGeekus on 2008-05-23
Type 
```
man fstab
```
and
```
man mount
```
You will get all the info you need.

---

