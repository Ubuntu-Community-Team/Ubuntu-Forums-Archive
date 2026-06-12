---
title: "rename  group of files"
date: 2012-12-21
forum: Programming Talk
---

### Post by snowlizard31 on 2012-12-21
I have a script to rename files that getting the error   "error 21 the system cannot  find the file specified"

```

import os

src = "C:\\Users\\snowlizard\\Desktop\\fa"
files = os.listdir(src)


num = 1
for f in files:
    os.rename("%r"%f,"%d"%num)
    num += 1

```

---

### Post by spjackson on 2012-12-22
The result of os.listdir is a list of file **names**. It does not include the **path** to the directory containing the files. If you use print inside your for loop instead of os.rename, you will see this. Therefore the os.rename is trying to rename files in your current directory using the names from the src directory. Hopefully, these won't exist!

---

### Post by linuxonbute on 2012-12-22
> **snowlizard31 said:**
> I have a script to rename files that getting the error   "error 21 the system cannot  find the file specified"

```

import os

src = "C:\\Users\\snowlizard\\Desktop\\fa"
files = os.listdir(src)


num = 1
for f in files:
    os.rename("%r"%f,"%d"%num)
    num += 1

```

If you alter your code like this:
```

import os

src = "C:\\Users\\snowlizard\\Desktop\\fa"
dirnow=`pwd`

cd %src

files = os.listdir(src)

num = 1
for f in files:
    os.rename("%r"%f,"%d"%num)
    num += 1

cd $dirnow


```

i think it would work.

---

### Post by ofnuts on 2012-12-22
> **snowlizard31 said:**
> I have a script to rename files that getting the error   "error 21 the system cannot  find the file specified"

```

import os

src = "C:\\Users\\snowlizard\\Desktop\\fa"
files = os.listdir(src)


num = 1
for f in files:
    os.rename("%r"%f,"%d"%num)
    num += 1

```

Besides the obvious directory problem, you are also shooting yourself in the foot with the '***"%r"%f***' construct. listdir() returns a list of str, and for the str type, __repr__() return the string bracketed in single quotes. So instead of renaming "***foo***"you are trying to rename a file named "***'foo'***". You likely want something like:
```

os.rename("%s/%s" % (src,f), "%s/%d" % (src,num))

```You can also avoid the whole directory issue by moving to that directory:
```

os.chdir(src)
files = os.listdir('.')
for f in files:
    os.rename(f,str(num))
    num += 1

```

---

