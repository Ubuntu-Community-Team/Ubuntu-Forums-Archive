---
title: "problem compiling c++ program"
date: 2011-05-13
forum: Programming Talk
---

### Post by coolcav on 2011-05-13
I am working or remote server and programming in C++. The code was in C and was later modified to support C++. The code gets compiled well in the remote server without any error and warnings. But when I copy the same code in my laptop (from git repository) and compile it, it shows lots of errors and warnings. I am u sing g++ compiler in both machines..but the version is different... Information about the version is given below:

[me@remote_server ~]$ g++ --version
g++ (GCC) 4.1.2 20071124 (Red Hat 4.1.2-42)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

me@my_machine:~$ g++ --version
g++ (Ubuntu/Linaro 4.5.2-8ubuntu4) 4.5.2
Copyright (C) 2010 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

The error and warnings that I get in my machine are: 

filex.c:107:42: error: ‘memset’ was not declared in this scope
filex.c:108:69: error: ‘strncpy’ was not declared in this scope
filex.c:117:30: error: ‘memset’ was not declared in this scope
filex.c:118:53: error: ‘strncpy’ was not declared in this scope

utilities.c:561:22: warning: deprecated conversion from string constant to ‘char*’
utilities.c:562:22: warning: deprecated conversion from string constant to ‘char*’
utilities.c:563:22: warning: deprecated conversion from string constant to ‘char*’

I don't understand why I get these errors in my machine but not in remote machine with g++ compiler? My laptop has Ubuntu 11.04 Is it due to the version of g++?

Looking for your help.

---

### Post by noah++ on 2011-05-14
Looks like your compiler needs you to add an *#import* statement or two.

---

### Post by SledgeHammer_999 on 2011-05-14
In filex.c put ```
#include <cstring>
```

Also, shouldn't you change the file extension to .cpp so others don't get confused?

---

### Post by coolcav on 2011-05-14
> **SledgeHammer_999 said:**
> In filex.c put ```
#include <cstring>
```Also, shouldn't you change the file extension to .cpp so others don't get confused?

Well, i kept #include <string.h> header file in filex.c and some errors reduced. But I still have many warnings - "warning: deprecated conversion from string constant to ‘ char*’ " . I thiink it has something to do with compiler. I removed gcc 4.4.5 and installed 4.1.2 . Earlier to compile i had to use g++ only, now i have to use g++4.1 command. But this compiler does not give errors and warnings.How to make it compile with g++ command only?
 But now i am having other problems with this... I am using mpi and earlier with 4.4.5, mpic++ worked, now it is not working. Would removing openmpi and reinstalling it work?
Suggestions please.

---

### Post by dwhitney67 on 2011-05-14
> **coolcav said:**
> 
The error and warnings that I get in my machine are: 

filex.c:107:42: error: &#8216;memset&#8217; was not declared in this scope
filex.c:108:69: error: &#8216;strncpy&#8217; was not declared in this scope
filex.c:117:30: error: &#8216;memset&#8217; was not declared in this scope
filex.c:118:53: error: &#8216;strncpy&#8217; was not declared in this scope

utilities.c:561:22: warning: deprecated conversion from string constant to &#8216;char*&#8217;
utilities.c:562:22: warning: deprecated conversion from string constant to &#8216;char*&#8217;
utilities.c:563:22: warning: deprecated conversion from string constant to &#8216;char*&#8217;


If you are developing a C++ program, then use .cpp, .cxx, or .C as your file extension.  Also use "g++" as the compiler.

If you are developing a C program, then use .c as the file extension, and use "gcc" as the compiler.

As for the errors, for C++, include <cstring> to resolve the errors.  If you are programming in C, then include <string.h>.

For the warnings, declare the offending strings as const char*.  For example:
```

char* str = "Some String";         // BAD

const char* str = "Some String";   // GOOD

```

---

### Post by coolcav on 2011-05-17
Thanks guys.

---

### Post by SevenMachines on 2011-05-17
theres a few of these in porting old code to >= gcc 4.3, you might want to quickly look over 
[http://gcc.gnu.org/gcc-4.3/porting_to.html](http://gcc.gnu.org/gcc-4.3/porting_to.html)

---

### Post by cgroza on 2011-05-17
> **dwhitney67 said:**
> If you are developing a C++ program, then use .cpp, .cxx, or .C as your file extension.  Also use "g++" as the compiler.

If you are developing a C program, then use .c as the file extension, and use "gcc" as the compiler.

As for the errors, for C++, include <cstring> to resolve the errors.  If you are programming in C, then include <string.h>.

For the warnings, declare the offending strings as const char*.  For example:
```

char* str = "Some String";         // BAD

const char* str = "Some String";   // GOOD

```
I also saw .cc as a file extension.

---

