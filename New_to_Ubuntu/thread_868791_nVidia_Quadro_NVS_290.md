---
title: "nVidia Quadro NVS 290"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by pzs on 2008-07-24
I'm about to buy a new machine from Dell and have been quoted for a box with the above graphics card. I need this to run dual-head. Can anybody tell me whether they've made this work?

---

### Post by overdrank on 2008-07-24
> **pzs said:**
> I'm about to buy a new machine from Dell and have been quoted for a box with the above graphics card. I need this to run dual-head. Can anybody tell me whether they've made this work?

Hi and some users have had issues with nvidia graphics but could you give us some more system specs, plus is it a desktop or laptop?

---

### Post by Hospadar on 2008-07-24
Generally nvidia cards tend to work great with ubuntu.  I've done several dual-head setups with an older 5900 and my new 8600, both with relative ease and good quality.  I'd assume the quadros will be no exception as they use basically the same hardware as the geforce cards.  That said, if you could get a geforce in the machine for the same price, I'd do it, more people use them, i.e. they will be better supported in the community and otherwise.  The only exception would be maybe if you plan on using CUDA to do crazy style matrix math on your graphics card, but if you were that smart, you probably wouldn't be asking around here =P  Besides, CUDA will run basically the same on a geforce.

---

### Post by pzs on 2008-07-24
Thanks for the quick response.

T5400-Intel Xeon X5460 (3.16GHz,1333FSB,2x6MB,Quad Core)
Memory : 8GB (4x2048) 667MHz DDR2 Quad Channel FBD
256MB PCIe x16 nVidia Quadro NVS 290 (ULGA8), Dual Monitor DVI or VGA
Graphics Card
Hard Drive : 750GB (7200Rpm) Serial ATA II
Display : 19in 1908FP UK/Irish Black UltraSharp (1280 x 1024) TCO99 DVI-D (x2)

The quote (1600ukp) seems to come with Windows XP and a bunch of other software I don't need. I'd quibble over this, but it's been hard enough to get the quote in the first place. This is the problem with "approved suppliers" - if they're slow you don't have a good threat to get them moving. If I don't get the thing ordered soon I'll be left twiddling my thumbs with no machine to work on.

Any advice on this spec or managing Dell in general most welcome :)

---

### Post by enkrypt3d on 2009-05-18
> **pzs said:**
> Thanks for the quick response.

T5400-Intel Xeon X5460 (3.16GHz,1333FSB,2x6MB,Quad Core)
Memory : 8GB (4x2048) 667MHz DDR2 Quad Channel FBD
256MB PCIe x16 nVidia Quadro NVS 290 (ULGA8), Dual Monitor DVI or VGA
Graphics Card
Hard Drive : 750GB (7200Rpm) Serial ATA II
Display : 19in 1908FP UK/Irish Black UltraSharp (1280 x 1024) TCO99 DVI-D (x2)

The quote (1600ukp) seems to come with Windows XP and a bunch of other software I don't need. I'd quibble over this, but it's been hard enough to get the quote in the first place. This is the problem with "approved suppliers" - if they're slow you don't have a good threat to get them moving. If I don't get the thing ordered soon I'll be left twiddling my thumbs with no machine to work on.

Any advice on this spec or managing Dell in general most welcome :)

Just found this thread because I'm trying to install Kubuntu 9.04 x64 on my new Dell T5400 with dual quadro NVS 290's... and it wont even startx during the install... 

"no screens found"... I have tried removing the 2nd monitor with same result.. Maybe it doesn't like the dual quadro cards? I can't seem to find any info on it... and yea i know this is the ubuntu forums but this applies here as well.

---

### Post by penguinv on 2009-10-28
> **pzs said:**
> I'm about to buy a new machine from Dell and have been quoted for a box with the above graphics card. I need this to run dual-head. Can anybody tell me whether they've made this work?

I'd like to know what dual-head means.
TY
I am interested in the Quadro card which is why I am reading this thread.
For my present machine if would be AGP not PCIe. Unless I upgrade.

---

### Post by penguinv on 2009-10-28
> **Hospadar said:**
> Generally nvidia cards tend to work great with ubuntu.  I've done several dual-head setups with an older 5900 and my new 8600, both with relative ease and good quality.  I'd assume the quadros will be no exception as they use basically the same hardware as the geforce cards.  That said, if you could get a geforce in the machine for the same price, I'd do it, more people use them, i.e. they will be better supported in the community and otherwise.  The only exception would be maybe if you plan on using CUDA to do crazy style matrix math on your graphics card, but if you were that smart, you probably wouldn't be asking around here =P  Besides, CUDA will run basically the same on a geforce.

The quadro card is recommended for an animation program I want to use, called Maya. 

Just to let you know there are reasons, other than CUDA.

---

### Post by falconindy on 2009-10-28
> **penguinv said:**
> I'd like to know what dual-head means.
TY
I am interested in the Quadro card which is why I am reading this thread.
For my present machine if would be AGP not PCIe. Unless I upgrade.
Old thread is old. Dual-head means 2 monitors on the same graphics card.

---

### Post by penguinv on 2009-11-02
> **falconindy said:**
> Old thread is old. Dual-head means 2 monitors on the same graphics card.

Do you have to have a special graphics card with two monitor inputs for that?

---

### Post by wshaffer79 on 2013-01-29
> **falconindy said:**
> Old thread is old. Dual-head means 2 monitors on the same graphics card.
 
Yes old thread is old, but if the thread relates to a current problem, it's sometimes useful to resurrect the thread.  When does a thread become "too old"?
 
I didn't see an actual answer to the original question in this thread other than "nvidia cards usually work..."  OP posted in 2008.  It's 2013 and there still seems to be an issue with this card, at least with propietary drivers.  See my other thread here:
 
[http://ubuntuforums.org/showthread.php?t=2096541](http://ubuntuforums.org/showthread.php?t=2096541)
 
My system has two NVIDIA Quaddro NVS 290 cards installed, each with a dual head DVI port (via a splitter on each card -- 4 monitors total).
 
Short story:  Ubuntu 12.10 with the default nouveau drivers enables one card to run two displays, but the second card is not detected by the display properties (but it IS detected by the kernel).  Proprietary NVIDIA drivers result in a "Video BIOS not available" message from the kernel (maybe from the driver?) upon reboot... and total system freeze.
 
Should I just give up on this card with Ubuntu?  Is this also an issue with other distros with this NVS 290 card?

---

### Post by oldos2er on 2013-01-29
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

