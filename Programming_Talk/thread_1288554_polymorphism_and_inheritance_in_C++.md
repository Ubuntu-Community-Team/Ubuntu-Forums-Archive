---
title: "polymorphism and inheritance in C++ ??"
date: 2009-10-11
forum: Programming Talk
---

### Post by MrStill on 2009-10-11
Hi,

I am an intermediate Java programmer who is trying to learn C++. I am having some difficulties with some of the more useful points of polymorphism. This is what I am trying to do (in Java):

```

public class Function{
      //method declarations 
}
public class SpecificFunction1 extends Function{
      //override every method of function 
}
public class SpecificFunction2 extends Function{
      //override every method of function 
}
public class Driver{
    public static void main(String[] args){
           Function functions[] = new Function[2];
           functions[0] = new SpecificFunction1();
           functions[1] = new SpecificFunction2();
           // call methods common to Function
    }
}

```

So far, I have created header files for Function and SpecificFunction1 and SpecificFunction2 using this general form:

```

#include "Function.h"

class SpecificFunction1: public Function{
public:
        //function headers
        //all functions were declared virtual in Function.h
};

```

This has provided general functionality so far; in that, I can require a Function type to be present in a class (using Function.h) and I can pass it SpecificFunction1 with no error.

But, if I try to include the header files from both subclasses of Function I get an error:

```

In file included from LnXoverXFunction.h:1,
                 from Analysis.cpp:8:
Function.h:1 error: redefinition of 'class Function'
Function.h:1 error: previous definition of 'class Function'
In file included from XeXFunction.h:1,
                 from Analysis.cpp:9:
Function.h:1 error: redefinition of 'class Function'
Function.h:1 error: previous definition of 'class Function'

```

Any suggestions would be appreciated.

---

### Post by MadCow108 on 2009-10-11
in c/c++ you have to provide include guards to prevent multiple definitions:

someheader.h
```

#ifndef __SOMEHEADER_H // arbitrary but unique name
#define __SOMEHEADER_H
// definitions
#endif

```
#ifndef and #define are preprocessor directives which are parsed before compilation

---

### Post by dwhitney67 on 2009-10-11
Without your complete code being listed, it is hard to determine where your programming went awry.

So, here's a simple example that hopefully will help to put you on track...

```

#include <iostream>

class Base
{
public:
   Base() {}

   virtual void doSomething() = 0;   // pure virtual
};

class Subclass : public Base
{
public:
   Subclass() {}

   void doSomething() { std::cout << "Subclass is doing something." << std::endl; }
};

int main()
{
// with pointer
//
   Base* base = new Subclass;

   base->doSomething();

// with reference
//
   Subclass sc;
   Base&    bc = sc;

   bc.doSomething();

// lastly
//
   //Base bs;   // can't do... Base is abstract.
}

```

---

### Post by MrStill on 2009-10-11
Thanks to both of you. I changed my header file as follows:

```

#ifndef FUNCTION_H
#define FUNCTION_H

class function{
     virtual double f(double);
     // more definitions
};
#endif

```

After that I was able to create my array of functions:

```

#include "SpecificFunction1.h"
#include "SpecificFunction2.h"

int main(){
     SpecificFunction1 sf1;
     SpecificFunction2 sf2;
     Function *functions[2];
     functions[0] = &sf1;
     functions[1] = $sf2;
     double x = functions[0]->f(3.0);
     double y = functions[1]->f(3.0);
     // etc ...
     return 0;
}

```

---

