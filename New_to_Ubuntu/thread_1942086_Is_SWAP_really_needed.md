---
title: "Is SWAP really needed?"
date: 2012-03-16
forum: New to Ubuntu
---

### Post by d4m1r on 2012-03-16
Hey guys, I am gearing up for the release of 12.04 where I will be nuking my 32 bit 11.10 install and going with a copy of Precise x64. Anyway, when I setup this partition, I specifically disabled any SWAP space on purpose before really understand what it does. While I kinda understand it better now, I still see it like the Windows paging file and would argue that letting my system use RAM (I have plenty, 8GB) is MUCH quicker than forcing it to use my HDDs....Anyone care to disagree and explain why?



Even when I am doing "heavy" stuff under Ubuntu, I rarely exceed 1GB/8GB usage and never notice slow downs. It's why I am inclined to disable SWAP space for 12.04 as well.

---

### Post by MG&amp;TL on 2012-03-16
You're not forcing it to do anything...swap is more of a backup plan for when you run out of memory...I think it's a good idea to have about a GB, but opinions differ. Make your own mind up, unless you have a pitiful amount of RAM, you probably won't notice anyway.

---

### Post by d4m1r on 2012-03-16
> **MG&TL said:**
> You're not forcing it to do anything...swap is more of a backup plan for when you run out of memory.

From what I've understood though, it doesn't just use it when it runs out of RAM though, no? Someone previously asked how much swap they should use for Ubuntu partition and they also had 8GB of ram, and someone told them 8.5GB...Is it possible even to use that much RAM under Ubuntu?

I am also pretty sure that as long as *any *space is allocating for swap, the system will use it, regardless of if RAM is maxed out or not...

---

### Post by MG&amp;TL on 2012-03-16
It will use a little, yes, and I'm not entirely sure why. But it will definitely not use ALL of it, probably only a tiny percentage.

---

### Post by jerome1232 on 2012-03-16
Ram unused by applications will get used as file cache, if your box is doing a lot of file operations and unused application data is sitting in ram, sometimes it will opt to swap out that application data for more file cache, and yes file cache WILL fill up your ram, quickly.

That's about it to my knowledge, swap is good to have (with out it your system will crash if it ever did run out of ram, memory leaks do happen)

---

### Post by Haneef Mubarak on 2012-03-16
I think this ought to explain it to you the best:

Just turn off swap (by setting swappiness to zero), restart your system, and try to use it. You will notice it will be slower. Then go set swappiness back to the previous setting and restart. Now it feels faster. See?

---

### Post by sammiev on 2012-03-16
For what I do my swap is only used well I suspend. Every user can and maybe different.

---

### Post by QIII on 2012-03-16
Actually, Haneef, swappiness may or may not make much difference with as much memory as people have now.  A DBA probably needs to tune it.  Or someone administering servers.  With 8GB on a run of the mill desktop, I don't suspect that memory will be aggressively moved to swap because there will probably be no need.  When we were all trying to run 17 applications on 256MB it was different.  The kernel doesn't have to worry so much about the competition for memory (well, not as much.) any more.

A memory leak that would gobble 8GB before you caught it would be a real issue and would probably take leaking by design.  I've done that for demonstration purposes.   But leaks do happen when people are forgetful, I suppose.

Swap is necessary if you want to suspend to disk.  1.1 - 1.25x memory is sufficient.  All you need is enough to maintain what is held in memory.  Back when memory was at a premium we used to say 2x memory so you could preserve both the memory state and what was already in swap.

With memory as plentiful as it is, many people simply don't use a swap and suspend to RAM when they need to.  If you have 16GB of memory and only ever use 5 - 10% of it, why waste the space on a partition that is of no ther use?

---

### Post by d4m1r on 2012-03-16
I was hoping for a more technical explanation but;

a) I never suspend my system (and yes, this wouldn't work well without swap space, just like my Windows 7 partition wouldn't suspend nicely because of no paging file)

b) I noticed better performance under Windows 7 without the paging file, and it is proven you will too if you have 4GB+ RAM.

Anyway, I will be poking around for linux literature on swap vs non-swap performance but my guess is that my eyes don't deceive me, and disabling swap = better performance (as long as your RAM is faster than your HDD, which is most likely the case).

