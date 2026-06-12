---
title: "Language converter tool"
date: 2009-07-25
forum: Programming Talk
---

### Post by nipunreddevil on 2009-07-25
Is there a theoretical possibility that some one develops such a tool which converts code in one language say Java to code doing same thing in c??
We have converters from say Hebrew to English and other stuff,so on similar lines can such a tool not be created.

---

### Post by CptPicard on 2009-07-25
Actually, natural language translation is a much harder task because of all the ambiguities involved. Programming languages can at least in theory *always* be mapped from one to the other. In particular you can at least always interpret one language in an interpreter written in terms of the other.

Now, the gotcha here is that while you may be able to do this, it may not look pretty. You can convert Python to C by dumping a good part of the python interpreter along with your code to get the functionality in Python that is not readily a part of C language proper. On the other hand if you want to take some machine code and convert that into a higher-level language representation, figuring out what sort of higher-level design will match what the asm does is not an easy task to automate. It all boils down to how much semantics about the "meaning" of the source is present.

(Interestingly, this is a whole new way to look at the long-running high vs. low-level language expressiveness debate we've been having... you reading this nvteighen?)

---

### Post by nipunreddevil on 2009-07-25
A potential application of this hypothetical tool could be;
I write my code in Java,without worrying about pointers
Convert to c using this tool
Compile using gcc and have a lot of efficiency

---

### Post by matthew.ball on 2009-07-25
I think there is a tool called Perthon which converts from Python to Perl (and vise versa).

---

### Post by nipunreddevil on 2009-07-25
> **matthew.ball said:**
> I think there is a tool called Perthon which converts from Python to Perl (and vise versa).
So,this concept is a reality
will be interesting if high to low level converters are available

---

### Post by lisati on 2009-07-25
The only tools I've used to translate between programming languages (other than the normal use of compilers) have been [BCX ]("http://tech.groups.yahoo.com/group/bcx/")(designed for translating Windows progams written in a dialect of BASIC to C) and its predecessor [BASM]("http://vetusware.com/download/BASM286%203.0/?id=4599") (a subset/dialect of BASiC to 80286 assembly)

Studying the source code can be interesting, and might provide some insight for someone trying to tackle a Linux-friendly project in a similar vein.

---

### Post by matthew.ball on 2009-07-25
> **nipunreddevil said:**
> So,this concept is a reality
will be interesting if high to low level converters are available
I believe early GHC used to just compile to standard C, which helped make it portable.

---

### Post by CptPicard on 2009-07-25
> **nipunreddevil said:**
> 
will be interesting if high to low level converters are available

They are usually called "compilers"... decompilation is the more challenging way to go.

---

### Post by lisati on 2009-07-25
> **CptPicard said:**
> They are usually called "compilers"... decompilation is the more challenging way to go.

True: even the disassemblers I've looked at (on a couple of different platforms) sometimes needed a bit of help distinguishing between data and code. Trying to convert the result into useful code in a more abstract programming language than ASM would be a bigger challenge.

---

### Post by nipunreddevil on 2009-07-25
> **CptPicard said:**
> They are usually called "compilers"... decompilation is the more challenging way to go.

I guess i was misinterpreted,
I meant i write a bubble sort prog in Java use this tool and i have the code in c.
is this possible

---

### Post by CptPicard on 2009-07-25
Theoretically "yes", but I do not think performance would be any better than one you'd get from a dedicated Java JIT-compiler. It would probably be worse, actually, as the Java to C converter would have to compile a lot of Java-related support code for anything else except a trivial application, and the converter wouldn't be able to magically insert C-specific ways of doing things that would speed up a human-written implementation...

---

### Post by nvteighen on 2009-07-25
> **CptPicard said:**
> 
(Interestingly, this is a whole new way to look at the long-running high vs. low-level language expressiveness debate we've been having... you reading this nvteighen?)

:)

I guess here we should set what the goal is... Something that takes some Java code and transforms it into **working** C code is certainly possible, but the generated C code will be probably very hard to read for the programmer, as the machine will be satisfied by just creating some working code and not even care whether it's easier or harder to understand. It'll be "code written in C", but probably not "code in C".

Something that writes some C code into working Python code may also be possible... but again, the machine will be translating aiming to just mantain designation (the reality a text points to) and never caring about meaning (how the designation is considered in a certain semantic system). So, for example, I guess a program like that will take this C code:
```

int i;
for(i = 0; i < something; i++)
{
    /* ... */
}

```

And translate it into this Python code:
```

for i in xrange(0, something, 1):
    # ...

```

First issue is that all Python coders know that xrange call can be written as just xrange(something)... but will the machine be able to distinguish that nuances? Maybe it will... But the nuance the machine will never be able to translate is what the C code is **meaning** (no just what it designates... which is just "count from 0 upto something stepping by 1 and repeat the block until the previous statement is true") and how to translate that meaning into another language. Maybe the "correct" translation of the C for-loop was actually this Python code:
```

for i in some_list:
    # ...

```

But that "some_list" is referred elsewhere in the code. Will the machine be able to analyze contexts that perfectly to know and uderstand the conceptual "network" the C programmer had in mind and map it into a network natural to Python? I think not; machines are not creative and will always translate by a 1:1 relationship... maybe they can be taught to distinguish more elements and build a "3:3" or a "4:4" relationship, but it'd still be a "1:1" one ;)

Look at Lisp's macro system, considered the most powerful feature of metalinguistic manipulation in programming. Even being a very profound feature, a Lisp macro just rewrites stuff, it doesn't interpret what it means. Ok, you can put some conditionals... but it will still be just a rewriting. 

I was thinking these days on a project like this: a Scheme <-> Common Lisp translator. Using Lisp macros would make this "easy" being both Lisp dialects... Ok, "easy" in the sense that manipulating some Lisp's syntax to another Lisp is almost trivial. But what about the concepts? Where Schemers use tail-recursion, Common Lispers use a loop... &#925;&#959;, it's not a trivial difference... as the first one is guaranteed to be purely functional and the second is almost probably imperative and may modify variables. And what about the whole Common Lisp classes tree that Scheme completely lacks? And maybe the worst of all: Scheme doesn't distinguish between values and procedures and Common Lisp does... but in some cases not (example: creating a procedure in a let binding)... In a Scheme->CL translation, how can I make the machine distinguish something that has been abstracted away... sometimes?

---

### Post by slavik on 2009-07-25
> **nipunreddevil said:**
> A potential application of this hypothetical tool could be;
I write my code in Java,without worrying about pointers
Convert to c using this tool
Compile using gcc and have a lot of efficiency
And you memory leaks move from a VM to the OS.

---

### Post by unknownPoster on 2009-07-25
The closest I've ever gotten to something like this was about 7 years ago. 

I was big into programming the TI calculators and someone out there released software that supposedly could convert TI-BASIC into TI-assembly (A adaptation of Zilog Z80 assembly with a few TI specific system calls). It was unreliable at best, I could never get a simple version of "Hello World" working.

This is a fairly difficult task to accomplish. Heck, even online language translators have their faults. I challenge you to find a Language X to Language Y translator that's really good. I happen to know that the German to English and English to German translators are pretty good, but they lack support for idiomatic phrases among other things.

---

### Post by Reiger on 2009-07-25
"Language converter" tools have been an industry standard for the XML family of languages for years now. 

This is key point in ORM API's which quintessentially are about taking one set of semantics (the R) and applying them to another set (the O) using intermediate constructs (the M) -- usually encoded in something like schema-constrained XML.

EDIT: This is still very limited, but it is quite possible to convert Database queries to postscript or a PDF document on the fly using an XML representation of the query results and a XSLT stylesheet for conversion.

Apart from the XML family of languages there is of course the special case of Ook! and brainf*ck which can be converted into each other without much of a hassle since they are isomorphic equivalent. Similar things hold for pure functional language: it is quite possible to transform one Haskell program (for instance) into an equivalent form with better run-time characteristics. And it should be fairly trivial to transform one pure functional program into another because -in theory- all you have to do is define the atomic expressions in a program in terms of those of the target language.

---

### Post by matthew.ball on 2009-07-25
Just something I have been very interested in recently (probably because I have been doing some philosophy courses at uni) is propositional calculus (aka Natural Deduction).

I briefly touched on Gentzen's Natural Deduction in a CS Formal Methods course I did, but we covered it pretty fast and didn't really get into much detail. This particularly relates to the Curry-Howard correspondence - that there is an isomorph between a Natural Deduction proof and Alonzo Church's Lambda Calculus.

I guess what follows is the study of Completeness and Consistency - Natural Deduction is Sound: Every provable theorem is a tautology. If you can prove it, it's true.
Natural Deduction is Complete: Every tautology is a theorem provable with the rules of Natural Deduction.

Essentially, this says we can automate a machine, which will "prove" a logical theorem.

The isomorph is in direct regards to Church's Lambda Calculus, but we know from other research that the Lambda Calculus is computationally equivalent to a Turing machine, can we conclude the isomorph holds for Turing machines?

Also interesting is Kleene's work in Deterministic and Non-deterministic Finite-State Automata and Regular Languages :p

*Yikes* I could keep going.

---

### Post by abhilashm86 on 2009-07-26
> **nipunreddevil said:**
> Is there a theoretical possibility that some one develops such a tool which converts code in one language say Java to code doing same thing in c??
We have converters from say Hebrew to English and other stuff,so on similar lines can such a tool not be created.

actually we can develop an algorithm for program you are doing, which is almost understood by a person who dosen't know the launguage(programming ones!!), so he can get a view of what exactly you are doing, so finally he can implement or do whatever:)

---

### Post by CptPicard on 2009-07-26
> **matthew.ball said:**
> The isomorph is in direct regards to Church's Lambda Calculus, but we know from other research that the Lambda Calculus is computationally equivalent to a Turing machine, can we conclude the isomorph holds for Turing machines?


Whoah, hold your horses.

You are going wrong at some point. We can't build a machine that in general proves theorems except for restricted subsets of logic... look up Gödel Incompleteness Theorems. These are the fundamental restrictions on computation and result in halting problem-like base proofs...

EDIT: Ofc this then means that natural deduction is sufficiently restricted a logic to be complete and therefore not subject to the existence of Gödel sentences among other nasties...

---

### Post by jero3n on 2009-07-26
> **CptPicard said:**
> We can't build a machine that in general proves theorems except for restricted subsets of logic... look up Gödel Incompleteness Theorems. These are the fundamental restrictions on computation and result in halting problem-like base proofs...
I've read about Godel's theorem only in papers for A.I., I havent read the proof.
I always wondered how strict are these subsets of logic are and if Godel theorem restrictions arise often in practical problems.

---

### Post by Reiger on 2009-07-26
Well as a consequence of that proof, there cannot be one unifying notation system for Mathematics: any system rich enough to describe natural numbers is either incomplete or contradicts itself...

---

### Post by jero3n on 2009-07-26
> **Reiger said:**
> Well as a consequence of that proof, there cannot be one unifying notation system for Mathematics: any system rich enough to describe natural numbers is either incomplete or contradicts itself...
Yes indeed, the consequence of this, is that there exist expressions that we cannot prove if they are true or false. However, how often do we face such situations in real problems?

---

### Post by CptPicard on 2009-07-26
> **jero3n said:**
> if Godel theorem restrictions arise often in practical problems.

It is actually a phenomenon that has very direct implications for "[practical]("http://en.wikipedia.org/wiki/Halting_problem")" programs... and a lot of proofs about the non-computability of some problems rely on the proof structure of proving that "if we could do X, we could solve the halting problem, therefore, we can't do X".

Wouldn't it be nice to have an automatic debugger that fixes your bugs for you... :)

---

### Post by jpkotta on 2009-07-26
[http://en.wikipedia.org/wiki/Greenspun's_Tenth_Rule](http://en.wikipedia.org/wiki/Greenspun's_Tenth_Rule)

Computer languages are for humans.  Machine code (and we'll say assembly too) is for computers.  When you write a program in Java, you will use Javaisms that don't map perfectly to the C way of doing things.  C's efficiency comes from the fact that you have almost total control of the program.  It's because the human knows exactly the meaning of the code, and is doing some of the work of the VM or interpreter in a higher level language.  The VM will take care of these details in a safe, generic, probably slower way.  OTOH, there is no guarantee that one can do better than a VM, because VM writers are almost certainly better programmers than you or me.

C isn't faster because it's written in C.  It's faster because an intelligent human programmed in a very detail-oriented language.

---

### Post by jero3n on 2009-07-27
> **CptPicard said:**
> It is actually a phenomenon that has very direct implications for "[practical]("http://en.wikipedia.org/wiki/Halting_problem")" programs... and a lot of proofs about the non-computability of some problems rely on the proof structure of proving that "if we could do X, we could solve the halting problem, therefore, we can't do X".

Wouldn't it be nice to have an automatic debugger that fixes your bugs for you... :)
Hehe :) You reminded me some of Penrose's ideas.
Writing a language translating program or that "automatic debugger" or a universal theorem prover, all are fields of A.I.

Indeed Godel theorem is a good argument against A.I. but it is a bit dry. Like Penrose's books. If Godel's theorem consequences prevents the making of intelligence programs, I dont see why the same doesnt prevent a human to solve debuging problems or translate. In fact the theorem of incompleteness is great, just to show us how we should not cope with intelligence, i.e as a set of hard coded rules and transformations to give answers like to Halting problem. A.I is not formal logic. Neither a human can do this. That's why we develop neural networks, support vector machines, genetic algorithms and the like. The point is, we dont need to prove that the *best* translation is possible with an algorithm or not, but to simulate behaviours that do fairly good translations, which are getting better with new ideas or training. Like a human does.

Anyway, it is a great but huge discussion :)

---

### Post by CptPicard on 2009-07-27
> **jero3n said:**
> You reminded me some of Penrose's ideas.

They are interesting. As far as neuroscience goes he is considered to be a bit of a crackpot, but his discussion of the implications of theory of computation to philosophy of AI is the best I've read.

> If Godel's theorem consequences prevents the making of intelligence programs, I dont see why the same doesnt prevent a human to solve debuging problems or translate.

Well, that's the interesting question. There are two possibilities. Either there is something genuinely superior to the human mind as a computational device, or alternatively the Gödel sentences of Turing Machines and our brains are just simply *different* (this is completely possible). It is an interesting suggestion that there may be thoughts that are "intractable" to the mind ;)

Then there are more supernatural explanations of course...

> 
A.I is not formal logic. Neither a human can do this. That's why we develop neural networks, support vector machines, genetic algorithms and the like.

Actually it does not have to be formal logic. Turing machines are in general limited by the halting problem (for example, with the incompleteness idea being the theoretical basis), so you can't get around that using neural networks etc if you're going to still run them on a TM.

Interestingly, if the Church-Turing thesis holds and all physically computable stuff is computable using a TM, then we have seriously interesting questions facing us regarding the workings and limitations of the mind... (see possibility #2 above).

---

### Post by jero3n on 2009-07-27
> **CptPicard said:**
> Actually it does not have to be formal logic. Turing machines are in general limited by the halting problem (for example, with the incompleteness idea being the theoretical basis), so you can't get around that using neural networks etc if you're going to still run them on a TM
This is where my opinion stands. Indeed, you never know if a TM running a neural network will ever halt, giving the *best* trained network.

But IMO this is not of any true importance. While the TM is running, a neural network is trained, always approaching a better solution (assuming that is not trapped to a local minimum).

However, there are problems that neither a human can halt, giving the *best* solution. He stands with a solution that seems to work fine, if he is not traped to a local minimum of the problem's searchspace too. :)

Indeed, computation theoretical stuff is great, but in practice stupid numerical analysis iterations like those in BP, give more promising results in real problems. Like a human does.

---

### Post by CptPicard on 2009-07-27
"Artificial Intelligence is the class of all those problems that have not been solved yet", my professor used to say...

---

### Post by lisati on 2009-07-27
> **jero3n said:**
> Yes indeed, the consequence of this, is that there exist expressions that we cannot prove if they are true or false. However, how often do we face such situations in real problems?

This reminded me of a discussion in a programming book I once saw about the nature of problems you couldn't design an adequate algorithm for. To cut a potentially long and boring story short, the author used as an example a program that, given a particular program and its data, was meant to evaluate the "correctness" and style of said program. Suppose that there was a subtle bug in the program that amounted to an infinite loop when it encountered a "good" program but it otherwise worked perfectly. Suppose further that you ran the program using its own source as data. What would happen?

---

### Post by CptPicard on 2009-07-27
lisati, sounds like the classic universal-turing-machine halting problem intractability proof. :)

---

### Post by jero3n on 2009-07-27
> **CptPicard said:**
> "Artificial Intelligence is the class of all those problems that have not been solved yet", my professor used to say...
Intelligence is not computation. Research in neurosciences goes just fine without Godel. :)

