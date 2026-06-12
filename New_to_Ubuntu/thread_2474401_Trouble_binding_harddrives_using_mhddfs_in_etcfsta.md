---
title: "Trouble binding harddrives using mhddfs in /etc/fstab"
date: 2022-04-28
forum: New to Ubuntu
---

### Post by renekat14 on 2022-04-28
Hello Amazing Ubuntu community,
I'm fairly new to this arena and I've gotten myself in a pickle. 

I have two 4TB harddrives installed on my computer; however, only one (/dev/sda2) was initially mounted. 
Following [this tutorial]("https://techguides.yt/guides/how-to-partition-format-and-auto-mount-disk-on-ubuntu-20-04/#4_Mount_disks_on_Ubuntu"), I tried to bind my two hard drives to my home directory so that I had "one" 8TB directory. 
I created two new mount points: /mnt/ext1 and /mnt/ext2. Successfully reformatted /dev/sdb1 and mounted it at /mnt/ext2. However, /dev/sda2 was the HD I had been using up until this point (4TB HD full) and it was mounted to / . When i tried to 'umount /dev/sda2' I got the error that it was in use. I searched online and found an answer that if I restarted my computer, the HD would no longer be in use and I could unmount it. 
So, you can imagine what happened, I restarted my computer with the /etc/fstab file already configured for the new mounts and binding. And I've been stuck with Boot Failed similar to [this post]("https://unix.stackexchange.com/questions/185026/how-to-edit-etc-fstab-when-system-boots-to-read-only-file-system"). 

Following some [advice]("https://askubuntu.com/questions/822887/boot-failed-failed-to-start-remount-root-and-kernel-file-systems"), I've been able to install Ubuntu on the /dev/sdb1 drive and get access to all my files. But now I have two Ubuntu installations with two different computer names etc. I want to use the original one because I already have a static IP address that I can ssh into. Where do I go from here?

Here is the **Boot-Info Summary: [https://paste.ubuntu.com/p/f3QTDdXxWy/](https://paste.ubuntu.com/p/f3QTDdXxWy/)**

The goal is to successfully get the two 4TB HDs binded on the / directory using my original Ubuntu installation. Thank you for any and all advice.
-René

---

### Post by Tadaen_Sylvermane on 2022-04-28
[https://github.com/trapexit/mhddfs](https://github.com/trapexit/mhddfs)

Mergerfs is easier as well. That being said it can create unforseen problems. I recently switched my media storage from a pool to a raid 1 with lvm.

---

### Post by renekat14 on 2022-05-04
Hi Tadaen,
I appreciate your reply. I'm a biologist trying to set up this new server and I'm at the point where I have installed Ubuntu twice and seemingly have two separate "computers" (@fch and @xavier). The new install I can access all files fine but don't know how to access my software installs (i.e. conda environments). On this new computer, it says conda is not installed. I don't want to reinstall all my software, as it's on the computer, I just don't know how to point to it (update $PATH maybe??). 

I have completely given up on binding these hard drives. One of the SSD is full of data, is that why the binding wouldn't work? Is it only possible to bind SSD that are empty?  

I'd like to only have one computer, ideally the original one which I have a static IP address for and can ssh into (@fch). Where do I go from here? Do the fstab files have to be the same for each computer? For example, on the @xavier computer the mount points for each SSD are different than the @fch computer. Is that okay, or should they be the same? Sorry if this is such a basic question, but I'm confused why the @fch computer is not loading at all.

I need some serious Ubuntu IT support but none of my IT guys are familiar with Ubuntu, only Windows. So, I appreciate any help from the community on this one.

All the Best,
René

---

### Post by Tadaen_Sylvermane on 2022-05-04
Ok. Direct root mountpoint binding doesn't work. This software is meant for data storage. Not OS. If you have backups your ideal solution would be to blast the drives and make a single logical volume across the drives. Beware if one drive dies you lose both. Not much different than a raid 0 except without the io increase. This is a case of wrong software for the task.

Your fix is to do it right from the start.

Make a backup of what you can.
From a live boot wipe both drives partition structures then create gpt partitions. Depending on UEFI / MBR boot you will need a boot partition. In gdisk these options are ef00 and ef02 respectively. Then use the rest of the space for a single partition on each drive.
Create a physical volume the make a volume group one just one of the drives. Put your logical volumes here. I'm thinking at least a root and swap. How you want to keep the rest is up to you. Once the system is up and running it is trivial to create the lvm partition on the other drive and just extend and resize. Problem solved. Again keep in mind that this method means if one disk dies they both die (as far as data is concerned). Backups are essential.

---

### Post by renekat14 on 2022-05-04
Hi Tadaen, Thanks again for your guidance. 
I have all my data backed up thankfully. 
Is there an online tutorial I could follow? I'm just not familiar with most of the terminology in your instructions. :?

---

### Post by Tadaen_Sylvermane on 2022-05-04
I'm not sure of a guide specifically. Command line gdisk should be simple enough to figure out, just make sure you use it on the proper disk spot (/dev/sda instead of /dev/sda1 - sda just example). For lvm [https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm) is my go to if I forget something. Also the Arch wiki is amazing regardless of distro, possibly the best wiki for all things linux. Is a fairly simple process really. Just do one disk for the initial install then once it's booted extend the vg to the next disk. Then you can resize the lvs as needed.

---

### Post by renekat14 on 2022-05-04
Great, thanks so much for those references! I appreciate your advice.

---

