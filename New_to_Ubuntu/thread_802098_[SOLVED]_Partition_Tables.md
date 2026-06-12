---
title: "[SOLVED] Partition Tables"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by melrom on 2008-05-21
Okay, so I messed up my Windows partition again [surprise, surprise], and I'm going to re-do the tables but I'm still deciding the best plan of action. So right now, it's partitioned pretty crappily [i.e. when I installed it two years ago, I didn't know how frequently I'd be using linux]. It's got about 80 gig windows, 18 gig ubuntu (+ swap), and then a dell utility partition. I was thinking of having a seperate shared NTFS data partition, but ultimately, I can't decide if I want it to be NTFS or not. I'm also wondering if Windows will get snippy about this. :) Moreover, I'm not exactly sure how much space to allocate to the actual OS partitions. 

Anyway, any suggestions?

---

### Post by PinkFloyd102489 on 2008-05-21
Both Windows and Ubuntu could survive on 10 gigs each, if you would be putting everything else into a storage partition. Windows cant handle Linux partitions without tweaking, so it would be best to go with NTFS. Not FAT32 either as it cant handle data transmissions of over 4GB at a time.

---

### Post by rolnics on 2008-05-21
I would agree with Pinkfloyd with his answer, but i would maybe give windows a little more room, but it depends what you are doing with it.

---

### Post by melrom on 2008-05-21
Thanks yeah, I'm thinking. What if I went 20/20. And then 60 NTFS? I've got a 250 gig external, so I don't think I'll run out of space if I only have 60 on the shared.

---

### Post by rolnics on 2008-05-21
Ubuntu / linux would be fine with 10gb, its just from experience of trying to keep windows in 10gb that i personally found hard.

---

### Post by Th3Professor on 2008-05-23
You can go down to 8 GB for WinXP and still put like... one program on it... ;)

---

### Post by logos34 on 2008-05-23
> **rolnics said:**
> Ubuntu / linux would be fine with 10gb, its just from experience of trying to keep windows in 10gb that i personally found hard.

the trick with XP is it will fit just fine on 10gb (even allowing for 15% free space to run defrag) as long as you turn system restore down all the way and move swap to another partition.
Before I dumped my x64 XP it fit cosily in a 9.77 gb partition with a fair number of apps/programs installed.

As far as a shared partition goes, why not just make it ext3 and install fs-driver so windows can access/read/write to it?  It's a popular solution and I don't think there's any issues with it

---

### Post by louieb on 2008-05-23
I have an old desktop w/ XP Home on an 8GB hard drive.
My laptop has XP Pro + Office 2003 in 14 GB partition - uses about 8GB.

On both Ubuntu gets 7GB for / (root) and 5GB for /home. 
The remainder of  of the disk space on both is a data partition. Because I use Linux about 90% of the time their formated ext3. If I used Windows most of the time I would have formated the data partition NTFS.     

Works quite well for sharing data and it also work well when distro upgrade time rolls around. I'll just boot to a live CD and run partimage to backup / and /home to the data partition. 
Then let it upgrade. If it works after upgrading fine. But if it doesn't it a quick restore  to put it back  to a working condition.

---

### Post by logos34 on 2008-05-23
> **louieb said:**
> Then let it upgrade. If it works after upgrading fine. But if it doesn't it a quick restore  to put it back  to a working condition.

That's what I do too.  I wish more people were familiar with partimage and how easy it actually is to use to backup /.  It would sure save a lot of folks unnecessary grief after major updates and upgrade time

---

### Post by Raccoon1400 on 2008-05-23
> **PinkFloyd102489 said:**
> Both Windows and Ubuntu could survive on 10 gigs each, if you would be putting everything else into a storage partition. Windows cant handle Linux partitions without tweaking, so it would be best to go with NTFS. Not FAT32 either as it cant handle data transmissions of over 4GB at a time.

You can tweak windows to read ext3? How?

---

### Post by louieb on 2008-05-23
> **Raccoon1400 said:**
> You can tweak windows to read ext3? How?
[Ext2 IFS Win w/write support]("http://www.fs-driver.org/index.html")
[Explore2fs ext3 viewer - read only]("http://www.chrysocome.net/explore2fs")

---

### Post by Raccoon1400 on 2008-05-24
> **louieb said:**
> [Ext2 IFS Win w/write support]("http://www.fs-driver.org/index.html")
[Explore2fs ext3 viewer - read only]("http://www.chrysocome.net/explore2fs")

Neat! This could come in handy, and even if it doesn't, I like tinkering.

---

