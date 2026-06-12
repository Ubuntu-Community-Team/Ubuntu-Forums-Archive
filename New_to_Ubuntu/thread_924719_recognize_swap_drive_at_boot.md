---
title: "recognize swap drive at boot?"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by klemperal on 2008-09-19
For whatever reason my swap isn't recognized at boot.  I think it had something to do with resizing it.  I know how to turn it on via sudo swapon, but i wish I knew how I could get it back to simply being recognized at boot.  Any ideas?

---

### Post by iaculallad on 2008-09-19
> **klemperal said:**
> For whatever reason my swap isn't recognized at boot.  I think it had something to do with resizing it.  I know how to turn it on via sudo swapon, but i wish I knew how I could get it back to simply being recognized at boot.  Any ideas?

Post the output of the following terminal commands:

```
sudo fdisk -l
cat /etc/fstab
sudo blkid
free -m
```

---

### Post by kansasnoob on 2008-09-19
I had the same problem:

[http://ubuntuforums.org/showthread.php?t=879192](http://ubuntuforums.org/showthread.php?t=879192)

You may also want to see this:

[http://ubuntuforums.org/showthread.php?t=857565](http://ubuntuforums.org/showthread.php?t=857565)

---

### Post by klemperal on 2008-09-19
sudo fdisk -l


Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x19bf19be

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8434    67746073+   7  HPFS/NTFS
/dev/sda2            8435       48641   322962727+   5  Extended
/dev/sda5            8435       47988   317717473+  83  Linux
/dev/sda6           47989       48641     5245191   82  Linux swap / Solaris

cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=5eaa0c9e-3cf0-46d8-bf5a-180ed4d66da5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=1b47fc54-4ca7-4dae-828c-7c2ddc104cdf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

sudo blkid
/dev/sda1: UUID="640831E80831B9BE" TYPE="ntfs" 
/dev/sda5: UUID="99c34e63-5359-4feb-b1b7-e667440beef3" TYPE="ext3" 
/dev/sda6: TYPE="swap" LABEL="ID_FS_USAGE=oth" UUID="5eaa0c9e-3cf0-46d8-bf5a-180ed4d66da5" 

free -m
             total       used       free     shared    buffers     cached
Mem:          2018       1769        248          0        727        607
-/+ buffers/cache:        434       1584
Swap:         5122          0       5122

---

### Post by iaculallad on 2008-09-19
> **klemperal said:**
> sudo fdisk -l


Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x19bf19be

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8434    67746073+   7  HPFS/NTFS
/dev/sda2            8435       48641   322962727+   5  Extended
/dev/sda5            8435       47988   317717473+  83  Linux
/dev/sda6           47989       48641     5245191   82  Linux swap / Solaris

cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=5eaa0c9e-3cf0-46d8-bf5a-180ed4d66da5 /               ext3    relatime,errors=remount-ro 0       1
[B][COLOR="DarkRed"]# /dev/sda6
UUID=1b47fc54-4ca7-4dae-828c-7c2ddc104cdf none            swap    sw              0       0[/COLOR][/B]
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

sudo blkid
/dev/sda1: UUID="640831E80831B9BE" TYPE="ntfs" 
/dev/sda5: UUID="99c34e63-5359-4feb-b1b7-e667440beef3" TYPE="ext3" 
**[COLOR="DarkRed"]/dev/sda6: TYPE="swap" LABEL="ID_FS_USAGE=oth" UUID="5eaa0c9e-3cf0-46d8-bf5a-180ed4d66da5" [/COLOR]**



Compare the UUID's of your SWAP from blkid and fstab, Notice the difference?

Now edit your fstab file:

```
gksudo gedit /etc/fstab
```

and change the value **[COLOR="DarkRed"]UUID=1b47fc54-4ca7-4dae-828c-7c2ddc104cdf[/COLOR]** to **[COLOR="DarkRed"]UUID=5eaa0c9e-3cf0-46d8-bf5a-180ed4d66da5[/COLOR]**. Save and close the file. While on your terminal:

```
sudo mount -a
sudo swapon /dev/sda6

```

---

### Post by klemperal on 2008-09-19
Thanks for the help.  Something I noticed is that the UUID for sda5 and sda6 were the same.  What should sda5's UUID be?

---

### Post by iaculallad on 2008-09-19
> **klemperal said:**
> Thanks for the help.  Something I noticed is that the UUID for sda5 and sda6 were the same.  What should sda5's UUID be?

It should be: UUID=5eaa0c9e-3cf0-46d8-bf5a-180ed4d66da5, w/c is correct.

---

### Post by klemperal on 2008-09-19
Thanks again, I do appreciate the help.

---

