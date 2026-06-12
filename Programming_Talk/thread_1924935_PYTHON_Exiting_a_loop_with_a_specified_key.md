---
title: "PYTHON: Exiting a loop with a specified key"
date: 2012-02-13
forum: Programming Talk
---

### Post by EmilHem on 2012-02-13
Hello. I'm wondering how I can use a while loop that's exited when the user presses 'e'.
I'm only intending to use this on Linux.

I'm using Python version 2.7.2+

Pseudocode:
```
while key_pressed('e') == False:
    do awesome stuff here
```

or
```
while True:
    do awesome stuff here
    if key_pressed('e'):
        break
```

---

### Post by Arndt on 2012-02-13
> **EmilHem said:**
> Hello. I'm wondering how I can use a while loop that's exited when the user presses 'e'.
I'm only intending to use this on Linux.

I'm using Python version 2.7.2+

Pseudocode:
```
while key_pressed('e') == False:
    do awesome stuff here
```

or
```
while True:
    do awesome stuff here
    if key_pressed('e'):
        break
```

Here is something I used a while ago. There may be cleaner solutions. I don't think termios exists on Windows.

```

import time
import sys
import select
import tty, termios

global old_settings

def setraw():
    global old_settings
    fd = sys.stdin.fileno()
    old_settings = termios.tcgetattr(fd)
    tty.setraw(sys.stdin.fileno())

def unsetraw():
    global old_settings
    fd = sys.stdin.fileno()
    termios.tcsetattr(fd, termios.TCSADRAIN, old_settings)


setraw()
timeout = 0

while True:
    print "hello\r"
    time.sleep(1)
    sel = select.select([sys.stdin], [], [], timeout)
    if sel[0]:
        c = sys.stdin.read(1)
        if ord(c) == 3:
            break
        print "%s\r" % c
        if c == 'e':
            break

unsetraw()

```

---

### Post by EmilHem on 2012-02-13
Thanks for the response.

I'm afraid that I'm getting this error when I run it:
```
Traceback (most recent call last):
  File "/home/emil/Documents/Python programming workspace/check_keyboard_keys.py", line 21, in <module>
    setraw()
  File "/home/emil/Documents/Python programming workspace/check_keyboard_keys.py", line 11, in setraw
    fd = sys.stdin.fileno()
AttributeError: 'PyShell' object has no attribute 'fileno'
```

I have python 2.7.2+ if it makes any difference.

---

### Post by ofnuts on 2012-02-14
> **EmilHem said:**
> Hello. I'm wondering how I can use a while loop that's exited when the user presses 'e'.
I'm only intending to use this on Linux.

I'm using Python version 2.7.2+

Pseudocode:
```
while key_pressed('e') == False:
    do awesome stuff here
```or
```
while True:
    do awesome stuff here
    if key_pressed('e'):
        break
```
Use select.select() with a short timeout? 

[http://docs.python.org/library/select.html](http://docs.python.org/library/select.html)

---

### Post by Arndt on 2012-02-14
> **EmilHem said:**
> Thanks for the response.

I'm afraid that I'm getting this error when I run it:
```
Traceback (most recent call last):
  File "/home/emil/Documents/Python programming workspace/check_keyboard_keys.py", line 21, in <module>
    setraw()
  File "/home/emil/Documents/Python programming workspace/check_keyboard_keys.py", line 11, in setraw
    fd = sys.stdin.fileno()
AttributeError: 'PyShell' object has no attribute 'fileno'
```

I have python 2.7.2+ if it makes any difference.

What exactly is PyShell? I haven't used it. My program works if I run it an ordinary terminal emulator. Maybe PyShell has some other methods that do the same job.

---

### Post by EmilHem on 2012-02-16
> **Arndt said:**
> What exactly is PyShell? I haven't used it. My program works if I run it an ordinary terminal emulator. Maybe PyShell has some other methods that do the same job.

Hmm. In IDLE it doesn't work I guess. That code does work in a normal terminal launching it with python [name of file.py]

In IDLE when I run it, it gives that error.

I think that that will do it. Thanks!

---

