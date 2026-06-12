---
title: "Disk Access Denied - What Should I Do?"
date: 2022-04-06
forum: New to Ubuntu
---

### Post by timufovi on 2022-04-06
Hello! Help me please! 
In general, I have 2 operating systems installed. They are Linux Ubuntu and Windows 11. 
I bought an SSD 3 months ago, moved windows, then wanted to install linux back(I deleted it before buying the ssd). I accidentally installed it on the HDD instead of the SSD. I didn't notice it for a long time, and then I noticed that the partitions are on the hdd, but the ssd has nothing from linux. 
I destroyed those partitions and installed linux on the ssd without errors. Then I did something to the HDD, I don't remember exactly. And after these actions, no OS can access the disk. There is a conflict between Linux and Windows. Bios can see it, Windows can't see it in Windows Explorer, but if you go into partition manager, it's there, but you can't do anything with it, and Linux can see it, but you can't do anything with it. 
What should I do in this situation?

---

### Post by Bashing-om on 2022-04-06
timufovi; Hello

Maybe it is as simple as that "you" are not authorized to access the file system(s) on the hard drive.

Post back - between code tags - the output of terminal command:
```

sudo fdisk -lu

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

And advise us of which partition you want to look at; we see that we can mount the partition and change the ownership rights.

[INDENT]Maybe yes
[INDENT][INDENT]could be though - not so yes
[/INDENT][/INDENT][/INDENT]

---

### Post by UltimateCat on 2022-04-08
Another way to look at partitions is to open gparted and have a look at the partitions.
If you have trouble looking for the other drive go the the drop down menu in gparted in the upper right hand corner.

---

### Post by yancek on 2022-04-09
>   Bios can see it, 

What is the 'it' you are referring to in that sentence, the HD?  If so, what is on the drive?  What filesystem type?  Posting the information requested in the above posts should provide that information.  Windows will show a Linux partition in tools like Disk Management but you will not be able to see or read any files from windows on a Linux filesystem with a default windows.
  
>  Then I did something to the HDD

That complicates things for you and others trying to help.  Any time you are making changes to a HD or partitions, you need to make note of it as otherwise people trying to help are just guessing but it's a good starting point..

---

