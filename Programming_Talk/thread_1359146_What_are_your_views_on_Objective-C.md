---
title: "What are your views on Objective-C?"
date: 2009-12-19
forum: Programming Talk
---

### Post by Igniteflow on 2009-12-19
Hi,
I've been using Ubuntu and programming in Java and various web languages for a couple of years now, and wanted to ask some advice.  I'm considering getting a Mac so that I can learn Objective-C with the goal of programming iPhone apps.  Does anyone have any experience with Objective-C?  I've heard it can be tricky to get into.  It'd be good to hear your opinions on going this route before I take the plunge.  (Of course, I'll always have my Linux box though)

---

### Post by nvteighen on 2009-12-19
I've got some ObjC experience and can tell it isn't tricky at all. It is a quite clean language, non-bloated... just a "C with classes". That's a good thing, as many use C++ (and get frustrated) just because they want to add OOP to C... and get an overcomplicated language featuring a lot of other things you can't avoid. Objective-C makes it rather simple.

The issue with Objective-C is that it lacks a Standard Library. It uses the C Standard Library, but writing C-like code in Objective-C can get you into some troubles as C built-in types aren't classes. Then, you get forced into using the OpenStep libraries: Apple NeXTStep + Cocoa (GUI toolkit) and GNUStep in GNU/Linux. I don't think there's any support for Windows.

This is that grave that people tend to unify "Objective-C" and "OpenStep" into one single concept in their minds.

Also, both the Objective-C and the OpenStep spec are in the hands of Apple and therefore, the GNU Objective-C Runtime and GNUStep are outdated. For instance, Objective-C 2.0 is not supported by the GNU ObjC Runtime yet... so no automatic garbage collection in GNU/Linux, nor propierties, etc.

A very good Objective-C tutorial can be found in the GNUStep manual 

btw, I happen to have written two How-To's. The first is about using gcc to compile Objective-C (and a little introduction) and the second, about GNUStep, what it is and how to use it.

[http://ubuntuforums.org/showthread.php?t=1064045](http://ubuntuforums.org/showthread.php?t=1064045)
[http://ubuntuforums.org/showthread.php?t=1338278](http://ubuntuforums.org/showthread.php?t=1338278)

@end (you'll soon know what that means :))

---

### Post by pelle.k on 2009-12-19
It's rather neat.
I wouldn't consider it on any other platform than OSX or the iPhone though. There's hardly any good language bindings for Obj-C in linux/windows.
Cocoa is a very nice framework to work with, but it's Apple specific. I sometimes wish GTK/QT had as many cool GUI widgets to work with.
I find "messaging" in ObjC to be rather unintuitive.
I like the built in support for garbage collecting.

Personally i prefer MacRuby, but you can't use that for developing iPhone apps though. Not yet, anyway.

On a side note, apparently you can use mono to develop for the iphone...

---

### Post by Igniteflow on 2009-12-19
Thanks nvteighen and pelle.k, it's good to get some input.  I'll definitely check out those tutorials once I get a Mac.

---

### Post by grayrainbow on 2009-12-19
> **Igniteflow said:**
> Hi,
I've been using Ubuntu and programming in Java and various web languages for a couple of years now, and wanted to ask some advice.  I'm considering getting a Mac so that I can learn Objective-C with the goal of programming iPhone apps.  Does anyone have any experience with Objective-C?  I've heard it can be tricky to get into.  It'd be good to hear your opinions on going this route before I take the plunge.  (Of course, I'll always have my Linux box though)
You could in general do obj-C with gcc compiler on Linux, but yea it could be tricky couse it's really ridiculous as a language(not as a lib on Mac). The fact that java/C# inheired from C++ and nobody inheired from obj-C speak for itself. And yea(again) obj-C is only for Apple stuff(in reality) and if at some point you decide to go for some better platform(android, maemo) your obj-C experiece will basicly mean nothing. But if you really want it - go for it, and don't use functions with many arguments :)
Good luck!

---

### Post by nvteighen on 2009-12-20
> **grayrainbow said:**
> You could in general do obj-C with gcc compiler on Linux, but yea it could be tricky couse it's really ridiculous as a language(not as a lib on Mac). The fact that java/C# inheired from C++ and nobody inheired from obj-C speak for itself. And yea(again) obj-C is only for Apple stuff(in reality) and if at some point you decide to go for some better platform(android, maemo) your obj-C experiece will basicly mean nothing. But if you really want it - go for it, and don't use functions with many arguments :)
Good luck!

It's not the language, it's the lack of libraries and the zero-to-none interest from anyone except Apple. Which is a pity, because ObjC is really the best you can get when you just want "C with Classes" without all the C++-hype.

Meanwhile, you could use C libraries, but that will be utterly hard to integrate nicely with "Objective-C Objective-C" code (I mean, contrasted to "C Objective-C"...). In the end, you'll end up writing bindings for those libraries.

Of course, a language without libraries is (almost) useless... and that's the current situation of ObjC in GNU/Linux. Nevertheless, OOLite (a Free Software clone of "Elite") is written in Objective-C (it's in the repos) :p So, you can do really cool things in ObjC if you are patient enough.

In conclusion, it's a shame. So, use it in Apple platforms.

---

### Post by grayrainbow on 2009-12-20
> **nvteighen said:**
> It's not the language, it's the lack of libraries and the zero-to-none interest from anyone except Apple. Which is a pity, because ObjC is really the best you can get when you just want "C with Classes" without all the C++-hype.

Meanwhile, you could use C libraries, but that will be utterly hard to integrate nicely with "Objective-C Objective-C" code (I mean, contrasted to "C Objective-C"...). In the end, you'll end up writing bindings for those libraries.

Of course, a language without libraries is (almost) useless... and that's the current situation of ObjC in GNU/Linux. Nevertheless, OOLite (a Free Software clone of "Elite") is written in Objective-C (it's in the repos) :p So, you can do really cool things in ObjC if you are patient enough.

In conclusion, it's a shame. So, use it in Apple platforms.
I think we might need to make another lesson on recursion...as I sad - let facts speak...is there C# for Linux? Is it use more than obj-C for Linux? I won't even mention java, apart from this sentence. When some 'smart' guy decide to make 'the next great thing' in programming languages, not always(in reality very rarely) something useful happen. Look, Smalltalk was good idea of its time, but how many people really use it nowadays? It's even not object oriented in modern sense.
Otherwise cocoa is good framework for Apples stuff, but quite useless on good platforms(meaning something that could run not only on 0.1% of the hardware in the world, more % usually lead to community, collaboration, and you get it to what this lead). And again as I sad - if somebody like it he/she could go and use it, just when the platform got old(iPhone is already old), he/she will left behind the stuff that comes out in the near future(and as it looks very interesting hardware gadgets will come out in next few years, some already came).

---

### Post by nvteighen on 2009-12-20
> **grayrainbow said:**
> I think we might need to make another lesson on recursion...as I sad - let facts speak...is there C# for Linux? Is it use more than obj-C for Linux? I won't even mention java, apart from this sentence. When some 'smart' guy decide to make 'the next great thing' in programming languages, not always(in reality very rarely) something useful happen. Look, Smalltalk was good idea of its time, but how many people really use it nowadays? It's even not object oriented in modern sense.
Otherwise cocoa is good framework for Apples stuff, but quite useless on good platforms(meaning something that could run not only on 0.1% of the hardware in the world, more % usually lead to community, collaboration, and you get it to what this lead). And again as I sad - if somebody like it he/she could go and use it, just when the platform got old(iPhone is already old), he/she will left behind the stuff that comes out in the near future(and as it looks very interesting hardware gadgets will come out in next few years, some already came).

I totally agree with you, actually. I'm just trying to make further analysis of the fact "ObjC is useless in GNU/Linux". I think it's not because of a fundamental flaw in the language, but just lack of interest in developing stuff in it like libraries and such... maybe just because of ideological issues against Apple.

But well, if the OP is interested in the iPhone, well... you never know... there might be a new iPhone supporting new stuff anytime soon and you can't say the iPhone is totally obsolete right now. Of course there are better platforms, someone has told me fantastic things about Maemo.

Let's all use Forth.

---

### Post by grayrainbow on 2009-12-20
> **nvteighen said:**
> I totally agree with you, actually. I'm just trying to make further analysis of the fact "ObjC is useless in GNU/Linux". I think it's not because of a fundamental flaw in the language, but just lack of interest in developing stuff in it like libraries and such... maybe just because of ideological issues against Apple.

But well, if the OP is interested in the iPhone, well... you never know... there might be a new iPhone supporting new stuff anytime soon and you can't say the iPhone is totally obsolete right now. Of course there are better platforms, someone has told me fantastic things about Maemo.

Let's all use Forth.
If you follow the logic of ideological(idiocraticy in hateboys cases) then C#, as microsoft product, would has a lot more problems, but people use it. And apart from stupid advertising(and idiocratic fanboys) stuff, Apple deserve a lot of respect for their part in PC revolution, just obj-C and lack of desire to open theirs platforms are not part of it, but I'm sure they have their reasons :)
Anyway, back to original topic I see obj-C as fundamentally wrong and I suspect that OP will find this 'the hardway'. But you know...if you look at new language as battle - hard victory is the sweetest victory :)

