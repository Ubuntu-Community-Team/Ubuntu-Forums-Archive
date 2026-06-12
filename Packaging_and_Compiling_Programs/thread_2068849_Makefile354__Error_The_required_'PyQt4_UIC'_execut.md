---
title: "Makefile:354: *** Error: The required 'PyQt4 UIC' executable file can't be found"
date: 2012-10-10
forum: Packaging and Compiling Programs
---

### Post by Ralph L on 2012-10-10
I am installing ubuntu precise pangolin 12.04.  I am trying to install fcronq, which needs pyqt4 (python 3).  Using Synaptic I installed python3-pyqt4.  It also installed python3, python3-minimal, python3-pyqt4, python3-sip, python3.2, and python3.2-minimal.  When I follow the instructions on [http://code.google.com/p/fcronq/wiki/Installation#Installation](http://code.google.com/p/fcronq/wiki/Installation#Installation) and do the:
```
make all
```

I get:
```
Makefile:354: *** Error: The required 'PyQt4 UIC' executable file can't be found
```

I don't know anything about PyQt4 UIC.  However, I am concerned that it must be based on python 3.  Under Synaptic I found pyqt4-dev-tools, which mentions the user interface, but I am afraid to install it, because I don't know if it is based on python 3.

Can anybody tell me how to get PyQt4 UIC (based on python3) installed?

Thanks in advance.

---

### Post by oldos2er on 2012-10-10
Moved to Packaging and Compiling Programs.

---

### Post by spjackson on 2012-10-10
I haven't installed pyqt4 for python3, only for python 2.7.3 (and earlier). I've had a quick look at the source packages for python3/pyqt4 and am left confused!

pyuic4 is a very simple script:
```

$ cat /usr/bin/pyuic4
#!/usr/bin/env python
# there's no main function, so just import the module
import PyQt4.uic.pyuic

```It's trivial to get one that works for python3 and put it on your PATH. That should suffice for building fcronq. However, I can't see what is supposed to install it.

pyqt4-dev-tools does have a dependency on the python 2.7.3 and its libraries, so you probably don't want that.

---

### Post by Ralph L on 2012-10-11
spjackson

Thank you for responding.  I really appreciate it.  However, I did not really understand what you were telling me.  I don't know where you found the source script for pyuic4 and whether or not it is based on python3.  Also, I don't know what action is taken by "import PyQt4.uic.pyuic".  Would appreciate any hints, so that I learned something.

I did take a chance and, using synaptic, I installed "pyqt4-dev-tools".  The synaptic description said that it contained pyuic4.  It didn't say it was based on python3, so I don't know if it is. But it did have a Version of 4.9.1-2ubuntu, which is the same as the version of python3-pyqt4. Anyway, it worked.  After I installed it and restarted installing fcronq, the fcronq "make all" and "sudo make install" ran without errors, and I was able to launch fcronq satisfactorily.  I haven't had a chance to really use fcronq yet, but it appeared to run.

Again, thank you for responding.

Ralph

---

### Post by spjackson on 2012-10-11
The pyuic4 script I posted is the one I got from pyqt4-dev-tools which I installed for use with python 2.7.3.

I wasn't sure that it would work for you because I didn't know that the first line would resolve to python3. Providing the right python is running the script, it should then work because python will look in the right place for the import.

---

### Post by Ralph L on 2012-12-01
Just a note to finish this:  Instructions for installing fcron/fcronq scheduler are in [http://ubuntuforums.org/showthread.php?t=2057486](http://ubuntuforums.org/showthread.php?t=2057486)

---

