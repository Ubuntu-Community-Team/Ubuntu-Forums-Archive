---
title: "[SOLVED] How much space do I  ---really--- need for swap???"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by mariane_08 on 2008-08-11
Ok how much do really need for swap? I have 1GB RAM in my laptop. The swap partition is set at 400MB which is what the install set it as. 

I've been reading lots off older posts about this subject and am getting confused. If I understand correctly you actually don't need Swap at all if you have plenty of RAM. Another post told someone that their 8MB swap was enough because they had plenty of RAM (1GB like me). So do I need 400MB?

But then again I got this error message last night when I went to hibernate. It told me I had not enough swap!

I'm confused!

---

### Post by sdennie on 2008-08-11
If you plan to use hibernate, you will need at least as much swap as you have physical RAM.  Otherwise, the 400M that you have right now is probably a very reasonable amount.  Depending on how you use the machine, you may never use any of it but, as long as you aren't tight on disk space, it certainly won't hurt anything having it around.

---

### Post by Oldsoldier2003 on 2008-08-11
> **vor said:**
> If you plan to use hibernate, you will need at least as much swap as you have physical RAM.  Otherwise, the 400M that you have right now is probably a very reasonable amount.  Depending on how you use the machine, you may never use any of it but, as long as you aren't tight on disk space, it certainly won't hurt anything having it around.

I agree with vor completely here. On my 1GB system I rarely use ANY swap and I have been known to have a vm a compiler and several other apps running at the same time. Your mileage may vary, but I would say 400M is plenty unless you want to suspend/hibernate.

---

### Post by fahadsadah on 2008-08-11
Disk is plentiful in modern laptops. You should easily be able to spare 1 GB, let alone 400 MB.

If you get an error detailing insufficient swap, allocate more (use gparted [System|Administration|Partition Editor] from the LiveCD - don't run from local disk please)

---

### Post by anewguy on 2008-08-11
Actual swap usage is dependent on the hardware and applications you are running.  It varies as much between users as what they use their computers for and what applications they run.  So one persons "I hardly use swap" may be replaced by anothers "my swap gets used a lot".  So, how much?

This will depend on who you ask.  Some people will say you never need more than "x", others may say much more.  In practice, it is hard to say.  For laptops, to try avoid problems associated with going into and coming out of hibernation, the swap size should be at LEAST as big as the amount of physical memory.  To actually go 1 1/2 times as big would be my suggestion.  Others will strongly disagree.  But IF you run a lot of apps, it is possible to need the entire physical memory size.  Adding some for the additional overhead which goes into hibernation would be mandatory.  You have plenty of disk - give it a swap size of 1 1/2 the physical memory size.

To those who would disagree - eveyone has their opinion - I have just stated mine.  I don't want arguements with anyone, so lets try to avoid that.  Yes, most people don't need a swap that big.  But the truth is that laptop hibernation is a different issue from those encountered on most desktops.  Disk is cheap - be generous.  :)

---

### Post by mariane_08 on 2008-08-11
> **anewguy said:**
> Actual swap usage is dependent on the hardware and applications you are running.  It varies as much between users as what they use their computers for and what applications they run.  So one persons "I hardly use swap" may be replaced by anothers "my swap gets used a lot".  So, how much?

This will depend on who you ask.  Some people will say you never need more than "x", others may say much more.  In practice, it is hard to say.  For laptops, to try avoid problems associated with going into and coming out of hibernation, the swap size should be at LEAST as big as the amount of physical memory.  To actually go 1 1/2 times as big would be my suggestion.  Others will strongly disagree.  But IF you run a lot of apps, it is possible to need the entire physical memory size.  Adding some for the additional overhead which goes into hibernation would be mandatory.  You have plenty of disk - give it a swap size of 1 1/2 the physical memory size.

To those who would disagree - eveyone has their opinion - I have just stated mine.  I don't want arguements with anyone, so lets try to avoid that.  Yes, most people don't need a swap that big.  But the truth is that laptop hibernation is a different issue from those encountered on most desktops.  Disk is cheap - be generous.  :)

