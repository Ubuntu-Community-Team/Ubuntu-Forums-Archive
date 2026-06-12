---
title: "Python 3: No module named sha256 error"
date: 2012-10-13
forum: Programming Talk
---

### Post by touches on 2012-10-13
Hi all, I am learning python and i have installed python 3 on my Ubuntu 11.10. Now i just tried writing a simple import random statement and i get
```

from hashlib import sha512
Traceback (most recent call last):
  File &quot;<stdin>&quot;, line 1, in <module>
  File &quot;/usr/local/lib/python3.2/hashlib.py&quot;, line 138, in <module>
    globals()[__func_name] = __get_hash(__func_name)
  File &quot;/usr/local/lib/python3.2/hashlib.py&quot;, line 74, in __get_builtin_constructor
    import _sha256
ImportError: No module named _sha256

```I have searched the net and i find no clues relating to Python 3 with this module. Can anybody help me out?? Python learning is turning out to be a tough battle with just clearing up all the module errors!!

---

### Post by spjackson on 2012-10-13
This probably doesn't help you, but that import statement works with python 3.1.2 on Lucid (installed from the repository). The documentation for 3.2 suggests that it should work there too. This suggests to me that it's an issue with your python3 installation rather than with your code, but I could be wrong.

---

### Post by touches on 2012-10-13
@spjackson
Hmmm it could be so if i want to re-install Python 3, how do i remove the existing copy of Python 3 and what would be the best way to install Python 3? I'd really like to get started with python

---

### Post by spjackson on 2012-10-13
I don't know how you installed it in the first place, but since it is in  /usr/local/lib/python3.2 it won't have been from the Ubuntu repositories. Python 3.2 is available in the repositories for 11.04, so I suggest that you install that via synaptic, apt-get or whatever your preference.

---

### Post by touches on 2012-10-13
@spjackson

Yes i didn't install it from the repositories,so if want to install from the repositories how do i remove the existing version of python 3.2? Are there any commands to remove them or how do i do it?

---

### Post by trent.josephsen on 2012-10-13
Depends on how you installed it in the first place. You can't use apt to uninstall something that it didn't put there to begin with -- it's not part of the package database.

If you installed with "make install", "make uninstall" has been known to work with some packages. I don't know about Python.

---

### Post by encolpe on 2012-12-20
Try to add libsasl2-dev package then your python.

---

