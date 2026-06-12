---
title: "can't import python lib"
date: 2007-11-29
forum: Programming Talk
---

### Post by skunkwerk on 2007-11-29
Hi, I've been having problems running a simple 2-line python program.  It works on Windows, but not on 2 linux machines I've tried it on.  I'm aware that line endings are different on the two platforms so I typed it up in vi, but I still got the error "no filename given"

#!/usr/bin/python
import zlib

when I replace zlib with another library, like sys, it works fine and doesn't complain.  I have zlib.so in my /usr/lib/python2.4/lib-dynload directory.

any suggestions?

thanks

---

### Post by aquavitae on 2007-11-29
The location of zlib.so shouldn't matter, but to import zlib you need a python interface, zlib.py.  Do you have zlib.py anywhere? (possibly zlib.pyc or zlib.pyo)

---

### Post by skunkwerk on 2007-11-29
thanks,
   I don't seem to have any of the 3 files you mentioned.  how do i fix that - do i need to install some package?

---

### Post by aquavitae on 2007-11-30
I've just had a look at the python docs and it seems zlib should be built in.  I'm not at my linux pc at the moment so I can't check it there, but it seems to work on windows, although I can't find a zlib file either, so maybe it is built in.  I don't realy know how python is put together so I don't know if this is a reasonable assumption, but in any case it should work.  What if you start a python command line (type python in a terminal) and 'import zlib'.  Line ending etc shouldn't make a difference then.

---