A Universe Of Consciousness by Gerald Edelman & Giulio Tononi is highly suggested.

---

### Post by CptPicard on 2009-07-27
> **jero3n said:**
> Intelligence is not computation. Research in neurosciences goes just fine without Godel. :)

So you're saying AI using computation is not possible? :)

---

### Post by jero3n on 2009-07-27
> **CptPicard said:**
> So you're saying AI using computation is not possible? :)
Haha
Oops, did I say that? :D

No, I didn't. I wish my English was better to analyse this. I just can not get why the restrictions that apply to algorithmic systems *have* to also apply to the systems that they *simulate* and the opposite. In other words, why body cells *have* to behave like molecules & atoms.

---

### Post by ibuclaw on 2009-07-27
Converting from one language to another ... possible, I can name one example: cobc, which converts Cobol into C, then compiles.

A better design would be to use a language extension to make the "writing" easier. for example: yacc/bison. Both extend onto the C language, both generate C code.


Regards
Iain

---

### Post by CptPicard on 2009-07-27
I mean, if you're saying "intelligence is not computation" then you're flat out denying the possibility of strong AI, which would have to, by definition, have to be computation. How can you compute something that is not computation? :)

Mind you, by "computation" I mean TM-computable functions of course, and the question is more formally specified... whether there are TM-computable functions for a machine that behave the same as intelligence, which would imply intelligence is computable.

