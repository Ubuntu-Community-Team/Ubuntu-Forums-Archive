---
title: "__int64 equivalent in GCC?"
date: 2008-08-14
forum: Programming Talk
---

### Post by mentallysilent on 2008-08-14
Hello, 

I'm currently working on a project where I have to port a massive API written on windoze to Linux (My 7.10 box with gcc 4.1.3). The original code was written in MSVC++ and makes heavy use of the __int64 extension. I'm just wondering how to move this to g++? I've read somewhere that init64_t is an equivalent but comes from C. Any suggestions? Thanks muchly.

---

### Post by dwhitney67 on 2008-08-14
Add this include to your project:
```
#include <inttypes.h>
```
Then use **uint64_t** or **int64_t**.

---

### Post by mentallysilent on 2008-08-14
Thanks so much. So then what is the difference between <stdint.h> and <inttypes.h>?

---

### Post by Zugzwang on 2008-08-14
> **mentallysilent said:**
> Thanks so much. So then what is the difference between <stdint.h> and <inttypes.h>?

inttypes.h includes stdint.h and just adds more macros/functions. So both should be fine.

---

### Post by mentallysilent on 2008-08-14
And this is good for use with pure C++ right?

---

### Post by dwhitney67 on 2008-08-14
Yes it is.  Many features used in C++ have been inherited from C, including many of the functions in the C library.

---

### Post by mentallysilent on 2008-08-14
Thanks guys :)

---

### Post by Jessehk on 2008-08-14
> **dwhitney67 said:**
> Yes it is.  Many features used in C++ have been inherited from C, including many of the functions in the C library.

AFAIK, that's incorrect. stdint.h is a C99 header and most C++ compilers haven't bothered implementing the C99 standard. GCC might be an exception, but I'm not sure.

I may be wrong. :)

---

### Post by dwhitney67 on 2008-08-14
On my Fedora 9 system, which uses GCC 4.3.0, it has a 'cinttypes' header file, whereas with GCC 4.2.3 it doesn't exist.

However, even when attempting to compile with 'cinttypes' on F9, the following error is produced:
```
In file included from /usr/lib/gcc/i386-redhat-linux/4.3.0/../../../../include/c++/4.3.0/cinttypes:40,
                 from test.cpp:1:
/usr/lib/gcc/i386-redhat-linux/4.3.0/../../../../include/c++/4.3.0/c++0x_warning.h:36:2: error: #error This file requires compiler and library support for the upcoming ISO C++ standard, C++0x. This support is currently experimental, and must be enabled with the -std=c++0x or -std=gnu++0x compiler options.
```

---

### Post by pansz on 2008-08-15
> **mentallysilent said:**
> And this is good for use with pure C++ right?

No, I can confirm that int64_t is not part of ISO C++98 Standard.

the int64_t is part of ISO C99 standard, which is incompatible with ISO C++98.

gcc support int64_t in C++ but that's not the standard. 
visual c++ support __int64 but that again is not the standard.
My suggestion: only use int64_t in C, use of int64_t in C++ makes your source platform dependent. (some versions of gcc does not support int64 in c++)

---

### Post by bender1234 on 2009-08-21
gah WTB more standarised c++ 

thx for the heads up though, I was struggling with the same here myself.

---

### Post by Zugzwang on 2009-08-21
Here is another solution: Use some cross-platform library such as SDL - They define their own integer types. This leaves such a problem to the developers of the library.

---

### Post by MadCow108 on 2009-08-21
they probably just do something like this:
```

#ifdef WINDOWS
typedef __int64          Long64_t;  //Portable signed long integer 8 bytes
typedef unsigned __int64 ULong64_t; //Portable unsigned long integer 8 bytes
#else
typedef long long          Long64_t; //Portable signed long integer 8 bytes
typedef unsigned long long ULong64_t;//Portable unsigned long integer 8 byte
```

no need to link a library to get 64 bit integers :)

---

### Post by Zugzwang on 2009-08-22
> **MadCow108 said:**
> they probably just do something like this:
```

#ifdef WINDOWS
typedef __int64          Long64_t;  //Portable signed long integer 8 bytes
typedef unsigned __int64 ULong64_t; //Portable unsigned long integer 8 bytes
#else
typedef long long          Long64_t; //Portable signed long integer 8 bytes
typedef unsigned long long ULong64_t;//Portable unsigned long integer 8 byte
```

no need to link a library to get 64 bit integers :)

It suffices to include the respective integer type header filed from SDL. Linking against it is also not required. Additionally, you can be sure to get support for more than just GCC in Linux and VC in Windows.

---

### Post by napsy on 2009-08-22
long long is C99;

so why not typedef long long int64_t?

---

