---
title: "What do you think of the D programming language"
date: 2007-10-14
forum: Programming Talk
---

### Post by rekahsoft on 2007-10-14
Hi all...i was just reading up on the D programming language...i had never really heard of it before..it is suposably a cleanup of C++...with some new features and a little different syntax...does anybody have any experiance with it? how often is it used? What are your opinions of it?...thanks for your input :P

---

### Post by Wybiral on 2007-10-14
Considering it's lack of use professionally and the existence of languages like Java, C#, and Objective-C. I, personally, wouldn't invest too much time into it. But I've never used it so I can't really say much about it.

---

### Post by samjh on 2007-10-15
I've only trialled it for trivial programs.

It appears to be a gentler version of C++, with some unsafe features discarded, and safer features implemented.  It is supposedly very fast and has automatic garbage collection, which is quite an interesting combination.

So far, the language is too immature to make a good judgment of it.  But give it maybe another two or three years and we will see.  It is certainly promising.

---

### Post by pmasiar on 2007-10-15
Wikipedia on [D](http://en.wikipedia.org/wiki/D_%28programming_language%29) gives [D  vs Other Languages](http://www.digitalmars.com/d/comparison.html) feature comparison.

Looks like C++ with garbage collection and other interesting ideas borrowed from more dynamic languages. About time :-) GC is very good idea, because it is extremely hard to do right by hand if you have exceptions, and IMHO GC is the reason why Java gained popularity. D Looks like Java done right. I am afraid it is not different enough for people to make the switch from Java. But maybe C++ people may switch... keeding of course :-)

D looks like notch above other the 8K+ languages wannabees. Maybe it does have a chance after all. [TIOBE](http://www.tiobe.com/tpci.htm) meaningless rank places D within top 20, which is not bad for an upstart in crowded area.

Of course "too soon to tell now", IMHO.

---

### Post by yigal100 on 2007-10-19
D is already a mature language. You can you D 1.x which is the current stable version. there's also a D 2.x which adds new features but is a moving target at the moment so not suitable for production.
INHO, D is a great language - "C++ done right".
if you want to use a language with a VM, than you should look at Scala which is the next generation of Java IMO. otherwise, you really should take a serious look at D. it contains a GC but compiles to native code which makes it hella fast, outperforming c/c++. also there are currently a few parser/lexer projects underway which would enable the use of LLVM, or other back-ends, and there's a version of gcc for d called dgcc or gdc for short.

---

### Post by Lutger on 2007-10-19
I've been using D now for some time and it's a joy to program in. It does remove or fix unsafe features from C++, but it's much more than that. It's hard to sum up such a rich language's features, i think at the moment two things stand out compared to the other C-family languages (C++, C# and Java):

1)  D adopts some ideas of higher level languages (ruby, python) in that productivity enhancing features are implemented in the core language where this makes sense. For example, one of the best things about D is it's support for arrays, slices and associative arrays. 

2) D takes the metaprogramming of C++ to a higher level, not only by implementing a much saner and powerful template support, but also has a built-in interpreter which can evaluate functions at compile time and a nice way to achieve compile-time reflection. It's also way easier to work with. 

As for maturity, while D users are still 'early adopters', there is now a stable branch and tools (IDE, debuggers) are available. It also helps that the designer of D (Walter Bright) is a compiler writer expert thus a quality implementation is available. Some people are using D in the commercial space.

Well, this post may sound a bit like a commercial for D, but it's how I think of D.

---

### Post by LaRoza on 2007-10-19
> **yigal100 said:**
> 
it contains a GC but compiles to native code which makes it hella fast, outperforming c/c++.

Really? Or is that just hype, or a way of saying it is faster than Java?

---

### Post by pmasiar on 2007-10-19
Show me person claiming that high-level system like D, with type control, dynamic arrays, high-level data types and GC can outperform manually finetuned C or C++ program, and I show you a liar.

In C or C++ you have pain of managing your data (and responsibility to not screw), and you have gain. No pain, no gain, that should be obvious.

