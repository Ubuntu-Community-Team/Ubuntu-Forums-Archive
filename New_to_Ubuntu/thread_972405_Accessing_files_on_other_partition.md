---
title: "Accessing files on other partition"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by mindlessly self indulgent on 2008-11-05
Is there any way that I can access the files that I have on my XP partition (such as .jpegs .mp3s and all that good stuff) through Ubuntu?

---

### Post by taurus on 2008-11-05
Yes.  You just need to mount it first before you can access it.  With ntfs-3g driver, you can even write to it if you wish.  Which partition is your windows--ntfs?

Open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by ponto18 on 2008-11-05
Yeah, of course! You can not only access them, but change them as well.
Go to the System>Administration>Synaptic and search for ntfs-conf. Install it and go to
Applications>system tools>NTFS Configuration Tool. You can set there your options: read-only or write-read on ntfs partitions.
But you can access them on read mode. In the Computer folder there must be your XP partitions, and you can access them through there...Try it.

---

### Post by Paqman on 2008-11-05
The easiest thing to do is install the package ntfs-config. It'll get your Windows partition mounted and usable in no time.

---

### Post by zwygart on 2008-11-05
Hi,

For sure they is a way. And it is not very difficult.( I made it very often)

If you want to access others partitions (NTFS, FAT16, FAT32, ext2, ext3, etc.), go in a terminal and type "sudo fdisk -l". You must be root (like administrator on Windows). This way you see which partition XP is on (normally /dev/sda1)

Then you type "sudo mkdir /media/XP"
This makes a folder from where you can access your datas.
Type "sudo mount /dev/sda1 /media/XP"
replace sda1 with the right letters.
A icon should appear on the desktop.
If not you can go manually to the directory /media/XP.

Your datas are now in /media/XP/"Documents and Settings"/*username*/"My documents"

To mount the partition on boot time and others additionnal inforamtion look at this [http://users.bigpond.net.au/hermanzone/p10.htm]("http://users.bigpond.net.au/hermanzone/p10.htm")

---

