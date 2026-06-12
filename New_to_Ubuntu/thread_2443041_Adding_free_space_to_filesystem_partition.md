---
title: "Adding free space to filesystem partition"
date: 2020-05-10
forum: New to Ubuntu
---

### Post by notone2 on 2020-05-10
Hello,

is it possible to add these 6gb of free space to filesystem partition? I tried resizing it but nothing happens. Thank you.

[IMG]https://imgur.com/HpCyJm7.png[/IMG]

---

### Post by crip720 on 2020-05-10
Needs to be done from separate Linux OS, like the USB you install from.  Cannot be done when mounted.  Boot from USB and should not have problems adding to home.  Unless /(file system) is near full, would leave a lone,  30GBs usually more than enough.  If getting full can delete some older kernels.  Root partitions can be touchy if size is  changed or moved.  It is better in your case since free space is next and to the right.  Delete free space and re-size partition one, partition 5 should expand with it.  Gparted might better to use from USB.

---

### Post by notone2 on 2020-05-11
Thanks a lot, can you recommend what usb os would be easiest to install, and how to delete old kernels, as i dont have enough space on it to install new ubuntu os update. thank you.

---

### Post by oldfred on 2020-05-11
May be better to backup and totally reinstall.
What version are you running?

I normally suggest 25 to 30GB for / (root) when using separate /home and/or data partitions. 
So what is in / using all the space?
Only very old versions of Ubuntu kept old kernels, unless you did not houseclean before & upgraded, so you have many very old kernels that now are difficult to delete.

It also is strange to have / in extended partition with the old MBR partitioning, but than can work.
New systems also now are UEFI with gpt partitioning. How old is your system?

---

### Post by TheFu on 2020-05-11
Partition 5 is completely contained inside Partition 1.  I don't think P1 can be modified as long as P5 exists.
It really would be easier to see all of this using the output from **sudo fdisk -l**  Then we'd see the partition table.
Add in the output from **df -hT -x squashfs -x tmpfs -x devtmpfs** and we'd have a good picture.

30G is huge for /, though I suppose if you install 10 large snap packages, then that could account for all the wasted storage.  Before snaps existed, I had entire systems that fit, including HOME and all my web-app development files, in a 17G partition.

---

### Post by Impavidus on 2020-05-11
You can modify partition 1 as long as partition 5 doesn't have to be moved to remain inside it. So in this case, partition 1 can be extended. The best live usb to use would be the same one as you used to install Ubuntu.

But your problem is not that your partition is too small, it's that you collected to many files, or too large files. With a separate /home partition (I assume that's that big partition 3), a 30 GB root partition should be plenty. You already collected 15GB more than expected, so it won't take that long to fill your additional 6GB. You don't need a live disk for cleanup, only to resize the partition – or to fix things if severly broken, but that doesn't appear to be the case here.

Find out which directories take all that storage. There is the disk usage analyser, which is not as intuitive as you might think, or you can use the command line:```
sudo du -kx -d1 / | sort -nr
```Dig down until you find what's taking all that space, then we can help you clean it up.

---

