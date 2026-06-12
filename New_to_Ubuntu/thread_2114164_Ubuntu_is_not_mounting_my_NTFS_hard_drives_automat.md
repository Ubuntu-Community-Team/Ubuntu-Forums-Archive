---
title: "Ubuntu is not mounting my NTFS hard drives automaticaly"
date: 2013-02-09
forum: New to Ubuntu
---

### Post by whitefish10 on 2013-02-09
Hi guys, I have two 500 GB that got all my files from windows. I cant understand why Ubuntu is not mounting them automatically. 

This is the result of the fdisk -l

med@med-PH67A-UD3-B3:~$ sudo fdisk -l
[sudo] password for med: 

Disk /dev/sda: 500.1 GB, 500106780160 bytes
240 heads, 63 sectors/track, 64601 cylinders, total 976771055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe80015da

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   976766975   488382464    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8c521881

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   976769023   488383488    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x47f2995e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048    15624191     7811072   82  Linux swap / Solaris
/dev/sdc2   *    15624192   113281023    48828416   83  Linux
/dev/sdc3       113281024  2930276351  1408497664   83  Linux

Disk /dev/mapper/isw_echficidac_Server: 500.1 GB, 500103643136 bytes
255 heads, 63 sectors/track, 60800 cylinders, total 976764928 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8c521881

                            Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_echficidac_Server1            2048   976769023   488383488    7  HPFS/NTFS/exFAT

Since I am new to linux. I not sure what to do since I may mess my hard drives and loss my data!!!

Please advise me. And thanks.

---

### Post by Impavidus on 2013-02-09
You should be able to mount them by clicking in your file manager (nautilus, I presume). I wouldn't really call that automatic. If you want to mount them automatically when you boot you'll have to add them to your /etc/fstab. Partitions containing just data are fine to mount read-write, the windows system may be saver if you mount that partition read-only.

See [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) for some explanation and examples.

---

