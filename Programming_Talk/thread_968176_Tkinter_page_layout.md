---
title: "Tkinter page layout"
date: 2008-11-02
forum: Programming Talk
---

### Post by luke77 on 2008-11-02
Hi guys,

I'm having trouble with weird activity with a Tkinter GUI I'm creating. I've stripped down the code somewhat to simplify the problem somewhat, and I've posted it below:

```
from Tkinter import *
import tkFileDialog,tkSimpleDialog


WINDOWWIDTH=500
WINDOWHEIGHT=500
class App:
    def __init__ (self,master):
        self.window = Frame(master)
        self.window.pack()
        self.master= master
        #Create frame to contain all others
        self.display=Frame(self.window,width=WINDOWWIDTH,height=WINDOWHEIGHT, bg='black')
        self.display.pack()
        self.addMenu(self.master)
        #Create widgets
        self.createwidgets()
        
        
        
        
        
        
        
    def createwidgets(self):
        

        self.leftframe=Frame(self.display, width=WINDOWWIDTH/3,height=WINDOWHEIGHT, bg='white')
        self.rightframe=Frame(self.display, width=2*WINDOWWIDTH/3,height=WINDOWHEIGHT, bg='blue')
        self.leftframe.pack(side="left", expand="yes", fill="x")
        self.rightframe.pack(side="left", expand="yes", fill="x")
        
    
    def displayStories(self):
        self.lb = Text(self.leftframe)
        self.lb.pack()
        
       
        
    def addMenu(self,master):
        self.menu = Menu(self.window)
        master.config(menu=self.menu)
        

        self.feedmenu = Menu(self.menu)
        self.menu.add_cascade(label="RSS", menu=self.feedmenu)
        self.feedmenu.add_command(label="Load RSS", command=self.displayStories)


        
        
root=Tk()
app=App(root)

root.mainloop()
        
```

        


Basically I'm trying to create 2 columns on the page so that (eventually) I will be able to have sepearte text boxes in each column. The code so far creates a leftframe and rightframe, with parent frame self.display . When I run the script this happens as expected.

But next, I want to create a text box within self.leftframe which is done in  function displayStories . self.lb is created with parent self.leftframe . When this is run, the text box shows up, but my layout goes to hell. I want the text box to be contained within self.leftframe, but when it is added self.leftframe disappears (or is completely filled by the text box), the dimensions that I had specified for self.leftframe and self.rightframe are forgotten about, and I can see self.display (black background) on the part of the screen in the left frame that is not filled by the text box. This makes a lot more sense if you run the simple script I've posted.

I've tried adjusting various options, and also using the "grid" manager instead of "pack", but I can't seem to figure out why this is happening. Can anyone help out?

Thanks,
Luke

---

### Post by luke77 on 2008-11-03
Bump?

---

### Post by stevescripts on 2008-11-03
bear with me a bit - on my list of things to-do as time allows ...

Steve

---

### Post by stevescripts on 2008-11-03
The short answer here, is that your frame width and height are in
pixels, and the text widget width and height are computed based 
on the font used ...

Also, as you specify no width or height for the text widget it 
automagically becomes the default, so when it is displayed, the
geometry of your GUI is changed.

If you tinker with the width and height of the text widget, you
can get it to match your defualt UI (more or less), of course you
could always do the math ... 

Hope this helps a bit
Steve
(try something like 27 for the width and 38 for the height of your text widget ...
this of course depends upon font and resolution a bit)

---

### Post by luke77 on 2008-11-04
See, that's what I was thinking too, and I spent many hours trying to adjust the sizing of my text boxes, thinking that was the problem. The trouble is, when I specify dimensions of the text boxes, no matter how high or low, the enclosing frame seems to adjust to fit the new boxes. So, for instance, if I try inserting a text widget in leftframe with dimensions 1x1, leftframe shrinks down to 1x1. If I make the text widget 100x100, leftframe takes that size. What I want, and what seems like should be happening, is if I have leftframe which is 500X500 pixels, and I create a text box wit effective dimensions of 200X200 (I understand that text widgets use lines as dimensions), the text box should take up a little less than half of leftframe, with leftframe remaining 500X500 pixels. Instead, leftframe is shrinking down to become 200X200, and I can't figure out why.  After a while I tried remmoving the text boxes and I got the same problem. I think maybe this code will better illustrate the problem. This first set of code is the toally stripped down version, and you can see leftframe in white on the left, and rightframe in blue on the right.


