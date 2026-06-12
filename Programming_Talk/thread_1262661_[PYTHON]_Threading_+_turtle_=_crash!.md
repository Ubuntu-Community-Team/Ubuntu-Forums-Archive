---
title: "[PYTHON] Threading + turtle = crash!"
date: 2009-09-10
forum: Programming Talk
---

### Post by The-ITu on 2009-09-10
hey people, 
i was wandering about runin more tham one prosses at a time and found a tutorial about a module name threading. I decided to test out what i learnt from it using the turtle module.
[img]http://i674.photobucket.com/albums/vv109/the-it/pythoncrash.jpg[/img]

here is the code:
```
import threading
import turtle as t
t.up()
t.goto(0, -200)
t.down()
r = t.clone()
t.color('green')
r.color('yellow')

class FirstThread(threading.Thread):
    def run(self):
        for x in range(5):
            t.circle(20, 180)
            t.left(180)
            t.circle(20, -180)
            t.left(180)

class SecondThread(threading.Thread):
    def run(self):
        for x in range(5):
            r.circle(20, -180)
            r.left(180)
            r.circle(20, 180)
            r.left(180)

FirstThread().start()
SecondThread().start()

raw_input()
```python crashes every time i run it.
each time at a difrent spot. 
but some times it doesnt crash and just gives some wier error somear in the middle.
only one (out of like 100 trys) did it make it to the end.

Any1 know how to fix this?
Thanks!!
The-ITu

---

