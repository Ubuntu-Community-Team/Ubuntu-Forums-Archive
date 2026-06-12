---
title: "Total Newbie Question"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by deell2 on 2008-04-23
Hi Guys

Sorry if you've heard this a million times before but - I have a Toshiba Satellite Pro Laptop running Windows XP Pro and a 60Gb drive divided into two logical 30Gb drives (C: (system) and D:) both are NTFS partitions.  I want to install Ubuntu on Drive D: with the option to boot into XP or Linux when starting up the laptop.

Question: I haven't got a clue how to go about doing this,  is there a beginners/dummy guide giving step by step instructions, or am I hoping for too much ?

---

### Post by Canis familiaris on 2008-04-23
You cannot install Ubuntu on the Windows D: because Ubuntu requires its own native filesystem like ext3 ot ReiserFS.
You first need to either resize or delete your D: partition and create two partitions for Ubuntu. One Root partition and one SWAP partition.

In case you do not want to risk playing with partitions, I suggest you wait for Hardy (new ubuntu version to release) and install Ubuntu in Wubi environment which will not require you to modify your file system and will install in a disk image. (i.e. as a file in D: )

---

### Post by wormser on 2008-04-23
You should read. threw this whole [site]("http://www.psychocats.net/ubuntu/index.php").  Then wait until tomorrow and download the new version.  You might be interested in the Wubi installer.  Search the forums for a howto.[URL="http://www.psychocats.net/ubuntu/index.php"]
[/URL]

---

### Post by jeffus_il on 2008-04-23
Download the Ubuntu Live CD and burn it. Make sure your D: partition is empty. Delete it. Boot from the Live CD and run Install. Make sure that Ubuntu uses the non partitioned space to do a default install. You automatically get Grub installed for a dual boot.

---

### Post by Nepherte on 2008-04-23
The easiest solution is to remove the D partition in Windows. Don't create a new partition but leave it be Raw data. Then you install Ubuntu and during the installation, choose to install it on the disk with the most free space. Another option is to choose to install it on a specific disk. You have a list of sda1..sdan, sdb1..., etc. The a means first physical hard drive, b means second physical hard drive, ... So Sda1 means first partition on disk a, Sda2 means second partition on disk a. Most likely your c: partition will be sda1 and your d: sda2. But if you're not hure, ask here again.

---

### Post by chogoria on 2008-04-23
I'm facing a similar promlem to this thread starter

> **jeffus_il said:**
> Download the Ubuntu Live CD and burn it. Make sure your D: partition is empty. Delete it. Boot from the Live CD and run Install. Make sure that Ubuntu uses the non partitioned space to do a default install. You automatically get Grub installed for a dual boot.

I want to install Ubuntu onto my D:. So I've got rid of any files off of it by moving them onto my C:. What do you literally mean by 'deleting the partition' and how would I go about doing this?

---

### Post by cOzAtS on 2008-04-23
> **chogoria said:**
> I'm facing a similar promlem to this thread starter



I want to install Ubuntu onto my D:. So I've got rid of any files off of it by moving them onto my C:. What do you literally mean by 'deleting the partition' and how would I go about doing this?


