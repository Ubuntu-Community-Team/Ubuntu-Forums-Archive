---
title: "optical drives"
date: 2014-04-13
forum: New to Ubuntu
---

### Post by james120 on 2014-04-13
I've installed ubuntu 12.04 lts using wubi installer.  I'm just getting around to using the optical drives in the computer.  I have two.  One a dvd-rom, cd/rw and one dvd writer.  Under windows they are listed as e and f.  They both open, eject and will read and I think write as a diaog box came up asking if i wanted to add files to cd- r (i selected write to disk)  I believe both will work, but the operating system hasn't assigned a drive letter to either drives.  When I open the home folder under devices it only shows my other internal hdd and floppy which I never use and have disabled. I guess my question is:  Is it normal to not show drive letters for optical drives under devices or do I need to put the drive letters in myself somehow? Or is this even relevent.  Could it have something to do with the os not being on it's own partion?  Thanks

---

### Post by tripp98 on 2014-04-13
Linux doesnt assign drive letters.  The drives will show up when you put something in them.  Put in a blank cd/dvd and you will see how easy it is to copy things to it.  Brasero is an application that you have that can help you create dvd/cd media.  Check into that program as well.

---

### Post by Double.J on 2014-04-13
Hi there!

incase anyone hasn't said so yet, welcome to the forums!

short answer - totally normal. Long answer below!

So, in answer to your question, maybe it's best to look at those drive letters. This is a Windows convention. Right back when the IBM PC launched in 1981, hard drives were few and far between for home users. Costs were anything up to double the cost of the machine and storage was just a few megabytes. To make desktop computing possible as we now know it, floppy disks were used. Basically the firmware of a machine was sotred on ROM, and system software stored on floppys. You either booted with the system floppy, then removed it to put in your software floppy, or used two floppy drives. Hard drives didn't become popular until the end of the eighties. This means that drive A: and drive B: are used for floppy disks, and drive C: is used for the primary HDD partition in windows. It then adds a new letter to each 'drive' it finds - floppy, partition, optical. So the drive letter of the disc drive may be different on each system depending how many partitions your hard drive has and how many optical/removable disks are connected.

ubuntu runs gnu/linux which is a descendant of unix and uses it's conventions. Now a hard drive and a memory sticks are all pretty similar in how data can be read and write, but optical drives are not - it may be read only, or write once or rewrite-able. So they are assigned differently. Similarly floppy disks are slow to write and are also assigned differently again.

All known devices are listed in /dev. Now a hard drive will show up as
```
/dev/sda
/dev/sdb
/dev/sdc
```Where the last letter is the drive so it could be seen as drive a, drive b, drive c and so on, but it will be helpful to remember them as sda, sdb, sdc. Hard drives can be partitioned to appear as multiple drives, however three partitions on a hard drive to windows look like C:, D:, E:. To linux they look like
```
/dev/sda1
/dev/sda2
/dev/sda3
```note that all these partitions will show up as 'file system **GB' in the file manager, not drive whatever.

So what about the CD? Well when ubuntu loads, it does check for the optical drive and adds it to /dev if found. Now, as i said ubuntu knows that a cd isn't like a hard drive and should be treated differently, so it will be assigned cd0, and the next optical drive will be cd1 and so on. If you look in the file system on your machine you should see 
[CODE]/dev/cd0
/dev/cd1[/[CODE]

so why don't the show up in the file browser even though ubuntu knows about them? Well, you can't do anything with an empty cd tray can you? Pop in a browsable dvd/cd and it will appear ;) 

Typical operation is the picture of a cd as an icon with any name the disk has, then you click on it to 'open'. At this point the cd is 'mounted' by the system and information added at /media/cd/. Always eject a cd through ubuntu rather than the tray (by clicking the eject button.

hope it helps! When I first started out so many of my early questions where about filesystems too ;)

Jj

---

### Post by Double.J on 2014-04-13
Sorry trip98,

i replied to this from my phone, apparently it didn't submit unit i just unlocked it!

Jj

---

### Post by james120 on 2014-04-13
Thank you, that helped alot.  I believe both are working.  It's like and is trying to learn a whole new operating system.  I do like it though and use it for everything except photos.  I have to write everything down so I won't forget it.  Old age I think.  Hopefully the more I use it the better I'll understand it.

---

### Post by Double.J on 2014-04-13
Hey there!

glad to help :D

really glad to hear you are enjoying ubuntu! When you say not pictures, is this because you are dual booting with windows? Don't worry, most of us do! (You inevitably come across some piece of software you need it for... Plus you've paid for it!) it is usually best practice to make a partition for sharing data between windows and ubuntu. It's best to use ntfs. As you've probably noticed, ubuntu can read windows, windows can't read ubuntu. The reason for this is that it's generally not advisable to routinely access windows C: drive for data. Ubuntu will be able to make changes that windows would try to protect itself from. By using a shared ntfs partition, both systems can have access to the data without risk!

Jj

ps there's a great learning resources thread [here]("http://ubuntuforums.org/showthread.php?t=2015424")

---

