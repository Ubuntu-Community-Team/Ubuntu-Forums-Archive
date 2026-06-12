---
title: "How to freeze a Python script using pysqlite2?"
date: 2006-06-21
forum: Programming Talk
---

### Post by ketsugi on 2006-06-21
I'm trying to freeze a python script which imports dbapi2 from pysqlite2 but it's not working at all.

Using the regular freeze.py, I copied the entire pysqlite2 directory into my source directory and ran

```
python ~/Development/Python-2.4.3/Tools/freeze/freeze.py -X codecs -X copy -X distutils -X encodings -X locale -X macpath -X ntpath -X os2emxpath -X popen2 -X pydoc -X warnings -m dumbledore.py
```

followed by 'make'. Trying to run the executable gave me:

```
ketsugi@Asahara:/tmp/freezey$ ./dumbledore
Traceback (most recent call last):
  File "/home/ketsugi/Documents/Work/Yew Kee/AustDow/Dumbledore/dumbledore.py", line 5, in ?
    from database import sqlite_module as dbmod
  File "/home/ketsugi/Documents/Work/Yew Kee/AustDow/Dumbledore/database/sqlite_module.py", line 4, in ?
    from pysqlite2 import dbapi2 as sqlite
  File "/home/ketsugi/Documents/Work/Yew Kee/AustDow/Dumbledore/pysqlite2/dbapi2.py", line 32, in ?
    from pysqlite2._sqlite import *
ImportError: No module named _sqlite

```

I tried an alternate freeze called [cx_Freeze](http://starship.python.net/crew/atuining/cx_Freeze/) and got this output instead:

```
ketsugi@Asahara:~/Documents/Work/Yew Kee/AustDow/Dumbledore$ dist/dumbledore
Traceback (most recent call last):
  File "/usr/local/bin/initscripts/Console.py", line 26, in ?
    exec code in m.__dict__
  File "dumbledore.py", line 5, in ?
    from database import sqlite_module as dbmod
  File "database/sqlite_module.py", line 4, in ?
    from pysqlite2 import dbapi2 as sqlite
  File "pysqlite2/dbapi2.py", line 32, in ?
    from pysqlite2._sqlite import *
  File "ExtensionLoader.py", line 12, in ?
ImportError: /home/ketsugi/Documents/Work/Yew Kee/AustDow/Dumbledore/dist/pysqlite2._sqlite.so: undefined symbol: PyUnicodeUCS4_AsUTF8String

```

Any ideas? I'm trying to compile this script so I can distribute it to my professor and not require him to install Python and PySQLite. I'll eventually try to freeze it on win32 for him, but for now I'm just playing with the Linux version and finding it quite depressing that I can't get this to work here. I assume that trying it on Windows will be an even bigger pain.

---

