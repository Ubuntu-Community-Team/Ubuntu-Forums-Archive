---
title: "Wow, development should really be done in Python..."
date: 2007-12-19
forum: Recurring Discussions
---

### Post by kripkenstein on 2007-12-19
I just spent some time reading the source code to the gnome panel applets. In about an hour I found 4 minor memory leaks. Nothing you'd easily notice in practice - just unallocated strings. But it might explain why e.g. an applet takes 4 MB on startup and 7 MB after running for a few days.

This is exactly why development should be done in modern languages like Python. Handling all the reference incrementing/decrementing and memory allocating/freeing is ridiculous, the language can do it for you. Programming in Python with PyGTK is a lot of fun. GTK in C is quite tedious, and not only because of memory management, but also the whole object-management scheme (writing OO code on top of C).

Anyhow, sorry for the rant, but I was sort of shocked to see what kind of code has been running my desktop for the last few years. Really, Python should be the way to go for developing new apps. In fact, I feel like rewriting some existing GNOME apps in Python right now (but I probably shouldn't...).

(To be fair I guess Java and C# are also much better than C/C++. Vala also looks very interesting.)

---

### Post by LaRoza on 2007-12-19
"Better" is subjective.

C is a modern language, and is very powerful.

Are you sure that these memory leaks are leaks?

(Post a little code?)

---

### Post by bruce89 on 2007-12-19
"Modern" languages are slow, 'nuff said.

---

### Post by kripkenstein on 2007-12-19
> **LaRoza said:**
> "Better" is subjective.

C is a modern language, and is very powerful.

Are you sure that these memory leaks are leaks?

(Post a little code?)
Well, one of the leaks is confirmed, they committed my patch into svn. The other leaks are pending, but they are more of the same, so I think they are all actual leaks.

Here are the bugreports, they contain patches, so you can see what I mean:
[Confirmed memory leak]("http://bugzilla.gnome.org/show_bug.cgi?id=504435")
[Some more leaks]("http://bugzilla.gnome.org/show_bug.cgi?id=504489")

I do agree in general that 'better' is subjective. But seeing GObject/GTK code in C versys PyGTK in Python, this seems the most absolute case of good vs. bad I have seen in a long time ;)

---

### Post by Wybiral on 2007-12-19
> **bruce89 said:**
> "Modern" languages are slow, 'nuff said.

lol, maybe if your gnome applet is running some kind of massive physic simulation. Otherwise I highly doubt you will notice any runtime efficiency loss. Either way, you can always write the module in C and use Python to glue it together. Python makes for much cleaner code and works well to glue libraries together when you need to.

---

### Post by LaRoza on 2007-12-19
> **kripkenstein said:**
> Well, one of the leaks is confirmed, they committed my patch into svn. The other leaks are pending, but they are more of the same, so I think they are all actual leaks.

Here are the bugreports, they contain patches, so you can see what I mean:
[Confirmed memory leak]("http://bugzilla.gnome.org/show_bug.cgi?id=504435")
[Some more leaks]("http://bugzilla.gnome.org/show_bug.cgi?id=504489")

I do agree in general that 'better' is subjective. But seeing GObject/GTK code in C versys PyGTK in Python, this seems the most absolute case of good vs. bad I have seen in a long time ;)

Maybe they should be in Python.

---

### Post by bruce89 on 2007-12-19
> **LaRoza said:**
> Maybe they should be in Python.

Now there's a good way to lower GNOME's memory use.

---

### Post by Majorix on 2007-12-19
This is why you should write your code in Python and do the processor-intensive parts in C.

---

### Post by bruce89 on 2007-12-19
> **Majorix said:**
> This is why you should write your code in Python and do the processor-intensive parts in C.

Arg, you'll pry C from my cold, dead hands.

---

### Post by kripkenstein on 2007-12-19
> **bruce89 said:**
> Now there's a good way to lower GNOME's memory use.
Thing is, if the GNOME cpufreq applet has 4 memory leaks (that I found - perhaps there are more), then a running GNOME desktop probably has hundreds, I would guess? So that might be a lot of memory being leaked. It might actually be better to write it in Python - sure, there is memory overhead for the language, but no leaks.

I'm not saying it would be better, but that it isn't obvious that it wouldn't be.

---

### Post by Wybiral on 2007-12-19
> **bruce89 said:**
> Now there's a good way to lower GNOME's memory use.

Considering Pythons libraries are likely to already be loaded in memory, I doubt you would see much memory increase. Remember, Python itself is a C program making use of various compiled C libraries, the overhead for applications like this will be negligible.

> **bruce89 said:**
> Arg, you'll pry C from my cold, dead hands.

You can use C with Python when you need it, but only when you need it. Most applications however don't, and you lose in the development/testing/fixing memory leaks time.

---

### Post by LaRoza on 2007-12-19
> **bruce89 said:**
> Arg, you'll pry C from my cold, dead hands.

Programming languages are tools, that is like saying we have to pry a 3/8ths in wrench from your hands when we are supposed to use a metric set.

---

### Post by pmasiar on 2007-12-19
> **kripkenstein said:**
> This is exactly why development should be done in modern languages like Python. ... 

C was probably best choice back them when they started.

OLPC did made the switch, Sugar is developed in Python, and is fast enough, even if CPU is not the fastest. As always, good design and algorithm choice beats mindless low-level optimization.

C is good tool for tasks where it fits, but not the only tool we have.

> **bruce89 said:**
> "Modern" languages are slow, 'nuff said.

Modern languages are more concerned about productivity of the programmer, and let CPU to work hard to earn the wats. You can do whatever you want with your time, but my CPU is idling most of the time, so I have no problem to shift some of my workload to it.

