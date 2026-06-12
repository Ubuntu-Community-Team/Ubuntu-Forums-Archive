---
title: "[SOLVED] I have a seperate home partition and want fresh / install"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by jimmy the saint on 2008-10-29
This is going to seem silly, but I want to confirm my logic before I attempt this.  I have two drives set up like this
```

|--------|-----------|---------------------------| Disk1
300MB * * * 40GB * * * * The rest of the drive
Boot * * * /(root) * * * * */home

|----------|--------------------------------------|Disk2
4GB * * * * * * * * * *The rest
Swap * * * * * *Media storage & VBox drives 
```

How do I use the installer to reinstall / with intrepid, while not touching my /home partition?  I tried before and wound up with a new home directory in the tiny / partition.  I am concerned that I may either end up with that, or reformatting my /home partition.

How would I set this up in the partition manager in the installer?

Thanks

JTS

---

### Post by macogw on 2008-10-29
When you get to the partitioning step, choose manual partitioning.  Then make sure you tell your old /home partition to be mounted at /home (and *do* *not* format it).  Tell the / part to be mounted as / and you're good.

---

### Post by Paqman on 2008-10-29
[list]
[*]Go for manual partitioning. 
[*]Select your current / with the mount point as /. Format this parition.
[*]Likewise with swap.
[*]Select your current /home with mount point /home. DO NOT format this partition.
[/list]

---

### Post by jimmy the saint on 2008-10-29
Thats what I thought.  Last time I am pretty sure I did that, but at 2am who can say!

---

### Post by Paqman on 2008-10-29
> **jimmy the saint said:**
> Thats what I thought.  Last time I am pretty sure I did that, but at 2am who can say!

I tend to double check the partition table and write down exactly which partition is what before I do any installing. Backing up beforehand would be sensible, too.

---

