---
title: "Python Tkinter Checkbox Weirdness"
date: 2011-07-08
forum: Programming Talk
---

### Post by DBQ on 2011-07-08
Hi Everybody, 

I got this code from a website which demos how to use CheckButton in Tkinter:

```

import Tkinter as tk
root = tk.Tk()

var = tk.IntVar()
cb = tk.Checkbutton(root, text="the lights are on", variable=var)
cb.pack()

def showstate():
    if var.get():
        print "the lights are on"
    else:
        print "the lights are off"

button = tk.Button(root, text="show state", command=showstate)
button.pack()

root.mainloop()


```

The code works fine. However, as soon as I add a line ```
root1 = tk.Tk()
``` in the very beginning, the variable corresponding to the checkbutton is never updated (I always get "the lights are off" regardless of whether the button is checked).

I need to be able to use multiple forms in Tkinter.  Any ideas on how to get this work? Thank You!

---

### Post by DBQ on 2011-07-09
Any ideas?

---

### Post by DBQ on 2011-07-09
I wonder if creating another form somehow affects the event handling.

---

### Post by GWBouge on 2011-07-09
It's been a while since I've used Tk, but I think you can (or almost certainly, should) only have one root widget in the program.  You might need to either create a new Frame, or check out the Toplevel widget.

---

### Post by DBQ on 2011-07-09
The Toplevel widget solved my problem -- thank you so much! This have been frustrating me for hours.

---

### Post by juancarlospaco on 2011-07-09
I have learned all from this PDF:  infohost.nmt.edu/tcc/help/pubs/tkinter.pdf

---

