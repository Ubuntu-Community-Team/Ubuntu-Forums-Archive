---
title: "Hi! A few questions from a noob who wants to try out all the desktops"
date: 2015-07-14
forum: New to Ubuntu
---

### Post by TestTestington on 2015-07-14
Hi,

I appreciate any help I get here, so thanks.

Firstly, can I change my username on these forums?

I recently installed Ubuntu 15.04 and I don't really like the GUI and so I was wondering what is the best way to try out all the other GUIs so that I can eventually find one I like?

I already tried this on Ubuntu:
sudo apt-get update
sudo apt-get install kubuntu-desktop
and it installed, but then there were graphics glitches in Plasma and it's completely un-usable. I repeated this on a clean installation and had the same problem. However when I formatted and installed Kubuntu 15.04 from the ISO it worked. So it seems like they don't play nicely together. Do I need to install each flavor of Ubuntu on a new partition? Am I using the wrong command? Any advice is appreciated.

Ideally I want to have one Ubuntu partition with all the different GUIs installed and then I'll eventually remove the ones I don't like.

---

### Post by howefield on 2015-07-14
> **devan2 said:**
> Firstly, can I change my username on these forums?

Sure, post a thread in the [Resolution Centre]("http://ubuntuforums.org/forumdisplay.php?f=123") or pm me with 3 alternatives.

> Do I need to install each flavor of Ubuntu on a new partition?

That's one way of doing it (and my preferred way), or you can install each desktop and choose which one to use at the login screen which can be messy as you end up with mixed software/menus not to mention potential conflicts.

The graphical glitches you experienced with KDE may have been down to a drivers issue, did you check for additional drivers which may make your card work better ?

There are several threads already in the forums that you might want to browse.. eg
[http://ubuntuforums.org/showthread.php?t=2173651](http://ubuntuforums.org/showthread.php?t=2173651)
[http://ubuntuforums.org/showthread.php?t=2201030](http://ubuntuforums.org/showthread.php?t=2201030)
[http://ubuntuforums.org/showthread.php?t=2224294](http://ubuntuforums.org/showthread.php?t=2224294)

---

### Post by v3.xx on 2015-07-14
A couple of desktop environments that DO NOT add clutter or conflict if installed to Ubuntu.

Flashback
to install
```
sudo apt-get install gnome-panel
```

LXDE
```
sudo apt-get install lxde
```

There are others; that’s just the first two I thought of :)

---

### Post by sammiev on 2015-07-14
Welcome,

You can also try all the different flavors using a USB/DVD live and see which one suits you.

---

### Post by TestTestington on 2015-07-14
I think it probably was a driver issue because when I installed and updated VirtualBox Guest Additions then rebooted, even my clean install of Kubuntu broke. I am just not sure how to revert the drivers without formatting though.

BTW I am running off a physical partition that is bootable which I also run in VirtualBox.

Thanks for the links to other threads and the suggestions. I will try them out.

---

### Post by SeijiSensei on 2015-07-15
Kubuntu 15+ uses the Plasma 5 desktop from KDE which, in my opinion, isn't ready for prime-time.  You should really be using 14.04LTS to start out since it will be supported for a long time to come and is very stable.  Avoid non-LTS releases until you have a good bit of experience with Linux and Ubuntu.

---

