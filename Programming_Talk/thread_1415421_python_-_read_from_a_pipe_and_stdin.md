---
title: "python - read from a pipe and stdin"
date: 2010-02-24
forum: Programming Talk
---

### Post by benj1 on 2010-02-24
im trying the write a python app that will take data from a pipe as well as non blocking input while running. 
the problem is, is that it won't take input if something has been piped to it.
im assuming its because stdin is still connected to the pipe but ive also tried flushing stdin and modifying it to read from /dev/stdin, all to no avail.

any suggestions ?

EDIT:
ive made some progress, resetting stdin using
```
sys.stdin = open('/dev/tty', 'r')
```
and then calling a custom getch
```

def getch():
    fd = sys.stdin.fileno()
    tty_mode = tty.tcgetattr(fd)
    tty.setcbreak(fd)
    try:
        ch = os.read(fd, 1)
    finally:
            tty.tcsetattr(fd, tty.TCSAFLUSH, tty_mode)

    return ch

```
gets me basic functionality, although non ascii codes will be problematic

the curses builtin getch is still being problematic

---

### Post by d3v1150m471c on 2010-02-24
```

#!/bin/bash/py
var=input([Enter your name: ])

```

It's been a while since I touched python. This may work as well and better suit your need.
```

var2=input('print hello world')

```

---

### Post by benj1 on 2010-02-25
> **d3v1150m471c said:**
> ```

#!/bin/bash/py
var=input([Enter your name: ])

```

It's been a while since I touched python. This may work as well and better suit your need.
```

var2=input('print hello world')

```

input() and raw_input() have the same problem (well at least until I reset stdin) of just immediately returning an empty string.
Anyway i want it non blocking, ie not having to press enter after a command, so they won't work.

I think my getch() implementation will probably be ok, I still haven't worked out why curses getch() isn't functional, I suspect its because its setup to point to stdin before the script runs, so when i reassign stdin, curses getch() ignores it an carries on reading from the pipe.

ps
```
#!/bin/bash/py
```
I like it :D

---

