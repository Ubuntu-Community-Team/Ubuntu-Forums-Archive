---
title: "Is python a high level programming Language?"
date: 2010-01-13
forum: Programming Talk
---

### Post by nbo10 on 2010-01-13
Hi all,
I'm applying for a job that asks for c, c++ or other high-level languages experience. I have used c++ in the past, but most of everything I've worked on recently has been in python. Most of the relevant programming for the job I've done in python. python would be a good fit for the problem that the employer wants to solve.

So is python considered a high level language?

---

### Post by shadylookin on 2010-01-13
of course it is.

---

### Post by nbo10 on 2010-01-13
What's the definition of a high level language? and what is considered a low level language? Thanks

---

### Post by KarlIvan on 2010-01-13
I very barely looked over python at one point...bottom line is, its a scripting language...so no. your high level languages are c (i think it is anyway because of its applications and complexity), c++, c#, java, and the like.

i dont know any c++ myself, but I would recommend learning java or c#...I do know a lot about java, its my most fluent language, but none of c#, i hope to learn soon...point is, from what i understand, you should only need to know one or the other, because they seem to be very similar. the only differences would be a few different keywords, or mildy different syntax, and obviously c# doesnt run ontop of the jvm, so i assum there would need to be checks written into your software to make your programs OS independent

anyway, i dont consider python a high level language, but if youre going after a job, it doesnt matter how high level it is or not, you throw out everything you know. i interviewed for a job and mentioned html. i played it down obviously because thats a joke of a language (to be honest i dont even consider it a language) but it cushions your abilites, and makes you look more desireable the more you know

---

### Post by Ozitraveller on 2010-01-13
assembler

---

### Post by Reiger on 2010-01-13
C is kind of low level; especially by modern standards. C++ is already a bit more high level but there we get to a point of some high level languages are more so than others: typical distinguishing features of high level languages are built-in memory management, boundary checking, and language-level access control. C++ has none of those. E.g.: private in C++ has no real meaning at run time and can effectively be subverted at compile-time by casts; whereas in languages such as Java, Python, PHP it does and there is no getting around that.

---

### Post by shadylookin on 2010-01-13
> **nbo10 said:**
> What's the definition of a high level language? and what is considered a low level language? Thanks

