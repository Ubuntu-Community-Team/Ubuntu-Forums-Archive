---
title: "Partition Sizes"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by ChompTheMan on 2008-04-23
Greetings.  It's 1 day until Hardy Heron is officially released so I thought now would be a good time to ask my simple partitioning questions.  I plan on creating the partitions I will need with Gparted and then installing manually.  My questions have to do with partition size and order:

1) How big should I make the root partition?  Disk space is not an issue and I like to try new software constantly.

2) How big should the swap partition be?  Again, space is not an issue.  I have 1.5 gigs of ram, but plan on adding lots more in the future.

3) Does the order of partitions matter?  I was going to do my partitions in this order: root, swap, home, windows.  Is this the proper order to do this in?  Am I missing anything?

Basically, I never, ever want to have to partition my hard drive again after this, so I want my root and swap partitions big enough so that I won't have to resize them in the future.  But I am unsure as to what would be good sizes for them and need your recommendations.  If you need more information from me in order to better answer my queries please feel free to ask.  Thank you.

---

### Post by Thelasko on 2008-04-23
For number 2 I would say the same size as the amount of RAM you have (or are planning on having).  Because when your computer goes into hibernation etc. it puts the contents of your RAM in the swap.

---

### Post by mlentink on 2008-04-23
> **ChompTheMan said:**
> 
1) How big should I make the root partition?  Disk space is not an issue and I like to try new software constantly.
You would have to try out and awful lot of software to get up to, say, 30 Gigs or so. Mine is currently at 6.

> **ChompTheMan said:**
> 
2) How big should the swap partition be?  Again, space is not an issue.  I have 1.5 gigs of ram, but plan on adding lots more in the future. 3 Gig is more than enough. Basically, you don't need more than your ram, and if you have lots of ram, you will not need swap. Swap was designed for lack of ram, so if you have enough, you don't need swap...

> **ChompTheMan said:**
> 3) Does the order of partitions matter?  I was going to do my partitions in this order: root, swap, home, windows.  Is this the proper order to do this in?  Am I missing anything?
Windows likes to be first. Windows dislikes to not be first. If you need Windows, give the emperor his due, then root and then home and swap.


edit: Oops, forgot about hibernation

---

### Post by Ub1476 on 2008-04-23
Here's how I do it on my laptop:

/=10GB
/home=20GB (I usually store all data on an external HDD)

On my laptop with 1GB ram, I just had about 350mb Swap. I don't think it really matters much. If you have enough ram, you are very likely not to even use the swap.

However, on my stationary were the Heron automatic made me a swap partition, it's 953,7MB. This is with 3.8GB ram.

Here's how ArchLinux organized my custom partitions:

[LIST]
[*]/
[*]Swap
[*]/home
[/LIST]

If you have enough space available, I would maybe do x2 of my setup.

---

### Post by ace007 on 2008-04-23
The link in my profile to Pyschocats has a little partition planning section.

---

### Post by ChompTheMan on 2008-04-23
Thank you very much everyone I now have an excellent idea of what I am going to do.  I'm a little saddened to have to add a partition for Windows(I've been Windows-free since 7.04), but I am eagerly expecting a game to come out this year and I doubt it will just work out of the box with Wine.  So the emperor will get his little bit of space at the beginning, but will be largely ignored and kept in it's place by Grub.  Thanks again.

---

### Post by Thelasko on 2008-04-23
You have a fast computer. Run windows in Virtualbox or VMware.  Unless your game is a massive resource hog.

---

### Post by mlentink on 2008-04-23
> **Thelasko said:**
> You have a fast computer. Run windows in Virtualbox or VMware.  Unless your game is a massive resource hog.

Nah. The graphics in virtual machines are simply not good enough for games, imho

---

### Post by ChompTheMan on 2008-04-23
I'll be playing a next-generation MMORPG when it comes out, so there's no way it will run smoothly(if at all) in a VM.  For the moment anyways.

---

