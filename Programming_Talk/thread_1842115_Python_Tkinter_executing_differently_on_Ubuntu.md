---
title: "Python Tkinter executing differently on Ubuntu"
date: 2011-09-10
forum: Programming Talk
---

### Post by e24ohm on 2011-09-10
Folks:
I am trying to learn Python and Tkinter. I built the following simple app on Windows using Tkinter. It runs fine, and gets all the output I expect.

However,when I run it on Ubuntu 11.04 I only get a tiny little box located at the top left side of the screen. In addiition, the application has no menu bar.

Not sure what is wrong.

Windows code
---------------
```
from Tkinter import *

class AppUI(Frame):

    def __init__(self, master=None):
        Frame.__init__(self, master)

        self.menubar = Menu(self)

        menu = Menu(self.menubar, tearoff=0)
        self.menubar.add_cascade(label="File", menu=menu)
        menu.add_command(label="New")
	menu.add_command(label="Quit", command=self.quit)
        menu = Menu(self.menubar, tearoff=0)
        self.menubar.add_cascade(label="Edit", menu=menu)
        menu.add_command(label="Cut")
        menu.add_command(label="Copy")
        menu.add_command(label="Paste")

        try:
            self.master.config(menu=self.menubar)
        except AttributeError:
            # master is a toplevel window (Python 1.4/Tkinter 1.63)
            self.master.tk.call(master, "config", "-menu", self.menubar)

        self.canvas = Canvas(self, bg="white", width=400, height=400,
                             bd=0, highlightthickness=0)
        self.canvas.pack()


root = Tk()

app = AppUI(root)
app.pack()

root.mainloop()
```

Ubuntu code
----------------
```
#!/usr/bin/python

from Tkinter import *

class AppUI(Frame):

    def __init__(self, master=None):
        Frame.__init__(self, master)

        self.menubar = Menu(self)

        menu = Menu(self.menubar, tearoff=0)
        self.menubar.add_cascade(label="File", menu=menu)
        menu.add_command(label="New")
	menu.add_command(label="Quit", command=self.quit)
        menu = Menu(self.menubar, tearoff=0)
        self.menubar.add_cascade(label="Edit", menu=menu)
        menu.add_command(label="Cut")
        menu.add_command(label="Copy")
        menu.add_command(label="Paste")

        try:
            self.master.config(menu=self.menubar)
        except AttributeError:
            # master is a toplevel window (Python 1.4/Tkinter 1.63)
            self.master.tk.call(master, "config", "-menu", self.menubar)

        self.canvas = Canvas(self, bg="white", width=400, height=400,
                             bd=0, highlightthickness=0)
        self.canvas.pack()


root = Tk()

app = AppUI(root)
app.pack()

root.mainloop()
```

---

### Post by Senesence on 2011-09-10
Don't know what the problem is, but just thought you should know that there is a program called diff (man diff) which can actually show the differences between two text files - assuming there are any.

The only difference between the script you use on windows, and the one you use on ubuntu, is the shebang at the top.

So, only one copy of the script would have been sufficient - you could have said: "Here's the script on Linux, it's the same script I use on windows, just with an added shebang (I confirmed that with diff).".

---

### Post by e24ohm on 2011-09-11
I found out my issue.

My issue was the fact that I created my Python app in Notepad, and emailed the application.

I needed to run dos2unix on the file, since unix uses different characters for hard returns.

After performing the latter, my app worked.

thanks everyone.

---

