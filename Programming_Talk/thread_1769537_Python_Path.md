---
title: "Python Path?"
date: 2011-05-28
forum: Programming Talk
---

### Post by Fusuy on 2011-05-28
Hello, people.

I was practicing python on windows and i wrote this module to easily import modules from my workspace folder when using interpreter.

```

from sys import path

def printPath():
    for p in path:
        print p

def addToPath():        
    path.append("d:\workspace\python\test")
    path.append("d:\workspace\python\diveInto")

if __name__ == "__main__":
    addToPath()
    printPath()
```

when i drop this module where python.exe, i simply call writing "import pypath" on interpreter then execute addToPath function after that i can easily import modules on my workspace.

but now on ubuntu i can't find where python files is. how can i write a module acting like this one on ubuntu and where can i place it.

sorry about my english.

Thanks to all.

---

### Post by ssam on 2011-05-28
the traditional way to do this on linux is to add the directories to the PYTHONPATH environment variable.

put the following in you .bashrc file (in your home folder).

```

export PYTHONPATH=\workspace\python\test:\workspace\python\diveInto:$PYTHONPATH

```

the more robust method, once you are creating packages that you want to distribute is to use setuptools or distribute to install your package into the standard python directories.

---

### Post by Fusuy on 2011-05-28
i added this line into .bashrc file but when i print, sys.path my path doesn't seem there.*

```
export PYTHONPATH=/home/yusuf/workspace/MyTestProject/src/test/:$PYTHONPATH
```is this bash programming? i am totaly noob of this.

* edited.

---

### Post by Smart Viking on 2011-05-28
```

import sys
sys.path = sys.path + ['/some/directory']

```

---

### Post by Fusuy on 2011-05-28
oh, i did it!

.bashrc stuff just worked. I think, i have to restart terminal everytime i changed bash files to effect?

thanks a lot everyone.

(=

---

