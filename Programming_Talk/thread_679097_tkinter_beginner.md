---
title: "tkinter beginner"
date: 2008-01-26
forum: Programming Talk
---

### Post by bschleusner on 2008-01-26
I am trying to display a result in my python/tkinter program, and I can't figure out how.](*,)

I tried to just change the text in a label, but that doesn't seem possible, so I want to try to do something different.

My current idea is to:
delete old label
place new label where old one was
update ui

any ideas on how to do that? Am I headed in the right direction on this or is there an easier way?

---

### Post by Senesence on 2008-01-26
No need to "flip-flop" labels. Just change the text of the existing label like this:

```

from Tkinter import *

class App:
    def __init__(self, master):
        frame = Frame(master)
        frame.pack()

        self.lblText = StringVar()
        self.lblText.set("Initial text")
        self.label = Label(frame, textvariable=self.lblText)
        self.label.pack()

        self.button = Button(frame, text="Change", command=self.change)
        self.button.pack()

    def change(self):
        self.lblText.set("Changed text")

root = Tk()
app = App(root)
root.mainloop()

```

Tkinter is nice because it's easy to get started, but it looks very ugly, and the amount of widgets it provides is lacking a bit.

I recommend wxPython as an alternative (*with wxPython, not only do you get access to pretty much any widget you could ever want, but your GUI will also have the native look and feel of the host platform*)

Good Luck.

---

### Post by Majorix on 2008-01-26
As suggested, you can use the set() function to change the text property.

OR, you can use a dialog box.
[php]Tk.DialogBox(title="Your Title")[/php]

---

### Post by bschleusner on 2008-01-26
wow, that was easier than I thought. Thanks. :biggrin:

---

