---
title: "Installed PyMySQL using pip but module not found"
date: 2014-05-05
forum: Programming Talk
---

### Post by donsy on 2014-05-05
I successfully installed module PyMySQL using pip

 and it shows up in
```
pip list
```
as 
```
PyMySQL (0.6.2)
```
However, when I try importing it in a script as in
```
import PyMySQL
```
I get the following error:
```
ImportError: No module named 'PyMySQL'
```

Is there some kind of path that needs to be set up in order to use this?

---

### Post by donsy on 2014-05-05
My mistakes, pip installs only for python2.7 and I was using python3.4, also PyMySQL is the package name but the imported module name is pymysql.

To use package PyMySQL with python3:

```

sudo apt-get install python3-pip
sudo pip3 install PyMySQL

```

---

