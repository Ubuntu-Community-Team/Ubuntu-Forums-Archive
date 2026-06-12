---
title: "Python: ligthweight curse alternative for cross-platform?"
date: 2012-12-10
forum: Programming Talk
---

### Post by honeybear on 2012-12-10
Hi,

I would like to create a python program for the console of windows, linux, ... that would use a minimum of dependencies.

Curses would be ideal for that but pdcurses or ncurses are one port that might be more or less similar to curses. With some differences.



Would you know a lightweight alternative that exists, well ported and developed, for Windows and Linux?

Pygames would be an alternative but this is not lightweight at all.

Any inputs are welcome

---

### Post by panza on 2012-12-12
Check out [libtcod]("http://doryen.eptalys.net/libtcod/features/"). I've used it for several programs (not just games).

---

### Post by honeybear on 2012-12-14
> **panza said:**
> Check out [libtcod]("http://doryen.eptalys.net/libtcod/features/"). I've used it for several programs (not just games).

it is amazing. does it really work under the tty console? 
[http://www.youtube.com/watch?v=1FU0NeDFfjU](http://www.youtube.com/watch?v=1FU0NeDFfjU)


visibly he used x11 to play it: [http://www.youtube.com/watch?v=B6yBR4C8YsM](http://www.youtube.com/watch?v=B6yBR4C8YsM)
is there a code for that?

---

### Post by squakie on 2012-12-14
You can also use GTK for the GUI - it's cross platform.  You just need to install the Windows version on the Windows platform.  I'm going to assume you'll be doing the development in Ubuntu - in which case you need to install the GTK dev package as well.

---

### Post by honeybear on 2012-12-14
> **squakie said:**
> You can also use GTK for the GUI - it's cross platform.  You just need to install the Windows version on the Windows platform.  I'm going to assume you'll be doing the development in Ubuntu - in which case you need to install the GTK dev package as well.

Well, I would like to develop under non gtk, simply curses like

for the linux console

---

### Post by jpeddicord on 2012-12-14
*Thread moved to **Programming Talk**.*

---

