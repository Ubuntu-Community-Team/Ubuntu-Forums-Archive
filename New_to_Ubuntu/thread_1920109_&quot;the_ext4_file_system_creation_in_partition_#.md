---
title: "&quot;the ext4 file system creation in partition #1 (0,0,0)(sda) failed.&quot;"
date: 2012-02-04
forum: New to Ubuntu
---

### Post by Nirubu on 2012-02-04
Hello. Months ago, my laptop crashed. I had USB drive or empty CD, so I kind of forgot about Linux until yesterday.

I downloaded the Desktop version of Ubuntu 11.10. I am using an Acer laptop though. Everything worked fine, until I got this one error, that not even Google would help me to fix!

 "the ext4 file system creation in partition #1 (0,0,0)(sda) failed." Yep, that is it. I have been googling around for awhile, checking several Linux/Ubuntu forums to solve this, but they do not explain it good enough whatsoever.

I hope someone here can help me. If you have time, please give me a detailed guide, preferably with pictures. I am using the test thing. Or option 1, if that is easier to understand.

 "the ext4 file system creation in partition #1 (0,0,0)(sda) failed."   happens when I am erasing my disk to install Ubuntu fresh.

Thanks in advance.

---

### Post by Nirubu on 2012-02-04
Bump.

Pictures:
[IMG]http://i42.tinypic.com/2hwd647.png[/IMG]

[IMG]http://i42.tinypic.com/64gtxu.png[/IMG]

[IMG]http://i44.tinypic.com/2lsuntc.png[/IMG]

[IMG]http://i39.tinypic.com/o8f8sl.png[/IMG]

---

### Post by mörgæs on 2012-02-04
If you want to erase everything troublesome on the disk before installing, [http://www.dban.org/](http://www.dban.org/) or [http://www.killdisk.com/](http://www.killdisk.com/) are helpful.

---

### Post by Nirubu on 2012-02-04
> **mörgæs said:**
> If you want to erase everything troublesome on the disk before installing, [http://www.dban.org/](http://www.dban.org/) or [http://www.killdisk.com/](http://www.killdisk.com/) are helpful.

I havent got a cd to burn it on though. It seems like everything on my computer was wiped off after the OS crash.

---

### Post by westie457 on 2012-02-04
Hi, welcome to the UF.

Can you remember what you were doing when the computer crashed because at the moment the error you getting looks like the hard drive has bad sectors in the MBR area of the drive.

To check this boot into a LiveCD/USB in try mode, open Disc Utility and check the SMART status of the drive. As a secondary check open a terminal (Ctrl+Alt+T) and run 'badblocks' - without the quotes. While that is running it will take a while. Have a coffee, go for a walk or do something else for a couple of hours.


After that amount of time if badblocks is still running your hard drive probably has so many bad sectors on it that it will never be usable.

Badblocks is a diagnostic program that only reads the surface of the drive it does not write to it. See ```
man badblocks
``` for more details.

Thank you.

---

### Post by Nirubu on 2012-02-04
> **westie457 said:**
> Hi, welcome to the UF.

Can you remember what you were doing when the computer crashed because at the moment the error you getting looks like the hard drive has bad sectors in the MBR area of the drive.

To check this boot into a LiveCD/USB in try mode, open Disc Utility and check the SMART status of the drive. As a secondary check open a terminal (Ctrl+Alt+T) and run 'badblocks' - without the quotes. While that is running it will take a while. Have a coffee, go for a walk or do something else for a couple of hours.


After that amount of time if badblocks is still running your hard drive probably has so many bad sectors on it that it will never be usable.

Badblocks is a diagnostic program that only reads the surface of the drive it does not write to it. See ```
man badblocks
``` for more details.

Thank you.

Thank you.

Should I just play some Battlefield 3 while I have this open? Or as you suggested, go for a walk or something.

[IMG]http://i43.tinypic.com/fbz3f9.png[/IMG]

---

### Post by Nirubu on 2012-02-04
Bump.

Does anyone know how to fix the hd without waiting for hours?

---

### Post by joetait on 2012-02-04
> **Nirubu said:**
> Bump.

Does anyone know how to fix the hd without waiting for hours?

Have you tried partitioning it and formatting with gparted? It's not long term, but you might be able to get something working, and having your "/home" directory in a separate partition can make it easier with upgrading. Just give 15GB to the partition and partition it, and then you might miss the bad bits that are stopping it.

If you note the name of partition (of the form "dev/sda/somenumber") then you can select manual installation, install "/" to that partition, and you won't need to format it.

Just an idea, but shouldn't do any harm to give it a try.

---

### Post by Nirubu on 2012-02-04
> **joetait said:**
> Have you tried partitioning it and formatting with gparted? It's not long term, but you might be able to get something working, and having your "/home" directory in a separate partition can make it easier with upgrading. Just give 15GB to the partition and partition it, and then you might miss the bad bits that are stopping it.

If you note the name of partition (of the form "dev/sda/somenumber") then you can select manual installation, install "/" to that partition, and you won't need to format it.

Just an idea, but shouldn't do any harm to give it a try.

2 of the things in gparted are locked though. I can click on swapoff to unlock them, but I do not know what do to in partition afterwards. What option am I supposed to click?

---

### Post by oldfred on 2012-02-04
Some general info on gparted:

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

If you have no data to save, just delete the existing partitions and create new ones. Then during install choose Something else select the created partitions, format them and assign to / and /home. If swap created in advance it will automatically use it.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by joetait on 2012-02-04
> **Nirubu said:**
> 2 of the things in gparted are locked though. I can click on swapoff to unlock them, but I do not know what do to in partition afterwards. What option am I supposed to click?

What are the "things"? And by locked do you mean you are not allowed to select the things?

---

### Post by oklokl on 2012-02-04
sudo -i
fdisk -l
umount -l /dev/sda

dd if=/dev/zero of=/dev/sda bs=512 count=12342


badblocks -vw /dev/sda

longtime.. testing.. 

stop Ctrl+Z 
or
D

gparted 

mkfs.ext4 -L "" /dev/sda1

---

