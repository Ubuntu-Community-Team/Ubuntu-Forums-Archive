---
title: "Partitioning ... advice required"
date: 2012-05-26
forum: New to Ubuntu
---

### Post by czgirb on 2012-05-26
Currently, I'm planning to install 100% Ubuntu on my system, **CQ40 2GB-RAM 320GB-HDD** with the following partition (all ext4):
[B]
* / ... 10GB ... for OS
* /home ... 300GB ... for my data
* /swap ... the remaining[/B]

I used to separate OS from my data, so ... if clean re-install required. It would affect my data. Is the size is OK? Please advise ...
**Thank you.**

---

### Post by westie457 on 2012-05-26
Just a suggestion for you. 
How does this look to you?

Root = 20-25 GB (lots of room for system files).
Home = 20-25 GB (plenty of room for configuration files).
Swap = 2 GB
Data = The rest (storage of personal files, never gets touched with a reinstall unless you make a mistake).

---

### Post by garvinrick4 on 2012-05-26
> 
* / ... 10GB ... for OS
* /home ... 300GB ... for my data
* /swap ... the remainingI like it. But formatted you will only get total of 289 gig or so I believe.
Just leave 4 or 5 gig for swap. Cannot hurt to have good size swap. 
Make your partitions in Gparted first would be nice also. Can use a 
Live CD (Ubuntu install CD using Try Ubuntu) to use Gparted.
Or can make a disk from Gparted sight.

---

### Post by codemaniac on 2012-05-26
> **westie457 said:**
> Just a suggestion for you. 

Data = The rest (storage of personal files, never gets touched with a reinstall unless you make a mistake).

How about making all the data partitions NTFS ?

---

### Post by 3rdalbum on 2012-05-26
> **czgirb said:**
> Currently, I'm planning to install 100% Ubuntu on my system, **CQ40 2GB-RAM 320GB-HDD** with the following partition (all ext4):
[B]
* / ... 10GB ... for OS
* /home ... 300GB ... for my data
* /swap ... the remaining[/B]

I used to separate OS from my data, so ... if clean re-install required. It would affect my data.

Note that you can have /home in the same partition as / and NOT lose data if you do a clean install of Ubuntu. Most posters here are not aware of this, but it's true as long as you use the "Upgrade" or "Something else?" option of the Ubuntu installer when you're clean-installing to a single partition that already contains Ubuntu.

**TL;DR: You can put /home and / on the same partition and not lose data on a clean install.** With any version of Ubuntu from 10.04 upwards.

Otherwise, if you're wedded to the idea of different partitions, here's how I'd do it.

12 gigs for /
1.5x your RAM for swap - so if you have 2 gigs of RAM, put 3 gigs for swap
Use the rest in /home.

Use Ext4 filesystem for / and /home.

---

### Post by 3rdalbum on 2012-05-26
> **codemaniac said:**
> How about making all the data partitions NTFS ?

Disaster - you'd get slow write speeds and the ever-present threat of losing data and not being able to do a reliable filesystem check.

---

### Post by codemaniac on 2012-05-26
> **3rdalbum said:**
> Disaster - you'd get slow write speeds and the ever-present threat of losing data and not being able to do a reliable filesystem check.

Agree that it is unfortunately extremely slow compared to both NTFS on Windows, and any native Linux filesystem. Still it is the only way to make the partitions cross platform .

---

### Post by fantab on 2012-05-26
I would make 25GB / ; 2-4GB SWAP ; Remaining GB ext4 DATA. Helps me to Clean Upgrade after every new version release.

---

### Post by czgirb on 2012-05-26
[B]At first, I'd like to thank you for all of you, who are willing to share their opinion.
I'm very very appreciate it ... Thank you.
 Since /home is not for data. So, what about this:
* /root ... 30GB ... for OS.
* /data ... the remaining for my data.
* /swap ... 10GB.

Where is the right place for me to put the SWAP partition?
After the /root or after the /data?
[/B]

---

### Post by Sgt-Slyde on 2012-05-26
I have SWAP at the end, after everything else, but my machine as 4 GB of RAM and runs fine with only about 500 MB of SWAP.

I have about 30 GB for Ubuntu root, another 30 GB for OpenSUSE root, and pretty much the rest of my HD for /home/<my_user_name> - then have that mounted as my home directory in both Ubuntu and OpenSUSE.  I don't recommend this setup for everyone as I'm not sure it's stable but it works for me.

Except about the SWAP space - I've heard all the formulae about how much to assign for that but I've never had a problem running very minimal SWAP on any machine with more than 3 GB RAM.

---

### Post by slavssn on 2012-05-26
I'm assuming your real HDD space is about 298 GB. Here's what I'd do:

sda1: **/boot**, 200 MB (ext2, bootable)
sda2: **swap**, 2 GB (not really necessary, but just in case)
sda3: **/(root)**, 20 GB (ext4)
sda4: **/home**, all that's left (ext4, 0% of reserved blocks)

---

### Post by Primefalcon on 2012-05-26
I'd go about 20gb for root

while no I am not using 10gb... I am close... have a look 

```
Filesystem                  Size  Used Avail Use% Mounted on
/dev/sda1                    20G  9.3G  9.2G  51% /
```

no point cutting the space too fine is there? I also have 2gb for swap since on this system I have 1G of ram.. a good rule of thumb is to double the amount of ram you have for swap

---