---

### Post by QIII on 2012-03-16
Five or six years ago this was a real bone of contention.

My feeling is this:

For a desktop, it can't hurt but it will probably never be used.

For a server or a machine that hosts a large database, you'd better.

---

### Post by alquery on 2012-03-16
> **d4m1r said:**
> I was hoping for a more technical explanation but;

a) I never suspend my system (and yes, this wouldn't work well without swap space, just like my Windows 7 partition wouldn't suspend nicely because of no paging file)

b) I noticed better performance under Windows 7 without the paging file, and it is proven you will too if you have 4GB+ RAM.

Anyway, I will be poking around for linux literature on swap vs non-swap performance but my guess is that my eyes don't deceive me, and disabling swap = better performance (as long as your RAM is faster than your HDD, which is most likely the case).

In my experience with Windows (XP and Vista at least), the page file is used much more aggressively than with Linux. When I had Vista on my comp when I bought it, the page file would go up to 1.4GB in  some cases with 4GB RAM. In Linux, I have never seen it go above 170 or so KB, and that kind of size shouldn't be an issue. For a while I had to delete my swap to make room for another primary partition, and I noticed no speed improvements or decreases. I like to keep it around though for that sole reason that when my laptop runs out of power, I don't lose whatever I'm working on.

---

### Post by yetiman64 on 2012-03-16
> **d4m1r said:**
> From what I've understood though, it doesn't just use it when it runs out of RAM though, no? Someone previously asked how much swap they should use for Ubuntu partition and they also had 8GB of ram, and someone told them 8.5GB...Is it possible even to use that much RAM under Ubuntu?

I am also pretty sure that as long as *any *space is allocating for swap, the system will use it, regardless of if RAM is maxed out or not...
To hibernate a machine requires the swap to be at least the same size as RAM, as the memory contents are written to the HDD when hibernating.

IF you don't need hibernation and with your 8GB of RAM you probably would get away with no swap partition without any problems. But note the next quote ;)

> For a server or a machine that hosts a large database, you'd better.     I like the idea posted above about altering the swappiness setting and see how it goes first.

Cheers.

---

### Post by bodhi.zazen on 2012-03-17
This question has been debated for years without a single answer that works for everyone.

The size of RAM has been ever increasing, but so has the size of hard drives. 

See [http://kerneltrap.org/node/3000](http://kerneltrap.org/node/3000)

---

### Post by Jake5 on 2012-03-17
> **d4m1r said:**
> Someone previously asked how much swap they should use for Ubuntu partition and they also had 8GB of ram, and someone told them 8.5GB...
Correct me if I am wrong, but I was under the impression that you could not create a swap partition larger than 2 gigs, never seeing a reason to test this, I haven't.

---

### Post by radon7 on 2012-03-17
From what I have read, the Linux kernel is set to start using swap when ram used is between 85 and 90 percent depending on the distribution.  So the real question is whether you will be using that much memory or not. It is possible under Ubuntu if you run programs as video editing or 3d animation such as blender. The average user will usually not use anywhere near 8GB of memory so I would say it would be OK to leave it off.  If you currently have a swap partition but didn't use it, you may edit /etc/fstab to mount it as swap and if you notice any difference you may turn it back off or leave it on.  Besides suspending the operating system, which like you I never do, if you don't use near 85 percent of your RAM you shouldn't even notice any difference.  But think about the fact that HDDs are so big that if you use 4 to 12 GB for swap, will it even bother you to lose that much just in case you decide to start editing videos or other memory intensive programs later on?

---

### Post by Elfy on 2012-03-17
> **Jake5 said:**
> Correct me if I am wrong, but I was under the impression that you could not create a swap partition larger than 2 gigs, never seeing a reason to test this, I haven't.

You are indeed incorrect :)

I've seen particularly silly amounts of swap being accidentally created around here. Mine got created at 3.5Gb when doing a 'let the installer create' the partitions install, they are gone though now.

---

### Post by kurt18947 on 2012-03-17
Another option to a swap partition is a swap *FILE*.  I did this when I was running a machine with 1 GB. RAM and saw no problem with it.  If I want to suspend to disk, I would have needed a swap partition. A swap file will not support suspend-to-disk or hibernation.  A swap file doesn't take up one of four primary partitions and I think a swap partition must be primary, it can't be extended.

