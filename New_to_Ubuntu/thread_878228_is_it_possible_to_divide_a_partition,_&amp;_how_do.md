---
title: "is it possible to divide a partition, &amp; how do files know which partition to go in"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by johnlvs2run on 2008-08-02
1)  Ubuntu set up one big partition, which has Ubuntu and all of the files.
Is it possible to use gparted to divide this into an extended partition as follows?
If so, what are the things to look for.

ext
/ root - ubuntu
/home (files)

2)  I'm planning to add other logical partitions, and wondering how the files know which 
/home partition to go into, and how do they know to go into /home instead of to / root.  

Thanks.

---

### Post by drs305 on 2008-08-02
> **johnlvs2run said:**
> 1)  Ubuntu set up one big partition, which has Ubuntu and all of the files.
Is it possible to use gparted to divide this into an extended partition as follows?
If so, what are the things to look for.

ext
/ root - ubuntu
/home (files)

2)  I'm planning to add other logical partitions, and wondering how the files know which 
/home partition to go into, and how do they know to go into /home instead of to / root.  

Thanks.

You should only have one /home and one /root unless you have multiple distros on your computer. Fstab tells ubuntu where to look for /home (if separate), /root and /swap.

Gparted can divide the partitions up for you. Backup, backup, backup first of course.

Here is a link for making a separate /home partition if you aren't planning a reinstall:
[Separate Home Partition]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by johnlvs2run on 2008-08-02
I'm adding mint and arch, planning for the partition to look something like this:

ext
/ root - ubuntu
/home (ubuntu files)
/ root - mint
/home (mint files)
/ root - arch
/home (arch files)

> **drs305 said:**
> Fstab tells ubuntu where to look for /home (if separate), /root and /swap.

So after I make /home, it will automatically keep existing email in home instead of in root?  
That's great.  Thanks.

---

