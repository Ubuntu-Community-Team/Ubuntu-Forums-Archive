---
title: "How Do I Write Programs For Windows?"
date: 2007-08-23
forum: Programming Talk
---

### Post by Noodels on 2007-08-23
Hi there, I have another annoying question to a problem about programming. Ever since I've started using ubuntu and writing programs most of the time they work fine for me, and when they don't work for me it's just because I've made some stupid mistake somewhere. But, when I write a program and send it to windows, apparently there's some sort of illegal instruction and the program wont run, EVEN if I put a .exe extension on the end (apparently windows likes to have those). So my question is this :

How do I compile windows compatible programs?

---

### Post by Paul820 on 2007-08-23
You can't compile a program in linux and expect it to execute in windows. It's a completely different environment. What programming language are you using? You never said.

---

### Post by Noodels on 2007-08-23
I am using C. Is there some sort of program or something that takes the source file to compile and emulates a windows compiler to make a program useless to me but works on a windows computer?

---

### Post by Paul820 on 2007-08-23
If you keep to the standards and not use any system specific calls you will be fine for basic programs for the terminal ( console ). I have never heard of a compiler emulating a windows compiler, the only way to make the program run in another environment is by modifying the code and then rebuilding in that environment.

When you write code in windows, lots of things get added to the finished exe. Things specific to windows.

---

### Post by aks44 on 2007-08-23
> **Paul820 said:**
> You can't compile a program in linux and expect it to execute in windows.

Wrong. I'd rephrase it: you can't compile a program *for* Linux and expect it to execute in Windows. But you can compile a program *on* Linux *for* Windows.

> **Noodels said:**
> But, when I write a program and send it to windows, apparently there's some sort of illegal instruction and the program wont run, EVEN if I put a .exe extension on the end (apparently windows likes to have those). So my question is this :

How do I compile windows compatible programs?

The mingw toolkit is a Linux C++ cross-compiler for Windows targets. Qt makes a good cross-platform library (GUI as well as lower level stuff). I guess this could be possible using GTK too, and wxWidgets is also an option (not sure for all the system stuff concerning those two though).


As far as I'm concerned I managed to have a working cross-compilation environment for both Linux and Windows targets, using Qt4.
However I quite struggled to fully set it up, I'm not quite sure what I really did (I tinkered with it for more than a week before having it working).

So concerning mingw+Qt4 all I could do for now is give you a bunch of links and my Qt4 x-win32-g++ mkspecs if you are interested. Putting it all together is left as an exercise, since I don't remember what I did exactly (promised, when I switch to 7.10 I'll keep track of the install procedure and make a howto out of it ;)).


Note however that even though C++ is not for the faint of heart, setting this kind of environment for the first time is, well... pretty hardcore even for an experienced C++ programmer.

As a comparison (keep in mind I never used a Linux/Unix environment before installing Ubuntu) :
- setting up G++, first hello world program on Linux: 10mn (most of this time spent reading)
- setting up Qt4, first Qt hello world on Linux: I guess about 15mn (plus maybe 30mn of read)
- setting up a Linux/Windows Qt4 cross-compilation environment: errrmmm... 20, 30 hours, dunno for sure. :oops: But as a result I managed to write a "xmake" script (equivalent in functionnality to qmake) that handles Qt .pro projects correctly for both platforms. :D

Seeing how you don't even know the difference between both runtime environments, system APIs, PE vs ELF etc etc, I would strongly advise you to forget what I just said. Go for something easier (Python anyone? ;)).


EDIT: I just saw you are using C. So I guess Qt is not an option for you. Maybe mingw is still something to explore though. I may even be easier to just use vanilla mingw rather than also trying to integrate Qt into it.
Yet if anyone is interested I can still post the links that helped me, and the few scripts / mkspecs I wrote for Qt4.

---

### Post by Quikee on 2007-08-23
> **Paul820 said:**
> I have never heard of a compiler emulating a windows compiler, the only way to make the program run in another environment is by modifying the code and then rebuilding in that environment.


Not really... you can cross-compile binaries even for Windows (GCC ia also available for windows). In the repository there is a package called minigw32 which is exactly that - a cross compiler for linux to build windows binaries. But don't ask me how.. I never done it. Search for a how-to ;)

---

### Post by AnRa on 2007-08-23
Install [mingw32](http://packages.ubuntu.com/feisty/devel/mingw32). ;)

---

### Post by pmasiar on 2007-08-23
> **Paul820 said:**
>  the only way to make the program run in another environment is by modifying the code and then rebuilding in that environment.

So you need to use C preprocessor to create separate code snippets for different environments, when compile in Windows. It is hard work and that's why not many people are willing to stand the pain.

You may want to consider Mono, which reimplemented C#/.NET (with some success and some failures), or other cross-platform language like Python. You will still need be careful about platform dependencies and use proper libraries, but your life might be easier.

It's hard to tell because we don't know what you want.

---

### Post by Paul820 on 2007-08-23
Never even heard of mingw32 :) So i was wrong, sorry about that.

---

### Post by aks44 on 2007-08-23
[QUOTE=pmasiar]Join with your sig to terminate Endless September![/QUOTE]

Huh, just noticed your sig. I almost forgot about that, yet I was wondering why so many threads... Silly me. ;)

---

### Post by aks44 on 2007-08-23
> **pmasiar said:**
> So you need to use C preprocessor to create separate code snippets for different environments, when compile in Windows. It is hard work and that's why not many people are willing to stand the pain.

You don't want to do that. What you really want is to use a cross-platform library that exposes a single API whatever platform you run on (as I said previously, Qt is one of those, but it's C++ ; dunno about any C one).

---

### Post by pmasiar on 2007-08-23
> **aks44 said:**
> You don't want to do that. What you really want is to use a cross-platform library that exposes a single API whatever platform you run on (as I said previously, Qt is one of those, but it's C++ ; dunno about any C one).

Yes you are right. **I don't** want to do that, and I hope I never will have to! :-)

I was giving my "best guess" advice, (how to do it if you cannot find sane cross-platform library) but others (like you) gave better advice. Including suggesting Python :-)

---

### Post by Noodels on 2007-08-23
I was only gone two hours and now I have all this! Okay, I'm going to look through the suggestions and probably skip the harder ones, if all that fails I'll see what happens when I use a windows compiler through wine. Thanks for the help everyone!

---

### Post by aitorcalero on 2007-08-24
Very simple, use Java, :D

---

### Post by samjh on 2007-08-24
> **Noodels said:**
> I was only gone two hours and now I have all this! Okay, I'm going to look through the suggestions and probably skip the harder ones, if all that fails I'll see what happens when I use a windows compiler through wine. Thanks for the help everyone!

For C and C++, I run Dev-C++ (which includes the mingw32 compiler and tools) on Wine.  Works like a charm.

---

### Post by LaRoza on 2007-08-24
> **samjh said:**
> For C and C++, I run Dev-C++ (which includes the mingw32 compiler and tools) on Wine.  Works like a charm.

I was going to recommend that also, you can use gcc and g++ from the command line, with that also, just set your path to look in C:\Dev-cpp\bin assuming you installed in the default location.

Interestingy, it also works in Wine, so you can compile it there.

---

### Post by Wybiral on 2007-08-24
> **aks44 said:**
> You don't want to do that. What you really want is to use a cross-platform library that exposes a single API whatever platform you run on (as I said previously, Qt is one of those, but it's C++ ; dunno about any C one).

There's nothing wrong with using preprocessor directives in C to create more portable code. Sure, in a perfect world you can have every library you need completely cross platform (this is where pmasiar jumps in and says "you can, it's called python").

