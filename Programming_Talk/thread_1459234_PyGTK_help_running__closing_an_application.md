---
title: "PyGTK help running / closing an application"
date: 2010-04-21
forum: Programming Talk
---

### Post by Srbjan on 2010-04-21
If you can launch an application like this
```

import os

def wn1_btn1_clicked(self, widget):
os.system("python /path/App.pyc")

```
Can you kill the same application in a similar method or let say other application "wine /path/to.exe"

---

### Post by giuspen on 2010-04-21
> **Srbjan said:**
> If you can launch an application like this
```

import os

def wn1_btn1_clicked(self, widget):
os.system("python /path/App.pyc")

```
Can you kill the same application in a similar method or let say other application "wine /path/to.exe"

you can probably do it using the subprocess module:

[http://docs.python.org/library/subprocess.html](http://docs.python.org/library/subprocess.html)

---