---

### Post by pqwoerituytrueiwoq on 2012-03-17
> **forestpiskie said:**
> You are indeed incorrect :)

I've seen particularly silly amounts of swap being accidentally created around here. Mine got created at 3.5Gb when doing a 'let the installer create' the partitions install, they are gone though now.
3.5 gb that is nothing i have a whopping 17GB of swap (that i have never once used, lol) if i ever wanted to use hibernate i can even if i max out my ram at 16gb

---

### Post by jwbrase on 2012-03-17
> **d4m1r said:**
> I was hoping for a more technical explanation but;

a) I never suspend my system (and yes, this wouldn't work well without swap space, just like my Windows 7 partition wouldn't suspend nicely because of no paging file)

b) I noticed better performance under Windows 7 without the paging file, and it is proven you will too if you have 4GB+ RAM.

That's because Windows starts swapping much sooner than it needs to. My Ubuntu 10.04 system doesn't start swapping significantly until the amount of RAM used by programs approaches 100 percent. Having swapping enabled has zero performance impact until you actually start swapping. Windows starts swapping long before RAM is anywhere near full, which is why you see the performance hit.

> 
Anyway, I will be poking around for linux literature on swap vs non-swap performance but my guess is that my eyes don't deceive me, and disabling swap = better performance (as long as your RAM is faster than your HDD, which is most likely the case).

RAM is *always* faster than HDD, (generally in the range of a hundred thousand to a million times faster). Even if it were the same speed, stuff swapped to the HDD is read into RAM before being used, so swapping would still be slower. But as long as you're using an OS with a sane swapping policy, nothing will be written out to disk unless it absolutely has to be to make room.

I primarily have swap on my machine to allow for hibernating, but it doesn't get in the way in normal use, and has even come in handy a few times with really memory-intensive programs.

> **Jake5 said:**
> Correct me if I am wrong, but I was under the impression that you could not create a swap partition larger than 2 gigs, never seeing a reason to test this, I haven't.

My swap partition is 3 gigs (enough to allow for my machine to hibernate).

---

### Post by asifnaz on 2012-03-17
yes sap in needed for my old Pentium 3 with 256 mb ram and 512 mb swap  really help me to run many applications at same time

---

### Post by kurt18947 on 2012-03-17
> **asifnaz said:**
> yes sap in needed for my old Pentium 3 with 256 mb ram and 512 mb swap  really help me to run many applications at same time

Absolutely.  Swap seems necessary with any machine with < 3-4 GB. RAM.  It probably also matters what the machine will be used for.  I expect web browsing and word processing require less RAM than video transcoding or editing, for instance.

---

### Post by d4m1r on 2012-03-17
@Jake5, yep it's definitely possible I am pretty sure you can set you swap to anything....there might be a theoretical limit though that is lower than your HDD (32GB? Not sure on this one).

@bodhi.zazen, I am not asking from a HDD perspective as I have plenty of space but a speed perspective. I could have configured swap and it wouldn't even have made a dent in my storage space (2.5TB) but I am now certain my Ubuntu partition would be slower with it.

@jwbrase, "**Having swapping enabled has zero performance impact until you actually start swapping**" Wrong ;) As I covered earlier, Ubuntu seems to start using swap space even before the physical memory is 100% full. If it only used it then, I would definitely configure some in the rare event my applications used more than 8GB of RAM. But what happens is if you have ANY swap configured, it will automatically use it and my HDDs are slower than my RAM so...

Seems like noone could convince me otherwise so I'll be installing 12.04 specifically without space space as well :lol: The only thing I now don't understand is how having swap configured on a server being used specifically for DB stuff (even if it has 12-24GB) could speed it up....We have the same policy at work where we use Oracle DB and configure 1:1 RAM to swap on these already beastly machines.

---

### Post by BertN45 on 2012-03-17
SWAP is not really needed. In the past I have run Ubuntu without a swap partition on a 2GB machine and never had any problem. The OS will keep everything in memory, but a desktop with 8 GB will do that anyway in practice. If you succeed in filling your huge memory (very unlikely), it will refuse to start new programs and programs requesting more memory dynamically might pause or crash dependent on the quality of the program.