---

### Post by dhasenan on 2007-10-19
> 
Show me person claiming that high-level system like D, with type control, dynamic arrays, high-level data types and GC can outperform manually finetuned C or C++ program, and I show you a liar.

In C or C++ you have pain of managing your data (and responsibility to not screw), and you have gain. No pain, no gain, that should be obvious.


D is faster than Java, hands down. It's about par with C++ for most things. Garbage collection is more reliable than manual memory management much of the time, but in certain portions of your code, it'll be a possible bottleneck. In those situations, D allows manual memory management; so in the worst case, you write D without bothering about a garbage collector. Which is a bit of a pain to do throughout a large application, but in performance-critical sections, it should be okay. And as long as you don't allocate memory using the garbage collector inside your performance-critical sections, the garbage collector shouldn't be invoked at all.

One of the great things about D, in my opinion, is that you get pretty much of the features of C#, which is a great language, but then you also get to do a lot of compile-time stuff. I have found a few situations in C# where I wanted to do some compile-time hackery (getting the type of a field) and there was no simple way of doing that. Of course, then there are mixins, which can save you a fair bit of code duplication; I miss them in C# on occasion.

The main things that D lacks are a good IDE (though the Descent project is changing that) and library support. While D can interface with any C library with minimal fuss, native libraries can sometimes be hard to come by.

As for more dangerous features of C++ discarded, the only one was multiple inheritance, that I can recall. Java discards most dangerous features of C++, and makes it difficult to shoot yourself in the foot. D, on the other hand, makes it easier not to shoot yourself in the foot, by providing simpler syntax for safe operations than for unsafe ones.

---

### Post by simhau on 2007-10-19
I’ve been using D for some time now, and I have to say I’m really enthusiastic about it.

It has a _very_ clear and nice syntax, garbage collection, compile time reflection, templates (done right!), compile time functions etc. etc.
It’s all the little things you’ll love right away. Coming from a background of mostly C, C++ and some high level languages like Python I have to say that D has combined them in a good way. The thing I miss the most from higher level languages is runtime reflection, but that’s scheduled for the next release (D 2.0).

With D, productivity will go _way_ up compared to C++. There are however several shortcomings as it’s a very young language.
There are two runtime libraries that’s more or less a standard. These two is not yet compatible, although it’s being worked on. There are still few libraries, but as D easily can connect to C that’s not the biggest problem. Many of the tools are immature. IDE support is not yet the greatest. Debugging is not perfect.

These issues are quickly being fixed, and the language itself is mature enough for production use.

As I’ve pointed out, there are some issues that has to be fixed before D can enter the mainstream arena, but I’m betting that this will happen very soon. The community exists of a lot of brilliant people, and Walter Bright (the language designer/compiler writer) is very active in the community and asks for feedback on new features.

D is still for early adopters, but I recommend everyone to try it out and get hooked! And if you’re not convinced, check out the alpha release of the 2.0 version.

I think learning D now will be like learning Java when it first appeared.

---

### Post by Lutger on 2007-10-19
> **pmasiar said:**
> Show me person claiming that high-level system like D, with type control, dynamic arrays, high-level data types and GC can outperform manually finetuned C or C++ program, and I show you a liar.

In C or C++ you have pain of managing your data (and responsibility to not screw), and you have gain. No pain, no gain, that should be obvious.

But it isn't obvious. At the moment, I don't think the D implementations clearly outperform C++, but it's on par. It has the potential to outperform them though. 

Type control: What do you mean by this? 

Dynamic arrays: In C++ you use std::vector or some handtuned container if you have a very specialized requirement perhaps. How do you think std::vector is able to outperform a built-in array, where the compiler has more knowledge about your code? In D you can iterate over arrays with 'foreach(value; array) /*blah blah*/', the compiler can optimize this. Of course you can finetune too, but it isn't unreasonably to think that most of the time, the compile does that better than you. Same goes for associative arrays.

