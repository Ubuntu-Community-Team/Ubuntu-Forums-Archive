---
title: "Solid state and disk hard drive help"
date: 2013-08-25
forum: New to Ubuntu
---

### Post by Ben_Hylton on 2013-08-25
my laptop has two hard drives a 25gb soid state and a 750gb regular hard drive. i installed ubuntu onto the solid state drive so it would boot faster. i assumed ubuntu would be able to read both drives and be able to save onto both. but i went into details from the system settings window and it says i have 15 gb of disk space now this may be true for the solidsate drive but there is no way that is all the spave i have left on both hard drives. why isnt ubuntu reading both drives? and how do i get it to do so?

---

### Post by eternal243 on 2013-08-26
Okay, it seems that Ubuntu couldn't automount your drive, so lets try to see whats going on, first open terminal and write this command, then reply with the result.
```
sudo fstab -l
```

This will print out some information about your installed harddrives.

---

### Post by Werne on 2013-08-26
Ubuntu reads the space on the currently mounted partitions, if only the partitions from the SSD are currently accessed, it will read only the size/free space from those.

For example, I have two hard drives, one 250GB and one 320GB and I have an Ubuntu 12.04 (320GB HDD) and Debian 7.1 (250GB HDD) dual-boot. If I don't mount any of the Ubuntu partitions on Debian, my HDD space will be reported as 228GB with 117 free and if I do, it will report 521GB (228 on one HDD plus 293 on the second HDD). Same thing happens on Ubuntu if I don't mount Debian's partitions.

While the partitions on your 750GB HDD are detected (aka, they're visible in Nautilus/whatever file manager you use), they are not mounted. If you click on them in your file manager, they will be mounted and Ubuntu will detect the correct amount of total storage space.



Why that happens (a boring explanation) is because Linux doesn't see partitions as "drives" like Windows, so instead of accessing a partition as an independent file system like on WIndows, it gets mounted onto a folder and is shown as an extension of the root ( / ) file system. That's the reason you can have separate partitions for /home, /boot, /usr, /var, etc in your /etc/fstab. If it's not mounted, it's not being "read", therefore the total amount of storage space is not properly calculated since it calculates the size of the root partition with all it's extensions (mounted partitions).

---

### Post by 3rdalbum on 2013-08-26
Your hard disk should appear on the left bar of the screen. Click it to mount it and be able to use it.

You might have been better off installing Ubuntu to the SSD, with your /home on the hard disk. If you want to, you can still modify your /etc/fstab file to mount the hard disk as /home, then the contents of your home directory will automatically be the hard disk.

Google will help you find a howto for modifying your fstab.

---

### Post by varunendra on 2013-08-26
First off, Welcome to the Forums Ben_Hylton !!

Just rephrasing what has already been said -

Ubuntu (or Linux in general) does not mount all the available partitions. There is a good reason for this.

It only mounts root ("/", where it is installed) and partitions that are set to mount at startup in **/etc/fstab** file.

In order to see all available space, you'll have to first mount all the available partitions, which you'll have to do manually if they are not included in the /etc/fstab file.

Even when all the partitions are mounted, I believe, the System Settings > Details will show only the space available on the root partition, since it only shows the space on "system partition". To see the space available on other partitions, you may use "df -h" command (the other partitions must be mounted to be scanned by it).

---

