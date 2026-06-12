---
title: "boost"
date: 2010-08-29
forum: Programming Talk
---

### Post by houshdaran on 2010-08-29
Hello.I have installed many boost stuff  through the software center.But I cannot use them, Nor do I know where they are installed.Help me please.I have to turn in my program before it is too late.

---

### Post by James78 on 2010-08-29
The documentation for Boost is [here]("http://www.boost.org/doc/libs/"). Using some Google searches, you could find what headers to include, and how to use the code.

As per your question though, Boost is located in, /usr/include/boost

---

### Post by dwhitney67 on 2010-08-29
That's right, the header files are /usr/include/boost.  The important thing to remember when including boost header files is preface the header file with "boost/".  For example:
```

#include <boost/thread.hpp"

```
When using a boost container (object) that is **not** templated, then you will undoubtedly require to link in the appropriate shared-object library with your application.  These are located in /usr/lib.  For building an app that requires threading, something like this is used:
```

g++ -Wall MyApp.cpp -lboost_thread-mt

```
If you wish to link in the equivalent static library, then something like this is used:
```

g++ -Wall MyApp.cpp -static -lboost_thread-mt

```

---

### Post by houshdaran on 2010-08-29
> **dwhitney67 said:**
> That's right, the header files are /usr/include/boost.  The important thing to remember when including boost header files is preface the header file with "boost/".  For example:
```

#include <boost/thread.hpp"

```When using a boost container (object) that is **not** templated, then you will undoubtedly require to link in the appropriate shared-object library with your application.  These are located in /usr/lib.  For building an app that requires threading, something like this is used:
```

g++ -Wall MyApp.cpp -lboost_thread-mt

```If you wish to link in the equivalent static library, then something like this is used:
```

g++ -Wall MyApp.cpp -static -lboost_thread-mt

```

1)What is -lboost_thread-mt

2)what is -wall?

3)what do u mean by linking the equivalent static library?

4)Isn't it true that lboost should be proceeded with boost/?

5)Why would I proceed the included file name with 'boost/'?

6)What if I copy the boost directory in my program sorce directory?

---

### Post by dwhitney67 on 2010-08-29
> **houshdaran said:**
> 1)What is -lboost_thread-mt

2)what is -wall?

3)what do u mean by linking the equivalent static library?

4)Isn't it true that lboost should be proceeded with boost/?

5)Why would I proceed the included file name with 'boost/'?

6)What if I copy the boost directory in my program sorce directory?

:-\"   Have you considered pursuing studies in a business school, perhaps chucking the entire educational thing and becoming a truck (lorry) driver?

The questions you posed above seem to indicate you don't have a clue about boost, yet it was you that first inquired about it.  I would suggest that you read the documentation, provided via this link:
[http://www.boost.org/doc/](http://www.boost.org/doc/)

---

### Post by houshdaran on 2010-08-29
> **dwhitney67 said:**
> :-\"   Have you considered pursuing studies in a business school, perhaps chucking the entire educational thing and becoming a truck (lorry) driver?

The questions you posed above seem to indicate you don't have a clue about boost, yet it was you that first inquired about it.  I would suggest that you read the documentation, provided via this link:
[http://www.boost.org/doc/](http://www.boost.org/doc/)
Due to my illness, I cannot drive.Unfortunately, I have little time

---

### Post by James78 on 2010-08-29
> **houshdaran said:**
> 1)What is -lboost_thread-mt

2)what is -wall?

3)what do u mean by linking the equivalent static library?

4)Isn't it true that lboost should be proceeded with boost/?

5)Why would I proceed the included file name with 'boost/'?

6)What if I copy the boost directory in my program sorce directory?
1) [Here]("http://www.boost.org/doc/libs/1_44_0/doc/html/thread.html").

2) The -Wall option specifies that you want all warning messages to be reported to you. ("W" <- as in warning -> "all")

3) You really need to read about [libraries]("http://en.wikipedia.org/wiki/Library_%28computing%29"), [static libraries]("http://en.wikipedia.org/wiki/Static_library"), and [dynamic (shared) libraries]("http://en.wikipedia.org/wiki/Shared_library#Shared_libraries").

4) No, -lboost specifies to the compiler that you want to link with the library "libboost.so", or in this case -lboost_thread-mt and "libboost_thread-mt.so".

5) Because it's under /usr/include/boost. If it was under /usr/include/foobar, you would precede it with "#include <foobar/foo.hpp>" just as much so.

6) That's completely unneeded, as boost is already in your system. Just #include <boost/foobar.hpp> as you would normally. If you copy it over, you'll likely have to change some compilation flags, like -I/includeDir/, -L/libpath/, plus it'd be wasting your time anyways.

