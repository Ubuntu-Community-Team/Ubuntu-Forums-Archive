---
title: "C and colors in terminal?"
date: 2007-11-12
forum: Programming Talk
---

### Post by Can+~ on 2007-11-12
This must be a very easy question, I want to use colors with C on terminal, and also get some keyboard events.

A certain function, prints a menu list, the user presses up and down to move between the options, but the thing is, that I want to highlight the selection, like this:

> 
0. Add Contact
1. Remove Contact
[COLOR="Red"]2. Do other stuff[/COLOR]


"User presses <Up>"

> 
0. Add Contact
[COLOR="Red"]1. Remove Contact[/COLOR]
2. Do other stuff


How can I highlight with colors? It isn't really important, but it would be nice to know.
How can I get when users presses up or down? conio.h doesn't work in ubuntu =(.

---

### Post by LaRoza on 2007-11-12
Use NCursed, my wiki has it. [http://laroza.pbwiki.com/LinuxSpecific](http://laroza.pbwiki.com/LinuxSpecific)

---

### Post by bunker on 2007-11-12
If you don't want to use ncurses, you could use simple terminal colours as you would with a PS1:

```
printf("\033[01;32mThis will be green!\033[0m\n");
```

and use termios.h to control the output buffer yourself.  I think ncurses would likely be easier though, and you can do a lot more.  For instance aptitude is written using ncurses.

---

