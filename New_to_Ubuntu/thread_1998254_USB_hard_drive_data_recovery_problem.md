---
title: "USB hard drive data recovery problem"
date: 2012-06-06
forum: New to Ubuntu
---

### Post by CK000 on 2012-06-06
[SIZE=2][FONT=Garamond] Hello,

I hope some-one will kindly be able to assist me and thank them in advance.

I have bought a USB powered hard drive enclosure to read two different SATA hard drives. My problem is that ubuntu 10.04 does not appear to recognise them and they do not appear in the file system... 

I have used "disk utility" and they are recognised there, but are listed as 'un-partitioned'. There is no option to mount them either.

Well, my issue is that I know they are partitioned: One is taken from an old Playstation 3 which gave up the ghost and I wish to recover the music and photographs. The other I rescued from an accidentally broken old Linux Laptop which I no longer have that ran Linux 8.?? Thus the first should be FAT or FAT32 and the other at least read-able by a Linux system.

So, all in all I simply wish to recover the data and would appreciate any help to do so.

My system is ubuntu 10.04 using a laptop.

Many thanks.
[/FONT][/SIZE]

---

### Post by Gone fishing on 2012-06-06
I would download the parted magic live cd [http://partedmagic.com](http://partedmagic.com) this has lots of tools for recovering data test disk etc. Boot up on the live cd and see if the disks can be read if not then parted magic probably has the tools you need to get the data back.

---

### Post by oldfred on 2012-06-06
If the drives do not mount, I am not sure sure any of the software will work.

Some laptops do not put out enough power on the USB port for a hard drive. Is yours only USB powered?

If you run this before & after plugging in USB device what shows?

```
lsusb
```

---

### Post by CK000 on 2012-06-06
Output from running lsusb command:-

BEFORE:-

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

AFTER:-

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 1bcf:0c31 Sunplus Innovation Technology Inc. 
Bus 001 Device 002: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by Hadaka on 2012-06-06
There are some great examples on data recovery and USB hard drive
commands in this link.

[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

Don't let the "newbie" in the link fool you.    dd should ALWAYS be used with caution,
an error in the if= and of= can and will destroy your good data...forever.

read through..use caution and patients.

good luck.

---

### Post by Gone fishing on 2012-06-06
oldfred Makes a very good point - normal usb cables will not  usually work for a hard drive (bitter experience)you will need one of the double usb cables (for hard drives) or a short thick cable usb hard drive cables.

If that isn't the problem I'd still try parted magic and see if test disk can see the partitions.

---

### Post by oldfred on 2012-06-06
It is mounting this:

Sunplus Innovation Technology Inc.

So is that the external drive? Then if it is not working I would check to make sure you have enough power.

---

### Post by CK000 on 2012-06-06
[SIZE=2][FONT=Garamond]Thank you so much for all your help so far. 

PartedMagic is reporting one drive as unpartitioned or of an unknown partition type.

There does not seem to be any hardware problems and the drive unit is receiving enough power (both with and without an externally powered USB hub)

Many thanks.
[/FONT][/SIZE]

---

### Post by Gone fishing on 2012-06-06
Can test disk on the parted magic cd see the partitions [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step).

I would suggest you don't change the drive if the data is important.

---

### Post by CK000 on 2012-06-06
[SIZE=2][FONT=Garamond]Well, PartedMagic does not appear to be recognising or seeing the partitions no.[/FONT][/SIZE]

---

### Post by Gone fishing on 2012-06-07
Sorry but if niether Ubuntu or Parted Magic can see any partitons with gparted and Test disk can not see any partitions or evidence of partitions I think it is likely that the disk has died.

I think the right approach would have been to copy the disk bit for bit with dd [http://www.cyberciti.biz/tips/how-do-i-save-recover-data-from-crashed-disks-with-dd-and-ddrescue-command.html](http://www.cyberciti.biz/tips/how-do-i-save-recover-data-from-crashed-disks-with-dd-and-ddrescue-command.html) and then use fsck (Linux partition)or chkdisk (fat etc) and test disk to fix the disk and recover any partitions.

---

### Post by CK000 on 2012-06-13
[FONT=Garamond][SIZE=2]Firstly, I really appreciate everyone's help and advice in their posts thus far, so thank you very much indeed.

Secondly, one of the hard drives was as Gone Fishing accurately predicted completely useless. This drive was from an old laptop and as I can scarcely recall what data I have lost upon the drive I am no longer concerned.

Thirdly, the other drive (160 GB) was taken from an old Play Station 3 which as I mentioned gave up the ghost after five years of service. 

Some say the Play Station 3 is formatted as FAT32, others that it is JFS, others still say that it is a proprietary format and is encrypted by the Play Station it originated from. I would suggest that the last one of these apparent possibilities is the most likely. Considering my method for accessing the data I am not convinced it is FAT32 and I personally have almost no knowledge of JFS (but I believe it is a peculiar Linux format) thus it is proprietary. However whether it is truly encrypted remains to be seen and I will let my readers judge for themselves.

There is both good news and bad news and I hope my readers will forgive my long pre-amble.

The good news: I managed to recover my music; my pictures and my videos id est everything that a user might wish to place upon their Play Station 3 other than games. I thus suggest that a Play Station 3 is not entirely encrypted.

The bad news: Whilst there was certainly evidence of other data non of it was usable at an end user level. This data was obviously the saved game data. When transferred however the games I posses either did not recognise the data at all or refused to allow me to use it. The message on some games was "This is not your data" on others the game behaved as if I had no prior saved data at all.

I can say that Gone Fishing's advice was a great help to me as was Old Fred's too, in fact all of you have been useful in my quest.

My modus operandi was simple: 
[/SIZE][/FONT]
[FONT=Garamond][SIZE=2]1) I used a double power cable to power up and eventually mount the drive;
2) Parted Magic to attempt to read it and establish the partition type;
3) An over night bit for bit clone of the drive (as you'll know it takes hours);
4) Repair any bad sectors using Parted Magic;
5) Access the music; picture and video files using Linux;
6) Copy them to the computer's Hard Drive;
7) Copy them to the Play Station 3  via an USB drive (several journeys);

Thus the Play Station 3 does not seem to allow you to utilise your saved game data after your Play Station 3 sadly dies, if and when it dies, on a new Play Station 3. This is how Sony presumably wish it to be and how I assume it must be. 

Note bene: I had and have no wish to hack or reverse engineer a Play Station 3 system I simply wished to access my own data. Well to some extent as I have elaborated I succeeded in that recovery.

Thanks and best wishes.
[/SIZE][/FONT]

---

