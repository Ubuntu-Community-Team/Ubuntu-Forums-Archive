---
title: "Can I make Ubuntu 12.04 mouse-and-keyboard-focused like Linux Mint"
date: 2012-06-14
forum: New to Ubuntu
---

### Post by pepperminty on 2012-06-14
Because of bugs in Mint 13 MATE 64-bit, I plan on installing Ubuntu 12.04 Gnome on my computer.


Is there a way I could make Ubuntu 12.04 look like Mint 13/Maya?
No, I'm not talking about the desktop theme or desktop wallpaper. I'm talking about getting rid of the big fat squares on the left sidebar, getting rid of the tablet/touchscreen interface, and going back to a for-keyboard-and-mouse-input environment that Mint focuses on.

Some things that I would like to have if I switch to Ubuntu 12.04:
1. A Sofware Update manager like Mint's. Designed to prevent inexperienced users from installing updates that are unnecessary or require a certain level of knowledge to configure properly. It assigns updates a safety-level (from 1 to 5), based on the stability and necessity of the update. Updates can be set to notify users (as is normal), be listed but not notify, or be hidden by default. In addition to including updates specifically for the Linux Mint distribution, the development team tests all package-wide updates.
2. An environment focused on keyboard and mouse.


Thanks.

---

### Post by steve7777777 on 2012-06-14
Those " the big fat squares..." are Unity. What "bugs" did you find in Mint 13 Maya?

---

### Post by ross56 on 2012-06-14
Like steve said, the squares on the left are part of unity, one of Ubuntu's default desktop environments. The de is still designed for a mouse and keyboard, and the functionality is pretty similar to the launchbar in Windows 7, the Unity bar being on the left side rather than the bottom. If that still isn't your preference, you can go back to the Gnome desktop, or try out KDE, XFCE, or LXDE. The last two can be a little tougher to customize and maintain, if you're more of a beginner/casual user. Kubuntu, Xubuntu, and Lubuntu are versions of Ubuntu that come with those de's, respectively, but you can always install more, if you want to try others. Check out some screenshots, read what people think about each, and feel free to try a few before you decide on one.

As far as the updates go, I have not yet come across an update through the update manager that required anything more than a restart. I made the mistake of installing a proprietary driver for my graphics card, but that was not something the Update Manager forced me to do, or even recommended me doing (plus it's the kind of thing that works for some people and not for others; you might want to explore this yourself). If you're still unsure about installing updates, the manager lists what is important, recommended, and optional or third party. I believe the default is for the manager to tell you each day if there are updates available, but you still have the option of removing some. Update frequency can be changed, though, and you can set the manager to automatically install updates, depending on your preference.

---

### Post by Derek Karpinski on 2012-06-14
[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed)

---

### Post by buzzingrobot on 2012-06-14
Both MATE and Cinnamon, the two Mint DE's, are available via PPA's for Ubuntu 12.04.

Be aware that the differences between Mint and Ubuntu are pretty small. Almost all the code you run in Mint is Ubuntu.

---

### Post by pepperminty on 2012-06-14
steve7777777,
The bugs I'm experiencing with Mint 13 64-bit MATE are:

**Power button causes shutdown, but I chose "Ask me"**
(bug report: [https://bugs.launchpad.net/linuxmint/+bug/1010608](https://bugs.launchpad.net/linuxmint/+bug/1010608))

**computer freezes/hangs when I plug in external monitor**
([https://bugs.launchpad.net/linuxmint/+bug/1012164](https://bugs.launchpad.net/linuxmint/+bug/1012164))

**"could not write bytes: Broken pipe" is message at shutdown**
 (I don't know if this error message is just cosmetic or whether it affects my Linux Mint)
([https://bugs.launchpad.net/linuxmint/+bug/1003538](https://bugs.launchpad.net/linuxmint/+bug/1003538))

**Shutdown is very slow unless i first disable networking**
[https://bugs.launchpad.net/linuxmint/+bug/1012159](https://bugs.launchpad.net/linuxmint/+bug/1012159)

---

### Post by pepperminty on 2012-06-14
buzzingrobot,

Thanks for your reply.

1. How do I install MATE inside Ubuntu?
2. Would installing MATE inside Ubuntu cause any problems?
3. What must I uninstall if I want MATE to work in Ubuntu? (For instance, should I remove Gnome and Unity?)

---

### Post by cortman on 2012-06-14
> **pepperminty said:**
> buzzingrobot,

Thanks for your reply.

1. How do I install MATE inside Ubuntu?
2. Would installing MATE inside Ubuntu cause any problems?
3. What must I uninstall if I want MATE to work in Ubuntu? (For instance, should I remove Gnome and Unity?)

1. Instructions [here]("http://www.howtogeek.com/110052/how-to-install-the-mate-desktop-go-back-to-gnome-2-on-ubuntu/").
2. I don't believe so- it's just another DE.
3. Nothing. Keep everything the way it is.

Although I would recommend you [install Cinnamon ]("http://www.howtogeek.com/103691/install-linux-mints-new-cinnamon-desktop-on-ubuntu/")rather than MATE- Cinnamon is a fork of the current and officially supported Gnome shell, whereas MATE is a fork of the dead Gnome2.
Cinnamon is looking very nice these days, too.

---

### Post by Myrddin Emrys on 2012-06-17
Cinnamon is worth a try, but MATE is much more complete and, far from being dead, is in active development. I find it works well without removing Unity, though you may need to apply a couple of post-installation tweaks:

[http://ubuntuforums.org/showpost.php?p=11931784&postcount=20](http://ubuntuforums.org/showpost.php?p=11931784&postcount=20)

---

