---
title: "compile a unix program in linux environment"
date: 2009-03-14
forum: Packaging and Compiling Programs
---

### Post by poonam on 2009-03-14
I have used a new header file called CURSES.H and my whole program is based on that header file.when i try to compile my program it shows me error "No such path or directory".What can be done?.A part of the program is given below
#include<unistd.h>
#include<stdlib.h>
#include<curses.h>
#include<string.h>
#include<ctype.h>
void init_curses()
{
	initscr();
	getmaxyx(stdscr,LINES,COLS);
	start_color();
	init_pair(1,COLOR_WHITE,COLOR_BLUE);//for editor
	init_pair(2,COLOR_BLUE,COLOR_WHITE);//for menu
	init_pair(3,COLOR_RED,COLOR_WHITE);//for shortcur key
	init_pair(4,COLOR_BLUE,COLOR_CYAN);//for welcome
	init_pair(5,COLOR_BLACK,COLOR_RED);//for welcome
	init_pair(6,COLOR_MAGENTA,COLOR_YELLOW);
	noecho();
	keypad(stdscr,TRUE);
	cbreak();
}

---

### Post by poonam on 2009-03-14
PLZ its urgent!!!!!!!!!!!Give me the solution as soon as possible

---

### Post by mcla0203 on 2009-03-14
Here are the types of includes, make sure you use the right one for it:
```
#Local dependent
#include "local.h"

#CLib dependent
#include <clib.h>

#CppLib dependent
#include <cpplib1.hpp>
#include <cpplib2>
```

---

### Post by lloyd_b on 2009-03-14
In a terminal window:```
sudo apt-get install libncurses5-dev
```
"ncurses" an updated version of the older Unix curses library, and should provide all the functionality you need for that program.

Lloyd B.

---

### Post by kcode on 2009-03-15
After installing ncurses, compile your program with option -lncurses.

---

### Post by lloyd_b on 2009-03-15
> **kcode said:**
> After installing ncurses, compile your program with option -lncurses.

Assuming he has a makefile that does "-lcurses" it will still work - the ncurses package creates a "libcurses.so" (which is a symlink to "libncurses.so").

Lloyd B.

---

