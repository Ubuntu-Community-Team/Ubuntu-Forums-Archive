---
title: "Problem migrating to larger HD with clonezilla"
date: 2011-10-23
forum: New to Ubuntu
---

### Post by goodbye-windows(tm) on 2011-10-23
I bought a 250 GB HD for my primary computer and wanted to move the entire setup from my old (30 GB) hard drive. After the move, I planned to use Gparted to expand the partition out so that most or all the drive was available for expansion. 

The move went well and I thought I was home free. I tested the setup on the bigger HD and everything worked just as before.... 

I went to resize the 30 GB partition on the larger HD, but found I could not move or modify the 1.5 GB partition (sda5) that ubuntu created. Not being able to move the 1.5 GB partition prevents me from expanding the 30 GB partition. So, most of my drive is unusable and I'm limited to the original drive size (which is 30 GB).

Is there some way around this problem???? 

TIA.

Art

---

### Post by papibe on 2011-10-23
Could you post an screenshot of Gparted showing the disk's partition?
Also, could you post the results of these 2 commands:
```
df -h

sudo fdisk -l
```
Regards.

EDIT: you can't resize/modify the root partition if you are using it. You have to use Gparted on the LiveCD.

---

### Post by goodbye-windows(tm) on 2011-10-23
> art@art-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              24G  7.5G   16G  34% /
udev                  744M  4.0K  744M   1% /dev
tmpfs                 302M  744K  301M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  754M  156K  754M   1% /run/shm
/home/art/.Private     24G  7.5G   16G  34% /home/art
art@art-desktop:~$ 




art@art-desktop:~$ sudo fdisk -l
[sudo] password for art: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b532e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    50319359    25158656   83  Linux
/dev/sda2        50321406    53463039     1570817    5  Extended
/dev/sda5        50321408    53463039     1570816   82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6cff8916

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   488392064   244196001    7  HPFS/NTFS/exFAT

Disk /dev/mapper/cryptswap1: 1608 MB, 1608515584 bytes
255 heads, 63 sectors/track, 195 cylinders, total 3141632 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xadc24921

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table
art@art-desktop:~$ 

I do use gparted from the live cd. I'll get a sreenshot and post it in a few minutes.


Regards.

Art

---

### Post by Mark Phelps on 2011-10-23
sda5 is contained INSIDE sda2.  So, you have to resize the Extended partition (sda2) first.

Then, you can resize the contained partition to fill the Extended partition.

I'm concerned though, that the 1.5GB partition is shown as Unknown.

---

### Post by goodbye-windows(tm) on 2011-10-23
I've seen that 1.5 GB unknown partition every time i look at the partitions, I didn't realize it was unusual or atypical. It might have something to do with my encrypted home folder?? 

When I first saw that the format type for the 1.5 GB partition was 'unknown', I thought it was the ubuntu method for protecting the OS from being modified. Yes, it could be deleted, but it can't be messed with without corrupting the entire 1.5 GB partition.

Anyway, I tried to resize sda2, it worked. But, sd2 could not be moved, all the menu items in gparted are grayed out as soon as sda2 is selected. 

I attached another screen shot showing the results of resizing sda2....

Regards,

Art

---

### Post by Shazaam on 2011-10-23
The unknown partition was probably the original swap and might not have been unmounted (swapoff) before/during cloning.

---

### Post by goodbye-windows(tm) on 2011-10-24
> **Shazaam said:**
> The unknown partition was probably the original swap and might not have been unmounted (swapoff) before/during cloning.

Tnx Shazaam,

If it was an old left over swap file, then I should be able to delete it from the new drive I created yesterday without suffering any ill effects.

I'll delete it and try to boot once it's gone.

Here goes.....

---

### Post by goodbye-windows(tm) on 2011-10-24
Success!!!

I deleted the unknown 1.5 GB partition, although it took 4 separate procedures. The final procedure allowed me to create a single partition for xubuntu at 180 GB in size.

When I rebooted, there was no sign of an error. After the reboot, I looked at the drive again and found only the 180 GB partition-the OS did not create any additional partitions.

I'll continue playing with the system and will mark this issue as solved if I do not have additional errors pop up.

Thanks to all that replied.

Regards,

Art

---

