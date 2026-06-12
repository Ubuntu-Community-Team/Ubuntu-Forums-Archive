---
title: "Java Vs C++ Speed"
date: 2008-11-15
forum: Programming Talk
---

### Post by Kilon on 2008-11-15
I came across a benchmark which I think it may interest alot of people for the folowing reasons:

1) It tests the stereotype that "C++ is much Faster than JAVA" 

2) Uses a a very recent high-tek hardware (Core2 Quad Q6600 running at 3.15 GHz, with 6 GB DDR2 SDRAM in dual-channel configuration running slightly above 800 MHz, with Nvidia 8800 GTS 640 MB graphics card)

3) the benchmark runs on Linux 

4) it uses very recent builds of C++ and Java 


For me Java speed is not that trivial or important , but of course is something that interests me cause I always want to know what each language has to offer . 

The benchmark explains in what cases Java can be faster than C++ . It opens a discussion for useful optimization where it is truly needed. 

Enjoy

[http://zi.fi/shootout/](http://zi.fi/shootout/)

---

### Post by drubin on 2008-11-15
Thanks

Java is not as slow as it used to be. It is also only slower at starting up because of the VM but once it is running the speed difference is trivial.

---

### Post by cl333r on 2008-11-15
For a full picture I'd suggest to take into consideration the memory overhead and startup time too.
That's the main reason why being a Java developer I started learning C, not because of the overall runtime speed.

---

### Post by CptPicard on 2008-11-15
My main breadwinner (in a very literal sense) is a betting analysis toolkit that runs through really huge numbers of potential combinations of results and runs expected risk/reward analysis on them. Speed is quite adequate. Also, Java threads are easy... because the problem is easily divisible into separate chunks, development of multicore-leveraging algorithms is much more convenient in Java.

One very important point to remember in writing high-performing Java is not to spam objects around. Allocate what you need, then try to be stable with that. Preferably reuse objects. The JIT compiler is good, most slowness of Java comes from a lot of calls to "new", which implies a need to GC a lot.

The memory overhead is an issue admittedly if you consider the possibility of running many Java applications at once. For this there really needs to be some sort of JVM sharing which in turn probably requires some kind of OS integration... difficult stuff.

---

### Post by cl333r on 2008-11-15
Sharing the same JVM is implemented for applets running on windows starting from java 6 update 10. As usually important kudos go to windows only.

---

### Post by Cracauer on 2008-11-15
I didn't go through all the code, but in general, there are two aspects here that throw language benchmarks off:

1) C++ needs a stronger programmer to do everything right. In particular you need to control template bloat by switching to a one-expansion-works-on-pointers-to-various-types mechanism at the right time, you need people who know how to use stack allocation at the right time.

