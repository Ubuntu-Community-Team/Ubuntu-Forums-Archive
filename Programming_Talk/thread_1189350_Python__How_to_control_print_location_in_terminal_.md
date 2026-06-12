---
title: "Python : How to control print location in terminal ??!!"
date: 2009-06-16
forum: Programming Talk
---

### Post by Ahmedmb on 2009-06-16
:p Hi All

i need to print countdown timer but i need it to print in same line 
not like this:
01:22
01:21
01:20

how i move the cursor and print in same location >??
:) THX

---

### Post by Can+~ on 2009-06-16
Easiest way?
[http://en.wikipedia.org/wiki/Carriage_return](http://en.wikipedia.org/wiki/Carriage_return)

```
print "I hate carriage return\rI love",
```

Use the "," to avoid the python automatic newline.

Or if you already jumped into python3:

```
print("I hate carriage return\rI love", end="")
```

---

### Post by unutbu on 2009-06-16
[PHP]#!/usr/bin/env python
from time import sleep
import sys
for x in range(10):
    print '\r%s'%x,
    sys.stdout.flush()
    sleep(1)
[/PHP]
You'll need to flush the output too...

---

### Post by fr4nko on 2009-06-16
The '\r' tip is a good one. Just for information, if you want a full control of your terminal display you can use the [curses]("http://docs.python.org/howto/curses.html") module.

---

### Post by Can+~ on 2009-06-16
Pair it with string multiplication to create a loading bar:

[PHP]#!/usr/bin/env python
from time import sleep
import sys

for x in range(100):
    print '\rDownloading: %s (%d%%)' % ("|"*(x/2), x),
    sys.stdout.flush()
    sleep(0.1)  [/PHP]

(Remember that "hello "*3 = "hello hello hello ")

---

### Post by Ahmedmb on 2009-06-17
THX All :p

---

