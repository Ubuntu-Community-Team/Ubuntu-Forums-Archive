---
title: "function to clear the screen in C language"
date: 2010-04-28
forum: Programming Talk
---

### Post by princeofindia on 2010-04-28
This thread is for the one who knows C Programming under windows and Linux well.can anyone please tell me the function to clear the console in linux using C language.It is done under windows by using clrscr() by including <conio.h>.Also,please tell me the header file to use and the respective function.

---

### Post by DBQ on 2010-04-28
Assuming you are using linux:

system("clear");

---

### Post by princeofindia on 2010-04-28
But which header file to use this function?

---

### Post by DBQ on 2010-04-28
#include <stdio.h>
#include <stdlib.h>

---

### Post by StephenF on 2010-04-29
When it comes to taking complete control of the console you'll want to use the ncurses library. 

Keeping things simple:
[http://ascii-table.com/ansi-escape-sequences.php](http://ascii-table.com/ansi-escape-sequences.php)

Escape sequence example:
```

printf("\x1b[s\x1b[2J\x1b[10;25HTaking control of your console.\x1b[u");

```

---

### Post by slavik on 2010-04-29
1. use ncurses
2. escape chars are evil
3. system() is evil

---

### Post by nvteighen on 2010-04-29
> **slavik said:**
> 1. use ncurses
2. escape chars are evil
3. system() is evil

+1

ncurses is the standard way to go not only on GNU/Linux but also in all the rest of UNIX and Unix-like OSs. It's a weird library in some extents, but is much nicer than all other solutions.

Also, system("clear") won't work very well when running under a virtual terminal (xterm, gnome-terminal, etc.) because scrolling the text up will still show the previous contents because "clear" actually just inserts as much whitespace necessary to place the prompt back again to the first line... at console, using Shift+PgUp will also have the same effect.

---

