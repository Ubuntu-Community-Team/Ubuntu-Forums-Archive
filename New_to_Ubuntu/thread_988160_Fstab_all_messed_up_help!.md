---
title: "Fstab all messed up help!"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by bdelin88 on 2008-11-20
I am really trying with this whole ubuntu thing... but here's my deal:
I used hardy back in the day and my NTFS partitions were automatically mounted when I logged in.  With intrepid it has somehow lost that feature.

I have read tutorials trying to figure this one out... eventually leading to installing pysdm, a GUI for editing FSTAB.  **pysdm** reports that my partition containing windows is a swap partition, which is wrong.  I can't get it to change that option and save it.  **Basically I have NTFS partitions I want mounted: sda1, sdb1, and sdb2**

***Partitions I want to automount on boot**
*Windows: sda1
Linux: sdb3
Swap: sdb4
*Extra Storage: sdb2, sdb3

**Here is my fdisk output (fdisk -l):**
Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa341a341

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10012    80415744    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xabd7166f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24867   199740380    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2           31871       60802   232384512    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sdb3           24868       31263    51375870   83  Linux
/dev/sdb4           31264       31870     4875727+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 2047 MB, 2047868416 bytes
255 heads, 63 sectors/track, 248 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1          10       80293+   0  Empty
/dev/sdc2              11         248     1911732    b  W95 FAT32

**ALSO, if you're looking for some more ubuntu kinks to fix, maybe someone could take a look at the problem I am having with virtualbox seemless... seems like a minor fix:**
[http://ubuntuforums.org/showthread.php?p=6214788#post6214788](http://ubuntuforums.org/showthread.php?p=6214788#post6214788)

---

### Post by bdelin88 on 2008-11-20
**Typing: "cat /etc/fstab" into Terminal reveals the following:**
proc                                       /proc          proc         defaults                    0  0  
UUID=c2dc53c5-81ee-42d9-a6bf-bd8e86528816  /              ext3         relatime,errors=remount-ro  0  1  
UUID=96e6d499-040a-46f6-b0f0-5bcfb9bba987  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
none                                       /proc/bus/usb  usbfs        devgid=1001,devmode=664     0  0  
none /proc/bus/usb usbfs devgid= *enter vboxusers Group ID number HERE*,devmode=664 0 0  
/dev/sdb2                                  /media/sdb2    ntfs         nls=iso8859-1,umask=000,ro  0  0   
/dev/sdb1                                  /media/sdb1    ntfs         nls=iso8859-1,umask=000,ro  0  0

**^^^^^The last two entries for sdb2/sdb1 were made with _pysdm_, but those entries do not look like anything I have seen on the forums and they don't do the job very well...**

---

### Post by ajgreeny on 2008-11-20
To automount partitions at bootup you first need to make mount points for them with commands like ```
sudo mkdir /media/windows
``` but using whatever name you want.  Now using those mount points you will need to edit fstab with ```
gksudo gedit /etc/fstab
```Now add to fstab lines with the following patterns:-

Automount ntfs windows.  Add line to /etc/fstab:-
/dev/sda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0


Automount linux partition.  Add line to /etc/fstab:-
/dev/sdb3       /media/linux   ext3    defaults  0  1

and so on for all the partitions you want to mount.  You can use the UUID instead of /dev/sda notation if you prefer, as in the way your fstab notes the partitions, but both work OK.  To find the UUIDs use ```
sudo blkid
```

---

### Post by bdelin88 on 2008-11-20
Thanks!  I'll see if this works or not...

---

### Post by bdelin88 on 2008-11-21
I think it worked?

---

### Post by bsnapp on 2008-11-23
Thanks ajgreeny!  This really helped.

---

### Post by Dedoimedo on 2008-11-23
Hello,

I posted this simple tutorial just 4 days ago ...

How to automount NTFS drives in Linux:
[http://www.dedoimedo.com/computers/automount_ntfs.html](http://www.dedoimedo.com/computers/automount_ntfs.html)

Dedoimedo

---

