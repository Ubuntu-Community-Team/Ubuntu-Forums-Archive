---
title: "Functional Programming"
date: 2012-12-30
forum: Programming Talk
---

### Post by tehcavil on 2012-12-30
What are all your thoughts on FP and why it doesn't get as much love as procedural and OOP.

---

### Post by Bachstelze on 2012-12-30
This belongs in recurring discussions...

---

### Post by Mikeb85 on 2012-12-30
I like functional programming.  I've been learning Ruby, but also dabbling in Clojure and OCaml, and I definitely prefer smaller classes, shorter functions, and immutable variables.  I also don't think there's a huge difference between OO and FP, both accomplish the same thing, just in slightly different ways, and it seems an OO language like Ruby can be written functionally, and OCaml, which is functional, has classes (if you want).  In Clojure you can also create Java classes.  

And functional programming does seem to get love, OCaml, F#, Haskell, Erlang are all used by large corporations, albeit not in a highly visible way.  Clojure is getting quite a bit of love for a language only a few years old, and F# has Microsoft's blessing.  Ruby, Python, and Scala can be written functionally, as can others I bet.  

And from dabbling in OO and FP, there really doesn't seem to be a huge difference apart from some catch phrases and hype on either side.  Then again, I haven't tried anything like Java or C++ since I'm learning programming for my own benefit and to write programs that I need, not to work for anyone else.

---

### Post by slavik on 2012-12-30
Because people have been brain dead since college and "a program is a series of instructions." Alan Turing learned the same thing.

We are not taught to think in terms of functions.

Think about the actions you need to take to get into a car and drive it. Now think about it in terms of functions and not having a "do this thing, then do this next thing."

---

### Post by xytron on 2013-01-01
Functional programming needs to be seen as just another programming tool.

I think the subject does suffer from a bit of a "bandwagon" mentality of late.  Some people make it sound as if functional programming is the solution to all programming problems.  We've all been doing it wrong for all these years.

Well that's very doubtful.  Functional programs solve certain programming problems well and imperative programming is best for others, sometimes the simplest solution is just to use a global variable.

It's not at all new, LISP the ancestor of all functional languages goes back to the 1960's.

Often when functional programming is taught or discussed the topic is treated in a very theoretical manner where the actual use of a functional language is not the main focus.

---

### Post by tehcavil on 2013-01-28
> **xytron said:**
> Functional programming needs to be seen as just another programming tool.

I think the subject does suffer from a bit of a "bandwagon" mentality of late.  Some people make it sound as if functional programming is the solution to all programming problems.  We've all been doing it wrong for all these years.

Well that's very doubtful.  Functional programs solve certain programming problems well and imperative programming is best for others, sometimes the simplest solution is just to use a global variable.

It's not at all new, LISP the ancestor of all functional languages goes back to the 1960's.

Often when functional programming is taught or discussed the topic is treated in a very theoretical manner where the actual use of a functional language is not the main focus.

It's true that there is no silver bullet to solve all programming problems, nevertheless, FP does solve many of the problems of OOP (state and concurrency/parallelism) as well as having a few additional benefits which will be fully realized with time.

FP languages tend to have higher levels of abstraction (Lisp, Haskell). This is a good thing as it trades CPU cycles for programmer productivity. 

No one denies that moving from assembly to structured programming was a good thing - although some people still write assembler (kernel hackers, etc), no one would think to write the vast majority of programs using nothing but labels and gotos/jumps. structured programmed offered a higher level of abstraction which most programmers would (now) find tedious to work without. 

Not everyone at the time agreed with this. As we know some people kept programming assembly even well into the 80's, by which time most were forced to used structured programming.

Later, object oriented came and largely superseded plain structured programming. And just like before most were opposed, and some even still are.

But aside from special cases, again such as kernels or anything else that would require mucking around in the low level details of the computer, most people would not write a dynamic web server page or even a GUI desktop app in ANSI/ISO C.

Because object oriented offered more safety and was superior with the cost of some overhead (again, a cost which is too high for certain projects, but not most). 

However, now the tide of programming history is turning again. Just like the assembler programmers who desperately tried to hold on to the past, with the cry of "structure this!", the object oriented folks continue to hold on to their paradigm because they are too set in their ways to learn FP.

With more and more cores on machines... Mutable state objects are the modern spaghetti code. And I firmly believe in a few decades, FP will supersede OOP as the dominant programming paradigm. 

