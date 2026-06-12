---
title: "ncurses"
date: 2009-03-26
forum: Programming Talk
---

### Post by cmay on 2009-03-26
hi. 
i am reading a book where there is some tutorials on ncurses in it and i want to try them out. i can compile this and when i try to run it it it complaints as if the library is not installed. i did cat |/usr/include/ncurses.h to check if its installed  and it is there.  how can i make it work. the gtk examples works and i installed the gnome-devel package and use geany but from commandline it do not compile either. 
[PHP]#include <ncurses.h>

int main()
{    
    initscr();            /* Start curses mode           */
    printw("Hello World !!!");    /* Print Hello World          */
    refresh();            /* Print it on to the real screen */
    getch();            /* Wait for user input */
    endwin();            /* End curses mode          */

    return 0;
}[/PHP]

thanks for the time.

---

### Post by dwhitney67 on 2009-03-26
The ncurses.h is not the *complete* library.  It is merely a header file that provides declarations of ncurses functions.

You need to link your application with -lncurses to obtain the "real" library which contains the actual function definitions (implementations).

---

### Post by cmay on 2009-03-26
thanks. it worked. 
i dont know why it did not the first times but i actually did compile it this way. 
gcc -o hurray ./hello_world_ncurses.c -lncurses
whit out succes the first time. thats why i asked here what to do. but then just now i copied the -ncurses option from your post and did it again and it worked. i guess i have maybe mispelled it the first few times. 

anyway thanks alot.

---

