---
title: "Question for C++ programmers: reference to superclass"
date: 2009-09-20
forum: Programming Talk
---

### Post by Keyper7 on 2009-09-20
Heya,

I have a simple questions and I hope some C++ guru can help me out here.

I'm in the following situation: I have an abstract class, let's call it Thingy, and three concrete subclasses SubThingy1, SubThingy2 and SubThingy3. I need to instantiate only one of them, according to certain conditions, and later use it as a generic Thingy. The easiest way would be to use explicit allocation with pointers and new:

```

Thingy *t;

if(blah)
    t = new SubThingy1;
else if(bleh)
    t = new Subthingy2;
else
    t = new Subthingy3;

```

But I don't want to use that because it's not very RAII (I would have to explicitly call destructors after, creating risk of memory likes and whatever). I'm currently doing the following:

```

SubThingy t1;
SubThingy t2;
SubThingy t3;

Thingy *t;

if(blah)
    t = &t1;
else if(bleh)
    t = &t2;
else
    t = &t3;

```

I suppose I don't have to comment on the ugliness of this. Not to mention the waste of resources (two of the subthingies are allocated but never used).

Can someone propose an elegant and RAII-friendly alternative? Ideally, it should be something using references like this

```

Thingy &t;

if(blah)
    t = SubThingy1;
else if(bleh)
    t = SubThingy2;
else
    t = SubThingy3;

```

or

```

if(blah)
    Thingy &t = SubThingy1;
else if(bleh)
    Thingy &t = SubThingy2;
else
    Thingy &t = SubThingy3;

```

Of course, none of those two proposals above are valid. In the first, it's invalid because a reference should refer to something on declaration and cannot change. In the second, the scope of t is restricted to the if/else clause.

---

