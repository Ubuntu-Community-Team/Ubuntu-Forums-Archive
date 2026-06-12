---
title: "Tkinter help"
date: 2008-10-25
forum: Programming Talk
---

### Post by luke77 on 2008-10-25
Hi guys,

I'm new to Python, Tkinter, and programming in general. I'm writing my first program using Tkinter and am having trouble understanding why my program is doing what it's doing. Here's my code, somewhat stripped down:

```

from Tkinter import *

class App:
    def __init__(self, master):
        #Create frame to contain all others
        frame=Frame(master,width=700, height=700)
        
        frame.pack()

        # create a top menu
        self.menu = Menu(frame)
        root.config(menu=self.menu)

        self.filemenu = Menu(self.menu)
        self.menu.add_cascade(label="File", menu=self.filemenu)
        self.filemenu.add_command(label="Create New Portfolio")
        self.filemenu.add_command(label="Open Saved Portfolio")
        self.filemenu.add_command(label="Save Portfolio")
        self.filemenu.add_separator()
        self.filemenu.add_command(label="Exit")

        self.stocksmenu=Menu(self.menu)
        self.menu.add_cascade(label="Stocks", menu=self.stocksmenu)
        self.stocksmenu.add_command(label="Add stock")
        self.stocksmenu.add_command(label="Look up stock quote")
        self.stocksmenu.add_command(label="Remove stock")

        self.helpmenu = Menu(self.menu)
        self.menu.add_cascade(label="Help")
        self.helpmenu.add_command(label="About...")

        # create a toolbar
        self.toolbar = Frame(frame)

        self.b = Button(self.toolbar, text="New Portfolio", width=10)
        self.b.pack(side=LEFT, padx=2, pady=2)

        self.b = Button(self.toolbar, text="Open Portfolio", width=10)
        self.b.pack(side=LEFT, padx=2, pady=2)

        self.b = Button(self.toolbar, text="Save Portfolio", width=10)
        self.b.pack(side=LEFT, padx=2, pady=2)



        self.toolbar.pack(side=TOP, fill=X)

        self.status = StatusBar(frame)
        self.status.pack(side=BOTTOM, fill=X)



class StatusBar(Frame):

    def __init__(self, master):
        Frame.__init__(self, master)
        self.label = Label(self, bd=1, relief=SUNKEN, anchor=W)
        self.label.pack(fill=X)

    def set(self, format, *args):
        self.label.config(text=format % args)
        self.label.update_idletasks()

    def clear(self):
        self.label.config(text="")
        self.label.update_idletasks()
root = Tk()

app = App(root)

root.mainloop()
```

When I run this, it creates a (tiny) window whose dimensions do not match the ones I specified (700X700). If I strip away everything but the root and frame, leaving this code:
```

from Tkinter import *

class App:
    def __init__(self, master):
        #Create frame to contain all others
        frame=Frame(master,width=700, height=700)
        
        frame.pack()


root = Tk()

app = App(root)

root.mainloop()
```

the window has the correct dimensions. I can't figure out what it is that makes it behave differently in the first example. I think it probably has something to do with the "pack()' command, but it seems to me that if frame is specified as the master for all my other widgets, they should not override the dimensions of frame.

Also, 2 more semi related questions:

1. When creating the initial frame (with root as its parent), is it best to declare it as

```
        frame=Frame(master,width=700, height=700)
        
        frame.pack()
```

or

```
        self.frame=Frame(master,width=700, height=700)
        
        self.frame.pack()
```

Finally, can anyone point me towards some good fairly basic programs/code that use tkinter? There are many good reference materials and tutorials that show the behavior of individual widgets, but I'm having trouble finding examples that "put it all together", that are not insanely complex.

Thanks very much.
Luke

---

### Post by luke77 on 2008-10-25
Also, one more (sorry!):

I am creating a new method, onNew, which makes a popup box when activated. This code works:
```

    def onNew(self):
       
        win3 = self.win3 =Toplevel(root)

```

but when I try to use frame as the parent:
```

def onNew(self):
        
        win3 =Toplevel(frame)
```

I get the error "NameError: global name 'frame' is not defined". 

Do I need to change frame to self.frame in order to call it from other parts of the class?

