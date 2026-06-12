---
title: "Partitioning Trainwreck"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by brett_jackson on 2008-08-03
I just reformatted, and my intention was to dual boot Xp/Ubuntu.. when I was formatting for Xp I created 2x 50Gb partitions, with plans to put Ubuntu on one and Xp on the other.. then I left the rest of the space un-formatted which I planned to use as a file partition accessible by both OS's. So Xp installed fine, then I went to install Ubuntu and it wouldn't install on the other 50Gb partition I had allotted for that purpose. Long story short(er) Xp is now has a 25Gb partition, Linux formatted 132Gb (my original free space) as Ext3 and there is 25Gb of unallocated and 50Gb of unformatted space. To (hopefully) make things clearer here is a screen shot of PartitionMagic:
[[IMG]http://img230.imageshack.us/img230/4236/partitionbo1.th.jpg[/IMG]](http://img230.imageshack.us/my.php?image=partitionbo1.jpg)
So what I want to do is make Linux and Xp both similar sized.. 25Gb maybe.. and then format the rest of the space for music, video, and document storage which can be accessed by both Xp and Linux.. any suggestions? Should I do this with PartitionMagic?

Thanks in advance, 
Brett

---

### Post by Elfy on 2008-08-03
Personally unless you have done a lot of work I would just redo the partitioning and installation, but if you don't want to I would use the partition editor in the buntu livecd. 

Effectively you need to resize the large 132Gb, delete the 50Gb unformatted space, then resize th extended and create some new partitions.

Which would you prefer.

---

### Post by Paqman on 2008-08-03
Your Swap is a bit humungous as well. It only needs to be as big as your RAM, maximum.

For your shared data partition you can either use NTFS (Ubuntu can read/write this natively) or go for Ext3 and install ext2ifs in Windows.

---

### Post by Elfy on 2008-08-03
> Your Swap is a bit humungous as wellDidn't see that next to the 132Gb one :)

---

### Post by brett_jackson on 2008-08-03
Thanks for your help, sounds like starting over is easiest to do.. and yeah I'm not even sure what the swap does (nub lol) I just let ubuntu automatically partition everything.. something I won't let happen next time.

---

### Post by Elfy on 2008-08-04
Firstly - it might be worth getting a livecd partition editor, burn it as an iso and you can boot with -exactly as you did with the buntu download, I prefer [partedmagic]("http://partedmagic.com/") - or you can od it with the buntu livecd.

If you use the ubuntu livecd run this command in a treminla before you start

```
sudo swapoff -a
```

Open the partition editor in the system - admin menu.

Delete the  3 partitions within the extended partition, that is the 50Gb, 132Gb and 5Gb partitions - apply.

You should now have the vista partition and the rest as unallocated space.

Right click in the unallocated space and create an extended partition to fill the space - unless you like to keep some spare.

Now within the extended create - 

ext3 - 25Gb
swap - this depends on whether you want to hibernate or not - if you do then swap=RAM, if not then I have 1Gb RAM and swap which is more than enough swap
NTFS - remaining space

Now you should have inside the extended - 3 new partitions.

That part is done - now start the install and when you get to the partition section - use manual, you will get a new screen.

Select the ext3 partition and towards the bottom is an edit partition button - in the new screen you need to - select use this partition as ext3 and change the mountpoint to /
 Close that window and you will be back at the first partition window - finish

Carry on with the installation - if you get lost, worried or just want to double check post back here.

---

### Post by vikramaditya on 2008-08-04
Sorry, no suggestions re your partitions :( ...but, please consider switching to some other image-hosting service.  Image Shack has an obnoxiously aggressive ad-serving style.

---