Garbage collection: again you can finetune D here too. Unlike Java and C#, you can sidestep the GC and manage memory yourself. Yet, in certain situations, GC can outperform manual memory management.

As you see, D can be as finely tuned as C or C++. I don't think the assumption that just because something is easiest to code it must be slower is a valid one. And don't forget you can have pain for gain in D as well, all the way to inline asm. It's much closer to C / C++ than Java and C# in this aspect.

---

### Post by 0ffh on 2007-10-19
> **pmasiar said:**
> Show me person claiming that high-level system like D, with type control, dynamic arrays, high-level data types and GC can outperform manually finetuned C or C++ program, and I show you a liar.

In C or C++ you have pain of managing your data (and responsibility to not screw), and you have gain. No pain, no gain, that should be obvious.

It may look like this at first sight, but consider:
D is a compiled language very much like C or C++, complete with all the hardcore low level stuff such as pointers and pointer arithmetics. Anything you could possibly "manually finetune" in C/C++ you can also in D.
The difference is that you don't have to do any of the memory management stuff because auf the garbage collector. That has two main consequences:
1. It saves you tons of time and hassle debugging your memory management.
2. It has been shown that a good GC is mostly faster than even good explicit memory management.
And be frank, many people are quite happy when they have their MM working at all, they will seldom take the time to make it really fast and efficient. It's a bit like Greenspuns 10th rule.... :)

Conclusion: Yes, the D language DOES actually outperform C/C++ for many applications.
Reservation: Of course it depends on the application and the actual concrete source code and your compiler.

Regards, Frank

---

### Post by JarrettBillingsley on 2007-10-19
For a somewhat contrived example of D's speed, you can check out the benchmarks at [The Computer Language Benchmarks Game](http://shootout.alioth.debian.org/).  You can see how the standard D implementation, DMD, compares to other languages.  GCC and G++ come in first and second, DMD comes in a close third to both in virtually every test.  There are also reports of the output of GDC (uses the GCC backend) being faster than DMD.

But really, even if it's 5-10% slower than C or C++, I'd much rather use D than either because you know what?  I don't want to have to spend all of my time managing memory.  A 10% performance decrease, especially on today's computers, doesn't mean much.  OMG, my program could be running as if it were on a 2.4GHz machine but instead it's only running as fast as on a 2.16GHz machine, sorrows upon sorrows.  

And execution speed isn't the only plus: compilation speed with D is phenomenal.  I can use heavily templated code and it will compile in a matter of two or three seconds at the longest.  It's not uncommon to compile all the bits of the standard library you're using every time you compile your program because it's just so damn fast.  Things like keeping around object files after a make don't really make sense when they might be shaving half a second off your compile time.  

And yes, D can be used to do low-level high-speed stuff.  It's basically a semantic superset of C: anything C can do, D can do too (although sometimes with slightly different syntax).  My friends and I are writing an x86-64 exokernel with D.  At this level we don't have any GC or even the concept of virtual memory yet, so we're using it kind of as "C with templates".  What's nice is that we can then scale up the language runtime and our programming capabilities as we get higher on the abstraction ladder, instead of having to rely on different languages to get things done.

---

### Post by pmasiar on 2007-10-19
> **dhasenan said:**
> D is faster than Java, hands down. 
Being faster that java is not same thing as faster than C, as yigal100 claimed, or is it?

> Garbage collection is more reliable than manual memory management much of the time, 

Always. GC is always more reliable. If human makes no mistakes, is as reliable as GC, but not more.

> but in certain portions of your code, [GC]  be a possible bottleneck. In those situations, D allows manual memory management; so in the worst case, you write D without bothering about a garbage collector. 

Nice trick. I wonder how many real-world programmer would be able to see difference and use it properly, but it is cute feature.

But I do not think it is a problem for programmers who need performance, to write parts of the code in C (which they already know) to get top performance, and parts in Python to get the simplicity, and link them together. D bets that this linking is a problem, and provides language which tries to be equally competent in both areas. I think it is not possible, and waste of efforts, you like it. Time will decide.

---

