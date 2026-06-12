---
title: "newbie wants to get help in runnin python"
date: 2008-10-04
forum: Programming Talk
---

### Post by Daniel_wang on 2008-10-04
I get a source pakage about python code,

but I try to run it using the command 

python python.py

it always prompt me that some module is not find like this 

```
my-desktop:~/BPDistr/BayesPrune$ python PruneGUI.py 
Traceback (most recent call last):
  File "PruneGUI.py", line 11, in <module>
    import numpy
ImportError: No module named numpy
```

---

### Post by Daniel_wang on 2008-10-04
is it any problme with the pythonpath?

---

### Post by CptPicard on 2008-10-04
Well, do you have numpy installed?

---

### Post by gomputor on 2008-10-04
You have to install the **numpy** library for Python.
Open a terminal and:
```
sudo apt-get install python-numpy
```

---

