---
title: "Problems with the ncurse library"
date: 2009-08-01
forum: Programming Talk
---

### Post by DiegoTc on 2009-08-01
Well I download the nucurse library with this command
> apt-get install ncurses*

And this is the code I want to run

> 
#include <ncurses.h>

int main() {
    char nombre[100];
   //erase();
   printw( "Ejemplo de \"getch\"\r\n\r\n" );
   printw( "Pulsa una tecla: " );
   printw( "\'%c\'\r\n", getch() );
   printw( "Pulsa una tecla para continuar..." );
   getch();

   return 0;
}


And this error appers:

> 
/tmp/ccnxdqNS.o: In function `main':
xd.cpp:(.text+0x27): undefined reference to `printw'
xd.cpp:(.text+0x33): undefined reference to `printw'
xd.cpp:(.text+0x38): undefined reference to `stdscr'
xd.cpp:(.text+0x40): undefined reference to `wgetch'
xd.cpp:(.text+0x50): undefined reference to `printw'
xd.cpp:(.text+0x5c): undefined reference to `printw'
xd.cpp:(.text+0x61): undefined reference to `stdscr'
xd.cpp:(.text+0x69): undefined reference to `wgetch'
collect2: ld devolvió el estado de salida 1



Thanks

---

### Post by dwhitney67 on 2009-08-01
When you link your object file(s), you need to specify the ncurses library.  Something like (algo como):
```

gcc MySource.c -lncurses

```

---

