---
title: "Help with partitions in hardy"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by evilkastel on 2008-10-15
well, at first I installed Kubuntu with wubi. Since i liked Ubuntu, but no so much the KDEI decided to delete the Wubi-Kubuntu and installed Ubuntu from the live cd, leaving me with these:
35GB NTFS partition with WinXp
15GB ext3(i guess, i let ubuntu auto assign partitions) with Ubuntu
100GB partition NTFS no boot, just files. music video, etc.

I've decided I'm a keeper and I'll like to use ubuntu as main OS. so, to make my life easier i want:
35GB WinXp (hopefully keeping the same 35 GB partition untouched). 
Also i want to delete my 100GB NTFS (backing up in dvd the content) and add that space to ubuntu's 15 GB.

Is there anyway to do this without deleting all the partitions and start from scratch? Is there a way to do this keeping my current Xp and Ubuntu (as they are), so I don't have to install any OS?

Thanx for your help

---

### Post by TCSnyder on 2008-10-16
GParted is like a livecd you can boot from it and i think you should be able to format your 100 gb partition and add it to your ubuntu partition. it should show your partitions and you should see your 100 gb one there. then you should delete it and it will turn into unallocated space. then you should be able to add it to ubuntu

---

### Post by Cl0ud9 on 2008-10-16
You definitely won't have to reinstall XP.
I don't know how to merge partitions, but I recommend just using the 100GB partition as a seperate /home partition. This way you won't have to touch the main Ubuntu installation, and there are many advantages in having a separate /home partition. Google it to find out more.

Anyway the first step would be in backing up all of the data on the 100GB partition.

The use Gparted to make the 100 GB ntfs partition an ext3 partition.
```

sudo apt-get install gparted

```

There are many guides on the web on how to use gparted. Again Google to find one.

After you have the 100 GB ext3 partition just follow this [guide]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/") to mount your /home directory on that partition.

---

### Post by evilkastel on 2008-10-16
Gparted it is.... I can't believe this. Not 5 minutes had passed and already you solved this issue... I looked up, It shall do just fine, and I'm listening to you Cloud, I'm making it a /home. this is one of the gratest things about linux, the people. But i'm getting offtopic here. Gparted solves my problem, so, thank you guys very much.

---

### Post by trikster_x on 2008-10-16
Okay, this is actually pretty easy as long as gParted doesn't want to be stupid.  You'll have to boot in the liveCD to edit your partitions, since you can't edit mounted partitions.  If you want to just wipe all of the 100GB partition, all you need to do is reformat it.  Obviously this is after you have backed up all your media.  Then you just resize the partition Ubuntu is on.  This shouldn't cause a loss of any data, but you will want to back up important files anyways.  If your swap partition is between the 100 gb and Ubuntu, you will need to move that to the end of the empty space before you can resize the Ubuntu partition.  If the 100 GB is next to ubuntu, then it is a simple matter of resizing that partition to take over the 100GB.  If you take your time and think before you actually do anything, you'll be fine.

---

### Post by Keen101 on 2008-10-16
yeah the Gparted Live-CD should do what you want.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

