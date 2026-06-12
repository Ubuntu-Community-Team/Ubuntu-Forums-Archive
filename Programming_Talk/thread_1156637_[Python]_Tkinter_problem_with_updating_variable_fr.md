---
title: "[Python] Tkinter problem with updating variable from Entry widget"
date: 2009-05-11
forum: Programming Talk
---

### Post by Dorzu on 2009-05-11
I recently decided that I wanted to expand from command line scripts to GUI interfaces. I've been using a WYSIWYG GUI creator on Solaris so I understand the concepts of Widgets, Containers, et cetera. However, I haven't ever made a solid attempt at coding one "from scratch", so I decided to apply my Python and use Tkinter to convert a script.

I worked through a couple of examples, read the pythonware.com tutorial, and now I'm trying to convert one of my simpler scripts. Of course, I finished most of it and found an error that I cannot correct, despite searching and reading man pages/tutorials.

How do I make a variable update after typing in an Entry widget?
Some code from my little project: 
```

self.filename = ""
Label(master, text="File: ", justify="right").grid(row=0) 

self.file_entry = Entry(root, textvariable=self.filename)
self.file_entry.grid(row=1)

open = Button(root, text='Browse', command=self.askopenfilename).grid(row=2)

#The open command gets a filename and sets self.filename.

```
It works just fine, but, if I type something _new_ into the text field, the filename variable isn't updated.

This is troublesome because I have another problem elsewhere that behaves the same way. Unlike the code above, I have one entry field that doesn't have a method acting to set the variable. As a result, its behavior is to print a value of "PY_VAR3"(Type: instance?) since it hasn't been set by the first use in my source code.

Any ideas? I'm very lost. I can post/attach the full source if necessary.:confused:

---

### Post by stevescripts on 2009-05-12
Dorzu,

You may find the following a bit helpful:

```

from Tkinter import *

root = Tk()

file = ""

def file_open():
	t.delete(1.0, END)
	fn = e.get()
	f = open(fn, 'r')
	data = f.read()
	f.close()
	t.insert(1.0, data)

l = Label(root, text = 'File: ')

e = Entry(root, width = 40, background = 'white', textvariable = file)

b = Button(root, text = 'Open', command=file_open)

t = Text(root, background = 'white')

l.grid()
e.grid(row = 0, column = 1)
b.grid(row = 0, column = 2)
t.grid(row = 1, columnspan = 3)

root.mainloop()

```

That said, it appears you may be a bit confused, and that you really want to use the stock tkFileDialog and a menu - a simple example follows:
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
		self.text.delete(1.0, END)
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

Sorry for the delay in responding - been a busy day.

Let me know if this helps (or, for that matter if it **doesn't**)!

Steve

---

### Post by Dorzu on 2009-05-12
I'm not confused about what I'm doing, just how Entry worked. Basically, my script was a "front-end" for a command line function. I wrote it for my girlfriend to have an automated selection of options. I didn't want menus when converting to a GUI, only a "Configuration Panel" with a "Run" button. 

I solved it though. I still don't understand why Entry widgets have a "textvariable" option if the common method is to use get() on the widget and save the returned value in another variable. I quit trying to make sense of it, used set/get and all is well. It's not great, but this will do well.

I appreciate the help though. I'll keep that menu creation in mind for a future project! :-) Furthermore, in addition to understanding what you did, I tested it. It appears to work for me. Thanks again.

---

### Post by stevescripts on 2009-05-13
I am not nearly as competent with Python/Tkinter as I am with tcl/tk -
FWIW - Tkinter just doesnt seem to play as nicely with textvariables as
plain old Tk. (just my $.02 here)

Glad to be of a little help.

Steve
(glad to know that you are not confused about what you are doing, *I*, however, *was* confused about what you are doing... ;) )

---

