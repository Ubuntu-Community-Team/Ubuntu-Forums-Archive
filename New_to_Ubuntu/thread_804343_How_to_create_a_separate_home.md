---
title: "How to create a separate /home"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by sayakb on 2008-05-23
Hello all
Last time I created 3 different partitions: /home , / and swap
But on starting, Gutsy just froze once nautilus was loaded.
Can you tell me exactly how to create a separate /home
Plus, is 10GB enough for Hardy (which I recently downloaded). I would just be installing a few themes and some apps like thunderbird and a few gstreamer plugins, vlc etc.

---

### Post by iaculallad on 2008-05-23
> **LinuxIsInnovation said:**
> Hello all
Last time I created 3 different partitions: /home , / and swap
But on starting, Gutsy just froze once nautilus was loaded.
Can you tell me exactly how to create a separate /home
Plus, is 10GB enough for Hardy (which I recently downloaded). I would just be installing a few themes and some apps like thunderbird and a few gstreamer plugins, vlc etc.


Try browsing this [page]("http://www.psychocats.net/ubuntu/separatehome") on creating separate /home partition. 10Gig would be just fine for Hardy.

---

### Post by FuturePilot on 2008-05-23
This is a good guide. :)
[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by forestpixie on 2008-05-23
Create the partitions as you have - when installing use manual partitioning method. Edit each of / and /home and select appropriate mountpoint for each pick / for / and /home for /home. When you install it will use those mountpoints.

Is 10Gb enough for what? If you are only using 10Gb you will not have much in the way of a /home partition - / and swap will need to be seperate.

---

### Post by sayakb on 2008-05-23
Don't these tutorials show how to create a /home AFTER installing ubuntu? And a link in the 1st paragraph that guided me to a page which claimed to show how to create a /home BEFORE installation does not even show how to create a separate /home :( :( :(

---

### Post by sayakb on 2008-05-23
> **forestpixie said:**
> Create the partitions as you have - when installing use manual partitioning method. Edit each of / and /home and select appropriate mountpoint for each pick / for / and /home for /home. When you install it will use those mountpoints.
I did that last time, but Gutsy froze as I started it.
 
> **forestpixie said:**
> Is 10Gb enough for what? If you are only using 10Gb you will not have much in the way of a /home partition - / and swap will need to be seperate.
No, I have a 160GB HDD.. Just wanted to ask that is 10GB enough for / or not :)

---

### Post by forestpixie on 2008-05-23
> No, I have a 160GB HDD.. Just wanted to ask that is 10GB enough for / or notMore than enough if you don't intend filling it up :) I have a 10Gb / and it's half full.

> I did that last time, but Gutsy froze as I started it.Can't imagine that's anything to do with the partition layout - I have the same and the only freezes I've had have been either my fault or kernel upgrades during alpha stage.

---

### Post by bumanie on 2008-05-23
Yes, 10g is enough for root, my / partition is usually somewhere between 6-7g.
At the partitioning stage, choose the manual radio button. Then check the space you have allocated for ubuntu from the drive/partition list. Then click edit to be able to edit the partition.
First area is space in mb to allocate
Second area is to choose filesystem format
Third area should be able to choose / followed by swap followed by /home.
These are done in three separate operations of course. I hope that makes sense, I find it easy enough to do, but it is hard to explain without any graphics/screenshots.

---

### Post by sayakb on 2008-05-23
I seem to have installation problems that I have posted in a separate thread :(
Would try these methids as soon as the installer starts!!

---

### Post by ugm6hr on 2008-05-23
> **forestpixie said:**
> Can't imagine that's anything to do with the partition layout - I have the same and the only freezes I've had have been either my fault or kernel upgrades during alpha stage.

Agreed.  This sounds like you are not asking the right question.  It also sounds like you set up your partitions correctly.

10GB for /, 1.5x RAM for swap and whatever you want for /home is fine.

Did the LiveCD work?

---

### Post by sayakb on 2008-05-23
I deleted my existing Gutsy partitions. And checking whether the LiveCD is working or not. Will post the response shortly..

---

### Post by ugm6hr on 2008-05-23
Since this is a single problem - I will close this thread.

Please post in your other thread here: [http://ubuntuforums.org/showthread.php?t=804362](http://ubuntuforums.org/showthread.php?t=804362)

---