But the world isn't perfect, if you want your C code to be portable, sometimes you have no choice. Not just for operating systems either, you may need to change certain algorithms as a result of the machine (32bit vs 64bit / endianness / inline assembly).

C++ users may frown on this, but it is part of the language and sometimes you just need to. Naturally, the goal is to avoid it wherever you can, but if that leads to bloated/inefficient code trying to get around it... Just use a portable language to begin with (such as python) and save yourself the time/trouble.

---

### Post by pmasiar on 2007-08-24
> **Wybiral said:**
> in a perfect world you can have every library you need completely cross platform (this is where pmasiar jumps in and says "you can, it's called python").

Sadly, even with big efforts, some python libraries don't work on Windows. Most do, but not all, you need to check. Windows sucks so mightily it can suck  mountains - mountain ranges! Continents! Planets! Sorry dudes, close, but no cigar. Just switch to Ubuntu :-)

> Just use a portable language to begin with (such as python) and save yourself the time/trouble.

It is amazing, that with dedicated effort, ingenuity, lots of sweat, and bit of luck, you can overcome problems which you would not have if you picked proper platform :-)

---

### Post by kcirtap on 2007-08-24
Shouldn't it be enough to code according to the standard? C is a portable language after all if you skip the unportable libraries and system calls.

---

### Post by Noodels on 2007-08-24
> **aitorcalero said:**
> Very simple, use Java, :D

I speak amateur in many computer languages. (Uh, I think 4... But 4 is many!) Java not being one of them, and I always thought of Java as a less powerful language, probably due to all the applications I've seen for it I never though that good, being high level you can do more stuff but it requires more cpu (not exactly got a lot of that at the mo (1.4Ghz someone save me plz!)). I prefer lower level languages, and if I need to I'll set up functions.

> **samjh said:**
> For C and C++, I run Dev-C++ (which includes the mingw32 compiler and tools) on Wine.  Works like a charm.

Oh if only I knew how... Unfortunately me being me and amateurish after installing mingw32 I was completely at a loss as to how to actually use it....:(

> **LaRoza said:**
> I was going to recommend that also, you can use gcc and g++ from the command line, with that also, just set your path to look in C:\Dev-cpp\bin assuming you installed in the default location.

Interestingy, it also works in Wine, so you can compile it there.

I DO use gcc from the command line though, I didn't even know I had a choice! :D

> **Wybiral said:**
> There's nothing wrong with using preprocessor directives in C to create more portable code. Sure, in a perfect world you can have every library you need completely cross platform (this is where pmasiar jumps in and says "you can, it's called python").

But the world isn't perfect, if you want your C code to be portable, sometimes you have no choice. Not just for operating systems either, you may need to change certain algorithms as a result of the machine (32bit vs 64bit / endianness / inline assembly).

C++ users may frown on this, but it is part of the language and sometimes you just need to. Naturally, the goal is to avoid it wherever you can, but if that leads to bloated/inefficient code trying to get around it... Just use a portable language to begin with (such as python) and save yourself the time/trouble.

I did learn a little python, but the tutorial site I have is all awkward and it's very hard to learn from there. Currently I use python as a calculator, my favourite thing being that you can set up integers unlike a usual calculator. I would like to learn more python but I'm going to have to go through THAT site. [shudder]

> **pmasiar said:**
> Sadly, even with big efforts, some python libraries don't work on Windows. Most do, but not all, you need to check. Windows sucks so mightily it can suck  mountains - mountain ranges! Continents! Planets! Sorry dudes, close, but no cigar. Just switch to Ubuntu :-)

Hell yeah! The only reason I am asking this is because I have friends who have not "seen the light" as it were and always like to show off whatever I've just learned in C or whatever. The only reason I haven't put a dual boot of windows to go with ubuntu on my laptop (video game addict) is because then I'd have to deal with windows [shudder].

> **kcirtap said:**
> Shouldn't it be enough to code according to the standard? C is a portable language after all if you skip the unportable libraries and system calls.

It's a very basic code, but no matter how basic the code, windows just wont have it, at the moment I am using a compiler on my poor laptop that bears the burden of windows, it's really annoying, it keeps telling me to register, the nerve of asking someone to pay for something they've worked hard on, tsk. :D

Well that was a long reply...

---

### Post by Wybiral on 2007-08-24
> Shouldn't it be enough to code according to the standard?

In a world where standards are always implemented properly and every compiler for every platform was the same. Unfortunately some platforms simply refuse the standards or try to reinvent them all together.

> C is a portable language after all if you skip the unportable libraries and system calls.

Skipping the unportable libraries is not always an option.

---

### Post by aks44 on 2007-08-24
> **Wybiral said:**
> There's nothing wrong with using preprocessor directives in C to create more portable code.
[...]
you may need to change certain algorithms as a result of the machine (32bit vs 64bit / endianness / inline assembly).

C++ users may frown on this, but it is part of the language and sometimes you just need to.

You sure made a point. However, I found that trying to write portable low level stuff (network, threads etc) really is a pain in the *** (especially the testing part, when you don't have access to alien platforms). So, why bother when there are boost, ACE+TAO, Qt, GTK+ or wxWidgets out there? :)
And yes, C++ users are really relunctant to use most precompiler directives, those things are just plain [Evil]("http://www.parashift.com/c++-faq-lite/big-picture.html#faq-6.15").


> **kcirtap said:**
> Shouldn't it be enough to code according to the standard? C is a portable language after all if you skip the unportable libraries and system calls.

If you want to restrict yourself to console mode, and don't need network or other "advanced" stuff then yes, go for it...

C may be portable but the *standard* is **very** limited (just as the C++ standard BTW).

The goal of a programming language standard is to be the greatest common denominator between all platforms it is intended to run on, ie. nothing much useful (read: fancy) in real life applications, unfortunately (yes, GUIs, networking, multithreading etc are "fancy" stuff in standardese since they can hardly be standardized).


So we will always need an additional layer of abstraction that hides the platform specifics in order to provide a uniform portable framework, and as Wybiral put it, that layer has to use Evil tricks to achieve its goal.

---

### Post by pmasiar on 2007-08-24
> **Noodels said:**
> I always thought of Java as a less powerful language...I prefer lower level languages, and if I need to I'll set up functions.

Java is not "less powerfull" - it is just placing priorities in wrong (for me) places. IMHO it is strange idea to have **virtual** machine, when you already have **real** one at your desk :-) Virtualization comes with price, and not all people (including me, and apparently, you) are willing to pay it, and learn it, and abstract into JVM all the functionality from perfectly good C libraries which do most of this abstraction, and much faster.

So you can have high level language what can access all low level functions of underlying OS using effective  wrappers (not too thin, not too thick, not too dumb), like Python. There are language for writing low-level functionality (C), and languages to use those libraries to solve problems in flexible ways (like Python). Java tries to be both, and fails both ways, IMHO.

> I did learn a little python, but the tutorial site I have is all awkward and it's very hard to learn from there. 

Use better one! "Dive Into Python" book should work for you if you are programmer, and know what variable, loop, and function is. You can even download it for free. Python has loads of free documentation of decent quality.

See wiki in my sig for more links.

---

### Post by CptPicard on 2007-08-24
If he needs to, he'll set up *functions*. Wow. Imagine that. Such a massive concession to abstraction in programming ;) -- he'd much rather code it all in one long block, if given the chance, I suppose.

I am not going to bet my head on this, but my gut feeling is that without function calls a language is not going to be recursive, therefore it's not even Turing-complete. Such minimalism is commendable... not. You don't want to go all the way to assembly because it's supposedly more "powerful" than other languages.

N00bs really need to get over this machismo-seeking "low-level is more powerful" fetish. It's not. You're just wasting your time while you could be actually educating yourselves first on general concepts that will help you get started quicker, and that will be more useful for you later on.

I really want you guys to frame this on your wall:

*All Turing-complete languages are equally computationally powerful, and outside of computational complexity theory, a language's "power" is a concept related to how suitable the language is for any given task and programmer. Low-level languages are not, in the computational sense, "more powerful" than high-level languages, and in the programmer productivity sense, high-level languages are often actually far more powerful than low-level languages.*

Can someone make a sticky of a statement along these lines... please?

---

### Post by aks44 on 2007-08-24
> **CptPicard said:**
> N00bs really need to get over this machismo-seeking "low-level is more powerful" fetish. It's not. You're just wasting your time while you could be actually educating yourselves first on general concepts that will help you get started quicker, and that will be more useful for you later on.

I really want you guys to frame this on your wall:

*All Turing-complete languages are equally computationally powerful, and outside of computational complexity theory, a language's "power" is a concept related to how suitable the language is for any given task and programmer. Low-level languages are not, in the computational sense, "more powerful" than high-level languages, and in the programmer productivity sense, high-level languages are often actually far more powerful than low-level languages.*

Very well put, although I'd even add (wouldn't it have been strange if I didn't? :p):

*Only a language that allows **both** high level and low level constructs can really be complete (not only in the Turing sense, though).*

IOW know *all* your tools, use the best when appropriate.



Why don't you make that sticky yourself? (to me you seem to master English way more than I do, I don't have the language level to express those ideas as clearly as you :oops:).

