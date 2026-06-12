---
title: "Python script problem module import problem"
date: 2009-05-01
forum: Programming Talk
---

### Post by dvine on 2009-05-01
Hello,

when I run my python scripts from inside IPython 0.9 (Ubuntu 9.04, Python 2.6) they work fine. 

When the same scripts are run from the terminal some modules I import raise an ImportError exception. So modules that are installed and can be found by ipython cannot be found when running from the terminal. I don't understand why?

For example, the following code runs under IPython:

```

#test.py
#!/usr/bin/env python
import os
import scipy as sp

def main():
    m=sp.zeros((100))

if __name__ == '__main__':
    main()

```

but if I run the same script from the terminal as
```
python test.py
``` 
i get
```
ImportError: no module names scipy
```

Any ideas?

Thanks in advance,
David

---

### Post by loell on 2009-05-01
you just need to install **python-scipy**

```
sudo apt-get install python-scipy
```

---

### Post by dvine on 2009-05-01
@loell: Thanks - tried it and it says I have the latest version of scipy  installed.

---

### Post by loell on 2009-05-01
wierd, i just got scipy imported with python-scipy installed,  and no error.

---

### Post by geirha on 2009-05-01
It'll look for that module in all directories listed in sys.path, so print out sys.path in both IPython and python and compare.

```
import sys
print sys.path
```

---

### Post by imdano on 2009-05-01
Does it work if you use the python interactive prompt (as opposed to ipython)?

---

### Post by dandaman0061 on 2009-05-01
It may also depend on what directory you are currently in when you run the script.  This will show up in geirha's suggestion of printing sys.path.  This is the order of directories python will look to find modules.

Another environment variable to check is $PYTHONPATH
in terminal:
```
echo $PYTHONPATH
```

Usually the sys.path will be something like .(current_dir):$PYTHONPATH:/usr/lib/pythonX.X/:/usr/lib/pythonX.X/site-packages
There will be more than that if you have installed packages.

And YET another thing for you to try... is to see if you have more than 1 version of python installed.
run ipython and look at the version number of python that it prints out.  Then in the terminal try just running the normal interpreter 'python' and seeing if they are the same version.

P.S. Your she-bang line should be the first line in your script.
```

#!/usr/bin/env python

#test.py

```

---

