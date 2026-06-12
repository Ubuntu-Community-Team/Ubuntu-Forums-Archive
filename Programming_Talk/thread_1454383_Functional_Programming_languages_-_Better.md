---
title: "Functional Programming languages - Better?"
date: 2010-04-14
forum: Programming Talk
---

### Post by km0r3 on 2010-04-14
After reading the [article]("http://sites.google.com/site/yacoset/Home/how-to-become-a-professional-programmer") *"How to  become a professional programmer*" I re-read this part twice:
> 
**Go back to school to learn the languages that nobody is using right  now**
For example, Haskell is not listed for most professional gigs  right now. But either Haskell or a similar functional language (Erlang,  ML, F#) will be in demand. This is where evolution is headed, and  you'll either be working in those languages or you'll be working in  languages that borrow so much from them that the concepts will be the  same. This will continue indefinitely, long after functional languages  are old-hat. One day you'll write programs by defining the desired  outcome, and your compiler will be a genetic algorithm[SIZE=2]First off, I don't think you can be a professional programmer by **only** guiding yourself by a manual or a singular algorithm of doing things.[/SIZE]
Back to topic: Can you guess why the author of the article says "functional programming is where evolution is headed"? Does this mean that other programming paradigms are "old-timers" or is this just another personal preference of a programmer X?
I remember people stating Object Oriented Programming as the **de facto** future of Software Development. Is this just another fairy-tale (not pretending to satirize OO Programming)?

> [...]
or you'll be working in  languages that borrow so much from them that the concepts will be the  same
[...]So, are functional programming languages "better"?

---

### Post by CptPicard on 2010-04-14
It is not quite that straightforward. But yes, functional languages have some important concepts to them that are valuable to understand.

> **km0r3 said:**
> 
Back to topic: Can you guess why the author of the article says "functional programming is where evolution is headed"? Does this mean that other programming paradigms are "old-timers" or is this just another personal preference of a programmer X?

The funny thing about functional programming is that it is, if you will, *the* old-timer programming paradigm, all the way from lambda calculus. The year was 1936, and it wasn't even run on computers back then, because they did not exist yet. So just because it has caught on in recent years in mainstream computing doesn't mean that its theoretical basis hasn't been well established for a long long time. 

Functional languages have until now mostly stayed in academia though due to two things -- relative performance problems, and, I suppose, the fact that a lot of coders whose mindset is very "imperative" and not particularly theory-minded, will have issues seeing why functional languages are of interest, or how to do things in them.

> 
I remember people stating Object Oriented Programming as the **de facto** future of Software Development. Is this just another fairy-tale (not pretending to satirize OO Programming)?

The programming world goes through silver-bullet-fad periods, assuming that some single approach will solve all problems. This is of course not the case... object-orientedness in the Java vein is not the be-all, end-all paradigm. But however, if you observe pretty much any programming language, object-orientedness is present in some form -- after all, you're dealing with "things in memory" which probably have some sort of type, and some kind of operations can be performed on that data, perhaps according to the type. 

A lot of modern programming languages have on the other hand started loosening the OOP-chokehold (but do note that in general, everything still *is* an object), and have started adopting features from functional programming languages, where functions and most importantly their lexical environment are also first class objects...

> 
So, are functional programming languages "better"?

They certainly have a somewhat different feel to them, and make you code in terms of declarative data transformations and function compositions instead of a sequence of operations on data. It's much more like working with a computable subset of mathematics, than writing programs.

An important feature of pure-functional languages is that they are side-effect free, which means that in our world of parallelism and distributed computing, the problem spots of shared data that requires  thread/process communication of some sort just go away, essentially. Of course formulating your problems in terms of Haskell's monads or whatever is initially an exercise for the brain, but once one learns to do this, you learn to think like a functional-programmer. This is the important educational aspect -- I find myself applying functional-kind of thinking in my problem solving even in usual imperative languages.

Of course I tend to believe that a competent programmer will be able to look at the problem from multiple perspectives and to apply the one that is most natural and fits the constraints of the language. This is why Lisp is awesome -- it doesn't have the ability to strictly keep side effects provably away, but it allows for *all* kinds of approaches, derived from its really, really simple basics. One could say that it defines the bare minimum a programming language symbolically consists of (in an abstract sense, not the bit-fiddling sense), and then pretty much any other programming language idea is a relatively brief distance away, in implementation terms.

---

### Post by nvteighen on 2010-04-14
It's difficult to add something to CptPicard's reply :p

> **km0r3 said:**
> 
I remember people stating Object Oriented Programming as the **de facto** future of Software Development. Is this just another fairy-tale (not pretending to satirize OO Programming)?


Well, OOP isn't opposed to functional programming (FP). It's a bit counter-intuitive at first (because of our "imperative prejudices"); I can tell you because after several years of doing OOP Scheme, I've resorted to mixed functional/imperative solutions till today, that I've thought on the idiotic thing I've been doing on one of my projects (see FreeTruco on my sig, but mind you, the code is quite "impure").

---

### Post by Reiger on 2010-04-14
It's the exposure to problem solving that counts. 

If you get that you are able to think of multi threading as a simple invocation of `map', of complex database transactions as operators on &#8220;state&#8221; (e.g. Haskell monads). And if you are able to understand continuations you will have an easier time understanding the logic behind and implementing callback interfaces, REST and all that event driven jazz.

Plus it tends to improve you documentation skills; because a semi-formal description of what a method/function does tends to be easier to write once you have learned to comment pure functional programs properly.

---

### Post by CptPicard on 2010-04-14
> **Reiger said:**
> And if you are able to understand continuations you will have an easier time understanding the logic behind and implementing callback interfaces, REST and all that event driven jazz.

After Lisping for quite a while and getting used to having automatic tailcall optimization and hence the ability to write CPS, I feel so incredibly tied down to the stack whenever I go back to a language that behaves like C does. It's like a straightjacket knowing that I always will *have* to just go back up the call stack... once you free your mind of those assumptions your view on writing code changes; but before that "switch" happens, it can really seem a bit weird because the C-mindset is so strong. This is one of the reasons why I would like to teach beginners in C -- C works better as a general case of Lisp, but not the other way around.

---

### Post by km0r3 on 2010-04-14
@CptPicard: Thanks for the Crash-Course. Now I first have to digest your words :)  .

> If you get that you are able to think of multi threading as a simple  invocation of `map', of complex database transactions as operators on  “state” (e.g. Haskell monads). And if you are able to understand  continuations you will have an easier time understanding the logic  behind and implementing callback interfaces, REST and all that event  driven jazz.

Sounds like all I've learned about OOP in the past was for nothing in FP.
 I like this new approaching "mindset", so learning a language like Lisp or Haskell will be on my To-Do list.

[QUOTE=CptPicard]
A lot of modern programming languages have on the other hand started  loosening the OOP-chokehold (but do note that in general, everything  still *is* an object), and have started adopting features from  functional programming languages, where functions and most importantly  their lexical environment are also first class objects...[/QUOTE]
This is a helpful observation and very true for languages like Python and Ruby.

My skills are limited to C/C++, VisualBasic, dynamic languages like Ruby  and Python, JavaScript and some Java and you notice the big popularity  of the OOP approach (except, of course, in C).
I somehow started learning basic constructs of FP in Python, like lambda (which was stolen from Lisp [?]) and list comprehensions, but I not yet acquired an earlier mentioned mindset.
For me, it's just a faster way of doing things in Python.

A very simple example would be:
```

 div = [n for n in range(500) if n % 2.0 == 0]
```
or```

div = filter(lambda x: x % 2 == 0, range(500))

```

the procedural approach:

```
div = []
for i in range(500):
    if i % 2.0 == 0:
        div.append(i)

```

Speaks for itself.

Thanks for the many great answers.

---

### Post by soltanis on 2010-04-14
Heh, functional programming languages are great. They put you in a totally different mindset from imperative programming, and in many cases, thinking functionally instead of imperatively lets you solve problems in less than half or even a fourth the number of lines.

I've been trying to use Python in a more functional sense recently. First class functions are nice but there's something lacking in a language which forces all your lambda functions to be one line.

---

### Post by CptPicard on 2010-04-14
> **km0r3 said:**
> 
 I like this new approaching "mindset", so learning a language like Lisp or Haskell will be on my To-Do list.

My humble suggestion would be Lisp... either Scheme or Common Lisp. Scheme is a great learning tool, and most of the stuff transfers as is to Common Lisp should you go in that direction.

This is not to be taken as an anti-Haskell-statement -- Haskell is more specific and arguably "harder" because its strict pure-functionality. Lisp is just a conceptually minimized "general programming language"... but the concepts are chosen such that although you can give the core language definition in a very concise manner, you really can build pretty much any concept from other languages with a relatively small effort. 

Also, really understanding "how Lisp works" essentially gives you the ability to write interpreters at will, as Lisp *is* the core evaluation mechanism to write "any language". The functional features are a nice bonus, you can do FP in Lisp too.

---

### Post by km0r3 on 2010-04-14
> **CptPicard said:**
> My humble suggestion would be Lisp... either Scheme or Common Lisp. Scheme is a great learning tool, and most of the stuff transfers as is to Common Lisp should you go in that direction.

This is not to be taken as an anti-Haskell-statement -- Haskell is more specific and arguably "harder" because its strict pure-functionality. Lisp is just a conceptually minimized "general programming language"... but the concepts are chosen such that although you can give the core language definition in a very concise manner, you really can build pretty much any concept from other languages with a relatively small effort. 

Also, really understanding "how Lisp works" essentially gives you the ability to write interpreters at will, as Lisp *is* the core evaluation mechanism to write "any language". The functional features are a nice bonus, you can do FP in Lisp too.

Your suggestion is very welcome, as you apparently are very experienced at that area.

I'll keep your suggestion in mind! :)

---

### Post by Cracauer on 2010-04-15
There is no question that learning a language with a radically different approach from all the OOP ones will be of great value. OOP as such is actually not that great for many things. OOP in a language with a lack of const strictness, much less one with dynamic typing only can be real trouble. It's really not that hot anymore, it will just do what made it popular in the first place: better than nothing.

However, claims that functional programming will take over are just bogus, and have been bogus since about 1960, unchanged. It's not gonna happen, acceptance and performance are just not there.

Lisp is a good choice since you can do any programming paradigm including functional. Common Lisp with the right implementation is also more practical and can perform much better than purer functional languages.

But it wouldn't be such a valuable experience if you just used Lisp to do sideeffect heavy programming, because it will let you. If you want to stretch your mind then something purer and statically typed might be a choice.

---

### Post by soltanis on 2010-04-15
Haskell is actually extremely fast, performing in some benchmarks close to C. Admittedly, in benchmarks that are designed to test imperative or object oriented languages, this tends to be the case.

The reason is that the Haskell's pure functionality makes it easy to implement very good optimizations, including lazy evaluations and memoization, which compilers like gcc can't do for C.

Saying that functional languages are performance-bound isn't really true. Functional languages are just different, and in the cases of things like Haskell or Scheme, I think that academics get too carried away with the purity of the language or minimalism, not really paying attention to things like readable syntax or practicality. Common Lisp is a different story -- unfortunately, good compilers for CL are hard to come by.

---

### Post by CptPicard on 2010-04-15
> **Cracauer said:**
> OOP as such is actually not that great for many things. OOP in a language with a lack of const strictness, much less one with dynamic typing only can be real trouble. It's really not that hot anymore, it will just do what made it popular in the first place: better than nothing.

It's just the static-typed OOP that essentially forces all those design patterns into existence -- you need to define even more types to jump through hoops. One of the major culprits to this is also single dispatch -- the insane idea that a method, that in an OOP language needs to be associated to data, is actually "owned" by a single type (or descendants) and the method is resolved only by the "this" object. It's a mad restriction, that CLOS fortunately does away with.

I don't get the dynamic-typing issue -- everything is an object, and the interface of the object is simply implicit, or can be investigated during runtime. Even CL is dynamically typed by default as you know...

Broadly taken, OOP is quite pervasive in all kinds of programming.

> 
However, claims that functional programming will take over are just bogus, and have been bogus since about 1960, unchanged. It's not gonna happen, acceptance and performance are just not there.

May not be that we'll all be coding FP in the future, but you must admit that the simple need to reduce communication between parallel threads whether it is on different cores or machines will greatly benefit from FP strategies.


> 
But it wouldn't be such a valuable experience if you just used Lisp to do sideeffect heavy programming, because it will let you.

Well, if we allow performance-related arguments... pure-functional style (Common) Lisp seems to cons like hell most of the time. And of course in CL you lose the provability guarantees you get in pure-FP.

Of course, I'm with you in the "it lets you do any kind of programming" sentiment in general, as I said above too. It's good to see how these things relate, and Lisp makes that clearer.

>  If you want to stretch your mind then something purer and statically typed might be a choice.

Haskell's type system is an interesting thing in its own right, and the reason why such static-typedness actually works there is the referential transparency -- the compiler can see a piece of data being declared, and because references never change their referents, can follow that piece of data through the code most of the time, inferring types. Haskell thus behaves almost as a dynamic-typed language most of the time, while not being one.

The comparison to your regular static-typed imperative language is interesting... annotating types is mostly an exercise where you just tell the compiler something you already know (I'm not a big believer in the theory that it actually prevents errors at compile-time). When a language is not as strongly inferrable the compiler is reduced to just crying when you make a mistake -- and ludicrously the language is such that the compiler is still able to mostly tell you *what is wrong*, but you are the one that needs to satisfy it although it *almost* could do it by itself.

Haskell can break through that barrier -- it's able to confidently infer a lot of stuff, and where it gets lost, it is able to tell you exactly where it is running out of information (although a bit cryptically sometimes) and then you just fill in the blank and off it goes again.

> **soltanis said:**
> 
unfortunately, good compilers for CL are hard to come by.

Is there something wrong with SBCL? :confused:

---

### Post by Shin_Gouki2501 on 2010-04-15
For all who want (or will be) working on the JVM there is: 
Scala [www.scala-lang.org](www.scala-lang.org)
combining OOP AND FP (blasphemy!), more balanced they say,quite different from OCaml
Clojure : [http://ubuntuforums.org/showthread.php?t=951509](http://ubuntuforums.org/showthread.php?t=951509)
(Its a LISP YEAH!)

---

### Post by CptPicard on 2010-04-15
> **Shin_Gouki2501 said:**
> 
combining OOP AND FP (blasphemy!)

This is a huge misconception. FP and OOP are not in any sense mutually exclusive -- actually, object-oriented programming can be thought of falling out of storing data members in closures and returning them from there according to some selector key that is passed into the function.

In addition, many/most FP languages implicitly have their data items as "objects" of some type, and then, depending on the dispatching mechanism, the function/method gets chosen according to that. Object-orientedness is not just a Java/C++/C# thing.

---

### Post by azagaros on 2010-04-15
I am reading this thread I see something like C vs C++ in its essence.

FP vs OOP has had its debate for years.  I have learned both forms since I began programming in 1982.  Each has it advantages and disadvantages.  It all comes down to preference of programming styles and implementation ease in the various languages.

Certian OOP langauges have tried to simplify the abstracts of programming, which I personally take for granted.  I am not a fan of Java or C# because of this lazy approach to programming.  Forgive me I learned Intel based Assembly at one time.

I still love to program in c and c++, with a splash of assembly.  I learned the old line numbered approach to basic and Old styles of pascal before I ventured into OPP approaches of Pascal and C/C++.  (one of the books I have on my shelf is called moving from c to C++.)

You need to know FP forms of programming to do OOP forms but the access and deviations are different.  As far as I know most of the languages out there try to make implementation of these ideas simpler and harder in some cases.

Sorry if I put my 2cents in with my experiences.

---

### Post by Shin_Gouki2501 on 2010-04-15
> **CptPicard said:**
> This is a huge misconception. FP and OOP are not in any sense mutually exclusive -- actually, object-oriented programming can be thought of falling out of storing data members in closures and returning them from there according to some selector key that is passed into the function.

In addition, many/most FP languages implicitly have their data items as "objects" of some type, and then, depending on the dispatching mechanism, the function/method gets chosen according to that. Object-orientedness is not just a Java/C++/C# thing.
Yes Scala for example is much more OOP than Java : [http://en.wikipedia.org/wiki/Scala_%28programming_language%29#Object-oriented_features](http://en.wikipedia.org/wiki/Scala_%28programming_language%29#Object-oriented_features)
and still has a lot nice FP features.

---

### Post by CptPicard on 2010-04-15
> **azagaros said:**
> 
FP vs OOP has had its debate for years.

But one needs to remember that FP's roots tend to be more theoretical, whereas OOP (as in it's C++-style implementations) has arisen more from the practical need of having an extensible type system with ability to associate operations with said types. What has held back FP's widespread adoption have been performance issues and just frankly programmer inability to grasp the concepts...

> It all comes down to preference of programming styles and implementation ease in the various languages.

I would venture a claim that the things that make FP languages what they are are objectively speaking qualitatively different in the sense that they are worth learning; it's not all just a matter of preference.

> 
Certian OOP langauges have tried to simplify the abstracts of programming, which I personally take for granted.  I am not a fan of Java or C# because of this lazy approach to programming.

I wonder if you mean the machine-specifics... it is interesting how the meaning of "abstract" seems to be completely opposite for different people. Assembly is at least from my POV very "concrete", but if I'm building a cathedral, it's the architectural blueprints that are important, not the rocks it's made of.

> 
  Forgive me I learned Intel based Assembly at one time.

Well, likewise -- just can't help noticing the high-level language vs. low-level language mindset seems interestingly irreconcilable. It's just an interesting thing I've noticed. 

> 
You need to know FP forms of programming to do OOP forms

I am not sure what you mean by this. Most OOP programmers I know couldn't program their own small object system in Scheme if they tried. I am actually getting the impression that you're confusing structured/procedural programming with functional programming...

---

### Post by azagaros on 2010-04-15
FP and its own abstraction.   I had to look up this set of concepts to get what I may have never learned.

Starting here for some basics of what I didn't understand.  
[http://en.wikipedia.org/wiki/Functional_programming](http://en.wikipedia.org/wiki/Functional_programming)

Most programmers never learn these abstractions.  I learned some of them over the 20 years of programming when I had a need for the concept in the programming process.  I didn't have problems understanding the concepts.

Getting accurate reals in an abstraction is how the bits are managed and sorted out, which can be accomplished in any language I have been associated with as long as I can manage the processor reasonably well, which most of the libraries I found stemming from that article did do.

Type checking and none type checking the basic of the void pointer in c with simple idea of type casting as you mathematically across the computer.  The oddities of writing an OS.

---

### Post by Vox754 on 2010-04-15
> **azagaros said:**
> FP and its own abstraction.   I had to look up this set of concepts to get what I may have never learned.

Starting here for some basics of what I didn't understand.  
[http://en.wikipedia.org/wiki/Functional_programming](http://en.wikipedia.org/wiki/Functional_programming)

Most programmers never learn these abstractions.  I learned some of them over the 20 years of programming when I had a need for the concept in the programming process.  I didn't have problems understanding the concepts.

Getting accurate reals in an abstraction is how the bits are managed and sorted out, which can be accomplished in any language I have been associated with as long as I can manage the processor reasonably well, which most of the libraries I found stemming from that article did do.

Type checking and none type checking the basic of the void pointer in c with simple idea of type casting as you mathematically across the computer.  The oddities of writing an OS.

Huh?
What the hell are you talking about?!

(Hint: it makes no sense... It's not even related to the topic of this discussion...)

---

### Post by Vox754 on 2010-04-15
> **CptPicard said:**
> But one needs to remember that FP's roots tend to be more theoretical, whereas OOP (as in it's C++-style implementations) has arisen more from the practical need of having an extensible type system with ability to associate operations with said types. What has held back FP's widespread adoption have been performance issues and **just frankly programmer inability to grasp the concepts...**

Quit dancing around Captain.

Answer this: why are programmers unable to grasp the "functional" paradigm? It is because our brains are naturally "procedural", "object-oriented", or what?

Is it simply a matter of which paradigm we were exposed first? 


> 
I am not sure what you mean by this. Most OOP programmers I know couldn't program their own small object system in Scheme if they tried. I am actually getting the impression that you're confusing **structured/procedural** programming with **functional** programming...

LOL! He is totally missing the point.

Actually, I think we've seen this before, people confusing "functional" with "procedural".

A lot of people have the wrong conception that because "C" has functions, it must be a "functional language". Perhaps, a new term need to be used for functional languages to avoid this sort of confusion. What about calling them "lambda languages" or another fancy term?

---

### Post by CptPicard on 2010-04-15
> **Vox754 said:**
> 
Is it simply a matter of which paradigm we were exposed first? 


Quite probably, and I maybe even likely. This is why I would be very curious to see what a programmer would be like who got exposed to functional programming first :)

FP does seem to be a bit challenging and/or mind-blowing for a lot of people who are used to procedurality/imperativeness... it was, for me, back in the day.

> 
Actually, I think we've seen this before, people confusing "functional" with "procedural".

Yes, it's quite common, that's why I'm suspecting it. :)

---

### Post by km0r3 on 2010-04-15
> **CptPicard said:**
> 
> FP does seem to be a bit challenging and/or mind-blowing for a lot of people who are used to procedurality/imperativeness... it was, for me, back in the day.

Yes, it's quite common, that's why I'm suspecting it. :)

:D

For those who don't know the difference:

[http://en.wikipedia.org/wiki/Procedural_programming](http://en.wikipedia.org/wiki/Procedural_programming)

[http://en.wikipedia.org/wiki/Functional_programming](http://en.wikipedia.org/wiki/Functional_programming)

---

### Post by slavik on 2010-04-16
> **CptPicard said:**
> After Lisping for quite a while and getting used to having automatic tailcall optimization and hence the ability to write CPS, I feel so incredibly tied down to the stack whenever I go back to a language that behaves like C does. It's like a straightjacket knowing that I always will *have* to just go back up the call stack... once you free your mind of those assumptions your view on writing code changes; but before that "switch" happens, it can really seem a bit weird because the C-mindset is so strong. This is one of the reasons why I would like to teach beginners in C -- C works better as a general case of Lisp, but not the other way around.
Write good C/C++ and your code will be tailcall optimised. :)

[http://amitksaha.wordpress.com/2009/05/23/tail-recursion-optimization-gcc-gdb/](http://amitksaha.wordpress.com/2009/05/23/tail-recursion-optimization-gcc-gdb/)

---

### Post by Shin_Gouki2501 on 2010-04-16
Using Haskell and its LLVM Backend you get quite notable Results(tail Call opt.?!)

---

### Post by jase21 on 2010-04-17
As for Functional programming, Lisp is more suitable that any other. I quite often see people ignoring Lisp when they speak about functional programming, and speaks about Haskell, ML, etc.
There is a version of Lisp for parallel computing developed years before called QLisp, which is totally cool.
There are other languages where one can program in a Functional manner, like in ECMAScript based languages like JavaScript.

---

### Post by CptPicard on 2010-04-17
> **jase21 said:**
> As for Functional programming, Lisp is more suitable that any other. I quite often see people ignoring Lisp when they speak about functional programming, and speaks about Haskell, ML, etc.

Well, IMO the important point about Lisp that it is the most "multiparadigm" of languages while also having the most cleanly defined core. It certainly has some core functional tools, most importantly the lambda, but Lisp is not "only" a functional language, although you can code in functional style in it.

Most importantly it's not "pure" which is an either/or proposition. Therefore, Lisp code lacks the useful theoretical guarantees that come from never, ever having side-effects...

---