### Post by MadCow108 on 2009-09-20
use smart pointers:
[http://www.boost.org/doc/libs/1_40_0/libs/smart_ptr/smart_ptr.htm](http://www.boost.org/doc/libs/1_40_0/libs/smart_ptr/smart_ptr.htm)
[http://www.boost.org/doc/libs/1_39_0/libs/smart_ptr/pointer_cast.html](http://www.boost.org/doc/libs/1_39_0/libs/smart_ptr/pointer_cast.html)

---

### Post by Keyper7 on 2009-09-20
> **MadCow108 said:**
> use smart pointers:
[http://www.boost.org/doc/libs/1_40_0/libs/smart_ptr/smart_ptr.htm](http://www.boost.org/doc/libs/1_40_0/libs/smart_ptr/smart_ptr.htm)
[http://www.boost.org/doc/libs/1_39_0/libs/smart_ptr/pointer_cast.html](http://www.boost.org/doc/libs/1_39_0/libs/smart_ptr/pointer_cast.html)

Thanks. I was looking for an alternative that didn't require pointers at all, but using smart pointer does seem better than all previous attempts so far.

---

### Post by dwhitney67 on 2009-09-20
> **Keyper7 said:**
> 
...
But I don't want to use that because it's not very RAII (I would have to explicitly call destructors after, creating risk of memory likes and whatever).
...

What are you referring to here?  If you have declared your base-class' destructor as virtual (btw, this the recommended thing to do when the class has virtual methods) then you won't have a problem.

For example:
```

#include <iostream>

class Thingy
{
public:
   Thingy() {}

   // virtual destructor
   virtual ~Thingy() { std::cout << "Thingy destroyed." << std::endl; }

   // pure-virtual method that makes this class abstract
   virtual void doSomething() = 0;
};

class SubThingy1 : public Thingy
{
public:
   SubThingy1() {}

   ~SubThingy1() { std::cout << "SubThing1 destroyed." << std::endl; }

   void doSomething() {}
};

int main()
{
   Thingy* t = new SubThingy1();
   delete t;
}

```

---

### Post by Keyper7 on 2009-09-20
dwhitney, the problem is that I want to avoid using new and delete and use "instantiation through declaration" instead. It's cleaner and it avoids memory leak pitfalls, specially when exceptions are involved.

---

### Post by dwhitney67 on 2009-09-20
> **Keyper7 said:**
> dwhitney, the problem is that I want to avoid using new and delete and use "instantiation through declaration" instead. It's cleaner and it avoids memory leak pitfalls, specially when exceptions are involved.

Well good luck with your quest.  I do not believe what you want is achievable, unless you instantiate the 3 subclass objects as you presented earlier.  And as you have stated yourself, this is wasteful.  Imagine if you had more than 3 objects!

If you want, you can use auto_ptr, or as MadCow108 suggested, smart pointers.  The latter is available with Boost, and also with the TR1 extensions.

Using the example I presented earlier, here's an example using auto_ptr:
```

#include <memory>
...
int main(int argc, char** argv)
{
   std::auto_ptr<Thingy> t;

   if (argc > 1) {
      t = std::auto_ptr<Thingy>(new SubThingy1);
   }
   else {
      t = std::auto_ptr<Thingy>(new SubThingy2);
   }

   t->doSomething();
}

```

The TR1 shared_ptr will look similar; here's an example:
```

#include <tr1/memory>
...
int main(int argc, char** argv)
{
   std::tr1::shared_ptr<Thingy> t;

   if (argc > 1) {
      t = std::tr1::shared_ptr<Thingy>(new SubThingy1);
   }
   else {
      t = std::tr1::shared_ptr<Thingy>(new SubThingy2);
   }

   t->doSomething();
}

```

---

### Post by TheStatsMan on 2009-09-20
What you want to do is straightforward using static polymorphism, which uses templates.

[php]//base class
template<typename TypeThingy>
class Thingy
{
    public:
    void method1(){
        tthingy.method1();
    }

    private:
    TypeThingy tthingy
};
//derived class 1
class SubThingy1
{
    public:
    void method1(){
        ....
    }
}

//derived class 2
class SubThingy2
{
    public:
    void method1(){
        ....
    }
}[/php]Then the code to use


[php]if(blah){
    Thingy<SubThingy1> t
}
else{
    Thingy<SubThingy2> t
}[/php]I don't know what you are making such a big deal about new and delete though. It is really very easy, for every new use a delete. It is pretty much that simple to avoid memory leaks.

---

### Post by MadCow108 on 2009-09-20
> **dwhitney67 said:**
> Well good luck with your quest.  I do not believe what you want is achievable, unless you instantiate the 3 subclass objects as you presented earlier.  And as you have stated yourself, this is wasteful.  Imagine if you had more than 3 objects!


replace your new's with:
boost::make_shared<Thingy>(SubThingy1);
and you have archived it (at least that what I think the question was)

@ statsman, of course its possible to match your new's with deletes but in complex programs it may be hard to track which object is still referenced where and where does it's lifetime really end.
shared pointers or RAII solve this problem
its good practice to use smart pointers everywhere where pointers are needed (except in very performance critical regions where not even intrusive_ptr is good enough or trivial small programs where the syntax overhead is just annoying)

---

### Post by dribeas on 2009-09-21
Pointers are a required feature of the language. While you should avoid working with raw pointers (or with pointers in general) as much as possible, there are places where you cannot avoid it. Notice that in all applications pointers are needed: when you use any STL container you are indirectly using pointers.

That is where RAII comes into play, store all your resources inside RAII objects smart pointers for memory management... At some point you will even want to explictly pass raw pointers and have the receiving code encapsulate with RAII techniques. As an example (yours) a factory method could be defined as:

```

Type* createObject1( ArgType1 arg1, ArgType2 arg2...);
std::auto_ptr<Type> createObject2( ArgType1 arg1, ArgType2 arg2...);
std::tr1::shared_ptr<Type> createObject3( ArgType1 arg1, ArgType2 arg2...);

```

The advantage of 2 and 3 is that the code is safe with respect to memory leakages: the objects come encapsulated inside a smart pointer, if the caller does not take the returned value then it will automatically be managed by RAII and released. The disadvantage is that you are deciding what RAII object your caller can use to get your result. 

I work in a shop where raw pointers variables are forbidden, and with such a guide of style I would go for option1: return a raw pointer, assuming that if the caller is (as they should) using RAII techniques she will capture the returned object within the most appropriate smart pointer for their usage (which might be different than the previous two versions: std::tr1::scoped_ptr, std::unique_ptr [c++0x], some LOKI smart pointer...).

It is a little more fragile, but much more flexible if the users are accustomed to only using smart pointer variables.

---

### Post by Keyper7 on 2009-09-21
Hi everyone, sorry, I was away from this thread for a while.

I want to thank everyone who helped me here. I'm currently using auto_ptr but the suggestion of using static polymorphism and the other pointers were also very interesting.

This forum rocks. :)

---

### Post by MadCow108 on 2009-09-21
just be aware of the drawbacks of auto_ptr
it takes over ownership of the object and copies of auto_ptr are not equivalent.
so you must not use them in STL containers!
its an annoying flaw of the current standard
fortunately the new standard fixes that with the shared pointers

---

