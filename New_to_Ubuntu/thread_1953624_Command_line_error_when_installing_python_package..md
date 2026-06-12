---
title: "Command line error when installing python package. What does it mean?"
date: 2012-04-06
forum: New to Ubuntu
---

### Post by kramer65 on 2012-04-06
Hello,


I just downloaded a [little python package]("http://code.google.com/p/deap/") (for developing evolutionary algorithms) which I tried to install using their setup.py file by typing: "*python setup.py install*".

Unfortunately this results in the following error: 
> running install
running build
running build_py
running build_ext
building 'deap.cTools' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -I/usr/include/python2.7 -c deap/cTools.cpp -o build/temp.linux-i686-2.7/deap/cTools.o
cc1plus: watch out: command line option ‘-Wstrict-prototypes’ is valid for Ada/C/ObjC but not for C++ [enabled by default]
deap/cTools.cpp:1:20: fatal error: Python.h: File or folder does not exist
compilation terminated.
error: command 'gcc' failed with exit status 1

I also tried doing it using "sudo", but this resulted in the same error.

I don't really know what the problem is here. Does anybody know how I can install this package anyway? All tips are welcome!

---

### Post by kramer65 on 2012-04-06
Nevermind! I fixed it by installing the python headers through Synaptic: python-dev

Sorry for your time!

---

