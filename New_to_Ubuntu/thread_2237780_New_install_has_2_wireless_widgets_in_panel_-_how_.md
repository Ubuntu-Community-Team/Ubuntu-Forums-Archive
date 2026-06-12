---
title: "New install has 2 wireless widgets in panel - how to remove one?"
date: 2014-08-03
forum: New to Ubuntu
---

### Post by JeQhdMD on 2014-08-03
Just recently installed Lubuntu LXLE and notice there are two wireless network widget in the panel.   upon trying to edit panel, I am not seeing an obvious way to remove one of the applet/widgets.   I'm not especially familiar with the LX desktop . . .  so any tips appreciated.

---

### Post by Dennis N on 2014-08-03
Try the solution given here for the double network icon in LXLE:

[http://www.lxle.net/forum/#/discussion/477/64bit-double-network-icon](http://www.lxle.net/forum/#/discussion/477/64bit-double-network-icon)

---

### Post by Bucky Ball on 2014-08-03
I have the same issue on 14.04 Lubuntu, but have never bothered about it. I will give this a go. Cheers.

---

### Post by Dennis N on 2014-08-04
> **Bucky Ball said:**
> I have the same issue on 14.04 Lubuntu, but have never bothered about it. I will give this a go. Cheers.

I had followed the advice given at: [http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html](http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html) so I removed nm-applet from the "Manual Autostarted Applications" and that was it.  After restarting, there was only one network manager icon. The "network" box under "known applications" in that dialog is still checked on my system.

So, the Lubuntu users who were advised to use and followed that webupd8 suggestion, probably could do the same to fix this.

---

### Post by vasa1 on 2014-08-04
Interesting to see this:
> LXLE acronym change, originally 'Lubuntu eXtra Life Extension' which made sense before Lubuntu had an official LTS release, since 14.04 however, LXLE will now adopt the nomenclature 'LXDE eXtra Luxury Edition' and we think this release doubles down on that.Makes sense because LXLE offers a lot more (for those who want it by default).

Source: [http://lxle.net/articles/?post=lxle-releases-1404-64bit-12044-32bit-revisited](http://lxle.net/articles/?post=lxle-releases-1404-64bit-12044-32bit-revisited)

---

