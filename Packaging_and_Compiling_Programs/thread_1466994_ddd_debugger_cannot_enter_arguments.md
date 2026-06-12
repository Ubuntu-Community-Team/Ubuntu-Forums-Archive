---
title: "ddd debugger: cannot enter arguments"
date: 2010-04-30
forum: Packaging and Compiling Programs
---

### Post by clubsoda on 2010-04-30
In ddd, pressing F2 or selecting Program->Run from the menu, the "Run Program" box comes up but no arguments can be added. This appears to affect XFCE, KDE and Gnome.
Anyone out there using ddd?

---

### Post by MadCow108 on 2010-04-30
works for me.
you have to hover the mouse on top of the lower input box for it to work.

---

### Post by jtniehof on 2010-04-30
I use ddd and am able to enter arguments. There are two oddities about it: first, the I cursor for the arguments box is always greyed-out, as if it's inactive. The other is that the mouse cursor has to actually be in the arguments box (i.e. over where you're typing) for it to work.

Hope that helps.

---

### Post by clubsoda on 2010-05-01
Thanks for your helpful replies, but still no luck here. In the "Run with Arguments" input box I am seeing the ghost of a cursor as described by jtniehof, however I cannot type in there even with a mouse-over.

However, I've just found that I can paste text into that box using the middle mouse button, so it seems to be the keyboard which is disconnected from this pop-up window. This may relate somehow to [focus stealing issues](http://ubuntuforums.org/showthread.php?t=1467076) I'm getting in Xubuntu. I'll check if the suggested fix works for me in Gnome or KDE.

Cheers.

---

### Post by MadCow108 on 2010-05-01
you can always fall back to the gdb shell if nothing works.
run programs with arguments with the run command:
>run argument1 argument2 ...

---

### Post by clubsoda on 2010-05-08
Thanks for the suggestions - fully working now.
As far as Gnome/KDE it was probably just the trick of having to mouse-over the input box while typing.
In Xubuntu it was most likely due to incomplete installation of languages and/or ongoing use of scim instead of ibus/anthy. This happened because the system was upgraded, not freshly installed.
Marking as solved.
Cheers.

---

