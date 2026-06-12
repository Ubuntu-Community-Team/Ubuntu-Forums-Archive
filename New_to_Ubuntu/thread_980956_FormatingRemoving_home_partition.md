---
title: "Formating/Removing /home partition"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by varunrajan on 2008-11-13
Hi,

I have a separate /home partition of about 30GB on my laptop, running Intrepid Ibex.

Now I want to format this partition with vfat filesystem, because i want to be able to access(read and write) the partition through my windows XP. 

I would like to know if after doing this, using GParted, say, would I be able to log in using my default user account? I mean, are the details for the user and their configuration files saved in /home or / partitions?

Also, if the user does get deleted please also suggest what I can do alternatively.

Thanks in advance :)

---

### Post by philinux on 2008-11-13
You dont need to do that anyway. It can access ext3 too.

[http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd)

---

### Post by OldGrey on 2008-11-13
Don't format your /home partition, you'll loose all your data and configuration files. phillinux's suggestion is the best.

---

### Post by varunrajan on 2008-11-13
> **OldGrey said:**
> Don't format your /home partition, you'll loose all your data and configuration files. phillinux's suggestion is the best.
No worries there. I have backed up all data and dont care for the configuration files. I just want to delete the home partition so that the / partition will store my user. Is that possible?

---

### Post by Duck2006 on 2008-11-13
> Is that possible?

Yes it is. You have to make a home folder in your / partition, copy all your home files from your home partition, then edit your fstab to tell ubuntu where to look for your new home file, so when you boot next time it knows where to look for the home file. Then format your old home partition.

---

### Post by Kellemora on 2008-11-14
Hi var

I think what you are asking is can you have Smith or Jones under Root instead of under Home

The answer is NO you cannot have a user in the root directory for security reasons.  That being said, root IS the user in the root directory!

I tried it and messed up things ROYALLY, hi hi............

I wanted to keep /home on sda in it's own partition, due to the configuration files, but keep the User Files on sdb and use ALL of sdb only for data files.

I did it, using a lengthy cheat sheet to follow, but still have no idea what I did or why.  But learned the hard way, you can't have TWO /home directories.

TTUL
Gary

---

