---
title: "How does C++ 'modularize'?"
date: 2010-09-17
forum: Programming Talk
---

### Post by ownaginatious on 2010-09-17
Okay, so I'm learning C++ now (already know C# and Java, and comfortable in C), but I'm having trouble finding any significant information on how one separates a C++ program into pieces.

First of all, how do I separate classes into their own source files? My guess is I do just that... and then do I do something like this in another program where I would like to use the class?:

```
#include "AwesomeClass.cpp"
```

Do I want to use a header file instead (throw the definition of the class in there)? If I do, how does the header file 'link' to that class? Does it just look for something in the same folder?

I'm currently doing all this with gedit and g++ :p

So what's the proper and professional way of going about this?

Thanks!

---

### Post by lisati on 2010-09-17
Instead of using #include to pull in a .cpp file, I'd suggest identifying multiple input files on the command line and/or using tools such as a makefile.

---

### Post by MadCow108 on 2010-09-17
it is bad practice to include *.cpp files. (the only reason to do so is for test suites)

The declarations are all the compiler needs to compile an object file (exception see below).
you place the declarations in header files and include that in the implementation files which need it.
local project headers are included with "abc.h"
system headers are included with <abc.h>

"" are searched in the working directory first and then in the system paths (e.g. /usr/include)
<> are searched only in the system paths.

you can add system paths to be searched with the -I/folder/to/headers flag

an exception are templated classes and functions.
They need to be defined completely before they are used which means they have to defined in headers.

---

### Post by nvteighen on 2010-09-17
Hm... what one usually does is the following.

1. Write a header file (.h, .hpp are the usual extensions) for each class. There you describe your interface... **only** the interface, no code (except templated classes and functions...). For example:

```

#ifndef SILLY_HPP // This is used to avoid including a header more than once.
#define SILLY_HPP

#include <string> // std::string

class Silly
{
public:
    Silly(std::string);

    void printName();
    void countCallTimes();

private:
    int data;
    std::string name;
};

#endif

```

2. Code the implementation into a module. Usually, the class is implemented in a single file... there might be occasions where that's not advisable, but it's not the case. Let's implement this silly class Silly:

```

#include "silly.hpp"
#include <iostream> // std::cout

Silly::Silly(std::string myname)
{
    // I don't like initialization lists too much...

    name = myname;
    times = 0;
}

void Silly::printName()
{
    std::cout << name << std::endl;
    times++;
}

void Silly::countPrintTimes()
{
    std::string time_or_times;
    if(times == 1)
        time_or_times = " time!";
    else
        time_or_times = " times!";

    std::cout << "I've been printed " << times << time_or_times << std::endl;
}

```

3. Now, we want to use this in a program, let's do a simple test suit:
```

#include "silly.hpp" // All we need is our Silly class

int main()
{
    Silly mySilly("Hello!");
    
    int i = 0;
    for(; i < 3; i++) 
        mySilly.printName();

    mySilly.countPrintTimes();

    return 0;
}

```

4. Now, how to put all this together? Well, very easy, you use all **.cpp** files as input for g++ (-Wall -Wextra for enabling useful warnings... use them always!):
```

g++ -o myapp main.cpp silly.cpp -Wall -Wextra

```

How does this work, well... because when compiling, the compiler takes each file separately and turns them into Assembly... then the assembler takes each Assembly (temporary) "files" and turn them into native object binaries. Then the linker takes all binaries and join them into a single file, thus resolving the references between each module.

This is also valid for C (actually, this behaivor comes from C...), so use it if you use C as well in the future.

---

### Post by ownaginatious on 2010-09-17
Ahh excellent, nvteighen. This makes perfect sense to me now :). So I guess that means a header functions like how an 'interface' in Java or C# would.

Thanks to everyone else who responded too :).

---

