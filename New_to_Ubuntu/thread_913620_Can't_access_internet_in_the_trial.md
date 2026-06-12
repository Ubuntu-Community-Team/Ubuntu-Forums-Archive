---
title: "Can't access internet in the trial"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by EternallyNoob on 2008-09-07
Hi, I have yet to actually partition my hard drive and install Ubuntu, and the only reason for that is that I have very few privileges in the trial and can't connect to the internet. I'm pretty sure I would get more privileges once I've installed, that makes sense... But no internet? Hopefully these issues won't carry over once I've installed, but I just want to make sure... Is this supposed to happen? Thanks in advance.

---

### Post by Zzl1xndd on 2008-09-07
When you say Trial do you mean the live CD? And if so how are you connecting to the internet?

---

### Post by rossjman1 on 2008-09-07
You have the same privilages on the live cd as you do on an actual install. I'm assuming that you're trying to connect to the internet via wireless, because if you're plugged in via ethernet you should be connected to the internet. If you install you will need to configure your NIC.
What's the output of ifconfig? To do this you need to go to Applications > Accessories > Terminal and type in "ifconfig" and press the enter key.

---

### Post by Xiong Chiamiov on 2008-09-07
First, it's not a trial. ;)  Trials are free handicapped versions of paid-for software; this is free is all senses of the word, and not handicapped at all.  Any priviledge issues you have are due to you not operating as root (administrator in Windows-talk), which is a Good Thing(tm).  You can read a bit more about it [here]("http://openprinting.org/show_printer.cgi?recnum=HP-DeskJet_600").

What kind of wireless card do you have?  We might be able to tell you if it's going to work (well, easily) or not.

---

### Post by EternallyNoob on 2008-09-07
> **Xiong Chiamiov said:**
> First, it's not a trial. ;)  Trials are free handicapped versions of paid-for software; this is free is all senses of the word, and not handicapped at all.  Any priviledge issues you have are due to you not operating as root (administrator in Windows-talk), which is a Good Thing(tm).  You can read a bit more about it [here]("http://openprinting.org/show_printer.cgi?recnum=HP-DeskJet_600").

What kind of wireless card do you have?  We might be able to tell you if it's going to work (well, easily) or not.

Alright, I'm on an AirPort Extreme  (0x168C, 0x87) card. And, yes, I did mean I'm running from the live CD. I called it a trial because I'm pretty sure that's what it calls itself in the boot options. But let's try the terminal thing as a last resort. I'd rather not have to reboot if I don't have to. Oh, I don't know if it matters, but I'm on a mac.

---

### Post by Xiong Chiamiov on 2008-09-07
> **EternallyNoob said:**
> Oh, I don't know if it matters, but I'm on a mac.
Pff, well then, your hardware is compatible with Unix-like systems, so you (theoretically) shouldn't have any problems once you find the appropriate driver.

EDIT: Ok, well it seems like it's [this]("http://bcm43xx.berlios.de/") driver you'll need.  There are [a few]("http://ubuntuforums.org/showthread.php?t=142727") [guides]("http://ubuntuforums.org/showthread.php?t=314036") that I don't think you'll want to undertake before installing, as you wouldn't want to do it again.

---

### Post by EternallyNoob on 2008-09-07
> **Xiong Chiamiov said:**
> Pff, well then, your hardware is compatible with Unix-like systems, so you (theoretically) shouldn't have any problems once you find the appropriate driver.

Oh, good. Now, where do I go about finding this appropriate driver and installing it?

Edit: Looks like you answered before I finished posting. Man, this is a great community...

---

### Post by Xiong Chiamiov on 2008-09-07
> **EternallyNoob said:**
> Oh, good. Now, where do I go about finding this appropriate driver and installing it?

Edit: Looks like you answered before I finished posting. Man, this is a great community...
There's a reason I still hang out here even though I don't use Ubuntu.  Seriously, it breaks all the rules of online communities.

---

