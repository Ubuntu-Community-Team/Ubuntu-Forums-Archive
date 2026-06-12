---
title: "No Vista after Ubuntu install."
date: 2008-05-22
forum: New to Ubuntu
---

### Post by josegutter on 2008-05-22
I decided to try ubuntu by installing if on a 3rd drive on my pc. I currently have 2 80GB drives in raid 0 running vista and a separate 80GB drive to install Ubuntu. After installing ubuntu and getting an error when trying to boot to ubuntu drive (no OS found) I decided to disconnect the ubuntu drive and re-boot. when I rebooted expecting Vista from my raid I get a GRUB error. Even if I unplug the ubuntu drive. Did I damaged my vista raid? Can I fix this without re-installing vista? When I intalled ubuntu I selected sdi drive which I think was my 3rd drive.//

Thanks in advance

Jose

---

### Post by sharks on 2008-05-22
try these:
[www.sorgonet.com/linux/grubrestore/](www.sorgonet.com/linux/grubrestore/)

[www.ubuntuforums.org/archive/index.php/t-24113.html](www.ubuntuforums.org/archive/index.php/t-24113.html)

[www.ubuntuforums.org/showthread.php?t=224351](www.ubuntuforums.org/showthread.php?t=224351)

---

### Post by sharks on 2008-05-22
Restoring GRUB may help u.

---

### Post by Sef on 2008-05-22
Use a Live CD and open the terminal:

Applications > Accessories > Terminal

then type in this code:

```
sudo fdisk -l
``` small L

Then copy and paste the results here.

---

### Post by josegutter on 2008-05-23
SEF, I went ahead and booted the computer using the ubuntu 8.04 CD, opened a terminal and copied the list of drives:

 Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x24afb3a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19930   160078848    7  HPFS/NTFS

Disk /dev/sdb: 0 MB, 327680 bytes
255 heads, 63 sectors/track, 0 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb9add69a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9964    80035798+   7  HPFS/NTFS
root@ubuntu:/home/ubuntu#

---

### Post by josegutter on 2008-05-23
Can anyone take a look at this and help me?

Jose

---

### Post by lswest on 2008-05-23
looks fine to me, you can restore Vista's bootloader to make sure everything works before trying to re-install grub.  I have instructions in a how-to in the link on the 3rd line of my sig.

One quick question though, did that sudo fdisk -l output come from the system while the ubuntu disk was unplugged?

---

### Post by josegutter on 2008-05-23
Yes, the Ubuntu disk is unpluged. right now I am just worried about my vista raid being damaged.

---

### Post by josegutter on 2008-05-24
LSWEST, how can i restore the Vista bootloader, I read about a super grub disk. Is this the tool I need?

---

### Post by tom56 on 2008-05-24
You need the Vista Recovery CD. Take a look at my post here - [http://ubuntuforums.org/showpost.php?p=4925940&postcount=27](http://ubuntuforums.org/showpost.php?p=4925940&postcount=27). Ignore the bit about the partitions at the top - that was a response to an earlier post in that thread.

---

