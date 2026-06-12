---
title: "Brand new to python in Linux"
date: 2007-02-27
forum: Programming Talk
---

### Post by iamBevan on 2007-02-27
Hi there, sorry for the extreamly newbie post here, but i've only ever programmed with PASCAL in Windows. The Python Interpreter is installed, but i just don't know how to use it, and how to compile my code. Any help would be greatly appreciated.


Thanks.

- Bevan

---

### Post by Ozitraveller on 2007-02-27
[http://www.python.org/](http://www.python.org/)

Using the Python Interpreter 
Invoking the Interpreter 
[http://docs.python.org/tut/node4.html](http://docs.python.org/tut/node4.html)

This might get you started.

IDLE is useful

[http://www.python.org/doc/current/lib/idle.html](http://www.python.org/doc/current/lib/idle.html)

---

### Post by thumper on 2007-02-27
Just invoke the python interpreter from the command line and you are away laughing.

```
$ python
Python 2.4.4c1 (#2, Oct 11 2006, 21:51:02)
[GCC 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> print 'Hello world'
Hello world
>>>

```

---

### Post by Wybiral on 2007-02-28
You can also save your programs as "*.py" and execute them from the command line.

```

# Save this as hello.py

print "Hello world!"

```

Then execute it from the command line with:

```

python hello.py

```

---

### Post by dwblas on 2007-03-02
This is a link to online books and tutorials
[http://python-forum.org/py/viewtopic.php?t=12&postdays=0&postorder=asc&start=0](http://python-forum.org/py/viewtopic.php?t=12&postdays=0&postorder=asc&start=0)

---

### Post by Choad on 2007-03-02
> **Wybiral said:**
> You can also save your programs as "*.py" and execute them from the command line.

```

# Save this as hello.py

print "Hello world!"

```

Then execute it from the command line with:

```

python hello.py

```
or put 

#!/usr/bin/env python

at the beginning of the file, then you can execute it regardless.

---

### Post by stani on 2007-03-06
In case you are looking for a good editor, try SPE which has an interpreter built in:
[http://pythonide.stani.be](http://pythonide.stani.be)

There will be a new release soon which is very focused on running smooth on Ubuntu. You can also try out the old release:

sudo apt-get install spe

Stani

---