OK understood. So do I need as much to just suspend? Given that I don't want to keep applications running but just want avoid having to reboot?

---

### Post by billgoldberg on 2008-08-11
I always double the amount of ram I have.

However, the biggest amount of swap I've ever used is around 500mb.

---

### Post by SunnyRabbiera on 2008-08-11
Well me I usually just use 2.9 gigs for swap, but just one gig for swap is plenty.
Actually depending on your hardware a swap partition can be smaller like 512 MB but its normally not advised.
Swap comes in handy even with large capacity ram, as it still helps manage the system.

---

### Post by alienexplorers on 2008-08-11
I always use double the amount of system ram.  Read somewhere this is how to set it up.

---

### Post by RedPandaFox on 2008-08-11
I agree with double, yeah you probably wont use it all, but in the off chance you may, it would be good, and I'm sure that 2gb wont send you to memory shortage unlike me, My EeePC has only a 2gb ssd so pretty much, I cant have swap and that works OK for me. But I wouldnt do this in a normal situation

---

### Post by Dr Small on 2008-08-11
It depends upon how you run your system. For me, I don't need swap.

---

### Post by mc4100 on 2008-08-11
> **Dr Small said:**
> It depends upon how you run your system. For me, I don't need swap.

I like to keep mine running light (at least I think so, ~200 megs after logging in) so I give swap space a low priority when partitioning: usually 500 megs or so.

---

### Post by sstusick on 2008-08-11
I've allocated 1 GB for swap as I have 1 GB system memory and I rarely use more than 50 MB of swap.

---

### Post by Dr Small on 2008-08-11
> **mc4100 said:**
> I like to keep mine running light (at least I think so, ~200 megs after logging in) so I give swap space a low priority when partitioning: usually 500 megs or so.
I have 300MBs of swap space, but I plan to eliminate it sometime when I get bored, because it never gets used.

---

### Post by sandysandy on 2008-08-11
see these links

