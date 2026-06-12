---
title: "Python 3 on Ubuntu 11.10"
date: 2012-03-24
forum: Programming Talk
---

### Post by kemuri22 on 2012-03-24
I can't import random module in Python3.2
Maybe I need to install some addons or reinstall
Any help?

terminal say:

kemuri@kemuri-Extensa-5230:~/Desktop$ python3.2
Python 3.2 (r32:88445, Mar 23 2012, 07:26:07) 
[GCC 4.6.1] on linux3
Type "help", "copyright", "credits" or "license" for more information.
>>> import random
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/local/lib/python3.2/random.py", line 46, in <module>
    from hashlib import sha512 as _sha512
  File "/usr/local/lib/python3.2/hashlib.py", line 138, in <module>
    globals()[__func_name] = __get_hash(__func_name)
  File "/usr/local/lib/python3.2/hashlib.py", line 74, in __get_builtin_constructor
    import _sha256
ImportError: No module named _sha256

---

### Post by MadCow108 on 2012-03-24
/usr/**local**/lib/python3.2/hashlib.py

the local in there indicates you installed something yourself, and probably something went wrong during that.
The python3 shipped with ubuntu 11.10 works fine,  can't you use that?

---

