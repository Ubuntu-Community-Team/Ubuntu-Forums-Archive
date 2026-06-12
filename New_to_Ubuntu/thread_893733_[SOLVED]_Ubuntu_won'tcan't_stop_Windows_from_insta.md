---
title: "[SOLVED] Ubuntu won't/can't stop Windows from installing, right?"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by Sydius on 2008-08-18
So I send my mother a laptop with Linux.  She loves it.  But then she gets an ATT wireless USB Internet connection that requires either Windows software or some moderately-complicated (to a computer-illiterate mother) Linux fiddling.  I send her a Windows XP disc--the laptop has a valid (legal) license of Windows associated with it, anyway (I just thought Ubuntu was better--still do).

Unfortunately, it, as well as every other Windows XP disc she has tried, will not install--they all freeze, crash, or do other bad things.  It's an old laptop, and not unlikely that the DVD drive is slightly broken--that's my theory, anyway.  The same discs work in other computers.  I told her to just wipe the Ubuntu install and put Windows only (to keep things easy), but it doesn't get to the point of asking her which partition to install before crashing.

Of course, everyone in western Colorado who knew a slight amount about computers but not enough to be of real help suddenly popped up offering to fix it for her.  They managed to reformat the hard drive and ruin the boot partition, but that's about it so far.  They are all impressed that a kid (I'm 23) could do something as advanced as install Linux on a computer (... *sigh*), but insist it is preventing Windows from installing properly.

Various people have suggested that--at least three, including one "professional computer technician," (the guy who said he was impressed I could have installed Linux in the first place, since installing Linux is something only a REAL pro can do).  They gave various reasonings for this theory, such as the laptop having been made for Windows and that having Linux blocks it.  I say nay, but alas, I am a thousand miles away in California, and my opinion matters less (being a mere professional programmer and all).

Dell (it's a Dell laptop) even said that, should she be able to boot up to the point of having Internet access (golly, the very reason she wanted Windows...) they could direct her to a web site, where she would click a link that would install Windows for her from a web site (what?! ...).

Okay, am I going insane? I can't conceive of a way Linux would prevent Windows from installing or even getting the partition list, unless there were a hardware problem.  I also don't know how Dell could do what they claim, and have to believe there's a big misunderstanding there.

So frustrated.

---

### Post by rockerphil on 2008-08-18
ok, i seriously doubt that Ubuntu/Linux would stop Windows from installing, it's simply mind boggling how that's even possible. it very well may be a hardware issue and a simple CD device replacement may do the trick, also what pops to mind is the machine being a bit too old for XP to run well, but how would that stop the installation? my suggestion is to try replacing the CD device, or try an older version of Windows possibly 2000. best of luck and hope you get the problem solved,

Phil

---

### Post by Sydius on 2008-08-18
> **rockerphil said:**
> ok, i seriously doubt that Ubuntu/Linux would stop Windows from installing, it's simply mind boggling how that's even possible. it very well may be a hardware issue and a simple CD device replacement may do the trick, also what pops to mind is the machine being a bit too old for XP to run well, but how would that stop the installation? my suggestion is to try replacing the CD device, or try an older version of Windows possibly 2000. best of luck and hope you get the problem solved,

Phil

It originally came preloaded with XP and more than meets the requirements.

---

### Post by rockerphil on 2008-08-18
if the box more than meets the minimum XP requirements then i can't think of anything other than a hardware issue, and i've never heard of being able to install Windows from a web site, but somehow it wouldn't surprise me in this day and age, don't know how it would work though, but as i said before, i'd try replacing the CD device.

Phil

---

### Post by f37u5g0d on 2008-08-18
I have heard of windows vista not letting linux install on another partition but that has vista and we're talking about xp.  I seriously doubt that linux is "blocking" an xp install.  It is confusing though because the xp install fails while the ubuntu install succeeds with the exact same hardware so unless the drive broke after the ubuntu install that is obviously ruled out.  I do however think that something is wrong with the hardware on her computer.  You could try running the live CD completely reformatting the entire drive and then installing xp.  If xp won't install then I think it's clear that some part of the laptops hardware is broken.

BTW where did you find all of the computer clowns?  And wtf is dell talking about?  Just for laughs you should try and get that website and post it on these forums.

---

### Post by Sydius on 2008-08-18
> **f37u5g0d said:**
> I have heard of windows vista not letting linux install on another partition but that has vista and we're talking about xp.  I seriously doubt that linux is "blocking" an xp install.  It is confusing though because the xp install fails while the ubuntu install succeeds with the exact same hardware so unless the drive broke after the ubuntu install that is obviously ruled out.  I do however think that something is wrong with the hardware on her computer.  You could try running the live CD completely reformatting the entire drive and then installing xp.  If xp won't install then I think it's clear that some part of the laptops hardware is broken.

BTW where did you find all of the computer clowns?  And wtf is dell talking about?  Just for laughs you should try and get that website and post it on these forums.

I installed Ubuntu before mailing it to her; she tried installing XP after receiving it.  So very possible it was broken in transit.  She's also the one who found all the people and talked to Dell.  I told her to just go get a USB CD drive from the store (it can boot from USB devices, the BIOS says), and try that, but no... she believes the experts more... who tell her they will fix it sometime this week.

---

### Post by Crafty Kisses on 2008-08-18
No, Ubuntu won't stop Windows from installing, if anything there is a problem with the HD on that laptop and the technician guy doesn't sound that savvy with computers if he thinks installing Linux is hard, but yeah definitely a hardware issue, I'd say tell your mom to send the laptop back to Dell, assuming that it's still under warranty and have Dell take look at it and maybe they can solve the issue and everything can be good again.

---

### Post by LowSky on 2008-08-18
I don't know exactly how old the laptop is but if the laptop has a SATA hard drive then Windows XP cannot install because XP needs the SATA drviers.

Other possible theory s that the RAM has a few bad sectors. But if you install UBunutu just fine I kinda doubt that.

Why don't you have her mail you the laptop and you fix it.

PC techs are trained as if they are washer machine repairmen. They get one certification and think it will cover their 40 year career. Most of them know little about operating systems or anything beyond the guts of the computer, and only understand how they fit together, nothing about how they actually work. They will almost always suggest replacement of parts or reinstallation of the OS (Windows Whatever) with little or any diagnosis.

---

### Post by Sydius on 2008-08-18
At this point, I feel as if, if she doesn't want to take my advice, so be it.  I just wanted to be sure I wasn't lying when I said the tech was silly and that Linux can't block Windows from installing.

Symptoms include a solid blue screen (with no text), or errors saying various files could not be found on the CD.  That's why I think it's a CD drive issue.  Linux was running fine (until one of the "helpers" thought reformatting the drive before installing would help it install more easily).

---

### Post by arpanaut on 2008-08-18
> I don't know exactly how old the laptop is but if the laptop has a SATA hard drive then Windows XP cannot install because XP needs the SATA drviers.


I second that notion... SATA drives won't be reconized and the install process will fail without installing those drivers at the initial phase...

Immediatly upon booting the install CD, F6 needs to be hit to install the SATA drivers...  

But a "trained Professional" windows tech should know that LOL

Good Luck!

---

