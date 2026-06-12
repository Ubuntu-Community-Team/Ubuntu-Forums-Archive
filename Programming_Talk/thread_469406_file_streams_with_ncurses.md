---
title: "file streams with ncurses"
date: 2007-06-09
forum: Programming Talk
---

### Post by yurimxpxman on 2007-06-09
I wrote some core functions to my text editor with stdio.h, and now that I'm ready to make the interface, I'm trying to switch all the functions to use ncurses. So now I'm using all ncurses functions for printing the text; however, when I try to use stdio's fopen(), etc., functions, I get this run-time error:

```
yurimxpxman@yurimxpxman-laptop:~/Desktop/karlie$ ./karlie src/karlie.c
Error opening terminal: xterm.
yurimxpxman@yurimxpxman-laptop:~/Desktop/karlie$
```

Any ideas? Is there a different approach for handling files with ncurses?

Thanks,

Josh

---

### Post by bboozzoo on 2007-06-10
seems like bad termcap/terminfo for xterm, try setting TERM to linux
```

TERM=linux ./karlie src/karlie.c

```

---

### Post by yurimxpxman on 2007-06-10
> **bboozzoo said:**
> seems like bad termcap/terminfo for xterm, try setting TERM to linux

With a little (okay, so a LOT) of help from the guys in ##c and #ncurses, I got it working. It turns out that a function I made, called read(), was in conflict with one of the header files.

---