Read [The hundred year language](http://www.paulgraham.com/hundred.html), maybe you get enlighted. :-)

---

### Post by aks44 on 2007-12-19
> **kripkenstein said:**
> In about an hour I found 4 minor memory leaks.
[...]
This is exactly why development should be done in modern languages like Python.

IMHO the problem has nothing to do with C or Python. It has to do with competent programmers vs less experienced ones.

The solution to lower the memory usage of an "*applet that takes 4 MB on startup and 7 MB after running for a few days*" (supposedly written in C at the moment?) is not to rewrite it in Python (BTW, how much memory takes the Python VM itself?) but to educate the programmer of that applet (or maybe (s)he should just give the project to someone able to handle it).


Don't get me wrong, I have nothing against Python, but I believe that anyone that lets memleaks clutter his code is probably not competent enough WRT C, and should educate himself instead of working around his deficiencies by switching to a language that hides them.


Now regarding your comment on C++... *_when will people realize that with proper C++ code you **don't** have to manage memory by hand_*? (RAII) :|


I seriously doubt that the "solution" to bad programming practices is to use huge VMs. They may take care of some details for you, but there is a price... memory occupation & a bit of speed (JIT nicely attenuates the latter though). Anyway the best durable solution is to educate people.

</rant> ;)

---

### Post by Wybiral on 2007-12-19
> **aks44 said:**
> BTW, how much memory takes the Python VM itself?

Not all VMs are memory munchers like Java :) Pythons is very lightweight and makes use of a number of shared libraries that are probably already loaded in memory. In most cases (but certainly not all) it's negligible.

---

### Post by kripkenstein on 2007-12-19
> **aks44 said:**
> 
I seriously doubt that the "solution" to bad programming practices is to use huge VMs.
Well, two things:
[LIST=1]
[*]I agree that better programmers have fewer memory leaks in C. Still, even the best can miss a few here and there. And they can program in a better way when they aren't worrying about leaks.
[*]Not all VMs are 'huge'. The reason people assume they are is that Java used to be such. But load Python right now: the VM loads up around 3 MB or RAM - that's it. Yes, there is more overhead per variable when compared to C, but the days of 'huge VMs' are behind us.
[/LIST]

---

### Post by pmasiar on 2007-12-19
JVM is presumably rather bad design: Google for Android mobile phone platform decided to develop whole JVM to avoid using original "free" JVM. One (but not only one) reasons was the Sun's JVM design I guess.

Forth's "VM" has about 4K-6K, including compiler: all you need to run Forth code on bare metal (in text-only mode, no GUI of course). In 32K, we run Pascal compiler with execution visualization and P-code VM, all implemented in Forth :-)

---

### Post by Klipt on 2007-12-19
Isn't this what [Valgrind](http://valgrind.org/) is for?

And I don't understand why people say C/C++ when programming in pure C is *very* different to using the OOP and template extensions C++ is capable of. In fact you could say that the STL+BOOST is like a separate language on top of C++, like CLOS is for Common Lisp.

---

### Post by tyoc on 2007-12-19
Without read the rest of the thread, this raise to my eyes

>  the language can do it for youthe language only serve for write, nothing more nothing less.

The the implementation of the lang, the execution environment, is the one that can do that, not the lang (the lang is only words make up of letters).

in python lang you dont have directly a malloc/new, but still you can see clearly where objects are __init__ and when, still the lang show "del" that is something about deallocation.

What I say is that you need to separete the python execution env from the lang, specially when doing an affirmation like "the language can do it for you".


For example, if the C developers (not the C users like I or any other C programming guy) choose to do a malloc that also can allocate in the stack.

```
¿is new memory show to outer scope?
yes: alloc in heap
no: alloc in stack

```Thus you will be able to do in C mallocs inside a function like this:

```

int simpletest1(&val){
   // alloc in stack
   char *x = malloc(1234);
   struct name *ret = NULL;
   if(boolean test){
       // alloc in stack
      struct name *yea = malloc(7*sizeof(struct name));
      //....
    // alloc in heap
     ret = malloc(sizeof(struct name));
     ret->algo1 = yea[i].algo1;
     ret->algo2 = yea[i].algo2;
   }
  // this is alloc in the heap because it return
   return ret;
}

```thus you have automatic deallocations. (yes, you can trick it, but then you will need to do a correct algorithm for handle that).

Without to much change and effort, even a malloc called stackmalloc that will do that, and you will not need to modify internally C.

Even if they apply in the implementation of the lang and extend the application furter, using the previously write function, they will be able to automatic free heap allocated data, some like this:

```

int simpletest2exterior(&val){
    char *x = malloc(1234);
    struct name *ret = NULL;
   if(some){
     //...
     // this new memory is alloc in the heap, because the previous
      ret = simpletest1(pthing);
      // handle some with ret...
    if(ret->algo1 == ret->algo2){
       // a loss of memory!!!!
      // Nein!, because in the assign, the same semantics can apply
       // will be return? or is tied to something external?, no deallocate it
       return 1;
     }
   }
}
 
```run it in your head, it work, perhaps there are some "cases" that will need to be taked more carefully.

You see, there was not many changes to actuall C (the semantics and the malloc/free still the same at sight), even you can still free by hand if you want, but sure, that implement that even that it doesnt change the lang itself, it is changed all the internall behaviour of a lang... the environment.


Thus dont blame a lang for not having something for what the implementation wasnt thinked... in fact you can't compare langs to implementation of langs. Dont blame it because the sloopy behaviour of some things, human or environment related.

lang is very different of all the underground decisions for the environment that will support the lang.


Stil, you can write your own malloc or in other case your malloc wrapper, that will handle the deallocations for you.


--- blah, why I write: [http://www.linuxjournal.com/article/6679](http://www.linuxjournal.com/article/6679) for first match...

---

### Post by slavik on 2007-12-19
10% speed penalty on an app is fine. 10% speed penalty on a system is not.

---

### Post by aks44 on 2007-12-19
@Wybiral, kripkenstein and pmasiar:

Oh my, I should have known I'd get that kind of answers... ;)

Again, I'm in no way belittling Python, I know there are very good to prefer it to other languages in some contexts. But I don't feel the reasons given in the OP are good ones.

To me the reasons the OP gives are like saying to a kid: "*You can't be bothered to learn to read & write? Fine, just watch TV, find a manual work, and marry someone who will take care of the mandatory reading/writing for you (taxes, ...). This way you won't have to deal with it.*" Come on, noone wants to raise his/her kids that way, do you?


And back to the "huge VM" thing: from my POV, adding a 3MB Python VM (notwithstanding other speed/memory costs) to a C application that "only" uses 4MB is definitely huge. YMMV :)


