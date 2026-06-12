---
title: "Python Attribute Error"
date: 2009-03-08
forum: Programming Talk
---

### Post by nesh87 on 2009-03-08
Hello all,

Im facing a rather frustrating error in python. 

```

Traceback (most recent call last):
  File "/home/t/Desktop/pymsn-0.3.3/pymsn/gui/contactlistgui.py", line 58, in showaddDialog
    print self.controller
AttributeError: 'TTb' object has no attribute 'controller'


```

I read that it might be a naming conflict so i renamed my classes and file name so that it wont interfere with other names.

```
class cList(gtk.VBox):

    def __init__(self, parentWindow, controller):
        gtk.VBox.__init__(self)
        self.parentWindow = parentWindow
        self.controller = controller

        ... #irrelevant code

        topToolBar = TTb(self, controller)
        print "INIT:", topToolBar.controller           
        #this print works fine and i get the controller class
  
```

INIT: <__main__.Client object at 0x864f90c>

```

class TTb(gtk.Toolbar):

    def __init__(self, parentBox, controller):
        gtk.Toolbar.__init__(self)
        self.controller = controller

        self.addBox = gtk.VBox(False, 1)
        self.addButton = gtk.ToolButton()
        self.addButton.set_stock_id(gtk.STOCK_ADD)
        self.addButton.connect('clicked', self.showaddDialog)
        addText = gtk.Label('add')
        self.addBox.pack_start(self.addButton, False, False, 0)
        self.addBox.pack_start(addText, False, False, 0)

def showaddDialog(self, *args):
        print self.controller

```

 print self.controller
AttributeError: 'TTb' object has no attribute 'controller'

It seems that i cant call self.controller from inside the class, but i can call it from outside.

---

### Post by Greyed on 2009-03-08
[php]
>>> class foo():
...     def __init__(self, bar):
...         self.bar = bar
...     def spam(self):
...         print self.bar
...
>>> baz = foo('bar')
>>> baz.bar
'bar'
>>> baz.spam()
bar
[/php]

Well, doesn't appear to be something with Python as a base.  Something interaction with the wrapping class around GTK?

---

### Post by WW on 2009-03-08
Is showaddDialog supposed to be a method of the TTb class?  If so, the indentation of the def statement for showaddDialog is wrong in the code that you have shown above; it needs four spaces in front of it to if it is to be a method in the TTb class.

If that is not the case, then I think we need to see the code where you call showaddDialog, so we can see how you create the variable that you are passing to the funcion.

Also, if showaddDialog really is just a function (and not a method of the TTb class), why is the first argument of the showaddDialog called 'self'?  Using 'self' when you are not defining a class method is a great way to confuse the reader of your code!

---

### Post by nesh87 on 2009-03-09
> **WW said:**
> Is showaddDialog supposed to be a method of the TTb class?  If so, the indentation of the def statement for showaddDialog is wrong in the code that you have shown above; it needs four spaces in front of it to if it is to be a method in the TTb class.

If that is not the case, then I think we need to see the code where you call showaddDialog, so we can see how you create the variable that you are passing to the funcion.

Also, if showaddDialog really is just a function (and not a method of the TTb class), why is the first argument of the showaddDialog called 'self'?  Using 'self' when you are not defining a class method is a great way to confuse the reader of your code!

Hey,

The indentation is correct in the file, i probably missed it while adding it to the code blocks. 

Ive attached the file for you to take a look at.

Thanks

---

### Post by days_of_ruin on 2009-03-09
```
topToolBar = TTb(self, controller)
```

Why are you passing self to TTb?

---

### Post by coys Crisford on 2009-03-09
i cant understand sorry

---

### Post by imdano on 2009-03-09
> **days_of_ruin said:**
> ```
topToolBar = TTb(self, controller)
```

Why are you passing self to TTb?He wants TTb to have a reference to its parent, cList.

---

### Post by Can+~ on 2009-03-09
addbox, addbutton, ugh. Pygtk does some things right, but I think is way easier to create a glade-3 xml file and use gtkbuilder to import it.

As for the OP; I tried to run your code, but what is "controler" supposed to be?

---

### Post by WW on 2009-03-09
Instead of 'print self.controller', try 'print self' to see what self is.

