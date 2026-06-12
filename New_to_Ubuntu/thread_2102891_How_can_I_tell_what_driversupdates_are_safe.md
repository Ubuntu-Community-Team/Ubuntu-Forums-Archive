---
title: "How can I tell what drivers/updates are safe?"
date: 2013-01-08
forum: New to Ubuntu
---

### Post by tbrann on 2013-01-08
System info:
TOSHIBA Satellite C655D laptop
Processor:AMD E-300 APU with Radeon HD Graphics 1.3GHz 2 Core(s), 2 Logical Processors
Display: AMD Radeon HD 6310 Graphics
RAM: 2.00 GB

I have had problems in the past where I would get a complete freeze of my keyboard and mouse soon after installing Ubuntu 12.04 from a CD. I had checked the box for installing proprietary drivers, and I also installed all the updates. After restarting the computer, nothing would work, and I could only power off the computer. No one knew how to help me. In the end I just had to reformat my hard drive and reinstall.

This time during the installation, I did not install the proprietary drivers. 

But I don't have any way of knowing what caused the problem. So my question is, what can I do to be sure that the drivers and updates I install won't crash my system? And if the problem happens again, how can I track down what caused it?

---

### Post by haqking on 2013-01-08
> **tbrann said:**
> System info:
TOSHIBA Satellite C655D laptop
Processor:AMD E-300 APU with Radeon HD Graphics 1.3GHz 2 Core(s), 2 Logical Processors
Display: AMD Radeon HD 6310 Graphics
RAM: 2.00 GB

I have had problems in the past where I would get a complete freeze of my keyboard and mouse soon after installing Ubuntu 12.04 from a CD. I had checked the box for installing proprietary drivers, and I also installed all the updates. After restarting the computer, nothing would work, and I could only power off the computer. No one knew how to help me. In the end I just had to reformat my hard drive and reinstall.

This time during the installation, I did not install the proprietary drivers. 

But I don't have any way of knowing what caused the problem. So my question is, what can I do to be sure that the drivers and updates I install won't crash my system? And if the problem happens again, how can I track down what caused it?


how to be sure = you cant

how to see what happened = check the logs

Make backups/clones before doing anything, that way you can restore to a working system in minutes.

Peace

---

### Post by tbrann on 2013-01-08
How do I check the logs? Is there a command for that?

---

### Post by MG&amp;TL on 2013-01-08
> **tbrann said:**
> How do I check the logs? Is there a command for that?

Logs for jockey (which I *think* is what Ubuntu uses for driver install these days-could be wrong), can be found in the file /var/log/jockey.log

---

### Post by sandyd on 2013-01-08
> **MG&TL said:**
> Logs for jockey (which I *think* is what Ubuntu uses for driver install these days-could be wrong), can be found in the file /var/log/jockey.log
The logs for the _initial_ jockey run (i.e. when you first click on the hw drivers utility and install the drivers) are there. Any updates later on are in the DKMS buildlogs

---

### Post by tbrann on 2013-01-08
So when there's a crash and I can only get to the Root menu in Recovery mode, what would I type in to see those files?

---

### Post by MG&amp;TL on 2013-01-08
> **tbrann said:**
> So when there's a crash and I can only get to the Root menu in Recovery mode, what would I type in to see those files?

```
less /var/log/jockey.log
```

As for sandyd's catch, you'll have to wait for her. :)

---

### Post by Mark Phelps on 2013-01-08
Logs only help you AFTER the damage is done.

A better way to deal with this is to image off your setup BEFORE you make any changes.

Clonezilla can do this, will only take a few minutes, and gives you a way to cleanly restore your setup, also in only a few minutes.

---

