---
title: "C++ garbage collector"
date: 2010-11-06
forum: Programming Talk
---

### Post by worksofcraft on 2010-11-06
Many of us are aware that C++ hasn't got one, but I actually need one now :shock:

So I was thinking of using the Glib reference counter thingy... but reading the documentation seems to throw up more questions than answers:

Like:
[LIST]
[*]can I use it with objects of my own classes that I create with operator new()
[*]does it have to be something explicitly allocated from the Glib shared memory context?
[*]What about circular references where two objects refer to each other
[*]what if I want to be able to mix in objects that are statically allocated
[/LIST]
Then I read things like [http://www.demko.ca/blog/200705_gtkmm_refcoutning.html:](http://www.demko.ca/blog/200705_gtkmm_refcoutning.html:)
> 
 "... GTK+ (with it's floating reference nonsense)
has made a mess of a seemingly simple concept..."


So not really much of recommendation :(

Just wondering in anyone has experience with alternatives or whether I better off digging out my old floppy disks where I vaguely remember having once had my own working solution for this.

---

### Post by worseisworser on 2010-11-06
Always go for the floppy disks.

---

### Post by CptPicard on 2010-11-06
[http://www.hpl.hp.com/personal/Hans_Boehm/gc/](http://www.hpl.hp.com/personal/Hans_Boehm/gc/)

---

### Post by dwhitney67 on 2010-11-06
> **worksofcraft said:**
> Many of us are aware that C++ hasn't got one, but I actually need one now :shock:


If you are really at the point that you have realized that your app is poorly designed and that you need something to clean up its allocated memory but you have lost track of who owns what pointer, then consider using Boost's or TR1's smart pointers.

For example:
```

#include <tr1/memory>

typedef std::tr1::shared_ptr<int> SmartIntPtr;

class Foo
{
public:

   Foo(int val) : myData(new int(val)) {}

   SmartIntPtr data() const { return myData; }

private:
   SmartIntPtr myData;
};

int main()
{
   Foo foo(10);

   SmartIntPtr data = foo.data();   // second reference to data pointer
}
   // no leaks here! (verify with valgrind)

```

---

### Post by worksofcraft on 2010-11-06
> **dwhitney67 said:**
> If you are really at the point that you have realized that your app is poorly designed and that you need something to clean up its allocated memory but you have lost track of who owns what pointer, then consider using Boost's or TR1's smart pointers.

For example:
```

#include <tr1/memory>

typedef std::tr1::shared_ptr<int> SmartIntPtr;

class Foo
{
public:

   Foo(int val) : myData(new int(val)) {}

   SmartIntPtr data() const { return myData; }

private:
   SmartIntPtr myData;
};

int main()
{
   Foo foo(10);

   SmartIntPtr data = foo.data();   // second reference to data pointer
}
   // no leaks here! (verify with valgrind)

```

Well thanks for that link, I'll check it out in a mo :)

However I don't agree that it's a consequence of poor design. You may have gathered elsewhere that I am working with a recursive data structure. I know **exactly** where all the references are, however when I remove an instance from said structure I have no desire to go visit all the other nodes to count how many other references there are still outstanding before I can decide whether or not to delete and dispose of the allocated memory.

---

### Post by worksofcraft on 2010-11-06
> **CptPicard said:**
> [http://www.hpl.hp.com/personal/Hans_Boehm/gc/](http://www.hpl.hp.com/personal/Hans_Boehm/gc/)

Thanks for that link I'm trying it out right now :)

I see it has the ability to call object destructors and I remember there can be issues when that destructor references something that may have already been deleted :shock:

update:

./configure
make
make install
make check

all work which is a good start :)

---

### Post by worksofcraft on 2010-11-06
> **worseisworser said:**
> Always go for the floppy disks.

Sadly my floppy disk wasn't readable anymore :(

I seem to remember setting the reference counter to -1 when not constructing the object with the new operator. That way it could cope with a mixture of references to static and dynamically allocated things... it only leaked if an object had at some stage had more that MAXINT references... but I think many other reference counting systems malfunction in that case too... assuming you don't run out of memory long before that :D

---

### Post by worksofcraft on 2010-11-06
> **CptPicard said:**
> [http://www.hpl.hp.com/personal/Hans_Boehm/gc/](http://www.hpl.hp.com/personal/Hans_Boehm/gc/)

I can't get it to work with C++ atm...
It's supposed to replace the standard new and delete with it's own versions... but I'm not sure what I'm doing wrong here:
[php]
// g++ gctest.cpp -lgc
#include "gc_cpp.h"
#include <cstdio>

int gCountInstances = 0;

struct my_struct {
	int iD;
	my_struct *qNext;
	my_struct(int i): iD(i) {
		++gCountInstances;
	}
	~my_struct() {	
		--gCountInstances;
	}
} *gList = NULL;

int main() {
	GC_INIT();	/* Optional on Linux/X86; see below.  */

	for (int i = 0; i < 100; ++i) {
		my_struct * pMe = new my_struct(i);
		pMe->qNext = gList;
		gList = pMe;
	}
	printf("allocated 100, gCountInstances=%d\n", gCountInstances);
	delete gList;
	gList = NULL;

	GC_gcollect(); // explicitly do the collection

	// but it hasn't collected anything
	return !printf("deleted list head, gCountInstances=%d\n", gCountInstances);
}
[/php]

---

### Post by krazyd on 2010-11-07
> **worksofcraft said:**
> Just wondering in anyone has experience with alternatives or whether I better off digging out my old floppy disks where I vaguely remember having once had my own working solution for this.
Why not use QT?
[http://doc.trolltech.com/4.7/implicit-sharing.html](http://doc.trolltech.com/4.7/implicit-sharing.html)

also see this blog post:
[http://labs.qt.nokia.com/2009/08/25/count-with-me-how-many-smart-pointer-classes-does-qt-have/](http://labs.qt.nokia.com/2009/08/25/count-with-me-how-many-smart-pointer-classes-does-qt-have/)

---

### Post by worksofcraft on 2010-11-07
> **krazyd said:**
> Why not use QT?
[http://doc.trolltech.com/4.7/implicit-sharing.html](http://doc.trolltech.com/4.7/implicit-sharing.html)

also see this blog post:
[http://labs.qt.nokia.com/2009/08/25/count-with-me-how-many-smart-pointer-classes-does-qt-have/](http://labs.qt.nokia.com/2009/08/25/count-with-me-how-many-smart-pointer-classes-does-qt-have/)

OMG... they have 8 different types of smart pointers :shock:
and they all make sense too :)

That QT package really is very comprehensive and I have got it installed I can see I could make a whole study of garbage collection and smart pointer techniques.

I made a generator for randomly connected graphs of nodes that can include cyclic and disconnected patterns and optionally a mixture of statically and dynamically allocate nodes.

... also I did eventually manage to recover my own ancient "smart pointer" code and I messed around with it for a quite a while. I'll post it here for those who want to see for themselves how reference counting fails even with the most simple cyclic garbage link.

[php]
// g++ -DTEST cs_trash.cc
// use-counter trash disposal
#include <new>

// base class for collectable trash
struct cs_trash {
	static int gNewCount; // initial number for use counter
	int iCount; // actual number of users

	cs_trash(): iCount(gNewCount) {
		gNewCount = -1; // back to static allocation
	}
	virtual ~cs_trash() {} // will be deleteing thru the base class

	// implicitly new is a static operator
	void * operator new(size_t iSize) {
		gNewCount = 0; // dynamically allocated so make it zero references to *this
		return ::new char[iSize]; // actually allocate blank memory
	}
};

int cs_trash::gNewCount = -1; // assume static allocation

// must use this as pointer to automatically track how many uses
struct cs_smart {
	cs_trash *qTrash; // 
	void unuse(); // remove a use
	void use() { if (qTrash && qTrash->iCount >= 0) ++qTrash->iCount; }
	cs_smart & assign(cs_trash *pG);

	cs_smart & operator= (cs_trash *pG) { return assign(pG); }
	cs_smart & operator= (cs_smart & rS) { return assign(rS.qTrash); }
	cs_smart(cs_trash *pG = NULL): qTrash(pG) { use(); }
	cs_smart(const cs_smart & rS): qTrash(rS.qTrash) { use(); }
	~cs_smart() { unuse(); }
	// dereference
	cs_trash * operator->() { return qTrash; }
	cs_trash & operator*() { return *qTrash; }
};

cs_smart & cs_smart::assign(cs_trash *pG) {
	unuse(); // forget the old
	qTrash = pG;
	use();
	return *this;
}

void cs_smart::unuse() {
	if (!qTrash) return; // not allocated
	if (
		(qTrash->iCount < 0) || // static allocated
		(--(qTrash->iCount) > 0) // still referenced elsewhere
	) return;
	delete qTrash;
	qTrash = NULL; // just to be safe
}

#ifdef TEST
#include <cstdio>

// derive new class of trash
struct junk: cs_trash {
	cs_smart kill_me; // a smart linked list
	junk() { printf("junk at %p\n", this); }
	~junk() { printf("destroyed at %p\n", this); }
};	

int main() {
	junk sJ; // static junk
	junk *pJ = new junk; // dynamic junk
	pJ->kill_me = &sJ; // links to the static junk
	sJ.kill_me = new junk; // that links to more dynamic junk
	cs_smart jS = pJ; // reference by a smart pointer
	jS = NULL; // should delete j2
	// and that will try to delete j1 but find it is static
	// and so j1 and the one it points to stay till the static goes out of scope

	printf("However reference counting fails for cyclic junk:\n");
	cs_smart pG = new junk;
	// this syntax is a bit :P
	dynamic_cast<junk &>(*pG).kill_me = pG; // point to self

	return !printf(":P\n");
}
#endif
[/php]

p.s. don't you just love how my constructor knows static from dynamic allocation :D However remember it's not the internals of library code that matter, it's teh api... which is here used in the little TEST program at the end.

---

### Post by worksofcraft on 2010-11-07
After I read the documenation for the boost library shared_ptr class template I expected to be able to make a simple linked list with these shared pointers and delete the head of the lsit to see all the others get garbage collected.

However IDK if it's just me being really dense here, but it just seems I can't do pointerish things with these so called pointers. The compiler doesn't like it:

```

#include <tr1/memory>
#include <cstdio>

class Foo;
typedef std::tr1::shared_ptr<Foo> SmartFooPtr;

class Foo
{
public:

   Foo() {
		printf("Foo@%p\n", this);	
	}
   ~Foo() {
		printf("deleting@%p\n", this);	
	}

   SmartFooPtr myData;
};

int main()
{
	**SmartFooPtr foo1 = new Foo;**
	return 0;
}

```

... and if you change that "Foo" to read Foo* it also don't compile.

I mean I setting a pointer to point to the new object is what it's all about isn't it :confused:

---

### Post by CptPicard on 2010-11-07
IIRC see the "reset" method. I'm not sure why it's not coded in terms of assignment operator but there are probably good reasons to that.

---

### Post by GeneralZod on 2010-11-07
> **CptPicard said:**
> I'm not sure why it's not coded in terms of assignment operator but there are probably good reasons to that.

I think that would require implicit conversions from Foo* to share_ptr<Foo>, which would be very risky: for example, a function taking a shared_ptr<Foo> as an argument would then accept a Foo* argument, in which case the Foo* argument would be *deleted* when the function returns - very probably not what the programmer intended :)

Edit:

Oh, and in case it's not clear, the idiom for initialising a shared_ptr<Foo> with a Foo* is

```

shared_ptr<Foo> foo1(new Foo);

```

---

### Post by worksofcraft on 2010-11-07
> **CptPicard said:**
> IIRC see the "reset" method. I'm not sure why it's not coded in terms of assignment operator but there are probably good reasons to that.

Thanks :)
Yes that works and it does dispose of my linked list when the smart pointer goes out of scope, so I try moving on... and well the next problem is how to explicitly unreference something (e.g like I want to remove it from said list.
```

... Foo-ish stuff as before

int main()
{
	Foo staticFoo;
	staticFoo.myData.reset(new Foo); // append dynamic instance
	Foo *pFoo = new Foo;

	pFoo->myData.reset(&staticFoo); // append static instance
	SmartFooPtr foo1(pFoo); // bung it in a smart pointer

	**foo1.reset(NULL); // delete them?**
	return !printf("about to exit\n");
}

```

With normal pointers you would call delete and then set the link to NULL in your linked list. The idea of smart pointers is that you don't have to call delete and indeed there is no method that suggests there is something for deleting, but I still need to terminate the list where the thing has been removed. In my own version I simply assign NULL to smart pointer and that then precipitates all the reference counting and disposal. However..

For me the problem seems to be with the documenation... after googling I could only find things like [http://msdn.microsoft.com/en-us/library/bb982026.aspx](http://msdn.microsoft.com/en-us/library/bb982026.aspx)

As a reference or explanation of what is what, I just don't get it :confused: Looking at the header files I'm no better off: Reams and reams of declarations identifying just about every conceivable combination *except* of course the obvious ones...

The whole thing is completely unclear where the actual reference counter is being held, but one thing that is clear from the documentation and discussions I could find on the web is that **ALL** these so called smart pointers fail for cyclicly linked data.

My test case is as follows:
From a graph of potentially cyclicly and multiply linked nodes, remove a node and "unreference" it. Any nodes that are no longer reachable from the main graph should consequently be disposed of and their destructors called.

This is a job for a *proper* garbage collector, so the most likely candidate is that one from Hans_Boehm... although I still need to get it to call my destructors and already learnt that it may malfunction if I throw exceptions :(

Failing that I have to make my own algorithm: Something like...
Keep a list of all nodes (done by constructor/destructor). I can iterate the main graph to flag the ones that are reachable. Then remove and dispose of all the ones that were not so flagged. It should be possible to make that run as a back-ground garbage collection process... however I shouldn't still have to be writing this sort of stuff in 21st century IMO :popcorn:

---

### Post by GeneralZod on 2010-11-07
> **worksofcraft said:**
> 
For me the problem seems to be with the documenation... after googling I could only find things like [http://msdn.microsoft.com/en-us/library/bb982026.aspx](http://msdn.microsoft.com/en-us/library/bb982026.aspx)


I'm not sure how much (if at all) boost and tr1's shared_ptrs have diverged, but you should definitely read this:

[http://www.boost.org/doc/libs/1_44_0/libs/smart_ptr/shared_ptr.htm](http://www.boost.org/doc/libs/1_44_0/libs/smart_ptr/shared_ptr.htm)

---

### Post by worseisworser on 2010-11-07
> however I shouldn't still have to be writing this sort of stuff in 21st century IMO

Yeah, it's odd; it's not like this stuff was solved in 1959 or something.

---

### Post by worksofcraft on 2010-11-07
> **GeneralZod said:**
> I'm not sure how much (if at all) boost and tr1's shared_ptrs have diverged, but you should definitely read this:

[http://www.boost.org/doc/libs/1_44_0/libs/smart_ptr/shared_ptr.htm](http://www.boost.org/doc/libs/1_44_0/libs/smart_ptr/shared_ptr.htm)

Thanks, I did :)
So what they suggest is to break cycles by using "weak pointers". I don't quite see the difference between a weak pointer and a regular pointer type yet... but now the problem facing creation of a link becomes how to decide whether to make it a shared_ptr or a weak pointer and even worse, when I remove a shared pointer.. how to decide which previously weak pointers should now be made into shared pointers.

One thing I do like about their implementation is that the instance pointed to can be any type and does not need to incorporate the reference counter the way I had done it. If I run out of things to do I might try fathom how they did that :)

---

### Post by worksofcraft on 2010-11-07
> **worseisworser said:**
> Yeah, it's odd; it's not like this stuff was solved in 1959 or something.

No, but back in 1995 I remember it working just fine for Java virtual machines. So why is 15 years later the C++ world still using reference counting I do wonder :confused:

---

### Post by Reiger on 2010-11-07
1959 probably refers to LISP, which was designed in 1958. C++ is built to do everything from C to LISP in a 80/20 fashion: it stubbornly refuses to compromise on either end. Or: with 20% of the effort get 80% of the pain.

---

### Post by worksofcraft on 2010-11-07
> **Reiger said:**
> 1959 probably refers to LISP, which was designed in 1958. C++ is built to do everything from C to LISP in a 80/20 fashion: it stubbornly refuses to compromise on either end. Or: with 20% of the effort get 80% of the pain.

Ah yes... I don't know any lisp but I presume they had proper garbage collection working in that language long before Java was even so much as a twinkle in the eye of an aspiring coffee bean farmer ;)

From what I gathered, a lot of people have been lobbying the C++ standards committee(s) to add garbage collection specification and so I find it weird they are still pratting about with so called 'auto pointers' and 'smart pointers'.

Part of this reluctance stems from the problem of invoking destructors of objects that may then attempt to reference objects that have already been destroyed. OTOH it should be patently obvious that if A references B and B references A then you gunna get problems with that regardless: It's not an issue for the garbage collector to solve IMO.

---

### Post by nvteighen on 2010-11-08
> **worksofcraft said:**
> No, but back in 1995 I remember it working just fine for Java virtual machines. So why is 15 years later the C++ world still using reference counting I do wonder :confused:

> **worksofcraft said:**
> From what I gathered, a lot of people have been lobbying the C++ standards committee(s) to add garbage collection specification and so I find it weird they are still pratting about with so called 'auto pointers' and 'smart pointers'.

Part of this reluctance stems from the problem of invoking destructors of objects that may then attempt to reference objects that have already been destroyed. OTOH it should be patently obvious that if A references B and B references A then you gunna get problems with that regardless: It's not an issue for the garbage collector to solve IMO.


Because people consider C++ should also be a low-level language. That's the greatest issue of C++: it's schizophrenic... It tries hard to be an "all-level" language, failing to be a good and uniform one... But no, C++ is neither low- nor high-level. C++ coders would only accept to have GC if the specs added it as an optional feature (like the STL), so that they could choose when and how to use it (because forcing people to use GC would make C++ lose low-levelness)... adding more semantic complexity to the language: some stuff will have to behaive differently depending on whether GC is or not activated...

---

### Post by worksofcraft on 2010-11-08
> **nvteighen said:**
> Because people consider C++ should also be a low-level language. That's the greatest issue of C++: it's schizophrenic... It tries hard to be an "all-level" language, failing to be a good and uniform one... But no, C++ is neither low- nor high-level. C++ coders would only accept to have GC if the specs added it as an optional feature (like the STL), so that they could choose when and how to use it (because forcing people to use GC would make C++ lose low-levelness)... adding more semantic complexity to the language: some stuff will have to behaive differently depending on whether GC is or not activated...

The simple solution would seem to me that the garbage collector only collects garbage that is derived from a base "trash" class.

---

### Post by worksofcraft on 2010-11-12
Anyway I would quite like to hear if anyone got a proper garbage collector to work with C++ because I just can't seem to get that one to work with C++. test_cpp.cc is provided with the package and without modifications IDK but I suspect it's cuz I'm running 64 bit...

```

$ g++ test_cpp.cc -I./gc6.8/include -lgc

$ ./a.out 5
Starting iteration 1
*** glibc detected *** ./a.out: free(): invalid pointer: 0x0000000000b05fe0 ***
======= Backtrace: =========
/lib/libc.so.6(+0x775b6)[0x7f33517e15b6]
... and a lot more

```
:confused:

looks like I'll have to get my "wheel inventor's tool kit on floppy disk" back out of the garage after all :P

---

### Post by interval1066 on 2010-11-12
> **worksofcraft said:**
> Anyway I would quite like to hear if anyone got a proper garbage collector to work with C++ because I just can't seem to get that one to work with C++. test_cpp.cc is provided with the package and without modifications IDK but I suspect it's cuz I'm running 64 bit...


C++ is a great language, and I find its lack of features one of its strengths; you're not locked into any particular garbage collecting library, you're not locked into any particular library at all. You can always write your own if a 3rd party offering is overkill (like boost often is).

If you're using the latest GCC compiler chain you should have access to C++ features like std::auto_ptr, which for all its faults will solve most of your problems, and you even have access to the superior std::shared_ptr with C++0x, which should be available with the latest gnu g++ updates (its as of version 4.something, I'm on Ubuntu 10.04 LTS and got the C++0x update some time ago.)

Go to google code search and look around for C++ code that does memory management. There's lots of clever code by clever people that there and there's probably a class that will do what you need.

---

