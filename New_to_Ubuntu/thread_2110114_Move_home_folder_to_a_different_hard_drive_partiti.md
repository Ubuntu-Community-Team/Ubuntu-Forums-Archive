---
title: "Move home folder to a different hard drive partition ?"
date: 2013-01-29
forum: New to Ubuntu
---

### Post by Madarox on 2013-01-29
I downloaded steam beta today and I was going to install team fortress 2.I found out that it will take 10GB out of the 13GB remaining space in the partition I installed ubuntu on(I think) which is too much.I wanted to install it on a different partition but I found out that it won't let me install it anywhere else outside home folder.I assumed that I have to move the home folder in a different partition with more space.Is it possible ? if so,how do I do it ? I got windows 7 installed in one of the partitions(I got 5) if that makes any difference.

---

### Post by omeomi on 2013-01-29
Can't you just create a folder on the other partition and then create a symbolic link from your home folder to that folder?
```
mkdir /otherPartition/teamFortress
ln -s /otherPartition/teamFortress ~/teamFortress
```

---

### Post by Bucky Ball on 2013-01-29
> **omeomi said:**
> Can't you just create a folder on the other partition and then create a symbolic link from your home folder to that folder?
```
mkdir /otherPartition/teamFortress
ln -s /otherPartition/teamFortress ~/teamFortress
```

My thoughts exactly. 

@ Madarox: You will need to replace the labels in the path in the example to match your requirements.

---

### Post by Madarox on 2013-01-29
Hmm,simpler than I thought.I'm supposed to do that after installing the game,right ?

---

### Post by omeomi on 2013-01-29
> **Madarox said:**
> Hmm,simpler than I thought.I'm supposed to do that after installing the game,right ?

No before. You create the folders and then when you install the game in Steam you point it to the symbolic link (~/teamFortress in my example, but can be anything you like)

---

### Post by Bucky Ball on 2013-01-29
Yep. Install the game in /otherpartition/game, then create the symlink in your /home directory in /

You could, in fact, copy all the personal data to folders on another partition (or just copy the existing directories from /home in / to /otherpartition/alternatehomedirectory), delete the folders in your /home directory on / and create symlinks to all of them, which would give you a heap of room in /. 

Test one out and make sure you have the data safely backed up before attempting, though, so you know what you are doing. ;)

* I seem to be contradicting omeomi but if I understand correctly it could be done either way. I was typing this but they beat me to it. ;)

---

### Post by omeomi on 2013-01-29
> **Bucky Ball said:**
> Yep. Install the game in /otherpartition/game, then create the symlink in your /home directory in /

In the OP it was mentioned that Steam wouldn't let him install outside the /home folder. That is why I suggested making the symlink first.

---

### Post by Madarox on 2013-01-29
ok,I still got a problem.The terminal doesn't detect that partition as a directory.The partition name(default name) is 28BC8705BC86CD2E
I tried this:
```
mkdir /28BC8705BC86CD2E/teamFortress
```
And I get:
```
mkdir: cannot create directory `/28BC8705BC86CD2E/teamFortress': No such file or directory

