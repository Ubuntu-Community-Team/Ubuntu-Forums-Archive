---
title: "What's with the popularity of C over C++?"
date: 2008-06-25
forum: Programming Talk
---

### Post by matthewhaworth on 2008-06-25
To be honest, before I came to Ubuntu (yesterday) I thought that C and C++ were Windows only lol, I feel quite stupid now to be honest.  Anyway, I've read on these forums that Python is the preferred language for the Ubuntu environment, however, I'd rather learn C since this is more popular (as stupid as that sounds) and it's more powerful..but the thing is why not C++?  When I look around the forums there seems to be more talk of C than C++, the only difference is that C++ is object-oriented right? I thought object-oriented was the way forward and thus I expected C to be deprecated now, but obviously not.. also, where's Java got to? What's wrong with it? lol.. I don't know, I'm just not really into the idea of using Python, no idea why but it just sounds like the Linux equivalent of using Visual Basic.. as powerful as they both may be, I'm still ignorant to them being used as a proper language.

---

### Post by Greyed on 2008-06-25
> **matthewhaworth said:**
> I don't know, I'm just not really into the idea of using Python, no idea why but it just sounds like the Linux equivalent of using Visual Basic..

...  Them thar's fighting words.  :P

---

### Post by matthewhaworth on 2008-06-25
> **Greyed said:**
> ...  Them thar's fighting words.  :P

Sorry? I don't understand

I realise that I sound very arrogant, I didn't intend to lol, I'm just a very confused newbie lol

---

### Post by LaRoza on 2008-06-25
> **matthewhaworth said:**
> To be honest, before I came to Ubuntu (yesterday) I thought that C and C++ were Windows only lol, I feel quite stupid now to be honest. 

