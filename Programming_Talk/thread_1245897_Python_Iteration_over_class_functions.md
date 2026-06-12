---
title: "Python: Iteration over class functions?"
date: 2009-08-21
forum: Programming Talk
---

### Post by kumoshk on 2009-08-21
In Python, is it possible to iterate over the function objects of any given class/object?

---

### Post by kumoshk on 2009-08-21
Sorry. I asked a similar question before and I got an answer (forgot about that). However, the following method gets everything. Is it possible just to get functions? It would be nice if I could do it without including __init__, other things surrounded by underscores, and inherited functions.

This is the code to get everything (instance variables and all):
from inspect import getmembers
getmembers(someObjectOrClass)

---

### Post by slakkie on 2009-08-21
I used this to check which functions all the classes had, including the documentation:

```

#!/usr/bin/env python
#

import include_path
import os
import string
import sys

# Setting up the connection and execute commands
def info(object, spacing=10, collapse=1):
    """Print methods and doc strings.
    Takes module, class, list, dictionary, or string."""

    print object.__module__
    print object.__doc__
    print ""

    methodList = [method for method in dir(object) if callable(getattr(object, method))]
    processFunc = collapse and (lambda s: " ".join(s.split())) or (lambda s: s)
    print "\n".join(["%-40s %s" %
                      (method.ljust(spacing),
                       processFunc(str(getattr(object, method).__doc__)))
                     for method in methodList])

    print " "

def load_modules(dir, module_prefix = None):
    files = os.listdir(dir)
    files.sort()
    for filename in files:
        if not filename.endswith('.py') or not filename[0:1].isupper():
            continue

        filename = filename[:-3]
        if module_prefix == None:
            module_name = filename
        else:
            module_name = '%s.%s' % (module_prefix, filename)

        # Work around for http://bugs.jython.org/issue1111
        # mod = __import__(modules, {}, {}, [ filename ], -1)
        mod = __import__(module_name)
        components = module_name.split('.')
        for comp in components[1:]:
            mod = getattr(mod, comp)

        c = getattr(mod, filename)
        o = c()
        info(o)


path = "/home/wesleys/sbox/blpython/src/lib/OSS/bladelogic"

#sys.path.append(path)
load_modules(path, "OSS.bladelogic")
#load_modules(path)

```

Output is something linke this:

```

OSS.bladelogic.Utility
permissions class, implements some default permissions functions

__init__                                 Initialize the class
_cmd                                     Executes the JLI command
_log_error                               Log an error in case we need to log it..
_unsupported                             Function which tells the user the called function is not supported..
jli                                      Set a jli component so we can call it
print_me                                 Function just here for testing.. to be removed


```

---

