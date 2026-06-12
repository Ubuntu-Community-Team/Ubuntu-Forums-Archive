---
title: "Python syntax error"
date: 2008-01-30
forum: Programming Talk
---

### Post by mrblue182 on 2008-01-30
I will get right to the point
```
#!/usr/bin/env python

import pygtk
pygtk.require('2.0')
import gtk
import random

class craps():
    def __init__(self):
        
        # initiate the window
        self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
        self.window.set_border_width(10)
        self.window.set_title('CRAPS')
        self.window.connect("delete_event", gtk.main_quit)
        self.window.connect('destroy', gtk.main_quit)
        
        # create a main box
        self.mainbox = gtk.HBox(False, 0)
        self.window.add(self.mainbox)
        
        # initiate the vbox's
        self.vbox1 = gtk.VBox(False, 0)
        self.vbox2 = gtk.VBox(False, 0)
        self.vbox3 = gtk.VBox(False, 0)
        
        # initiate the hbox's
        self.hbox1 = gtk.HBox(False, 0)
        self.hbox2 = gtk.HBox(False, 0)
        self.hbox3 = gtk.HBox(False, 0)
        
        # initiate the start button
        self.cmdStart = gtk.Button("START")
        self.vbox3.pack_start(self.cmdStart, False, False, 5)
        self.cmdStart.connect("clicked", self.start)
        self.cmdStart.show()
        
        # initiate the roll button
        self.cmdRoll = gtk.Button('ROLL')
        self.vbox3.pack_start(self.cmdRoll, False, False, 5)
        self.cmdRoll.connect("clicked", self.roll)
        self.cmdRoll.show()
        
        # initiate the quit button
        self.cmdQuit = gtk.Button("QUIT")
        self.vbox3.pack_start(self.cmdQuit, False, False, 5)
        self.cmdQuit.connect("clicked", gtk.main_quit)
        self.cmdQuit.show()
        
        self.mainbox.add(self.hbox1)
        self.mainbox.add(self.hbox2)
        self.mainbox.add(self.hbox3)
        
        self.hbox3.add(self.vbox1)
        self.hbox3.add(self.vbox2)
        self.hbox3.add(self.vbox3)
        
        self.vbox1.show()
        self.vbox2.show()
        self.vbox3.show()
        
        self.hbox1.show()
        self.hbox2.show()
        self.hbox3.show()
        
        self.mainbox.show()
        self.window.show()
        
    def start(self):
        if canStart == True:
        
            # roll the dice
            self.rolldie()
            
            # checks to see if you win, lose, or continue to roll
            if intSum == (2 or 3 or 11):
                self.lose()
            elif intSum == (7 or 11):
                self.win()
            else:
                global intPoints
                global intDie1
                global intDie2
            
                intPoints = intSum
                boolRoll = True
                boolStart = False
    
    def roll(self):
        print 'roll'
        
    def win(self):
        print 'win'
        
    def lose(self):
        print 'lose'

    def rolldie(self):
        global intDie1
        global intDie2
        global intSum
        intDie1 = random.randint(1, 6)
        intDie2 = random.randint(1, 6)
        intSum = intDie1 + intDie2
        
canStart = True
canRoll = False
        
if __name__ == "__main__":
    craps = craps()
    gtk.main()
```

It is a simple craps game that i made in regular, command-line python that I am attempting to transfer to pygtk. But for some reason, whenever I click on the "start", or "roll" button, I get this output

```
Traceback (most recent call last):
  File "crapspygtk.py", line 110, in <module>
    craps = craps()
  File "crapspygtk.py", line 35, in __init__
    self.cmdStart.connect("clicked", self.start(self))
TypeError: start() takes exactly 1 argument (2 given)

```

I have tried changing
```

self.cmdStart.connect("clicked", self.start)
```

to 

```

self.cmdStart.connect("clicked", self.start())
```

and

```

self.cmdStart.connect("clicked", self.start(self))
```

but i have no idea. Any help would be nice.

PS: If you find a more efficient way to do something in my code, don't hesitate to say so =]

---

### Post by foxylad on 2008-01-30
Class methods have an implicit first argument ("self" in your example). I don't know how GTK works, but it looks like the connect function results in the function being called with another argument - you'd have to look at the documentation to see what it is.  You definately want to be using "self.cmdStart.connect("clicked", self.start)" though.

One solution might be to make a stub function outside the class, which then calls the class method - that way you could work out what was going on.

---

### Post by Quikee on 2008-01-31
Connect shoulb be:
```
self.cmdStart.connect("clicked", self.start)
```

Also start method does not take 0 arguments (self excluded) but 1 argument - button which has been clicked:

```
def start(self, button):
    ...
```

---

### Post by Quikee on 2008-01-31
> **foxylad said:**
> Class methods have an implicit first argument ("self" in your example)...

Class methods are defined as:

```
@classmethod
def someClassMethod(class, *arguments, **keywords):
    ...
```

and as you can swe get the class as implicit first argument.

I think what you meant as class method is instance method, which always gets implicit instance (usually named "self") as first argument.

```

def someInstanceMethod(self, *arguments, **keywords):
    ...
```

---

### Post by mrblue182 on 2008-01-31
Thanks, putting the button name as an argument got it to work. =]

---

