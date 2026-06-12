---
title: "x11 window in kommander"
date: 2008-03-11
forum: Programming Talk
---

### Post by krait on 2008-03-11
ok, i need to embed the x11 window produced by gnuplot into a kommander dialogue. mite anyone of u know how this can be done?

basically i need to come up with a front end with gnuplot outputs embedded in it. if u think theres an easier alternative to kommander, also advice.

thanks in advance. 

cheers

---

### Post by Zugzwang on 2008-03-11
This might be quite tricky if it is solvable without going too much into X's internals at all. It's probably easier to let gnuplot write a .png file of the graph and simply read the generated image. You could also run gnuplot each time your GUI window is resized to get an image of the matching size.

---

### Post by krait on 2008-03-11
hmm, i thought of this. however, i d love to have the mouse zoom features which the x11 output from gnuplot offers, as my xy-space is quite big.

i found a class (link below) fr qt which i think offers what i want. however,im really uncomfortable entering qt, kommander seems much simpler.but since kommander is derived from qt?, i believe somethin similar is possible in kommander as well?

[http://doc.trolltech.com/4.1/qx11embedcontainer.html](http://doc.trolltech.com/4.1/qx11embedcontainer.html)

or alternatively, is there any gnuplot output format that offers zoom which i can embed? a huge png? which i can zoom using some kde pic viewer? 

thanks n cheers

---

### Post by krait on 2008-03-12
anyone????????

---

### Post by Zugzwang on 2008-03-12
I guess most people here didn't ever use kommander (including myself) before, so this forum might be too general to help you.

---

