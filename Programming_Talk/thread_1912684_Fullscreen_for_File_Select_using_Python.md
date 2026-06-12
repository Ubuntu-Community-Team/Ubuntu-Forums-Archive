---
title: "Fullscreen for File Select using Python ?"
date: 2012-01-21
forum: Programming Talk
---

### Post by honeybear on 2012-01-21
Hello,

I would like to have a list of files in fullscreen to select a file. 

Like a zenity for file selection dialog

Would you know where I could find such a code using those : 
```
#!/usr/bin/python

import os
import pygtk
pygtk.require('2.0')
import gtk
import glib
import sys

```


thank you

---

### Post by ubudog on 2012-01-21
*Thread moved to Programming Talk.*

Hope you get more help here.

---

### Post by MG&amp;TL on 2012-01-21
You could use a gtk.fielchooserdialog, if I understand you correctly.

[http://www.pygtk.org/docs/pygtk/class-gtkfilechooserdialog.html]("http://www.pygtk.org/docs/pygtk/class-gtkfilechooserdialog.html")

---

