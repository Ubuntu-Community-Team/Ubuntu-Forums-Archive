---
title: "Importing python modules in C++ (python 2.6)"
date: 2009-11-21
forum: Programming Talk
---

### Post by Enk on 2009-11-21
Hi

I am currently working on a little hobby project in C++, but wants to move some of the code to a scripted language. 

I've used some Python and really like it so it was an obvious choice :)

I found [this]("http://www.codeproject.com/KB/cpp/embedpython_1.aspx") article on codeproject.com, but this doesn't work with 2.6.

I'm getting an "ImportError: Import by filename is not supported." at the PyImport_Import()-function since 2.6 doesn't allow loading of modules this way.

So how can I load python scripts in C++?

---

### Post by TheStatsMan on 2009-11-21
If you just want to run a python script (eg: foo.py) from c++ then you can use something like this 

```

#include "python2.6/Python.h"

    Py_Initialize();
    FILE *fp=fopen("foo.py","r+"); 
    PyRun_SimpleFile(fp,"foo.py");
    Py_Finalize();

```

You will need to link to libpython2.6 as well.

---