I never found myself in that situation with I think Ubuntu 8.04 and 2GB of RAM.

Besides I am not very impressed by the swapping of Linux, because as soon as it starts swapping, it really gets slow, much slower then Windows 7 with an equally sized page file.

I expect that Linux keeps everything in memory, disabling the page cache in memory. That means that the "soft page faults" will disappear and you will save the interrupt processing time needed to insert the cached page in the page table again and it will not look periodically for pages to be cached.

Linux uses almost all free memory for IO buffers and page cache. I think only 10% is kept free, which means that when a large program is started there is not enough memory on a desktop like mine. It has to free some pages from the page cache and occasionally it will have to save a few  pages to disk. It is very lazy in returning those pages to memory and that is why you see sometimes a few MB in the SWAP.

---

### Post by shuttleworthwannabe on 2012-03-18
I thought swap was needed for hibernation mainly (hence recommendation of 1.5 to 2x size of RAM); I a not sure what recommendation if RAM is >8GB-is their max limit to swap size as RAM increases?

but for suspend, system uses RAM, not swap. Did I get this wrong?

---

### Post by 1clue on 2012-03-18
First, yes you CAN create a large swap partition.  At least 12g.

There is no easy answer for many of the questions here.

Memory use comments:
[LIST=1]
[*]If you use virtual machines your memory use can be very large.
[*]A typical Linux desktop that's just used as a personal computer is not likely to need more than 4g.
[*]Any memory you aren't using eventually gets used as disk cache.  My 12g system takes about a month to fill up with normal use, assuming I don't start any virtual machines or do anything else to claim RAM.
[*]If you use server software such as a large database you can use a large amount of RAM.
[*]If you perform large calculations or simulations (weather prediction) you can use more memory and more CPU than you and any 10 other guys can afford.
[/LIST]

Swap comments:
[LIST=1]
[*]Generally speaking if you have 4g RAM on your desktop machine you probably won't run out, swap or no.
[*]Hibernate, as has already been mentioned, requires a swap partition which is at least as large as RAM.
[*]There are other features which use the swap mechanism.  My favorite is TMPFS.
[/LIST]

TMPFS is a temporary filesystem.  It uses the SWAP mechanism to operate and creates a RAM disk which is used to store volatile (won't survive a shutdown) data.  If you have an application which rapidly writes a lot of temporary stuff to the disk, you can make it much faster by making the directory it writes to a tmpfs partition.

Since SWAP is handling this, the filesystem is normally in RAM until you need that RAM.  Once you need to flush, SWAP decides what to write out, which may be your TMPFS filesystem or it may be some utility you used a week ago.  We don't know and don't care, because SWAP is very good at deciding what to push out.  So the system is as fast as RAM until such time as it actually needs to use the drive, and then it's much better than we could anticipate and reproduce manually.

One example of this is Gentoo Linux, on which every application or utility you install is compiled by that system, including the kernel.  I've found that by using tmpfs on the directories that portage uses (the package manager for Gentoo) you can dramatically increase the speed of those compiles.

What I do is a bit overkill, but I have 4 drives, each of which has a 12g swap partition, so each could theoretically be used to hibernate the system.  The way Linux works, there will only ever be one partition.

Anyway, I mount as tmpfs any directory my activities use for volatile storage, and some of those spaces could theoretically grow to be larger than RAM. I have all that swap space "just in case" and rarely use any of it.

Good luck and have fun.

---

### Post by TenPlus1 on 2012-03-18
I have 2gb ram and no swap partition, swappiness set to 0 and use tmpfs to put temp files and logs into memory, plus I use virtualbox on occasion and all works fast and fine :)

---

### Post by bodhi.zazen on 2012-03-18
> **d4m1r said:**
> @bodhi.zazen, I am not asking from a HDD perspective as I have plenty of space but a speed perspective. I could have configured swap and it wouldn't even have made a dent in my storage space (2.5TB) but I am now certain my Ubuntu partition would be slower with it.

I think you completely missed the point of my post.

There are two things to consider:

1. This has been debated for years, the link I gave you goes back to 2004. The kernel developers do not agree on how to answer this question.

