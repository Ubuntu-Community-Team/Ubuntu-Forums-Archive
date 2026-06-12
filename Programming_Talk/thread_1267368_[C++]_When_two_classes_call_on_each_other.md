---
title: "[C++] When two classes call on each other?"
date: 2009-09-15
forum: Programming Talk
---

### Post by dr.silly on 2009-09-15
my program roughly looks like this:

```
class Item
{
    Q_OBJECT
    public:
        List parent;
};

class List
{
    Q_OBJECT
    public:
        QList<Item> list;
};


```

The problem is no matter which class is compiled first it will require the other class which wasn't compiled.

What's the way around this?

---

### Post by dribeas on 2009-09-15
In the general case, if you have two classes that depend on each other and one dependency is only on references or pointers, you can forward declare one of them before declaring the other, and define the methods after both are declared:

```

struct X;
struct Y
{
   Y( X & other ); // arguments (passed by pointer/reference/value are allowed)
   X f();    // return values are allowed
   X* xp; // pointers are allowed
   X& xr; // so are references
   std::tr1::shared_ptr<X> sp; // some smart pointers are allowed
// std::auto_ptr<X> ap; // others aren't
};
struct X
{
   X();
   Y y;  // this is allowed, at this point the compiler has the full definition, as any other use
};

```

---