### Post by Quxxy on 2007-10-19
> **pmasiar said:**
> > Garbage collection is more reliable than manual memory management much of the time, 

Always. GC is always more reliable. If human makes no mistakes, is as reliable as GC, but not more.

This isn't actually true at the moment.  D uses a conservative GC that does not have complete type information available.  This means that the GC will sometimes not collect memory if there is something that could be pointing at it.

Simplest example of this: imagine a struct that contains a pointer and an int.  Because of the presence of the pointer, all instances of the struct will be marked as having pointers.  So anything the int field "points" to won't be collected.

> **pmasiar said:**
> > but in certain portions of your code, [GC]  be a possible bottleneck. In those situations, D allows manual memory management; so in the worst case, you write D without bothering about a garbage collector. 

Nice trick. I wonder how many real-world programmer would be able to see difference and use it properly, but it is cute feature.

It's not just cute; the ability to manually manage large allocations is incredibly useful.  But you are right; it's up to the programmer to realise the need for it, and apply it correctly.  Same with anything.

> **pmasiar said:**
> But I do not think it is a problem for programmers who need performance, to write parts of the code in C (which they already know) to get top performance, and parts in Python to get the simplicity, and link them together. D bets that this linking is a problem, and provides language which tries to be equally competent in both areas. I think it is not possible, and waste of efforts, you like it. Time will decide.

Well, their knowledge of C will translate pretty easily to D.  I've shown a number of C programmers D code, and they've not only been able to understand it with at most a few hints, but they usually end up remarking how certain things look better in D than in C.  Just today, I had someone comment that arrays in D were how C should have done them in the first place.