C was actually created before Windows ever existed (in the 70's) for the purpose of writing Unix. C++ was invented by someone who thought C was too simple and easy to use.

> 
 Anyway, I've read on these forums that Python is the preferred language for the Ubuntu environment, however, I'd rather learn C since this is more popular (as stupid as that sounds) and it's more powerful..but the thing is why not C++?  

Python is a popular language, but C++, Java, Perl, and others are common also. As for power, it is all in the eyes of the beholder, Python (Perl, etc) are much more "powerful" when you want to do some things.

Why not C++? Linux has spoken! [http://advice.cio.com/esther_schindler/linus_torvalds_why_c_sucks](http://advice.cio.com/esther_schindler/linus_torvalds_why_c_sucks)

> 
When I look around the forums there seems to be more talk of C than C++, the only difference is that C++ is object-oriented right? I thought object-oriented was the way forward and thus I expected C to be deprecated now, but obviously not.. also, where's Java got to? What's wrong with it? 
No, the difference is how programs are written. C and C++ are two entirely different languages, and should be used differently. There is a link in the sticky to a thread that lists "Holy Wars", why to hate C++ is one of them.

> 
lol.. I don't know, I'm just not really into the idea of using Python, no idea why but it just sounds like the Linux equivalent of using Visual Basic.. as powerful as they both may be, I'm still ignorant to them being used as a proper language.


Go to the link in my sig, go to the articles and read "Beating the Averages" and "Scripting for the 21 century" (title may be off here)

---

### Post by pmasiar on 2008-06-25
C, C++ and Python are completely different languages with completely different (and complementary) usage.

Python is preferred language for ubuntu in areas where C has weak points, and vice versa:

C is good for deep libraries where CPU speed and resources are critical (and you are willing to spend developer time to get the speed), Python is where development time is crucial (and speed is taken care of by those C libraries).

C++ is attempt to sit on those two stools.

VB is brain-damaged language, hard to compare with Python, for so many reasons I will just ignore the flamebait.

---

### Post by Greyed on 2008-06-25
> **matthewhaworth said:**
> Sorry? I don't understand

Python is not the VB of Linux.  That's like saying a Porche is the same as a first-year Hyundai because both are "just cars".  ;)

---

### Post by matthewhaworth on 2008-06-25
Thank you for your help, it is greatly appreciated, I am very new to all of this despite the fact that I thought I knew a lot more than I evidently do lol.

I have another question now however, what is the deal with Visual Basic? Is it really bad or have I just been brought up with stupid misconceptions?
Also, can I do object oriented programming in C?

---

### Post by LaRoza on 2008-06-25
> **matthewhaworth said:**
> 
I have another question now however, what is the deal with Visual Basic? Is it really bad or have I just been brought up with stupid misconceptions?
Also, can I do object oriented programming in C?

Visual Basic is a UI oriented language derived from BASIC (BASIC is a crippled language by design)

Visual Basic itself isn't that bad. It is indeed a RAD tool beyond compare (from what I see). However, I think Visual Basic is a tool for very advanced users. For new users, it just cripples the mind and programming experience.

(Visual Basic is also Windows only)

As a programming language, Visual Basic is not good.

You can do OO programming in C, but you'd have to understand the concepts of OO.

---

### Post by Wybiral on 2008-06-25
You make weird use of the word "power" without explaining what that means. Low level number crunching and bit manipulation? Power of expressibility (expressing more powerful concepts with less typing)?

I personally prefer C over C++ because it's better for library development. It has a simpler ABI and doesn't mangle names or create any extra data within the binaries... Making it exceedingly simple to link with and use for writing extensions for higher level languages.

Python is a very powerful language in terms of expressibility, and when paired with modules written in C for low-level work, it can benefit from both worlds.

Python and VB are in completely different realms. Python being dynamically typed, standardized interfaces for duck-type design, functional concepts such as lambdas/map/filter/reduce, lazy sequence objects such as generators, decorators, etc etc. The list goes on... Python is MUCH more expressive than VB :)

---

### Post by descendency on 2008-06-25
Visual Basic (Before VB.NET) is a terrible language. Visual Basic .NET is a much better language, it's just not better than the other alternatives.

For example C# .NET (AKA Mono to OSS).

As far as Why C is more popular than C++, that's simple. There is about 20 years of reasons. Code written in C a while ago would have to be re-written in C++ with no advantage of doing such. Honestly, that's why C is more popular than a lot of languages. 

C++ has a growing market though, so in 20-30 years, I would suspect if C++ isn't taken over, it will lead the market. 

Why not pick another language? Simple. Little to gain from paying a programmer to reprogram the stuff. However updates and maintaining of that software requires a C programmer. Where there is a job, there usually is money. Where there is money, people will follow.

*hides from the hordes of Python lackies*

---

### Post by LaRoza on 2008-06-25
> **descendency said:**
> 
C++ has a growing market though, so in 20-30 years, I would suspect if C++ isn't taken over, it will lead the market. 

[http://www.tiobe.com/index.php/content/paperinfo/tpci/index.html](http://www.tiobe.com/index.php/content/paperinfo/tpci/index.html)

I suspect C++ will be gone in 20-30 years, replaced with higher level languages or better designed languages (D perhaps)

---

### Post by nvteighen on 2008-06-25
C is "popular" because it had been succesfully used for great projects that have changed the world! UNIX, to begin with. I don't know where would computers be if either UNIX nor C hadn't existed. Its historical importance relies on being the first high-level language (compared to Assembly) flexible enough but also small (very small) to create a whole OS. BCPL, the funny B language and other ALGOL-derived weren't useful for that. Read this article from one of C's creators Dennis Ritchie on the language's (fascinating, at least to me) history: [http://cm.bell-labs.com/cm/cs/who/dmr/chist.html](http://cm.bell-labs.com/cm/cs/who/dmr/chist.html) (the code examples there follow some outdated C standards, so don't use them to learn the language!).

C++, in turn, hasn't achieved any remarkable milestone in computing history... yet. Yes, there are great projects written in it (KDE, parts of Firefox, e.g.) and it is an important language, but it hasn't been part of the development of a whole new technology as UNIX was in its times.

I really believe there's much of this behind the survival of C, a 36 years-old programming language (Are we going to celebrate its 40th anniversary in 2012?). 36 years in computer techonlogies are as long as eternity, like you all know... but there it stands, with no sign of near death. The same could be applied to Lisp, surely (which is older!).

---

### Post by LaRoza on 2008-06-25
> **nvteighen said:**
> 
I really believe there's much of this behind the survival of C, a 36 years-old programming language (Are we going to celebrate its 40th anniversary in 2012?). 36 years in computer techonlogies are as long as eternity, like you all know... but there it stands, with no sign of near death. The same could be applied to Lisp, surely (which is older!).

Fortran and Lisp are older (Fortran is the oldest, Lisp second), but I think C is probably third.

---

### Post by DrMega on 2008-06-25
> **LaRoza said:**
> C was actually created before Windows ever existed (in the 70's) for the purpose of writing Unix. C++ was invented by someone who thought C was too simple and easy to use.

Come on now, you know that's not quite true:)

C was the logical progression from a language which was called 'B', which wasn't really successful. The name 'C' was chosen partly in humour.

Even C isn't standard. K&R C, which predates the more widely accepted ANSI C had key fundamental differences (no function prototypes for one thing, and you had to define your functions before you defined main() ).

People messed about with C, being the ace open language that it was, and eventually ANSI came along and defined some standards. This is when we start to see function prototypes in header files, standard types and a range of functions and keywords that were considered standard.

Time passed as time does, and object oriented techniques became prevalent. It was possible to define classes in ANSI C by using structs with function pointers as members, but it was messy, so C++ was developed (sticking with the geek humour naming conventions, it means "C incremented by 1" as that's what the ++ does). Initially it was implemented as a text preprocessor that you had to run first, which produced ANSI C as it's output, which you would then compile, but later C++ compilers came about, and have been around since.

Then came Java. A great idea, implemented poorly, with slow code execution for one thing. MS tried to gain a monopoly on it even though it wasn't theirs, and started implementing MS specific elements into it. A fateful court case happened and MS was banned from releasing its version of Java for some period of time. Choosing to circumvent that ruling, they invented C#, and had it defined as a standard, thus being another descendant of C, but somewhat less popular in the Linux world I fear, for although its ancestors are of noble blood, one of it's parents is MS.

There you go, a little history lesson.

---

### Post by LaRoza on 2008-06-25
> **DrMega said:**
> Come on now, you know that's not quite true:)

C was the logical progression from a language which was called 'B', which wasn't really successful. The name 'C' was chosen partly in humour.

I know, I was giving the short version

> 
Even C isn't standard. K&R C, which predates the more widely accepted ANSI C had key fundamental differences (no function prototypes for one thing, and you had to define your functions before you defined main() ).

I know, and function parameters types were defined differently also.

> 
People messed about with C, being the ace open language that it was, and eventually ANSI came along and defined some standards. This is when we start to see function prototypes in header files, standard types and a range of functions and keywords that were considered standard.

Time passed as time does, and object oriented techniques became prevalent. It was possible to define classes in ANSI C by using structs with function pointers as members, but it was messy, so C++ was developed (sticking with the geek humour naming conventions, it means "C incremented by 1" as that's what the ++ does). Initially it was implemented as a text preprocessor that you had to run first, which produced ANSI C as it's output, which you would then compile, but later C++ compilers came about, and have been around since.


Well, C++ has deviated very far from C.

> 
Then came Java. A great idea, implemented poorly, with slow code execution for one thing. MS tried to gain a monopoly on it even though it wasn't theirs, and started implementing MS specific elements into it. A fateful court case happened and MS was banned from releasing its version of Java for some period of time. Choosing to circumvent that ruling, they invented C#, and had it defined as a standard, thus being another descendant of C, but somewhat less popular in the Linux world I fear, for although its ancestors are of noble blood, one of it's parents is MS.

Well, it was originally designed for devices. It just so happened that the web came along and it was made popular.

---

### Post by Greyed on 2008-06-25
> **LaRoza said:**
> Well, it was originally designed for devices. It just so happened that the web came along and it was made popular.

I'm still trying to figure out who's idea it was that Java would work well for devices when it is often 30-50 times larger than Python which is, in turn, about 4-10 times larger than compiled C.  Devices, of course, being limited in the amount of memory they have one would imagine you'd want a compact solution, not an obscenely bloated one.

---

### Post by xlinuks on 2008-06-25
And once again programming language flames, as usually everyone believes the technology he uses is the best around :)

---

### Post by DrMega on 2008-06-25
> **Greyed said:**
> I'm still trying to figure out who's idea it was that Java would work well for devices when it is often 30-50 times larger than Python which is, in turn, about 4-10 times larger than compiled C.  Devices, of course, being limited in the amount of memory they have one would imagine you'd want a compact solution, not an obscenely bloated one.

I guess it's just progress. Java was a fairly new idea when it came out. Prior to that embedded stuff was written in C, C++ or assembly language.

Java was a great idea. It was somewhere between the compactness and speed of a compiled language (like C) and the platform independence of an interpreted one. It just wasn't implemented very well. Incidentally, although it was a "fairly" new idea, it wasn't brand new. There was a flavour of Pascal that was designed for that exact same purpose that pre-dates Java, but it wasn't considered to be credible due to Pascal's origins as a teaching language.

---

### Post by pmasiar on 2008-06-25
> **nvteighen said:**
> I don't know where would computers be if either UNIX nor C hadn't existed.

why, we would hack in PL/1 in VMS, or RATFOR (Rational structured Fortran) on PDP/11 and Vax. There were nice technologies and smart people long before unix.
 
> Its (C language) historical importance relies on being the first high-level language (compared to Assembly) flexible enough but also small (very small) to create a whole OS. 

PL/1 was flexible and effective as C - unfortunately it was not small enough, because it contained all Cobol-like formatting needed to process business data. But for it's time, it was extremely nice language uniting business flexibility of Cobol, structured programming as Algol, and raw numeric power of Fortran.

PL/1 was C before C.

C++ is OOP language but lacks memory management.

IMHO programming will naturally separate into two layers: statically typed C for low-level libraries, and bunch of dynamically typed languages for developer's productivity - and Python will be leading this change. :-)

---

### Post by pmasiar on 2008-06-25
> **Greyed said:**
> I'm still trying to figure out who's idea it was that Java would work well for devices 

For devices with small memory, nothing (even ASM) can beat Forth. Forth was lost when PCs came along, and unwashed masses of users started writing macros in Lotus 1-2-3, and sadly never recovered.

25 years later, new programmers are reinventing  tricks and approaches from before PC era.

---

### Post by pmasiar on 2008-06-25
> **LaRoza said:**
> Fortran and Lisp are older (Fortran is the oldest, Lisp second), but I think C is probably third.

You are kidding, right? C was not even among first 1000 languages!

---

### Post by LaRoza on 2008-06-25
> **pmasiar said:**
> You are kidding, right? C was not even among first 1000 languages!

I mean, oldest languages still in development and in widespread use.

Lisp, Fortran and C have stayed alive and well for a long time.

---

### Post by DrMega on 2008-06-25
> **LaRoza said:**
> Lisp, Fortran and C have stayed alive and well for a long time.

Fortran is evil. We should burn it and bury its ashes deep underground, and build a huge perimeter wall round the burial site and have guard dogs patrolling.

I remember Fortran from my Uni days. I managed to block out much of the memory but I still remember their being too many full stops, and a massive list a functions that didn't have intuitive names, but instead had a letter and a serial number.

I did as much as I needed to do to get through my course work, and then went to the student bar to numb my brain with alcohol.

---

### Post by LaRoza on 2008-06-25
> **DrMega said:**
> Fortran is evil. We should burn it and bury its ashes deep underground, and build a huge perimeter wall round the burial site and have guard dogs patrolling.

I remember Fortran from my Uni days. I managed to block out much of the memory but I still remember their being too many full stops, and a massive list a functions that didn't have intuitive names, but instead had a letter and a serial number.


Things have changed ;)

I still use Fortran 77, but the latest developments are much more modern (Fortran 2008 is the latest I think)

It is still the most used language on super computers.

---

### Post by Greyed on 2008-06-25
> **pmasiar said:**
> nothing (even ASM) can beat Forth.

(ObJoke)
Third?
(/ObJoke)

---

### Post by nvteighen on 2008-06-26
> **pmasiar said:**
> why, we would hack in PL/1 in VMS, or RATFOR (Rational structured Fortran) on PDP/11 and Vax. There were nice technologies and smart people long before unix.

Of course there were nice technologies by smart people before UNIX, but you must admit UNIX was an advance and there it is still among us! (under spin-offs, of course).

> PL/1 was flexible and effective as C - unfortunately it was not small enough, because it contained all Cobol-like formatting needed to process business data. But for it's time, it was extremely nice language uniting business flexibility of Cobol, structured programming as Algol, and raw numeric power of Fortran.

PL/1 was C before C.

Yes, I know that... until C came out. A programming language is a tool; if a new tool comes out, the previous will have to compete. And there's no room for both. So, C displaced PL/1... Now, C has resisted C++ and heir-pretenders; if a language wants to throw C out from its place in this world, it will have to be a very good and mature one.

> 
IMHO programming will naturally separate into two layers: statically typed C for low-level libraries, and bunch of dynamically typed languages for developer's productivity - and Python will be leading this change. :-)

Never better said.

Conclusion from that paragraph of yours: C++ won't have a chance :)

---

### Post by DrMega on 2008-06-26
> **nvteighen said:**
> Yes, I know that... until C came out. A programming language is a tool; if a new tool comes out, the previous will have to compete. And there's no room for both. So, C displaced PL/1... Now, C has resisted C++ and heir-pretenders; if a language wants to throw C out from its place in this world, it will have to be a very good and mature one.
...
Conclusion from that paragraph of yours: C++ won't have a chance :)

Why should C and C++ have to compete? I don't get that. C++ can do *everything* that C can do. It is the logical progression from C, and in fact it started life as a text preprocessor that converted C++ to ANSI C ready for compilation.

To say that C and C++ have to compete, is like saying that Ubuntu Dapper and Ubuntu Hardy have to compete (OK the Hardy example is not ideal, given the problems that some have had with it).

Neither C nor C++ are in any danger of disappearing. If you need fast compact, super low level code, C or C++ are the idea choice. I've been a professional programmer for over 12 years now, and I can tell you that it is very common for an application to be built using several different languages, each best suited to a particular role. I doubt if that will change any time soon.

---

### Post by eryksun on 2008-06-26
> **LaRoza said:**
> Things have changed ;)

I still use Fortran 77, but the latest developments are much more modern (Fortran 2008 is the latest I think)

It is still the most used language on super computers.

Thankfully I never had to use Fortran... But I did have to use Lisp for a couple AI classes (and Prolog, but that's another story). I liked what could be accomplished with function mapping and lambda functions, but the recursive designs, mixed with all the nested parentheses, made me a little bug-eyed trying to debug even my own code. 

C++ is all over the map (imperative, OOP, functional, generic); it wants to be everything to every programmer. You can be a competent C++ programmer and get tripped up by parts of the language you rarely use. IMO, programming languages shouldn't be as diverse and ad hoc as natural languages. They're engineering tools, not Shakespeare.

Java and C# are good (I'm no Mono hater; maybe IronPython has a future), but bytecode distribution lends itself more to closed source, IMO. Parts of a program such as the user interface and glue logic should be readily and readably hackable on the live system. You shouldn't have to recompile everything. That's what I love about Python; it's a dynamically translated bytecode interpreter with dynamic data typing. A lot of [[COLOR="Blue"]people here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=594409"), including me, started using computers as kids in the late 70s to mid 80s on BASIC systems (Commodore 64, TRS 80, CoCo, Apple II, Sinclair, Atari -- most of which used licensed versions of Microsoft BASIC), so working in an interpreted language is practically in our blood. Performance takes a hit; but the truly CPU-bound parts of the back-end code, which only a handful of developers need to see, can be implemented in C (or C++, or even assembly), while the rest can be accelerated up to 40x (typically ~8x) with Psyco, a JIT compiler for Python. 

On the other hand, like C++, Python is multi-paradigm (imperative, functional, OOP), which makes reading someone else's code, who may use an entirely different mix of the 3 paradigms, a bit awkward and also counter to Python's own philosophy that there should be [[COLOR="Blue"]only one obvious way to solve a problem[/COLOR]]("http://www.python.org/dev/peps/pep-0020/") with Python.

---

### Post by CptPicard on 2008-06-26
> **DrMega said:**
> Why should C and C++ have to compete? I don't get that.

They don't really have to compete, but one can be statistically better than the other most of the time in the niche they are... :)

>  C++ can do *everything* that C can do.

Any other Turing-equivalent language can do everything any other Turing-equivalent language can do. This really is no argument, the actual point is somewhere else.

> If you need fast compact, super low level code, C or C++ are the idea choice.

But which one?

The point is that C++ for building the entire huge system is threatened. If and when you really need that super compact fast code, odds are that it actually is C you are looking for. C++ just adds unnecessary complication.

> I can tell you that it is very common for an application to be built using several different languages, each best suited to a particular role.

Agreed. Although what does change is the languages that take up those particular roles :)

---

### Post by nvteighen on 2008-06-26
> **DrMega said:**
> Why should C and C++ have to compete? I don't get that. C++ can do *everything* that C can do. It is the logical progression from C, and in fact it started life as a text preprocessor that converted C++ to ANSI C ready for compilation.

Well, what you say is evidence that they competed at certain point. C++ was created as a superset of C, i.e. to replace it, because Soustrup thought C wasn't enough for programmer needs. Otherwise, he wouldn't have bothered that much. Both languages initially were meant to be system/application languages, targeting the same kind of goals.

What happened? It seems to me that C's and C++'s goals have diverged. C, low-level libraries, drivers and systems; C++, end-user applications.

Maybe nowadays C++'s competition is against other OOP-languages like Java and C#, languages also meant for applications. C++ is not dead and probably those languages won't put it on any serious danger... The danger comes from higher-level languages. Why would you mind to use C++ if you can do the same in Python + C to gain speed in one function? Or will you use C++, a OOP language, combined to another OOP one just to do low-level stuff? Isn't that a waste?

But then, again, I'm not an expert and I may be proven to be wrong. I hope to have explained what I meant... *EDIT: CptPicard has explained it better (and faster) than myself*

---

### Post by pmasiar on 2008-06-26
C++ does allow tight control over big projects, but for the price of being really really complex.  If you need the speed in a huge project and are ready to pay the price (in slow development time), C++ is good choice. 

I know only one project where using anything else (except C++) would not make sense: automatic stock trading program, where being 10ms faster that the other guys can make you 100M USD **a day** (and being slower will lose you the same amount), because dozen trading houses place trades based on same ticker info.

But even these guys write automated tests for C++ in Ruby - it is just so much faster and easier to do.

Other niches for C++ I can imagine is Google's custom file system (BigTable), database engine, etc: deep dark areas of huge systems.

For most other apps, developer's productivity and design flexibility is more important, and if you need speed, you get it simpler by writing (relatively small) C libraries (reimplementing prototypes done in HHL), called from HHL like Python.

---

### Post by DrMega on 2008-06-26
> **CptPicard said:**
> They don't really have to compete, but one can be statistically better than the other most of the time in the niche they are... :)

Sorry, I still don't get it. How can one be statistically better? If you mean that more people use one over the other, that doesn't make one better, it just makes it more popular.

> **CptPicard said:**
> Any other Turing-equivalent language can do everything any other Turing-equivalent language can do. This really is no argument, the actual point is somewhere else.

I point was in answer to somebody else's point that C and C++ are in competition with each other. I don't see that.

> **CptPicard said:**
> But which one?

The point is that C++ for building the entire huge system is threatened. If and when you really need that super compact fast code, odds are that it actually is C you are looking for. C++ just adds unnecessary complication.

C++ doesn't add any complication. You don't have to use the extra features. Admittedly C will let you get away with some stuff the C++ is more particular about. C isn't as strongly typed as C++ and you can, for example, assign a character to an integer without complaint, whereas C++ would have something to say unless you made an explicit cast, but that's the only real thing that I'm aware of that breaks backward compatibility with C. C++ offers much more concise and clean ways of doing certain things, all things which are possible in C, but would take more code to achieve.

> **CptPicard said:**
> Agreed. Although what does change is the languages that take up those particular roles :)

