---
title: "[Curses][Python] Typed text in terminal is invisible _after running program_"
date: 2009-03-05
forum: Programming Talk
---

### Post by fiddler616 on 2009-03-05
Hello,
Today I learned about curses--and found this tutorial.
To make sure I was doing things right, I made a simple Hello World! script:
[PHP]import curses as c
stdscr = c.initscr()
c.noecho()
c.cbreak()
stdscr.keypad(1)
stdscr.addstr("Hello World!\n")
stdscr.refresh()

c.nocbreak(); stdscr.keypad(0); c.echo() #To return terminal back to normal[/PHP]
Which outputs:
```
Hello World!
timmy@Stanway01:~$ 

```
And then I can use my terminal like normal--except I can't see anything I type in. For example:
```
Hello World!
timmy@Stanway01:~$ Python 2.5.2 (r252:60911, Oct  5 2008, 19:24:49) 
                                                                    [GCC 4.3.2] on linux2
         Type "help", "copyright", "credits" or "license" for more information.
                                                                               >>> timmy@Stanway01:~$ 
```
I typed in python, and then exit(). And yes, it did that spacing.

How do I solve this? Thank you.

---

### Post by wmcbrine on 2009-03-05
You need to call endwin() when you're done, before exiting the program. Your last line is nonsense; replace it with "c.endwin()".

Of course, this will clear the screen. To avoid that, insert a getch() before the endwin(). The screen will still be cleared, but at least you'll get a chance to read it. If you want to put up output that will remain when you exit the program, then curses isn't really what you want.

Meanwhile, if your program does exit without calling endwin(), you can run "reset" on the command line to restore the terminal state.

---

### Post by fiddler616 on 2009-03-06
Hmm...getch() and curses.getch() both raise error. curses.endwin() works though--thanks! (Although you're right--it does whizz by the screen)

---

### Post by wmcbrine on 2009-03-06
In Python, getch() is a window method: stdscr.getch()

---

### Post by fiddler616 on 2009-03-06
> **wmcbrine said:**
> In Python, getch() is a window method: stdscr.getch()
Ah, that'll do it.

Thanks a lot!

*Solved*

---

