---
title: "Partition creating"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by stevh0 on 2008-06-14
Hey Guys, 

Ive been running gutsy from about feb, and i need to split my main ext3 drive into 80% Ext 20% Ntfs

Obviously i would like to do it without losing any data from my Gutsy setup. 

Is there something similar to Partition magic ? that i can use in the same way for linux?

---

### Post by housam on 2008-06-14
use [[COLOR="Red"]_Gparted live cd_[/COLOR]]("http://gparted.sourceforge.net/livecd.php")
or the partition editor on ubuntu live cd ( after unmounting the ubuntu partition )

---

### Post by ukripper on 2008-06-14
> **stevh0 said:**
> Hey Guys, 

Ive been running gutsy from about feb, and i need to split my main ext3 drive into 80% Ext 20% Ntfs

Obviously i would like to do it without losing any data from my Gutsy setup. 

Is there something similar to Partition magic ? that i can use in the same way for linux?

Make sure you create backup of files and data before partitioning.

---

### Post by rraj.be on 2008-06-14
Gparted is Best.


go here for good graphical illustartion
```
[ubuntuforums.org/showthread.php?t=282018]("ubuntuforums.org/showthread.php?t=282018")
```

---

### Post by stevh0 on 2008-06-14
thanx for the replies. 

Is there nothing i can do while booted in linux, while still keeping things semi sane? 

Housam, I cant unmount my ubuntu partition as it is my primary partition that i would like to resize without have any risk for any data loss on here. 

Would it not be easier to use partition magic on a windows box then ?

---

### Post by sam_delta on 2008-06-14
nope, you need to boot from the live cd as you cant resize mounted partitions
if you are in your linux install, your partition is mounted

sam

---

### Post by halitech on 2008-06-14
I can't say for sure but typically windows cant see ext3 drives so I would have to guess that partition magic probably won't see it either but I could be wrong.

my guess would be best thing to do would be grab the gparted live cd and do it from there

---

### Post by rraj.be on 2008-06-14
If you have a windows partition and you are well known with partition magic,

then its the best option that i will say.

But better to try with LIVE CD.

---

### Post by archer6 on 2008-06-14
> **halitech said:**
> I can't say for sure but typically windows cant see ext3 drives so I would have to guess that partition magic probably won't see it either but I could be wrong.
You are not wrong, unless a newer version of partition magic has added this ability. As I have a three year old copy of partition magic (which I have a lot of experience with) and it could not see the ext3 partition. 

> **halitech said:**
> my guess would be best thing to do would be grab the gparted live cd and do it from there

I certainly agree with this statement as it worked perfectly for me. 

Cheers

---

### Post by housam on 2008-06-14
As I've  mentioned above , use the Gparted live CD . it is the best solution.

---

### Post by Duck2006 on 2008-06-14
Or parted magic.

[http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)

---

