---
title: "How run .py file?"
date: 2012-02-28
forum: Programming Talk
---

### Post by eli1 on 2012-02-28
Hi,

I`m trying to run myfile.py in ubuntu terminal but its just givinig me :

Traceback (most recent call last):
  File"query.py", line 11, in <module>
    from cogent.db.ncbi import EUtils
ImportError: No module named cogent.db.ncbi

Please let me know what i have to do.

---

### Post by Hetepeperfan on 2012-02-28
To me it sound like python is running perfectly. However in the program you call function or object from a file called query.py, which is probably in the same directory as myfile.py is an import error. Import errors result occur when you are trying to import some functionality which is not installed on your machine.

cogent.db.ncbi import EUtils

On line 11 of query.py is the code somthing like:

```
from cognet.db.ncmi import EUtils
```you probably have to install a cognet module.

I don't know what it is.so search for it on the www and see how you can install it on your Ubuntu machine. And then your program might run without the import error.

cheers,

Maarten

---

### Post by jakewan on 2012-02-28
Here's information about PyCogent and ways to install it: [http://pycogent.sourceforge.net/install.html](http://pycogent.sourceforge.net/install.html).  Once installed, your program should at least make it passed that import.

Good luck,
Jacob

---

### Post by eli1 on 2012-02-28
hi...tanX for ur reply, I already download the PyCogent-1.5, but I have problem with installation. I went to [http://pycogent.sourceforge.net/install.html]("http://pycogent.sourceforge.net/install.html") and try to figure out how install it, but still not working and seems PyCogent is not installed. :confused:#-o

---