---

### Post by CptPicard on 2007-08-24
Your suggested addition is ok I suppose, although I don't think such a hypothetical ******* of a language would be much good for anything -- it would essentially be just a mishmash of grammars/paradigms/virtual machines from multiple different types of languages. The "know your tools" part is the really important one. Seeking the One Language to Rule Them All is just intellectual laziness from anyone who desires to be a software developer worth anything. Any language is good enough to start with, and over time, one will learn a dozen of them anyway.

The further you go from the usual lot of general-purpose programming languages, the more details you bury beneath the environment and the "style and spirit" of the language. Which is of course a good thing, as it empowers the programmer more to pursue one's goal efficiently... as long as you stay within Turing-completeness, I like to think that for any given problem, there is a given, fixed amount of "Turing-complete" effort to be made to solve the problem, and by the choice of tool, you move a part of that effort over to either the programmer or the language/tool/libraries/interpreter. By choosing the wrong tool, you'll just have to put in more programmer effort to fight the way your language wants to do things, but optimally, the Turing-complete amount of effort is the same. Then, if you give up the Turing-completeness, you get something like HTML, which is really easy on the programmer, but also no longer capable of solving "everything".

And as regards to stickiness, I'm not sure a regular Joe User can just stick a post at the head of the forum... and thanks for the language compliment, English isn't my mother tongue either though.. :)

---

### Post by DavidBell on 2007-08-24
I've used wxWidgets and C++ for cross platform - vc/Windows, gcc/Linux in both directions with no major problems. You just get it working in one platform with -WALL showing no warnings, then recompile as is in the other ... you will probably get some extras warnings if you swapped compiler, fix those and there is 99% chance it's good to go. DB

---

### Post by hod139 on 2007-08-24
How did a thread titled " How Do I Write Programs For Windows" turn to a discussion on Turing completeness?

Anyways, since we all seem to be nitpicking each other, I'll chime in.
[quote=CptPicard]
 ... I like to think that for any given problem, there is a given, fixed amount of "Turing-complete" effort to be made to solve the problem, and by the choice of tool, you move a part of that effort over to either the programmer or the language/tool/libraries/interpreter. By choosing the wrong tool, you'll just have to put in more programmer effort to fight the way your language wants to do things, but optimally, the Turing-complete amount of effort is the same. 
[/quote]
What does this even mean,  "Turing-complete" effort? That doesn't make any sense. Even in the theoretical computation world that doesn't make sense.  There are a whole host of Turing equivalent machines (2 stack push down automaton, multi-tape Turing machine, etc) each requiring different "effort". 

The point of modern programming languages are not to be able to solve a larger class of problems, but to be more powerful in other senses, e.g. memory usage, cpu usage, developer time, etc.

> 
Then, if you give up the Turing-completeness, you get something like HTML, which is really easy on the programmer, but also no longer capable of solving "everything".It isn't even known (though it is hypothesized) if all possible algorithmic calculations can be performed by a Turing machine.  So, dropping Turing-equivalence may actually allow you to solve more problems.  At least you put everything in quotes, as there are plenty of problems provable unsolvable.

---

### Post by aks44 on 2007-08-24
> **CptPicard said:**
> The "know your tools" part is the really important one. Seeking the One Language to Rule Them All is just intellectual laziness from anyone who desires to be a software developer worth anything.

As far as I'm concerned, I found C++ (yeah, still advocating it) to be a rather good **compromise**. Even though it is not that "One Language To Rule Them All", its low level constructs are useful enough for real life applications, and its high level constructs are... well... let's say useful enough too. Anyway you can still do very high level stuff with it, with enough effort.

But as we both agree I guess, one tool is not enough.

I've seen myself coding inline assembly, as well as interfacing with very high level stuff (which is not even a proper programming language by itself, check eg. "FormScape", a document output management system) in the same application.

So again, to anywone reading that, as CptPicard & I already said... use whatever fits best the problem at hand... and F***ing stop reinveiting the wheel...

Granted, this post is kinda useless but I felt I had to say it *clearly* anyway :p

---

### Post by CptPicard on 2007-08-24
> **hod139 said:**
> 
The point of modern programming languages are not to be able to solve a larger class of problems, but to be more powerful in other senses, e.g. memory usage, cpu usage, developer time, etc.

You're simply stating in different terms what I am saying, and I am quoting what I'm saying because I'm full aware I am not being theoretically rigorous. :)

Think of things in a complexity measure of your preference... there is, using some fundamental computational model, an amount of work to be done, and you can distribute the pain any way you want, but it's not going to be any less pain in aggregate; compare your own Turing-equivalent examples. That's the point a n00b needs to take home.

> It isn't even known (though it is hypothesized) if all possible algorithmic calculations can be performed by a Turing machine.

This heavily depends on your definition of an algorithmic calculation. If you define it as whatever is definable as a Turing machine, then we certainly know full well it can't perform all possible calculations.

> So, dropping Turing-equivalence may actually allow you to solve more problems.

Of course it does, I am not disputing this in any way. It's just that so far, Turing-equivalent machinery is all we've got, and dropping Turing-equivalence "downwards" is not going to help us in any way...

---

### Post by aks44 on 2007-08-24
> **CptPicard said:**
> Think of things in a complexity measure of your preference... there is, using some fundamental computational model, an amount of work to be done, and you can distribute the pain any way you want, but it's not going to be any less pain in aggregate. That's the point a n00b needs to take home.

Again, this totally makes sense. However as hod put it, maybe... ermm... we should stop hijacking this thread? ;)

---

### Post by CptPicard on 2007-08-24
> **aks44 said:**
> Again, this totally makes sense. However as hod put it, maybe... ermm... we should stop hijacking this thread? ;)

Not as long as I keep seeing these completely unfounded claims about some language being more powerful than some other language.... fight the Endless September, I say.

---

### Post by aks44 on 2007-08-24
> **CptPicard said:**
> fight the Endless September, I say.

As you want, Don Quichote... Good luck with those windmills ;)
:lolflag:

---

### Post by Wybiral on 2007-08-24
> **CptPicard said:**
> If he needs to, he'll set up *functions*. Wow. Imagine that. Such a massive concession to abstraction in programming ;) -- he'd much rather code it all in one long block, if given the chance, I suppose.

