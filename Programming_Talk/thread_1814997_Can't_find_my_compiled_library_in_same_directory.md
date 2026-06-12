---
title: "Can't find my compiled library in same directory?"
date: 2011-07-30
forum: Programming Talk
---

### Post by AlexRamallo on 2011-07-30
I compiled a simple shared library for my program using g++. Its named "libFunctionLib.so" and it is in the same directory as the program.

I compiled the program(the one that uses it) using this command:
```

g++ main.cpp -o out -L. -lFunctionsLib

```
and that produced the program 'out' in the same directory as the libFunctionLib.so file. The problem is that when I try to run 'out' with the command
```
./out
```
I get this error:
> ./out: error while loading shared libraries: libFunctionsLib.so: cannot open shared object file: No such file or directory
(and that file definitely exists and it is in the same directory as the binary)
It seems like its only searching in the /usr/lib directory and not the local working directory. Is there a way get around this so that it searches for libraries in the working directory as well rather than just the systems /usr/lib directory?

---

### Post by karlson on 2011-07-30
> **AlexRamallo said:**
> I compiled a simple shared library for my program using g++. Its named "libFunctionLib.so" and it is in the same directory as the program.

I compiled the program(the one that uses it) using this command:
```

g++ main.cpp -o out -L. -lFunctionsLib

```
and that produced the program 'out' in the same directory as the libFunctionLib.so file. The problem is that when I try to run 'out' with the command
```
./out
```
I get this error:

(and that file definitely exists and it is in the same directory as the binary)
It seems like its only searching in the /usr/lib directory and not the local working directory. Is there a way get around this so that it searches for libraries in the working directory as well rather than just the systems /usr/lib directory?

Have you set LD_LIBRARY_PATH to include the directory where the library is?  You also may want to check
[http://manpages.ubuntu.com/manpages/hardy/man8/ldconfig.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/ldconfig.8.html)

---

### Post by ziekfiguur on 2011-07-30
Make sure the library file is set as executable.

---

### Post by AlexRamallo on 2011-07-30
> **karlson said:**
> Have you set LD_LIBRARY_PATH to include the directory where the library is?  You also may want to check
[http://manpages.ubuntu.com/manpages/hardy/man8/ldconfig.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/ldconfig.8.html)
Thanks I got it to work
> Make sure the library file is set as executable.
I think g++ does that automatically, because it was already marked as executable

---

