---
title: "[SOLVED] Why won't Ubuntu load on these specs?"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by Confused Computer User on 2008-08-18
Hi. I have a Dell Dimension 3000 with Intel Celeron CPU (2.4 GHz) and 254MB RAM (one 254MB RAM DDR1 memory stick). 

Note: the computer has a Intel video card and the RAM is as displayed when running dxdiag under Win XP

My question is. How come Ubuntu (live CD) won’t load on it? 
Here is the deal. I have an older computer with Pentium III (400MHz) and 256MB RAM (two 128 MB RAM  memory sticks)

Note: for the second computer I am not sure if the memory is SDRAM or something else (it’s not DDR1 or DRR2).

Umbutu Loads on the older computer but not on the newer. It identifies the components (presumably since it does load the desktop background and the mouse) and it goes to the point where it loads the desktop but that’s where I have to wait for ages. I see the background and the mouse is semi responsive but nothing else.

Why is this happening? Can Intel Celeron play such a difference compared to an old Pentium III? I mean in terms of processing speed Pentium III is 6 times slower than Intel Celeron.

I’m not a computer wiz but I know that Intel Celeron is sort of a cheaper processor because it has less cache but how does that affect Ubuntu?:confused:

Thanks in advance.

---

### Post by halitech on 2008-08-18
typically Ubuntu requires 384meg of ram to run the live cd. If you are running the alt cd, it should install on either machine with no problem. It might be the difference in the video cards with the better system using on-board.


(ps. memory comes in amounts divisible by 8 so it would be 256meg but might be using 2 meg for on-board video??)

---

### Post by Confused Computer User on 2008-08-18
Hi Halitech,

Thanks for the reply.I have to disagree to some extent. The 384MB RAM are needed to run the installation process with a graphical interface. However if i simply boot from the CD I can use a lesser amount of RAM than 384. This can be attested by the fact that it ran on the older computer.

---

### Post by Daveski on 2008-08-18
> **Confused Computer User said:**
> 
Umbutu Loads on the older computer but not on the newer. It identifies the components (presumably since it does load the desktop background and the mouse) and it goes to the point where it loads the desktop but that’s where I have to wait for ages. I see the background and the mouse is semi responsive but nothing else.

Have you tried booting the LiveCD in a 'safe' video mode? F4 at the boot screen I think...

---

### Post by halitech on 2008-08-18
> **Confused Computer User said:**
> Hi Halitech,

Thanks for the reply.I have to disagree to some extent. The 384MB RAM are needed to run the installation process with a graphical interface. However if i simply boot from the CD I can use a lesser amount of RAM than 384. This can be attested by the fact that it ran on the older computer.

thats why I said typically requires 384 to run but I've seen stranger things happen :D

> Have you tried booting the LiveCD in a 'safe' video mode? F4 at the boot screen I think...

I'd suggest trying as Daveski suggested and try a different mode cause if you are showing 254 meg of ram in windows and your system has 256 then you only have 2 meg going to your video and it may not have enough power to run it properly.

---

### Post by Confused Computer User on 2008-08-18
Thank you Halitech and Daveski. I will try what you suggested and I will post back my results tomorrow.

Note: The video card is an Integrated Intel extreme Graphics 2. From another computer I know that usually, Intel graphic cards have a certain amount of memory and then they take the rest from the RAM. Usually it's about 32MB and then the rest is from RAM.

In my case when running dxdiag in Win XP I am told the video card has 96MB. it seems weird but that's it.

Again thank you for the posts. I'll reply back with results tomorrow. :popcorn:

---

### Post by Living2007 on 2008-08-18
I don't belive the processer is to blame for Ubutnu not to load.

When you insert the LiveCD, do you get the Ubuntu to load with a list like: "Install Ubuntu", or "Boot from Hard Disk". Commands like that!

---

### Post by halitech on 2008-08-18
> **Confused Computer User said:**
> Thank you Halitech and Daveski. I will try what you suggested and I will post back my results tomorrow.

Note: The video card is an Integrated Intel extreme Graphics 2. From another computer I know that usually, Intel graphic cards have a certain amount of memory and then they take the rest from the RAM. Usually it's about 32MB and then the rest is from RAM.