---

### Post by The Cog on 2009-03-09
It looks to me like a TTb can't fail to have a cltroller attribute when it's constructed. Are you sure you're not calling **del xxx.contoller** somewhere? Just a wild guess.

---

### Post by nesh87 on 2009-03-09
> **WW said:**
> Instead of 'print self.controller', try 'print self' to see what self is.


in the __init__ function print self gives me:

```
<TT object at 0x8625cd4 (GtkToolbar at 0x8809800)>

```


in the showadddialog print self gives me:
```
<TT object at 0x8625cd4 (uninitialized at 0x0)>

```

Im guessing the problem is the unitialized..

---

### Post by Can+~ on 2009-03-09
[PHP]gtk.Toolbar.__init__(self)[/PHP]

Wha-

(oh, and emesene is a python msn client btw)

---

### Post by nesh87 on 2009-03-09
> **Can+~ said:**
> [PHP]gtk.Toolbar.__init__(self)[/PHP]

Wha-

(oh, and emesene is a python msn client btw)


 def __init__(self, parentBox, controller):
        gtk.Toolbar.__init__(self)


already have that line..

i know about emesene, i already use it and hack it to my needs. I just wanna do this for fun. Plus im using pymsn, emesene guys have their own protocol implementation.

should i add the gtk.Toolbar.__init__ in showadddialog too? That shouldnt be necessary..

---

### Post by Can+~ on 2009-03-10
> **nesh87 said:**
> def __init__(self, parentBox, controller):
        gtk.Toolbar.__init__(self)

Of course, I took it from there. I'm just wondering if it's a good idea to do that.

---

### Post by imdano on 2009-03-10
> **Can+~ said:**
> Of course, I took it from there. I'm just wondering if it's a good idea to do that.I'm pretty sure that's the correct way to inherit from gtk.Toolbar.

edit: nesh, I think something is happening to the TT instance outside of the code you posted.  It looks like it's getting deleted, either explicitly or as part of garbage collection.  Are you calling destroy() on something that might have a reference to it?

---

### Post by days_of_ruin on 2009-03-10
> **imdano said:**
> I'm pretty sure that's the correct way to inherit from gtk.Toolbar.

edit: nesh, I think something is happening to the TT instance outside of the code you posted.  It looks like it's getting deleted, either explicitly or as part of garbage collection.  Are you calling destroy() on something that might have a reference to it?


Idk if using the same 'self' to initialize two different gtk widgets is a good idea.

---

### Post by imdano on 2009-03-10
> **days_of_ruin said:**
> Idk if using the same 'self' to initialize two different gtk widgets is a good idea.The TT class inherits from gtk.Toolbar.  You're supposed pass 'self' as an argument when you call any method in a parent class, including __init__.  See [here](http://docs.python.org/tutorial/classes.html#inheritance).  He could do this instead ```
super(TT, self).__init__()
```But I don't think it would make any difference here, since he's not using multiple inheritance.

---

### Post by days_of_ruin on 2009-03-10
> **imdano said:**
> The TT class inherits from gtk.Toolbar.  You're supposed pass 'self' as an argument when you call any method in a parent class, including __init__.  See [here](http://docs.python.org/tutorial/classes.html#inheritance).  He could do this instead ```
super(TT, self).__init__()
```But I don't think it would make any difference here, since he's not using multiple inheritance.

```
gtk.VBox.__init__(self)
```

```
gtk.Toolbar.__init__(self)

```

That is the same 'self' object or whatever its called.
Don't know it this is causing the problem but it doesn't seem 
like a good thing.I think that means the cList now would have gtk.Toolbar attributes which would overwrite some of the gtk.VBox attributes.

---

### Post by imdano on 2009-03-10
> **nesh87 said:**
> 
```
class cList(gtk.VBox):

    def __init__(self, parentWindow, controller):
        gtk.VBox.__init__(self)
        topToolBar = TTb(self, controller)
```
```
class TTb(gtk.Toolbar):

    def __init__(self, parentBox, controller):
        gtk.Toolbar.__init__(self)
```It's doesn't look like it's the same 'self' to me.  The 'self' attribute getting passed from cList becomes 'parentBox' inside TTb.

---