Yes, there will still be special uses, just like  some still write assembler, and C now, some will continue to write, or at least maintain legacy OOP code in the future.

EDIT: also not to be a nitpicker but when LISP came out it really wasn't a functional language , it was dynamically scoped (breaks RT), had no TCO, etc. LISP only came to be associated with FP over time. The first real FP language was ML, and Acadamia really didn't start to get into FP till the 80's with SICP/Scheme and Miranda etc.

---

### Post by muteXe on 2013-01-28
Oh god, not again.

---

### Post by trent.josephsen on 2013-01-28
I will allow myself to be provoked, and apologize in advance if I cause offense.

> **tehcavil said:**
> FP languages tend to have higher levels of abstraction (Lisp, Haskell). This is a good thing as it trades CPU cycles for programmer productivity.
This is a feature that is generally desirable, but not specific to languages designed for functional programming, so I don't see how it's relevant.

> Later, object oriented came and largely superseded plain structured programming.
Eh, not really, in my experience. Lots of code, and not only old code but new code as well, is still essentially procedural.

> With more and more cores on machines... Mutable state objects are the modern spaghetti code. And I firmly believe in a few decades, FP will supersede OOP as the dominant programming paradigm.

You are confusing the advance of technology with the caprices of public opinion. Moving from machine code to FORTRAN was a question of making a compiler that would be cost-effective to use, in an era when machine time was more expensive than programmer time. The improvement in compiler technology made more powerful and more portable languages possible, but they still vary in how they approach problems. Beware the notion that the appropriate choice of programming paradigm must lead to well-implemented solutions.

