---
title: "Need help manually mounting thumbdrive"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by hovzio on 2008-05-03
hi, got some questions concerning mounting in general. Ubuntu automatically mounts thumbdrives as soon as stick them in, but I would learn how to properly use the mount command. (how to mount a drive to my home folder and down the road from a lan for instance) The drive is unmounted and I use fdisk -l to see what the drive is called and I get this: 

Disk /dev/sdb: 4126 MB, 4126670848 bytes
16 heads, 32 sectors/track, 15742 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

Now I would like to mount this drive:

holio@holio-laptop:~$ sudo mount /dev/sdb
mount: can't find /dev/sdb1 in /etc/fstab or /etc/mtab
holio@holio-laptop:~$ sudo mount /media/sdb
mount: can't find /media/sdb1 in /etc/fstab or /etc/mtab

With or without sudo it doesn't work and Im not even trying to mount it to my home dir. yet. I Can't imagine that I have to manually add portable drives to mtab or fstab. Am I missing some options in the syntax? Ubuntu mounts the drive just fine so I thought I would unmount it(right click, unmount) and then try mounting from cml. I looked at the man pages but I have to admit I am new to linux and have a hard time understanding them.(they are great for reference if I am already familiar with a command) I tried the "--help" but I guess I'm just not getting this one. How can I find out the name of a drive? How can I manually mount a drive? And how can I mount it to a certain location? I would appreciate any input or a link that can could help me.

---

### Post by wormser on 2008-05-03
You need to specify the device then the mount point.

```
 sudo mount /dev/sdb1 /media/sdb1
```That command assumes the device name is right and you have a folder called /media/sdb1.

---

### Post by 3rdalbum on 2008-05-03
First, you create a mount point:

```
sudo mkdir /media/thumbdrive
```

This will be where the contents of the drive will be available.

Then you perform the mounting:

```
sudo mount /dev/sdb /media/thumbdrive
```

The permissions of users to access the device depends entirely on the permissions of the mount point itself. So if you want your own user account to be able to read and write to the thumbdrive, you would use chmod to change the permissions of /media/thumbdrive so you can write it.

Unmounting is easier:

```
sudo umount /media/thumbdrive
```

---

### Post by hovzio on 2008-05-03
Thanks a bunch, I get the jist of it. Mount tells me i need to specify the filesystem type. How is this done? (its fat 32)

---

### Post by MONODA on 2008-05-03
[http://www.tuxfiles.org/linuxhelp/mounting.html](http://www.tuxfiles.org/linuxhelp/mounting.html)
i suggest using google next time since you know exactly what you want and you can get proper, acurate results faster.
PS. tuxfiles.org is great, bookmark it.

---

### Post by wormser on 2008-05-03
> **hovzio said:**
> Thanks a bunch, I get the jist of it. Mount tells me i need to specify the filesystem type. How is this done? (its fat 32)

Use the type switch (-t).

```
mount -t vfat /dev/sdb1 /media/sdb1
```

---

### Post by hovzio on 2008-05-03
hi, this is what I get;

$ sudo mount -t vfat /dev/sdb /home/holo/thumb/
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

holo@holo-laptop:~$ dmesg | tail
[ 4588.888000] sd 2:0:0:0: [sdb] Write Protect is off
[ 4588.888000] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 4588.888000] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 4588.888000]  sdb: sdb1
[ 4588.888000] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[ 4588.888000] sd 2:0:0:0: Attached scsi generic sg2 type 0
[ 8759.832000] FAT: invalid media value (0x00)
[ 8759.832000] VFS: Can't find a valid FAT filesystem on dev sdb.
[ 8881.336000] FAT: invalid media value (0x00)
[ 8881.336000] VFS: Can't find a valid FAT filesystem on dev sdb.

When I fdisk -l it tells me the filesystem is W95 FAT32. 

I tried "fat32, FAT32, W95 FAT32" but none of them worked. Thanks for the help I really appreciate it.

---

### Post by cwgatling on 2008-05-03
Looks right, except for maybe mount -t vfat /dev/sdb1 rather than /dev/sdb.

---

### Post by hovzio on 2008-05-03
Thanks for the help! It worked :)

---

### Post by cwgatling on 2008-05-03
Good news :)

---

