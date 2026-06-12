---
title: "Default values of variables inside a C++ class"
date: 2008-08-06
forum: Programming Talk
---

### Post by WebDrake on 2008-08-06
Hello all,

I have a class -- let's call it myClass -- which is intended to have several subclasses.  One of its protected elements is a vector, whose size should be set in the constructor:

```

class myClass {
protected:
    int n;
    vector<double> v;
public:
    myClass() {
        v.resize(n);
    };
};

```

Note that in this snippet I haven't actually set n, which of course I could do in the constructor, but don't want to for this reason: different subclasses will have different values of n, and hence the size of v should be different for these subclasses.

If I initialise n inside the myClass() constructor (say, n=0) then v will always be initialised to size 0.  If in a subclass I want a different vector size then I will have to use another v.resize() command, which I would like to avoid.

So, is there a way of setting default values of n for myClass and for its subclasses, such that the myClass() constructor will always use the appropriate one?

Alternatively -- since I think it's clear what I'm trying to achieve here -- is there another way of achieving what I want which doesn't rely on the subclass having to do anything other than set the value of n?

Many thanks & best wishes,

    -- Joe

---

### Post by supirman on 2008-08-06
You should be able to achieve what you want by doing something similar to this (the code likely isn't quite right, but it should give you the idea):

```
class myClass {
  int n;
  vector<double> v;

  // initialize n with the passed in integer
  myClass(int i) : n(i) { v.resize(n); }
};
class mySubclass: myClass {
  // initialize my base class with the passed in size
  mySubclass(int i): myClass(i) { }
  
  // initialize base class with predefined size
  mySubclass(): myClass(7) { }
};
```

You can create a constructor for your base class which accepts 'n' as input.  In the initializer list for the subclass, you call myClass(i) to initialize the base class's 'n' member.

---

### Post by WebDrake on 2008-08-06
> **supirman said:**
> You should be able to achieve what you want by doing something similar to this (the code likely isn't quite right, but it should give you the idea):


Thanks very much -- I was able to modify your suggestion to do pretty much exactly what I wanted.  Not the syntax I'd imagined, but it works! :-)

---

