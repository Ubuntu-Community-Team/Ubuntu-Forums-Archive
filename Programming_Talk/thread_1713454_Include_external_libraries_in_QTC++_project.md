---
title: "Include external libraries in QT/C++ project"
date: 2011-03-24
forum: Programming Talk
---

### Post by Action_Radar on 2011-03-24
Hi!

Maybe someone can help me with this. 
I want to use the Platinum UPnP SDK for my QT4 project. The SDK has several .a lib files. I already read that including libraries is done via the .pro file like so:

```

INCLUDEPATH - is the location of directory with header files
LIBPATH - is the location of directory with *.a files 
LIBS - contains list of libraries you want to use in your application

```I set all these variables to the according paths/libs. 

But when I include "Platinum.h" for instance I get an error from within the Platinum.h.
According to the error message the includes within Platinum.h are not found.

Did anyone try to use Platinum SDK or has anyone any idea what I'm doing wrong?

---

### Post by Action_Radar on 2011-03-24
I just wanted to make my solution to this problem public.

Platinum has all it's .h files in the Source folder. But there are  several subfolders which apparently have to be included separately. 

All the .a library files have to be included like this (for instance for libFoo.a) :

```
LIBS += -lFoo -Lpath/to/libfolder
```Problem solved.

---