@slavik:
good point

---

### Post by psusi on 2007-12-19
Most environments have an allocator function that allocates from the stack instead of the heap.  It wouldn't help in this case though since the allocated memory was being returned by the function to its caller, so it couldn't be allocated on the stack.

---

### Post by aks44 on 2007-12-19
> **psusi said:**
> Most environments have an allocator function that allocates from the stack instead of the heap.  It wouldn't help in this case though since the allocated memory was being returned by the function to its caller, so it couldn't be allocated on the stack.

And when it comes to C or C++, malloc/new is necessary if the size of the block is determined at runtime. C++0x will remove that limitation though.
But of course other languages may already be able to handle this kind of code:

```
void foo(int size)
{
  // invalid C, invalid C++, valid C++0x (although doubtful due to the use of an array :-p)
  char buf[size];
}
```

---

### Post by Jessehk on 2007-12-19
C++ done correctly can be completey free of memory leaks.
For example:
```

#include <iostream>
#include <vector>

#include <boost/foreach.hpp>
#include <boost/shared_ptr.hpp>

#define foreach BOOST_FOREACH

class Resource {
private:
    int n_;
public:
    Resource( int n ) :
        n_( n ) {}
    
    inline const int &n() const { return n_; }
};

typedef boost::shared_ptr<Resource> ResourcePtr;
typedef std::vector<ResourcePtr> ResourceList;

const int SIZE = 10;

int main() {
    ResourceList resources;
    
    for ( int i(0); i != SIZE; ++i )
        resources.push_back( ResourcePtr( new Resource( i + 1 ) ) );
    
    foreach ( ResourcePtr r, resources ) {
        std::cout << r->n() << std::endl;
    }
}

```

```

$ valgrind ./example
==11254== Memcheck, a memory error detector.
==11254== Copyright (C) 2002-2007, and GNU GPL'd, by Julian Seward et al.
==11254== Using LibVEX rev 1732, a library for dynamic binary translation.
==11254== Copyright (C) 2004-2007, and GNU GPL'd, by OpenWorks LLP.
==11254== Using valgrind-3.2.3-Debian, a dynamic binary instrumentation framework.
==11254== Copyright (C) 2000-2007, and GNU GPL'd, by Julian Seward et al.
==11254== For more details, rerun with: -v
==11254== 
1
2
3
4
5
6
7
8
9
10
==11254== 
==11254== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 17 from 1)
==11254== malloc/free: in use at exit: 0 bytes in 0 blocks.
==11254== malloc/free: 25 allocs, 25 frees, 448 bytes allocated.
==11254== For counts of detected errors, rerun with: -v
==11254== All heap blocks were freed -- no leaks are possible.

```

---

### Post by psusi on 2007-12-20
> **aks44 said:**
> And when it comes to C or C++, malloc/new is necessary if the size of the block is determined at runtime. C++0x will remove that limitation though.
But of course other languages may already be able to handle this kind of code:

```
void foo(int size)
{
  // invalid C, invalid C++, valid C++0x (although doubtful due to the use of an array :-p)
  char buf[size];
}
```

You can achieve that in many compilers with something like:
```

char *buff;
buff = alloca( size );

```

But yea, having the ability to just declare a dynamic array will be nice if they ever get around to approving the new standard.

> **Jessehk said:**
> C++ done correctly can be completey free of memory leaks.


A program in ANY language done correctly will be completely free of memory leaks.  The question is how hard is it to do?  C++ provides a number of tools to make the job easy that you don't have in C, but without the overhead of full blown garbage collection like in python or java.

---

### Post by SNYP40A1 on 2007-12-20
My favorite language of the moment is Java.  Mostly because the syntax is much cleaner that C++ and also I like the garbage collection, Eclipse IDE content assist (yeah, not a feature of the language itself, but Eclipse Java IDE is just so easy and productive to use and the continuous compile saves a lot of debug time).  So for me, it's really about the whole package.  If I needed performance, I would use C or C++, however, Java is getting much faster and in principle, runtime optimization, something that requires a virtual machine can produce a faster program than something that does not run on a virtual machine.  There are a few reasons, but the main reason is that the VM knows during runtime which segments of the program are run most often and it can make these parts very fast.  C / C++ cannot do this because the compiler does not have this information at compile time, in other words, while running a Java program can be tuned to run faster than a C++ program.  (There are runtime traces that can be fed back into the C++ compiler in an attempt to achieve the same effect...however, with Java, the VM optimizations are automatic, the programmer does not have to do anything special.  Also, there is a lot of research going into garbage collection so the "fee" for this service is becoming less every year.  I really don't care about performance for what I develop, I'll just take the simplest approach and let the CPU do all the hard work.  If I want to make the program run faster, I can go back and re-write it more efficiently, open-source it and let someone else do that, or buy a faster CPU / more memory.  Hardware is getting really cheap...I can buy faster hardware, but I can't buy more time.

---

### Post by Klipt on 2007-12-20
> **aks44 said:**
> And when it comes to C or C++, malloc/new is necessary if the size of the block is determined at runtime. C++0x will remove that limitation though.
But of course other languages may already be able to handle this kind of code:

```
void foo(int size)
{
  // invalid C, invalid C++, valid C++0x (although doubtful due to the use of an array :-p)
  char buf[size];
}
```

That is already valid C99. It is also supported by g++ and will likely be valid C++ in the next standard.

---

