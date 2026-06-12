---
title: "Splash Screen Disappears Part Way through Boot"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by jdennis_99 on 2008-05-18
I'm having a problem with my usplash, which is disappearing part-way through bootup, and only appears part-way through shutdown.

I have checked using Startup Manager to make sure that usplash is enabled. From other threads, I have managed to work out that its something to do with initramfs, and that I need to change the UUID on a swap partition (whatever that means ;-))

Basically, I've been doing the following:

sudo blkid

With the aim of getting the UUID for the swap partition. Only problem is, I don't appear to have a swap partition. This is results of sudo blkid:

/dev/sda1: UUID="F8CC4BDBCC4B9334" LABEL="Hard Drive" TYPE="ntfs" 
/dev/loop0: UUID="4b0184b0-71c3-485b-bb53-b79640ff81ea" TYPE="ext3" 
/dev/sdb1: UUID="6014A21E14A1F6E6" LABEL="Backup" TYPE="ntfs" 

I'm then told that I need to modify the "/usr/share/initramfs-tools/conf.d/resume" file so that the correct UUID is present on the swap line. However, I don't have that file - the conf.d directory is empty!

My PC:
Pentium 4 1.6GHz
nVidia GeForce MX400
512MB RAM
80GB HDD
Running Ubuntu 8.04 Hardy Heron LTS
Dual Boot with Windows XP SP2 (Ubuntu installed from inside Windows)

---

### Post by plucky on 2008-05-18
Try this in a terminal window ```
ls -l /dev/disk/by-uuid
``` That is a lower case L not a 1.
 and ```
cat /etc/fstab
``` and ```
sudo fdisk -l
``` That is lower case L not 1

Copy and paste to forums so that we can see how your swap partition is set up.

---

### Post by jdennis_99 on 2008-05-18
Plucky:

First of all, thank you for replying!

'ls -l /dev/disk/by-uuid' produces this:

lrwxrwxrwx 1 root root 10 2008-05-18 18:25 6014A21E14A1F6E6 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2008-05-18 19:25 F8CC4BDBCC4B9334 -> ../../sda1

'cat /etc/fstab' produces this:

/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

and 'sudo fdisk -l' produces:

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41b841b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9963    80027766    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS

Hope this helps!

---

### Post by plucky on 2008-05-18
jdennis_99,


Is Ubuntu installed with WUBI or VMware? I am not familiar with any of the outputs to those commands that I gave you,maybe someone who has installed Ubuntu in the same way that you have can help with your problem.

At least your thread will get bumped.

Good Luck

---

### Post by jdennis_99 on 2008-05-19
Plucky:

My Ubuntu is not installed via VMWare, but I'm not sure what WUBI is...

I installed Ubuntu from inside Windows XP. When you go into Add/Remove Programs in Windows XP, Ubuntu is listed as an option. Is that WUBI?

---

### Post by philinux on 2008-05-19
> **jdennis_99 said:**
> Plucky:

My Ubuntu is not installed via VMWare, but I'm not sure what WUBI is...

I installed Ubuntu from inside Windows XP. When you go into Add/Remove Programs in Windows XP, Ubuntu is listed as an option. Is that WUBI?

Could be wubi. [http://wubi-installer.org/](http://wubi-installer.org/)

There's some useful stuff on the site, faq' etc. I've never used it so hopefully someone will help you out.

---

### Post by jdennis_99 on 2008-05-19
Philinux:

Checked out the website - yes, I installed using WUBI. You can tell I'm a newbie, can't you ;-)

I checked the FAQs, but there's nothing in particular. In regards to 'technical support', it refers me... here! OK, it actually refers me to the WUBI section.

I had a look at the WUBI section, but there doesn't seem to be any mention of my problem. There was some talk about usplash not showing on boot, but I've checked my menu.lst file and 'splash' is tagged on the end of the kernel line. It does display, just not for very long ;-)

---

