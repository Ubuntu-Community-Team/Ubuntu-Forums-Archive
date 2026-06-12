---
title: "New Install Formatting Question (Advise and Specifics Wanted)"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by mrwonx on 2008-10-23
I plan on doing a fresh install for 8.10 when it's released, and I remember reading somewhere in the forums a thread about the recommended partitions setup for Ubuntu. I can't remember it all, and I normally just let Ubuntu auto format the hard drive as it see's fit. I remember it was set up so that you had the system and programs to a set amount of space and the rest went to a separate partition for file, etc. They recommended it because you could then load a new OS over top of the partition, and keep all you files safe.

Guess I'm just looking for recommendations for the best partition setup for Ubuntu.

---

### Post by Crandom on 2008-10-23
I (and probably most people in these forums) would suggest having a 12-15gb / partition and then the rest as /home. That way you can just reformat and copy new files to your / when you upgrade, leaving your /home with all the documents and settings the same.

---

### Post by mikewhatever on 2008-10-23
Check out this guide ->[http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning).

---

### Post by ugm6hr on 2008-10-23
> **Crandom said:**
> I (and probably most people in these forums) would suggest having a 12-15gb / partition and then the rest as /home. That way you can just reformat and copy new files to your / when you upgrade, leaving your /home with all the documents and settings the same.

I manage with just 10GB for **/**; don't forget about 2xRAM for **/swap** (max 1GB is usually enough, unless you use the suspend to disk option).

What you are asking about is having a separate **/home** partition (no need to over-write each time you reinstall).  I would definitely recommend it.

In the past, when problems occurred due to my tinkering, I found that a separate /home (and a backup of /var/cahce/apt/archives) meant that Ubuntu could be reinstalled within about 30 minutes without fuss.  I know - not the best way to learn about Linux, but it certainly got me back to a fully working system faster than a lot of googling...

---

### Post by hyper_ch on 2008-10-23
I used to have a seperate /home partition but now I don't anymore. I don't see much use for it.

---

### Post by mrwonx on 2008-10-24
I'm installing it on a 250GB Hard Drive, so I might go 20GB for Ubuntu, 1GB for the swap, then the rest for /home. The guide cleared up a lot of what I was looking for (what types of partitions, the swap, etc.)

When you reload Ubuntu, will it Automatically see the OS's partition and install it there, or will I have to point it to it each time? I know this probably changes from OS to OS, but I'll probably be sticking with Ubuntu for most of the foreseeable future.

---

### Post by ugm6hr on 2008-10-24
> **mrwonx said:**
> I'm installing it on a 250GB Hard Drive, so I might go 20GB for Ubuntu, 1GB for the swap, then the rest for /home. The guide cleared up a lot of what I was looking for (what types of partitions, the swap, etc.)
Sounds like a good plan.

> When you reload Ubuntu, will it Automatically see the OS's partition and install it there, or will I have to point it to it each time? I know this probably changes from OS to OS, but I'll probably be sticking with Ubuntu for most of the foreseeable future.
You have to reinstall using the manual option, and tell it which partitions are which.

---

### Post by Joe on 2008-10-24
If I'm doing a triple boot of XP, Kubuntu, and Mint, is it possible for me to have separate /home partitions for Kubuntu and Mint or will there be problems since there will be two /home partitions?  Anyone know if it's possible for Mint and Kubuntu to share a /home partition without any problems?

---

### Post by jerome1232 on 2008-10-24
I actually separate out /opt where I install programs out of the repos, like etqw, doom3, and various other programs. 

Instead of separating out my /home I carve out /mnt/data and put symlinks in /home to the data partition (ie Pictures -> /mnt/data/Pictures), I like to keep settings and data separate for the purpose of automatic backups I have set to run. And I like a clean slate every time I goto a new release only bringing my /opt and /mnt/data across installs.

edit:Sharing /home's across distro's is usually a bad choice as your settings for programs will probably conflict.

---

