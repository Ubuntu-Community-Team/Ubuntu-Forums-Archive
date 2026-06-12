---
title: "python-xml???"
date: 2010-02-03
forum: Packaging and Compiling Programs
---

### Post by gh4ever on 2010-02-03
Hi,
I'm trying to package the program fofix.
[http://code.google.com/p/fofix/](http://code.google.com/p/fofix/)
When I run:
```
dpkg-buildpackage -rfakeroot
```
I get the error:
```
xml.sax.drivers2.drv_pyexpat,\
GameResultsScene src/FoFiX.py
Traceback (most recent call last):
  File "/usr/bin/cxfreeze", line 5, in <module>
    main()
  File "/usr/lib/pymodules/python2.6/cx_Freeze/main.py", line 170, in main
    freezer.Freeze()
  File "/usr/lib/pymodules/python2.6/cx_Freeze/freezer.py", line 405, in Freeze
    self._FreezeExecutable(executable)
  File "/usr/lib/pymodules/python2.6/cx_Freeze/freezer.py", line 145, in _FreezeExecutable
    finder = self._GetModuleFinder(exe)
  File "/usr/lib/pymodules/python2.6/cx_Freeze/freezer.py", line 251, in _GetModuleFinder
    finder.IncludeModule(name)
  File "/usr/lib/pymodules/python2.6/cx_Freeze/finder.py", line 397, in IncludeModule
    module = self._ImportModule(name, deferredImports)
  File "/usr/lib/pymodules/python2.6/cx_Freeze/finder.py", line 201, in _ImportModule
    raise ImportError, "No module named %s" % name
ImportError: No module named xml.sax.drivers2.drv_pyexpat
make[1]: *** [dist] Error 1
make[1]: Leaving directory `/home/gh4ever/My Project/fofix-3.121'
make: *** [build-stamp] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2

```
I know I'm missing the dependency python-xml, and I've even downloaded a package I found floating around and added it to the control file, but still no-go. What package do I need to install to get this to work right???
BTW, I'm using the instructions to package here:
[http://ubuntuforums.org/showthread.php?t=51003](http://ubuntuforums.org/showthread.php?t=51003)
This is my first attempt at packaging, so I have no clue at what's going on (I'm also relatively new to Linux).

---

### Post by SevenMachines on 2010-02-05
although the package python-xml has been deprecated in favour of xml2 for the last couple of releases its that one you need to install for this program. 
It seems you've done that. using oython2.6, it seems to find the correct module, its looks like more of a problem with cxfreeze, i cant get that to find the correct module no matter what --include-path= options i add to it.

---

### Post by SevenMachines on 2010-02-05
Sadly i know nothing about cxfreeze, its that thats the stumbling block though

---

### Post by gh4ever on 2010-02-05
I see...ok, I'll just start on something simpler.
Thanks for the info!

---

### Post by zubin71 on 2010-04-03
i would always suggest using distutils, a module available in the stdlib of python for packaging. Currently distutils lacks the --uninstall feature but is being worked on, under another namespace "distutils2" which will be out soon enough.

you might want to check out distutils for now.

---

