---
title: "Ruined my OS"
date: 2012-12-06
forum: New to Ubuntu
---

### Post by camelface on 2012-12-06
I was running 10.10 or 11.04 (I always thought it to be 10.10 but when I would click on About Ubuntu it would say I was running 11.04 even though in the upgrade manager it would say upgrade TO 11.04). 

Anyway, I tried to instal the 12.04 upgrade by burning the iso to a cd and loading the cd into the Synaptic Upgrade Manager. I installed all available upgrades and notices a changed in my system: firefox new look, openoffice replaced by libreoffice, etc. But I restarted my computer and it does not boot anymore!

It says something like the following:

Ubuntu 10.10

Loading

Wait or Press S for skip system mount and M for manually boot/mount




But waiting does nothing, and this screen boots up even if my 12.04 disk is not in. Forgot to say as well that before going to this screen, the computer asks me to go in normal or recovery mode (offering different version of Linux for each) since I force restart it. 

Anyway, any help would be appreciated. I know these are things a newb shouldn't do, but now they are done and I would like some help out!

---

### Post by mythic97 on 2012-12-06
Have you got any important data on there?

check the BIOS boot options (F something on start up it should say)

select CD boot first

Boot from live system

Drastic action:

If not use Gparted (from a live CD) Move your data to a new partition then format the old partition then install 12.04 or anything you please on the old partition

---

### Post by monkeybrain2012 on 2012-12-06
I am afraid what you said doesn't make any sense. What do you mean by burning a live CD and load it in synaptic update manager?? 

You need to boot into the CD to install Ubuntu, that will wipe out your 11.04 (or 10.10??) so you would need to backup your data first.

---

### Post by camelface on 2012-12-06
> **monkeybrain2012 said:**
> I am afraid what you said doesn't make any sense. What do you mean by burning a live CD and load it in synaptic update manager?? 

You need to boot into the CD to install Ubuntu, that will wipe out your 11.04 (or 10.10??) so you would need to backup your data first.

I loaded the Cd I had burned of 12.04 ISO into the drive. Then I got a pop-up that said your Cd contains updates, would you like to add them to the Synaptic Upgrade Manager.. something like that. So I clicked yes and made those updates. Now my computer won't boot. 

So I'll try to boot from CD.




This is what it prints: 

Ubuntu 10.10

* * * *

The disk drive for / is not ready yet or not present

Continue to wait; or Press S to skip mounting or M for manual recovery

[http://askubuntu.com/questions/25302/error-after-upgrade-to-11-04-from-10-10-does-not-mount-volumes-correctly](http://askubuntu.com/questions/25302/error-after-upgrade-to-11-04-from-10-10-does-not-mount-volumes-correctly)

sounds like a separate problem

---

### Post by TheFu on 2012-12-06
> **camelface said:**
> I was running 10.10 or 11.04 (I always thought it to be 10.10 but when I would click on About Ubuntu it would say I was running 11.04 even though in the upgrade manager it would say upgrade TO 11.04). 

Anyway, I tried to instal the 12.04 upgrade by burning the iso to a cd and loading the cd into the Synaptic Upgrade Manager. I installed all available upgrades and notices a changed in my system: firefox new look, openoffice replaced by libreoffice, etc. But I restarted my computer and it does not boot anymore!

Without the facts, we are just guessing.  That could cause more issues than you already have.  Upgrades between versions of Ubuntu must follow a certain path.

* You can update from LTS release to LTS release 
OR
* You can update from any release to the next (not skipping) release.

It is not possible to safely upgrade from a non-LTS release by skipping to another release. This should not be allowed by the update process since it would be dangerous and possibly very bad.

Going from 10.10 to 12.04 is **not** supported.
Going from 11.04 to 12.04 is **not** supported.
**From 10.10, only an update to 11.04 is supported.**
The only approved, supported, way to get to 12.04 LTS is from either 
* 11.10 or
* 10.04 LTS.

Exactly which version of Ubuntu were you running and which version are you running today?  The only way that I know to get the most accurate data is to look inside the /etc/lsb-release file and get the result of `uname -a`. Of course, if you aborted the update process, then your lsb-release file could have inaccurate data.

A few years ago, I did update from 6.06 to 8.04 by installing 1 release at a time. It wasn't fun, but it wasn't hard either.  Since 2008, Canonical has made it easier to understand updates - April (04) and October (10) are when they release new versions. 12.04 is from April 2012 and 12.10 is from Oct 2012.  In April 2013 13.04 will be released. It will not be an LTS - that happens only during April of even years. Simple.

To avoid this sort of confusion, it is best for non-techincal and/or lazy people to stay on LTS releases only and update every 2 years from LTS to LTS to LTS. There are pros and cons to this method.  It works for me, but I'm just lazy and want minimal hassles.

It is possible that your forced non-supported upgrade path broke the install and has left not just the boot sector in a bad state, but the entire OS programs and settings too.  At this point, I'd trust my "pre-upgrade" backup, wipe the OS, and install a fresh 12.04.  Then I'd restore my $HOME and selected other data.

Perhaps someone else will provide some hope, but I fear it will be false hope. Good luck to you.

---

### Post by camelface on 2012-12-06
My data is not super important but I do hope to keep it. I'll try to do something that will enable me to keep it, back it up and then to a complete reboot/format. So let me see what the liveCD allows me to do...

---

### Post by camelface on 2012-12-06
Booted from the 12.04 liveCD. I selected the option "Upgrade" and was able to keep all my files. I just need to reconfigure everything. 


PS. Unity is hrmm-how-could-I-say-it-nicely-?

---

### Post by monkeybrain2012 on 2012-12-06
> **camelface said:**
> Booted from the 12.04 liveCD. I selected the option "Upgrade" and was able to keep all my files. I just need to reconfigure everything. 


PS. Unity is hrmm-how-could-I-say-it-nicely-?

I suggest you to back up your data and do a fresh install to avoid later problems and "upgrade" will take hours even if it works. Fresh install takes 20-30 minutes. If you have installed third party applications or proprietary drivers you need to remove them first and reverse (downgrade) software install through ppas, so it is more troubles then it is worth if your system is a not so pristine.

In your case upgrade is even more dicey because for one reason or another your original system is broken.

P.S. I love Unity. :)

---

