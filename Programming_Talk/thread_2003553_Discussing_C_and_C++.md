---
title: "Discussing C and C++"
date: 2012-06-14
forum: Programming Talk
---

### Post by dagoth_pie on 2012-06-14
Hey there folks.

I've noticed that a lot of programmers say that they perfer C to C++. I've never purely done C, although in my opinion I learned to program C++ in quite a C-like way. So I'm wondering, why do some of you prefer C over C++.

My guess is that it has something to do with the STL libraries, would that be close to the truth in anyones mind?

And let's try not to flame each other guys. :D

---

### Post by codemaniac on 2012-06-14
You can find some good reading on the below link .

[http://unthought.net/c++/c_vs_c++.html](http://unthought.net/c++/c_vs_c++.html)

---

### Post by Bachstelze on 2012-06-14
> **codemaniac said:**
> You can find some good reading on the below link .

[http://unthought.net/c++/c_vs_c++.html](http://unthought.net/c++/c_vs_c++.html)

I find this extremely funny. The guy writes a program to count the number of distinct words in a text file. Who ever writes programs for that? Nobody, that's who. The comparison is in general really flawed.

Personally, I don't even really "prefer C over C++", because I know nothing in C++. Zero. I couldn't even write "hello world" with it.

---

### Post by 11jmb on 2012-06-14
obligatory FQA link: [http://yosefk.com/c++fqa/](http://yosefk.com/c++fqa/)

I personally prefer C because of its simplicity. As a simple example, K&R is less than 300 pages long, while its cousin by Stroustrop is over 1000, and I think both go into similar levels of detail.

Another reason I prefer C is the style. C++ created a lot of unnecessary constructs (many of which have been backported to C, but it is still not the C style to use them) such as inline functions instead of macros, references, const instead of #define, and a few more. Some C++ features are overused, like exceptions (only really needed for constructors, overloaded operators, and dtors), overloaded operators (such as bitwise shift operators for printing reading in iostream), dynamic_cast (the C++ style is to use this for everything, when it is only really needed for objects)

The main reason that I do not use C++ when I don't have to, though, is that I just don't see the point. You use C when performance is absolutely critical. Even though you can write C-like code in C++, the purpose of the language is to provide high-level constructs for faster development when performance is not critical. The classic tradeoff of developer time vs. runtime. When performance is negotiable, Python wins over C++ in my book

---

### Post by trent.josephsen on 2012-06-14
> **codemaniac said:**
> You can find some good reading on the below link .

[http://unthought.net/c++/c_vs_c++.html](http://unthought.net/c++/c_vs_c++.html)
An interesting piece, but I'd like to offer a counterpoint.

The author looks at simple problems that benefit from the high-level features of C++, and notably the STL. He then goes on to say that this makes C++ a better language.

For problems like the ones described, **I would not even consider using C**. If you are presented with a problem like counting word frequencies, and your first inclination is to use C, it's probably because C is the only language you know. **The same applies for C++.** I can write a Perl script that does the same thing in under a minute. Is it faster? Maybe, maybe not; it probably doesn't matter, because *programmer time is usually more valuable than machine time.*

C used to be a great all-around general purpose language. With the advent of higher level languages its niche shrunk. Now (aside from old programs written in C) it's mainly the domain of hardware drivers, kernels, low-level system utilities, and embedded systems.

C++ is now in the situation C was in a few decades ago: its niche is shrinking. But **C++ doesn't have a fallback**. On the one hand, it can't effectively compete with higher level languages for speed of development; on the other, it can't compete with C and assembly for size and agility.

I think C++ is dying a very slow and painful death. Most of the programs that would traditionally be good applications for C++ have succumbed to cheaper, faster computers and can be done for less investment overall in Java or Python. Like Microsoft is mostly abandoning C++ in favor of .NET.

That's not to say there isn't a market for C++ programmers -- there is, and there will be for decades to come. There's still a market for COBOL programmers, for crying out loud. But the linked article ignores the technological implications of C++ as opposed to C in favor of just saying "C++ is a better language."

@OP: I like C better than C++ personally because it has a cleaner design and I prefer the style of good C programs over that of good C++ programs. If I find C doesn't meet my needs, I turn to Python, not C++.

---

### Post by Bachstelze on 2012-06-14
> **trent.josephsen said:**
> 
For problems like the ones described, **I would not even consider using C**. If you are presented with a problem like counting word frequencies, and your first inclination is to use C, it's probably because C is the only language you know. **The same applies for C++.** I can write a Perl script that does the same thing in under a minute. Is it faster? Maybe, maybe not; it probably doesn't matter, because *programmer time is usually more valuable than machine time.*

Even Perl is overkill IMO. I would just do

```
cat file | tr ' ' "\n" | sort | uniq | wc -l
```

EDIT: I just tried this on a txt of the complete works of Shakespeare from Project Gutenberg:

```
firas@av104151 ~ % time (cat shakespeare.txt | tr ' ' "\n" | sort |uniq|wc -l)
   83715
( cat shakespeare.txt | tr ' ' "\n" | sort | uniq | wc -l; )  1.20s user 0.03s system 5% cpu 22.494 total

```

So performance isn't even that bad.

---

### Post by satsujinka on 2012-06-14
Additionally, the C++ examples are only clearer to read due to the "standard" nature of the library code used. I could easily write a library that cleans up the C code to the same level of clarity. The only reason you might not understand it at first glance would be because this library in question isn't "standard."

In that regard, the STL is "better" than the standard libraries of C. However, standard libraries != the language itself. 

As an aside, I find the namespace syntax to be hideous. There's really no reason that namespaces couldn't use the same syntax as structures (like, you know, every other language that has a qualified import concept.) I realize that you can use "using namespace ..." but having to work around the language seems like a waste of time to me.

---

### Post by Bachstelze on 2012-06-14
> **trent.josephsen said:**
> 
If I find C doesn't meet my needs, I turn to Python, not C++.

This is exactly why I don't know C++ and have no intention of learning it. C, Python, and the shell tools provide everything I need for any kind of serious programming. And for non-serious programming, Haskell or Ada are a lot more fun than C++ seems to be.

---

### Post by trent.josephsen on 2012-06-14
> **satsujinka said:**
> Additionally, the C++ examples are only clearer to read due to the "standard" nature of the library code used. I could easily write a library that cleans up the C code to the same level of clarity. The only reason you might not understand it at first glance would be because this library in question isn't "standard."

In that regard, the STL is "better" than the standard libraries of C. However, standard libraries != the language itself. 

I agree with your conclusion, but not your reasoning, so I'm going to play devil's advocate for a moment and defend C++. <shudder>

A programming language is only as good as the libraries available for it, and what a language makes easy is largely limited by what's possible without installing a ton of third-party libraries. One of Python's most widely touted strengths is its large standard library (often described by the phrase "batteries included").

Furthermore, C++ has flexibility: you can write C-like, close-to-the-hardware code one minute and turn around to use high-level constructs and advanced techniques the next. Using C++, you can write computationally intensive modules that run nearly as fast as possible, linking them directly to flexible high-level code without having to switch between languages or interface them together. That's why C++ is often used for games and complex desktop applications: it provides excellent performance where needed along with a large standard library and a grab bag of advanced language constructs that speed development time.

---

### Post by the_unforgiven on 2012-06-15
One of the reasons why C++ is still going strong has more to do with its abilities in simplifying modelling of application-domain concepts into code (which coupled with compiled-to-native-code nature of C++ makes for an excellent performing implementation).

In case of C, you end up viewing everything from computer memory's point-of-view - everything as data and functions.

This, I believe, is the primary reason why C++ is vastly popular for implementing GUI toolkits (compare QT (C++) with gtk+ (C)).

Again, I'm of the opinion that what tool to use depends on both the developer's own preferences as well as the problem-at-hand itself.
Some problems may have simpler solutions when implemented using C++ than C.

---

### Post by gardnan on 2012-06-15
I would say I prefer C over C++ but...

Saying that you prefer C over C++ is like saying you prefer a hammer over a wrench. It all depends on the problem being solved. In general, if the problem at hand is easily modeled by a system of interactive objects then it would be better to use C++. If something needs to be faster, and has an inherently procedural structure, then C is the way to go.

---

### Post by satsujinka on 2012-06-15
> **trent.josephsen said:**
> I agree with your conclusion, but not your reasoning, so I'm going to play devil's advocate for a moment and defend C++. <shudder>

A programming language is only as good as the libraries available for it, and what a language makes easy is largely limited by what's possible without installing a ton of third-party libraries. One of Python's most widely touted strengths is its large standard library (often described by the phrase "batteries included").

Furthermore, C++ has flexibility: you can write C-like, close-to-the-hardware code one minute and turn around to use high-level constructs and advanced techniques the next. Using C++, you can write computationally intensive modules that run nearly as fast as possible, linking them directly to flexible high-level code without having to switch between languages or interface them together. That's why C++ is often used for games and complex desktop applications: it provides excellent performance where needed along with a large standard library and a grab bag of advanced language constructs that speed development time.
I'll happily admit that libraries are a huge part of what makes a language. Which is one of the reasons why I almost always choose Go over C (aside from Go code generally looking cleaner.) However, the other factor is syntax/features. Generally, all of C++'s additional features suffer from terrible syntax, are harmful, or just generally of little benefit (namespaces, multiple inheritance, and i/o operations like cout respectively, you're free to disagree with these examples as they're mostly opinion.)

---

### Post by trent.josephsen on 2012-06-15
> **satsujinka said:**
> I'll happily admit that libraries are a huge part of what makes a language. Which is one of the reasons why I almost always choose Go over C (aside from Go code generally looking cleaner.) However, the other factor is syntax/features. Generally, all of C++'s additional features suffer from terrible syntax, are harmful, or just generally of little benefit (namespaces, multiple inheritance, and i/o operations like cout respectively, you're free to disagree with these examples as they're mostly opinion.)

I'll admit C++'s namespace syntax isn't what I would have come up with, but I don't think it's a bad solution to the problem. Namespace resolution is fundamentally a different thing from accessing members of a composite object, and you can make a strong case that using . has the potential to confuse when used for both operations interchangeably. In any case, weird namespace syntax isn't a reason to dismiss the entire language out of hand.

As for multiple inheritance, I'm sorry, I legitimately can't agree with you there. Multiple inheritance is not often useful, but when it is it's hard to work around not having it, and enforcing single inheritance only seems like such an arbitrary rule.

cout I think was a stronger argument for C++ having awful syntax :)

> **gardnan said:**
> Saying that you prefer C over C++ is like saying you prefer a hammer over a wrench. It all depends on the problem being solved. In general, if the problem at hand is easily modeled by a system of interactive objects then it would be better to use C++. If something needs to be faster, and has an inherently procedural structure, then C is the way to go.

It's possible, and sometimes easy, to beat C for speed in C++, as codemaniac's link illustrates. That combined with the fact that you aren't obligated to use any of C++'s extra features, and can simply use it *almost* as a drop-in replacement for C if the application demands, weakens your argument significantly. C++ handles procedural structure in exactly the same way as C. (Granted, writing C in C++ is an abomination your maintenance programmers will hate you for.)

Switching sides again...

Sure, there are cases when C++ has a clear advantage over C. But there are very few cases when C++ has a clear advantage over C **and** a clear advantage over a higher level language like Java or Python. So, in my personal opinion, it's not useful to ask "Is C or C++ better for X?" Instead, you should ask "Is there a better language for X than C or C++?"

Significantly more than half the time, I think, you will find that C++ is beaten either on one side or the other. C is smaller and easier to port to new architectures when C++'s extra features aren't necessary. Higher level languages have the extra features without all the syntactic cruft of backwards compatibility with C. (Improving JIT compiler technology and Moore's law make the performance issue more or less moot in that area.)

In short, C++ is often a *better* choice than C, but it is rarely if ever the *best* choice for new development.

---

### Post by youknowme on 2012-06-15
I started out studying C, then switched to C++ for no particular reason in 1998.

There are *certain people* who seem to slag off C++, but the fact is that any programming language is only as good as it's user. Another fact is that C++ is a challenging language to learn and *certain people* perhaps avoid it for that reason.:(

It really makes me laugh when i hear things like C++ cant do this or that.  :) It is well documented that *everything that is achievable in C is also achievable in C++*. That is a fact whether the task is low level operating system code, embedded pci devices or whatever.

I am glad that i went through the hard task of learning C++.:popcorn:

---

### Post by N0oki3 on 2012-06-15
I "had" to learn in my high school (computer tehnician) c++, python, php, javascript. And from all, I find c++ most useless and hardest to learn (might be just me...since it was first language i had to learn)

---

### Post by 11jmb on 2012-06-15
> **youknowme said:**
> 
There are *certain people* who seem to slag off C++, but the fact is that any programming language is only as good as it's user. Another fact is that C++ is a challenging language to learn and *certain people* perhaps avoid it for that reason.:(


So I dislike C++ because I'm unintelligent and/or lazy? What about Brainfuck or Malbolge? Are those languages only as good as their users?

> **youknowme said:**
> 
It really makes me laugh when i hear things like C++ cant do this or that.  :) It is well documented that *everything that is achievable in C is also achievable in C++*. That is a fact whether the task is low level operating system code, embedded pci devices or whatever.

I am glad that i went through the hard task of learning C++.:popcorn:


C++ was designed to be a superset of C, you you can still write code that is C-like. Once you start using features that are not part of the C-like subset, such as STL containers & virtual functions, you are using features that a) degrade performance and b) are easier to implement in higher-level languages. 

