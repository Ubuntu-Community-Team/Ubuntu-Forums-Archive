---
title: "Black screen after 295.49 driver installation"
date: 2012-05-10
forum: New to Ubuntu
---

### Post by damianmuti on 2012-05-10
First of all, my name is Damián and im from Mar del Plata, Arentina.
This is the first time i install a linux distro on my computer (windows guy), so i dont rly know anything about how u do things.

So heres the situation:

I had 295,40 nvidia drivers installed (GeForce 6200), and i felt unity and the whole system was running slow (athlon xp 64 3000+ oc to 2250, 2gb ddr) although my spects are not that bad for ubuntu 12.04.
I searched on the web that the slow performance was because those 295.40 drivers, so i found a method to update to 295.49 drivers that corrects those problems.

Updated the drivers, rebooted,but now all i get afted grub is a black screen. I can go into terminal mode pressing alt+ctlr+f1, i run:

```
sudo service lightdm start
```

but nothing happens, it goes back to black screen.


I'd love a hand on this since as ive said, i rly dont know how to fix it.

Thanks in advance, and best regards from the "happy city" :)

---

### Post by anewguy on 2012-05-10
I know the first thing I would try:

- press F^ repeatedly as the system is booting to get to the boot menu.  Add nomodeset to the boot line and let it boot.  If that works, we can make it permanent.

Dave ;)

---

### Post by damianmuti on 2012-05-10
> **anewguy said:**
> I know the first thing I would try:

- press F^ repeatedly as the system is booting to get to the boot menu.  Add nomodeset to the boot line and let it boot.  If that works, we can make it permanent.

Dave ;)

Ty for ur answer, Dave :)

Somehow i managed to change "quiet splash" in the boot line for "nomodeset" (pressing "e" in the grub OS selector).

Tried to reboot that way, but now it says:

```
Loading, please wait...
Begin: Loading essential drivers ... done.
```

and a couple more lines, but stops there; nothing else happens.

---

