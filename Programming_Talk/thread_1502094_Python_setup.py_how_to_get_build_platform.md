---
title: "Python setup.py: how to get build platform"
date: 2010-06-05
forum: Programming Talk
---

### Post by simeon87 on 2010-06-05
Does anyone know how I can obtain in the setup.py file itself the value of the platform that the build command will build to? What I mean is this: when I run python setup.py build, it creates a directory called /build/<platform>/ and I'd like to determine the name of that directory in the setup.py script. On my computer, it happens to be 'lib.linux-x86_64-2.6' but I need to adapt the code so it will work on other computers too.

I've noticed that there exists a variable $PLAT which contains that value: [http://docs.python.org/install/#custom-installation](http://docs.python.org/install/#custom-installation) but I was unable to get it into a variable in setup.py itself. Would anyone know how to get it? I've also looked into distutils.sysconfig but it doesn't have a command/dict to obtain the value from.

---

### Post by ssam on 2010-06-05
you can probably use distutils.util.get_platform()
[http://docs.python.org/distutils/apiref.html#module-distutils.file_util](http://docs.python.org/distutils/apiref.html#module-distutils.file_util)

why do you need to do this?

---

### Post by simeon87 on 2010-06-05
Ah yes, thanks for that. Using some concatenation, I can construct the string I need.

The software that I'm developing is not really ready for installing (python setup.py install) but I do need to build it (python setup.py build) to get the .so files of the C extensions. So I run python setup.py build and then I move the .so files to the .py files so they can be accessed when running the Python software. I was currently globbing the build directory but that's not really a pretty way to do it.

---

