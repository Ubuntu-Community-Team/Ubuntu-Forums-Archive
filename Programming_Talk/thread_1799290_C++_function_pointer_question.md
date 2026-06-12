---
title: "C++ function pointer question"
date: 2011-07-07
forum: Programming Talk
---

### Post by cgroza on 2011-07-07
Hello everyone, I am implementing an event system in my application and I was wondering if there is some C++ equivalent to this python:
 ```
 
def callback_test(function):
    function()
class Test:
    def event_callback(self):
        print "called"
t = Test()
callback_test(t.event_callback)
 
``` So, I was wondering if I can do such a thing in C++ using function pointers.
 Right now I am using some Java-ish function objects.
 in C++, I have already done this with regular functions and static methods, but I have no idea how to do it with regular instance methods.

 Thanks.

---

### Post by psusi on 2011-07-07
If you want a third party function to be able to call a member function passed as a parameter, then yes, you need to pass it a function pointer, but specifically a pointer-to-member.

```

class Test;

void callback_test( Test *obj, void (Test::*member)() )
{
  (obj->*member)();
}

```

---

### Post by Npl on 2011-07-07
there are multiple options.
1) use templates if you know the classes involved (at compile-time)
2) use a "MyCallbackObject" interface and inherit this to any class you want to have a callback.
3) use method pointers (quirky, poorly covered in standard).
4) use delegates. Nonstandard, but usefull and closest to other languages.

if you want to know about the issues with method pointers and delegates (arent C++ standard so there various implementations floating around), search for ["c++ Delegates"]("http://www.google.com#q=c%2B%2B+Delegates"). [This is a good starting point]("http://www.codeproject.com/KB/cpp/FastDelegate.aspx").

---

### Post by cgroza on 2011-07-07
> **psusi said:**
> If you want a third party function to be able to call a member function passed as a parameter, then yes, you need to pass it a function pointer, but specifically a pointer-to-member.

```

class Test;

void callback_test( Test *obj, void (Test::*member)() )
{
  (obj->*member)();
}

```
Hmmm, that would mean that all my classes that will pass such a member function pointer  will need to have a common base? 

I was wondering how toolkits such as wxWidgets and Qt do it.

---

### Post by psusi on 2011-07-07
> **cgroza said:**
> Hmmm, that would mean that all my classes that will pass such a member function pointer  will need to have a common base? 

Yes.

> **cgroza said:**
> I was wondering how toolkits such as wxWidgets and Qt do it.

They have a common base class, but they also use a runtime method lookup mechanism using a string to locate a method pointer in a table that is registered by the constructor.

---

### Post by cgroza on 2011-07-07
> **psusi said:**
> Yes.



They have a common base class, but they also use a runtime method lookup mechanism using a string to locate a method pointer in a table that is registered by the constructor.
OK, well, all the bases that I need indirectly inherit from wxObject so I will think about converting if the current object function design becomes to clunky.

Also, I would be interested to know what are the advantages/disadvantages of the 2 approaches?
Thanks for the info.

---

### Post by dwhitney67 on 2011-07-07
If you take psusi's idea, along with the template idea suggested by Npl, you could implement your own callback construct.

For example:
```

#include <iostream>

template <typename T>
class Callback
{
   typedef void (T::*Function)(void);

public:
   Callback(T* instance, Function function)
      : myInstance(instance), myFunction(function)
   {
   }

   void test()
   {
      (myInstance->*myFunction)();
   }

private:
   T*       myInstance;
   Function myFunction;
};

class A
{
public:
   void doSomething() { std::cout << "A is doing something." << std::endl; }
};

class B
{
public:
   void doSomething() { std::cout << "B is doing something." << std::endl; }
};

int main()
{
   A a;
   B b;

   Callback<A> call1(&a, &A::doSomething);
   Callback<B> call2(&b, &B::doSomething);

   call1.test();
   call2.test();
}

```
Note that classes A and B are *not* derived from a common base class.

---

### Post by cgroza on 2011-07-07
Thank you for your help. I think I am going to spend a few hours to pick one of the approaches.

Thank you again.

---

