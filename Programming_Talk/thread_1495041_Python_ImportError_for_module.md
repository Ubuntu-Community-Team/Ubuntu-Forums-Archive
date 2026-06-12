---
title: "Python: ImportError for module"
date: 2010-05-27
forum: Programming Talk
---

### Post by kalasoka on 2010-05-27
Hi All,

I've a package, 'my_app', which contains some files say, main.py, continent.py, country.py, and of course, __init__.py (which is blank in my case). There's another script, manage.py, which imports this package. The import lines look like:

```
import my_app
import my_app.main
```Finally, there's the 'setup.py' script that uses distutils to install the application.

I've installed the app using the setup script as sudo (which installs the Python package at appropriate location.) Now when I open Python interpreter, I'm able to import the package, and other modules inside it.

The problem is, my 'manage.py' script (located at /usr/local/bin) fails to import my_app.main or any other module. (It can import the package.)

Can anybody plz give some suggestions?

Thanks!

---

### Post by dodle on 2010-05-27
You say that "manage.py" is located in /usr/local/bin.  Where are your other files located?  If they are not in the same directory or somewhere in the system PATH it will not be able to find them.  

You will have to tell "manage.py" where the files are located with os.path.append():
[php]#! /usr/bin/env python
import sys
sys.path.append("/path/to/files")
import my_app[/php]

**Edit:** Sorry, I meant "sys.path.append()".

---

### Post by kalasoka on 2010-05-28
Hello,

My "other files" comes as a package and the package is installed at /usr/local/lib/python2.6/dist-packages, which is already included in sys.path.

I restate my problem: The script /usr/local/bin/manage.py is _able_ to do ```
import my_app
```, but it fails when it attempts ```
import my_app.main
```. Following is the error I get:

Traceback (most recent call last):
  File "/usr/local/bin/manage.py", line 5, in <module>
    import my_app
  File "/usr/local/bin/manage.py", line 9, in <module>
    import my_app.main
ImportError: No module named main

---

### Post by kalasoka on 2010-05-28
Sorry for bothering, but I figured out the problem.

By mistake my script was named as **/usr/loca/bin/my_app.py**, with same name as the package name. I renamed that script, and now it works fine!

---

