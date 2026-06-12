---
title: "Alternative for conio.h -&gt; ncurses.h not working help"
date: 2008-08-05
forum: Programming Talk
---

### Post by Gaurav_Shah on 2008-08-05
From somewhere I came to know ncurses.h is alternative for conio.h .
This is my code.
//test.c
#include<ncurses.h>
int main()
{
    int i=0;
    char a[]="Help Me! ",ch;
    initscr();
    
    do
    {
        noecho();
        ch=getch();
        printw("%c",a[i%9]);
        i++;
    }while(ch!=27); // 27 means ESC
    
    endwin();
    return 0;
}
i tried it to compile with "gcc test.c" but it is not working can you tell me how to use this ?
Thanks.

---

### Post by lisati on 2008-08-05
Is this the first C/C++ program you've tried to compile? If so, you might need to run ```
sudo apt-get install build-essential
``` 

Have you previously successfully compiled programs? What error message(s) and/or problems are you experiencing? Do you have ncurses installed on your computer?

---

### Post by nvteighen on 2008-08-05
Not forget to install: libncurses5-dev

And to use the link flag, e.g: "gcc test.c *-lncurses*"

---

### Post by samjh on 2008-08-05
> **Gaurav_Shah said:**
> i tried it to compile with "gcc test.c" but it is not working can you tell me how to use this ?
Thanks.

What errors is the compiler producing?  Or if it compiles, what happens when you run the resultant executable?

As Lisati has mentioned, have you install the build-essential package?  This package includes files needed to successfully compile C/C++ programs (and more):
```
sudo apt-get install build-essential
```

Then, have you installed the NCurses development libraries, as mentioned by Nvteighen?
```
sudo apt-get install libncurses5-dev
```

And make sure to link the libraries when you compile:
```
gcc test.c -o test -lncurses
```

---

### Post by Nimra on 2008-11-02
Hi,

I also tried to compile source code where I included curses.h
The curses.h file was not found in /usr/include. Maybe try to include <ncursesw/curses.h> instead of <curses.h>. In my case this helped.

Hope this helps you

---

