---
title: "ImportError: No module named"
date: 2020-08-12
forum: New to Ubuntu
---

### Post by vineet40 on 2020-08-12
Hi Everyone,

I am facing issue while using python under ubantu.

Python version - 3.5


Python file = mycode.py at current project directory


PyObject *pName ;
pName = PyUnicode_FromString("mycode");  

When execute getting below error :


**ImportError: No module named 'mycode'**


Please help , it would be really appreciated.

Thanks
Vineet

---

### Post by drpjkurian on 2020-08-23
I'm not well versed in Python. But I beleive this [page]("https://leemendelowitz.github.io/blog/how-does-python-find-packages.html") might helpyou.

---

### Post by monkeybrain20122 on 2020-08-23
python has to be able to find your "mycode". It will  search the standard locations.  e.g  ~/.local/lib/pythonXY/site-packages, /usr/local/lib/pythonXY/site-packages ... (the first one you can place files without sudo) If your module is in a location other than these standard ones, one way to make python aware of it is  to add this to the beginning of your script that imports "mycode"

```
import sys
sys.path.insert(0, "/path/to/mycode")
```

---

