---
title: "Gparted"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by EvanRogers on 2008-10-03
OK i am trying to completely get rid of my windows on my system.

I open up gparted and when i select the windows partition it wont let me delete it. it says its mounted and that could be the problem but it wont let me unmount it...please help me.

---

### Post by kylet450 on 2008-10-03
[http://www.sysresccd.org/](http://www.sysresccd.org/)

burn it as an .iso

use the program on there to unmount it, and delete it.

---

### Post by Elfy on 2008-10-03
Can you run these from a terminal (Accessories menu) and post the outputs please, if you haven't yert used sudo it will ask for password - enter your normal password, be aware that it will not be visible

```
sudo fdisk -l
cat /etc/fstab
df -h
```

That is a lower case L in the first command.

---

### Post by wolfen69 on 2008-10-03
run ```
sudo fdisk -l
```to find out what your windows drive/partition is. (sda/sdb1, etc) then do ```
sudo umount /dev/sda1
``` or whatever it is, to unmount. or, if you run gparted as root, ```
sudo gparted
``` to open gparted, right click the partition and unmount.

---

### Post by EvanRogers on 2008-10-03
> **kylet450 said:**
> [http://www.sysresccd.org/](http://www.sysresccd.org/)

burn it as an .iso

use the program on there to unmount it, and delete it.

what program? i see a lot on there.

---

### Post by kylet450 on 2008-10-03
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download) 

Choose your architecture.

do x86 if you dont know what one you have.

---

### Post by Elfy on 2008-10-03
Just making sure here - the ubuntu install that you have is a normal install and not wubi - if it is wubi and you delete the windows you will have problems.

---

### Post by EvanRogers on 2008-10-03
> **kylet450 said:**
> [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download) 

Choose your architecture.

do x86 if you dont know what one you have.

Well that program is huge, and i have dsl..but i only get 32-33 kbps for some reason so it will take over 2 hours, any easier ways?

---

### Post by EvanRogers on 2008-10-03
> **forestpixie said:**
> Just making sure here - the ubuntu install that you have is a normal install and not wubi - if it is wubi and you delete the windows you will have problems.

Well this is the wubi one, so thank you for informing me, how do i get a different one\what will go wrong if i delete it?

---

### Post by kylet450 on 2008-10-03
sudo apt-get qtparted

That will work.

But if you cant -> download the cd. Sorry mate - best i can do.

---

### Post by Elfy on 2008-10-03
You already have a partition editor available on the livecd, but there is not any reason to boot that as you will be able to do what you need from within ubuntu unless you wish to resize the ubuntu partition - if you do want to do that then boot the livecd.

---

### Post by Elfy on 2008-10-03
If you have installed with wubi then you must migrate your install to it's own partition before you remove windows.

To do so you need to use LVPM - never done it myself as I haven't used wubi. The information can be found here - [https://wiki.ubuntu.com/WubiGuide#How](https://wiki.ubuntu.com/WubiGuide#How) do I migrate to a real partition, and/or get rid of Windows entirely?

The wiki is here [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

There is also a specific wubi forum which is likely to have more specific knowledge - [http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)

---

### Post by EvanRogers on 2008-10-03
> **forestpixie said:**
> You already have a partition editor available on the livecd, but there is not any reason to boot that as you will be able to do what you need from within ubuntu unless you wish to resize the ubuntu partition - if you do want to do that then boot the livecd.

Ok lets go through what i did, i downloaded the live cd a couple days ago, opened it up and clicked on wubi and it instsalled it and created its own partitions and everything. 

Now I'm on ubuntu and i want to get rid of my windows so that i will only have the ubuntu OS.

---

### Post by Elfy on 2008-10-03
To be clear here - wubi is ubuntu installed from within windows, you can remove it with the windows add/remove system - there will be a wubi folder/file visible from within windows. Wubi installs on a virtual disk so deleting wqindows also removes ubuntu.

'Normal' dual boot is installed directly form the livecd (if you have the livecd) - it isn't removable from within windows.

To get rid of windows if ubuntu is installed as wubi - you have 2 choices 
1 - use LVPM to migrate the install to it's own partition 
2 - reinstall ubuntu from the livecd 

To remove windows if ubuntu is installed 'normally' you just need to remove the partition that windows resides on.

If you are in any doubt whatsoever then run 
```
df -h
sudo fdisk -l
``` 

post the output and we can tell you.

---

### Post by EvanRogers on 2008-10-03
> **forestpixie said:**
> To be clear here - wubi is ubuntu installed from within windows, you can remove it with the windows add/remove system - there will be a wubi folder/file visible from within windows. Wubi installs on a virtual disk so deleting wqindows also removes ubuntu.

'Normal' dual boot is installed directly form the livecd (if you have the livecd) - it isn't removable from within windows.

To get rid of windows if ubuntu is installed as wubi - you have 2 choices 
1 - use LVPM to migrate the install to it's own partition 
2 - reinstall ubuntu from the livecd 

To remove windows if ubuntu is installed 'normally' you just need to remove the partition that windows resides on.

If you are in any doubt whatsoever then run 
```
df -h
sudo fdisk -l
``` 

post the output and we can tell you.

Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                       13G  3.0G  9.4G  25% /
varrun                251M   96K  251M   1% /var/run
varlock               251M     0  251M   0% /var/lock
udev                  251M   44K  251M   1% /dev
devshm                251M   12K  251M   1% /dev/shm
lrm                   251M   39M  213M  16% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon       13G  3.0G  9.4G  25% /home/evan/.gvfs


Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        9297    74637990    7  HPFS/NTFS
/dev/sda3            9298        9725     3437910   db  CP/M / CTOS / ...

---

### Post by Elfy on 2008-10-03
Yes - wubi - the /host/ubuntu/disks/root.disk and the fact there is no linux partition points to that.

It will probably be easier to do a clean installif you've not done much to the ubuntu yet but if you want to keep the install then you will have to use lvpm to move it to a partition.

---