2. That is because "it depends". It depends on many factors, how do you use your system, and how do you expect it to perform.

IMO the vast majority of Desktop users do not need more then 2 Gb of ram and with that much RAM will not ever use swap.

But that is not the same thing as saying all users need only 2 Gb or ram and will never use swap.

Factors to consider include what you use your system for (server ? desktoop ? multimedia ? virtualization ?), what your definition of responsiveness is (foreground tasks only, foreground and background tasks ? ), your tolerance for faults (having a desktop crash is not the same as having a production server crash), and if you use suspend / hibernation.

In general, for desktops, I use swap = RAM X 2 , max 1 Gb

In general, assuming you have 2 Gb + RAM, it is highly unlikely you will ever use swap on a single user system where all you do is web browsing, email, and word processing.

In general, for servers and laptops, I use swap = RAM + 512 Mb

In general, if you turn swap off, you take a small risk that at some time you might use up all your memory, and your system will then crash, and you may have data loss.

Any claim that the system is "faster" with any particular swap setting need to be backed up by benchmarks.

If you make a swap partition, you can always turn it on an off =)

---

### Post by bodhi.zazen on 2012-03-18
It is worth quoting what the developers are talking about on that KernelTrap mailing list in terms of swap ...

> Andrew Morton humorously replied, "I'm gonna stick my fingers in my ears and sing 'la la la' until people tell me 'I set swappiness to zero and it didn't do what I wanted it to do'."

Which promptly sparked 

> And don't even get me started on multimedia apps - swapping out apps in that field is criminal. But probably Andrew doesn't care about that; well, no wonder, since he stuck his fingers in his ears now - how do you expect him to enjoy multimedia content without his ears properly functioning? :-)))

Sort of the bottom line with swap - It does not affect performance to have a swap partition (or file), but it does add a safety net against using up all your ram, for any reason, from memory leaks (bugs) to unexpected spikes (burning a DVD, firing up one too many VM). If you are seeing a slow down (using swap), you need more RAM or to lighten up your workload.

---

### Post by d4m1r on 2012-03-18
> **bodhi.zazen said:**
> 
Sort of the bottom line with swap - It does not affect performance to have a swap partition (or file), but it does add a safety net against using up all your ram, for any reason, from memory leaks (bugs) to unexpected spikes (burning a DVD, firing up one too many VM). If you are seeing a slow down (using swap), you need more RAM or to lighten up your workload.

I disagree, as previously mentioned, if you have ANY swap space allocated, the system will begin to use it even BEFORE you run out of physical memory. In my case and most others, that would mean it would be doing things on my HDDs rather than my RAM (which is much faster) even though my RAM could be 50% unused.


This = drop in performance.

---

### Post by MG&amp;TL on 2012-03-18
> **d4m1r said:**
> 
This = drop in performance.

I think this is a "whatever you want to think" question-if the kernel devs can't agree, why should we?

---

### Post by bodhi.zazen on 2012-03-18
> **d4m1r said:**
> I disagree, as previously mentioned, if you have ANY swap space allocated, the system will begin to use it even BEFORE you run out of physical memory. In my case and most others, that would mean it would be doing things on my HDDs rather than my RAM (which is much faster) even though my RAM could be 50% unused.


This = drop in performance.

I have never seen that behavior. Again, optimizing swap is highly subjective and personal, not to mention technical.

You may well have a bug, please post details and benchmarks.

---

### Post by anewguy on 2012-03-18
Here's my personal take, and I could be very wrong here or my opinion may not be that welcome. ;)

With the use of newer computers, their higher memory, and the use the average user puts Ubuntu to (hey, email, voip, messaging, surfing the net, playing a game or 2) if you have enough memory and if, in the case of a laptop, you don't intend to hibernate, then swap at best can be tiny, if non-existant.

Also, sometimes I think swap should just be an automatic by the install.  You see, swap can be a file, just like the paging file in Windows.  The speed may not be quite as fast as the transfers in and out of a separate swap partition - if so, I think it would be negligable.  For the majority of average users coming from a Windows environment to Ubuntu (or any Linux), swap becomes a matter of confusion - a mystery that some worry about.  Why not do like Windows (okay, you can kill me now! ;) ), allocate a swap file, then give the option for the user to move it after an install is complete.  This way it's invisible to the average user.