I suggest you read up on C++, and programming, as this answers these types of questions, and for any other questions you have, do a Google search first.. The answers are fairly simple to find and are abundant out there if you take the time to look for them.

---

### Post by houshdaran on 2010-08-29
but I want to be able to carry it to my school, showing it to my teacher

---

### Post by houshdaran on 2010-08-29
> **James78 said:**
> 1) [Here]("http://www.boost.org/doc/libs/1_44_0/doc/html/thread.html").

2) The -Wall option specifies that you want all warning messages to be reported to you. ("W" <- as in warning -> "all")

3) You really need to read about [libraries]("http://en.wikipedia.org/wiki/Library_%28computing%29"), [static libraries]("http://en.wikipedia.org/wiki/Static_library"), and [dynamic (shared) libraries]("http://en.wikipedia.org/wiki/Shared_library#Shared_libraries").

4) No, -lboost specifies to the compiler that you want to link with the library "libboost.so", or in this case -lboost_thread-mt and "libboost_thread-mt.so".

5) Because it's under /usr/include/boost. If it was under /usr/include/foobar, you would precede it with "#include <foobar/foo.hpp>" just as much so.

6) That's completely unneeded, as boost is already in your system. Just #include <boost/foobar.hpp> as you would normally. If you copy it over, you'll likely have to change some compilation flags, like -L/includeDir/, plus it'd be wasting your time anyways.

I suggest you read up on C++, and programming, as this answers these types of questions, and for any other questions you have, do a Google search first.. The answers are fairly simple to find and are abundant out there if you take the time to look for them.

there is a problem
I looked at the documentation(your given URL), but I tried to execute the first example(demo.cpp) for serialization and it failed!I simply copy-pasted the example in a file and g++'ed it.
but there where  no .o file generated:I typed:
```
g++ test_serialization.cpp
```

---

### Post by James78 on 2010-08-29
> **houshdaran said:**
> but I want to be able to carry it to my school, showing it to my teacher

In that case, try these steps, although I make no guarantees it'll work, so do some testing before you approve it.

Copy over the boost include directory to your source directory, copy over any libraries you have to link too to your source directory, then cd to the source directory, and do something like this (use the absolute path just to be safe).

In this example:
[LIST]
[*]Your source code is in ~/Projects/myprojects/src
[*]The libraries you have to link with were copied over to ~/Projects/myprojects/src
[*]Boost is located under ~/Projects/myprojects/src/boost
[*]Your C/C++ include statements are like: #include "boost/foobar.hpp"
[/LIST]

If you have to link libraries with your program:
```
g++ -Wall -L/home/user/projects/myprojects/src -I/home/user/projects/myprojects/src/boost -lfoo -lbar *.cpp *.hpp -o executable
```

If you don't have to link any libraries:
```
g++ -Wall *.cpp *.hpp -o executable
```

> **houshdaran said:**
> there is a problem
I looked at the documentation(your given URL), but I tried to execute the first example for serialization and it failed!I simply copy-pasted the example in a file and g++'ed it.
but there where  no .o file generated:I typed:
```
g++ test_serialization.cpp
```
Boost serialization needs to be linked with the boost serialization library.
```
g++ -lboost_serialization test_serialization.cpp -o serialization
```

---

### Post by houshdaran on 2010-08-29
thx.worked.What would be the output file name?

---

### Post by James78 on 2010-08-29
"-o serialization" specified the output filename. So look for a binary named "serialization" in the same directory you compiled it in. If you don't specify -o, then the binary will be named "a.out"

---

### Post by houshdaran on 2010-08-29
This is What I typed at the cdommand line and the result is at the end:
> soheil@soheil-PC:/media/g_$ g++ -lboost_serialization test_serialization.cpp 
soheil@soheil-PC:/media/g_$ test_serialization.out
test_serialization.out: command not found
did I have any mistakes?So why it was not executed?

---

### Post by James78 on 2010-08-29
> **James78 said:**
> "-o serialization" specified the output filename. So look for a binary named "serialization" in the same directory you compiled it in. **If you don't specify -o, then the binary will be named "a.out"**

> **houshdaran said:**
> This is What I typed at the cdommand line and the result is at the end:
did I have any mistakes?So why it was not executed?
Your file is named "a.out" because you didn't specify -o, unless you changed the name. To execute a binary located in the current directory, you need to prepend "./" to the name.
```
./a.out
```
And to execute a binary not in the system PATH, use the absolute path to the binary.
```
/media/g_/a.out
```

---

### Post by houshdaran on 2010-08-30
The boost documentatioon states that if one wants to for example save gps objects members of a serializable class, they need to implement Serialize method in gps class.
 
if a class has, say, string type data members( I mean one that has no serialized method)
can they be serialized?t

Thanx for taking your precious time

---

