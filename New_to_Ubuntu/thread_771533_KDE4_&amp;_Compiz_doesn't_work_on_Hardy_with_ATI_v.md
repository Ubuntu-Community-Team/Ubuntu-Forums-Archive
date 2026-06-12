---
title: "KDE4 &amp; Compiz doesn't work on Hardy with ATI videocard"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by bodzasfanta on 2008-04-27
So I have installed Hardy Heron with KDE4.

I installed the restricted video driver (fglrx) and
enabled the desktop effects.
After reboot I can login but I got a black sreen.
I hear the startup music but nothing works.
I can login in failsafe mode.
I tried **dpkg-reconfigure xserver-xorg**, but it doesn't help me. 

Can anyone help me?

---

### Post by NightwishFan on 2008-04-27
You mean the kwin effects? I had this problem once luckily I enabled expo which is ctrl+f8, and that brings my screen back. I will search for another thread for a better answer.

try this:
press ctrl alt f1 to get to a terminal, log in and run this command:
```
mv ~/.kde4 ~/.kde4.BAK
```
Then restart and try to log in again.

---

### Post by bodzasfanta on 2008-04-27
Yes, I mean kwin effects. Someone told me to try **kwin --replace** but nothing happens...

---

### Post by Paqmann on 2008-05-01
I'm running Gnome, not KDE, but I had all kinds of issues with my ATI card and Compiz when I upgraded to Hardy. It turns out that the fix was really, really simple--I just had to install the package ubuntu-restricted-extras and everything worked fine. Hope this helps.

---

