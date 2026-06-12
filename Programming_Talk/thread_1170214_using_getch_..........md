---
title: "using getch ........."
date: 2009-05-26
forum: Programming Talk
---

### Post by muctadir on 2009-05-26
i am trying to make a program in c using getch() function. but it did not worked. so, i downloaded ncurses-dev file. but still it is not working. please tell me how can i solve the problem.......???????
in windows getch() inputs a data without pressing enter. 
in ubuntu is it possible.......???

---

### Post by lloyd_b on 2009-05-26
> **muctadir said:**
> i am trying to make a program in c using getch() function. but it did not worked. so, i downloaded ncurses-dev file. but still it is not working. please tell me how can i solve the problem.......???????
in windows getch() inputs a data without pressing enter. 
in ubuntu is it possible.......???

"man cbreak" in a terminal window.  Normally, the tty device is in "line-buffered" mode, where keypresses are not available to a program until the <ENTER> key is pressed.  By calling the cbreak() function, you can change this so that keypresses are available immediately.

Lloyd B.

---

### Post by samjh on 2009-05-26
First, what do you mean by "doesn't work"???  Does it crash?  Does it not compile?  What does it do (or not do) to make you say it doesn't work?

Second, did you consult the documentation available for ncurses?
See: [http://tldp.org/HOWTO/NCURSES-Programming-HOWTO/index.html](http://tldp.org/HOWTO/NCURSES-Programming-HOWTO/index.html)

I tried to Hello World example in that link, and it worked fine for me.
```
#include <ncurses.h>

int main(void)
{
	initscr();
	printw("Press any key to exit.\n");
	refresh();
	getch();
	endwin();

	return 0;
}
```
Compile with:
```
gcc test.c -o test -lncurses
```
Notice that the example uses getch().  No problem.

---

### Post by muctadir on 2009-05-26
sorry. can you make it a little clear for me.......?????????

---

### Post by muctadir on 2009-05-26
> **samjh said:**
> First, what do you mean by "doesn't work"???  Does it crash?  Does it not compile?  What does it do (or not do) to make you say it doesn't work?

Second, did you consult the documentation available for ncurses?
See: [http://tldp.org/HOWTO/NCURSES-Programming-HOWTO/index.html](http://tldp.org/HOWTO/NCURSES-Programming-HOWTO/index.html)

I tried to Hello World example in that link, and it worked fine for me.
```
#include <ncurses.h>

int main(void)
{
    initscr();
    printw("Press any key to exit.\n");
    refresh();
    getch();
    endwin();

    return 0;
}
```Compile with:
```
gcc test.c -o test -lncurses
```Notice that the example uses getch().  No problem.











thanks..........i will try........

---