Just a thought - maybe not a good one - but indeed it's a thought ;)

Dave ;)

---

### Post by Holdolin on 2012-03-18
I thought i read somewhere that the most Linux kernels look for a swap file at least to be there (sorry, it was something i read a while ago and honestly may no longer even apply).  It can be set quite small tho, perhaps 256MB in size.  That's what I use on my servers, they have 8GB RAM each, so i'm not worried about acutally needing swap sapce.  I keep tabs on them just to make sure they're ok, and they've never even pushed to 50% mem usage.

---

### Post by anewguy on 2012-03-18
And if so, just that much more reason to make it automatic.  Allocate a swap file automatically on install and base it's initial size according to how much memory the system reports.

Dave ;)

---

### Post by The Peanut on 2012-03-18
I run a hp netbook 2040 with 2GB of ram, and with NO SWAP, and it runs completely fine, I spoke to a friend of mine, who has been using ubuntu for about 2 years now, and he has said "while it may not be completely necessary, it may be a considerable option". But I went without swap. It all depends on what you are going to be using it for, if your going to be using it for allot of gaming and recording then I would personally use swap, but if your using as a normal OS for general purposes, then swap may not be needed but, I've personally got a dual boot with windows 7 and rarely ever use windows 7, but have only had ubuntu 10.04  desktop edition for around 2 weeks now. As many other users have posted, it is entirely UP TO YOU! ;D

Regards

The Peanut

---

### Post by ratcheer on 2012-03-18
I also have 8 GB RAM and I use an 8 GB swap partition. It is never used, but it doesn't hurt a thing. Besides, this one swap partition is shared among four Linux installations.

Tim

---

### Post by shuttleworthwannabe on 2012-03-19
> **anewguy said:**
> And if so, just that much more reason to make it automatic.  Allocate a swap file automatically on install and base it's initial size according to how much memory the system reports.

Dave ;)

This is exactly how Windows OS does it (but is also user accesible if need be to increase or decrease the pagefile size).

---

