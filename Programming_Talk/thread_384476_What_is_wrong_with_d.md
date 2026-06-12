---
title: "What is wrong with d?"
date: 2007-03-14
forum: Programming Talk
---

### Post by Tuna-Fish on 2007-03-14
Recently, I've been learning a little d, and I am getting more and more confused the more I learn. Not about d, it is simple and easy enough for anyone with a c/c++ background, but about why nobody uses it. So far, from what I've learned, d is in every possible way better than c. It is simpler, safer, quicker to code in, at least as expressive, and at least according to this: 
[http://shootout.alioth.debian.org/debian/benchmark.php?test=all&lang=all&calc=Calculate&xfullcpu=1&xmem=1&xloc=0&binarytrees=1&chameneos=1&message=1&fannkuch=1&fasta=1&knucleotide=1&mandelbrot=1&nbody=1&nsieve=1&nsievebits=1&partialsums=1&pidigits=1&recursive=1&regexdna=1&revcomp=1&spectralnorm=1&hello=0&sumcol=1](http://shootout.alioth.debian.org/debian/benchmark.php?test=all&lang=all&calc=Calculate&xfullcpu=1&xmem=1&xloc=0&binarytrees=1&chameneos=1&message=1&fannkuch=1&fasta=1&knucleotide=1&mandelbrot=1&nbody=1&nsieve=1&nsievebits=1&partialsums=1&pidigits=1&recursive=1&regexdna=1&revcomp=1&spectralnorm=1&hello=0&sumcol=1)
at least as fast and more memory-efficient.

So, I think there has to be something horribly wrong with it that I just cannot figure out, otherwise everyone would be using it.

Your thoughts?

---

### Post by yaaarrrgg on 2007-03-14
The only real "problem," I think, is that it's still relatively new.  It is being used, a.lthough it will take a little to gain more momentum.

---

### Post by Wybiral on 2007-03-14
Possibly because it is similar to C/C++?
I found this "hello world" program tutorial for D...

```

void main()
{
    printf("Hi");
}

```

Minus the fact that it allows a void return, it's just C code.

More D code:

```

int main()

{   
   for (int i=1; i<=10; i++)
   {
      printf("%d\n", i);
   }
   return 0;
}

```

So, it being so similar to C/C++, why should I bother learning it's little quirks?

It looks like a mix of C and C++ with a slightly new library.

I mean... I could be wrong, I'm just saying why *I* haven't invested any time into D.

---

### Post by lnostdal on 2007-03-14
..maybe you've just answered your own question; the problem with D is that it does not have enough users?

I don't know D though, so I do not know if there might exist any technical reasons why not more people are using it.

Another reason might be that people view it as redundant. Maybe we don't need yet another C-style language (C, Java, C++, C#) like D.

---

### Post by Tuna-Fish on 2007-03-14
> **Wybiral said:**
> Possibly because it is similar to C/C++?
I found this "hello world" program tutorial for D...
(snip)
Minus the fact that it allows a void return, it's just C code.

Actually, it doesn't even allow a void return, it just returns 0 when void.
> 
More D code:

So, it being so similar to C/C++, why should I bother learning it's little quirks?

It looks like a mix of C and C++ with a slightly new library.

I mean... I could be wrong, I'm just saying why *I* haven't invested any time into D.

A good reason to use D: if you can use C++, you already can use D, and D has GC that is, most of the time, faster than explicit memory free. 

Simple code doesn't change much (at all, really), but when dealing with complex stuff, like objects that are used in many places before retiring, you can just plain forget all the headaches of explicitly freeing memory. Just use the object, and when a function no longer needs something, set it's pointer to null. This sounds simple, but has quite long-reaching consequences. For one, exception handling turns from total pain in the *** into an useful, functional tool.

Alongside that, D avoids most of the pitfalls of garbage-collected languages by allowing the programmer very close control of the GC when needed. Need one part of the program to be really predictable? Call std.gc.disable() beforehand, and std.gc.enable() after. The GC is very efficient, and as a copying collector, mostly removes the issue of memory fragmentation. 
(this, by the way, is the major reason D is more memory efficient than C++. This effect is visible even in small programs that contain a lot of mutable data, but it increases quickly in larger ones.) Using data so it heavily fragments does cause some performance penalties as everything needs to be copied during a sweep, but the gc has very predictable access patterns so it can do the whole memcopy really quickly.

Oh and as a bonus point: The inline assembler is <3. Not very useful for real application development, but i love it.

---

### Post by Wybiral on 2007-03-14
OK, I can see how that would benefit a lot of people... But I've become very comfortable with handling my own memory.

If you understand what goes on behind GC, it should make sense that it really isn't faster (it has to do periodic checks to see if the memory is still referenced, often times the GC keeps a reference count on every pointer and free the memory when the count is 0, which adds to memory overhead).

If you know when the memory needs to be free, so that you can set it to NULL for the GC to free it, what makes that any easier than just freeing it right there?

Also, C compiles into pretty clean assembly code. Since D has GC, I'm assuming it isn't going to compile as transparent as C. I would be happy to see some D assembly dumps so I can see how efficiently and cleanly it compiles.

Another reason people probably don't use D as much is that when you start a project, you don't usually want a language that no one else uses or you aren't going to get much help with your project. People will be like "D, WTF is that... Screw this project"

I guess that causes a sort of chicken-and-egg situation.

---

### Post by pmasiar on 2007-03-14
Obviously D does not compete with C/C++: to get every last drop of CPU speed, even if paying for it by need to explicitly manage memory. Other two players in C-like app development space are Java and C#: Java is used by huge companies heavily invested in compatibility with old tools: they switched from COBOL to Java, and they are done switching for 20 years or more. C# is MS own Java - enough said.

So I do not see the niche - do not see the problem for which D will be the breakthrough solution. To be "new kid" or even "new smarter kid" is obviously not enough. All other popular languages have a niche and are good enough solutions for problems from that niche (of course not necessary as good for other niches).

So: what is the D's niche? What problems D is supposed to solve so much better that is will make sense to switch from existing languages in that niche and dislodge them from embedded and fortified positions?

---

### Post by Tuna-Fish on 2007-03-14
> **Wybiral said:**
> often times the GC keeps a reference count on every pointer and free the memory when the count is 0, which adds to memory overhead).
This is not how d gc works. old gc's, from a decade ago or so, worked like this. D has a copying collector.
> 
If you understand what goes on behind GC, it should make sense that it really isn't faster (it has to do periodic checks to see if the memory is still referenced
The difference is the jump a lot on a trampoline vs jump once from empire state building. The point is that modern computers are a lot better in sequential transfers than random access. When you allocate and free memory by hand, both operations need several random (from the computer's point of view) accesses to memory. 

In D, to allocate memory the gc maintains a single continuous memory area. To allocate from it, you need just the starting location and to check it has enough length. both values are actively kept in cache, meaning mem allocating is a lot faster than the dynamic allocation in c, which needs look for open space in heap, taking potentially tens random accesses to memory. in the other end of the pipe, when freeing memory gc reads all references and (if needed, and deemed appropriate) copies all the data they point to into a new contiguous block, leaving all the garbage as new contiguous block of open space. In the end, the gc does more work, but as an assembly programmer, which would you rather do:

1. 100*5 random accesses to memory at random parts of the program.
     or
2. 100 reads from cache and a single large memcopy that sequentially reads all the references, then sequentially reads all the memory it needs to copy and puts it all into a new contiguous block, then writes back new pointers.

As a nice additional bonus, the memory space is going to stay unfragmented, both speeding access a little and not wasting memory. (Of course, only to a point. the GC isn't going to move 10MB to free an int.)

This all comes with the price that while in c++, you know that allocating memory is going to take roughly x time, in D most of the time it takes very little time but when the gc runs out of free space and deems it necessary to free some of it, as opposed to just asking more from  the kernel, the single mem alloc takes a long time. In critical moments, you can hint the gc that you'd really rather want new memory now, but in some apps that need to be rt all the time this obviously wont work.


> 
If you know when the memory needs to be free, so that you can set it to NULL for the GC to free it, what makes that any easier than just freeing it right there?

What if you use it in more than one place? Whenever coding anything a bit bigger in C++ I've ran into the need of elaborate schemes to maintain who owns an object. If the object only has one user, then by all means delete() it after you stop using it, but the ability to pass around references to objects without risk of a dangling reference or a memleak is liberating.

> 
Also, C compiles into pretty clean assembly code. Since D has GC, I'm assuming it isn't going to compile as transparent as C. I would be happy to see some D assembly dumps so I can see how efficiently and cleanly it compiles.

D runs it's GC in another thread just for this issue. Assigning memory is very simple, and the assembly itself just forgets about freeing it. The only thing to remember is that pointers to gc-managed memory are not "reliable", as in they always point to the correct object, but the object can at any moment move anywhere in memory, so you cannot for example test p1>p2.
> 
Another reason people probably don't use D as much is that when you start a project, you don't usually want a language that no one else uses or you aren't going to get much help with your project. People will be like "D, WTF is that... Screw this project"

good point.
> **pmasiar said:**
> Obviously D does not compete with C/C++: to get every last drop of CPU speed, even if paying for it by need to explicitly manage memory.
D's gc is **faster** than explicit dynamic mem management in C/C++. The biggest point I already stated, here are more from dm's pages:
[http://www.digitalmars.com/d/garbage.html](http://www.digitalmars.com/d/garbage.html)

(edit) Of course, static allocation is always faster than dynamic allocation of any kind. (until you hit the swap...) then again, d also does staic allocation.(/edit)
> 
Other two players in C-like app development space are Java and C#: Java is used by huge companies heavily invested in compatibility with old tools: they switched from COBOL to Java, and they are done switching for 20 years or more. C# is MS own Java - enough said.


One point here, on the java apps i've made one of the selling points was that if a machine dies from age, since the VM doesn't change you can just get a new machine to run it on, even decades after the app was made. I wonder how C# does that, does MS really guarantee it will continue to work on new platforms, even on vista+2(or3)?

And this is not just a minor point, several times the requirements explicitly stated that, for example, the date is stored so there is not going to be another Y2K in at least a hundred years or so. Well, there won't, as long as they don't change the calendar (like move the DST :twisted: )

> 
So I do not see the niche - do not see the problem for which D will be the breakthrough solution. To be "new kid" or even "new smarter kid" is obviously not enough. All other popular languages have a niche and are good enough solutions for problems from that niche (of course not necessary as good for other niches).

So: what is the D's niche? What problems D is supposed to solve so much better that is will make sense to switch from existing languages in that niche and dislodge them from embedded and fortified positions? I asserted that it's niche is being better than c/c++ in everything that c/c++ does. I dunno.

---

### Post by Wybiral on 2007-03-14
> **Tuna-Fish said:**
> I asserted that it's niche is being better than c/c++ in everything that c/c++ does. I dunno.

***everything*** that c/c++ does?

That's a bold statement... I'm going to need to see some assembly output to back that up.

First off, C and C++ are in two totally different worlds... How can you just say that one language is ultimately better than both of them?

GC seems to be the only "niche" you mentioned it has over C and C++... What about programs that don't use dynamic memory (not all of them do)?

How is D better than C or C++ in those cases?

How clean and efficient does it compile? Can you post some assembly to compare?

How well does it interface with HLL languages? C does this almost seamlessly (probably because a lot of HLL were written in C in the first place)

How stable is it's use of pointers, you mentioned their location in memory isn't reliable, well... Sometimes you need to know these things to have full control over program and data flow. If I don't have a way of controlling these things, how can I use them to optimize my code? Can I output the assembly and manually optimize my program without screwing up the GC system?

When I create massive amounts of dynamic memory, can I depend on the GC to free it all in time to allocate more, or will I loose performance reliability due to the GC not freeing it when I need it freed?

EDIT:

BTW, I'm not attacking D, just questioning your assertion that it's better than C or C++. It may be... But I need proof before I'll believe that. Unfortunately I'm usually not impressed by GC in languages, it's going to need more than that to qualify as being better than C or C++

---

### Post by Tomosaur on 2007-03-14
D is a great language - the only thing holding it back is that it's still under heavy development, and the phobos lib set is incomplete at the moment. If you want to do everything from scratch, you can, more or less, but it's just not economical at the moment. D is well worth getting your teeth into now though, because I really do think it'll take off. It already has a GNU compiler (gdc, in case you were wondering), and if you know any C/C++, you'll get to grips with it very quickly.

---

### Post by Tuna-Fish on 2007-03-14
> **Wybiral said:**
> ***everything*** that c/c++ does?

That's a bold statement... I'm going to need to see some assembly output to back that up.

It was intentional provocation.

ATM, I have not programmed much on D, at least not enough to evangelize it, not by a long shot.  I used to do quite a bit of C++, lately have been using mostly java for work and python for personal projects. A friend pointed me to D, marketing it as a language as easy as java but faster than c++. I was very skeptical, thinking gc is something for scripting languages. Well, he pointed me at the performance figures back [here]("http://shootout.alioth.debian.org/debian/benchmark.php?test=all&lang=dlang&lang2=gpp") and I decided to try it out. It is so much faster and plain easier to code than c++, at least for me, and still is in the same performance ballpark, slightly faster on average, that I am kind of baffled.

> 
First off, C and C++ are in two totally different worlds... How can you just say that one language is ultimately better than both of them?
Can't really. I've only learned C after I did C++ and I've always thought of C as a subset of c++. I'm by far not familiar enough with C to judge it.

> 
GC seems to be the only "niche" you mentioned it has over C and C++... What about programs that don't use dynamic memory (not all of them do)?

How is D better than C or C++ in those cases?

Safe and strong typing? I don't really know. From Wikipedia:
>  D adds to the functionality of C++ by also implementing design by contract, unit testing, true modules, automatic memory management (garbage collection), first class arrays, associative arrays, dynamic arrays, array slicing, nested functions, inner classes, closures (anonymous functions), lazy evaluation and has a reengineered template syntax. D retains C++'s ability to do low-level coding, and adds to it with support for an integrated inline assembler. C++ multiple inheritance is replaced by Java style single inheritance with interfaces and mixins. D's declaration, statement and expression syntax closely matches that of C++

[quote=Wybiral]
How clean and efficient does it compile? Can you post some assembly to compare?
[/quote]
It would appear not very. I don't have any of my own code on this machine, so i just picked the binary tree entry from the programming language shootout and did a compile on that. Unoptimised: 436 lines, optimised: 850 lines. Can't post here 'cos there is a 5000 char limit or so.
> 
How well does it interface with HLL languages? C does this almost seamlessly (probably because a lot of HLL were written in C in the first place)

D contains the C standard library, split into different namespaces but still, and completely supports C ABI. If it works with C, it works with D.
> 
How stable is it's use of pointers, you mentioned their location in memory isn't reliable, well... Sometimes you need to know these things to have full control over program and data flow. If I don't have a way of controlling these things, how can I use them to optimize my code? Can I output the assembly and manually optimize my program without screwing up the GC system?

You can turn the GC off for specific objects if you want. I think you cannot really manually optimize  compiler output in d, that is what the inline assembler is for. Then again, I don't really know. I'm a boring application developer, I have never actually sold anything that had hand-optimized assembler in it. Perhaps that's why I like the inline assembler so much.
> 
When I create massive amounts of dynamic memory, can I depend on the GC to free it all in time to allocate more, or will I loose performance reliability due to the GC not freeing it when I need it freed?

The GC generally works if and when something requests memory and there isn't enough free on it's free block. You can force it to do it arbitrarily, which should buy relative safety for a while, but gc inherently always brings with it that uncertainty of the time a mem allocation takes.

Oh, one little pointer: because of the way it works, the GC always frees all the memory it finds worthwhile to free. You can allocate and free massive amounts of memory, and one GC sweep after that you are back to as if you'd never done that.

> EDIT:
BTW, I'm not attacking D, just questioning your assertion that it's better than C or C++. It may be... But I need proof before I'll believe that. Unfortunately I'm usually not impressed by GC in languages, it's going to need more than that to qualify as being better than C or C++
Nor am I mindlessly evangelizing it. Actually, I can see why a hard core C++/C/ASM programmer might not be all that impressed in it, but for someone mainly programming in java, a language that has everything important that java has (strong, safe typing, GC, and the tools that help development (dbc, unit testing)) and compiles to machine code and is actually **faster** than c++ sounds quite awesome.

---

### Post by Wybiral on 2007-03-14
> **Tuna-Fish said:**
> ... and is actually **faster** than c++ ...

I've seen those benchmarks, but benchmarks aren't really conclusive. D may have been faster in certain areas, especially faster than C++ since it largely uses the C library. But weighted in specific areas or types of programs, and those benchmarks are completely different.

Most of the time, C is smaller and faster than C++ because it lacks the overhead of OOP and is easier for the compiler to optimize. So comparing it with C++, and D probably is faster.

But C is incredibly low-level and really easy to optimize. In many cases it's like an easy-to-read form of assembly. D might be able to compare with it, but it would probably be a stretch to actually say that it's FASTER.

Off topic:

The reason I don't like inline is because it's slightly unpredictable, unless you use the "volatile" keyword. Even then it doesn't help that much, I think it's easier to let the compiler output the entire object file to assembly, optimize there, then assemble it. Sometimes I just use C to draft my assembly since it's much faster to write in and produces such clean assembly.

---

### Post by Mirrorball on 2007-03-14
If you turn off "memory use" from those benchmarks, C is the fastest language. D is interesting, but I think it needs more excellent libraries, like Ruby, which was really obscure until Ruby On Rails.

---

### Post by pmasiar on 2007-03-15
> **Tuna-Fish said:**
> The difference is the jump a lot on a trampoline vs jump once from empire state building.

Manual memory management is hard, but if I am willing to pay the price, there is no jumping needed. IOW, Linux kernel stays in C. Do you claim D is good enough for Linux kernel? Don't make me laugh.

> D's gc is **faster** than explicit dynamic mem management in C/C++. The biggest point I already stated, here are more from dm's pages:
[http://www.digitalmars.com/d/garbage.html](http://www.digitalmars.com/d/garbage.html)

This page states obvious: GC is not predictable: when it runs, other processing has to wait. If this is not acceptable (real time processing), D is unusable - this is C/C++ niche I mentioned earlier. And this is the jump from Empire State Building you wanted to avoid :-)

> One point here, on the java apps i've made one of the selling points was that if a machine dies from age, since the VM doesn't change you can just get a new machine to run it on, even decades after the app was made. I wonder how C# does that, does MS really guarantee it will continue to work on new platforms, even on vista+2(or3)?

Yes. Both .NET and Java are standards and have independent open-source implementation. (MS may have some patents in .NET but that's not relevant here). So interested parties can keep VM around as long as it makes economic sense. Some very deep trenches. :-)

> I asserted that it's niche is being better than c/c++ in everything that c/c++ does. I dunno.

I agree, you do not know :-) 

> **Tuna-Fish said:**
> It was intentional provocation.

Yes, obviously, I knew that.

That's I asked for stating what is D's niche - and you do not found any.

>  gc is something for scripting languages.(...) [D] is so much faster and plain easier to code than c++,

You are mixing apples and oranges. Of course C++ is harder to code in - you need to manage memory by hand. If you let GC do it, you pay the price in performance. It is a trade-off: sometimes it makes sense (and you use C++), sometimes is not worth and you can use GC language.

Rapid application development uses higher-level languages, which generate slower code. 

> , but for someone mainly programming in java, a language that has everything important that java has (strong, safe typing, GC, and the tools that help development (dbc, unit testing)) and compiles to machine code and is actually **faster** than c++ sounds quite awesome.

Java has machine-independent jars. Presumably D code needs be compiled for target architecture. Might be pain for some situations.

Obviously D is new kid, learned from others, has nice flexible data types like Python, and could be faster than Python bytecode. But compiling is rather simple thing to do - there is couple of Python compilers. They are just not very important: if you need raw speed, use C/C++ anyway. If you code for enterprise, use Java or C#. For AI, Lisp is traditional choice. For most of everything else, Python/Ruby/PHP have own niches. So D will be yet another contender in this crowded landscape. Coming from far behind.

Python 3.0 may have optional typing, and compiled subset. D might have nice ideas (block GC in some parts of code) but I am not sure it is enough to dislodge Python/Ruby/PHP. All good ideas could be easily stolen :-) Maybe in some border areas makes more sense to use D, but I do not see it as killer language solving all problem from now onwards.

---

### Post by runningwithscissors on 2007-03-15
Are the language spec and the libraries open?

It simply looks like an effort to bring sanity to C++.

---

### Post by lnostdal on 2007-03-15
It seems the implementation is the spec (a good thing in general IMHO): [http://en.wikipedia.org/wiki/D_language#Implementation](http://en.wikipedia.org/wiki/D_language#Implementation) .. and they are GPL'ed or Open yes.

---

### Post by Tuna-Fish on 2007-03-15
> **Wybiral said:**
> I've seen those benchmarks, but benchmarks aren't really conclusive. D may have been faster in certain areas, especially faster than C++ since it largely uses the C library. But weighted in specific areas or types of programs, and those benchmarks are completely different.
True. C seems to win when the thing can be reduced to simple computational structures, D wins when there is insane memory use and C++ is somewhere in between.
> 
Most of the time, C is smaller and faster than C++ because it lacks the overhead of OOP and is easier for the compiler to optimize. So comparing it with C++, and D probably is faster.

But C is incredibly low-level and really easy to optimize. In many cases it's like an easy-to-read form of assembly. D might be able to compare with it, but it would probably be a stretch to actually say that it's FASTER.

Still, it is in the same ballpark. I think I'm gonna learn doing some things in plain C next when I have a suitable project. If I have gotten it right, the proper way to do something in plain C is just good old structured programming; functions, loops and selection, and their different versions. Right?

> Off topic:

The reason I don't like inline is because it's slightly unpredictable, unless you use the "volatile" keyword. Even then it doesn't help that much, I think it's easier to let the compiler output the entire object file to assembly, optimize there, then assemble it. Sometimes I just use C to draft my assembly since it's much faster to write in and produces such clean assembly.

Actually, that makes so much sense I'm gonna try it out.

> **pmasiar said:**
> Manual memory management is hard, but if I am willing to pay the price, there is no jumping needed. IOW, Linux kernel stays in C. Do you claim D is good enough for Linux kernel? Don't make me laugh.
I can very much see why GC is NOT good for a kernel. However, doing mem management by hand doesn't mean there's no jumping needed. Ever timed malloc()? Ever first ran malloc() and free() a couple of thousand times with varying sizes and left the mem area nice and fragmented, and then timed a malloc()? A malloc does quite a lot of work.
> 
This page states obvious: GC is not predictable: when it runs, other processing has to wait. If this is not acceptable (real time processing), D is unusable - this is C/C++ niche I mentioned earlier. And this is the jump from Empire State Building you wanted to avoid :-)

Actually, I can manage the jump, as long as it costs me less smaller jumps, and I can pick the time. Heck, I've been programming the past 3 years on a platform that had both the occasional jump from the top of the Empire State building, and the gazillion trampoline jumps :).
> 
Yes. Both .NET and Java are standards and have independent open-source implementation. (MS may have some patents in .NET but that's not relevant here). So interested parties can keep VM around as long as it makes economic sense. Some very deep trenches. :-)

This also explained to me why ms let's mono use their patents: it is needed to lure developers.
> 
You are mixing apples and oranges. Of course C++ is harder to code in - you need to manage memory by hand. If you let GC do it, you pay the price in performance. It is a trade-off: sometimes it makes sense (and you use C++), sometimes is not worth and you can use GC language.

Rapid application development uses higher-level languages, which generate slower code. 

But still again, my big point here is that application developent on D is like using a higher level language, only the performance of the resulting code is in the ballpark of C and C++, not python or java. Look at the site: D does things on average 2-30 times faster than  java and 5-100 times faster than python. The extremes are probably just badly coded implementations, but still. To me, this sounds a viable niche.

You might not want to use it for rendering 3d realtime, at least unless you toggle off of the GC from a thread and just use static allocation and the stack, in which case you are just using C with D syntax, really. But I bet I sure could make some GUI's seem a lot more snappy with it, and cut hardware costs when deploying something that needs some actual calculating performance 

> 
Java has machine-independent jars. Presumably D code needs be compiled for target architecture. Might be pain for some situations.

Correct. D can be provided as a script, but that is really nothing but the source code which is ran trough a perfectly normal compiler then instantly started, so not very useful, at least for complex programs.

> 
Obviously D is new kid, learned from others, has nice flexible data types like Python, and could be faster than Python bytecode.
Not could be, is, and by pretty much the same margin as C and C++.
> 
But compiling is rather simple thing to do - there is couple of Python compilers. They are just not very important: if you need raw speed, use C/C++ anyway. If you code for enterprise, use Java or C#. For AI, Lisp is traditional choice. For most of everything else, Python/Ruby/PHP have own niches. So D will be yet another contender in this crowded landscape. Coming from far behind.
Python 3.0 may have optional typing, and compiled subset. D might have nice ideas (block GC in some parts of code) but I am not sure it is enough to dislodge Python/Ruby/PHP. All good ideas could be easily stolen :-) Maybe in some border areas makes more sense to use D, but I do not see it as killer language solving all problem from now onwards.
Well, the concept of a killer language is kinda braindead, but I still think you're comparing D to the wrong languages. Well, we will see. Now it just needs some good libs.

---

### Post by russell.h on 2007-03-15
Does D have any built in multithreading features that set it appart from C/C++? Thats definitely the only reason I have ever even considered Java, and in the end pthreads turned out to be a better solution.

---

### Post by Wybiral on 2007-03-15
I see why fragmentation can slow down memory allocation, but why wouldn't it slow down GC too? Does it still not have to find a place to put the new memory? Maybe it reorganizes the memory... But even then, would it not slow it down to have to clean and reorganize the memory?

I'm not saying that D is a bad language or anything... Every languages has their ups and downs. D seems to be an interesting blend of the ups and downs between C, C++, and Java. But, I'm not sure that a blend is always good. If I need low-level stuff without GC, I'll use C. If I need high-level stuff with GC, then I'll probably use python.

Rarely do I ever seek something in the middle (sure it has some of the ups of both, but it also has some of the downs of both too). Plus, if my project does require something between low-level and high-level, I'll just interface the high-level language through the low-level one (such as C or C++ with either embedded python or as a python module depending on when side needs the other more)

But usually plain old C or C++ suite my needs. I really don't have that much of a problem with manual memory management, especially if you break all of your code into nice clean modules that handle their own memory.

But, that's just me. I can see why people like GC. It's just not my thing (maybe I'm a control freak)

---

### Post by Tomosaur on 2007-03-15
> **russell.h said:**
> Does D have any built in multithreading features that set it appart from C/C++? Thats definitely the only reason I have ever even considered Java, and in the end pthreads turned out to be a better solution.

[Yes](http://www.digitalmars.com/d/phobos/std_thread.html).

Phobos is the standard library set for D. It contains all of the 'basic' libraries / modules to allow you to do pretty much anything you like. The problem is that, like Java, things change quite a bit between releases, and some parts of it are still incomplete. It will get better though, and you're unlikely to run into any serious problems.

---

### Post by Tuna-Fish on 2007-03-15
> **Wybiral said:**
> I see why fragmentation can slow down memory allocation, but why wouldn't it slow down GC too? Does it still not have to find a place to put the new memory? Maybe it reorganizes the memory... But even then, would it not slow it down to have to clean and reorganize the memory?
It has to do with the way a copying collector works. First it loads all the existing references. Then it moves all the memory referenced by them into a single contiguous block at the start of the heap, then it saves back new references, then it sets the start of free memory at the end of the last reference. 

Thus, when allocating memory, all it ever does is loads the point where free memory starts and how much memory is already allocated. At that point it checks if the new allocation fits. If it does, it moves the pointer to start of free mem and allocates the memory, if it does not, it chooses whether to do a collection cycle, or just allocate more  free memory and do a page fault.

This way, you don't really lose performance itself, as by average this is faster than doing a malloc() every time. What you lose is performance reliability, as 999 mem allocations are very fast, but when you run out of that free memory block and there is enough time from last collection cycle that it finds collecting a sane way to do things, a good part of the memory is going to be moved, which takes time.

---

### Post by Wybiral on 2007-03-15
> **Tuna-Fish said:**
> It has to do with the way a copying collector works. First it loads all the existing references. Then it moves all the memory referenced by them into a single contiguous block at the start of the heap, then it saves back new references, then it sets the start of free memory at the end of the last reference. 

Thus, when allocating memory, all it ever does is loads the point where free memory starts and how much memory is already allocated. At that point it checks if the new allocation fits. If it does, it moves the pointer to start of free mem and allocates the memory, if it does not, it chooses whether to do a collection cycle, or just allocate more  free memory and do a page fault.

This way, you don't really lose performance itself, as by average this is faster than doing a malloc() every time. What you lose is performance reliability, as 999 mem allocations are very fast, but when you run out of that free memory block and there is enough time from last collection cycle that it finds collecting a sane way to do things, a good part of the memory is going to be moved, which takes time.

I'm having trouble believing that ALL of that is faster than simple fragmented memory allocation.

Eventually, it will fragment, and the way you explain sounds like a ton of operations to sort the heap.
Empty memory:
[_______]

Allocate 4 bytes:
[####___]

Allocate 2 bytes:
[####XX_]

Remove first four:
[____XX_]

Allocate 3 bytes:
Whoops. Now we have to go through the entire process of reordering the stack. Whereas a fragmented memory system would just put the 3 bytes in front.

It would be cool if you could clean the memory via a command so you could do it at a non-critical moment.

But say I'm writing a 3d game and having to allocate and free LOTS of memory, frequently. I have a feeling that just dealing with fragmentation will be faster than having to stop, reorder the heap, then allocate the memory.

Unless they have some super-efficient method of sorting the memory and rereferencing it, I just can't believe that it would be that much faster, if any (in most cases anyway).

---

### Post by Tuna-Fish on 2007-03-16
> **Wybiral said:**
> I'm having trouble believing that ALL of that is faster than simple fragmented memory allocation.

Eventually, it will fragment, and the way you explain sounds like a ton of operations to sort the heap.
Empty memory:
[_______]

Allocate 4 bytes:
[####___]

Allocate 2 bytes:
[####XX_]

Remove first four:
[____XX_]

Allocate 3 bytes:
Whoops. Now we have to go through the entire process of reordering the stack. Whereas a fragmented memory system would just put the 3 bytes in front.
Well, yes and no. What would happen in your example is:

(snip)

Allocate 3 bytes:
[____XXYYY

memory is given out in pieces of 4K, so it makes no sense to trigger a GC sweep until you have allocated it all and would otherwise cause a page fault. If you have a critical part in the program, you can just do a sweep before it, to get a large empty buffer, and then turn the GC off. While the GC is off, no memory is reclaimed by any means, so if you allocate, and then instantly free 1MB 100 times, the mem usage of the program rises up to 100MB, page faulting and getting new memory as it goes. When you turn GC back on and allocate more memory, the next time it runs the mem use reverts to normal.

And, even normally, there is some intelligence in whether the GC wants to do a page fault or a collection cycle.
> 
It would be cool if you could clean the memory via a command so you could do it at a non-critical moment.

But say I'm writing a 3d game and having to allocate and free LOTS of memory, frequently. I have a feeling that just dealing with fragmentation will be faster than having to stop, reorder the heap, then allocate the memory.

Unless they have some super-efficient method of sorting the memory and rereferencing it, I just can't believe that it would be that much faster, if any (in most cases anyway).
I don't know. I think I'm gonna run some tests and get back to you.

---

### Post by Coyote21 on 2007-09-21
Well, it's like this I've just known D, like an 3 months ago. And the main problem of D, is still the standard library (phobos), that it isn't that large, and even if D, let's you skip the garbage collector, the standard library isn't quite adapted to do that, so, if you want to do serious development like you do in C/C++, you will have to program without phobos,

About, the language constructs D, has many things that C++ don't have, like interfaces, delegates and most important strings aren't null based, and ressemble more the C++ string class from STL. Plus I've seem very funny code in D :D, like this one: [http://www.dsource.org/projects/tutorials/wiki/IntFunctionDelegateExample](http://www.dsource.org/projects/tutorials/wiki/IntFunctionDelegateExample)

Now, about D vs java and C#, well D is an compiled language, it will always run faster than the other two (at least if the compiler is good enough), but D could make use of java reflexion api, it would be an better improvement to use with interfaces, but once again that's phobos fault.

Plus, there aren't yet, any good debugger for D.

---

### Post by pmasiar on 2007-09-23
Maybe as you said, D is interesting, but below the radar? No tools, so only real experts dare to try?

Languages and tools win acceptance not on features alone: language without strong community is useless for most developers. It is like Catch-22: why waste time learning something what nobody else is learning and might be a flop? :-)

---

