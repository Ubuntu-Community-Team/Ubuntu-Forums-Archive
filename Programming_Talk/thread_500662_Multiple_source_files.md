---
title: "Multiple source files"
date: 2007-07-14
forum: Programming Talk
---

### Post by MiCovran on 2007-07-14
Where could I learn about breaking up a program into multiple source and header files with C++? I'm really getting interested in this object oriented programming concept.

Thanks.

---

### Post by lisati on 2007-07-14
I suggest that you might want to divide into separate files according to function. Another possibility is that if you might want to port (translate) the application to another OS at some stage, then keep the OS-dependent modules in a file of their own.

As I understand it, the header files are often used for definitions that are common to different module - it can help save typing!

---

### Post by MiCovran on 2007-07-14
Maybe I wasn't clear: I would like to learn how to do it first, not how to organize files. I want to learn what header file should contain, what different source files should contain, how to compile such programs...

---

### Post by runningwithscissors on 2007-07-14
Simple C++ header : app.hh

```

#ifndef __APP_HH__
#define __APP_HH__
#include <iostream>

class app {
public:
        app(std::string);
};
#endif

```

Source file : app.cc

```

#include "app.hh"

app::app(std::string msg)
{
        std::cout << msg << std::endl;
}

```

Main source file: test.cc
```

#include "app.hh"

int main(int argc, char** argv)
{
        app("Hello World");
        return 0;
}

```

Compile and execute with:
```
$ g++ app.cc test.cc -I./
$ ./a.out
```

---

### Post by MiCovran on 2007-07-14
And that's it? Wow. Thanks. I didn't think it would be so simple. There are just four things I would like to clarify:
[LIST=1]
[*]How can you use strings if you didn't use #include <string>?
[*]Does it matter in which order I list sources when compiling?
[*]What do I need this #ifndef block for? Compiling works without it, too.
[*]Can I use "using namespace std" in app.cc or app.hh?
[/LIST]
Oh, and one more thing: is there a way to share variables between parts of code in different files or is every new file like a small program with it's own variables?

---

### Post by slavik on 2007-07-14
> **MiCovran said:**
> And that's it? Wow. Thanks. I didn't think it would be so simple. There are just four things I would like to clarify:
[LIST=1]
[*]How can you use strings if you didn't use #include <string>?
[*]Does it matter in which order I list sources when compiling?
[*]What do I need this #ifndef block for? Compiling works without it, too.
[*]Can I use "using namespace std" in app.cc or app.hh?
[/LIST]
Oh, and one more thing: is there a way to share variables between parts of code in different files or is every new file like a small program with it's own variables?

1. string.h only exists in C I believe, in C++, they are in the language by default (I am not too sure on this)
2. no
3. because if you don't have it and you include the file more than once in a single file, you will get repeat definitions. try doing #include of the same file without the ifndef block and it will blow up. :P
4. yes, but highly unrecommended. using namespace std; should only be used when you 100% know there is no other namespace (boost library has its own namespace), hence in a library, you cannot guarantee that someone using it is using namespace std and it will produce errors and mess up the code somewhat.

*: variables are "shared" if they are global. but you need a good reason to have global variables. :)
eventually all the source code gets combined into a single file. :)

---

### Post by Mr. C. on 2007-07-14
MiCovran,

Re: (3), there is a difference between the **definition** of a variable, and **declaring** a variable. A variables definition defines its type and storage.  A declaration simple tells the compiler or other tools *about* the variable, but does not define storage.

It used to be the case that the C compiler would tolerate multiple definitions of a variable, and would resolve the multiple definitions into one.   Thus, programmers would include files such as:

```
# include.h

int c;
extern int c;

```
in multiple C files, so that they did not have to worry about which file contained the "int c" and which contained the declaration "extern int c".

Today, this is not valid; there must be one and only one definition of a variable, and each compilation unit (eg. source file) that references that variable must have a declaration.  In other words, the variable goes in one place, and all other places say "that thing in some other file declared as such".

Using the #ifdefs is a way to prevent multiple copies (ensure idempotency) of the included files.

MrC

---

### Post by aks44 on 2007-07-14
> **slavik said:**
> 1. string.h only exists in C I believe, in C++, they are in the language by default (I am not too sure on this)

Strings are definitely not part of the language itself, rather of the Standard Library (so they need to be included at some point).

In C++ the relevant header is <string>, however in this very case it wasn't needed to include it because <iostream> already includes it.

---

