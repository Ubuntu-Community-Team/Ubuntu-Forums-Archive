---
title: "[SOLVED] Seems like Ubuntu thinks I am still playing a fullscreen game"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by ConMan318 on 2008-08-07
I was setting up Warsow a few minutes ago, and I changed to max refresh rate from 90 to 200 (because that's what Sauerbraten runs at without any effort).  Immediately things got screwed up.  The screen went white, then I could see portions of my desktop, but all my clicks caused in-game noises to happen.  So I Crtl+Alt+Backspaced out of it.  Logged back in (through a login screen with screwed up resolution) and got to a desktop with screwed up resolution: I could only see about a third of my desktop and couldn't see my Apps/Places/System menus.  So I restarted.

Now the screen is at least centered, but resolution looks like 800x600 (on a 22" monitor) and desktop effects are at 'none' and cannot be enabled.  This computer is a new build and more than capable of running compiz with all the settings, and my drivers are all installed, so it's not a hardware thing.



It seems like Ubuntu thinks I am playing a game.  Fullscreen apps will not launch.  Can anyone help me out?

Thanks in advance.

---

### Post by freak42 on 2008-08-07
which refresh rate did you change? 
the one of your monitor? 
usually monitors cannot sustain such high refresh rates.
You might be able to change your settings in xorg.conf:
/etc/X11/xorg.conf

hth

---

### Post by ConMan318 on 2008-08-07
I check out the xorg.conf and it was less than a page; everything was generic.  Fortunately I had changed something unrelated in there earlier and had a backup from a few hours ago.  Thank you, I didn't think it would have screwed up my xorg.conf, I though it was just an in-game cap.

---

### Post by freak42 on 2008-08-07
me neither ;-)

---

