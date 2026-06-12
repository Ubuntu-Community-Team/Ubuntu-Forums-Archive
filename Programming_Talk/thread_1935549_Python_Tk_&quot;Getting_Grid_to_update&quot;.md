---
title: "Python Tk &quot;Getting Grid to update&quot;"
date: 2012-03-04
forum: Programming Talk
---

### Post by markmandp on 2012-03-04
To get to work in the morning, I can take one of five buses. I want to write a program that gets the bus arrival times, and then posts them to Frames in Tk. I was the frame with the bus arriving soonest to go to the first column first row in Tk. 
 
To get me started on this process, I modified an example from [http://www.tkdocs.com/tutorial/grid.html](http://www.tkdocs.com/tutorial/grid.html)
 
I modified the example by adding two extra labels at the bottom of the screen. Then, i added a function that switches the labels (i.e. label1 starts on the 4th row, but when the "Okay" button is pushed, it goes to the 5th row).
 
Am I missing something fundamental? Is there something about Tk and the Grid geometry manager that prevents you from moving widgets around a window once they have been placed? Any help would be appreciated.
 
my code:
 
[PHP] 
from tkinter import *
from tkinter import ttk
root = Tk() #sets the parent
content = ttk.Frame(root)
frame = ttk.Frame(content, borderwidth=5, relief="sunken", width=200, height=100)
namelbl = ttk.Label(content, text="Name")
name = ttk.Entry(content, text="trust")
onevar = BooleanVar()
twovar = BooleanVar()
threevar = BooleanVar()
onevar.set(True)
twovar.set(False)
threevar.set(True)
 
namelbl2=ttk.Label(content, text="Name 1")
namelbl3=ttk.Label(content, text="Name 2")
x1=4
x2=5
 
def switch(x1,x2):
x11 = x1
x22 = x2
x1 = x22
x2 = x11
namelbl2.grid(column=0,row=x1,columnspan=5)
namelbl3.grid(column=0,row=x2,columnspan=5)
return x1,x2
 
one = ttk.Checkbutton(content, text="One", variable=onevar, onvalue=True)
two = ttk.Checkbutton(content, text="Two", variable=twovar, onvalue=True)
three = ttk.Checkbutton(content, text="Three", variable=threevar, onvalue=True)
ok = ttk.Button(content, text="Okay",command=switch(x1,x2))
cancel = ttk.Button(content, text="Cancel")
content.grid(column=0, row=0)
frame.grid(column=0, row=0, columnspan=3, rowspan=2)
namelbl.grid(column=3, row=0, columnspan=2)
name.grid(column=3, row=1, columnspan=2)
one.grid(column=0, row=3)
two.grid(column=1, row=3)
three.grid(column=2, row=3)
ok.grid(column=3, row=3)
cancel.grid(column=4, row=3)
 
namelbl2.grid(column=0,row=x1,columnspan=5)
namelbl3.grid(column=0,row=x2,columnspan=5)
 
root.mainloop()
[/PHP]

---

### Post by PeterP24 on 2012-03-06
Here is a thought: You have two labels. Would it suit you to modify the program in order to switch the strings of the labels? It will give the same effect - the labels would appear to change place when in fact their content is changed between them. As for actually changing two widgets (maybe two buttons?) I would actually suggest using .grid_forget() method on the widgets, then calling grid method with the appropriate settings for each widget. 

Here is the first solution (changing the strings of the labels - not the label widget themselves):
```
from tkinter import *
from tkinter import ttk
root = Tk() #sets the parent
content = ttk.Frame(root)
frame = ttk.Frame(content, borderwidth=5, relief="sunken", width=200, height=100)
namelbl = ttk.Label(content, text="Name")
name = ttk.Entry(content, text="trust")
onevar = BooleanVar()
twovar = BooleanVar()
threevar = BooleanVar()
onevar.set(True)
twovar.set(False)
threevar.set(True)

name1=StringVar()   # changed here
name2=StringVar()   # changed here

name1.set("Name 1") # changed here
name2.set("Name 2") # changed here
 
namelbl2=ttk.Label(content, textvariable=name1) # changed here
namelbl3=ttk.Label(content, textvariable=name2) # changed here
x1=4
x2=5
 
def switch():           # changed here (all the function)
    aux = name1.get()
    name1.set(name2.get())
    name2.set(aux)
    namelbl2.update_idletasks()
    namelbl3.update_idletasks()
 
one = ttk.Checkbutton(content, text="One", variable=onevar, onvalue=True)
two = ttk.Checkbutton(content, text="Two", variable=twovar, onvalue=True)
three = ttk.Checkbutton(content, text="Three", variable=threevar, onvalue=True)
ok = ttk.Button(content, text="Okay",command=switch)  # changed here - use functools to pass a function with parameters
cancel = ttk.Button(content, text="Cancel")
content.grid(column=0, row=0)
frame.grid(column=0, row=0, columnspan=3, rowspan=2)
namelbl.grid(column=3, row=0, columnspan=2)
name.grid(column=3, row=1, columnspan=2)
one.grid(column=0, row=3)
two.grid(column=1, row=3)
three.grid(column=2, row=3)
ok.grid(column=3, row=3)
cancel.grid(column=4, row=3)
 
namelbl2.grid(column=0,row=x1,columnspan=5)
namelbl3.grid(column=0,row=x2,columnspan=5)
 
root.mainloop()
```

The second solution - changing the widgets position:

```
from tkinter import *
from tkinter import ttk
root = Tk() #sets the parent
content = ttk.Frame(root)
frame = ttk.Frame(content, borderwidth=5, relief="sunken", width=200, height=100)
namelbl = ttk.Label(content, text="Name")
name = ttk.Entry(content, text="trust")
onevar = BooleanVar()
twovar = BooleanVar()
threevar = BooleanVar()
onevar.set(True)
twovar.set(False)
threevar.set(True)
 
namelbl2=ttk.Label(content, text="Name 1")
namelbl3=ttk.Label(content, text="Name 2")
x1=4  
x2=5 
 
def switch():  # changed here (all the function body)
    global x1
    global x2
    aux = x1
    x1 = x2
    x2 = aux

    namelbl2.grid_forget()
    namelbl3.grid_forget()
    
    namelbl2.grid(column=0,row=x1,columnspan=5)
    namelbl3.grid(column=0,row=x2,columnspan=5)

    namelbl2.update_idletasks()
    namelbl3.update_idletasks()

    return x1,x2
 
one = ttk.Checkbutton(content, text="One", variable=onevar, onvalue=True)
two = ttk.Checkbutton(content, text="Two", variable=twovar, onvalue=True)
three = ttk.Checkbutton(content, text="Three", variable=threevar, onvalue=True)
ok = ttk.Button(content, text="Okay",command=switch) # changed here
cancel = ttk.Button(content, text="Cancel")
content.grid(column=0, row=0)
frame.grid(column=0, row=0, columnspan=3, rowspan=2)
namelbl.grid(column=3, row=0, columnspan=2)
name.grid(column=3, row=1, columnspan=2)
one.grid(column=0, row=3)
two.grid(column=1, row=3)
three.grid(column=2, row=3)
ok.grid(column=3, row=3)
cancel.grid(column=4, row=3)
 
namelbl2.grid(column=0,row=x1,columnspan=5)
namelbl3.grid(column=0,row=x2,columnspan=5)
 
root.mainloop()
```

---

