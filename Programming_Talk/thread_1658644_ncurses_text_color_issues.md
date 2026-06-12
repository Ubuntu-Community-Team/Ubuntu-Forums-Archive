---
title: "ncurses text color issues"
date: 2011-01-02
forum: Programming Talk
---

### Post by cesiel1990 on 2011-01-02
I was playing around with ncurses and had trouble printing colored text to the terminal.

I'd like to turn the text red.  This is the code I was using:
```
#include "ncurses.h"
#include <cstdlib>

using namespace std;

int main(){

   initscr();
   if(has_colors() == FALSE)
   {
       endwin();
       printf("Your terminal does not support color\n");
       exit(1);
   }
   
   attron(A_BOLD | COLOR_PAIR(1));
   printw("TEST");
   attroff(A_BOLD | COLOR_PAIR(1));
   getch();
   endwin();
   return 0;
}

```

The program prints bold "TEST" in the terminal but the text color is not red.  What could be causing this?

---

### Post by odyniec on 2011-01-03
You need to call the start_color() function, and initialize the color pair with init_pair(), e.g.:

```
start_color();
init_pair(1, COLOR_RED, COLOR_BLACK);
```

---

