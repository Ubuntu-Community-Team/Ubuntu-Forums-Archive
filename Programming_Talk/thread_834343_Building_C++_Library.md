---
title: "Building C++ Library"
date: 2008-06-19
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-06-19
I have recently made the switch from interpreted languages (Python, Java) to C++ (Great yet annoying). And in doing this I rewrote some of my personal favorite classes. Now I want to make a library out of them.

I Googled and got little to nothing, and what i got didn't work. All i want is to make a static library (personal use) out of these classes, also i must be able to use them.

Also i have these classes in .h files. And i am willing to change formats and whatever.

If you think i need to use Dynamic or shared libraries then teach me Static first

Remember this is C++ not C (as most tutorials gave me) so respond respectively.

Thanks

---

### Post by LaRoza on 2008-06-19
> **Mr.Macdonald said:**
> I have recently made the switch from interpreted languages (Python, Java) to C++ (Great yet annoying). And in doing this I rewrote some of my personal favorite classes. Now I want to make a library out of them.

I Googled and got little to nothing, and what i got didn't work. All i want is to make a static library (personal use) out of these classes, also i must be able to use them.

Also i have these classes in .h files. And i am willing to change formats and whatever.


[http://crasseux.com/books/ctutorial/Building-a-library.html](http://crasseux.com/books/ctutorial/Building-a-library.html) (Works same way)

However, you are (it seems) misusing .h files (.hpp for C++ ;))

---

### Post by Mr.Macdonald on 2008-06-19
can i put my classes into .cc and "g++ -c test.cc" to make a .o
if i then put the test.o into a library could i access the classes

also does anyone have an example using g++ instead of gcc (i never got gcc to compile c++).

and finally, is .hpp more commonly used (theres a word for it) than .h regarding c++, ill use it if so but i prefer .h (im OCD like that)

---

### Post by LaRoza on 2008-06-19
> **Mr.Macdonald said:**
> can i put my classes into .cc and "g++ -c test.cc" to make a .o
if i then put the test.o into a library could i access the classes

also does anyone have an example using g++ instead of gcc (i never got gcc to compile c++).

and finally, is .hpp more commonly used (theres a word for it) than .h regarding c++, ill use it if so but i prefer .h (im OCD like that)

g++ works the same way in that respect. 

From the man page of gcc:

```

 For any given input file, the file name suffix determines what kind of
       compilation is done:

       file.c
           C source code which must be preprocessed.

       file.i
           C source code which should not be preprocessed.

       file.ii
           C++ source code which should not be preprocessed.

       file.m
           Objective-C source code.  Note that you must link with the libobjc
           library to make an Objective-C program work.

       file.mi
           Objective-C source code which should not be preprocessed.

       file.mm
       file.M
           Objective-C++ source code.  Note that you must link with the
           libobjc library to make an Objective-C++ program work.  Note that
           .M refers to a literal capital M.

       file.mii
            Objective-C++ source code which should not be preprocessed.

       file.h
           C, C++, Objective-C or Objective-C++ header file to be turned into
           a precompiled header.

       file.cc
       file.cp
       file.cxx
       file.cpp
       file.CPP
       file.c++
       file.C
           C++ source code which must be preprocessed.  Note that in .cxx, the
           last two letters must both be literally x.  Likewise, .C refers to
 a literal capital C.

       file.mm
       file.M
           Objective-C++ source code which must be preprocessed.

       file.mii
           Objective-C++ source code which should not be preprocessed.

       file.hh
       file.H
           C++ header file to be turned into a precompiled header.

       file.f
       file.for
       file.FOR
           Fixed form Fortran source code which should not be preprocessed.

       file.F
       file.fpp
       file.FPP
         Fixed form Fortran source code which must be preprocessed (with the
           traditional preprocessor).

       file.f90
       file.f95
           Free form Fortran source code which should not be preprocessed.

       file.F90
       file.F95
           Free form Fortran source code which must be preprocessed (with the
           traditional preprocessor).

       file.ads
           Ada source code file which contains a library unit declaration (a
           declaration of a package, subprogram, or generic, or a generic
           instantiation), or a library unit renaming declaration (a package,
           generic, or subprogram renaming declaration).  Such files are also
           called specs.

       file.adb
           Ada source code file containing a library unit body (a subprogram
          or package body).  Such files are also called bodies.

       file.s
           Assembler code.

       file.S
           Assembler code which must be preprocessed.

       other
 An object file to be fed straight into linking.  Any file name with
           no recognized suffix is treated this way.

       You can specify the input language explicitly with the -x option:

       -x language
 Specify explicitly the language for the following input files
           (rather than letting the compiler choose a default based on the
           file name suffix).  This option applies to all following input
           files until the next -x option.  Possible values for language are:

                   c  c-header  c-cpp-output
                   c++  c++-header  c++-cpp-output
                   objective-c  objective-c-header  objective-c-cpp-output
                   objective-c++ objective-c++-header objective-c++-cpp-output
                   assembler  assembler-with-cpp
                   ada
                   f95  f95-cpp-input
                   java
                   treelang

       -x none
           Turn off any specification of a language, so that subsequent files
           are handled according to their file name suffixes (as they are if
           -x has not been used at all).

```

