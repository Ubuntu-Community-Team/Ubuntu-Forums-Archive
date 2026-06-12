---
title: "an embarrassing mistake i made..."
date: 2008-05-26
forum: New to Ubuntu
---

### Post by napolean9 on 2008-05-26
this is a rather embarrassing mistake i made, but i really need help so i'll just explain. basically, i tried to reconfigure my mount options for my ipod mini, going to properties, mount settings, and changing the ro to rw. unfortunately, now i've made it so my ipod won't even mount. it says "invalid mount option when attempting to mount the volume '________'s ipod." 

now i did more research and i know how to get my ipod to be read-write, but i'm still stuck because i can't even mount my ipod anymore!

is there any way for me to reset the mount options on my ipod, or something?

---

### Post by aysiu on 2008-05-29
I don't know, but can you paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal) (with your ipod plugged in): ```
sudo fdisk -l
df -h
cat /etc/fstab
``` and then paste the output back here?

---

### Post by napolean9 on 2008-05-31
this is from fdisk -l:

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4998    40146403+  83  Linux

Disk /dev/sdb: 20.4 GB, 20490559488 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0bb77142

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2491    20008926    5  Extended
/dev/sdb5               1        2491    20008894+  83  Linux

Disk /dev/sdc: 4095 MB, 4095737344 bytes
126 heads, 62 sectors/track, 1023 cylinders
Units = cylinders of 7812 * 512 = 3999744 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

    df -h:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              38G  5.0G   31G  14% /
varrun                379M   92K  379M   1% /var/run
varlock               379M     0  379M   0% /var/lock
udev                  379M   68K  379M   1% /dev
devshm                379M   12K  379M   1% /dev/shm
lrm                   379M   38M  342M  10% /lib/modules/2.6.24-17-generic/volatile
/dev/sdb5              19G  9.2G  8.7G  52% /home


  fstab: 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=c2cb4092-269c-4ecf-a75a-085837f431c4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=aea8c1fd-ae4d-4890-a0af-2485d679147c /home           ext3    defaults        0       2
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0

---

### Post by FuturePilot on 2008-05-31
Can you mount other things like USB flash drives or is this only your iPod?

---

### Post by napolean9 on 2008-05-31
only ipod, because i messed up the mount settings when i went to preferences, volume, settings and messed around in it.

---

### Post by FuturePilot on 2008-05-31
Hmmm. Try this.

```
mv ~/.gconf/system ~/.gconf/system_backup
```

~/.gconf/system is where things like the mount options are stored. The system directory will automatically be recreated when you login again, which will reset those to the default settings. So go ahead and log out and back in again. Then try mounting your iPod.

---

### Post by napolean9 on 2008-05-31
thanks that worked! i've been trying to fix that for a while now, thanks.

---

### Post by FuturePilot on 2008-05-31
No problem. :)

---

### Post by unutbu on 2008-05-31
napolean9's fdisk reported
```
Disk /dev/sdc: 4095 MB, 4095737344 bytes
126 heads, 62 sectors/track, 1023 cylinders
Units = cylinders of 7812 * 512 = 3999744 bytes
Disk identifier: 0x00000000

**Disk /dev/sdc doesn't contain a valid partition table**

```

Is /dev/sdc the ipod?
Is it normal for ipods to lack a partition table?

---

