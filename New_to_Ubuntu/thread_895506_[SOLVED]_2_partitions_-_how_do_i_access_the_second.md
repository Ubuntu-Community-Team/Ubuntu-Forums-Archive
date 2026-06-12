---
title: "[SOLVED] 2 partitions - how do i access the second?!"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by phantomjoker on 2008-08-20
Hi

Really simply - i have 2 partitions on my HDD, both are accessable from each other - how do i access my other one?

is it like /home/?? 

its not in /media? so where do i find it - by the way - i have 512mb of free space, and my computer is now deleting bits of itself! PLEASE HURRY 

thanks

---

### Post by Potatoj316 on 2008-08-20
go into the places menu and you should see a xGB drive where x is the size of the drive.  Click on that and it will prompt for your password.  Enter your password and your HD will show up on your desktop.  If this works I can help you in setting it up to automount.

I also dont think your computer will automatically delete parts of itself without asking you.  Try emptying the trash, that might clear up some space.  You also could increase your partition size, unless you really want to have your 2 partitions the sizes they currently are.  GParted from your Live CD could help you with repartitioning, and it should be non-destructive

---

### Post by phantomjoker on 2008-08-20
i dont have that - under places i have

home
desktop
computer
cd
floppy
network
connect to server

?!

---

### Post by Potatoj316 on 2008-08-20
post the output of 
```
fdisk -l
```
it may need sudo, i dont know, but probably not

---

### Post by phantomjoker on 2008-08-20
ok -

> Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13681367

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1217        2432     9767520   83  Linux
/dev/sda3            2433        7297    39078112+   5  Extended
/dev/sda5            2433        2494      497983+  82  Linux swap / Solaris
/dev/sda6            2495        7297    38580066   83  Linux

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1b93a530

Disk /dev/sdb doesn't contain a valid partition table


---

### Post by Potatoj316 on 2008-08-20
it looks like you have 2 hard drives but the second one is messed up/has no partitions (makes it unuseable)

to mount partition 2 of hd1 use these commands

```
mkdir /media/hd2
sudo mount /dev/sda2 /media/hd2
```

---

### Post by Elfy on 2008-08-20
I'd find out which partitions you have mounted first

```
df -h
```

and just calm down a bit - although until you get your coursework back that's easier said than done I'm sure :)

You've got 3 threads all dealing with little bits of your problem at the moment - you will confuse yourself and others won't know the rest of the story.

Edit - have you started to try and recover without having anywhere torecover it to?

---

### Post by phantomjoker on 2008-08-20
ok i have found it - i set the partition as a temp so yer - all good....

---

### Post by phantomjoker on 2008-08-20
you dont want to get into how messed up my partitions are - i just lost 3 weeks of gcse coursework because of my **** partion tables, i am in serious hardware/software meltdown here!

---

### Post by Potatoj316 on 2008-08-20
theoretically: you should be able to recover all of your data.  

actually: you probably will have some trouble recovering even part of your data

If the partitions were only removed/recreated then you should be able to get your stuff back because it only changes the partition tables and doesnt do anything to the files.

Have you tried recuva? (windows program) it might help

---

