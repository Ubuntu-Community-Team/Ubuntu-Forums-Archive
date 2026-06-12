---
title: "Other partitions fail to mount after re-install"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by rockstar on 2008-07-03
Since I re-installed Ubuntu all of my partitions other than my "/" and "/home" partitions will not mount.  all of the other advice I've found usually involves things mounting with the wrong permissions or mounting incorrectly, but these partitions aren't mounting at all.  Maybe my install messed up these mount points.  I loaded gparted and /dev/sda1 is a ntfs file system with the mount point /windows.  Another partition is /dev/sda6 with no mount point.

Here is information about my system that people requested on other threads

```
paul@paul-laptop:~$ sudo fdisk -l



Disk /dev/sda: 100.0 GB, 100030242816 bytes

255 heads, 63 sectors/track, 12161 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x1b521b52



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1        3648    29302528+   7  HPFS/NTFS

/dev/sda2            3649        5429    14305882+  83  Linux

/dev/sda3            5430       11994    52733362+   5  Extended

/dev/sda4           11995       12161     1341427+  82  Linux swap / Solaris

/dev/sda5            5430        9562    33198291   83  Linux

/dev/sda6            9563       11994    19535008+  83  Linux


paul@paul-laptop:~$ cat /etc/fstab

# /etc/fstab: static file system information.

#

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    defaults        0       0

# /dev/sda2

UUID=73120e58-fa5c-4da8-90d4-ebfac936b92e /               ext3    relatime,errors=remount-ro 0       1

# /dev/sda6

UUID=3b813dbf-af15-4bec-9a20-ecbdbe6a07ad /dev/sda6       ext3    relatime        0       2

# /dev/sda5

UUID=17cb59c8-caaa-486b-bc92-2996edfd7fb6 /home           ext3    relatime        0       2

# /dev/sda1

UUID=5874DA1B74D9FC26 /windows        ntfs    defaults,umask=007,gid=46 0       1

# /dev/sda4

UUID=1451f1db-3bab-4466-a9c0-0598460e79e8 none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


paul@paul-laptop:~$ mount

/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)

proc on /proc type proc (rw,noexec,nosuid,nodev)

/sys on /sys type sysfs (rw,noexec,nosuid,nodev)

varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)

varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)

udev on /dev type tmpfs (rw,mode=0755)

devshm on /dev/shm type tmpfs (rw)

devpts on /dev/pts type devpts (rw,gid=5,mode=620)

lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)

/dev/sda5 on /home type ext3 (rw,relatime)

/dev/sda1 on /windows type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)

securityfs on /sys/kernel/security type securityfs (rw)

gvfs-fuse-daemon on /home/paul/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=paul)

/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=paul)


paul@paul-laptop:~$ sudo blkid

/dev/sda1: UUID="5874DA1B74D9FC26" TYPE="ntfs" 

/dev/sda2: UUID="73120e58-fa5c-4da8-90d4-ebfac936b92e" TYPE="ext3" 

/dev/sda4: TYPE="swap" UUID="1451f1db-3bab-4466-a9c0-0598460e79e8" 

/dev/sda5: UUID="17cb59c8-caaa-486b-bc92-2996edfd7fb6" TYPE="ext3" 

/dev/sda6: UUID="3b813dbf-af15-4bec-9a20-ecbdbe6a07ad" TYPE="ext3" SEC_TYPE="ext2" 

paul@paul-laptop:~$ 


```

---

### Post by logos34 on 2008-07-03
looks like sda6 is the only one not mounting, and here's why:
> 
# /dev/sda6

UUID=3b813dbf-af15-4bec-9a20-ecbdbe6a07ad [COLOR=Red]/dev/[/COLOR]sda6       ext3    relatime        0       2 Change mount point to [B][COLOR=Blue]/media/[/COLOR]sda6.

[/B] Then,[B]

sudo mkdir /media/sda6

sudo mount -a
[/B]

---

### Post by rockstar on 2008-07-03
Thanks.  That worked.  I must have destroyed my Windows Xp partition when I re-installed by mounting it as /windows. Or I accidentally checked the Format box.

Is there something new or different in Hardy that let you install Windows in Hardy or Hardy in Windows? Because that might have confused me when I re-installed.

---

### Post by logos34 on 2008-07-03
according to the output above, sda1 is mounting with the ntfs-3g driver ('fuseblk') at '/windows'.  But if it's empty, then I guess maybe it did get formatted during install.  Nothing in the installation procedure has changed.

---