[http://en.wikipedia.org/wiki/High-level_programming_language](http://en.wikipedia.org/wiki/High-level_programming_language)
[http://en.wikipedia.org/wiki/Low-level_programming_language](http://en.wikipedia.org/wiki/Low-level_programming_language)
[http://en.wikipedia.org/wiki/Python_%28programming_language%29](http://en.wikipedia.org/wiki/Python_%28programming_language%29)

---

### Post by KarlIvan on 2010-01-13
> **Reiger said:**
> C is kind of low level; especially by modern standards. C++ is already a bit more high level but there we get to a point of some high level languages are more so than others: typical distinguishing features of high level languages are built-in memory management, boundary checking, and language-level access control. C++ has none of those. E.g.: private in C++ has no real meaning at run time and can effectively be subverted at compile-time by casts; whereas in languages such as Java, Python, PHP it does and there is no getting around that.
yea, but the garbage collecter creates a large overhead (as does most things in java) so its really a trade off. c is capable of things that java just isnt, because of its strict(er) rules. but i get what youre saying. like i said though, ive seen some pretty amazing stuff in c, which is why i consider it one

---

### Post by nmccrina on 2010-01-13
I can't add anything meaningful to what the others have already said WRT Python, but good luck with your application! I hope you get the job! :popcorn:

---

### Post by Vox754 on 2010-01-13
> **KarlIvan said:**
> I very barely looked over python at one point...bottom line is, its a scripting language...so no. your high level languages are c (i think it is anyway because of its applications and complexity), c++, c#, java, and the like.

i dont know any c++ myself, but I would recommend learning java or c#...I do know a lot about java, its my most fluent language, but none of c#, i hope to learn soon...point is, from what i understand, you should only need to know one or the other, because they seem to be very similar. the only differences would be a few different keywords, or mildy different syntax, and obviously c# doesnt run ontop of the jvm, so i assum there would need to be checks written into your software to make your programs OS independent

anyway, i dont consider python a high level language, but if youre going after a job, it doesnt matter how high level it is or not, you throw out everything you know. i interviewed for a job and mentioned html. i played it down obviously because thats a joke of a language (to be honest i dont even consider it a language) but it cushions your abilites, and makes you look more desireable the more you know

Good God... I am speechless.

You need to learn basic Computer Science.

**Python is a high-level language.** It has nothing to do with it being a "scripting" language, or doing "pretty amazing" stuff with it.

Low-level, high-level, etc. is defined in terms of "abstraction", not "raw power", whatever you may define it.

C# doesn't use the Java Virtual Machine, but it uses the "Microsoft Virtual Machine", better known as the .NET framework.

This just shows you are talking about stuff you know nothing about.

I'm so mad I cannot say anything more.

---

### Post by denarced on 2010-01-13
I must agree that python is a programming language,
but I must say that there is no real definition of what makes a programming language. That being said, there is a consensus and some people think that language must be turing complete, which is what Python is.

---

### Post by lisati on 2010-01-14
Can't add much beyond this:

Loosely speaking, a "low level" language is close to the internal workings of the computer, while a "high level" language expresses things closer to the abstractions used by the programmer.

---

### Post by wmcbrine on 2010-01-14
Python is one of the highest-level languages you're likely to work in today. C is the lowest (that you're likely to work in -- ASM is lower-level, but it's kind of niche these days IMHO). If an ad is asking for experience in high-level languages, and then providing C as an example... well, that's kind of peculiar. Technically correct, but odd.

---

### Post by lisati on 2010-01-14
> **wmcbrine said:**
> Python is one of the highest-level languages you're likely to work in today. C is the lowest (that you're likely to work in -- ASM is lower-level, but it's kind of niche these days IMHO). If an ad is asking for experience in high-level languages, and then providing C as an example... well, that's kind of peculiar. Technically correct, but odd.

It can be relative. :)
I used to do a lot of ASM coding, so in some ways, for me, C is high level.

---

### Post by CptPicard on 2010-01-14
> **nbo10 said:**
> What's the definition of a high level language? and what is considered a low level language? 

The difference is in the abstractions. Low-level languages work in terms of machine operations, higher-level languages work in terms of... abstract... abstractions. Higher-order functions, closures, objects, iterable sequence types... there is no strict definition and it moves over time. Once C was high-level, now it tends to be classed as low-level.

> **KarlIvan said:**
> I very barely looked over python at one point...bottom line is, its a scripting language...so no.

Umm.. :) I hope this is not a form of the "scripting languages are not programming languages" argument... anyway, Python goes pretty high up the abstraction ladder, so you'll be quite alone with that definition.

> 
 your high level languages are c (i think it is anyway because of its applications and complexity)

C is actually really small and primitive. Which is also a downside; it takes a lot of work to put stuff together in it.

> i interviewed for a job and mentioned html. i played it down obviously because thats a joke of a language (to be honest i dont even consider it a language)

HTML can't do recursive structures, either on implicit stack or in an explicit data structure, so it is not Turing-complete, so not a programming language... if someone mentioned HTML as a programming language on a CV or in an interview, it would make the person seem a bit clueless.

> **KarlIvan said:**
> yea, but the garbage collecter creates a large overhead (as does most things in java)

The garbage collector only becomes a real noticeable problem in certain usage scenarios where you're aggressively trashing the heap...

Of course, it is a general algorithm for a common problem, so there is a tradeoff, though.

What are these "most things" in Java? :) I find Java's actual execution speed to always have been quite acceptable considering it's not a purely native compiled language...

