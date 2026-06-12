---
title: "I think I am going to do it."
date: 2008-05-02
forum: New to Ubuntu
---

### Post by andybob on 2008-05-02
So I think it is time to install Hardy.

I have backed up all the important stuff and defragged a million times.  Just still a little nervous as to what my HD looks like:

[IMG]http://i51.photobucket.com/albums/f391/andybob1001/defrag3.jpg[/IMG]

I think I will be fine if I do a small partition.  I am thinking just 8 GB and if I run out of room I will put some one my External HD.

Question, when you do the auto partition does it create a swap partition?
-And
How advanced is the advanced partition tool?

Thanks,


Andybob

---

### Post by Tatty on 2008-05-02
You are fairly low on space on your primary drive there.  Remember that a good general rule for filesystems is to always keep 20% free, otherwise you run into all sorts of fragmentation problems.

Yes stick to 8Gb for hardy and it should all be fine.

The partitioner in ubuntu is excellent, it will automatically create a swap for you, no problems.  Its a very automated process.  Just make sure you read what you are selecting, so you dont erase your windows partition ;)

If you want more fine control over your partitions then you can use Gparted before starting the install, in System->Administration->Partition Editor

---

### Post by NightwishFan on 2008-05-02
If you understand the theory of partitioning its very simple just remember you can set up the partitions before hand so you have like 10-15gb of empty space, then just use the: "Guided: Use largest continuous free space" option, which will take the free space and automatically make an ubuntu ext3, and swap partition, I say 10-15 because if you want 8 you will need to make a little room for the ext3 reserved space and the swap which will amount to 2-3gb perhaps. I recommend more because after you use ubuntu for a while you will want less space on xp. :)

Good luck, and ask any questions if needed.

---

### Post by andybob on 2008-05-03
Just got it all installed and it went perfect.  I am on Windows now but at some point I will get it connected to ethernet so I can download the b43-fwcutter so I can have wireless.  Gotta love Broadcom cards...lol

Thanks for all your help guys, it was a peice of cake.



Andybob

---

### Post by RequinB4 on 2008-05-03
> **andybob said:**
> Just got it all installed and it went perfect.  I am on Windows now but at some point I will get it connected to ethernet so I can download the b43-fwcutter so I can have wireless.  Gotta love Broadcom cards...lol


I have to interject - I STRONGLY suggest not using fwcutter.  It's a lot slower and can have problems with a lot of Broadcom cards.  Read this - [http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

---

### Post by articpenguin on 2008-05-03
or if space is imporant use jfs. It has less overhead than ext3.

---

### Post by bsharp on 2008-05-03
> **RequinB4 said:**
> I have to interject - I STRONGLY suggest not using fwcutter.  It's a lot slower and can have problems with a lot of Broadcom cards.  Read this - [http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

I agree, go with ndiswrapper, you will get the full speed out of your card. When I used the fwcutter my card was stuck at 11mbps ](*,)

Ndiswrapper allowed the full 54mbps, but if you are a little evil (like me) you won't be able to put it in monitor mode for cracking your school's wireless...oops, did I say that out loud?

---

### Post by andybob on 2008-05-03
For some reason I couldn't get the fwcutter to work, I looked into ndiswrapper but I am not sure how to make it work.  Broadcom cards sure are a PITA.  Any help is good. lol
Thanks,



Andybob

---

### Post by bsharp on 2008-05-03
Old, but it is what I used to get mine working:
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper))

---

### Post by fluffman86 on 2008-05-03
Broadcom "just works" out of the box for me.  I just plugged in to an ethernet port and downloaded the restricted drivers.  

Seems to work pretty fast, too... :/

---

