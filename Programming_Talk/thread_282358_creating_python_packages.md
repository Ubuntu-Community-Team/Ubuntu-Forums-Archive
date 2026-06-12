---
title: "creating python packages"
date: 2006-10-22
forum: Programming Talk
---

### Post by orlox on 2006-10-22
I've made a simple python application that consists in only one module. I want to make a package from it (an rpm or a deb), but I can't manage to do it....

I found a way to make rpm packages from python modules by creating a setup.py file that's like this:

```
from distutils.core import setup
setup(name="kika",
      version="1.0",
      py_modules=["kika"])
```

where kika.py is the module I want to package. Then, I perform the packaging by doing:

> python setup.py bdist_rpm


Wich makes lot's of files along with one named "kika-1.0-1.noarch.rpm" wich contains the python script. I tried to install this file (using alien to generate the deb package), but after that, it's not available as an executable so i could just run it from a terminal. Instead, it becomes abailable for importing from other python scripts, but that's not what i'm looking for](*,) .

So, does anyone know how to package a python module so you can just execute it after installing the package??

---

### Post by po0f on 2006-10-22
orlox,

If it's just a stand-alone application, I would just distribute a tarball.  Include a README and whatever else, and you should be good to go.

---

### Post by orlox on 2006-10-22
I guess that could work for now. But I have another more complex projects in mind wich should have dependencies, and I'd like to know how to package a python application for these cases....

---

### Post by etank on 2006-10-22
You may want to try to submit the app to [http://cheeseshop.python.org/pypi](http://cheeseshop.python.org/pypi). Then I think that you could use easy_install to install the file.

Just a thought.

---

### Post by [woodstock] on 2006-10-23
I suggest you download the sources of some python packages and look how it is done there. IIRC gazpacho uses cdbs. I think this would be a good starting point, if nothing fancy has to be done.
You can find more info about the debian python policy [here]("www.debian.org/doc/packaging-manuals/python-policy/").

---

### Post by crmccreary on 2007-12-28
I found this link rather helpful:
[https://help.ubuntu.com/community/PythonRecipes/DebianPackage](https://help.ubuntu.com/community/PythonRecipes/DebianPackage)

---

### Post by pmasiar on 2007-12-28
python eggs is standard distribution format for Python code

---