If you have something to say in defense of the idea that the unique problems of the next decade or two will be particularly well-suited to a functional approach, feel free to speak in your capacity as a futurist and I will not suppose to contradict you. But so far you have given no analysis of the problems you expect the future to hold, nor evidence that functional programming is any better at solving them (nor today's problems) than the next best idea, and your prediction that functional programming shall become "the dominant programming paradigm" is (as far as I can see) entirely founded on your belief that one or two minor features is enough to take the entire programming industry by storm. This is just the same tired argument supported by the same overblown generalities.

(You also apparently labor under the unfortunate assumption that C and assembly and all such inferior languages are reserved for tiny market niches like compilers and device drivers. Although this is only tangentially relevant to the topic, I beg to remind you that vastly more software is written every day than just what runs on the spawn of Intel.)

---

### Post by slickymaster on 2013-01-28
_Functional Programming advantages:_
Manipulating programs is simpler
Proof of property
Transformation (eg optimization)
Concurrency exploited in a natural way
_Functional Programming disadvantages:_
"The world is not functional!"
Inefficient implementations
Primitive I/O mechanisms and formatation

_OOP advantages:_
All from imperative programming
Classes encourage data-centric design: modularity, reusability and extensibility
Increasing commercial acceptance

---

### Post by satsujinka on 2013-01-28
@trent
While it certainly won't be a lisp (or other) that "takes the industry by storm" it does seem that fp already has. In that all the top languages support fp. 

C#, C++, and Java (have added|are adding) in lambdas. You can't do lambdas in C, but with function pointers higher order functions are possible (which covers most of fp even if I wouldn't want to try CPS in C.) For example, NASA's coding guidelines essentially reduce down to a functional language (from C.)

It seems that nearly all of the scripting languages also support fp. JavaScript, Python, Perl, and Ruby do. From a quick google, it can also be faked in a shell.

The biggest issue is just that fp isn't advertised or taught. So even though all the common languages support it, there's relatively little noise.

EDIT:
@slickymaster
Nice leaving out any disadvantages of imperative/oop!

Also, none of your disadvantages of functional programming have any substance. 
The world may very well be functional (I don't know, are you a physicist?) I will accept that the common mode of thought might be imperative, but that's at worst a teaching issue.
The ML languages are frequently toe for toe with C in performance (Haskell occasionally manages, but is typically just behind Java due to how difficult it is to optimize laziness)
I/O in all functional languages is trivial. Certainly no harder than in imperative languages. I think what might irk people is the constraint that a pure language imposes on where I/O can occur, but this is a non-issue in impure languages (and is merely good design anyways.)

A more substantial claim against functional programming would be: Immutability can be difficult to work around, especially when the natural solution appears to require it.

---

### Post by CptPicard on 2013-01-28
> **satsujinka said:**
> You can't do lambdas in C, but with function pointers higher order functions are possible (which covers most of fp even if I wouldn't want to try CPS in C.)

Another important feature of functional programming languages are closures (that is, the scope you can access from within your lambda), and they essentially require garbage collection. Function pointers only get you kind of half the way. 

CPS requires general TCO, and I suspect I'd like to have closures to go with it as well at least if I don't want to build some kind of a explicit context every time I call a continuation...

---

### Post by satsujinka on 2013-01-28
> **CptPicard said:**
> Another important feature of functional programming languages are closures (that is, the scope you can access from within your lambda), and they essentially require garbage collection. Function pointers only get you kind of half the way. 

CPS requires general TCO, and I suspect I'd like to have closures to go with it as well at least if I don't want to build some kind of a explicit context every time I call a continuation...
As I said, I wouldn't want to do CPS in C.

I won't deny that closures are an important part of fp, but they're not necessary for most of the advantages (primarily, they serve as a more convenient way of doing things.) So my point was that function pointers let you do the interesting things of fp, even if they aren't ideal.

To this end, the Gang of 4 Command Pattern technically gives you higher order functions by passing in a function object. This is even more ugly than function pointers, but it enables the same behavior.

---

### Post by CptPicard on 2013-01-29
> **satsujinka said:**
> 
I won't deny that closures are an important part of fp, but they're not necessary for most of the advantages (primarily, they serve as a more convenient way of doing things.)

I personally find my FP to be rather crippled without them. Certainly you can always build a context structure and pass it along the call stack, but even that doesn't give it an arbitrary lifetime and most certainly won't just magically compute it for you...

---

### Post by satsujinka on 2013-01-29
> **CptPicard said:**
> I personally find my FP to be rather crippled without them. Certainly you can always build a context structure and pass it along the call stack, but even that doesn't give it an arbitrary lifetime and most certainly won't just magically compute it for you...

There's no disagreement here...

---

### Post by tehcavil on 2013-01-29
> **trent.josephsen said:**
> 
(You also apparently labor under the unfortunate assumption that C and  assembly and all such inferior languages are reserved for tiny market  niches like compilers and device drivers. Although this is only  tangentially relevant to the topic, I beg to remind you that vastly more  software is written every day than just what runs on the spawn of  Intel.)

Point taken. I was wrong to throw C under the bus like that.

> 
If you have something to say in defense of the idea that the unique  problems of the next decade or two will be particularly well-suited to a  functional approach, feel free to speak in your capacity as a futurist  and I will not suppose to contradict you. But so far you have given no  analysis of the problems you expect the future to hold, nor evidence  that functional programming is any better at solving them (nor today's  problems) than the next best idea, and your prediction that functional  programming shall become "the dominant programming paradigm" is (as far  as I can see) entirely founded on your belief that one or two minor  features is enough to take the entire programming industry by storm.  This is just the same tired argument supported by the same overblown  generalities.


I think it would be fair to say that  object oriented programming sees a program as a society, where different  members of that society interact with one another. The society is  hierarchically organized, with smaller units of society being derived  from larger ones. You have a city, for example. Then "neighbourhood"  extends city, and family extends neighborhood, etc. But it's only in an  abstract, typological way. An OOP programmer sees a program like a  sociologist sees society; a family is a social institution (class) with  attributes that all families have. A particular family "Browns" is an  instantiation of that abstract sociological unit (an object).

This  approach seems intuitive for certain tasks: such as a 3d video game.  It's easy to imagine all the 3d objects in the game (trees, buildings,  player models, etc.) as objects. The programmer can imagine a generic  tree class which is extended by "pine" which is given certain  attributes: so many branches, certain height, etc. And the objects  interact with one another for example, when the player's model runs into  a tree. 

Functional programming on the other hand, sees programs  as functions. A function takes input(s) and produces an output.  Essentially, functional programming sees a program as a series of  transformations on data. We think of programs in terms of data flow  rather than manipulation of stateful objects.

This approach is a good fit for stuff like:

Compilers.  A compiler is essentially functional. It takes an input (code of a high  level language), does a series of transformations on the data  (lexing/parsing), and emits an output (rewritten code in a lower level  language).

Dynamic web page. A dynamic web page is also  inherently functional. It takes inputs (user input in the form of get,  post, forms, as well as information from the database) and does a series  of transformations on the data, then emits an output (html page).

Graphics  programming. Graphics pipeline is essentially a data-flow network. We  can think of it as a function which maps vertex descriptions to bitmaps,  and the function involves a series of transformations.

And much more, but that's what I can think of off the top of my head.
-=-=-

There are also several generic benefits to FP:

Unit  testing. Because of referential transparency, you only need to worry  about the arguments when testing your functions (edge cases). You don't  have to worry about global state variables, or calling the functions in a  certain order, because each one behaves the exact same each time. You  just check the return value.

Debugging. This also greatly helps  debugging as those only-occur-once-in a blue moon bugs which happen only  under certain very rare state conditions of globals, member variables,  state of other classes (which might also rely on those), doesn't really  happen in an FP language, because there is no state. It's much, much  easier to reproduce a bug because if it's right, it's always right. If  it's wrong, it will always be wrong.

Concurrency/Parallelism. FP  makes this much easier. I remember in college it was mandatory to study  the case of the Therac-25, one of the first multithreaded programs which  was used to a run a radiation therapy machine. A race condition in the  imperative code caused the death of several people who were overdosed  with radiation. Was not cool. FP eliminates deadlocks and race  conditions, you don't need to deal with messy thread  locking/deadlocks/race conditions, because there is no mutation, no data  is modified by even the same thread, much less another one. FP programs  can be made concurrent much more easily and safely than their  imperative counterparts.

---

### Post by trent.josephsen on 2013-01-30
Well reasoned, but I'm not convinced. I will refrain from quoting your entire post piecemeal, but try to simply address a few points from it.

Your analysis of OOP is somewhat lacking. OOP doesn't really enforce hierarchical organization within a program; what it enforces is *classification* of objects into types with certain commonalities. No programmer worth his salary would write "class Neighborhood extends City", since a neighborhood is not a specific subtype of city, but a different kind of thing entirely. Nevertheless, I digress; I didn't want to start blathering about OOP.

You mention compilers as an example of an "essentially functional" program, which I think is interesting because of how a compiler lends itself to the stateful-object model. A compiler has many internal units, like the lexer, parser, and optimizer, each of which is a complex component by itself, and all of which need to interact at times to resolve ambiguity and perform compile-time checks -- contextual analysis is made much more difficult otherwise.

As for Web development, you pass over "information from the database" as if it's a minor point, but the role of a database is essentially to save state. Stateless CGI is simply not useful. With that in mind, I don't see a compelling reason why CGI scripts should be seen as "inherently functional". My point being that it's always possible to solve non-trivial problems in several different ways, and there's no reason to prefer functional programming over any other method based solely on *one interpretation* of the problem.

Now, I'm not much on graphics programming, but I'd say you're right on that point. GPU stuff requires a lot of concurrency, for which FP is a useful model for the very reasons you give.

As for your other points, I won't venture to disagree. But I doubt that they are sufficient to motivate a paradigm shift of any notable size. For most complex programs, OOP works just fine when properly implemented -- and as many people as there are who don't use it properly, OOP still presents a comparatively small risk that your newest programmer will drag down the whole team by failing to understand the code. For a new paradigm to "take over" in any meaningful sense, it must be not only powerful, but accessible, and this is, as I see it, the primary failing of today's functional languages.

//

---

### Post by satsujinka on 2013-01-30
> **trent.josephsen said:**
> 
As for your other points, I won't venture to disagree. But I doubt that they are sufficient to motivate a paradigm shift of any notable size. For most complex programs, OOP works just fine when properly implemented -- and as many people as there are who don't use it properly, OOP still presents a comparatively small risk that your newest programmer will drag down the whole team by failing to understand the code. For a new paradigm to "take over" in any meaningful sense, it must be not only powerful, but accessible, and this is, as I see it, the primary failing of today's functional languages.

I'm curious as to why you find functional code less accessible than OO code. As personally, I find OO code much harder to read than functional code (and much more difficult to get into a OO code base than a functional one.)

---

### Post by lisati on 2013-01-30
The old chestnut "use what works" comes to mind.....

<nostalgia>
Most of the coding I did when I first started work 30-something years ago was in assembly language (on an IBM mainframe) - it suited the job I was doing better than  another favourite at the company, COBOL.
</nostalgia>

---

