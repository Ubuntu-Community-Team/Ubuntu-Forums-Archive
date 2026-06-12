---
title: "Help with Zenity in Python"
date: 2011-02-06
forum: Programming Talk
---

### Post by Datweakfreak on 2011-02-06
The following piece of code in a bash script:

```
g='abc'
zenity --info --text="$g"
```

returns the value of g, that is 'abc', in a zenity dialog box.

Its equivalent in Python:

```

import os
g='abc'
os.system('zenity --info --text="$g"')

```

This doesn't return 'abc', though. It just shows an empty dialog box.

Is there any other equivalent for '**$g**' in Python?

---

### Post by kimet on 2011-02-06
Bash can't know who is 'g'. Put inside os.system:

```
import os

os.system('g="abc"; zenity --info --text="$g"')

```

Or try another toolkit, ex.Tkinder

```
from Tkinter import *
g='abc'
w = Label(text= g)
w.pack()
mainloop()
```

---

### Post by MadCow108 on 2011-02-06
you might want to use pyzenity:
[http://pypi.python.org/pypi/PyZenity/0.1.1/](http://pypi.python.org/pypi/PyZenity/0.1.1/)
though I never used it.

to do it directly subprocess is usually preferable to os.system:
```

import subprocess
g="a bc"
subprocess.call(["zenity", "--info", "--text", g])

```

---

### Post by Datweakfreak on 2011-02-06
> **kimet said:**
> Bash can't know who is 'g'. Put inside os.system:

```
import os

os.system('g="abc"; zenity --info --text="$g"')

```

That worked!

I'll try out the other suggestions too, just for the learning cause.

Thanks, guys! :p

---

### Post by Miyavix3 on 2011-02-07
You could always use a string formatter.

```

import os
var = "This is an info box"
os.system("zenity --info --text=%s" %(var))

```

Seems a little bit easier.

---

