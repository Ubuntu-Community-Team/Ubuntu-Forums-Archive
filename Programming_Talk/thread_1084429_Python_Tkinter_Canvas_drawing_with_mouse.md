---
title: "Python Tkinter Canvas drawing with mouse"
date: 2009-03-02
forum: Programming Talk
---

### Post by Acapulco on 2009-03-02
Hello. I'm working on this project based on Python, and I need to be able to create a canvas so I can draw in it with the mouse. I haven't found any "put_pixel()" function or something similar, so how do you suggest I can do this? Basically I need a Paint program, just being able to clear the screen, erase, change pen colors, etc. 

I've thought of using lines, starting and ending in consecutive mouse positions, but then I would have to say something like "if mouse hasn't moved for the last half a second, start a new sequence of lines", right? any ideas?

Thanks!

---

### Post by stevescripts on 2009-03-02
Acapulco - as a simple place to start, see post #6 in this thread:

[http://ubuntuforums.org/showthread.php?t=1008390](http://ubuntuforums.org/showthread.php?t=1008390)

It's a start, let me know if you run into trouble building up your app from there.

Steve

---

### Post by stevescripts on 2009-03-02
Oops!!! My bad, that is the tcl/tk version - here goes in python:

```

#!/usr/bin/python

from Tkinter import *

root = Tk()

root.title("Simple Graph")

root.resizable(0,0)

points = []

spline = 0

tag1 = "theline"

def point(event):
	c.create_oval(event.x, event.y, event.x+1, event.y+1, fill="black")
	points.append(event.x)
	points.append(event.y)
	return points

def canxy(event):
	print event.x, event.y

def graph(event):
	global theline
	c.create_line(points, tags="theline")
	

def toggle(event):
	global spline
	if spline == 0:
		c.itemconfigure(tag1, smooth=1)
		spline = 1
	elif spline == 1:
		c.itemconfigure(tag1, smooth=0)
		spline = 0
	return spline


c = Canvas(root, bg="white", width=300, height= 300)

c.configure(cursor="crosshair")

c.pack()

c.bind("<Button-1>", point)

c.bind("<Button-3>", graph)

c.bind("<Button-2>", toggle)

root.mainloop()

```

Steve
(monday morning brainfart there ... ;) )

---

### Post by Acapulco on 2009-03-02
Hey great! That's 90% of what I was looking for :)

Thanks a lot.

Just one thing. Is there a way to configure the line so the bezier control points don't show up?

In short, I'm trying to "draw" with the mouse, so I would need to plot the path of the movement. So I poll my input device and when I have 3 points I create a bezier...right? then with the last one and 2 more, I create a new bezier and so on..right?

But how can I hide the control points so it looks like a smooth path?

Thanks again!

---

### Post by stevescripts on 2009-03-02
> **Acapulco said:**
> 
...
But how can I hide the control points so it looks like a smooth path?

Thanks again!

Hmm, I *thought* I posted something a few minutes back, but at the risk of a double post - here goes again ...

You can either delete the points after the curve is drawn, or re-configure them to be the same color as the canvas widget.

Steve
(glad to be of a little assistance)

---

### Post by Acapulco on 2009-03-02
Ahh. It works great now. Thanks again. :)

---

