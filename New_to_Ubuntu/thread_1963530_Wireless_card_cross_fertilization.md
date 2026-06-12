---
title: "Wireless card cross fertilization"
date: 2012-04-22
forum: New to Ubuntu
---

### Post by JXR on 2012-04-22
I'm hoping someone involved with Ubuntu might be able to supply some information to solve my wireless card problem. 
 
Background: I installed Ubuntu on a Dell Inspiron 2650, but Linux overwhelmed the system and I could never get the laptop's keyboard/touchpad to work and so it was suggested I try an antiX (Linux) install. I succeeded in the antiX install and, glory be, the keyboard and touchpad worked in that OS!!
 
Problem is, my wireless card--a **Belkin 802.11b 2.4 GHz DSSSPCMCIA wireless Notebook Network Card F5D6020 ver.2 ...card (IEEE 802.11b/11Mbps)**--isn't being 'seen' by antiX and the folk that are trying to solve this problem are pulling their hair out.
 
These are some of their comments:
- This is the first time I have ever seen inxi -F fail to pick up a pcmcia card for wireless.
- I downloaded the XP driver and extracted the .exe file to look inside to see if I could find your chip. Nothing was in install.ini or any other .exe file I extracted that showed what wireless chip is used.
- from [http://questier.com/howto.html#Belkin](http://questier.com/howto.html#Belkin) Since kernel 2.6, driver support for this card is built in in the kernel.
However, a proprietary firmware is needed. This can be installed very easy with synaptic or with apt-get: apt-get install atmel-firmware
- This new version of the Belkin F5D6020 is hard to distinguish from the previous version, but uses a complete different chipset, anno 2003 not yet supported out of the box in all Linux distributions.
- Debian Sarge is ancient compared to Debian Wheezy and that card is also ancient.
- I would still like to know what chip that card uses though via a inxi readout or some other readout to be sure before continuing with this thread.
 
Ubuntu immediately recognized the wireless card (which, incidentally, still works just fine in the XP part of the (antiX/XP) dual boot) without a hitch and was immediately able to connect me with my LinkSys router.
 
BECAUSE UBUNTU DOES RECOGNIZE AND WORK WELL WITH THIS WIRELESS CARD is there any information I can get from this Ubuntu forum that might relate to the problem at hand.
 
Thanks.

---

### Post by anewguy on 2012-04-22
Do you have to install a pcmcia support package first?

Also - I had a 2650 years ago, and I had Ubuntu in those days and had no problem with the touchpad or the keyboard (in those days you had to install the synaptic touch driver).I'm curious about how much memory you have, also.  If memory serves me correctly, I believe those systems came with 128mb, upgradable to 512mb.  If you're memory isn't maxed out, I would.

Also, I think 1 of the lighter versions of ubuntu or another linux would ne called for.

I think it's been about a year ago I got 2 Dell's very cheap on EBay - 1 was another 2650, but I just reinstalled Windows on both of those and sold them.  Sticks in my head I had to upgrade the memory in it also before Windows wanted to cooperate.

Also - lspcmcia should list pcmcia devices - and hopefully we can get an id from that list that will help us find the chipset being used in your adapter.

Dave ;)

---

