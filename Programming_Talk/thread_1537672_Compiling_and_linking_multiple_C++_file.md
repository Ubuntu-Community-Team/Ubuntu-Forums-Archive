---
title: "Compiling and linking multiple C++ file"
date: 2010-07-23
forum: Programming Talk
---

### Post by adhika on 2010-07-23
Hi,

I need help on an issue with my program. 

I am writing a C++ code for GPS receiver and would like to program it using objects. 

I have separated the class header and methods into separates files (.h and .cpp files respectively) for organization and intend to use the Makefile to create objects from different classes and link them together. 

I have two classes so far with different methods in it and one main program file.

However, I am also defining a data structure that would be used throughout the three files. I intended to use "typedef struct" to do it. However, I was not able to make the file using Makefile with error message:
```

In file included from main.cpp:12:
RawMsg.h:44: error: ‘bin1msg’ does not name a type
RawMsg.h:45: error: ‘bin96msg’ does not name a type
In file included from main.cpp:13:
RxObj.h:45: error: ‘XYZ’ does not name a type
RxObj.h:50: error: ‘bin1msg’ has not been declared
RxObj.h:50: error: ‘bin96msg’ has not been declared
RxObj.h:56: error: ‘XYZ’ has not been declared
main.cpp: In function ‘int main()’:
main.cpp:37: error: ‘class RawMsg’ has no member named ‘msg1’
main.cpp:37: error: ‘class RawMsg’ has no member named ‘msg96’
main.cpp:40: error: ‘class RawMsg’ has no member named ‘msg1’
main.cpp:40: error: ‘class RawMsg’ has no member named ‘msg96’

```

I wrote all the structure definition (on typedef format) on another header file and include that on the .cpp method files (both RxObj.cpp and RawMsg.cpp).

Can you enlighten me how to do this?

Thanks.

Adhika

---

### Post by Simian Man on 2010-07-23
If you reference your structure in the header files, you need to include them there - not in the source file.  Basically things should always be declared directly or indirectly through a #include before they are used.

Also you don't need to typedef your structs if you're using a C++ compiler - that is an old C trick.

Also read [this]("http://www.gamedev.net/reference/articles/article1798.asp").

---