When performance is critical, yes *everything that is achievable in C is also achievable in C++* but at that point you're pretty much writing C anyway, the only differences being small things like new/malloc. The purpose of higher-level constructs is to spare developer time at the cost of memory and cycles. As I explained before, once it is determined that performance is negotiable, you're going to save more valuable development time by selecting Python or Perl over C++.

---

### Post by CptPicard on 2012-06-15
> **youknowme said:**
> 
There are *certain people* who seem to slag off C++, but the fact is that any programming language is only as good as it's user. 

It really is no excuse; any language is as good as its user -- even intentionally nasty ones such as Malbolge, but the job of the language is to be a tool. There is inherent *complexity* in a problem and then *complication* introduced by the language; overcoming the latter is no worthy intellectual feat. On the other hand, a correctly designed language can introduce you to ideas you would never have thought of.

> Another fact is that C++ is a challenging language to learn and *certain people* perhaps avoid it for that reason.

It just has lots of quirks to memorize. Admittedly it's a worthy attempt to introduce some commonly needed stuff on top of C. It does show all the symptoms of "organic growth", though.

> 
It really makes me laugh when i hear things like C++ cant do this or that.  :) It is well documented that *everything that is achievable in C is also achievable in C++*.

Theoretically, anything is achievable in anything, and when you exclude the domain-specific issues (such as hardware dependencies), what is left are the *universally* interesting things. It is these things that should be introduced ASAP in particular to the learner of computation, without unnecessary hoops to jump through.