```
It's mounted btw.

---

### Post by omeomi on 2013-01-29
Can you cd to the partition?

Where did you mount it? Usually it is in /media
```
ls /media
```

---

### Post by TheFu on 2013-01-29
The idea to use a softlink to another partition is smart and probably the best, but if you really want to move your HOME somewhere else, that is relatively easy too.

There are 2 steps.
* change /etc/passwd for the specific account to point to the new HOME directory
* move all the files from old-HOME to new-HOME

It really is that simple and you don't need to move any other user accounts, if you don't want.

---

### Post by Madarox on 2013-01-29
> **omeomi said:**
> Can you cd to the partition?

Where did you mount it? Usually it is in /media
```
ls /media
```
Oh,that did the trick.Silly me,lol.
> **TheFu said:**
> The idea to use a softlink to another partition is smart and probably the best, but if you really want to move your HOME somewhere else, that is relatively easy too.

There are 2 steps.
* change /etc/passwd for the specific account to point to the new HOME directory
* move all the files from old-HOME to new-HOME

It really is that simple and you don't need to move any other user accounts, if you don't want.
I currently don't need to move it since I can install the game elsewhere but I will consider that if I needed to do it in the future.

Thanks everyone for the help ! :D

---

### Post by TheFu on 2013-01-29
Putting anything but data under /media seems foolish to me.  That is a temporary place for USB flash drives to be mounted. Real HDDs should be mounted by UUID someplace else AND you probably should never install any programs to a non-Linux file system.  That /media/xxxxxxxx mount point looks like an NTFS or vFAT file system.  I don't think that will work for the running the game server.

---

### Post by Madarox on 2013-01-29
> **TheFu said:**
> Putting anything but data under /media seems foolish to me.  That is a temporary place for USB flash drives to be mounted. Real HDDs should be mounted by UUID someplace else AND you probably should never install any programs to a non-Linux file system.  That /media/xxxxxxxx mount point looks like an NTFS or vFAT file system.  I don't think that will work for the running the game server.

ok,I can do that.Thank you !

---

### Post by Bucky Ball on 2013-01-29
> **TheFu said:**
> Putting anything but data under /media seems foolish to me.  That is a temporary place for USB flash drives to be mounted. Real HDDs should be mounted by UUID someplace else AND you probably should never install any programs to a non-Linux file system.  That /media/xxxxxxxx mount point looks like an NTFS or vFAT file system.  I don't think that will work for the running the game server.

OP is not doing this. The partition is on an internal drive which would be in /media.  They are not creating anything under /media. They are creating folders on an internal partition mounted at boot already in /media.

Incidentally, everything mounts by default in /media for me using Xubuntu 12.04 LTS, including USB dongles. In Ubuntu perhaps /mnt is used for USB devices.

---

### Post by TheFu on 2013-01-29
> **Madarox said:**
> ok,I can do that.Thank you !

Please let me clarify opinion vs fact.
* where to mount things is opinion.
* to not use NTFS or FAT-anything for Linux programs is FACT.

You can use NTFS and FAT for Linux programs, but the programs won't like it and the lack of UNIX-like permissions (especially the execute permission) will likely cause other problems.  For a single script, you can force them to run on a non-Linux file system, but as a program becomes more complex, it is more likely to fail.

NTFS/FAT is bad for anything except data and MS-Windows. Data like videos, music, big data, data that permissions do not matter concerning.  If you want the data to only be viewed by specific users, then NTFS and FAT are bad for that data too.

---

### Post by Bucky Ball on 2013-01-29
> **TheFu said:**
> Please let me clarify opinion vs fact.
* where to mount things is opinion.
* to not use NTFS or FAT-anything for Linux programs is FACT.

You can use NTFS and FAT for Linux programs, but the programs won't like it and the lack of UNIX-like permissions (especially the execute permission) will likely cause other problems.  For a single script, you can force them to run on a non-Linux file system, but as a program becomes more complex, it is more likely to fail.

NTFS/FAT is bad for anything except data and MS-Windows. Data like videos, music, big data, data that permissions do not matter concerning.  If you want the data to only be viewed by specific users, then NTFS and FAT are bad for that data too.

All good points, until now overlooked.

---

### Post by Roll Casket on 2013-01-29
:popcorn:

---

### Post by Madarox on 2013-01-29
> **TheFu said:**
> Please let me clarify opinion vs fact.
* where to mount things is opinion.
* to not use NTFS or FAT-anything for Linux programs is FACT.

You can use NTFS and FAT for Linux programs, but the programs won't like it and the lack of UNIX-like permissions (especially the execute permission) will likely cause other problems.  For a single script, you can force them to run on a non-Linux file system, but as a program becomes more complex, it is more likely to fail.

NTFS/FAT is bad for anything except data and MS-Windows. Data like videos, music, big data, data that permissions do not matter concerning.  If you want the data to only be viewed by specific users, then NTFS and FAT are bad for that data too.

So using NTFS/fat is not recommended. Even if it's possible to run linux apps there,it can be problematic.

---

### Post by SeijiSensei on 2013-01-29
> **Bucky Ball said:**
> Incidentally, everything mounts by default in /media for me using Xubuntu 12.04 LTS, including USB dongles. In Ubuntu perhaps /mnt is used for USB devices.

/mnt is largely deprecated these days in favor of /media.  Usually /mnt is described as a *temporary* mount point.  Now I mount most everything under /media including remote NFS shares.

---

