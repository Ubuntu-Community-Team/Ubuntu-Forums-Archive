---
title: "use glutInitDisplay() w/ SDL?"
date: 2009-07-14
forum: Programming Talk
---

### Post by Quarg on 2009-07-14
Hello all, 

     Should I use the glutInitdDisplay() when developing with SDL? Or  do I need it? I used a program without it easily, and added the function at the beginning of a function, and it worked just the same. Is it necessary?

---

### Post by slavik on 2009-07-15
SDL does the init, glut doesn't in this case ... avoid glut when using SDL.

---

### Post by Quarg on 2009-07-19
O.K. Thanks! I have found the boundaries between the two confusing at times. that helps.

---

