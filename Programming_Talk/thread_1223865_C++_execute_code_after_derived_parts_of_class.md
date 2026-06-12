---
title: "C++: execute code after derived parts of class?"
date: 2009-07-26
forum: Programming Talk
---

### Post by stair314 on 2009-07-26
I'm assuming the answer to this is no, but is there any way to
set up code that will run after the derived classes finish constructing?
Essentially I'm looking for a way to make sure that a few
virtual methods get called every time an object is allocated.
Unfortunately, one cannot call virtual methods from the base
class constructor, so right now I have to have each of the derived
classes duplicate the initialization code / and I have to have
arguments in the constructor to tell each class whether it is
the most derived class or not. Not a very elegant solution.

As an example, I would like to be able to do this:

```

class A
{
  public:
    A() {  finishConfig(); }
    virtual void finishConfig() { doSomething(); }
};

class B
{
  public:
    B() {}
    void finishConfig() { doSomething(); }
};

```

but instead I must do this


```

class A
{
  public:
    A(bool isMostDerived=true) {  if (isMostDerived) finishConfig(); }
    virtual void finishConfig() { doSomething(); }
};

class B
{
  public:
    B(bool isMostDerived=true) : A(false) { if (isMostDerived) finishConfig(); }
    void finishConfig() { doSomething(); }
};

```

Apart from it being annoying to write more, I also don't like
this setup because it means 3rd party developers will need to know to call finishConfig() in their derived classes.

---

### Post by dribeas on 2009-07-27
As you said, there is no solution to your problem there. You need a two step construction mechanism and that requires users (implementors of most derived classes) to call the init() (/finishConstruction()) _after_ they have constructed the object. Note that it is not _at the end_ of the constructor but rather after the object has been built:

```
// user code
MostDerived d;
d.init(); 
```

The problem with your proposed solution (where the constructor receives a boolean identifying whether it is the most derived element) is that it is error prone:

```

class Base {
   Base( bool mostDerived = true );
};
class Derived : public Base { // not meant to be derived now...
   Derived() : Base( false ) {};
};
// Now I decide to derive:
class MostDerived : public Derived {
   MostDerived() : Derived() {}
};

```

And this will get quite funny to debug for your users... The advice is _never_ to call virtual methods, not just _try_ not to call.

---

