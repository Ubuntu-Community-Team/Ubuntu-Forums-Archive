---
title: "Controlling STout"
date: 2006-07-25
forum: Programming Talk
---

### Post by sadscientist on 2006-07-25
Yar!

I'm trying to control stout in a way similar to what "top" does.  How does top update it's output to the terminal without making it scroll?

---

### Post by xtacocorex on 2006-07-25
It uses ncurses. I'd offer to explain more, but I haven't used the curses library yet in a program of mine.

My friend did use it in a perl script and it doesn't seem that hard to use.

Here are some links to some tutorials:
[http://www.captain.at/howto-curses-example.php](http://www.captain.at/howto-curses-example.php)
[http://web.cs.mun.ca/~rod/ncurses/ncurses.html](http://web.cs.mun.ca/~rod/ncurses/ncurses.html)
[http://www.linux.com/howtos/NCURSES-Programming-HOWTO/index.shtml](http://www.linux.com/howtos/NCURSES-Programming-HOWTO/index.shtml)

Hope this helps.

---

### Post by sadscientist on 2006-07-25
That ROCKS!  Here comes Terminal Pong(osity?).

Quick note:

ncurses came installed with kubuntu, but I needed to add the -dev package (to get curses.h):
```
$ sudo apt-get install libncurses5-dev
```

---

### Post by xtacocorex on 2006-07-25
Terminal Pong!? 

I started working on a version of Pong with QT a year ago, but never got anywhere since I don't know game programming and didn't have a clue as to GUI programming back then. I think I got rid of the craptacular source code I had because it was worthless.

Sorry for not mentioning the need for the -dev package, but I'm glad you figured it out.

Good luck with the project!

---

### Post by sadscientist on 2006-07-25
Haha, it's not perfect but it was fun:

Makefile:
```

all:: pong

pong: pong.c
        gcc -o $@ $? -lncurses

clean::
        rm -f pong

.PHONY: clean

```

pong.c
```

#include <ncurses.h>
/* butchered win_border.c from 
   http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/NCURSES-Programming-HOWTO.html
   
   weee, pong!
 */

WINDOW *create_newwin(int height, int width, int starty, int startx);
void destroy_win(WINDOW *local_win);

int main(int argc, char *argv[])
{	WINDOW *my_win;
        WINDOW *ball; 
	WINDOW *border;

        int px, py, width, height;      /* for the paddle.. */
        int x, y, bsize, vx, vy;	/* for the ball.. */
	int ch;

	initscr();			/* Start curses mode 		*/
	halfdelay(1);			/* Line buffering disabled, and.. */
					/*  animate every 1/10 second!	*/
	
	keypad(stdscr, TRUE);		/* I need that nifty F1 	*/

	bsize=2;                        /* size of the 'ball' */
	height = 2;                     /* height and size of the ball */
	width = 10;
	py = (LINES - height) - 4;	/* Calculating for a center placement */
	px = (COLS - width) / 2;	/* of the paddle		*/
	y=2*(LINES - height) / 9;       /* then place the ball..*/
	x=(COLS - width) / 2;           

	vx=1;                           /* velocity of the ball in x */ 
	vy=1;                           /* and y directions */

	refresh();

	border= create_newwin(LINES-2, COLS-2, 1, 1);  /* draw ourselves a border*/
	my_win = create_newwin(height, width, py, px); 
	ball = create_newwin(bsize,bsize,y,x);

	while((ch = getch()) != KEY_F(1)) /* wait 1/10 second for input..*/
	{	
	        switch(ch)  
		{	case KEY_LEFT:
			        destroy_win(my_win);
				if(px>3)
					px-=2;
				my_win = create_newwin(height, width, py,px);
				break;
			case KEY_RIGHT:
				destroy_win(my_win);
				if(px+width<COLS-3)
					px+=2;
				my_win = create_newwin(height, width, py,px);
				break;
		}	

	        /* move the ball */
		destroy_win(ball);
		
		/* bounce off of walls */
		if(x>=(COLS-4) || (x+vx)<=1){
			vx*=-1;
		}
		if(y>=(LINES-4) || (y+vy)<=1){
			vy*=-1;
		}

		/* bounce off of the paddle */
		if((y+vy)>=py){			
			if((x+vx)>(px-2)){
				if((x+vx)<(px+width)){
					vy*=-1;	
				}
			}
		}

		x+=vx;
		y+=vy;	
		ball = create_newwin(bsize,bsize,y,x);

		/* display this in the top left corner*/
		move(0, 0);
		printw("Press F1 to exit ..");

	}
		
	endwin();			/* End curses mode		  */
	return 0;
}

WINDOW *create_newwin(int height, int width, int starty, int startx)
{	WINDOW *local_win;

	local_win = newwin(height, width, starty, startx);
	box(local_win, 0 , 0);		/* 0, 0 gives default characters 
					 * for the vertical and horizontal
					 * lines			*/
	wrefresh(local_win);		/* Show that box 		*/

	return local_win;
}

void destroy_win(WINDOW *local_win)
{	
	/* box(local_win, ' ', ' '); : This won't produce the desired
	 * result of erasing the window. It will leave it's four corners 
	 * and so an ugly remnant of window. 
	 */
	wborder(local_win, ' ', ' ', ' ',' ',' ',' ',' ',' ');
	/* The parameters taken are 
	 * 1. win: the window on which to operate
	 * 2. ls: character to be used for the left side of the window 
	 * 3. rs: character to be used for the right side of the window 
	 * 4. ts: character to be used for the top side of the window 
	 * 5. bs: character to be used for the bottom side of the window 
	 * 6. tl: character to be used for the top left corner of the window 
	 * 7. tr: character to be used for the top right corner of the window 
	 * 8. bl: character to be used for the bottom left corner of the window 
	 * 9. br: character to be used for the bottom right corner of the window
	 */
	wrefresh(local_win);
	delwin(local_win);
}

```

---

### Post by xtacocorex on 2006-07-25
Not bad at all. Using F1 to exit causes the Gnome Terminal help to open, but it's all good. 

For a first attempt, it's far better than what I got.

Keep up the good work!

---

### Post by sadscientist on 2006-07-26
Hmm.. I'm using KDE so I didn't have the F1 problem.  Shouldn't be hard to change it to ESC.

My goal is actually to make a little online role-playing game that'll run from the console without much hastle.. ncurses seems like a good library to use for a simple UI.  Thanks again!

---