The reason why we have programming language design as a subfield of CS *at all* is that we have this idea that certain ways of constructing a programming language are better suited for the human brain in general. Let us make use of this.

> I am glad that i went through the hard task of learning C++.:popcorn:

Try Lisp next. Trivial on the surface, very profound when you start thinking about it.

---

### Post by CptPicard on 2012-06-15
> **11jmb said:**
> 
When performance is critical, yes *everything that is achievable in C is also achievable in C++* but at that point you're pretty much writing C anyway

It is very rare that I find myself "defending" C++, but IMO this is wrong. The difference comes from the strict typing of C++ that C does not have; in C code you often end up writing lots of pointer indirection that you have to eventually cast out of. C++ allows carrying around more strict type information, especially with templates, that in the end allows for more compiler inlining.

---

### Post by Simian Man on 2012-06-15
C is a very elegant language for what it was designed to be: a portable assembly language.  It is great for systems programming tasks.  Unfortunately, for whatever reason, people use C for many other programming domains where it is horribly wrong-footed, like desktop applications.  This led to people discovering that they wanted things like classes, exceptions and templates to make their lives easier.  Instead of finding a language that fit their problem domain better, they bolted the features they wanted onto C, which has given us the horrible amalgamation known as C++.

I would rather program in C++ than C for most tasks, but that's only because most tasks are not suited for a systems programming language.  Basically C is great at what it's good for, C++ is not really suited for anything, and both languages are terribly over-used.