2) The major problem with pretty much all language benchmarks (as I said, I haven't read all the code for this one) is that it's simple enough that Java's main weakness can be avoided: collections is Java can't contain user-defined data types (structs) without additional pointer indirection.


Consider this C++ code:

```

struct baz {
  int one;
  int two;
};
void foo(void)
{
  struct bar {
    struct baz blah[2];
    int bang;
  } mydata[42];

  // code munching on mydata
  // [...]
  // no free of GC required, all stack-allocated
}

```

In C++ these arrays of user-defined structs, even nested one, are stored inline, with no pointers in between. That's a huge advantage both space-wise (64 pointers are nasty big) and cache wise, because your pointer indirection blocks one more cache line. That hurts.

This example also shows stack allocation of structs, something that Java doesn't have either. That's less of a factor, let's concentrate on placement. But stack allocation is MUCH faster in many sitations. You really want to avoid allocating on the heap where you later need to GC.

Here is what you would get in Java (C syntax):
```

struct baz {
  int one;
  int two;
};
struct bar {
  struct baz *baz;
  int bang;
};
void foo(void)
{
  struct bar *mydata = new bar[42]; // array of 42 pointers in Java
  for (int i = i; i < 42; i++) {
    mydata[i].baz = new baz; // 42 more pointers inside require in Java
  }
  // code munching on mydata
  // [...]
  // GC or manually free all this junk on the heap
}

```

Lotsa pointers, lots heap allocation. If you have 32 bit ints and 64 bit pointer the above structure is 840 bytes in C++ and 1512 bytes in C++. You wasted space by nearly a factor of 2, and that doesn't account for more data used in memory allocation mechanisms.

Ok.

WAKE UP!

The point I'm going to make about all language benchmarks I have see so far is that they are simple enough that they *do not use or don't have to use collections of user-defined data types*.

You see, you can fix the problem with allocation in Java. You just don't use structs. You split up the structs above into arrays of plain int, like this (C syntax):

```

void foo(void)
{
  int ones[84];
  int twos[84];
  int bangs[42];
  // code to munch on it that now directly access the above
}

```

This is being allocated with no pointers in Java, and it's even stack-allocated.

Performance problem: solved. 

Maintainability: ruined.

But you see, if you are writing a language benchmark, it is simple enough to do the above headache. And you never have to maintain it, it's not that people would even notice bugs in the first place.

%%

This is, precisely, why Java looks pretty good in language benchmarks, is bearable in scientific computing (where large arrays of plain numbers are common) but completely breaks down for complex systems.

---

### Post by CptPicard on 2008-11-15
Good observations, but some commentary...

> **Cracauer said:**
> collections is Java can't contain user-defined data types (structs) without additional pointer indirection.

Well, ok, I give this for as long as you are simply using something that reduces nicely to structs that serve as value types and that you handle as pretty much straight values.

For a more complex object inlining your object into a collection brings up the usual "rope you can hang yourself with" of C++ of having to know exactly how to manage object internals, when temporaries are made, to be really aware of the fact that you have a value copy in your collection and another value copy perhaps on stack... at that point I usually just give up and have a collection<sometype*> :)

>  but completely breaks down for complex systems.

Depends on your meaning of complex... it is my feeling that when system becomes more and more complex, you will want to make sure your language platform helps you manage the complexity, and in a complex system you can usually afford to dedicate resources to that, too.

In particular, a "complex" system these days tends to span multiple machines, and Java is great for that.

---

### Post by Cracauer on 2008-11-15
"Complex" == lots of code, and the code can't be "properly" separated into modules that are entirely independent (e.g. by a RPC mechanism or some other broker). Typically these are high performance systems (if performance is not a concern you can use a broker, in practice that usually ends up a SQL database and your "structs" are rows in a table).

But if you have complexity *and* high performance requirements it means that messing with a data structure in code piece A requires you to also make changes to B and C, because you don't have a broker and both access the same binary data.

Now, if you do not use "structs" or "classes" or whatever your abstract data types are called you end up in a nightmare, because instead of dangling from one detected syntax error to the next when changing B and C you'll now see B and C happily compile and do something bogus at runtime. *This is why structs have been invented in the first place.*

