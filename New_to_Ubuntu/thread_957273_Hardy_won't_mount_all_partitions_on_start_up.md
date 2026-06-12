---
title: "Hardy won't mount all partitions on start up"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by Udibuntu on 2008-10-24
Hi,

Recently installed Hardy clean on top of Feisty.

In contrast to Feisty, Hardy will not mount all partitions (i.e show them on desktop) after start up.

All partitions do show in "locations" menu, and do appear on desktop after I click them in "locations" menu.

I know there is a fix but I don't know the exact script/method.

Cheers,

Udi

---

### Post by Liviu-Theodor on 2008-10-24
Run the following in terminal:
```
sudo blkid
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
```
The first command gives the UUID for each partition. At the last command, insert the partitions, with the mount points that you wish (ie [FONT="Courier New"]/home[/FONT]).

But still that will not show all the partitions on desktop, but will have them mounted and usable as such (standard POSIX folders).

---

### Post by Udibuntu on 2008-10-24
Thanks LT. Your solution will do fine but I need an idiot proof code, like:

yadayada /home/partition name

Or something...

---

### Post by kpkeerthi on 2008-10-24
Post the output of 
```
sudo fdisk -l
```
* Hightlight the partitions you want to mount at boot, in the output of the above command.

```
sudo blkid
```
```
mount
```

---

### Post by Udibuntu on 2008-10-25
> **kpkeerthi said:**
> Post the output of 
```
sudo fdisk -l
```
* Hightlight the partitions you want to mount at boot, in the output of the above command.

```
sudo blkid
```
```
mount
```

> Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed1f86f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2480    19920568+   7  HPFS/NTFS
/dev/sda2            2481        5874    27262305    f  W95 Ext'd (LBA)
/dev/sda3            6749        7296     4392360   12  Compaq diagnostics
Partition 3 does not end on cylinder boundary.
/dev/sda4            5875        6748     7020405   83  Linux
/dev/sda5            2481        3785    10482381   83  Linux
/dev/sda6            3786        3916     1052226   82  Linux swap / Solaris
**/dev/sda7            3917        5874    15727603+   7  HPFS/NTFS**

Partition table entries are not in disk order
udi@udi-laptop:~$ 

OK, thanks, now what do I do?

---

### Post by kpkeerthi on 2008-10-28
See [https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by Udibuntu on 2008-11-03
I can use the partitions all right, but they are not shown as icons on the desktop and links to stuff that is in those partitions do not work after start up - I have to click on the partition on "places" menu and then the partition appears on the desktop and everything works.

What I need is for this to be done automatically, like in Feisty which I had.

Thanks again,

Udi

---

