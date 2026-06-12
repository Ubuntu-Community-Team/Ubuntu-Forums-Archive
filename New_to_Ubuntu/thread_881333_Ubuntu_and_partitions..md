---
title: "Ubuntu and partitions."
date: 2008-08-05
forum: New to Ubuntu
---

### Post by Delirium_Trigger on 2008-08-05
As far as this goes, I am a complete n00b.
In case it matters, I'm running Ubuntu 8.04 on a Toshiba Satellite A205-S5831.
Bare with me, because I'm trying to post all the info in this one post so I can get a quick response without having to answer 50 questions.

First off..
I installed Ubuntu twice on my computer.
The first time I got it installed I couldn't get my wireless to work.
So I went back to my Vista partition and deleted Ubuntu from the programs and features thinking that would also remove the 50GB partition I gave Ubuntu as well.

The second time I installed Ubuntu I made a smaller partition.. 
I believe I made it about 7GB.
I was unaware at the time that Ubuntu was installed twice.
(Again I am a n00b..)
I did get my wireless working though. :]

I later attempted to delete my older install of Ubuntu using Gparted.
Note that I did this from my fresh install of Hardy since I cannot get the Live CD to work for some reason.
GParted wouldn't let me because the partition was SDA5 or higher..
Something like that.

I did however resize it to 3GB.
Thus I am left with 47GB unallowcated.
Now my question is:
How can I move the unallowcated space to my latest install?

Sorry, I know thats a lot of background info and reading..
Any help would be appreciated.

---

### Post by Paqman on 2008-08-05
> **Delirium_Trigger said:**
> 
Thus I am left with 47GB unallowcated.
Now my question is:
How can I move the unallowcated space to my latest install?


You'd need to use some kind of LiveCD (eg: the Ubuntu one or the Gparted one) since you can't make changes to a partition which is mounted.

If the free space is adjacent to your root partition the job is easy. If not you'd have to move some of the other partitions around to make it adjacent, which can be very slow.

---

### Post by Delirium_Trigger on 2008-08-05
They are side-by-side.
So you're saying I can use my Ubuntu install disc to resize?
Or am I misunderstanding..
I did try the GParted Live CD but it always failed to boot up.
I have no clue what was wrong with it.
If you need more info on that I still have the disc and I can write down what errors it gives me.

---

### Post by Paqman on 2008-08-05
> **Delirium_Trigger said:**
> They are side-by-side.

Then you're in luck!
> 
So you're saying I can use my Ubuntu install disc to resize?

Yep, the Ubuntu LiveCD actually has Gparted on it already. Boot up into a live session and go to System > Admin > Partition Editor.

---

### Post by Delirium_Trigger on 2008-08-05
> **Paqman said:**
> Then you're in luck!

Yep, the Ubuntu LiveCD actually has Gparted on it already. Boot up into a live session and go to System > Admin > Partition Editor.

Awesome!
I'll give this a try and post back my results! :]

---

### Post by Living2007 on 2008-08-05
> **Delirium_Trigger said:**
> I did however resize it to 3GB.
Thus I am left with 47GB unallowcated.
Now my question is:
How can I move the unallowcated space to my latest install?

Sorry, I know thats a lot of background info and reading..
Any help would be appreciated.
IT is posailbe, but make sure no other partition is in the way between the unallocated space and the partition you want to increase.

---

### Post by Delirium_Trigger on 2008-08-05
Okay I ran the live cd of Ubuntu and resized how I saw fit.
Now it says:

(Ubuntu)
/dev/sda7: 68.13GiB 
Used: 65.97GiB
Unused: 2.6GiB

There's no way I've used 65.97 GiB just by MOVING the partition.
I'm clueless as to what the problem is.
Again, thanks!

---

### Post by Living2007 on 2008-08-06
> **Delirium_Trigger said:**
> Okay I ran the live cd of Ubuntu and resized how I saw fit.
Now it says:

(Ubuntu)
/dev/sda7: 68.13GiB 
Used: 65.97GiB
Unused: 2.6GiB

There's no way I've used 65.97 GiB just by MOVING the partition.
I'm clueless as to what the problem is.
Again, thanks!
What is your partition table, and which partition do you want to resize to fill the entire hard drive?

---

### Post by photoman64 on 2008-08-06
I never could make work the gparted so I downloaded boot cd 9.5 and there are some partition programs.

---

### Post by logos34 on 2008-08-06
sda7 is the original ubuntu root, right? If so, since you can boot the ubuntu live cd, you want to delete it (NOT the extended partition holding it!), then grow your adjacent new ubuntu root partition to take up the free space.  Like living2007 said, post your partition table:

**sudo fdisk -l**

---

