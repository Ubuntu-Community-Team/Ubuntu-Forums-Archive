---
title: "proper way to resize an x window?"
date: 2011-01-25
forum: Programming Talk
---

### Post by sigflup on 2011-01-25
Download here: [http://hobones.dogsoft.net/main.c](http://hobones.dogsoft.net/main.c)

compile with

$gcc main.c -lX11

Hey. I'm getting back into xlib. I can't resize my window. It catches resizerequest events but the actual dimensions of the window I can't change. When you resize it bigger then the starting size it doesn't catch events outside it's initial size or draw outside of it. I don't think I'm doing this right, can anyone catch my problem?

.. yes I know about the x double buffer extension but I want to fix this problem first.

thanks yous!!

-sigflup

---

### Post by sigflup on 2011-02-02
Wow!! thank you for the very thoughtful reply. Now I'm using ConfigureNotify and everything works just fine. Ossum!!! Thanks yous!

---

