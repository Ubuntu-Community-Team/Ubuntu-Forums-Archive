---
title: "Basic python-tkinter question"
date: 2008-05-14
forum: Programming Talk
---

### Post by bg11 on 2008-05-14
I'm trying to follow an online tutorial for python/tkinter (from [http://www.greenteapress.com/thinkpython/html/book020.html#toc196](http://www.greenteapress.com/thinkpython/html/book020.html#toc196)), but am having trouble with a particular part.

The following runs
```

from Gui import *
g = Gui()
g.title('Title')
canvas = g.ca(width=500, height=500)
canvas.config(bg='white')
item = canvas.circle(0,0, 100, fill='red')
print type(canvas), type(item)

```
but the output indicates that item is an integer.  The relevant method in Tkinter.py does seem to return an integer:
```

def _create(self, itemType, args, kw): # Args: (val, val, ..., cnf={})
        """Internal function."""
        args = _flatten(args)
        cnf = args[-1]
        if type(cnf) in (DictionaryType, TupleType):
            args = args[:-1]
        else:
            cnf = {}
        return getint(self.tk.call(
            self._w, 'create', itemType,
            *(args + self._options(cnf, kw))))

```
(Gui.py can be found at [http://allendowney.com/sd07spr/code/Gui.py](http://allendowney.com/sd07spr/code/Gui.py).)

So when I add the following to change the circle:
```

item.config(fill='yellow', outline='orange', width=100)

```

I get the error:
```

item.config(fill='yellow', outline='orange', width=100)
AttributeError: 'int' object has no attribute 'config'

```

So, how can I change the circle in a manner that the tutorial instructs?

Btw, I'm a beginner in python and so would appreciate no "lolz @ teh stoopid noobz" responses.

---

### Post by celljak on 2008-05-15
> **bg11 said:**
> I'm trying to follow an online tutorial for python/tkinter (from [http://www.greenteapress.com/thinkpython/html/book020.html#toc196](http://www.greenteapress.com/thinkpython/html/book020.html#toc196)), but am having trouble with a particular part.

The following runs
```

from Gui import *
g = Gui()
g.title('Title')
canvas = g.ca(width=500, height=500)
canvas.config(bg='white')
item = canvas.circle(0,0, 100, fill='red')
print type(canvas), type(item)

```
but the output indicates that item is an integer.  The relevant method in Tkinter.py does seem to return an integer:
```

def _create(self, itemType, args, kw): # Args: (val, val, ..., cnf={})
        """Internal function."""
        args = _flatten(args)
        cnf = args[-1]
        if type(cnf) in (DictionaryType, TupleType):
            args = args[:-1]
        else:
            cnf = {}
        return getint(self.tk.call(
            self._w, 'create', itemType,
            *(args + self._options(cnf, kw))))

```
(Gui.py can be found at [http://allendowney.com/sd07spr/code/Gui.py](http://allendowney.com/sd07spr/code/Gui.py).)

So when I add the following to change the circle:
```

item.config(fill='yellow', outline='orange', width=100)

```

I get the error:
```

item.config(fill='yellow', outline='orange', width=100)
AttributeError: 'int' object has no attribute 'config'

```

So, how can I change the circle in a manner that the tutorial instructs?

Btw, I'm a beginner in python and so would appreciate no "lolz @ teh stoopid noobz" responses.


Don't you need a ":" after def _create(self, itemType, args, kw): # Args: (val, val, ..., cnf={}) ?

So

def _create(self, itemType, args, kw): # Args: (val, val, ..., cnf={}):
        """Internal function."""

...
...
...


I"m rather new to python to. not sure if this would cause the error.

---

### Post by bg11 on 2008-05-15
> **celljak said:**
> Don't you need a ":" after def _create(self, itemType, args, kw): # Args: (val, val, ..., cnf={}) ?

So

def _create(self, itemType, args, kw): # Args: (val, val, ..., cnf={}):
        """Internal function."""


That's not it.  The '#' character is used for commenting, so everything proceeding it on the same line is ignored by the interpreter.

---

### Post by jjmurph on 2008-05-15
The canvas create methods return a handle to the object created, not the object itself.  You want to change that line to:
```
canvas.itemconfig(item,fill='yellow', outline='orange', width=100)
```

---

### Post by stevescripts on 2008-05-15
jjmurph - nicecly explained (and well ahead of me .. I made a post (I thought) about a half-hour ago...

OP - if you want to use a wrapper around Tkinter, take a look at easygui.  At some point, it might be a good idea to spend at least some time, becoming familiar with Tkinter.

Since I spent a few minutes on a simple script, you may find it a bit useful/infomational :

```

#!/usr/bin/python

from Tkinter import *

g = Tk()

g.title('Change it')

c = Canvas(width=200, height=200)

c.configure(bg='white')

def mycommand():
	c.itemconfigure(tagOrId='reddot', fill='blue')

item = c.create_oval(10,10,100,100, fill='red', tags='reddot')

b = Button(text='test', width = 20, command=mycommand)

b.pack(fill='x')

c.pack()

g.mainloop()

```

Note the use of "tags" and "tagOrId" , and the callback command on the button widget.  In this case, if there were more than one item on the canvas, with the *same* tag - the button would change the color of all of those items, which can be quite useful at time.

Hope someone finds this somewhat helpful.

Steve

---

### Post by bg11 on 2008-05-16
Thanks to all who responded.

Re: jjmurph
Cheers, that worked perfectly.

Re: stevescripts
The tutorial I'm using treats tkinter as an introductory, beginner's level tool to using gui libraries with python.  So I was under the impression that there're better gui libs out there.  Do you consider tkinter to be worth learning in greater detail?  If so, do you know where I can find good tutorials for it?

What do other people think?

---

### Post by stevescripts on 2008-05-16
bg11 -

I do most of my programming in tcl, using the Tk widgets.  Yes, I certainly consider Tkinter worth learning, among other reasons, it is still the defacto standard for Python...  I am trying to get comfortable with Python, and Tkinter, for mostly personal information/satisfaction.

I have links to what I consider better information on my machine at home, will post them tonight.  Again, easygui is a better, more complete wrapper.

Steve

---

### Post by LaRoza on 2008-05-16
> **bg11 said:**
> 
The tutorial I'm using treats tkinter as an introductory, beginner's level tool to using gui libraries with python.  So I was under the impression that there're better gui libs out there.  Do you consider tkinter to be worth learning in greater detail?  If so, do you know where I can find good tutorials for it?

What do other people think?

Tkinter is the standard GUI toolkit for Python. It is often used in beginner tutorials because it is shipped with standard Python.

It isn't just for beginners. There are better looking GUI toolkits. In reality, the principles are the same, so learning one doesn't hinder using another. My wiki might have enough information for you.

---

### Post by bg11 on 2008-05-17
Thanks for the advice everyone, feel free to post tkinter tutorial links.

---

### Post by stevescripts on 2008-05-18
Here are a few I have found useful:

[http://www.pythonware.com/library/tkinter/introduction/]("http://www.pythonware.com/library/tkinter/introduction/")

[http://www.python.org/doc/life-preserver/]("http://www.python.org/doc/life-preserver/")

[http://infohost.nmt.edu/tcc/help/pubs/tkinter/]("http://infohost.nmt.edu/tcc/help/pubs/tkinter/")

I especially find the one from New Mexico Tech helpful, but, then again, I have many years of experience with Tk ... ;)

Steve
(who apologizes for taking this much time to get around to it ... also don't overlook LaRoza's website)

---

### Post by LaRoza on 2008-05-18
> **stevescripts said:**
> 
Steve
(who apologizes for taking this much time to get around to it ... also don't overlook LaRoza's website)

I didn't have the python.org one on my wiki, added. The other two were already there. 

Thanks.

---

