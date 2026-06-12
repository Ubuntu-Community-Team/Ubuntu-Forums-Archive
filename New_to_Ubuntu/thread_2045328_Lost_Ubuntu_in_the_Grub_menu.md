---
title: "Lost Ubuntu in the Grub menu"
date: 2012-08-21
forum: New to Ubuntu
---

### Post by ub07 on 2012-08-21
I installed another OS along side Ubuntu 12.04, and now Ubuntu disappeared from Grub. I know Ubuntu is still there because I can mount the file system from the other OS. But I want to be able to boot into Ubuntu (it's my primary OS). 

I used a live Kubuntu CD to effect a repair (I can't believe that the Ubuntu Live CD doesn't have the rescue option), and I got Ubuntu back but then I lost the other OS. I reinstalled the other OS and lost Ubuntu again. But, as I said, it is still there because I can see it.

How do I add Ubuntu back into the Grub menu?

---

### Post by thomsebastin on 2012-08-21
> **ub07 said:**
> I installed another OS along side Ubuntu 12.04, and now Ubuntu disappeared from Grub. I know Ubuntu is still there because I can mount the file system from the other OS. But I want to be able to boot into Ubuntu (it's my primary OS). 

I used a live Kubuntu CD to effect a repair (I can't believe that the Ubuntu Live CD doesn't have the rescue option), and I got Ubuntu back but then I lost the other OS. I reinstalled the other OS and lost Ubuntu again. But, as I said, it is still there because I can see it.

How do I add Ubuntu back into the Grub menu?

Might need to update GRUB by doing: 
```
sudo update-grub

```

---

### Post by drmrgd on 2012-08-21
If running update grub does not fix it, it might be worthwhile to run Boot Repair (or at the very least post the results of the Boot Info Summary here so that we can see how the system is set up).  You can find some documentation and links to the very excellent Boot Repair tool here:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by NikTh on 2012-08-21
Hi , 
can you please tell us what is this "other OS" ? 
Thanks

---

### Post by ub07 on 2012-08-21
> **NikTh said:**
> Hi , 
can you please tell us what is this "other OS" ? 
Thanks

The other OS is Scientific Linux.

---

### Post by ub07 on 2012-08-21
> **drmrgd said:**
> If running update grub does not fix it, it might be worthwhile to run Boot Repair (or at the very least post the results of the Boot Info Summary here so that we can see how the system is set up).  You can find some documentation and links to the very excellent Boot Repair tool here:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Thanks. I will try running boot repair, but I think boot repair is what the rescue disk did. I'll try it again.

---

### Post by ub07 on 2012-08-21
> **thomsebastin said:**
> Might need to update GRUB by doing: 
```
sudo update-grub

```

Thanks. Does the update-grub re-detect the operating systems on the disk?

---

### Post by ub07 on 2012-08-21
Does Grub have a configuration file that I can edit to include the other OS?

---

### Post by cortman on 2012-08-21
> **ub07 said:**
> Does Grub have a configuration file that I can edit to include the other OS?

There's grub.cfg, but that gets overwritten every time you run update-grub- did update-grub not work?

---

### Post by kemtnbkr on 2012-08-21
> **ub07 said:**
> Thanks. Does the update-grub re-detect the operating systems on the disk?

Yes.  It scans your /boot directory for bootable kernels, plus memtest.  It also scans other stuff, ex. it will find windows 7, I don't know the exact specifics of what all it scans.

---

### Post by drmrgd on 2012-08-21
If update Grub did not work, there's probably something else going on.  It should detect any OS that has a properly configured boot loader on the system.  Editing grub.cfg isn't the best way to manually enter the information .  Better would be to use the custom entries in /etc/grub.d/ and edit those.  When you run 'update grub' it'll detect your changes in those files.

I think we need to see a report from the Bootinfo Script that is a part of the Boot Repair package to assess how your system is configured currently.

---

### Post by ub07 on 2012-08-21
Ok, I'm going to switch computers and run update-grub.

---

### Post by NikTh on 2012-08-21
> **ub07 said:**
> The other OS is Scientific Linux.

Hi , 
Ok , Scientific Linux .. fedora-based I think. 

Try something.. 
boot from ubuntu regular install and first mount the partition that includes Scientific Linux and then run update-grub. 
e.g: 
If Scientific Linux installed on /dev/sda2 
```
sudo mount /dev/sda2 /mnt
sudo update-grub
```give here the result of last command. 

Put the results inside ```
 tags . 
[noparse][code]the results here
```[/noparse]
Thanks

---

### Post by ub07 on 2012-08-21
Thanks, NikTh, but I got it working (partially). sudo update-grub did not work, but sudo boot-repair did. Now I can boot into everything from grub.

However, I have another problem. Ubuntu (sda1) thinks that swap is not available even though sda2 is a swap partition. I can see this by booting into my Kubuntu live CD and using the KDE partition manager. I really need swap because this computer only has 2 Gb of RAM.

How can I point Ubuntu to the swap partition?

---

### Post by NikTh on 2012-08-21
> **ub07 said:**
> 
However, I have another problem. Ubuntu (sda1) thinks that swap is not available even though sda2 is a swap partition. I can see this by booting into my Kubuntu live CD and using the KDE partition manager. I really need swap because this computer only has 2 Gb of RAM.

How can I point Ubuntu to the swap partition?

Hi , 
boot to Ubuntu , login , open a terminal and 
```
sudo blkid
```you will see the UUID of swap.. 
then go to /etc/fstab 
```
gksudo gedit /etc/fstab
``` and replace the UUID of swap with the UUID from blkid command (result). 

Then do in terminal 
```
sudo swapon -a 
```and give the results of 
```
free -m
```****Be careful with fstab** , if you don't understand something (cuz my English are in low level)  post here the results of these commands**** **
```
sudo blkid 
cat /etc/fstab
```Thanks

---

### Post by ub07 on 2012-08-21
NikTh, you are a genius! Looks like it is working:


```
jeo@jeo-Satellite-L355D:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1758        768        989          0        114        348
-/+ buffers/cache:        305       1452
Swap:         3004          0       3004

```

```
jeo@jeo-Satellite-L355D:~$ sudo blkid
/dev/sda1: UUID="4e02595d-9e27-48b9-939d-ca49d42e95fe" TYPE="ext4" 
/dev/sda2: UUID="09cb7f0f-9e88-4c34-b5f4-90247423e9ca" TYPE="swap" 
/dev/sda3: UUID="7e3e7d4c-96da-42d6-b9c4-19423f0550e2" TYPE="ext4" 
/dev/sda5: UUID="xx0yxw-QA1L-1s6Q-CP03-aflc-LKNp-wcAj1l" TYPE="LVM2_member" 
/dev/mapper/vg_brainiac-lv_root: UUID="0c40ffd0-f8cd-4e34-9394-21738ad89ff0" TYPE="ext4" 
/dev/mapper/vg_brainiac-lv_home: UUID="393e092c-c9f1-4f21-a00f-76b7507f8caf" TYPE="ext4" 
/dev/mapper/vg_brainiac-lv_swap: UUID="cc9f2588-2f67-4954-92fb-ff005b3b50ed" TYPE="swap" 
```


```
jeo@jeo-Satellite-L355D:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=4e02595d-9e27-48b9-939d-ca49d42e95fe /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
# swap moved to /dev/sda2 (8-21-12)
UUID=09cb7f0f-9e88-4c34-b5f4-90247423e9ca none            swap    sw              0       0

```


Thanks so very much!

---

### Post by NikTh on 2012-08-21
Hi ,
do not thank me , swap is not so important as grub. Thank _[Yannbuntu]("http://ubuntuforums.org/member.php?u=485559") _, the developer of boot-repair who makes our lifes (in Ubuntu) easier. 

I will post my complain here now :P 

I really do not understand why this excellent program is not in the Official Ubuntu repos. (except if developer don't want to...then OK). 
Thanks

---

