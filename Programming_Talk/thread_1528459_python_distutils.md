---
title: "python distutils"
date: 2010-07-10
forum: Programming Talk
---

### Post by miak on 2010-07-10
Hi I was working with SWIG and python and was trying different approaches and installing different software.
I got swig work using distutils, but after I installed packages "python-distutils-extra" and "ython-setuptools" I am getting wierd errors when I run 
```
python setup.py
```Here is the error message I'm getting:
```
Traceback (most recent call last):
  File "/home/arsen/workspace/vlbi/phringes/trunk/swig/myModule/setup.py", line 16, in <module>
    py_modules = ["myModule"],
  File "/usr/lib/python2.6/distutils/core.py", line 140, in setup
    raise SystemExit, gen_usage(dist.script_name) + "\nerror: %s" % msg
SystemExit: usage: setup.py [global_opts] cmd1 [cmd1_opts] [cmd2 [cmd2_opts] ...]
   or: setup.py --help [cmd1 cmd2 ...]
   or: setup.py --help-commands
   or: setup.py cmd --help

error: no commands supplied

```I'm pretty sure it's because of that packages, I uninstalled them and reinstalled python(from synaptics) but i am still getting that problem, any idea what's going on????

Here is my setup.py
```
#!/usr/bin/env python

"""
setup.py file for myModule SWIG module
"""

from distutils.core import setup, Extension

myModule = Extension('_myModule', sources=['myModule_wrap.c', 'myModule.c'],)

setup ( name = 'myModule',
        version = '0.1',
        author = 'miak',
        description = """Simple example module""",
        ext_modules = [myModule],
        py_modules = ["myModule"],
        )

```

---

### Post by miak on 2010-07-12
I reinstalled all python packages and after that it worked, but i still needed to supply arguement to python setup.py(python setup.py build_ext).

I think it was originally my mistake and had nothing to do with the packages al all.

---

### Post by nvteighen on 2010-07-13
Uh... nobody noticed this thread?

When installing with distutils, you need to do this:

```

python setup.py install

```

Be aware that distutils doesn't include a removal feature.

---

