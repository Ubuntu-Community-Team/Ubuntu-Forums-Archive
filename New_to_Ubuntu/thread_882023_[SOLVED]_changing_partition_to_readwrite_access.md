---
title: "[SOLVED] changing partition to read/write access"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by einfinger on 2008-08-06
i have a partition that is set to read only and therefore deluge wont download files to this partition, how do i set it to be read and write ?

---

### Post by Blutack on 2008-08-06
Could you please past the contents of the file /etc/fstab?
Also, what is the exact error?  Are you sure it is read only, or do you not have to correct permissions?  To check that, type
gksudo nautilus
into a terminal, navigate to your partition and attempt to create a new folder.

---

### Post by ConMan318 on 2008-08-06
You could try 
```

sudo chown **yourUserName partitionLocation**

```

If that doesn't work do
```

sudo chmod 750 **partitionLocation**

```

If you do an 'ls -l' there, and it says it's owned by root, the first code should work.

If it says you're the owner, try the chmod.  It might be the permissions, if the 'ls -l' shows it with something like
```

dr-xr-xr-x

```

it means you don't have write permissions, so do the chmod.

---

### Post by einfinger on 2008-08-06
whats fstab ?

---

### Post by einfinger on 2008-08-06
i tried doing chmod and all and all i get is


chmod: changing permissions of `/media/disk-1': Read-only file system

---

### Post by Blutack on 2008-08-06
Ahh, sorry.  If you open your home folder (the one with Music/Documents in) and keep pressing the up button until you can't any more.
From there, look for the folder called etc.
Inside is a file called fstab.  Open it and copy and paste the contents.  Although this is more likely to be a permissions thing, so you might like to try the 
sudo nautilus
thing, and if it works use ConMans fix.

---

### Post by einfinger on 2008-08-06
fstab says: 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=7a6e90a4-3df1-4a3e-a1cf-490cd4906cf9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=2b088777-5fdc-4fd6-9ef3-302102963420 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by sisco311 on 2008-08-06
post:
```
sudo fdisk -l
``````
sudo blkid
```and
```
mount
```

---

### Post by einfinger on 2008-08-06
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x131ccfcf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4891    39286926   83  Linux
/dev/sda2            4892       12911    64420650    b  W95 FAT32
/dev/sda3           12912       14219    10506240   83  Linux
/dev/sda4           14220       14593     3004155    5  Extended
/dev/sda5           14220       14593     3004123+  82  Linux swap / Solaris



/dev/sda1: UUID="7a6e90a4-3df1-4a3e-a1cf-490cd4906cf9" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="2b088777-5fdc-4fd6-9ef3-302102963420" 
/dev/sda2: UUID="487E-2450" TYPE="vfat" 
/dev/sda3: UUID="cac17e25-6e7f-476a-aad2-e61655cf1b9d" TYPE="reiserfs" 




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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/linni/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=linni)
/dev/sda2 on /media/disk-1 type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sda3 on /media/disk type reiserfs (rw,nosuid,nodev,uhelper=hal)
/dev/sdb1 on /media/NIKON D40 type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
linni@linni-laptop:~$

---

### Post by sisco311 on 2008-08-06
edit the fstab:
```
gksu gedit /etc/fstab
```
and add this line:
> UUID=487E-2450 /media/***INSERT_NAME_HERE ***vfat defaults,umask=0007,gid=46 0 0

create the mount point:
```
sudo mkdir /media/***INSERT_NAME_HERE***
```

mount the partition:
```
sudo mount -a
```

---

### Post by einfinger on 2008-08-06
that did the trick but deluge still says the destination still is read only..?

---

### Post by sisco311 on 2008-08-06
> **einfinger said:**
> that did the trick but deluge still says the destination still is read only..?
did you try to restart deluge and/or the computer?

---

### Post by einfinger on 2008-08-06
it works now, thank you guys :)

---

### Post by sisco311 on 2008-08-06
> **einfinger said:**
> it works now, thank you guys :)
then please mark your thread as solved
(Thread tools -> Mark this thread as solved)

---

