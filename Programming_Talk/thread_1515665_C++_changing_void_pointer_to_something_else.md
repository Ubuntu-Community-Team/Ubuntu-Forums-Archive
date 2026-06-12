---
title: "C++ changing void pointer to something else"
date: 2010-06-22
forum: Programming Talk
---

### Post by kachofool on 2010-06-22
Hey all,

I have a situation where user input will determine which kind of object is created in my program. This object is wrapped with another class. So the user's input needs to invoke object creation at execution. The issue is some higher level classes need a generic way to call this object:

Car Object -> (EngineA Object, EngineB Object, EngineC Object...etc)

EngineA,B,C all have the same function calls (that the car object sees anyway). I need a persistent pointer that points to either A, B, or C (which is decided at runtime). I thought I could create a void pointer and then change what type of pointer it is, but I think my understanding on this is a little off. I basically need to create some pointer and have it point to a different object depending on runtime. Is this possible?

---

### Post by MindSz on 2010-06-22
I think I've seen stuff like this before:

```
void *myVoidPtr;
int *myIntPtr;
int myInt;

myInPtr = &myInt;

myVoidPtr = (void *) myIntPtr;
```

Syntax may be a little off, but the general idea is to type-cast it.

---

### Post by PaulM1985 on 2010-06-22
You could create an abstract class called Engine.  Engine would have all of the engine functions but none of them implemented.  the implementations would be in the derived classes.

Classes EngineA, EngineB and EngineC would derive from this Engine class.  

You could then create a EngineFactory class.  In the EngineFactory class you could have static functions called CreateEngineA(), CreateEngineB() and CreateEngineC() which would return the appropriate Engine type.

At runtime you could have something like:
```

Engine *myEngine;

if (needEngineA)
{
     myEngine = EngineFactory.CreateEngineA();
}
else if (needEngineB)
{
     myEngine = EngineFactory.CreateEngineB();
}
else
{
     myEngine = EngineFactory.CreateEngineC();
}

```

Have a look at Factory method pattern.  I think that is the term for this.  By doing this you don't need a void pointer.

Paul

---

### Post by dribeas on 2010-06-22
The answer to the question in your title is that you can convert from a void pointer to any other type of pointer by using a static cast. But that is most often a bad idea, as you will be loosing all the type-safety that comes in the language.

The first solution to the actual problem is creating a class hierarchy and using pointers to the base type:

```

class engine {
public:
   virtual void start() = 0;
   virtual void stop() = 0;
};

class car_engine : public engine {
//...
}

engine * e = get_engine(); // might return any type of engine
e->start(); // we can start it because it is an engine
e->stop();  // and stop it... of course

```

Even in cases where you want to hold completely unrelated pointers (think of a variant type in a spreadsheet that can hold numbers, formulas, text, dates...) there are better solutions than using void pointers, like boost::any, or boost::variant.

---

### Post by kachofool on 2010-06-22
Thanks for the replies!

Will a pointer for the parent class be able to call all member functions of the child object (whether they be inherited or not)?

---

### Post by dwhitney67 on 2010-06-22
> **kachofool said:**
> Thanks for the replies!

Will a pointer for the parent class be able to call all member functions of the child object (whether they be inherited or not)?

No; for non-virtual methods of a sub-class, you will need to cast your base-class pointer to the appropriate sub-class type, before attempting to call the non-virtual method.

---

### Post by johnl on 2010-06-22
> **dwhitney67 said:**
> No; for non-virtual methods of a sub-class, you will need to cast your base-class pointer to the appropriate sub-class type, before attempting to call the non-virtual method.

And to add to this, I believe the appropriate cast for downcasting is a dynamic_cast<>, which will throw an exception (or return NULL?) if the pointer you passed cannot be cast to the sub-class.

e.g.

```

class engine;

class car_engine : public engine;

class truck_engine : public engine;

engine* e = new car_engine();

truck_engine* tr = dynamic_cast<truck_engine*>(e); 
// will throw exception or return NULL, not sure which.
// it might be exception for references and NULL for pointers.

```

---

