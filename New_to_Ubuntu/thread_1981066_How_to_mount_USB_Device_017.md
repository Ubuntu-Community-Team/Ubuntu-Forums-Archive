---
title: "How to mount USB Device 017?"
date: 2012-05-16
forum: New to Ubuntu
---

### Post by Boyntonstu on 2012-05-16
boyntonstu@boyntonstu-s5704y:/media$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 001 Device 003: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 002 Device 002: ID 0781:5530 SanDisk Corp. Cruzer U3 4gb SDCZ36
Bus 002 Device 003: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 001 Device 004: ID 04ca:0040 Lite-On Technology Corp. 
Bus 001 Device 005: ID 192f:0416 Avago Technologies, Pte. 
Bus 001 Device 014: ID 045e:070f Microsoft Corp. 
Bus 001 Device 007: ID 1058:0704 Western Digital Technologies, Inc. Passport External HDD
Bus 001 Device 017: ID 0781:5530 SanDisk Corp. Cruzer U3 4gb SDCZ36
boyntonstu@boyntonstu-s5704y:/media$ ls /dev/|grep ugen
boyntonstu@boyntonstu-s5704y:/media$ ls /dev/usb
hiddev0


I would like to view Device 017

I have no idea what Device 002 is.


BTW  Device 017 is 8 GB (not 4 GB)

Dev 001 is the 16 GB boot 11.10 (not 4 GB)

---

### Post by Boyntonstu on 2012-05-17
Bump

---

### Post by jtarin on 2012-05-17
I've had problems in the past with mounting USB sticks and overcame them easily by formatting them in Windows using FAT32. You can easily transfer NTFS files to them to and from Linux afterwards.

---

### Post by layers on 2012-05-17
Aren't those USB interfaces?

Anyways, let me help you mount your Cruzer.

(I'm assuming the drive is not automounted)

to see how your system sees it, you should do ```
sudo fdisk -l
```
then make a folder to mount it in ```
sudo mkdir /media/here
```
then mount it```
sudo mount ### /media/here
```
### is how it is listed from fdisk (eg./dev/sda1)

post output of fdisk -l for step by step from us if you're at a loss

---

### Post by Boyntonstu on 2012-05-18
> **layers said:**
> Aren't those USB interfaces?

Anyways, let me help you mount your Cruzer.

(I'm assuming the drive is not automounted)

to see how your system sees it, you should do ```
sudo fdisk -l
```
then make a folder to mount it in ```
sudo mkdir /media/here
```
then mount it```
sudo mount ### /media/here
```
### is how it is listed from fdisk (eg./dev/sda1)

post output of fdisk -l for step by step from us if you're at a loss


boyntonstu@boyntonstu-s5704y:/$ sudo mount /dev/sde1 /media/here
mount: you must specify the filesystem type
boyntonstu@boyntonstu-s5704y:/$

---

### Post by layers on 2012-05-19
try
```
mount -t <filesystem type> /dev/sde1 /media/here
```
do you know the system type? like ext2, ext3, vfat, fat16, reiser, smbfs, ntfs

---

### Post by Oldnews2 on 2012-05-19
Hi
I don't know why this works, but after much googling this is what I added to /etc/fstab 

```
gksudo gedit /etc/fstab
```then add 
```
none        /proc/bus/usb    usbfs    auto,rw,user,busgid=108,busmode=0775,devgid=108,devmode=0664    0    0
```hope this helps ...

---

