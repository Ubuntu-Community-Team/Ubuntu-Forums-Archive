---
title: "ncurses key testing"
date: 2007-04-26
forum: Programming Talk
---

### Post by ironfistchamp on 2007-04-26
Hey all

I have started using ncurses and I seem to be getting the hang of it. One thing I am having problems with is testing to see what key was pressed. I had been told somewhere to use getch to get a keypress into an int variable. That works fine. The question is how do I test what the value it. I understand it comes out as an ASCII code but I don't know what they are and it would be much easier to say 

if (choice == "w")

How might I be able to do this?

Thanks

Ironfistchamp

---

### Post by wmcbrine on 2007-04-26
You're on the right track. Just change that to single quotes:

if (choice == 'w')

That's for regular keys. For things like the up arrow key, use the symbols defined in curses.h:

if (choice == KEY_UP)

Note that if you want to be able to read those special keys, you need to set the keypad mode on the window before calling getch():

keypad(stdscr, TRUE);

---

### Post by ironfistchamp on 2007-04-26
Excellent now I can get on with my learning by doing :) 

Thanks very much

Ironfistchamp

---

