---
title: "Python: Getting file name."
date: 2010-11-24
forum: Programming Talk
---

### Post by Sailor5 on 2010-11-24
Ahoy Sailor!

So I've compiled my Python script using Py2Exe. Now I'm facing a dilemma, getting the file name of itself ( the file I compiled ).

I've used two different commands to get the name. However they both have issues.
```
print sys.argv[0]
```This works fine and dandy. If you execute the script via console. If you execute it via double clicking. It won't hold the name.

```
nme = inspect.currentframe().f_code.co_filename
```This comes back with the original source file name. So after we've built an executable from SOURCE.py to get EXECUTABLE.exe and use this method. It will come back with SOURCE.py not the executable name which we want.

What other methods are there?

Thanks Bye!

---

### Post by DaithiF on 2010-11-24
```
import os, sys

if __name__ == '__main__':
    print 'Hello world'
    if hasattr(sys,"frozen") and sys.frozen in ("windows_exe", "console_exe"):
        path = (os.path.abspath(sys.executable))
    else:
        path = os.path.abspath(__file__)
    print 'hello from %s' % path

```

---

### Post by Sailor5 on 2010-11-26
> **DaithiF said:**
> ```
import os, sys

if __name__ == '__main__':
    print 'Hello world'
    if hasattr(sys,"frozen") and sys.frozen in ("windows_exe", "console_exe"):
        path = (os.path.abspath(sys.executable))
    else:
        path = os.path.abspath(__file__)
    print 'hello from %s' % path

```

```
Hello world
Traceback (most recent call last):
  File "Python.py", line 25, in ?
NameError: name '__file__' is not defined
```

---

### Post by DaithiF on 2010-11-26
what is sys.frozen when you execute it as an .exe?

---

### Post by Sailor5 on 2010-11-26
> **DaithiF said:**
> what is sys.frozen when you execute it as an .exe?
it comes back with```
AttributeError: 'str' object has no attribute 'frozen'
```

---

### Post by DaithiF on 2010-11-26
hmm, can you check you code carefully for typos -- that error indicates you've asked for the frozen attribute of some string object, but i'm asking you what the frozen attribute of the sys module is.

---

### Post by Sailor5 on 2010-11-26
> **DaithiF said:**
> hmm, can you check you code carefully for typos -- that error indicates you've asked for the frozen attribute of some string object, but i'm asking you what the frozen attribute of the sys module is.
Oops I'd defined a variable named sys (Doh!) printing sys.executable gets me the file name. Thanks a lot!

---

