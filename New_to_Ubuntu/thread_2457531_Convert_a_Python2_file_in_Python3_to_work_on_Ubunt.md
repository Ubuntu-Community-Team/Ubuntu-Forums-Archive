---
title: "Convert a Python2 file in Python3 to work on Ubuntu 20.04"
date: 2021-02-04
forum: New to Ubuntu
---

### Post by elioi on 2021-02-04
I have an application that run on Ubuntu 16.04 but I want to migrate it on Ubuntu 20.04. It doesn't work because I think it's not compatible with Python3. What are the steps to follow to update it? Thank you for your help

---

### Post by Impavidus on 2021-02-04
Open the Python code in a text editor and change it to work in Python 3. You have to know Python 2 and Python 3 to do so.

Maybe the file is actually compatible with both Python 2 and Python 3, but fails to say so. In that case, just changing the first line (declaring the interpreter to use) may fix it. python and python2 refer to Python 2, python3 refers to Python 3. This is because some old programs don't tell for which Python version they were written and for those one must assume Python 2.

Finally, on Ubuntu 20.04 it's still possible to install Python 2. It's no longer installed by default and no longer maintained from upstream. It's in the universe repository, so you may have to enable that.

---

### Post by oldfred on 2021-02-04
This program will convert about 80% (depending) of your code. 
[https://docs.python.org/3/library/2to3.html](https://docs.python.org/3/library/2to3.html)

The more complex the code the more difficult it is to convert.

---

