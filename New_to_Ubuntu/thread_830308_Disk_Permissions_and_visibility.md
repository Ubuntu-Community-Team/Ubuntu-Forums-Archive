---
title: "Disk Permissions and visibility"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by njigsaw on 2008-06-15
I have started form scratch and reformatted my disks as ext3.
My OS is on one small 40 GB disk and I have a larger 120GB disk set aside for all my personal storage.
At present I cannot write at all to my 120GB disk due to the message "unable to determine permissions".

Could some one please assist in setting up this disk as I do not fully understand the command code required.

I also find that the disk dev/sdb though shown in the places section and through fdisk is not shown in fstab or mount!?!?!?

Thanks in anticipation.

please see attached following fdisk, fstab and mount files as well as attached screen shot:

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00b900b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4905    39399381   83  Linux
/dev/sda2            4906        4998      747022+   5  Extended
/dev/sda5            4906        4998      746991   82  Linux swap / Solaris

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcfca8540

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14946   120053713+  83  Linux


neal@neal-desktop:~$ sudo mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-18-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/neal/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=neal)







# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4689e496-32b8-447d-855d-17560d275c8d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=e982ab18-18fd-4996-bafc-2b85db96d17d none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by drs305 on 2008-06-15
Make a mount point for sdb1 (Name it what you wish) Bold requires user input:
```
sudo mkdir /media/**sdb1**
sudo chown -R **username:username** /media/**sdb1**
```

Add this line to fstab (substitute UUID for /dev/sdb1 if desired):
```
# /dev/sdb1
/dev/sdb1 /media/**sdb1**   ext3    defaults  0  2

```

Refresh fstab (you will get 'device busy' messages):
```

sudo umount -a
sudo mount -a

```

If you want to substitute the UUID you can get it with the following command:
```

sudo blkid

```

---

### Post by njigsaw on 2008-06-16
Right then got a little futher, again.

Having followed the previous instructions and played for a bit I decided to go back to bascis and load Hardy again.

I thought that some of my original problems were through not understanding or using the partition control correctly when installing Hardy.

I now have the second hard disk actually shown as mounted in to "home". 

However I can still not see it in "places/ home" or find out how to get access to it.
I can see via disk usage monitor that all the memory I'm expecting (120 + 40 GB) is there, somewhere.

Further advice required please to get this damned drive up so I can see it then hopefully I can see whether I then have RW access/ permissions to it.

Thanks in advance.



See attached files and shots:


neal@neal-desktop:~$ sudo fdisk -l

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00b900b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1        4998    40146403+   5  Extended
/dev/sda5            4906        4998      746991   82  Linux swap / Solaris
/dev/sda6               1        4905    39399318   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcfca8540

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14946   120053713+  83  Linux


neal@neal-desktop:~$ sudo mount
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
/dev/sdb1 on /home type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/neal/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=neal)


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=fd44889a-671d-46a3-882a-62d47291a9ed /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb1
UUID=a6e8cd77-ab33-4d3f-a441-c38f4f5ab53f /home           ext3    defaults	        0       2
# /dev/sda5
UUID=e982ab18-18fd-4996-bafc-2b85db96d17d none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by njigsaw on 2008-06-16
Now then I might have just solved my own problem.

Not realising quite to look and relying too much on windows layout. I have now found my free space and how to write to it.

Thanks for previous help.

Cause of this original problem appears to be me not using the partition control correctly when installing Hardy and not understanding how the mount action works or where to mount the disk.

Maybe some clearer instructions required on this from transferring windows users????

---

