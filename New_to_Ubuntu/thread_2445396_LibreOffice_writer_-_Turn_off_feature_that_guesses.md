---
title: "LibreOffice writer - Turn off feature that guesses where I want the cursor"
date: 2020-06-13
forum: New to Ubuntu
---

### Post by moonguide on 2020-06-13
Years ago, up arrow meant move the cursor up one line and leave it in the same position on that line as it was on the previous line. Sometime in the last few versions that changed so that Writer thinks I want the cursor to go to some other location on the above line. I know I can stop that if I move the cursor forward or backward before going up, but I often don't remember to do that. Is there a way to turn off the feature that thinks it knows where I want the cursor?

I posted this question on the LibreOffice forum and got this reply:
--------
I cannot reproduce the said behaviour with v.6.4.4.2 on Windows: when I press up or down arrow, the cursor ends up in the ~same horizontal position as it was on previous line. There's no configuration for this behaviour AFAIK. Please mention which LO version you use, and which OS (but in fact, OS should be unrelated).
--------

I replied:

--------
LO version 6.0.7.3 Build ID: 1:6.0.7-0ubuntu0.18.04.10 OS: Xubuntu 18.04

For those not familiar with it, Xubuntu is one of the versions of Ubuntu, which is one desendents Debian, which is of the distributions of Linux.

Since the problem doesn't show up in the Windows version of LO I'll bring it up with the Ubuntu folk and see if anyone there sees the problem.
--------

Does anyone know why arrow up responds this way for me?

Thanks.

---

### Post by zeekstern on 2020-06-13
You can change the keyboard mappings in Libre Writer by going to Tools->Cusomize->Keyboard.
By the way, my up arrow moves the cursor up one line in the same position without having to move it left or right.

---

### Post by Holger_Gehrke on 2020-06-13
Using the exact same OS and version of LO. When I move vertically using the cursor keys, LO does a good job at staying close to the horizontal position the cursor had when I started moving. Of course it can't keep the horizontal position when I move into a short or empty paragraph or a paragraph with an indentation that overlaps the desired cursor position, but it remembers where the cursor should be and as soon as I move into a paragraph where it's possible to put the cursor where it should be LO will do so.

Holger

---

### Post by moonguide on 2020-06-13
I'm not sure what advantage there would be to changing the mapping. I still expect to use the up arrow key for arrow up.

---

### Post by moonguide on 2020-06-13
I neglected to mention that I can avoid the problem by moving the cursor left or right before moving up. But that's an extra keystroke I'd like to avoid.

Thanks.

---

### Post by zeekstern on 2020-06-13
I was thinking that maybe set the up arrow to something else and see if that work. Then go back in and change it back to see if that made any difference. Never can tell:))
Good luck..

---

