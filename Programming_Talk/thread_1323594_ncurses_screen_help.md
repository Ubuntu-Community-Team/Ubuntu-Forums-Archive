---
title: "ncurses screen help"
date: 2009-11-11
forum: Programming Talk
---

### Post by chris200x9 on 2009-11-11
I am having a problem looping the area allowed to move. The code below is what I have so far. 
```
 #include <ncurses.h>			  
#include <string.h> 

int main()
{
	
 int row,col, ch;	
 initscr();
 raw();				/* Line buffering disabled	*/
	keypad(stdscr, TRUE);		/* We get F1, F2 etc..		*/
	noecho();			/* Don't echo() while we do getch */

int currentr, currentc;

 char guy = '*';
 getmaxyx(stdscr,row,col);	
 int midr = row/2;
 int midc = col/2;
 mvaddch(midr, midc, guy); 
  while (ch != 'q')
	
 {
	 ch = getch();
	 mvaddch(midr, midc, ' ');
	 getyx(stdscr, currentr, currentc);
	 
		 if( ch == KEY_UP)
	 {
		 if ( currentr == row)
		 {
			 midr = 1;
		 }

	midr--;
}
if (ch == KEY_LEFT)
{
	midc--;
}

if (ch == KEY_RIGHT)
{
	midc++;
}
if (ch == KEY_DOWN)
{
	midr++;
	}

 mvaddch(midr, midc, guy);

}
 refresh();

 endwin();

 return 0;
}

```

the part in question is:
```
 getyx(stdscr, currentr, currentc);
	 
		 if( ch == KEY_UP)
	 {
		 if ( currentr == row)
		 {
			 midr = 1;
		 }

	midr--;
}
```

I fail to see why my "guy" goes off screen when I reach the upper edge, and not show back up at the bottom of the screen.

---

### Post by 0cton on 2009-11-12
maybe because upper left corner is 0,0
it goes like this the screen:
 x 0 1 2 3 ...
y
0
1
2
3

---

### Post by chris200x9 on 2009-11-12
> **0cton said:**
> maybe because upper left corner is 0,0
it goes like this the screen:
 x 0 1 2 3 ...
y
0
1
2
3

ah oops thanx

---

