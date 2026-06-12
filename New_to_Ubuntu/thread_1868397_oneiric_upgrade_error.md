---
title: "oneiric upgrade error"
date: 2011-10-24
forum: New to Ubuntu
---

### Post by X_Ricardo_X on 2011-10-24
Hi everyone from ubuntuforums

I have been using it for several months now and never actually had to ask a question myself, but I couldn't find any answers for this one no matter how i searched.

But anyway, I'm running ubuntu with kde desktop almost as usual, but I'm not able to manage packages because dpkg was locked during the upgrade by ttf-mscorefonts-installer, wich asks me if I have a proxy (wich I don't), and when I answer it just asks again and again and never lets dpkg move on.

So, whenever I run sudo dpkg --configure -a, it stays locked in this package, and I would like to skip it's installation, is that possible?

---

### Post by mastablasta on 2011-10-24
what happens if you first uninstall that package (these are just MS fonts i believe) and then do the upgrade?

---

### Post by X_Ricardo_X on 2011-10-24
Thank you for replying, but unless I'm mistaken, I'm fully unable to manage packages, at least it's not possible with synaptics, Kpackagekit and apt-get. Is there anyway to enable package managing without sudo dpkg --configure -a?

---

