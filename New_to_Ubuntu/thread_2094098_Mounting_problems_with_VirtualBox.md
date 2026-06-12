---
title: "Mounting problems with VirtualBox"
date: 2012-12-12
forum: New to Ubuntu
---

### Post by Amjad88 on 2012-12-12
I've recently installed VirtualBox and have installed an XP machine through it. The problem is that the Virtual Image is on an NTFS partition which requires mounting before VirtualBox can access it. I've set up a udisks command at start-up to mount the partition but VirtualBox still won't access it. Strangely enough, when I unmount the partition and then remount it again using nautilus, everything works fine. I don't really understand the difference between mounting the partition though nautilus and mounting it through a udisks command, specially considering the inconvenience of the former. Any ideas?

Thank you

---

### Post by PinkFloyd102489 on 2012-12-12
Why not just put an entry in */etc/fstab* to mount the partition on startup?

---

### Post by N00b-un-2 on 2012-12-12
+1 for /etc/fstab

It sounds to me like the disk is not actually being mounted with 'udisk', at least not to a valid mount point that is accessible by VirtualBox.
To add the ntfs partition to your fstab (the proper way to mount disks at boot) open a terminal with su privileges
```
$ sudo -s 
```
Then you first need to determine where the disk is located with
```
# fdisk -l
```
once you've determined the device name of the NTFS partition or disk in question -- eg; /dev/sda3 -- you will need to edit your /etc/fstab
```
# nano /etc/fstab
```
and add a line that looks something like this
```
/dev/sda3   /windows   ntfs   defaults,umask=007,gid=46 0 0
```

hit ctrl+x to save and exit.  The next time you boot up, your ntfs partition will be mounted properly.
* NOTE: the mount point specified, in this case '/windows', must exist.  if it does not, create it now.  eg;
```
# mkdir /windows
```

---

### Post by Amjad88 on 2012-12-13
Thank you both.

Indeed the problem was simply the mount point. Nautilus sets up the mount point at /media/user/<Device UUID> while the udisks mount command mounts it to /<Device_UUID>, so the simple solution was to add a line to fstab with the correct mount point and now it works like a charm.

Thanks again for the help.

---

