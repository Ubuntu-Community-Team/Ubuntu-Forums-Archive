---
title: "why ubuntu doesnt have ncurses.h header???"
date: 2011-11-19
forum: Programming Talk
---

### Post by shevin on 2011-11-19
I am trying to compile a program , it doesnt give me header error in redhat [gives me some other error] but in ubuntu it says it doesnt have ncurses.h

> ~/Desktop/temp$ gcc bouncer.c -o bouncer -lncurses
bouncer.c:3:22: fatal error: ncurses.h: No such file or directory
compilation terminated.

and it deosnt exist when I search for it

> ~/Desktop/temp$ locate ncurses.h
~/Desktop/temp$ 



but in redhat it compiles fine , and it does have ncurses.h on (redhat machine)
>  $ locate ncurses.h
/usr/include/ncurses.h
/usr/include/ncurses/ncurses.h
/usr/include/ncursesw/ncurses.h


---

### Post by Bachstelze on 2011-11-19
Install [font=monospace]libncurses5-dev[/font].

---

### Post by shevin on 2011-11-19
thanks works now

---

