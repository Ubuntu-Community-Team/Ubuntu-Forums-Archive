---
title: "c in ubuntu"
date: 2012-01-14
forum: Programming Talk
---

### Post by chandu suresh on 2012-01-14
when using c language using gcc "conio.h" is not possible then how can i use the 'getch()' .I want to take characters instantly?

---

### Post by howefield on 2012-01-14
Thread moved to "*Programming Talk*" forum.

---

### Post by trent.josephsen on 2012-01-14
Look into the ncurses library.  man ncurses or Google for some examples.

---

### Post by MadCow108 on 2012-01-14
use the standard C function getc (or getchar)

---

### Post by SGFzc2U= on 2012-01-14
[http://www.etsimo.uniovi.es/cscene/topics/unix/nossenus-termios.xml.html](http://www.etsimo.uniovi.es/cscene/topics/unix/nossenus-termios.xml.html)

I hate it when people say "ncurses".

---

### Post by cgroza on 2012-01-14
conio.h is no longer used and I think it is DOS related.
You need to use stdio.h as a replacement.

---