Agreed to some extent, but often you will be expected to work on an established system that still has need for development skills in older languages, while newer elements might be written in newer languages (or using newer technologies). My defence of C++ wasn't because I think it is always (or even mostly) the right tool for the job. I just couldn't and can't understand why some people consider C and C++ to be in competition with each other.

---

### Post by Mickeysofine1972 on 2008-06-26
I dont think C and C++ are in competition really.

Also, I seem to remember that the kernel is written in mostly C. I know all the usb driver info I've looked at for making modules for different devices are all in C.

This is just my opinion of course but I personally like C and C++ in equal amounts.

Mike

---

### Post by Mickeysofine1972 on 2008-06-26
> **Greyed said:**
> ...  Them thar's fighting words.  :P

LMAO !

You know he's right  !!!!

Mike

---

### Post by nvteighen on 2008-06-26
> **DrMega said:**
> 
C++ doesn't add any complication. You don't have to use the extra features. Admittedly C will let you get away with some stuff the C++ is more particular about. C isn't as strongly typed as C++ and you can, for example, assign a character to an integer without complaint, whereas C++ would have something to say unless you made an explicit cast, but that's the only real thing that I'm aware of that breaks backward compatibility with C. C++ offers much more concise and clean ways of doing certain things, all things which are possible in C, but would take more code to achieve.

