---
title: "python TK radio button help"
date: 2009-06-24
forum: Programming Talk
---

### Post by The-ITu on 2009-06-24
Hi, I have been a python programer for a while, however, I am fairly new to GUI programing.
I have been trying to think of a technique to create a multiple choice quiz on Tk but the radio button don't seem to change the  variable.

```
import Tkinter as tk
root = tk.Tk()

def call(par):
    if par == 'correct':
        lab2 = tk.Label(root, text='CORECT!!!!').grid(row=4)
    elif par == 'wrong':
        lab2 = tk.Label(root, text='of corse your wrong').grid(row=4)
        lab2 = tk.Label(root, text='how could you be so stupid?').grid(row=5)

correct  = False
rad = tk.Radiobutton(root, text='yes', variable=correct, value='correct')
rad2 = tk.Radiobutton(root, text='no', variable=correct, value='wrong')
lab = tk.Label(root, text='Is the maker awsome?')
btn = tk.Button(root, text='submit', command=lambda: call(correct))

lab.grid(row=0)
rad.grid(row=2, column=0)
rad2.grid(row=2, column=1)
btn.grid(row=3)

tk.mainloop()
```
Thanks for any help :)
The-IT(u)

---

### Post by asdfhjkla on 2009-06-24
To the best of my knowledge, Tkinter has to use an instance of IntVar, StringVar, BooleanVar or DoubleVar for the variable used by the radio buttons.

I've changed correct to an instance of BooleanVar (this has default value of False), changed the value= arguments of the radio buttons to True and False, and used the result of the get() method of the BooleanVar *correct* as the argument to the callback function.

[PHP]import Tkinter as tk
root = tk.Tk()

def call(par):
    if par:
        lab2 = tk.Label(root, text='CORECT!!!!').grid(row=4)
    else:
        lab2 = tk.Label(root, text='of corse your wrong').grid(row=4)
        lab2 = tk.Label(root, text='how could you be so stupid?').grid(row=5)

correct  = tk.BooleanVar()
rad = tk.Radiobutton(root, text='yes', variable=correct, value=True)
rad2 = tk.Radiobutton(root, text='no', variable=correct, value=False)
lab = tk.Label(root, text='Is the maker awsome?')
btn = tk.Button(root, text='submit', command=lambda: call(correct.get()))

lab.grid(row=0)
rad.grid(row=2, column=0)
rad2.grid(row=2, column=1)
btn.grid(row=3)

tk.mainloop()[/PHP]

---

### Post by The-ITu on 2009-06-24
o yes it works now. that you very much.
is seams as tho Tkinter does no accept python variable but only Tk variables.
thanks a bunch for that list of functions.
but may i ask, what is DoubleVar() for? (i know everything else)

---

### Post by asdfhjkla on 2009-06-24
No problem.

DoubleVar is for floating point numbers. [This]("http://effbot.org/tkinterbook/variable.htm") may be of interest.

---

### Post by The-ITu on 2009-06-25
thanks for the link.
but when you say floating value do you mean a variable with a float value, as in a number with a decimal point like 23.43?
sorry its just don't know what you mean by floating point.

---

### Post by asdfhjkla on 2009-06-25
Yeah that's what I meant :)

---

### Post by stevescripts on 2009-06-25
The-ITu -

As an avid user of tcl/Tk, and a frequent tinkerer with Python/Tkinter,
I personally find the following the most useful (for me) references:

[http://infohost.nmt.edu/tcc/help/pubs/tkinter/index.html](http://infohost.nmt.edu/tcc/help/pubs/tkinter/index.html)

[http://www.pythonware.com/library/tkinter/introduction/](http://www.pythonware.com/library/tkinter/introduction/)

Hope that you find these useful too.

Steve

---

