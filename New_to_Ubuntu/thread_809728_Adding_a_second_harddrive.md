---
title: "Adding a second harddrive"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by JustAnotherVagueAnon on 2008-05-27
Hello, I have Vista and Hardy installed on my primary HDD and just now installed a second HDD where I want to store data and non-program files. I want to format this new drive in fat32 and don't know where to start.

Output of sudo fdisk -l:
```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19190   154139719+   7  HPFS/NTFS
/dev/sdb2           19191       19197       56227+  83  Linux
/dev/sdb3           29263       30401     9149017+   7  HPFS/NTFS
/dev/sdb4           19198       29262    80847112+   5  Extended
/dev/sdb5           19198       19445     1992028+  82  Linux swap / Solaris
/dev/sdb6           19446       29262    78855021   83  Linux

```
How do I format /dev/sda?

---

### Post by sayakb on 2008-05-27
Install GParted:
```
sudo apt-get install gparted
```

Goto system->administration->partition editor and select /dev/sda from top-right drop-menu. Then delete/format accordingly.

---

### Post by Duck2006 on 2008-05-27
Use gparted or parted magic to format the drive.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

[http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)

Once formated, mount the drive in linux and it's set to go.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by JustAnotherVagueAnon on 2008-05-27
I got it partitioned but I'm having trouble setting a mount point. here's the output of **sudo fdisk -l** now:
```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dfd9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38913   312568641    b  W95 FAT32

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19190   154139719+   7  HPFS/NTFS
/dev/sdb2           19191       19197       56227+  83  Linux
/dev/sdb3           29263       30401     9149017+   7  HPFS/NTFS
/dev/sdb4           19198       29262    80847112+   5  Extended
/dev/sdb5           19198       19445     1992028+  82  Linux swap / Solaris
/dev/sdb6           19446       29262    78855021   83  Linux

Partition table entries are not in disk order

```

---

### Post by JustAnotherVagueAnon on 2008-05-27
By the way, my fstab looks like this:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=a0369f42-e602-4e22-939f-85c97405ed65 /               ext3    relatime,erro$
# /dev/sda2
UUID=83113965-0e0c-485a-985b-fb7360801fa8 /boot           ext3    relatime     $
# /dev/sda5
UUID=22be3a91-936b-45f8-a61f-b3e66b9126d6 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


```

---