...

[i]All Turing-complete languages are equally computationally powerful, and outside of computational complexity theory, a language's "power" is a concept related to how suitable the language is for any given task and programmer.

...



I must have missed something... Where do functions and turing-completeness tie into portability?

Some things are simply NOT portable, the solution is to construct a compile-time condition that solves it for both situations (preprocessor directives).

Like I said, you generally don't want to... But like I also said... Sometimes it's unavoidable.

You can sit and cry if you can't find a portable library to do what you want, or you can use a method that's slightly less appreciated in the C++ community, it's your choice.

EDIT:

Maybe you brought this in because I mentioned Python, fair enough... But it isn't unfair to say that Python is more portable then C or C++. Python has already been compiled... There is no language bias here (in fact, I'm a C(++) programmer myself).

---

### Post by CptPicard on 2007-08-24
> **Wybiral said:**
> I must have missed something... Where do functions and turing-completeness tie into portability?


Frankly... I have to admit I just might have had to read the whole thread like I just did :oops:

Ok, you got me and I take back my patronizing, sorry. Anyway, the general argument I didn't even make about portability does hold -- you don't want to be doing low-level cross-platform coding when you do not have to.

---

### Post by pmasiar on 2007-08-24
I am with you, hod. "Practicality beats purity".

> **hod139 said:**
> What does this even mean,  "Turing-complete" effort? That doesn't make any sense. Even in the theoretical computation world that doesn't make sense.  

I don't know if in theory it makes sense (and CptPicard will tell us shortly :-) ) but I don't care. If whitespace or brainfuck are turing-complete, it does not tell much about **solving real problems in real life** - and that's all I care about.

If all (most, all major, modern, whatever) programming languages are turing-complete (whatever that means, I don't care either), knowledge of that factoid does not help us evaluate languages for usability to solve certain kind of problems. I never bothered to inquire if any language is turing-complete - I recall that turing machine is pretty stupid (but I forgot the details long time ago  - I don't care about them). 

> The point of modern programming languages are not to be able to solve a larger class of problems, but to be more powerful in other senses, e.g. memory usage, cpu usage, developer time, etc.

Exactly!

There are scientist who solve more esoteric problems and they care about Turing, NP-complete and crap, but **I** don't: I care about how to query and display data from my database in a way so user will be able to remember how to use it.  :-) And I very much care how "powerful" is language I use, and even if they are all turing-complete, they very much differ in power is suitability to solve different real-life problems.

> It isn't even known (though it is hypothesized) if all possible algorithmic calculations can be performed by a Turing machine. 

I guess some people can make pretty good living in some ivy tower solving it, and they [enjoy the process of doing it](http://www.c2.com/cgi/wiki?MentalMasturbation) but real programmers in trenched cannot care less about that.

As they say **In theory, there is **no difference** between theory and practice. In practice, there is.** :-)

So don't try on me NP, Turing, schmuring, completeness - I forgot what they are, and cannot care less about it anymore.

---

### Post by slavik on 2007-08-24
2 turing complete languages (or 2 systems showed to be turing complete) given an infinite amount of time and an infinite amount of memory have the ability to emulate each other.

if a C2D/8800GTX system and an ARM9 based cell phone both have an infinite amount of memory (RAM/HDD/etc.) then they will be able to emulate each other. Please note that there is nothing being said on "speed." Turing completeness takes into account computability, not complexity.

so, in theory (and in practice) you can write an AJAX type page in assembly/forth/machine code. ;)

---

### Post by samjh on 2007-08-25
> **Noodels said:**
> I speak amateur in many computer languages. (Uh, I think 4... But 4 is many!) Java not being one of them, and I always thought of Java as a less powerful language, probably due to all the applications I've seen for it I never though that good, being high level you can do more stuff but it requires more cpu (not exactly got a lot of that at the mo (1.4Ghz someone save me plz!)). I prefer lower level languages, and if I need to I'll set up functions.Java is certainly quite powerful, although it won't allow as much low-level access as C/C++.

But it is powerful enough to write remote control software for the Hubble Space Telescope, image processing software for the Mars Rover, develop software for portable military devices and C3I systems, stake its place as one of the most popular mobile device programming platforms, and run back-end data management infrastructure for large businesses. :)

You like going low-level, which is perfectly fine if that is your area of interest.  But if you're more into learning programming in general, high-level languages like Java, Python, Ruby, Lua, etc., will serve you just as well (if not better) than C/C++.


