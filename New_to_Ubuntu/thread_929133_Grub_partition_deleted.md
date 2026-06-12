---
title: "Grub partition deleted"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by Jengajam2 on 2008-09-24
My sister was trying to format a usb flash drive, and somehow deleted the Grub partition. I do not have a Ubuntu live cd (and cannot download one), and I'm using a Slax live cd now. If someone could tell me how to boot lilo or grub on a usb flash drive, that would be apreciated.

---

### Post by sneeks on 2008-09-24
bit more info,is your os on the usb stick,or on the main pc?

---

### Post by caljohnsmith on 2008-09-24
On the Slax Live CD, does it have the grub shell command and the grub-install command:
```
which grub
which grub-install
```
If that returns the path to those commands, great, if not you would have to figure out how to install the Grub package to your Live CD so you can run those commands. And when you say your sister deleted your Grub partition, was Grub the only thing on that partition or was it maybe a /boot partition? It would be helpful if you could post:
```
fdisk -l

```
And be sure to run fdisk as root user.

---

### Post by Jengajam2 on 2008-09-24
heres what i got when i ran fdisk:
```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19131   153669726    7  HPFS/NTFS
/dev/sda2           19132       29273    81465615    5  Extended
/dev/sda3           29274       30401     9060660    c  W95 FAT32 (LBA)
/dev/sda5           28855       29273     3365586   82  Linux swap

```
and slax doesn't have grub on the live cd, is there a way to get grub (or lilo) to a usb flash drive?
EDIT:sry, it was formatted, not deleted.

---

### Post by caljohnsmith on 2008-09-24
What exactly are you ultimately trying to accomplish? From your fdisk output, was it your sda3 partition the one that your sister formatted? What OS was there before? Are you just trying to reinstall Grub so you can boot your Windows partition sda1, or are you eventually going to put a Linux OS on sda3? If you just want to be able to boot Windows in sda1, and if you have your Windows Install CD, just go to the recovery console and run the command:
```
fixmbr
```
And you should be able to boot Windows.

---

### Post by Jengajam2 on 2008-09-24
> **caljohnsmith said:**
> What exactly are you ultimately trying to accomplish? From your fdisk output, was it your sda3 partition the one that your sister formatted? What OS was there before? Are you just trying to reinstall Grub so you can boot your Windows partition sda1, or are you eventually going to put a Linux OS on sda3? If you just want to be able to boot Windows in sda1, and if you have your Windows Install CD, just go to the recovery console and run the command:
```
fixmbr
```
And you should be able to boot Windows.

whenever I boot my computer, Iget a Grub 17 error. So what I'm trying to do is get Grub working again; oh yeah, and it was sda 3. Like I said, is there any way to get Grub onto a usb pendrive, because i could just boot usb from the bios and that would work.

---

### Post by meierfra. on 2008-09-24
sda3 seems to big  for a Grub partition.

Did you dual boot Ubuntu and Windows before the incident?

According the fdisk where is also about 70GB of unallocated space on your hard drive. 
Do you know what kind partitions you had before the incident?

Are you trying to boot  into Windows and into  Ubuntu? Or just into Windows?

---

### Post by Jengajam2 on 2008-09-24
> **meierfra. said:**
> sda3 seems to big  for a Grub partition.

Did you dual boot Ubuntu and Windows before the incident?

According the fdisk where is also about 70GB of unallocated space on your hard drive. 
Do you know what kind partitions you had before the incident?

Are you trying to boot  into Windows and into  Ubuntu? Or just into Windows?
I had ubuntu with 2 different kernels, and 2 recovery modes for both kernels, windows Xp,and the 98/2000/xp recovery under "other operating systems"

---

### Post by meierfra. on 2008-09-24
If you follow caljohnsmith advice from post #5 you should be able to boot into Windows. 

Your Ubuntu partition is probably lost. Do you know how large your Ubuntu partition was?  If  you had some valuable data on your Ubuntu partition, you could try to rescue  it  with testdisk/photorec.
Did you have a separate home partition?

---

