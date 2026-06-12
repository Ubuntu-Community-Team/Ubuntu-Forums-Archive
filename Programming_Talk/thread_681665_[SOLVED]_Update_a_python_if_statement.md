---
title: "[SOLVED] Update a python if statement?"
date: 2008-01-29
forum: Programming Talk
---

### Post by banewman on 2008-01-29
As a learning project I'm making a countdown timer that closes when it reaches zero. The problem I'm having is I can't find out how to update the if statement as the program counts down.

```
#!/usr/bin/env python

from Tkinter import *

from itertools import count

#Been trying to place if here#
def start_counter(label):
    x = int(ent.get())
    counter = count(-x)
    def update_func():
         label.config(text=str(-counter.next()))
         label.after(1000, update_func) # 1000ms
    update_func()

root = Tk()
root.title("Countdown Timer")

def show():
    label = Label(root, width=15,bg="white",fg="red", font = ("arial", 20, "bold"))
    label.pack()
    start_counter(label)    

ent = Entry(root,bg="white", width = 5)
ent.pack()

b1 = Button(root, text='Start', width=30, command=show)
b1.pack()

b = Button(root, text='Stop', width=30, command=root.destroy)
b.pack()

ent.focus()

root.mainloop()
```

Any help appreciated

---

### Post by pmasiar on 2008-01-29
confused: update the if statement? I use text editor for that.

---

### Post by banewman on 2008-01-29
I need to place a conditional statement in this part of the code and the  if statement has to be updated each second because the value it checks changes each second - if I'm approaching it right.
The if statement checks the value each second to see if it equals zero.


```
#Been trying to place if here#
def start_counter(label):
    x = int(ent.get())
    counter = count(-x)
    def update_func():
         label.config(text=str(-counter.next()))
         label.after(1000, update_func) # 1000ms
    if counter <= 0       <<<<<Doesn't work
        root.destroy()
    update_func()
```

---

### Post by Ramses de Norre on 2008-01-29
Sounds like you're in need of a *while* statement instead of *if*.

---

### Post by pmasiar on 2008-01-29
Two style comments:
1) "from Tkinter import *" is bad habit, you are polluting your namespace with Guido knows what. Import specific names like your second import.

2) You define update_func() function inside of start_counter() function. Smells like bad design?

Mind you I never used Tkinter and have no clue how to use it, but it looks strange.

---

### Post by popch on 2008-01-29
Please forgive me for being blunt. 

The way you state your question and the way your program is written appear to indicate that you just have started learning how to program. 

That's cool. 

However, I think that a good tutorial would be more useful for you at this point in time than some disconnected suggestions by members in this forum, no matter how helpful they are trying to be.

The sticky notes at the start of this forum contain lots of pointers for people who want to start learning how to program.

---

### Post by pmasiar on 2008-01-29
Exactly. And if you just learn basics, stay away from GUI for a while, in plain text/commandline everything is much simpler.

See wiki in my sig for free books and training tasks.

---

### Post by Martin Witte on 2008-01-29
> **pmasiar said:**
> Two style comments:
1) "from Tkinter import *" is bad habit, you are polluting your namespace with Guido knows what. Import specific names like your second import.

2) You define update_func() function inside of start_counter() function. Smells like bad design?

Mind you I never used Tkinter and have no clue how to use it, but it looks strange.

about your first style comment: 9 out of 10 your right about namespace polution, Tkinter is an exception to this rule, see e.g. [http://docs.python.org/lib/node686.html](http://docs.python.org/lib/node686.html)

---

### Post by pmasiar on 2008-01-29
1) Zen of the Python says: "exceptions are not important enough to break the rules"
2) How would you know which names were imported from Tkinter, so you will not redefine them by mistake? I remember such error happen once (in Perl, and not to me) and it was not pretty. VERY confusing error messages.

Of course, you are free to write code as you wish - and then have fun debugging  it :-)

---

### Post by LaRoza on 2008-01-29
> **pmasiar said:**
> 
Of course, you are free to write code as you wish - and then have fun debugging  it :-)

You can show a programming good habits, but you can't make her do it.

(I'll admit, I tried using Tkinter without import *, and it is a pain. I use "import Tkinter as tk" or something now)

---

### Post by banewman on 2008-01-31
Thanks to all that were interested.
I've got it working well now.
:)
```
#!/usr/bin/env python

from Tkinter import *
from itertools import count

def countdown(lab):
    n = int(ent.get())
    counter = count(-n)
    def running():
        a = (-counter.next())
        if a > 0 :
            lab.config(text=str(a))
            lab.after(1000, running)
        else:
            root.destroy()
    running()

def outp():
    countdown(lab)

root = Tk()

ent = Entry(root, bg = "white", width = 10)
ent.pack()

b1 = Button(root, width = 30, text = "Start", command = outp)
b1.pack()
b2 = Button(root, width = 30, text = "Quit", command = root.destroy)
b2.pack()

lab = Label(root, width = 5, bg = "white", font = ("arial",16,"bold"), \
          fg = "red")
lab.pack()

ent.focus()

root.mainloop()
```

---

