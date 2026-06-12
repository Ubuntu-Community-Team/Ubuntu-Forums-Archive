---
title: "Add in C programs to python"
date: 2009-02-09
forum: Programming Talk
---

### Post by djbushido on 2009-02-09
How would one go about loading a C program into a module? I tried a plain import (knowing it could never be that easy) and guess what - it didn't work (the source WAS inside the module's directory). 
So how would I import the functions, etc? (from x import *)?
Also, is it possible to link to functions in a compiled C program? Doubt it, but it's worth checking.

---

### Post by DeadRobot on 2009-02-09
Try checking this out:
[http://docs.python.org/library/ctypes.html](http://docs.python.org/library/ctypes.html)

---

### Post by djbushido on 2009-02-09
Nice, if I was going to do dll's. I need "C" source files to import. Thanks though.

---

### Post by Wybiral on 2009-02-09
> **djbushido said:**
> Nice, if I was going to do dll's. I need "C" source files to import. Thanks though.

That's the thing, you compile the C file to a shared object / dll, and then you can access the functions/symbols in Python.

There are also things like SWIG which will generate a Python interface for your C source...

---

### Post by Tony Flury on 2009-02-10
> **djbushido said:**
> Nice, if I was going to do dll's. I need "C" source files to import. Thanks though.

Cleary importing the C source is never ever going to work - the python interpreter will never be able to understand the C source - you will need a C compiler to understand the C source code. You would not expect the C compiler to be able to understand your python code would you.

Have a read of : [http://docs.python.org/c-api/index.html](http://docs.python.org/c-api/index.html) - i have not used it, but if it is anything like the rest of the documentation on that site, it will explain very well exactly what you need to do to get your Python code to be able to execute your functions written in C.

---

### Post by djbushido on 2009-02-10
Okay, thanks for all your guys' help.
I'm not wanting to do SWIG, as it would force me to prototype all variables, etc. Since I am doing this for the flam3 program, that would take forever.
How would one then go about creating a shared object library?
And for extra credit, how would this happen on windows?

---

### Post by nvteighen on 2009-02-10
To create a shared library from a C source: [http://crasseux.com/books/ctutorial/Building-a-library.html#Building%20a%20library](http://crasseux.com/books/ctutorial/Building-a-library.html#Building%20a%20library)

Then, you have to put the .so file into a place the system can recognize it. You have two options.

1) Copy it to /usr/local/lib
2) Do this in Terminal:
```

export LD_LIBRARY_PATH=(the directory):$LD_LIBRARY_PATH

```

The second one will be lost when closing the Terminal, unless you copy that line into you ~/.bashrc file. I'd recommend using the fisrt one.

After that (no matter what option you chose), you have to do the following in order to update the system's libraries database:
```

sudo ldconfig

```

---

### Post by djbushido on 2009-02-10
okay, i had another idea: ./configure --enable-shared.
That should work, right?
Also, can python link to class (technically structure) types? Ex. in the C program there is a "my_class" structure, can python use this? I assume an "import ctypes" is needed.

---