My point is, strict performance requirements in Java (such as in benchmarks that show that Java isn't slower) break away from this.  I have just read some of the code used in this thread and in fact I see lots of arrays of ints and no complex hierarchies of user-defined data structures. It's OK here because it's mostly semi-simple scientific calculation.

But in general (and for more complex systems), I don't think that anybody would have argued that doing away with "structs" (or classes or whatever you call them) can possibly be a good thing.  But it is, precisely, what Java people do when they show us how fast their language is.

The sad part is that although the above benchmarks don't seem to use user-defined data structures, much less arrays of them, the Java code *still* falls 50% short of C++' performance. Might be improvable by playing with GC options and JITs, but that's sad.

(NOT a slam against the OP, the code presented here is perfectly adequate with simple data types. I am explaining why complex system in Java very suddenly feel like wading through half-molten rubber)

---

### Post by tinny on 2008-11-16
> **CptPicard said:**
> Also, Java threads are easy... because the problem is easily divisible into separate chunks, development of multicore-leveraging algorithms is much more convenient in Java.


My understanding is that the standard JVM will take advantage of multicore architectures, however it does quite a clumsy job of this.

Interesting reading for creating multicore enabled Java apps:
[http://java.dzone.com/news/building-multi-core-ready-java](http://java.dzone.com/news/building-multi-core-ready-java)

---

### Post by dribeas on 2008-11-16
> **CptPicard said:**
> One very important point to remember in writing high-performing Java is not to spam objects around. Allocate what you need, then try to be stable with that. Preferably reuse objects. The JIT compiler is good, most slowness of Java comes from a lot of calls to "new", which implies a need to GC a lot.

In generational GCs, the kind Java uses, it is usually better to acquire new memory than reuse existing memory chunks. The cost of allocation in Java is negligible (don't remember the real number, but I believe that it was below 10 cpu instructions). The cost of GC depends only on alive objects, unreachable objects do not amount unless they have finalizers. Most objects have a short life span and never make through the first couple of GC runs.

If you artificially extend the life of objects (by reusing them) you might end up in situations where long lived objects must be updated for each young generation GC, making GC much more expensive than needed. There are quite a few articles on GC in Java and what you should not do to 'help' the GC. Google for it.

In general, short lived inmutable objects are nice, mutating long lived objects are not so nice for th GC to handle.

[http://www.ibm.com/developerworks/library/j-jtp01274.html]("http://www.ibm.com/developerworks/library/j-jtp01274.html")
[http://java.sun.com/javase/technologies/hotspot/gc/index.jsp]("http://java.sun.com/javase/technologies/hotspot/gc/index.jsp")

> **CptPicard said:**
> Also, Java threads are easy... because the problem is easily divisible into separate chunks, development of multicore-leveraging algorithms is much more convenient in Java.

If the problem is easily divisible in Java I am quite sure that it is just as easy to divide in C/C++/Python or assembler. Now, I have used threads in Java, C (pthreads) and C++ (ACE, Boost, QT threads) and there is really no difference in how the problem is solved.

In Java you must either inherit from Thread (similar to ACE or QT) or implement Runnable (equivalent to PoCo, and conceptually similar to boost and c++0x, which even lease the interface implementation away --from a point of view of java implements or C++ inheritance). In C you must provide a function callback, but, well, it is not object oriented, so there is not much more that you could do. In QT, it even goes a step forward and implements a simple thread safe messaging protocol that is transparent to the programmer (QT signals and slots are safe across thread calls while having no extra overhead if the slot and the signal are in the same thread, without any user interaction).

---

### Post by myrtle1908 on 2008-11-16
> **CptPicard said:**
> My main breadwinner (in a very literal sense) is a betting analysis toolkit that runs through really huge numbers of potential combinations of results and runs expected risk/reward analysis on them.

We talking horses here Captain?  I have written software for Australian racing (we have racing practically every day of the year here).  I find this style of statistical analysis fascinating (and occasionally financially rewarding).

/thread hijack

---

### Post by CptPicard on 2008-11-16
> **myrtle1908 said:**
> We talking horses here Captain?

Mostly ice hockey and soccer. We find horses to be a bit too "unpredictable" for what we do... there *is* a horses version of my tools, but we're not quite yet sure whether the result is dominated more by the probability estimates that we have than whatever the tool is able to contribute in edge discovery, bet sizing and associated risk management...

> 
I have written software for Australian racing (we have racing practically every day of the year here).  I find this style of statistical analysis fascinating (and occasionally financially rewarding).

Very interesting. I am actually the technical right hand guy of the biggest betting team in Finland. €30M or so played in the past 5 years or so, and best year saw a +300% gain, although that's when we also got very very lucky ;)

It's sort of interesting that we do not really do statistical analysis in order to try to predict what will happen, but instead try to find situations where the other guys are playing obviously wrong, and cover enough of all possible profitable outcomes so that eventually in the long term we end up in the black. I'm sure you're familiar with Kelly betting...

---

### Post by myrtle1908 on 2008-11-16
> **CptPicard said:**
> Very interesting. I am actually the technical right hand guy of the biggest betting team in Finland. €30M or so played in the past 5 years or so, and best year saw a +300% gain, although that's when we also got very very lucky ;)

Wow!  I'm certainly not wagering (or collecting) to anything near that level :)  I'm more of a hobbyist and use the software I have written to attempt to gain an edge (albeit small in most cases).  I had a very large win a while back where for AUD120 outlay I reaped ~85K (picked first four horses in order in the biggest race in Australia ... The Melbourne Cup).  Easily my best ever win.

Anyways, this is waaaay off topic so good luck and happy punting!

---

### Post by Kilon on 2008-11-17
I am very glad I opened this topic, I have seen some very interesting opinions and some very good ideas that I could implement to my programming. 

What strikes me in the benchmark is this

> Polymorphism

The purpose of the methcall test is to see how long it takes to make a call on a pointer on which the program needs to resolve the actual embed type runtime. Unfortunately Java apparently detects that the test does nothing and optimizes most of it away. The first half, which is supposed to do 2e9 function calls **takes no time at all**, while in C++ both halves take approximately same time, as is expected. A more complex benchmark is needed for meaningful results.

impressive stuff, I did not know that languages have became so clever. I think that this might be the future, a language that can automatically optimise your code. Blows my mind . And think that to sit here and actually talk about the possibility of Java being faster than C++ is plain nuts. There are so many things to learn, it is unbelievable the possibilities that programming can give.

---

### Post by dribeas on 2008-11-17
> **Kilon said:**
> I think that this might be the future, a language that can automatically optimise your code. Blows my mind . 

There are works in that line. Current VMs are getting to adapt and optimize the code with runtime information. First time I heard about runtime optimization was in a microprocessor anyway. Back, if I recall correctly in 1999 a company by the name of Transmeta built a family of processors (Crusoe) that was able to process x86 instructions translating into its own internal processor instructions. The processor did profiling during runtime and optimized those parts of the code that were more often run. That was a rather neat piece of hardware. But did not catch up in market trends. Only a couple of companies built laptops with those families back then and they did not sell out of Japan.

---

### Post by Bichromat on 2008-11-17
> **Kilon said:**
> impressive stuff, I did not know that languages have became so clever. I think that this might be the future, a language that can automatically optimise your code. Blows my mind . And think that to sit here and actually talk about the possibility of Java being faster than C++ is plain nuts. There are so many things to learn, it is unbelievable the possibilities that programming can give.

Compilers are becoming clever, not languages. But a language can be conceived so as to help the compiler optimize your code.

---

### Post by pmasiar on 2008-11-17
> **Kilon said:**
> I did not know that languages have became so clever. I think that this might be the future, a language that can automatically optimise your code. 

This is exactly the BS optimization: it makes code faster in a benchmark (to help win benchmark competitions) but does little to make it faster in real life: it makes harder to make meaningful benchmarks, because you cannot use some simple dummy code which compiler will optimize away, you have go to pain and really put some real code there, to figure out what the runtime cost of the code would be.

Thanks but no thanks: compile what I said my code is, don't try be smarter than me. or at least give me option to turn it off when i want to. So I can compare apples with apples, and not with bananas.

---

### Post by Cracauer on 2008-11-17
> **Kilon said:**
> I am very glad I opened this topic, I have seen some very interesting opinions and some very good ideas that I could implement to my programming. 

What strikes me in the benchmark is this



impressive stuff, I did not know that languages have became so clever. I think that this might be the future, a language that can automatically optimise your code. Blows my mind . And think that to sit here and actually talk about the possibility of Java being faster than C++ is plain nuts. There are so many things to learn, it is unbelievable the possibilities that programming can give.

This has always been the problem with toy benchmarks.

If some results to be computed aren't actually used they can be optimized away. 

In the real world it's rare (but not unknown) that this happens.

Benchmarks comparing languages are usually worse at this than normal benchmarks. Since you have to implement the same logic in several languages people cut even more corners.

---

