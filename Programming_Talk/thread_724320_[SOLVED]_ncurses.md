---
title: "[SOLVED] ncurses"
date: 2008-03-14
forum: Programming Talk
---

### Post by vikasmk on 2008-03-14
```
#include<stdlib.h>
#include<ncursesw/ncurses.h>
int main()
 { initscr();
   printw("hello world");
 refresh();
 getch();
 endwin();
 return(0);
  }
```
  
 here is what i get after complation
 ```
vikasmk@vikasmk:~/cprograms/ncur$ gcc hello.c
/tmp/cceDQDjR.o: In function `main':
hello.c:(.text+0x12): undefined reference to `intitscr'
hello.c:(.text+0x1e): undefined reference to `printw'
hello.c:(.text+0x23): undefined reference to `stdscr'
hello.c:(.text+0x2b): undefined reference to `wrefresh'
hello.c:(.text+0x30): undefined reference to `stdscr'
hello.c:(.text+0x38): undefined reference to `wgetch'
hello.c:(.text+0x3d): undefined reference to `endwin'
collect2: ld returned 1 exit status

```
 
 What is the problem??
Do i have to configure ncurses or something??

---

### Post by LaRoza on 2008-03-14
You have to link to the ncurses library.

```

gcc <filename> -lncurses

```

On my setup, I need to include <ncurses.h>, but you would get another error if your #include were wrong.

---

