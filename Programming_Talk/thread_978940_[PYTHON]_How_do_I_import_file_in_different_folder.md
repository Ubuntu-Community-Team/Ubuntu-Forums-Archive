---
title: "[PYTHON] How do I import file in different folder?"
date: 2008-11-11
forum: Programming Talk
---

### Post by regomodo on 2008-11-11
#

---

### Post by LaRoza on 2008-11-11
> **regomodo said:**
> I'm a bit perplexed by a certain section of a [tutorial]("http://www.die-offenbachs.de/eric/tutorials/LogParser/chap5.html") in where a root file imports a file "./ui/MainWindow.py" by using:

```
from ui.MainWindow import MainWindow
```

I've tried to do this as well but the interpreter spits error about not being able to do the same. Has this person making the tutorial got this wrong? How would I go about doing this?

Put a file named "__init__.py" in ui/.

---

### Post by Zootropo on 2008-11-11
> **regomodo said:**
> I'm a bit perplexed by a certain section of a [tutorial]("http://www.die-offenbachs.de/eric/tutorials/LogParser/chap5.html") in where a root file imports a file "./ui/MainWindow.py" by using:

```
from ui.MainWindow import MainWindow
```

I've tried to do this as well but the interpreter spits error about not being able to do the same. Has this person making the tutorial got this wrong? How would I go about doing this?
This is because ui is a folder, but it's also a package. A package in Python is just a folder with an __init__.py file in it.

---

### Post by regomodo on 2008-11-11
#

---

### Post by nvteighen on 2008-11-11
> **regomodo said:**
> Ah. So that rather crucial step is omitted in that tutorial. Is the file blank?
Usually yes, unless you need some variables global to the package and that kind of things.

---

### Post by regomodo on 2008-11-11
#

---

