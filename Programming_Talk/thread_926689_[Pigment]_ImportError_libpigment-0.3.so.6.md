---
title: "[Pigment] ImportError: libpigment-0.3.so.6"
date: 2008-09-22
forum: Programming Talk
---

### Post by Intosia on 2008-09-22
Hi

I installed Pigment (0.3.9) & Pigment-Python (0.3.7) from source (from the website), but when i try to run a example code i get the folowing error:

```
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "pgm/__init__.py", line 28, in <module>
    from _pgm import *
ImportError: libpigment-0.3.so.7: cannot open shared object file: No such file or directory

```

But when i search for the file i get this:
```

root@intosia-laptop:/home/intosia/pigment-python-0.3.7# find / libpigment-0.3.so.7|grep libpigment-0.3.so.7
find: /home/intosia/.gvfs: Permission denied
/home/intosia/pigment-0.3.9/pgm/.libs/libpigment-0.3.so.7.0.0
/home/intosia/pigment-0.3.9/pgm/.libs/libpigment-0.3.so.7
/usr/local/lib/libpigment-0.3.so.7.0.0
/usr/local/lib/libpigment-0.3.so.7
find: libpigment-0.3.so.7: No such file or directory

```

I dont know there Python is searching the file??

Im struggling with this for like 2 weeks, and i really need it to work for a project at school :(

---

