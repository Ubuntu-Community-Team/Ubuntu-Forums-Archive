---
title: "I Can't Find The Disk That I Installed Ubuntu Onto"
date: 2012-12-19
forum: New to Ubuntu
---

### Post by Joebagadounuts on 2012-12-19
I have Windows 7 HE 64-bit installed on my primary hard drive. When I installed Ubuntu, I installed it onto that same hard drive. Now when I shutdown my computer I have the option to boot into either Windows or Ubuntu. The problem is that when booted into Ubuntu I cannot find the hard drive that it is installed on, and it isn't under devices alongside my other drives. I have no idea why this is and would appreciate any help toward fixing this problem.

Thank you

EDITED: I am new to Linux and have found out that the host drive doesn't show up under devices but it is there. I was able to find my files from my installation drive after a little digging. [COLOR=Red]**Pay this thread no mind.**[/COLOR]

---

### Post by The Cog on 2012-12-19
Not an idiot, just finding your way round an unfamiliar system. If you can expand the solution you found slightly, your post would serve as a useful pointer to other people who are having the same problem.

Hope it doesn't offend if I move the post to Absolute Beginners though.

---

### Post by Rockstarever on 2012-12-19
you must have installed with the help of windows installer (wubi) as a result u have all the files on the same drive as as that of windows 7. so when ever you boot into ubuntu mounts only the files that it need and said to be accessed so you have to manually mount them to access the data.

**< How to mount >**

Mounting is done with the mount command.

When mounting, you must tell the mount command what is the device or partition you want to mount and what is the mount point. The mount point must be a directory that already exists on your system. 
For example, to mount your floppy:

[PHP]$ mount /dev/fd0 /mnt/floppy[/PHP]

In this example, /dev/fd0 is your floppy drive, and /mnt/floppy is the mount point. Now when you access /mnt/floppy, you'll actually access the files on your floppy.

**< How to see the list of available drives >**

you can use the following command: 
[PHP]$ sudo fdisk -l[/PHP]



hope so this is your answer. and solves your problem. good luck.

---

### Post by Jvdy on 2012-12-19
do you mean you can't see a drive in file manager like you see in windows explorer c:/ or d:/ drive ? if its what you mean try open nautilus (a folder icon at left side of your computer) klik and open menu go to computer at very top of screen

try look at disk mgr 
hit super(windows)button and type 'disk'(without quotes) and enter

---

### Post by Jvdy on 2012-12-19
you can also mount a partition with a gui tool

type '**disk**'(without quotes) and hit enter

klik on your hdd in left panel at this apps select the partition you want to mount, right click and choose mount

---

### Post by stoopidGuy on 2012-12-19
Also, if the disk isn't mounted, you can use df -h to see if your windows partition even exists.  It'll probably be something like /dev/sdb

---

### Post by audiomick on 2012-12-19
I don't think the problem the OP had was one of mounting.

The original post was edited by the OP to say that the problem is sorted. I think the problem was simply the it wasn't clear how the Linux file system works, i.e. that everything starts at / and one doesn't see drive letters like C: as one does in windows.

---

