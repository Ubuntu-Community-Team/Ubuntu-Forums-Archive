---
title: "Ubuntu locks when switching users"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by PoopyTheJ on 2008-04-30
When trying to switch users Ubuntu goes to a black screen and locks. I let it sit all night just to see if it was slow, but no, it was lcoked. What do I need to do to fix this?

---

### Post by SlappyPappy on 2008-04-30
What hardware do you have, specifically video card? I'm guessing ATI.

I heard about this while cycling through the forums a few weeks ago. Can't remember a solution but there should be some help hidden somewhere in the forums.

Good luck man.

---

### Post by PoopyTheJ on 2008-04-30
ATI video card. 2GB RAM, E4600, p5kse motherboard. Thanks, do you know what I should search for?

---

### Post by garyed on 2008-04-30
I'm running Feisty on my Toshiba laptop & I have the same problem & have not found a fix for it yet. I heard there was some kind of bug but it only happens on some computers. Its been so long since I tried to switch users that I'm not sure but I think it used to just lock up after I entered the password. I just tried it again & it gets me back into Gnome but then locks up. I have to reboot every time. If you find a solution please post it because I'm pretty much resigned to it until I upgrade.

---

### Post by SlappyPappy on 2008-04-30
Keywords switch user freeze brings up some stuff.

[http://ubuntuforums.org/showthread.php?t=640373](http://ubuntuforums.org/showthread.php?t=640373)

---

### Post by PoopyTheJ on 2008-04-30
Ok after perusing the forums and google I found this, [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/120444](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/120444), this is talking about a crash using the fglrx drivers from ati. I am crashing as the screen is black, machine responds to no input, no HSS activity light, etc. So now being the absolute newb I am how do I find out if I'm using the fglrx driver? I used envy to dl and install the driver from ATI, does that mean I'm using the fglrx driver. And if so, I am using Compiz, what do I have to do to uninstall the fglrx driver, and install some other driver. Do I need to do anything with compiz? What am I going to see as a difference when using the Open rather than closed driver and how do I get the open driver?

---