In my case when running dxdiag in Win XP I am told the video card has 96MB. it seems weird but that's it.

Again thank you for the posts. I'll reply back with results tomorrow. :popcorn:

I've only dealt with 1 system that had onboard video and I put an actual card in instead of using the onboard so not sure how they usually work. Maybe Windows can pull from the RAM if its needed but Ubuntu doesn't have that ability to do the same?

good luck and hopefully the safe mode will work for you

---

### Post by cariboo on 2008-08-18
I've got a MSI motherboard with on board video according to System-->Administration-->Nvidia X server Settings I have 256MB video ram, even though I set the video ram to 32MB in the bios, So it seems Ubuntu takes the amount of ram it needs to make the video adapter work.

Jim

---

### Post by Confused Computer User on 2008-08-19
Ok.

So I used F4 at the main menu prior to loading Linux (ie. Where you are asked to select if you wish to install or just run from the CD) and selected safe graphics mode.

It worked and Linux Loaded but with a 640x480 resolution. It loaded relatively fast but it was still a bit slow on certain things. Which brings me to the question: Can a too small resolution have a similar effect to a higher resolution in terms of slowing down the computer?

Note: I ran Ubuntu Release 8.04 (Hardy). Using System Monitor I found that Ubuntu recognizes 248.2MB RAM and it supposedly uses 54% of it.  I am not certain how much the video memory is.

Cariboo907, you say:

> I've got a MSI motherboard with on board video according to System-->Administration-->Nvidia X server Settings I have 256MB video ram, even though I set the video ram to 32MB in the bios, So it seems Ubuntu takes the amount of ram it needs to make the video adapter work.

