---
title: "C++ header files: functions within structs"
date: 2011-04-24
forum: Programming Talk
---

### Post by mcweaver1 on 2011-04-24
Afternoon all,

I have a c++ file, let's call it file.cpp, for which I am trying to make a header file, file.h.  I need to include the functions defined within file.cpp in other c++ files, and since the function definitions are fairly long I don't want to just rename it file.h.

The issue I am having is that file.cpp defines a structure, and all of the function definitions occur inside that structure, like:

```

struct myStruct {

    double value;
    ... other variable definitions...
    myStruct(double in_value) : value(in_value) {}

    double function1(double in) {
      // code...
    }

    inline void function2(double in) {
      // code...
    }

}

```

I am having trouble setting up the function declarations in the header file: currently I have the following in file.h
```

struct myStruct {

    double value;
    myStruct(double in_value) : value(in_value) {}

};

double myStruct::function1(double in);

inline void myStruct::function2(double in);

```

which is producing errors saying "no member function ... myStruct::function1 ... declared in class myStruct".

How can I create this header file successfully so that I can use all the functions in file.cpp from elsewhere by only including file.h?

Thanks in advance.

---

### Post by cjcopi on 2011-04-24
The issue you are having is where things need to be/are defined.  If something is part of a struct or class it must be defined in that struct or class.  Modifying your example you want file.h to be something like

```

struct myStruct {

    double value;
    ... other variable definitions...
    myStruct(double in_value) : value(in_value) {}

    double function1(double in);
    double function2(double in);
    // ... Other lengthy functions ...

    inline void ifunction1(double in) {
      // code...
    }
    // ... Other inline functions with their full code.  I think inline functions MUST
    // be fully defined inside a header.  Since these should only be short functions 
    // it is reasonable to put them here.
};

```You would then need a companion file.cpp that provides the definitions of the functions in myStruct
```

#include "file.h"

double myStruct::function1(double in)
{
  // ... code
}

double myStruct::function2(double in)
{
  // ... code
}

```Now if you have myprog.cpp it can just include file.h and compile it along with file.cpp to get all the functions in myStruct defined.

---

### Post by mcweaver1 on 2011-04-27
Thanks very much, that solves my problem perfectly :)

---

