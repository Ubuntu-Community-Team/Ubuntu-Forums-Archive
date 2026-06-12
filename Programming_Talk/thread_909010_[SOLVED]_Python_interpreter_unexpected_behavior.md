---
title: "[SOLVED] Python interpreter unexpected behavior"
date: 2008-09-03
forum: Programming Talk
---

### Post by tbunix on 2008-09-03
tried to list all the modules available via the built-in help...
Did not expect the the interpreter to actually start modules - just find and list them
This locks up the terminal and disables Compiz window decorators
What did I do wrong?

Ubuntu 8.0.4.1

[PHP]~$ python
Python 2.5.2 (r252:60911, Jul 31 2008, 17:28:52) 
[GCC 4.2.3 (Ubuntu 4.2.3-2ubuntu7)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> help()

Welcome to Python 2.5!  This is the online help utility.

If this is your first time using Python, you should definitely check out
the tutorial on the Internet at http://www.python.org/doc/tut/.

Enter the name of any module, keyword, or topic to get help on writing
Python programs and using Python modules.  To quit this help utility and
return to the interpreter, just type "quit".

To get a list of available modules, keywords, or topics, type "modules",
"keywords", or "topics".  Each module also comes with a one-line summary
of what it does; to list the modules whose summaries contain a given word
such as "spam", type "modules spam".

help> modules

Please wait a moment while I gather a list of all available modules...

 * Detected Session: gnome
 * Searching for installed applications...
 * NVIDIA on Xorg detected, exporting: __GL_YIELD=NOTHING
 * Starting Compiz
 ... executing: compiz.real --replace --sm-disable --ignore-desktop-hints ccp
compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
compiz.real (core) - Warn: pixmap 0x160013a can't be bound to texture
Starting gtk-window-decorator
/usr/bin/gtk-window-decorator: Screen 0 on display ":0.0" already has a decoration manager; try using the --replace option to replace the current decoration manager.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

[/PHP]

---

### Post by Bachstelze on 2008-09-03
Nothing to do with Python, those are init messages. Are you using a VT or xome kind of X terminal emulator?

---

### Post by tbunix on 2008-09-03
That is the standard gnome desktop terminal installed with Ubuntu Hardy.

---

### Post by tbunix on 2008-09-03
I agree they are initialization messages

but why is the python interpreter re-initialing the X system when 

>>>help()
blah blah blah
>modules

is entered?

---

### Post by pmasiar on 2008-09-03
Maybe Python help does not like Compiz? Can you turn Compiz off and try again?

---

### Post by tbunix on 2008-09-03
disabled compiz in sytem->preferences->appearance->visual effects, none

disabled emerald and AWN in sytsem->sessions->startup

no change 

help> modules

still runs the gnome desktop startup and still tries to start compiz???

this is turning into one of those fun little puzzles.

assume this isn't a widely reported issue?
compiz + python help()

also happens in IDLE (be really weird if it didn't)

---

### Post by tbunix on 2008-09-03
at least I'm not alone

[http://www.nabble.com/Odd-behavior-of-python-module-listing-td17741929.html](http://www.nabble.com/Odd-behavior-of-python-module-listing-td17741929.html)

can't see where he found an answer either

---

### Post by tbunix on 2008-09-03
removing the compiz fusion icon did the trick for me.

Why the python interpreter is affected by that bit of useless code is a puzzle for another day--someone else?

so compiz works, emerald works, AWN works and so does the python builtin help(modules)

---

### Post by quodlibetor on 2008-10-17
Just came across this, it looks like fusion-icon is a python program (who knew?) that keeps a config file in /usr/share/pyshared-data:

```

locate fusion-icon | grep py:

/usr/share/doc/fusion-icon/copyright
/usr/share/pyshared-data/fusion-icon

```

and if you look at that file, it points to a whole bunch of other ones in pyshared:

```

most /usr/share/pyshared-data/fusion-icon:

[python-package]
format = 1
python-version = all
[pycentral]
version = 0.6.1
[files]
/usr/share/pyshared/FusionIcon=d
/usr/share/pyshared/FusionIcon/interface_qt4=d
/usr/share/pyshared/FusionIcon/interface_qt4/__init__.py=f
/usr/share/pyshared/FusionIcon/interface_qt4/main.py=f
/usr/share/pyshared/FusionIcon/interface_gtk=d
/usr/share/pyshared/FusionIcon/interface_gtk/__init__.py=f
/usr/share/pyshared/FusionIcon/interface_gtk/main.py=f
/usr/share/pyshared/FusionIcon/__init__.py=f
/usr/share/pyshared/FusionIcon/data.py=f
/usr/share/pyshared/FusionIcon/interface.py=f
/usr/share/pyshared/FusionIcon/parser.py=f
/usr/share/pyshared/FusionIcon/util.py=f
/usr/share/pyshared/FusionIcon/environment.py=f
/usr/share/pyshared/FusionIcon/execute.py=f
/usr/share/pyshared/FusionIcon/start.py=f
/usr/share/pyshared/fusion_icon-0.0.0_git.egg-info=f

```

I would imagine that help("modules") goes through all those, and at least one of them just automatically loads, instead of having a construct like
```

if __name__ == "__main__":
    init()

```

A quick grep of the directory doesn't reveal that construct anywhere, and while i'm a really (really) novice python programmer, and so don't know of any other equivalent equivalent thing to keep a file from being called when it's touched, it is a possibility.

And, now, switching the call to init in /usr/share/pyshared/FusionIcon/interface_gtk/main.py to use the `if __name__ == "__main__":' construction fixes my python  help(), although it breaks fusion icon :-D

---

### Post by tbunix on 2008-10-21
nice bit of detective work, quodlibetor!

haven't missed the compiz-fusion icon once since I uninstalled it;)

---