---

### Post by Igniteflow on 2009-12-21
Interesting points being made.  I'm well aware of the fact that Objective-C is pretty much only relevant for programming for the Apple platform, but I don't think that learning a new programming language is ever a waste of time.  I'm learning Perl right now, despite the fact my job will probably never require it, but I know it'll make me a better, more rounded programmer.  Objective-C seems interesting because it's more low level than anything I've worked with before, but must agree that outside of Apples sphere it's not widely used.  

Market predictions suggest the iPhone is not going out of fashion anytime soon, quite the opposite really.  Android does look very attractive though...

---

### Post by CptPicard on 2009-12-21
> **Igniteflow said:**
> I'm well aware of the fact that Objective-C is pretty much only relevant for programming for the Apple platform, but I don't think that learning a new programming language is ever a waste of time.

"Platform support" is a pragmatic consideration certainly, but programming languages in themselves can have interesting design elements that make them worth learning simply for the exposure to the ideas. Also, languages that have their core "well defined" tend to also have good standard libraries written for them. Unfortunately, in Objective-C's case, this seems to have happened mostly on Apple.

> I'm learning Perl right now, despite the fact my job will probably never require it, but I know it'll make me a better, more rounded programmer.

If you're into putting a scripting language into your toolbox, consider Python. For general "rounding" of your understanding, nothing beats Lisp. As ESR says, you might not use it much, but it makes you a better programmer in all the other languages you use, for the rest of your days.

