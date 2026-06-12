---
title: "[SOLVED] how do you delete files with .!rf as extension at command line"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by stinger30au on 2008-11-03
i have a directory with a ton of zip files and many other files all mixxed together and im slowly sorting thru them

i have a ton of files like this

data1.!rf
data2.!rf

what command do i use to delete all the .!rf files????



thanks

---

### Post by taurus on 2008-11-03
Maybe

```
rm *rf
```
And if you don't want it to ask you for a confirmation for each delete, you can use the -rf argument.

```
rm -rf *.rf
```

---

### Post by asmoore82 on 2008-11-03
^^ That is a good answer, but be sure to use extreme caution with ``rm -rf''

and you can also "backslash escape" the special character(``!'' in this case)
if you need finer-grained control:

```
rm data1.\!rf
```

---

### Post by stinger30au on 2008-11-04
awesome, thanks guys

---

