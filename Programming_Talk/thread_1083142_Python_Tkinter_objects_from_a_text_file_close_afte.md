---
title: "Python: Tkinter objects from a text file close after program runs."
date: 2009-02-28
forum: Programming Talk
---

### Post by kapok on 2009-02-28
If i create a canvas object from Tkinter by running code from a text file, how do I get it to stay open?

I am trying to write a program that takes simple commands(up, down, left, and right) to move objects around so I need the canvas created to stay open long enough to take commands. 

My code works fine when i enter it manually after typing 'python' into the console, because it waits for a key to be pressed.

But when i run the program from the text file, it instantly sees that no key is pressed, and terminates itself.

How do I get it to stay up after running it from a text file? 
Such simple questions are almost impossible to find in Python resources. :(

---

### Post by Barriehie on 2009-03-02
Post the code you've got and we can help figure it out.

Barrie

---

### Post by stevescripts on 2009-03-02
> **Barriehie said:**
> Post the code you've got and we can help figure it out.

Barrie

+1 on posting some code ....

In the meantime, maybe this helps a bit? 
```

#!/usr/bin/python

from Tkinter import *

root = Tk()

root.title("Move it!")

root.resizable(0,0)

def callback(event):
	c.move(CURRENT, 10, 10)

def north(event):
	c.move(ball, 0, -1)
	print c.coords(ball)

def south(event):
	c.move(ball, 0, 1)

def east(event):
	c.move(ball, -1, 0)

def west(event):
	c.move(ball, 1, 0)

c = Canvas(root, bg="white", width=200, height=200)

ball = c.create_oval(10, 10, 50, 50, fill="blue", tags="movable")


# bind the root window to the arrow keys...
root.bind("<Up>", north)
root.bind("<Down>", south)
root.bind("<Left>", east)
root.bind("<Right>", west)

c.pack()

root.mainloop()

```

Hope this helps a bit.

Steve

---

### Post by kapok on 2009-03-02
Here is the code:
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
def move(x, y):
	while True:
		canvas.bind_all('<KeyPress-Up>', move_triangle)
		canvas.bind_all('<KeyPress-Down>', move_triangle)
		canvas.bind_all('<KeyPress-Left>', move_triangle)
		canvas.bind_all('<KeyPress-Right>', move_triangle)
		canvas.move(1,x,y)
		tk.update()
		time.sleep(0.02)
move(0, 0)
	
```

I figured it out though. Thank you to stevescrips for that useful stuff.
In fact, very useful. The tutorial I learned from left out the fact that you can bind single objects to keys.

Perhaps I should just get some documentation and than experiment and teach myself.

I have another question: does Pygame still exist?
i've tried
```
sudo apt-get install pygame
sudo apt-get install python pygame
sudo apt-get install python-pygame
```
but to no avail.

---

### Post by kapok on 2009-03-04
bump

---

### Post by Barriehie on 2009-03-04
> **kapok said:**
> 
I have another question: does Pygame still exist?
i've tried
```
sudo apt-get install pygame
sudo apt-get install python pygame
sudo apt-get install python-pygame
```but to no avail.

Can't help with the key detection.  I've got a pygame app. that I have to launch from terminal before it opens the graphic and then I have to switch back to the terminal for the key catch to work.  TTY thing. ;)

In regards to python-pygame it is still around.  It's in the universe section and it's in synaptic, or, here's what I got from the cli:

```

sudo apt-get -s install python-pygame
password: *****
Reading package lists...
Building dependency tree...
Reading state information...
python-pygame is already the newest version.
The following packages were automatically installed and are no longer required:
  python-wxtools libaudclient1 libmowgli1 pychecker libmcs1 winpdb kiki
  python-wxglade
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```Barrie

---

### Post by kapok on 2009-03-05
thanks. 
it seems i already had it; the problem being i thought i didn't because it wouldn't initialize. 
i have it:
```
sudo apt-get install python-pygame
```
returns
```
kapok@kapok-desktop:~$ sudo apt-get install python-pygame
[sudo] password for kapok: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-pygame is already the newest version.
The following packages were automatically installed and are no longer required:
  libclucene0ldbl librdf0 librasqal0 redland-utils libstreamanalyzer0
  libstreams0 libraptor1 raptor-utils
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kapok@kapok-desktop:~$ 

```

but in python, i type:
```

import pygame, sys,os
from pygame.locals import *
pygame.init()
```

and nothing comes up. (it is supposed to return number of working modules, number of not working modules, while i receive a blank line without the >>> thing.

---

### Post by Can+~ on 2009-03-05
> but in python, i type:
```

import pygame, sys,os
from pygame.locals import *
pygame.init()
```

and nothing comes up. (it is supposed to return number of working modules, number of not working modules, while i receive a blank line without the >>> thing.

It usually doesn't output anything. If you do [FONT="Courier New"]import pygame[/FONT] and it doesn't raise an [FONT="Courier New"]ImportError[/FONT], then it's working.

Also, I recommend you doing
```
sudo apt-get autoremove
```

to remove all those orphaned packages.

---

### Post by kapok on 2009-03-05
well i did the autoremove thing.

```
Python 2.5.2 (r252:60911, Oct  5 2008, 19:24:49) 
[GCC 4.3.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import pygame
>>> pygame.init()


```

where do i go from here?
i can't use anything in pygame without python starting back up.

---

### Post by Can+~ on 2009-03-05
> **kapok said:**
> well i did the autoremove thing.

```
Python 2.5.2 (r252:60911, Oct  5 2008, 19:24:49) 
[GCC 4.3.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import pygame
>>> pygame.init()


```

where do i go from here?
i can't use anything in pygame without python starting back up.

Wait, are you using only the python interpreter? You know that you can write a "myscript.py" and run it with "python myscript.py", right?

Well, if you want to learn pygame, use the tutorial on it's website

[http://www.pygame.org/docs/](http://www.pygame.org/docs/)

---

### Post by kapok on 2009-03-06
i know; i've read that tutorial and run it from a script.
but it still doesn't even try to do anything.
i get nothing and no error messages.

---

