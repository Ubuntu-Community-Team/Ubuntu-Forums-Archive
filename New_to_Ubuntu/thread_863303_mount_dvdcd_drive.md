---
title: "mount dvd/cd drive?"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by tparker on 2008-07-18
My cd/dvd drive used to work fine and now it doesn't work at all. None of my searches have given me any way to fix this and I have been trying for many weeks.

The drive shows up under Places>Computer but when I click on it I get: Unable to mount location, no media in drive (whether there is a disk in the drive or not it's the same message.)

If I put a known working, commercial DVD in the drive and start Xine or Kaffeine I get errors that the source can't be read, doesn't contain data, or no disk in drive.

This all worked fine (same drive, os, disk, set up) until a few updates ago when it magically stopped. I can't even try to reinstall because it can't see the Live CD.

The system is Hardy, was a fresh install not upgrade, 32 bit version (AMD 64 cpu). The cd/dvd is HP 840i, worked fine previously, works when moved to a windows computer, is the only cd/dvd drive in this box.

/etc/fstab says:
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d6cb6439-7c8e-4d7d-b52d-14df7b47515d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=b08693d7-1f32-4903-8ab7-fdcb597ded6c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
core:/mnt/PublicShare/share	/mnt/public	nfs	defaults	0	0
core:/home	/home	nfs	defaults	0	0
/dev/scd0       /media/dvd0   udf,iso9660 user,noauto,exec,utf8 0       0

Not sure what else to give for info but let me know what is needed and I'll find it.

---

### Post by benfindlay on 2008-07-18
Could you also post the output of dmesg?

Cheers

Ben

---

### Post by dracayr on 2008-07-18
from a terminal:
```
sudo mkdir /mnt/cd
sudo mount scd0
```

If those commands give no output, the drive was successfully mounted on /mnt/cd. else, post the output

dracayr

---

### Post by tparker on 2008-07-18
> **benfindlay said:**
> Could you also post the output of dmesg?


I looked and I don't see dmesg in the places I can think of, can you tell me where to find it? Sorry, still learning this. :)

---

### Post by tparker on 2008-07-18
> **dracayr said:**
> from a terminal:
```
sudo mkdir /mnt/cd
sudo mount scd0
```

If those commands give no output, the drive was successfully mounted on /mnt/cd. else, post the output



The first line gave no output, the second gave me:
mount: can't find scd0 in /etc/fstab or /etc/mtab

---

### Post by cloverz7 on 2008-07-18
Don't want to thread jack but I also have the problem

mkdir: cannot create directory `/mnt/cd': File exists
 from the first command 

mount: can't find scd0 in /etc/fstab or /etc/mtab
from the second

---

### Post by benfindlay on 2008-07-20
> **tparker said:**
> I looked and I don't see dmesg in the places I can think of, can you tell me where to find it? Sorry, still learning this. :)

You open a terminal and type dmesg into it and press enter, then it will print a load of stuff on screen!

Hope this helps!

---

### Post by sisco311 on 2008-07-20
also post the output from:
```
sudo lshw -C disk
```

---

### Post by Potts on 2008-10-22
> **sisco311 said:**
> also post the output from:
```
sudo lshw -C disk
```

I too am having the exact same problem... here is my output:

david@Ubuntu-Linux:~$ sudo lshw -C disk
  *-disk                  
       description: ATA Disk
       product: ST3400620A
       vendor: Seagate
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 3.AA
       serial: 5QH08HVA
       size: 372GiB (400GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=b179b179
  *-cdrom
       description: DVD writer
       product: DVDRW SOHW-812S
       vendor: LITE-ON
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: US0J
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=open

---

### Post by dennisdunbar on 2008-11-18
> **sisco311 said:**
> also post the output from:
```
sudo lshw -C disk
```

I have the same problem here is the output:
  *-disk                  
       description: ATA Disk
       product: Maxtor 6Y160P0
       vendor: Maxtor
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: YAR4
       serial: Y47XDCFE
       size: 152GiB (163GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000e7a66
  *-cdrom
       description: DVD-RAM writer
       product: DVD+-RAM 530L v1
       vendor: Memorex
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 5M64
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc

There was a good copy of the LiveCD in the drive at the time.

Help!

---

### Post by dennisdunbar on 2008-11-18
> **dennisdunbar said:**
> I have the same problem here is the output:
  *-disk                  
       description: ATA Disk
       product: Maxtor 6Y160P0
       vendor: Maxtor
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: YAR4
       serial: Y47XDCFE
       size: 152GiB (163GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000e7a66
  *-cdrom
       description: DVD-RAM writer
       product: DVD+-RAM 530L v1
       vendor: Memorex
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 5M64
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc

There was a good copy of the LiveCD in the drive at the time.

Help!

Oh and here is another clue.

The machine recognizes and works with its original CD-Rom drive perfectly.

BTW it is a Dell GX270 and I'm running 8.10.

---

### Post by geomantic8 on 2008-11-18
I'd like to jump in since I'm having similar issues...

The light on the CD blinks, it spins, drawer opens/shuts, but in the end the computer doesn't find the CD at boot time. I've gone round and round looking through all the usual places- dmesg, /etc/fstab, lshw, but none of the logs even acknowledge its existence (although there is an entry in fstab for the CD). 

I should add that I'm running old hardware but the CD drive is relatively new: Gateway 1000, 1Ghz processor, 512Mb RAM, Ubuntu 8.04

Any help much appreciated because I am going crazy
-g8

---