That's the point: why do you want to use C++ without its particular features? That way would be the same as creating a program and link it to a library that you don't use...

What I meant is that C and C++ had to fight over the same "market" because the later was meant to be a superset of C. Times changed and now we have C++ running against Java and C# on the OOP application programming. And C seems unbeatable, monopolizing lower-level system and drivers programming... at least for now, until something does that job better. 

> Agreed to some extent, but often you will be expected to work on an established system that still has need for development skills in older languages, while newer elements might be written in newer languages (or using newer technologies). My defence of C++ wasn't because I think it is always (or even mostly) the right tool for the job. I just couldn't and can't understand why some people consider C and C++ to be in competition with each other.

No, I don't claim you're defending "C++ for anything". That's absurd. Let's code a webpage in C++!... (The sad part is that some "leet" kiddie could try to do it...). Programming languages are tools and you have to use the best tool for your task; but why use a missile/C++ to just kill a mouse/search for a regexp?

---

### Post by DrMega on 2008-06-26
> **nvteighen said:**
> That's the point: why do you want to use C++ without its particular features? That way would be the same as creating a program and link it to a library that you don't use...

...

Programming languages are tools and you have to use the best tool for your task; but why use a missile/C++ to just kill a mouse/search for a regexp?

I agree, but my point is, given that C++ is the natural progression from C, I don't see the point in having two seperate compilers. I know we have one compiler for both jobs, but the point I'm trying to make is that while someone shunned C++ because C is better, I'm trying to get to the bottom of that logic. If I could only have one compiler on my machine, and it could only compile C or C++, I would choose the C++ one because as I see it, the syntax differences between ANSI C and C++ are minimal, but if you need them, you have the extra features of C++ at your disposal at the same time.  My persistence on this line of enquiry started from someone claiming that C and C++ were competing with one another, which I don't see.

