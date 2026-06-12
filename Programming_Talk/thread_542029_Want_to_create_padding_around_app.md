---
title: "Want to create padding around app"
date: 2007-09-03
forum: Programming Talk
---

### Post by yuvlevental on 2007-09-03
```

from Tkinter import *
import tkMessageBox

class App:

    def __init__(self, master):
	
	master.title("Type Some Text")
        self.frame = Frame(master)
	self.CreateWidgets()
        self.frame.grid()

    def CreateWidgets(self):

        lbText = Label(text="Enter Text:")
	lbText.grid(row=0, column=0)
	self.enText = Entry()
	self.enText.grid(row=0, column=1, columnspan=3)
	btnDisplay = Button(text="Display!", command=self.Display)
	btnDisplay.grid(row=0, column=4)

    def Display(self):
        """Called when btnDisplay is clicked, displays the contents of self.enText"""
        tkMessageBox.showinfo("Results:", "You typed: %s" % self.enText.get())

root = Tk()

app = App(root)

root.mainloop()

```

I want to create a padding for the frame self.frame that is (padx=10, pady=10).

How do I do it?

Thanks,
Yuvlevental

---

### Post by cwaldbieser on 2007-09-03
```

    f = Frame(master)
    f.configure(padx=10, pady=10)

```

---

