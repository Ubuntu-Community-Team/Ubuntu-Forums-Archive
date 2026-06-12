---
title: "Residual Terminal Commands"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by timjohn7 on 2008-08-14
As a relative noob, I have tried various options (blindly) to solve some teething problems eg getting my wireless card working, setting up my home network, getting virtualization working.
In all cases, I copied & pasted commands from extremely helpful contributors and in all cases with great success.
I have also installed various packages, both from repos and from other sources.  Some I have kept and others, discarded.

My problem is that I think that I have LOTS of residual fragments of code, drivers, bridges, and other stuff floating around in my system.  I am not knowledgeable enough to clean any of it up, but my boot message seems huge and lspci seems to give me far more than appears healthy.  I know for example that I tried parprouted to get wireless working in VBox but then found another method.  I never removed parprouted and it still seems to be floating around.

Besides a clean install, what can I do to get rid of what I don't want/need?

My bootmessage is attached if any expert would care to peruse it...

---

### Post by phidia on 2008-08-14
If you installed packages from source then you should read the README and INSTALL files for info on how to remove those. 
For programs you installed through apt you can > apt-get autoremove to clean up.

---

### Post by timjohn7 on 2008-08-14
Thanks phidia,

It's not so much apps that are the problem.  If I could provide an example...

I recently bought an Acecad Flair II Graphics Tablet (USB).  Everything except pressure sensitivity worked as soon as I plugged it in under Hardy (tested in the Gimp).

I checked Synaptic and installed X.Org X server -- AceCad input driver.  No change... I checked the forums and Google and found some old drivers that seemed promising so I downloaded the debs and installed them, testing the system after each one.

The first was for a Wacom Tablet.  The second caused a complete failure of the hardware.

I reverted to my backed up version and everything worked again.  I now want to remove the Wacom package and any residual dependencies from the other package but don't know where to start.

Autoremove reports:

tim@tim-laptop:~$ sudo apt-get autoremove
[sudo] password for tim: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

Also, looking at my bootmessage, I see ath0 and wifi0 but only have 1 Atheros card.  I remember trying to bridge it while following instructions to get wireless working in Vbox.  Can I remove either of them? DOes it make any difference that they are both loaded/referred to?

Apologies for the newness and probably naive questions.  I'm trying to learn and build confidence.

---

### Post by phidia on 2008-08-14
> **timjohn7 said:**
> Thanks phidia,

It's not so much apps that are the problem.  If I could provide an example...

I recently bought an Acecad Flair II Graphics Tablet (USB).  Everything except pressure sensitivity worked as soon as I plugged it in under Hardy (tested in the Gimp).

I checked Synaptic and installed X.Org X server -- AceCad input driver.  No change... I checked the forums and Google and found some old drivers that seemed promising so I downloaded the debs and installed them, testing the system after each one.

The first was for a Wacom Tablet.  The second caused a complete failure of the hardware.

I reverted to my backed up version and everything worked again.  I now want to remove the Wacom package and any residual dependencies from the other package but don't know where to start.

Autoremove reports:

tim@tim-laptop:~$ sudo apt-get autoremove
[sudo] password for tim: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

Also, looking at my bootmessage, I see ath0 and wifi0 but only have 1 Atheros card.  I remember trying to bridge it while following instructions to get wireless working in Vbox.  Can I remove either of them? DOes it make any difference that they are both loaded/referred to?

Apologies for the newness and probably naive questions.  I'm trying to learn and build confidence.

We were all new to this once so no need to apologize. I don't think  removing those modules, generally, is necessary. 

For the deb packages removing them should be as easy as "sudo dpkg -r packagename" See the dpkg [online man page]("http://www.annodex.net/cgi-bin/man/man2html?1+dpkg"). 

Are there any problems/symptoms with your install? If not then those packages probably don't matter much. 

As I said before anything you installed from source i.e a tar.gz package should have a text explanation on how to uninstall in the README files. For the .deb packages just use the command I provided and/or check out the man page link.

---

