---
title: "Calling wx from Tkinter error (using python)"
date: 2011-08-29
forum: Programming Talk
---

### Post by DBQ on 2011-08-29
Hi Everybody,

I have an application which calls wx from Tkinter. Here is the wx code I am trying to run (changed it from [http://stackoverflow.com/questions/4767808/new-wxnotebook-pages-stay-empty-in-wxpython](http://stackoverflow.com/questions/4767808/new-wxnotebook-pages-stay-empty-in-wxpython)). It resides in the module which I import in the main program.

```

import wx

def run(nb):
    for i in range(1, 5, 1): 
        adp(nb, i)

def adp(nb, p): 
    newpage = Page(nb)
    newpage.SetBackgroundColour(wx.GREEN)
    wx.StaticText(newpage, -1, "PAGE "+str(p), style=wx.ALIGN_CENTRE)
    wx.CallAfter(nb.AddPage, newpage, "Page "+str(p))

class Page(wx.Panel):
    def __init__(self, parent):
        wx.Panel.__init__(self, parent)
        wx.StaticText(self, -1, "This is a Page object", (20,20))

class MainFrame(wx.Frame):
    def __init__(self):
        wx.Frame.__init__(self, None, title="Notebook Test")
        p = wx.Panel(self)
        self.nb = wx.Notebook(p)
        self.page1 = Page(self.nb)

        sizer = wx.BoxSizer()
        sizer.Add(self.nb, 1, wx.EXPAND)
        p.SetSizer(sizer)



def funkyfunc():
    app = wx.App()
    mf = MainFrame()
    mf.Show()
    mf.nb.AddPage(mf.page1, "Testseite 1")
    run(mf.nb)
    app.MainLoop()          

```

In my Tkinter code, when the user clicks on a menu, I simply call funkyFunc() to show my wx notebook. After I close the notebook, and then close the main tkinter app, on exit I get the following error:

```

The program 'python' received an X Window System error.
This probably reflects a bug in the program.
The error was 'RenderBadPicture (invalid Picture parameter)'.
  (Details: serial 1040 error_code 164 request_code 155 minor_code 7)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

Note, other oddities happen as well after closing the wx form. For example, not being able to write to a proc file which I can do before (yes, that /proc file was meant to be writable).

Please help! I spent hours trying to figure this out...

Note: everything works fine when I do not call the wx.

---

### Post by DBQ on 2011-08-30
I tried to call wx by creating a different thread, but that did not help.

---

### Post by Smart Viking on 2011-08-30
Works for me?
```
import hay
hay.funkyfunc()

```

EDIT:
My version of wx: 2.8.10.1

libgtk2.0-bin - 2.20.1-2

---

### Post by DBQ on 2011-08-30
Did you try to run it from Tkinter? E.g. make a Tkinter form, create a menu, and make the action of the menu run funkyfunk(). After you close the wx form, and then close the tkinter form, you should get this.

You did give me an idea though -- perhaps I need to upgrade my wx.

---

### Post by DBQ on 2011-08-31
Here is a minimal working example:  I got a simple python code (below: tkt.py) which calls the wx code (bellow: wxt.py) from the tkinter menu. I run it using python tkt.py.  Next, on the displayed form I go to Menu->SubMenu and display the wx form.  Finally, I close the wx form and then the tk form (in that order!). The result is this error:

```

The program 'python' received an X Window System error.
This probably reflects a bug in the program.
The error was 'RenderBadPicture (invalid Picture parameter)'.
  (Details: serial 463 error_code 164 request_code 155 minor_code 7)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


```



Here are the two files:

The tk code

```

# tkt.py
#! /usr/bin/env python
from Tkinter import *

import tkMessageBox
import wxt

class tkt(Frame):


	def __init__(self, master):
		
        	Frame.__init__(self,master)      
 
        	self.menu = Menu(self)
        	self.master.config(menu=self.menu)
		self.tkMenu = Menu(self.menu)
        	self.menu.add_cascade(label="Menu", menu=self.tkMenu)
		self.tkMenu.add_command(label="SubMenu", command=self.Menu)

	def Menu(self):
		wxt.funkyfunc()

if __name__ == "__main__":
	root = Tk()
	app = tkt(root)
	root.mainloop()

```

and the wx code:

```

import wx


# Some classes to use for the notebook pages.  Obviously you would
# want to use something more meaningful for your application, these
# are just for illustration.

class PageOne(wx.Panel):
    def __init__(self, parent):
        wx.Panel.__init__(self, parent)
        t = wx.StaticText(self, -1, "This is a PageOne object", (20,20))

class PageTwo(wx.Panel):
    def __init__(self, parent):
        wx.Panel.__init__(self, parent)
        t = wx.StaticText(self, -1, "This is a PageTwo object", (40,40))

class PageThree(wx.Panel):
    def __init__(self, parent):
        wx.Panel.__init__(self, parent)
        t = wx.StaticText(self, -1, "This is a PageThree object", (60,60))


class MainFrame(wx.Frame):
    def __init__(self):
        wx.Frame.__init__(self, None, title="Simple Notebook Example")

        # Here we create a panel and a notebook on the panel
        p = wx.Panel(self)
        nb = wx.Notebook(p)

        # create the page windows as children of the notebook
        page1 = PageOne(nb)
        page2 = PageTwo(nb)
        page3 = PageThree(nb)

        # add the pages to the notebook with the label to show on the tab
        nb.AddPage(page1, "Page 1")
        nb.AddPage(page2, "Page 2")
        nb.AddPage(page3, "Page 3")

        # finally, put the notebook in a sizer for the panel to manage
        # the layout
        sizer = wx.BoxSizer()
        sizer.Add(nb, 1, wx.EXPAND)
        p.SetSizer(sizer)


def funkyfunc():
    app = wx.App()
    MainFrame().Show()
    app.MainLoop()

```

---

### Post by DBQ on 2011-09-01
bump

---

