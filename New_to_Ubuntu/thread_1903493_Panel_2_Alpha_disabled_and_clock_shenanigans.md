---
title: "Panel 2 Alpha disabled and clock shenanigans"
date: 2012-01-02
forum: New to Ubuntu
---

### Post by Crisopa on 2012-01-02
Hi, i've recently installed Xubuntu in an old laptop to revive it (one of those faulty Presario F700 with the rubbish Nvidia chip), and it's doing fine... So what's the problem? Well, i logged out and then back in, but i felt curious and selected "Xfce" instead of "Xubuntu" in the list below; no problem, i just logged out again. However, next time i logged into Xubuntu, my Panel 2 was solid black instead of translucent. When i go to Panel/Preferences/Appearance, Alpha is "disabled" (it won't show no matter what i do). This happened also in a virtual machine in my desktop, but all i did then was to load a snapshot.

Another problem i have is the clock... After i installed Xubuntu, the time was set to Jan 1 2011 00:00 and can't seem to change/update it.

Please, if someone could help me with these, that'd be nice.

---

### Post by irkan on 2012-10-21
i noticed this bug too, this bug present in xubuntu 12.10 also

if you logged in Xubuntu session, then logged out and in XFCE session and then back to Xubuntu, the transparency is gone

you can re-enable the transparency in  xubuntu session 

go to settings > Window Manager Tweaks > Compositor then tick "Enable display compositing" after that the alpha option will be selectable.

---

### Post by black veils on 2012-10-22
open the **terminal**, copy-paste this
```
dpkg-reconfigure tzdata
```

press Enter, and follow the instructions. login again (or reboot) and see..

---

### Post by r_avital on 2013-07-04
Thank you, irkan, for the quick solution.  Just to be accurate, in case another poor soul wastes too much time on this, it's actually:
Settings->**Settings Manager**>Window Manager Tweaks etc.

Just installed xubuntu from a thumb-drive, tested it, love it, might just abandon gnome (for all my machines except those running Lucid).

I found out (to my delight) that not only could I set the panel to transparent, but that the indicator applet would respect that transparency (whereas on gnome-any kind of session that has panels it stays opaque no matter what, a known bug.

Thanks again, Happy Fourth!

Cheers

---

