---
title: "Dual boot Partitioning (WinXP and Ubuntu8.04)"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by raedbenz on 2008-05-22
HI,,
I want to have 2 Operating systems on my PC. 
I already use Win XP, and I have two partitions C (where windows is installed) and D (for my files and application).
Drive D has 30 Gb free space, hence i want to use it for Installing Ubuntu8.04.

I am reading the documents on Ubuntu's website but i am a little bit confused. Here we go:
I get three options for Partitioning (during installations steps). 

1. Guided: resize. and there is a bar (can be resized) says [/dev/sda5] and [Ubuntu 8.04]
2. Guided: use entire 
3. Manual
 
Q1. which one should i select?

inside the manual partitioning i get /dev/sda1,2,4,5, and 6.

Q2. what should i do here , because when i click next it asks me for Root partition ?

Q3. I found in the options inside Manual partition sthg called Mount Point with /DOS and /Windows options, what is there effect?

Thanks

---

### Post by sharks on 2008-05-22
1. go for manual partion.
2. select the partition where  u want to install ubuntu and give the mountpoint as / .

---

### Post by PPAAUULL on 2008-05-22
Ya Manual is the best way to go. Select the mount as "/" like Sharks said which is the root files system. Now you can also make a partition for your home directory which is like your documents and settings. Some suggest it so when you want to install the next version of Ubuntu you can have all you old settings and themes and documents and such but in the end it is up to you.

---

### Post by stalkier on 2008-05-22
Sharks is correct. Manual partition, choose the D drive, mount partition as / (root), then install. It will install GRUB over the MBR (MS boot will be over-written). GRUB will autodetect the OS's. 

Just in case you have to ever reinstall windows you will have to reinstall GRUB. If you do not reinstall GRUB then it will automatically goto windows. 

I hope this helps.

---

### Post by raedbenz on 2008-05-22
Thanks

what about what is inside the manual partitioning; /dev/sda1,2,4,5,6? they are with different types, likee NTFS, FAT 16 etc...

Q1. should i keep them all???
Q2. moreover should i create (byself) the swap file?
Q3. will i loose any data from windows??
thanks

---

### Post by sharks on 2008-05-22
Change the filesystem type ext3 where u want to install ubuntu.
if u want to keep windows alive,keep that drives.

---

### Post by sharks on 2008-05-22
Change the filesystem type ext3 where u want to install ubuntu.
if u want to keep windows alive,keep that drives.

---

### Post by sharks on 2008-05-22
if u have more ram , then less swap memory is enough. ya u should keep the swap.

---

### Post by Victormd on 2008-05-22
> **sharks said:**
> 1. go for manual partion.
2. select the partition where  u want to install ubuntu and give the mountpoint as / .

Don't forget to make a partition for SWAP (~512MB should do...)

---

### Post by raedbenz on 2008-05-22
> **sharks said:**
> Change the filesystem type ext3 where u want to install ubuntu.
if u want to keep windows alive,keep that drives.

HI Sharks..
But i dont have ext 3. only 1,2,4,5,6. and there settings are:
 
sda1 --> fat16 , 115Mb
sda2 --> ntfs, 35Gb (where is windows installed: C drive)
sda5 --> ntfs, 70Gb (drive D, where i want to install Ubuntu) 
sda6 --> fat32, 2Gb
sda4 --> fat32, 3Gb

what are there settings individually?????
thanks

---

### Post by PPAAUULL on 2008-05-22
Do you have free space to put the new partition? If not you might have to resize or delete one in order to put linux on your computer.

---

### Post by sharks on 2008-05-22
sda5 --> ntfs, 70Gb (drive D, where i want to install Ubuntu) 

go to manual, select this partition and format this and change the filesystem to ext3 journaling system and give the mount point as / and select format.

---

### Post by PPAAUULL on 2008-05-22
BUT that will delete ALL the info and files on that drive or partition.

---

### Post by raedbenz on 2008-05-22
> **sharks said:**
> sda5 --> ntfs, 70Gb (drive D, where i want to install Ubuntu) 

go to manual, select this partition and format this and change the filesystem to ext3 journaling system and give the mount point as / and select format.

BUt i dont want to loose my data from D. is there a way to use the free part of it??
what about the rest sda's? no changes for them ??
thankx

---

### Post by PPAAUULL on 2008-05-22
You can resize it but I would make sure you back up your data first and defrag it. use only what freespace you have on it otherwise you will lose some of it if you resize it too small.

---

### Post by raedbenz on 2008-05-22
> **PPAAUULL said:**
> BUT that will delete ALL the info and files on that drive or partition.

HI.
then how can i resize drive D and install Linux? without affecting my old data from Windows ???

---

### Post by sharks on 2008-05-22
if u want to use only part of D,go to system-->administration-->gparted or partition editor on live cd. it will list ur partitions.select D,unmount it.then modify it.it will ask for the size to be allocated,u can enter it manually.10gb is sufficent. no changes on rest of sda's.

---

### Post by raedbenz on 2008-05-22
> **PPAAUULL said:**
> You can resize it but I would make sure you back up your data first and defrag it. use only what freespace you have on it otherwise you will lose some of it if you resize it too small.

ok thats fine...
from where can i do the resize?

---

### Post by PPAAUULL on 2008-05-22
DO NOT just resize it. FIRST back up the info then defrag it THEN resize it otherwise you run a serious risk of killing some of your data.

Like sharks said you should use gparted it is probably the easiest way to go about it.

---

### Post by raedbenz on 2008-05-22
> **sharks said:**
> if u want to use only part of D,go to system-->administration-->gparted or partition editor on live cd. it will list ur partitions.select D,unmount it.then modify it.it will ask for the size to be allocated,u can enter it manually.10gb is sufficent. no changes on rest of sda's.

thankx

---

### Post by raedbenz on 2008-05-22
> **PPAAUULL said:**
> DO NOT just resize it. FIRST back up the info then defrag it THEN resize it otherwise you run a serious risk of killing some of your data.

Like sharks said you should use gparted it is probably the easiest way to go about it.

Thanks.
the Defrag should be done from Windows or Ubuntu live CD??

---

### Post by raedbenz on 2008-05-22
> **Victormd said:**
> Don't forget to make a partition for SWAP (~512MB should do...)

How do i create the swap partition? i mean after resizing my drive D(in windows), i get free space and ready to install Ubuntu.
then from where do i get lets say extra 1Gb for swap??
thanks

---

