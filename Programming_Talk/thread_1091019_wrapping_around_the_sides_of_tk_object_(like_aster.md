---
title: "wrapping around the sides of tk object (like asteroids)"
date: 2009-03-08
forum: Programming Talk
---

### Post by kapok on 2009-03-08
i have to get the little green ovals i create to come up on the left side when they leave the right side, visa-versa, same with up and down.
here is the code:
```
from Tkinter import *
import time
import random
tk = Tk()
#################################################################
def update():
	enviornment.update()
#################################################################
def populate(x):
	for y in range(0,x):
		y1 = random.randrange(0,400)
		x1 = random.randrange(0,400)
		y2 = y1 - 10
		x2 = x1 - 10
		enviornment.create_oval(x1,y1,x2,y2,fill='green')
#################################################################
enviornment = Canvas(tk,width=400,height=400)
enviornment.pack()
update()
number_of_cells = 30
populate(number_of_cells)
while True:
	for x in range(1,number_of_cells+1):
		enviornment.move(x,random.randrange(-2,3),random.randrange(-2,3))
	time.sleep(0.01)
	update()

```

---

### Post by tneva82 on 2009-03-09
> **kapok said:**
> i have to get the little green ovals i create to come up on the left side when they leave the right side, visa-versa, same with up and down.

Well. Quick&dirty solution would be something like this(C code since I'm not even sure what language you use :D). Tried this on my darkGDK test project though I suppose you need bit better than this. Problem with this is that the object just dissapears :-/ Caused nasty surprises to me when my ship passed the border and asteroid appeared out of nowhere so to speak(crash boom!). 

```
	if(x>maximumX || x<-minimumX) {
		x=0-x;
	}
	if(y>maximumY || y<-minimumY) {
		y=0-y;
	}

```

---

### Post by kapok on 2009-03-09
it seems like that should work. :/
well, i did figure it out in my language (i use python) with the help of one of my teachers from school.
the code is as follows: (assuming this is in a while True type loop and it checks the if's every time whatever object moves.)
```
                if enviornment.coords(x)[0] < 0:
			enviornment.move(x,400,0)
		if enviornment.coords(x)[1] < 0:
			enviornment.move(x,0,400)
		if enviornment.coords(x)[0] > 400:
			enviornment.move(x,-400,0)
		if enviornment.coords(x)[1] > 400:
			enviornment.move(x,0,-400)
```
well i had to edit this because when i hit tab to indent it, the "post" was selected. then i hit enter. :/
anyway, object x is always an oval in this example, and enviornment.coords is an array like this: [x1,y1,x2,y2] of the coordinates of the oval.
x1,y1 is the leftmost vertex, so every time the coordinates of any object (they're moved one by one) exites the boundaries, it appears on the opposite side. this is tested and working. thanks for the input though.

---

