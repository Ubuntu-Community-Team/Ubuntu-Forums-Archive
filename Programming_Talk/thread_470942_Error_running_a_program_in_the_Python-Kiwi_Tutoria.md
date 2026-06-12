---
title: "Error running a program in the Python-Kiwi Tutorial"
date: 2007-06-11
forum: Programming Talk
---

### Post by fatsheep on 2007-06-11
I'm using python-kiwi (1.9.13-0ubuntu) on ubuntu 7.04 "feisty fawn" and I didn't get far through the tutorial before I had an error:
[http://www.async.com.br/projects/kiwi/howto/person.html](http://www.async.com.br/projects/kiwi/howto/person.html)

Here are my results when I run person.py:

> 
fatsheep:~/Programming/python-kiwi examples/framework/person$ ./person.py
Traceback (most recent call last):
  File "./person.py", line 14, in <module>
    delete_handler=gtk.main_quit)
  File "/var/lib/python-support/python2.5/kiwi/ui/delegates.py", line 130, in __init__
    delete_handler)
  File "/var/lib/python-support/python2.5/kiwi/ui/views.py", line 830, in __init__
    domain)
  File "/var/lib/python-support/python2.5/kiwi/ui/views.py", line 240, in __init__
    self._glade_adaptor = self.get_glade_adaptor()
  File "/var/lib/python-support/python2.5/kiwi/ui/views.py", line 848, in get_glade_adaptor
    return _open_glade(self, self.gladefile, self.domain)
  File "/var/lib/python-support/python2.5/kiwi/ui/views.py", line 998, in _open_glade
    "load the gladefile %s" % (loader_name, gladefile))
**RuntimeError: Could not find gazpacho.loader, it needs to be installed to load the gladefile /home/fatsheep/Programming/python-kiwi examples/framework/person/Person.glade**


What is gazpacho.loader and how could I remedy this problem?  I get this error on several other python-kiwi scripts as well.

---

### Post by FuturePast on 2007-06-11
This is just a guess but try:
```
$ sudo apt-get install gazpacho
```

---

### Post by fatsheep on 2007-06-11
> **FuturePast said:**
> This is just a guess but try:
```
$ sudo apt-get install gazpacho
```

That appears to have fixed it.  Thanks a lot.

---

