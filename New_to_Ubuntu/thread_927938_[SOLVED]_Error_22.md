---
title: "[SOLVED] Error 22"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by strtomas on 2008-09-23
I recently wiped my hard drive deleting both my windows and linux partitions. The wipe finished, and windows finished reinstalling its new partition. I removed the boot CD, and the computer restarted. However when it began to boot, it brought up a screen saying "Grub 1.5" "Error 22" 

I thought that windows had not deleted the linux partition so I tried using a "Partition Logic" CD and since i couldn't use an OS I had to use F2 to force it to run the disk. It only saw 1 partition, my windows partition. 

So i ran my boot CD again, and rewiped my hard drive. Still nothing. Third times a charm? nope. 

So i finally booted from my Linux CD but, to no avail. Linux's partition editor only sees the 1 windows partition, nothing else. 

So basically, im assuming that this "Grub" item was left over, and since linux was my primary partition my computer is automatically going to it. I'm not even getting a screen to select which partition to use, because according to everything else theres only 1 partition. Windows is there but i cant get to it. Help?

---

### Post by Titan8990 on 2008-09-23
GRUB is not written to a partition. It is written to the MBR. You will need to run a utility that will clean the MBR (although the Windows bootloader should just overwrite GRUB during reinstalliton).

I would use a Bart's PE to fix the MBR.

---

### Post by strtomas on 2008-09-23
Ok, I dont mean to nag but, how do I use Bart's PE to fix this. I understand that I am to use this to boot windows right? Ok so once i get windows loaded....then what?

---

### Post by Titan8990 on 2008-09-23
Bart's PE does not load Windows. It is a compilation of technical utilities that is based on Windows.

[http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)


The "Getting Started" section give instructions on how to make the disk. You will need a Windows Install disk to build it.

---

### Post by cariboo on 2008-09-23
You could also boot from your xp install disk into the recovery console and use FIXBOOT and FIXMBR to repair the mbr.

Jim

---

### Post by strtomas on 2008-09-23
Ok, well I do not have a standard Windows installation Disk. Do you know of any other utilities that i could use to clean the MBR?

---

### Post by Titan8990 on 2008-09-23
duh, don't know what I was thinking, especially when I have used FIXMBR from recovery console before.

My collection of bootable disks has spoiled me.



> Ok, well I do not have a standard Windows installation Disk.


What kind of Windows disk do you have?

---

### Post by strtomas on 2008-09-23
> **cariboo907 said:**
> You could also boot from your xp install disk into the recovery console and use FIXBOOT and FIXMBR to repair the mbr.

Jim

ok that sounds promising, i will attempt that now.

---

### Post by strtomas on 2008-09-23
> **Titan8990 said:**
> duh, don't know what I was thinking, especially when I have used FIXMBR from recovery console before.

My collection of bootable disks has spoiled me.






What kind of Windows disk do you have?

I have a Recovery disk

---

### Post by Titan8990 on 2008-09-23
I don't think you can get the recovery console from a OEM recovery disk. With those I believe your only option is wipe everything.

---

### Post by Steve1961 on 2008-09-23
You can fix the mbr with Super Grub disc or just get hold of a windows  98 boot disk and do an fdisk /mbr.

Of course you need to be able to get online to do any of this, so boot with a live linux cd to get hold of [SGD]("http://www.supergrubdisk.org/") or a [win98]("http://www.bootdisk.com/bootdisk.htm") boot disc

---

### Post by strtomas on 2008-09-23
Ok, if thats the case. Do you know of an alternate program that i can use to wipe my hard drive.

---

### Post by strtomas on 2008-09-23
> **Steve1961 said:**
> You can fix the mbr with Super Grub disc or just get hold of a windows  98 boot disk and do an fdisk /mbr.

Of course you need to be able to get online to do any of this, so boot with a live linux cd to get hold of [SGD]("http://www.supergrubdisk.org/") or a [win98]("http://www.bootdisk.com/bootdisk.htm") boot disc

I have a 98 boot disk, i can do that.

---

### Post by strtomas on 2008-09-23
Ok i attempted to run fdisk.exe/mbr using my windows 98 boot disk. This command would not work. fdisk.exe ran without any problem, however fdisk.exe/mbr did nothing....not even an error it just didnt do anything.

---

### Post by Titan8990 on 2008-09-23
Does the GRUB menu still come up?

---

### Post by strtomas on 2008-09-23
Ok all is well now, turns out fdisk.exe/mbr command did work it just didnt say it had executed. Thanks to everyone for your help.

---

### Post by Titan8990 on 2008-09-23
Don't forget to mark your thread as solved.

---

### Post by Steve1961 on 2008-09-23
> **strtomas said:**
> Ok all is well now, turns out fdisk.exe/mbr command did work it just didnt say it had executed. Thanks to everyone for your help.

Glad you got it fixed.  Just as an 'in case it happens again' provision, it is worth checking out bartpe, or even better, UBCD:

[http://www.ubcd4win.com/](http://www.ubcd4win.com/) works for me every time :)

---