As the late, great E. Dijkstra said, the tools we use influence our thinking.

> 
  Objective-C seems interesting because it's more low level than anything I've worked with before

If ObjC had decent libraries on Linux, I would certainly use it much more. In most of the C I ever write, I end up always formulating some sort of object system with some kind of opaque pointers and inherited structs and prototype-pattern-ish(?) method association with structs.

These design idioms crop up so often that it is no wonder that it's been formalized into Objective-C as a kind of very lean addition, while retaining C as a subset. The method call resolution by using selectors is also quite much more flexible than the Simula-style static-compiled system adopted by C++.

But alas, library support on Linux is so lame that I tend to focus on writing Python extensions in C instead these days. It also gives you best of both worlds, but requires some understanding of CPython's internals.

---

### Post by Igniteflow on 2010-01-06
Thanks CptPicard, I appreciate your input.  I have now got hold of a Mac and have begun working through Kochan's 'Programming in Objective-C 2.0'.  Three chapters in and it's helping me better understand some elements of OOP that must have gone over my head the first time round, or that I just thought I understood, but didn't properly.  I'm also getting my first glimpses of C, which is interesting.  

I will take a look at Python and Lisp as soon as I'm done with this book, I'm not good at studying two languages at once - must be all the coffee!  So much to learn, hopefully I'll be skilled up enough at some point in the future to get involved and give something back to the community.  If it wasn't for Ubuntu and Open Source I never would have got involved with programming in the first place.

---

