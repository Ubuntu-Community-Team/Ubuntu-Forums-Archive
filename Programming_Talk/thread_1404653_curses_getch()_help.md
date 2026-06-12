---
title: "curses getch() help"
date: 2010-02-11
forum: Programming Talk
---

### Post by dincay on 2010-02-11
Hi. I need a program that user enters characters but they shouldn't be visible on screen. So I wrote the following program. However getch() doesn't wait for a character to be entered and returns -1. The program exits immediately. I tried cbreak(), raw(), noecho() but they didn't work. I couldn't understand their meanings also. Probably I am missing a point. Why getch() doesn't wait?

#include <stdio.h>
#include <curses.h>

int main(void)
{
int x,y;

printf("Enter two character\n");
x = getch();
y = getch();
printf("Entered Values = %c and %c\n",x,y);
printf("Entered Values = %d and %d\n",x,y);

return 1;
}

---

### Post by Some Penguin on 2010-02-11
Read the getch man page about how it behaves in no-delay mode.

Then read the curs_inopts man page and you'll see how to change modes.

---

### Post by dincay on 2010-02-14
I got it. Thanks Some Penguin.
Problem is program is in no-delay mode. To change the delay mode I put 

nodelay(stdscr,0);

to my code. Now it is working,

---

