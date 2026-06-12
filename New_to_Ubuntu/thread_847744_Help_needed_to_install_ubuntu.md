---
title: "Help needed to install ubuntu"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by sxytrillian on 2008-07-02
Previously i have installed windows XP it have created lot of problems which i can't even boot to my computer.
So now i want to install ubuntu 8.04 in my system.

I have put Ubnutu live CD and pressed install now option and it went upto the prepare disk space part, there it showing four options namely guided-resize,guided-use entiredisk,guided -use the largest continuous free space,
Manual.

Note: i have 250 GB hard disk which i have partioned into 4 dirves . 30 GB for my windows XP and Rest 3 drives for important files.
I want to format and install Ubuntu in that 30 GB which has Windows XP before.

Here is the problem in the first option i.e guided resize its showing the drive D which i have lot of files when i used windows XP. so i don't want to install in this drive. moreover all of drives are having important files.

So i need to install ubuntu in the C: drive where i have Windows XP.

So help me in this regard how i can perform this. And further i will use Windows VISTA anyhow someday. so is it possible to install with ubuntu? 

And i am new to Linux platform i am not aware of Swap area what it will do.

So guide me how i can freshly install ubuntu in the C:drive which has 30 GB not other drives because it have important files and give me the settings for doing it manually, i.e how much space it want to choose swap or any other thing i want to add.

In simple give me an line by line instruction to do it manually,..

---

### Post by untermensch on 2008-07-02
Call me wrong but.. I'm 90% sure you can't put two OS in the same partition. And as to your swap file.. You should make it ruffly twice the size of your ram. or you can just put 1 gb.

---

### Post by bodhi.zazen on 2008-07-02
Well I have two pieces of advice (partitioning is confusing, espeically when you are learning a new OS).

First, it sounds as if you have a single hard drive with 4 partitions.

See this link re: basic partitioning :

[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

Basically Linux (Ubuntu) does not call partitions "C:\" and C:\ refers to a partition not a hard drive :twisted:

===================

Second, you can only have 4 primary partitions on a hard drive (see the like I gave you). So you need to create an extended partition with 2 logical partitions, one for / (root) and the second for swap (well you do not *need* a swap, but it is a good idea).

===================

So you have 2 options :

1. You can delete a partition, this will destroy all the data in that partition, and devote the space to Ubuntu. Choose this option if you are wanting to destroy windows (but preserve your data) and boot ONLY Ubuntu.


2. Wubi. Wubi allows you to install Ubuntu in a File within Windows. This *may* be the easiest solution at the moment.

Home: [http://wubi-installer.org/](http://wubi-installer.org/)


Guide : [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)


The third option involves some major re-partitioning. That would be XP + Vista + Ubuntu -> you need to move data off your hard drive and re partition. Windows XP and Vista each want a primary partition. Put your other partitions, including windows data, into an extended / logical partition. Once your hard drive is re-partitioned you can restore the data.

---

### Post by untermensch on 2008-07-02
I personally use wubi. but that's because I couldn't partition my hard drive.

---

### Post by untermensch on 2008-07-02
bodhi.zazen, are you Tao?

---

### Post by sxytrillian on 2008-07-02
In simple i want to install ubuntu in sda1 which is 30 gb.

So please help me to install in it and also describe what are the values i want to give? My RAM is 1gb.

Please describe what all the things i want to do to install ubuntu in sda1 and it should boot from sda1.

I am bit confused about Ext3 journaling file system, Ext2 file system what they are? can you explain it?

Moreover i have formated my c drive i.e sda1 using gparted. so now i need to install freshly ubuntu in my sda1 so help me out..

---

### Post by Miljet on 2008-07-02
I believe the OP would have a hard time using wubi, since he no longer has any Windows installed.

Using manual partitioning, change sda1 to an extended partition. Then create three logical partitions within the extended partition. One should be about 5 GB for /. Another should be 1 GB for swap and the rest of the 30 GB will be for /home.

The / and /home partitions should be formatted as Ext3. Leave the swap space unformatted.

---

### Post by Miljet on 2008-07-02
Forgot to mention, if you are planning to add Vista to this drive in the future, you will have to re-install everything. All versions of Windows need to be installed first in a dual boot system. You can work around this by adding a separate drive and installing Vista on that.

---

### Post by sxytrillian on 2008-07-02
Don't mistake me i am a newbie how to change sda1 to extended partition.

Please help me step by step instructions in this aspect.

---

### Post by bodhi.zazen on 2008-07-02
> **sxytrillian said:**
> Don't mistake me i am a newbie how to change sda1 to extended partition.

Please help me step by step instructions in this aspect.

Boot the Ubuntu live CD.

start gparted

Delete partition sda1 (this will destroy the data on sda1) -> apply changes

You will not have 3 partitions, and unformatted, free space.
create an extended partition in the free space.

See also : [Gparted Documentation](http://gparted.sourceforge.net/documentation.php)

---

### Post by Miljet on 2008-07-02
Sorry, I am not familiar enough to guide you step by step. But basically when you start the manual partition manager, it should show your current partitions at the top of the screen. Select sda1, then look at your toolbar for an option to change the partition type. Then you will click on apply changes. Then use the slider bar to make your logical partitions and again click apply changes.

---

### Post by sxytrillian on 2008-07-02
bodhi.zazen As you said i have deleted sda1 using gparted and it is showing that space as unallocated and when i click new its showing only primary partition and the extended partition is blurred.

So how can i select it?

---

### Post by bodhi.zazen on 2008-07-02
My best guess is you need to do this in two steps.

Delete sda1 and apply changes.

then select the unallocated space and make a new partition, you should be able to then select extended, again apply changes.

Alternately, just delete the partition and apply changes. Then install Ubuntu and select the option to install into free space.

---

### Post by HotCupOfJava on 2008-07-02
Yes - boot from the live CD (the "Try Ubuntu without making any changes" option). Go to "System"- then - "Administration" at the top tool bar. There is a tool called gparted (Gnu PARTition EDitor). This tool is much better than the Ubiquity partitioner the install process uses. Use it to edit/delete whatever partition you need. THEN reboot and install. When you get to the screen where you choose your partitioning options, choose "use largest continuous free space". This should install Ubuntu in the partition you deleted (or in the space you left behind when you moved a partition). If you intend to leave any Windows partitions on the hard drive, I recommend you run Window's disk defragmenter on those partitions several times before editing the partitions. This will help prevent data loss. Hope this helps.

---

