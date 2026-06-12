---
title: "Noob with four swaps seeks partitioning scheme feng shui."
date: 2012-01-08
forum: New to Ubuntu
---

### Post by /z@ch on 2012-01-08
:-k It would appear I've accrued a few extra swap partitions over my (re)installation lifetime:

```
z@ch:~$ sudo fdisk -l
[sudo] password for z: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x514e6243

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   292968812   146484375    7  HPFS/NTFS/exFAT
/dev/sda2       359950334   625137344   132593505+   5  Extended
/dev/sda5       613827648   625137344     5654848+  82  Linux swap / Solaris
/dev/sda6       603430912   613826559     5197824   82  Linux swap / Solaris
/dev/sda7       599502848   603416575     1956864   82  Linux swap / Solaris
/dev/sda8       359950336   595572735   117811200   83  Linux
/dev/sda9       595574784   599496703     1960960   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 4009 MB, 4009754624 bytes
124 heads, 62 sectors/track, 1018 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005969d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62     7826383     3913161    c  W95 FAT32 (LBA)
```

:mad: I'm pretty sure I didn't create these manually, so I guess they were made when I used the Ubuntu installer to install over my current Ubuntu on the disk. I don't know if this is a bug, or just my ignorance. Probably the latter. :oops:

As you can see, I have Windows, my Ubuntu, and a bunch of swaps. I only became aware of my mess because I wanted to triple-boot, adding the 12.04 alpha. Obviously, there's no click and go button for setting up triple-boots in the installer, so I had to look at the manual option. I'm just doing this for fun/out of curiosity, and I don't have any important data to lose. So I don't mind booting in to the 11.10 installer again, deleting all the swaps, the ext4, and installing clean. I do, however, want to learn a good partitioning scheme so I can have Win7, 11.10, and 12.04 alpha. Can I have a shared partition in there too, so I can access/save files from any OS? BTW, my Windows partition is 150gb, but I wouldn't mind shrinking it. While I wait, I'll boot in to that and see what space I have.

Thanks in advance for any guidance. :)

---

### Post by Paqman on 2012-01-08
> **/z@ch said:**
> I don't mind booting in to the 11.10 installer again, deleting all the swaps, the ext4, and installing clean.

No need for that. Boot up into your LiveCD or USB and run Gparted, which is the same partition editor the installer uses. Then right click on any/all of your swaps that have a little key symbol on them and "swapoff". Then you can go ahead and delete all but one of them and give the space to your other partitions.

Once you're booted back into Linux you can edit the file /etc/fstab to remove any reference to swap partitions you no longer have. To edit that file:
```

gksudo gedit /etc/fstab

```
Leaving those entries in won't cause any b0rkage, but it's tidier to get rid of them.

> 
Can I have a shared partition in there too, so I can access/save files from any OS?


Yes, the best filesystem for this would be NTFS, as both Linux and Windows play nicely with NTFS.

Some people also keep /home on a separate partition. Doing so can make reinstalling simpler, although it's less crucial than it used to be. Different Linux installs can share a /home partition, just as long as you use different user accounts on each system.

---