> Oh if only I knew how... Unfortunately me being me and amateurish after installing mingw32 I was completely at a loss as to how to actually use it....:(No need.

Install Wine.  Go to [www.winehq.org](www.winehq.org) and follow the links and instructions to install Wine for Ubuntu.

After installing Wine, hop into your command-line terminal, and type:```
winecfg
```to set up Wine.  By default, your "C: drive" will be ~/.wine/drive_c
That is like a fake C: that Wine uses for its Windows programs.

(By the way ~/ is your user's home directory.  So if your username is bartsimpson, then your ~/ is the same as /home/bartsimpson/ directory.)

Download Dev-C++ from here: [http://prdownloads.sourceforge.net/dev-cpp/devcpp-4.9.9.2_setup.exe](http://prdownloads.sourceforge.net/dev-cpp/devcpp-4.9.9.2_setup.exe)

Open up your terminal, go to the directory where you saved Dev-C++ and type:```
wine devcpp-4.9.9.2_setup.exe
```That will install Dev-C++ for you.

Still in your terminal, go to ~/.wine/drive_c/Dev-C++ (that will be the default installation directory for Dev-C++), and run the .exe file for Dev-C++.  I can't remember the exact name of the Dev-C++ executable, because I don't have it installed at the moment, but your command should look something like:```
wine devcpp.exe
```

Follow the first-time usage instructions.  If you cannot get past the splash screen, press the [ENTER] key.  It worked for me. :)

---

### Post by Noodels on 2007-08-25
Okay thanks everyone for your constructive, if not rather harsh, input. I guess the knack is to choose the programming language best for the job (I figured that out after the first cruel posts :( ) . I'm writing in C because it's the language I am learning at the moment, I am learning a little python too and I really would like to learn more, I'm not trying to do any particular job with it, although when I do then at least I'll know the language. Thanks for your help everyone, although it did go a *little* off topic for a while.

---

### Post by Paul820 on 2007-08-25
> Thanks for your help everyone, although it did go a *little* off topic for a while.

It always does :(

---

### Post by hod139 on 2007-08-25
> **CptPicard said:**
> 
Think of things in a complexity measure of your preference... there is, using some fundamental computational model, an amount of work to be done, and you can distribute the pain any way you want, but it's not going to be any less pain in aggregate; compare your own Turing-equivalent examples. That's the point a n00b needs to take home.

Complexity measure (whatever your definition of that may be, there is an entire field of information theory devoted to it) is not a "practical" measure nor is it a simple concept that "newbs" should be learning.  Computability theory, and complexity theory are upper level courses with very abstract ideas, not for light reading or "newbs". For those that are interested, Mike Sipser's book is one of the better introductory texts.

> 
This heavily depends on your definition of an algorithmic calculation. If you define it as whatever is definable as a Turing machine, then we certainly know full well it can't perform all possible calculations.
Mathematicians were discussing complexity theory well before Turing came along.  Calling the class of solvable problems those that a Turing machine can solve is cyclic.  For details of what I was talking about see the [Church-Turing thesis]("http://plato.stanford.edu/entries/church-turing/").

---

### Post by pmasiar on 2007-08-25
> **CptPicard said:**
> Not as long as I keep seeing these completely unfounded claims about some language being more powerful than some other language.... fight the Endless September, I say.

So you claim that if two languages are both Turing complete, it does not matter which one is used to solve some concrete task? Using either one, we will get working program for same budget? Equally easy to maintain and enhance?

Or your information theory of complexity does not bother with such lowly and boring matters like money, budget, real people solving real problems?

Just interesting to know your opinion about real world problems, where I live.

---

### Post by kknd on 2007-08-25
Cross-compile / ask someone to compile your program, or program it under a interpreted language (Java wins on this sector, but there's also Python, Ruby, etc).

---

### Post by Noodels on 2007-08-28
> **samjh said:**
> Java is certainly quite powerful, although it won't allow as much low-level access as C/C++.

But it is powerful enough to write remote control software for the Hubble Space Telescope, image processing software for the Mars Rover, develop software for portable military devices and C3I systems, stake its place as one of the most popular mobile device programming platforms, and run back-end data management infrastructure for large businesses. :)

You like going low-level, which is perfectly fine if that is your area of interest.  But if you're more into learning programming in general, high-level languages like Java, Python, Ruby, Lua, etc., will serve you just as well (if not better) than C/C++.


No need.

Install Wine.  Go to [www.winehq.org](www.winehq.org) and follow the links and instructions to install Wine for Ubuntu.

After installing Wine, hop into your command-line terminal, and type:```
winecfg
```to set up Wine.  By default, your "C: drive" will be ~/.wine/drive_c
That is like a fake C: that Wine uses for its Windows programs.

(By the way ~/ is your user's home directory.  So if your username is bartsimpson, then your ~/ is the same as /home/bartsimpson/ directory.)

Download Dev-C++ from here: [http://prdownloads.sourceforge.net/dev-cpp/devcpp-4.9.9.2_setup.exe](http://prdownloads.sourceforge.net/dev-cpp/devcpp-4.9.9.2_setup.exe)

Open up your terminal, go to the directory where you saved Dev-C++ and type:```
wine devcpp-4.9.9.2_setup.exe
```That will install Dev-C++ for you.

Still in your terminal, go to ~/.wine/drive_c/Dev-C++ (that will be the default installation directory for Dev-C++), and run the .exe file for Dev-C++.  I can't remember the exact name of the Dev-C++ executable, because I don't have it installed at the moment, but your command should look something like:```
wine devcpp.exe
```

Follow the first-time usage instructions.  If you cannot get past the splash screen, press the [ENTER] key.  It worked for me. :)

When I try to install (I am using wine) it says "Error writing temporary file. Make sure your temp folder is valid." and I can't figure out what that means, any ideas?

---

### Post by Noodels on 2007-08-28
> **kknd said:**
> Cross-compile / ask someone to compile your program, or program it under a interpreted language (Java wins on this sector, but there's also Python, Ruby, etc).

Don't know how to cross compile, only other people who aren't computer incompetent that I know use linux and have the same problem and I don't actually know how to write in any other language as well as I do in C (even that's not very good).

---

### Post by samjh on 2007-08-28
> **Noodels said:**
> When I try to install (I am using wine) it says "Error writing temporary file. Make sure your temp folder is valid." and I can't figure out what that means, any ideas?

In what part of the installation process do you get that error?

---

### Post by CptPicard on 2007-08-28
I am not really sure what your exact complaint with what I'm after here is -- that is,  but let's try to counter you anyway, whatever it is.. :)

> **hod139 said:**
> Complexity measure (whatever your definition of that may be, there is an entire field of information theory devoted to it)

Kolmogorov complexity is particulary interesting from a CS data/information/computation perspective, but let's not go there, and unfortunately I graduated before I had the chance to take the class :)

> is not a "practical" measure nor is it a simple concept that "newbs" should be learning. Computability theory, and complexity theory are upper level courses with very abstract ideas, not for light reading or "newbs".

I disagree with this. I am not making them read Sipser as the first thing -- what I am saying that a noob could take home the basic idea that for example, when they are flaming about whether "my language is bigger than yours", it's a fundamentally moot point. They may be saving themselves effort using some particular language for some particular problem, of course.

And by the way, if they are too difficult for n00bs, why the problem with my "quoting"? ;)

> Mathematicians were discussing complexity theory well before Turing came along.  Calling the class of solvable problems those that a Turing machine can solve is cyclic.  For details of what I was talking about see the [Church-Turing thesis]("http://plato.stanford.edu/entries/church-turing/").


Yes, and I did not suggest that nothing existed before Turing. 

But as I said, if we choose the TM as your model, as we are prone to do as we are computer science people, we know it's limited, the roots of which are in the Entscheidungsproblem and the incompleteness theorem, as is the case for all sufficiently strong syntactic manipulation systems. No need to patronize me with links to the C-T thesis, as I personally do not feel as if I have actually said anything particularly nonsensical  -- essentially just that all programming languages are just computationally speaking different kinds of syntactic sugar, and you just shift effort around. This goes for TM complexity as well; you can take variants of the same idea, RAM machines or whatever, and you're just putting more effort into your machinery in order to gain some other kind of subjective power elsewhere.


> **pmasiar said:**
> So you claim that if two languages are both Turing complete, it does not matter which one is used to solve some concrete task? Using either one, we will get working program for same budget? Equally easy to maintain and enhance?

To put this to rest, no, I do not claim this. :)

Actually, I tend to favour higher-level languages like you do for this very reason, and my argument is simply a way to point out to the noobs from a more theoretical perspective, that their "w00t assembler is the most powerful language!!1" ideas are ... pointless.

---

### Post by pmasiar on 2007-08-28
> **Noodels said:**
> When I try to install (I am using wine) it says "Error writing temporary file. Make sure your temp folder is valid." and I can't figure out what that means, any ideas?

Why you quote whole page, including Mars Rover etc, if you replay on last paragraph? Is it that hard to delete irrelevant lines?

It is not against you personally, it is about netiquette  - making net better for everyone. See my sig - join the battle ! :-)

---

### Post by pmasiar on 2007-08-28
> **pmasiar]
So you claim that if two languages are both Turing complete, it does not matter which one is used to solve some concrete task? Using either one, we will get working program for same budget? Equally easy to maintain and enhance?[/quote]

[QUOTE=CptPicard said:**
> 
To put this to rest, no, I do not claim this. :)

Actually, I tend to favour higher-level languages like you do for this very reason, and my argument is simply a way to point out to the noobs from a more theoretical perspective, that their "w00t assembler is the most powerful language!!1" ideas are ... pointless.

You are not entirely consistent with your arguments. You dismissed in other thread Forth, because it has low-level power, even if it is very high-level language. Are you familiar with Forth (and should i dig out the link)? Or you prefer theoretical problems in computability over solving real-life problems? I am surprised how many people can make living on that... :-)

---

### Post by CptPicard on 2007-08-28
> **pmasiar said:**
> You are not entirely consistent with your arguments. You dismissed in other thread Forth, because it has low-level power, even if it is very high-level language. Are you familiar with Forth (and should i dig out the link)? Or you prefer theoretical problems in computability over solving real-life problems? I am surprised how many people can make living on that... :-)

Nope, I am not being too inconsistent here, I think :) Yes, I was unfamiliar with Forth and I did educate myself about it after you pointed it out. An interesting language indeed.

It is also true that I prefer theoretical problems, and when I was a student I always lost interest in all of my hobby projects after I figured out how the tough bits were achieved. This is why I am honestly not too good a real-world programmer ... but I do enjoy the algorithmic aspects of it. And this is also why I like keeping things high-level in general, be it in pure theory or in programming languages. I never found too much pleasure in tuning the last bit of performance out of something by writing it in C, if I knew that it's the choice of algorithm that dominates execution time.

