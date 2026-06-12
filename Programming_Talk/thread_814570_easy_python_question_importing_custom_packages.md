---
title: "easy python question: importing custom packages"
date: 2008-05-31
forum: Programming Talk
---

### Post by MicahCarrick on 2008-05-31
This should be an easy one...

My file structure looks like:

```
myapp/
  widgets/
    __init__.py
    somewidget.py
    anotherwidget.py
  __init__.py
  main.py 
```

I want to use something like this from main.py

```
from myapp import widgets
widget1 = widgets.SomeWidget()
widget2 = widgets.AnotherWidget()
```

How do I get it to act like a package? I get "ImportError: No module named myapp"

---

### Post by geirha on 2008-05-31
the myapp dir must be available in the python path. You can add it to the $PYTHONPATH environment variable, or do ```
import sys
sys.path.append('path/to/dir/containing_myapp')
```

The dir that main.py is located in is automatically in the path, so if you are referring to main.py inside myapp/ in your file structure above, then you should simply do
```

import widgets

```

---

### Post by pmasiar on 2008-05-31
my hunch is you need __init__.py in top module level, myapp

---

### Post by MicahCarrick on 2008-05-31
Got it. Thanks guys.

---

### Post by pmasiar on 2008-05-31
that's nice, but tell us how?

---

### Post by MicahCarrick on 2008-06-01
I didn't have the __init__.py files like I thought, so with those in place I'm importing things from widget.whatever

---

