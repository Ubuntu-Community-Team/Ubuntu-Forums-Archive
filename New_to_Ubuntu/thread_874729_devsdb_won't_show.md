---
title: "/dev/sdb won't show"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by twedellj on 2008-07-30
I used GParted and turned sdb into a ext3 and formated it even and it still won't show up in my computer. how can i get this to show?



Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x45e645e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2327    18691596   83  Linux
/dev/sda2            2328        2434      859477+   5  Extended
/dev/sda5            2328        2434      859446   82  Linux swap / Solaris

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf83ef844

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2434    19551073+  83  Linux

---

### Post by brujoand on 2008-07-30
you can try to mount it by:

sudo mkdir /media/disk
sudo mount /dev/sdb1 /media/disk

If this makes the drive pop up, you can edit the fstab to have it mount everytime you reboot.

---

### Post by iaculallad on 2008-07-30
Output whatever displays when you issue the following commands below:

```
sudo blkid
```
and
```
cat /etc/fstab
```
and
```
sudo fdisk -l
```

---

### Post by twedellj on 2008-07-30
> **GrimmVarg said:**
> you can try to mount it by:

sudo mkdir /media/disk
sudo mount /dev/sdb1 /media/disk

If this makes the drive pop up, you can edit the fstab to have it mount everytime you reboot.

This made the drive accessible. i got fstab up. what do i type in this txt file to make it boot everytime?

this is what stab says currently 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=bc3b4c22-de03-42c1-8a6a-a8b1f8c241ad /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=5be343c9-8fad-45d7-8945-327de00e01cb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by twedellj on 2008-07-30
> **iaculallad said:**
> Output whatever displays when you issue the following commands below:

```
sudo blkid
```
and
```
cat /etc/fstab
```
and
```
sudo fdisk -l
```

twedell@twedell-desktop:~$ sudo blkid
/dev/sda1: UUID="bc3b4c22-de03-42c1-8a6a-a8b1f8c241ad" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="5be343c9-8fad-45d7-8945-327de00e01cb" 
/dev/sdb1: UUID="7139040e-4f30-43d4-a5b2-d66b6a296953" TYPE="ext3" 

twedell@twedell-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=bc3b4c22-de03-42c1-8a6a-a8b1f8c241ad /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=5be343c9-8fad-45d7-8945-327de00e01cb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0






Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x45e645e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2327    18691596   83  Linux
/dev/sda2            2328        2434      859477+   5  Extended
/dev/sda5            2328        2434      859446   82  Linux swap / Solaris

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf83ef844

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2434    19551073+  83  Linux

---

### Post by twedellj on 2008-07-30
would i just add /dev/sdb1 auto?

---

### Post by iaculallad on 2008-07-30
> **twedellj said:**
> would i just add /dev/sdb1 auto?

Create you mount point:

```
sudo mkdir /media/mydrive
```

Edit your fstab file:

```
gksudo gedit /etc/fstab
```

and add the line of text below on the last part of the file (Copy and Paste it):
```

/dev/sdb1 /media/mydrive           ext3    defaults        0       2
```

Save and Close gedit. Open your terminal and issue the command below:

```
sudo mount -a
```

---

### Post by twedellj on 2008-07-30
thx a ton man. problem solved

---

