---
title: "remove partitions"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by jon zendatta on 2008-05-08
hell0
somehow i have managed to get an additional partition whilst using gparted..
i cannot remove partition or re-size to unallocated hard drive because it has a padlock symbol & obviously has permissions. what would the bash code to remove it please.
cheers

---

### Post by zach382 on 2008-05-08
Sounds like you're partition might be mounted. Try unmounting it first. ```
sudo umount /dev/sda1
``` or sda2 or whatever partition it is. Use ```
sudo fdisk -l
``` to get a list of your partitions. Then make sure you are running gparted as administrator. If you really wanna make sure Alt+f2 then gksudo gparted. Hope that helps.

---

### Post by Tatty on 2008-05-08
If this partition is on your primary hard drive then you will need to boot into a live CD as you cannot alter the partitions on a mounted drive.

the live CD will probably use the swap partition on your hard drive, so you will need to right click on the swap partition and choose "swapoff"

---

### Post by lgastmans on 2008-05-08
a bootable cd with gparted on it worked magic for me a short while ago. i moved, resized partitions without problems.

---

### Post by kirios on 2008-05-09
Run **sudo fdisk -l** and **mount** in a terminal (Applications > Accessories > Terminal), then copy-and-paste the output of both commands into your next post. 

> **jon zendatta said:**
> hell0
somehow i have managed to get an additional partition whilst using gparted..
i cannot remove partition or re-size to unallocated hard drive because it has a padlock symbol & obviously has permissions. what would the bash code to remove it please.
cheers

---

### Post by jon zendatta on 2008-05-09
on@jon-laptop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1ba117c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sda2            2612        3276     5341612+  83  Linux
/dev/sda3            8601        9729     9068692+   5  Extended
/dev/sda5            9545        9729     1485981   82  Linux swap / Solaris
jon@jon-laptop:~$ 
/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

---

### Post by jon zendatta on 2008-05-09
yes so my aim is to just have a dual boot as i have 41Gib unallocated that i just want to increase the linux partition.:KS

---

### Post by logos34 on 2008-05-09
yeah, you should be able to boot the live cd and use gparted to grow ubuntu root sda2 to the left into the unallocated space.  It can take a long time to resize the left boundary, though (it has to copy and move all the files over)

---

### Post by kirios on 2008-05-09
> **jon zendatta said:**
> yes so my aim is to just have a dual boot as i have 41Gib unallocated that i just want to increase the linux partition.:KS

Yes, you have around 40GB free space between the Ubuntu / partition on sda2 and the extended partition (sda3). Interestingly, you also have another 7GB free space on the extended partition immediately before swap on sda5. You could try booting from the gparted live CD (or even the Ubuntu live CD) and resizing the / partition on sda2. It would be simpler to leave the swap partition alone. 

> **jon zendatta said:**
> hell0
somehow i have managed to get an additional partition whilst using gparted..
i cannot remove partition or re-size to unallocated hard drive because it has a padlock symbol & obviously has permissions. what would the bash code to remove it please.
cheers

I think you may be referring to the swap partition (sda5).This functions like pagefile.sys on a Windows system and is required for Ubuntu to run properly.

---

### Post by kwacka on 2008-05-09
An alternative might be to use gparted to create a fourth (and final) partition in the space. 

As you are dual-booting, if you make this a FAT32 it can be read by both systems.  Could be NTFS, but I'd rather go with FAT32.

if you want to increase the space available to Linux, I'd suggest making this a independent /Home partition.

---

