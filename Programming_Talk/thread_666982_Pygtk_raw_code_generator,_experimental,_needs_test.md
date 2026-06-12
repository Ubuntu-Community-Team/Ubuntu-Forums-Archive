---
title: "Pygtk raw code generator, experimental, needs testing"
date: 2008-01-13
forum: Programming Talk
---

### Post by paxmanchris on 2008-01-13
Hello PyGtk Programmers. I am currently writing a script that will take a glade file (written in glade 3) and generate python code, without using libglade.

the code is here:
[https://code.launchpad.net/~paxmanchris/+junk/modgtc](https://code.launchpad.net/~paxmanchris/+junk/modgtc)
and attached in a zip.


the code will eventually be part of [gladex]("https://launchpad.net/gladex"). And so far it pretty functional.

GtkMenus do not work yet. I plan to use gtk.ItemFactory, because to create the menu widget by widget is possible, but makes the code complicated.

any ways included with modgtc are glade files. the only one that does not work with modgtc is example.glade.

to generate raw code:
```

cd /path/to/modgtc/dir/

./modgtc inputglade.glade outputpythonfile.py


#and if you want to use the glade file included, do:
./modgtc various.glade out.py
#then do:
python out.py
#this runs the file, hit clt -> c to exit

```

What I would like from the programming community is feedback on the output style.
currently its all bunched up in one file. My plan it to put call backs and widget creation into separate files. 

also, compared to other python glade to code programs, what do you think of this one?

any other comments or suggestions are welcomed.

---

### Post by Quikee on 2008-01-14
Instead of your own template in modgtc.py you could use string.Template

Example:
[PHP]
from string import Template
template = Template("My name is $name and I live in $city")
substitutedString = template.substitute(name="Tomaz", city="Maribor")
[/PHP]

See [http://docs.python.org/lib/node40.html]("http://docs.python.org/lib/node40.html")

Also propertys is correstly spelled properties.

Instead of:
[PHP]if packing.has_key("type")[/PHP]
I prefer (because it reads like a sentence):
[PHP]if "type" in packing:[/PHP]

Instead of:
[PHP]for key in dict.keys():
    value = dict[key][/PHP]
I prefer:
[PHP]for key, value in packing.itervalues()[/PHP]

Generally I don't like the code (of the generator) - it's unnecessary complicated and hard to read. For example create_program is one huge function but if could be many smaller functions or even better - a class (or more of them). The idea is interesting on the other hand but code generation can get quite messy for python.

---

### Post by paxmanchris on 2008-01-16
i do agree with you the code is messy. 

mind you it is sill in baby stages of creation. and the finally overhall will be to run it with a gui.


thanks very much for the suggestions i will take them in to consideration.



where you able to get it to work?

what do you think of the output?

---

### Post by Acglaphotis on 2008-01-16
I hate writing GUI by hand so i'll give it try. Sounds promising : ).

---

### Post by Wybiral on 2008-01-16
Can you post some of the output from a simple GUI so we don't have to download, build a GUI, and run it?

---

### Post by charlie763 on 2008-01-17
> **Wybiral said:**
> Can you post some of the output from a simple GUI so we don't have to download, build a GUI, and run it?

Download modgtc.zip attached to paxmanchris' post above, extract it, and move into that directory at the terminal. Then execute
```
./modgtc.py various.glade out.py
python out.py

```
Attached is out.py, which I made using these instructions.

> **Acglaphotis said:**
> I hate writing GUI by hand so i'll give it try. Sounds promising : ).
You may want to give [Gladex]("https://launchpad.net/gladex") a try. There isn't a PPA for it, so you'll have to download the [packages]("https://launchpad.net/gladex/+download") directly. The output uses libglade, so unless you have some reason for not using libglade, it's probably a good solution for you. (I'm one of the Gladex developers.)

---

### Post by Wybiral on 2008-01-17
> **charlie763 said:**
> Download modgtc.zip attached to paxmanchris' post above, extract it, and move into that directory at the terminal. Then execute
```
./modgtc.py various.glade out.py
python out.py

```
Attached is out.py, which I made using these instructions.

I know HOW to do it, I just think they would get more comments if people didn't have to download something.

After looking at the source posted by charlie763, I do have one big problem with the style of the code, it uses tabs! According to the [PEP8]("http://www.python.org/dev/peps/pep-0008/") you should use four spaces, not tabs. This is a very common standard in Python. Also, the "#END# labelN as a GtkLabel ##" doesn't have a newline  (I'm guessing its supposed to since the rest of them do).

---

### Post by charlie763 on 2008-01-17
I agree that it should conform to the four space standard. I think modgtc has the indentation as a variable that can be set to anything. Once it's finished and in [Gladex]("https://launchpad.net/gladex") it will be like the other plugins and have the indentation style as a preference.

