---
title: "Problem running Python scripts"
date: 2009-09-25
forum: Programming Talk
---

### Post by gbablon on 2009-09-25
Hi all.

I've written a Glade / Python script that exists in the folder Projects/PyHelloWorld/ in my home directory.

I can run the script (which just loads a small, brain dead GUI) from a terminal by going to the folder (cd) and from there calling ```
python PyHelloWorld.py
```This works fine.

However, I'd like to be able to run the script without navigating to the folder within terminal. For instance, if I'm in the /Projects directory, aka. one folder up, I think I should be able to do 

```
python /PyHelloWorld/PyHelloWorld.py
```This gives me the following error however:

```
(PyHelloWorld.py:4946): libglade-WARNING **: could not find glade file 'pyhelloworld.glade'
Traceback (most recent call last):
  File "PyHelloWorld/PyHelloWorld.py", line 30, in <module>
    hwg = HellowWorldGTK()
  File "PyHelloWorld/PyHelloWorld.py", line 22, in __init__
    self.wTree = gtk.glade.XML(self.gladefile) 
RuntimeError: could not create GladeXML object
```Even though the pyhelloworld.glade file exists (and is found when I call the python script from within its local directory).

Any ideas? I'm guessing this has something to do with permissions on the .glade file, but I really don't know! I need to be able to access the script remotely because eventually I want to hook it up to Ubuntu's start up apps (System -> Preferences -> Startup Applications).

Cheers!

---

### Post by DaithiF on 2009-09-25
Hi,
its not permissions that are the problem, just that if your not starting from the script directory then python needs to know that your glade file is in the same directory as your script, rather than the current directory.
import os.path if not already imported, then change the line like this:
```
self.wTree = gtk.glade.XML(os.path.join(os.path.dirname(__file__), self.glade_file))
```

---

### Post by gbablon on 2009-09-25
DaithiF,

Thank you very much, that did the trick!

Best regards.

---

