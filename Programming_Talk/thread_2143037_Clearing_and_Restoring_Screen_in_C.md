---
title: "Clearing and Restoring Screen in C"
date: 2013-05-07
forum: Programming Talk
---

### Post by red willow on 2013-05-07
How do Linux apps like Vi, Less, Lynx, etc, clear the terminal screen before starting, and then restore it after closing? Ie what command(s) would they use?

Thanks!

---

### Post by Tony Flury on 2013-05-08
I would imagine that all of these applications use the ncurses library

[http://invisible-island.net/ncurses/ncurses-intro.html](http://invisible-island.net/ncurses/ncurses-intro.html) seesm to be a good tutorial.

Essentially you start a new "screen" using the ncurses library - and on exit you close the screen using ncurses.

It can be tricky for a beginner, since if your program crashes and you don't exit properly you might get your prompt and your cursor back - but various things like your keyboard echo might be disabled - meaning you wont be able to see what you are typing - typically ncurses programs disable key echo by default, and the application has to manage echo's itself when required.

---

### Post by red willow on 2013-05-08
Thanks! That seems to be what I was looking for. I'll have to explore it further before marking the thread as solved, though.

Edit: Solved!

---

### Post by nvteighen on 2013-05-09
> **Tony Flury said:**
> 
It can be tricky for a beginner, since if your program crashes and you don't exit properly you might get your prompt and your cursor back - but various things like your keyboard echo might be disabled - meaning you wont be able to see what you are typing - typically ncurses programs disable key echo by default, and the application has to manage echo's itself when required.

Just for the record: when something like that happens, using the "reset" command restores your terminal back to normal.

---

