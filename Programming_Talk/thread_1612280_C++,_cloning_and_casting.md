---
title: "C++, cloning and casting"
date: 2010-11-03
forum: Programming Talk
---

### Post by worksofcraft on 2010-11-03
Somewhere in the depth of my code I take two instances of the same class and call a method that produces a new instance of the same type from the old ones.

That's not too hard, except the problem is I only have references to some base class... Here let me put in code...
[php]
#include <cstdio>
#include <cstring>

struct base {
	// from *this and rClone create a new instance on the heap
	virtual base * q_clone2(const base &rOld) const = 0;
};

struct derived: base {
	const char *mytext;
	derived(const char *aTxt): mytext(aTxt) {}

	virtual derived * q_clone2(const base &rB) const {
		// unchecked type cast
		derived &rOld = * (derived *) &rB;
		// just any dumb demo combining *this and rOld to make qNew
		char *pNewText = new char[strlen(rOld.mytext) + strlen(mytext) + 1];
		strcpy(pNewText, mytext);
		strcat(pNewText, rOld.mytext);
		return new derived(pNewText);
	}
};

// parameters and return type are intended to always the same
base * q_combine2(const base &one, const base &two) {
	return one.q_clone2(two);
}

int main(int argc, char *argv[]) {
	// unchecked type cast
	derived *qC = (derived *) q_combine2(
		derived(argv[0]), derived("+old item")
	);

	printf("new = %s\n", qC->mytext);
	// 'q' is my "cue" to remember dispose of it ;P
	delete qC;
	return 0;
}
[/php]

The problem is my use of unchecked type casts: Once on a parameter of q_clone2 which I had to declare as reference to the base or it would not overload the same method, and once again when I come back out I have to simply assume the pointer is to my derived class.

So I was wondering if there is a better way to do this type cloning of new instances from existing ones?

---

### Post by dwhitney67 on 2010-11-03
The method signatures for q_clone2() do not match between the base and the derived classes.  It is Ok to define the method to return a base object pointer, even though in the implementation of the method (in derived), a derived object is allocated.

Also you may be required to employ RTTI checking of your derived objects to ensure that they are the correct type for cloning.

Here's a working example, which I developed in haste:
```

include <iostream>
#include <cassert>


class Base
{
public:
   Base() {}

   virtual ~Base() {}

   virtual Base* clone() const = 0;

   virtual Base* cloneOther(const Base* other) const = 0;
};

class Derived1 : public Base
{
public:
   Derived1(int val) : attr(new int(val)) {}

   Derived1(const Derived1& other) : attr(new int(*other.attr)) {}

   virtual ~Derived1() { delete attr; }

   virtual Base* clone() const { return new Derived1(*this); }

   virtual Base* cloneOther(const Base* other) const { return other->clone(); }

   friend std::ostream& operator<<(std::ostream& os, const Derived1& der)
   {
      os << "I'm a Derived1 object with attr = " << *der.attr;
      return os;
   }

private:
   int* attr;
};

class Derived2 : public Base
{
public:
   Derived2(int val) : attr(new int(val)) {}

   Derived2(const Derived2& other) : attr(new int(*other.attr)) {}

   virtual ~Derived2() { delete attr; }

   virtual Base* clone() const { return new Derived2(*this); }

   virtual Base* cloneOther(const Base* other) const { return other->clone(); }

   friend std::ostream& operator<<(std::ostream& os, const Derived2& der)
   {
      os << "I'm a Derived2 object with attr = " << *der.attr;
      return os;
   }

private:
   int* attr;
};

int main()
{
   Derived1 der1(10);
   std::cout << "REAL : " << der1 << std::endl;

   Derived1* clone1 = dynamic_cast<Derived1*>(der1.clone());
   std::cout << "CLONE: " << *clone1 << std::endl;

   Derived2 der2(20);
   std::cout << "REAL : " << der2 << std::endl;

   Derived2* clone2 = dynamic_cast<Derived2*>(der2.clone());
   std::cout << "CLONE: " << *clone2 << std::endl;

   Derived2* clone3 = dynamic_cast<Derived2*>(der1.cloneOther(&der2));
   std::cout << "CLONE: " << *clone3 << std::endl;

   delete clone1;
   delete clone2;
   delete clone3;
}

```

---

### Post by worksofcraft on 2010-11-03
> **dwhitney67 said:**
> 
Here's a working example, which I developed in haste:
...


TYVM :)

I never used dynamic_cast before, so it's good to see how it is supposed to be done. Although I think I understand how it is supposed to work, the linker is giving me a silly error message:
```

$> g++ base2.cpp
/usr/lib/gcc/x86_64-linux-gnu/4.4.3/../../../../lib/crt1.o: In function `_start':
(.text+0x20): undefined reference to `main'
collect2: ld returned 1 exit status

```
Yet I can see 'main' as clear as day in the source code :confused:

