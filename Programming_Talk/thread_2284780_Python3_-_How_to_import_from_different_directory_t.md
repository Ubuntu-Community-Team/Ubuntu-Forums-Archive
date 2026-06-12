---
title: "Python3 - How to import from different directory to access from /usr/bin"
date: 2015-07-01
forum: Programming Talk
---

### Post by flaymond on 2015-07-01
Hi everyone! I got a problem to import modules from different directory in Python3. I know that I can import module from different directory if that directory got** __init__.py **in it. So I try to do that like this -

```
myprogram/
    executable.py
    mymoduledir/
        __init__.py
        mymodule.py

```

Above structure let me access mymodule.py from executable.py -

```

#!/usr/bin/python3

from mymoduledir.mymodule import *

hi("Ubuntu") # Output "Hello, and Hi to the Ubuntu community"

```

but ***how I can import modules, say in /usr/lib ***(that don't have __init__.py (I need to access the module from /usr/bin))

If it's in C, it will be simple as ***#include "../to/path"*** and let me use the headers with ease from /usr/lib

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

So here is my question -

How can I access the modules in /usr/lib (says, the module name usr/lib/lizard.py, and accessed by /usr/bin/my_program.py)?

What or which "import" statement do I need to modify and invoke in my_program.py?

Thanks for every helps! :D

# Hmmppf, I think I gotta spend my time with my first programming language and learn the OO facilities it provide (Python), than switching to others and learn new syntax to do the same thing.

---

### Post by oldfred on 2015-07-01
Closed.
Duplicate here:
[http://ubuntuforums.org/showthread.php?t=2284781](http://ubuntuforums.org/showthread.php?t=2284781)

---

