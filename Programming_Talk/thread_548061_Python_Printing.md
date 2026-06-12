---
title: "Python: Printing"
date: 2007-09-10
forum: Programming Talk
---

### Post by boopyg on 2007-09-10
-

---

### Post by Nekiruhs on 2007-09-10
```
#!/usr/bin/python

from Tkinter import *
[COLOR="Red"]import os[/COLOR]

def Print():
    [COLOR="Red"]printer = os.popen('lpq', 'w').readlines()[/COLOR]
    printer.write(text.get("1.0", END))
    printer.close()
def Save2():
    fileObj = open("%s","w"  %(saven))
    fileObj.write(text.get("1.0", END))
    fileObj.close()
def Save1():
     top = Toplevel()
     top.title("Save")
     saven = Entry(top)
     saven.pack()
     button = Button(top, text="Dismiss", command=Save)
     button.pack()
def Save():
    global saven
    top = Toplevel()
    top.title("Save")
    saven = Entry(top)
    saven.pack()
    button = Button(top, text="Save", command=Save2)
    button.pack()
if __name__ == "__main__":
    root = Tk()
    root.geometry("650x400")
    root.title("BoopyText")

    textframe = Frame(root)

    text = Text(textframe)
    save_button = Button(textframe, text="Save", command = Save)

    text.pack(side=LEFT, fill=X, expand=1)
    save_button.pack(side=LEFT)

    print_button = Button(textframe, text="Print", command = Print)
    print_button.pack(side=RIGHT)

    textframe.pack(fill=X)

    root.mainloop()
```
Try that. By the way, you don't to import a module inside a function that you could call more than once. Just put it at the top of your code

---

### Post by boopyg on 2007-09-10
-

---

