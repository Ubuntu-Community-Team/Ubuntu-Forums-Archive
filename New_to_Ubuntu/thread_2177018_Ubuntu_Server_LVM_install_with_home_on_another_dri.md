---
title: "Ubuntu Server LVM install with /home on another drive?"
date: 2013-09-26
forum: New to Ubuntu
---

### Post by qwerty3656 on 2013-09-26
I'm trying to [re]install a ubuntu 12.04 server.  I have a small ssd drive and 2 large drives.  I'm trying to mount root, boot and swap on the ssd and mount /home on one of the big drives and have it all setup in an LVM.  I've tried every combination in the installation program.  I can either 1) use the lvm automated install which sets up the lvm, but mounts everything on the SSD; or 2) do manual setup and can partition and mount exactly like I want, but can't setup LVM.

What am I doing wrong?

---

### Post by DuckHook on 2013-09-27
You need to set the LVM up first in a LiveDVD/USB environment making sure that it is both assigned a volume group and then initialized. Then install choosing "something else" when the install process asks you where you want the various directories. You should now be able to assign /home to the LVM.

Instructions for creating a LVM are [here]("https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall"). This help doc also gives you instructions for migrating your /home to an LVM after install, which might be all that you need.

To prevent write fatigue and premature SSD failure, you may not wish to use the SSD for swap or for any other heavily accessed file system. On my system, not only is swap on a HDD partition but also /tmp and /var, the first of which is used for temporary files and the second of which is used for log files (and therefore sees heavy I/O activity).

---

### Post by qwerty3656 on 2013-09-27
That "something else" option is on the desktop version of the install disk, but I don't see it on the server version of the install?  Maybe I should just install the system and then do the "migration".

---

### Post by DuckHook on 2013-09-27
I'm going by memory, but I'm pretty sure that the server version already offers (and only offers) the equivalent of "something else". In other words, it should already allow you to map /home (or any other directory, for that matter) to the partition of your choice. Server installs would have to act that way because the whole point of creating servers is to have fine tuned control of where you want things to go.

---

### Post by qwerty3656 on 2013-09-27
[I don't doubt that I am missing it, but I don't see it.  I think I am going to try the regular install and then set up LVM afterward.]  Thanks for your help

EDIT: I made one more try and I think I figured it out.  FWIW In-case someone searches and happens upon this thread, the rough basic steps I took are below.

I have a 30GB SSD (driveA) and two 2TB drives (driveB and driveC).  For now (I'll do the rest in webmin) I wanted to get:

ON driveA:
12 GB with Root mounted (/)
256 MB with /boot mounted

ON driveB
8.6 GB swap
4 GB /tmp
4 GB /var
800 GB /home

- Selected manual partition
- Just made 1 partition per drive (12GB partition on driveA and 817GB partition on driveB) and don't mount them or use them.
- select manage LVM  
- create Volume Group and select the 2 partitions I made
- create 6 logical volumes the sizes listed above.
- then mount them using ext4

Thanks again for your help

Edit2: you should ignore the sizes of the partitions-they are likely not optimal

---