---

### Post by y-lee on 2008-10-25
As to your first question, the statement ```
frame=Frame(master,width=700,height=700)

```

creates a frame that acts as a container for the other frames and objects you place in it. For whatever reason and I am hardly a tkinter expert adding your toolbar causes it to be resized. To fix this what I did was change the original declaration of frame to

```
frame=Frame(master)
```

and simply view this frame as a container, add the menu and toolbar and status bar as you have and then create a frame for whatever you wished to display:

```

self.display = Frame(frame, width=700, height=700)
self.display.pack()
```

I am not sure what you want in this area, text graphics or whatever, put add to this frame here in your code.

> **luke77 said:**
> 
1. When creating the initial frame (with root as its parent), is it best to declare it as

```
        frame=Frame(master,width=700, height=700)
        
        frame.pack()
```

or

```
        self.frame=Frame(master,width=700, height=700)
        
        self.frame.pack()
```


I prefer self.frame=Frame(master) myself. I suppose tho it depends on whether you need access to this frame variable in other spots in your code. If it defined simply as frame = Frame(master) in your __init__ method then outside of this method you would not be able to access this variable, like suppose you want to add something to it or whatnot in another class method or function.

As to example code you might want to take a look at [Python and Tkinter Programming]("http://www.manning.com/grayson/") by John E. Grayson. You can download all the example code from the book :)

You are also free to look at my uncompleted and probably poorly coded tkfractal program, attached.  lol

---

### Post by y-lee on 2008-10-25
> **luke77 said:**
> Also, one more (sorry!):

I am creating a new method, onNew, which makes a popup box when activated. This code works:
```

    def onNew(self):
       
        win3 = self.win3 =Toplevel(root)

```

but when I try to use frame as the parent:
```

def onNew(self):
        
        win3 =Toplevel(frame)
```

I get the error "NameError: global name 'frame' is not defined". 

Do I need to change frame to self.frame in order to call it from other parts of the class?

in your original code frame is local to your App.__init__ method, you need to change your logic if you wish to use it elsewhere in your code. See my post above. :)

---

### Post by luke77 on 2008-10-25
Thanks, but when I make these changes the window size is still incorrect and now the menubar does not show up as well! I'll post my complete code; perhaps there is something I thought was unimportant that is screwing things up. Here it is, with your changes included (this is obviously unfinished):


