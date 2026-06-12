---
title: "Python Questions"
date: 2010-12-08
forum: Programming Talk
---

### Post by ngrieb on 2010-12-08
Hi all,
I was just trying to build some applets, applications, and games using python, pygame, and pygtk. I first want to say that I am doing this to learn Python. I have found it to be very powerful and very frustrating. I have played a bit with class programing as I know C++, but never really got into it too much because well I could more easily form and understand my own functions. At any rate I have been scouring the web and reading python books for many weeks looking for examples, and attempting to build a game, an applet, and a math program, but there are a few things I have been unsuccessful with.

First of all I wrote a small applet which I posted weeks ago here:

[http://ubuntuforums.org/showthread.php?t=1631548](http://ubuntuforums.org/showthread.php?t=1631548)

as far as I can tell the bonobo server file is choking (kills all my other applets when I move it to the servers dir), but knowing little about python and less about bonobo I have no idea why. Can someone have a look at it and tell me where I am going wrong?

I have in the last few days been attempting to learn PyGTK, which has me very confused. I attempted to use a GUI window development tool (can't remember what it was called (not eric though)), but that left me more confused than trying to simply write the python code. Anyways, I have a problem now. I want to have some combobox buttons at the top of my window, and when I open a file (using a push button), I should populate the list. Problem is I have no clue how to regenerate the comboboxes after the call (I was hoping for a simple combobox.update() function, but that would just make my life too easy). Also I was searching for a way to place graphics on pushbuttons...is there a simple way to do this?
I am brand new to gtk widgets and semi new to python so I'm sorry if I am completely clueless.

Thanks in advance.

---

### Post by ngrieb on 2010-12-08
Alright I found the server file consistency problem. But now there is a problem with the GUI interface correctly working in the applet. Also is there a better way to run a background process, which may need to be restarted, other than subprocess.Popen? I need to reset background processes if the user makes a change in settings. I also would like to know if there is a call to get the panel width and make the applet icon's alpha channel stay as is?

---

### Post by OgreProgrammer on 2010-12-09
I too found pygtk very frustrating, and I am much happier using wxpython.

---

### Post by ngrieb on 2010-12-10
I'll look into it. Yet another thing to learn in Python. 

The problem is that I have most of it kinda working already. I attempted to use Glade, but was very confused as to how to interface things and get buttons to line up in a single hbox, which of course means packing multiple vboxes into hboxes (ahhh). 

Anyways the main problem I am having now is with the subprocess calls to long running (more like sleeping) background processes. I need to kill or restart it if the user changes the setting. Keeping track of these and being able to kill and restart them is key. 

Also is there a way to loop back through or refresh the creation of widgets if a certain callback function is called? For instance:

Class Converse():
   global hi_bye_str
   
   def __init__(self):
       main_window()
       self.create_widgets()
       self.connect_signals()
       main_window.show_all()
       gtk_main()

   def create_widgets(self):
       hi_bye_srting = "?"
       self.vbox = gtk.VBox()
       self.button_hi = gtk.Button("Hi")
       self.button_bye = gtk.Button("Bye")
       label = gtk.Label(hi_bye_string)
       label.show()
       self.vbox.pack_start(button_hi)
       self.vbox.pack_start(button_bye)
       self.vbox.pack_start(label)
       self.main_menu.add(self.vbox)

   def connect_signals(self):
       self.hi_button.connect("clicked", self.hi)
       self.bye_button.connect("clicked", self.bye)

   def bye(self, widget):
       global label
       hi_bye_str = "Oh"
       time.sleep(4)
       hi_bye_str = "Leaving so soon?"
       time.sleep(4)
       hi_bye_str = "It must be late..."

   def hi(self, widget):
       global label
       hi_bye_str = "Good Morning"
       time.sleep(4)
       hi_bye_str = "How are you today?"
       time.sleep(4)
       hi_bye_str = "Need some coffee?"

Now I want to be able to change/update the label item while inside the call back function...i.e.
when the user selects the hi option I want the label area to update the conversation so that the user sees "Good Morning" ... pause 4 secs "How are you today?" pause 4 more "Need some coffee?". Should I structure my loops differently if I want this to be the case, or is there a way to do this??

---

### Post by ngrieb on 2010-12-14
Ok. I think I am slowly getting a hang of this. I have not messed with updating labels yet, but I might be able to find what I need easier, now that I know callback naming the patterns slightly better. 

Now I have an easier problem that I cannot figure out. How can I make a spinbutton show 2 integer places as in "01"? Increasing the decimal places only gives a "0.1" etc... thanks.

---

### Post by StephenF on 2010-12-14
> **ngrieb said:**
> How can I make a spinbutton show 2 integer places as in "01"? Increasing the decimal places only gives a "0.1" etc... thanks.
Short answer: with a lot of messing about. Enjoy...
```
# This code is GPL2.0+ and 80% Copyright (C) 2010 Andrew Clover (and@doxdesk.com)

import pygtk
pygtk.require("2.0")
import gtk

try:
    import ctypes
except ImportError:
    ctypes= None

class CustomSpinButton(gtk.SpinButton):
    """This code should make your eyes bleed"""

    def __init__(self, adjustment, climb_rate= 0.0, digits= 0):
        gtk.SpinButton.__init__(self, adjustment, climb_rate, digits)
        self._value = adjustment.get_value()
        self._iscustom = ctypes is not None
        if self._iscustom:
            self.connect('input', self._on_input)
            self.connect('output', self._on_output)

    def _on_input(self, _, ptr):
        if not repr(ptr).startswith('<gpointer at 0x'):
            self._iscustom= False
        if not self._iscustom or not isinstance(self.get_adjustment(), CustomAdjustment):
            return False
        try:
            value= self.get_adjustment().read_input(self.get_text())
        except ValueError:
            value= self._value
        addr= int(repr(ptr)[15:-1], 16)
        ctypes.c_double.from_address(addr).value= float(value) # danger!
        return True

    def _on_output(self, _):
        if not self._iscustom or not isinstance(self.get_adjustment(), CustomAdjustment):
            return False
        adj= self.get_adjustment()
        self.set_text(adj.write_output(adj.get_value()))
        return True

    def set_adjustment(self, adjustment):
        v= self.get_adjustment().get_value()
        gtk.SpinButton.set_adjustment(self, adjustment)
        if v!=adjustment.get_value():
            adjustment.set_value(v)
        else:
            adjustment.emit('value-changed')


class CustomAdjustment(gtk.Adjustment):
    def read_input(self, text):
        return float(text)
    def write_output(self, value):
        if int(value)==value:
            value= int(value)
        return str(value)


class LeadingZeroAdjustment(CustomAdjustment):
    def __init__(self, value = 0, min = 0, max = 99):
        CustomAdjustment.__init__(self, value, min, max, 1)
    def read_input(self, text):
        return int(text.lstrip("0"))
    def write_output(self, value):
        return "%02d" % value
        

if __name__ == "__main__":
    w = gtk.Window()
    w.connect("delete-event", lambda w, e: gtk.main_quit())
    cs = CustomSpinButton(LeadingZeroAdjustment())
    w.add(cs)
    w.show_all()
    gtk.main()
```

---

### Post by ngrieb on 2010-12-15
Thanks. Wow...really all that to add a zero in front? The eyes bleeding part is partially true. Perhaps is there a way to make the spinner contain a list of strings rather than integers? I'm thinking that might almost be easier than this...or is that what this is doing? Can I use this if it is (c)?

---

### Post by StephenF on 2010-12-15
> **ngrieb said:**
> Thanks. Wow...really all that to add a zero in front? The eyes bleeding part is partially true. Perhaps is there a way to make the spinner contain a list of strings rather than integers? I'm thinking that might almost be easier than this...or is that what this is doing? Can I use this if it is (c)?
You can put any text in a SpinButton. Here is a silly example. It's silly because there is no obvious numerical progression in the data forcing the user to step through each of the items until the right one is found. A ComboBox would be a better choice for this data set.
```

class BeatlesAdjustment(CustomAdjustment):
    band = ("John", "Paul", "Ringo", "George")
    # The base number is chosen to give enough room to show the longest text.
    base = 10 ** len(max(band, key=len)) 
    def __init__(self, value = 0):
        CustomAdjustment.__init__(self, value, self.base, self.base + len(self.band) - 1, 1)
    def read_input(self, text):
        return self.base + self.band.index(text) 
    def write_output(self, value):
        return self.band[int(value) - self.base]

```

---

### Post by ngrieb on 2010-12-16
Thanks. I am just trying to get a "minutes" spinner to not look ridiculous with only one digit (it works, but you just don't usually associate a one digit number with a time.) If I'm using a numerical spinner though is there a way to also set a null value like say if I want no minutes have a "--" character to signify this?

---

### Post by StephenF on 2010-12-16
> **ngrieb said:**
> Thanks. I am just trying to get a "minutes" spinner to not look ridiculous with only one digit (it works, but you just don't usually associate a one digit number with a time.) If I'm using a numerical spinner though is there a way to also set a null value like say if I want no minutes have a "--" character to signify this?
This untested code fragment will substitute "--" for zero, though you might want to add a new method to CustomAdjustment, possibly by subclassing it if you need more control.
```

class LeadingZeroAdjustment...
    ...
    def write_output(self, value):
        if value:
            return "%02d" % value
        else:
            return "--"

```

---

### Post by ngrieb on 2010-12-16
Thanks again. May I ask how you know all this? I can barely seem to find the calls I need to make different types of boxes and inputs...do you have any good resources you can pass on for learning pygtk?

Argh...one more problem in python (no gtk this time). Sorry I will try and make this the last question so this doesn't become a 100 page thread. Does Python have types? I took a google look and it seems as though something was happening in C or C++ not python. Anyways I am trying to form a point type...which I am fairly certain can be done with a class (in a python text I have this is how they do it)

class Point(Object):
def __init__(self,x,y,z,other):
self.x = x
self.y = y
etc.

now I need to create a list of Point objects, but this is where I get stuck. I'm not sure the best way to
list objects or numerical items for future processing (sorting)in python. In fortran 90 or C one could create a typedef Point and make a pointer array to these types...but here I have no idea how to go about this. other than a huge tupple string, which I would imagine would be monstrously slow...and I kinda want the speed here.

---

### Post by Vaphell on 2010-12-17
not sure if i understand, what do you mean by huge tuple string exactly?
this?

```
class Point:
  def __init__( self, x, y ):
    self.x = x
    self.y = y
  
plist = []
plist.append( Point(0,0) )
```

---

### Post by StephenF on 2010-12-17
> **Vaphell said:**
> not sure if i understand, what do you mean by huge tuple string exactly? this? [8< code example omitted]

Exactly that if allowed to grow. He also wants to be able to sort them but has not laid out any criteria. Sort by x, y, x+y, angle, distance from polar centre?

I think OPs problem is with the idea of sorting causing the list element data to be overwritten during sorting operations rather than just pointers to that data which is a quicker operation. This confusion is based on a misunderstanding of how variables are done in python.

There are namespaces at the module level (called global), the class level, the class instance level, locally within free functions and class methods. These namespaces contain names, and corresponding references to objects.

Lists are no different. They exist within namespaces and contain multiple unnamed references to objects, not the objects themselves. When an item is removed from the list only the reference is removed. In Python all variables are just names that currently are bound to a particular object.
---
PyGTK reference. I'm guessing you are just using the tutorial.
[http://library.gnome.org/devel/pygtk/stable/](http://library.gnome.org/devel/pygtk/stable/)

---

### Post by ngrieb on 2010-12-17
I'm sorry if I was not very specific, I will try again to explain what I want to do. I would like to be able to sort with respect to any variable in the point class, most likely through another function SortPointList(PointList, variable). I do not necessarily need to or care to reorder the point list, but I would like to assign a Point attribute after sorting the points in the point list called "point_id" that I can use as sorted order.

```

class Point:
  def __init__( self, x, y ):
    self.x = x
    self.y = y

plist = []
plist.append( Point(0,0) )

#Here is where I'm having trouble
#How can I call data from the Point object inside the List object?
#Is there a way to sort in this way afterwards?
def SortPoints(plist, variable):
  if variable == 'x':
     sort_wrt_x()
     #Depending on x value and other criteria assign a point number
     #Fairly sure I tried something like this...
     #Is this even legal?
     plist[i].Point.id = value
  if variable  == 'y':
     sort_wrt_y()
     ...


```

---

### Post by Vaphell on 2010-12-18
plist[i] is an instance of Point class already, so you got a redundancy there
plist[i].id = value is enough

you can use sort() which sorts the list in place (reorders elements). Since we've got objects here, we need to define a custom function that will return the sorting value of list elements. Example below sorts the list by x, y and r and assigns values to x/y/r_order attribute

```

#!/usr/bin/env python

import math

class Point:
  def __init__( self, x, y ):
    self.x = x
    self.y = y
  
plist = []

plist.append( Point( 0, 3 ) )
plist.append( Point( 4, 1 ) )
plist.append( Point( 3, 2 ) )
plist.append( Point( 3, 5 ) )
plist.append( Point( 4, 4 ) )

print "initial list"
for p in plist:
  print "%d. (%d,%d)" % ( plist.index( p ), p.x, p.y )
print
  
plist.sort( key = lambda p: p.x )
for p in plist:
  p.x_order = plist.index( p )
  
plist.sort( key = lambda p: p.y )
for p in plist:
  p.y_order = plist.index( p )

plist.sort( key = lambda p: math.sqrt( p.x**2 + p.y**2 ) )
for p in plist:
  p.r_order = plist.index( p )
  p.r = math.sqrt( p.x**2 + p.y**2 )

for p in plist:
  print "%d. (%d,%d) r=%f x_order=%d y_order=%d r_order=%d" % ( plist.index( p ), p.x, p.y, p.r, p.x_order, p.y_order, p.r_order )

```

i have no idea if such sorting is efficient or not, but at least it's incredibly easy
loops with x_order, y_order and r_order are optional because sorting itself reorders elements just like you want it, but i added them in case you want persistent info

---

### Post by StephenF on 2010-12-19
Looks like OP doesn't want an in-place sort. For that Python offers the more versatile sorted() function.
```

#!/usr/bin/env python

def show(point_data, title_text):
    print title_text
    for i, d in enumerate(point_data):
        print "%d. (%d,%d)" % (i, d.x, d.y )
    print

class Point:
    def __init__(self, x, y):
      self.x = x
      self.y = y

data = ((0,3), (4,1), (3,2), (3,5), (4,4))
initial = [Point(*d) for d in data]

show(initial, "unsorted point data")

after = sorted(initial, lambda a, b: cmp(a.x**2 + a.y**2, b.x**2 + b.y**2))

show(after, "sorted by magnitude")
show(initial, "original data is unchanged")

```

---

### Post by Vaphell on 2010-12-19
in general OP wants to read this to know what's available :)
[http://wiki.python.org/moin/HowTo/Sorting](http://wiki.python.org/moin/HowTo/Sorting)

---

### Post by ngrieb on 2010-12-19
Hmm...that is a bit to process. 

Vaphell:
Thanks for the clarification on how to gather the data from a list of class objects. I now see that.

Stephen F:
Lets see if I got this right:
So in the code below you are creating a pointer object which points to the data given in each tupple, and the sorted function gives you the pointers reordered as they are sorted? (only the pointers get sorted here so you are not moving huge chunks of data, right).

---

### Post by StephenF on 2010-12-19
> **ngrieb said:**
> Stephen F:
Lets see if I got this right:
So in the code below you are creating a pointer object which points to the data given in each tupple, and the sorted function gives you the pointers reordered as they are sorted? (only the pointers get sorted here so you are not moving huge chunks of data, right).
A second list is built that refers to the same objects as the first but in a different order.

Lists don't really contain their objects though it sometimes helps to think that they do.
```

>>> l = [1, 2]
>>> a = l[0]
>>> id(l[0])
134573456
>>> id(a)
134573456

```
Is 1 in both l[0] and a? Or neither? If you said the list, what if you had created a before l?

In the code example I could do a del l[0]. Did I then move 1 out of l and into a? It would appear its object id was the same throughout.

Variables in Python behave somewhat like pointers though you need to have another object on hand in order to reassign one.

---

### Post by ngrieb on 2011-01-03
Alright. Thanks a lot. Just trying to get a hang of python, it is very powerful, but I have heard that it is also fairly slow with computations. (But there are always options like numpy and python to Fortran).

I currently have two applets that are just about ready to be posted, but I am having some troubles with gnome. If I run them in a terminal, they run as they should but if I run them as applets they do not work properly...and one of them does not run at all. This is what is happening with the one that does work as an applet:

[http://ubuntuforums.org/showthread.php?t=1647737](http://ubuntuforums.org/showthread.php?t=1647737)

Any ideas? I have a few print statements throughout the code for debugging...could this be the problem? I can post the applet server files and possibly the code...if needed, but some of them are fairly long.

Here is what I have for the server file that doesn't work at all:

```

<oaf_info>
<oaf_server iid="OAFIID:NWSApplet_Factory" type="exe" location="/usr/lib/NWS/NWSApplet.py">
            
        <oaf_attribute name="repo_ids" type="stringv">
                <item value="IDL:Bonobo/GenericFactory:1.0"/>
                <item value="IDL:Bonobo/Unknown:1.0"/>
        </oaf_attribute>
        <oaf_attribute name="name" type="string" value="NWSApplet"/>
        <oaf_attribute name="description" type="string" value="NWS Weather Forecast"/>
</oaf_server>

<oaf_server iid="OAFIID:NWSApplet" type="factory" location="OAFIID:NWSApplet_Factory">

        <oaf_attribute name="repo_ids" type="stringv">
                <item value="IDL:GNOME/Vertigo/PanelAppletShell:1.0"/>
                <item value="IDL:Bonobo/Control:1.0"/>
                <item value="IDL:Bonobo/Unknown:1.0"/>
        </oaf_attribute>
        <oaf_attribute name="name" type="string" value="NWSApplet"/>
        <oaf_attribute name="description" type="string" value="NWS Weather Forecast"/>
        <oaf_attribute name="panel:category" type="string" value="Utility"/>
        <oaf_attribute name="panel:icon" type="string" value="/usr/lib/NWS/AppletWindowIcon.png"/>
</oaf_server>
</oaf_info>

```

It shows up in the applet menu but fails to load with an OAFIID error.

---

