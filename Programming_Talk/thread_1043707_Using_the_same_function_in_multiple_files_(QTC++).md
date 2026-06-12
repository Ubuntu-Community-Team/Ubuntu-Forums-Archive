---
title: "Using the same function in multiple files (QT/C++)"
date: 2009-01-18
forum: Programming Talk
---

### Post by Zorgoth on 2009-01-18
I'm using QT with C++ and a while ago I put some functions in a header to use in a program I'm writing.  But now that I have two separate .cpp programs using it, I'm getting errors from "make" about multiple definitions of functions from said header file, one in each .o file including my header.  

The functions are defined on the same line of the same file, with the usual #ifndef #define #endif routine to protect the definitions.

It should be noted that this is the first time I've done a project involving multiple .cpp files.

Is there something special one has to do to use a header file in C++/QT for anything but a class definition?

---

### Post by Zorgoth on 2009-01-18
Incidentally, why can't I mark threads as solved anymore?  Did they move it at some point?

---

### Post by SledgeHammer_999 on 2009-01-18
Here's an example:
test1.h
[php]
//declaring prototype of "my_function" function
int my_function(int a);
[/php]

test1.cpp
[php]
#include "test1.h"

//actually implementing "my_function"
int my_function(int a)
{
  return a+1;
}

//calling "my_function"
int main()
{
  int b;
  b = my_function(4);
}
[/php]

test2.cpp
[php]
//just calling "my_function" from another function
void foo()
{
  int b;
  b = my_function(5);
}
[/php]

Hope you understand how to use the same function.
Just remember: You need to implement it just ONCE.

---

### Post by Zorgoth on 2009-01-18
Thanks!  I've got it working.  I think I understand these better now; declaring the function with the semicolon in the header file was the key.

---

### Post by snova on 2009-01-18
> **Zorgoth said:**
> Incidentally, why can't I mark threads as solved anymore?  Did they move it at some point?

Temporarily disabled. See: [http://ubuntuforums.org/showthread.php?t=1039481](http://ubuntuforums.org/showthread.php?t=1039481)

It's interesting to note how many people have been missing it as of late...

---

