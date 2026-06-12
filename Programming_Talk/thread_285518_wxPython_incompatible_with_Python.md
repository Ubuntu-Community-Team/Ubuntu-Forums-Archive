---
title: "wxPython incompatible with Python"
date: 2006-10-26
forum: Programming Talk
---

### Post by jeffbarish on 2006-10-26
I have the Python 2.4.2 that installs with the OS.  I installed python-wxgtk2.6 from the Ubuntu universe repository.  When I import wx, I get the error message:

undefined symbol: PyUnicodeUCS4_FromEncodedObject

This message is telling me that the Python was not compiled with support for wide Unicode.  Is there a package available with such a Python?  Is there a wxPython package that does not require wide Unicode?  Better still, how about compatible packages with current versions of both Python (2.5) and wxPython (2.7)?  I don't understand why there is a package in the Ubuntu repository that does not run on the Python that ships with the OS.

---

