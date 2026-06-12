---
title: "Netbeans 6.7 &amp; python - import errors with pygtk"
date: 2009-07-31
forum: Programming Talk
---

### Post by Tony Flury on 2009-07-31
I have just installed Netbeans 6.7 - and thought I would try out the debugger on an application which runs fine via the command line.

However when I run the application from Netbeans, i get the following error :
Netbeans Debugger output : 
```

>>>Exception in thread MainThread:Traceback (most recent call last):
  File "/home/tony/netbeans-6.7/python1/jython-2.5/Lib/threading.py", line 247, in _Thread__bootstrap
    self.run()
  File "/home/tony/.netbeans/6.7/config/nbPython/debug/nbpythondebug/jpydaemon.py", line 590, in run
    exec self._cmd in self._myglobals,self._mylocals
  File "<string>", line 1, in <module>
  File "/home/tony/Development/python/calculator/calc.py", line 3, in <module>
    import app
  File "/home/tony/Development/python/calculator/app.py", line 1, in <module>
    import gui_main
  File "/home/tony/Development/python/calculator/gui_main.py", line 4, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 38, in <module>
    import gobject as _gobject
  File "/var/lib/python-support/python2.5/gtk-2.0/gobject/__init__.py", line 30, in <module>
    from gobject.constants import *
  File "/var/lib/python-support/python2.5/gtk-2.0/gobject/constants.py", line 22, in <module>
    from _gobject import type_from_name
ImportError: No module named _gobject

``` 

Netbeans run (nodebugger) output : 
```

Traceback (most recent call last):
  File "/home/tony/Development/python/calculator/calc.py", line 3, in <module>
    import app
  File "/home/tony/Development/python/calculator/app.py", line 1, in <module>
    import gui_main
  File "/home/tony/Development/python/calculator/gui_main.py", line 4, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 38, in <module>
    import gobject as _gobject
  File "/var/lib/python-support/python2.5/gtk-2.0/gobject/__init__.py", line 30, in <module>
    from gobject.constants import *
  File "/var/lib/python-support/python2.5/gtk-2.0/gobject/constants.py", line 22, in <module>
    from _gobject import type_from_name
ImportError: No module named _gobject

```

I also get very similar errors within Netbeans in the interactive console - when i import pygtk and the import gtk manually. 

In all cases it complains about not knowing the name _gobject (despite the earlier "import gobject as _gobject"). I can only assume that Netbeans is some how interfering in the namespaces - but i have no idea how to fix it.


Note that this application runs fine from the normal terminal.

[SOLVED] The project was bound to the default Python Platform, which did not have gtk in the path, so for some reason it found some (but not all) the gtk libraries Still odd though.

---

