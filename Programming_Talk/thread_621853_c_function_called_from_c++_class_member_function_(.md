---
title: "c function called from c++ class member function (callback)"
date: 2007-11-24
forum: Programming Talk
---

### Post by monkeyking on 2007-11-24
Is it possible (without staticing everything), to call a c function, from a member function in a class. And the c function takes a function pointer to anothr member function in my class.
-------------------------------------------------------------------------------
The reason for this strange need, is the simpel fact that I already have en optimization function, that optimezes a function, given by a function pointer.
This optimization is written in c, Anjd I don't want to implement it in c++.

But this is just a small part of a bigger program so I need to have the "function to be optimized" as a member of a class. (I need some strange datastructures).
That's why I don't do everything i c.


That is,
 the optim method, optimizes a parameter space given by a double array.
But the function to be optimized relies on some other datastructures

-------------------------------------------------------------------------------
These are some trimmed downed c-files (the function that will optimize).
```

//----------------------------cFun.h
double findmax_bfgs(double *invec, double (*fun)( double x[]));

 //----------------------------cFun.c
#include "cFun.h"

double findmax_bfgs(double *invec, double (*fun)( double x[])){
  double result;
  result = (*fun)(invec);
  return result;
}

```

These are the class def. and implementations

```

//-----------------------cppFun.h
class cppClass {
private:
  int a,b;
public:
  double myFunction(double *ptr);
  double run_optim();
};

//-----------------------cppFun.cpp
#include <iostream>
extern "C" {
#include "cFun.h"
}
#include "cppFun.h"

double cppClass::myFunction(double *ptr){
  return ptr[0];
}

double cppClass::run_optim(){
  double tmp[3] = {3,2,1};

  double var = findmax_bfgs(tmp,&myFunction);
  return var;
}

int main(){
  cppClass muob;
  double res = muob.run_optim();
  std::cout<<"res:"<<res<<std::endl;
}

```

These will ofcause not optimize anything,
but that will be fixed.
The major problem is that they wont't compile.

btw I compile with

```

gcc -c cFun.c
g++ cppClass.c cFun,o

```

Thanks in advance

---

### Post by aks44 on 2007-11-24
Even if standard C++ had closures / delegates (that's how a pointer to a non-static member function is called), C wouldn't support them since it is not an OO language.

When calling *obj.func()* what really happens under the hood is that the compiler calls *func()* with a hidden *this* pointer pointing at *obj*, something like *Class::func(&obj)*.

So a delegate would require two pointers: a pointer to the object, and a function pointer. Things quickly get complicated with (multiple) (virtual) inheritance which require pointer fix ups to access the correct part of the object. If you want to know some of the gory details, [this article]("http://www.codeproject.com/cpp/FastDelegate.asp") explains them quite well (but keep in mind that doesn't work with C).


The common method to achieve what you want is to pass a function pointer to a static callback along with a pointer to your object (as a void*), and have the static callback take this additional pointer so it can correctly call the member function:

```
extern "C" int c_callback(void* obj, int (*func)(int), int otherparams /*...*/)
{
  // check for null pointers (obj / func)
  return (*func)(obj, otherparams);
}


class Foo
{
private:
  int member_callback(int otherparams /*...*/)
  {
    // ... do your stuff
    return 0;
  }
  static int static_callback(void* obj, int otherparams /*...*/)
  {
    // check for null pointer (obj)
    return reinterpret_cast<Foo*>(obj)->member_callback(otherparams);
  }
public:
  int run()
  {
    return c_callback(reinterpret_cast<void*>(this), &Foo::static_callback, otherparams);
  }
};
```


But again, you gotta be careful with casting to and from void* since you loose all type-safety here, which can badly screw up things if it isn't done correctly.

---

### Post by monkeyking on 2007-11-24
thanks, very informative

---