> **nvteighen said:**
> No, I don't claim you're defending "C++ for anything". That's absurd. Let's code a webpage in C++!... (The sad part is that some "leet" kiddie could try to do it...).

Ah yes, the early days of dynamic websites, with CGI :) It's not so different now though really. PHP is a very powerful language, it has developed very far beyond its humble origins as a basic scripting language.  PHP is fully object oriented.

---

### Post by Frak on 2008-06-26
Why program in C? It's low level. And C++ really isn't low level, more mid-level.

Isn't that enough?

---

### Post by Wybiral on 2008-06-26
> **DrMega said:**
> I know we have one compiler for both jobs, but the point I'm trying to make is that while someone shunned C++ because C is better, I'm trying to get to the bottom of that logic. If I could only have one compiler on my machine, and it could only compile C or C++, I would choose the C++ one because as I see it, the syntax differences between ANSI C and C++ are minimal, but if you need them, you have the extra features of C++ at your disposal at the same time.

The thing is that C compilers are optimized for C code (and optimized very well for that purpose), while C++ compilers are optimized for C++.

I _need_ the C compiler, because I need the ease of linking to symbols and creating modules and bindings for other languages. I don't need the C++ compiler, because it has poor support for these things, mangles names, adds things like the vtables, etc.

---

### Post by Greyed on 2008-06-26
Ok, here's my take as neither a C or C++ programmer but someone who does look into why things are adopted like, for example, Linux on the desktop.  >.>

