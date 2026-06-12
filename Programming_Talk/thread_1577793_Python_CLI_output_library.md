---
title: "Python CLI output library"
date: 2010-09-19
forum: Programming Talk
---

### Post by Dooley on 2010-09-19
Hey there,

I'm writing a python program that I wish to interact with the cli. I need to execute a number of subprocesses, collect and parse the output from these process then display them reasonably well via cli output. I'll need to be able to display a variable number of rows and columns and keep it all within the the current view of the terminal. I'm just wondering if there's a decent wrapper that can help me with this, I'm completely new to this.

Thanks,
Dooley

---

### Post by schauerlich on 2010-09-19
[curses](http://docs.python.org/library/curses.html). ([wikipedia](http://en.wikipedia.org/wiki/Ncurses))

---

### Post by Dooley on 2010-09-19
Perfect, exactly what I was looking for!

---

### Post by nvteighen on 2010-09-19
Python curses is even better than the original C ncurses... It's a bit saner... Enjoy!

---

### Post by juancarlospaco on 2010-09-19
also check python-dialog

---

