---
title: "Tkinter Problem"
date: 2013-04-27
forum: Programming Talk
---

### Post by linuxonbute on 2013-04-27
I am trying to learn to do gui programming in python and am starting to familiarize myself with tkinter.
I have version 3.2 installed ( I think ) and have copied and pasted some code.
I modified one line:
```

        okButton = Button(self, text="Save")

```

to
```

 
       okButton = Button(self, text="Save", fg="red")

```

Without the change it works fine.
The full code is
```

#!/usr/bin/python




"""
ZetCode Tkinter tutorial


In this script, we use pack manager
to position two buttons in the
bottom right corner of the window. 


author: Jan Bodnar
last modified: December 2010
website: www.zetcode.com
"""


from Tkinter import Tk, RIGHT, BOTH, RAISED
from ttk import Frame, Button, Style




class Example(Frame):
  
    def __init__(self, parent):
        Frame.__init__(self, parent)   
         
        self.parent = parent
        
        self.initUI()
        
    def initUI(self):
      
        self.parent.title("Buttons")
        self.style = Style()
        self.style.theme_use("default")
        
        frame = Frame(self, relief=RAISED, borderwidth=5)
        frame.pack(fill=BOTH, expand=1)
        
        self.pack(fill=BOTH, expand=1)
        
        okButton = Button(self, text="Save", fg="red")
        okButton.pack(side = "top",padx=45, pady=5 )
        printButton = Button(self, text="Print")
        printButton.pack(padx=45, pady=5)
        closeButton = Button(self,  text="Close",  command=self.quit)
        closeButton.pack(padx=45, pady=5)




              


def main():
  
    root = Tk()
    root.geometry("300x200+300+300")
    app = Example(root)
    root.mainloop()  


if __name__ == '__main__':
    main()  

```

Now I get the following error:
 Traceback (most recent call last):  File "./buttons1.py", line 58, in <module>
    main()  
  File "./buttons1.py", line 54, in main
    app = Example(root)
  File "./buttons1.py", line 27, in __init__
    self.initUI()
  File "./buttons1.py", line 40, in initUI
    okButton = Button(self, text="Save", fg="red")
  File "/usr/lib/python2.7/lib-tk/ttk.py", line 614, in __init__
    Widget.__init__(self, master, "ttk::button", kw)
  File "/usr/lib/python2.7/lib-tk/ttk.py", line 560, in __init__
    Tkinter.Widget.__init__(self, master, widgetname, kw=kw)
  File "/usr/lib/python2.7/lib-tk/Tkinter.py", line 1977, in __init__
    (widgetName, self._w) + extra + self._options(cnf))
_tkinter.TclError: unknown option "-fg"

Can anyone help please?
tia

---

### Post by alan9800 on 2013-04-27
as explained [here]("http://docs.python.org/2.7/library/ttk.html#using-ttk"), it would be preferable to use the following code```
from Tkinter import *
from ttk import *
```BTW, you're using python 2.7, as shown in these two error messages> File "/usr/lib/python2.7/lib-tk/ttk.py", line 614, in __init__
  File "/usr/lib/python2.7/lib-tk/ttk.py", line 560, in __init__

---

### Post by linuxonbute on 2013-04-27
> **alan9800 said:**
> as explained [here]("http://docs.python.org/2.7/library/ttk.html#using-ttk"), it would be preferable to use the following code```
from Tkinter import *
from ttk import *
```BTW, you're using python 2.7, as shown in these two error messages
Thanks for the suggestions and the link.
i tried the import changes but I still get the same error. I meant it was Tkinter 3.2  I removed that and installed the 2.7 version but again I get the same error.
I copied and pasted some of the examples from the link you provided and they work fine. I will study that information and try more there. I guess I will be back with more questions;)

---

### Post by alan9800 on 2013-04-27
only one more thing: keep in mind that in python 3.2 the Tkinter module has been renamed tkinter (with lowercase "t"), hence pay attention to which version of python you're using  when you invoke that module.

---

