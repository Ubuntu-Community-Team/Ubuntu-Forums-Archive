---
title: "LUKS + mdadm (mounted and open) = disk access every second!"
date: 2016-10-01
forum: New to Ubuntu
---

### Post by tibitek on 2016-10-01
Hi there,

I'm new to ubuntu, so i'm having some trouble as expected. I've got a RAID10 (with 4 disks), and each time I luksOpen and mount it the computer disk drive LED blinks each second indicating that some disk access is preventing the disks from going to sleep. I've set everything in /etc/hdparm.conf and when not mounted the disks go to sleep. I've looked up if there is some disk access going on but even ps on the mounted dir doesn't give any meaningful result. 

My configuration:
Ubuntu 16.04.1, everything up to date

D: Halp plz ;-;

---

### Post by frostschutz on 2016-10-01
Which filesystem? ext4 lazy init might annoy the disks for a few days. 

I use LUKS, mdadm, XFS and no issue with disk standby.

---

### Post by tibitek on 2016-10-01
Ah i see. I didnt even know that ext4 doesn't initialise all inode tables on format, now since I know I'll make sure to mkfs.ext4 next time with lazy init disabled. Luckily, disk access has stopped (I think it finished doing the inode stuff), and the problem can be regarded as resolved. I even considered maybe reinstalling ubuntu since I didnt know what was going on.

Danke dir :)

---

