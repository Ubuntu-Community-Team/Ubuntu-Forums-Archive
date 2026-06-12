---
title: "[pygtk]trouble packing buttons stored in a list"
date: 2010-09-03
forum: Programming Talk
---

### Post by OgreProgrammer on 2010-09-03
I am having trouble understanding how to pack a button in my VBox. The error occurs in the newlistbutton function. I hope to append a button to the list called funcbutton, but it doesnt seem to work. I guess I am failing to understand something critical. 

The idea is that the user(me) will be adding buttons at run time.

I guess I am asking how to access the VBox called secondary from my function. It works fine from __init__().

```

#!/usr/bin/env python

import pygtk
pygtk.require('2.0')
import gtk

class slide:
    
    def __init__(self):
        window = gtk.Window(gtk.WINDOW_TOPLEVEL)
        window.set_default_size(640,480)
        window.set_resizable(True)
        window.connect("destroy", self.closeapp)
        window.set_title('nothing special')
        window.set_border_width(0)
        # next I have to set up containers - 2 vertical slices
        # false means that the contents dont share equal space. num = border space
        primary = gtk.HBox(False, 0) 
        window.add(primary) # squeeze it in
        primary.show() # and cause it to display
        
        secondary = gtk.VBox(False, 0) # for the content buttons
        primary.pack_start(secondary, False, False, 0)
        secondary.show()
        
        # to do: will need to do scrolling for these buttons when # gets large.
        funcbutton = []
        funcbutton.append(gtk.Button('Functions'))
        for button in funcbutton:
            button.connect('clicked', self.closeapp) # placeholder - it will create a menu
            secondary.pack_start(button, False, False, 0)
            button.set_flags(gtk.CAN_DEFAULT)
            button.show()
        # add button w/ popup asking for a name - kludge it for now.
        addListbutton = gtk.Button('New List')
        addListbutton.connect('clicked', self.newlistbutton(funcbutton, secondary, 'boo'))
        secondary.pack_start(addListbutton, False, False, 0)
        addListbutton.show()
        
        scratchpad = gtk.ScrolledWindow()
        # POLICY_AUTOMATIC tells the text winder to handle its scrollbars
        scratchpad.set_policy(gtk.POLICY_AUTOMATIC, gtk.POLICY_AUTOMATIC)
        textview = gtk.TextView()
        textbuffer = textview.get_buffer()
        textbuffer.set_text("blah")
        scratchpad.add(textview)
        scratchpad.show()
        textview.show()
        primary.pack_start(scratchpad)
        window.show()
        
    def newlistbutton(self, buttonlist, packplace, newname):
        newbut = gtk.Button(newname)
        newbut.connect('clicked', self.closeapp) # placeholder function
        packplace.pack_start(newbut, False, False, 0)
        newbut.show()
        buttonlist.append(newbut)
        
    def closeapp(self, widget): gtk.main_quit()
    
def main():
    gtk.main()
    return 0       

if __name__ == "__main__":
    slide()
    main()

```

---

### Post by StephenF on 2010-09-03
You lack basic Python knowledge best found in the official Python tutorial. I could give you a few pointers but then you would be back to your GUI obsession and hitting the next brick wall.

---

### Post by Tony Flury on 2010-09-04
The short answer is that the thing you call secondary, is only called secondary in your init function, it has no direct name you can use in another other function.

You have two choices :
1) you could store your "secondary" object in a form that is accessible to all functions, you may want to do this with other items too.
2) you could traverse the object hierarchy each time you call your funcbuttons functions so that you can re-find your "secondary" VBox.

you are also trying to use a class just as a function - i.e. the slide class. although it would appear to mostly work, as most of your functionality is in the init function for the class, it is not a good habit to get into. The point of a class is to provide an object with data and functions - for instance (this example wont work with your code).

```

window = slide() # get a object of type slide
window.CreateWindow() # call the CreateWindow method on the slide class
window.closeWindow() # call the closeWindow method on the slide class

```
here all the complexities are hidden in the slide class - and the class itself exposes a simple interface out to the application - i.e. an interface which allows you to create and close windows. everything else is handled internally in the class.

