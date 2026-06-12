---
title: "What install configuration should I pick for my hardware?"
date: 2011-12-10
forum: New to Ubuntu
---

### Post by mitman94 on 2011-12-10
I currently have a Dell B866r Pentium III 866MHz 256MB RDRAM computer with an (extremely) outdated video card.  I have a new 80GB Samsung IDE hard drive waiting to be used.  It can handle Windows XP, but is slow when handling many applications.  While this is not my newest computer, I would still like to install some form of Linux on it.  With this configuration, I'm wondering if I should install K/X/L/Ubuntu or another distro, which setup I should use if I choose an Ubuntu derivative (desktop vs. alternate install vs. a custom minimalist install).  What would be best for this configuration given I'll be mostly be using Firefox/Office and developing using Eclipse for C/C++/Java, phpMyAdmin, LAMP, etc, and possibly dual-booting with Win XP?

---

### Post by Bucky Ball on 2011-12-10
Xubuntu or Lubuntu. Forget Kubuntu, it will run badly, if at all, on those specs. Straight Ubuntu won't be much better.

If you had a little more experience I would definitely advise the minimal install. It installs an extremely basic system, enough to get you running and online, then you download the packages you want only (not everything else). You can do this also by adding you desired packages to the packages to be loaded initially for the base install. This can be tricky if you've little to no experience with Ubuntu, though. A real learning curve!

---

### Post by bluexrider on 2011-12-10
with those specs you need a extremely light distro

[http://distrowatch.com/table.php?distribution=damnsmall](http://distrowatch.com/table.php?distribution=damnsmall)

---

### Post by ilikelinuxitisthebest on 2011-12-10
i honestly don't reccomend Ubuntu or any of its variants for that old of a computer. there is a very lightweight distro called puppy Linux that you can use. damn small is also nice but puppy is better and easier to use.

---

### Post by pakopako on 2011-12-10
> **ilikelinuxitisthebest said:**
> i honestly don't reccomend Ubuntu or any of its variants for that old of a computer. there is a very lightweight distro called puppy Linux that you can use. damn small is also nice but puppy is better and easier to use.
I really like **Puppy Linux** and keep a liveCD for emergencies, but Puppy has you as root all the time which feels a little odd for a long term OS.

I had a similar issue with an old Dell Pentium-III a long time ago and was suggested **Anti-X** Linux as well. (I wound up installing XP and gave it to my grandparents as their "gaming" machine.)

---

### Post by wildmanne39 on 2011-12-10
I agree with Bucky Ball that Lubuntu or xubuntu will work okay but Lubuntu is lighter then xubuntu is at this time.

The other distributions would be harder for a new person to set up.

---

### Post by mcduck on 2011-12-13
I'd definitely do a minimal install and add Openbox or pure LXDE on machine with those specs. But Lubuntu might be OK as well. (Lubuntu uses about three times the RAM my own minimal install+Openbox system does)

The biggest issue I see is the low RAM, while doing the development stuff might be quite tolerable things like web browsers, office apps and Eclipse will be quite horrible to use. If there's any chance at all to upgrade the RAM you should do it. Even upgrading it to 512MB would make a big difference in usability, and if you could make it 1024MB you'd defintely have much better experience.

The sad thing is that it doesn't matter how lightweight desktop environment or base system you use, modern browsers simply require so much RAM to work nicely that 256MB is definitely not enough for even a decent experience.

---

### Post by mastablasta on 2011-12-13
lubuntu will work ok. you will need to use light applications. 
 
also ther eis a bug in graphcis installer in Lubuntu that can make it crash on install with 256 MB or less. Use alternate CD or mini.iso to overcome this isue.
 
lubuntu uses about 80 MB at idle. 
 
Indeed another interesting option is Puppy linux. They have a version based on Ubuntu repositories.

---

