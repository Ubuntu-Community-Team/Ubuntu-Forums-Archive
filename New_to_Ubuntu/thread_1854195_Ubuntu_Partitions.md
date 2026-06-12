---
title: "Ubuntu Partitions"
date: 2011-10-03
forum: New to Ubuntu
---

### Post by JaggedImage on 2011-10-03
I'm new to Ubuntu and loving it. I have Ubuntu installed along with Winows 7. I planned on moving most of my files from Windows to Ubuntu then make the Windows partition smaller and the Ubuntu partition larger. The problem is that I'm using Windows and was about to make the partition size changes when I noticed that there are 3 partitions instead of 2. I didn't do the partitioning, Ubuntu did that for me in the installation process. I never had the drive partitioned prior to installing Ubuntu on my system. The partitions are 8.78 GB and 1.99 GB.

I'd like to know:
1. Can I remove one of them? If so which one?
2. If I can't remove one then which one do I make larger?
3. Is it a case where one of them has the Ubuntu files and the other is the 'swap' space?
4. What is the purpose of 'swap' space?

Thanks

---

### Post by wildmanne39 on 2011-10-03
Hi, did you install using wubi?

You should load ubuntu then open gparted and take a screenshot so we can see what is where.
Thank you

---

### Post by JaggedImage on 2011-10-03
I had used Wubi to try out Ubuntu before doing a real installation. I'll put up the screenshot soon.

---

### Post by Bucky Ball on 2011-10-03
Just a word about resizing your Win partition ...

Defrag several times if poss (Power Defragmenter is free and does a better job that the generic Win defragmenter). Use the Windows software to shrink the partition, not Gparted. 

Best setup, for mine, is:

/ = root partition, where Ubuntu OS is;
/home = partition where all your personal data is;
/swap = swap.

Reason? If you break Ubuntu or want to re-install, all your personal files are in your /home partition and won't be touched. Without a separate /home your personal data would be in /, same place as your operating system (and consequently deleted if you reinstall).

If you want to share files between Win and Ubuntu it's also a good idea to create a /share partition (call it what you like) which is NTFS (not EXT3). Both OSs can see, read and write to that filesystem. Win can't see, read or write to a native Linux EXT* partition. 

Hope that gives you some ideas. When  you take a look with Gparted you will get a better idea of what's happening (if you can get into Ubuntu okay you can just use Gparted there from System>Administration>Gparted (or Partition Editor). Using LiveCD is not necessary unless you actually want to shrink/expand a Ubuntu partition ...

---

### Post by JaggedImage on 2011-10-03
[IMG]http://i1122.photobucket.com/albums/l534/KronosDesigns/Screenshot--dev-sda-GParted.png[/IMG]

---

### Post by wildmanne39 on 2011-10-03
Hi, you can use the 1.99 gig as your swap, at the very least it will be needed to suspend and hibernate your system.

The 8.78 can be used for /root you can change the size if you like, I personally do not make mine to small anymore because I ran out of space when I created a 4 gig that was recommended at the time, but you do not need it larger then it is unless you are going to be installing a lot of packages because most things are not installed to root.

Follow Bucky Ball's advice on everything, he gave good guide lines to follow.
Thank you

---

### Post by JaggedImage on 2011-10-03
What I planned on doing was moving files over Ubuntu and shrinking the ntfs partition that is the Windows partition. I'd like to know if I can remove the 1.99 gb partition. I found out that I can access my files and stuff in Windows from Ubuntu  so I might not go through with the resizing of that partition but I'm  still wondering what I should do about that 1.99 gb partition. Is it really necessary?

---

### Post by wildmanne39 on 2011-10-03
Sorry I was writing this post and never pushed the send button, I was still working on it when there was some kind of glitch,five minutes later I get through with the way I wanted it and it showed all ready posted I am not sure how that happened since I was still working on it, so I sorry, this was not meant to be sent.

---

### Post by JaggedImage on 2011-10-03
Thank you both for your help. I'm very grateful.

---

### Post by wildmanne39 on 2011-10-03
Hi,

There is no way to tell what is in side of it since it is listed as unknown, so it could possibly damage your system, but it is showing not used, if you trust it.
Thank you

---

### Post by Mark Phelps on 2011-10-04
When you go to shrink the Win7 OS partition, be sure to use the Win7 Disk Management utility to do that. Do NOT use GParted to do that.

---

### Post by Bucky Ball on 2011-10-05
> **Mark Phelps said:**
> When you go to shrink the Win7 OS partition, be sure to use the Win7 Disk Management utility to do that. Do NOT use GParted to do that.

+1. As previously mentioned. 

Depending on which Win you are using, that 1.99Gb partition might be some recovery partition or something to do with Win. Maybe have a look in Win disk management and see if that gives you more of a clue. Otherwise, as also previously mentioned, perfect size for your /swap partition.

---

