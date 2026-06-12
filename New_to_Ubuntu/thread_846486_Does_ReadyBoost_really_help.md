---
title: "Does ReadyBoost really help?"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by wariskampar on 2008-07-01
I read in some else that Ubuntu can also enjoy ReadyBoost feature as Vista user. I'm just curious if this method really help because if it does I would rather buy additional USB pen drive than RAM.

---

### Post by KenBW2 on 2008-07-01
That's what linux's swap has been for years - before Vista.
It's a section of your Hard Drive that basically contains the overflow from your RAM, or if your PC doesnt see you using that info any time soon.

---

### Post by logos34 on 2008-07-01
> **KenBW2 said:**
> That's what linux's swap has been for years - before Vista.
It's a section of your Hard Drive that basically contains the overflow from your RAM, or if your PC doesnt see you using that info any time soon.

+1

plus it's a lot slower when compared to swap on hard disk.  AND it wears out your usb.

In other words, a typical windows gimmick

---

### Post by sayakb on 2008-07-01
Formatting any removable media/HDD partition with swap and turning it on (by firing **swapon /dev/sda**x) filesystem will enable Linux to use it as swap/virtual RAM. When SWAP is utilized, generally the OS becomes very slow (as removable media as well as disks are very slow as compared to RAM). ReadyBoost is even slower. You can adjust the swap usage tendency by changing the swappiness: [http://lifehacker.com/software/feature/slim-down-and-speed-up-linux-333798.php](http://lifehacker.com/software/feature/slim-down-and-speed-up-linux-333798.php)

---

### Post by Paqman on 2008-07-01
> **wariskampar said:**
> I would rather buy additional USB pen drive than RAM.

Even if it's cheaper, it's a false economy. Any performance boost you get will be poor. You'd get much better value out of actual RAM.

---

### Post by lazyart on 2008-07-01
Let's clarify a few things here.

Linux swap partition is equivalent to Windows swap file.  Hard drive space used as physical memory.

ReadyBoost is a quicker version of the same, using your flash drive as the swap file.  Is there a way to temporarily mount a thumb drive as swap?  I dunno if there is.

If your swap is getting a lot of use then it's probably time to add memory.  I run 4 gb and my swap usage is always at zero.  Yes, you're better off with more physical memory than using swap.  Readyboost would be quicker than a hard drive for swap but agreed it can kill off a flash drive (they only have so many read/write cycles) and it's really just a band-aid.

---

### Post by sdennie on 2008-07-01
You should also check to see if you actually need more RAM.  For a typical user, with 1G of RAM, you will rarely, if ever need swap.  With 2G of RAM, unless you are using VMs or other memory intensive apps, it would be very hard to get the machine to actually use swap.

---

### Post by wolfen69 on 2008-07-01
i have never heard of ubuntu using a pendrive as memory. as far i know, this feature does not exist. if it does, prove it.

---

### Post by wariskampar on 2008-07-01
Thanks guys. I'll dump this idea once and for all. May have to live with my 1GB RAM until I can afford a new one

---

### Post by Steveway on 2008-07-01
> **wolfen69 said:**
> i have never heard of ubuntu using a pendrive as memory. as far i know, this feature does not exist. if it does, prove it.

I just killed an USB-stick (as an experiment) by using it as swap.
The stick lasted about a week till it refused to work.
ReadyBoost is a really stupid idea.

---

### Post by wolfen69 on 2008-07-01
unless you have 30 apps open at once, 1gb is more than enough to run ubuntu. you must stop thinking in windows terms. you will probably never use the full 1 gig. im a power user and have never used more than 450mb.

---

### Post by wolfen69 on 2008-07-01
> **Steveway said:**
> I just killed an USB-stick (as an experiment) by using it as swap.
The stick lasted about a week till it refused to work.
ReadyBoost is a really stupid idea.

you may be able to set it up as swap, but not like ready boost. which is stupid anyway.

---

### Post by Steveway on 2008-07-01
> **wolfen69 said:**
> you may be able to set it up as swap, but not like ready boost. which is stupid anyway.

That's what I did, and what I said.

---

### Post by KenBW2 on 2008-07-01
I have 512MB RAM and never run out. Read carefully...

A.NORMAL.OS.DOES.NOT.NEED.1GB.MINIMUM!

---

### Post by sayakb on 2008-07-01
One of my laptops has 1GB RAM. And it actually, does run out of RAM. I have 3-4 screenlets on the screen. Usually when I use Firefox continuously for about 7-8 hrs, the RAM usage goes upto 900MB. Now since I have reduced the swappiness to 10, the swap usage starts rising at 900MB+ RAM usage. Killing and re-launching FF brings it down to 700. Right now, I have only the SysMonitor screenlet + FF and its using 600MB of RAM. Also, in another laptop of mine, I don't have swap on my HDD but on a 2GB SD card. Im using it since 3 months and its working perfectly.

---

### Post by damis648 on 2008-07-01
They call ReadyBoost "innovation"...

...Ummm... when exactly did we come up with swap?!

---

### Post by Tomatz on 2008-07-01
> **logos34 said:**
> +1

plus it's a lot slower when compared to swap on hard disk.  AND it wears out your usb.

In other words, a typical windows gimmick

Wrong

The seek time on a small flash drive is much faster than a HDD...


But it's no substitute for physical ram. ;)

---

### Post by damis648 on 2008-07-01
> **Tomatz said:**
> The seek time on a small flash drive is much faster than a HDD...

Yes. Exactly why we want SSDs and why they are so expensive.

---

### Post by Tomatz on 2008-07-01
> **damis648 said:**
> Yes. Exactly why we want SSDs and why they are so expensive.

I have done it before on my eeepc which only has 512 ram and did notice a difference when playing Wolf ET on it.

But i would suggest just buy ram as it is so cheap now ;)

