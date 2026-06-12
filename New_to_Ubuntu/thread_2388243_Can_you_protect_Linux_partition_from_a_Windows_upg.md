---
title: "Can you protect Linux partition from a Windows upgrade."
date: 2018-03-30
forum: New to Ubuntu
---

### Post by crip720 on 2018-03-30
I was wondering if there is a way to protect or isolate Ubuntu/Linux partitions if you wanted to upgrade a Windows OS.  I know about backups/cloning should be done and that grub will have to be reinstalled, but wanted to know if there is anyway to make sure a Windows upgrade does not make a mess of Linux type partitions if they are on the same hard drive.  Have been stories that some upgrades make Ubuntu partitions almost disappear or are unreadable.  Thank you.

---

### Post by TheFu on 2018-03-30
No. Not if they are on the same disk.

All patching, whether it is Windows or Linux brings risks.  Things that load new OSes, tend to touch partition tables. That is risky.  Usually things go fine, but not always.

---

### Post by yancek on 2018-03-30
Some major windows upgrades rewrite the partition table and Linux partitions are left out.  If you run sudo fdisk -l from an Ubuntu (or other Linux) on a Live DVD or flash drive, you will be able to see that the partitions are still there by sector size.  Testdisk should be able to recover the partition table.  If you are going to be using both Ubunt and window, it will be a lot less trouble to have each on a separate drive.

---

### Post by crip720 on 2018-03-30
Thank you for your answers.  They are what I thought, but thought I would ask just to make sure.

---

