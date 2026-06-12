---
title: "Python Class problems"
date: 2008-03-02
forum: Programming Talk
---

### Post by willis on 2008-03-02
This has got to be a stupid mistake but I can't figure it out...

[PHP]
#! /usr/bin/python
import curses, traceback, sys

class map_object():
	char = "n"
	x = 0
	y = 0
	maxx = 0
	maxy = 0
	oldx = 0
	oldy = 0
	def __init__(self, x=0, y=0, maxx=0, maxy=0, char="n"):
		self.x = x
		self.y = y
		self.maxx = maxx
		self.maxy = maxy
		self.char = char
	def draw(self, screen, x=self.x, y=self.y):
		screen.addch(self.y,self.x,ord(self.char))
		screen.addch(self.oy,self.ox,ord(" "))
[/PHP]

Why does this return:
```

Traceback (most recent call last):
  File "tmp.py", line 5, in <module>
    class map_object():
  File "tmp.py", line 19, in map_object
    def draw(self, screen, x=self.x, y=self.y):
NameError: name 'self' is not defined

```

---

### Post by Can+~ on 2008-03-02
Once you call a function inside a class, it passes the argument self, THEN in that function you use the self, not before.

It would be something like:

```
#! /usr/bin/python
import curses, traceback, sys

class map_object():
    def __init__(self, x=0, y=0, maxx=0, maxy=0, char="n"):
        self.x = x
        self.y = y
        self.maxx = maxx
        self.maxy = maxy
        self.oldx = 0
        self.oldy = 0
        self.char = char
    def draw(self, screen):
        screen.addch(self.y,self.x,ord(self.char))
        screen.addch(self.oy,self.ox,ord(" "))  
```

The main advantage of having classes, is that you can define variables inside the class, referred to "self", then, you don't have to throw those variables around, if you need self.x, you just call, in that function, self.x.

Also, I removed the pre-variables. You don't need them actually. *edit* I forgot oldx,y

I would help you more with your script if you tell what is for.

---

### Post by willis on 2008-03-02
Ah ok so if I understand correctly it was the calling of the self.x and self.y in the arguments of the draw function which triggered the error.

Thanks a bunch.

---

### Post by Can+~ on 2008-03-02
You should probably read more about Classes, jumping on the Object Oriented programming side is quite difficult if you're just starting:

[http://docs.python.org/tut/node11.html](http://docs.python.org/tut/node11.html)

---