---

### Post by Raistlin355 on 2008-07-01
Since I heard about the "Vista Readyboost" I immediately thought of the swap file in Linux and the pagefile in Windows (same thing just different names) and I wondered "What would be the use for this?!?" and then it hit me.  Vista wants like 2gb of memory to run smoothly and M$ knew this but they wanted people to upgrade their OS so they came out with readyboost so people with old machines didn't have to buy ram and go through the *hassle* of installing it, they could just plug in a usbn drive and viola!! no more swapping.   Now having used this on a Vista box with 512MB of memory, readyboost is the worst, the performance you get is crappy (as usb xfer rate is slower than RAM) and it wore out my usb drive in 2 days.  Someone said earlier itt "Typical M$ gimmick" that is true, it is no more than a gimmick to get people who don't know any better to buy their crappy os.

---

### Post by wariskampar on 2008-07-01
I often heard people say that RAM is cheap nowadays. I'm afraid it's not true for SODIMM 1GB 333Mhz (2.5 CLS and blah blah..). I really dont understand why of all the RAM available in market, this is the most expensive (around EURO 70 compare to EURO 40 for other type). My HP PAvilion dv4000 is so happen to use this type of RAM:(. Can I substitute it with different speed (666Mhz) which is cheaper?

---

### Post by Tomatz on 2008-07-02
> **wariskampar said:**
> I often heard people say that RAM is cheap nowadays. I'm afraid it's not true for SODIMM 1GB 333Mhz (2.5 CLS and blah blah..). I really dont understand why of all the RAM available in market, this is the most expensive (around EURO 70 compare to EURO 40 for other type). My HP PAvilion dv4000 is so happen to use this type of RAM:(. Can I substitute it with different speed (666Mhz) which is cheaper?

Yeah the older ddr ram is more expensive because it is not made in large quantities anymore. You couldn't substitute with 666mhz because that would be ddr2 which would be incompatible with your board.


Ebay?

---

