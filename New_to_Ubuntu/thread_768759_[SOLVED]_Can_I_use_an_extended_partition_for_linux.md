---
title: "[SOLVED] Can I use an extended partition for linux-swap?"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by the8thstar on 2008-04-26
I know how to use Gparted to create, edit and delete partitions. Since I already have 4 active partitions (see my sig) and no swap, I was wondering if I could create a 2Gb extended partition which I could assign as linux-swap.

Apparently gparted would only format it to extended, not to linux-swap. Is there a way around that?

---

### Post by vanadium on 2008-04-26
For sure, you can create a swap partition in an extended partition. In fact, that is how the Ubuntu installation program does it by default when you instruct it to use the entire drive.

---

### Post by the8thstar on 2008-04-26
Okay, from there what do you recommend I do? Should I use fdisk -l to know my partition and edit fstab accordingly? How do I automount this partition? with swapon?

---

### Post by forestpixie on 2008-04-26
To add an extended partition you will need to lose one of the others or change an existing primary to extended. I'm not sure that you can change a primary to extended though. If you can I guess the best one to change would be the home - it will also need changing in fstab as it will have a different position. IF you can't change type then you will have to delete a partition - then make an extended partition, inside that you can then reinstate the deleted partition and add a swap

---

### Post by the8thstar on 2008-04-26
> **forestpixie said:**
> To add an extended partition you will need to lose one of the others or change an existing primary to extended. I'm not sure that you can change a primary to extended though. If you can I guess the best one to change would be the home - it will also need changing in fstab as it will have a different position. IF you can't change type then you will have to delete a partition - then make an extended partition, inside that you can then reinstate the deleted partition and add a swap

Perhaps I'm missing your point, but if you're right, then what's the interest of having extended partitions over primary partitions if they can't exceed 4 per disk?

---

### Post by maniac_X on 2008-04-26
> **the8thstar said:**
> Perhaps I'm missing your point, but if you're right, then what's the interest of having extended partitions over primary partitions if they can't exceed 4 per disk?
You can have many partitions in an Extended partition. Extended partitions aren't limited to the "4 partiton rule". :)

What forestpixie is suggesting for you is:

Primary:FreeBSD
Primary:Vista
Primary:Ubuntu
Extended: Logical1:Swap, Logical2:Home, Logical3:etc

---

### Post by forestpixie on 2008-04-27
Exactly - you can have a maximum of 4 primary or extended partitions on any hdd - extended partitions can contain many logical partitions.

Windows won't install to an extended partition to the best of my knowledge but Ubuntu, and I assume other unix types, will install to logical partitions.

There are many pages on the net regarding how many partitions are allowed - [this]("http://www.linuxquestions.org/questions/general-10/partitions-logical-vs-primary-528766/") is one of them.

---

### Post by louieb on 2008-04-27
The way it works is primary + extended partitions less than or equal to 4.
You are allowed one and only one extended partition.
To get more that 4 partitions  you make logical partitions inside the extended partition. Example.


[LIST=1]
[*]primary 1
[*]primary 2
[*]primary 3
[*]extended 4
[LIST=1]
[*]logical 5
[*]logical 6
[*]logical ,,,
[/LIST]
 
[/LIST]
So if you already have 4 primary partitions. You will have to sacrifice one  (delete it) and create an extended partition in its place.  
Then you can subdivide the extended partition into logical partitions.  
lou.

---

### Post by the8thstar on 2008-04-27
Thanks for clearing this out for me guys. I thought I could have 4 primary partitions + any number of extended ones. Now I understand it's 3 primary + 1 extended in this config.

I don't think it's worth the hassle to move my /home around just to creeate an extended partition with /swap on. Also, both Windows and FreeBSD require a primary partition to install anyway and moving Windows files around the disk is always a daunting task.

However, I do thank you all for taking the time to share your knowledge with me. Now I can share it back with other people on the forums. :)

---

### Post by Moop on 2008-04-27
XP doesn't require a primary partition. It installs fine to logical partitions too.

---

### Post by forestpixie on 2008-04-27
You can use swap files instead of a swap partition -

[https://help.ubuntu.com/community/SwapFaq#head-75ffcb00cefe143fc380f84d7ea9203f16a596d0](https://help.ubuntu.com/community/SwapFaq#head-75ffcb00cefe143fc380f84d7ea9203f16a596d0)

---

### Post by the8thstar on 2008-04-29
Excellent tip, **forestpixie**! I followed the tutorial and set a 2Gb swapfile in my home partition.

Thank you so very much! :D

---

### Post by forestpixie on 2008-04-29
Excellent would say mark thread solved - but I don't think the tool is back yet :)

Glad I could help.

---

