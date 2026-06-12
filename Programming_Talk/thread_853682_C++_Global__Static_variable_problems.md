---
title: "C++ Global / Static variable problems"
date: 2008-07-08
forum: Programming Talk
---

### Post by SNYP40A1 on 2008-07-08
I have a C++ project that compiles fine.  However, as soon as I include a global variable or a static variable in one of the classes, it compiles, but I get a ton of linking errors.  Even if I include a global like 

int two = 2;

I get tons of linking errors with the description of multiple definition of two.  So I am thinking that the problem has something to do with how I am including files.  Does it make a difference whether an include is in the header file or .cc file?  Any ideas on how to fix this?  There's too much code to post.  This is the worst part of C++, I never had these problems in Java.

---

### Post by LaRoza on 2008-07-08
> **SNYP40A1 said:**
> I have a C++ project that compiles fine.  However, as soon as I include a global variable or a static variable in one of the classes, it compiles, but I get a ton of linking errors.  Even if I include a global like 

int two = 2;

I get tons of linking errors with the description of multiple definition of two.  So I am thinking that the problem has something to do with how I am including files.  Does it make a difference whether an include is in the header file or .cc file?  Any ideas on how to fix this?  There's too much code to post.  This is the worst part of C++, I never had these problems in Java.

First, ask yourself if you need global variables. Then, look into the keyboard "extern".

You shouldn't be including code, which is what it sounds like. Compile the files separately.

---

### Post by SNYP40A1 on 2008-07-08
> **LaRoza said:**
> First, ask yourself if you need global variables. Then, look into the keyboard "extern".

You shouldn't be including code, which is what it sounds like. Compile the files separately.

Well, it's a bunch of classes and the classes all depend on each other.  Compiling goes fine.  It's linking where I hit the problems.

---

### Post by WW on 2008-07-08
Without seeing a bit of the code, we can only guess.  Here goes...

> **SNYP40A1 said:**
> 
int two = 2;

This must only occur once.  It should not be in a header file.

---

### Post by SNYP40A1 on 2008-07-08
> **WW said:**
> Without seeing a bit of the code, we can only guess.  Here goes...


This must only occur once.  It should not be in a header file.

I put it in a header file.  How does putting it in the *.cc file and not the header file guarantee that it only gets included once?  In my *.cpp files, I include other header files.  It's one big cyclic mess.

---

### Post by LaRoza on 2008-07-08
> **SNYP40A1 said:**
> I put it in a header file.  How does putting it in the *.cc file and not the header file guarantee that it only gets included once?  In my *.cpp files, I include other header files.  It's one big cyclic mess.

Headers are not supposed to be used that way. C++ is not Java (it isn't C either).

Look up inclusion guards (for headers) and extern for globals.

---

### Post by dwhitney67 on 2008-07-08
> **SNYP40A1 said:**
> ...
This is the worst part of C++, I never had these problems in Java.
That is because in Java you _cannot_ define a global variable.  Why are you trying to do something silly like this in C++?  There is no need for a global variable if you have a proper design.

If you feel you must pursue a path of writing bad code, then define your global variable in the main module, and everywhere else with the 'extern' prefix.

Better yet, define the variable in a header file, and ensure that at least one module instantiates the variable; all other modules should refer to it as an 'extern'.  Here's how:

Header.h
[PHP]#ifndef HEADER_H
#define HEADER_H

#ifdef MAIN
#define EXTERN
#else
#define EXTERN extern
#endif

EXTERN int myGlobalVariable;

#endif[/PHP]
Main.cpp:
[PHP]#define MAIN
#include "Header.h"
...[/PHP]
Other.cpp:
[PHP]#include "Header.h"
...[/PHP]
Now, if it is static variables within a class that are causing you grief, then presuming you have a class similar to the following:

MyClass.h:
[PHP]#ifndef MYCLASS_H
#define MYCLASS_H

class MyClass
{
  ...

  static int myStaticVariable;
};

#endif[/PHP]

then you will need to initialize the static variable in at least one module (typically the Main module, but does not need to be):

Main.cpp:
[PHP]#include "MyClass.h"
...
int MyClass::myStaticVariable = 0;

int main()
{
  ...
}[/PHP]

Let me know if you still have any problems understanding any of the concepts described above.

---

