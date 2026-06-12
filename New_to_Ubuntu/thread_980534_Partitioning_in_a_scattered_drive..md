---
title: "Partitioning in a scattered drive."
date: 2008-11-12
forum: New to Ubuntu
---

### Post by fixedvision on 2008-11-12
I have a quick question, I want to dual boot with XP currently installed. I have another hard drive so I moved a lot of files off the current boot drive (C:) and after I did a defragment to clean it up for Ubuntu but I still have files scattered from end to end on the drive.

So my question is, will the manual partitioning work well even with a drive with information peppered across it? I know a lot of times Defrags help keep the files grouped together and leave white space for new partitions. But I'm not sure how the partitioning works with Ubuntu and if it needs a solid block of white space or if it will slide all the scattered files to the windows partition.

Thanks for any advice.

---

### Post by handydan918 on 2008-11-12
The more compacted you can get the files on the ntfs partition, teh better. Running consecutive defrags can help quite a bit. I have done this as many as a dozen or so times prior to install/partitioning.

---

### Post by fixedvision on 2008-11-13
awesome, thanks it worked great!

---

### Post by Kellemora on 2008-11-13
Hi FV

On Winders, some files are shown as IMMOVABLE files during defrag!
But the partition shrinker manages to move them and/or builds a fence around them, hi hi.........
Usually they move just fine when the partitioner moves them!
Same as making WinDOZE think the original drive was only that big.

I wondered about that too when I first started doing partitioning myself.  But played around with different drives installing, partitioning, shrinking and installing Linux programs until I knew what to expect by having those IMMOVABLE files moved.  Not once did it ever cause problems.  And only once, did they not move but were given an extended partition partition all their own, and that was on a super OLDE 10 gig hard drive to start with.
I've even installed Ubuntu on a 4 gig drive and it worked great, no room to add anything else, so I used the 10 gig hard drive for the /home partition.

I may be olde, but I'm having phun learning all this stuff!
It's simply AMAZING the amount of things you can do in Ubuntu and the CONTROL you have over each and every thing!

AS one of the forum members sigline says.  They said I need Windows or BETTER so I got UBUNTU, hi hi...........

TTUL
Gary

---

