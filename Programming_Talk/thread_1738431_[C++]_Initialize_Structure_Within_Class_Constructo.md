---
title: "[C++] Initialize Structure Within Class Constructor"
date: 2011-04-24
forum: Programming Talk
---

### Post by dodle on 2011-04-24
This isn't a serious problem, the compiler just gives me a warning when initializing a structure from within a class' constructor.

[php]#include <iostream>
using namespace std;

struct Move
{
    int rangeA;
    int rangeB;
};

class Area
{
  public:
    Area();
    Move m;
    Move GetRange() {return m;};
};

Area::Area()
{
    m = {8, 10};
}

int main()
{
    Area a;
    Move x = a.GetRange();
    
    cout << "Range A: " << x.rangeA << endl;
    cout << "Range B: " << x.rangeB << endl;
    
    return 0;
}[/php]

Warning:
```
$ g++ test3.cpp -o test
test3.cpp: In constructor 'Area::Area()':
test3.cpp:20:15: warning: extended initializer lists only available with -std=c++0x or -std=gnu++0x
test3.cpp:20:15: warning: extended initializer lists only available with -std=c++0x or -std=gnu++0x
```

Is there a way to get rid of this error? I don't know much about C programming, but if I try to use "gcc" instead of "g++" I get all kinds of complaints from the compiler.

---

### Post by cjcopi on 2011-04-24
The basic issue is that each class/struct should contain all the information it needs to describe itself and you should try not to assume knowledge about other classes/structs.  Essentially you want to provide an api with the internal implementations being irrelevant to the user.  Here is a small modification to you code.
```

#include <iostream>
using namespace std;

struct Move
{
    int rangeA;
    int rangeB;
    Move() : rangeA(0), rangeB(0) {}
    Move (int a, int b) : rangeA(a), rangeB(b) {}
};

class Area
{
  public:
    Move m;
    Area() : m(8,10) {}
    /* The above is equivalent to this but if you compile with
       -Weffc++ it will give you a warning telling you that the above
       is the preferred way to do things.
     */
    //Area() { m.rangeA=8; m.rangeB=10; } 
    Move GetRange() {return m;};
};

int main()
{
    Area a;
    Move x = a.GetRange();
    
    cout << "Range A: " << x.rangeA << endl;
    cout << "Range B: " << x.rangeB << endl;
    
    return 0;
}  

```Here I have created constructors for Move and used them to intialize m in Area without having to know anything about Move.  This is a more correct way of doing what you wanted.

Now if you change Move but don't change the fact that it takes two integers to describe it then Area doesn't have to care about that, it will continue to work.

---

### Post by nvteighen on 2011-04-25
I don't get why you want to use a C++ struct like a C struct. It's possible, but it kinda defeats the purpose of C++ structs being classes with everything set as public by default (instead of protected)... That's why cjcopi suggests you to write a constructor for the struct, effectively making use of the fact that C++ structs are classes too.

But I may be missing something, so here's how structs are to be initialized in C and in C++98 when used as C structs.

In C structures are initialized exactly like arrays. This means, you can use the initialization list only when defining a new structure. If you just declare a structure, you'll have to initialize each field separately, exactly as you would do with an array. The reason for this aren't clear to me and it seems they aren't for the C++0x drafters either; I see no technical reason for this limitation for structures (and also arrays) stored in the stack (if someone knows one, please tell me). But that's how C was defined and C++ inherited that behaivor.

So, this boils down to the following:

```

// In C++, the struct keyword is optional.
struct Move m = {1, 2};

// ...

// m = {2, 5}; would be incorrect here. You have to use:
m.rangeA = 2;
m.rangeB = 5;

```

```

struct Move m;

// m = {1, 2}; incorrect. Use:
m.rangeA = 1;
m.rangeB = 2;

```

In the C world, this has lead to the practice of creating initializing functions... even for structures meant to be stored in the stack (for heap-stored ones, you have no choice but to write one). These initialization functions are semantically no different to C++ constructors.

---

### Post by layers on 2011-04-25
> **dodle said:**
> I try to use "gcc" instead of "g++" I get all kinds of complaints from the compiler.
Good points by the others.
The way I see it, is you use gcc for *.c written in C, and g++ for *.cpp written in C++.

---

### Post by Zugzwang on 2011-04-25
> **dodle said:**
>  I don't know much about C programming, but if I try to use "gcc" instead of "g++" I get all kinds of complaints from the compiler.

Note that you don't get these errors from the compiler, but rather from the linker. Both "gcc" and "g++" determine whether a file should be treated as a C++ or a C file from its extension. Only in the linking phase, it makes a difference whether you used "gcc" or "g++", as only in the latter case the C++ standard library is linked against.

---

### Post by dodle on 2011-04-25
**@cjcopi:**

Thanks, I will study that over. I didn't know how to write a constructor for a struct.

**------ EDIT ------**

Okay, a question about that code: How come I have to define the constructor within the class definition?

[php]Area() : m(8, 10) {}[/php]

Why can't I do it outside of the definition?

[php]Area::Area()
{
    m(8, 10);
}[/php]

Or am I just doing it wrong? I'm just trying to figure out how and why things are done. I probably don't need to point out, but I will :), that I am a newbie.

**------ EDIT ------**

I see now that writing a constructor for a stuct is identical to writing one for a class.

---

### Post by dwhitney67 on 2011-04-25
> **dodle said:**
> [b]How come I have to define the constructor within the class definition?

Why can't I do it outside of the definition?

By the time the execution point has reached the "body" of the constructor, the class object has already been constructed.  I wish books/tutorials would explain this better.
```

class Foo
{
public:
   Foo();

private:
  int member;
};

Foo::Foo()
   : member(10)   // at this level, the class is constructed
{
   // at this point, the class is constructed.
   // any other code here is probably (but not always) unnecessary.
}

```

> **dodle said:**
> 
I see now that writing a constructor for a stuct is identical to writing one for a class.
A class and a struct are identical in every sense, except one.  By default, all functions and member data declared in a class are considered private, unless otherwise indicated.  In a struct, these entities are by default public.

---

