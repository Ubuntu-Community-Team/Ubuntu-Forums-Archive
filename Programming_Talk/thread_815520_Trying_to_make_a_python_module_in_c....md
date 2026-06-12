---
title: "Trying to make a python module in c..."
date: 2008-06-01
forum: Programming Talk
---

### Post by days_of_ruin on 2008-06-01
I am following the directions here [http://www.python.org/doc/ext/simpleExample.html]("http://www.python.org/doc/ext/simpleExample.html")
But I get these errors.```
ex.c:1:20: error: Python.h: No such file or directory
ex.c:3: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token

```

---

### Post by Can+~ on 2008-06-01
Are you compiling with the -I flag?

gcc sample.c -I/usr/include/python2.5 -o executable_name

I suggest to make a make file.

---

### Post by days_of_ruin on 2008-06-01
Same errors.

---

### Post by geirha on 2008-06-01
Do you have [python-dev](apt://python-dev) installed?

---

### Post by Phenax on 2008-06-01
Get the "python-dev" package then try Can+~'s suggestion.

Also: Check out [SWIG]("http://www.swig.org/") too.

---

### Post by days_of_ruin on 2008-06-01
It is installed.The Python.h is in the right directory I don't know
why gcc can't find it:mad:

---

### Post by days_of_ruin on 2008-06-01
Okay I figured it out.I was using the wrong letter.I thought it was and "L"
but its actually an "I"

---

### Post by geirha on 2008-06-01
Try
```

gcc `python-config --cflags` -c prog.c
gcc `python-config --ldflags` -o prog prog.o

```

---

### Post by days_of_ruin on 2008-06-01
I dont have python-config installed, but that doesn't seem to be my problem.
I no longer get the header error, now I just get this:
```
/usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../lib/crt1.o: In function `_start':
(.text+0x18): undefined reference to `main'
/tmp/ccVJDIAu.o: In function `spam_system':
/home/isaiah/python/spammodule.c:9: undefined reference to `PyArg_ParseTuple'
/home/isaiah/python/spammodule.c:12: undefined reference to `Py_BuildValue'
collect2: ld returned 1 exit status

```
:confused::confused:

---

### Post by geirha on 2008-06-01
Add these parameters:
```
$ python-config --ldflags
-L/usr/lib/python2.5/config -lpthread -ldl -lutil -lm -lpython2.5

```

/usr/bin/python-config is installed by the python-dev package. Sure you don't have it?

---

### Post by Phenax on 2008-06-01
[http://www.python.org/doc/ext/building.html#building](http://www.python.org/doc/ext/building.html#building)

---

### Post by days_of_ruin on 2008-06-01
oops, I confused python2.5-dev with python-dev.
So I don't have it installed.Is that why I get all those compile errors?

---

### Post by geirha on 2008-06-01
> **days_of_ruin said:**
> oops, I confused python2.5-dev with python-dev.
So I don't have it installed.Is that why I get all those compile errors?

No, python2.5-dev contains the files you need. python-dev just depends on python2.5-dev and installs python-config. Though I see now, python2.5-dev installs python2.5-config which does the same thing.

---

### Post by SunTzuWarmaster on 2013-01-22
I was having this issue under the following configuration, but it is probably valid for your configuration:
Windows 7
GCC (from mingw64)
Python 2.7 (64 bit)
Eclipse IDE

I have had to take the following steps in the IDE to resolve:
1 - In eclipse, include the relevant include files.  Add "C:\Python27\include" to the C/C++ compiler includes (C++ Build, Settings, Tool Settings, GCC C++ Compiler, Includes).
2 - Add the python library to the MinGW Linker.  Add "python27" to the linked libraries (C++ Build, Settings, Tool Settings, MinGW C++ Linker, Libraries).

If this were a command-line compilation (as is likely your case), I would have added "-IC:\python27\include" and "-lpython27" to the g++ command.

---

### Post by Tony Flury on 2013-01-23
> **SunTzuWarmaster said:**
> I was having this issue under the following configuration, but it is probably valid for your configuration:
Windows 7
GCC (from mingw64)
Python 2.7 (64 bit)
Eclipse IDE

I have had to take the following steps in the IDE to resolve:
1 - In eclipse, include the relevant include files.  Add "C:\Python27\include" to the C/C++ compiler includes (C++ Build, Settings, Tool Settings, GCC C++ Compiler, Includes).
2 - Add the python library to the MinGW Linker.  Add "python27" to the linked libraries (C++ Build, Settings, Tool Settings, MinGW C++ Linker, Libraries).

If this were a command-line compilation (as is likely your case), I would have added "-IC:\python27\include" and "-lpython27" to the g++ command.


Except that if he is compiling on Ubuntu - then the path C:\python27\include wont exist - but i am sure there will be a Ubuntu equivalent - probably /usr/include/python2.7

---

