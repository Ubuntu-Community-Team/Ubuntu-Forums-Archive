---
title: "[SOLVED] Partitions..."
date: 2008-10-27
forum: New to Ubuntu
---

### Post by economy on 2008-10-27
Hi all,

Here's the situation:

About 2 months ago I decided to dual boot my laptop with Vista/Ubuntu (Vista installed first). My Vista installation is big and has a lot of files on it, and so the Ubuntu installation is only partitioned to use a small amount of the hard disk. 

I have decided to keep Vista, but I'd like to move my files to the Ubuntu installation and increase the partition size so that the large majority of my disk space is used by Ubuntu instead. I have gparted, but of course you can't modify partitions in use. 

I'd rather not reinstall Ubuntu as I have a lot of settings and programs I really like here on this partition. Is there any way to increase the partition space on Ubuntu after I move the files from Vista to a removable HD (thus freeing up the space)? If not, is there a way to save my Ubuntu settings so a reinstall would be quick and painless?

I've come to rely on this forum, have had some great answers here, so thanks for any help you can give.

---

### Post by drs305 on 2008-10-27
Yes, you can do this. Of course the first thing to do is to backup your important data from both partitions. The second thing to do is to run the windows defrag program to ensure the data in the windows program is at the front of the partition. If you are paranoid, do it twice. ;-)

You can shrink the windows partition after moving your data out of it. Many would choose to use a windows partitioner such as Partition Magic but gparted can do it as well.

Once you have shrunk the windows partition, you will most likely have:
windows empty ubuntu

To expand ubuntu, as you correctly stated, you will have to exit the OS. You can use the livecd, a dedicated gparted cd, or a systemrescue cd to do this. I like having a systemrescue cd on hand, but that is personal preference. You can download it here: [http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page") Using any of these methods you will start gparted from outside ubuntu and resize the partition while it is unmounted.

One thing that you will find is that expanding a partition to the left, which is probably what you will be doing, takes longer than expanding to the right. Another option would be to create a data or /home partition out of the newly created space and not move your linux system at all. Just something to think about.

---

