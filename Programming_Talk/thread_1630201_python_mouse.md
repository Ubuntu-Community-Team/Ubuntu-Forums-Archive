---
title: "python mouse"
date: 2010-11-24
forum: Programming Talk
---

### Post by flyingsliverfin on 2010-11-24
is there a way to use python to simulate mouse clicks? I don't know how it works within the computer, but alternately could i feed numbers into the program that "gets" the clicks?
Im planning on starting on C sometime within the next one or two months, so if theres an easy way to do it in C that would also be possible

thanks

---

### Post by ziekfiguur on 2010-11-25
> **flyingsliverfin said:**
> is there a way to use python to simulate mouse clicks? I don't know how it works within the computer, but alternately could i feed numbers into the program that "gets" the clicks?
Im planning on starting on C sometime within the next one or two months, so if theres an easy way to do it in C that would also be possible

thanks

I think it's possible, though I'm not exactly sure how. My guess is that you should use the PyGTK library. 
I know it is possible for the keyboard, as onboard is written in python. Maybe you can find some pointers in /usr/bin/onboard

Good Luck.

---

### Post by Tony Flury on 2010-11-25
If you have a program which is using a GUI, and you want to emulate clicking on a given button (and not a specific pixel) then you will probably find that which ever GUI toolkit you use has the capability to programatically "click" a GUI element (a button, a menu etc) - I know GTK does, but that does rely on you being able to get to the GUI elements from your program - which might not be easy if you did not write the orginal GUI.

If you really want to programmatically emulate a mouse click anywhere on the screen, no matter what program is to be clicked -then you might have to delve into the X windows library.

---

### Post by nvteighen on 2010-11-25
IIRC, the way to do this in GTK+ is by forcing the "clicked" signal for a desired widget via g_signal_emit()... which btw has a very weird interface... :P

---

