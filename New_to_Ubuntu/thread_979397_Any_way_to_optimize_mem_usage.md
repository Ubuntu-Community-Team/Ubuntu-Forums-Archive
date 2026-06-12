---
title: "Any way to optimize mem usage?"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by CryptiniteDemon on 2008-11-11
I have Xubuntu 8.10 installed on a machine with 256 mb of ram and a 2.0 ghz processor.  Everyone keeps telling me that it would run xubuntu fine, but it's as slow as can be. 

Any way I can suck less ram up?

---

### Post by ghost_ryder35 on 2008-11-11
This might help you [https://help.ubuntu.com/community/Fluxbox](https://help.ubuntu.com/community/Fluxbox) has a very small memory footprint

---

### Post by tgalati4 on 2008-11-11
Run top in a terminal and see what is eating your CPU cycles.  You can also run htop:
>sudo apt-get install htop
>htop

If this is a new installation, there may be indexing going on which will make things run slow for a while.

---

### Post by blackened on 2008-11-11
> **CryptiniteDemon said:**
> I have Xubuntu 8.10 installed on a machine with 256 mb of ram and a 2.0 ghz processor.  Everyone keeps telling me that it would run xubuntu fine, but it's as slow as can be. 

Any way I can suck less ram up?

For machines with less than 512MB of RAM, I always found xfce slow. As Ghost_Ryder suggested, I would also recommend using fluxbox. It's not as user friendly as xfce, but it makes up for that in speed and responsiveness.

---

### Post by Hospadar on 2008-11-11
you might try starting with an ubuntu server installation and then manually installing a light window manager like fluxbox on top of it.

If you want graphical login and whatnot, I think you can use xdm to log into something like fluxbox

---

### Post by igknighted on 2008-11-12
Unless you are very comfortable on linux and don't mind manually tweaking stuff, forget fluxbox.  There is no reason fluxbox should be necessary on a computer of that spec.  I used to run KDE on computer with a quarter of that processing power and the same amount of (slower) ram, and it was fine.  The problem is not that your computer can't handle it, rather you are almost certainly in one of three situations.

1) Your hardware is failing or in disrepair.  For example, if this is a really old computer and filled with dust, get some compressed air (less than $5 USD at any electronics store) and clean it out.  Also run the memory check on the liveCD to see if all your memory is working properly.  Finally, listen to your computer run.  Do you hear any noises coming from it that shouldn't be?  Especially grinding noises, probably from a hard drive?  A computer with that spec is likely of the age that a hard drive failure is becoming likely.

2) There is a driver issue.  Often a device not recognized properly (usually a graphics card) can cause the system to run painfully slow.  Try typing the command 'lspci' into the terminal and posting the results, as well as the command 'glxinfo | grep direct'.  We can see if any of the results indicate a potential driver issue.

3) A program is crashing in the background, tying up system resources.  Many things could cause this.  A bad install disk, a bad hard drive, or just bad luck, or even a bug.  The top command above will tell you what is running and how much memory and CPU it is using.  Also, if you run the command 'ps aux' and post the results we could look at it and see what we think (top produces constantly changing readout, difficult to copy/paste)

Hope this helps.

---

