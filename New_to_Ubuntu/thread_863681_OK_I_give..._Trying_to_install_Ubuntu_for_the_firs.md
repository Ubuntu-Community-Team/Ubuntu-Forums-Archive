---
title: "OK I give... Trying to install Ubuntu for the first time"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by ishmael2k on 2008-07-18
:confused:  I am trying to install Ubuntu on a spare pc to try it out and have run into a wall. (Maybe....) 

The install goes fine up to the hdd partitioning at which point all it shows are sda partitions. Am I missing something? I thought that the master IDE hdd would show as an hda. 

Also don't I need to have a separate partition for the root? 

I have tried all 3 types of partition installations given with no luck. I did finally go ahead an install using the Guided_entire disk and it installed fine but I have no partitions that I can see but the desktop. 

I have checked through the help topics and through the New to Ubuntu thread but am unable to get a handle on what is going wrong. (If anything.) 

BTW the pc I am putting it on has the following specs:
Gigabyte 8PE667 Ultra mb
P4 226
1gb memory
New Seagate 250 gb hdd
Matrox 550 video card.
Onboard LAN 

I have a fairly good handle on MS command line and am willing to learn the Linux variant.

Any help would be greatly appreciated.

One last thing, as I said above it installed fine but when I went to install the Linux driver for the vid card it wanted me to do it from the root and I was not able to figure out how to get there....

---

### Post by avtolle on 2008-07-18
You have two partitions on your hdd; / (root) and swap. To see them, from the CLI (terminal, accessed by Applications>>Accessories>>Terminal) ```
sudo fdisk -l
```type your password when prompted (the same password used to log in) which you will not see, nor will there be any other visual feedback of putting it in, press Enter.

To be "root", you need to type sudo before the command (which again will need to be done from the CLI).

---

### Post by Elfy on 2008-07-18
Hi and welcome :)

> The install goes fine up to the hdd partitioning at which point all it shows are sda partitions. Am I missing something? I thought that the master IDE hdd would show as an hda.Gnenerally all pata and sata hdd's are seen as satas now so sda they are.

> I have tried all 3 types of partition installations given with no luck. I did finally go ahead an install using the Guided_entire disk and it installed fine but I have no partitions that I can see but the desktop.If you used the whole disc option then everything will be inside / (root) - Desktop is part of your home folder ( /home) - everythiing will be inside root for you - except swap which wioll be seperate.

> One last thing, as I said above it installed fine but when I went to install the Linux driver for the vid card it wanted me to do it from the root and I was not able to figure out how to get there....Unless you have a pressing need to do so the best way is throuigh the hardware driver GUI in sys >admin menu.. generally if something need root rights, use suod if in a terminal or command prompt - gksudo for apps with a GUI

> I have a fairly good handle on MS command line and am willing to learn the Linux variant.Oh good..,. that will speed help up a bit :D

Welcome, again, and good luck

---

### Post by ryniek on 2008-07-18
You must install Ubuntu on hdd with partitions like those: **/** is root partition, **SWAP** partition and **/home** partition. If you have for example 40Gb for Linux make something like this: max 9GB for root partiton, 512 MB for SWAP and rest for /home. If you install it, you must add proper repositories and install graphic drivers from Drivers Manager or from Envy. If you want be a root, you must type **sudo su** in console.

---

### Post by bhadotia on 2008-07-18
Install Gparted , it will tell you the state of your partitions and let you edit them. Open a terminal (Applications>Accessories>Terminal) and paste the following command:
```
sudo apt-get install gparted
```
Gparted will be found in System>Administration after the installation.

> One last thing, as I said above it installed fine but when I went to install the Linux driver for the vid card it wanted me to do it from the root and I was not able to figure out how to get there....
Are you installing the driver from the source code or from the repositries ?
If the driver is available from the repos , you just install it via the terminal as above:
```
sudo apt-get install driver-package
```
where driver-package is the name of the package (driver) for your video card.

Post back if you have difficulty understanding the above instructions.
Good Luck.:)

---

### Post by Miljet on 2008-07-18
And don't get stressed over your hard disk showing up as either sda or hda, Ubuntu seems to use the terms interchangeably. It doesn't make an iota of difference in the operation of the system.

---

### Post by ugm6hr on 2008-07-18
> Also don't I need to have a separate partition for the root?

No (unless you are referring to root as the root directory, aka "/", which is automatically created for you).

> I have tried all 3 types of partition installations given with no luck. I did finally go ahead an install using the Guided_entire disk and it installed fine but I have no partitions that I can see but the desktop.

The first statement contradicts the second.  You have successfully installed using the Guided - Whole Disk option.  No luck required.

There are many reasons to have a separate /home partition, but it is not necessary.  The only *compulsory* partitions are "/" (which is where everything is installed, including your own files etc) and "swap" (which is for virtual RAM).  These were automatically created during the Guided - Entire Disk process.  "/" can consist of one single partition, with directories within it, or each directory can be located on a separate partition ("/home" is a common one to have separate, but any of them can be separate if you want - just look in "File System / Computer" in the disk browser (aka Nautilus).

But, more to the point...  Why not just enjoy using Ubuntu for now, and worry about partitioning later?

---

### Post by ishmael2k on 2008-07-19
Wow all I have to say is that this is the most helpful forum I have been a member of. As of right now I am in a state of flux as I have had to relinquish a large section of my pc desk to my wife. (So what if she is pursuing her Masters degree and in the middle of he thesis. :lolflag: ) 

Anyway I am going to set up another desk for myself and will get the Ubuntu pc up and running at that time. It should take me a day or so to rearrange the basement to do this.

Thanks again, from what I see in these replies I should be off and running. Looking forward to a none MS pc!

Try

---

