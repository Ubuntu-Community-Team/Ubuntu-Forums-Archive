---
title: "No module named matplotlib.pyplot after update to python 3.2 Ubuntu 12.04"
date: 2012-06-25
forum: Programming Talk
---

### Post by surfcast23 on 2012-06-25
After updating to python 3.2 I get the following error when I try to run a script using  IDLE 

```
No module named matplotlib.pyplot
```I can import matplotlib in the terminal using python 2.7.3, but not python3. The module is installed in 
```
/usr/lib/pymodules/python2.7/matplotlib/pyplot.pyc -> /usr/share/pyshared/matplotlib/pyplot.py
``` My guess is that python 3.2 and and IDLE do not know where to look for Matplotlib.pyplot. I would like to ask if someone can explain to me how to have python 3.2 find and import matplotlib and its associated modules. Thanks in advance.

---

### Post by surfcast23 on 2012-06-26
Bump

---

### Post by Zugzwang on 2012-06-26
Did you actually install the Python3-version of the library?

---

### Post by surfcast23 on 2012-06-26
I downloaded what was available in the software center

---

### Post by Zugzwang on 2012-06-26
The answer appears to be here: [http://stackoverflow.com/questions/8605847/how-to-install-matplotlib-with-python3-2](http://stackoverflow.com/questions/8605847/how-to-install-matplotlib-with-python3-2)

---

### Post by surfcast23 on 2012-06-26
I did see that, but was hoping that a package might have been released through Ubuntu in the time since that post.  Thank you

---

### Post by MadCow108 on 2012-06-26
there is no official matplotlib release supporting python3

but the current git head does, so the next release 1.2, will very likely have python3 support. But its still while away.

---

### Post by surfcast23 on 2012-06-27
Thank you

---

