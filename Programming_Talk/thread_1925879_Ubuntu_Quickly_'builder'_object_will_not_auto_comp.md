---
title: "Ubuntu Quickly 'builder' object will not auto complete in eclipse"
date: 2012-02-15
forum: Programming Talk
---

### Post by prestondocks on 2012-02-15
Hi All,

I am trying to use Quickly to develop a GUI App. I am editing my code with eclipse/Pydev just because I prefer that over Gedit, but no doubt that will fill this thread with opinions rather than an answer to my question.

Here is some basic information on my project in case it helps.

Project Name: ListFiles
Call backs to signals located in: ListFilesWindow.py

Here is the question.
I am using the 'builder' object to set_text() and get_text() but I don't get any code completion. 
I am assuming that this object has been created by 'Gtk.Builder'. If I make calls directly to Gtk.Builder code completion does work, but this is just creating a new object that is not linked to the GUI that has been created by Quickly.
The following line is included in ListFilesWindow.py by default
```
from gi.repository import Gtk # pylint: disable=E0611
```
But even if I comment out this line the programme still works.

So how do I get code completion to work on Gtk objects in eclipse and am I putting my callbacks in the correct file?

Here is the full content of my ListFilesWindow.py so far. It works fine, but if I could Gtk code completion to work that would be the icing on the cake.

```

# -*- Mode: Python; coding: utf-8; indent-tabs-mode: nil; tab-width: 4 -*-
### BEGIN LICENSE
# This file is in the public domain
### END LICENSE


import gettext
from gettext import gettext as _
gettext.textdomain('listfiles')

from gi.repository import Gtk # pylint: disable=E0611
import logging
logger = logging.getLogger('listfiles')

from listfiles_lib import Window
from listfiles.AboutListfilesDialog import AboutListfilesDialog
from listfiles.PreferencesListfilesDialog import PreferencesListfilesDialog

# See listfiles_lib.Window.py for more details about how this class works
class ListfilesWindow(Window):
    __gtype_name__ = "ListfilesWindow"
    
    def finish_initializing(self, builder): # pylint: disable=E1002
        """Set up the main window"""
        super(ListfilesWindow, self).finish_initializing(builder)

        self.AboutDialog = AboutListfilesDialog
        self.PreferencesDialog = PreferencesListfilesDialog

        # Code for other initialization actions should be added here.

    def buttonClick(self, builder):
        print "Hello World"
        self.builder.get_object('messageText').set_text("Hello")

```


Thanks
Simon

---

### Post by kermit666 on 2012-04-08
Hi Simon,

I'm also a PyDev fan and am trying to use it to edit Quickly projects.

I think that, given that you get the builder object as an argument for a method you created yourself, PyDev can't know what its type might be (for all it's concerned you could be calling it with a str object).

What you can do in PyDev is give it some hint so that it can infer the object's type. For example, if you have an assert command similar to:

```

assert isinstance(builder, Gtk.Builder)
builder.get_object('messageText').set_text("Hello")

```

PyDev will know that builder must be an instance of a Builder class and will offer autocompletions. This is supported in PyDev since 1.3.7 and you can read more details about it [here]("http://pydev.org/history_pydev.html").

Now, can I ask you a question. How did you set your launch configuration? What are you running? I have created a dev_run.py in the root of the project with the following code:

```

import project_name
project_name.main()

```

(because that is what the runner script in the bin/ folder calls in the end)

Now, running dev_run.py gives me an error with the following traceback:

```

/usr/lib/python2.7/dist-packages/gi/overrides/Gtk.py:391: Warning: g_object_set_property: construct property "type" for object `Window' can't be set after construction
  Gtk.Window.__init__(self, type=type, **kwargs)
Traceback (most recent call last):
  File "/home/kermit/programi/Eclipse/plugins/org.python.pydev.debug_2.0.1.2011051614/pysrc/pydevd.py", line 1141, in <module>
    debugger.run(setup['file'], None, None)
  File "/home/kermit/programi/Eclipse/plugins/org.python.pydev.debug_2.0.1.2011051614/pysrc/pydevd.py", line 925, in run
    pydev_imports.execfile(file, globals, locals) #execute the script
  File "/home/kermit/projekti/lp/desktopology/dev_run.py", line 2, in <module>
    desktopology.main()
  File "/home/kermit/projekti/lp/desktopology/desktopology/__init__.py", line 33, in main
    window = DesktopologyWindow.DesktopologyWindow()
  File "/home/kermit/projekti/lp/desktopology/desktopology_lib/Window.py", line 35, in __new__
    new_object.finish_initializing(builder)
TypeError: finish_initializing() takes exactly 3 arguments (2 given)

```

From the debugger I saw that this happens after reaching the code to initialize the window:

```
window = DesktopologyWindow.DesktopologyWindow()
```

It would be much better to launch the app from Eclipse instead of having to run 'quickly run' in a terminal - for one to be able to use the debugger :)

Cheers,
Dražen

---

### Post by kermit666 on 2012-04-08
Solved the problem and described it in [an edit to the Eclipse answer in this question]("http://askubuntu.com/a/101563/6418"):

Basically you first need to create your Quickly application as shown in the examples, then create a project in eclipse with PyDev (I used the same name) and set the location of your Quickly application as the project location. To be able to launch the project from Eclipse, rename the executable script called in the bin/ folder to something like *_launcher.py* (the name must differ from the module with the rest of the code).

Now, one nasty piece of work is to make the schema settings work (a bug about this is filed). First, to move automatic compiling from the quickly run script to *_launcher.py* append this code to the end of the file, right before the import command:

```
### BEGIN inserted from Quickly's run.py
# Compile schema if present
schemapath = os.path.abspath("data/glib-2.0/schemas")
if os.path.exists(schemapath):
    subprocess.call(["glib-compile-schemas", schemapath])
### END
```

Then to tell the application to look for schemas locally as well you have to edit the PyDev launch configuration and in the Environment tab add a variable XDG_DATA_DIRS with a value

*/usr/share/ubuntu:/usr/share/gnome:/usr/local/share/:/usr/share/:/path/to/your/project/data*

(adjust to match your project path)

You'll be able to modify any files and test if it works and even debug the program, and you can still use normal commands from quickly.

**Filed [a bug about this]("https://bugs.launchpad.net/quickly/+bug/976817") to the Quickly devs.**

---

