---
title: "unable to link ncurses correctly"
date: 2014-05-10
forum: Packaging and Compiling Programs
---

### Post by siddiqui_1985 on 2014-05-10
Assalam-o-Alikum!! and Hi to All

I am new to ncurses and i have a HOWTO ncurses pdf file and i followd the process they give in their book on how to install and link ncurses 

but when i tried to compile. it gives me this error :

```


waqar@waqar-virtual-machine:~/Documents$ gcc -o curses1 -lncurses curses1.c
/tmp/ccBAXETc.o: In function `main':
curses1.c:(.text+0xa): undefined reference to `initscr'
curses1.c:(.text+0x16): undefined reference to `printw'
curses1.c:(.text+0x1b): undefined reference to `stdscr'
curses1.c:(.text+0x23): undefined reference to `wrefresh'
curses1.c:(.text+0x28): undefined reference to `stdscr'
curses1.c:(.text+0x30): undefined reference to `wgetch'
curses1.c:(.text+0x35): undefined reference to `endwin'
collect2: error: ld returned 1 exit status
waqar@waqar-virtual-machine:~/Documents$ 


```

Also here is the sample code which they provide

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

now what i'm doing wrong ?

---

### Post by oldos2er on 2014-05-10
Moved to Packaging & Compiling Programs.

---

### Post by steeldriver on 2014-05-10
The linkage order is important - subordinate libraries need to go later on the command line than the things that reference them

```

gcc -o curses1 **curses1.c -lncurses**

```

---

