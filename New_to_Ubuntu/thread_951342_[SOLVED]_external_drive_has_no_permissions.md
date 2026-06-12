---
title: "[SOLVED] external drive has no permissions"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-10-18
I have an external USB 80 gig drive. At first it wouldn't mount. Then I d/l'd GParted and formatted the disk ext3.

This is the relevant output of 

ls -l /media

drwxrwxr-x 3 mark mark  4096 2008-10-17 21:35 usb


I tried to change the permissions:

mark@Lexington-19:~$ sudo chown -R mark:mark /media/usb

but failed.

The external drive is jumpererd as** CS** Cable Select.

The disk was probably originally formatted to NTFS

the relevant output of lsusb is:

Bus 004 Device 004: ID 04b4:6830 Cypress Semiconductor Corp. USB-2.0 IDE Adapter

I tried some Absolute Beginner searches, but came up w/o a solution. I sure wish Plug 'n Play didn't mean Plug 'n Pray.

---

### Post by jigsaws on 2008-10-18
Have you formated it or only set the filesystem type? It looks like ntfs.

Check the device and filesystem type of this disk by
mount -l | grep usb

Then backup your data, umount /media/usb and make ext3 filesystem by:
/sbin/mkfs.ext3 /dev/....

/dev/.... you found by mount -l

---

### Post by Mark_in_Hollywood on 2008-10-18
> **jigsaws said:**
> Have you formated it or only set the filesystem type? It looks like ntfs.

Check the device and filesystem type of this disk by
mount -l | grep usb

Then backup your data, umount /media/usb and make ext3 filesystem by:
/sbin/mkfs.ext3 /dev/....

/dev/.... you found by mount -l

The output of 

mount -l | grep usb

is:
mark@Lexington-19:~$

that is, nothing. The drive is mounted. It is an EXTERNAL drive connected via USB 2.0. 

I will use it for backup, once it's working. There is nothing on it now. It's icon on the desktop calls itself: "80.0 GB Media". 

Anything else?

---

### Post by drowner on 2008-10-18
do
```

fdisk -l
```

if that comes up with nothing (which it might if the permissions are funny) then try 

```
sudo fdisk -l
```

---

### Post by Mark_in_Hollywood on 2008-10-18
> **drowner said:**
> do
```
fdisk -l
```
if that comes up with nothing (which it might if the permissions are funny) then try 
```
sudo fdisk -l
```

In my first post I put:

drwxrwxr-x 3 mark mark 4096 2008-10-17 21:35 usb

and you ask me to fdisk -l

how will fdisk know which disk to operate on? More, as I posted the "permissions", in the post, can you explain whether you think they are "funny" or not?

---

### Post by jigsaws on 2008-10-19
First, show us "mount" output to determine device (disk) path (/dev/sdb? /dev/sdc?)

---

### Post by Mark_in_Hollywood on 2008-10-19
I have no idea as to how to show the "mount". Thanks.

---

### Post by jigsaws on 2008-10-21
Type "mount" and put here the output.

---

### Post by Mark_in_Hollywood on 2008-10-21
mark@Lexington-19:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-21-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mark/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mark)
/dev/sdb1 on /media/UDISK 28X type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sdc1 on /media/PRESTON type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sdd1 on /media/disk type ext2 (rw,nosuid,nodev,uhelper=hal)

---

### Post by jigsaws on 2008-10-23
Ok:

/dev/sdb1 on /media/UDISK 28X type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1 000,utf8,umask=077,flush)
/dev/sdc1 on /media/PRESTON type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1 000,utf8,umask=077,flush)

Is UDISK or PRESTON is your USB drive with permission problem? Both are FAT32.

---

### Post by Mark_in_Hollywood on 2008-10-29
The fault lay with the electronics somewhat. After getting the fstab's UUID set the device "hung" above ground. Once I un-powered and removed the usb cable and reset, things went fine.

Thanks one and all.

---