> c is capable of things that java just isnt, because of its strict(er) rules.

C has very loose rules, it's weakly typed! Interestingly, a garbage collector lets you do things C just simply can't do, such as closures which are probably the most important thing a high-level language typically can do that a low-level language can't do...


> **denarced said:**
> I must agree that python is a programming language,
but I must say that there is no real definition of what makes a programming language. That being said, there is a consensus and some people think that language must be turing complete, which is what Python is.

+1

There are people who insist that a "programming language" has to be native-compiled, but IMO the theoretical definition of Turing-completeness is much more meaningful and interesting. If it can solve all the problems any other programming language can solve ("problem" here in the CS textbook sense, not in some business programmin sense), it's a programming language.


> **lisati said:**
> It can be relative. :)
I used to do a lot of ASM coding, so in some ways, for me, C is high level.

It's a portable, glorified assembler... ;)

---

### Post by SunSpyda on 2010-01-14
As far as Linux people in this forum are concerned, it's a high-level language. As far as most employers are concerned, it's a skiddy scripting language that is frail and doesn't work on 'real' OSes, like NT.

Now, we know that this isn't true. We know it is a real language that has been used at NASA etc. But the employers don't think that (unless they are non-Windows savvy).

Do I think Python is a high-level language? No. I think it's a scripting language, like Ruby, Perl, and sh. I put this down to its loose typing and the fact it's completely interpreted (yes it's compiled at runtime, but the fact is, it starts by interpreting a human-readable script).

Before I get flamed, I'd like to say that scripting languages don't have the negative baggage they used to have. People now know that scripting languages can actually so serious things (although I personally would prefer Java for a application that needs to be robust due to it's strong, static typing and compile-time exception checks.)

But look at it from your employers POV. If he/she is Windows-centric, then you can almost can guarantee they'll think Python as a crappy scripting language.

EDIT - fwiw, I really like Ruby as a language (which is basically on the same level of abstraction as Python). It's a scripting language, but I can get stuff done so fast in it, with maintainable results, so I don't care that it's a scripting language :p

---

### Post by CptPicard on 2010-01-14
> **SunSpyda said:**
> As far as Linux people in this forum are concerned, it's a high-level language.

According to most definitions I've read and the basis on which I've discussed on this at length, it is a high level language, as it provides a lot of abstractions (which are not the same thing as "library calls", mind you) that are not possible without, uh, high-levelness. The distinction has to do with what the language's concepts deal with.

> 
 As far as most employers are concerned, it's a skiddy scripting language that is frail and doesn't work on 'real' OSes, like NT.

I know you don't necessarily agree with the employer-view, but I feel a need to point out that most employers look for replaceable code-monkeys that are relatively "average" -- the problem is that with a high-functioning salary-programmer, rest of the programmers are in intellectual trouble, and the guy is not replaceable...

> 
Do I think Python is a high-level language? No. I think it's a scripting language, like Ruby, Perl, and sh.

I wonder where this idea comes from that a scripting language is not a so-called high-level language. Not that the labels matter much, they're just words, but it's curious anyway. Do you classify "high-levelness" with the amount of brute-force manual work a language forces on the programmer?

> 
 I put this down to its loose typing and the 

Dynamic typing. "Loose" typing brings to mind "weak" typing (as in C), which can be a fairly bug-prone feature... Python's typing is not static, but it is strict (the type of the value is enforced at runtime, the bits can't just be magically interpreted as anything).

> fact it's completely interpreted 

It doesn't matter. It can solve the same class of problems just fine as compiled languages, and the human input in actually providing the actual solution formulation just gets the by definition machine-translatable (and thus non-intelligence-requiring) parts for free; the rest of the solution, that has to be provided, is the stuff that a machine could never actually provide, no matter how strong the interpreter was (in *general case*, I do not mean that "you could have a library call..").

> (yes it's compiled at runtime, but the fact is, it starts by interpreting a human-readable script).

The human-readability is a huge plus. Mathematical notation is also quite simple, concise and human-readable (once you get the hang of it), and nobody is complaining that it detracts from the usefulness or intellectual challenge of mathematics itself (and I've never seen anyone claim the abstractness of mathematics "dumbs it down", like some claim about HLLs). Same goes for computable functions (programs).

> 
Before I get flamed, I'd like to say that scripting languages don't have the negative baggage they used to have.

Just noting that I'm not flaming -- just being conscious of the fact that Lisp did most everything right in 1958, and it is quite different from the Serious Programming-Languages(tm) ;)

> 
 but I can get stuff done so fast in it, with maintainable results, so I don't care that it's a scripting language :p

Good! Maybe you'll get disabused of an ingrained bias. :) One of the things you'll still need to "get" IMO is that the development speed and maintainability is just simply a side-effect of good language design... there is more to it, and that has to do with how you actually formulate/design things in a high-level language compared to your typical "alter state in registers by commands" style low-level language. It is the "thinking about programs" aspect that a lot of very experienced programmers talk about...

---

### Post by grayrainbow on 2010-01-14
Well, if somebody describe C/C++ as high level, that could mean - this person is old or this person do some speed critical programming. Since you claim python will feet the problem - only the 'person is old' thing is left.
Anyway, to the thread question: python IS a high level programming language. But there is a good reason why people call it script(in difference than C# for example), and modern 'general purpose' script is a better definition for python then language, but it's quite longer, and sound stupid :)

---

### Post by nbo10 on 2010-01-14
Thanks for all the responses.

Programming is only part of the job desciption, but will be a large task at the beginning. So this isn't a pure CS/programming position.

---

### Post by Maheriano on 2010-01-14
> **KarlIvan said:**
> I very barely looked over python at one point...bottom line is, its a scripting language...so no. your high level languages are c (i think it is anyway because of its applications and complexity), c++, c#, java, and the like.

i dont know any c++ myself, but I would recommend learning java or c#...I do know a lot about java, its my most fluent language, but none of c#, i hope to learn soon...point is, from what i understand, you should only need to know one or the other, because they seem to be very similar. the only differences would be a few different keywords, or mildy different syntax, and obviously c# doesnt run ontop of the jvm, so i assum there would need to be checks written into your software to make your programs OS independent

anyway, i dont consider python a high level language, but if youre going after a job, it doesnt matter how high level it is or not, you throw out everything you know. i interviewed for a job and mentioned html. i played it down obviously because thats a joke of a language (to be honest i dont even consider it a language) but it cushions your abilites, and makes you look more desireable the more you know

Reading this hurts my brain.

A lot of people think high level means it can do a lot and is very powerful. Conversely, the same people think low level means it can't do much.
In reality, high level means you can write the code without having to worry about the low level things like pointer scripting and garbage collection. All of this is taken care of for you in the compiler. With a low level language like C (yes, C is low level), you have to worry about these things, specify your pointers and God...OH GOD!..... don't miss one!

So basically:
Low Level = "I'm going to put your car on the ramp, drop the gearbox, pull apart the clutch plates, remove them and resurface each one individually prior to reassembling everything and testing it."
High Level = "I'm going to fix your problem."

And Java and C# are more opposite, not alike. I guess they're both object oriented but C# is closer to (almost the same as) VB.NET.

---

### Post by myrtle1908 on 2010-01-15
> **Maheriano said:**
> And Java and C# are more opposite, not alike. I guess they're both object oriented but C# is closer to (almost the same as) VB.NET.

Whilst C# is an ok language, the whole .NET framework is so bloated and such a steaming pile of mess that if I have the choice its Java every time.  Assemblies, registry, RegAsm, cross your fingers, hey it works on my machine, blah blah blah ... such a rubbish design.  I wish it would go away.

---

### Post by nvteighen on 2010-01-15
I just can't believe what sort of things I've read in this thread... and a phrase from Francis Bacon's "Novum Organum" comes to my mind: "At idola fori omnium molestissima sunt; quae ex foedere verborum et nominum se insinuarunt in intellectum." ("And the idols of the forum are the most molesting of all; as they slip into thought from the association of words and names". Book I, LXI)

High-level and low-level are bad and misguiding terms... because those aren't the "real" terms; "High abstraction level language" and "Low abstraction level language" are the real terms... just that, as Saussure said in his "Course in General Linguistics", people are lazy and seek economy when speaking... therefore, we get "high-level" and "low level" languages.

But these are technical terms discussed in a very concrete technical context. Being high- and low-level is determined by the "distance" of the language from the machine internals (and/or from human natural language... I can explain this if wanted, but it will be completely off-topic so I reserve it for another time). So, if your programming language talks about memory addresses and another one talks about lists, as lists is a human concept, the second language is said to be higher-level than the first.

That's all of it. It has nothing to do with the "quality" of the language. But I do recognize the shortened terms may easily confuse anyone.

---

### Post by Puzzled Guy on 2010-01-15
Why not just ask them if they will accept a python programmer?

---

### Post by CptPicard on 2010-01-15
> **nvteighen said:**
> Being high- and low-level is determined by the "distance" of the language from the machine internals (and/or from human natural language...

I guess it should be specifically pointed out that "natural language" needs to be taken quite loosely here, programming languages that specifically try to emulate natural language end up being pretty bad. One wants stuff in the language that is "natural" to the abstract concepts present in computable functions, which is what we're describing with programming languages.

---

### Post by ajackson on 2010-01-15
> **SunSpyda said:**
> Do I think Python is a high-level language? No. I think it's a scripting language
I'm so glad that C can't be used as a scripting language as that would blow the whole "a high-level language can't also be used for scripts" out of the water and leave egg on a few peoples face.

Oh [darn]("http://csl.sourceforge.net/csl.html").

---

### Post by humphreybc on 2010-01-15
Eh I can't remember back to my Comp sci lectures but I believe Python was included in the list of "high level languages."

It's a fairly powerful language, and used in a lot of applications. I would be surprised to hear it classes as anything but "high level."

:)

---

### Post by SunSpyda on 2010-01-15
> **CptPicard said:**
> According to most definitions I've read and the basis on which I've discussed on this at length, it is a high level language, as it provides a lot of abstractions (which are not the same thing as "library calls", mind you) that are not possible without, uh, high-levelness. The distinction has to do with what the language's concepts deal with.
Which is why I like higher-level languages like Python and Ruby :p

I feel that using the highest-level language feasible is a good rule to stick by. I only use lower-level languages if I *have* to (and even then, it's usually C modules for the higher-level language.)

> **CptPicard said:**
> I know you don't necessarily agree with the employer-view, but I feel a need to point out that most employers look for replaceable code-monkeys that are relatively "average" -- the problem is that with a high-functioning salary-programmer, rest of the programmers are in intellectual trouble, and the guy is not replaceable...
Ah yes, I completely forgot about this. A Java/.NET coder writes code that others can maintain... because they're common as rabbits.

Thus they're employed more than the coder that writes in a language that is slightly less common, right?

> **CptPicard said:**
> I wonder where this idea comes from that a scripting language is not a so-called high-level language. Not that the labels matter much, they're just words, but it's curious anyway. Do you classify "high-levelness" with the amount of brute-force manual work a language forces on the programmer?
You've got me labeled completely wrong :)

I'm in no way a Speed Kiddy (I heard you coined that term?)

I don't classify 'scripting language' as a derogatory term. I use it for any language that is abstracted away, beyond a conventional language, to the extent that you can automate things with it easy. I don't mean underpowered in the slightest. These are usually *more* powerful than languages like C, due to the fact the programmer maps ideas and solutions into it, not spoon-feeding compilers/interpreters and wrestling with low-level machine issues.

> **CptPicard said:**
> Dynamic typing. "Loose" typing brings to mind "weak" typing (as in C), which can be a fairly bug-prone feature... Python's typing is not static, but it is strict (the type of the value is enforced at runtime, the bits can't just be magically interpreted as anything).
The *only* problem is parameters not type-checking. Apart from that, it's complete preference. Other than that I have no problems with loose typing (and non whatsoever with dynamic typing.) I just have a personal *preference* for full strong typing (and that includes parameter type checking IMHO.) It's not because I think 'OMZG, DYNAMIC TYPINGS FOR NOOBZ!', it's because I personally map problems in my head using types, not just random types holding any type of data.

> **CptPicard said:**
> It doesn't matter. It can solve the same class of problems just fine as compiled languages, and the human input in actually providing the actual solution formulation just gets the by definition machine-translatable (and thus non-intelligence-requiring) parts for free; the rest of the solution, that has to be provided, is the stuff that a machine could never actually provide, no matter how strong the interpreter was (in *general case*, I do not mean that "you could have a library call..").
Exactly. Anyway, they both get translated into machine code that the CPU ends up executing anyway, so whether it takes a alternate route to get there is irrelevant IMO.

> **CptPicard said:**
> The human-readability is a huge plus. Mathematical notation is also quite simple, concise and human-readable (once you get the hang of it), and nobody is complaining that it detracts from the usefulness or intellectual challenge of mathematics itself (and I've never seen anyone claim the abstractness of mathematics "dumbs it down", like some claim about HLLs). Same goes for computable functions (programs).
I like the way I can punch maths into a calculator, and punch it into Haskell, and it works the same :D

Again, I agree with you. Although I think in *certain* circumstances, the programmer should know what the abstraction is doing, and a general clue at how.

> **CptPicard said:**
> Just noting that I'm not flaming -- just being conscious of the fact that Lisp did most everything right in 1958, and it is quite different from the Serious Programming-Languages(tm) ;)
Quite... No side-affects, encapsulation, etc... it's funny that these were buzz-word waaaaaaaay after Lisp could already do it :p

> **CptPicard said:**
> Good! Maybe you'll get disabused of an ingrained bias. :) One of the things you'll still need to "get" IMO is that the development speed and maintainability is just simply a side-effect of good language design... there is more to it, and that has to do with how you actually formulate/design things in a high-level language compared to your typical "alter state in registers by commands" style low-level language. It is the "thinking about programs" aspect that a lot of very experienced programmers talk about...
You just interpreted me wrong :p Or I used the wrong terminology, which is likely seeing as Computing is a mere hobby for me - my academic path is *far* different.

The higher-level, the more I can map out solutions rather than having my intelligence insulted by explicitly telling it how to do a hash-table using memory addresses ;)

...except loose typing, like parameters with no type checking, which is one higher-level concept that is not a good one IMHO.

---

### Post by lisati on 2010-01-15
> **CptPicard said:**
> I guess it should be specifically pointed out that "natural language" needs to be taken quite loosely here, **programming languages that specifically try to emulate natural language end up being pretty bad**. One wants stuff in the language that is "natural" to the abstract concepts present in computable functions, which is what we're describing with programming languages.

Aaaargh! Flashback to COBOL! :D

Keep up the good work with with the interesting posts. :)

---

### Post by CptPicard on 2010-01-15
> **SunSpyda said:**
> 
Ah yes, I completely forgot about this. A Java/.NET coder writes code that others can maintain... because they're common as rabbits.

Indeed. Although I must admit that I personally write my biggest breadwinner piece of code in Java -- the speed/convenience/multiplatformness tradeoff is about right, and if you've got to use a static-typed OOP-language, Netbeans maintains your type information very nicely.

> 
Thus they're employed more than the coder that writes in a language that is slightly less common, right?


The Lisper that I respect more than any programmer alive in the world works part-time as a construction worker so that he can work on his Lisp project...

> 
You've got me labeled completely wrong :)


Sorry; I only cursorily read UF PT these days and I can't help but recognize patterns in posters... sometimes I'm wrong.

> 
I'm in no way a Speed Kiddy (I heard you coined that term?)


I'm not quite sure who did, but *I* think it was **pmasiar**. It's been attributed to me (by pmasiar himself!) but I can't quite feel like it's me... it's either of us.

> it's because I personally map problems in my head using types, not just random types holding any type of data.

That's actually a very valid mental model, nothing wrong with that. It's just that at least duck-typed languages just let the type definitions emerge on their own... you might want to check out something like multiple dispatch in Lisp... types do not have to be so strictly combined to operations, for example.

> 
Exactly. Anyway, they both get translated into machine code that the CPU ends up executing anyway, so whether it takes a alternate route to get there is irrelevant IMO.

The low-level people would say that one still does not understand how to actually implement these things.

The high-level guys would say that you will understand how to implement them if you understand how to program in high-level terms -- after all, *you already understand everything that is humanly important to understand, so you can handle the machine*. 

> 
Again, I agree with you. Although I think in *certain* circumstances, the programmer should know what the abstraction is doing, and a general clue at how.

My retort to this would be that if one is a perfectly competent high-level programmer, understanding how the abstraction works in terms of a low-level language is a triviality. Without that prior exposure, it is not, and the learning process is much more contrived and difficult.

> 
Quite... No side-affects, encapsulation, etc... it's funny that these were buzz-word waaaaaaaay after Lisp could already do it :p


I will take it that you are being sarcastic ;)

Pure-functionality is actually a rather profound language design choice. If you allow for any kind of state-alteration in your language, you've lost "no side-effects" for good. It is a binary choice... either you have it or you do not. Therefore, if Lisp is going to include mutability of data in it, it can't be pure-functional -- the guys who created Lisp were perfectly aware of this, and I'm willing to bet that the original Lisp was actually pure-functional as it was created as a notation of algorithms for printed academic papers.

Encapsulation is just a random wild choice... you can add it to any language. There is no invention in just deciding that some pieces of data are out of limits, and it has no real meaning to anything. I personally never understood why one should assume that programmers should be protected like that from themselves -- if some functionality or data is functionally not to be messed with, you simply should not mess with it. This can be covered in the documentation.

> 
You just interpreted me wrong :p Or I used the wrong terminology, which is likely seeing as Computing is a mere hobby for me - my academic path is *far* different.

Nvteighen is actually a linguist and computation is a mere hobby for him -- he's a damned strong hobbyist mind you :)

> 
The higher-level, the more I can map out solutions r
ather than having my intelligence insulted by explicitly telling it how to do a hash-table using memory addresses ;)

I love you, man!

> 
...except loose typing, like parameters with no type checking, which is one higher-level concept that is not a good one IMHO.


Let's at least use proper terminology. There is no such thing as "loose" typing. There is weak, static, strict, dynamic typing... and "weak" typing in particular is something quite unhelpful.


> **lisati said:**
> Aaaargh! Flashback to COBOL! :D

I was going to mention that, but refrained as most of the kids around here won't get it.

> 
Keep up the good work with with the interesting posts. :)