---

### Post by satsujinka on 2012-06-15
> **trent.josephsen said:**
> I'll admit C++'s namespace syntax isn't what I would have come up with, but I don't think it's a bad solution to the problem. Namespace resolution is fundamentally a different thing from accessing members of a composite object, and you can make a strong case that using . has the potential to confuse when used for both operations interchangeably. In any case, weird namespace syntax isn't a reason to dismiss the entire language out of hand.

As for multiple inheritance, I'm sorry, I legitimately can't agree with you there. Multiple inheritance is not often useful, but when it is it's hard to work around not having it, and enforcing single inheritance only seems like such an arbitrary rule.

cout I think was a stronger argument for C++ having awful syntax :)

Namespaces are very much like classes. In C++ they are in essence classes of classes/structs/functions/variables. Classes in turn are an expansion of structs, which is why they share syntax and why namespaces should too. 
Namespaces are also very similar (if not identical to) modules. Off the top of my head, I can think of two languages that use dot notation for modules: Go and Haskell. Mind you, they only use dot notation for qualified imports (Go is qualified by default and Haskell isn't,) but so too does C++. By using the "using namespace" feature you're essentially turning off a qualified import.
Which isn't to say that C++'s namespace syntax is reason to dismiss the language, however, I still have full rights to think it's ugly. ;)

Personally, I've never used multiple inheritance. So I'll accept that it may be very useful. However, I've been told (and agree with) that multiple inheritance does lead to ambiguity issues: ex. if you inherit from two classes with the same method name, and call the method, what gets executed?
Maybe this is similar to novice mistakes we all make with any new feature (new to us at least) and this never happens in real code. However, in real code I've never felt the need to use single inheritance either*... so multiple inheritance certainly isn't going to be very impressive to me.

So not only is cout bad syntax but of little benefit? Ouch.

*By which I mean that I tend to use interfaces for common behavior and composition for common implementation.

---

### Post by trent.josephsen on 2012-06-15
> **Simian Man said:**
> C is a very elegant language for what it was designed to be: a portable assembly language.  It is great for systems programming tasks.  Unfortunately, for whatever reason, people use C for many other programming domains where it is horribly wrong-footed, like desktop applications.  This led to people discovering that they wanted things like classes, exceptions and templates to make their lives easier.  Instead of finding a language that fit their problem domain better, they bolted the features they wanted onto C, which has given us the horrible amalgamation known as C++.

The main reason for C's popularity in such domains is that before many of today's languages were invented, C often was the best choice.

Similarly, C++ still makes sense for a shrinking niche of applications. I mentioned games before because many game programmers really do need to worry about combining excellent performance with object-oriented design. In such a case, I wouldn't condemn the use of  C++.

What I'm really trying to say can be summed up rather succinctly:

1) There is currently no viable replacement for C in systems and embedded programming.
2) C++ is less well designed than C, but that fact alone does not make C better than C++ for any given purpose.
3) Other languages exist that are often preferable to C or C++, trading performance for ease of use.
4) Cheaper, faster computers will continue to make the concern of code performance less and less relevant.

