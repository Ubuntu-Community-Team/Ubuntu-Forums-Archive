---
title: "Will Ubuntu detect my hardware better than Mandriva did?"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by MrCanuck on 2008-11-05
Hello.  

I recently got a copy of Linux Mandriva, and have had nothing but problems getting it to run on my Desktop, to me it does not seem very user friendly, and i know a good bit about computers.  It does not detect my proper video card, and does not detect my dial up modem so i cant get online, and no one seems to know how to fix it.

Looking at the Ubuntu site, this one looks to be very straight forward and user friendly, is my assessment right?  

Are there problems with Ubuntu detecting video cards (i have a NVIDIA GeForce FX 5500) and with dial up modems (i have a U.S. Robotics 56k Fax Win).  

Just wondering before i get a copy of Ubuntu and install it.  

Thanks.  :popcorn:

---

### Post by kurtymckurt on 2008-11-05
Let me tell you. I would suggest ubuntu to any new Linux user! It's based off of Debian which is a great Linux distribution.  When I first started installing ubuntu, i couldn't believe how easy it really was! Usually Ubuntu recognizes graphics cards very well.  I've never had a problem. One thing you will want to know is that there are restricted drivers as an option in the System menu. You'll want to go check that right away if it seems Ubuntu didn't recognize it well. 

One plus side to Ubuntu, if something doesn't work like your graphics card, you can submit a bug and in a short period of time you'll see an upgrade that will fix your problem. I've had this happen several times.  The community is very good about not letting bugs go on (unlike Microsoft).

Enjoy your experience with Ubuntu and let me know if there are any more questions or problems. Thanks
Kurtymckurt

---

### Post by DGortze380 on 2008-11-05
> **MrCanuck said:**
> Hello.  

I recently got a copy of Linux Mandriva, and have had nothing but problems getting it to run on my Desktop, to me it does not seem very user friendly, and i know a good bit about computers.  It does not detect my proper video card, and does not detect my dial up modem so i cant get online, and no one seems to know how to fix it.

Looking at the Ubuntu site, this one looks to be very straight forward and user friendly, is my assessment right?  

Are there problems with Ubuntu detecting video cards (i have a NVIDIA GeForce FX 5500) and with dial up modems (i have a U.S. Robotics 56k Fax Win).  

Just wondering before i get a copy of Ubuntu and install it.  

Thanks.  :popcorn:

NVIDIA cards shouldn't be a problem.
Disclaimer: 8.10 has some driver issues with legacy NVIDIA cards, but these cards function properly in 8.04 LTS. Don't know if your card is effected.

As far as the modem, I don't use dial up but have seen a number of threads on the forum about it. A quick search should yield some results.

---

### Post by philinux on 2008-11-05
Just try out the livecd.

---

### Post by mjitkop on 2008-11-05
If you can get a copy of the Live CD, you can just try it without installing anything. This way you will know if all works with your system. :)

P.S. [philinux]("http://ubuntuforums.org/member.php?u=353083") beat me to it! ;)

---

### Post by Krydahl on 2008-11-05
As I understand it (and I've never used one, so may be completely wrong) most win modems don't work well with linux (of any flavour) because they rely on windows to implement part of the stack that they really ought to handle themselves. I believe you can get dial-up modems that will work with linux, but they tend to be more expensive.

---

### Post by jamesrl on 2008-11-05
I find ubuntu to be very user friendly.  It gets slightly less friendly when you want to do more complicated things (e.g., say 4 years ago getting most b/g wireless cards were a major pain, and two years ago say dual monitors was difficult for me).  The last few installations (different computers for different people) those sorts of things worked out of the box with no real difficulties (the restricted drivers manager works great).  I still imagine that getting certain things like say getting a specific TV tuner cards, a draft-n wireless card, (e.g random cutting edge hardware), etc. working (where the hardware manufacturer doesn't have linux support, so someone from the community has to write it) or getting say a draft-n wireless card working could give you some issues.  But Nvidia and ATI graphics cards work great nowadays with the latest closed-source proprietary drivers.

Also unless you run virtualized windows (e.g., VirtualBox or Parallels, where you own a copy of windows, install it, and run it from within linux), you shouldn't expect to be able to run specific windows applications (mostly games and adobe photoshop) that aren't released for linux.  [You can get lucky and it could perfectly work within wine, but I wouldn't exect that.]

---

### Post by aysiu on 2008-11-05
Honestly, I'm not that hopeful.

In theory, Ubuntu's Hardware Manager should automatically detect your Nvidia card and install the proprietary driver for it. In practice, people have had mixed success with this tool (I and others have had success, but there are plenty of those who had not).

I believe the Nvidia driver would be fetched from an *online* software repository, anyhow, so if your dial-up isn't working, then that'd be hard.

Ah, which brings me to dial-up. Most modems are what are called "winmodems" and do not work well in Linux. But even if you were able to get it working, most Linux distributions (including Mandriva and Ubuntu) rely on a fast internet connection to install software, so having that dial-up connection will make software installation (including updates and proprietary drivers) difficult.

If you have dial-up, I would strongly recommend against switching to Ubuntu right now.

The best conditions for Ubuntu hardware-wise are to 1) buy it preinstalled or build your own computer with known Linux-friendly hardware and then 2) have a fast wired internet connection (or a fast connection on a Linux-friendly wireless card)

---

### Post by MrCanuck on 2008-11-05
Thanks for all the replies.  

So far i like this forum a lot better than the Mandriva one, :lolflag: much faster response here.  

I also have a new Acer laptop, so i will probably put Ubuntu on there also, and with that i can go into the City and pick up the wireless high speed to do all my updates, :p.  

Personally i am really tired of Microsoft, so i cant wait to get Ubuntu running.

---

