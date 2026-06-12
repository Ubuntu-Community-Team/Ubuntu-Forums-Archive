---
title: "Transitioning from Java to C++"
date: 2010-02-09
forum: Programming Talk
---

### Post by jwbrase on 2010-02-09
I took three years of computer science in Java in high school and would now like to pick up C++. Does anybody have advice on what concepts I should familiarize myself with (Memory management and pointers seem to be something I'll really need to learn, for instance, as Java lacks them totally), pitfalls to watch out for, and good programming exercises that can give me practice with the major differences?

---

### Post by Zugzwang on 2010-02-09
I'd like to suggest reading "Thinking in C++" by Bruce Eckel. He once distributed this book as pdf, so you'll find it in many places on the web. The book(s?) covers all the important stuff like memory management, templates, pointers to functions, multiple inheritance, etc.

---

### Post by sharpdust on 2010-02-09
Many can suggest books, but I can only offer my advice:

Pointers were by far one of the hardest things I had to learn. I learned Java as my first programming language and then picked up C++. Had it been the other way around, things may have been different.

After doing C++ for about a year now as a full time position, I realize how much I took for granted all the things that Java did for me. But then I think about how it made me an 'ignorant' programmer since it hides all the inner details that make you more aware of what's really going on. Yes, I realize there's a sense of abstraction, but when you do this stuff daily, eventually it's nice to know what's 'under the hood'.

To sum up, all I can say that you can read all the books in the world, but you won't start fully understanding C++ until you actually write it. And write it often.

Once you start getting good, you should find yourself referencing this website a lot:
[http://www.sgi.com/tech/stl/](http://www.sgi.com/tech/stl/)
I find it to be the best resource for writing correct standard template library code.

---

### Post by CptPicard on 2010-02-09
Okay, I'll promise not to suggest either Python or Lisp instead if C++ is what you specifically want... ;)

A few things:

1. Learn to adopt proper idioms (think RAII) and really understand what things like copy constructors and pass/return by value actually do. Put some printing statements into little classes and play with them to genuinely get it. C++ explodes quite happily in your face otherwise. Add usage of initialization lists, safe exceptions...

2. Get into the habit of using Boost from the start. It helps you write idiomatic, safe code and not reinvent the wheel.

3. Learn templates early on. They are called an advanced technique for some reason, but the more C++ I write, the more templating I tend to use. This is certainly the influence of *other* languages than C++ or Java in that too (duck-typing/type-inferencing)... templated code also tends to be "viral" in your project; the more you use it, the more other stuff becomes templated.

4. It's not really the pointer that is new and magical (think of it just a kind array index that is also a Java-style object reference) -- the C++ reference is actually a more interesting beast. It really *is* the referred-to-object and behaves as such, assignment operator etc. included.

5. Where in Java you might create a composite class of other classes and then implement the composite elements' interfaces, in C++ you will use multiple inheritance. Java interfaces are C++ pure virtual base classes.

C++ is essentially just "added complexity on top of Java" so that manual memory-management in a native-compiled language can be accomodated. Otherwise, most design works pretty much the same. You don't have anonymous inner classes though, which is a pity -- writing function objects is more cumbersome, and you won't get the outside scope automatically.


> **sharpdust said:**
> 
Pointers were by far one of the hardest things I had to learn. I learned Java as my first programming language and then picked up C++. Had it been the other way around, things may have been different.

I hear this so often, but it puzzles me... admittedly I learned C as around my third language a long time ago so I may have forgotten the issue, but they really are given credit for far too much. They're indexes into an implicit array (the RAM) with type information attached that tells the compiler what kind of type is placed at the pointed-to location.

Otherwise, when used as just object reference types, they do not behave too differently from Java, except that you need to manage their lifecycle yourself.

> But then I think about how it made me an 'ignorant' programmer since it hides all the inner details that make you more aware of what's really going on. Yes, I realize there's a sense of abstraction, but when you do this stuff daily, eventually it's nice to know what's 'under the hood'.

I understand that the under-the-hood part is part of a programmer's education certainly, but the "meaning" of that stuff to a program in a higher-level language shouldn't be over-emphasized... in most of the really interesting code I've ever seen, the low-level semantics are irrelevant... unless it is, of course, specifically something that is supposed to push the hardware. Then again, the code I tend to consider fascinating is functional programming or something like that ;)

---

### Post by sharpdust on 2010-02-09
> **CptPicard said:**
> I understand that the under-the-hood part is part of a programmer's education certainly, but the "meaning" of that stuff to a program in a higher-level language shouldn't be over-emphasized... in most of the really interesting code I've ever seen, the low-level semantics are irrelevant... unless it is, of course, specifically something that is supposed to push the hardware. Then again, the code I tend to consider fascinating is functional programming or something like that ;)

When referring the under the hood, I don't mean way to low level, I'm talking about all the stuff Java gives you for free that C++ doesn't (unless you got some external libraries).
Stuff that comes to mind that I've had to write in C++ that Java had built in: [FileOutputStream]("http://java.sun.com/j2se/1.4.2/docs/api/java/io/FileOutputStream.html") and [HashMap]]("http://java.sun.com/j2se/1.4.2/docs/api/java/util/HashMap.html").
However the benefits (templates, overloading operators, multiple inheritance, etc.) really has won me over.

---

### Post by CptPicard on 2010-02-09
Well, yes, data structure implementations really are something one should investigate on one's own in any language. (STL does have hash_map btw...)

Multiple inheritance is a bit questionable... interfaces + delegation to some composite object does the same trick. Programming to interfaces is what you should be mostly doing anyway.

---

### Post by Some Penguin on 2010-02-09
> **jwbrase said:**
> I took three years of computer science in Java in high school and would now like to pick up C++. Does anybody have advice on what concepts I should familiarize myself with (Memory management and pointers seem to be something I'll really need to learn, for instance, as Java lacks them totally), pitfalls to watch out for, and good programming exercises that can give me practice with the major differences?

 There's less stuff 'built in' to C++.  That is, while there are a lot of third-party libraries that you can link to, they're not part of the actual language definition and you can't necessarily assume their existence if you want to write something that gets widely deployed.  Hence, things like configure scripts to see what people actually /do/ have... and people who have accumulated libraries of handy-dandy basic data structures and wrappers.  Also, C and C++ are generally looser standards in certain respects.  In Java, for instance, all the numerical primitives have a specific size (C only sets minimum sizes and an ordering constraint, IIRC) and a specific byte ordering (versus the native endianness).  This can result in you needing to be very careful if you're going to be doing things like writing data that you want to be able to interpret on multiple platforms.  If you think about it, even 'how do I create a new process' is not specified by the C standard -- Unix systems tend to use a fork() / exec() model, but that's not universal and it's not actually specified by C or C++.  Ditto for, say, "how do I clear the screen" or "how do I open a TCP connection to {host,port}".  Hence, if you want to do multiplatform work and the like, it will probably save you frustration if look for libraries that have already been ported to many OSes.  Memory management is something you'll want to pay attention to, indeed; C++ programs don't run in an environment that provides automatic garbage collection while the process is alive.  And there are such things as invalid pointers (whereas it's usually harder to have an invalid reference in Java, say) -- trying to dereference an address after you have already deallocated the memory, for instance.  OTOH, because it's driven entirely by your code, you don't necessarily have delayed-finalization problems like you can in Java, where the GC fails to actually collect your objects and run your finalizers for arbitrarily long times or the like.  You will probably want to learn gdb or the like, and perhaps a framework like Purify, because bugs resulting from some misdirected write corrupting data can result in significantly weird behavior some distance (in terms of function and time) from the code that did the bad write.  Multiple inheritance is possible, interfaces aren't, non-OOP code is more likely, header files provide the API declarations, unions are added, operator overloading is possible for syntactic sugar.   Call-by-reference is possible in C++ where Java is purely call-by-value (the values being references, yes, but it's still call by value; you cannot reassign the reference itself so that the caller's reference has been replaced with a reference to a completely different object, for instance).  And you can use either arrays of objects and arrays of pointers to objects.  Java has only arrays of references to objects... leading to people who have made the transition in the other direction wondering why their "Foo[] bar = new Foo[some_big_number];" call resulted in bar being full of nulls instead of valid Foo instances.

---

### Post by VertexPusher on 2010-02-10
Proper understanding of RAII is what separates good C++ programmers from crappy ones.

---

### Post by akshayy on 2010-02-10
needless to say, solve algorithms, code them in C, C++. And practice some applicaiton development in C,C++. You are done. Read books for basic concepts, I recommened C++ Primer by Stanley Lippmann.
Also Trust me, Pointers are not hard at all. Just use them safely.

And learn it all, there are lots of differences. Inheritance for example. And Deleting ununsed memory, objects, lol. Don't forget and do properly.

---

### Post by VertexPusher on 2010-02-11
> **akshayy said:**
> And Deleting ununsed memory, objects, lol. Don't forget and do properly.
No offense intended, but you're the crappy type of C++ programmer I was talking about in post #8. :P

---

### Post by sxmaxchine on 2010-02-11
if you wanted to learn c++ on a windows pc you can download visual c++ for free along with other programing langauges. the program is great for starting with a langauge, but the downside is that it only works on windows dont even try it with wine as it will not work.

get info on visual c++ here [http://www.microsoft.com/express/Windows/]("http://www.microsoft.com/express/Windows/")

---

### Post by akshayy on 2010-02-12
> **VertexPusher said:**
> No offense intended, but you're the crappy type of C++ programmer I was talking about in post #8. :P

ok RIAA is the best design pattern and the only way. and only RIAA is the most important that for a programmer, and not his ability to crack problems using amazing algorithms. And programmers should focus only design patterns... 
enjoy, be happy

---

### Post by TheStatsMan on 2010-02-12
> **CptPicard said:**
> 

3. Learn templates early on. They are called an advanced technique for some reason, but the more C++ I write, the more templating I tend to use. This is certainly the influence of *other* languages than C++ or Java in that too (duck-typing/type-inferencing)... templated code also tends to be "viral" in your project; the more you use it, the more other stuff becomes templated.



Haha, 'viral' is a good way to describe it.

---

### Post by CptPicard on 2010-02-12
> **TheStatsMan said:**
> Haha, 'viral' is a good way to describe it.

Yeah, that's how it feels like.. templating one thing results in templating another thing, and before long, all of your code is as templates, in the headers...

---

