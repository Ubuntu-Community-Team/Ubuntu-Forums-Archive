---
title: "strange titlebar behaviour"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by vikramaditya on 2008-09-09
Often, the titlebar of an app partially disappears when I mouse over it.  I've determined that this only occurs in a _maximised_ window while _compiz is enabled_.  When the window is unmaximised, or compiz is turned off, titlebars remain stable. System specs:

Intel D845EBG2L
Intel P4 2.4g CPU
2 gigs RAM
GeForce FX 5600 AGP 4x
Corsair 450w PSU

---

### Post by graben3 on 2008-09-09
I had the same problem and played with compiz settings and that did it.

First, check if you have the compiz settings package installed :

In a terminal :

sudo apt-get install compizconfig-settings-manager

Then, go into System -> Preferences -> Advanced Desktop Effects Settings

Now, this is where I dont remember what option in compiz from the 10000 available does that...

Try de-activating each plugins one by one to test if it still do it, youll be able to narrow down the problem to 1 compiz plugin and then try to play with its options to set it right !

Hope it helps !

---

### Post by vikramaditya on 2008-09-09
> **graben3 said:**
> I had the same problem and played with compiz settings and that did it.
Thanks for the help! :) I _do_ have settings manager installed, but the prospect of sorting thru all those plugins is indeed depressing.

---

