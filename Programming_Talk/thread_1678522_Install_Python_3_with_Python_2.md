---
title: "Install Python 3 with Python 2"
date: 2011-01-30
forum: Programming Talk
---

### Post by seandude on 2011-01-30
I'm taking a class that requires us to use Python 3, but I'd like to not have all my applications in Python 2 to break.  Is there any way to install Python 3.1.3 so that it won't overwrite the older version?

---

### Post by Queue29 on 2011-01-30
Yea, just do:

```
sudo apt-get install python3
```

Ubuntu deliberately packages python3 in such a way it won't interfere with python2. 

To run your programs, you'll type "python3" at the command line instead of just "python".

---

### Post by seandude on 2011-01-30
> **Queue29 said:**
> Yea, just do:

```
sudo apt-get install python3
```

Ubuntu deliberately packages python3 in such a way it won't interfere with python2. 

To run your programs, you'll type "python3" at the command line instead of just "python".

Wow, thank you.  I really didn't expect it to be nearly that easy.  Frankly I was expecting to have to build it from source and redirect that outputs into uniquely named directories.  This really makes life a hell of a lot more convenient.

---

### Post by Vox754 on 2011-01-30
> **seandude said:**
> Wow, thank you.  I really didn't expect it to be nearly that easy.  Frankly I was expecting to have to build it from source and redirect that outputs into uniquely named directories.  This really makes life a hell of a lot more convenient.

That was the case some distributions ago, but now Python 3 is finally packaged, so it should be easier to test Python 2 and 3 without users breaking their systems.

Always look for packaged software first.

However, remember that the default Python is still version 2, don't do anything crazy like arbitrarily changing the symbolic links to redirect the default Python, as other modules have not been ported yet to version 3.

---

