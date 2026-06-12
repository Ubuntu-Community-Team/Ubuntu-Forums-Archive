---
title: "Install on IBM Desktop with 2 hard drives"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by Glenn_H on 2008-06-03
What is the best way to install ubuntu on a PC with 2 hard drives. I have tried to work out the best way to partition but can't find anything on pc's with 2 hard drives???

---

### Post by gvartser on 2008-06-03
Either configure disks using: 

* RAID 0 = Striped disk, (Presented as one disk with sum of both disks. This also speeds up the disk IO. BUT, if one disk should fail all data is lost.)

* RAID 1 = Mirrored disk, (Everything gets written twice, secure if one disk should fail you still can access data on the one that is left)

To setup RAID is possible from the Ubuntu Install Guide.
[U]
Links of interest:[/U]
* [https://wiki.ubuntu.com/Raid](https://wiki.ubuntu.com/Raid)
* [http://ubuntuforums.org/showthread.php?t=611462](http://ubuntuforums.org/showthread.php?t=611462)
/g

---

### Post by gn2 on 2008-06-03
Size and type of hard drives?

Any OS already installed and which drive is it on?

---

### Post by Paqman on 2008-06-03
When you partition you turn a single hard drive into a number of virtual devices that your PC treats like individual hard drives. So installing to a machine with two HDDs isn't really much different to installing to a machine with two partitions already.

Of course, if you have Windows installed already you can take the easy route and not do any partitioning at all. Use [Wubi](http://wubi-installer.org/).

---

### Post by Glenn_H on 2008-06-03
can you point me to some instructions on how to do this?

---

### Post by gvartser on 2008-06-03
Check this out:
* [http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)


/g

---

### Post by Glenn_H on 2008-06-03
c: drive has windows xp sp2 installed, the d: drive [currently disabled from windows] has nothing on it.

Both are 40 Gig NTFS drives and manufactured by Standard Disk drives.

---

### Post by Patb on 2008-06-03
Glenn,

I'll presume the simplest setup for a start: you have a single boot machine, plenty of space, and want to update to later releases in future.  In this case, you would partition most of your first hard drive, probably designated /dev/sda, as the root file system ie "/".  You would partition all of your second drive, probably designated /dev/sdb, as your /home partition.  

But that is almost certainly over simplistic - I gave specifics merely to answer your question.  The final choice is up to you.  

Here is a good starting point for your choice.  [http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning](http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning)

Cheers, Pat

---

### Post by Paqman on 2008-06-03
> **Glenn_H said:**
> c: drive has windows xp sp2 installed, the d: drive [currently disabled from windows] has nothing on it.

Both are 40 Gig NTFS drives and manufactured by Standard Disk drives.

I'm guessing that Windows doesn't have much spare room left on it's drive. If that's the case leave that one alone and set Ubuntu up on the second drive.

How much partitioning you want to do is up to you. Some options include:

1) Let the installer use the whole second disk.
Advantage: very easy
Disadvantage: installs the whole system onto one partition, making it more of a hassle to reinstall later

2) Use Wubi, telling it to use all 40GB
Advantage: even easier than above
Disadvantage: requires the drive to be formatted to NTFS beforehand (which it may already be). Is also a hassle to reinstall later. 

3) Do some manual partitioning
Advantage: you can create a seperate / and /home partition, giving you a lot of flexibility to reinstall
Disadvantage: can be confusing if you've never done it before, and requires a bit of forward planning.

---

