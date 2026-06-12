---
title: "Python key press detect (in terminal, no enter or pause)"
date: 2018-06-19
forum: Programming Talk
---

### Post by Spae on 2018-06-19
I've made most of the game snake so that it runs directly in the terminal, the graphics being character blocks.
Now I have to figure out how to allow a change of direction via key press to finish it up. I haven't had to use any external libraries so far so I'd prefer to keep it that way, if possible.
As far as I can tell, curses won't detect keys without first drawing its' own window. So maybe this isn't possible at all... I thought it'd be neat to make something that plays directly in the terminal.

---

### Post by Skaperen on 2018-06-20
what language are you programming in?

---

### Post by Spae on 2018-06-21
python

---

### Post by The Cog on 2018-06-22
This seems to work nicely:
[http://www.jonwitts.co.uk/archives/896](http://www.jonwitts.co.uk/archives/896)

---

### Post by Spae on 2018-06-22
wow, thank you so much!

---

### Post by Spae on 2018-06-23
Hmm, it seems to stop in the getch function if no key is pressed which pauses the game. There should be an output if no key is pressed, or a break rather than waiting for a key.

---

### Post by spjackson on 2018-06-23
> **Spae said:**
> Hmm, it seems to stop in the getch function if no key is pressed which pauses the game. There should be an output if no key is pressed, or a break rather than waiting for a key.

This is because sys.stdin.read() blocks. One option for non-blocking input (at least on Linux) is as follows. (Changes from [http://www.jonwitts.co.uk/archives/896](http://www.jonwitts.co.uk/archives/896) are marked in red.)
```

#!/usr/bin/python3
 
# adapted from https://github.com/recantha/EduKit3-RC-Keyboard/blob/master/rc_keyboard.py
 
import sys, termios, tty, os, time
[COLOR=#ff0000]import fcntl[/COLOR]
 
def getch():
    fd = sys.stdin.fileno()
    old_settings = termios.tcgetattr(fd)
    try:
        tty.setraw(sys.stdin.fileno())
        ch = sys.stdin.read(1)
 
    finally:
        termios.tcsetattr(fd, termios.TCSADRAIN, old_settings)
    return ch
 
button_delay = 0.2

[COLOR=#ff0000]fd = sys.stdin.fileno()
fl = fcntl.fcntl(fd, fcntl.F_GETFL)
fcntl.fcntl(fd, fcntl.F_SETFL, fl | os.O_NONBLOCK)[/COLOR]
 
while True:
    char = getch()
 
    if (char == "p"):
        print("Stop!")
        exit(0)
 
[COLOR=#ff0000]    lif (not char):
        print("No char")
    elif (char == "a"):
[/COLOR]        print("Left pressed")
        time.sleep(button_delay)
 
    elif (char == "d"):
        print("Right pressed")
        time.sleep(button_delay)
 
    elif (char == "w"):
        print("Up pressed")
        time.sleep(button_delay)
 
    elif (char == "s"):
        print("Down pressed")
        time.sleep(button_delay)
 
    elif (char == "1"):
        print("Number 1 pressed")
        time.sleep(button_delay)

```

---

