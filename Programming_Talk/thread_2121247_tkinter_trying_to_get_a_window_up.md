---
title: "tkinter trying to get a window up"
date: 2013-03-01
forum: Programming Talk
---

### Post by wingnut2626 on 2013-03-01
hi guys here is the code i am working with

```
from Tkinter import *


root = Tk() root.title("Note Taker")


root.mainloop()

```

and im getting a syntax error from the 2nd line.  It should just pop up a basic window, right?

---

### Post by nidzo732 on 2013-03-01
Why are you putting "root = Tk()" and "root.title(`Note taker`)" on the same line?
Put them on separate lines.

---

