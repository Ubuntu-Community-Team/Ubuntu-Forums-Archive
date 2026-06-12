---
title: "C++ compile error, inheritance related (I think)"
date: 2010-07-06
forum: Programming Talk
---

### Post by kernco on 2010-07-06
I'm having trouble fixing a compile error I'm getting.  I'm using the Qt library, and in my project I've subclassed QVector2D with my own Vector class.  Another class I have, Foo, has this constructor:

```
Foo(const Vector &, qreal, Bar*)
```

The error comes when I try to instantiate one of them like this:

```
foo = new Foo(Vector(1, 0.3).normalized(), 1, this);
```
I get the error

```
no matching function for call to ‘Foo::Foo(QVector2D, int, Bar* const)’
candidates are: Foo::Foo(Vector, qreal, Bar*)
Foo::Foo(const Foo&)
```

The normalized() function returns a QVector2D, but since Vector inherits QVector2D, shouldn't it work?  Is there some type of copy constructor I need to write?  I also notice that it looks like I'm trying to pass a "Bar* const" to the constructor, but it takes "Bar*".  I don't think this is the source of the error, since I'd expect a "discards qualifiers" error if it was.

---

### Post by GreenN00b on 2010-07-06
If you have to classes Base and Derived and Derived inherits from Base then a function that accepts a parameter of type Base will accept Deriver, not the other way around.

---

### Post by Some Penguin on 2010-07-06
What is the 'greal' type, and have you tried casting to it?

---

### Post by jim_24601 on 2010-07-07
> **Some Penguin said:**
> What is the 'greal' type, and have you tried casting to it?

"Typedef for double on all platforms except for those using CPUs with ARM architectures. On ARM-based platforms, qreal is a typedef for float for performance reasons." according to the Qt documentation.

Anyway, what GreenN00b said. You can't pass a base class where a derived one is expected (what if the called function wants to use some derived functionality that the base doesn't implement?)  You'll need to either change the Foo constructor to take a QVector2D, or construct a Vector of your own to pass it.

You also seem to have a const problem. If the Foo constructor doesn't need the Bar passed it to be mutable, you can just make it take it as const. Otherwise, you'll have to get rid of the const-ness. (Not by using const_cast.)

---

