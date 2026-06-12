---
title: "How to disable auto-mounting of partitions?"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by newbuntuxx on 2008-09-27
Hey...

when I had 7.10, my partitions wouldn't auto-mount up on start-up, unless i double click them (or mount them through terminal), and i will be asked to enter my password before they are mounted. Also, when they were mounted, I only had read permissions, unless i was root. 

After the upgrade to 8.04, my ext3 partition would auto-mount, with full read/write permissions without asking for my password.

I would like to stop it from auto-mounting. I also want the system to ask me for my password when ever I want to mount it. And when it is mounted, only root should be able to write to it or delete files from it.

I looked around the net and didn't get a straight answer, and since this is my *third* ubutnu installation, i want to get it right from the first time.

any help is appreciated. thanks guys

---

### Post by iaculallad on 2008-09-27
Try removing the partition entry from your /etc/fstab file.

```
gksudo gedit /etc/fstab
```

---

### Post by lucasl on 2008-09-27
Instead of removing the entry from fstab entirely, it's probably better to only remove the 'auto' keyword for the partition.

---

### Post by iaculallad on 2008-09-27
> **lucasl said:**
> Instead of removing the entry from fstab entirely, it's probably better to only remove the 'auto' keyword for the partition.

Removing the 'auto' option from the fstab file does not have any connection from being auto-mounting on startup. 
The 'auto' option is used when you want fstab to automatically detect the file system types and not on auto-mounting the partition on startup.

---

### Post by lucasl on 2008-09-27
> **iaculallad said:**
> Removing the 'auto' option from the fstab file does not have any connection from being auto-mounting on startup. 
The 'auto' option is used when you want fstab to automatically detect the file system types and not on auto-mounting the partition on startup.

Sorry, I should have been more specific. I meant auto in the fourth column.
> **auto and noauto** With the auto option, the device will be mounted automatically (at bootup). auto is the default option. If you don't want the device to be mounted automatically, use the noauto option in /etc/fstab. With noauto, the device can be mounted only explicitly.

You want the fstab entry to look like this:
```
<device path here> <mount point here> auto noauto,nouser,rw,exec,async <two numbers here; leave them>
```
noauto means no auto mount and nouser means only root can mount. You can change that to user if you want.

Example:
```
/dev/hda3 /media/MyDrive auto noauto,nouser,rw,exec,async 1 3
```

---

### Post by newbuntuxx on 2008-09-27
hey

here is the output of: fdisk -l

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3c6c3c6c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3047    24474996   83  Linux
/dev/sda2            3048       10949    63472815   83  Linux
/dev/sda3           10950       11435     3903795   82  Linux swap / Solaris
/dev/sda4           11436       30401   152344395   83  Linux

```

Here is the output of my /etc/fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e0bbb6aa-daee-4de3-b4e0-c0fb4eb6168c /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=41bd4046-5e7f-4ad0-b706-d239e051f3eb /home           ext3    defaults        0       2
# /dev/sda3
UUID=fadd9a20-42bb-4e63-b02c-5c6784ed2f29 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

strangely enough, as you can see, my /dev/sda4 partition is not listed in the fstab file. So, I checked the output of mount, which was:

```
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
/dev/sda2 on /home type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
localhost:/var/lib/cfs/.cfsfs on /var/cfs type nfs (rw,port=3049,intr,nfsvers=2,udp,addr=127.0.0.1)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sda4 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)

```

So, sda4 was mounted although it was not listed in fstab. Nonetheless, I went and added the line that you suggested, with some modifications of course. So, the new output of fstab is:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e0bbb6aa-daee-4de3-b4e0-c0fb4eb6168c /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=41bd4046-5e7f-4ad0-b706-d239e051f3eb /home           ext3    defaults        0       2
# /dev/sda3
UUID=fadd9a20-42bb-4e63-b02c-5c6784ed2f29 none            swap    sw              0       0
# /dev/sda4
/dev/sda4 /media/disk auto noauto,nouser,rw,exec,async 1 3
# cd rom
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

Now, I have to mount the drive from the terminal. I can not simply double click it and enter my root password, which is a bit annoying. 

Is it possible to mount/umount it by using the mouse and entering a password into a box?

thanks

---

### Post by newbuntuxx on 2008-09-28
hey guys...any suggestions?

I wrote a small script to mount/umount the partition. It asks for the password. Thats what i am using in the meantime. However, if there is a way to do it without having an extra launcher on the desktop, which i dont need, then please share it with me.

thanks...

here it is:

```

#!/bin/bash

# mount partition with root privileges. if partition is already mounted, then umount it.

if df | grep sda4; then
  echo "Unmounting partition..."
  sudo umount /dev/sda4
else
  echo "Mounting partition..."
  sudo mount /dev/sda4
fi

exit

```

---