My interest in going all the way to Turing machines with some people shouldn't be construed as "low-level" interest.. I consider it to be an argument for high-level thinking, and therefore I am not being inconsistent in my views, I think... I use Turing-equivalence as a way to seek to prove that esp. the noob idea that they need to go for low-level languages for "power" is misguided, as they aren't, in the theoretical sense, getting any more computational strength and are just making themselves go through more pain coding. 

There may be Forth, but I'd think you of all people will be the first to admit that Python is better than machine code... (for high-level tasks that is)

---

### Post by pmasiar on 2007-08-28
> **CptPicard said:**
> I never found too much pleasure in tuning the last bit of performance out of something by writing it in C, if I knew that it's the choice of algorithm that dominates execution time.

That's very good habit - many people would be beter off doing it :-) First, solve right problem, then wonder solving it right ;-)

> the noob idea that they need to go for low-level languages for "power" is misguided, as they aren't, in the theoretical sense, getting any more computational strength and are just making themselves go through more pain coding. 

Yup. I see where are you coming from. Agree.

>you of all people will be the first to admit that Python is better than machine code... (for high-level tasks that is)

Yes, obviously.

But even high-level languages are not equivalent, there are still differences in programmer's productivity. I would argue that Python is better than most high-level programming languages on most high-level tasks... :-) I found good discussion about it at c2 - the original wiki: [http://c2.com/cgi/wiki?BlubParadox](http://c2.com/cgi/wiki?BlubParadox) . Lots of good articles there...

---

### Post by j_g on 2007-08-28
Um, did anyone (besides the first respondent) think to tell this poor guy that a Linux executable is not a Windows executable? You can't just take a Linux executable, rename it so that it ends with a .EXE extension, and then presume that it will run on Windows. The first respondent told you as much. Everyone else went off on an irrelevant tangent that not only didn't help you, but undoubtably confused you.

Here's the rest of what you need to know:

Windows uses something called a PE file format for its executables. Linux uses ELF. They are entirely different. They have different headers, sub-sections, etc. An executable is not just some (Intel 80x86) opcodes. It also contains "organizational data" and other data to assist the operating system in loading/running the opcodes.

Your Linux compiler/linker will generate an ELF binary. If your C code doesn't use any Linux specific API calls, and your compiler/linker supports alternately generating a PE format, then you can create a Windows executable. Usually, you supply some "flag" to the compiler/linker to tell it what binary format to generate. Check the flags with GCC, and tell it to generate PE format (assuming it supports that) if you want a Windows executable. (P.S. Don't attempt to run the PE binary under Linux. Well, you could probably run it under Wine, but not as a Linux executable).

P.P.S. I've said it before, and I'll say it again. This is a really, really bad place to get advice about Windows programming, and this thread is just further demonstration why.

---

### Post by Vox754 on 2007-08-28
> **j_g said:**
> Um, did anyone (besides the first respondent) think to tell this poor guy that a Linux executable is not a Windows executable? You can't just take a Linux executable, rename it so that it ends with a .EXE extension, and then presume that it will run on Windows. The first respondent told you as much. Everyone else went off on an irrelevant tangent that not only didn't help you, but undoubtably confused you.


I can't believe I'm saying this but yes, j_g is right.

[QUOTE=Vox754]
..., j_g is right.
[/QUOTE]

Why, why, why, why, why, why, why, why, why, why, why, why?

Why did we all hijack this thread?