### Post by psusi on 2007-12-20
> **SNYP40A1 said:**
> My favorite language of the moment is Java.  Mostly because the syntax is much cleaner that C++ and also I like the garbage collection, Eclipse IDE content assist (yeah, not a feature of the language itself, but Eclipse Java IDE is just so easy and productive to use and the continuous compile saves a lot of debug time).  So for me, it's really about the whole package.  If I needed performance, I would use C or C++, however, Java is getting much faster and in principle, runtime optimization, something that requires a virtual machine can produce a faster program than something that does not run on a virtual machine.  There are a few reasons, but the main reason is that the VM knows during runtime which segments of the program are run most often and it can make these parts very fast.  C / C++ cannot do this because the compiler does not have this information at compile time, in other words, while running a Java program can be tuned to run faster than a C++ program.  (There are runtime traces that can be fed back into the C++ compiler in an attempt to achieve the same effect...however, with Java, the VM optimizations are automatic, the programmer does not have to do anything special.  Also, there is a lot of research going into garbage collection so the "fee" for this service is becoming less every year.  I really don't care about performance for what I develop, I'll just take the simplest approach and let the CPU do all the hard work.  If I want to make the program run faster, I can go back and re-write it more efficiently, open-source it and let someone else do that, or buy a faster CPU / more memory.  Hardware is getting really cheap...I can buy faster hardware, but I can't buy more time.

I  have never understood the claims that it has cleaner syntax, but I guess that's mostly a matter of personal taste.  Personally I hate automagic garbage collection because it ends up using a lot more memory and hanging the app at odd times while the compactor runs, which also chews up more cpu.  I also hate teaching programming with gc since NOT having to learn to properly manage memory produces poor programmers.  

As for runtime efficiency, a vm will NEVER be able to beat a well written native program because at best, it will end up doing exactly the same thing, but will the additional overhead of the interpreter/jit compiler.  There isn't anything magical about a vm that can optimize heavily used segments of code better than a C/C++ compiler can optimize all the code.

---

### Post by aks44 on 2007-12-20
> **Klipt said:**
> That is already valid C99.
I didn't know that :oops: for once C is ahead of C++ feature-wise, thanks for letting me know. :)


> **Klipt said:**
> It is also supported by g++
And Borland C++ has the **__property** keyword, but that doesn't change the fact that neither properties nor runtime-dependent stack-allocated arrays are valid C++ (for now).

---

### Post by slavik on 2007-12-20
> **Klipt said:**
> That is already valid C99. It is also supported by g++ and will likely be valid C++ in the next standard.
I am pretty sure you can do that in C++ ...

---

### Post by aks44 on 2007-12-20
> **slavik said:**
> I am pretty sure you can do that in C++ ...

8.3.4 mandates that the array size be a constant (compile-time) expression. A few C++ dialects may allow that but it's definitely not valid C++.

---

### Post by psusi on 2007-12-20
Technically yes, but any decent compiler these days supports it since it is valid C99, much like most compilers have long supported C++ style // comments in C, even though it technically isn't valid.

---

### Post by SNYP40A1 on 2007-12-20
> **psusi said:**
> I  have never understood the claims that it has cleaner syntax, but I guess that's mostly a matter of personal taste.  Personally I hate automagic garbage collection because it ends up using a lot more memory and hanging the app at odd times while the compactor runs, which also chews up more cpu.  I also hate teaching programming with gc since NOT having to learn to properly manage memory produces poor programmers.  

As for runtime efficiency, a vm will NEVER be able to beat a well written native program because at best, it will end up doing exactly the same thing, but will the additional overhead of the interpreter/jit compiler.  There isn't anything magical about a vm that can optimize heavily used segments of code better than a C/C++ compiler can optimize all the code.

Well then why don't you program everything in assembly?  Whether the programmer should know about memory management or not depends on what the programmer needs to program for.  Someone who only needs to write scripts does not need to know about memory management.  I am not proposing that Java or any other modern language should be used for everything.

---

### Post by Lster on 2007-12-20
Just have a look at this:

