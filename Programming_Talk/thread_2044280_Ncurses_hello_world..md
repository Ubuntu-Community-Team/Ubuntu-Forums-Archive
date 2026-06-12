---
title: "Ncurses hello world."
date: 2012-08-19
forum: Programming Talk
---

### Post by Ankitshah on 2012-08-19
1 #include<ncurses.h>
  2 
  3 int main(int argc,char *argv[])
  4 {
  5         initscr();
  6         printw("hello, world.");
  7 
  8         getch();
  9         endwin();
 10         return 0;
 11 }


Compile Command: gcc  -std=c99  -o  1  1.c  -lncurses 
Output: hello, world.

Why does the above program display the output without the use of refresh() function.
I also tried using wprintw(stdscr,"hello, world"); instead of line6, but the program still shows the output.

libncurses5 installed on my Ubuntu.


Thanks in advance.
Ankit Shah.

---

### Post by nothingspecial on 2012-08-19
*Thread moved to **Programming Talk**.*

---

### Post by Odexios on 2012-08-19
(w)getch() automatically refreshes the window.

From `man getch`:

```
If the window is not a pad, and it has been moved or modified since the
last call to wrefresh, wrefresh will be called before another character
is read.
```

---

### Post by Ankitshah on 2012-08-19
Thank you :-)

---

