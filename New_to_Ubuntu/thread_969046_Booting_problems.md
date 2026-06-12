---
title: "Booting problems"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by africanpenguin810 on 2008-11-03
Whenever I boot Xubuntu in my computer, I always get the BusyBox command line, not the login window. What should I do?

---

### Post by cool_penguin on 2008-11-03
Try to re-burn your CD at a slower speed and try again if this is a problem you are facing with the Xubuntu live CD. 

Good Luck.

---

### Post by bennachie on 2008-11-03
There has been a lengthy correspondence on this issue. Few people seem to have found that re-burning the CD made any difference. The solution that worked for many, including me, was to hit F6 during the initial pre-booting dialog, then add the following commands after the list of standard boot parameters that appears as a result:

all_generic_ide floppy=off irqpoll

This appears to work around a bug that prevents the installer from navigating the chain of possible boot devices presented to it by some computer systems(I'm sure you'll find a more accurate description of the problem elsewhere in the forum).

Incidentally, I would like to extend my personal thanks are due to the contributor who first worked out this distinctly non-obvious, but quite simple, solution to a frustrating problem!

---