```



from Tkinter import *
import tkFileDialog,tkSimpleDialog,tkMessageBox


WINDOWWIDTH=500
WINDOWHEIGHT=500
TITLEFONT = ("Courier",12,"normal")
HEADINGFONT = ("Helvetica",9,"bold")



class App:
    def __init__ (self,master):
        self.window = Frame(master,width=WINDOWWIDTH,height=WINDOWHEIGHT)
        self.window.pack(expand=YES, fill=BOTH)
        self.master= master
        self.currentfeeds = []
        #Create frame to contain all others
        self.display=Frame(self.window,width=WINDOWWIDTH,height=WINDOWHEIGHT, bg='black')
        self.display.pack()
    


        #Create widgets
        self.createwidgets()
        
        
        
        
        
        
        
    def createwidgets(self):
        # create a top menu
        self.addMenu(self.master)
        self.addToolbar()
        self.leftframe=Frame(self.display, width=WINDOWWIDTH/3,height=WINDOWHEIGHT, bg='white')
        self.rightframe=Frame(self.display, width=2*WINDOWWIDTH/3,height=WINDOWHEIGHT, bg='blue')
        self.leftframe.pack(side="left", expand="yes", fill="x")
        self.rightframe.pack(side="left", expand="yes", fill="x")
        


  
        
    def addMenu(self,master):
        self.menu = Menu(self.window)
        master.config(menu=self.menu)
        
        self.filemenu = Menu(self.menu)

        
        
    def addToolbar(self):
        self.toolbar = Frame(self.display)

     
        self.toolbar.pack(side='top',expand="yes", fill="x")
        
        

root=Tk()
app=App(root)

root.mainloop()
```





Next, if I try to pack ANYTHING inside rightframe, it shrinks down to size and totally distorts my screen dimensions. Here is the exact same code, adding a label widget in self.rightframe. It completely shrinks rightframe and disorts the screen dimensions. Does my question make sense now?

```
from Tkinter import *
import tkFileDialog,tkSimpleDialog,tkMessageBox


WINDOWWIDTH=500
WINDOWHEIGHT=500
TITLEFONT = ("Courier",12,"normal")
HEADINGFONT = ("Helvetica",9,"bold")



class App:
    def __init__ (self,master):
        self.window = Frame(master,width=WINDOWWIDTH,height=WINDOWHEIGHT)
        self.window.pack(expand=YES, fill=BOTH)
        self.master= master
        self.currentfeeds = []
        #Create frame to contain all others
        self.display=Frame(self.window,width=WINDOWWIDTH,height=WINDOWHEIGHT, bg='black')
        self.display.pack()
    


        #Create widgets
        self.createwidgets()
        
        
        
        
        
        
        
    def createwidgets(self):
        # create a top menu
        self.addMenu(self.master)
        self.addToolbar()
        self.leftframe=Frame(self.display, width=WINDOWWIDTH/3,height=WINDOWHEIGHT, bg='white')
        self.rightframe=Frame(self.display, width=2*WINDOWWIDTH/3,height=WINDOWHEIGHT, bg='blue')
        self.leftframe.pack(side="left", expand="yes", fill="x")
        self.rightframe.pack(side="left", expand="yes", fill="x")
        


        self.label=Label(self.rightframe,text='Current story',font=HEADINGFONT).pack(side='top')
  
        
    def addMenu(self,master):
        self.menu = Menu(self.window)
        master.config(menu=self.menu)
        
        self.filemenu = Menu(self.menu)

        
        
    def addToolbar(self):
        self.toolbar = Frame(self.display)

     
        self.toolbar.pack(side='top',expand="yes", fill="x")
        
        

root=Tk()
app=App(root)

root.mainloop()
```

---