[http://shootout.alioth.debian.org/gp4/benchmark.php?test=all&lang=gcc&lang2=python](http://shootout.alioth.debian.org/gp4/benchmark.php?test=all&lang=gcc&lang2=python)

C clearly slaughters Python for efficiency in almost all respects. At time of writing this, C was 266 times faster than Python on the "recursive" test...

---

### Post by LaRoza on 2007-12-20
> **Lster said:**
> 
C clearly slaughters Python for efficiency in almost all respects. At time of writing this, C was 266 times faster than Python on the "recursive" test...

How much longer would it take for a programmer to write a C program vs a Python program that does the same thing?

I am not saying C is bad (it is a language I like, in fact) but there are more expensive resources than processor cycles in many cases.

---

### Post by Lster on 2007-12-20
[QUOTE=LaRoza]How much longer would it take for a programmer to write a C program vs a Python program that does the same thing?

I am not saying C is bad (it is a language I like, in fact) but there are more expensive resources than processor cycles in many cases.[/QUOTE]

I agree Python has some brilliant benefits like rapid development and lovely syntax (in my opinion), but I don't really think it is best to use it here. I am just a performance nut - really I love everything to run optimally! Which is probably why I hate Vista.

---

### Post by Vadi on 2007-12-20
What I think that everybody is missing out here is that the user is not running one application at a time. But many at a time. And some people just don't want to take into account :/

---

### Post by Wybiral on 2007-12-20
> **Lster said:**
> I agree Python has some brilliant benefits like rapid development and lovely syntax (in my opinion), but for an operating system component it seems stupid to write it in Python. I am just a performance nut - really I love everything to run optimally! Which is probably why I hate Vista.

These are just panel applets, it's not like we're talking about the operating system or anything. There's no reason the GUI can't be written in a higher level language like Python. As pmasiar already mentioned, OLPC's sugar is written in Python and it performs well even in a limited environment.

Also, as far as recursion goes, you can always use stackless Python if you know you'll need strong recursion since C-Python has known inefficiencies in that area. You can also write those parts in C if you need to, but only if you need to... Why waste your time writing everything in C when you can write it in Python and write the bottlenecks in C? That's what profilers are for, so you don't have to optimize the entire program just because one tiny part is slow!

---

### Post by Sporkman on 2007-12-20
If you write your c/c++ in a clean & methodical way, memory leaks shouldn't be a problem.

---

### Post by slavik on 2007-12-20
when you write scripts, no, you shouldn't worry about memory management ... but then you shouldn't be doing something like the following in java:

```

String input;
while(char a = readchar()) {
  input = input + a;
}
```

that will work nicely on small input, but if you are reading something huge, expect the garbage collector to start running as much as your code.

---

### Post by bruce89 on 2007-12-20
> **LaRoza said:**
> Programming languages are tools, that is like saying we have to pry a 3/8ths in wrench from your hands when we are supposed to use a metric set.

Nope, imperial is daft.

> **LaRoza said:**
> How much longer would it take for a programmer to write a C program vs a Python program that does the same thing?

I am not saying C is bad (it is a language I like, in fact) but there are more expensive resources than processor cycles in many cases.

I doubt it's an order of magnitude anyway.

Using a specific language doesn't make a program any good. For instance, bad C causes leaks. Bad Python probably does something nasty.

---

### Post by tyoc on 2007-12-21
Also I think that the knowledge of other things, for example where I work the system should be in C, is about mobile devices, the environment is very restricted, but there are lot of things that can be improved in the design, people there have show me how they code, and in fact there are lots of room for improvement, that will lead to the possibility to be more productive, with best integration (with new apps) and a great code base for further developments, they have 1 now but isn't optimus rom my POV.


They haven't give me a schedule of how many time they normally use, but anyway, there are lots of unnecessary complexity in those "little programs" because the way that is done now, and probably because the way they learn it. By fortune, they have let that I do my app under my own guidelines.


Still, you need to be very careful, because mobiles are limited, and they don't have graceful exception handling, also I think after I make a presentation of nice things that can be done (@work and "standardize" them), I think there will open another door, and there should be more room for new ideas.

> Bad Python probably does something nasty.By instance, I have write little toys for the job in python, and after terminate them (only for do the work), I can qualify them by bad designed, now is time for refactor/rewrite, you know prototype is only that, there are lots of room for improvement after that in lots of ways.

---

### Post by pmasiar on 2007-12-21
> **bruce89 said:**
> I doubt it's an order of magnitude anyway.
... Bad Python probably does something nasty.

You have no hard facts and no personal experience, just prejudices. Good enough for you? I use Python daily and it continues to amaze me how more productive I am compared with statically typed languages, which I used for more than decade.

I am not aware of any real expert (ie not a forum member, but real well-known expert, who publishes books and is paid for opinions) who say what you do, but many experts who prefer dynamic languages. Some prefer Ruby, some Python, but noone says "C is the only way". Most people who say bad things about Python are people who never used it, have no real clue, just prejudices.

Of course, there are parts of a system deep down which are better of written in C for speed - but it's 5% of code. 30 years ago same arguments were used against C: people claimed that ASM is the only way, and C is not effective enough. Today, your PC is 95% idle. We have enough CPU cycles today to burn and let CPU to help improve programmer's productivity. Read "Hundred years language".

Or ignore it. For some people, inconvenient facts can be ignored just to keep intact good old prejudice.

---

### Post by Lster on 2007-12-21
[QUOTE=pmasiar]Of course, there are parts of a system deep down which are better of written in C for speed - but it's 5% of code. 30 years ago same arguments were used against C: people claimed that ASM is the only way, and C is not effective enough. Today, your PC is 95% idle. We have enough CPU cycles today to burn and let CPU to help improve programmer's productivity. Read "Hundred years language".[/QUOTE]

I use both C and hand optimized assembly. Even as processors get faster and are able to run even unoptimized code fast enough, there is waste and so more could be done.

---

### Post by tyoc on 2007-12-21
Another example is that all people can run, but only some special people (with lot of training) can get mark of 100m under 10s ;), you know olimpic games ;). they get the most of their body, while lots of people if not 99% or near 100% of the rest are average or worse, that is why they can go to a competition from all the world, and have the oportunity to take gold.

---

### Post by Klipt on 2007-12-21
> **psusi said:**
> There isn't anything magical about a vm that can optimize heavily used segments of code better than a C/C++ compiler can optimize all the code.
There is one case: runtime code generation. Compile time optimizations won't help there. A number of lisp implementations provide a compiler as part of the runtime and I think there's a lisp regular expression library that outspeeds Perl because it can compile the regexes into machine code at runtime.

Of course C libraries can use the same technique (the FFTW library does) but it requires the library implementor to pretty much be an expert on machine code for the supported platforms.

The down side of adding a compiler to the runtime environment is an increase in executable size and memory use.

> **pmasiar said:**
> Today, your PC is 95% idle.
For the average user, sure. But if you're doing hectic scientific computation, even C may not be fast enough, you'll use Fortran :D If a dataset takes 3 days to process using a program in C, you don't want to use a language that's 10 times slower (30 days) or 100 (300 days!)

---

### Post by LaRoza on 2007-12-21
> **Klipt said:**
> 
For the average user, sure. But if you're doing hectic scientific computation, even C may not be fast enough, you'll use Fortran :D If a dataset takes 3 days to process using a program in C, you don't want to use a language that's 10 times slower (30 days) or 100 (300 days!)

Considering Super Computers use Fortran that is true, but this thread is about GNOME Applets, which are usually not meant to be so critical.

In case anyone is joining in, this thread is about a few small memory leaks in GNOME applets written in C, and the OP thought Python would be better for such small unimportant apps. You would have never guess it.

---

### Post by Klipt on 2007-12-21
> **LaRoza said:**
> In case anyone is joining in, this thread is about a few small memory leaks in GNOME applets written in C, and the OP thought Python would be better for such small unimportant apps. You would have never guess it.

Ok. Here's another alternative: C++ with a [garbage collector](http://www.hpl.hp.com/personal/Hans_Boehm/gc/).

