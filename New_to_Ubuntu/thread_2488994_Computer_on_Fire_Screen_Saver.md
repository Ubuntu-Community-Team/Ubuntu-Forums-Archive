---
title: "Computer on Fire Screen Saver"
date: 2023-07-14
forum: New to Ubuntu
---

### Post by tiffafk on 2023-07-14
I was running Kubuntu/kfce on ubuntu and when my computer went into suspension (sort of) the screen became an emergency broadcast of primary colors with the image of a computer monitor on fire.

I removed Kubuntu, but

What was that?

---

### Post by Xian on 2023-07-15
Sounds like an instance of the xscreensaver application. 

You can remove:

$ sudo apt-get remove xscreensaver

---

### Post by guiverc on 2023-07-15
Kubuntu uses the KDE Plasma Desktop; a less corporate *owned* desktop (*or Kool Desktop Environment*) aimed as a replacement for the prior CDE or prior Common Desktop environment. It uses the Qt toolkit/libraries.

X forms led to the creation of Xfce, which actually started around the same time as KDE but using more of the earlier XForms code thus the Xf in Xfce. Xfce was ported to use GTK in due course.

Lubuntu currently uses xscreensaver, alas neither Kubuntu (KDE) or Xubuntu (Xfce) have, at least not for a long time.

The home page of xscreensaver can be viewed here ( [https://www.jwz.org/xscreensaver/](https://www.jwz.org/xscreensaver/) ) where you'll see the 'fiery' logo of the project.

Xscreensaver provides both **screensaver** & **lock** capabilities. KDE Plasma & Xfce have had their own screen lock functions, and with screensavers *out of vogue* neither Kubuntu or Xubuntu have used xscreensaver for some time. Lubuntu still uses it (*the LXQt desktop used by Lubuntu doesn't have screenlock capabilities** & thus Lubuntu uses xscreensaver to provide that*)

---