CptPicard, [you started it all](http://ubuntuforums.org/showpost.php?p=3246936&postcount=24); hod139, [you disappoint me](http://ubuntuforums.org/showpost.php?p=3247302&postcount=28).

Please people, keep it simple.

This thread is locked.

Wait, I forgot this is not a dream, I don't have superpowers.

---

### Post by j_g on 2007-08-29
> He just wants to know how to compile Linux C programs that would run in Windows. This implies far less than the whole Windows programming.

I didn't say that his question implied "the whole Windows programming" (whatever that means). I simply noted that he took a Linux ELF executable, renamed it with an .EXE extension, and expected it to become a Windows PE executable. I told him why that doesn't work. I also noted that, aside from the very first respondent (who noted that you can't do the former, but not specifically why you can't do it), none of the _pages_ of further responses provided the OP with an appropriate, suitably specific, and informative answer to solve his Windows programming dilemma. It has been my personal experience that this is not atypical of this forum, and I very much stand by my conclusion regarding the quality of Windows programming advice here. I think that people who can't answer a question with substantive information should be discouraged from attempting to do otherwise. And frankly, there are a few people whose responses appear all over the forum, including in threads where frankly, they lack the experience and authority to be offering their "2 cents". It tends to make the entire forum suspect as a place to get legitimate, quality information.

---

### Post by Vox754 on 2007-08-29
> **j_g said:**
> ... I simply noted that he took a Linux ELF executable, renamed it with an .EXE extension, and expected it to become a Windows PE executable. I told him why that doesn't work.

Yes. Exactly. I agree. No need to repeat this part.

> **j_g said:**
> 
... It tends to make the entire forum suspect as a place to get legitimate, quality information.
No, no, no. You are doing it again. Even if you are just giving your thoughts this kind of comment may be easily interpreted as flame bait. We need to be extra careful when expressing our feelings towards other members or this subforum as a whole.
Remember, this is a community forum, anyone can join. This is definitely not intended as a place to gather all gurus.

I'll tell you what, j_g, you edit out the last [P.P.S. comment](http://ubuntuforums.org/showpost.php?p=3270840&postcount=52) and the last post #54, and I'll also remove traces of everything said after it so we can end this mini discussion. I'll just leave it as ["j_g is right"](http://ubuntuforums.org/showpost.php?p=3271786&postcount=53).

---

### Post by CptPicard on 2007-08-29
The OP's question got answered essentially in the second post of the thread. "You can't compile on Linux and expect it to run on Windows" :)

---

### Post by j_g on 2007-08-29
> **Vox754 said:**
> this is a community forum, anyone can join.

That's fine. But obviously, not everyone should be answering every question posted on this forum. When I don't have a reasonably substantive answer to a particular question, or just plain don't know anything about the topic, I don't reply.

But there are certain people whose names appear in every other thread, and when it comes to certain topics, for example, anything to do with Windows programming, their answers/information are just plain bad. They should be discouraged from doing that. It really makes the entire forum seem like a very dubious source of useful information. And I _do_ stand by my assessment of this forum's usefulness in regard to Windows programming, and will continue to hold that assessment as long as the quality of the information remains as it has in this, and other threads, I've read on this forum.

---

### Post by pmasiar on 2007-08-29
j_g is doing it again

I was happy to see you back, because of your expertise in Windows, which is occasionally needed.

But I really don't like your tone. I know two good members, giving interesting insight to many topic (one of them old Lisp hand - and yes it **is** interesting to see Lisper POV) who left the forum to nevr come back, disgusted by your tone and fight with admins.

> **j_g said:**
> That's fine. But obviously, not everyone should be answering every question posted on this forum. When I don't have a reasonably substantive answer to a particular question, or just plain don't know anything about the topic, I don't reply.

So if you like to help, please do. If you want to set rules about how run this forum, better start your own.

Answers go tangent from OP question, it is fact of life.

> But there are certain people whose names appear in every other thread, and when it comes to certain topics, for example, anything to do with Windows programming, their answers/information are just plain bad. They should be discouraged from doing that. It really makes the entire forum seem like a very dubious source of useful information. 

It is good enough for most of us. Do you like it here? What is your goal here? What do you want to accomplish?

> And I _do_ stand by my assessment of this forum's usefulness in regard to Windows programming, and will continue to hold that assessment as long as the quality of the information remains as it has in this, and other threads, I've read on this forum.

As many of us explained you many times, this forum is **not** focused on Windows programming - It is focused on programming in general, and ubuntu in particular. So even for windows-based question, I like and appreciate linux-flavored answer - I am here to learn more about Linux, among others. I do use windows, but I am working slowly to get rid of it.

Don't try to poison it here. Help if you see someone needing Windows help, and follow your own advice and ignore other posts.

---

### Post by Wybiral on 2007-08-29
> **j_g said:**
> That's fine. But obviously, not everyone should be answering every question posted on this forum.

Hey j_g, welcome back.

You are right really... People interested in Windows programming are probably not in the right place ( and people interested in praising Windows programming and hating Linux development and portability probably aren't going to be liked much around here either :) ).

But if someone asks a question on a _public forum_ they have to realize that this isn't a help desk... It's a place to publicly debate and discuss.

Personally, I thought the first page or two was fine in terms of people explaining what might be needed (cross compiler / mingw32 / preprocessor directives / portable languages).

But I will stress this again... It's a public forum, not a help desk. Sure, it can be a great place to ask questions to fellow programmers, but you have to understand that debate and conversation are perfectly natural in the forum world. If you're looking for plain information and no debate / conversation... Google it.

---

### Post by LaRoza on 2007-08-29
> **j_g said:**
> 
P.P.S. I've said it before, and I'll say it again. This is a really, really bad place to get advice about Windows programming, and this thread is just further demonstration why.

What forum / other would you recommend? 

You're correct in saying this isn't the best place, which is an Ubuntu Linux forum, to get advice on Windows specific programming, but it was never intended to be.

---

### Post by hod139 on 2007-08-29
> **Vox754 said:**
> I can't believe I'm saying this but yes, j_g is right.



Why, why, why, why, why, why, why, why, why, why, why, why?

** Why did you all hijack this thread**?

CptPicard, [you started it all]("http://ubuntuforums.org/showpost.php?p=3246936&postcount=24"); hod139, [you disappoint me]("http://ubuntuforums.org/showpost.php?p=3247302&postcount=28").

Please people, keep it simple.

This thread is locked.

Wait, I forgot this is not a dream, I don't have superpowers.
(emphasis added)

And what are you doing to this thread with this post?  I don't see an answer to the OP's question anywhere (or any question for that matter), only ranting. Reminds me of an old saying, "The pot calling the kettle black."

Threads have been going off topic for years around here, why the sudden hate?  I admittedly got sucked into CptPicard's post, but so what.  Many of us have been sucked into an off topic debate before.  In hindsight, I should have posted an answer to the OP's question, but no changing that now.

---

### Post by abadfish on 2007-08-29
> **LaRoza said:**
> What forum / other would you recommend? 

You're correct in saying this isn't the best place, which is an Ubuntu Linux forum, to get advice on Windows specific programming, but it was never intended to be.
here is a decent place to start:

[http://forums.microsoft.com/msdn/default.aspx?siteid=1](http://forums.microsoft.com/msdn/default.aspx?siteid=1)

I'm sure you could find other forums more specific to whatever flavor of windows programming you are interested in (e.g. MFC, VB, .Net, ATL, COM, etc).

---

### Post by LaRoza on 2007-08-29
> **abadfish said:**
> 
I'm sure you could find other forums more specific to whatever flavor of windows programming you are interested in (e.g. MFC, VB, .Net, ATL, COM, etc).

Actually, I don't want anything to with programming that doesn't work on more than one OS, it is just that some must dirt was flung at this forum, and no remedy or alternative was given. 

Thanks for the link, maybe others will find it useful.

---

### Post by qamelian on 2007-08-29
> **CptPicard said:**
> The OP's question got answered essentially in the second post of the thread. "You can't compile on Linux and expect it to run on Windows" :)

Sure you can. That is the purpose of a cross compiler: to compile code on a platform other than the target on which the code will be run. Even gcc supports cross compilation provided the necessary parts of the tool chain are available on both the development and target platforms.

---

### Post by Wybiral on 2007-08-29
> **qamelian said:**
> Sure you can. That is the purpose of a cross compiler: to compile code on a platform other than the target on which the code will be run. Even gcc supports cross compilation provided the necessary parts of the tool chain are available on both the development and target platforms.

Exactly. As was mentioned on the first page, a cross compiler and portable libraries are all you need.

If you can't make portions of the code portable for some reason, use preprocessor directives to conditionally compile it for each platform.

---

### Post by CptPicard on 2007-08-29
> **qamelian said:**
> Sure you can. That is the purpose of a cross compiler: ...

Yes, but not the way the OP was expecting it to work (tagging .exe at the end), so the first really simple answer is that the binaries you get out of Linux gcc aren't compatible in the sense you could "expect" them to just work. The cross-compiling answer was rapidly given too in the following posts... so I would think the OP got sufficient information of the thread, and the hijacking happened later on :p

---

### Post by j_g on 2007-08-29
Look, the guy took a Linux executable, renamed it with an .EXE extension, and then expected it to run as a Windows executable. Ok, he's obviously learning about programming, and new programmers _are_ going to make mistakes that more seasoned programmers know not to make, and _why_.

And that's why a new programmer asks a question in a programming forum -- because he figures a seasoned programmer will explain to him why he's making a mistake, and how he should correct it.

So first we have someone saying essentially "What you did doesn't work". Yes, that's true, but that doesn't tell him why, nor offer him a solution.

Next we have a couple people mention mingw32. What's the problem with that? Without telling him anything about the issue of ELF versus PE file format for executables, you haven't told him anything about _why_ what he did doesn't work. It's not like you have to write a dissertation about it. I wrapped it up in 2 short paragraphs. The only thing I didn't do is mention a particular cross-compiler such as mingw32, because I don't use those Linux tools and therefore do not have those specific references. So I just gave him generic advice about looking for a "compiler/linker flag" that causes the generated executable to be PE format. Done.

And think about that. The guy thought that renaming a Linux exe's filename makes it run under Windows. Do you actually think he knows what a cross-compiler is??? Without explaining to him what a cross-compiler does, you haven't given him any real information even if you say "use mingw32". He still doesn't know why what he did doesn't work. And the odds of him getting the cross-compiler working are much lower because he doesn't know what it's supposed to be doing. (I'm not sure what he did, but it almost sounds like he tried to install and run the thing under Wine. If it's a Linux cross-compiler, why would he be doing that??? Probably because the answers confused the hell out of him, rather than explain to him why what he did doesn't work.)

Worse, the discussion of cross-compiling is framed in discussions of "portable libraries" (particularly graphics libraries) and conditional defines. That has nothing to do with his immediate problem. Just address the issue at hand. After he gets _that_ solution, _if_ he has additional problems, he'll be back (because his first question was answered succinctly and successfully -- he'll expect subsequent results to be as good). In this particular case, it appears that he's writing console programs that just use the C library, so all the talk about portable libs and conditional defines undoubtably just confused him and made him mistakenly think that this somehow contributed to him getting an error message when he renamed his Linux exe under Windows and double-clicked on it. Ok, so even if he had written some XWindows C app, he'll just get a different error/problem, and he'll be back to ask a question about that, and _then_ you can answer that (without hopefully confusing him with irrelevant additional issues).

<snip>

---

### Post by Paul820 on 2007-08-29
[[img]http://www.emoticonzone.com/msn-emotions/animated/clap.gif[/img]]("[URL=http://www.emoticonzone.com)"][[img]http://www.emoticonzone.com/msn-emotions/animated/clap.gif[/img]](http://www.emoticonzone.com)[/URL]

---

### Post by Wybiral on 2007-08-29
> **j_g said:**
> Look, the guy took a Linux executable, renamed it with an .EXE extension, and then expected it to run as a Windows executable. Ok, he's obviously learning about programming, and new programmers _are_ going to make mistakes that more seasoned programmers know not to make, and _why_.

And that's why a new programmer asks a question in a programming forum -- because he figures a seasoned programmer will explain to him why he's making a mistake, and how he should correct it.

So first we have someone saying essentially "What you did doesn't work". Yes, that's true, but that doesn't tell him why, nor offer him a solution.

Next we have a couple people mention mingw32. What's the problem with that? Without telling him anything about the issue of ELF versus PE file format for executables, you haven't told him anything about _why_ what he did doesn't work. It's not like you have to write a dissertation about it. I wrapped it up in 2 short paragraphs. The only thing I didn't do is mention a particular cross-compiler such as mingw32, because I don't use those Linux tools and therefore do not have those specific references. So I just gave him generic advice about looking for a "compiler/linker flag" that causes the generated executable to be PE format. Done.

And think about that. The guy thought that renaming a Linux exe's filename makes it run under Windows. Do you actually think he knows what a cross-compiler is??? Without explaining to him what a cross-compiler does, you haven't given him any real information even if you say "use mingw32". He still doesn't know why what he did doesn't work. And the odds of him getting the cross-compiler working are much lower because he doesn't know what it's supposed to be doing. (I'm not sure what he did, but it almost sounds like he tried to install and run the thing under Wine. If it's a Linux cross-compiler, why would he be doing that??? Probably because the answers confused the hell out of him, rather than explain to him why what he did doesn't work.)

Worse, the discussion of cross-compiling is framed in discussions of "portable libraries" (particularly graphics libraries) and conditional defines. That has nothing to do with his immediate problem. Just address the issue at hand.

Sorry, I generally just don't assume the OP is a complete moron.

You are trying to force your philosophy on others... My way of helping people is to tell them what they need to look for, not hold their hand and walk them through every step. If someone mentions "cross compiler" I expect the OP to Google "Win32 cross compiler for Linux" and come back with questions if they get stuck.

I also think mentioning portable libraries and preprocessor directives _is_ relative to the question at hand because the OP will likely have to change some code to get everything to work on all the platforms they wish to support.

---

### Post by pmasiar on 2007-08-29
Maybe we need to wait OP to post **his** opinion how helpful was the help, and how much this forum sucks...

---

### Post by Noodels on 2007-08-30
> **pmasiar said:**
> Maybe we need to wait OP to post **his** opinion how helpful was the help, and how much this forum sucks...

And that I shall!

Firstly j_g's post was vastly correct, although I think I was somewhat under estimated, I figured pretty much that a cross compiler compiles programs for windows and linux, and I didn't expect renaming an executable with a .exe extension would work, but I was out of options, imagine how stupid I'd look if I posted on here and that was the answer.

As for Wybiral, I wasn't expecting to use google, I had mistakenly assumed the software was on synaptic, therefore I looked there. I actually found min32gw there and installed it, it just doesn't seem to have any effect whatsoever, whereas if I had looked on google there probably would be instructions.

My only problem with the answers in this thread were that most of the solutions were that people were telling me to use a different programming language even though I had made what I wanted in my first two posts fairly clear : A compiler FOR windows IN linux. Someone did say something about a windows compiler that ran under wine, but when I tried to get that to work an error came up and I asked for help, so far no reply, you never know, there might be a reply *somewhere* between page 3 and 7.

Conclusion : None, I still haven't found a way to compile programs for windows in linux that actually works. Although it's nice to see people so interested.

---

### Post by Wybiral on 2007-08-30
> **Noodels said:**
> I figured pretty much that a cross compiler compiles programs for windows and linux

A cross compiler compiles things FOR another system FROM your system. It can't compile for Linux and Windows, but it can allow you to compile Windows EXE's from Linux.

Basically, I only brought up Google because knowing that a cross compiler is what you need, you should really do some research looking into the most popular ones and how to use them. Then come back and ask specific questions when you hit a bump. What problems did you encounter with MingW32?

Personally I don't use a cross compiler (I don't have Windows and I expect a Windows user somewhere to compile it themselves if they want to use it, but all of my work is open source), but I do know what they are and why you need them.

Also, relevant to libraries... Your Linux libraries will not work when compiling for Windows. You'll need to find a Windows version for them (and hope that they're portable).

---

### Post by LaRoza on 2007-08-30
> **Noodels said:**
> 

 Someone did say something about a windows compiler that ran under wine, but when I tried to get that to work an error came up and I asked for help, so far no reply, you never know, there might be a reply *somewhere* between page 3 and 7.



Get the portable version, install it under windows (actually, unzip it) to a flash drive. Run that in Wine.

[http://www.softpedia.com/get/PORTABLE-SOFTWARE/Programming/Windows-Portable-Applications-Dev-C-Portable.shtml](http://www.softpedia.com/get/PORTABLE-SOFTWARE/Programming/Windows-Portable-Applications-Dev-C-Portable.shtml)


Sometimes threads here get used for discussion if it is though the original problem was solved. If a question is overlooked, you could redirect the discussion.

---

### Post by pmasiar on 2007-08-30
**Executive summary:**
- you can use cross-compiler to compile windows executables on Linux, but it is order of magnitude more complicated than plain compiling (ie: it is not obvious and **hard** to make it work)
- this forum **does not** suck (even if people like to wander off-topic), despite some known whiners suggesting otherwise
- many people suggested their own favorite more cross-platform solution, with inevitable comparing: then, everybody has an opinion **and** rebuke
- until [ESP](http://en.wikipedia.org/wiki/Extra-sensory_perception) will become commonplace, best what we can do is:  **before** start answering, first responder should ask OP more questions, find out unstated assumptions. Otherwise different people will answer using different assumptions, inevitable getting different results.
Or maybe we should require OP to read [How To Ask Questions The Smart Way](http://catb.org/~esr/faqs/smart-questions.html) before starting thread? Yeah, right, we all know **neither** one is gonna ever happen, so if you cannot stand off-topic answers, you are better not reading forums. :-)

---

### Post by David Marrs on 2007-08-30
> **aks44 said:**
> You don't want to do that. What you really want is to use a cross-platform library that exposes a single API whatever platform you run on (as I said previously, Qt is one of those, but it's C++ ; dunno about any C one).

GLib, GObject and Gtk+ (all part of the Gnome framework) are also x-platform compatible.

---

### Post by Noodels on 2007-08-31
> **Wybiral said:**
> What problems did you encounter with MingW32?

That's very simple. I installed off synaptic, then didn't know what to do.

---

### Post by samjh on 2007-08-31
> **Noodels said:**
> That's very simple. I installed off synaptic, then didn't know what to do.
For normal C/C++ programs without any non-standard libraries, you can use them like normal gcc and g++ compilers.  The key differences are the commands.

Instead of using gcc, it is:
i586-mingw32msvc-gcc

Instead of using g++, it is:
i586-mingw32msvc-g++

All command-line switches are exactly the same as gcc or g++.  The only thing I'd recommend is that the output file have .exe as the extension, so you can easily see that it is a Win32 executable.

For example, to compile hello.cpp to hello.exe, you can use this:
```
i586-mingw32msvc-g++ hello.cpp -o hello.exe
```

But if your program needs non-standard libraries, you will need to obtain the Win32 versions of the libraries, and hand-link them when compiling.

If you're a new programmer, you shouldn't need to worry about non-standard libraries yet.

---

