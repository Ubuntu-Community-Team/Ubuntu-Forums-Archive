---
title: "Python3 - How to import from different directory to access from /usr/bin"
date: 2015-07-01
forum: Programming Talk
---

### Post by flaymond on 2015-07-01
Hi everyone! I got a problem to import modules from different directory in Python3. I know that I can import module from different directory if that directory got** __init__.py**in it. So I try to do that like this -

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

hi("Ubuntu")

```

but ***how I can import modules, say in /usr/lib ***(that don't have __init__.py (I need to access the module from /usr/bin))

If it's in C, it will be simple as ***#include "../to/path"*** and let me use the modules with ease from /usr/bin

-----------
So here is my question -

How can I access the modules in /usr/lib (says, the module name usr/lib/lizard.py, and accessed by /usr/bin/my_program.py)?

What or which "import" statement do I need to modify and invoke?

Thanks for every helps! :D

# Hmmppf, I think I gotta spend my time with my first programming language and learn the OO facilities it provide (Python), than switching to others and learn new syntax to do the same thing.

---

### Post by flaymond on 2015-07-01
--

## Accidental reply ## (I don't know what is happening today)
# This is the original one

---

### Post by ian-weisser on 2015-07-01
You can import any compatible python script or snippet that is in Python's sys.path list. The presence or absence of __init__.py is irrelevant.

Example
```
>>> import sys

>>> sys.path
['', '/usr/lib/python3.4', '/usr/lib/python3.4/plat-x86_64-linux-gnu', '/usr/lib/python3.4/lib-dynload', '/usr/local/lib/python3.4/dist-packages', '/usr/lib/python3/dist-packages']

>>> sys.path.append('/usr/lib')

>>> import lizard

```

Generally, /usr/lib is a location for upstream packages - be careful that you don't create namespace conflicts. I recommend using /usr/local instead.
One common solution is to symlink your various python scripts to /usr/local/lib/python3.4/dist-packages , which is already included in the default sys.path. Then 'import lizard' magically works without mucking about with sys.path.

---

### Post by trent.josephsen on 2015-07-02
I didn't know the answer to this question, but I thought of a way to find out. SCons is a build tool (similar to make) and it is written in Python 2, not 3, but I bet we can get very close to an answer by looking at the source for SCons. (I use Arch. On Ubuntu the paths and versions may be slightly different.)

First things first, let's just look at the scons executable (my shell prompt is a percent sign %):
```
% which scons
/usr/bin/scons
% file /usr/bin/scons
/usr/bin/scons: a /usr/bin/env python2 script, ASCII text executable
% wc -l /usr/bin/scons
205 /usr/bin/scons
```
That's encouraging -- 205 lines isn't nearly enough to write the whole application in, so it's definitely pulling in extra Python libraries from somewhere else. Since I know that /usr/bin/scons is a Python script, I can open it up and see how it works.
```
% vim /usr/bin/scons
```
I see some variables being defined near the top, followed by "import os" and "import sys" but no other imports. However, if I go to the bottom of the file I see this:
```
if __name__ == "__main__":
    try:
        import SCons.Script
    except:
        print("Import failed. Unable to find SCons files in:")
        for path in libs:
          print "  %s" % path
        raise
```

I'm pretty sure that import won't work in a standard python2 environment, but I check just to be sure:
```
% python2
Python 2.7.10 (default, May 26 2015, 04:16:29) 
[GCC 5.1.0] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import SCons.Script
>>>
```
... ok, I was completely wrong about that. It appears SCons installs itself in a global location that all Python scripts can access. Good to know. Better, if we could find out exactly what path that is. Fortunately, there is a clue in the except-clause, which strongly hints that the variable "libs" has something to do with it.

Looking just a few lines earlier in the file, I find this:
```
sys.path = libs + sys.path
```

Aha! So there's something called "sys.path" which we're modifying by prepending "libs" to it, which -- I assume -- has an effect on where Python searches for modules. At this point I'm going to fall back on official documentation, since "sys" is a standard library module and "sys.path" sounds like something important. [The Python 2 standard library documentation](https://docs.python.org/2/library/sys.html) has this to say (emphasis mine):
>  sys.path

    **A list of strings that specifies the search path for modules**. Initialized from the **environment variable PYTHONPATH**, plus an installation-dependent default.

    As initialized upon program startup, the first item of this list, path[0], is the directory containing the script that was used to invoke the Python interpreter. If the script directory is not available (e.g. if the interpreter is invoked interactively or if the script is read from standard input), path[0] is the empty string, which directs Python to search modules in the current directory first. Notice that the script directory is inserted before the entries inserted as a result of PYTHONPATH.

    **A program is free to modify this list for its own purposes**.
Yep, we're getting somewhere. Before I continue, though, I'm going to check and see if this feature has been renamed or replaced in Python 3. [The relevant page of the docs for 3.4.3 has almost the exact same wording](https://docs.python.org/3/library/sys.html#sys.path), which suggests the feature probably hasn't changed much, if at all.

Now I'm going to check and see what sys.path actually is in Python 3:
```
% python3
Python 3.4.3 (default, Mar 25 2015, 17:13:50) 
[GCC 4.9.2 20150304 (prerelease)] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import sys
>>> sys.path
['', '/usr/lib/python34.zip', '/usr/lib/python3.4', '/usr/lib/python3.4/plat-linux', '/usr/lib/python3.4/lib-dynload', '/usr/lib/python3.4/site-packages']
```
Predictably, it's a list of paths. /usr/lib/python34.zip doesn't exist, but I recognize the names of some standard library modules in /usr/lib/python3.4.

From what we've gathered so far, I can guess at three possible ways to achieve the desired result:
1. Add the path to your Python module to sys.path at runtime;
2. Install your Python module into one of the paths that is already in sys.path;
3. As hinted in the documentation, set the environment variable PYTHONPATH so that Python will look in the right place.

Probably you want to do #2. The name "site-packages" suggests that it might be the right place for this kind of thing. Looking back at SCons, I notice that it keeps files in /usr/lib/python2.7/site-packages/SCons.

So I tried it (I had to become root to put stuff in /usr/lib):
```
% sudo -s
# mkdir /usr/lib/python3.4/site-packages/mymodule
# cat >/usr/lib/python3.4/site-packages/mymodule/__init__.py <<EOF
def hello(name):
    print("hello, "+str(name))
EOF
# exit
% python3
Python 3.4.3 (default, Mar 25 2015, 17:13:50) 
[GCC 4.9.2 20150304 (prerelease)] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import mymodule
>>> mymodule.hello('world')
hello, world
>>> 
```
Hey, it works!

It looks like I was too slow to beat Ian for the quick answer, but I learned a lot in the process and I hope you did too. Let me know if you would like clarification on anything.

---

### Post by flaymond on 2015-07-02
Thanks to both of you : ian-weisser and trent.josephsent. The sys.path is worked like charm! :D

* trent.josephsen - I will have a look at SCons, for my old python2 program. :D. 

Thank you very much for all responses! ;)

---

