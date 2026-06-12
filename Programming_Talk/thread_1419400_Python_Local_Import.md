---
title: "Python Local Import"
date: 2010-03-01
forum: Programming Talk
---

### Post by ctult on 2010-03-01
Hi.
    I need a Python snippet that runs a local Python script.  I know there is import, but I need something to do it locally (like in the same directory.)

---

### Post by wmcbrine on 2010-03-01
import is still what you want, then.

---

### Post by snova on 2010-03-01
> **ctult said:**
> Hi.
    I need a Python snippet that runs a local Python script.  I know there is import, but I need something to do it locally (like in the same directory.)

I would guess you need [**subprocess**]("http://docs.python.org/library/subprocess.html").

```
import subprocess
subprocess.Popen(["python", "your-script.py"])
```

---

### Post by epicoder on 2010-03-01
Put the thing you want to import in the same directory, then use import normally.

Say I have program.py and I want to import extraClasses.py.

I would put extraClasses.py in the same directory as program.py, then put "import extraClasses" (without the quotes) in program.py.

---

### Post by snova on 2010-03-01
Importing a module and running it as a subprocess really aren't the same at all.

The way the question is phrased, and considering the OP is apparently familiar with imports, I'm led to think the latter is desirable.

---

### Post by wmcbrine on 2010-03-01
But his confusion seems to be about the location, not the run/import distinction.

I guess we need the OP to elaborate on what he's tried, and what's not working.

---

### Post by nvteighen on 2010-03-02
Curiously, I've been thinking on (I think) the same issue some minutes ago before reading this thread :p

What the OP may be trying to do is to "import" a Python file which is not in any of the sys.path paths and **run** it from another source file, but having the results be accesable. Popen won't do it because as soon as the subprocess ends, the script will be lost.

In other words, using something like Common Lisp **load** (as opposed to **require**)

In my case, I need it because I need to read a variable from a package __init__.py before I actually import the package as it's a plugin-like architecture... something in between normal modularization and plugins. The situation is as follows: I have a package, but that package can be installed either in the same directory (source tarball), in the site-packages system-wide folder (distutils install) or wherever the python-support installs it. The package has a real name, used for importing, but also has a "real" name set by the writer and which is to be shown in a menu. That real name is set in __init__.py for convenience and not having another configuration file and to ease development.

That's why I need such a functionality, but I wonder if the OP also does.

This code could work (not entirely tested):
```

myscript = open(path, "r")
exec myscript.read()
myscript.close()
# Do stuff with whatever you got from the script
# ...

```

In some way, this is like breaking Python's high-level module system into a low-level C-like #include.

---