Thanks, I like to know you appreciate it. Mind I suggest to both of you (SunSpyda and you) that you check out LambdaGrok?

---

### Post by SunSpyda on 2010-01-15
> **CptPicard said:**
> I will take it that you are being sarcastic ;)
Not at all! When using Haskell, I never get variables being wiped out without adequate warnings due to imperative side-effects (I *hate* reference-passing), or nasty side-effects ruining the program logic, taking decades to debug. All the imperative code is 'quarantined' into a monad, thus I can write *predictable* code, without learning a zillion scoping or memory-management features of a language. It either works or it doesn't... whereas OO/imperative code can *semi* work, needing things like exception-handling to redeem itself (which functional languages don't even need.) And all variables being immutable is just... so encouraging compared to ones that can be modified at any random time (you get what I mean :) .)

> **CptPicard said:**
> 
Let's at least use proper terminology. There is no such thing as "loose" typing. There is weak, static, strict, dynamic typing... and "weak" typing in particular is something quite unhelpful.
Ah, *weak* and strong, not *loose* and strong - thanks for the info.

EDIT - Oh wait... I mean strict, not strong - wrong lingo again! :)

> **CptPicard said:**
> Thanks, I like to know you appreciate it. Mind I suggest to both of you (SunSpyda and you) that you check out LambdaGrok?
Is it some sort of programming forum... or...?

