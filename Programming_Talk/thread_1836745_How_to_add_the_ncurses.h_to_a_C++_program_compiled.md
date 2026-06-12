---
title: "How to add the ncurses.h to a C++ program compiled on gcc"
date: 2011-08-31
forum: Programming Talk
---

### Post by padfootpak on 2011-08-31
[SIZE=2]I am totally new to C++ programming on gcc. I wanted to add color to my text on the output to the console. Since there is no conio.h on linux, I researched and found that ncurses.h could do the trick[/SIZE]. N[SIZE=2]ow the only problem is that I do not know how to download it and then add the library. Can someone please describe the method?

Also, if anybody can describe whether ncurses.h is a better option than curses.h or if I am completely wrong in using curses.h?
[/SIZE]

---

### Post by Bachstelze on 2011-08-31
If all you want is colored output, you don't need curses, just use the ANSI color codes.

[http://en.wikipedia.org/wiki/ANSI_escape_code#Colors](http://en.wikipedia.org/wiki/ANSI_escape_code#Colors)

---

### Post by Smart Viking on 2011-08-31
> **padfootpak said:**
> [SIZE=2]
Also, if anybody can describe whether ncurses.h is a better option than curses.h or if I am completely wrong in using curses.h?
[/SIZE]
I am of the understanding that curses.h and ncurses.h on most GNU/Linuxt systems are the same files, curses.h added for compability with older programs:
```
$ diff /usr/include/ncurses.h /usr/include/curses.h 
$
```Correct me if I'm wrong.

---

