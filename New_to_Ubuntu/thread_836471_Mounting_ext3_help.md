---
title: "Mounting ext3 help"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by jonathonball on 2008-06-21
I have a Western Digital 500gb SATA drive that I just converted to Ext3.  I tried to set the mount point in the properties window of Nautilus and now get the following error.  

"Cannot mount volume. Unable to mount the volume.  mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)"

Here is my fstab.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ad13ed25-ba8a-4517-95f4-71c8464f0857 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=adc17dd9-1c27-49d9-a74d-2e20125e357e none            swap    sw              0       0
# dvd burner
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

The GUI window that I entered mount information to is no longer reachable now that the drive is unmountable.  Please help.

Also, when/if I fix this problem; where should I mount the drive in the file system and what should the fstab look like?  The drive is going to hold my long term storage docs/apps/games and movies and music.

---

### Post by avtolle on 2008-06-21
[https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs#head-15858102c5c29ecb7a37da25feedd6c091445e2d](https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs#head-15858102c5c29ecb7a37da25feedd6c091445e2d) Take a look at this, it might be helpful.

---

### Post by jonathonball on 2008-06-21
> **avtolle said:**
> [https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs#head-15858102c5c29ecb7a37da25feedd6c091445e2d](https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs#head-15858102c5c29ecb7a37da25feedd6c091445e2d) Take a look at this, it might be helpful.

Thank you,. but I don't have Windows XP installed on this system at all.  It's just Ubuntu.  I put some apparently incorrect settings into the Volume tab of the drive "Properties" window of Nautilus and now I can't access that same menu again or mount the drive, effectively locking me out of it.  I'm not sure how that link helps me, sorry if I'm wrong.

---

### Post by jonathonball on 2008-06-21
I tried deleting the ext3 partition in gparted and recreating it and it's still giving me the same error.

---

### Post by Baelus on 2008-06-21
You may need to get stuck into the command line for this. I don't know how familiar the terminal is to you, so I'll just go through it in as much detail as I can for now.

Open Applications ==> Accessories ==> Terminal.

Type this

```
sudo fdisk -l
```

That'll give you a bunch of info on what disks are attached to your system.

You will probably see a block starting with something like this:

```
Disk /dev/sdb: 500.0 GB
```

followed by some lines that look a bit like this

```
Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24060   193261918+  83  Linux
```

From your fstab it looks like Ubuntu is installed on /dev/sda (your main drive).

That means your second drive (the 500gb one) will probably be on /dev/sdb, but fdisk will tell you exactly.

If it is /dev/sdb then the first (and maybe only) partition will be /dev/sdb1.

Alternatively, let gParted tell you. It will be listed under "Partition".:)

Make a directory to mount it with this

```
sudo mkdir /media/wdigital
```

Use whatever name you like.

Now you can try to mount it with this

```
sudo mount -t ext3 /dev/sdb1 /media/wdigital
```

That should mount the 500gigs on /media/wdigital.

I think you need to change permissions to make it accessible to anyone other than root. But that can come later. First see if you can get it to mount.

- B

---

### Post by jonathonball on 2008-06-21
fdisk -l returns


```
Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x72877287

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24792   199141708+   b  W95 FAT32

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13a87a74

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30139   242091486   83  Linux
/dev/sdb2           30140       30515     3020220    f  W95 Ext'd (LBA)
/dev/sdb5           30140       30515     3020188+  82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5d7dc0ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   83  Linux

Disk /dev/sdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5590326a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        9728    78140128+   7  HPFS/NTFS

```

**/dev/sda** is a 200gb WD drive I'm using to hold some movie files while I do this conversion, it will be removed from the system when the 500gb drive is working.

**/dev/sdb** is the drive i installed ubuntu to.

**/dev/sdc** is the 500gb in question.

**/dev/sdd** is an 80gb I will eventually  put an emergency winxp install.

i can mount the drive with the command line no problem and access it in nautilus, so thank you that works... but i'd like to undo the damage i did originally when i edited the mount information in the Volume tab of the Nautilus properties window.

---

### Post by Baelus on 2008-06-21
This may help a bit. Also deals with Nautilus and mount points. 

[http://ubuntuforums.org/showthread.php?p=5224524#post5224524]("http://ubuntuforums.org/showthread.php?p=5224524#post5224524")

Any good?

- B

---

### Post by jonathonball on 2008-06-21
no dice... does anyone know where the nautilus configuration files are?  maybe I can find the setting and remove it from there.

---

### Post by jonathonball on 2008-06-21
i tried reinstalling nautilus from synaptic and am still having the problem.

here is a shot of the error

[http://theangrysnowflakes.net/hardpics/ss1.png](http://theangrysnowflakes.net/hardpics/ss1.png)

here is a shot of the screen i entered mount info to that screwed up my whole operation.  (different drive, same screen.)

[http://theangrysnowflakes.net/hardpics/ss2.png](http://theangrysnowflakes.net/hardpics/ss2.png)

---

### Post by Baelus on 2008-06-21
From this thread: [http://ubuntuforums.org/showthread.php?t=688144]("http://ubuntuforums.org/showthread.php?t=688144")

> "I had this same problem, only it was for my external hard drive. In the mount point, I entered /media/usbdisk because it was mounting as /media/disk.

I got the same error message, mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)

I found the setting by going Places | Computer. From there, was able to see my drive but it gave me that error when trying to mount. Right click | Properties | Volume Tab | Removed the mount point setting.

I found that if you want to change the mount point, you only have to put what it should be named. For instance, to have my disk mounted as /media/usbdisk, I put usbdisk into the box (an not the entire path)."

That's the best I got. Hope you find something that helps.

- B

---

