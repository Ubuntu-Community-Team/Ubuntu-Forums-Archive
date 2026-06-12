---
title: "Problem with ncurses library"
date: 2010-08-14
forum: Packaging and Compiling Programs
---

### Post by maedez on 2010-08-14
Hello, I'm new to programming and I'm starting of with C. I want to make a gui using ncurses. I've already installed ncurses-base and libncurses5-dev and I'm using the latest version of Ubuntu. I found a code online ([http://tldp.org/HOWTO/NCURSES-Programming-HOWTO/index.html](http://tldp.org/HOWTO/NCURSES-Programming-HOWTO/index.html)) to try out but when I type in

```
gcc hello_world.c -o hello
```it prints out

```

/tmp/ccjhcHpV.o: In function `main':
hello_world.c:(.text+0x5): undefined reference to `initscr'
hello_world.c:(.text+0x14): undefined reference to `printw'
hello_world.c:(.text+0x1b): undefined reference to `stdscr'
hello_world.c:(.text+0x23): undefined reference to `wrefresh'
hello_world.c:(.text+0x2a): undefined reference to `stdscr'
hello_world.c:(.text+0x32): undefined reference to `wgetch'
hello_world.c:(.text+0x37): undefined reference to `endwin'
collect2: ld returned 1 exit status

```What's wrong?

btw the code for the sample program is:
```
#include <ncurses.h> 
 
int main() 
{     
    initscr();            /* Start curses mode           */ 
    printw("Hello World !!!");    /* Print Hello World          */ 
    refresh();            /* Print it on to the real screen */ 
    getch();            /* Wait for user input */ 
    endwin();            /* End curses mode          */ 
 
    return 0; 
}
```

---

### Post by itcotbtoemik on 2010-08-14
gcc hello_world.c -o hello -lncurses

---

### Post by maedez on 2010-08-14
may I ask why need to add

gcc hello_world.c -o hello **-lncurses  **?

---

### Post by itcotbtoemik on 2010-08-15
man ncurses

       A  program  using  these  routines  must  be  linked with the -lncurses
       option, ...

---

