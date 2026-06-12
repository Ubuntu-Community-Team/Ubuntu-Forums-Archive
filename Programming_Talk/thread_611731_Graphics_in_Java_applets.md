---
title: "Graphics in Java applets"
date: 2007-11-13
forum: Programming Talk
---

### Post by WebDrake on 2007-11-13
Hello all,

I'm busy working on a Java applet that will allow the user to play a simple game online.  It's a demonstration of some of the topics of my university research group: some time ago we implemented it in Flash but the data got lost (what comes of having one person doing the implementation and a voracious IT administration enthusiastic for the deletion of the accounts of ex-students....) and in any case Java seems like a more attractive platform now as it becomes ever freer.

One of the frustrations, though, is that the basic Java graphical libraries produce very ugly output---a strong contrast to the beautiful vector graphics produced by the Flash interface (an image from which I still have hanging by my desk to torment me).  Are there any alternative Java graphical libraries out there that can produce more attractive output?  Or, if it's simply a case of using the existing libraries correctly, could someone point to some good tutorials?

(If anyone's wondering what I mean by "ugly", consider the case of a diagonal straight line.  In Flash it looked just like that.  With Java, it appears as a combination of vertical straight lines.  YUCK.)

Thanks in advance for any advice,

     -- Joe

---

### Post by novice_forever on 2007-11-13
Hi,

check this out: [http://java.sun.com/docs/books/tutorial/2d/index.html](http://java.sun.com/docs/books/tutorial/2d/index.html)

---

### Post by stroyan on 2007-11-13
In particular look at the effect of VALUE_ANTIALIAS_ON from [http://java.sun.com/docs/books/tutorial/2d/advanced/quality.html](http://java.sun.com/docs/books/tutorial/2d/advanced/quality.html) .
That should make your diagonal line look much better.

---