```

from Tkinter import *
import tkFileDialog,tkSimpleDialog
import cPickle
import urllib
import re


class App():

    def __init__(self, master):
        #Create frame to contain all others
        frame=Frame(master)
        
        self.display = Frame(frame, width=700, height=700)
        self.display.pack()

        # create a top menu
        self.addMenu()
        self.addToolbar()

        

        #Add status bar
        self.status = StatusBar(self.display)
        self.status.pack(side=BOTTOM, fill=X)


    def addMenu(self):
        self.menu = Menu(self.display)
        root.config(menu=self.menu)

        self.filemenu = Menu(self.menu)
        self.menu.add_cascade(label="File", menu=self.filemenu)
        self.filemenu.add_command(label="Create New Portfolio", command=self.onNew)
        self.filemenu.add_command(label="Open Saved Portfolio", command=self.onOpen)
        self.filemenu.add_command(label="Save Portfolio", command=self.onSave)
        self.filemenu.add_separator()
        self.filemenu.add_command(label="Exit", command=self.onExit)

        self.stocksmenu=Menu(self.menu)
        self.menu.add_cascade(label="Stocks", menu=self.stocksmenu)
        self.stocksmenu.add_command(label="Add stock", command=self.newStock)
        self.stocksmenu.add_command(label="Look up stock quote", command=self.lookupStock)
        self.stocksmenu.add_command(label="Remove stock", command=self.removeStock)

        self.helpmenu = Menu(self.menu)
        self.menu.add_cascade(label="Help", menu=self.helpmenu)
        self.helpmenu.add_command(label="About...", command=self.onAbout)
    def addToolbar(self):
        self.toolbar = Frame(self.display)

        self.b = Button(self.toolbar, text="New Portfolio", width=10, command=self.onNew)
        self.b.pack(side=LEFT, padx=2, pady=2)

        self.b = Button(self.toolbar, text="Open Portfolio", width=10, command=self.onOpen)
        self.b.pack(side=LEFT, padx=2, pady=2)

        self.b = Button(self.toolbar, text="Save Portfolio", width=10, command=self.onSave)
        self.b.pack(side=LEFT, padx=2, pady=2)



        self.toolbar.pack(side=TOP, fill=X)
        
    def onNew(self):
        #New portfolio
        



        newtitle=tkSimpleDialog.askstring("New Portfolio","Enter Portfolio Name: ")
        self.win3 =Toplevel(self.frame,width=700, height=700)
        
        self.win3.title(newtitle)
        self.addMenu()
        
        header=['Company name','Ticker','Number of Shares','Starting Price']
        colnum=0
        for name in header:
            self.label=Label(self.win3,text=name,justify=LEFT)
            self.label.grid(row=0,column=colnum)
            colnum+=1
        
        self.colnum=0
        self.rownum=1

    def onAbout(self):
        pass
        
    def onOpen(self):
        a=tkFileDialog.askopenfilename(title='Open Portfolio')
        

        if a:
            b=open(a,'r')
            self.currentportfolio=cPickle.load(b)
            print b
            self.displayPortfolio(self.currentportfolio)
        
    
    
    def onSave(self):
        a=tkFileDialog.asksavefile(title='Save Portfolio')
    def onExit(self):
        root.destroy()
    def addToPortfolio(self):
        print "You want to add to your portfolio:", self.ticker.get()
        print self.shares.get()," shares"
        print "At a price of", self.price.get()
        stock=[self.name.get(),self.ticker.get(), self.shares.get(),self.price.get()]

        for variable in stock:
            self.entry=Entry(self.win3, width = 30)
            self.entry.insert(0,variable)
            self.entry.grid(row=self.rownum,column=self.colnum)
            self.colnum+=1
        self.rownum+=1
        self.colnum=0
        self.win2.destroy()
            
        
        
    def newStock(self):
        win2 = self.win2 =Toplevel(frame)
        win2.title("New Stock")

        self.namelabel=Label(win2,text='Company Name: ',justify=LEFT)
        self.name=Entry(win2, width = 30)
        self.tickerlabel=Label(win2,text='Ticker: ',justify=LEFT)
        self.ticker=Entry(win2, width = 30)
        self.shareslabel=Label(win2,text="Number of Shares",justify=LEFT)
        self.shares=Entry(win2, width = 30)
        self.pricelabel=Label(win2,text="Starting Price",justify=LEFT)
        self.price=Entry(win2, width = 30)


                 

        self.enter=Button(win2,text='Add',width = 30, command=self.addToPortfolio)
        self.namelabel.grid()
        self.name.grid()
        self.tickerlabel.grid()
        self.ticker.grid()
        self.shareslabel.grid()
        self.shares.grid()
        self.pricelabel.grid()
        self.price.grid()
        self.enter.grid()



    def lookupStock(self):
        ticker=tkSimpleDialog.askstring('Look up Stock', prompt='Please Enter Ticker:')
        self.ticker=self.get_quote(ticker)
        print self.ticker
        c1 = Toplevel(frame)
        c1.title(ticker)
        c1.transient(frame)
        Label(c1, text=ticker+" last tradede at: "+self.ticker).grid()
    def removeStock(self):
        ticker=tkSimpleDialog.askstring('Remove Stock', prompt='Please Enter Ticker:')
        pass

    def displayPortfolio(self,portfolio):
        win3 = self.win3 =Toplevel(root)
        win3.title("Portfolio")

        self.b = Button(self.toolbar, text="Add stock", width=10, command=self.newStock)
        self.b.pack(side=LEFT, padx=2, pady=2)

        self.b = Button(self.toolbar, text="Stock quote", width=10, command=self.lookupStock)
        self.b.pack(side=LEFT, padx=2, pady=2)

        self.b = Button(self.toolbar, text="Remove stock", width=10, command=self.removeStock)
        self.b.pack(side=LEFT, padx=2, pady=2)
        
        #Create new row for each stock, but begin by making header with labels
        # row 0 -------------------------------------------
        header=['Company name','Ticker','Number of Shares','Starting Price']
        colnum=0
        for name in header:
            self.label=Label(win3,text=name,justify=LEFT)
            self.label.grid(row=0,column=colnum)
            colnum+=1
        # row 1 thru x -------------------------------------------
        self.colnum=0
        self.rownum=1
        for stock in portfolio:
            for variable in stock:
                self.entry=Entry(win3, width = 30)
                self.entry.insert(0,variable)
                self.entry.grid(row=self.rownum,column=self.colnum)
                self.colnum+=1
            self.colnum=0
            self.rownum+=1
            
    def get_quote(self,ticker):
        
        base_url = 'http://finance.google.com/finance?q='
        content = urllib.urlopen(base_url + ticker).read()
        m = re.search('class="pr".*?>(.*?)<', content)
        if m:
            self.ticker = m.group(1)
        else:
            self.ticker = 'N/A'
        return self.ticker

   

                

class StatusBar(Frame):

    def __init__(self, master):
        Frame.__init__(self, master)
        self.label = Label(self, bd=1, relief=SUNKEN, anchor=W)
        self.label.pack(fill=X)

    def set(self, format, *args):
        self.label.config(text=format % args)
        self.label.update_idletasks()

    def clear(self):
        self.label.config(text="")
        self.label.update_idletasks()




root = Tk()

app = App(root)

root.mainloop()
```


