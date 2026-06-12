---
title: "python &amp; Tkinter: check for text in text box"
date: 2008-10-21
forum: Programming Talk
---

### Post by cyclobs on 2008-10-21
hey guys,

does anyone know how to make python check for text in a text box and if there is none it does some code?


many thanks

---

### Post by unutbu on 2008-10-21
Perhaps what you are looking for is an Entry widget.
You can find out what text it contains by calling the get method. 

For example:
```

#!/usr/bin/env python
from Tkinter import *

class Quitter(Frame):                          # subclass our GUI
    def __init__(self, parent=None):           # constructor method
        Frame.__init__(self, parent)
        self.pack()
        widget = Button(self, text='Quit', command=self.quit)
        widget.pack(side=LEFT)
    def quit(self):
        Frame.quit(self)
     
def fetch():
**    print 'Input => "%s"' % ent.get() **             # get text
     
root = Tk()
ent = Entry(root)
ent.insert(0, 'Type words here')                   # set text
ent.pack(side=TOP, fill=X)                         # grow horiz
     
ent.focus()                                        # save a click
ent.bind('<Return>', (lambda event: fetch()))      # on enter key
btn = Button(root, text='Fetch', command=fetch)    # and on button 
btn.pack(side=LEFT)
Quitter(root).pack(side=RIGHT)
root.mainloop()  

```
This example comes from Mark Lutz's Programming Python book. You can download this, and more Tkinter examples from [http://examples.oreilly.com/python3/](http://examples.oreilly.com/python3/)

---

### Post by stevescripts on 2008-10-21
As simple an example as I could hack out:
```

#!/usr/bin/python

from Tkinter import *

root = Tk()

root.title("test")

root.resizable(0, 0)

def test():
	data = t.get(1.0, END)
	print len(data)
	print data


b = Button(root, text="test", command=test)

b.pack()

t = Text(root, width=80, height= 40, bg='white')

t.pack()

root.mainloop()


```

A couple of things to note here.  The beginning (zeroth) index of a Tk text widget is 1.0, rather than 0. (line 1, index 0).

This accounts for the difference between the entry get posted earlier by unutbu, and the text get().

The length of the variable data will be 1, if the text widget contains no data (*IF* I recall correctly, that is a newline...),
so, you can define your function to do whatever it is you are after by testing that the length of data is > 1.

Hope this is somewhat helpful.

Steve

---

### Post by cyclobs on 2008-10-23
ahh ok i see. i'll try it out thanks :)

---