---

### Post by nvteighen on 2008-06-19
Thread-hijacking, but related to this.

Is the "extern" keyword actually necessary in the header files?? Isn't that used for calling global variables from other **source file**, so why are we supposed to use it to grab functions from **machine code**?

---

### Post by Mr.Macdonald on 2008-06-19
When i want to include the library do I do
```
#include <libname>
```
not
```
#include "name_of_.h_in_lib"
```

---

### Post by LaRoza on 2008-06-19
> **Mr.Macdonald said:**
> When i want to include the library do I do
```
#include <libname>
```
not
```
#include "name_of_.h_in_lib"
```

I am unsure from your posts, but it seems like you have the code in headers. Headers don't contain the implementations of what they contain. They only contain prototypes, definitions and preprocessor macros.

#including something (for the standard headers) hides the linking because gcc (and g++) do it automatically.

What you want to do is make a library, make a header for it, and include the header and link to the library. 

```

/*testing.c*/
#include "library.h"

int main(void)
{
    library();
}

```
```

/*library.c*/
#include "library.h"
#include "stdio.h"
void library(void)
{
    puts("I am a library");
}

```

```

/*library.h*/
#ifndef LIBRARY_H
#define LIBRARY_H
void library(void);
#endif

```

```

~$touch testing.c library.h library.c
~$gcc -c library.c
~$ar rs liblibrary.a library.o
~$gcc -c testing.c
$gcc --static -o testing testing.o -L./ -llibrary
~$./testing
I am a library

```

The link I gave has a guide to answer your questions, especially the include path and what all those things I did mean.

---

### Post by Mr.Macdonald on 2008-06-19
**I want a c++ example using g++. I have heard that's it is the same, but in my practice that hasn't proved true.**

So ...

could someone provide an example with a library that holds a class (testlib.a) and a source file (test.cc) and compile it into an executable (test) that uses that class. please use g++ and have a generic example and NO C because the whole internet can tell me how to do that.


G++ and C++ not GCC and C

---

### Post by LaRoza on 2008-06-19
> **Mr.Macdonald said:**
> **I want a c++ example using g++. I have heard that's it is the same, but in my practice that hasn't proved true.**

(testlib.a) 

G++ and C++ not GCC and C

All the guides I got from google say it is the same.

"testlib.a" won't work, libraries have to start with "lib". Look at my example more closely.

---

### Post by nvteighen on 2008-06-19
g++ is gcc, so don't worry.

It will work because the linking part is done by ld (see "man ld") for any executable binary code produced. AFAIK, it's a language independent process and gcc/g++ calls ld as last compiling step.

---

### Post by LaRoza on 2008-06-19
> **nvteighen said:**
> g++ is gcc, so don't worry.

It will work because the linking part is done by ld (see "man ld") for any executable binary code produced. AFAIK, it's a language independent process and gcc/g++ calls ld as last compiling step.

It does (although you can stop it from doing it, and do it manually).

---

### Post by nvteighen on 2008-06-19
> **LaRoza said:**
> It does (although you can stop it from doing it, and do it manually).
That's the freedom this OS gives us :)

---

### Post by LaRoza on 2008-06-19
> **nvteighen said:**
> That's the freedom this OS gives us :)

But don't you think pressing the little triangle/square/x/watermelon button on $IDE is easier?
</visual studio fan jab>

---

### Post by WW on 2008-06-19
OK, here's an example:

**myclass.h**
```

//
//  myclass.h
//

class myclass
    {
    private:

    int order;
    double ratio;

    public:

    // Constructor
    myclass();

    // Getters and setters
    void set_order(int k);
    int get_order(void);
    void set_ratio(double r);
    double get_ratio();
    };

```

**myclass.cpp**
```

#include "myclass.h"

myclass::myclass()
    {
    order = 0;
    ratio = 0.0;
    }

void myclass::set_order(int k)
    {
    order = k;
    }

int myclass::get_order()
    {
    return order;
    }

void myclass::set_ratio(double r)
    {
    ratio = r;
    }

double myclass::get_ratio()
    {
    return ratio;
    }

```

Note that myclass.h only contains the declaration of the class and its methods. The actual code is in myclass.cpp.  To create a library that can be statically linked:
```

$ g++ -c myclass.cpp             # Compile myclass.cpp, create myclass.o
$ ar rs libmyclass.a myclass.o   # Create libmyclass.a

```
Now the two files that you will make available for use in other programs are myclass.h and libmyclass.a.  A traditional place to put these files is in /usr/local/include and /usr/local/lib, respectively.  E.g.
```

$ sudo cp myclass.h /usr/local/include
$ sudo cp libmyclass.a /usr/local/lib

```
(If either /usr/local/include or /usr/local/lib don't already exist, you'll have to create them before copying the files.)

Here is a program that uses this library.