First I recommend backing up all your files (just in case as i see you don't even know how to delete a partiition...no offense:D). The right click my computer>manage>disk management(or something like that). You should see the partitions there, c: and d: Right click on d: and delete it (be sure you've back up everything and it IS the D: partition. Put the live CD and follow the instructions, its quite simple. BUT be careful cause during the install you wont see c: and d: but sda sdb etc. Normally you will see c: as sda1 and d: as sda2 or (raw image or unpartitioned, don't remember well). Go with sda2 (or whatever the name). 

Oh, an something important, if you cant understand something be carefull or you might end up deleting windows and your files too.

The best option to avoid all this stress is wubi,wait till tommorow and get Hardy, it will all be done a lot more safe and easier than all these. Its up to you!

Hoped that helped!

*I case you delete d: partition and for some reason want it back for windows use follow the same way but instead of delete right click and format the unpartitioned space. *

---

### Post by candtalan on 2008-04-23
> **deell2 said:**
>  a 60Gb drive divided into two logical 30Gb drives (C: (system) and D:) both are NTFS partitions 

The (semi)automatic installer on the live cd will only see a hard drive which is full of NTFS. I do not know how (or if) it will resize one or both partitions, it might give a choice, not sure.
However, a much more certain approach is to initially use the ubuntu live CD which I think contains a partition editor (gparted) to re size (shrink) your D partition to 20GB so you have about 10GB space on the drive. Do not create a new partiton in the space nor format or such, simply leave the 10GB space un allocated. After you do this, and then run windows (XP?), it will probably want to check itself initially.

Then when you use the live CD installer, choose the option to install into the largest unallocated space on the drive. (your 10GB space will be chosen automatically).

You will then have ubuntu installed into approximately 10GB on your HD. It will be a dual boot machine.

Note that any partition editing has the (small) possibility of seriously loosing all of your data on the HD, not just the one partiton, so take backups seriously first, if you go this way.

Good idea also to scandisk for errors first also and defrag at least once also.
good luck

---

### Post by deell2 on 2008-04-23
Hi Guys

Thanks for all of your advice so far.  I've downloaded Ubuntu-Server 6 and burned a CD.  I can see the list of files and directories on the CD (.disk, dists, doc, install etc.) but how do I now start the install process ?  I have tried re-starting the laptop with the CD in the drive but it just starts up XP as usual.

---

### Post by ivze on 2008-04-23
> **deell2 said:**
> Hi Guys

Thanks for all of your advice so far.  I've downloaded Ubuntu-Server 6 and burned a CD.  I can see the list of files and directories on the CD (.disk, dists, doc, install etc.) but how do I now start the install process ?  I have tried re-starting the laptop with the CD in the drive but it just starts up XP as usual.
1. The CD is bootable, so it seems that the trouble is with your laptop (may be, see manual on how to boot from cd).
2. you should have downloaded 'desktop' version =) If you manage to install what you've got, you will get a nice text interface.
3. Better wait a day and download Hardy Heron. And see wubi.

---

### Post by cOzAtS on 2008-04-23
First of you dont need the server edition, at least not if you need graphic enviroment to work. Server edition comes with just command line. I suggest you get the normal ubunt live cd.

After that when you start your pc hit DEL or F2, it will get you to the BIOS menu of your motherboard. In the boot menu you will see the boot device order. Make sure your cd-rom is first and your hard disk second. Save changes and exit having the live cd in the drive. If you done it correctly it will start ubuntu after a while. In there there is an install icon on desktop. Hit it and welcome to Ubuntu. :)

---

### Post by cOzAtS on 2008-04-23
> **ivze said:**
> 3. Better wait a day and download Hardy Heron. And see wubi.

Quoted for emphasis!!

It's just some hours away!

---

### Post by chogoria on 2008-04-23
> **cOzAtS said:**
> First I recommend backing up all your files (just in case as i see you don't even know how to delete a partiition...no offense:D). The right click my computer>manage>disk management(or something like that). You should see the partitions there, c: and d: Right click on d: and delete it (be sure you've back up everything and it IS the D: partition. Put the live CD and follow the instructions, its quite simple. BUT be careful cause during the install you wont see c: and d: but sda sdb etc. Normally you will see c: as sda1 and d: as sda2 or (raw image or unpartitioned, don't remember well). Go with sda2 (or whatever the name). 

Oh, an something important, if you cant understand something be carefull or you might end up deleting windows and your files too.

The best option to avoid all this stress is wubi,wait till tommorow and get Hardy, it will all be done a lot more safe and easier than all these. Its up to you!

Hoped that helped!

*I case you delete d: partition and for some reason want it back for windows use follow the same way but instead of delete right click and format the unpartitioned space. *

No offence taken, the more basic your instructions the better tbh. Thanks for your help so far. So you think using Wubi will be a lot better and easier than a (dare i say) *standard* install? 

After deciding to use Wubi would I still need to delete the D: partition or will Wubi sort everything out itself. Will Wubi still install onto another partition?

---

### Post by Sef on 2008-04-23
> After deciding to use Wubi would I still need to delete the D: partition or will Wubi sort everything out itself. Will Wubi still install onto another partition?

Wubi will sort everything out.   Wubi does not install onto another partition.  Read about [wubi]("http://wubi-installer.org/").

---

### Post by aschaetter on 2008-04-23
Wubi will install Ubuntu inside your windows partition, so no other work is needed. You just follow the on screen instructions.

---

### Post by chogoria on 2008-04-23
> **Sef said:**
> Wubi will sort everything out.   Wubi does not install onto another partition.  Read about [wubi]("http://wubi-installer.org/").

> **aschaetter said:**
> Wubi will install Ubuntu inside your windows partition, so no other work is needed. You just follow the on screen instructions.

Thanks to the both of you for your help. I'll give Wubi a go tomorrow.

---