---

### Post by 11jmb on 2012-06-18
> **CptPicard said:**
> It is very rare that I find myself "defending" C++, but IMO this is wrong. The difference comes from the strict typing of C++ that C does not have; in C code you often end up writing lots of pointer indirection that you have to eventually cast out of. C++ allows carrying around more strict type information, especially with templates, that in the end allows for more compiler inlining.

That's a good point. I should have explained myself better. I did not mean to suggest that the two languages are the same. My point was that when people begin to use C++ to match the runtime performance of C, their style becomes more similar to the C style (e.g. raw pointers instead of STL containers). I consider C++ features such as const/inline/new, which admittedly allow for more type safety than #define/#define/malloc, to be a matter of preference rather than a significant shift in style. On the other hand, the OO approach of using "smart pointers" and STL in the C++ style rather than primitives in the C style offers a much sharper contrast. When people really need to squeeze out constants and fit the memory footprint of a small device, the OO approach starts to get in the way, and people opt for the programming style preferred by C developers.

> **Simian Man said:**
> C is a very elegant language for what it was designed to be: a portable assembly language.

I agree almost entirely with your post, but C also has a huge advantage over assembly in expressive power, not just portability.

---

### Post by dagoth_pie on 2012-06-18
> **11jmb said:**
> That's a good point. I should have explained myself better. I did not mean to suggest that the two languages are the same. My point was that when people begin to use C++ to match the runtime performance of C, their style becomes more similar to the C style (e.g. raw pointers instead of STL containers). I consider C++ features such as const/inline/new, which admittedly allow for more type safety than #define/#define/malloc, to be a matter of preference rather than a significant shift in style. On the other hand, the OO approach of using "smart pointers" and STL in the C++ style rather than primitives in the C style offers a much sharper contrast. When people really need to squeeze out constants and fit the memory footprint of a small device, the OO approach starts to get in the way, and people opt for the programming style preferred by C developers.
Interestingly enough, I've always preffered to use dynamic arrays to STL containers. I've also never bothered to use smart pointers. And I specifically only use (const wherever convinient) references to pass variables around in place of pointers so that I know not to free them.

