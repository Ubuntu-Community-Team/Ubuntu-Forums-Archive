---
title: "Help understanding C++ single colon (:) usage"
date: 2007-12-19
forum: Programming Talk
---

### Post by JupiterV2 on 2007-12-19
Normally, a single colon refers to a label you can jump to with goto, but that's not the only time you can use it. You use it with class inheritance for one:

class SomeClass: public InheritedClass {};

What I don't understand is the usage in the following example and how I can take advantage of it:

[php]
class Testable {
    bool ok_;

  public:
    explicit Testable(bool b = true): ok_(b) {}

    operator bool() const { return ok_; }
}

int main() {
    Testable test;

    if( test ) std::cout << "Test is true\n";
    else std::cout << "Test is false\n";

    return 0;
}
[/php]

I don't understand the: ...): ok_(b)... part. Anyone clarify this for me?

---

### Post by LaRoza on 2007-12-19
I am rusty with C++, but this may help: [http://www.artima.com/cppsource/safebool.html](http://www.artima.com/cppsource/safebool.html)

It uses the same code, so that may be a C++ thing, and not unique to where ever you found it.

(It has something to do with overloading boolean operators)

---

### Post by Majorix on 2007-12-19
You can also use a colon in the ternary operator: [http://en.wikipedia.org/wiki/%3F:](http://en.wikipedia.org/wiki/%3F:)

However I have no idea about the usage in your example.

---

### Post by Wybiral on 2007-12-19
You can use the semicolon to initialize a member when a method is called. It's usually used to initialize constants in the constructor.

Example:

```

#include <iostream>

class object {
    const int m_member;
    public:
    object(const int member);
    int getMember();
};

object::object(const int member) : m_member(member) {
}

int object::getMember() {
    return m_member;
}

int main(int argc, char *argv[]) {
    object o(10);
    std::cout << o.getMember() << std::endl;
    return 0;
}

```

---

### Post by aks44 on 2007-12-19
The part after the colon is called an "initializer list", and is specific to class constructors.


Imagine that class:
```
class Foo
{
private:
  int bar;
public:
  Foo();
};
```

When a Foo object is constructed, you will probably want to initialize its private variable(s).

For some types of variables, you can get along with the old fashioned way, using assignments in the constructor:
```
Foo::Foo()
{
  bar = 0;
  /*...*/
}
```



Now if bar is not an int but a user-defined type (let's call that type Bar):
```
Foo::Foo()
{
//  bar = Bar(); // useless, C++ already called bar's default constructor
  bar = Bar(0); // see below
  /*...*/
}
```

As stated, the first assignment (using the default constructor) is useless as C++ by default constructs all objects using their default constructor.

The second assignment uses much overhead:
1) bar is default constructed
2) a temporary Bar(0) is constructed
3) bar is assigned the temporary object just created in (2)
4) the temporary object is destructed



Also, const and reference members just can't be assigned a value in any other place than the initializer list (trying to assign to a const member will give you a compiler error, and references have no way to be default-constructed).



The solution to all those problems is such an "initializer list":
```
class Foo
{
private:
  int m_int;
  const int m_const;
  Bar m_bar;
  Bar& m_ref;
};

Foo::Foo()
  : m_int(0),
    m_const(3), // can't be changed anymore since it's a const
    m_bar(0), // Bar is constructed using the Bar(int) constructor
    m_ref(m_bar) // m_ref references m_bar, this can't be changed anymore
{
  /*...*/
}
```

This way, even before entering the bracketed code { /*...*/ } you are sure that all members have a correct value assigned to them, in the most efficient way.
In C++, this is considered very bad practise NOT to use initializer lists.

They allow better exception handling too, but let's not dive into that right now... ;)


IOW, *_always_* use them, and initialize *_all_* your member variables explicitly this way.

---

### Post by JupiterV2 on 2007-12-19
Extremely useful! Once again, I am in dept to the Ubuntu Programmer Community! Kudos guys, exactly what I was looking for!

---