---

### Post by bruce89 on 2007-12-21
> **pmasiar said:**
> You have no hard facts and no personal experience, just prejudices. Good enough for you? I use Python daily and it continues to amaze me how more productive I am compared with statically typed languages, which I used for more than decade.

Indeed, I have no interest in Python.

I don't really see the argument, C will leak memory if you're not careful, but Python needs an interpreter. Surely both waste memory.

---

### Post by LaRoza on 2007-12-21
> **Klipt said:**
> Ok. Here's another alternative: C++ with a [garbage collector](http://www.hpl.hp.com/personal/Hans_Boehm/gc/).

D is also in the works, and I here good things about it.

---

### Post by LaRoza on 2007-12-21
> **bruce89 said:**
> Indeed, I have no interest in Python.

I don't really see the argument, C will leak memory if you're not careful, but Python needs an interpreter. Surely both waste memory.

For somethings, the Python interpreter overhead is worth it in terms of time saved trying to hack it in C. A small GNOME applet surely is Python worthy.

You have no interest in Python? Do you prefer another language?

---

### Post by Lster on 2007-12-21
[QUOTE=LaRoza]For somethings, the Python interpreter overhead is worth it in terms of time saved trying to hack it in C. A small GNOME applet surely is Python worthy.

You have no interest in Python? Do you prefer another language? [/QUOTE]

I know that *I* would find it easier to program in C. I like Python but I've never been a script-style programmer really. And I guess thats where my views are that Python is OK for scripts, but languages like C and Fortran are better for larger applications - even a small widgit.

---

### Post by LaRoza on 2007-12-21
> **Lster said:**
> I know that *I* would find it easier to program in C. I like Python but I've never been a script-style programmer really. And I guess thats where my views are that Python is OK for scripts, but languages like C and Fortran are better for larger applications - even a small widgit.

C can be used for scripts, and Python can be compiled.

Compiled languages are better for large applications in most cases. Python and C work together, so some large applications, most notably games, use Python although C is used for the engine.

---

### Post by SNYP40A1 on 2007-12-21
> **Lster said:**
> I use both C and hand optimized assembly. Even as processors get faster and are able to run even unoptimized code fast enough, there is waste and so more could be done. Not just that but inefficiency leads to hotter processors that need more cooling and consume more power (I know this isn't always true, I am generalizing).

By definition you aren't getting the most out of a system if it is inefficient. Think about how much we try so save battery life and stop global warming...

All this needs to be taken in perspective.  Optimizing an application requires someone's time.  The application can also run faster via faster hardware.  So a little money for faster hardware vs. my time...my time is more expensive, I'll go with the hardware and make all my applications run faster.  Moore's Law for the win!  However, in cases where the application is widely used, yeah, then maybe it pays to make it more efficient.  It really depends on what the application is used for.  

Regarding the three line inefficient Java code example posted earlier, I would even consider that fine for a script.  Only optimize if you need to.  Using your time to ensure your code is correct is much more important anyway.  Don't optimize something if it does not need to be optimized.

Also, inefficiency does not lead to hotter processors.  The processor will run longer, but not hotter.  Nothing heats up a processor like an application like Folding@Home, which is very efficiently hand-coded using assembly.  Depending on how long the application runs, yeah, it probably would consume more power, but likely to be negligible.  

Also, optimizing a program, unless it is very widely used is not going to put a dent in global warming or energy conservation.  If you really cared about this goal, try to get people to stop using screensavers and turn off their displays instead :-), that would do much more good.

---

### Post by Lster on 2007-12-21
[QUOTE=SNYP40A1]All this needs to be taken in perspective. Optimizing an application requires someone's time. The application can also run faster via faster hardware. So a little money for faster hardware vs. my time...my time is more expensive, I'll go with the hardware and make all my applications run faster. Moore's Law for the win! However, in cases where the application is widely used, yeah, then maybe it pays to make it more efficient. It really depends on what the application is used for. [/QUOTE]

Sure, but in this case that applet is probably used by many people, some with very little amounts of RAM and old processors.

---

### Post by kripkenstein on 2007-12-21
I've taken a closer look at [Vala]("http://live.gnome.org/Vala#head-d9d4a1654d3124a5fb2ed39406b42d269e7a7ca3"), which is a C#-like language that compiles directly into C+GObject (so it is basically for development on GNOME only).

The syntax is somewhat like C#, so it's very nice (not as nice as Python IMO, but still very good). It also appears to have excellent [performance]("http://code.google.com/p/vala-benchmarks/wiki/BenchResults") due to being compiled first into C: Almost as good as C, and significantly better than Mono's C#.

Vala is still under development, but it looks like it might offer the right mix of good, modern syntax (and memory management, etc.) along with performance.

---

### Post by Lster on 2007-12-21
[QUOTE=LaRoza]C can be used for scripts, and Python can be compiled.[/QUOTE]

You're right, I assume too much... :)

---

### Post by Vadi on 2007-12-21
Where does it say that an average PC is 95% idle?

:/

---

### Post by LaRoza on 2007-12-21
> **Vadi said:**
> Where does it say that an average PC is 95% idle?

:/

In my experience at least, my processors are almost never above 5% for any length of time, unless I am using Vista but that is a different story.

---

### Post by Lster on 2007-12-21
Yup. That's mine too, except Vista. :(

---

### Post by Wybiral on 2007-12-21
Some things just don't need to be that optimized. I used to be a byte-saving junky too. But after experiencing the productivity increase from using higher level languages and seeing the minimal runtime efficiency difference (in most situations) there no way I would go back to pure C. The biggest advantage of HLLs is that you can abstract your problem and solve it more algorithmically instead of trying to shave off little bits and bytes (which rarely increases efficiency much). And once again... If you PROFILE your applications then you know where the bottlenecks are and you can write those tight loops in C when you need to. But writing the entire application in C is just a plain waste of time,