Why C over C++ is the wrong question to ask.  The right question is why C++ over C?  Since C is the incumbent it is C++ that has to compete, yes, *compete* for people who program in C.  For C++ to get people to switch it is not enough to be kinda ok at doing what C does.  It has to be clearly better at doing what C does.  It can't just have more stuff bolted on.  It has to have more stuff which is polished and works and, importantly, makes sense to a C programmer.

From what I have read on the net the problem with C++ is that it does not meet those requirements well enough for the people for whom it matters.  The old stuff isn't supported well enough to have people switch and maintain their old habits.  The new stuff isn't polished or works well enough to compel people to switch.  In a nutshell, I get the impression that C++ encumbers the user with more work than it benefits the user.  Even if that ratio is even it isn't enough.  The additional work a language gives the programmer has to be greatly exceeded by the benefits to compel a switch.  Not break even.  Not a little gain in benefits over work.  The benefits have to be pronounced.

That is why earlier in the thread someone said that C++ is doomed because it is bracketed.  It has C as a lower boundary and Perl/Python/Ruby encroaching on the upper boundary.  It is not sufficiently beneficial over C for the average C jockey to switch.  On the flip side any new programmer is apt to aim much higher than C++'s baby step past C and go for one of the interpreted languages because the benefits they give and the relatively minor drawbacks as compared to C++ far outweigh the extra work involved.

So, yes, C++ is competing with C because it's users are going to largely come from that base.  It has to be a large enough step forward to overcome inertia and the cost of learning/extra work.  The real debate is if that step forward is large enough.

---

### Post by Frak on 2008-06-26
C++ just feels like a poor attempt at tacking on features and promising RAD.

---

### Post by nvteighen on 2008-06-26
> **Frak said:**
> Why program in C? It's low level. And C++ really isn't low level, more mid-level.

Isn't that enough?

That's part of the problem. To be in the middle and keep there makes you target to lower-level programmers and higher-level simultaneously (and keep things harmonically integrated to the language).

And to claim C shouldn't be used because it's low level is ridiculous. There are things you must do in low-level languages; others in high. The problem is what to do with the languages that are between them... as Greyed explained in his post: beginners for high-level and experienced have sticked with a senior language that still does its job done.

---

### Post by Frak on 2008-06-26
> **nvteighen said:**
> That's part of the problem. To be in the middle and keep there makes you target to lower-level programmers and higher-level simultaneously (and keep things harmonically integrated to the language).

And to claim C shouldn't be used because it's low level is ridiculous. There are things you must do in low-level languages; others in high. The problem is what to do with the languages that are between them... as Greyed explained in his post: beginners for high-level and experienced have sticked with a senior language that still does its job done.
I was supporting C, since I'm a skeptic of C++.

---

### Post by DrMega on 2008-06-26
> **Frak said:**
> Why program in C? It's low level. And C++ really isn't low level, more mid-level.

Isn't that enough?

No. The point was that somebody claimed that C and C++ were in competition with each other. C++ is capable of being very low level, but I'll admit, if forced to choose for really low level stuff, I would choose C, but if I needed a generic language that was good for a wide range of jobs, a multirole language if you will, then C++ would be my choice.

There is no competition, just tools for jobs. I'm not persisting with this line of enquiry because I want to prove that one is better than the other, I am just trying to get to the bottom of the logic behind the claim that C and C++ are in competition in some way.

> **Wybiral said:**
> The thing is that C compilers are optimized for C code (and optimized very well for that purpose), while C++ compilers are optimized for C++.

I _need_ the C compiler, because I need the ease of linking to symbols and creating modules and bindings for other languages. I don't need the C++ compiler, because it has poor support for these things, mangles names, adds things like the vtables, etc.

Excellent point. I'd forgotten about name mangling. You can get round that of course (at least you could on MS's implementation, which I have to admit I'm more familiar with than any other implementation). You can declare stuff as extern_C (or something like that - long time since I've used it), but you are right, in C you don't have to mess about with that.

---

### Post by pmasiar on 2008-06-26
> **DrMega said:**
> I agree, but my point is, given that C++ is the natural progression from C, 

"natural progression"? why? and where?