### Post by MiCovran on 2007-07-15
> **slavik said:**
> using namespace std; should only be used when you 100% know there is no other namespace (boost library has its own namespace), hence in a library, you cannot guarantee that someone using it is using namespace std and it will produce errors and mess up the code somewhat.
As I understand this, I can't use it in header files (which get #include-d). But ".cc" files don't get included, can I use "using namespace std;" there?

> **Mr. C. said:**
> Today, this is not valid; there must be one and only one definition of a variable, and each compilation unit (eg. source file) that references that variable must have a declaration. In other words, the variable goes in one place, and all other places say "that thing in some other file declared as such".
So I put "extern int c" in only one file and "int c" in all files that use it or...?

---

### Post by Wim Sturkenboom on 2007-07-15
> 
So I put "extern int c" in only one file and "int c" in all files that use it or...?

Other way around :)

---

### Post by Mr. C. on 2007-07-15
> **MiCovran said:**
> As I understand this, ...

So I put "extern int c" in only one file and "int c" in all files that use it or...?

As mentioned by the previous poster, you have it backwards.

Think from the compiler's point of view...

The compiler reads the source file, and finds a "int c;" definition.  It then:

[LIST]
[*]Knows the type (int)
[*]Allocates space (eg. 4 bytes)
[*]Sets its storage location to the data segment (or bss, depending upon initialization)
[*]Places the sybol "c" in the symbol table
[/LIST]

Now, when the C compile comes around to another source file, it has no knowledge of the previous compile session (which just made a .o file).  So you must help the compiler understand what "c" is in this second source code file.  All it needs to know is the type, so that it can know how much space the variable uses and perform compile-time type-checking.  The "extern int c" statement does exactly that.  It doesn't allocate space, nor does it try to resolve the variable's definition at this time - it leaves that to the linker.

The linker then visits each .o file, and relocates code and variables as necessary and resolves all "extern" declarations to their definitions.

Given this description, you should also be able to see that the of compilation does not matter, and final resolution occurs at link time.

MrC

---

### Post by grado on 2007-07-15
MiCovran might also want learn about [make]("http://www.eng.hawaii.edu/Tutor/Make/") files.
That the right way to deal with multiple files. Of course, there is ant, jam and other make-like tools but the idea is similar. Besides, most C/C++ projects use make!

---

### Post by MiCovran on 2007-07-16
Thank you a lot. Now I understand a lot more than I did two days ago. I really liked this Mr. C.'s explanation of compiler and linker and the tutorial grado posted.

Could someone, please, just post at least a short yes/no answer to this "using namespace std;" question? I just don't like writing "std::" all the time. :popcorn:> As I understand this, I can't use it in header files (which get #include-d). But ".cc" files don't get included, can I use "using namespace std;" there?

---

### Post by runningwithscissors on 2007-07-16
> **MiCovran said:**
> Could someone, please, just post at least a short yes/no answer to this "using namespace std;" question? I just don't like writing "std::" all the time. :popcorn:

I think you can. I don't see any reason not to use it in source files. But, I don't really code much C++, so I am not aware of any standard convention regarding the use of it.

---

### Post by aks44 on 2007-07-16
> **MiCovran said:**
> Could someone, please, just post at least a short yes/no answer to this "using namespace std;" question? I just don't like writing "std::" all the time.

Well, in source files (.cpp / .cc) you can use "using namespace std;" although it is generally regarded as bad form.
The logic behing it is that namespaces are here for a reason (ie. preventing name clashes), and "using namespace std;" brings many clutter in the global namespace, which could easily lead to name clashes. I guess it's ok though in a source file.

Just **don't** put it in a header, as it can quickly become problematic there (people including your headers won't expect std:: members to be available in the global namespace, and they may declare functions that conflict with it).

I personnaly prefer avoiding any "using namespace ..." altogether, even in source files: the overhead of prefixing with std:: is not that much, and IMHO it makes it clearer what function / class you use when you come back after some time and read the code.

---

### Post by MiCovran on 2007-07-16
Thanks for your help. I just love this forum, so many helpful people. :)

---

### Post by hod139 on 2007-07-16
I just now saw this thread, and I have some general comments about this example code posted by runningwithscissors.   I have added comments in bold to his/her code.  I realize the point of the example was to keep things simple, and runningwithscissors may very well be aware of all the comments I am making, but I think it is worthwhile to teach good habits early and point out these changes.
> **runningwithscissors said:**
> Simple C++ header : app.hh

```

#ifndef __APP_HH__
#define __APP_HH__
#include <iostream>  **//Do not include iostream in header files, include iosfwd**

class app {
public:
        **// Constructors should be explicit and the parameter ****should take a constant reference to the string, not a copy**
        app(std::string); 
};
#endif

```Source file : app.cc