Before complaining about the development time increase from having to interface C with Python, check out [SWIG]("http://www.swig.org/") (which works for other HLLs as well) and [Pyrex]("http://www.cosc.canterbury.ac.nz/greg.ewing/python/Pyrex/"). So when you need to shave some operations, you can use C. But why on earth would you waste all of your time developing the entire application in a language that requires you to micromanage everything when someone has already written (and tested) a nice system for handling memory and a huge standard library just waiting for you to use it!

---

### Post by Lster on 2007-12-21
[QUOTE=Wybiral]Some things just don't need to be that optimized. I used to be a byte-saving junky too. But after experiencing the productivity increase from using higher level languages and seeing the minimal runtime efficiency difference (in most situations) there no way I would go back to pure C. The biggest advantage of HLLs is that you can abstract your problem and solve it more algorithmically instead of trying to shave off little bits and bytes (which rarely increases efficiency much). And once again... If you PROFILE your applications then you know where the bottlenecks are and you can write those tight loops in C when you need to. But writing the entire application in C is just a plain waste of time,

Before complaining about the development time increase from having to interface C with Python, check out SWIG (which works for other HLLs as well) and Pyrex. So when you need to shave some operations, you can use C. But why on earth would you waste all of your time developing the entire application in a language that requires you to micromanage everything when someone has already written (and tested) a nice system for handling memory and a huge standard library just waiting for you to use it! [/QUOTE]

You speak good sense. Ofcourse there are some things like and OS, scientific simulation, drivers or games that would require *such* a high level of performance that hand optimized assembly would only do.

Even for other things, I feel that there are merits of optimal optimization and it gives great satisfaction when I reduce running time by 50% or whatever!

Something I'm still interested in, if anyone can answer it for me, is whether a optimized code would be more power and heat efficent than unoptimzed code. Sorry to take this a little off topic - I'm just curious.

---

### Post by LaRoza on 2007-12-21
> **Lster said:**
> 
Something I'm still interested in, if anyone can answer it for me, is whether a optimized code would be more power and heat efficent than unoptimzed code. Sorry to take this a little off topic - I'm just curious.

I highly doubt it unless there is a real issue with the code.

My CPU (the heatsink, anyway) is 82.5 F (28 C) and if a program can cause a significant difference in that versus an unoptimized version, there is a problem with the code.

(I used an IR thermometer for the temperature  reading)

---

### Post by Wybiral on 2007-12-21
> **Lster said:**
> You speak good sense. Ofcourse there are some things like and OS, scientific simulation, drivers or games that would require *such* a high level of performance that hand optimized assembly would only do.

Even for other things, I feel that there are merits of optimal optimization and it gives great satisfaction when I reduce running time by 50% or whatever!

Of course something like a kernel or a device driver, you should use C. But I don't write kernels, and I doubt most of us do (and if you do, then this doesn't apply to you).

I've written games in Python without seeing much of a performance decrease. I used [PyGame]("http://pygame.org/news.html"), [PyOpenGL]("http://pyopengl.sourceforge.net/"), and [PyODE]("http://pyode.sourceforge.net/"). While you can't write every component of a game engine in Python, you can write most of it. And there are tons of optimized vector/matrix mathematics modules (such as [NumPy]("http://numpy.scipy.org/")). Not to mention game engines for Python such as [Soya3d]("http://home.gna.org/oomadness/en/soya3d/index.html") and [PyOgre]("http://www.ogre3d.org/wiki/index.php/PyOgre"). It's a myth that Python isn't capable of 3d graphics.

It's better to increase your runtime performance by 50% by using a clever algorithmic optimization. I rarely find that simply pushing low-level bits around gains that much speed. But like I said, if you need that 50% increase and you know you can get it from C, then write that portion in C. But you don't have to write the entire thing in C.

---

### Post by ThinkBuntu on 2007-12-21
GNOME is slow enough as it is. I'd hate to see the desktop written in mostly Python! By the way, what are the major DEs written in anyway? Too lazy to research right now, so I hope someone in here already knows.

[LIST]
[*]Xfce
[*]KDE
[*]Fluxbox
[*]Enlightenment
[/LIST]

?

---

### Post by Jessehk on 2007-12-21
> **ThinkBuntu said:**
> 

[LIST]
[*]Xfce
[*]KDE
[*]Fluxbox
[*]Enlightenment
[/LIST]

?

Xfce: C++
KDE: C++
Fluxbox: C++

---

### Post by Wybiral on 2007-12-21
> **ThinkBuntu said:**
> GNOME is slow enough as it is. I'd hate to see the desktop written in mostly Python! By the way, what are the major DEs written in anyway? Too lazy to research right now, so I hope someone in here already knows.

[LIST]
[*]Xfce
[*]KDE
[*]Fluxbox
[*]Enlightenment
[/LIST]

?

I don't think anyone is saying GNOME should be written in Python, just certain components and addons (like GNOME applets). There is obviously a place for C in low level components like the kernel and the core of the desktop environment. But I see no reason why small applets shouldn't be written in Python.

---

### Post by LaRoza on 2007-12-21
> **ThinkBuntu said:**
> GNOME is slow enough as it is. I'd hate to see the desktop written in mostly Python! By the way, what are the major DEs written in anyway? Too lazy to research right now, so I hope someone in here already knows.


GNOME is in C. Although you might already know that.

---

### Post by bruce89 on 2007-12-21
> **LaRoza said:**
> You have no interest in Python? Do you prefer another language?

I can hardly even do C, so I can't be expected to know others.

If you want to rewrite gnome-applets in Python, go on. Nothing is stopping you. One thing I wouldn't like about this is the delay when starting GNOME for the Python interpreter to start up. Sure it might be ~2 seconds, but it would be great ammunition for GNOME flamers.

For instance, see the delay when starting the "External Tools" plugin in GEdit, and this only a small Python plugin.

I am thinking of rewriting command-not-found in C, as it seems a bit slow.

