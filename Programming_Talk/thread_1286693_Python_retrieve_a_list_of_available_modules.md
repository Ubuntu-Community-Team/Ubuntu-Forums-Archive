---
title: "Python retrieve a list of available modules"
date: 2009-10-09
forum: Programming Talk
---

### Post by giuspen on 2009-10-09
Hi,
I'm searching for a function that lists all the available modules to import but I found no way, anybody can help me?
Thanks in advance,
Giuseppe.

---

### Post by Pyro.699 on 2009-10-09
Does this help? [http://www.wellho.net/resources/ex.php4?item=y108/listmethods](http://www.wellho.net/resources/ex.php4?item=y108/listmethods)

---

### Post by giuspen on 2009-10-09
> **Pyro.699 said:**
> Does this help? [http://www.wellho.net/resources/ex.php4?item=y108/listmethods](http://www.wellho.net/resources/ex.php4?item=y108/listmethods)

This explains how to retrieve the attributes of an object, so also the attributes of a module (being the module an object too) but does not explain how to list the modules that I could import.

---

### Post by unutbu on 2009-10-09
Python makes no distinction between python scripts and python modules. They both can be imported using the same syntax. So really any file in any directory in your sys.path that ends in .py is a module as far as import is concerned.

This should list them all: (*)[PHP]
#!/usr/bin/env python
import sys
import os
files=[]
for directory in sys.path:
    files.extend([filename.replace('.py','') for filename in os.listdir(directory)
                  if filename.endswith('.py')])
print files
[/PHP]

(*) Edit: Hm. I forgot about directories containing __init__.py...

---

### Post by giuspen on 2009-10-12
> **unutbu said:**
> Python makes no distinction between python scripts and python modules. Thy both can be imported using the same syntax. So really any file in any directory in your sys.path that ends in .py is a module as far as import is concerned.

This should list them all: (*)[PHP]
#!/usr/bin/env python
import sys
import os
files=[]
for directory in sys.path:
    files.extend([filename.replace('.py','') for filename in os.listdir(directory)
                  if filename.endswith('.py')])
print files
[/PHP]

(*) Edit: Hm. I forgot about directories containing __init__.py...

Thanks for your help, I created this script according to your lead: [PHP]#!/usr/bin/env python
import sys, os

files=[]

for directory in sys.path:
   for dirpath, dirnames, filenames in os.walk(directory):
      if dirpath == directory and "__init__.py" in filenames:
         for filename in filenames:
            if filename.endswith('.py'): files.append(filename.replace('.py',''))

files.sort()

print files[/PHP]

but in the resulting list I can't find for example the module "gtk" while I can do "import gtk".

---

### Post by unutbu on 2009-10-12
To understand your code I cut it down to
[PHP]
#!/usr/bin/env python
import sys, os
files=[]
for directory in sys.path:
   for dirpath, dirnames, filenames in os.walk(directory):
       if dirpath == directory and "__init__.py" in filenames:
           print(dirpath)
[/PHP]
and found on my installation that it only prints
```

/usr/lib/python2.5/site-packages/PIL
```

I think the criterion is only getting satisfied when dirpath is itself in sys.path *and* dirpath contains a file called __init__.py. This criterion is too restrictive.

Here is an script which attempts to cull modules including those buried in directories containing __init__.py. 

[PHP]
#!/usr/bin/env python
import sys
import os
import operator

def find_modules(path,prefix=[]):
    modules=[]
    if not os.path.isdir(path):
        return []
    listing=os.listdir(path)
    for filename in listing:
        fullname=os.path.join(path,filename)
        # print('Checking %s'%fullname)
        if os.path.isdir(fullname):
            initfile=os.path.join(fullname,'__init__.py')
            # print('  Checking for %s'%initfile)
            if os.path.exists(initfile):
                # print('  %s is a module'%filename)
                modules.append('.'.join(prefix+[filename]))
                modules.extend(
                    find_modules(fullname,prefix+[filename]))
        elif (os.path.isfile(fullname) and filename.endswith('.py') and
              filename!='__init__.py'
              ):
            modules.append('.'.join(prefix+[filename.replace('.py','')]))
    return modules

modules=list(
    set(reduce(operator.add,[find_modules(directory) for directory in sys.path])))
modules.sort()
print(modules)
[/PHP]

Please tell me if you find a bug.

---

### Post by giuspen on 2009-10-13
Hi and thanks for your help.
Running your script in windows xp I have the following result:
[PHP]Traceback (most recent call last):
  File "D:\BEPPE\cherrytree\modules_list.py", line 27, in <module>
    set(reduce(operator.add,[find_modules(directory) for directory in sys.path])))
  File "D:\BEPPE\cherrytree\modules_list.py", line 8, in find_modules
    listing=os.listdir(path)
WindowsError: [Error 3] The system cannot find the path specified: 'C:\\WINDOWS\\system32\\python25.zip/*.*'[/PHP]
That's why I replaced os.listdir() which seems to cause problems.
I needed this in windows xp as I wanted to package one my application ([cherrytree]("http://open.vitaminap.it/en/cherrytree.htm")) for windows in addition to ubuntu but have a problem installing the package pygtksourceview in windows (after installation, the "import gtksourceview" causes an error telling module unknown) and wanted to understand better the modules import criterion.

---

### Post by unutbu on 2009-10-13
I edited the script in my previous post with this:
[PHP]
def find_modules(path,prefix=[]):
    modules=[]
    if not os.path.isdir(path):
        return []
[/PHP]
Perhaps that will help, though I'm not sure.

It appears that under Windows, sys.path includes
'C:\\WINDOWS\\system32\\python25.zip/*.*'.

I don't understand what Windows is trying to do here.
First, the *.* suggests this path is not a directory. I thought all elements of sys.path were directories.

Second, this path mixes Windows-style backslashes with unix-style forward-slashes. Is that allowed?

Since I don't understand what this path is supposed to do, I added some code to cause the script to ignore such paths. If that is a mistake, then the script won't find all the modules.

---

### Post by giuspen on 2009-10-14
Your script works perfectly now, thanks for the help!

---

### Post by unutbu on 2009-10-14
Great! Glad I could help.

---

### Post by engla on 2009-10-14
Python has lots of awesome tools for modules and whatnot hidden away in the standard library. I discovered **pkgutil** -- that generalizes package listing and module loading for Python.

I wanted to make it as general as possible so that my application could still load if packages in a .zip package, yes that python2.5.zip in sys.path is no strange thing, python also supports modules in zips, but I can't tell you why. Anyway, pkgutil helped me generalize my problem -- extract and eval a module partially. Basically you can get the source of any module as a compiled code object with pkgutil, then eval that.

```
    loader = pkgutil.get_loader(modulename)
    attributes = {}
    try:
        eval(loader.get_code(), attributes)
    except Exception, exc:
        pass

```
The module may raise an exception on import, but all functions, constants etc that were evaluated before the exception are stored in attributes with this code snippet -- pretty cool, that's "rescue mode" module importing.

----

**However, what I wanted to say** was that I found a function in pkgutil now, which seems to be close to what you were looking for previously.. pkgutil.iter_modules() ; it returns a generator of all toplevel modules in your path (together with an importer object should you wish to import it programmatically).

---

### Post by giuspen on 2009-10-15
It's interesting but I can't make it work.
I tried this script:
[PHP]import pkgutil

loader = pkgutil.get_loader("pickle")
attributes = {}
try:
   eval(loader.get_code(), attributes)
except Exception, exc:
   pass[/PHP]
but I always catch the exception

About
[PHP]pkgutil.iter_modules()[/PHP]
I can't understand how to use it, can you provide a short example?
Thanks.

---

### Post by Can+~ on 2009-10-15
> **giuspen said:**
> 
[PHP]pkgutil.iter_modules()[/PHP]
I can't understand how to use it, can you provide a short example?
Thanks.

It returns an iterable, whenever you declare a class, a method, or even a function to be "iterable", then the for loop can iterate over it (and other functions, like reduce, that demand iterables):

[PHP]
import pkgutil

for pkg in pkgutil.iter_modules():
    print pkg[/PHP]

---

### Post by giuspen on 2009-10-16
> **Can+~ said:**
> It returns an iterable, whenever you declare a class, a method, or even a function to be "iterable", then the for loop can iterate over it (and other functions, like reduce, that demand iterables):

[PHP]
import pkgutil

for pkg in pkgutil.iter_modules():
    print pkg[/PHP]

Really cool, thanks a lot.

---

