---
title: "Converting a recursive function into a while loop"
date: 2009-03-01
forum: Programming Talk
---

### Post by kapok on 2009-03-01
Recursive functions have a limit to how many instances of them you can have on the stack at one time. I wrote a program in Python (which I have been at only a few days and am very impressed with thus far) which uses a recursive function to move a little triangle around the window created by the Tk object based upon which directional arrow you press. Here is the code.

```
from Tkinter import *
import time
tk = Tk()
canvas = Canvas(tk, width=400, height=400)
canvas.pack()
canvas.create_polygon(10, 10, 10, 60, 50, 35)
x = 0
y = 0
def move_triangle(event):
	if event.keysym == 'Up':
		move(0,-2)
	elif event.keysym == 'Down':
		move(0,2)
	elif event.keysym == 'Left':
		move(-2,0)
	elif event.keysym == 'Right':
		move(2,0)
def move(x,y):
	canvas.bind_all('<KeyPress-Up>', move_triangle)
	canvas.bind_all('<KeyPress-Down>', move_triangle)
	canvas.bind_all('<KeyPress-Left>', move_triangle)
	canvas.bind_all('<KeyPress-Right>', move_triangle)
	canvas.move(1,x,y)
	tk.update()
	time.sleep(0.02)
	move(x, y)
move(0,0)
	
```

The program terminates after about 20 seconds saying "Runtimeerror: maximum recursion depth has been exceeded. 

Is there any way to turn the move(x,y) function into a while loop so it would run forever?

---

### Post by NovaAesa on 2009-03-01
Maybe something like this:

```

from Tkinter import *
import time
tk = Tk()
canvas = Canvas(tk, width=400, height=400)
canvas.pack()
canvas.create_polygon(10, 10, 10, 60, 50, 35)
x = 0
y = 0
def move_triangle(event):
	if event.keysym == 'Up':
		move(0,-2)
	elif event.keysym == 'Down':
		move(0,2)
	elif event.keysym == 'Left':
		move(-2,0)
	elif event.keysym == 'Right':
		move(2,0)
def move(x,y):
    while true:
	canvas.bind_all('<KeyPress-Up>', move_triangle)
	canvas.bind_all('<KeyPress-Down>', move_triangle)
	canvas.bind_all('<KeyPress-Left>', move_triangle)
	canvas.bind_all('<KeyPress-Right>', move_triangle)
	canvas.move(1,x,y)
	tk.update()
	time.sleep(0.02)
move(0,0)

```

Note that I'm at a Windows PC atm and haven't tested it (at uni waiting for lecture to start) so it might not work. But at least that gives you something to start with.

---

### Post by monkeyking on 2009-03-01
use tail recursion, if you don't bother with the rewritting.

---

### Post by kapok on 2009-03-01
why coudn't i think of that on my own? x(

oh well.
thanks NovaAesa

---

### Post by CptPicard on 2009-03-01
> **monkeyking said:**
> use tail recursion, if you don't bother with the rewritting.

Only tail recursions can be rewritten into simple loops in the first place, and not all recursions are easily convertible into tail-recursive form (this example actually "almost" is though). If this is not the case, and you still want to use a loop, you need to use an explicit stack to replace the call stack.

Also, as Python doesn't do tailcall optimization, it doesn't help if your recursion is a tail-recursion...

---

