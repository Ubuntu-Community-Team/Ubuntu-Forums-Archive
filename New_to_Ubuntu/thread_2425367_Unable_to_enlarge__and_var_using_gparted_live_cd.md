---
title: "Unable to enlarge / and /var using gparted live cd"
date: 2019-08-24
forum: New to Ubuntu
---

### Post by ugh25 on 2019-08-24
I installed ubuntu with default options, after plex media server built its thumbnail database the /var partition is out of space. Tried to enlarge the extended partition containing /var, but was still unable to enlarge /var itself.  Using Gparted live cd, confirmed no partitions including swap were busy/mounted. How do I enlarge the default partitions?

---

### Post by oldfred on 2019-08-24
Default install does not do a separate /var.
It now only has / by default & if UEFI an ESP. Swap is now a file, not a partition. Many do like to have /home or data partitions.

Post this:
sudo parted -l

Generally you cannot have partitions mounted to resize them, so have to use live installer which has gparted or use a gparted live ISO based flash drive.

---

### Post by yancek on 2019-08-25
Since the default install will not create a separate partition for /var, the user or person installing would have to create it.  So how big is it, posting the output of parted -l should tell us that.
Are you using the older Legacy/msdos partitioning rather than the more current GPT?  If you were using GPT there would be no Extended partition.  If you do in fact have an Extended partition, you would have to verify all the logical partitions were unmounted before trying to resize and you would need free/unallocated space available with the Extended.

---

### Post by TheFu on 2019-08-25
This is one of those times when using LVM would make resizing much easier.  I don't know about newer installs, but with 16.04, if LVM is selected during install, MBR partitioning with an extended + logical partitions is what got created by the installer.

**lsblk** would show the layout and if lvm is used. No need to boot from alternate media to get that data or the **sudo parted -l** information.

---

