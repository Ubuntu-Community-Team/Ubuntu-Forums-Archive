---
title: "[SOLVED] GnuStep network and filemanager"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by TNAFan on 2008-11-12
I just got done installing the gnustep desktop that uses WindowMaker.  I have found myself liking it a lot.  Though I just have two questions.  What is everyone's idea of "the best" filemanager to use with WindowMaker?  And what is the easiest way to access the network under WindowMaker?

---

### Post by TNAFan on 2008-11-12
Bump?  Oh, and also, does anyone know where I can find a deb to install a trash applet?

---

### Post by cariboo on 2008-11-12
You're really supposed to wait 24 hours before bumping, but oh well.

When I used Windowmaker I used mc in a terminal. I still use Midnight Commander for a lot of things.

Jim

---

### Post by kerry_s on 2008-11-12
i thought it had a file manager already? fsviewer?
[http://gnustep.org/experience/apps.html](http://gnustep.org/experience/apps.html)

i'm pretty sure you can use what ever file manager you like best, a lot of people like pcmanfm or rox-filer.

---

### Post by TNAFan on 2008-11-13
Just so everyone knows, I have found the answer to the biggest problem I had with Window Manager.  I now use Dolphin with Window Maker!  It accesses the network without taking over the desktop like Nautilus!  I now have found my favorite Desktop Environment!  GnuStep!

---

### Post by kerry_s on 2008-11-13
> **TNAFan said:**
> Just so everyone knows, I have found the answer to the biggest problem I had with Window Manager.  I now use Dolphin with Window Maker!  It accesses the network without taking over the desktop like Nautilus!  I now have found my favorite Desktop Environment!  GnuStep!

nautilus has to be called " nautilus --no-desktop " to run by it self. always take a look at the man pages " man program "
example:
man nautilus
man dolphin
man wmaker
etc...

---

### Post by g0nad on 2009-07-22
I'm using Ubuntu Alternate 9.04 with WindowMaker, I've installed nautilus but when I click on nautilus' network icon I get the message "Nautilus cannot handle "network" locations.".

I believe that I'm probably missing a package but whatever package I'm missing wasn't a dependency of nautilus.

I'm stuck.

If I install KDE's "dolphin", that can browse network shares.  I don't like dolphin, I'd rather have nautilus work as it does in a default Ubuntu install.

---

