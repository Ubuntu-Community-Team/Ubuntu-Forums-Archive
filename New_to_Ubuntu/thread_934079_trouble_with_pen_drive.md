---
title: "trouble with pen drive"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by nnjond on 2008-09-30
There's a padlock on my .trash folder and Ubuntu now claims my pen drive is read only?

nick@nick-desktop:~$  sudo blkid
[sudo] password for nick: 
/dev/sda1: UUID="d2cde2b7-321f-4db5-888a-eaf52aa5f66d" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="892c3006-824a-9fa7-1a23-63503cd3b37d" 
/dev/sdb1: UUID="4842-C799" TYPE="vfat" 
/dev/sda3: UUID="addc5919-5aff-48af-b534-0c4e43f914c7" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: SEC_TYPE="msdos" UUID="48B1-AE88" TYPE="vfat" 
nick@nick-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d2cde2b7-321f-4db5-888a-eaf52aa5f66d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=892c3006-824a-9fa7-1a23-63503cd3b37d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
nick@nick-desktop:~$ mount
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
gvfs-fuse-daemon on /home/nick/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=nick)
/dev/sdc1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sdb1 on /media/disk-1 type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
nick@nick-desktop:~$

---

### Post by kpkeerthi on 2008-09-30
Copy your data off the drive if required and reformat it using Ubuntu Live CD.

1. Boot with ubuntu Live CD
2. Insert your pen drive
3. Press ALT+F2 and type **gparted**
4. Select your pen drive and unmount it.
5. Delete the partition and create a new FAT32 partition.

See gparted [documentation]("http://gparted.sourceforge.net/documentation.php") for more info.

---

### Post by gandaran on 2008-09-30
open nautilus as root, code: **sudo nautilus** navigate to the pen drive, now you can have access to the files or even change the permissions

---

### Post by timcredible on 2008-09-30
if it's fat16 or fat32 formatted, try running dosfsck on it, linux will mount a fat16 or fat32 drive as read-only if it's got filesystem errors.

---