Thanks again!

---

### Post by y-lee on 2008-10-25
> **luke77 said:**
> Thanks, but when I make these changes the window size is still incorrect and now the menubar does not show up as well! I'll post my complete code; perhaps there is something I thought was unimportant that is screwing things up. Here it is, with your changes included (this is obviously unfinished):


Not quite what I meant. :)

Use frame to add your menubar, statusbar and so on to not the display frame. I changed it so that it works, I think I changed all instances of frame to self.frame too since you need access to this in your other methods. 

```
from Tkinter import *
import tkFileDialog,tkSimpleDialog
import cPickle
import urllib
import re


class App:

    def __init__(self, master):
        #Create frame to contain all others
        self.frame=Frame(master)
        self.frame.pack()
        # create a top menu
        self.addMenu()
        self.addToolbar()
        #Add status bar
        self.status = StatusBar(self.frame)
        self.status.pack(side=BOTTOM, fill=X)
        self.display = Frame(self.frame, width=700, height=700)
        self.display.pack()

    def addMenu(self):
        self.menu = Menu(self.frame)
        root.config(menu=self.menu)
        self.filemenu = Menu(self.menu)
        self.menu.add_cascade(label="File", menu=self.filemenu)
        self.filemenu.add_command(label="Create New Portfolio", command=self.onNew)
        self.filemenu.add_command(label="Open Saved Portfolio", command=self.onOpen)
        self.filemenu.add_command(label="Save Portfolio", command=self.onSave)
        self.filemenu.add_separator()
        self.filemenu.add_command(label="Exit", command=self.onExit)

        self.stocksmenu=Menu(self.menu)
        self.menu.add_cascade(label="Stocks", menu=self.stocksmenu)
        self.stocksmenu.add_command(label="Add stock", command=self.newStock)
        self.stocksmenu.add_command(label="Look up stock quote", command=self.lookupStock)
        self.stocksmenu.add_command(label="Remove stock", command=self.removeStock)

        self.helpmenu = Menu(self.menu)
        self.menu.add_cascade(label="Help", menu=self.helpmenu)
        self.helpmenu.add_command(label="About...", command=self.onAbout)
        
    def addToolbar(self):
        self.toolbar = Frame(self.frame)

        self.b = Button(self.toolbar, text="New Portfolio", width=10, command=self.onNew)
        self.b.pack(side=LEFT, padx=2, pady=2)

        self.b = Button(self.toolbar, text="Open Portfolio", width=10, command=self.onOpen)
        self.b.pack(side=LEFT, padx=2, pady=2)

        self.b = Button(self.toolbar, text="Save Portfolio", width=10, command=self.onSave)
        self.b.pack(side=LEFT, padx=2, pady=2)
        self.toolbar.pack(side=TOP, fill=X)
        
    def onNew(self):
        #New portfolio
        newtitle=tkSimpleDialog.askstring("New Portfolio","Enter Portfolio Name: ")
        self.win3 =Toplevel(self.frame,width=700, height=700)
        self.win3.title(newtitle)
        self.addMenu()
        header=['Company name','Ticker','Number of Shares','Starting Price']
        colnum=0
        for name in header:
            self.label=Label(self.win3,text=name,justify=LEFT)
            self.label.grid(row=0,column=colnum)
            colnum+=1
        
        self.colnum=0
        self.rownum=1

    def onAbout(self):
        pass
        
    def onOpen(self):
        a=tkFileDialog.askopenfilename(title='Open Portfolio')
        

        if a:
            b=open(a,'r')
            self.currentportfolio=cPickle.load(b)
            print b
            self.displayPortfolio(self.currentportfolio)
        
    
    
    def onSave(self):
        a=tkFileDialog.asksavefile(title='Save Portfolio')
    def onExit(self):
        root.destroy()
    def addToPortfolio(self):
        print "You want to add to your portfolio:", self.ticker.get()
        print self.shares.get()," shares"
        print "At a price of", self.price.get()
        stock=[self.name.get(),self.ticker.get(), self.shares.get(),self.price.get()]

        for variable in stock:
            self.entry=Entry(self.win3, width = 30)
            self.entry.insert(0,variable)
            self.entry.grid(row=self.rownum,column=self.colnum)
            self.colnum+=1
        self.rownum+=1
        self.colnum=0
        self.win2.destroy()
            
        
        
    def newStock(self):
        win2 = self.win2 =Toplevel(self.frame)
        win2.title("New Stock")

        self.namelabel=Label(win2,text='Company Name: ',justify=LEFT)
        self.name=Entry(win2, width = 30)
        self.tickerlabel=Label(win2,text='Ticker: ',justify=LEFT)
        self.ticker=Entry(win2, width = 30)
        self.shareslabel=Label(win2,text="Number of Shares",justify=LEFT)
        self.shares=Entry(win2, width = 30)
        self.pricelabel=Label(win2,text="Starting Price",justify=LEFT)
        self.price=Entry(win2, width = 30)


                 

        self.enter=Button(win2,text='Add',width = 30, command=self.addToPortfolio)
        self.namelabel.grid()
        self.name.grid()
        self.tickerlabel.grid()
        self.ticker.grid()
        self.shareslabel.grid()
        self.shares.grid()
        self.pricelabel.grid()
        self.price.grid()
        self.enter.grid()



    def lookupStock(self):
        ticker=tkSimpleDialog.askstring('Look up Stock', prompt='Please Enter Ticker:')
        self.ticker=self.get_quote(ticker)
        print self.ticker
        c1 = Toplevel(self.frame)
        c1.title(ticker)
        c1.transient(self.frame)
        Label(c1, text=ticker+" last tradede at: "+self.ticker).grid()
    def removeStock(self):
        ticker=tkSimpleDialog.askstring('Remove Stock', prompt='Please Enter Ticker:')
        pass

    def displayPortfolio(self,portfolio):
        win3 = self.win3 =Toplevel(root)
        win3.title("Portfolio")

        self.b = Button(self.toolbar, text="Add stock", width=10, command=self.newStock)
        self.b.pack(side=LEFT, padx=2, pady=2)

        self.b = Button(self.toolbar, text="Stock quote", width=10, command=self.lookupStock)
        self.b.pack(side=LEFT, padx=2, pady=2)

        self.b = Button(self.toolbar, text="Remove stock", width=10, command=self.removeStock)
        self.b.pack(side=LEFT, padx=2, pady=2)
        
        #Create new row for each stock, but begin by making header with labels
        # row 0 -------------------------------------------
        header=['Company name','Ticker','Number of Shares','Starting Price']
        colnum=0
        for name in header:
            self.label=Label(win3,text=name,justify=LEFT)
            self.label.grid(row=0,column=colnum)
            colnum+=1
        # row 1 thru x -------------------------------------------
        self.colnum=0
        self.rownum=1
        for stock in portfolio:
            for variable in stock:
                self.entry=Entry(win3, width = 30)
                self.entry.insert(0,variable)
                self.entry.grid(row=self.rownum,column=self.colnum)
                self.colnum+=1
            self.colnum=0
            self.rownum+=1
            
    def get_quote(self,ticker):
        
        base_url = 'http://finance.google.com/finance?q='
        content = urllib.urlopen(base_url + ticker).read()
        m = re.search('class="pr".*?>(.*?)<', content)
        if m:
            self.ticker = m.group(1)
        else:
            self.ticker = 'N/A'
        return self.ticker

class StatusBar(Frame):

    def __init__(self, master):
        Frame.__init__(self, master)
        self.label = Label(self, bd=1, relief=SUNKEN, anchor=W)
        self.label.pack(fill=X)

    def set(self, format, *args):
        self.label.config(text=format % args)
        self.label.update_idletasks()

    def clear(self):
        self.label.config(text="")
        self.label.update_idletasks()


root = Tk()
app = App(root)
root.mainloop()
```

