---
title: "Classes with Constructors that take Arguments in a Vector"
date: 2008-10-14
forum: Programming Talk
---

### Post by Caged on 2008-10-14
That was a mouthful...

Hello. I've been playing a bit with vectors. Is it true that it is impossible to create a vector of classes that take arguments? This is just me experimenting with C++...

---

### Post by dwhitney67 on 2008-10-15
How much have you played/experimented?

Yes, it is possible to create a vector that holds class objects in which the constructor accepts arguments.  Bear in mind that the class must have a copy-constructor and an operator=() method (note this is not required if the class is stored by pointer, which is generally done).
[PHP]#include <vector>
#include <iostream>

class Foo
{
  public:
    Foo(int value) : m_value(value) {}

    Foo(const Foo& other) : m_value(other.m_value) {}

    ~Foo() {}

    int getValue() const { return m_value; }

    Foo& operator=(const Foo& other)
    {
      m_value = other.m_value;
      return *this;
    }

  private:
    int m_value;
};

int main()
{
  std::vector<Foo> vec;
  vec.push_back(Foo(10));
  std::cout << vec[0].getValue() << std::endl;
  return 0;
}[/PHP]

---

### Post by Caged on 2008-10-15
Only touched on the most basic stuff on vectors like push_back()... I tried making structures with vectors then I thought of classes.

I just read about copy constructors in a book and it looks like yours is a bit different from it. Can you explain what the colon in the middle here does?

Foo(int value) : m_value(value) {}

---

### Post by era86 on 2008-10-15
> **Caged said:**
> Only touched on the most basic stuff on vectors like push_back()... I tried making structures with vectors then I thought of classes.

I just read about copy constructors in a book and it looks like yours is a bit different from it. Can you explain what the colon in the middle here does?

Foo(int value) : m_value(value) {}

It is an initializer for class Foo.  A simple way to initiate variables rather than doing it in the constructor body.  Like this:

[php]
Foo(int value)
{
     m_value = value;
}
[/php]

---

### Post by dwhitney67 on 2008-10-15
> **Caged said:**
> Only touched on the most basic stuff on vectors like push_back()... I tried making structures with vectors then I thought of classes.

In C++, a struct(ure) and a class are identical in every way, except one... in a class, any defined value, method, constructor, destructor, etc are by default considered private; in a structure, they are all public.

Structures, like classes, can have constructors, destructors, virtual methods, and restricted areas (protected and private).

> **Caged said:**
> 
I just read about copy constructors in a book and it looks like yours is a bit different from it. Can you explain what the colon in the middle here does?

Foo(int value) : m_value(value) {}
As for this question, Era86 answered this in an earlier post.

---

### Post by Caged on 2008-10-15
Thanks guys.

---

### Post by dribeas on 2008-10-15
> **era86 said:**
> It is an initializer for class Foo.  A simple way to initiate variables rather than doing it in the constructor body.  Like this:

[php]
Foo(int value)
{
     m_value = value;
}
[/php]

Adding to this, to get a better insight:

Initializer lists have other differences, first being that in the sample code above the compiler will generate code to first default-construct m_value (ints get 0 by default) and then assign the value. While this may be a negligible performance hit in some cases, the important part is that the requirements on the initialized member attribute's class are different.

```

class X;

class Y
{
public:
   // Initializer lists
   Y( X const & x ) : x_( x ) {} // [1]
   Y( int i ) : x_( i ) {} // [2]

   // Assignment
   Y( X const & x ) { x_ = x; } // [3]
private:
   X x_;
};

```

To compile, in case [1], X must have an available constructor with the correct number of arguments (in [1] a copy constructor, in [2] a constructor of X must take a single int as argument). On the other hand, in case [3] X must have a default constructor (if all constructors take arguments or default constructor is marked private it will not compile), and X must also have an accessible assignment operator (even if it is the default provided, but cannot be private).

Note that references cannot be value initialized, that is:

```

class Z
{
public:
   Z( X& x ) : x_( x ) {}  // Correct
   Z( X& x ) { x_ = x; }   // Error: cannot value initialize a reference
private:
   X& x_;
};

```

---

