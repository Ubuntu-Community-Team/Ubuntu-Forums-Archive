---
title: "Already know Python, learn C, C++ or Vala?"
date: 2009-04-07
forum: Programming Talk
---

### Post by brynjarh on 2009-04-07
I'm looking into expending my programming knowledge by learning C, C++ or Vala ( [http://live.gnome.org/Vala](http://live.gnome.org/Vala) ).

I already know Python quite well and am mainly looking at C, C++ and Vala to extend Python but also to be able to read tutorials, books and such that "talk in C".

If you were in my position which would you focus on and why?

---

### Post by CptPicard on 2009-04-07
I tend to suggest C as the next language after python, as it's easy to extend python in C. And, well, because after you've got programming basics down you might just as well learn C as you want to know it anyway at some point. C++ is a much more complex beast on its own... and Vala, no idea really.

---

### Post by gtr32 on 2009-04-07
> **brynjarh said:**
> If you were in my position which would you focus on and why?

Depends on what you want to do. C++ would be the natural choice unless you're interested in doing low level programming. I wouldn't rule out C# either. Vala, well, if it is well suited for your purpose.

---

### Post by namegame on 2009-04-07
I'm definitely not an expert by any standards, but I feel that C, in comparison to many other languages, is a quite simple and succinct language. 

It's not terribly difficult to learn. I think the most difficult aspects for me were dynamic memory management and pointer arithmetic, which are tied together. That being said, once you wrap your head around these concepts, you learn to appreciate C for what it is.

---

### Post by soltanis on 2009-04-07
If you got a handle on Python and basic programming concepts, C is the next step.

In some ways, C is far more easy (as K&R wrote in their book, it is quite possible for you to know the entire language); but it is much more subtle (pointers are godly powerful, but tricky bastards) so in some ways, harder.

But C will really teach you how your computer really operates (your Kernel is written in it) and give you a new appreciation for programming. C++ is way too complicated (no one on Earth, probably not even Bjarne himself knows the entire language) in my opinion, and Vala is cool, but not widely used (teaching yourself might pose a challenge).

---

### Post by OutOfReach on 2009-04-07
I recommend C, since I was also in your situtation. (I learned Python then C). It's not as hard as it seems.

---

### Post by Sinkingships7 on 2009-04-07
Definitely learn C. I don't know anything about Vala. C++ probably won't be worth your time investment.

---

### Post by gtr32 on 2009-04-07
> **soltanis said:**
> C++ is way too complicated

At some point you do need to pick up OO language. Why learn C instead? Because it is "easier"? It isn't easier but it certainly is less powerful.

There is no right answer, it all depends on what you need it to do. IMHO it is easier to learn C++ and then learn C, rather than the other way.

---

### Post by soltanis on 2009-04-07
> **gtr32 said:**
> At some point you do need to pick up OO language. Why learn C instead? Because it is "easier"? It isn't easier but it certainly is less powerful.

I'm not going to get into the nonsense arguments of which paradigm/programming language is more "powerful", suffice it to say that if C++ has any power, it inherits it from C.

If you want to pick up an object-oriented language, Java is a fine substitute (or C#, or Python even). Actually, C is capable of object-orientation (through extensive [ab]use of the preprocessor), which is what the GObject system of Gnome is based on.

---

### Post by gtr32 on 2009-04-07
> **soltanis said:**
> I'm not going to get into the nonsense arguments of which paradigm/programming language is more "powerful", suffice it to say that if C++ has any power, it inherits it from C.

Maybe powerful was a poor choice of wording, lets just say C is much more cumbersome and less productive. ;)  

