---
title: "simple ncurses question"
date: 2009-05-08
forum: Programming Talk
---

### Post by chris200x9 on 2009-05-08
I am starting to learn ncurses, I have written a simple program (modified from the tutorial here: [http://tldp.org/HOWTO/NCURSES-Programming-HOWTO/init.html](http://tldp.org/HOWTO/NCURSES-Programming-HOWTO/init.html))

```
 
#include <ncurses.h>
using namespace std;
int main()
{	
	int ch;
	initscr();			/* Start curses mode 		  */
	keypad(stdscr, TRUE);
	printw("hit enter");	/* Print Hello World		  */
				/* Print it on to the real screen */
	getch();			/* Wait for user input */
	ch=wgetch(stdscr);
	if (ch == KEY_ENTER)
	{
	mvprintw(10, 10, "you hit enter");
	refresh();
}

	endwin();			/* End curses mode		  */

	return 0;
}

```

my question is why when I hit enter it does nothing, instead of printing you pressed enter at (10,10). I am confused as why this is happening it seems simple enough, any help would be greatly appriciated! :P

---

### Post by Neheb on 2009-05-08
the problem is that, at least on my computer, KEY_ENTER is not actually the value of the enter key. for me it worked checking ch == '\n'. in this case it would have been smart to do an else and print what ch is.

other things: you probably want to remove the first getch(), as right now it waits for 2 buttons to be pressed. You also want to add a getch() or wgetch() just before the endwin() so you can actually see it print something before it closes.

---

### Post by chris200x9 on 2009-05-08
thank you! (takk...I know norsk! :P)

---

