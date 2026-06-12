---
title: "Graphics/classes in Tkinter"
date: 2008-11-17
forum: Programming Talk
---

### Post by luke77 on 2008-11-17
Hi guys,

After a long day of much frustration teaching myself Tkinter in Python, I am here with a few questions I have been unable to resolve/understand. I appreciate any help or advice.

First question: This is the stripped down code for a Tkinter GUI which isolates my problem:
```

from Tkinter import *

WINDOWWIDTH=500
WINDOWHEIGHT=500


class App:    
     def __init__ (self,master):
        self.x=10
        self.y=10
        self.display = Frame(master, width=WINDOWWIDTH, 
height=WINDOWHEIGHT)
        self.canvas=Canvas(self.display, bg='blue')
               #Draw boxes, set up screen layout

        self.box1=self.canvas.drawBox()
        self.display.pack()
        self.canvas.pack()

    def drawBox(self):
        newbox=self.create_rectangle(self.x, self.y, self.x+70, 
self.y+70, width=5, fill='red')
   self.tag_bind(newbox, '<B1-Motion>', self.onDrag)
    return newbox

root= Tk()
app=App(root)
root.mainloop()
```

This should create a new box (self.box1) with parent self.canvas. It is bound to function self.onDrag, which I deleted from this code. However, when I try to run I keep getting the error "AttributeError: Canvas instance has no attribute 'drawBox'".I've tried deleting the return statement and just calling "self.canvas.drawBox(), with the same result. If I delete the drawBox function and just put the statements in "init", with no function call, it works correctly. I thought that by calling "self.canvas.drawBox()", I pass "self.canvas" 
to the function, so that in effect I am calling 
"newbox=self.canvas.create_rectangle(self.x, self.y, self.x+70, 
self.y+70, width=5, fill='red')". Clearly this is inaccurate because if I write "newbox=self.create_rectangle(self.x, self.y, self.x+70, self.y+70, width=5, fill='red')" in the constructor, it works correctly. Where am I thinking about this incorrectly?


Next, I am trying to bind an object or objects on the screen so that the user can click a button and set the latest object clicked (a ball, square, triangle, whatever) in motion. To do this I need to identify the latest object clicked on the canvas. Ive written the following function:

```
    def onClick(self,event):
        self.currx = event.x
        self.curry = event.y
        self.latest= event.widget
        
        self.move(self.latest, 10, 10)
```

For now, I've just set it up so that when a user clicks on the object it moves 10X10 pixels. Here is the function for adding a 
ball with this binding:
    ```
def drawBall(self,x=WINDOWWIDTH/4, y=WINDOWWIDTH/4, size=40, **kw):
        newball=self.create_oval(x-30, y-30, x+30, y+30, width=5, fill='black')
        self.tag_bind(newball, '<B1-Motion>', self.onDrag)
        self.tag_bind(newball, '<ButtonPress-1>', self.onClick)
```

I create the ball by calling:

```
app.drawBall(70,70,70,width=5, fill='black')

```

So when I click on an object, the object should be set as "self.latest", and then moved 10X10 pixels in the next line. When I run this, though, there is no movement. If I leave the rest of the code the same and change the move code to:

```
self.move(ALL, 10, 10)
```

all the objects are moved. So it seems that the problem has to do with setting self.latest as the current object. When I insert a print statement to output "self.latest", it prints an object ID of a bunch of numbers, so I'm at a loss as to why the object does not move.

Again, thanks for any help.

Luke

---

### Post by luke77 on 2008-11-19
Bump?

---

### Post by stevescripts on 2008-11-19
Does this help a bit?

[http://effbot.org/zone/tkinter-animation.htm](http://effbot.org/zone/tkinter-animation.htm)

---

### Post by wmcbrine on 2008-11-19
drawBox() is not a method of self.canvas, and it doesn't become one just by trying to call it as "self.canvas.drawBox()". You could either refer to self.canvas within drawBox(), or pass it as a parameter.

---

### Post by stevescripts on 2008-11-20
After finding a little time, a "brain-dead" simple script to move items on a canvas :

```

#!/usr/bin/python

from Tkinter import *

root = Tk()

root.title("Move it!")

root.resizable(0,0)

def callback(event):
	c.move(CURRENT, 10, 10)
	

c = Canvas(root, bg="white", width=200, height=200)

ball = c.create_oval(10, 10, 50, 50, fill="blue", tags="movable")

box = c.create_rectangle(50, 50, 75, 75, fill="red", tags="movable")

c.bind("<Button-1>", callback)

c.pack()

print c.gettags(ALL)

print c.coords(ball)

print c.coords(box)

root.mainloop()


```

Note the use of CURRENT.

Hope this helps.

Steve

---

### Post by luke77 on 2008-11-20
Thanks guys, this is very helpful.

---

