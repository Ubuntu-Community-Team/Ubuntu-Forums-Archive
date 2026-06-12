---
title: "Python code location?"
date: 2008-10-23
forum: Programming Talk
---

### Post by keeler1 on 2008-10-23
Is it possible to determine the directory where the currently running python code is located in at runtime.

I am writing a program which contains a main directory with multiple packages in the main directory.  One of the subdirectories needs a module in another directory.  How can I import this?

---

### Post by G|N| on 2008-10-24
If you are installing your application you should modify the setup.py file and add this:

```

setup(
    packages = [('main'),('main/otherdir')]
    )

```

and then:
```

from main.otherdir import myotherfile

```

If you really want to know the path:
```

os.getcwd()

```

Hope this helps

---

### Post by keeler1 on 2008-10-24
If I execute os.getcwd() it gives me the directory I am in, not necessarily the directory the code is in.

Is there any way to figure out where the code is.

---

### Post by fiddler616 on 2008-10-25
If your only problem is importing modules from a different directory, try playing around with the PYTHONPATH.

---

### Post by keeler1 on 2008-10-26
That was one of the ways I was considering.  The only problem is that I need to know a base directory to append to the PYTHONPATH.  It is quite easy to set the path using sys.path.append(<path>).  The problem remains that I do not know the path to.  

I will probably using an installation script with DistUtils.  Does anyone know exactly how this would act.  Supposedly the setup method will install your files to the proper locations.

Example:  on linux it should put all the libraries in /usr/lib/python<version>/site-packages/<myprogram name>, and the executable in /usr/bin.

Does anyone know if this is actually what it does or how it works.

---

### Post by imdano on 2008-10-26
> **keeler1 said:**
> 
Example:  on linux it should put all the libraries in /usr/lib/python<version>/site-packages/<myprogram name>, and the executable in /usr/bin.

Does anyone know if this is actually what it does or how it works.Yep, the setup() method that you call in the setup.py script has a "py_modules" keyword that takes a list of modules to install to /usr/lib/python<version>/site-packages/.  There's also a data_files keyword that you can use to install arbitrary files (like the executable) to any directory you want (like /usr/bin).

See the [Python documentation](http://docs.python.org/distutils/setupscript.html) on this subject for more info.

edit: Also, you could use the __file__ attribute that is created in every Python program to get the directory its running in.  It contains the path to the file currently running, so you could use os.path.dirname(os.path.realpath(__file__)) to just get the directory its running in.

---

### Post by keeler1 on 2008-10-27
Thanks a lot.  I knew there had to be a way to find that out.

Also is the DistUtils platform independent, or will I have to have different setup scripts for each platform?

---

### Post by cmat on 2008-10-27
```
import sys, os
myPath = os.path.dirname(sys.path[0])
print myPath
```

I used to use os.getcwd() but there are some cases that would not work.

---

### Post by imdano on 2008-10-27
> **keeler1 said:**
> Thanks a lot.  I knew there had to be a way to find that out.

Also is the DistUtils platform independent, or will I have to have different setup scripts for each platform?You can use just one script, though you might have to have some logic that changes the paths you use for the data_file list depending on the platform.

---

