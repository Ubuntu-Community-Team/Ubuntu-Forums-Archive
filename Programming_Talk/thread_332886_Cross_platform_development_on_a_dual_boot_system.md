---
title: "Cross platform development on a dual boot system?"
date: 2007-01-06
forum: Programming Talk
---

### Post by Ansible on 2007-01-06
I'm getting a laptop set up for development on ubuntu and windows.  So far I've got code on both my ubuntu and windows partitions, but I'm thinking it would be better to use one folder for both systems.  The difficulty here is that the windows partition is NTFS, so I'm assuming that means it is read only for linux.  I would allocate a FAT partition, but I already have all the disk space used up on the machine.

I recently saw an article on a windows utility ext2fsd, which allows you to access an ext2 partition through windows.  Here's the link:

[http://www.codejacked.com/automatically-mount-your-linux-partition-in-windows/](http://www.codejacked.com/automatically-mount-your-linux-partition-in-windows/)

Now I'm thinking that the solution may be the best; store all the code on my linux partition and access it from windows.  Has anyone done this?  Are there some other suggestions as to the best way to organize a dual boot system for C development?  Are there wierd snags I should watch out for with this stuff?  How about using SVN from windows and from linux using the same partition?  I suppose I could just try it and see, but I'd hate to get a long way down that road before I find out there's a problem.

---

### Post by Solver on 2007-01-06
[www.fs-driver.org](www.fs-driver.org) is the best way to access the Linux partitions from Windows.

Also, as of recently, ntfs-3g is available on Linux with NTFS write support. It's still beta software technically, but it works perfectly for me so far. It can't handle permissions and encrypted files on NTFS, but works like a charm for simple writing to partition. That's at [www.ntfs-3g.org](www.ntfs-3g.org)

---

### Post by pmasiar on 2007-01-06
or you can create shared FAT partition. Old, safe, rock-solid for both Win and Linux.

---

### Post by Tomosaur on 2007-01-07
I keep my cross-platform code on a USB thumb drive which is left permenantly plugged in.

---

### Post by Ansible on 2007-01-07
Ok, I'm trying out that [www.fs-driver.org](www.fs-driver.org) driver.  just copying files so far (10gb cpp folder), next I'll see if SVN, visual studio, C Builder, etc, work with it or not....

---

### Post by gh0st on 2007-01-07
Reading and writing to NTFS with NTFS-3G is so easy once you get it set up and it works perfectly for me, even if I use a disk intensive app like Azureus on my NTFS partition. I also have an external USB hard drive which is NTFS and now I've got it setup properly I can just plug it in and it pops up on the desktop in read/write mode. I've heard people complain there are bugs but I've only heard unsubstantiated rumors and I've been using NTFS-3G flawlessly for months now (famous last words :-)).

You should be able to keep your code on an NTFS volume and read and write it from Linux or Windows. I've shared stuff between OS's like this before no problem.

Check this thread out, it took me about 10mins to set this up and I'm very happy with it - [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

This thread is written by an NTFS-3G developer and he gives you the repo locations for all the stuff you need. I have used tools to access my ext3 partitions in Windows in the past but I wasn't very impressed by them. I found it easier doing it the other way round. It's a personal choice of course and whatever works for you is the best option but don't write off NTFS-3G without trying it. There's a pun in that last sentence somewhere I know it :D

---