edit: Oh... ok got it now, I just had to add the usual argc and argv to main... strange I never had it complain before!

Anyway so basically dynamic_cast returns a NULL if it can't be cast to that type and then I can use assert to abort the program or I can use a throw with some kind of error class. Cool, it's better than it just doing something unpredictable with the wrong data :)

---

### Post by dwhitney67 on 2010-11-03
I've modified the code I posted earlier to keep in with the spirit of calling cloneOther() as I believe you had intended.  Note that it only works properly if one implements the virtual clone() method.

One other thing that you should know about dynamic_cast is that it will throw an exception if you attempt to cast an object reference into an illegal type.  For example:
```

#include <iostream>
#include <stdexcept>

class Base
{
protected:
   Base() {}
   virtual ~Base() {}
};

class Derived1 : public Base
{
public:
   Derived1() {}
};

class Derived2 : public Base
{
public:
   Derived2() {}
};

int main()
{
   try
   {
      Derived1  der1;
      Base*     base = &der1;
      Derived2& der2 = dynamic_cast<Derived2&>(*base);
   }
   catch (std::exception& e)
   {
      std::cerr << "Exception caught: " << e.what() << std::endl;
      return -1;
   }
}

```

---

### Post by worksofcraft on 2010-11-03
> **dwhitney67 said:**
> I've modified the code I posted earlier to keep in with the spirit of calling cloneOther() as I believe you had intended.  Note that it only works properly if one implements the virtual clone() method.

One other thing that you should know about dynamic_cast is that it will throw an exception if you attempt to cast an object reference into an illegal type.  For example:


Thanks again :)
Certainly during development dynamic_cast is beneficial but ultimately it is intended for heavy use in a graphical application where performance will affect the user's perception of the application. I'll express it without too much clutter:
[php]
// base class for all the shapes
struct shape: cs_graph::node {
	virtual bool draw_me(placement &rPosition) = 0;
}

// a polyline is a shape made of lines that connect a sequence of points
struct polyline: shape, std::list<coord> { // aggregate of points
	virtual bool draw_me(placement &rEdge);
};

// placing shapes on the screen
// The whole drawing is defined in a structured display file
// stored as a cs_graph each node is placed using an affine transform
struct placement: cs_graph::graph_iterator, affine {
	// double vtable dispatch: each cs_graph defines it's own procedure for
	// "visiting" and each shape provides it's own method(s) for such visits
	virtual bool visit() {
		return (dynamic_cast<shape *> pNode)->draw_me(*this);
	}
}
[/php]
... I suspect dynamic_cast has to scan down the vtable hierarchy of pNode to see if this really is a pointer to a shape, where as simply telling the compiler to assume it is one, would have no overhead, producing better game performance. So what I want to do is make it a compile time option whether to use dynamic_cast... oh I think I just found a legitimate use for a macro :shock:

It's a bit harder to explain why I need the clone thing but consider that the placement of a shape depends on it's parent's placement + a relative placement within that parent that comes from the structured display file... however I won't bore anyone with that (yet), because I haven't got it to work.

You see IMO sometimes one has to do proof of concept coding to get ideas straight... I can't design this kind of thing in the abstract, (I know some think they can, but I can't): I need to see the basic principle work and discover where the problems are... not too worried about details like private/protected...

---

### Post by worksofcraft on 2010-11-03
... so now I progressed to looking at the memory leak issue.

What I have is a set of linked objects where there can be multiple links to the same object AND the structure can be cyclic so... like an object can link to itself or to other objects that might in turn cyclicly link back to it.

There is even the possibility of having things that are statically allocated in there, but perhaps it's best to insist they always are on the heap and copy them if need be.

Simple reference counting isn't good enough :( Does anyone know of dependable garbage collection implementation for C++?

Hum... maybe I need to write my own. The only good thing is that all these objects derive from the same base class and they all link to each other using the same mechanism :)

---

### Post by worksofcraft on 2010-11-03
Nope premature... back to casting and cloning...
```

cs_graph.h:97: error: cannot dynamic_cast &#8216;((_cs_graphiter*)this)->_cs_graphiter::<anonymous>._cs_list::front()&#8217; (of type &#8216;struct _cs_list*&#8217;) to type &#8216;struct cs_edgelink*&#8217; (source type is not polymorphic)

```

Well no, I know that it's not polymorphic! :P
My list class is meant to be a generic and very simple doubly linked list of anything... however the things it is linking in this case **are polymorphic** and if I statically cast the pointer I can call their virtual methods... so am I supposed to statically cast it to the base class and then dynamically cast it to the one I want... seems like shutting the stable doors after the horse has bolted :confused:

---

