---
title: "2gb ram = fine, 3gb ram = frozen-turtle-slow"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by BeastlyKings on 2008-05-14
My motherboard is an Abit IP-95, it has four RAM slots. 2x DDR and 2x DDR2. I had 1gb on one stick installed in one of the DDR2 slots.
Everything was fine and my computer was very fast. I installed 2gb on one stick into the free DDR2 slot and then booted windows. Everything was fine and my computer was fast. The I booted Ubuntu and I got an error after(?) grub saying something about an error acollating(?) the PCI bus on sector 1 and 9 or something like that. Then it proceeded to boot very slowly.
Instead of thrashing like it normally does on startup, the HDD just slowly churned here and there. And when I finally got a desktop the CPU was maxed out, then it calmed down, but anytime I tried doing anything it would max out and the comp was VERY slow.

I ran the live cd and got the same result. I haven't tried any other distro's to see if it is a kernal problem.

With just one of either stick of ram installed the system runs fine, but with both is bad news.. Right now I am running with only 2gb...

Please help? This is very frustrating.

---

### Post by tamoneya on 2008-05-14
are the clock speeds and cas latencies the same on both sticks?

---

### Post by wannadumpwindows on 2008-05-14
Try running the memory test on the LiveCD. Sounds like something isn't agreeing with each other with the two sticks. Doesn't make a whole lot of sense though. But see where memtest gets you. Let it run for a while and see what happens.

---

### Post by Don Giovanni on 2008-05-15
A lot of RAM (especially higher end stuff) tends to not operate well if you mix sizes.  Ideally you want to use the exact same make and size ram in each slot.  So it make simply be that the ram simply doesn;t agree with having 1x1GB stick and 1x2GB stick. Even if they are the same manufacture and same rating sometimes :P

But as was previously mentioned double check the clock speeds and latencies are the same.  Run memtest with both sticks in...if you get errors run with each stick individually to check both.

If both are fine on their own...I suggest either returning the 2GB module for a 1GB module.  Or sell off your 1GB module and get another 2GB module. 

Either way try to keep all your memory modules exactly the same. Best way to ensure stability.

---

### Post by jrusso2 on 2008-05-15
When using dual channel memory you should use two of the same sticks.

Same speed size and latency.  Its even wise to use the same brand at least on that channel

---

### Post by legolas on 2008-05-15
[http://ubuntuforums.org/showthread.php?t=164243](http://ubuntuforums.org/showthread.php?t=164243)

Went through the same problem.  It seems the kernel couldn't handle it and to keep the RAM upgrade, I would have had to re-build the kernel- WAY over my head.  I finally settled with 3gigs- 2 of my previous 512's and 2 of my new 1 gig sticks, and it seems to work fine.  Next time, I will try to re-install Ubuntu, with the RAM upgrade installed and it might adjust itself.

---

### Post by BeastlyKings on 2008-05-15
Thanks for all the replies guys! I will run memtest on both, then each, like you said. I tell you what I find out tonight.
As for the memory I'm using and the CAS latencies, they are the same and the only difference besides size that I can see is that one uses 0.1 volt less power.

The ram I had:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820231085](http://www.newegg.com/Product/Product.aspx?Item=N82E16820231085)
The ram I bought:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820231121](http://www.newegg.com/Product/Product.aspx?Item=N82E16820231121)

---

