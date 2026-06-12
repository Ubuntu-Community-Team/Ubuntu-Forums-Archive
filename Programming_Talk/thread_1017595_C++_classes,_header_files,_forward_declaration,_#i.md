---
title: "C++ classes, header files, forward declaration, #include..."
date: 2008-12-21
forum: Programming Talk
---

### Post by night_fox on 2008-12-21
I have a minor problem to do with the layout of my code. Lets suppose my code is this:

[PHP]
class Outer
{
    class Inner
    {
        int bla1,bla2
    };
    Inner InstanceOfInner;
};
[/PHP]

I want to declare the class Inner in another header file. How can I do that while having the #include directive at the beginning of the file? The class Inner MUST be a member of class Outer and cannot be global.

Please help me because if I stop forcing myself to be boringly consistent and modular etc. then I will automatically start writing rubbish sloppy code.

---

### Post by nvteighen on 2008-12-21
Hmmm... Inheriting Inner as public?

Otherwise, I don't fully understand why you'd like to do such a thing in OOP... What you're trying to do sounds to me like you were trying to use C++ classes as C and C++ structs.

---

### Post by dwhitney67 on 2008-12-21
> **night_fox said:**
> ...

 The class Inner MUST be a member of class Outer and cannot be global.

...


Please understand that there is a difference between a definition of a class (or struct) and the instantiation of such.  When referring to class member data, these are either instantiated objects or a handle (pointer) to an object type.

If you require that class Inner be defined in a separate file, then do it... make a separate header file.  Include this header file within the file that defines class Outer; then declare a member data item within class Outer of type Inner.  Just make sure though that Inner cannot be instantiated.

I would just leave the definition of Inner as you have it.

An alternative is this:

Inner.h:
[php]
#ifndef INNER_H
#define INNER_H

class Inner
{
  friend class Outer;

  // note that member data below are private, thus the need for the
  // "friend" declaration above.
  int bla1;
  int bla2;

  Inner() {}
  Inner(const Inner& other) { this->bla1 = other.bla1; this->bla2 = other.bla2; }
  Inner& operator=(const Inner& other) { this->bla1 = other.bla1; this->bla2 = other.bla2; return *this; }
};
#endif
[/php]

Outer.h:
[php]
#ifndef OUTER_H
#define OUTER_H

#include "Inner.h"

class Outer
{
  public:
    Outer() {}

  private:
    Inner m_inner;
};
#endif
[/php]

---

### Post by escapee on 2008-12-21
+1 for dwhitney67's solution.  It does what you want it to do in an OOP manner and in a very clean manner.

---

### Post by night_fox on 2008-12-21
Thanks for taking the trouble to reply, but I fully understand the problem, and obvious things like the difference between a class and it's instantiations. I should have made the code clearer by putting publics at the beginning of the classes. The reason I would like "Inner" to be within "Outer" is that I might choose to declare another class called "Inner" somewhere else in the program, so for instance I might need Outer1::Inner to be different from Outer2::Inner. I'm just trying to find a solution to the original question!

---

### Post by dribeas on 2008-12-21
> **night_fox said:**
> Thanks for taking the trouble to reply, but I fully understand the problem, and obvious things like the difference between a class and it's instantiations. I should have made the code clearer by putting publics at the beginning of the classes. The reason I would like "Inner" to be within "Outer" is that I might choose to declare another class called "Inner" somewhere else in the program, so for instance I might need Outer1::Inner to be different from Outer2::Inner. I'm just trying to find a solution to the original question!

You should try to state your intentions, what you really need, why you need the class to be defined in an external header, what your uses for the inner class will be... I really see no real reason not to define the Inner class inside Outter class is it is to be publicly available. On the other hand, if it is private it does make sense to use just a plain forward declaration in the header (google for PIMPL idiom). What are you really trying to achieve?

Now the technical answer. You can use a forward declaration in your header file if that suffices your intended use. That is, you cannot do it if you plan on defining a member of type Inner, but you can do it if you only declare pointers to Inner.

The reason is that for the compiler to generate class Outer in your code (where Inner is a member) it must know the size of that object. At the same time, for you to declare a inner class, the outer class must already have been defined. Else the compiler will complain about Outer not being defined: is it a class as you intend, or a namespace? Will there be a class without Innner defined as an internal class? The compiler must know the answer to these questions before generating the code. 

Now, if a pointer to it suffices in your class, then you can do it:

```

// outer.h
#ifndef OUTER_H
#define OUTER_H
class Outer
{
public:
   class Inner; // forward declaration
   Outer();
   ~Outer();     // you need to free inner_ on destruction
private:
   Inner * inner_; // raw pointer, not that you cannot use auto_ptr as Inner has not been defined
};
#endif

// inner.h
#ifndef INNER_H
#define INNER_H
#include "outer.h"
class Outer::Inner // Outer must have been declared before this, in the include
{
// code goes here
};
#endif

// Outer.cpp
#include "outer.h"
#include "inner.h"
Outer::Outer() : inner_( new Inner ) // allocate and initialize the inner_ field
{
}
Outer::~Outer() 
{
   delete inner_; // don't forget to delete the memory
}

```

You must note that with this separation, users of Outer class will have to manually include inner.h, or else they won't be able to use it.

---

### Post by night_fox on 2008-12-21
Thankyou very much dribeas, I did not state the problem at all well, but you have solved it!

My programs have segfaulted loads of times because of the PIMPL idiom but now I know what it is called, and also I should make sure I delete everything I dynamically allocate.

---