### Post by linuxonbute on 2013-04-28
Thanks for the heads up.
I found I still got an error until I changed it to:
```

import Tkinter
import ttk

```
which I found since I have been looking here [http://docs.python.org/2.7/library/ttk.html#using-ttk](http://docs.python.org/2.7/library/ttk.html#using-ttk)

---

### Post by linuxonbute on 2013-04-29
I have now found another site: [http://www.pythonware.com/library/tkinter/introduction/index.htm]("http://www.pythonware.com/library/tkinter/introduction/x5453-patterns.htm")
which seems to be very good.
I have put together the following code just to try some of it out and, although it is quite poor in itself, I thought it might be worth posting it here for others just as new to this as i am to play with.

```

#!/usr/bin/python
from Tkinter import *
import ttk


root = Tk()

root.geometry("600x480+400+120") # width, height, x position, y position (of top left corner)


style = ttk.Style()


ttk.Style().configure("TButton", padding=6, relief="flat", background="#ccc")


style.map("B.TButton",
    foreground=[('pressed', 'blue'), ('active', 'red')],
    background=[('pressed', '!disabled', 'grey'), ('active', 'white')]
    )


style.map("C.TButton",
    foreground=[('pressed', 'red'), ('active', 'blue')],
    background=[('pressed', '!disabled', 'green'), ('active', 'white')]
    )

#String variables and their initial text
myTextx=StringVar()
myTexty=StringVar()
myTextx.set("Hello")
myTexty.set("World")



# update of content of strings
def callback(event):
    myTextx.set(event.x)
    myTexty.set(event.y)

# click mouse button inside this frame to update values in myTextx and myTexty ( not on buttons within frame )
frame = Frame(root, width=500, height=300, relief=RAISED, borderwidth=5)
frame.bind("<Button-1>", callback)
frame.pack()


btn = ttk.Button(text="Sample")
btn.pack()


colored_btn = ttk.Button(text="Test", style="C.TButton").pack(padx=45, pady=5)
btn1 = ttk.Button(text="Hello").pack()

#click btn2 to close program - using the quit command
btn2 = ttk.Button(text="Goodbye", style="B.TButton", command=quit).pack(padx=45, pady=5)


redbutton = Button(frame, text="Red", fg="red2")
redbutton.pack(side = LEFT , padx=5, pady=25)


greenbutton = Button(frame, text="Green", fg="green4")
greenbutton.pack(side = LEFT ,padx=5, pady=25 )


bluebutton = Button(frame, text="Blue", fg="blue")
bluebutton.pack( side = LEFT , padx=5, pady=25)

# values displayed are updated automatically 
w = Label(root, textvariable=myTextx).pack()
x = Label(root, textvariable=myTexty).pack()


listbox = Listbox(root)
listbox.insert(END, "a list entry")
    
for item in ["one", "two", "three", "four"]:
    listbox.insert(END, item)


listbox.pack()




root.mainloop()

```

i hope this is of some use to others.

---

### Post by alan9800 on 2013-04-30
if I have rightly understood your code, it seems preferable to import the whole ttk module instead of its functions and methods.
This is however slightly different from what is suggested in the [Python library]("http://docs.python.org/release/2.7.3/library/ttk.html#using-ttk").

---

### Post by linuxonbute on 2013-04-30
if instead of
```

import ttk

```

I do
```

from ttk import *

```

I get 

> 
Traceback (most recent call last):
  File "./kinter1.py", line 8, in <module>
    style = ttk.Style()
NameError: name 'ttk' is not defined


As I have said I am a total beginner at this.
I am using python 2.7.3

---

### Post by alan9800 on 2013-04-30
if you write```
import ttk
```then you have to write```
style = ttk.Style()
```but if you write```
from ttk import *
```then you can write```
style = Style()
```without "ttk." since all functions and methods of ttk module have already been imported.

---

### Post by linuxonbute on 2013-04-30
Great thanks again. All working now. It's obvious I am new to this isn't it:)
I'm also old (69) and slow.

So to update my code for clarity:
```

#!/usr/bin/python

from Tkinter import *  # in python 3.x this would be from tkinter import *
from ttk import *


root = Tk()
root.geometry("600x480+400+120")

style = Style()

Style().configure("TButton", padding=6, relief="flat", background="#ccc")

style.map("B.TButton",
    foreground=[('pressed', 'green'), ('active', 'blue'), ('!pressed', 'red')],
    background=[('pressed', '!disabled', 'grey'), ('active', 'white')]
    )


style.map("C.TButton",
    foreground=[('pressed', 'red'), ('active', 'blue')],
    background=[('pressed', '!disabled', 'green'), ('active', 'white')]
    )


style.map("D.TButton",
    foreground=[('pressed', 'brown'), ('active', 'blue'), ('!pressed', 'green')],
    background=[('pressed', '!disabled', 'grey'), ('active', 'white')]
    )


style.map("E.TButton",
    foreground=[('pressed', 'yellow'), ('active', 'purple'), ('!pressed', 'blue')],
    background=[('pressed', '!disabled', 'grey'), ('active', 'white')]
    )


# String variables and their initial text 
myTextx=StringVar()
myTexty=StringVar()
myTextx.set("Hello")
myTexty.set("World")


# update of content of strings when mouse clicked within frame
def callback(event):
    myTextx.set(event.x)
    myTexty.set(event.y)


def hello():
    print "hello!"


# click mouse button inside this frame to update values in myTextx and myTexty ( not on buttons within frame )
frame = Frame(root, width=500, height=300, relief=RAISED, borderwidth=5)
frame.bind("<Button-1>", callback)
frame.pack()

btn = Button(text="Sample")
btn.pack()

colored_btn = Button(text="Test", style="C.TButton").pack(padx=45, pady=5)
btn1 = Button(text="Hello").pack()

#click btn2 to close program - using the quit command
btn2 = Button(text="Goodbye", style="B.TButton", command=quit).pack(padx=45, pady=5)


redbutton = Button(frame, text="Red", style="B.TButton")
redbutton.pack(side = LEFT , padx=5, pady=25)


greenbutton = Button(frame, text="Green", style="D.TButton")
greenbutton.pack(side = LEFT ,padx=5, pady=25 )


bluebutton = Button(frame, text="Blue", style="E.TButton")
bluebutton.pack( side = LEFT , padx=5, pady=25)


# values updated automatically
w = Label(root, textvariable=myTextx).pack()
x = Label(root, textvariable=myTexty).pack()


listbox = Listbox(root)
listbox.insert(END, "a list entry")
    
for item in ["one", "two", "three", "four"]:
    listbox.insert(END, item)


listbox.pack()


# create a toplevel menu
menubar = Menu(root)
menubar.add_command(label="Hello!", command=hello)
menubar.add_command(label="Quit!", command=root.quit)


# display the menu
root.config(menu=menubar)


root.mainloop()

```

---

