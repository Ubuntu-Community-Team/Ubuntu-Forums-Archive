---
title: "HOWTO: 2D Collision Detection"
date: 2006-12-27
forum: Programming Talk
---

### Post by Mickeysofine1972 on 2006-12-27
Hi

Theres a new HOWTO on The Ubuntu Games Developer Resource Wiki

Heres the link:
[http://ubuntu-gamedev.wikispaces.com/](http://ubuntu-gamedev.wikispaces.com/)

Credit goes again to CurvedInfinity, Excellent work man!

Mike

---

### Post by Wybiral on 2006-12-27
Btw, a lot of 3d collision detection is similar to the ones in that article, for instance 3d sphere-to-sphere collision is exactly the same as the 2d circle collision, just include the Z component in the length function. Some of the algorithms could be optimized some, but for the sake of an intro tutorial, that was pretty good. The gamedev wiki is starting to accumulate!

---

### Post by slavik on 2006-12-27
spheres/circles are easy ... try adding simple rotate boxes (there is a way to do it, too, if you use OpenGL). But once you start doing 'polygon soups' ... things get complicated.

---

### Post by Mickeysofine1972 on 2006-12-27
I've also heard that theres away to perform collision detection using OpenGL and you video cards fuctions!

Your right Wybiral, it's certainly building up! and in the new year theres more coming!

Mike

---

### Post by Wybiral on 2006-12-27
I've never used OpenGL's collision (I knew it had picking, but I've never heard of it handling collision) but simple triangle intersection collision isn't too hard. Often for most video games, you will need an ellipsoid-to-triangle collision routine (characters are ellipsoids) and triangle-to-triangle collision. It also depends how much collision you need and how precise, sometimes just cylinder-to-cylinder collision will do (which is similar to circle-to-circle).

I might write up a small tutorial on simple 3d collision with primitives when I get some more free time, no guarantee, I'll try.

---

### Post by slavik on 2006-12-27
> **Mickeysofine1972 said:**
> I've also heard that theres away to perform collision detection using OpenGL and you video cards fuctions!

Your right Wybiral, it's certainly building up! and in the new year theres more coming!

Mike
the way you do it, is you render one object and then you render the other object. but the trick is in taking the logical AND of both renders, this is basically overlapping pictures where you draw the parts of both pictures that overlap ... I don't think this is doable in 3D as you are using volumes rather than simple planes.

this is awesome and has small flash demos: [http://www.harveycartel.org/metanet/tutorials/tutorialA.html](http://www.harveycartel.org/metanet/tutorials/tutorialA.html)

the group (metanet) created a really awesome platformer called n-game, available at the same site. I recommend getting the windows version and running it under wine as you get better performance. :)

---

### Post by Mickeysofine1972 on 2006-12-28
WOW that is a really cool game!

and an excellent article too!

Mike

EDIT: I'm so impressed with that article I'm adding it to the wiki under the Links section!

---

### Post by hod139 on 2006-12-28
A discussion on broad phase versus narrow phase collision detection would be good too.  This article covers the narrow phase well, but also important is the broad phase.  For example, an oct-tree (quad-tree for 2D) is commonly used but there are other spacial decomposition methods available.

**Edit:** I just read the article more carefully and noticed that this was hinted at at the end of the article.

---

