---
title: "Need help making this program run easier with hotkeys"
date: 2009-01-14
forum: Programming Talk
---

### Post by perillux on 2009-01-14
There is no normal way for me to turn this laptop screen off, the best I could do was to set it to "blank screen" when it was idle but the backlight remained on.  Also, when the screen was blanked I could see weird patterns of colors on the screen (through some strange incompatibility, or video card setting... I don't know.) and it would keep doing that until the laptop hibernated.

Anyways, I found a .sh script online that allows me to REALLY turn the screen off, backlight and everything.  The only problem is that I have it in two parts off.sh and on.sh.  It's easy enough to do the off.sh but when I come back I have to type: sudo bin/on.sh then enter my password without being able to see the screen.  Now this really isn't all that difficult but I also have to switch to a virtual terminal at some point with ctrl+alt+F1.
If I don't do this then when I turn the screen back on it is flickering wildly and showing weird colors (all I have to do to fix this then is simply ctrl+alt+F1 then back to ctrl+alt+F7).

This is quite a hassle to do though every time I just want to turn the screen off.  I was wondering 2 things:

1) Is there a way to add code that will make it automatically switch to the terminal as if I had pressed ctrl+alt+F1 and then back to the gnome desktop?

2) How could I bind these two scripts to run when I press a button?  I would prefer it to "toggle", meaning that when I press the button to turn the screen off, I can then press the **same** button to turn it back on.

---

