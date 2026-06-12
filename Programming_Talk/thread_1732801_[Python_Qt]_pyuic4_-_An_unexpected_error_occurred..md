---
title: "[Python Qt] pyuic4 - An unexpected error occurred."
date: 2011-04-18
forum: Programming Talk
---

### Post by Emascu on 2011-04-18
I'm trying to learn python and qt using the book 'Rapid GUI Programming with Python and Qt', where they tell me to generate a .ui file from a python file. However, when I do so I get the following error. Does anyone have an idea how to solve this?

```
lars@lars-desktop:~/python/findreplace$ pyuic4 findreplace.ui
# -*- coding: utf-8 -*-

# Form implementation generated from reading ui file 'findreplace.ui'
#
# Created: Mon Apr 18 21:18:42 2011
#      by: PyQt4 UI code generator 4.8.3
#
# WARNING! All changes made in this file will be lost!

An unexpected error occurred.
Check that you are using the latest version of PyQt and send an error report to
support@riverbankcomputing.com, including the following information:

  * your version of PyQt (4.8.3)
  * the UI file that caused this error
  * the debug output of pyuic4 (use the -d flag when calling pyuic4)
lars@lars-desktop:~/python/findreplace$ 
lars@lars-desktop:~/python/findreplace$ pyuic4 -d findreplace.ui
# -*- coding: utf-8 -*-

# Form implementation generated from reading ui file 'findreplace.ui'
#
# Created: Mon Apr 18 21:32:06 2011
#      by: PyQt4 UI code generator 4.8.3
#
# WARNING! All changes made in this file will be lost!

PyQt4.uic.uiparser: UI version is 3.3
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.7/PyQt4/uic/port_v2/invoke.py", line 44, in invoke
    exit_status = driver.invoke()
  File "/usr/lib/pymodules/python2.7/PyQt4/uic/driver.py", line 69, in invoke
    self._generate()
  File "/usr/lib/pymodules/python2.7/PyQt4/uic/driver.py", line 103, in _generate
    self._opts.pyqt3_wrapper, self._opts.from_imports)
  File "/usr/lib/pymodules/python2.7/PyQt4/uic/__init__.py", line 170, in compileUi
    winfo = compiler.UICompiler().compileUi(uifile, pyfile, from_imports)
  File "/usr/lib/pymodules/python2.7/PyQt4/uic/Compiler/compiler.py", line 119, in compileUi
    w = self.parse(input_stream)
  File "/usr/lib/pymodules/python2.7/PyQt4/uic/uiparser.py", line 882, in parse
    assert version in ("4.0",)
AssertionError
lars@lars-desktop:~/python/findreplace$ 

```I included the .ui file in case it might help.

Thanks,
Emas

---

### Post by oldfred on 2011-04-18
This works for me. I created a bash file that I just run. Some change is coming and it will need the -py2, but that did not work. I think it is once we are on v3 and want v2 compatibility.

#!/bin/sh
# o File or --output=File
# -x or --execute
cd /home/fred/Projects/pyqt
#pyuic4 -o pyTestimportUi.py -x pyTestimport.ui -py2
[COLOR=Red]pyuic4 -o pyTestimportUi.py -x pyTestimport.ui[/COLOR]
chmod 755 pyTestimportUi.py

---

