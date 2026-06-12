---
title: "Python keys"
date: 2010-09-03
forum: Programming Talk
---

### Post by limestone on 2010-09-03
Help!
How to make a python program "recognize" a key press?
eg. I want to quit my program using ctrl+q or ctrl+l to load a file._ How to write that_ and _where in the program_?
The program is just a CLI not GUI.

---

### Post by surfer on 2010-09-03
i'd advise you to use [curses]("http://docs.python.org/howto/curses.html") (or do you already?). curses can intercept all keyboard inputs.

---

### Post by limestone on 2010-09-03
```

import curses
[FONT=Verdana]
[/FONT]while 1:
    c = stdscr.getch()
    if c == ord('p'): PrintDocument()
    elif c == ord('q'): break  # Exit the while()

```I guess the whole program shall be inside the while loop, right?
or can I make a def and call the function from anywhere?

---

