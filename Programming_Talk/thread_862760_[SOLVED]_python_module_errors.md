---
title: "[SOLVED] python module errors"
date: 2008-07-17
forum: Programming Talk
---

### Post by seventhc on 2008-07-17
I have a strange problem here when in interactive mode. I'm not sure how to phrase the problem, so I'll post the output.
[php]
>>> help()
help>modules
Please wait a moment while I gather a list of all available modules...

Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python2.5/site.py", line 342, in __call__
    return pydoc.help(*args, **kwds)
  File "/usr/lib/python2.5/pydoc.py", line 1649, in __call__
    self.interact()
  File "/usr/lib/python2.5/pydoc.py", line 1667, in interact
    self.help(request)
  File "/usr/lib/python2.5/pydoc.py", line 1683, in help
    elif request == 'modules': self.listmodules()
  File "/usr/lib/python2.5/pydoc.py", line 1804, in listmodules
    ModuleScanner().run(callback)
  File "/usr/lib/python2.5/pydoc.py", line 1855, in run
    for importer, modname, ispkg in pkgutil.walk_packages():
  File "/usr/lib/python2.5/pkgutil.py", line 110, in walk_packages
    __import__(name)
  File "/home/seventhc/curses.py", line 7, in <module>
    stdscr = curses.initscr()
AttributeError: 'module' object has no attribute 'initscr'
>>> 
[/php] I should be getting a list of modules here but I'm getting these errors instead.
I have python-doc installed. Am I missing something else that needs to be installed?
Does anyone know a fix for this?
Any help is appreciated.
Thank you.

---

### Post by ghostdog74 on 2008-07-17
change the file name (curses.py) to something different. curses is supposed to be from another module.

---

### Post by seventhc on 2008-07-17
Thanks for the quick reply. I got rid of curses.py and it looked like it was going to work since it took a little longer generating the list, but got this.

[php]
help> modules

Please wait a moment while I gather a list of all available modules...

Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python2.5/site.py", line 342, in __call__
    return pydoc.help(*args, **kwds)
  File "/usr/lib/python2.5/pydoc.py", line 1649, in __call__
    self.interact()
  File "/usr/lib/python2.5/pydoc.py", line 1667, in interact
    self.help(request)
  File "/usr/lib/python2.5/pydoc.py", line 1683, in help
    elif request == 'modules': self.listmodules()
  File "/usr/lib/python2.5/pydoc.py", line 1804, in listmodules
    ModuleScanner().run(callback)
  File "/usr/lib/python2.5/pydoc.py", line 1855, in run
    for importer, modname, ispkg in pkgutil.walk_packages():
  File "/usr/lib/python2.5/pkgutil.py", line 125, in walk_packages
    for item in walk_packages(path, name+'.', onerror):
  File "/usr/lib/python2.5/pkgutil.py", line 125, in walk_packages
    for item in walk_packages(path, name+'.', onerror):
  File "/usr/lib/python2.5/pkgutil.py", line 110, in walk_packages
    __import__(name)
  File "/var/lib/python-support/python2.5/django/core/cache/__init__.py", line 54, in <module>
    cache = get_cache(settings.CACHE_BACKEND)
  File "/var/lib/python-support/python2.5/django/conf/__init__.py", line 28, in __getattr__
    self._import_settings()
  File "/var/lib/python-support/python2.5/django/conf/__init__.py", line 53, in _import_settings
    raise EnvironmentError, "Environment variable %s is undefined." % ENVIRONMENT_VARIABLE
EnvironmentError: Environment variable DJANGO_SETTINGS_MODULE is undefined.
>>> 

[/php]

---

### Post by seventhc on 2008-07-17
OK, it is fixed now. The curses.py that was there was actually something i made...bad name to choose. :D After that I saw the errors from django, which I don't need, it was installed because I was messing around with it a while ago. I uninstalled that and now everything is fine. :)
Thanks for the help.
:)

---

