---
title: "Differences between C/C++ on Linux and C/C++ on Windows/DOS?"
date: 2006-11-07
forum: Programming Talk
---

### Post by Jucato on 2006-11-07
I'm trying to learn (and brush up on some previous knowledge) C/C++ on Linux. I was reviewing this old C book of mine (circa 1994) and tried some of the examples in the book. I quickly ran into a problem with getche(). After a short search in Google, I read that getche(), and perhaps everything in conio.h, doesn't work on Linux.

So what would be a replacement for getche() on Linux? Are there any other differences between C/C++ on Linux and on Windows/DOS that I should be aware of?

Thanks!

---

### Post by ansi on 2006-11-08
> **Jucato said:**
> 
So what would be a replacement for getche() on Linux?

Yes. For example, ncurses library -- port of this library for top platforms, such as, *BSD and Windows is available. More information you cat view here (if you have corresponding installed packages):
```
man ncurses
```
[about Linux getch]("http://www.die.net/doc/linux/man/man3/getch.3.html")

But work with this requires some knowledge and expirience.

> **Jucato said:**
> 
 Are there any other differences between C/C++ on Linux and on Windows/DOS that I should be aware of?

No. C as C++ has international standard, where is defined which functions are portable and hasn't differents between Windows/Linux/etc.

As for exterior libraries -- it depends from fantasy of concrete developers ;).

---

