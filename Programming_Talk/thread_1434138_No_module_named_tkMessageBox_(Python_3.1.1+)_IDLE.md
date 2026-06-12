---
title: "No module named tkMessageBox (Python 3.1.1+) IDLE"
date: 2010-03-19
forum: Programming Talk
---

### Post by houseonfire on 2010-03-19
I have been following a guide on [http://www.learningpython.com/2006/02/08/creating-a-gui-in-python-using-tkinter/](http://www.learningpython.com/2006/02/08/creating-a-gui-in-python-using-tkinter/) so I can learn python.

I get this error:
```
Traceback (most recent call last):
  File "/home/tim/Desktop/test.py", line 3, in <module>
    import tkMessageBox
ImportError: No module named tkMessageBox
```
When I try to run it.


from this script:
```
#! /usr/bin/env python
from tkinter import *
import TkMessageBox 

class GUIFramework(Frame):
    """This is the GUI"""
    
    def __init__(self,master=None):
        """Initialize yourself"""
        
        """Initialise the base class"""
        Frame.__init__(self,master)
        
        """Set the Window Title"""
        self.master.title("Type Some Text")
        
        """Display the main window"
        with a little bit of padding"""
        self.grid(padx=10,pady=10)
        self.CreateWidgets()
       
    def CreateWidgets(self):
        """Create all the widgets that we need"""
                
        """Create the Text"""
        self.lbText = Label(self, text="Enter Text:")
        self.lbText.grid(row=0, column=0)
        
        """Create the Entry, set it to be a bit wider"""
        self.enText = Entry(self)
        self.enText.grid(row=0, column=1, columnspan=3)
        
        """Create the Button, set the text and the 
        command that will be called when the button is clicked"""
        self.btnDisplay = Button(self, text="Display!", command=self.Display)
        self.btnDisplay.grid(row=0, column=4)
        
    def Display(self):
        """Called when btnDisplay is clicked, displays the contents of self.enText"""
        tkMessageBox.showinfo("Text", "You typed: %s" % self.enText.get())    
                
if __name__ == "__main__":
    guiFrame = GUIFramework()
    guiFrame.mainloop()#! /usr/bin/env python
from tkinter import *

class GUIFramework(Frame):
    """This is the GUI"""
    
    def __init__(self,master=None):
        """Initialize"""
        
        """Initialize the base class"""
        Frame.__init__(self,master)
        
        """Display the main window"""
        self.grid()
        
        """Create the Text"""
        self.HelloLabel = Label(master, text="Hello World!")
        self.HelloLabel.grid()
                
if __name__ == "__main__":
    guiFrame = GUIFramework()
    guiFrame.mainloop()

```


And also, I was wondering how I could execute a linux terminal command on python, after a button is pressed. With the button activating the command.

---

### Post by raydeen on 2010-03-22
As far as your first question goes, here's a link that may help you get the Tcl/Tk installed.

[http://tkinter.unpythonic.net/wiki/How_to_install_Tkinter]("http://tkinter.unpythonic.net/wiki/How_to_install_Tkinter")

Not sure about info for your second question.

---

### Post by raydeen on 2010-03-22
I tried to run the code from IDLE and it won't run. I think I've read elsewhere that GUI apps sometimes have trouble running from IDLE. Also, at the very top of your code, capitalize the 't' in Tkinter and make the 't' in tkMessageBox lowercase. 

```

#! /usr/bin/env python
from Tkinter import *
import tkMessageBox

```

Try running the code from the terminal. It seemed to work for me.

---

### Post by bobjohnbowles on 2012-07-19
> **raydeen said:**
> I tried to run the code from IDLE and it won't run. I think I've read elsewhere that GUI apps sometimes have trouble running from IDLE. Also, at the very top of your code, capitalize the 't' in Tkinter and make the 't' in tkMessageBox lowercase. 

```

#! /usr/bin/env python
from Tkinter import *
import tkMessageBox

```

Try running the code from the terminal. It seemed to work for me.
NO! The title says he is using Python 3, _NOT_ Python 2. Your setup must be for 2. The change required is to refer to messagebox, rather than tkMessageBox, because that has been renamed, too.

---

