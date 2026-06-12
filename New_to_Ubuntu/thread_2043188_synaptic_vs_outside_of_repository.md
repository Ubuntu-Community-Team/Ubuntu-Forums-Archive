---
title: "synaptic vs outside of repository"
date: 2012-08-16
forum: New to Ubuntu
---

### Post by kiers on 2012-08-16
Hi all,
(Still) Running 10.10 Maverick.
Normally i am using Synaptic package manager for all my updates and new functionality as needed. However, for the newfangled MTP and MTPFS (to connect new phones and tablets to my Ubuntu) i've had the need to compile and install libmtp from OUTSIDE the "universe" synaptic recommends for 10.10. 


But now, synaptic does NOT show the latest version of the lib (1.1.1). It still shows the old version 1.0.3-4 (with the orange box next to it filled in.)

Does this mean the new version i ran "make" on and "make install" did not take hold?

If one gets the occaisonal packages from a .gz direct download, should one UN install the older stuff first? or does the tar, config, make, make install process take care of everything?

Also, if I want to update libmtp yet again from 1.1.1 to 1.1.3 (again direct download from .gz file over the web) should i uninstall the previous 1.1.1 first? or is it automatic.

thanks

---

### Post by 3rdalbum on 2012-08-16
Synaptic doesn't keep track of what is actually on your hard disk, it only tracks what it installs. If you compile something it wont be known to Synaptic.

---

### Post by kiers on 2012-08-16
what about the uninstall step? should i do that or is it OK to simply run the "Make Install" process time and again on top of existing compiled .gz files?

---

### Post by ads52 on 2012-08-16
The easiest thing to do is to use the checkinstall utility, if used judiciously this will integrate your package into the Ubuntu package management system.

---

