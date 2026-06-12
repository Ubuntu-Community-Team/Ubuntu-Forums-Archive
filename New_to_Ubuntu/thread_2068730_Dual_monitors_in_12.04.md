---
title: "Dual monitors in 12.04"
date: 2012-10-09
forum: New to Ubuntu
---

### Post by Tobey666 on 2012-10-09
Hey all,

I just installed Kubuntu 12.04 on my desktop computer and have been having some trouble setting up dual monitors.

The good news is I've managed to get them working, more or less. However, every time I boot up the computer, the main screen (X or whatever it is in kubuntu) is on the monitor on my left instead of the one on my right. I would like to switch them around but I can't find any obvious way to do so. When I open NVIDIA X Server Settings, I see both monitors activated with the one on the right marked as my primary display for the X screen, and yet the primary screen is always on the left.

Admittedly, this is more an aesthetic problem than anything else, but it's really starting to bug me. I can move all my widgets, even the taskbar over to the right-hand screen, but it resets every time. 

Any help you could offer would be much appreciated.
Thanks

Additional info (if it helps):
-My video card is a NVIDIA GTX 550ti (the right hand screen connected via DVI and the left one via VGA.
-I am currently using the proprietary drivers for nvidia cards ("version current" not "post-release updates")

---

### Post by Tobey666 on 2012-10-11
bump

---

### Post by DuckHook on 2012-10-11
If they are the same make and model, the easiest solution is just to physically switch the cords (after powering everything off). If they are different make and model, DO NOT switch cords. Open nvidia control panel and drag primary monitor to other side.

---

### Post by Tobey666 on 2012-10-12
Unfortunately, part of the problem was that changing settings in the nvidia control panel had no effect (I should have mentioned).

Anyway, I managed to fix it. The issue was that my desktop widgets, including the panel (which I never would have guessed is a widget, but whatever) were not locked. So I fixed the problem by moving the panel and the desktop-widgets over to the left screen, right clicking on the desktop and selecting "lock widgets".

---

