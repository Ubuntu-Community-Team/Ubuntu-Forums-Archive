---
title: "Can not mount External HD"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by wariskampar on 2008-06-09
Hello, before this I can use(transfer file etc) my hard disk with a breeze. But since upgrading (i only assume!!) to kernel 18, my Ubuntu does not detect the HD again. However when I type lsusb in terminal, i can see my HD (LACIE) listed on it. I even try to boot with old kernel (17) but problem persist. What should be the problem???

---

### Post by hovzio on 2008-06-09
Ive had a similar problem and solved it by mounting it via terminal. Have you tried to manually mount the drive with a specified mount point. First create a mount point point with sudo:

    sudo mkdir /whereever/you/want/it
 
then see what the device name is

    sudo fdisk -l

should be /dev/sdb1 or something of the likes and then mount..

     sudo mount /dev/sdb1 /location/you made earlier.

you might be asked to provide the filesystem type, if so:

     sudo mount -t vfat /dev/sdb1 /location/you made earlier.

the above would be apropriate for a fat filesystem.

If youve already tried the above then thats all I can think of. Have you properly removed the drive from windows.This is important.

---

### Post by Helgiks on 2008-06-09
If the above doesn't help you post the output to the following

```
fdisk -l && cat /etc/fstab
```

Otherwise you should be able to access it with $ sudo mount -t <TYPE> /dev/<DRIVE> </mount/point> like he posted above, name of the <DRIVE> you can find out with fdisk -l.

If it doesn't auto mount than you should add the appropriate line in /etc/fstab file to do so. 

type $ man 5 fstab and if anything is still unclear post here for help.

---

### Post by kansasnoob on 2008-06-09
For hot-plugging USB devices ie: pen drives, cameras, etc I've found that installing usbmount or, if prefered, both pmount and hal to be simple and straight forward.

The only advantage of pmount + hal over usbmount is that a desktop icon pops up on the desktop automatically when most devices are plugged in. Of course either can be done using synaptic or apt. (I prefer synaptic)

Also I've found ntfsprogs to be invaluable for extended capabilities of working with ntfs partitions. It's also available in the repos.

[http://www.linux-ntfs.org/doku.php](http://www.linux-ntfs.org/doku.php)

---

### Post by wariskampar on 2008-06-09
how do i check my ext. HD is FAT32 or ntfs (i'm sure it is not etx3)?

---

### Post by didac on 2008-06-09
> **wariskampar said:**
> how do i check my ext. HD is FAT32 or ntfs (i'm sure it is not etx3)?

```
sudo fdisk -l
```

will tell you. Something like this:

```

/dev/sda1   *           1        3650    29318593+   7  HPFS/NTFS
/dev/sda2            3651        3772      979965    e  W95 FAT16 (LBA)
/dev/sda3            3773        3785      104422+  83  Linux
/dev/sda4            3786        9729    47745180    5  Extended
/dev/sda5            3786        9729    47745148+  8e  Linux LVM

```

Yours will be /dev/sdb1, most probably. The end of the line will tell you whar is it.

---

### Post by wariskampar on 2008-06-09
This is the result of fsdisk -l 


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1883    15125166    7  HPFS/NTFS
/dev/sda2            1884        9729    63022995    f  W95 Ext'd (LBA)
/dev/sda5            1884        4879    24065338+  83  Linux
/dev/sda6            4880        7747    23037178+  83  Linux
/dev/sda7            7748        9640    15205491   83  Linux
/dev/sda8            9641        9729      714861   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12345678

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312568641    c  W95 FAT32 (LBA)

Now, i will follow the first instruction and hope it will solve my problem.

---

### Post by wariskampar on 2008-06-09
OK, now my ext. HD is mounted and can be used. However i dont see its entry in fstab. Below is the result

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=4aa78148-ff25-4f74-8388-3cf5f6331a70 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=896b90c2-7748-4e30-9872-8c9e24b51cd6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

#/dev/nameofdisc1
/dev/sda5 /media/sda5 ext3 defaults 0 2
#/dev/nameofdisc2
/dev/sda6 /media/sda6 ext3 defaults 0 2
#/dev/sda1
/dev/sda1 /media/sda1 ntfs defaults 0 0 

Do I have to manually key in the appropriate entry (like i did for sda5,sda6 and sda1) to ensure that i dont have to go through the same process everytime i want to use my HD? (phew! very long question!!!)

---

### Post by wariskampar on 2008-06-09
Hello, as expected the solution on 2nd post do not solve my problem permanently. Once mounted, i do not unmount the HD (right click..). I reboot just in case the system need to be refreshed but the problem persist; my external HD do not appear automatically when i plug it in (like it use to be). fsdisk -l yield the same result as my previous post. Any solution guys?

---

### Post by Helgiks on 2008-06-09
If you wan't it to be mounted on boot, add the following to your /etc/fstab file.

/dev/sdb1 <LOCATION> vfat rw,user,noauto,umask=0 0 0 

And it wil mount on boot, and you will be able to mount it as a normal user with full permissions, if you don't want that, than remove umask=0 (or adjust it to your needs) and remove user, like this.

/dev/sdb1 <LOCATION> vfat rw,noauto 0 0

And ofcourse replace <LOACATION> with your mountpoint.

---

### Post by hovzio on 2008-06-09
To manually unmount the drive:

```
sudo umount /dev/sdb1
```

yes that is "umount" and not "unmount"

you will need to manually add the drive to /etc/fstab. Since you can manually mount the drive you know everything works so adding it shouldn't be a problem. Check this out:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by wariskampar on 2008-06-09
ok. here is my solution; manually add new entry in fstab for HD, sudo mount -a every time i plug in the HD and sudo eject if want to plug out. until i found way auto mount it (appear automatically on desktop whenever plug in), this method will do for me. Thanks

---

### Post by wariskampar on 2008-06-09
i miss the last 2 posts. @helgiks, i do not want to auto mount it on boot.i just want to mount it whenever i plug it in (because i share this HD with my wife). what is the entry in fstab. for the time being, i use this
/dev/sdb1 <location> vfat 0 0

---

