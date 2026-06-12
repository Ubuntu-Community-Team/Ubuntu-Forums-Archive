---
title: "[SOLVED] Detect running directory in Python"
date: 2008-06-04
forum: Programming Talk
---

### Post by gfa on 2008-06-04
Hello, i'm a novice Pythoner, so I have a problem with a little script (see the end).

When the script is called inside the directory have no problem, but if you run it from OTHER directory, it claims cant find the Glade file (gobject.GError).

I think I would solve passing to builder.add_from_file() the current path where the both files are (*.py and *.glade.xml), **but how could I do that?**

This is my script (obviosly there is a myGlade.glade.xml in the same path of the *.py, which is a Glade converted with *gtk-builder-convert*):
[PHP]
import sys

try:
    import pygtk
    pygtk.require('2.0')
    import gtk
except:
    print "You need PyGTK installed to run it"
    sys.exit(-1)
    

class myGlade:
    def on_main_window_destroy(self, widget, data=None):
        gtk.main_quit()
     
    def __init__(self):
        builder = gtk.Builder()
        builder.add_from_file("myGlade.glade.xml")
        
        self.main_window = builder.get_object("main_window")
        builder.connect_signals(self)

    
if __name__ == "__main__":
    myApp = myGlade()
    myApp.main_window.show()
    gtk.main()

[/PHP]

Thank you for any help or idea.
gFa

---

### Post by imdano on 2008-06-04
I think what you want to do here is just make sure it's always run from the same directory every time.[php]import os
...
if __name__ == "__main__":
    os.chdir("my/directory/")
    myApp = myGlade()
    myApp.main_window.show()
    gtk.main()  [/php]

---

### Post by dje on 2008-06-04
You could try:
```
import os

cwd = os.getcwd()
os.chdir(cwd)
```

hope that helps,
dje

---

### Post by gfa on 2008-06-04
> **imdano said:**
> I think what you want to do here is just make sure it's always run from the same directory every time.[php]import os

mmm, no, i would prefer to get the location of the file being executed and then pass it to the GtkBuilder.add_from_file(), example:

(if both files are under /home/tmp/myApp/):

/home/tmp/myApp/
  myApp.py
  myGlade.glade.xml

[PHP]current_path = WHAT_FUNCTION?? + "myGlade.glade.xml"
builder.add_from_file(current_path)[/PHP]

***WHAT_FUNCTION??*** should return a string containing: /home/tmp/myApp/.

That way, i can execute the script:
```
  ./myApp.py                #from /home/tmp/myApp/
  myApp/myApp.py            #from /home/tmp/
  /home/tmp/myApp/myApp.py  #from /
```

Thanks...
:)

---

### Post by dje on 2008-06-04
ok so you want to get the home directory + /myapp? try this:
```
home = os.environ['HOME']
prog_dir = home + "/myApp"

```
so prog_directory would be the "WHAT_FUNCTION", is that what you want?

dje

---

### Post by Can+~ on 2008-06-04
[PHP]sys.path[0][/PHP]

Returns the place of the current script, in the sys module. Recommended to use os.path.join() to attach the filename after, so it can use both "/" and "\" depending on the platform.

---

### Post by gfa on 2008-06-04
> **dje said:**
> You could try:
cwd = os.getcwd()
dje

mmm, just close, i tried this, but that function returns me the location where the script is runned, not the location where the files are...

for example in:

```
/home/tmp/myApp/myApp.py   #running the app from /
```

This function returns me: "/" so that is not working for me :(

I explained better what i need in:
[http://ubuntuforums.org/showpost.php?p=5114706&postcount=4](http://ubuntuforums.org/showpost.php?p=5114706&postcount=4)

---

### Post by dje on 2008-06-04
see my second post above, is that what you want?

dje

---

### Post by gfa on 2008-06-04
> **Can+~ said:**
> [PHP]sys.path[0][/PHP]

Returns the place of the current script, in the sys module.

[B]
YES!!! thanks... this is what i need...[/B]

---

