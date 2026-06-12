---
title: "some Python help"
date: 2006-07-23
forum: Programming Talk
---

### Post by Cyraxzz on 2006-07-23
Just used a py program that ships with Python 2.4, called freeze for compiling .py into executables, i perfomed a simple example just to check if this program worked.

I got an error msg in the terminal saying that it did not found an required file
named:
"/usr/lib/python2.4/config/config.c.in"

But how is that? isin't this supposed to be included in the python 2.4?

---

### Post by Daverz on 2006-07-24
It's in python-dev.  For these things I usually google on the filename and debian, though maybe experienced debian people know of some way to do it from the command-line.

---

### Post by Cyraxzz on 2006-07-24
i've fixed this problem, it was in another location here, something must have moved it.

---

### Post by ifokkema on 2006-07-24
> **Daverz said:**
> It's in python-dev.  For these things I usually google on the filename and debian, though maybe experienced debian people know of some way to do it from the command-line.
```
sudo apt-get install apt-file
sudo apt-file update
apt-file search /usr/lib/python2.4/config/config.c.in
```
:)

---