```

#include "app.hh"
**// Pull in the iostream header in this source file here**

app::app(std::string msg) **// Change to const reference**
{
        std::cout << msg << std::endl;
}

```Main source file: test.cc
```

#include "app.hh"
**// If the string class is forward declared in app.hh, pull in the string headers here **

int main(int argc, char** argv) **// why have a argc and argv param if not using them?**
{
        app("Hello World");
        return 0;
}

```Compile and execute with:
```
$ g++ app.cc test.cc -I./   **// you should add the -Wall flag, and the -I. flag is not needed (default)**
$ ./a.out
```

You should never include iostream in a header, always use iosfwd.  In my code below, I elected not to use iosfwd to forward declare the std::string datatype, instead including the string type inside the header.  The string header class is not very large and is standard, so it should be portable.  If I had used iosfwd, I would have to include string in test.cc, as it would be undefined at linking time.

Lastly, modern versions of GCC recognize the "#pragma once" directive, in replace of the #ifdef include guard.  The  #pragma once directive is not standards compliant, but I think it makes the headers look cleaner, and some people claim it improves compile time.  Here is the modified code:

Simple C++ header : app.hh
```

#pragma once     // Not standards compliant, but IMO neater
#include <string> // only need string, not all of iostream
//#include<iosfwd> // This would work and forward declare the string, but then the test.cc class would confusingly have to include string.

class app {
public:
        explicit app(const std::string& msg);
};

```Source file : app.cc

```

#include "app.hh"
#include <iostream> // need to pull in iostream.h here now, since it is not declared in app.hh

app::app(const std::string& msg)
{
        std::cout << msg << std::endl;
}

```Main source file: test.cc
```
#include "app.hh"

int main(void)
{
        app("Hello World");
        return 0;
}

```Compile and execute with:
```
$ g++ -Wall app.cc test.cc 
$ ./a.out
```

---

### Post by MiCovran on 2007-07-16
> You should never include iostream in a header, always use iosfwd.
What exactly is iosfwd?

> g++ -Wall app.cc test.cc
And what's -Wall?

---

### Post by aks44 on 2007-07-16
> **MiCovran said:**
> What exactly is iosfwd?
"iosfwd" is an abbreviation of "iostream forward". As its name suggests, this header contains forward declarations to the iostream header (ie. it's a way to let the compiler know the names you need, but not the details).
The fact is, iostream is a very heavy include so it's best avoided to include it in any header (which in turn may be included in numerous places).
As hod139 put it, only include iostream in a source file, not in a header.

> **MiCovran said:**
> And what's -Wall?
A gcc/g++ command line option to enable all warnings.

I also tend to use -Wold-style-cast (warn if an old C cast is used instead of one of the C++ casts) and -Werror (treat all warnings as errors) for compiling my own source files (beware of some libraries which headers generate warnings, you may then want not to use -Werror).

---

### Post by 7Priest7 on 2007-07-16
HEHE iostream as a "heavy include"
I have included iostream and other includes and used less than a MB
Maybe back when computers did not have a gui they may have been heavy includes
But not in todays society

Alex

---

### Post by 7Priest7 on 2007-07-16
I used these 3
#include <iostream> // For Input And Output
#include <fstream>  // For Getting The Bible
#include <string>   // For holding strings

and it still used only 400kb including my code
Feel free to view it [http://www.Dos-Bible.org](http://www.Dos-Bible.org)

Fact is the includes are tiny yet usefull

Alex

EDIT: Ohh and the linux binary was even less...
11kb Windows was the 400kb ...
Makes you wonder why windows has any users.

---

### Post by MiCovran on 2007-07-16
Well, thanks again.

---

### Post by aks44 on 2007-07-16
> **7Priest7 said:**
> HEHE iostream as a "heavy include"
I have included iostream and other includes and used less than a MB
Maybe back when computers did not have a gui they may have been heavy includes
But not in todays society

You sure have a deep understanding of the build process and of the Standard Library (formerly named the Standard *Template* Library... does it ring a bell?), if you base your judgement about iostream's heaviness on the resulting binary size...

Tip: it's all about compile-time matters, not runtime ones. Got it now?

---

### Post by 7Priest7 on 2007-07-16
I can compile my codes in seconds...
But I code more efficently than most people...
Most people over code...
I code just enough...

Alex

---

### Post by aks44 on 2007-07-16
> **7Priest7 said:**
> I can compile my codes in seconds...
But I code more efficently than most people...

Maybe you'll think about "including more efficiently" when you'll be writing something that takes way longer than "seconds" to build. You know, a real world application... :roll:

---

