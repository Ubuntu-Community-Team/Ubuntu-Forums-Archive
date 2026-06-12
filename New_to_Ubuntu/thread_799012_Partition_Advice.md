---
title: "Partition Advice"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by Mythrandil on 2008-05-18
I'm about to dual boot my laptop with Vista and Ubuntu 8.04.

I'm currently trying to decide on a partition scheme for the hard drive. Naturally i need one around 10gb for ubuntu root and 2gb~ for swap. Now I think I need to partition the rest into about 20-30gb for Vista+apps and the rest for a data partition which both ubuntu and vista share. I was told I don't need a share as the ntfs-3g driver allows reading and writing to ntfs filesystems but from what I understand it isn't optimised for performance and isn't 100% stable. A seperate partition for data also means I can reinstall each operating system without document loss.

First question is have I made the right choices or have I missed something? Second does the data partition need to be fat32? Third is ubuntu's document folder settings etc flexible enough so that I can specify that it shares document folders with vista on the data partition?

Thanks in advance for any advice.

---

### Post by UnWarierMage224 on 2008-05-18
Ubuntu can natively read NTFS partitions.. I've never had any problems with NTFS (stability or otherwise). 

The way I've got it set up, as an example you may want to work off of is

1 NTFS partition for windows XP 
1 Logical partition wherein is contained the following: 
*** 1 NTFS partition for my documents
*** 1 EXT3 partition for my /home
*** 1 EXT3 partition for root
*** 1 swapfile partition. 

Best, 

-'Mage

EDIT: Forgot to mention, with this I can work between Windows/Ubuntu no problem.

---

### Post by Mythrandil on 2008-05-18
So are you mapping win xp my documents to the ntfs partition in the logical partition?

I'm still unsure as I'd prefer to have one data store for both ubuntu and vista so I don't have to worry about where a file is on which operating system.

---

### Post by UnWarierMage224 on 2008-05-18
Yup, that's exactly how it works: one common store, two OSes. 

-'Mage

---

### Post by Living2007 on 2008-05-18
> **UnWarierMage224 said:**
> Ubuntu can natively read NTFS partitions.. I've never had any problems with NTFS (stability or otherwise). 

The way I've got it set up, as an example you may want to work off of is

1 NTFS partition for windows XP 
1 Logical partition wherein is contained the following: 
*** 1 NTFS partition for my documents
*** 1 EXT3 partition for my /home
*** 1 EXT3 partition for root
*** 1 swapfile partition. 

Best, 

-'Mage

EDIT: Forgot to mention, with this I can work between Windows/Ubuntu no problem.

If you were going to follow this layout, i'd suggest the EXT3 for /home fe formatted as a logical partition.

I myself, because of my 80GB HD, I would lay it out as

[LIST]
[*]60GB for Windows XP
[*]2GB for Linux-Swap
[*]And the rest -8MB for Ubuntu.
[/LIST]

---

### Post by louieb on 2008-05-18
> **Mythrandil said:**
> ...around 10gb for ubuntu root and 2gb~ for swap... 20-30gb for Vista+apps and the rest for a data partition which both ubuntu and vista share. 
Space allocation looks good to me.

> **UnWarierMage224 said:**
> ...The way I've got it set up, as an example you may want to work off of is...

I like that setup. Separate the data from the two operating systems. Having a separate /home has its own benefits come update, backup and if you need it restore time. Very similar to what I have on my dual boot computers.

---

### Post by axor1337 on 2008-05-18
i dual booted a friend vista laptop and due to all of the bloatware it kept crashing untill i re sized the vista drive to 45 gb   so he has 
vista 45 gb ntfs
root 25 gb  ext3
swap 2 gb  ext3
share data 28 gb ntfs

---