You may enjoy [interview with Stroustrup](http://www.chunder.com/text/ididit.html) even if fake :-)

---

### Post by LaRoza on 2008-06-26
> **DrMega said:**
> I agree, but my point is, given that C++ is the natural progression from C, 


I don't see it as a natural progression. C is small, elegant and powerful. C++ is big language with a small language trying to get out.

I would say Objective-C is a natural progression if anything.

---

### Post by Frak on 2008-06-26
I find [D]("http://en.wikipedia.org/wiki/D_%28programming_language%29") to be a natural progression from [C]("http://en.wikipedia.org/wiki/C_(programming_language)"), as was a progression from [B]("http://en.wikipedia.org/wiki/B_%28programming_language%29").

---

### Post by LaRoza on 2008-06-26
> **Frak said:**
> I find [D]("http://en.wikipedia.org/wiki/D_%28programming_language%29") to be a natural progression from [C]("http://en.wikipedia.org/wiki/C_(programming_language)"), as was a progression from [B]("http://en.wikipedia.org/wiki/B_%28programming_language%29").

I was going to say something like that, but I wanted to stick to the language instead of names. :-)

---

### Post by Frak on 2008-06-26
> **LaRoza said:**
> I was going to say something like that, but I wanted to stick to the language instead of names. :-)
I wanted to learn 3 letters of the Alphabet, skipping A. So, I guess I win now.

---

