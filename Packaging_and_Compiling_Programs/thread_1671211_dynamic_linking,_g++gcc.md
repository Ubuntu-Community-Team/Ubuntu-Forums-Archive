---
title: "dynamic linking, g++/gcc"
date: 2011-01-19
forum: Packaging and Compiling Programs
---

### Post by nearlymagicman on 2011-01-19
Hey,


i need to dynamic link a program with OTHER libraries than in /usr/lib or /usr/local/lib . 
So how am i gonna tell that to the programm? I was finally able to compile it, but as soon as I try to run it i get dependency errors:
```
./Tester: error while loading shared libraries: libModelv0.1.so: cannot open shared object file: No such file or directory

```

hope anybody can help.

A full line to finally compile the programm and be able to run it afterwarts would be perfectly fine.

My actual try is:
```
	g++ -o Tester main.cpp -L. -lModelv0.1 
```

---

### Post by SevenMachines on 2011-01-19
if you're looking for a command line version try setting LD_LIBRARY_PATH
$ LD_LIBRARY_PATH=/path/to/libs    mycommand

for more permanent special library dirs you might want to add and entry conf file in 
/etc/ld.so.conf.d/
and then run 
$ ldconfig -v

[EDIT] Sorry, LD_LIBRARY_PATH not _DIR,

---

