---
title: "Conceptual question"
date: 2008-10-27
forum: Programming Talk
---

### Post by luke77 on 2008-10-27
No specific problem here, I'm just having problems wrapping my head around the following. I'm new to programming and the whole concept of classes is taking some getting used to, but I'm doing better...anyways, here's my question:

What is the difference between the following:

```
from Tkinter import *


class App(Frame):

    def __init__(self,parent):

        Frame.__init__(self, parent)

root=Tk()

app=App(root)

root.mainloop()
```

and:


```
from Tkinter import *


class App:

    def __init__(self,parent):

        self=Frame(self, parent)

root=Tk()

app=App(root)

root.mainloop()
```


It seems like they should be the same but I'm not sure. Also, when implementing Tkinter programs I'm finding that some people pass Frame as the parent of the main class (App in this example) and some do not. Is there a particular reason for this?

Thanks,
Luke

---

### Post by pmasiar on 2008-10-27
class App(Frame) - inherits from class Frame. Other one does not.

If it is just OOP mumbo-jumbo which does not make sense, relax: you have exactly right! ;-)

IMHO beginner is much better off focusing on learning basics of programming "old way" - procedural, and possibly using existing OO classes, but not to worry defining your own. Most of what you need from a class can be provided by dictionary.

Python is not Java, you can program without OO, making beginner's life much simpler, so enjoy it! 8-)

---

### Post by stevescripts on 2008-10-28
> **pmasiar said:**
> 
...
Python is not Java, you can program without OO, making beginner's life much simpler, so enjoy it! 8-)

+1, Big Time.

Note, that this also applies to the use of Tkinter, although
nearly all of the examples that you run into seem to use OO.

Also, the flexibility of Tk/Tkinter, make it possible using the
pack and grid managers for widgets (and in *rare* cases using
place ..) to make nice looking apps without using frames at times.

(Frames are quite useful as containers, and can lead to easier
code re-use)


Steve
(will try to post a decent example of what I mean, as time/energy
allow)

---

### Post by nvteighen on 2008-10-28
> **stevescripts said:**
> 
(Frames are quite useful as containers, and can lead to easier
code re-use)


That's a point where GTK+ fails miserably, IMO. The layout system it has is really hard to manage...

---

### Post by stevescripts on 2008-10-28
OK - found a little time and energy this PM.

CAVEAT - these little examples contain *NO* error-checking!
(left as an exercise ... ;) )


OO style ...

```

#!/usr/bin/python

from Tkinter import *
from tkFileDialog import *

class SimpleEdApp:
	def __init__(self, parent=Tk()):
		self.mainWindow = (parent)
		self.mainWindow.title("Simple Editor")
		self.mainWindow.resizable(0, 0)
		self.make_mnu()
		self.make_txt()

	def make_txt(self):
		self.text = Text(self.mainWindow, width = 80, height = 40, background = 'white')
		self.scrollY = Scrollbar(self.mainWindow, orient = VERTICAL, command = self.text.yview, troughcolor = 'white')
		self.text["yscrollcommand"]  =  self.scrollY.set
		self.scrollY.pack(side = RIGHT, fill = Y)
		self.text.pack(expand = TRUE, fill = BOTH)

	def make_mnu(self):
		self.menubar = Menu(self.mainWindow)
		self.filemenu = Menu(self.menubar, tearoff = 0)
		self.filemenu.add_command(label = "Open", command = self.file_open)
		self.filemenu.add_command(label = "Save as...", command = self.file_save)
		self.filemenu.add_separator()
		self.filemenu.add_command(label = "Exit", command = self.mainWindow.destroy)
		self.menubar.add_cascade(label = "File", menu = self.filemenu)		
		self.mainWindow.config(menu = self.menubar)
		
	def file_open(self):
		filename =askopenfilename(filetypes=[("pythonfiles","*.py"),("tclfiles","*.tcl"),("allfiles","*")])
		f = open(filename, 'r')
		data = f.read()
		f.close()
		self.text.insert(1.0, data)

	def file_save(self):
		filename =asksaveasfilename(filetypes=[("pythonfiles","*.py"),("tclfiles","*.tcl"),("allfiles","*")])
		f = open(filename, 'w')
		data = self.text.get(1.0, END)
		f.write(data)
		f.close()
	
app = SimpleEdApp()

app.mainWindow.mainloop()


```

the old-fashioned way ...
```

#!/usr/bin/python

from Tkinter import *
from tkFileDialog import *

def file_open():
	filename =askopenfilename(filetypes=[("pythonfiles","*.py"),("tclfiles","*.tcl"),("allfiles","*")])
	f = open(filename, 'r')
	data = f.read()
	f.close()
	text.insert(1.0, data)

def file_save():
	filename =asksaveasfilename(filetypes=[("pythonfiles","*.py"),("tclfiles","*.tcl"),("allfiles","*")])
	f = open(filename, 'w')
	data = text.get(1.0, END)
	f.write(data)
	f.close()

mainWindow = Tk()

menubar = Menu(mainWindow)

filemenu = Menu(menubar, tearoff = 0)
filemenu.add_command(label = "Open", command = file_open)
filemenu.add_command(label = "Save as...", command = file_save)
filemenu.add_separator()
filemenu.add_command(label = "Exit", command = mainWindow.destroy)
menubar.add_cascade(label = "File", menu = filemenu)
mainWindow.config(menu = menubar)


text = Text(mainWindow, width = 80, height = 40, background = 'white')
scrollY = Scrollbar(mainWindow, orient = VERTICAL, command = text.yview, troughcolor = 'white')
text["yscrollcommand"]  =  scrollY.set
scrollY.pack(side = RIGHT, fill = Y)
text.pack(expand = TRUE, fill = BOTH)

mainWindow.mainloop()


```

I hope that this somehow helps the OP (and hopefully others) sort through his questions. (note the re-use of code where possible)

Enjoyed the break (and another little excursion into Python)anyhow.

Steve

---

