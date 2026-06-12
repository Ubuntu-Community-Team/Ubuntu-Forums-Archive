---
title: "non-blocking console input in PYTHON"
date: 2009-03-03
forum: Programming Talk
---

### Post by NetSkay on 2009-03-03
hello...
ive looked down and low, but i can't seem to find anything useful on google...
i would like to know if there is a nonblocking way to read from console input; please dont tell me to use threads, because that is still blocking, and waiting to press enter, either on raw_input or stdin.readline()

is there a way i can set a timeout that when reached and nothing is input it will go ahead and continue executing the code?!

any libraries?

thnx...

---

### Post by jimi_hendrix on 2009-03-03
i have no clue if this works or not but:

maybe do output in a thread and get input in the main program?

---

### Post by Can+~ on 2009-03-03
This behaviour also occurs in C when using scanf/gets/fgets, or any function that reads from the input buffer when it's empty. So I guess the answer isn't so simple.

Maybe it would be better using a GUI.

---

### Post by cabalas on 2009-03-03
I would assume that ncurses would have something which would do what you want and it has bindings to python [http://docs.python.org/library/curses.html](http://docs.python.org/library/curses.html)

---

### Post by NetSkay on 2009-03-03
> **jimi_hendrix said:**
> i have no clue if this works or not but:

maybe do output in a thread and get input in the main program?

dont matter where the output is, the input would still be blocking the socket thread, which is in nonblocking mode

---

### Post by NetSkay on 2009-03-03
> **cabalas said:**
> I would assume that ncurses would have something which would do what you want and it has bindings to python [http://docs.python.org/library/curses.html](http://docs.python.org/library/curses.html)

python curses wont work under windows, i donno why?!

---

### Post by cabalas on 2009-03-03
have you installed ncurses library (not the python binding for the library but the actual library itself) you can find a windows version here: 

[http://gnuwin32.sourceforge.net/packages/ncurses.htm](http://gnuwin32.sourceforge.net/packages/ncurses.htm) 

After getting that installed retry using/installing the curses python bindings

Edit: after a quick google I found that curses is not installed by default on the windows version of python though this package is offered as an alternative [http://adamv.com/dev/python/curses/](http://adamv.com/dev/python/curses/)

---

### Post by wmcbrine on 2009-03-04
There is some hope that curses will be in Windows Python soon... last I heard, it built fine with PDCurses, but they just needed to incorporate that into their build system. Older versions of PDCurses wouldn't link, because they were missing the stupid terminfo functions; so I added a bunch of stubs for those. They don't actually *work*, but you don't actually need them for curses-based programs. (Not implemented because they don't fit PDCurses' non-tty-based model.)

---

