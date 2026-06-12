---
title: "[SOLVED] Formatting a hard drive"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by loseby on 2008-09-27
Want to format a hard drive that has a previous installation of Ubuntu on it. At the moment I have a dual boot system with Vista and Ubuntu on seperate drives but I want to wipe out the previous Ubuntu version that is on a totally seperate drive.

How do you do this using Ubuntu ?

---

### Post by zephyrcat on 2008-09-27
To completely reformat a drive, which will destory all of your data, use Add/Remove (from the Application menu) to install GParted. Then, using GParted, choose the right hard drive and delete all the partitions. Finally, click apply.

This is not nessessarily a secure wipe, though. It is very likely that the data could be recovered (likely at significant cost and nothing is gurenteed), so if you have sensitive data, try something like DBAN:

[http://www.dban.org/](http://www.dban.org/)

Finally, be careful with wiping hard drives! You might even physically disconnect or remove the drive you do not want to wipe.

---

### Post by jpeddicord on 2008-09-27
If you want to install Ubuntu over the entire drive, just use the installer on the Desktop CD and choose "Use entire disk."

If you just want to format the drive, install gparted from Synaptic or Apps > Add/Remove. Access it from System > Administration > Partition Editor, select the drive/partition you want to format (make sure it isn't active or mounted) and select Format. Pick a filesystem type from the menu (Ext3 is normal for Ubuntu, FAT32 for most thumb drives/SD cards to work on all OSes). When you are **absolutely sure** you have the right drive and want to format it, click Apply (or OK) to continue.

---

### Post by loseby on 2008-09-28
> **zephyrcat said:**
> 

This is not nessessarily a secure wipe, though. It is very likely that the data could be recovered (likely at significant cost and nothing is gurenteed), so if you have sensitive data, try something like DBAN:

[http://www.dban.org/](http://www.dban.org/)

Finally, be careful with wiping hard drives! You might even physically disconnect or remove the drive you do not want to wipe.


Thankyou for your reply

I know which drive it is and I will take care that the right one is formatted and even if I somehow manage to muck things up all my important data is backed up elsewhere

---

### Post by lykwydchykyn on 2008-09-28
shred is a nice command for wiping out drives.
For instance:
```

#Don't try this at home, kids; it wipes out sdb for good
shred -vzn 1 /dev/sdb

```
Will overwrite sdb with random values once, then zeros.

---