The really deep issue comes from Church-Turing thesis... if TMs compute everything that can physically be computed, and if the mind is a materialistic computing device, and if the mind actually is stronger than TMs, then something's got to give...

---

### Post by lisati on 2009-07-27
> **CptPicard said:**
> lisati, sounds like the classic universal-turing-machine halting problem intractability proof. :)

If memory serves correctly, the context was something along those lines. I must have a hunt through my library and see if I still have the book I read it in.

---

### Post by dribeas on 2009-07-27
Going back to the initial post: you can automagically convert from one language to another and get the worst of both worlds in the way.

Consider that idioms in one particular language can be performance killers in another. The example I always give (first that comes to mind, there are many others) would be a tight loop like this:

```

// Java
for ( int i = 0; i < 100000; ++i ) {
   Type x = new Type();
   // simple operation on type
}

```

That is as efficient as it gets in Java. Now, the direct translation:

```

// C++
for ( int i = 0; i < 100000; ++i ) {
   std::auto_ptr<Type> x( new Type() );
   // simple operation on type
}

```

Besides the std::auto_ptr<> to hold resources and apply RAII techniques to the resource problem, this code is a performance killer. In C/C++ the cost of memory allocation is expensive, really expensive. The equivalent idiom in C++ would be:

```

// C++, using C++ idioms
for (int i = 0; i < 100000; ++i ) {
   Type x;
   // simple opearations on type
}

```

