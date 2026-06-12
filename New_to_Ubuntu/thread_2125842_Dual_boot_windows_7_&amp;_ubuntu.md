---
title: "Dual boot windows 7 &amp; ubuntu"
date: 2013-03-15
forum: New to Ubuntu
---

### Post by I@1n on 2013-03-15
Hi.

I'm running 12.04 LTS on a Toshiba Satellite Pro and have been on Ubuntu 100% for a few years but since my degree needs dictate that I use specific software I need to run Windows. I have the Windows CD and the serial still on the base of my laptop so that's lucky I guess... I've tried running the programs in Wine but they don't run properly and with marks at stake I'd not willing to risk it...

I've had a search through the forum and haven't found anything concrete in the way of warnings about partitioning my drive and putting Windows 7 on there... and I'm no expert in this - quite the opposite really.

Anyone know of any resources they can point me in the direction of to help me out?
Thanks.

---

### Post by Mark Phelps on 2013-03-15
Unfortunately, Win7 is too large to fit on a CD, so if it is actually a CD, and it came with the Toshiba, it's more likely to be a Recovery CD -- which is little more than WinPE (a boot able windows environment) and some code to start up a restore from the Recovery partition that Toshiba put on your laptop.  

If this is true and you erased the Recovery partition, then you have no way to restore Win7.

So, the first thing you should do is try booting from the disk and seeing what options it presents.  IF it is a DVD, not a CD, and if it does give you the option to install Win7, then you have the disk you need.

---

### Post by fantab on 2013-03-15
Windows' versions earlier than Windows7 do not run if they are not installed on the FIRST Partition of the HDD. Though Win7, supposedly works other partitions, I have my doubts that its working will be flawless.

So to be safe, you have to install Windows on the First Partition of your HDD. Your best bet is to REINSTALL both OS and Dual boot.

Remember:
BACK UP important DATA first.
Windows install takes lot more disk space than a Linux OS and for Windows to work 'properly' you need to have atleast 25% of free space in your C: partition.
[DOS Partition Table (MBR)]("http://wiki.osdev.org/Partition_Table") can have only FOUR PRIMARY Partitions... if you need more you have to CREATE an [EXTENDED PARTITION]("http://askubuntu.com/questions/151968/what-does-the-term-extended-partition-mean-is-it-safe-to-use-this-type-of-par") and within that extended partition you further create LOGICAL PARTITIONS, as many as you like.

Just repartiton your HDD accordingly and Reinstall.

EDIT after reading Mark's post: 
If you find out that your CD/DVD does not have install then you can download/obtain a copy of the Windows and use your KEY. Windows should be of the same version, for instance "Windows 7 Home Premium 32bit". Or rush to the Toshiba Service Center.. :D

---

### Post by Mark Phelps on 2013-03-15
I have Win7 installed to the Second partition on my drive -- and it works just fine.

---

