---
title: "Python curses problem"
date: 2009-03-12
forum: Programming Talk
---

### Post by Taidgh on 2009-03-12
So I have this piece of code:
```

import sys, time, curses

def main():
    menu = 1
    stdscr = curses.initscr()
    while menu:
        menu()
        input = stdscr.getch()
        if chr(input) == "p":
            practice = 1
            stdscr.clear()
            inBox = curses.newwin(5, 40, 7, 20)
            while practice:
                practice()
        if chr(input) == 'q':
            sys.exit()

def menu():
    stdscr.clear()
    curses.curs_set(0)
    stdscr.addstr("""PyVocab 0.1 
    -Practice Vocabulary [p]
    -Add Vocabulary Lists [a]
    -Quit [q]""")
    stdscr.refresh()
    
def practice():
    stdscr.addstr(0 , 0, "Practice mode", curses.A_REVERSE)
    inBox.addstr(0, 0, "")
    stdscr.refresh()

if __name__ == '__main__': 
    curses.wrapper(main())

```
I realise it's not exactly elegant, but it's a start. When I try to run it, I get this:
```

Traceback (most recent call last):
File "vb.py", line 53, in <module> curses.wrapper(main())
File "vb.py", line 27, in main menu()
TypeError: 'int' object is not callable
                 ------------------
(program exited with code: 1)
 Press return to continue

```
Is this a problem with curses.wrapper? I tried changing the line to curses.wrapper(main), but then I just get this:
```

  File "vb.py", line 53, in <module>
    curses.wrapper(main)
  File "/usr/lib/python2.5/curses/wrapper.py", line 44, in wrapper
    return func(stdscr, *args, **kwds)
TypeError: main() takes no arguments (1 given)

```
Any ideas?

---

### Post by WW on 2009-03-12
Your second version of the call to wrapper, with 'main' as the argument instead of 'main()', is correct, but main() must be defined so that its first argument is the main window 'stdscr' variable.  See the bottom of the [curses documentation web page](http://docs.python.org/library/curses.html).  So change your main() function to take stdscr as an argument.  You'll also have to pass stdscr as an argument to the functions menu() and practice() if they are going to use it.

---

### Post by Taidgh on 2009-03-12
Thanks for that.

---