Here is the generated source code as suggested by Wybiral.
```
#!/usr/bin/env python


import pygtk
pygtk.require('2.0')
import gtk

class monkey:

    def __init__(self):
        ## window1 as a GtkWindow ##
        window1 = gtk.Window(gtk.WINDOW_TOPLEVEL)
        
        window1.set_property("visible", True)
        window1.set_property("events", gtk.gdk.POINTER_MOTION_MASK | gtk.gdk.POINTER_MOTION_HINT_MASK | gtk.gdk.BUTTON_PRESS_MASK | gtk.gdk.BUTTON_RELEASE_MASK)
        
        
        #END# window1 as a GtkWindow ##

        ## notebook1 as a GtkNotebook ##
        notebook1 = gtk.Notebook()
        
        notebook1.set_property("visible", True)
        notebook1.set_property("can_focus", True)
        notebook1.set_property("events", gtk.gdk.POINTER_MOTION_MASK | gtk.gdk.POINTER_MOTION_HINT_MASK | gtk.gdk.BUTTON_PRESS_MASK | gtk.gdk.BUTTON_RELEASE_MASK)
        
        
        window1.add(notebook1)
        #END# notebook1 as a GtkNotebook ##

        ## button1 as a GtkButton ##
        button1 = gtk.Button("gtk-about",None,True)
        
        button1.set_property("can_focus", True)
        button1.set_property("visible", True)
        button1.set_property("use_stock", True)
        button1.set_property("receives_default", True)
        button1.set_property("events", gtk.gdk.POINTER_MOTION_MASK | gtk.gdk.POINTER_MOTION_HINT_MASK | gtk.gdk.BUTTON_PRESS_MASK | gtk.gdk.BUTTON_RELEASE_MASK)
        
        
        #END# button1 as a GtkButton ##

        ## label1 as a GtkLabel ##
        label1 = gtk.Label()
        
        label1.set_property("visible", True)
        label1.set_property("events", gtk.gdk.POINTER_MOTION_MASK | gtk.gdk.POINTER_MOTION_HINT_MASK | gtk.gdk.BUTTON_PRESS_MASK | gtk.gdk.BUTTON_RELEASE_MASK)
        label1.set_property("label", "page 1")
        
        
        notebook1.append_page(button1, label1)
        notebook1.child_set(button1,"tab_fill", False)        #END# label1 as a GtkLabel ##

        ## vbox1 as a GtkVBox ##
        vbox1 = gtk.VBox(False,0)
        
        vbox1.set_property("visible", True)
        vbox1.set_property("events", gtk.gdk.POINTER_MOTION_MASK | gtk.gdk.POINTER_MOTION_HINT_MASK | gtk.gdk.BUTTON_PRESS_MASK | gtk.gdk.BUTTON_RELEASE_MASK)
        
        
        #END# vbox1 as a GtkVBox ##

        ## button2 as a GtkButton ##
        button2 = gtk.Button("button",None,True)
        
        button2.set_property("can_focus", True)
        button2.set_property("visible", True)
        button2.set_property("receives_default", True)
        button2.set_property("events", gtk.gdk.POINTER_MOTION_MASK | gtk.gdk.POINTER_MOTION_HINT_MASK | gtk.gdk.BUTTON_PRESS_MASK | gtk.gdk.BUTTON_RELEASE_MASK)
        
        
        vbox1.add(button2)
        #END# button2 as a GtkButton ##

        ## button4 as a GtkButton ##
        button4 = gtk.Button("button",None,True)
        
        button4.set_property("can_focus", True)
        button4.set_property("visible", True)
        button4.set_property("receives_default", True)
        button4.set_property("events", gtk.gdk.POINTER_MOTION_MASK | gtk.gdk.POINTER_MOTION_HINT_MASK | gtk.gdk.BUTTON_PRESS_MASK | gtk.gdk.BUTTON_RELEASE_MASK)
        
        
        vbox1.add_with_properties(button4, "position", 1)
        #END# button4 as a GtkButton ##

        ## label2 as a GtkLabel ##
        label2 = gtk.Label()
        
        label2.set_property("visible", True)
        label2.set_property("events", gtk.gdk.POINTER_MOTION_MASK | gtk.gdk.POINTER_MOTION_HINT_MASK | gtk.gdk.BUTTON_PRESS_MASK | gtk.gdk.BUTTON_RELEASE_MASK)
        label2.set_property("label", "page 2")
        
        
        notebook1.append_page(vbox1, label2)
        notebook1.child_set(vbox1,"position", 1,"tab_fill", False)        #END# label2 as a GtkLabel ##

        ## button3 as a GtkButton ##
        button3 = gtk.Button("button",None,True)
        
        button3.set_property("can_focus", True)
        button3.set_property("visible", True)
        button3.set_property("receives_default", True)
        button3.set_property("events", gtk.gdk.POINTER_MOTION_MASK | gtk.gdk.POINTER_MOTION_HINT_MASK | gtk.gdk.BUTTON_PRESS_MASK | gtk.gdk.BUTTON_RELEASE_MASK)
        
        
        #END# button3 as a GtkButton ##

        ## label3 as a GtkLabel ##
        label3 = gtk.Label()
        
        label3.set_property("visible", True)
        label3.set_property("events", gtk.gdk.POINTER_MOTION_MASK | gtk.gdk.POINTER_MOTION_HINT_MASK | gtk.gdk.BUTTON_PRESS_MASK | gtk.gdk.BUTTON_RELEASE_MASK)
        label3.set_property("label", "page 3")
        
        
        notebook1.append_page(button3, label3)
        notebook1.child_set(button3,"position", 2,"tab_fill", False)        #END# label3 as a GtkLabel ##


    def main(self):
        gtk.main()

try:
    if __name__ == "__main__":
        prog = monkey()
        prog.main()
except KeyboardInterrupt:
    print "safe exit"
    pass
```

Would anyone be willing to reformat the above code (or a few snippets) the way they feel it should look? Maybe add some comments to the code with any detailed information.

---

### Post by paxmanchris on 2008-01-17
thank you charlie for responding to the comments. for some reason I am not getting email notification. 

this:
 #END# notebook1 as a GtkNotebook ##

is meant to be that way. to denote the end of setting up notebook1.

thank you
and thanks everyone for trying it out.

fell free to keep on playing with it and commenting here, all comments will be taken into consideration while I code.

---

