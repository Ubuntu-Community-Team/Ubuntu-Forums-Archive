---
title: "[python] multiple files of source code"
date: 2008-12-30
forum: Programming Talk
---

### Post by TreeFinger on 2008-12-30
how do I use multiple files of source code with python?

Right now I want to begin with one file that contains one class, along with GUI components. 

and have that class initialize an instance of another object that is defined in another file.

---

### Post by wmcbrine on 2008-12-30
The key is "import".

```

import yourmodule

newinstance = yourmodule.YourClass()

```

or you could say:

```

from yourmodule import YourClass

newinstance = YourClass()

```

---

### Post by Sprut1 on 2008-12-30
Also there is the "package" solution where you have a folder "Modules" (you can call the folder whatever you want) with several .py files which can all contain 1 or more classes. Inside the Modules folder you put a file called __init__.py (notice double _ before and after) where you import all modules within the folder.

Folder hiarchy:
```
Modules
    /Functions.py
    /MyOsRelatedSTuff.py
    /whatever.py
    /__init__.py
```

Inside __init__.py

```
from Functions import *
import MyOsRelatedSTuff
import whatever
```

Notice that you exclude the .py - then to import this in your main_app.py just:

```
Import foldername
```

In our case

```
Import Modules
```

Then to use a class within Functions you need to call Modules.Functions.YourClass()

This is a really great way of orginazing your code, although this is probably more used on bigger projects.

---

