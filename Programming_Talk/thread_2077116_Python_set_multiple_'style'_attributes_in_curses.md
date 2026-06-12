---
title: "Python: set multiple 'style' attributes in curses"
date: 2012-10-27
forum: Programming Talk
---

### Post by Erik1984 on 2012-10-27
How to apply more than one attribute to a printed string in the python curses library? So for example to apply both a curses.color_pair(n) and curses.A_BOLD or curses.A_REVERSE to a given string.

One attribute can be applied like this example
```

window.addstr(y,x,text,curses.A_REVERSE)

```
to reverse fore and background color.

But it's not clear to me from the documentation docs.python.org/library/curses.html how to combine two or more attributes and apply them to an addstr command. I've tried to just add it as an extra argument but that's not accepted.

---

### Post by Erik1984 on 2012-10-29
*bump*

---

### Post by spjackson on 2012-10-29
I'd expect it to be similar to C where you use bitwise-or on the flags. So:
```

window.addstr(y,x,text,curses.A_REVERSE | curses.A_BOLD)

```
I haven't tried it though.

---

### Post by Erik1984 on 2012-10-29
Wow, that was fast :D And it works, so thanks.

---

