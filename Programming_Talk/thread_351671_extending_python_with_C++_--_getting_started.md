---
title: "extending python with C++ -- getting started"
date: 2007-02-02
forum: Programming Talk
---

### Post by enrico_ on 2007-02-02
Hi All,

I am using kubuntu 6.10 and I am learning python, in particular I am trying to write an extension in C++ using distutils.  

I understand that the default compiler is gcc, which obviously is not happy if I try to compile c++ code.  

How can I tell distutils to use g++?

Would it be a good idea to rebuild python using g++?  If so what's the best way to do so?

Any suggestion is welcome.

Thanks,
Enrico

---

### Post by duff on 2007-02-02
gcc handles c++ code just fine.  just make sure you link to **libstdc++.so**.

---

### Post by ansi on 2007-02-02
You can also use [PyCXX](http://cxx.sourceforge.net/) to easy way for python modules development with C++.

---

### Post by Wybiral on 2007-02-02
"Viper" (in my signature) is a small OpenGL module I wrote for python in C++. The source is available at that link, it might be a good reference to see how you can register constants/functions into python and grab objects from parameters+return object.

EDIT:

Ooops... I thought you meant write modules for, not compile python itself!

---

### Post by enrico_ on 2007-02-03
> **duff said:**
> gcc handles c++ code just fine.  just make sure you link to **libstdc++.so**.

Thanks!
Adding it in setup.py as follows did the trick.
```

module1 = Extension('mytest',
                    libraries = ['stdc++'],
                    sources = ['mytest.cpp'])

```

Enrico

---

### Post by enrico_ on 2007-02-03
ansi and  Wybiral,
thanks for the pointers.

PyCXX looks great, unfortunately part of my requirements is for the code to work (also) on Symbian Series 60, which handles exceptions in a non standard C++ way and does not like STL :( 

Do you have suggestions/pointers for how to deal with memory allocation / deallocation in a C++ extension?  I see that the Python C api provides PyMem_New, however I understand that I cannot use it to allocate a C++ class (because it'd have the same effect of using malloc).  Is there any alternative way for my C++ code to let Python know that I am using memory allocated with new? 

Otherwise, is there a standard way to handle deallocation when my module is unloaded? (either in case of clean exit or in case of excetpion handling) I am thinking of something like a *module destructor* or like the atexit() function..

My module needs to instantiate a C++ class (which takes quite some memory) at initialization, and keep a global pointer to it.

Is it enough if I define a cleanup() function in C++ and then I create a wrapper Python class that calls cleanup() in  __del__(self)? I tried this and it seems to work.. is there any disadvantage? It seems *too easy*.. ..or is this why everyone likes Python? ;)

Thanks,
Enrico

---