**myclass_test.cpp**
```

#include <iostream>

#include <myclass.h>

using namespace std;

int main(int argc, char *argv)
    {
    myclass m;

    m.set_order(100);
    cout << "order = " << m.get_order() << "  ratio = " << m.get_ratio() << endl; 
    return 0;
    }

```
And here is how to compile and run this program:
```

$ g++ -c -I/usr/local/include myclass_test.cpp  
$ g++ myclass_test.o -L/usr/local/lib -lmyclass -o myclass_test 
$ ./myclass_test 
order = 100  ratio = 0
$

```
Also take a look at the comments I made in post #10 of [this thread](http://ubuntuforums.org/showthread.php?t=745218).

---

### Post by Sinkingships7 on 2008-06-19
> **LaRoza said:**
> But don't you think pressing the little triangle/square/x/watermelon button on $IDE is easier?
</visual studio fan jab>

:lolflag:

---

### Post by LaRoza on 2008-06-19
> **Sinkingships7 said:**
> ...

I actually don't know what the symbol is, but someone in defense of VS said compiling is easy just press the $SYMBOL which I thought was silly (and responded with a "Oh, its psychic and knows what I want to do?")

---

### Post by nvteighen on 2008-06-20
> **LaRoza said:**
> But don't you think pressing the little triangle/square/x/watermelon button on $IDE is easier?
</visual studio fan jab>

> **LaRoza said:**
> I actually don't know what the symbol is, but someone in defense of VS said compiling is easy just press the $SYMBOL which I thought was silly (and responded with a "Oh, its psychic and knows what I want to do?")

<rant>Oh, yeah much easier: after you have searched where the compiled preferences are, set everything manually (as usually defaults are useless); and if and only if the button has been placed in the toolbar, otherwise (e.g. you're compiling in someone else's computer or VS has screwed up your configuration, like sometimes MS applications do occasionally) you'll have to either search in the menus or press the so-intuitive F5 key (Ctrl+F5 if you want to run the application not through debugger)... which only makes sense if you come from QBASIC (F5 = run).</rant>

---

### Post by dwhitney67 on 2008-06-20
A couple of posts insinuated that header files should not contain the implementation for defined functions/methods, but instead only the declarations.

Well this would be ideal, however in the case of C++ templates, I don't think there is a way around this.  Sure there are "tricks" that one can do, but in the end it is the header file that contains the implementation of the code... not the library (that is, not the .a or .so).

Here's a trivial implementation of a template, where the declaration and the implementation appear to be separate, but from a preprocessor/compiler perspective, they are not.

MyTemplate.hpp:
[PHP]#ifndef MYTEMPLATE_HPP
#define MYTEMPLATE_HPP

template< class T >
class MyTemplate
{
  public:
    MyTemplate( const T &obj );

    //...

    const T& getObject() const;

  private:
    T m_obj;
};


// Include implementation for MyTemplate
//
#include "MyTemplateImpl.cpp"

#endif[/PHP]

MyTemplateImpl.cpp:
[PHP]template< class T >
MyTemplate<T>::MyTemplate( const T &obj )
  : m_obj( obj )
{
}

//...

template< class T >
const T& MyTemplate<T>::getObject() const
{
  return m_obj;
}[/PHP]

Main.cpp:
[PHP]#include "MyTemplate.hpp"
#include <string>
#include <iostream>

int main()
{
  std::string str( "This is my string" );
  MyTemplate< std::string > myT( str );
  std::cout << "str = " << myT.getObject() << std::endl;
  return 0;
}[/PHP]

It is almost certain that not everyone likes to separate a template definition from its implementation the way I have shown.  In such case, then it is acceptable to embed the implementation right into the class definition.

Another strong argument for embedding implementation code in a header file has to do with "inlining" accessor (get/set) methods.  By implementing trivial accessor functions within the class definition, the execution time of a program can be increased by obviating the need to jump to a trivial function.

----------------------------------

Mr.MacDonald -

As far as creating a C++ (or C) library, just use the archive (/usr/bin/ar) command to collect your individual object files into a lib<name>.a file, where the <name> is something you choose to identify your library.

So (perhaps in a Makefile!), something like the following would suffice:
```

SRCS     = src1.cpp src2.cpp srcN.cpp
OBJS     = $(SRCS:.cpp=.o)
CXXFLAGS = -Wall -pedantic
LIB      = libCollection.a

$(LIB) : $(OBJS)
        $(AR) r $(LIB) $(OBJS)

.cpp.o:
        $(CXX) $(CXXFLAGS) -c $< -o $@
```
To use the newly created library, something like:
```
g++ -Wall -pedantic -I./ MyProgram.cpp -L./ -lCollection
```
Note the 'lib' and the '.a' are not required when specifying the library name.

The -I option is used to specify the location of the project's header file(s); if the library's header file(s) are located elsewhere, then a separate -I can be used to specify that location.

The -L option is used to specify where the libCollection.a is located.  In the example above, the libCollection.a is in the current working directory.

---

