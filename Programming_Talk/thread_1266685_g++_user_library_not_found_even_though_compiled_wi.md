---
title: "g++ user library not found even though compiled with path"
date: 2009-09-14
forum: Programming Talk
---

### Post by geoglitch on 2009-09-14
Learning a little c++ shared library building.  I have packaged a library *libtester.so*.  I also have a main program that uses it *main.cpp*.  The library is in the same directory as main.  So I try compiling main as:
```
g++ -L. -ltester main.cpp -o main
```
But runnung
```
ldd main
```
says that libtester.so is not found, even though I told it where to look.  The library works because if I move it to /usr/lib, the library is found and the program runs.  Not sure where to go now, any help would be greatly appreciated.  I have tried expressing the directory in other ways with the -L option but none worked.

---

### Post by dribeas on 2009-09-15
When you run the program from the same directory the binary is, does it run? At any rate, you can always use LD_LIBRARY_PATH environment variable to tell the dynamic library loader where to look for extra dynamic libraries:

```

$ ls
exe libx.so
$ export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:.
$ ./exe

```

---

### Post by geoglitch on 2009-09-15
Thanks dribeas, that made it work.  If I open a terminal and cd to the folder, the program does not run with a 'cannot open shared object file: No such file or directory'.  If I add this directory to LD_LIBRARY_PATH, it then runs.  My issue is with having to set an environment variable for the program to work.  Am I wrong in thinking that the g++ -L flag is supposed to tell the linker to look in an aditional directory (effectively what setting the environment variable does)?  I would like to be able to elegantly use this library with many other of my own projects (mostly for learning c++).  Again thanks for your help.

---

### Post by dribeas on 2009-09-15
The problem is not with the linker, but with the dynamic library loader. The linker does find the library, else it would fail to compile and you would not have an executable. Depending on the distribution, sometimes dynamic libraries are found if they are bundled together with the executable without needing to modify the LD_LIBRARY_PATH variable.

---

### Post by geoglitch on 2009-09-15
Ah, that makes sense.  Heaps of thanks.

---