I am no great fan of tkinter and my knowledge of it and how it works is just enough for me to get by with what little I do with it. So I am suggesting you spend some time trying to debug it yourself, like hours or a day or so if necessary before asking for help. I just about refuse asking for help because that is the way I learn things. Programming is more debugging than coding, esp when one uses an API one is unfamiliar with.

good luck and peace.

---

### Post by luke77 on 2008-10-25
Thanks, I misunderstood what you were saying. This makes much more sense now. Although I still do not quite understand why the original code was not working. Logically, it seems like before I was creating a frame with parent "root", and frame was acting as parent to menu, toolbar, statusbar, etc. Now, it seems like all we are doing is the same thing but inserting a blank frame as "filler". I guess this is how tkinter works...

I have spent a good deal of time trying to debug on my own already; I only post here after much frustration :)

Finally, I swear this is my last question, but in this piece of code where I set the menu:

```
    def addMenu(self):
        self.menu = Menu(self.frame)
        root.config(menu=self.menu)
```

it is setting the menu as the menu in "root". I want to set it as the menu in "frame" instead. This is because if I call the addMenu method for another window (for instance, if I want a new window to pop up with a menu bar), it will create the menu in "root" rather than the frame in question. I have tried to modify the code as follows:

```
    def addMenu(self):
        self.menu = Menu(self.frame)
        self.frame.config(menu=self.menu)
```