---

### Post by mmix on 2010-01-15
yes, HLL with ugly syntax.

---

### Post by c0mput3r_n3rD on 2010-01-15
Low Level Language = directly assembled in to machine language

Everything else is high level.

Try programming in assembly, and then write a program in any other language and you'll know what I'm talking about.  A few of you explained it perfectly with the abstraction concept.

Definition of Programming language: Code of reserved words and symbols used in computer programs, which give instructions to the computer on how to accomplish certain computing tasks.

A programming language has nothing to do with whether it's interpreted, compiled, assembled, or what have you.  All that matters is that's it's a list of instructions that accomplishes a task.  Some of these posts really hurt my brain.  Don't make the issue of "what's a programming language?" and what's HL or LL more complicated than it is.

---

### Post by Sinkingships7 on 2010-01-16
> **SunSpyda said:**
> 
Is it some sort of programming forum... or...?

[http://lambdagrok.wikidot.com/forum:start](http://lambdagrok.wikidot.com/forum:start)

---

### Post by nvteighen on 2010-01-16
> **CptPicard said:**
> I guess it should be specifically pointed out that "natural language" needs to be taken quite loosely here, programming languages that specifically try to emulate natural language end up being pretty bad. One wants stuff in the language that is "natural" to the abstract concepts present in computable functions, which is what we're describing with programming languages.

A bit busy theses days and couldn't reply to you before.

When I said that higher level programming is nearer to human natural language, I did mean "natural language" in the very strict sense of it... Taking the term "loosely" is what ruins some languages like BASIC or COBOL (as far as I'm told), because they just focus on the surface issue of a very basic generative syntax without taking account of semantics, morphology. Moreover, programming languages' syntaxes are usually really bad examples of what a syntax system is, as they are based more on explicit markers (e.g. "{" means 'subordinate next statements to the previous' in C-like languages) instead of, for example, position, syntactic context or actually what stuff is. 

Higher-level languages work more like natural languages because, the higher you climb in the level of abstraction, the more you notice the language's "lexicon" becomes more conceptual. And when dealing with concepts, you introduce meaning and therefore, semantical constraints become relevant. For example, Python "arrays" are called lists... but not only called lists, but they also do behaive as we consider a list should... you can add a list to another, resize it at will, fill it, etc. You start having very primitive "semantical fields"... and, of course, relationships between them, e.g. files and strings are both read()-able (please, to understand this forget that the implementation of files is based on string buffers).

The most radical thing is, of course, the language which is the answer of my little riddle above: Lisp (in any of its modern forms: Scheme, Common Lisp, Clojure, Arc, etc.). In Lisp you've got Transformational grammar too in its macros. Therefore, full metalinguistic ability... While Python's eval/exec could be considered as a first step into Python-talking-about-Python (which is what metalanguage is)... In Lisp you can do it without any restraint and also modify the language's syntax in order to create a "surface structure" opposed to a "deep structure".

That's what I was meaning... Languages that just imitate English words or sentences is not what I had in mind. Otherwise, LOLCODE would be the perfect programming language.

---

