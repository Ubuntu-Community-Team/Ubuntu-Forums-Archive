---
title: "terminal chat window"
date: 2012-09-05
forum: Programming Talk
---

### Post by manascool on 2012-09-05
I want to make a simple terminal chat application having separate field for input and output.I have no idea about terminal application interface program in c.Please give me some example and useful links.Thanks in advance.

---

### Post by Lux Perpetua on 2012-09-05
The standard way to draw on a terminal is with the ncurses library. If you've ever used nano, vi, vim, less, or pretty much any other terminal application that does more than read input line by line and write output line by line, those are examples of programs that use ncurses. It isn't the only way, but it's the standard, and it'll save you from having to learn and use terminal escape sequences. The canonical language for ncurses is C, but Python (for example) comes with its own ncurses API (the standard library package "curses"), so you're not stuck with C.

---

### Post by pr0misc on 2012-09-05
you can always script something that parses both the 'finger' and 'write' commands :lolflag:

---

### Post by SlugSlug on 2012-09-05
I used to use ```
wall
```

---

