---
title: "[SOLVED] Only able to write to external HDD using sudo"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by dwally89 on 2008-05-14
Hi,

I have an external HDD formatted ext3.
When I try to write a file to it (e.g. copy and paste something to it in nautilus), I am unable to do it.
However when I run nautilus as root I am able to do it.

How can I make it that I can write to the HDD using my normal user?

Thanks

---

### Post by sisco311 on 2008-05-14
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Change the owner and group of the disk:
```
sudo chown -R **your-username**\:** /media/mount-point**
```

---

### Post by dwally89 on 2008-05-14
Hi,

I typed in sudo chown -R user\: /media/disk
user being my username, and /media/disk being the mount point of my external HDD, but I still can't write to it without opening nautilus in sudo.

Is there something else I need to do?

Thanks

---

### Post by sisco311 on 2008-05-14
Try:
```
sudo chmod -R 0775 /media/disk
```

This command will set read/write/execute permission for the owner and group and read/execute permission for others.

---

### Post by TeoBigusGeekus on 2008-05-14
> **sisco311 said:**
> Try:
```
sudo chmod -R 0775 /media/disk
```

Shouldn't that be
```
sudo chmod -R 777 /media/disk
```

---

### Post by dwally89 on 2008-05-14
OK I've just tried those two commands, and it still doesn't work.

Any other ideas?

---

### Post by TeoBigusGeekus on 2008-05-14
Do the chown and chmod command give you any messages?

---

### Post by dwally89 on 2008-05-14
Nope, it pauses for about 10 seconds, and then returns back to the command line.

---

### Post by alexandremrj on 2008-05-14
Then open nautilus in sudo, right click on the disk and go to properties.
Then in properties go to permissions and see what is there.

You need that group = your username must have permission in the folder and files

---

### Post by dwally89 on 2008-05-14
It says
> The permissions of "disk" could not be determined.

---

### Post by TeoBigusGeekus on 2008-05-14
Perhaps if you tried to add an entry for it in your fstab file...
Post us its contents
```
gksudo gedit /etc/fstab
```

Also, post us your drive's mount point (/media/disk, /media/storage ?)

Finally, post us the output of 
```
sudo fdisk -l
```
(-L)

---

### Post by sisco311 on 2008-05-14
Please post the output from:
```
mount
```

---

### Post by alexandremrj on 2008-05-14
Check this thread:

[https://answers.launchpad.net/ubuntu/+question/32917](https://answers.launchpad.net/ubuntu/+question/32917)

It has some of your questions, perhaps it can help

---

### Post by dwally89 on 2008-05-14
fstab:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=82fa0ba4-1f8b-4a7a-901e-9333b102da00 /               ext3    errors=remount-ro 0       1
# /dev/sda7
UUID=329325d9-0726-434c-8601-b5f96e38ff3d /home           ext3    defaults        0       2
# /dev/mmcblk0p1
UUID=3931-3237  /media/mmcblk0p1 vfat    utf8,umask=007,gid=46 0       1
# /dev/sda1
UUID=07D7-041A  /media/sda1     vfat    utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=0AECF7027E340363 /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=bc4b12de-2d13-4283-8232-269aecbd0bfc /media/sda3     ext3    defaults        0       2
# /dev/sda5
UUID=C8E9-A608  /media/sda5     vfat    utf8,umask=007,gid=46 0       1
# /dev/sda8
UUID=29e0b8e4-2679-476f-97e8-2c2ca980fd32 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

sudo fdisk -l:
> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          11       88326   de  Dell Utility
/dev/sda2            1498        7902    51448162+   7  HPFS/NTFS
/dev/sda3              12        1497    11936295   83  Linux
/dev/sda4            7903        9730    14676723+   f  W95 Ext'd (LBA)
/dev/sda5            9469        9730     2096128   dd  Unknown
/dev/sda6            7903        9040     9140890+  83  Linux
/dev/sda7   *        9041        9442     3229033+  83  Linux
/dev/sda8            9443        9468      208813+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/mmcblk0: 2032 MB, 2032664576 bytes
64 heads, 63 sectors/track, 984 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1         984     1983619+   6  FAT16

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcd2a4986

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       48641   390708801   83  Linux


---

### Post by TeoBigusGeekus on 2008-05-14
Which one is your drive and which is it's mounting point?

---

### Post by dwally89 on 2008-05-14
mount:
> /dev/sda6 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
/dev/sda7 on /home type ext3 (rw)
/dev/mmcblk0p1 on /media/mmcblk0p1 type vfat (rw,utf8,umask=007,gid=46)
/dev/sda1 on /media/sda1 type vfat (rw,utf8,umask=007,gid=46)
/dev/sda2 on /media/sda2 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/sda5 on /media/sda5 type vfat (rw,utf8,umask=007,gid=46)
none on /proc/bus/usb type usbfs (rw,devgid=46,devmode=664)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/user/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=user)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=user)
gvfs-fuse-daemon on /root/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev)
/dev/sda3 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)


---

### Post by dwally89 on 2008-05-14
My drive is /dev/sdb

---

### Post by TeoBigusGeekus on 2008-05-14
Add this line at the end of your fstab file:
```
dev/sdb1     /media/disk     ext3     relatime     0     2
```

reboot and post us the outcome.

---

### Post by dwally89 on 2008-05-14
> Check this thread:

[https://answers.launchpad.net/ubuntu/+question/32917](https://answers.launchpad.net/ubuntu/+question/32917)

It has some of your questions, perhaps it can help 

In that link it refers to the group "plugdev".

This group doesn't exist in my list. Should I just create it?

Thanks

---

### Post by sisco311 on 2008-05-14
post the output of:
```
ls -al /media
```

---

### Post by dwally89 on 2008-05-14
> Add this line at the end of your fstab file:
Code:

dev/sdb1     /media/disk     ext3     relatime     0     2

reboot and post us the outcome.

I did that, rebooted, and it works :-)

Thanks

---

