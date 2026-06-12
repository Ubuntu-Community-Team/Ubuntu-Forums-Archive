---
title: "My Grub setup how I got it to boot"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by jjascarm on 2008-05-12
I just got my Hardy grub setup sorted, and thought that it may be helpful to post how I got my particular Grub setup to work properly. I will start by explaining my setup: I have three hard drives, an 80GB IDE disk which has an existing Windows XP installation on it, two 320GB SATA disks, one for Linux and one for data storage. I installed hardy onto the fist 320GB drive (sdb) - I will elaborate on this later. I made sure that Grub was installed on this disk. I did this becasue I wanted to make sure that the Windows XP disk was untouched and could boot on its own. When I rebooted after the install I set the Linux to boot first in the bios, and it *did not boot*. So I rebooted into linux using the live CD so that I could edit the Grub menu.lst file. I did this by running ```
sudo gedit
``` and then browsing to the file. In the file the Ubuntu drive was setup as HD1,1 which should have been correct as fdisk recorder the three disks as follows:
```
isk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xebb6ebb6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xae801b68

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       37967   304969896   83  Linux
/dev/sdb2           37968       38913     7598745    5  Extended
/dev/sdb5           37968       38913     7598713+  82  Linux swap / Solaris

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008e53c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641    7  HPFS/NTFS
```

As I said though it *did not boot*, and as the Linux disk was now first in the boot order in the bios, I set it it to HD0,0 - Now Linux could boot.

Now to the XP disk:
My next step ws to get XP to boot - this took some time. As you can see from the fdisk listing Linux should have been HD1, but in reality was HD0. Because of this fact I though that I would try setting the Windows disk to HD1 and HD2 in the menu.lst file to see what would happen so I changed the Windows XP section to the following:
```
root (HD1,0
map  (HD0)(HD1)
map  (HD1)(HD0)
chainloader +1
```
The map command is to trick XP into thinking it is on the first disk
I tried this, as well as exchanging HD1, with HD2 with no luck, I got different errors in each situation. With HD1 I got error 11: invalid device string, and with HD2 I got error 25: disk read error.
I had almost given up and decided to just select the boot disk from the bios, but thought I would try using the Grub command line to boot Windows.
I typed root (HD1,0) that was ok.
I typed map (HD0)(HD1) that gave me error 11, as above...
I thought "invalid device string, hmmm maybe there is meant to be a space between the two brackets, so I typed
```
map (HD0) (HD1)
```
that was ok so I continued, and typed the following
```
map (HD1) (HD0)
chainloader +1
```
Then Windows booted ok.

I hope my description of my experience may help someone in trying to get there multi-boot system to work...

---