I think that'd be why I struggle to see the difference between C and C++. I'm getting a little bit sick of C# though, designed to be hard to do the low level stuff.

---

### Post by 11jmb on 2012-06-18
> **dagoth_pie said:**
> Interestingly enough, I've always preffered to use dynamic arrays to STL containers. I've also never bothered to use smart pointers. And I specifically only use (const wherever convinient) references to pass variables around in place of pointers so that I know not to free them.

I think that'd be why I struggle to see the difference between C and C++. I'm getting a little bit sick of C# though, designed to be hard to do the low level stuff.

The big differences between the two languages boil down to high-level constructs that are intended to save developers' time at the cost of performance. As previous posts have pointed out, there are some niche areas where C++ is a good fit, but in general, there is almost always a better tool for the job.

As for C#, it is more like Java than C or C++. It is better than either C or C++ for high-level tasks, but still not my favorite.

---

### Post by nvteighen on 2012-06-18
The problem is that C++ is a mess and its existence was safe until somebody came up with languages that did exactly the same without confusing and over-complex semantics. Its mess comes from the idea that you can coherently build a language that is both high- and low-level.

---

### Post by xb12x on 2012-06-18
> **dagoth_pie said:**
> I'm getting a little bit sick of C# though, designed to be hard to do the low level stuff.

C# was never intended to be low-level. 

C# was designed by Microsoft to be Microsoft's answer to Sun's Java. Since Microsoft did not own and control Java they replaced it.

---

### Post by LemursDontExist on 2012-06-18
For my own personal use, I have trouble coming up with projects which aren't better handled by C, Python, or some combination of the two than by C++.  Python provides vastly faster development, and for critical portions of the code that need to run fast, I can drop into C and write an extension to do what I want.

That said, I think people are being a little overly negative about C++ here.  Specifically, for larger projects where all aspects of performance are critical, C++ really does shine.  

As an example, C++ is the natural language for writing a web browser.  It's notable that both Firefox and Chromium are written in C++.  The way people use web browsers you want the maximum possible performance for every operation, and that rules out most high level languages, but the project is complex enough that writing it all in C would be much more difficult.

Another example is word processors.  I'm not a big fan of Microsoft, but Word is dramatically faster and more stable than OpenOffice Writer, and I think a lot of that is probably attributable to the choice of C++ over Java.

Anyway, for the most part I agree with the sentiments of this thread.  I certainly avoid C++ if I can.  But I think C++ is going to be around for a while yet!

---