### Post by Delirium_Trigger on 2008-08-06
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x39633962

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192        9681    76220703+   7  HPFS/NTFS
/dev/sda3            9682       19457    78525720    5  Extended
/dev/sda5            9682       10109     3437878+  83  Linux
/dev/sda6           19054       19457     3245098+  82  Linux swap / Solaris
/dev/sda7           10110       19003    71441023+  83  Linux
/dev/sda8           19004       19053      401593+  82  Linux swap / Solaris
```

Also if this helps at all here's a screenshot from GParted.

[http://img255.imageshack.us/img255/3038/screenshotdevsdagpartedyr4.png](http://img255.imageshack.us/img255/3038/screenshotdevsdagpartedyr4.png)

---

### Post by Living2007 on 2008-08-07
> **Delirium_Trigger said:**
> ```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x39633962
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192        9681    76220703+   7  HPFS/NTFS
/dev/sda3            9682       19457    78525720    5  Extended
/dev/sda5            9682       10109     3437878+  83  Linux
/dev/sda6           19054       19457     3245098+  82  Linux swap / Solaris
/dev/sda7           10110       19003    71441023+  83  Linux
/dev/sda8           19004       19053      401593+  82  Linux swap / Solaris
```
 
Also if this helps at all here's a screenshot from GParted.
 
[http://img255.imageshack.us/img255/3038/screenshotdevsdagpartedyr4.png](http://img255.imageshack.us/img255/3038/screenshotdevsdagpartedyr4.png)
 Well, i'm not sure about the NTFS Partition, because of the Excliamtion Sign, but just select on the partition next to the unallocated space -> select Resize, and drap the slider to the edge. If the partition is blocked by another, you will be unabe to move it, unless the blocking partition is deleted (I guess you don't want that to happen)

---

### Post by lisati on 2008-08-07
> **Living2007 said:**
> Well, i'm not sure about the NTFS Partition, because of the Excliamtion Sign, but just select on the partition next to the unallocated space -> select Resize, and drap the slider to the edge. If the partition is blocked by another, you will be unabe to move it, unless the blocking partition is deleted (I guess you don't want that to happen)
The NTFS partition is likely to be your Vista partition, and is probably best left alone (for now) if you want to keep Vista.

---

### Post by Delirium_Trigger on 2008-08-07
> **Living2007 said:**
> Well, i'm not sure about the NTFS Partition, because of the Excliamtion Sign, but just select on the partition next to the unallocated space -> select Resize, and drap the slider to the edge. If the partition is blocked by another, you will be unabe to move it, unless the blocking partition is deleted (I guess you don't want that to happen)

I'm not sure I understand..
As you can see from the image I uploaded, I already moved the unallowcated space.
I just don't see how all of the space was used up by simply moving it.
I should have 60+GB free instead of 2GB.
Why is this?

Also:

NFTS is my Vista partition. >.<
I have no idea what sda3 is.
sda5 is the partition I would like to delete.
It is my original Ubuntu install.
sda7 is the partition of Ubuntu I am currently on/using.
I would like to make it and Vista my ONLY two partitions.

---

### Post by loligager on 2008-08-08
yo this might be use full to you
[http://www.frozentech.com/content/livecd.php](http://www.frozentech.com/content/livecd.php)

---

### Post by Living2007 on 2008-08-08
> **Delirium_Trigger said:**
> I'm not sure I understand..
As you can see from the image I uploaded, I already moved the unallowcated space.
I just don't see how all of the space was used up by simply moving it.
I should have 60+GB free instead of 2GB.
Why is this?

Also:

NFTS is my Vista partition. >.<
I have no idea what sda3 is.
sda5 is the partition I would like to delete.
It is my original Ubuntu install.
sda7 is the partition of Ubuntu I am currently on/using.
I would like to make it and Vista my ONLY two partitions.

sda4-8 IS basically sda3, it i just an extened partition (logical). This means it that the computer will not boot to it, it is just primarily storage and other. It is capable of contain multiple partitions.

If you want to delete sda5, than sda6 (your linux wasp for the first Ubuntu you installed) needs to eb switched off. Right click on sda6 and select "unlock."

Then select sda5 & sda6 and delete.

PS Not sure why sda7 has more that 60+GB used. Must be something in the partition using it. Look at the disk analyser on that Ubuntu drive.

---

### Post by Delirium_Trigger on 2008-08-08
> **Living2007 said:**
> sda4-8 IS basically sda3, it i just an extened partition (logical). This means it that the computer will not boot to it, it is just primarily storage and other. It is capable of contain multiple partitions.

If you want to delete sda5, than sda6 (your linux wasp for the first Ubuntu you installed) needs to eb switched off. Right click on sda6 and select "unlock."

Then select sda5 & sda6 and delete.

PS Not sure why sda7 has more that 60+GB used. Must be something in the partition using it. Look at the disk analyser on that Ubuntu drive.

Thanks for all your help.
I decided to back up all my files and just wipe my hard-drive completely.
Now I'm using solely Ubuntu.
Again, thanks for all the help!

---

### Post by Living2007 on 2008-08-08
> **Delirium_Trigger said:**
> Thanks for all your help.
I decided to back up all my files and just wipe my hard-drive completely.
Now I'm using solely Ubuntu.
Again, thanks for all the help!
Or you can do what you have done, if all else fails

---