### Post by LaRoza on 2008-06-26
> **Frak said:**
> I wanted to learn 3 letters of the Alphabet, skipping A. So, I guess I win now.
[http://en.wikipedia.org/wiki/A%2B_(programming_language](http://en.wikipedia.org/wiki/A%2B_(programming_language))

Might be worth learning if you have that goal.

---

### Post by DrMega on 2008-06-26
> **LaRoza said:**
> I don't see it as a natural progression. C is small, elegant and powerful. C++ is big language with a small language trying to get out.

I would say Objective-C is a natural progression if anything.

<sigh> I give up.

People keep trying to draw me in to debates about why C is better than C++ or vice versa, when all I was trying to do was get to the bottom of the logic behind the claim that C and C++ are in competition.

I guess it will remain one of life's enigmas.

---

### Post by LaRoza on 2008-06-26
> **DrMega said:**
> <sigh> I give up.

People keep trying to draw me in to debates about why C is better than C++ or vice versa, when all I was trying to do was get to the bottom of the logic behind the claim that C and C++ are in competition.

I guess it will remain one of life's enigmas.

I was quoting the C++ creator in my description of C++ there, even he realises it.

---

### Post by ankursethi on 2008-06-26
C++ is okay if you use it simply as "C with classes". A little bit of OOP here and there never hurt anybody. But then it goes overboard and tries to do stuff that it wasn't *supposed* to do in the first place. I never could make out what to do with templates and the STL. Now I've happily forgotten how to use both.

Geeks, by nature, like the deadly combination of power + simplicity + uniformity. All the successful languages in the FOSS world possess these three qualities. Python is simple, Ruby is a bit complex but defines logical and clear rules for every little feature (uniformity at it's best), Lisp is simplicity at it's best and we all know about C. C++ is powerful, but it's neither simple nor uniform. Most C++ syntax seems to be tacked on as an afterthought. So no, FOSS doesn't really like C++ very much.

I'm just waiting for D to become mainstream. I doubt it will take more than an year or two for programmers to wake up to this nice little language, and then we can live peacefully once again, conveniently forgetting that a beast as vile as C++ ever existed.

---

### Post by LaRoza on 2008-06-26
> **ankursethi said:**
> 
I'm just waiting for D to become mainstream. I doubt it will take more than an year or two for programmers to wake up to this nice little language, and then we can live peacefully once again, conveniently forgetting that a beast as vile as C++ ever existed.

D is highly used: [http://www.tiobe.com/index.php/content/paperinfo/tpci/index.html](http://www.tiobe.com/index.php/content/paperinfo/tpci/index.html)

---

### Post by DrMega on 2008-06-26
> **LaRoza said:**
> D is highly used: [http://www.tiobe.com/index.php/content/paperinfo/tpci/index.html](http://www.tiobe.com/index.php/content/paperinfo/tpci/index.html)

EDIT: Remove the links, they didn't work.

Do a skills search on here for both 'C' and then 'D'

[http://www.jobserve.com]("http://www.jobserve.com")

---

### Post by ankursethi on 2008-06-26
> D is highly used: [http://www.tiobe.com/index.php/conte...pci/index.html](http://www.tiobe.com/index.php/conte...pci/index.html)
Whoa, nice :). It's just that I didn't see many mainstream OSS projects written in it ...

---

### Post by LaRoza on 2008-06-26
> **DrMega said:**
> EDIT: Remove the links, they didn't work.

Do a skills search on here for both 'C' and then 'D'

[http://www.jobserve.com]("http://www.jobserve.com")

My links worked (sometimes that site will lag though)

I am not saying for jobs, but for use.

> **ankursethi said:**
> Whoa, nice :). It's just that I didn't see many mainstream OSS projects written in it ...

Well, there is not much in the way. Perhaps it just needs a push.

---

### Post by DrMega on 2008-06-26
> **LaRoza said:**
> I am not saying for jobs, but for use.

Did you do a search on Jobserve? It's a massive well established recruitment site. It started life more than 10 years ago as a specialist IT recruitment site in the UK. Since then it has grown to include jobs from all over the world. Not a single job for a "D" programmer though. Not anywhere, nada, zip, zilch, not anywhere on the planet.

---

### Post by LaRoza on 2008-06-26
> **DrMega said:**
> Did you do a search on Jobserve? It's a massive well established recruitment site. It started life more than 10 years ago as a specialist IT recruitment site in the UK. Since then it has grown to include jobs from all over the world. Not a single job for a "D" programmer though. Not anywhere, nada, zip, zilch, not anywhere on the planet.

No, I am not going by jobs.

I don't care if D programmers are being hired or not.

---

### Post by Frak on 2008-06-26
> **DrMega said:**
> Did you do a search on Jobserve? It's a massive well established recruitment site. It started life more than 10 years ago as a specialist IT recruitment site in the UK. Since then it has grown to include jobs from all over the world. Not a single job for a "D" programmer though. Not anywhere, nada, zip, zilch, not anywhere on the planet.
Then the site is wrong. I've gotten recruitments for the U.S. Military for C, C++, Python, Delphi, Lisp, Perl and **D **programmers.

---

### Post by DrMega on 2008-06-26
> **Frak said:**
> Then the site is wrong. I've gotten recruitments for the U.S. Military for C, C++, Python, Delphi, Lisp, Perl and **D **programmers.

The site isn't wrong. It doesn't list *every* job going, just a lot. If you search for C, C++, C#, Java, Basic, Cobol, Delphi.... you'll see it has hundreds and in some cases thousands of jobs, yet not a single one for 'D'.

---

### Post by CptPicard on 2008-06-26
D is new... it says nothing regarding the language's merits.

For example, I am a consultant who fortunately gets to choose one's language. I don't go by popularity contests. If D fits the bill, I use it... (I don't know it though)

---

### Post by DrMega on 2008-06-26
> **CptPicard said:**
> D is new... it says nothing regarding the language's merits.

For example, I am a consultant who fortunately gets to choose one's language. I don't go by popularity contests. If D fits the bill, I use it... (I don't know it though)

I agree. I posted the jobserve link in response to a claim that it was widely used. I didn't say there was anything wrong with 'D', I've never even seen it, it might be the next best thing since sliced bread, but it's not widely used in the industry (yet).

---

### Post by Greyed on 2008-06-26
This isn't unexpected though.  It takes time for languages to catch on.  I mean I still consider Python as "new" even though I personally have been programming in it for close to a decade and it's coming up on its 20th birthday in just a scant 3 years time.  20 years and it's just now cracked 6-7% of projects tracked at ohloh.net.

On the other hand I am exciting since I see more and more Python positions offered.  I'd love to land one of those since the more I program in Python the more I fall in love with the language.

---

### Post by LaRoza on 2008-06-26
> **CptPicard said:**
>  (I don't know it though)
Think: C++ that doesn't try to be C and Java at once.


> **DrMega said:**
> I agree. I posted the jobserve link in response to a claim that it was widely used. I didn't say there was anything wrong with 'D', I've never even seen it, it might be the next best thing since sliced bread, but it's not widely used in the industry (yet).

It is like a (C++)++

---

### Post by ankursethi on 2008-06-27
Most languages start life with hobbyist and FOSS programmers writing small tools and utilities in them. It takes a while for them to catch on.

BTW, here are some D tutorials right now : [http://www.dsource.org/projects/tutorials/](http://www.dsource.org/projects/tutorials/)

(I need to start looking into this stuff. It's neat.)

---

### Post by Mickeysofine1972 on 2008-06-27
D looks ok but I cant really see what it does thats not covered by C/C++ or Python/Ruby.

BTW does anyone remember about 10 years ago you could get C-- ?

I tried googling for it but cant find the site anymore.

Mike

---

### Post by techmarks on 2008-06-27
uhmm... the thread is mostly just posturing going on.



[IMG]http://www.idg.com.au/gim.php/id/6598/res/2[/IMG]
Bjarne Stroustrup creator of C++



This is the link, I think it quite interesting;

[http://www.computerworld.com.au/index.php/id;408408016;pp;1;fp;16;fpid;1]("http://www.computerworld.com.au/index.php/id;408408016;pp;1;fp;16;fpid;1")

---

### Post by henchman on 2008-06-27
is one able to load a dynamic c++ library (eg. .so, .dll) into a d program? or to static link like this?

---

### Post by eryksun on 2008-06-27
> **techmarks said:**
> This is the link, I think it quite interesting;

[http://www.computerworld.com.au/index.php/id;408408016;pp;1;fp;16;fpid;1]("http://www.computerworld.com.au/index.php/id;408408016;pp;1;fp;16;fpid;1")

I've read Bjarne's [[COLOR="Blue"]book on C++[/COLOR]]("http://www.amazon.com/dp/0201700735"), some of his articles and interviews (including this one), but I still don't understand why C++ needs to handle every paradigm (imperative, OOP, functional, and generic). Imperative, ok, you need that for C compatibility. But why add on functional and generic programming? Should I really have to learn all that to honestly say I'm a C++ programmer (i.e. able to debug any C++ code you put before me without spending hours paging through technical docs like some tourist with a pocket phrase book)?

Ideally, what I would want is a simple imperative scripting language that can dynamically link objects (everything from GUI elements/events to file systems to an FFT algorithm) created by specialty languages (low-level assembly, high-level imperative, asbtract OOP, stateless functional, or whatever else someone can dream up). One problem, one object, created with one best-suited programming paradigm. Let the objects advertise their I/O data types. The OS would consist of an object store, including basic system objects and the master scripting object. You can boot to a coding prompt just like the 8-bit BASIC systems of the early 80s, and use scripts to weave together any kind of system you want, as long as you have the objects. 

If I've paid for some bit of code in Microsoft Office, why should I be limited in how I can use it on *my* system? MS Office would become an [expensive] suite of objects and scripts. But once it's on your system, any designer could come up with a script to use the objects, according to their advertised input/output data types, however the designer pleased, even in totally novel ways. But more likely people would opt for free (as in beer) objects that let people see what the objects do, and how they do it, and compile them for whatever hardware architecture and on as many systems as they want.

Feel free to tell me I'm insane; it's only a dream.

---

### Post by LaRoza on 2008-06-27
> **henchman said:**
> is one able to load a dynamic c++ library (eg. .so, .dll) into a d program? or to static link like this?

I think they can use shared libraries. Check the references for D.

---