[http://www.linux.com/feature/121916](http://www.linux.com/feature/121916)

[http://www.xenotime.net/linux/doc/swap-mini-howto.txt](http://www.xenotime.net/linux/doc/swap-mini-howto.txt)

regards

---

### Post by mc4100 on 2008-08-11
> **Dr Small said:**
> I have 300MBs of swap space, but I plan to eliminate it sometime when I get bored, because it never gets used.
I know the feeling, conky reports current Swap usage at ... 96.00 KiB.
But I know why I keep it around: frequently, something will slam my memory and the swap gives me enough time (room?) to find out what it is and kill it. It's also a pretty good indicator something bad just happened -- the led will stay on.

---

### Post by cdtech on 2008-08-12
I have 2G of SWAP and run my "swappiness" at 100 as well. I've notice during heavy loads (full backups especially) I don't use near that much SWAP space but HD space is no problem in my case.

I agree with Andrew Morton:
> "My point is that decreasing the tendency of the kernel to swap stuff out is wrong. You really don't want hundreds of megabytes of BloatyApp's untouched memory floating about in the machine.  Get it out on the disk, use the memory for something useful."

---

### Post by sdennie on 2008-08-12
> **cdtech said:**
> I have 2G of SWAP and run my "swappiness" at 100 as well. I've notice during heavy loads (full backups especially) I don't use near that much SWAP space but HD space is no problem in my case.

I agree with Andrew Morton:

I agree with Andrew Morton in principal but, in practice, we are in a time where machines are being sold for operating systems far, far more bloated than Ubuntu and so average workloads under Ubuntu probably don't need much (if any) swap to run smoothly with 1GB+ of RAM.  

If you start an application and it takes a few seconds, you aren't that bothered.  If you already have an application open and it takes a few seconds to read it back in from swap after you haven't used it for a while, you are highly annoyed.

I would say that unless you really understand your workload and how your system is going to handle it with regards to memory management, leave swap, swappiness, etc. at the default.  If you plan to use hibernate, then, yes, plan ahead for it.  However, hibernate is very, very often a waste if your machine can do suspend/resume anyway (which doesn't depend on swap but very slowly drains the battery over time (generally days)).

---

### Post by anewguy on 2008-08-12
> **billgoldberg said:**
> I always double the amount of ram I have.

However, the biggest amount of swap I've ever used is around 500mb.

I'm glad to see someone else from the old school as well!!  We normally always allocated twice our physical memory to swap space.  Since I no longer work I still try to stick to that.  Some people consider it a waste, and I'm sure some linux techno will disagree with me, but that used to be the standard for any machine using virtual memory.  We carried it over to Unix and never had any weird problems that we might otherwise have suspected memory on.

Like most, I also don't ever see all of my swap being used, and while the old adage the disk is cheaper than physical memory still holds, it's hard to get people to understand.  You could go check most companies and find their swap usage appears down - that's from lessons learned and knowing that the disk space used is small but well worth it.

Just glad to see someone who thinks the way us old guys do!

As far as this user is concerned, I would just make it easy on myself and allocate a minimum of 1 1/2, preferably 2, times the amount of memory I have as swap space.  If you have 1 gig of memory, just go ahead and make swap 2 gig.  Everyone has their opinions, but disk is cheap, and you need such a small chunk.  Allocate 2 gig and then just forget about worrying about it.

---

### Post by sdennie on 2008-08-12
> **anewguy said:**
> I'm glad to see someone else from the old school as well!!  We normally always allocated twice our physical memory to swap space.  Since I no longer work I still try to stick to that.  Some people consider it a waste, and I'm sure some linux techno will disagree with me, but that used to be the standard for any machine using virtual memory.  We carried it over to Unix and never had any weird problems that we might otherwise have suspected memory on.

Like most, I also don't ever see all of my swap being used, and while the old adage the disk is cheaper than physical memory still holds, it's hard to get people to understand.  You could go check most companies and find their swap usage appears down - that's from lessons learned and knowing that the disk space used is small but well worth it.

Just glad to see someone who thinks the way us old guys do!

As far as this user is concerned, I would just make it easy on myself and allocate a minimum of 1 1/2, preferably 2, times the amount of memory I have as swap space.  If you have 1 gig of memory, just go ahead and make swap 2 gig.  Everyone has their opinions, but disk is cheap, and you need such a small chunk.  Allocate 2 gig and then just forget about worrying about it.

I agree that disk is cheap and having large amounts of swap space causes you no harm.  However, if an average user is actually making use of that swap space, it probably indicates that either 1) A program you are using is very misbehaved and has a memory leak or 2) You need to buy more memory.  

I remember allocating large amounts of swap long ago when memory was sparse but, for what I would consider "average user workloads", with modern machine configurations, I think it's less and less relevant.

Yes, make some swap.  Yes, if you use hibernate, make it larger than your physical memory.  However, don't think that swap is going to improve the performance of the machine or likely even be used and, if it does in any noticeable way, it's likely indicative of some other problem.

---

### Post by Inxsible on 2008-08-12
I never go beyond 512MB of swap. On my current machine with 256MB RAM - it satisfies the 2x rule. But I keep swap at 512MB even on my machines with 1GB and 4GB of RAM. I never hibernate...I do occasionally suspend, so I dont need a huge swap. If you keep 2x rule, then for a 4GB RAM machine, you would need 8GB of swap. That would be a lot of wasted space.

If you plan to hibernate however, then you need to have a swap of more than your physical RAM just to make sure that you can get around the problem of bad blocks.

---

### Post by anewguy on 2008-08-12
[QUOTE=Yes, make some swap.  Yes, if you use hibernate, make it larger than your physical memory.  However, don't think that swap is going to improve the performance of the machine or likely even be used and, if it does in any noticeable way, it's likely indicative of some other problem.[/QUOTE]

Exactly - the average home user shouldn't be using all of swap, or really much of it at all.  However, as you agree with, for the hibernate issue it is best to make it (a) your physical memory size + (b) overhead.  Hence the suggestion at 2 gig just to make it easy for the user to set and forget about.:)

---

### Post by 3rdalbum on 2008-08-12
With one gigabyte of RAM, you don't need swap. The most swap I ever used on a 1 gig machine was 17 megabytes, and that was with plenty of RAM still available.

But sometimes Wine eats up memory like there's no tomorrow, so for those circumstances a 400 mb swap partition is a good idea to avoid crashes.

I'm running a 2 gigabyte machine with no swap at all, and it works rather well.

---

### Post by tarps87 on 2008-08-12
The swap size can be different for every user.  When your ram is used up the least/last used program is remove from the ram and stored into the swap "file".  When you hibernate your pc the entire contents of the ram is stored into the swap "file" so hibernating will need to be at least the size of the physical ram.  I agree that the swap file should be at least 1 1/2 times the physical memory, but if you can't spare it (like with some of the eeepc's) you can get away with using a smaller size.
If you get board look for memory paging and LRU (least recently used)

---

### Post by pgte3 on 2008-08-12
I would use the default swap space for Ubuntu. Over time monitor your computer usage and adjust accordingly.

---

### Post by anewguy on 2008-08-12
As stated before - you have the disk space, you want to hibernate, give it 1 1/2 to 2 times the physical memory size.  What is actually used at run time is a little immaterial in this discussion.

---

### Post by mariane_08 on 2008-08-12
OK I'll leave it at the default for now and see how it goes. Am in correct if I avoid hiberrnating and just use suspend instead swap is NOT an issue?

---

### Post by anewguy on 2008-08-12
Should be, but be aware it will be constantly draining your battery.

---

### Post by madhi19 on 2009-08-01
I stuck to the two times the physical memory rule even on my new rig running at 2GB of ram. After all if you got one TB of free space who care about loosing 4GB.

---

### Post by insane_alien on 2009-08-01
i have a swap partition but the most its ever got up to in 3 weeks of uptime is 512kiB not really worth it.

---

### Post by HotShotDJ on 2009-08-01
I know this topic has pretty much been beaten to death, yet I feel compelled to add one thought:

The RAM X 2 is what is called a "safe harbor" method of calculating swap space.  The purpose of allocating this amount is NOT for the purpose of day-to-day running of your system, but to prevent a catastrophic failure should a badly behaved application run amok on your system.

I can give you an example of this principle in a real-world situation:  One of the recent Ubuntu Kernels (not available in the repositories -- I believe it was from the 2.6.30 series) OR one of the xorg-video-intel drivers (also from a PPA, not in the regular Jaunty repositories) contained a regression that caused a huge amount of swapping.  If I had not set my swap partition to the admittedly over-sized default of RAM X 2, or worse, chose not to have a swap partition at all, my system would have come to a crashing halt before I was able to detect what was going on, look up the issue, and make the appropriate corrections to my system.

As others have noted, if a system has a sufficient amount of physical RAM, it is possible that the user will never experience any problems by shrinking, or even eliminating, the swap partition.  Also, I have seen recommendations that RAM X 2 is only correct for systems with less than 1 Gig RAM (the type of systems we old-timers used for most of our computing life), and that for systems with 1 or more GIG, the appropriate calculation is RAM X 1.5.  To me, this seems like a reasonable recommendation.  In any case, the cost of mitigating the potential risk is minimal compared to the cost of having a RAM related catastrophic failure.  The cost/benefit calculus seems to overwhelmingly support the use of either the RAM X 2 or at the very least, the RAM X 1.5 recommendation.

All systems that I set up have RAM X 2 swap partitions.  As previously mentioned, disk space is cheap, so I can think of no reasonable argument to change to another partitioning scheme.

---

