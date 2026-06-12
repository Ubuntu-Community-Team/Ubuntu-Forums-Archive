---
title: "Install wxPython on alternate Python interpreter"
date: 2009-01-25
forum: Programming Talk
---

### Post by dmub82 on 2009-01-25
Using Intrepid and learning Python. I installed Python 2.6 to /opt/python2.6 so it doesn't conflict with the default Python 2.5 installation that comes with Intrepid. Now I'd like to install wxPython onto the Python 2.6 installation. I installed the python-wxgtk - whatever version packages with apt-get, but they attached to the Python 2.5 interpreter ("import wx" worked fine in 2.5, but 2.6 could not find the module). 

What's the easiest way to install wxPython so it goes in the right place for Python 2.6 to use? Thanks.

---

### Post by snova on 2009-01-25
You could try adding the 2.5 libraries to the 2.6 search path, but it may not work:

```
import sys
sys.path.append('/usr/lib/python2.5/site-packages')
```

The libraries may not be binary compatible with the new version, however.

---

