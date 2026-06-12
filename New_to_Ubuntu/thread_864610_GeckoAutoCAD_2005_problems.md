---
title: "Gecko/AutoCAD 2005 problems"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by SARMedic on 2008-07-19
Hi all,
I just installed Ubuntu 8.04 as a second OS (vista sucks), with Wine 1.0.


 I installed AutoCAD, and it comes up as a trial version (click here to activate kinda deal). When I clicked "Next" to enter my serial number, an "error" came up and said to download Gecko something-or-other, so I did that. Now, when I click next, an HTML-looking (fixed-width) window pops up with just two <HR>'s (the lines), and two radio buttons - but no text. Right click -> View Source doesn't work.

I've tried re-installing gecko with [FONT="Courier New"]**sudo aptitude install wine gecko**[/FONT] without success. Any ideas?

---

### Post by spiderbatdad on 2008-07-19
[http://www.youtube.com/watch?v=b9xcoKXs7rM](http://www.youtube.com/watch?v=b9xcoKXs7rM)
It can be done.
Have you installed R14? How about the .wine directory...is it in your home folder? If not you may need to copy it there.

---

### Post by toasterboy1 on 2008-12-08
Having the same issue followed the tutorial in the wine apps db. No luck with the registering.

---

### Post by toasterboy1 on 2009-04-20
New instructions posted on WineHQ for install. Seems like wine 1.1.5 has to be used to register. Finally got mine working. Had to install riched30 also to get multiple line text to work.

---

