---
title: "New Dell with preinstalled Ubuntu"
date: 2019-11-13
forum: New to Ubuntu
---

### Post by dorininspiron on 2019-11-13
Hello,
First time opened Ubuntu and have some questions about the partitions on the SSD:
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]
SSD 256 GB[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]
ESP Partition 1, 891 MB FAT 32-bit, Name: EFI system partition
No flags at System partition, Hide from Firmware, Legacy BIOS bootable[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]
OS Partition 2 Basic 5.4 GB - 2.6 GB free
Partition type: Microsoft Reserved
FAT 32 - bit version[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]
UBUNTU Partition 3, 250 GB Ext 4, 222 GB free
Partition Type: Linux Filesystem
Content Ext 4 version 1.0 Mounted at Filesystem Root

Why there are 3 partitions?
Why a big 5.4 GB is reserved for Microsoft if I don't want to use Windows?
How can I create a partition only for Ubuntu and keep all the rest for my files?
If something goes wrong, can I install again Ubuntu in the same place without losing my personal files?
How can transfer all my stuff from my old Windows 10 to my new Ubuntu laptop?
Please help me. I am 67 years old but I want to learn using my new laptop and my new Ubuntu. 
Thank you in advance
[/FONT]

---

### Post by Impavidus on 2019-11-13
The EFI System Partition is mandatory for newer computers. It tells your computer how to boot. On older systems, that information is in the master boot record, before the start of the first partition. The third partition has the Ubuntu system and all your documents.

I don't know about the Microsoft Reserved partition. Maybe somebody with preinstalled-Dell experience knows.

Having one big partition for both your operating system and your documents is indeed not recommended. Many users have a ca. 25GB root partition for the OS and keep the rest of the drive as a /home or other type of data partition. That will enable you to reinstall Ubuntu without losing your files. You need a live disk to change the partition with Ubuntu on it, as you can't modify a partition that's in use. This can be the same usb drive (or dvd) as you can use to install Ubuntu and is a great tool to fix it. I suggest you get one. This guide tells about creating a /home partition: [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

To transfer the documents from your Windows computer to your Linux computer you can set up file sharing on your local network, or transfer them using an external drive. Do you keep backups of all important documents on an external drive? Then use that to transfer them to your new computer.

---

### Post by oldfred on 2019-11-13
At 5.4GB I doubt it really is the Microsoft reserved which normally is small.
It probably is a hidden Dell system recovery partition.

It is more likely they used the gpt GUID for Microsoft reserved.
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

### Post by dorininspiron on 2019-11-13
Thank you

---

### Post by sdsurfer on 2019-11-13
I would ask Dell why, you are (should be?) under warranty/support. A really good guess is they just installed Ubuntu on top of their default "install." The good (ish) news is, there may be a Windows OS in the partition and you can dual boot(??)

---

