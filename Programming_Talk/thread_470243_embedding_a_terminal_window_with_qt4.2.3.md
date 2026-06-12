---
title: "embedding a terminal window with qt4.2.3"
date: 2007-06-10
forum: Programming Talk
---

### Post by rbprogrammer on 2007-06-10
does any one know how to embed a terminal window within a qt4 application? i tried looking through [http://doc.trolltech.com/4.2/index.html](http://doc.trolltech.com/4.2/index.html) and [http://doc.trolltech.com/4.2/classes.html](http://doc.trolltech.com/4.2/classes.html) but i could not find anything that could help me.  and google just could not handle my question this time, so that was no help either.

 i dont know what else to post, i think that one question explains exactly what i want to do.

---

### Post by rbprogrammer on 2007-06-13
not sure if it will help, but i'm using KDE..  is there like a KDE library or something that can help?

i would like it to be as portable as possible, but if this one part depends on KDE, its not that big of a deal for me..

---

### Post by HackingYodel on 2007-06-14
> **rbprogrammer said:**
> not sure if it will help, but i'm using KDE..  is there like a KDE library or something that can help?

i would like it to be as portable as possible, but if this one part depends on KDE, its not that big of a deal for me..

I think the KDE element you are looking for is called Kparts, or more specifically the Konsole Kpart.  Please see:  [http://en.wikipedia.org/wiki/KPart](http://en.wikipedia.org/wiki/KPart)

I also found additional information at [http://phil.freehackers.org/kde/kpart-techno/kpart-techno.html](http://phil.freehackers.org/kde/kpart-techno/kpart-techno.html) Check out the links in its reference section.

I'm sorry I can't help you with actual code or how-to. This, more-or-less, is the limit of my knowledge on the subject.

Hope this helped (some)!

---