### Post by HiImTye on 2012-03-19
the simple answer is make a swap partition (or file) as large as you need (or don't)

the real answer is entirely dependant on your specific needs. you can have a swap partition, a swap file for overflow, set your swappiness to 100 (or some other number) and then create cgroups to change swappiness at varying levels entirely dependant on the needs of those tasks. everyones' needs are different and the system is entirely configurable to meet your needs

---

### Post by 42dorian on 2012-03-19
The way I understand SWAP, it's more than just a replacement for your page file.  It's a separate partition so that Linux can set it apart from your system, should something drastic happen to it, it makes it easier to recover from it.

In years before, this has been needed for day to day usage.  Indeed, now, we have systems with all the way up to 32GB of RAM.  Swap seems kinda useless in these cases, and I agree that it's an old concept.  However, Linux does things that Windows and Mac just don't bother to do.  Like, free updates.  And, as great as that may be, even upgrades can crash accidentally.  In those cases, it's nice to have a SWAP space so you can recover ~Something~ in case of you having to forcibly reboot the system in the middle of it.  Like, there's a thunderstorm and there's a power outage, that kind of thing.

I find this rule to be most helpful with today's systems.  64MB-2GB of RAM,1.5XRAM=SWAP Space.  4-8GB RAM, Equal Swap Space.  Over 8GB RAM, 1-2GB Max SWAP Space.  Older systems need proportionally more SWAP space, Relatively new, but low end systems need full blown just-in-case-it-all-goes-to-hell space, and everything above that just needs a couple GB to tell the Kernel that it has a space in case it needs to dump the system log or recover from a wacky install.

Swap is kind of Grandfathered-in to Linux.  Like the Scroll Lock key.  It's just a part of how the system works, even if it is several years since it's been mission-critical.

Or, that's how I understand SWAP.  I know what it is and how it works, but, I think you might need a philosophy professor to explain why we have it.

---

### Post by HiImTye on 2012-03-19
[https://help.ubuntu.com/community/SwapFaq#Why_do_I_need_swap.3F](https://help.ubuntu.com/community/SwapFaq#Why_do_I_need_swap.3F)

---

### Post by d4m1r on 2012-03-19
> **HiImTye said:**
> [https://help.ubuntu.com/community/SwapFaq#Why_do_I_need_swap.3F](https://help.ubuntu.com/community/SwapFaq#Why_do_I_need_swap.3F)

Nice find, this seems like the official word and seems to reaffirm that based on my usage, enabling swap now would make no difference apart from allowing me to now use the suspend feature, which I don't plan to anyway though....

---

### Post by Miljet on 2012-03-19
> enabling swap now would make no difference apart from allowing me to now use the suspend feature
And one more time, suspend does not use swap space, hibernate uses swap.

---

### Post by 1clue on 2012-03-19
> **d4m1r said:**
> I disagree, as previously mentioned, if you have ANY swap space allocated, the system will begin to use it even BEFORE you run out of physical memory. In my case and most others, that would mean it would be doing things on my HDDs rather than my RAM (which is much faster) even though my RAM could be 50% unused.


This = drop in performance.

How soon before?

Ever since I built my current box I've been checking page swaps from time to time.  I started with 6g and on the day I saw a page-out (using several VMs and a large database as well, all active) I went out and doubled my RAM.  Since then I have never had a page swap, and it's been over a year.

Depending on how you tune your swap, it could start swapping early, but chances are there is a significant event that causes it.

IMO swap should be there for most end users, but they should be able to go months at a time with no swap activity.

Swap in its original context is like a motorcycle helmet.  You never want to use it, but the consequences of needing it when it's not there is scary.

RAM is cheap right now.  For a regular user of a regular PC, there is no reason to not have enough memory to never need swap.  People should buy equipment that holds a ridiculously large (by whatever standard is in place "today") amount of RAM, buy enough they can only use half of it and leave plenty of room for expansion later.

On the other hand, the swap mechanism is useful in more ways than just an emergency system.  Tmpfs for example speeds up the system instead of slowing it down, and it's the same mechanism.

---

### Post by anewguy on 2012-03-20
> **shuttleworthwannabe said:**
> This is exactly how Windows OS does it (but is also user accesible if need be to increase or decrease the pagefile size).

Yep - see my earlier post in this thread.

I've also seen mention in the thread about the true need for swap.  While there used to be such thing as a "warm" start to unix, if you had swap in a separate partition it wouldn't do you any good in the case of a big failure - you can't warm restart then anyway.  What swap was truely intended and used as was virtual memory.  With unix (and I would think any Linux variant) in a production mode with a couple hundred users plus "batch" type jobs running, real memory runs low.  Virtual memory was just used as extended memory but on disk - roll out the least used segments, roll them back in when needed.  Common enough on time sharing systems. Got too much of that going on?  That's thrashing, and it's time to take a look at the job load on your system versus your hardware.  I stick by what I said originally - for the normal user, email, chat, internet, maybe a movie or two, music - todays systems usually come with enough memory to make swap almost mute.  However, the beauty of Linux compared to say Windows, is you can get it to run on some really "small" hardware  - older systems with lower memory, etc..  In those cases swap becomes critical.For more advanced users, depending on their hardware, swap may be needed.  If you want to hibernate, you need swap.

Yes, it's a choice.  What I'm saying is for the average convert from Windows, swap means nothing to them.  It just adds a point of confusion.  I say that by default allocate a swap file based on memory size, and have the options available for manual configuration - just as you can with partitioning.  I know that sounds very much like Windows - but what's wrong with what something sounds like if it's an effective way to deal with a perceived problem?

Again, just my 2-cents worth - if it's worth even that much.  With that, I'll leave the discussion up to others.

Hope everyone is having/has/had a good one!

Dave ;)

dave ;)

---

### Post by bodhi.zazen on 2012-03-20
> **anewguy said:**
> i've also seen mention in the thread about the true need for swap.  While there used to be such thing as a "warm" start to unix, if you had swap in a separate partition it wouldn't do you any good in the case of a big failure - you can't warm restart then anyway.  What swap was truely intended and used as was virtual memory.  With unix (and i would think any linux variant) in a production mode with a couple hundred users plus "batch" type jobs running, real memory runs low.  Virtual memory was just used as extended memory but on disk - roll out the least used segments, roll them back in when needed.  Common enough on time sharing systems. Got too much of that going on?  That's thrashing, and it's time to take a look at the job load on your system versus your hardware.  I stick by what i said originally - for the normal user, email, chat, internet, maybe a movie or two, music - todays systems usually come with enough memory to make swap almost mute.  However, the beauty of linux compared to say windows, is you can get it to run on some really "small" hardware  - older systems with lower memory, etc..  In those cases swap becomes critical.for more advanced users, depending on their hardware, swap may be needed.  If you want to hibernate, you need swap.

+1

---

### Post by Cheesemill on 2012-03-20
There's an application called swapspace which I've been thinking of trying (but haven't got round too yet).

You basically have an installation without a dedicated swap partition or file, swapspace creates temporary swap files which get created and deleted as needed.

[http://pqxx.org/development/swapspace/](http://pqxx.org/development/swapspace/)

Has anyone used this or have any thoughts on the thinking behind it?

By using swap files instead of a partition I'll also be able to take advantage of TRIM fully on my SSD - as far as I am aware the 'discard' mount option will only work on ext partitions, not swap.

---

### Post by The Peanut on 2012-03-21
> **Cheesemill said:**
> There's an application called swapspace which I've been thinking of trying (but haven't got round too yet).

You basically have an installation without a dedicated swap partition or file, swapspace creates temporary swap files which get created and deleted as needed.

[http://pqxx.org/development/swapspace/](http://pqxx.org/development/swapspace/)

Has anyone used this or have any thoughts on the thinking behind it?

By using swap files instead of a partition I'll also be able to take advantage of TRIM fully on my SSD - as far as I am aware the 'discard' mount option will only work on ext partitions, not swap.

Hmhmh, that may be useful later on, or to the older people who don't need a swap but may want one... Good find :D
I'll install it and let you know how it goes!

---

### Post by scarr0 on 2012-04-09
I disagree with everybodies' opinions/assumptions!  The only way to know if you need swap or not is to make some swap space and monitor it with ***System Monitor*** or ***Task Manager*** or other utility apps.  :)

On my xubuntu box I use ***/usr/bin/xfce4-taskmanager*** and the built-in ***System Monitor***

---

### Post by 1clue on 2012-04-09
> **scarr0 said:**
> I disagree with everybodies' opinions/assumptions!  The only way to know if you need swap or not is to make some swap space and monitor it with ***System Monitor*** or ***Task Manager*** or other utility apps.  :)

On my xubuntu box I use ***/usr/bin/xfce4-taskmanager*** and the built-in ***System Monitor***

If you had bothered to read the thread instead of react to the title, you would have read several posts saying pretty much the same thing as you're saying only with more detail.

You really didn't need to sign up for an Ubuntu forums account just to post a seat-of-the-pants reaction did you?

---

### Post by anewguy on 2012-04-09
> **1clue said:**
> If you had bothered to read the thread instead of react to the title, you would have read several posts saying pretty much the same thing as you're saying only with more detail.

You really didn't need to sign up for an Ubuntu forums account just to post a seat-of-the-pants reaction did you?

A BIG +1.  That's the problem with a LOT of the replies in the forum.  People jump in in the middle or the end of a thread and assume they know everything.  People, before you post to a thread, READ the ENTIRE thread first so you understand how things got to where they currently are.  Understand the CONTEXT in which something is posted.  PLEASE.

As for this thread, I think it has run its' course and will ask a moderator to close it if the deem so as well.

Dave ;)

---

### Post by bodhi.zazen on 2012-04-09
> **anewguy said:**
> A BIG +1.  That's the problem with a LOT of the replies in the forum.  People jump in in the middle or the end of a thread and assume they know everything.  People, before you post to a thread, READ the ENTIRE thread first so you understand how things got to where they currently are.  Understand the CONTEXT in which something is posted.  PLEASE.

I have been guilty of that behavior ...

> As for this thread, I think it has run its' course and will ask a moderator to close it if the deem so as well.

Dave ;)

I agree with closing this thread. Swap has been a controversial issue for a long time as you can see from some of the links I posted.

There is no single solution that works for everyone. 

If in doubt, use a 1 Gb swap partition (that is the safe choice).

If you so desire, you can tune swap for your personal use.

---

