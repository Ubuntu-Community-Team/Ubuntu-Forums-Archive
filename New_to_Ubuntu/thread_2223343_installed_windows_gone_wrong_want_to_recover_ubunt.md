---
title: "installed windows gone wrong want to recover ubuntu"
date: 2014-05-10
forum: New to Ubuntu
---

### Post by kr4k3n2 on 2014-05-10
recently I made a bootable usb with "winUSB" from Ubuntu and I installed the win8.1 64bit on another empty drive (not in the Ubuntu; in another partition disk) now I can't access to my Ubuntu os how to recover it, please help me :(

---

### Post by oldfred on 2014-05-10
Post link to BootInfo report.

If Ubuntu drive was set as boot drive with BIOS, Windows may have installed its boot files into the Ubuntu drive. It does not see Linux so it just overwrites whatever. You have to set Windows drive as boot drive before installing Windows.

Lets see details first.
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by kr4k3n2 on 2014-05-10
k I will answer it tomorrow or asap please don't close this threat :) thank you.

---

### Post by kr4k3n2 on 2014-05-12
heres my boot summary please help me
[http://paste.ubuntu.com/7452457/](http://paste.ubuntu.com/7452457/)

---

### Post by oldfred on 2014-05-12
We have seen exactly this before. Windows does not recognize Linux partitions and rewrites partition table without your Linux partition in the extended partition.

Do you have any documentation on exact partition. Is it one partition or more? Start will be a few sectors after start of extended partition and end a few sectors before the start of swap. If more than one partition where it is in the middle is unknown but testdisk often can find old partition and let you restore it to partition table. 
Do not reformat or recreate with formatting.

 [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
      
 Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

If you resized partitions several times, testdisk may find all those alternatives. You just want to recover the one (or more) missing partitions that will fit into  the space in the extended partition. It must be a logical partition.

---

### Post by kr4k3n2 on 2014-05-12
okay the TestDisk is not showing extended drive (where ubuntu partitions)

---

### Post by kr4k3n2 on 2014-05-12
screenshot[IMG]http://s27.postimg.org/kfklql2pf/dedfef.png[/IMG]

---

### Post by oldfred on 2014-05-12
I do not recognized Windows version of testdisk. Screen looks a bit different.

But it does not show extended partition. It just had primary and logical. All logical partitions then will be in one extended partition, so they must be next to each other on drive.

---

### Post by kr4k3n2 on 2014-05-12
should i have to proceed on physicaldrive 500gb?? then??

---

### Post by oldfred on 2014-05-12
Are there instructions for the Windows version? I have never checked?
If you do not write or save anything trying something is ok.

---

