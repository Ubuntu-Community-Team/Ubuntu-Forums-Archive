---
title: "mvprintw adds an extra zero to numbers &lt; 100 [ C, ncurses ]"
date: 2008-07-06
forum: Programming Talk
---

### Post by Yes on 2008-07-06
When health is 100, it prints 100.  But when it's less than 100 it adds an extra 0 to the end (i.e., 990 instead of 99).  If I try printing health where it's decremented, it prints correctly.  Why would that be?

```
void printEnemy (void) {
	cleanupEnemy ();
	if (alive) {
		mvprintw (y, x, "x");
		mvprintw (y + 1, x + 1, "x");
		mvprintw (y + 1, x, "x");
		mvprintw (y, x + 1, "x");
	}
	
	mvprintw (rows - 1, cols - 20, "Enemy health: %d", health);
}
```

Thanks!

---

### Post by odyniec on 2008-07-07
You may be overwriting the old value -- are you sure the "0" isn't already there?

Besides, I assume the "health" value can be in the range 0-100, so you could probably display it using a minimum field width of 3, ie.:
```
"Enemy health: %3d"
```

---

### Post by nvteighen on 2008-07-07
> **Yes said:**
> When health is 100, it prints 100.  But when it's less than 100 it adds an extra 0 to the end (i.e., 990 instead of 99).  If I try printing health where it's decremented, it prints correctly.  Why would that be?

```
void printEnemy (void) {
	cleanupEnemy ();
	if (alive) {
		mvprintw (y, x, "x");
		mvprintw (y + 1, x + 1, "x");
		mvprintw (y + 1, x, "x");
		mvprintw (y, x + 1, "x");
	}
	
	mvprintw (rows - 1, cols - 20, "Enemy health: %d", health);
}
```

I can deduce 'health' is a global variable, isn't it? (Otherwise, that code wouldn't compile). So, maybe another function is setting 'health' incorrectly and making it misbehaive; that's one of the disadvantages of global variables: they're more difficult to debug.

Probably, a "OOP-like" approach, using C structures would be better. So you package all relevant information into one data type and you can just pass the instances into functions. (I hope you know about data structures; they're the most similar thing to objects we have in C).

---

### Post by gnusci on 2008-07-07
I cannot see the problem, try with this small code an let me know whether you get the same problem or not?

[PHP]
#include <stdlib.h>
#include <curses.h>

int main(void){
    int health = 99;

    initscr();
    mvprintw(5,5,"Enemy health: %i\n", health);
    refresh();
    getch();
    endwin();
    return 0;
}
[/PHP]

---

### Post by Yes on 2008-07-07
Adding 3 infront of the d worked.  I.e., 'mvprintw (rows - 1, cols - 20, "Enemy health: %3d", health);'  Why is that?

Thanks.

---

### Post by geirha on 2008-07-07
It's probably because when health is 100, it uses three characters to print the number. 

[color=green]100[/color]

Then when health goes down to 99, it will print

[color=blue]99[/color][color=green]0[/color]

But you are not overwriting the third character, so the last 0 of 100 remains. 
The %3d format, ensures that the number uses 3 spaces no matter how small it is, so it will always overwrite all three characters.

[color=blue]_99[/color]

This is just a guess, based on a hunch.

EDIT: And this is basically just what odyniec said earlier, but in color.

---

### Post by Yes on 2008-07-07
OH!  Ok, that makes sense.  Thanks!

---