This code is much more efficient than the previous. Then you can say that you can automate translation from Java to C++ using this second idiom, but then again, sometimes you do need to hold dynamically allocated memory in C++.

The same goes in quite a bit of different places... in C++ you can pass by value, by reference, pointer by value, pointers by reference... while in Java you are tied to either value (basic types) or reference by value. (Without even looking at const-ness that is a feature not even present in Java), the translator would have to come with that information out of the blue and probably taking the safest options that need not be good.

---

### Post by PjotAwake on 2009-07-31
Recently I created a Basic to C converter using Kornshell or BASH. After conversion the resulting C code can be compiled into a binary. Link:

[http://www.turtle.dds.nl/bacon/](http://www.turtle.dds.nl/bacon/)

You can see from the script source which constructs were used to convert certain Basic keywords.

Particularly hard was a simple statement like 'PRINT', as a PRINT statement can have multiple arguments of different types, separated by a comma. These should be parsed correctly and converted to the correct C types and put into a 'printf()'.

Also dynamic string allocations were difficult to overcome, especially with nested string functions (e.g. LEFT$(MID$(CONCAT$(a$, b$)))).

It was challenging but fun! :P

---

### Post by nipunreddevil on 2009-08-01
> **PjotAwake said:**
> Recently I created a Basic to C converter using Kornshell or BASH. After conversion the resulting C code can be compiled into a binary. Link:

[http://www.turtle.dds.nl/bacon/](http://www.turtle.dds.nl/bacon/)

You can see from the script source which constructs were used to convert certain Basic keywords.

Particularly hard was a simple statement like 'PRINT', as a PRINT statement can have multiple arguments of different types, separated by a comma. These should be parsed correctly and converted to the correct C types and put into a 'printf()'.

Also dynamic string allocations were difficult to overcome, especially with nested string functions (e.g. LEFT$(MID$(CONCAT$(a$, b$)))).

It was challenging but fun! :P
i want to try and do something similar with java/python and c.
I really have little knowledge of shell scripting,could you please explain the algorithmic procedure you followed and the resources you referred

---

### Post by lisati on 2009-08-01
> **PjotAwake said:**
> Recently I created a Basic to C converter using Kornshell or BASH. After conversion the resulting C code can be compiled into a binary. Link:

[http://www.turtle.dds.nl/bacon/](http://www.turtle.dds.nl/bacon/)

You can see from the script source which constructs were used to convert certain Basic keywords.

Particularly hard was a simple statement like 'PRINT', as a PRINT statement can have multiple arguments of different types, separated by a comma. These should be parsed correctly and converted to the correct C types and put into a 'printf()'.

Also dynamic string allocations were difficult to overcome, especially with nested string functions (e.g. LEFT$(MID$(CONCAT$(a$, b$)))).

It was challenging but fun! :P
Was it modeled on or inspired by BCX by any chance?

---

### Post by PjotAwake on 2009-08-01
> 
Was it modeled on or inspired by BCX by any chance?


No, it was inspired by my own need for a simple language which compiles on multiple platforms. Doing a lot things with scripting, this has the disadvantage of slow speed and visible source code. With a converter it is possible to create binaries which execute fast, and of which the source not necessarily is visible. It was modeled after the old BASIC's of the 70's and 80's, and you probably also will find some influence of Scriptbasic.

Before starting to create this converter, I already found BCX. The BCX converter is only available for Win32, but it seems they are preparing a Linux port now. However, BCX resembles the C syntax so much that one also can use C instead. It is well developed, but I would not call it a 'BASIC' in the strict sense.

---

### Post by PjotAwake on 2009-08-01
> 
I really have little knowledge of shell scripting,could you please explain the algorithmic procedure you followed and the resources you referred.


It is not necessary to use Shell Scripting to implement a Basic-to-C converter. I used shell scripting because these shells are available on all Unix-based platforms, including MacOSX. Therefore the converter will run on many platforms too, execept for Windows, but who cares for Windows these days :P

To understand the implementation, maybe it is best to first look at the way a tokenizer and a parser works. I have learned a lot from the tutorials on Flex and Bison. Just Google for these tools, and read their manpages thoroughly.

---

