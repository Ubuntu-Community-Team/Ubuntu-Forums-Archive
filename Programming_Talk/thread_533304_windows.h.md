---
title: "windows.h"
date: 2007-08-23
forum: Programming Talk
---

### Post by cessna_89702 on 2007-08-23
How would I get a windows.h file so i can do c++ programs that use it

---

### Post by nitro_n2o on 2007-08-23
windows.h is a windows specific header file and is not for linux.. i'm sure if its possible to use in linux..

---

### Post by j_g on 2007-08-24
All windows C/C++ code references Windows.h, but you don't need that for Linux. Simply comment out that #include statement. If the code then compiles with lots of error messages, then the code may be using some Windows specific APIs. In that case, you'll need to rewrite the Windows-specific code.

NOTE: Besides defining some Windows-specific APIs, Windows.h also contains lots of typedefs to define standard C datatypes to various "generic Windows datatypes". For example DWORD is typedef to be a standard C unsigned long. If those error messages concern only such datatypes, then you could perhaps coerce the code into compiling by including those typedefs in the code, for example:

#ifndef DWORD
#define WINAPI
typedef unsigned long DWORD;
typedef short WCHAR;
typedef void * HANDLE;
#define MAX_PATH	PATH_MAX
typedef unsigned char BYTE;
typedef unsigned short WORD;
typedef unsigned int BOOL;
#endif

But if you really, really, really need Windows.h, then go to Microsoft's web site and download the "Platform SDK" (Platform Software Development Kit). You'll have to install it upon some Windows system, and somewhere in your program files directory, you'll find a Microsoft folder containing a bunch of subfolders filled with .H, .LIB, and other files. Among them, you'll find Windows.h (which itself includes a whole bunch of those other .H files).

---

### Post by travisc94 on 2011-01-04
Sorry to reopen this, but windows.h is included in the Wine Development packages. This will let you compile something thats looking for windows.h

---

