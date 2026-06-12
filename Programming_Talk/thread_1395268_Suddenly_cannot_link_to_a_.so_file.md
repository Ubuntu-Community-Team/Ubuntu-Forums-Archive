---
title: "Suddenly cannot link to a .so file"
date: 2010-01-31
forum: Programming Talk
---

### Post by ghartshaw on 2010-01-31
The program that I am writing contains a shared library. It used to work fine, but suddenly started to give this error message when I run the executable.

```

./1-shapes: error while loading shared libraries: libglxe.so.0: cannot open shared object file: No such file or directory

```I do not think that I changed anything that would break it. Can anyone tell me what I am doing wrong?

Thanks in advance.

---

### Post by dwhitney67 on 2010-01-31
Where does the file libglxe.so.0 reside?  Is there also a libglxe.so file in the same place?

The problem could be that your LD_LIBRARY_PATH is not setup with the location.

When running an app, typically /usr/lib is referenced.  On some systems, /usr/local/lib is also referenced.  If your library is not in one of these locations, you will need to manually specify the location when you run the app.  For example:
```

LD_LIBRARY_PATH=/some/path/to/my/lib:$LD_LIBRARY_PATH ./1-shapes

```

P.S.  Weird name for the executable... up to you though.

---

### Post by ghartshaw on 2010-01-31
The Makefile was putting libglxe.so.0 in the base of the build directory, same as the executables, and then running 
```

export LD_LIBRARY_PATH=.:$LD_LIBRARY_PATH.

```It seems to work if I specify the LD_LIBRARY_PATH each time I run the program.

The weird thing is, it used to work without the LD_LIBRARY_PATH when executed, but suddenly it matters now.


> 
P.S.  Weird name for the executable... up to you though.     
It's a demo program, there is currently one other, and I am planning to make more. 
They all have a number and then a brief description/title of the demo as their name.

---

### Post by ghartshaw on 2010-01-31
Fixed it. I needed to add ```
-Wl,-rname,.
``` to the arguments I used to compile the executable. It works now.

---

