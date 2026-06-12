---
title: "an error with curses.h library in gcc"
date: 2011-01-17
forum: Packaging and Compiling Programs
---

### Post by asixbabak on 2011-01-17
hi there

i am new to this forum

i am working on a course project,it is simplified Pacman .

i used to get "char"s from input w/o pushing enter button  , in windows compilers there is a library named conio.h but it is not standard
so i installed a similar(maybe!) library curses.h
using this command:

```
sudo apt-get install libncurses5
```and i included to my c++ code:

```
...
#include<curses.h>

...

int loop()
{
char a;
a=getch();
cout<<a<<endl;
...


```and I get two errors:
[COLOR=Red]undefined reference to 'stdscr'
undefined reference to 'stdscrwgetch'[/COLOR]

what should I do?

---

### Post by MadCow108 on 2011-01-18
have you linked with libcurses?

g++ -lcurses
or -lncurses if you use ncurses instead of curses

---

### Post by mchecca on 2011-01-21
Do you have the development package installed?

sudo apt-get install libncurses5-dev

"This package contains the header files, static libraries
 and symbolic links that developers using ncurses will need."

---

### Post by asixbabak on 2011-01-24
yes
i have installed curses precisely
but still got the problem

---

### Post by MadCow108 on 2011-01-25
are you sure you need stdscrwgetch?
as far as I can tell this function does not exist with this name in curses.

getch gets translated to: wgetch(stdscr) on my system
both these symbols exist in libcurses.
```

nm --dynamic /usr/lib/libncurses.so  | grep -E "wgetch|stdscr"
0000000000243db0 B stdscr
0000000000016d40 T wgetch

```

maybe a typo?

---