---

### Post by StephenF on 2010-09-04
> **Tony Flury said:**
> You are also trying to use a class just as a function - i.e. the slide class. although it would appear to mostly work, as most of your functionality is in the init function for the class, it is not a good habit to get into. The point of a class is to provide an object with data and functions.
I kind of dispute that last sentence. It's a bit like saying the point of a human is to have a bipedal ape with opposable thumbs.

As for the other points, it's not really his fault. The program style adopted comes straight out of the PyGTK tutorial which is aimed squarely at people who waded half way through the Python tutorial and got bored.

---

### Post by OgreProgrammer on 2010-09-05
Thanks for the replies. 

Tony I am thinking about what you said. Perhaps I am looking at it inside out. 

StephenF, "The Python Tutorial" sounds pretty definitive. But it seems I own a hard copy. Thanks for the tough love though. I'll make good use of my thumbs and your advice.

Indeed the project was written based on code taken from the pygtk site and/or the acire project. 

I purchased "An introduction to Python" by Guido van Rossum last year and have read it several times through. But I guess I am still enough of a newbie that I dont see where those pygtk violations of the spirit of python occur. The class implementation on pages 87 and 88 look identical in rough form to the examples from pygtk. 

From what I see the Acire project application is mostly a front end for the samples found at /usr/share/python-snippets.

So yeah, it annoys me to no end if the basic pygtk material presented is flawed in someway. I mean, I *want* to learn it right. 

My basic confusion is that you can get at some widgets outside the __init__ function, but apparently I cannot do that with the V and HBoxes. 

example: the combo box is referred to in 
```
    
def changed_cb(self, combobox):
        model = combobox.get_model()
        index = combobox.get_active()
        if index > -1:
            print model[index][0], 'selected'
```

from [http://www.pygtk.org/pygtk2tutorial/examples/comboboxwrap.py](http://www.pygtk.org/pygtk2tutorial/examples/comboboxwrap.py)

and yet I cant seem to use a passed VBox. 

```

def newlistbutton(self, secondary):
    newbut = gtk.Button("button")
    newbut.connect('clicked', self.closeapp)
    newbut.show()
    secondary.pack_start(newbut, False, False, 0)

```

Am I that obtuse? Isnt it counter intuitive?  The error I get says gtk.Button object has no attribute 'pack_start'.

So I pass in secondary to my function and use print(type(secondary)) as the first line and it tells me that secondary is a gtk.Button. Yet outside that function it prints its type correctly as a VBox. 

code with the print(type(secondary)) error checks: lines 37, 40 and 55.
[http://dl.dropbox.com/u/3735901/windowset.py](http://dl.dropbox.com/u/3735901/windowset.py)

---

### Post by StephenF on 2010-09-05
> **OgreProgrammer said:**
> Am I that obtuse?
In your original code.
```

addListbutton.connect('clicked', self.newlistbutton(funcbutton, secondary, 'boo'))

```
Wants to look something like.
```

addListbutton.connect('clicked', self.newlistbutton, funcbutton, secondary, 'boo')

```
The former runs the newlistbutton method then and there, takes the return value, a None, as the function to call.

The button you are getting is probably the widget that you used to trigger the callback. Just because you called it secondary won't make it magically pull secondary from the __init__ method. 

[http://library.gnome.org/devel/pygtk/stable/class-gtkbutton.html#signal-gtkbutton--clicked](http://library.gnome.org/devel/pygtk/stable/class-gtkbutton.html#signal-gtkbutton--clicked)
Note that when using class methods to prepend self.
Your true secondary value would be the user_param1, which you would need to pass in from the definition in the button's connect method.

Keep this under your hat, as they say.
[http://library.gnome.org/devel/pygtk/2.16/](http://library.gnome.org/devel/pygtk/2.16/)

If you really want to stuff another widget in a button use the add method.

---

### Post by OgreProgrammer on 2010-09-07
Thanks StephenF. I appreciate the time you devoted to alleviating my density.

---

