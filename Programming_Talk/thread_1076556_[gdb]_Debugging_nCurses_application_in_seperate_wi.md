---
title: "[gdb] Debugging nCurses application in seperate window"
date: 2009-02-21
forum: Programming Talk
---

### Post by unoodles on 2009-02-21
I am trying to debug a console application that uses the Curses library.
The problem is that I try to run it by executing 'gdb ./app'.
Then I set some breakpoints, but as soon as the Curses library is initialized, the console gets filled with the graphics from the application.
How do I step through an application if I cannot access the gdb prompt?

Thanks.

---

### Post by nvteighen on 2009-02-21
You can redirect gdb's output. Look at this guide:
[http://dirac.org/linux/gdb/07-Debugging_Ncurses_Programs.php](http://dirac.org/linux/gdb/07-Debugging_Ncurses_Programs.php)

---

