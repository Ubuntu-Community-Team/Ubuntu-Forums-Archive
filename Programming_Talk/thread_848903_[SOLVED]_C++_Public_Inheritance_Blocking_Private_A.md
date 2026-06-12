---
title: "[SOLVED] C++ Public Inheritance Blocking Private Access"
date: 2008-07-03
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-07-03
Take a look at the attachment,

I am getting very similar errors (see read me), it seems that the inheritance is not working correctly, the compiler says that AutoPlayer doesn't have access to the private Player data. yet it derives publicly??

please don't through masses of code at me, just explain in brief segments of code (basically don't over whelm me)

By the way this is a response to the Connect 4 challenge, please use useful code (credit isn't necessary but would be nice), and if you want a fully (possible future improvements) functional Python version just ask. or if you want comments (didn't think i needed to write them for debugging)

---

### Post by CptPicard on 2008-07-03
Without looking at your code, I am expecting Player to be the base class here. Everything works as expected, see here:

[http://www.parashift.com/c++-faq-lite/basics-of-inheritance.html](http://www.parashift.com/c++-faq-lite/basics-of-inheritance.html)

in particular #19.6.

See protected or private inheritance instead :)

---

### Post by jim_24601 on 2008-07-04
Without looking at your code either, I can say with very high confidence that you don't want to use private or protected inheritance.

I imagine that you have a situation like:

```

class Base
{
private:
  int m_foo;
};

class Derived : public Base
{
public:
  void f(void) { cout << m_foo; }
};

```

and the compiler is complaining that the derived class can't see the private member of the base class, right?

Well, the compiler is right. If you derive publicly from a base class, this doesn't mean that your derived class can use members of the base class as if they were public. That's the choice of the designer of the base class, not the derived class.

Private members are strictly private to that class (though not necessarily that object), and any friends it declares. Derived classes cannot access them. If you need a base class member to be accessible by derived classes, declare it protected.

A derived class can always access public and protected, but not private, members of its own base class(es). The type of inheritance defines what *other* code can use base class members through the derived class:
[LIST]
[*]Public inheritance: Any code can use public members inherited from the base class. This is the usual form.
[*]Private inheritance: Only the derived class can use (public and protected) members of its own base class. This isn't very much used--it's generally better to use a private member of the class type rather than deriving privately from it.
[*]Protected inheritance: Classes *further derived* from the derived class can use (private and protected) members of the base class. As far as I know, this inheritance type is never used at all.
[/LIST]

Example:

```

class Base
{
public:
  void f();
};

class PubliclyDerived : public Base
{
};

class PrivatelyDerived : private Base
{
};

PubliclyDerived pub;
pub.f();  // ok - can use public derived class like base
PrivatelyDerived pri;
pri.f();  // illegal - can't use as base

```

---

### Post by jim_24601 on 2008-07-04
I should add that it's a bad idea to use any sort of inheritance while under the influence of alcohol. Remember--don't drink and derive. :lolflag:

---

### Post by Mr.Macdonald on 2008-07-04
Wow that's annoying, the protected private thing worked.

also if class1 has friend class01

then a subclass of class01, class02 isn't a friend of class1

why, that's really unreasonable.

---

### Post by jim_24601 on 2008-07-07
Well, not really. You might trust your neighbour enough to give him a spare set of keys to your house, but do you want his delinquent teenage son coming in and trashing the place?

You're thinking from the point of view of a single developer designing the whole class hierarchy. Look at it as a library or framework developer: you've designed a linked pair of classes, one of which is a 'friend' of the other. If friendship was inherited, then *any* user of your framework could gain access to all the private members of the one class simply by inheriting from its friend, which would most likely break all your careful encapsulation work.

You can always use protected methods in the friend class to provide access to its subclasses, but if you're going to go that route you might as well just provide accessors in the first class.

---

