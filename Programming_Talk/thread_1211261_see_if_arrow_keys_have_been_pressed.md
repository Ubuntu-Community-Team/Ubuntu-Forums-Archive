---
title: "see if arrow keys have been pressed"
date: 2009-07-12
forum: Programming Talk
---

### Post by Gimp5y4 on 2009-07-12
Hi I'm new to c, I'm trying to read the arrow keys with out hiting the return key
I've tried several thing from different forums nothing works any ideas 

any help would be appreciated

---

### Post by Zugzwang on 2009-07-12
Do you use any toolkits? 

If not, you can try the "ncurses" library or if you want to go into game programming anyway, try "SDL". Use google to find details.

Also, in which environment should the solution work?

---

### Post by Gimp5y4 on 2009-07-12
Hi I need to write to a file in terminal mode

---

### Post by nvteighen on 2009-07-12
Then ncurses is what you need. Other options would lead you to very low-level terminal programming with termios and such stuff... ncurses, though a really weird piece of code (written with older standards in mind), will help you.

But may I ask you how "new to C" you are?

---

### Post by Zugzwang on 2009-07-12
Here's some example that lacks all error checking. It gives you some ideas how to perform your task:

[PHP]
#include <curses.h>

static WINDOW *mainwnd;
char *msg;
	
int main(void) {
   mainwnd = initscr();
   noecho();
   keypad(mainwnd,true);
   int current_getch = getch();
   if (current_getch == KEY_LEFT) {
        msg = "Left\n";
   } else {
        msg = "Some other key\n";
   }
   screen_end();
   endwin();
   printf(msg);
   return 0;
}
[/PHP]

Compile (link) with "-lcurses" as option.

---

### Post by Gimp5y4 on 2009-07-12
very new, i went to night school about 10 years ago but the class ended half way through
just geting back in to it geting most info out of books and the web

---

### Post by nvteighen on 2009-07-12
> **Gimp5y4 said:**
> very new, i went to night school about 10 years ago but the class ended half way through
just geting back in to it geting most info out of books and the web
Hm... A faux débutant... I guess you'll manage it with Zugzwang's example. Good luck! And don't forget to ask if you need it! :)

---