Can this mean that I am in need of more RAM?:(

Basing myself on Halitech’s statement about the required amount of RAM (348) and Daveski’s suggestion to run in Video safe mode it could mean that because of the video card I have, Ubuntu tries to enable some visual effects but it essentially cuts the branch from underneath its self by digging in the RAM. I say this because on the older Pentium III the video card is weak (8 MB maybe less). As I said Ubuntu runs on the old computer with a higher resolution (1024x768) but the RAM is left untouched 256, whereas on the Dell Dimension 3000 the RAM is partially allocated to the video card. 

Note: I make the assumption that similar to Vista (OS I use the most at this point in time) Ubuntu has the option of running some visual effects with the window interface (ie smoothing the edges, fading etc.). So depending on the Hardware these effects are enabled or disabled.

I ran Ubuntu a while back on a newer (low end) computer (Pentium IV HT, 2GB RAM, 32MB Video memory... note the video card is also an intel and it shares RAM under Vista but has 32MB of it's own memory) and I was amazed by the visual appearance of it, not to mention the speed and responsiveness.

Note: Living2007, thank you for the post but I did mention that i get to the point where I can see the Desktop Background so I pass the stage where I choose the set up Language and the “installation” mode. This was never the issue. The problem was getting the rest of Desktop (ie menus and shortcuts) to load.

Thank you all for the support so far.

P.S. My apologies if the post is a bit long. I tend to give the information in one big chunk in order to give a larger view of the problem.:(

---

### Post by hyper_ch on 2008-08-19
At the bottom: [http://www.ubuntu.com/products/WhatIsUbuntu/desktopedition](http://www.ubuntu.com/products/WhatIsUbuntu/desktopedition)
> 
System Requirements

Ubuntu is available for PC, 64-Bit PC and Intel based Mac architectures. At least 256 MB of RAM is required to run the alternate install CD (384MB of RAM is required to use the live CD based installer). Install requires at least 4 GB of disk space. 


Earlier version could boot the live cd with 256 mb ram. I think the Xubuntu live cd still works with 256mb ram... possibly less.

---

### Post by nynoah on 2008-08-19
I suggest using Xubuntu.  Even if you get it to load with normal Ubuntu, that computer will be a dog.  Xubutu is lighter and can still do most all the things Ubuntu can do. If that is still to large, try Flux Ubuntu.

---

### Post by Confused Computer User on 2008-08-19
Got it.

So I can either use another Linux flavor or increase RAM. I am certain that if I use another distro like PuppyLinux I can probably  do most of the things that Ubuntu does but, and this is a big but, would I be able to Run open office in it? I doubt it (not certain).

Also, given the specs for Dell Dimension 3000, would more RAM enable me to run Ubuntu?

Thank you for the support.

---

### Post by halitech on 2008-08-19
upping the ram to at least 512 would certianly allow you to run Ubuntu. Xubuntu should run as is but would be slower with only 256 meg of ram.

Not sure about running open office on puppy, I think it does have an older version you can install but not sure. I know dsl has it in its list of installable programs

---

### Post by candtalan on 2008-08-19
> **Confused Computer User said:**
> Got it.

So I can either use another Linux flavor or increase RAM. I am certain that if I use another distro like PuppyLinux I can probably  do most of the things that Ubuntu does but, and this is a big but, would I be able to Run open office in it? I doubt it (not certain).

Also, given the specs for Dell Dimension 3000, would more RAM enable me to run Ubuntu?

Thank you for the support.

There is a big difference in running *from* the live cd and running after having *installed* it. An installed system will run ok in  256 mb ram, even kubuntu (very slow) on PII machines (I use 384 mb). The live cd is a slightly special case and needs ram to work in, and more processor and cd time.

If you install using the alternate cd, not using the live cd to neither run nor install, things will improve.

Puppy is a great distro, it is more tuned and designed to run as live cd, in small resources, although if you install it it uses a slightly special install technique (which confused me.....I am sorry to say). 

If you install ubuntu using the alternate cd, then later, yuo can install (download) the xubuntu-desktop package an d then choose to log into the xubuntu session. Or if you are perverse like me also have the choice of kubuntu-desktop package benefits, albeit with a very significant slowness.

hth

---

### Post by snowpine on 2008-08-19
Hi Confused Computer, your computer is right at the low-end limit for running Ubuntu. You will certainly need to install using the Alternate CD and not the Live CD. You will see a HUGE difference in performance with a full hard disk install vs. running the Live CD. Whether or not that increased performance is fast enough for you is a personal preference. I used to have Ubuntu on a P3 with 256mb of ram, but my short attention span couldn't handle it! :)

There is an "official" derivative called Xubuntu that should give you a performance boost over Ubuntu, while still being fundamentally the same user experience. There are also "unoffical" distros (like Fluxbuntu, Crunchbang, etc.) that are quite a bit faster but less well supported. Finally, there are distros like Puppy, DSL, that are super-fast but aren't part of the Ubuntu family at all.

---

### Post by Irihapeti on 2008-08-19
> **Confused Computer User said:**
> Got it.

So I can either use another Linux flavor or increase RAM. I am certain that if I use another distro like PuppyLinux I can probably  do most of the things that Ubuntu does but, and this is a big but, would I be able to Run open office in it? I doubt it (not certain).

Also, given the specs for Dell Dimension 3000, would more RAM enable me to run Ubuntu?

Thank you for the support.

Yes, you can run OpenOffice in Puppy Linux.

Irihapeti

---

### Post by Confused Computer User on 2008-08-21
Thank you all for the support and help. 

Now to sum up this thread.

Problem: Loading Ubuntu (Hardy) from the live CD (no install)
Hardware: Dell Dimension 3000 (256 MB RAM, 32MB Video CARD, Intel Celeron processor 2.4GHz)
Solution: Multiple answers are available here. To load it I pressed F5 at the main menu screen (the menu where you choose if you wish to do an install, boot from CD, etc.) and select Safe Graphics Mode. This had the effect of giving me a very low resolution. The issue is that because of my amount of RAM, using the Live CD is very slow. So doing an install will help. Adding more RAM is also a solution.

Note: in my case the Video card has a small memory of its own and then takes extra memory from the RAM which reduces the amount of RAM available to Ubuntu. The solution is more RAM or an install or both. 

Well, that's about it. If anybody has something else to add or correct feel free to do so. I'll mark this thread as solve in 24-48 hours.

Once again, thank you all for the support. 

Cheers:guitar:

---

### Post by bigken on 2008-08-21
spend a tenner (£10) and double your ram

---

