---
title: "[SOLVED] mounting 2 HDs"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by AnLGP on 2008-07-08
I should have posted this in my other thread.  I want to be able to back up files to a second HD.  I have it installed and formatted as /ext3 .  I can't seem to mount it in gparted.  Can I mount two?  Here's the 

**fdisk -l**


Disk /dev/hdb: 61 GB, 61492193280 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/hdb1               1        7476    60050938   83  Linux

Disk /dev/sda: 250 GB, 250056737280 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1       30071   241545276   83  Linux
/dev/sda2           30072       30401     2642692    5  Extended
/dev/sda5           30072       30401     2642692   82  Linux swap
-----------------------------------------

**/etc/fstab**

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

**new HD screenshot**

[http://i65.photobucket.com/albums/h235/themangoduck/2008-07-08-031510_1280x1024_scrot.png](http://i65.photobucket.com/albums/h235/themangoduck/2008-07-08-031510_1280x1024_scrot.png)

**old HD screenshot**

[http://i65.photobucket.com/albums/h235/themangoduck/2008-07-08-031658_1280x1024_scrot.png](http://i65.photobucket.com/albums/h235/themangoduck/2008-07-08-031658_1280x1024_scrot.png)

Thank you.

---

### Post by iaculallad on 2008-07-08
If your second drive is /dev/hdb:

Create the mount point for the device:

```
sudo mkdir /media/DataBackup
```

Open /etc/fstab for editing:

```
gksudo gedit /etc/fstab
```

And, insert the line of text below:

> /dev/hdb /media/DataBackup ext3 defaults 0 2

Close and Save. Open your terminal and issue the command below:

```
sudo mount -a
```

---

### Post by AnLGP on 2008-07-08
[mntent]: warning: no final newline at the end of /etc/fstab
mount: wrong fs type, bad option, bad superblock on /dev/hdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb /media/DataBackup ext3 defaults 0 2

---

### Post by iaculallad on 2008-07-08
Could you again re-post whatever displays when you issue:

```
sudo fdisk -l
```

and 

```
sudo blkid
```

---

### Post by AnLGP on 2008-07-08
Disk /dev/hdb: 61 GB, 61492193280 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/hdb1               1        7476    60050938   83  Linux

Disk /dev/sda: 250 GB, 250056737280 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1       30071   241545276   83  Linux
/dev/sda2           30072       30401     2642692    5  Extended
/dev/sda5           30072       30401     2642692   82  Linux swap


/dev/hdb1: UUID="0b39f81b-72a9-4a1a-b5f6-2c904af2ab04" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda1: UUID="3421725e-7aa0-41be-8090-ccc2cb50805e" TYPE="ext3" 
/dev/sda5: TYPE="swap"

---

### Post by iaculallad on 2008-07-08
```
gksudo gedit /etc/fstab
```

This was your editted fstab file:

> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/sda1 / ext3 errors=remount-ro 0 1
/dev/sda5 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0
**/dev/hdb /media/DataBackup ext3 defaults 0 2**


Replace the bold line of text with:

> /dev/hdb1 /media/DataBackup ext3 defaults 0 2

Save file and open your terminal again:

```
sudo mount -a
```

---

### Post by AnLGP on 2008-07-08
[mntent]: warning: no final newline at the end of /etc/fstab

It got smaller :D

I fixed it.  At the end of it (the 2 in the last line) put the cursor there, hit enter & then save.

---

### Post by iaculallad on 2008-07-08
> **AnLGP said:**
> [mntent]: warning: no final newline at the end of /etc/fstab

It got smaller :D

I fixed it.  At the end of it (the 2 in the last line) put the cursor there, hit enter & then save.

Good, Im glad you had figured it out yourself. Good luck.

---

### Post by AnLGP on 2008-07-08
Thanks :)

---

