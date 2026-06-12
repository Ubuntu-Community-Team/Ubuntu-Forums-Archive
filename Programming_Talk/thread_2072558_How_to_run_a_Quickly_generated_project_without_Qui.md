---
title: "How to run a Quickly generated project without Quickly?"
date: 2012-10-18
forum: Programming Talk
---

### Post by Aerivan on 2012-10-18
As stated above, I'm not sure how this is done. I'm a 4'th year Software Engineering student but haven't played much with Python yet. The reason for wanting to do this? Just to understand what's going on.

The general idea of what I want to do (but which doesn't work):
```

quickly create ubuntu-application foo
python foo/foo/FooWindow.py

```

How should something like this be done or why can't it?

---

### Post by juancarlospaco on 2012-10-18
I think its:   quickly run

---

### Post by Aerivan on 2012-10-19
> **juancarlospaco said:**
> I think its:   quickly run

Yes, but the question is if I can start the application only with the python command or something similar - not Quickly. "quickly run" is not allowed to be used for the duration of this thread.

The point is that I want to know exactly what happens when I issue "quickly run" by instead entering the corresponding commands myself.

---

### Post by juancarlospaco on 2012-10-19
**python file.py**

quickly run just run python file.py

whatever you used for filename on it.

---

### Post by Aerivan on 2012-10-20
Ok, so this is what I do:

```

vind@Jeeves:~/Code/Ubuntu$ quickly create ubuntu-application foo
Creating project directory foo
Creating bzr repository and committing
Launching your newly created project!
Congrats, your new project is setup! cd /storage/Code/Ubuntu/foo/ to start hacking.

vind@Jeeves:~/Code/Ubuntu$ cd foo/
vind@Jeeves:~/Code/Ubuntu/foo$ python 
bin/      .bzr/     data/     foo/      foo_lib/  help/     setup.py  tests/    
vind@Jeeves:~/Code/Ubuntu/foo$ python foo/
AboutFooDialog.py         FooWindow.pyc             PreferencesFooDialog.py
AboutFooDialog.pyc        __init__.py               PreferencesFooDialog.pyc
FooWindow.py              __init__.pyc              

vind@Jeeves:~/Code/Ubuntu/foo$ python foo/__init__.py
Traceback (most recent call last):
  File "foo/__init__.py", line 12, in <module>
    from foo import FooWindow
ImportError: No module named foo


```

I've tried this with every single file but __init__.py is my best bet since it has a main-function. __init__.py looks like this:

```

# -*- Mode: Python; coding: utf-8; indent-tabs-mode: nil; tab-width: 4 -*-
### BEGIN LICENSE
# This file is in the public domain
### END LICENSE

import optparse

from locale import gettext as _

from gi.repository import Gtk # pylint: disable=E0611

from foo import FooWindow

from foo_lib import set_up_logging, get_version

def parse_options():
    """Support for command line options"""
    parser = optparse.OptionParser(version="%%prog %s" % get_version())
    parser.add_option(
        "-v", "--verbose", action="count", dest="verbose",
        help=_("Show debug messages (-vv debugs foo_lib also)"))
    (options, args) = parser.parse_args()

    set_up_logging(options)

def main():
    'constructor for your class instances'
    parse_options()

    # Run the application.    
    window = FooWindow.FooWindow()
    window.show()
    Gtk.main()

```

Now, as shown above, simply running "python foo/__init__.py" doesn't work so what am I missing? Since I'm very new to Python the answer might very well be obvious to someone with more experience, at least I hope so.

---

### Post by spjackson on 2012-10-20
To work out what "quickly run" does, you need to look first at /usr/bin/quickly, then at /usr/share/quickly/templates/ubuntu-application/run.py

What it boils down to is:
```

quickly create ubuntu-application foo
XDG_DATA_DIRS=$PWD/foo/data:$XDG_DATA_DIRS foo/bin/foo

```

---

