---
title: "ldconfig without root permissions?"
date: 2009-06-30
forum: Packaging and Compiling Programs
---

### Post by jsmidt on 2009-06-30
I am trying to install a program on a computer I do not have root permissions on.  I successfully built and installed the libraries the package builds on and the package itself with the libraries in ~/lib and the binaries in ~/bin.

Now, when I run the program I get this error: 

```
ImportError: liblapack.so: cannot open shared object file: No such file or directory
```

But liblapack.so is a library in ~/lib and the program isn't seeing it.  Normally I would do some type of ldconfig to get this to work right?

But since I don't have root permissions, how do I get my program to see liblapack.so in my ~/lib directory when I run it?  Thanks.

---

### Post by lensman3 on 2009-06-30
Do a "man ld.so" and look for the environment variable LD_LIBRARY_PATH.  You will have set this variable to point to ~/lib.  LD_LIBRARY_PATH is a user accessible library pointer for your problem.  You can add multiple directories to the path.  Syntax is similar to the PATH statement.

Hope this helps.

---

