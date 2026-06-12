---
title: "Python Text Editor help"
date: 2007-09-08
forum: Programming Talk
---

### Post by boopyg on 2007-09-08
-

---

### Post by cwaldbieser on 2007-09-08
```

fileobject.write(text.get(0, END))

```
Loading the text would entail reading it from the file and using the Text widget's insert() method.

---

### Post by boopyg on 2007-09-08
-

---

### Post by xtacocorex on 2007-09-08
You need to put the following code after the function definitions:
```

root = Tk()
root.geometry("650x400")
root.title("BoopyText")

```
I haven't test it because I don't feel like copying the code to my computer, but Python's layout is like C++ where you need to define functions before the main piece of code.

---

### Post by boopyg on 2007-09-08
-

---

### Post by xtacocorex on 2007-09-08
I got it to run, but doesn't display the save button nor does it work, but it's a start.
```

#!/usr/bin/python

from Tkinter import *
import pickle

def Save(mytext):
    t = raw_input("Save file as: ")
    f = t	
    fileObj = open("thing.txt","w")
    fileObj.write(mytext)
    fileObj.close()

def CopyToText(event):
    text.delete(0, END)
    current_note = listbox.get(ANCHOR)
    text.insert(0, current_note)

if __name__ == "__main__":
    root = Tk()
    root.geometry("650x400")
    root.title("BoopyText")

    textframe = Frame(root)

    textWidget = Text(textframe)
    save_button = Button(textframe, text="Save", command = Save(textWidget.get(1.0, END)))

    textWidget.pack(side=LEFT, fill=X, expand=1)
    save_button.pack(side=LEFT)

    textframe.pack(fill=X)

    root.mainloop()

```
This is where classes come in to play, you can define a class just to draw the UI and create an API for interfacing with the widgets.

---

### Post by pmasiar on 2007-09-08
I don't use Tkinter, but your line "from Tkinter import *" is if not wrong, then dangerous. You populate your namespace with guru knows what. Import only functions you need, so you will not accidentally define same name as local function.

It is just not a good style to "import *"

---

### Post by boopyg on 2007-09-08
-

---

### Post by xtacocorex on 2007-09-08
> **pmasiar said:**
> your line "from Tkinter import *" is if not wrong, then dangerous.
Yeah, I didn't bother fixing that.

---

### Post by boopyg on 2007-09-08
-

---

### Post by xtacocorex on 2007-09-08
> **boopyg said:**
> What should I use instead of "import *"?
It would be:
```

import Tkinter

... functions ...

root = Tkinter.Tk()

... 

textFrame = Tkinter.Frame(...)

```
You'd just have to add Tkinter. in front of the widgets.

---

### Post by cwaldbieser on 2007-09-08
> **pmasiar said:**
> I don't use Tkinter, but your line "from Tkinter import *" is if not wrong, then dangerous. You populate your namespace with guru knows what. Import only functions you need, so you will not accidentally define same name as local function.

It is just not a good style to "import *"

Tkinter is one of the few namespaces where it is common to import *.  It is intentionally designed to be used in this manner.
[http://effbot.org/pyfaq/what-are-the-best-practices-for-using-import-in-a-module.htm]("http://effbot.org/pyfaq/what-are-the-best-practices-for-using-import-in-a-module.htm")

---

### Post by cwaldbieser on 2007-09-08
> **boopyg said:**
> Thanks, but it still gives me this error:

```

  File "./tkinter", line 15, in Save
    fileObj.write(text.get(0,END))
  File "lib-tk/Tkinter.py", line 2965, in get
    return self.tk.call(self._w, 'get', index1, index2)
TclError: bad text index "0"

```
Sorry, the index should be "1.0" for line 1 position 0.

```

fileObj.write(text.get("1.0", END)

```

---

### Post by boopyg on 2007-09-08
-

---

### Post by cwaldbieser on 2007-09-08
> **boopyg said:**
> I still get the error:

  File "lib-tk/Tkinter.py", line 1406, in __call__
    return self.func(*args)
TypeError: Save() takes exactly 1 argument (0 given)

When I try and save

Try something like:
```

def Save():
    t = raw_input("Save file as: ")
    f = t	
    fileObj = open("thing.txt","w")
    fileObj.write(text.get("1.0", END))
    fileObj.close()

```
Notice how Save() doesn't have a formal parameter?  When you press the button, the GUI framework calls Save() with no arguments.  Before, your code expected it to pass an argument.

---

### Post by boopyg on 2007-09-08
-

---

### Post by cwaldbieser on 2007-09-09
That is because your variable "saven" is local to one function and you are trying to use it in another.  It would probably make more sense to write your editor as a class.  That way, all your widgets could be instance variables.  Also, your event callbacks could be methods, which tends to simplify things when you would like the event to have some arguments.

Otherwise, you will have to use some global variables, which may tend to make the code a bit messy, and maybe lead to some other problems as well.

---

### Post by boopyg on 2007-09-10
-

---

### Post by smartbei on 2007-09-11
You want 
```

fileObj = open("%s" %(saven),"w")

```
instead of:
```

fileObj = open("%s","w"  %(saven))

```
Or, more simply,
```

fileObj = open(str(saven),"w")

```

Though, looking over your code, it does not appear that saven is a string object at all, but a Tkinter Entry object.

---

### Post by zanpusnik on 2008-10-04
Wau! Thanks guys! You helped me alot!

So the final code (edited like SMARTBEI suggested) is:

```
#!/usr/bin/python

from Tkinter import *
import os

def Load():
    global loadf
    loadtop = Toplevel()
    loadtop.title = ("Load")
    loadf = Entry(loadtop)
    loadf.pack()
    loadb = Button(loadtop, text="Load", command = Load2)
    loadb.pack()
def Load2():   
    in_file = open(loadf, "r")
    text = in_file.read()
    in_file.close()
def Print():
    printer = os.popen('lpq', 'w').readlines()
    printer.write(text.get("1.0", END))
    printer.close()
def Save2():
    fileObj = open(str(saven),"w")
    fileObj.write(text.get("1.0", END))
    fileObj.close()
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
    load_button = Button(textframe, text="Load", command = Load)
    load_button.pack(side=LEFT)
    text.pack(side=LEFT, fill=X, expand=1)
    save_button.pack(side=LEFT)

    print_button = Button(textframe, text="Print", command = Print)
    print_button.pack(side=RIGHT)

    textframe.pack(fill=X)

    root.mainloop()
```

I tested it and it seem it CAN save the text file (even though the file gets the name *.12347472.12347592*) but it still cannot load other files. The *Print* button I didn't test.

---

### Post by prankstar008 on 2010-10-07
> **cwaldbieser said:**
> Sorry, the index should be "1.0" for line 1 position 0.

```

fileObj.write(text.get("1.0", END)

```

Sorry I don't have anything useful to add to this ancient thread... Just wanted to say thanks for this information.  Helped me a bunch.

---

