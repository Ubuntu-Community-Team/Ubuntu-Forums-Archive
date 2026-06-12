---
title: "How do I go about replacing noveau drivers with Nvidia?"
date: 2012-11-12
forum: New to Ubuntu
---

### Post by not1 on 2012-11-12
I'm getting GPU lockups frequently enough to warrant some troubleshooting, and removing Noveau seems to me to be the first way of going about it. I did select "use 3rd party software" when installing lubuntu from CD, but presumably Nvidia drivers were no part of this? 

Anyway, I'm a bit at odds of how to go about this. Does it have something to do with adding an Nvidia PPA? How do I find what specific driver is needed for my card? how do I go about uninstalling Noveau at the same time as installing the proprietary drivers?

---

### Post by gerowen on 2012-11-12
> **not1 said:**
> I'm getting GPU lockups frequently enough to warrant some troubleshooting, and removing Noveau seems to me to be the first way of going about it. I did select "use 3rd party software" when installing lubuntu from CD, but presumably Nvidia drivers were no part of this? 

Anyway, I'm a bit at odds of how to go about this. Does it have something to do with adding an Nvidia PPA? How do I find what specific driver is needed for my card? how do I go about uninstalling Noveau at the same time as installing the proprietary drivers?

In my experience, NVidia and ATI drivers are universal for all their cards.  For example, you install the fglrx drivers, and any ATI card should work (except in the latest version where the driver is at odds with the latest version of Xorg).

So for NVidia, I see 3 separate packages in the software center depending on which card you have.  Reading the descriptions shows that they actually tell you which cards are supported by which driver, so just hop into the software center, type "nvidia" into the search bar, and it's the top 3 results.  Attached is a screenshot for your reference.

Before installing it's a good idea to write down the actual package name so that if you reboot into a text login and the driver doesn't work, you can use apt-get to remove it and revert to the default driver.

---

### Post by not1 on 2012-11-12
Thanks gerowen! Installing the packages now. So... The Nvidia driver will automatically be used by the system over the noveau one?

---

### Post by gerowen on 2012-11-12
That's what happened for me when I installed the one for ATI. Part of the install was a script that set it up for me, saved me from having to manually edit .conf files,  :-)

---

### Post by not1 on 2012-11-12
Okay so the drivers changed over successfully on reboot, but now my cursor likes to disappear when I 'click' and youtube videos seem to play a little worse. I'm not sure if it has solved the GPU lockup problem yet. Nonetheless I may have to move back to noveau :/

Unless I can now fix this bug.

Thanks for your help :)

Edit: So going back to noveau would involve what? simply uninstalling the Nvidia package?
would that be: sudo apt-get remove Nvidia-current ?

---

### Post by newb85 on 2012-11-12
It may be easier using jockey.  You shouldn't have to uninstall anything to switch which drivers are in use.

From a terminal, type
```
sudo jockey-gtk
```
That should bring up a GUI for managing hardware drivers that is fairly straight-forward.

---

