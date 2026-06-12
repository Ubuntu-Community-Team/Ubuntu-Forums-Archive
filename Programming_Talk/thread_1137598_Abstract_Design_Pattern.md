---
title: "Abstract Design Pattern"
date: 2009-04-25
forum: Programming Talk
---

### Post by dwhitney67 on 2009-04-25
I was assigned to peer review some code (and presumably the design as well) the other day at work.

One of the CSCs that I came across appeared to be implementing the Abstract Design Pattern, which although I understand it conceptually, I was unable to accept what I saw in the design/code.

Below is some code I threw together that mimics what I came across:
```

#include <vector>
#include <iostream>
#include <algorithm>


class Base
{
};

class Interface
{
  protected:
    virtual ~Interface() {}
    virtual void doSomething() = 0;
};

class MyClass : public Base, virtual private Interface
{
  public:
    virtual ~MyClass() {}

    virtual void doSomething() { std::cout << "doing something." << std::endl; }
};


// This part below I made up to demonstrate how the Abstract Design Pattern is being
// used.
//
void myClassDoer(Base* b);

int main()
{
  typedef std::vector<Base*> BaseVec;
  BaseVec bv;
  bv.push_back(new MyClass);

  std::for_each(bv.begin(), bv.end(), myClassDoer);
}


void myClassDoer(Base* b)
{
  MyClass* mc = static_cast<MyClass*>(b);
  mc->doSomething();
}

```

Now, is it just me, or is this overkill?  The Base class has no virtual methods.  Thus it is useless should one wish to treat the subclass polymorphically.  A hard-cast must take place before the object can be used, thus in essence requiring the application developer to be aware of the context of the class being operated on.

Any thoughts on whether this is a standard practice, or am I just being over-zealous in my desire to nit-pick at this design?

---

### Post by Namtabmai on 2009-04-25
Personally I agree with you, but as the implementation you've shown really is only example I'd be forgiven to give them the benefit of the doubt.

If the code is supposed to demonstrate polymorphism then that's fine, but otherwise it's dubious.

What design pattern was this supposed to be implementing?

---

### Post by dwhitney67 on 2009-04-25
> **Namtabmai said:**
> Personally I agree with you, but as the implementation you've shown really is only example I'd be forgiven to give them the benefit of the doubt.

If the code is supposed to demonstrate polymorphism then that's fine, but otherwise it's dubious.

What design pattern was this supposed to be implementing?

Like the title of the thread states, the "Abstract" design pattern.

I think that the person who designed the code I was asked to review had good intentions, but went overboard with there design.  It would appear that he/she was looking for a common base-class (Base) to hold the objects that are inserted into a container (actually an STL map, not the vector as I demonstrated).  However, the common base-class could have easily been designed to be Interface, and that would have made more sense.

In either case, the original design "works", but makes very little sense.

---

