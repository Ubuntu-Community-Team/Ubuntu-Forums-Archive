---
title: "Testdisk? I've broken my partition table, any help appreciated."
date: 2008-09-11
forum: New to Ubuntu
---

### Post by Rorke on 2008-09-11
[UNSOLVED - I had to reinstall]
I still have my data, byt I can't mount the partitions.

Device Boot Start End Blocks Id System
/dev/sda1 * 1 3230 25944943+ 7 HPFS/NTFS
/dev/sda2 3231 30401 218251026 f W95 Ext'd (LBA)
/dev/sda5 3232 21295 145099080 83 Linux
/dev/sda6 28889 29645 6080571 82 Linux swap / Solaris
/dev/sda7 29646 30401 6072538+ 82 Linux swap / Solaris
__________________
I'm trying to use testdisk, but the tutorial doesn't describe my situation well.
I get no luck with GParted and I've tried Super Boot Grub - it worked once, but now I get Error 17 - unable to mount.
From Live Disk, I can acess all my files.
I don't know how to do simple things like mount a volume from a terminal (although I've seen it done).
I don't know which of the 2 swap file partitions is obsolete.
Every time I press a key in testdisk, it seems to lose the table that it just spent an hour building up!
Any help? Much appreciated. I currently can't boot anything except Live CD.

Thanks.
Simon

---

### Post by Rorke on 2008-09-11
Also, I don't know why I now seem to have W95 listed in that table. Some mistake using testdisk I guess!

---

### Post by gvartser on 2008-09-11
Here is an example on how to mount a disk manually from a terminal:

Mounting disk (Partition) "/dev/sdb4" into "/mnt/test_disk"

1) Open up an Terminal (shell)
2) Create an empty directory
   ```
sudo mkdir /mnt/test_disk
```
3) Mount the device into the directory created in step 2.
   ```
sudo mount /dev/sdb4 /mnt/test_disk
```
4) Done!

GR,
/g

---

### Post by caljohnsmith on 2008-09-11
> **Rorke said:**
> I still have my data, byt I can't mount the partitions.

Device Boot Start End Blocks Id System
/dev/sda1 * 1 3230 25944943+ 7 HPFS/NTFS
/dev/sda2 3231 30401 218251026 f W95 Ext'd (LBA)
/dev/sda5 3232 [COLOR="Red"]21295[/COLOR] 145099080 83 Linux
/dev/sda6 [COLOR="Red"]28889[/COLOR] 29645 6080571 82 Linux swap / Solaris
/dev/sda7 29646 30401 6072538+ 82 Linux swap / Solaris
__________________
I'm trying to use testdisk, but the tutorial doesn't describe my situation well.
I get no luck with GParted and I've tried Super Boot Grub - it worked once, but now I get Error 17 - unable to mount.
[COLOR="RoyalBlue"]From Live Disk, I can acess all my files.[/COLOR]
I don't know how to do simple things like mount a volume from a terminal (although I've seen it done).
I don't know which of the 2 swap file partitions is obsolete.
Every time I press a key in testdisk, it seems to lose the table that it just spent an hour building up!
Any help? Much appreciated. I currently can't boot anything except Live CD.

Thanks.
Simon
First thing I noticed is that you have a large chunk of your HDD that isn't allocated to any of your partitions; it's the space between sda5 and sda6. That in itself does not mean you have a corrupt partition table though--what problems have you had that leads you to believe your partition table is broken? Also, sda2 is an "extended" partition, meaning it is merely a container for all your logical partitions, or sda5, sda6, and sda7. If you use a Linux partition tool like gparted, it will leave a linux signature on the extended partition, but if you use a Windows-based partition editor, it usually leaves a Windows signature as the partition type; but it doesn't matter since both are extended partitions and that is all that matters. 

Since you say you can access your files, if you look in your /etc/fstab file on your Ubuntu partition sda5, you should see a line in there for your swap partition, and that will tell you which swap partition you are using. Once you know that you can delete the other one.

---

### Post by Rorke on 2008-09-11
After I posted this, I'd thought I'd got the hang of testdisk, and tried settting the partition table.
Unfortunately I don't have acess to any of the files any more :-(
Most of the important stuff is backed up to an external hard drive, but it did take months to get the OS working and running properly.

History:
Install Ubuntu.
Screw it up totally, but get Virtual Box running XP.
Re-size partition and re-install Ubuntu again in a new partition.
Have to re-boot every time I want to run VB with XP on it.
Buy a new PC game that's XP only.
Try to re-size the partitions so that I can install XP for real in a larger partition size, destroying the first Ubuntu.
Power failure half way through (Chinese Toaster!)
Spend several days panicking with Grub Super Boot and GParted. Finally find testdisk.
It seems like I've made the wrong Deleted partition the Undeleted real one.

---

### Post by Rorke on 2008-09-13
Hi, It looks like I'm using BOTH swap areas!!
I've got back to the condition of data available, but Error 17 on booting,.
I get this after I mount my filesystem to the LiveCD
:
ubuntu@ubuntu:/mnt/test_disk$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000deca2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3230    25944943+   7  HPFS/NTFS
/dev/sda2            3232       21295   145099080   83  Linux
/dev/sda3           28889       30401    12153172+   f  W95 Ext'd (LBA)
/dev/sda5           28889       29645     6080571   82  Linux swap / Solaris
/dev/sda6           29646       30401     6072538+  82  Linux swap / Solaris
ubuntu@ubuntu:/mnt/test_disk$ more /etc/fstab
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
/dev/sda6 swap swap defaults 0 0
ubuntu@ubuntu:/mnt/test_disk$

---

### Post by bumanie on 2008-09-13
You should not need testdisk to fix grub error 17. Check out this stuff.
[Follow this]("http://ubuntuforums.org/showthread.php?t=224351") to reinstall grub from the live ubuntu cd or get super grub disk. Could also be that your bios has got the hard drive order wrong since you changed your disks around - check your bios settings too. [Check here too]("http://users.bigpond.net.au/hermanzone/p15.htm"), about 2/3 down the page is heaps of info. on grub errors + possible fixes

---

