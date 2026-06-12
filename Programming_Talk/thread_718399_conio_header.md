---
title: "conio header"
date: 2008-03-08
forum: Programming Talk
---

### Post by vikasmk on 2008-03-08
well i saw that there isn't a conio.h in Linux , 
 I needed the 'gotoxy()' function really bad, is there any other function similiar to it.

---

### Post by yabbadabbadont on 2008-03-08
conio.h is not part of the C standard, but a DOS/Windows extension to it.  As far as I know, the only way to get the same functionality in Linux, is to use a library such as ncurses.  The wikipedia article has more details, as well as links to some tutorials.

[http://en.wikipedia.org/wiki/Ncurses](http://en.wikipedia.org/wiki/Ncurses)

---

### Post by Zugzwang on 2008-03-08
You could try to use [libconio]("http://sourceforge.net/projects/libconio"), but I'm not sure if that is mature enough.

---