or

```
    def addMenu(self):
        self.menu = Menu(self.frame)
        self.config(menu=self.menu)
```

and I get the following error messages:
"TclError: unknown option "-menu"
and
"AttributeError: App instance has no attribute 'config'"

respectively. I have tried modifying this code endlessly and cannot figure out why I cannot designate a menu in any window besides root. This command isn't restricted to the root (initial) window, is it?

---

### Post by y-lee on 2008-10-25
> Finally, I swear this is my last question, but in this piece of code where I set the menu:

   ```
def addMenu(self):
        self.menu = Menu(self.frame)
        root.config(menu=self.menu)
```

it is setting the menu as the menu in "root". I want to set it as the menu in "frame" instead.


Ah toplevel menus will work only with the root window or any other toplevel window, frame on the other hand is "a rectangular region on the screen. The frame widget is mainly used as a geometry master for other widgets, or to provide padding between other widgets." In other words it, Frame,  is a piece of your window.

This means you can't give frame a menu like that and that is why you get the error mesage you do when you try, frame has a config method but no option "-menu and the class you have defined Class App has no config method.

So I would suggest you change 

```
def addMenu(self ):
        self.menu = Menu(self.frame)
        root.config(menu=self.menu)
```

to 

```
def addMenu(self, master):
        self.menu = Menu(self.frame)
        master.config(menu=self.menu)
```

where in your App initialization you call it like:

```
def __init__(self, master):
        #Create frame to contain all others
        self.frame=Frame(master)
        self.frame.pack()
        # create a top menu
        self.addMenu(master)
```

and hence in other windows you create you could use the same addMenu function as long as you call it with master set to a TopLevel window.

hopefully that makes enough sense to you so that you can work out what you are trying to do.

---

### Post by luke77 on 2008-10-25
Thanks so much. This makes sense now.

---

