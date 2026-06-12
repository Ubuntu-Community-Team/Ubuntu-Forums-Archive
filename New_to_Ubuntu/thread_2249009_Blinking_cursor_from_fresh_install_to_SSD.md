---
title: "Blinking cursor from fresh install to SSD"
date: 2014-10-18
forum: New to Ubuntu
---

### Post by nparquette on 2014-10-18
Hi there,

So I recently made the switch to Ubuntu from Windows 7, primarily because Windows 7 failed on me. I have a 250 gb SSD and 1tb HD. I installed Ubuntu to the SSD and when I booted up after the bio screen I just get a black screen with a blinking cursor. So I also installed Ubuntu to the HD, and when I boot up on that it works just fine. Any idea what the issue is? Obviously I'd like to boot from the SSD.

Nvidia 560 ti
Intel i7 920
Asus motherboard
SSD is Samsung
HD is Hitachi

Thanks in advance

---

### Post by sandyd on 2014-10-18
> **nparquette said:**
> Hi there,

So I recently made the switch to Ubuntu from Windows 7, primarily because Windows 7 failed on me. I have a 250 gb SSD and 1tb HD. I installed Ubuntu to the SSD and when I booted up after the bio screen I just get a black screen with a blinking cursor. So I also installed Ubuntu to the HD, and when I boot up on that it works just fine. Any idea what the issue is? Obviously I'd like to boot from the SSD.

Nvidia 560 ti
Intel i7 920
Asus motherboard
SSD is Samsung
HD is Hitachi

Thanks in advance

Have you checked if the SSD works in another computer or another drive bay?

Run ubuntu on the HDD, and post the output of
```

sudo fdisk -l
```
from the terminal to check.

---

### Post by nparquette on 2014-10-18
The SSD should be fine. It was working the day before Windows failed, and I have no issue reading or writing to the SSD when I'm in Ubuntu

This is the output

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002fc97

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1934667775   967332864   83  Linux
/dev/sda2      1934669822  1953523711     9426945    5  Extended
/dev/sda5      1934669824  1953523711     9426944   82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ef87b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048      499711      248832   83  Linux
/dev/sdb2          501758   488396799   243947521    5  Extended
/dev/sdb5          501760   488396799   243947520   8e  Linux LVM

Disk /dev/mapper/ubuntu--vg-root: 240.1 GB, 240144875520 bytes
255 heads, 63 sectors/track, 29195 cylinders, total 469032960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-swap_1: 9651 MB, 9651093504 bytes
255 heads, 63 sectors/track, 1173 cylinders, total 18849792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table

---

### Post by nparquette on 2014-10-18
For what's it's worth, GRUB is installed on a separate partition on the SSD than the rest of the install. Is there any way to make sure that doesn't happen when I install Ubuntu?

---

### Post by yancek on 2014-10-18
The SSD install is an LVM install which I believe requires a separate boot partition.  You need to choose that option as it definitely isn't a default.  If you use the Something Else option on the Installation Type window, you can select what partitions to create.  In your case, it seems you just want one partition for Ubuntu which you can do easily.

---

### Post by oldfred on 2014-10-19
While I do like to have Ubuntu installed on every drive, I do not like the default install on very large drive. Better to have / (root) of 20 or 25GB and separate /home. Or with multiple drives you may also want various data partitions. Best to plan partitions in advance as it can be more difficult to change later.

Is system also UEFI? 
New hardware is also both UEFI and BIOS. So you can often install either way. 
Ubuntu will install either UEFI or BIOS from a gpt partitioned drive, but only in BIOS boot mode from a MBR(msdos) partitioned drive. So often better to use gpt if you may want to try UEFI later. 
Windows only installs in BIOS mode from MBR or only in UEFI from gpt partitioned drives.

I consider LVM an advanced way to install. It is logical partitions overlaying physical partitions. It may offer some flexibility on changing partitions but adds complexity. 
       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)

---

### Post by nparquette on 2014-10-20
Thanks all for the help. It turned out installing everything on one partition fixed the issue.

---

### Post by snowmobiler on 2014-10-21
Did you set the sata settings on the SSD to AHCI prior to install? That is necessary for TRIM to work. My new SSD just arrived today and I am planning the same thing.

---

