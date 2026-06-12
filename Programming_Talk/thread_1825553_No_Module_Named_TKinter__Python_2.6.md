---
title: "No Module Named TKinter : Python 2.6"
date: 2011-08-15
forum: Programming Talk
---

### Post by etdsbastar on 2011-08-15
Hello there,

I am using Python 2.6 and Geany as my Programming IDE. Please have a look in the simple code as below:

```
#!/usr/local/bin/python
from TKinter import *

class Application(Frame):
    def __init__(self, master=None):
        Frame.__init__(self,master)
        self.grid()
        self.createWidgets()
    
    def createWidgets():
        self.quitButton = Button(self, text='Quit', command=self.Quit)
        self.quitButton.grid()

app = Application()
app.master.title('Sample Application')
app.mainloop()
```I had python-tk, tcl and tk installed but still the above code is showing the error:

No Module Named TKinter.

Please help.

---

### Post by nidzo732 on 2011-08-15
It's not TKinter but Tkinter

---

### Post by etdsbastar on 2011-08-15
> **nidzo732 said:**
> It's not TKinter but Tkinter

Thanks that solved the problem.

But now one more occurred:

TypeError: createWidgets() takes no arguments (1 given)

---

### Post by etdsbastar on 2011-08-15
Solved every thing, here is the actual code:

There were some typos:

```
#!/usr/local/bin/python
from Tkinter import *

class Application(Frame):
    def __init__(self, master=None):
        Frame.__init__(self,master)
        self.grid()
        self.createWidgets()
    
    def createWidgets(self):
        self.quitButton = Button(self, text='Quit', command=self.quit)
        self.quitButton.grid()

app = Application()
app.master.title('Sample Application')
app.mainloop()

```

---