> **soltanis said:**
> 
If you want to pick up an object-oriented language, Java is a fine substitute (or C#, or Python even).

Java, C#, C++, pick your poison. However, pick it according to what you're planning to do. Is C easier than C++? I don't think it is. Is C a better choice than C++? Impossible to say without knowing what it will be used for and in what environment. For general purpose language I see very little reason to pick C over C++.

---

### Post by Jiraiya_sama on 2009-04-08
I am currently learning C++/C and I can only say that both are very fun. C++ recieves a lot of unwarranted hate due to being complex, but I love complexity. My advice is to get a good C++ or C book (K&R The C Programming language for C and C++ Primer 4th ed for C++) and work through the language bit by bit.

---

### Post by majamba on 2009-04-08
kind of like more C++ than c, like being able to objects -orienting programming and multiple inheritance,  i think c is harder than C++


but then ofcourse i started with java because that was the only class offered in high school
the easiest language to learn is java

---

### Post by soltanis on 2009-04-08
Compare:

The C Programming Language (2nd ed) 272 pages (including a language overview, a discussion of UNIX functions, working examples of storage allocators and a directory lister, the entire language grammar, a manual, and the standard library reference)

The C++ Programming Language (3rd ed) 975+ pages (including more or less the same thing).

C more cumbersome? ORLY? By my calculations, C is looking to be about 1/3 as cumbersome as C++ (which makes sense, since C++ duplicates all the facilities that C already provides about 3 times).

But anyway, we're recommending languages post-python learning; its up to you to decide which one you like/need to apply. There are plenty of situations where C++ is more suited and more concise than C. Just as, you know, there are plenty of situations where NASM assembly is more readable and concise than Visual Basic.

---

### Post by slavik on 2009-04-08
> also to be able to read tutorials, books and such that "talk in C".

you answered your own question, I think.

---

### Post by gtr32 on 2009-04-08
> **soltanis said:**
> By my calculations, C is looking to be about 1/3 as cumbersome as C++ (which makes sense, since C++ duplicates all the facilities that C already provides about 3 times).

Not as simple. I have a Canon 10D SLR camera which has a lot more functions than your regular point-and-shoot camera. It does not mean the 10D is hard to use at all, quite the opposite, you can take pictures just as easily as with PAS camera. If I choose to use the advance options that are available to me, I can. Sure, I just have to learn how to use them first.

On the other hand, with PAS camera you're restricted to just take your basic pictures. Dark? Too bad, no shutter control. SLR, no problem, lets play around with the shutter to see what happens...

---

### Post by slavik on 2009-04-08
the C vs. C++ argument stop now.

---

### Post by CptPicard on 2009-04-08
> **gtr32 said:**
> Maybe powerful was a poor choice of wording, lets just say C is much more cumbersome and less productive. ;)  

They are cumbersome in their own ways.. C++ makes you satisfy the language a lot and know the "tricks of the trade", C just makes you build everything from scratch. Especially when building well-defined, relatively small library style stuff, I prefer the latter, even going to the length of usually hacking up an object system. Which, of course, recently led me to investigate Objective-C...

> For general purpose language I see very little reason to pick C over C++.

Binary compatibility is the big one for libraries. I'm not a huge "use C everywhere at all costs so you seem manly" propononent of course, but that is the big reason for my C use, when I do use it.


> **Jiraiya_sama said:**
> C++ recieves a lot of unwarranted hate due to being complex, but I love complexity.

Is it really unwarranted, or are you just still at the phase where you are easily impressed by things that are "hard" regardless of the reason, or are you already able to discern for yourself when complexity represents genuine conceptual power? (They rarely are the same thing IMO)

---

### Post by nvteighen on 2009-04-08
> **slavik said:**
> the C vs. C++ argument stop now.
Thanks. It's absurd to compare C and C++ basing ourselves on OOP, when C can use OOP as well as C++ (look at GTK+). And the OP already knows Python, so he knows OOP...

I'd go for C after Python. Vala is a weird OOP C-like intermediate language which you pass through a preprocessor that returns an equivalent GObject C code.

---

### Post by ZuLuuuuuu on 2009-04-08
> **nvteighen said:**
> Vala is a weird OOP C-like intermediate language which you pass through a preprocessor that returns an equivalent GObject C code.

Actually, Vala is a compiler. The different thing about it is that it produces C output instead of assembly or machine language like most other compilers do.

Programming GTK+ applications with Vala is fun. But to extend Python, to extend your general programming knowledge I think C is more suitable.

---

### Post by gtr32 on 2009-04-08
> **CptPicard said:**
> Especially when building well-defined, relatively small library style stuff, I prefer the latter, even going to the length of usually hacking up an object system.

