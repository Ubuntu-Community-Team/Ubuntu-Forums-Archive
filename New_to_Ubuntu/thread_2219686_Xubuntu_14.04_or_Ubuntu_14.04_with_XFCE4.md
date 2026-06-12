---
title: "Xubuntu 14.04 or Ubuntu 14.04 with XFCE4"
date: 2014-04-25
forum: New to Ubuntu
---

### Post by zemega on 2014-04-25
Hi, with the release of 14.04 I am undecided whether to get Xubuntu of Ubuntu with XFCE. There is a big major bug to me in Xubuntu 14.04, that is "Xfce4 Power Manager does not restore screen power ([1259339]("https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1259339")), see the release notes for details and workarounds". I want to install Xubuntu on an old netbook with 1GB RAM. And this bug is raising my doubt in installing Xubuntu. This means that the user of this netbook will feel irritated with this bug. And those workaround are not really suitable for the user. So my question is, if I install Ubuntu 14.04 and install just the xfce4 package, will the bug still be around? Because, for me this seems like the best alternative. And no Lubuntu 14.04 since Lubuntu does not use the main Ubuntu repository.

---

### Post by deadflowr on 2014-04-25
> Lubuntu does not use the main Ubuntu repository.                 

Where does it grab the kernel from?

Anyway, if the xfce power problem has a fix in Ubuntu, then you can easily apply it to Xubuntu.

Edit: Forgot to say, Just install Xubuntu.

---

### Post by zemega on 2014-04-25
> **deadflowr said:**
> Where does it grab the kernel from?

I believe it uses the Lubuntu repository, at least that was the case with Lubuntu 12.04.

I dont think the xfce power problem has a fix in the Ubuntu, since installing xfce4 package will not install xfce4-power-manager, which seems to be the error source.

---

### Post by deadflowr on 2014-04-25
> **zemega said:**
> I believe it uses the Lubuntu repository, at least that was the case with Lubuntu 12.04.

I dont think the xfce power problem has a fix in the Ubuntu, since installing xfce4 package will not install xfce4-power-manager, which seems to be the error source.

Lubuntu uses the Ubuntu repos, like the others do.

I do see that xfce4-power-manager is part of the xubuntu-desktop package, which what xubuntu has.
for whatever that is worth.

---

### Post by zemega on 2014-04-25
Well. I'm just asking whether would the measure I propose will not trigger such bug. And I want to install the xfce4 package which does not contain the xfce4-power-manager , not the xubuntu-desktop package.

---

### Post by 3rdalbum on 2014-04-25
> **zemega said:**
> Well. I'm just asking whether would the measure I propose will not trigger such bug. And I want to install the xfce4 package which does not contain the xfce4-power-manager , not the xubuntu-desktop package.

If you want Xubuntu, install Xubuntu. It's easier than installing Ubuntu and then trying to grab all the bits of Xubuntu-Desktop that you want.

If you don't want xfce4-power-manager, just remove it again and install whatever the Gnome one is, if that's what you want to do.

---

### Post by Toz on 2014-04-25
To work around the bug you referenced, simply uninstall light-locker and install xscreensaver. The bug is with light-locker.

---

### Post by anaconda on 2014-04-25
> **zemega said:**
> This means that the user of this netbook will feel irritated with this bug. And those workaround are not really suitable for the user..

If you are installing it for someone else, why not install something, that wont need as much maintenance?
I prefer to install Debian stable (with xfce) for other peoples machines, that I have to maintain... It only needs minimal maintenance

Not much maintaining or problems. 

Or wait 6 months and install xubuntu 14.04 then, when worst bugs are already sorted out...

---

### Post by zemega on 2014-04-25
I'm not well versed in Linux environment as a whole, I just know Ubuntu. From some reading, it seems like its hard to make mtp work in Debian Wheezy. The Android mtp connection is actually the main factor for the user to stop using XP, as its really hard to get it working properly with the user Android phone, while in Ubuntu 14.04, it just work, plug in the Android phone and it opens up. No hassle at all. It also serve as a platform to be free from Windows.

I'll try the one with xscreensaver replacing light-locker first, but that was a major attraction to me, it sorts of standardise across the Ubuntu family.

---

