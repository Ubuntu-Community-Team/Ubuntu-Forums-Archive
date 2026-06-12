---
title: "Partition sizing for dedicated Samba file server."
date: 2008-07-09
forum: New to Ubuntu
---

### Post by _SiM on 2008-07-09
Hi everyone,

I am new to the forums. Used Ubuntu on my desktop a couple of weeks a little ago, but it broke when I changed graphics cards - so I am still a noob, but slightly familiar with a few things :)

I have 3 x 1TB hard drives which I would like to put into a mdadm raid 5 config. I have another 1TB drive too which I would like to add to the array once its set up. (I need to copy the data from that drive onto the array as its full of stuff).

The server will be connected onto a gigabit switch with another PC and the switch will be connected to the router. The router will go to the HTPC. The main purpose of this server is to serve the HTPC although there will be other file storing needed too.

I plan to leave it without a gui and admin it with Webmin.

OK, enough background, now my problem: I would like to maximise the size of the RAID array and create separate non-raid partitions for each of / , /var, /home and others. I am not sure how much space each one needs for a file server and what is the best way to do it.

I am guessing that 10GB from each drive will be enough, leaving the rest of the space for the arrays. So that is:
Drive 1:
100mb /boot
1900mb swap
8000mb /var
Rest of space in RAID partition

Drive 2:
10gb /
Rest of space in RAID partition

Drive 3:
4gb /home
6gb /usr

Is that ok? Is there an appropriate partition profile for me to use less that 10gb from each drive? 8gb for /var seems to big, would it be better to reduce to 4gb and then make a 4gb /opt its place?

Oh and the spec of the server is:
Epox 9NPA+ NF4 Ultra Mobo
Opteron 152 CPU
2x512mb DDR400 ram
4x1TB seagate in software RAID 5
7600gs passive
Gigabit PCIe network card
480W Xclio PSU
Ubuntu server AMD64

Possible upgrades available (will sell otherwise):
2x1GB ddr400 (overkill?)
4400+ X2 (overkill?)

Thanks for looking :)

---

### Post by LowSky on 2008-07-09
I cant see spliting the operationg system over 3 disks. Why not install it all to one partition of 15-20GB and using the rest for your RAID array?

And your system seems fine for most things, maybe more RAM maybe up to 4 GB if its going to be used as a Video server. if you want to use the server over more than one connection at a time.

---

### Post by _SiM on 2008-07-09
> **LowSky said:**
> I cant see spliting the operationg system over 3 disks. Why not install it all to one partition of 15-20GB and using the rest for your RAID array?
I thought there were advantages for servers in splitting it up?

If I do it all on 1 20GB partition, it will leave me with 2x20GB on the other 2 drives that I won't be able to put into the array...

> **LowSky said:**
> And your system seems fine for most things, maybe more RAM maybe up to 4 GB if its going to be used as a Video server. if you want to use the server over more than one connection at a time.
Will be only doing 1 demanding connection at a time. I thought 2GB would be overkill!

---

### Post by LowSky on 2008-07-09
I'm no RAID expert but can't you create the array and then partion for the OS? What I meant was that you don't need a seperate partion for every part of the OS, it just wasteful. Sure it makes fixing a certian part easier, but we aren't talking about a business solution but a home media server.

Video is very demanding especially if your streaming it to another computer. More RAM will mean less chances of Video hiccups or slow downs, even more so with large files.

---

### Post by _SiM on 2008-07-09
> **LowSky said:**
> I'm no RAID expert but can't you create the array and then partion for the OS? What I meant was that you don't need a seperate partion for every part of the OS, it just wasteful. Sure it makes fixing a certian part easier, but we aren't talking about a business solution but a home media server.

I can do that, I would just need a separate /boot partition. As the /boot cannot be read from a raid5 array. But, I want a completely separate partition for the shared folder. So if I can format/reinstall the OS without any problems. Hmm... maybe I would be better off with a separate OS drive?
 
> **LowSky said:**
> Video is very demanding especially if your streaming it to another computer. More RAM will mean less chances of Video hiccups or slow downs, even more so with large files.
Cool. I'll stick the 2GB I have in then...

Thanks :)

---

