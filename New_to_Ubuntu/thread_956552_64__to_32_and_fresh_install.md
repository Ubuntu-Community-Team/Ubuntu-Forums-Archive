---
title: "64  to 32 and fresh install"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by natman on 2008-10-23
I have Kubuntu 64 running on my machine, which has a home partition and a " /" partition. I am thinking of doing a fresh install when Kubuntu .10 comes out but using 32 bit instead ( flash never worked quite right and sick only seeing 32bit .debs and usually there is a solution to 32, 64 is good just 32 is that little better and i only have 2gb of ram so why bother)

Anyway if i fresh install a 32, will it screw up any save files or program files ( i have no idea where adept actually stores them in home or / partitions ).

Basically is it safe to have a home partition from a 64 install and have a 32 frsh install for "/"
Hope that makes sense? Thanks:

---

### Post by Paqman on 2008-10-23
> **natman said:**
> 
Basically is it safe to have a home partition from a 64 install and have a 32 frsh install for "/"


That's absolutely fine, it won't make any difference at all.

---

### Post by Crandom on 2008-10-23
Your /home will be perfectly fine, unless you have installed any x64 programs there. You will have to reinstall your / partition.

---

### Post by natman on 2008-10-23
Thats cool thanks, can i ask when adept fetchs a program for me where does it actually store it? ( by default )

---

### Post by markbuntu on 2008-10-23
There are many hidden files in your /home directory which contain configuration files for applications and system sevices. These may or may not translate directly from 64 to 32 bit applications so you should be aware of that.

---

### Post by jerome1232 on 2008-10-23
Generally the programs are stored in /usr
System wide configuration files are in /etc
User specific configuration files are in ~/
(I see no reasons for configs to not translate, I have never seen a program that uses different config setups for 64 vs 32 bit)

---