### Post by Mark Phelps on 2013-02-09
From the "dev/mapper" information, my guess (since I'm not an expert in this) is that you have some kind of RAID setup -- which will prevent simply mounting the drives.

---

### Post by coetzeec2380 on 2013-02-09
hi 

this is what i did and maybe can help you. you would need root accces to do most of the configuration. your on the right track so far with fdisk -l, this will show you what the drives are and the file system.

go in a terminal environment 
now remember the one you want focus on ie sda1

type 

sudo nano -w /etc/fstab .......this will bring up a text editor opening the fstab file which you have to edit for the automount.

in the file add something like this

/dev/sda1 /media/drive1 ntfs-3g defaults  ....... this will mount the drive partition sda1 under media/drive1

save and exit the file

now you still need to create the mountpoint
type 
sudo mkdir -p /media/drive1  
sudo chmod -R 0777 /media/drive1

if all is typed correctly and under root rights you should reboot for effects t take hold
type 
sudo reboot


hope it helps
regards

---

### Post by whitefish10 on 2013-02-09
> **Mark Phelps said:**
> From the "dev/mapper" information, my guess (since I'm not an expert in this) is that you have some kind of RAID setup -- which will prevent simply mounting the drives.

It is true, I was having these two hard drives under raid 1 in a different machine. But the motherboard got issues and I moved it and formatted before using them. Maybe that's way it is not working properly in my machine.

Please advise me on what to do.

Thanks.

---

### Post by Prince Valiant on 2013-02-09
Hey!  

I always thought that the fdisk method was too complex.  Pysdm is way simpler.  

sudo apt-get install pysdm

Cheers!
Val

---

### Post by coffeecat on 2013-02-09
> **Prince Valiant said:**
> 
I always thought that the fdisk method was too complex.  Pysdm is way simpler.  

sudo apt-get install pysdm


Which will fail in 12.10 because it has been removed from the repository. And not before time - pysdm has been unmaintained for years and can cause problems. Simple advice: don't use it; don't recommend it!

---

### Post by whitefish10 on 2013-02-11
> **coetzeec2380 said:**
> hi 

this is what i did and maybe can help you. you would need root accces to do most of the configuration. your on the right track so far with fdisk -l, this will show you what the drives are and the file system.

go in a terminal environment 
now remember the one you want focus on ie sda1

type 

sudo nano -w /etc/fstab .......this will bring up a text editor opening the fstab file which you have to edit for the automount.

in the file add something like this

/dev/sda1 /media/drive1 ntfs-3g defaults  ....... this will mount the drive partition sda1 under media/drive1

save and exit the file

now you still need to create the mountpoint
type 
sudo mkdir -p /media/drive1  
sudo chmod -R 0777 /media/drive1

if all is typed correctly and under root rights you should reboot for effects t take hold
type 
sudo reboot


hope it helps
regards

I tried to mount the hard drives as with the steps above but during the restart. Ubuntu boot said that the drives are unavailabe and I had to skip to continue.

As I said before the hard drives were in RAID 1 in a diffrent machine, But I pulled them and formatted them in Windows as NTFS before using them. if it is still in raid them I need to do something to mount raid!!! 

please advise me. and thank you.

---

### Post by black3agl3 on 2013-02-11
Try posting a copy of your /etc/fstab file

```
cat /etc/fstab
```

---

### Post by whitefish10 on 2013-02-11
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdc2 during installation
UUID=2a73a02e-b595-4b0a-99a1-43a0eb614064 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdc3 during installation
UUID=683087a7-5e4a-4b14-bbc3-065fd5510b28 /home           ext4    defaults        0       2
# swap was on /dev/sdc1 during installation
UUID=233517b0-a65b-4668-8863-73ffd9a9e9b3 none            swap    sw              0       0

Also

sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500106780160 bytes
240 heads, 63 sectors/track, 64601 cylinders, total 976771055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe80015da

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   976766975   488382464    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8c521881

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   976769023   488383488    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x47f2995e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048    15624191     7811072   82  Linux swap / Solaris
/dev/sdc2   *    15624192   113281023    48828416   83  Linux
/dev/sdc3       113281024  2930276351  1408497664   83  Linux

Disk /dev/mapper/isw_echficidac_Server: 500.1 GB, 500103643136 bytes
255 heads, 63 sectors/track, 60800 cylinders, total 976764928 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8c521881

                            Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_echficidac_Server1            2048   976769023   488383488    7  HPFS/NTFS/exFAT

Disk /dev/sde: 31.2 GB, 31201427456 bytes
11 heads, 4 sectors/track, 1385006 cylinders, total 60940288 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04030201

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               6    60940286    30470140+   7  HPFS/NTFS/exFAT

---

### Post by Morbius1 on 2013-02-11
And if you going to be posting some stuff anyway please post the output of this command as well:
```
sudo blkid -c /dev/null
```

---

### Post by whitefish10 on 2013-02-11
sudo blkid -c /dev/null
/dev/sda: TYPE="isw_raid_member" 
/dev/sdb: TYPE="isw_raid_member" 
/dev/sdc1: UUID="233517b0-a65b-4668-8863-73ffd9a9e9b3" TYPE="swap" 
/dev/sdc2: UUID="2a73a02e-b595-4b0a-99a1-43a0eb614064" TYPE="ext4" 
/dev/sdc3: UUID="683087a7-5e4a-4b14-bbc3-065fd5510b28" TYPE="ext4"

---

### Post by collisionystm on 2013-02-11
> **Morbius1 said:**
> And if you going to be posting some stuff anyway please post the output of this command as well:
```
sudo blkid -c /dev/null
```

Just out of curiosity, why would you instruct OP to use "blkid -c /dev/null" instead of just

sudo blkid

---

### Post by Morbius1 on 2013-02-11
[COLOR=Blue]Please do not do this until we get more feedback [/COLOR]from the other members on this topic because it's been too long ago that I did this last so it's best to get some feedback.

If I understand your posts these used to be raid but they are not set up that way now, they have been reformatted so there is nothing on them any longer, and you do not want them to be set up as raid. Is this correct?

I think you need to erase the raid metadata on those disks if you want them to be normal hdds and I think the command you use to do that is this one:
```
sudo dmraid -rE /dev/sda
```And:
```
sudo dmraid -rE /dev/sdb
```Can someone confirm this?
[COLOR=Blue]**EDIT**[/COLOR]:
> Just out of curiosity, why would you instruct OP to use "blkid -c /dev/null" instead of justblkid keeps a cache of what it has found. Do a lot of reformatting and resizing and it gets corrupted. This way it effectively runs without the cache.

[COLOR=Blue]**EDIT2**[/COLOR]: I did find the following thread with a nearly identical problem and it appears my commands are correct:  [http://ubuntuforums.org/showthread.php?t=1678827](http://ubuntuforums.org/showthread.php?t=1678827)

---

### Post by whitefish10 on 2013-02-11
> **Morbius1 said:**
> [COLOR=Blue]Please do not do this until we get more feedback [/COLOR]from the other members on this topic because it's been too long ago that I did this last so it's best to get some feedback.

If I understand your posts these used to be raid but they are not set up that way now, they have been reformatted so there is nothing on them any longer, and you do not want them to be set up as raid. Is this correct?

I think you need to erase the raid metadata on those disks if you want them to be normal hdds and I think the command you use to do that is this one:
```
sudo dmraid -rE /dev/sda
```And:
```
sudo dmraid -rE /dev/sdb
```Can someone confirm this?
[COLOR=Blue]**EDIT**[/COLOR]:
blkid keeps a cache of what it has found. Do a lot of reformatting and resizing and it gets corrupted. This way it effectively runs without the cache.

[COLOR=Blue]**EDIT2**[/COLOR]: I did find the following thread with a nearly identical problem and it appears my commands are correct:  [http://ubuntuforums.org/showthread.php?t=1678827](http://ubuntuforums.org/showthread.php?t=1678827)

Maybe this wasnt clear before but I got my data on those hard drives. Are you sure this will not effect my data?

---

### Post by Morbius1 on 2013-02-11
That I do not remember. When I did this before I was recommissioning them to another box so therey were going to be reformatted and repartitioned anyway. I thought  you had reformatted these drives.

---

### Post by oldfred on 2013-02-11
Some really old links now, but have seen many use these recently. May also be used recently with Intel SRT systems.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discussion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

