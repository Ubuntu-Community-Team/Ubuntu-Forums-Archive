---
title: "python: matplotlib data files not found"
date: 2010-10-05
forum: Programming Talk
---

### Post by maciejso on 2010-10-05
In the help mode I'm getting an error on issuing the command
```
modules
```
matplotlib works fine, I can plot graphs, it's just the python help command that needs to be fixed.
Can anybody help?


```
help> modules

Here is a list of matching modules.  Enter any module name to get more help.

Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python2.5/site.py", line 342, in __call__
    return pydoc.help(*args, **kwds)
  File "/usr/lib/python2.5/pydoc.py", line 1649, in __call__
    self.interact()
  File "/usr/lib/python2.5/pydoc.py", line 1667, in interact
    self.help(request)
  File "/usr/lib/python2.5/pydoc.py", line 1685, in help
    self.listmodules(split(request)[1])
  File "/usr/lib/python2.5/pydoc.py", line 1792, in listmodules
    apropos(key)
  File "/usr/lib/python2.5/pydoc.py", line 1890, in apropos
    ModuleScanner().run(callback, key)
  File "/usr/lib/python2.5/pydoc.py", line 1855, in run
    for importer, modname, ispkg in pkgutil.walk_packages():
  File "/usr/lib/python2.5/pkgutil.py", line 125, in walk_packages
    for item in walk_packages(path, name+'.', onerror):
  File "/usr/lib/python2.5/pkgutil.py", line 110, in walk_packages
    __import__(name)
  File "/usr/lib/python2.5/site-packages/matplotlib/config/__init__.py", line 5, in <module>
    from rcparams import rc
  File "/usr/lib/python2.5/site-packages/matplotlib/config/rcparams.py", line 117, in <module>
    rcParams = rc_params()
  File "/usr/lib/python2.5/site-packages/matplotlib/config/rcparams.py", line 49, in rc_params
    fname = get_config_file()
  File "/usr/lib/python2.5/site-packages/matplotlib/config/cutils.py", line 181, in get_config_file
    path =  get_data_path() # guaranteed to exist or raise
  File "/usr/lib/python2.5/site-packages/matplotlib/config/verbose.py", line 74, in wrapper
    ret = func(*args, **kwargs)
  File "/usr/lib/python2.5/site-packages/matplotlib/config/cutils.py", line 129, in _get_data_path_cached
    defaultParams['datapath'][0] = _get_data_path()
  File "/usr/lib/python2.5/site-packages/matplotlib/config/cutils.py", line 125, in _get_data_path
    raise RuntimeError('Could not find the matplotlib data files')
RuntimeError: Could not find the matplotlib data files

```

---

### Post by abottrill on 2011-07-18
I have this problem too

---

