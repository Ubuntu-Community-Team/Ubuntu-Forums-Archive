---
title: "Partition Help"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by Ericthegreat on 2008-07-27
i have to do a manual partition my hdd im installing ubuntu on my esata hdd what i should do is give 1gb to swap (only 512 ram) and the other 14 gigs to ext3 mounted on / right?

---

### Post by jamesrfla on 2008-07-27
Are you planning to just use the entire drive for Ubuntu? That will be enough for SWAP and yes that is what you do for the EXT3.

---

### Post by Ericthegreat on 2008-07-27
no its just a partition of the drive is that ok?

---

### Post by Pro-reason on 2008-07-27
Yes, that sounds fine.  You might want to have a separate partition for your personal files though, to keep them apart.  

I have Ubuntu on a reiserfs partition, and my own stuff on an ext3 partition.  It's up to you though.

> **Ericthegreat said:**
> no its just a partition of the drive is that ok?

I think he meant, do you intend to put another operating system on there too?

---

### Post by Ericthegreat on 2008-07-27
personal as in "files you would want to keep hidden" or as in video files ect?

---

### Post by Pro-reason on 2008-07-27
> **Ericthegreat said:**
> personal as in "files you would want to keep hidden" or as in video files ect?

Your own files, which belong to you.  They can be your bank records, your family photos, your MP3 collection, your kiddie porn, whatever.  People often like to keep that stuff separate, so that you can reinstall the operating system without touching your own files.  It also makes it easier to access if you have more than one operating system installed.

---

### Post by Ericthegreat on 2008-07-27
without a /home partition will i have a /home folder?

---

### Post by RequinB4 on 2008-07-27
> **Ericthegreat said:**
> personal as in "files you would want to keep hidden" or as in video files ect?

Part of ubuntu filesystem is the directory /home/, which has the personal (read: ALL data files, documents, work, games, whatever specific to the user) files of each user on it. The rest of the filesystem (read: everything off of / BUT /home) is ONLY used for files that tell your computer how to operate, program files (not the preferences in those programs, that goes in /home too), the access points to your external drives, etc, go elsewhere in /.

Some (Myself included) say you should have a seperate / and /home partitions (this is done under manual install - mount point have one mount point / and one mount point /home) for a few reasons:

1)  You can completely trash your system and still be able to recover all of your personal files
2) You can install multiple operating systems on the same computer and keep all your personal files just the way you like them, just mount the /home
3) Makes reinstall a sinch - just replace the / and mount the existing /home

Edit - without a /home partition, you will still have a /home folder that does the exact same thing, it just won't have the advantages above.

---

### Post by Ericthegreat on 2008-07-27
I see well then should my / partition be small? what size should it be since i tryed making one for / and one for / home but when i made the / partition 5000 it said the other 10000 free space was unusable?

---

### Post by RequinB4 on 2008-07-27
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

> If you choose to create a separate /home partition, allocate between 5 and 10 GB for the / partition—that's about all you'll need for the Ubuntu system and programs. The rest should be for your personal files (in /home). 

Good reading in general in that link

---

### Post by Ericthegreat on 2008-07-27
Actully i was thinking 
i have 230 gb on this drive for personal files so.... do i really need a separate /home partition?

---

### Post by Sef on 2008-07-27
Root should be about 8 - 10 GBs.

With ram below 1 GB, then swap should be 1 1/2 - 2x ram.   With 1 GB and above, only 1 GB swap is needed, if it use as all.

The rest should be used for home.

---

### Post by ath2o on 2008-07-27
I too have just started trying to install on my home system that already has XP loaded. I have tried to follow the instructions for a dual boot from Smart Computing [http://www.smartcomputing.com/editorial/article.asp?article=articles/archive/r1006/39r06/39r06.asp&guid=](http://www.smartcomputing.com/editorial/article.asp?article=articles/archive/r1006/39r06/39r06.asp&guid=) but the partitioning failed in Gparted. Are there any other threads that I should read to get the drive partitioned correctly?

---

### Post by Pro-reason on 2008-07-27
My Ubuntu is on a 40GB partition, and it's 3/4 full already.  I wouldn't advise trying to squeeze it on to a smaller partition.  You don't want to have to resize it just because you decide to install a whole load of software later.

The old rule of thumb about having twice as much swap as RAM doesn't make sense.  One gig of swap is a sensible amount for everyone.

---

### Post by Ericthegreat on 2008-07-27
yes but sence i have a partition with 230 gigs do i really need a /home partition sence that would pretty much be my main storage?

---

### Post by RequinB4 on 2008-07-27
> **Ericthegreat said:**
> yes but sence i have a partition with 230 gigs do i really need a /home partition sence that would pretty much be my main storage?

The benefits from having a seperate /home partition are completely seperate from how much space is actually on the partition.  It's good that you have room to spare (which means you should have a 10GB+ish / partition), but you're going to want to protect your personal files no matter how many of those files you have :P  See my above post

---

### Post by Ericthegreat on 2008-07-27
ok how about this i will use 1000 mb for swap it auto makes it 1003 leaveing 15109 mb how would you split between / and /home

---