> **kripkenstein said:**
> I've taken a closer look at [Vala]("http://live.gnome.org/Vala#head-d9d4a1654d3124a5fb2ed39406b42d269e7a7ca3"), which is a C#-like language that compiles directly into C+GObject (so it is basically for development on GNOME only).

The syntax is somewhat like C#, so it's very nice (not as nice as Python IMO, but still very good). It also appears to have excellent [performance]("http://code.google.com/p/vala-benchmarks/wiki/BenchResults") due to being compiled first into C: Almost as good as C, and significantly better than Mono's C#.

Vala is still under development, but it looks like it might offer the right mix of good, modern syntax (and memory management, etc.) along with performance.

Indeed, it's quite nice.

---

### Post by LaRoza on 2007-12-21
>I can hardly even do C, so I can't be expected to know others.

Ok, I thought you would have known C very well to not support Python.

>If you want to rewrite gnome-applets in Python, go on. Nothing is stopping you. One thing I wouldn't like about this is the delay when starting GNOME for the Python interpreter to start up. Sure it might be ~2 seconds, but it would be great ammunition for GNOME flamers.

Some are already in Python and Python starts up anyway

>For instance, see the delay when starting the "External Tools" plugin in GEdit, and this only a small Python plugin.

Being that it is a plugin, there would most likely be a noticable delay anyway.

---

### Post by kripkenstein on 2007-12-22
I started a followup thread, less focused on why Python is good and more on why C is bad, [here]("http://ubuntuforums.org/showthread.php?p=3995915"). The thread contains irrefutable proof of my claims ;)

---

### Post by LaRoza on 2007-12-22
> **kripkenstein said:**
> I started a followup thread, less focused on why Python is good and more on why C is bad, [here]("http://ubuntuforums.org/showthread.php?p=3995915"). The thread contains irrefutable proof of my claims ;)

C isn't bad, it is a very important language. C was designed for OS programming in the 70's, when OS's were written in assembly. It has a very lengthy history, and is the first language to be ported to a new processor. Without C, computing as we know it doesn't exist.

This thread has run a very ragged course, and now has resulted in a "C is bad" statement.

---

### Post by Perfect Storm on 2007-12-22
Closed for investigation.

---

### Post by bapoumba on 2007-12-22
Moved to "Recurring Discussions" and reopened.
Second chance. If it triggers reports again, we will not hesitate to close it down for good.
Have fun ;)

---

### Post by pmasiar on 2007-12-28
Well, not many people looks into this forum, so thread is as good as dead.

But I like the "recurring discussions" - can you please create subforum of "Programming Talk" so people will be able to find it?

---

### Post by CraigPaleo on 2009-01-12
> **Jessehk said:**
> Xfce: C++
KDE: C++
Fluxbox: C++

You're partly mistaken.
According to: [http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments#Desktop_comparison_information](http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments#Desktop_comparison_information)

Xfce: C
KDE:  C++
Fluxbox: Unclear. C, C++ or a combination.
Enlightenment: C
Gnome: C

---

### Post by CraigPaleo on 2009-01-12
> **pmasiar said:**
> Well, not many people looks into this forum, so thread is as good as dead.

But I like the "recurring discussions" - can you please create subforum of "Programming Talk" so people will be able to find it?

This is actually my favorite section. I sit on the sidelines and and take in all the different opinions. I'm not a programmer but I've learned quite a bit from this and some others here. What I gather is that low-level programing is good for the user while higher-level programing is good for the programer. It seems to me that Vala would give you the best of both worlds. Vala, a high-level language, which compiles into a low-level C language that can be tweeked even further from there. Brilliant - efficency for both the programer and the program!

---

### Post by Vadi on 2009-01-12
> **CraigPaleo said:**
> You're partly mistaken.
According to: [http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments#Desktop_comparison_information](http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments#Desktop_comparison_information)

Xfce: C
KDE:  C++
Fluxbox: Unclear. C, C++ or a combination.
Enlightenment: C
Gnome: C

It's not a clear-cut case with gnome. Look at how many apps are made via bindings, like Python. apturl, upgrade manager definitely are made with python - maybe the add/remove thing too.

---

### Post by Mr. Picklesworth on 2009-01-12
For GNOME, platform stuff is all C. This is so that bindings can easily be created for pretty much any other language under the sun. Anything higher level could really be written with anything. For example, gnome-app-install is written in Python, Tomboy in Mono, Epiphany in C and Seahorse (Passwords and Encryption Keys) in Vala.

In the future, we will see *a lot* of GNOME apps written in [Vala]("http://live.gnome.org/Vala"), since it is tailored around the gobject type system used by the platform.

I think C has its place but the problem is people feel pressured into using it. They see all the "cool" apps (eg: old, mature projects) using it and assume it's the only way to go. The result is software written by someone who is using C but doesn't really *want* to use C.
Vala is a good thing because it still is, arguably, C. Hopefully this way people will start writing higher level apps in a higher level way (not that C is low level) without feeling that their work is chubby.

---

### Post by bruce89 on 2009-01-14
> **Vadi said:**
> It's not a clear-cut case with gnome. Look at how many apps are made via bindings, like Python. apturl, upgrade manager definitely are made with python - maybe the add/remove thing too.

Technically, those are Ubuntu-only programs, not GNOME ones. Canonical has some weird fascination with Python.

> **Mr. Picklesworth said:**
> In the future, we will see *a lot* of GNOME apps written in [Vala]("http://live.gnome.org/Vala"), since it is tailored around the gobject type system used by the platform.

I think C has its place but the problem is people feel pressured into using it. They see all the "cool" apps (eg: old, mature projects) using it and assume it's the only way to go. The result is software written by someone who is using C but doesn't really *want* to use C.
Vala is a good thing because it still is, arguably, C. Hopefully this way people will start writing higher level apps in a higher level way (not that C is low level) without feeling that their work is chubby.

I like Vala, but lately I've been back to C. Vala is a wee bit hacky at the moment still.

The whole JavaScript GNOME 3.0 thing seems odd however.

---