Also, keep in mind that we have [PyD](http://dsource.org/projects/pyd) which makes writing Python extensions a breeze in D, that we can link directly to C code and that the latest 2.0 series compiler can link to certain C++ constructs.  AFAIK, D is the only* language apart from C++ that can link to C++ code.

* Excluding languages that are designed to compile down to C++ source, then to native code.  I mean, that's basically just cheating!  :)

---

### Post by pmasiar on 2007-10-19
Well, if D can be replacement of C, I would say: it is about time, C is 35 years old! If we did not learned anything during this time, we did not pay enough atention.

Having C with GC will be a great win, even if GC is not perfect, as you mentioned. I also can see point why having one language with "lazy" and "strict" memory management is interesting: you can push parts of your code to "strict" area piece by piece, without too much pain.

I'll be ready to swich to D the same second you persuade Linus to switch! :-)

---

### Post by LaRoza on 2007-10-19
I am now interested in D, and have added it to my wiki.

For those of you who do use D, in Linux, Windows or Mac, please look at what I have in the Wiki, and if you have any comments or suggestions, let me know. Thanks.

(I have not tried it yet)

---

### Post by aks44 on 2007-10-19
> **Lutger said:**
> Dynamic arrays: In C++ you use std::vector or some handtuned container if you have a very specialized requirement perhaps. How do you think std::vector is able to outperform a built-in array, where the compiler has more knowledge about your code? In D you can iterate over arrays with 'foreach(value; array) /*blah blah*/', the compiler can optimize this.

std::vector, like most of the C++ STL, is expanded inline. The compiler can and does apply exactly the same optimizations as if it was a builtin dynamic array.


> **pmasiar said:**
> In C or C++ you have pain of managing your data (and responsibility to not screw), and you have gain. No pain, no gain, that should be obvious.
> **JarrettBillingsley said:**
> But really, even if it's 5-10% slower than C or C++, I'd much rather use D than either because you know what?  I don't want to have to spend all of my time managing memory.

Manual resource management is very seldom in decent C++ code. Anyone claiming the contrary should read about RAII & smart pointers. As a bonus, RAII is just as performant as fine-tuned manual management, and beats the hell out of any GC anytime.



Back to the topic, the little I know of D looks interesting, since it seems to have solved many quirks of the C++ syntax. But it's way too young and unsupported for me to use it on a professional basis. Plus I'm far from convinced that removing multiple inheritance is actually a sane decision. Just because most people misuse multiple inheritance doesn't mean that it's a bad feature when properly used. YMMV.

---

### Post by rekahsoft on 2007-10-19
hm...thanks for the info everybody...very interesting for sure :P...perhaps i will add it to my list of languages to learn :D :P

---

### Post by yigal100 on 2007-10-19
to answer pmasiar's question:
in general automated memory management is almost always better than hand-tuned one. there are a lot of optimizations that can be done and most of the time manual MM just gets in the way.
for application programming the benefit of such an approach is near zero, and just not worth the effort due to amdhal's law. 
the only place that GC isn't suitable is real-time, but in real-time applications the memory is allocated in advance due to the fact that memory allocation is unbounded.
as others have mentioned, the use of a GC is optional in D and could be replaced with other memory policies, and there's also an API to control the GC so you could just stop the GC in your critical sections.
IMHO there isnt any use-case where a manual MM would be any better than a GC.

also the claim that a lower level language performance  is alway better than a high level one is an urban myth, otherwise we'd be still using assembly.
in fact the more high level a language is the better its performance can be. C++ is faster than C, and python with an aggressive optimizer is known to outperform C++ in many cases. optimization algorithms and techniques are better than any human fine-tuning. 

you can see that in c++ too: there are a few language features such as the register and inline keywords that have been deprecated as they interfere with the compiler optimizations and are considered harmful.

D allows low level programming which is needed for systems programming such as writing a kernel. besides that it's a very high level language and is on the same level as python and ruby as it borrows concepts from them. in my book that means that compiler optimizations and other techniques would give me more performance than I'd get with using C++.

Although the GC has a few rough edges, it is being currently being worked on and when the language matures further it'll be even better (performance wise) IMO.

---

### Post by KyleFurlong on 2007-10-19
> **aks44 said:**
> std::vector, like most of the C++ STL, is expanded inline. The compiler can and does apply exactly the same optimizations as if it was a builtin dynamic array.





Manual resource management is very seldom in decent C++ code. Anyone claiming the contrary should read about RAII & smart pointers. As a bonus, RAII is just as performant as fine-tuned manual management, and beats the hell out of any GC anytime.



Back to the topic, the little I know of D looks interesting, since it seems to have solved many quirks of the C++ syntax. But it's way too young and unsupported for me to use it on a professional basis. Plus I'm far from convinced that removing multiple inheritance is actually a sane decision. Just because most people misuse multiple inheritance doesn't mean that it's a bad feature when properly used. YMMV.

A few quick points. Walter Bright (author of D) read this thread and commented that he has a benchmark of RAII in C++ vs. GC in D, and you can find it here, [http://www.digitalmars.com/d/cppstrings.html]("http://www.digitalmars.com/d/cppstrings.html")

Also, what is the measure of "young and unsupported?" Have you been to the D newsgroups? dsource.org? Seen the tiobe ranking? Looked at the Tango project?

There is a large and growing community that uses D regularly, both for hobby and professional tasks. You can stop by #D on freenode, and chat with many of them there. (Last time I checked)

My personal opinion is that its just a matter of time for D adoption, C++ is only getting worse, with language bloat and incomprehensible interactions between features. Soon it will take a Ph.D just to write a library.

As always, this is definitely a controversial subject, and many people love C++ for the power it gives, so YMMV indeed. :grin:

---

### Post by Fbot1 on 2007-10-19
Way better than C=C+1 but not as good as C IMHO. Also, GC,compilers,ect are not _always_ better than the human coder. They're only ever going to be less sophisticated then the programmers.

---

### Post by Wybiral on 2007-10-19
> **KyleFurlong said:**
> ... Also, what is the measure of "young and unsupported?" ...

... C++ is only getting worse, with language bloat and incomprehensible interactions between features. Soon it will take a Ph.D just to write a library. ...

It's "young an unsupported" because it's rarely (if ever) used in the professional world. There may be a couple of projects using it, but how many jobs will knowing D get me? Name four or five companies that are looking for D developers right now. What incomprehensible interactions are there between C++ features? How is it getting worse?

---

### Post by dwhitney67 on 2007-10-19
I don't... that is, I don't think anything about the D programming language.  Should I??

---

### Post by hohums on 2007-10-20
> **aks44 said:**
> 
Manual resource management is very seldom in decent C++ code. Anyone claiming the contrary should read about RAII & smart pointers. As a bonus, RAII is just as performant as fine-tuned manual management, and beats the hell out of any GC anytime.


It is true that manual resource management can be done faster then GC if your willing to spend hours with a profiler figuring out page misses ext...  

However a first class GC (and D doesn't have a first class GC) can perform better then standard C++ RAII or reference counted GC (ie boosts smart pointers). 

Lets look at an example:

class B
{
~B() { delete ect... }
}

class A
{
...
B b = null;

~A()
{
    delete B;
}

}


...

A* a = new A[100];

delete [] a;

This example is terribly inefficient with the standard C allocator because it can't remove allocations in blocks.  It has to traverse the entire tree and delete each piece individually.   In C++ to get around this you could.

A) Allocate from a pool.  This can still be slower and less conservative then a GC because your pools are probably per item, not grouped together in a massive pool that can be remove blocks with a couple of writes.

B) Install Ned Alloc which does this kinda thing.  Still the deletions could be all over the place, not one after.  So you would have to very careful to make sure that when you delete, you delete at the same time and in the order that the objects are allocated, so ned can block deallocate better.  Also you would have to do it during times when the program was idle (waiting for a resource to become available load or something).

In my option getting the above optimized correctly to step around page misses and whatever else  in an attempt to beat the GC at something that doesn't happen to often, in a generally well written app is simply madness.

With many GCs you (on average), only pay for the deletion cost when you flush the GC.  Allocation costs are similar to that of a c malloc (some are faster like C#'s stack base GC). 

Lets take boosts smart pointers as an example:

class A
{
   boost::shared<B> b;
...
}

When B is allocated it must update a ref count.  A mark&Sweep GC would not have to do that but may have to indicate what type of data B is (some GCs do this at the beginning of the array rather then per item so the time overhead is less then that of reference counting).

The flush cost.  While the GC can delete many objects in blocks which is generally faster then C, figuring out what memory sections to delete can be expensive if not highly tweaked.  A first class GC implementation would rarely, if ever need to do a complete flush and in those cases the GC is faster then a hand tuned C++ one (unless they essentially write the code in a way that I indicated above).

Note: D doesn't have a first performance GC yet, but as others have said.  You can work around it or replace D's.

I hope that was useful.

---

### Post by aks44 on 2007-10-20
> **KyleFurlong said:**
> Walter Bright (author of D) read this thread and commented that he has a benchmark of RAII in C++ vs. GC in D, and you can find it here, [http://www.digitalmars.com/d/cppstrings.html]("http://www.digitalmars.com/d/cppstrings.html")

Having read it, all I can say is that there's no big news.

All points before the "Value vs Reference" point just exhibit syntax differences.

The "Value vs Reference" point itself is basically stating that water is wet, and that D has different design decisions than C++. WTR to string management, granted it is more efficient, but also way less safe IMHO. If COW is not automated (and it seems from the article that it is not, indeed) then the consequences are: either more code clutter, or *incorrectness* (not worse performance, mind you), choose one.

When it comes to the benchmark, the comparison between D and C++ code already shows, without even looking at the results, that the C++ code doesn't have anything in common performance-wise with the D one. The benchmark claims to "compare Apples and Apples" but what it really does is compare apples and oranges.
Honest, I was horrified when I saw the C++ "equivalents" of the D code, they are not the correct way to perform that task in C++.

> **c.l.c++.m (wccpp1)]> Would you like to write an equivalent in C++ using string, map, etc., for
> comparison?
Although I don't like your program ( it's rather C then C++ way ),
it wasn't too complicated to translate your program **word-for-word** to C++[/QUOTE]

So yeah, that benchmark managed to show at least one thing: directly transposing *apparently* similar concepts from one language to another without even thinking only leads to crappy code.


[QUOTE=KyleFurlong said:**
> Also, what is the measure of "young and unsupported?"

Show me that D has 10% as much resources available as C++, and it will barely begin to be "supported" IMO. And as Wybiral put it, is there a single company (apart from Digital Mars) that would hire me for knowing D?


> **KyleFurlong said:**
> My personal opinion is that its just a matter of time for D adoption, C++ is only getting worse, with language bloat and incomprehensible interactions between features. Soon it will take a Ph.D just to write a library.

Only time will tell. IIRC I already heard those arguments in the Java vs C++ war...



> **hohums said:**
> <snipped long GC evangelisation>

This kind of discussion is so old it's not even fun anymore.

What you don't seem to take into account is that in real life situations, there are very few cases where you can free memory "by blocks" without an afterthought. You almost always need to update data structures, etc...

RAII combines both "resource finalization" and "memory release" semantics.
GCs provide the latter, but only partially the former (and in a non-deterministic way, moreover).

So, again comparing apples and oranges. Hell, is it that hard to realize that memory is not the only resource out there (files, sockets, database connections, ...)?

---

### Post by KyleFurlong on 2007-10-20
> **aks44 said:**
> 
Show me that D has 10% as much resources available as C++, and it will barely begin to be "supported" IMO. And as Wybiral put it, is there a single company (apart from Digital Mars) that would hire me for knowing D?

[http://www.tiobe.com/tpci.htm]("http://www.tiobe.com/tpci.htm")

"The TIOBE Programming Community index gives an indication of the popularity of programming languages."

C++ = 9.584%
D = 1.594%

% Popularity of D WRT C++ = 16.6%

In addition, C++ has a 16 year head start on D, 1983 vs 1999.

I was hired two summers ago to work for ATT for an internship. I listed D as one of my proficient languages, and the interviewers had many questions and were quite impressed with it.

I asked later what one of the main reasons they hired me was, and my boss said they enjoyed seeing a candidate with so much breadth.

> **aks44 said:**
> 
Only time will tell. IIRC I already heard those arguments in the Java vs C++ war...


D is fundamentally different. Java is VM-based, write once run anywhere. D, like C++, is targeted for systems programming, write once, compile everywhere.

Java will always have a set of users who dont even know C++, because it targets a much different set of problems.

D targets the same problem space as C++, and IMHO does so with better grace.

The reason D users are usually so adamant about supporting the language, is that its just a joy to use. The syntax is natural for a C++ user, everything is well thought out, cohesive, and rational. Where design decisions have non-trivial answers, the practical approach, rather than the esoteric approach is taken.

This is another case of try it before you knock it. If you code something in D, you'll notice the difference immediately.

Then again, some people have been coding in C++ so long, that maybe the D way will seem ugly. But if you'll excuse me for saying so, thats like someone who's been eating twinkies all their life rejecting fine french cooking because they've come to love twinkies.

---

### Post by LaRoza on 2007-10-20
> **KyleFurlong said:**
> Just  But if you'll excuse me for saying so, thats like someone who's been eating twinkies all their life rejecting fine french cooking because they've come to love twinkies.

Is there an installer for the D compiler for Windows, and a .deb or repository for Ubuntu/Debian?

---

### Post by KyleFurlong on 2007-10-20
> **LaRoza said:**
> Is there an installer for the D compiler for Windows, and a .deb or repository for Ubuntu/Debian?

Walter Bright (creator) doesnt believe in installers, but there are a few community projects which help get it on your system.

My personal preference is Tango's installer. (Tango is a community driven  standard lib, akin to boost)

[http://www.dsource.org/projects/tango/wiki/DmdDownloads]("http://www.dsource.org/projects/tango/wiki/DmdDownloads")

Or if you prefer to use pure FOSS:

[http://www.dsource.org/projects/tango/wiki/GdcDownloads]("http://www.dsource.org/projects/tango/wiki/GdcDownloads")

An option on Windows, if you dont like zip files,  is this project:

[http://www.dsource.org/projects/dinstaller]("http://www.dsource.org/projects/dinstaller")

---

### Post by larsivi on 2007-10-21
> **LaRoza said:**
> Is there an installer for the D compiler for Windows, and a .deb or repository for Ubuntu/Debian?

As already mentioned, there are various installers out there. Note that the Windows with DMD from Tango is currently un-mantained.

As for .deb's, GDC is in Ubuntu's universe, at least in latest releases, Debian's unstable. I believe Tango is on it's way in there too.

To those requesting commercial use of D, I believe there are few open positions requesting it specificially, although I have had a short term contract where D was a requirement. I _do_ know of several commercial projects where D has been used, but none have involved hiring people from the open market.

FWIW, the university in Torun, Poland, will start a D course next semester, which I myself find a strong statement. It was initiated after a student project showing extremely good results after using D.

---

### Post by brianhsu on 2007-10-27
> **pmasiar said:**
> Show me person claiming that high-level system like D, with type control, dynamic arrays, high-level data types and GC can outperform manually finetuned C or C++ program, and I show you a liar.


Here is the benchmark from Computer Language Benchmark Game:

1.[D is slower than C.]("http://shootout.alioth.debian.org/debian/benchmark.php?test=all&lang=gcc&lang2=dlang")

2.[D is a little bit faster than C++ sometime and use less memory than C++.]("http://shootout.alioth.debian.org/debian/benchmark.php?test=all&lang=gpp&lang2=dlang")

3.[D is faster than Java and use less memory.]("http://shootout.alioth.debian.org/debian/benchmark.php?test=all&lang=java&lang2=dlang")

4.[D is much faster than high-level script language like Ruby/Python which also support dynamic length array/associative array .]("http://shootout.alioth.debian.org/debian/benchmark.php?test=all&lang=python&lang2=dlang")

---

### Post by LaRoza on 2007-10-27
> **brianhsu said:**
> Here is the benchmark from Computer Language Benchmark Game:
[/URL]

Interesting. (it doesn't disprove pmasiar challange, but it shows that D has a a future)

I have a feeling if "coding time" were a part of this, D would go down in rankings and interpreted dynamic typing languages would go up.

---

### Post by brianhsu on 2007-10-27
After finished this thread, I found that seems nobody metion about programming by contract and unittest are bulit-in feature of D language.

I think it is also interesting features that D has. I found that they really help me debug my algorithm homework much easiear/faster and I don't have to install 3rd party tool like JUnit when I use Java.

And here is my experience about D:

I'm a teaching assistant in a course of data structure and algorithm, and our professor use Java to implement algorithm. I also learned Java at universtiy and find it is useful and much simpler than C++.

But in other hand, I really hate VM. Using Java, I still have to compile Java source code but could not get excutable file, I have to download about 35MB SDK/JavaVM to writing and run a simple Java program like binary search or something like it.

Using D/Tango, I just download and uncompress a zip file about 2 or 3 MB, and I could start to coding algorithm example program and get excutable file which could directly run on every Windows XP.

Compare to Java, I also find although D provide lots of bulit-in feature that Java colud also achived, but the sytanx of D is much clean and beautiful than Java.

For example, when you need associative array or dynamic array in Java, you colud use Vector or Hashtable, but you can't use [index] to access a element in Vector.

But in D, dynamic length array and assocative array are just array. You colud change the length of array and still use [index] to access elements in dynamic length array.

For me, Java is too strict(no pointers, no operator overloading...) and C++ is too complex, I think D is a blance between Java and C++.

I also found that when I writting algorithm example using D, its more productive.

I colud use dynamic array and associative array and I don't have to write every try/catch block or add so much trows keyoword after function prototype. And I still got a reliable program since I could use contracts and unittest to check weather my program is correct or not.

IMHO, programming in D is really intersting and comfortable.

---