I have been saying all along that the choice of a language depends on the use and environment. I have done embedded software (mainly UI) on a device that did not have much of resources to spare (think of early 90's mobile phone), I have also done desktop GUI's with numerous tools, including the original VB, NI's CVI which is C, Visual Studio etc.

I wish there was one language that would fit all my needs but unfortunately that isn't so. 

> **CptPicard said:**
> Is it really unwarranted

What is so complex about using C++? I'm not trying to argue if it is or isn't, just want to know why you feel it is complex. Maybe it is just me that I don't see the complexity. Why couldn't someone start with C++ doing pretty much what C does but add a few basic things (data encapsulation, possibly inheritance)? They can learn about polymorphism later, no?

---

### Post by nvteighen on 2009-04-08
> **gtr32 said:**
> 
What is so complex about using C++? I'm not trying to argue if it is or isn't, just want to know why you feel it is complex. Maybe it is just me that I don't see the complexity. Why couldn't someone start with C++ doing pretty much what C does but add a few basic things (data encapsulation, possibly inheritance)? They can learn about polymorphism later, no?

Because, for that, you better use Objective-C, which is much cleaner...

---

### Post by eye208 on 2009-04-08
I strongly recommend C++ because of its superior resource management.

In C you have to track each pointer manually and release each shared resource by hand. In C++, if you adhere to [RAII](http://en.wikipedia.org/wiki/Resource_Acquisition_Is_Initialization) design principles, resource management is fully automatic. You need not worry about memory leaks, double deallocation, [dangling pointers](http://en.wikipedia.org/wiki/Dangling_pointer) etc. It's built into the language, similar to garbage collection in Java, but much faster.

---

### Post by wicky_ts on 2009-04-08
But if u are not familier with pointers and those stuff better to start with C.

---

### Post by eye208 on 2009-04-08
> **wicky_ts said:**
> But if u are not familier with pointers and those stuff better to start with C.
Why?

Because you don't know what a concrete wall is until you bang your head against it?

---

### Post by gtr32 on 2009-04-08
> **nvteighen said:**
> Because, for that, you better use Objective-C, which is much cleaner...

If the choice was not between C and C++, but included others as well, I would prefer C# (see my first post). ;)

I'm curious why you think OC is cleaner than C++, can you provide a brief example?

---

### Post by CptPicard on 2009-04-08
> **gtr32 said:**
> 
I wish there was one language that would fit all my needs but unfortunately that isn't so.

Actually, I am finding more and more that Common Lisp is such a language. Pretty much all of my "but I have issues doing X" end up being answered, and everything within a minimal, very internally consistent system too... it can fluidly move between abstraction levels as well when required. At the lowest abstraction level you can essentially have a very good idea of the sort of asm that gets generated, and directly influence it. At the highest level you're just composing functions to produce data transformations according to some domain-specific language you wrote...

> 
What is so complex about using C++? I'm not trying to argue if it is or isn't, just want to know why you feel it is complex.

C++ really is the most complex language I have used (in a subjective sense, take it or leave it), and not in the good sense. I can use it, but never enjoyed doing so, because there are so many things to take into account throughout the design and things to work around. I find myself spending most of the time working with the language instead of the problem -- it never just gets out of my way.

The issues lie somewhere between the pervasive low-levelness of the language and the attempts at abstraction that are being implemented  on top of it -- and even those abstractions don't actually end up being so great in the big picture. Oftentimes this seems like a fit that gets the worst of both worlds. Your typical higher-level C++ expression requires a lot of understanding of underlying infrastructure machinery so that your usage (or implementation) of it does not just break in subtle ways. Just think of the nontrivial pointer management you need to do when messing with passing/returning large objects -- this is essentially a trivial use case, but ends up having a need for auto-pointers... which gets me to the next point...

Modern C++ is an interesting development -- template metaprogramming (which is nowhere near as universally strong as lisp macros, mind you) seems to for example eventually pull everything into headers these days (see the boost graph library), which was something I saw coming a long long time ago...

Anyway, the point is that we're dealing with something that grows organically, and that could use a redesign. Personally I find that D is a very interesting attempt at clarification of the whole thing, plus addition of some important core constructs such as closures.

> 
 Maybe it is just me that I don't see the complexity.

I am not saying that you can't become a very proficient C++ programmer. A lot of people who are, have issues judging the language critically though (and interestingly seem to lack exposure to anything else out there). It is an interesting phenomenon.

>  Why couldn't someone start with C++ doing pretty much what C does but add a few basic things (data encapsulation, possibly inheritance)? 

Perhaps. I never could use C++ (or any language) without trying to go all the way ;)

> They can learn about polymorphism later, no?

It has nothing to do with the polymorphism. Essentially, virtual functions and the assorted machinery is pretty much all that C++ would ever need IMO -- and ObjC does an interesting job at that (although at a runtime cost which admittedly might be a show-stopper).

One can always discuss the actual virtues of static-typed OOP in general though, but it's a whole different discussion... :)

---

### Post by nvteighen on 2009-04-08
> **gtr32 said:**
> 
I'm curious why you think OC is cleaner than C++, can you provide a brief example?

If you just want C with native OOP support, IMO, ObjC is much saner than C++. What I mean: it just adds a new bunch of features, very cleanwise indeed, but not breaking the semantic layer C tries to target to. C++, instead, with its annoying amount of high-level features used alongside to low-level features makes it harder to define which is the real semantic layer in which the language works. In a very simple way: if you write C code using a C++ compiler, you're clearly not using C++... if you write STL code, you're certainly using C++, but still relying on stuff that is part of C (memory management, pointers, preprocessor, stack, etc.).

Take for example this Obj-C code and you'll see the language is pretty clean and quite simple. (Ok, this is not the usual way to do it... you usually put the @interface in a header file):

```

#include <objc/Object.h>
#include <stdio.h>

@protocol ComplexNum
// Let's define a protocol called ComplexNum that specifies a "standard"

-(int)getReal;
-(int)getComplex;

@end

@interface Complex : Object <ComplexNum>
/* Here we define the Complex class interface, and we establish conformance to 
 * protocol ComplexNum */

{
@public
    int real;
    int complex;
}

// Methods prototypes

-(id)init:(int)re complex:(int)compl; // Override the usual init!

// Not needed, but here for clarity
-(int)getReal;
-(int)getComplex;

-(void)increase:(id<ComplexNum>)arg1; /* id is a generic type, but we ask the
                                       * arg1 object, no matter what it is, to
                                       * comply to the ComplexNum protocol */
-(void)printComplex;

@end

@implementation Complex : Object
// Implement!

-(id)init:(int)re complex:(int)compl
{
    real = re;
    complex = compl;

    return self;
}

-(int)getReal
{
    return real;
}

-(int)getComplex
{
    return complex;
}

-(void)increase:(id<ComplexNum>)arg1
{
    real += [arg1 getReal]; /* We are sure this will work, because of the
                             * protocol */
    complex += [arg1 getComplex]; 
}

-(void)printComplex
{
    printf("(%d, i * %d)", real, complex);
}

@end

int main(void)
{
    Complex *myComplex = [[Complex alloc] init:3 complex:6];
    
    [myComplex printComplex];

    [myComplex free]; /* This is a limitation from GNU's runtime. Apple's
                       * NeXTStep does Garbage Collection... */

    return 0;
}

```

The messaging system allows you to dynamically define methods for a certain class... That's done through the @selector() operator and other techniques I honestly haven't taken a deep look yet.

---

### Post by SKLP on 2009-04-08
I'd say C# ;-) It's IMO a very nice language (like a cleaned up version of C++ which runs a bit slower, but *A LOT* faster than e.g. python, which I like as well). You also get a nice IDE (MonoDevelop 2.0), and high-quality bindings to many libraries (e.g. Gtk#).

---

### Post by gtr32 on 2009-04-08
> **nvteighen said:**
> If you just want C with native OOP support, IMO, ObjC is much saner than C++.

That's the thing, I don't want C with OOP, I just said one can easily do with C++ what one can do with C. You don't have to use all of the features of C++ BUT you can easily start at a later date if you so wish. One major issue with OC is that is a niche language and most likely will continue to be so.

> **nvteighen said:**
> Take for example this Obj-C code and you'll see the language is pretty clean and quite simple.

Maybe it's the eye of the beholder but the syntax of OC to me is very messy looking, almost borderline ugly. I don't mean any offense by it, just how I see it (and it's not about the included headers). Could you explain the features that make this better approach to C++? 

Shouldn't these be protected or private members instead of public?

```

{
@public
    int real;
    int complex;
}

```

---

### Post by ibuclaw on 2009-04-08
> Why couldn't someone start with C++ doing pretty much what C does but add a few basic things (data encapsulation, possibly inheritance)? 
That is what I sortof did, on and off with C++ and C... but I soon found myself so heavily dependent on C libraries, headers and routines - along with the fact that I never used templates, strings, vectors, or any feature of the C++ language that I just dropped it altogether and just stuck with C...

Albeit, with a few sugary syntax definitions taken along the way, IMO, the use of "and", "or" and "not" appears more aesthetically pleasing than the rather rudiment "&&" "||" and the angry "!".

Have even started writing up my own header file to compensate my ignorance. This isn't all of it, but you get the general picture:
[http://paste.ubuntu.com/147323/](http://paste.ubuntu.com/147323/)

Should you use the idea of it? Probably not... but fortunately I'm not looking for a career in programming, so I have an uncaring view of what standard I choose to write in ;)

> **gtr32 said:**
> Shouldn't these be protected or private members instead of public?```

{
@public
    int real;
    int complex;
}

```
I think that was just a general example of the language. I wouldn't take every bit of it to heart.

IMO, OC is probably best left for those interested in Apple and GNU/Hurd Desktop development. Other than that, it appears to be a very intriguing language indeed. Though I think I may be better off looking elsewhere. Perhaps D ... I haven't really decided :)

Regards
Iain

---

### Post by soltanis on 2009-04-08
Maybe everyone missed it, but the C vs. C++ debate needs to be terminated. Like, now. It's going nowhere, anyway.

> **CptPicard said:**
> Actually, I am finding more and more that Common Lisp is such a language. Pretty much all of my "but I have issues doing X" end up being answered, and everything within a minimal, very internally consistent system too... it can fluidly move between abstraction levels as well when required.


CptPicard++;

CL, while I was learning it, was amazing. It blew me away; every feature I wished the language had, I could just write for myself, and then use it later! And it was never easier to write code that wrote code. It required that you completely rethink your design principles and the way you wrote programs (perhaps to the point where it would kill a C++ programmer, whoops, did I bring that into the discussion again?). Instead of writing objects, how about you write a closure? Instead of writing a function that parses some data, how about writing a function that writes a function to parse data in the way you specify?

---

### Post by gtr32 on 2009-04-08
> **soltanis said:**
> Maybe everyone missed it, but the C vs. C++ debate needs to be terminated. Like, now. It's going nowhere, anyway.

What is the problem when everyone seems to be respectful? If the discussion was turning into a flame war I would understand. If however it is a sacred subject, this will be my last post about C, OC or C++, although I was genuinely interested in why someone would prefer OC over C++. I guess there is plenty of web material to read about the subject as there is about any xxx vs yyy vs zzz language.

---

### Post by Black_Wolf_92 on 2009-04-08
Just out of curiosity, the only programming language learnt at my school is Javascript, and I know full well the basic structure of programming, but which language would you recommend learning (javascript is a little limited). Out of C, C++, Python etc, for someone who is pretty much a beginner programmer?

---

### Post by gtr32 on 2009-04-08
> **Black_Wolf_92 said:**
> Out of C, C++, Python etc, for someone who is pretty much a beginner programmer?

I have been hesitant to recommend anything with a garbage collector to a beginner but recently I have started to lean towards C# as good beginners language.

---

### Post by slavik on 2009-04-08
All valid points have been brough up, there is no agreement. I am closing this thread.

If you wish to read about languages that everyone would recommend for a beginner, search the Recurring Discussion forum.

brynjarh if you want this re-opened, we can discuss this through PM.

---

