---
title: "help with the curses libary"
date: 2007-12-18
forum: Packaging and Compiling Programs
---

### Post by DFord425 on 2007-12-18
I am trying to compile a C program using the curses library but i get an error saying ```
dford@dford-laptop:~/CS355$ cc snake.c -lcurses -o snake
snake.c:9:20: error: curses.h: No such file or directory
snake.c: In function ‘main’:
snake.c:28: error: ‘LINES’ undeclared (first use in this function)
snake.c:28: error: (Each undeclared identifier is reported only once
snake.c:28: error: for each function it appears in.)
snake.c:22: warning: return type of ‘main’ is not ‘int’

```
Do i need to install it with build essential?  I thought i did that when i installed the other libraries for C.

---

### Post by adityakavoor on 2007-12-18
open synaptic
search ncurses
install libncurses5
libncurses5-dbg
libncurses5-dev

---

### Post by DFord425 on 2007-12-18
i installed libcurses5, but i could not find libcurses5-dbg, and libcurses5-dev

---

### Post by adityakavoor on 2007-12-18
```

sudo apt-get install libncurses5-dev libncurses5-dbg

```

---

### Post by DFord425 on 2007-12-18
I get this[CODE]dford@dford-laptop:~$ sudo apt-get install libncurses5-dev libncurses5-dbg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libncurses5-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libncurses5-dev has no installation candidate
[CODE]

---

### Post by adityakavoor on 2007-12-18
check whether the Universe component is checked in
System > Admin > Software Sources

run ```

sudo apt-get update

```

then try

---

### Post by DFord425 on 2007-12-21
still not working ```
E: Package libncurses5-dev has no installation candidate
```

---

