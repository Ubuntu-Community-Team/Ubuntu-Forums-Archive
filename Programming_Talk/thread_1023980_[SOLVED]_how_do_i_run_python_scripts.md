---
title: "[SOLVED] how do i run python scripts?"
date: 2008-12-28
forum: Programming Talk
---

### Post by SonnHalter on 2008-12-28
how do i run .py files i made?

---

### Post by pokerbirch on 2008-12-28
Manual method: cd to the directory of your py script and type:
```
python nameofyourscript.py
```

Easy method: use an editor with a 'run' button such as Geany

---

### Post by SonnHalter on 2008-12-28
thx, i like geany

---

### Post by catchmeifyoutry on 2008-12-28
if you want to make a python script executable as a command, place a special first comment line such that your shell knows how to execute it:
```

cmiyt@catchmeifyoutry-desktop>which python
/usr/bin/python
cmiyt@catchmeifyoutry-desktop>cat myscript.py
#! /usr/bin/python

print "hello world!"
cmiyt@catchmeifyoutry-desktop>chmod +x myscript.py
cmiyt@catchmeifyoutry-desktop>./myscript.py
hello world!

```

So the first line of your script should be "#! /usr/bin/python" and then change the file properties to executable.

---

