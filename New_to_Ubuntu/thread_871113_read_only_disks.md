---
title: "read only disks"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by stonecoldjha on 2008-07-26
all my drives are read only(ro).i am the administrator and would like to have all such previleages that an administrator has like modifying the contents of a partition and that of its folders.  when itry doing so,i get the message that the disk is ro.how do i fix this?

---

### Post by ibuclaw on 2008-07-26
Which drives would that be?
Can you connect and mount those devices and post the output of these commands in the terminal:
```
cat /etc/fstab
```
```
cat /etc/mtab
```

Regards
Iain

---

### Post by stonecoldjha on 2008-07-26
hello,i did exactly what u tol me to,the commands and their output is as follows:

sonu@sonu-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=4c13830d-1a25-4804-9d3e-8d531d018d9e /               ext2    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=a82d33fd-e439-4f6e-b903-499f49443f4e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#Added by diskmounter utility
/dev/sda1 /media/sda1 ntfs ro,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sda3 /media/sda3 ntfs ro,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sda5 /media/sda5 ntfs ro,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sda6 /media/sda6 ntfs ro,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sda7 /media/sda7 ntfs ro,user,fmask=0111,dmask=0000 0 0
sonu@sonu-desktop:~$ cat /etc/mtab
/dev/sda9 / ext2 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-19-generic/volatile tmpfs rw 0 0
/dev/sda1 /media/sda1 fuseblk ro,noexec,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096 0 0
/dev/sda3 /media/sda3 fuseblk ro,noexec,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096 0 0
/dev/sda5 /media/sda5 fuseblk ro,noexec,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096 0 0
/dev/sda6 /media/sda6 fuseblk ro,noexec,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096 0 0
/dev/sda7 /media/sda7 fuseblk ro,noexec,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/sonu/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=sonu 0 0
sonu@sonu-desktop:~$

---

### Post by arkara on 2008-07-26
ok
this is the fstab file.

```
sonu@sonu-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda9
UUID=4c13830d-1a25-4804-9d3e-8d531d018d9e / ext2 relatime,errors=remount-ro 0 1
# /dev/sda8
UUID=a82d33fd-e439-4f6e-b903-499f49443f4e none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
#Added by diskmounter utility
/dev/sda1 /media/sda1 ntfs **ro**,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sda3 /media/sda3 ntfs **ro**,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sda5 /media/sda5 ntfs **ro**,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sda6 /media/sda6 ntfs **ro**,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sda7 /media/sda7 ntfs **ro**,user,fmask=0111,dmask=0000 0 0
```

the bold ro's mean read only.
you should change them to rw which means read-write.

also, i am not sure if you must change the ntfs word with the word ntfs-3g

---

### Post by stonecoldjha on 2008-07-26
but i dont have the previleage to modify the fstab file....how can i change ro to rw?

---

### Post by Troll_the_Great on 2008-07-26
> **stonecoldjha said:**
> but i dont have the previleage to modify the fstab file....how can i change ro to rw?

I think you can modify it with 
```
sudo gedit /etc/fstab
```
But I could be wrong...Try it and post the result.
Cheers!

---

### Post by ibuclaw on 2008-07-26
```
sudo gedit /etc/fstab
```

Regards
Iain

---

### Post by stonecoldjha on 2008-07-26
it really worked........thanks a lot,by the way i wanted to know what would be the case if i had replaced 'ro' with 'defaults',instead of 'rw'.

---

### Post by arkara on 2008-07-26
> **stonecoldjha said:**
> it really worked........thanks a lot,by the way i wanted to know what would be the case if i had replaced 'ro' with 'defaults',instead of 'rw'.

defaults are equal to the following options 
```
rw,suid,dev,exec,auto,nouser,async.
```
but since the file plays nicely, do not edit it anymore.
:D

---

### Post by Troll_the_Great on 2008-07-26
Glad we could help.Please mark your thread as solved if you don't need further assistance.
Cheers!

---

