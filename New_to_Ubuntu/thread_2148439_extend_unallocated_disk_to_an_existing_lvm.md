---
title: "extend unallocated disk to an existing lvm"
date: 2013-05-25
forum: New to Ubuntu
---

### Post by pedenski on 2013-05-25
hello, im very new to linux and been using ubuntu server and i plan to create a media server where i store all my videos/pictures/etc. on my VM
windows can easily detect unallocated partition without restarting, can linux does this aswell?


ubuntu server is running on VM, initial setup was to have 10GB size, then increased it to 5GB, then added another 15GB for the total of 30GB.

```
Disk /dev/sda: 32.2 GB, 32212254720 bytes
255 heads, 63 sectors/track, 3916 cylinders, total 62914560 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002948a


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758    20969471    10233857    5  Extended
/dev/sda4        20969472    31457279     5243904   8e  Linux LVM
/dev/sda5          501760    20969471    10233856   8e  Linux 
```

when i try to create another partition out of /dev/sda, im getting below error

```
All primary partitions are in useAdding logical partition 6
No free sectors available
```

[COLOR=#333333][FONT=Ubuntu Beta]how can i use my unallocated disk to extend my lvm? i cant seem to create a new partition anymore. is there a limit to it?
should i still use LVM? gparted is no use when dealing with lvm type of system.


[/FONT][/COLOR]

---

### Post by yeats on 2013-05-25
There are several "layers" to consider: the filesystem size, the volume group size and the logical volume size... All three have to be increased after you've added empty space to the disk.

This would probably be a good reference for you: [http://tldp.org/HOWTO/LVM-HOWTO/extendlv.html](http://tldp.org/HOWTO/LVM-HOWTO/extendlv.html)

---

