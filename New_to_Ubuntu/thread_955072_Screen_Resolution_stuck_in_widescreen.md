---
title: "Screen Resolution stuck in widescreen"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by bonini on 2008-10-21
I'm on an old inspiron 1000 laptop and I recently connected it to a new plasma TV through VGA.  when it connected it first didn't show up on the tv, but on the laptop all the words on the screen were unreadable.  To restart x hoping it would fix the problem I pressed ctrl-alt-backspace which did make text visible, and after messing with the resolution a bit more I found some that were compatible with the tv.  But now the only resolutions available when I go to "Display" in the settings manager are wide screen, so the top and bottom of the laptop screen are cut off.  The highest of which is 1024 x 576 which is pretty hard to use.  Hopefully someone can help, thanks in advance.

---

### Post by roger_1960 on 2008-10-22
Hi

Open a terminal 'applications-accesories-terminal'(thats the ubuntu sequence, sorry!) and type

sudo displayconfig-gtk

Enter your password and then try using the GUI which appears.  Try changing the model and display resolutions to suit your kit. You can set screens 1 and 2 separately and test before accepting.  Its fairly self explanatory.

Good luck!

---

### Post by kansasnoob on 2008-10-22
This always gets me through my screen resolution problems:

[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

