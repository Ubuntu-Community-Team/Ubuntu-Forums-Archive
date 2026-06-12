---
title: "[ncurses] Memory leakage festival?"
date: 2008-07-29
forum: Programming Talk
---

### Post by nvteighen on 2008-07-29
I'm currently learning to use the ncurses library and have noticed that valgrind reports memory leakage when using it. Searching in Google shows me some people complaining on having the same problem... [The GNU ncurses page]("http://www.gnu.org/software/ncurses/") says something like "reduced memory leaks" in the ncurses 5.6 release notes. What does "reduced" mean?... It's a bit annoying to me that a such a popular library may fail in proper memory management...

...but, I already had some stupid valgrind reports when using the CUPS library, which was related to shared memory. GTK+ applications do also usually report memory leakages, even for the ["Hello World" from the GTK+ tutorial]("http://library.gnome.org/devel/gtk-tutorial/stable/c39.html#SEC-HELLOWORLD").

So, whose fault is this? valgrind's? ncurses'? mine? cosmic rays'?

Here it's a little "Hello World" written in C using ncurses. It will leak aprox. 30 KB, still reachable memory:

[PHP]
/* Compile with -lncurses. Be sure you have the libncurses5-dev package 
 * installed. */

#include <curses.h>

int main(void)
{
    initscr();
    cbreak();
    noecho();
    
    printw("Hello!");
    refresh();
    
    getch();
    
    endwin();
    return 0;
}
[/PHP]

The question is: If you use these libraries from a garbage collecting language like Python, there will also be leakages as they're occurring in a binary outside the collector's reach.

Thanks!

---

### Post by dwhitney67 on 2008-07-29
IMHO, there are two types of memory leaks:  1) ones that are recurring during the program's operation, thus consuming ever increasing amounts of system memory, or 2) ones that are one-time allocation(s) of memory that is needed for the purpose of supporting the application.

The latter type will be relinquished back to the system (OS) upon terminating the application.  I personally would not worry about this type.  Now, if your program runs for several hours, days, or whatever, and you see that memory is not being freed and your system resources are shrinking, thus bringing your system to its knees, then I would be concerned.

So to conclude, don't concern your self too much about this:
[PHP]int main()
{
  char *ptr = malloc( 100000 );
  return 0;
}[/PHP]
versus this:
[PHP]int main()
{
  while (1)
  {
    char *ptr = malloc( 100000 );
  }
  return 0;
}[/PHP]
Sure, the proper thing would be to free the allocated memory, but if the allocations are out of your control (such as those in a library), then don't sweat it too much unless your application begins to crash.  ncurses has been around for over 20 (30?) years; I'm sure each release is better than the last, even though there are obviously still some problems.

---

### Post by nvteighen on 2008-07-29
Thanks!

Of course, I know that if a shared library is leaking, it's absolutely out of control and not my problem... But, my concern is actually on whether is acceptable to have such leakages on such libraries or not.

Also, it seems all these cases are rendered as "still reachable" leaks by valgrind/memcheck.

---

### Post by kknd on 2008-07-29
GTK uses reference-counted objects, so valgrind is unable to detect memory leaks properly.

Probably, ncurses also uses a different scheme for memory managment, and valgrind is showing wrong results.

---

