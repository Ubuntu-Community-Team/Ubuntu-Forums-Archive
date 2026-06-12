---
title: "Help in C/C++ hybrid programming"
date: 2011-03-01
forum: Programming Talk
---

### Post by aworld on 2011-03-01
Dear all

I have a main.c file and I can compile it using the following command :

gcc -o test -L.-lftd2xx -Wl, -rpath /usr/local/lib main.c

Then, I have to do it in C++, but somehow I can not change this main.c directly to C++, but I need those functions in this main.c and called by my other .cpp files.

How to do this? And how to link those libs, (as you see, this main.c have to use a third party .o file) 

Glad if someone can give me a clue.


Thanks.°^^

---

### Post by PaulM1985 on 2011-03-01
Is it not as simple as changing the compiler to be g++?

```

g++ -o test -L.-lftd2xx -Wl, -rpath /usr/local/lib main.c myOtherClass.cpp

```

Paul

---

### Post by Mordred on 2011-03-01
Hi,

long time since I played around with that but if I remember
correctly looking up some info on 'extern C' declarations should
help you further.

---

### Post by aworld on 2011-03-02
> **PaulM1985 said:**
> Is it not as simple as changing the compiler to be g++?

```

g++ -o test -L.-lftd2xx -Wl, -rpath /usr/local/lib main.c myOtherClass.cpp

```

Paul


Hi, Paul, I have tried your code, simply it does not work directly with changing gcc to g++,  

one of the error message says: invalid conversion from 'const void' to 'void'


I think the problem is how to make this c program compilable with g++ compiler, and how to mix them with other c/c++ programs

---

### Post by ibuclaw on 2011-03-02
> **aworld said:**
> I think the problem is how to make this c program compilable with g++ compiler, and how to mix them with other c/c++ programs

The trick is to put all C function declarations into a header for the C++ code to use.


Short example:

mylib.c
```

#include <stdio.h>
#include "mylib.h"

void message(const void* ptr)
{
   char* msg = (char*) ptr;
    printf("Message is: %s\n", msg);
}

void message_if(int cond, const void* ptr)
{
    if (cond)
    {
        char* msg = (char*) ptr;
        printf("Message is: %s\n", msg);
    }
}

```


mylib.h
```

#ifdef MYLIB_H
#else
#define MYLIB_H

#ifdef __cplusplus
extern "C" {
#endif

void message(const void* ptr);
void message_if(int cond, const void* ptr);

#ifdef __cplusplus
}
#endif

#endif

```

myprog.cc
```

#include <iostream>
#include "mylib.h"

int main()
{
    int num;
    bool cond;

    message("Enter a number");
    std::cin >> num;

    cond = (num == 42);
    message_if(cond, "You entered '42'");

    return 0;
}

```

And compile with:
```

gcc -c mylib.c
g++ -c myprog.cc

g++ myprog.o mylib.o -o myprog

```

And run the compiled program to test. :)

Regards

---

### Post by Milliways on 2011-03-03
> **ibuclaw said:**
> The trick is to put all C function declarations into a header for the C++ code to use.

mylib.h
```

#ifdef MYLIB_H
#else
#define MYLIB_H

#ifdef __cplusplus
extern "C" {
#endif

void message(const void* ptr);
void message_if(int cond, const void* ptr);

#ifdef __cplusplus
}
#endif

#endif

```

C programs can call c++ functions (provided the c++ function only uses arguments/return values supported by c).

You need to tell the C++ compiler to use c compatible names.
(C++ normally "decorates" names to support polymorphism.)

I have used this on Windows (but not GNU/Linux)
The keywords **extern "C"** should do this.
This can be included in a header, or directly in the C++ code.

Another approach is write a C++ wrapper function around the c++ function.
This is appropriate if you are using a library that you do not want to (or can not) modify e.g.

```
extern "C" void test(void)
{
  c_pp_function();
}

```

NOTE I would not use a c program as main.
This should be c++ to ensure the correct run-time is linked.
As you are writing main there is no reason not to do so.

Similarly C++ programs can call c functions - you need to tell the c++ compiler to use the correct calling semantics.
```
extern "C" void test(void);
```

---

### Post by aworld on 2011-03-03
> **ibuclaw said:**
> The trick is to put all C function declarations into a header for the C++ code to use.


Short example:

mylib.c
```

#include <stdio.h>
#include "mylib.h"

void message(const void* ptr)
{
   char* msg = (char*) ptr;
    printf("Message is: %s\n", msg);
}

void message_if(int cond, const void* ptr)
{
    if (cond)
    {
        char* msg = (char*) ptr;
        printf("Message is: %s\n", msg);
    }
}

```


mylib.h
```

#ifdef MYLIB_H
#else
#define MYLIB_H

#ifdef __cplusplus
extern "C" {
#endif

void message(const void* ptr);
void message_if(int cond, const void* ptr);

#ifdef __cplusplus
}
#endif

#endif

```

myprog.cc
```

#include <iostream>
#include "mylib.h"

int main()
{
    int num;
    bool cond;

    message("Enter a number");
    std::cin >> num;

    cond = (num == 42);
    message_if(cond, "You entered '42'");

    return 0;
}

```

And compile with:
```

gcc -c mylib.c
g++ -c myprog.cc

g++ myprog.o mylib.o -o myprog

```

And run the compiled program to test. :)

Regards


Hi, thank you so much for your help, I have tried your code, and it works, that is so great.

I will try this way in my program, hope it works fine!!

---

