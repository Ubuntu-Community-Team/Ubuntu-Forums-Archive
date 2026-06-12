---
title: "fresh upgrade in dual boot"
date: 2012-08-17
forum: New to Ubuntu
---

### Post by DarinB on 2012-08-17
Hi 
I have been looking for a tutorial. 

I have windows vista dual boot with 10.04

i want to do a fresh upgrade to 12.04 lts. 

I will have everything backed up. 

I am not sure what to do with the partitions of 10.04

should I just erase them all via windows disk manager and then follow a dual boot from scratch? 

or can I pick the partitions and delete what is in them? 
I am not sure what to do. 
thank you so much....

---

### Post by Kickinthedoor on 2012-08-17
Either method shoukd work just fine. I did the same thing the other day and just deletd the partion and started from scratch. It seemed easier at the time, good luck

---

### Post by irv on 2012-08-17
There are a lot of howtos out here if you just do a search.
Here is a couple of them.

[http://opensource-sidh.blogspot.com/2012/04/ubuntu-1204-installationdual-boot-with.html]("http://opensource-sidh.blogspot.com/2012/04/ubuntu-1204-installationdual-boot-with.html")

[http://news.softpedia.com/news/Installing-Ubuntu-12-04-LTS-266201.shtml]("http://news.softpedia.com/news/Installing-Ubuntu-12-04-LTS-266201.shtml")

---

### Post by oldfred on 2012-08-17
I do not like using Windows to do anything with LInux partitions. Best to use Windows tools on Windows partitions to shrink or expand and Linux tools - gparted to add, change or delete Linux partitions.

If you are fine with your current partitioning you can do a clean install overwriting your existing install and restoring data from your backups.

But if you want to change partitions then now is the time. You may want to consider a separate /home to make new clean installs easier as it will then reuse your data and/or a separate NTFS share data partition to make it easier to share Windows data without directly writing into the Windows system partition.

If you have room and want to create a separate /home first:
To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by Deepak J on 2012-08-17
Installing from the scrap is always good as it eliminates all the unwanted files that were used by the older versions.

---

