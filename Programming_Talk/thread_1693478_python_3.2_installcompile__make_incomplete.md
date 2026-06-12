---
title: "python 3.2 install/compile  make incomplete"
date: 2011-02-22
forum: Programming Talk
---

### Post by cjejuni on 2011-02-22
hi all:
ubuntu 10.10 env...trying to install python 3.2 from python.org. got to the 'make' stage. did not have errors but missing some important bits to build complete python 3.2 env. i have checked the ff and are installed per synaptic pkg mgr. want 'make' to include modules bits when it is done. howto fix these and where?

'Python build finished, but the necessary bits to build these modules were not found:
_dbm               _gdbm              _sqlite3        
_tkinter           bz2                                
To find the necessary bits, look in setup.py in detect_modules() for the module's name.'

tia,
cj

---

### Post by lkjoel on 2011-02-23
> **cjejuni said:**
> hi all:
ubuntu 10.10 env...trying to install python 3.2 from python.org. got to the 'make' stage. did not have errors but missing some important bits to build complete python 3.2 env. i have checked the ff and are installed per synaptic pkg mgr. want 'make' to include modules bits when it is done. howto fix these and where?

'Python build finished, but the necessary bits to build these modules were not found:
_dbm               _gdbm              _sqlite3        
_tkinter           bz2                                
To find the necessary bits, look in setup.py in detect_modules() for the module's name.'

tia,
cj
For tkinter, type in:
```
sudo apt-get install python-tk

```
I don't know about the rest.

---

