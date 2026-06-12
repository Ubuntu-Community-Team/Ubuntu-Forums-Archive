---
title: "Problems while trying to install Ubuntu"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by daniell59 on 2008-10-25
I give up. I really wanted to try Ubuntu, but had zero success.
On my first attempt, I got error messages. This went away when I disabled the floppy drive in the BIOS. Why I had to do this I do not have a clue. I then tried to run it from CD. All I got was this prompt Initramfs -
I am running Vista 64 without any problems.
I really do not know where to go from here.

Thanks for listening

---

### Post by sethvath on 2008-10-25
I am assuming you are trying from the live cd/dvd. If it does not work judging from your initramfs thread try out [http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by daniell59 on 2008-10-25
I do not want to run it on windows. I burned a live CD, and wanted to try it first. I did two separate downloads on two different machines, yet I am not getting anywhere.

---

### Post by mdsmedia on 2008-10-25
> **daniell59 said:**
> I give up. I really wanted to try Ubuntu, but had zero success.
On my first attempt, I got error messages. This went away when I disabled the floppy drive in the BIOS. Why I had to do this I do not have a clue. I then tried to run it from CD. All I got was this prompt Initramfs -
I am running Vista 64 without any problems.
I really do not know where to go from here.

Thanks for listening
I'm a little confused. What did you try?

---

### Post by sethvath on 2008-10-25
Giving up after 2 tries? I have 14 laptops and desktops, and only 4 works "out of the box" with ubuntu. 

You will never get the full experience running a live cd.

---

### Post by sethvath on 2008-10-25
> **mdsmedia said:**
> I'm a little confused. What did you try?


Look up his previous 3 threads.

---

### Post by mdsmedia on 2008-10-25
> **sethvath said:**
> Giving up after 2 tries? I have 14 laptops and desktops, and only 4 works "out of the box" with ubuntu. 

You will never get the full experience running a live cd.
But if the Live CD doesn't work, it's a gimme that the full install will not be even attempted.

---

### Post by daniell59 on 2008-10-25
I really want to have some understanding what is going on.
1. Why did I have to disable the floppy drive in the BIOS to avoid the error message?

2. Why can't I run it from the live CD that I created?

---

### Post by philinux on 2008-10-25
What are your full hardware specs. Sometimes certain hardware can be the problem.

---

### Post by okey666 on 2008-10-25
I would help if you gave us the specifications of your machine and error messages that you are getting. Your machine may not be able to run the live cd for various reasons (not enough ram / slow cd drive etc). 

I have a friend who has ubuntu on his laptop. No live cd would work but once we managed to get it to install it runs really well with compiz fusion etc.

You say you are running 64-bit vista, are you trying to run 64-bit Ubuntu?

Please do not give up with Ubuntu, it should work and we will help you to get it to work. I had a really bad start with Ubuntu, it just froze every time I pressed start, but now I can't do without it.

---

### Post by mdsmedia on 2008-10-25
> **daniell59 said:**
> I really want to have some understanding what is going on.
1. Why did I have to disable the floppy drive in the BIOS to avoid the error message?

2. Why can't I run it from the live CD that I created?
To run it from the Live CD your computer needs to boot first from the CD/DVD drive that you're wanting to boot from. Why you had to disable the floppy I don't know. If you gave us an idea as to what the error was we might be able to help.

Is this a brand new PC with a floppy drive and does the computer want to boot from the floppy first?

---

### Post by sethvath on 2008-10-25
> **mdsmedia said:**
> But if the Live CD doesn't work, it's a gimme that the full install will not be even attempted.

Like I said in a previous post, 10 of my pcs refused to even work with the live cd. I had to spend days figuring out that I had to add an noapic acpi=off option to boot options before I can get them to play nice. They all run ubuntu, gentoo, fedora, opensuse and arch just fine now, if I gave up after the first 2 pcs I would never have found the solution. 

When times get tough, the tough get going.

---

### Post by daniell59 on 2008-10-25
Asus P5Q pro MB

Intel Core 2 Duo E8400 Wolfdale 3.0GHz 6MB L2 Cache LGA 775 65W Dual-Core Processor - Retail 

CORSAIR XMS2 DHX 4GB (2 x 2GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400
ASUS EAH3450/DI/256M Radeon HD 3450 256MB 64-bit GDDR2 PCI Express 2.0 x16 HDCP Ready CrossFire Supported Low Profile Video Card - Retail 

PS I really have not given up, but I just do not know what to do.

---

### Post by mdsmedia on 2008-10-25
> **sethvath said:**
> Like I said in a previous post, 10 of my pcs refused to even work with the live cd. I had to spend days figuring out that I had to add an noapic acpi=off option to boot options before I can get them to play nice. They all run ubuntu, gentoo, fedora, opensuse and arch just fine now, if I gave up after the first 2 pcs I would never have found the solution. 

When times get tough, the tough get going.I'm not saying that it won't work if LiveCD doesn't work. I'm saying if the LiveCD doesn't work it's a good chance the user won't try to install the OS. I know that having tried others, Ubuntu was the first that worked out of the box so I installed it. That was 3 years ago and I can't think of a reason not to use Ubuntu.

---

### Post by daniell59 on 2008-10-25
At this point I need concrete suggestions. I have two hard drives, and I was planning to install Ubuntu on the unused one.

---

### Post by mdsmedia on 2008-10-25
> **daniell59 said:**
> Asus P5Q pro MB

Intel Core 2 Duo E8400 Wolfdale 3.0GHz 6MB L2 Cache LGA 775 65W Dual-Core Processor - Retail 

CORSAIR XMS2 DHX 4GB (2 x 2GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400
ASUS EAH3450/DI/256M Radeon HD 3450 256MB 64-bit GDDR2 PCI Express 2.0 x16 HDCP Ready CrossFire Supported Low Profile Video Card - Retail 

PS I really have not given up, but I just do not know what to do.
What was the error given regarding the floppy drive? Was the computer trying to boot from the floppy before the CD/DVD?

---

### Post by daniell59 on 2008-10-25
The error is in my previous post. The DVD drive has priority in the boot order.

---

### Post by okey666 on 2008-10-25
The simple answer to live cd problems is to use the alternate install cd. This is not as user friendly however and will not allow you to try ubuntu. 

If you tell us the precise error the live cd gives we can tell you how to get it to work.

---

### Post by PmDematagoda on 2008-10-25
At what speed did you burn the live CD?

By the way, I am changing the title of this thread if you don't mind, the fact is that the current title is not very explanatory and the thread seems to have diverged from the original title's context.

---

### Post by daniell59 on 2008-10-25
In fact I tried 3 different CDs and two separate downloads on two different machines. It would be the height of presumption to believe that all three CDs are bad.

---

### Post by PmDematagoda on 2008-10-25
> **daniell59 said:**
> In fact I tried 3 different CDs and two separate downloads on two different machines. It would be the height of presumption to believe that all three CDs are bad.

But you still haven't answered my original question, at what speed did you burn the CDs? Did you test the CDs using the option in the Ubuntu live CD menu?

---

### Post by daniell59 on 2008-10-25
I don't remember the speed, but it was probably the maximum. I tried to the the integrity of the Cd, but that test would not work.

---

### Post by daniell59 on 2008-10-25
In fact the only thing that would work on the CD was the memory tester.

---

### Post by PmDematagoda on 2008-10-25
> **daniell59 said:**
> I don't remember the speed, but it was probably the maximum. I tried to the the integrity of the Cd, but that test would not work.

Well, then that may pretty much explain your problem.

Burn the Ubuntu live CD again, but this time burn it at a speed of 4x or less, nothing above, and then see if the Ubuntu live CD works properly.

---

