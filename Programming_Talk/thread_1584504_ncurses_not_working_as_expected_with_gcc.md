---
title: "ncurses not working as expected with gcc"
date: 2010-09-29
forum: Programming Talk
---

### Post by trubshac on 2010-09-29
I am having trouble with the ncurses library.  I have this code:
```
#include <ncurses.h>

int main(int argc, char **argv)
{
int i;

    initscr();
    nodelay(stdscr,TRUE);  // getch() is non-blocking

    for(i=0;i<20;i++);  // draw a diagonal line of Xs
    {
        move(i,i);
        addstr("X");
        refresh();
    }    
    addstr("Fred");
    refresh();
    while(getch()==-1)
    {
    }
    endwin();
    return 0;
}
```
..which I expect to display a diagonal line of Xs followed by the word Fred.  When I press a key, the display should clear and the program terminate.
What actually happens is that I only see the final single X at position 19,19 and the word Fred.

I am compiling with 'gcc (Ubuntu 4.4.1-4ubuntu9) 4.4.1' using ```
gcc -o test main.c -lncurses
```

I have tried 'man ncurses' and also searched this and other forums, but am unable to find a solution.  
Perhaps someone here could help?

---

### Post by pbrane on 2010-09-29
> **trubshac said:**
> I am having trouble with the ncurses library.  I have this code:
```
#include <ncurses.h>

int main(int argc, char **argv)
{
int i;

    initscr();
    nodelay(stdscr,TRUE);  // getch() is non-blocking

    **for(i=0;i<20;i++);**  // draw a diagonal line of Xs
    {
        move(i,i);
        addstr("X");
        refresh();
    }    
    addstr("Fred");
    refresh();
    while(getch()==-1)
    {
    }
    endwin();
    return 0;
}
```
..which I expect to display a diagonal line of Xs followed by the word Fred.  When I press a key, the display should clear and the program terminate.
What actually happens is that I only see the final single X at position 19,19 and the word Fred.

I am compiling with 'gcc (Ubuntu 4.4.1-4ubuntu9) 4.4.1' using ```
gcc -o test main.c -lncurses
```

I have tried 'man ncurses' and also searched this and other forums, but am unable to find a solution.  
Perhaps someone here could help?

Remove the **;** after the for loop. What you have is an empty loop followed by a code block to insert a single 'X'. And at this point the variable 'i' equals 19.

---

### Post by trubshac on 2010-09-29
Damn!  Such an elementary mistake - you wouldn't think I'd been programming in C for 23 years would you!
Well spotted. 
Thanks very much.

---

### Post by pbrane on 2010-09-29
> **trubshac said:**
> Damn!  Such an elementary mistake - you wouldn't think I'd been programming in C for 23 years would you!
Well spotted. 
Thanks very much.

I know the feeling!

---

