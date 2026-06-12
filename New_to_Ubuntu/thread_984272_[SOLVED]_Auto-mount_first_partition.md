---
title: "[SOLVED] Auto-mount first partition ?"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by Drakkor on 2008-11-16
Yeah, I just installed 8.10 Ibex,and want to automount my sda1 partition, as you can see sda5 and sda6 are my linux and swap partitions. Thanks :)
Here's some  output that was suggested on another thread

drakkor@drakkor-desktop:~$ sudo fdisk -l
[sudo] password for drakkor: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x49fa46e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       26626   213872070+   7  HPFS/NTFS
/dev/sda2           26627       59553   264486127+   5  Extended
/dev/sda5           26627       57713   249706296   83  Linux
/dev/sda6           57714       59553    14779768+  82  Linux swap / Solaris
drakkor@drakkor-desktop:~$ 

drakkor@drakkor-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=978f0eb3-e73b-4d0c-86ba-2eda8a3927b3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=259fa23b-530a-453a-8dc8-7b74460cba7f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
drakkor@drakkor-desktop:~$ 

drakkor@drakkor-desktop:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2008-11-16 02:10 259fa23b-530a-453a-8dc8-7b74460cba7f -> ../../sda6
lrwxrwxrwx 1 root root 10 2008-11-16 02:10 978f0eb3-e73b-4d0c-86ba-2eda8a3927b3 -> ../../sda5
lrwxrwxrwx 1 root root 10 2008-11-16 02:10 F058F6AA58F66F2A -> ../../sda1
drakkor@drakkor-desktop:~$

---

### Post by mapes12 on 2008-11-16
Try Pysdm which allows you to decide which drives to mount or unmount during startup. Pysdm is a GUI application and therefore easy to use.

To install it

```
sudo apt-get install pysdm
```

To run it after install

```
sudo pysdm
```

Home page: [http://pysdm.sourceforge.net/](http://pysdm.sourceforge.net/)

---

### Post by drs305 on 2008-11-16
If you decide to use pysdm, there is a link on how to use it in my signature line (SDM).

If you want to mount it in fstab by manually editing the file, add this to /etc/fstab. Change *mountpoint* to the name of an existing folder in /media or create a new one:
```

/dev/sda1 /media/*mountpoint* ntfs-3g auto,users,uid=1000,gid=100,utf8,umask=027 0 0

```

Make sure the mountpoint exists (/media/mountpoint). You can also change the ownership of the mountpoint to yourself (chown -R yourusername /media/mountpoint), although ntfs doesn't actually support permissions (ownership is established by the mount or fstab command).

---

### Post by Drakkor on 2008-11-16
Thanks,guys, I tried pysdm , but sda1 didn't show up,then I tried manually,and in my /etc/fstab added the line,and commented it like the other entries,and that didn't work, so then I uncommented it,and now it works fine !! :) 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
 /dev/sda1 /media/ACER ntfs-3g auto,users,uid=1000,gid=100,utf8,umask=027 0 0
# /dev/sda5
UUID=978f0eb3-e73b-4d0c-86ba-2eda8a3927b3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=259fa23b-530a-453a-8dc8-7b74460cba7f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by drs305 on 2008-11-16
> **Drakkor said:**
> 
 /dev/sda1 /media/ACER ntfs-3g auto,users,uid=1000,gid=100,utf8,umask=027 0 0

If you would like to change /dev/sda1 into a UUID like your other entries, you can run "sudo blkid | grep /dev/sda1" to see /dev/sda1's designation. You could then make the entry look like the others by replacing "/dev/sda1" with "UUID=" and the designation.

The advantage of identifying the partition by UUID is that the UUID designation will not change unless the partition is reformatted, whereas there is a *possibility* that the /dev/sda1 designation could change if another drive or device is added or if the system recognizes the devices in a different order for some reason.

---

### Post by Drakkor on 2008-11-16
Thanks, drs305 , I need a little help to properly apply it.  I got

/dev/sda1: UUID="F058F6AA58F66F2A" LABEL="ACER" TYPE="ntfs" 
 
I think I got it ! It does work,lol 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=F058F6AA58F66F2A /media/ACER ntfs-3g auto,users,uid=1000,gid=100,utf8,umask=027 0 0
# /dev/sda5
UUID=978f0eb3-e73b-4d0c-86ba-2eda8a3927b3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=259fa23b-530a-453a-8dc8-7b74460cba7f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

