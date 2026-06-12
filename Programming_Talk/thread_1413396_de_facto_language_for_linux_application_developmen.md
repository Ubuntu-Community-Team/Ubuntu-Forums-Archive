---
title: "de facto language for linux application development"
date: 2010-02-22
forum: Programming Talk
---

### Post by kolaperumal on 2010-02-22
I have been browsing this forum for the past few days in search for the ultimate programing language for linux application development.I am not an expert in programming but i can understand the language of the geeks in the forum lol!

Coming back to the subject, there is no such defacto language for linux apps development.While many users suggest using python , i feel it cannot be used for performance intensive apps ...still many will suggest to optimize the code by using extension modules developed in C.

About C++, performance wise it is better than python but there are not many libraries like the ones developed for java.Even if one exists they are just scattered as projects around the internet which makes life difficult for an average programmer like me to produce some good apps.

Turning our attention to Java,just look at the size of the class libraries they have ....they are really good for developing server side apps and not cute looking GUI apps.Now some would say SWING is really cool but I personally dislike SWING as it takes time to load and the performance of the components make me to think ..Why did i develop my GUI in SWING..

I have discussed all prominent languages i guess,the point is we dont have single unified language IDE ,libraries ,adding new modules offering best performance (Execution speed)..like MS visual studio which provides all in one environment for windows app development.Unless we give a serious thinking in this direction we are not going to have newer breed of young , inexperienced yet creative programmers jumping to Linux world for developing Applications.

Pls note all the above text are my personal opinion and I want your views too..Do correct me if I am wrong and I am interested in learning things!:)

---

### Post by CptPicard on 2010-02-22
C++ interfaces just fine with C libraries, so the combination of C and C++ libraries is technically all you'll ever need. If you want a "de facto" language, then we're talking C and/or C++... however...

How much of a programmer are you already? Python is an excellent learning tool, and also goes a long way in other development... not to mention it is a great amalgamation or a lot of ideas from different programming languages, so once you're competent in Python, you have a pretty good mindset ready for adapting to other languages...

---

### Post by Simian Man on 2010-02-22
> **kolaperumal said:**
> While many users suggest using python , i feel it cannot be used for performance intensive apps ...still many will suggest to optimize the code by using extension modules developed in C.
In any application, only a very small portion of it needs to be tuned for performance.  You can write those portions in C and the majority of your application in Python.

> **kolaperumal said:**
> About C++, performance wise it is better than python but there are not many libraries like the ones developed for java.Even if one exists they are just scattered as projects around the internet which makes life difficult for an average programmer like me to produce some good apps.
Actually C++ probably has the best library support of any programming language on earth.  Most libraries on Linux are written in C and then bound to other languages like Python.  The nice thing about C++ is that you can use these libraries directly - in addition to libraries that are written in C++ natively.

> **kolaperumal said:**
> Turning our attention to Java,just look at the size of the class libraries they have ....they are really good for developing server side apps and not cute looking GUI apps.Now some would say SWING is really cool but I personally dislike SWING as it takes time to load and the performance of the components make me to think ..Why did i develop my GUI in SWING..
Java does have a large standard library, but not as many third-party libraries as C or C++ or even Python.  As you mentioned, Swing is a pretty awful GUI toolkit.  I honestly would never choose Java for desktop application development.  If you want something like this but with better libraries, and Linux integration, look into C# and Mono.

> **kolaperumal said:**
> Coming back to the subject, there is no such defacto language for linux apps development.

Is there a de facto standard for *anything* on Linux? :)

In the end, the language you use to write your applications isn't *that* important.  Just pick one and get cracking :).

---

### Post by Some Penguin on 2010-02-22
Homogeneity tends not to spawn creativity.  For that matter, it goes against having the right tool for the job.

---

### Post by Dragonbite on 2010-02-22
Isn't Gnome or GTK more C based, while Qt (which KDE is based on) more C++ ?

I hear a lot about Python in these forums too.  Makes me want to look into Python and GTK development.

My first thought on the Java issue is Mono and GTK#.

---

### Post by kolaperumal on 2010-02-22
> **Simian Man said:**
> In any application, only a very small portion of it needs to be tuned for performance.  You can write those portions in C and the majority of your application in Python.

So can i develop a user friendly app with using the flexibility of python and at the same time the power of C to get system level tinkering.


> Actually C++ probably has the best library support of any programming language on earth.  Most libraries on Linux are written in C and then bound to other languages like Python.  The nice thing about C++ is that you can use these libraries directly - in addition to libraries that are written in C++ natively.

I do accept your point that most of the libraries are written in C or C++.The point is when you are building an application you will need libraries like a networking(like the one java has ery powerful and easy to use) , image processing  etc we have to spend many hours searching the net for one and there is no one place where i can get a consolidated information regarding the plus and minuses of these libraries..


> Java does have a large standard library, but not as many third-party libraries as C or C++ or even Python.  As you mentioned, Swing is a pretty awful GUI toolkit.  I honestly would never choose Java for desktop application development.  If you want something like this but with better libraries, and Linux integration, look into C# and Mono.

I have heard about eclipses SWT ..i think it is really good performance wise but it does not have automatic garbage collection..


> In the end, the language you use to write your applications isn't *that* important.  Just pick one and get cracking :).

For ppl like programmers , they can easily manage to get the applications running up after some searching(for libraries) and tweaking but for general users who just want to get the app running it is really a head ache .we need make things more simpler for them so they can just start the app and run it no googling  or any other kind of things

---

### Post by kolaperumal on 2010-02-22
> **Some Penguin said:**
> Homogeneity tends not to spawn creativity.  For that matter, it goes against having the right tool for the job.

I do accept that but think how VB (visual basic ) revolutionized the desktop app development for windows which we cannot deny ....Server side development is something more different and it had its own breed of development in the past and even in the future .A single concentrated environment something similar to ms studio will develop a unified approach for linux app development making it easier for ppl to develop , to get support , to upgrade what not.Many of the open source projects are not unified and are just spread around the internet ..there is no sort of synchronization between them..I think u can understand what I meant, correct me if i am wrong!

---

### Post by OgreProgrammer on 2010-02-22
> **kolaperumal said:**
> So can i develop a user friendly app with using the flexibility of python and at the same time the power of C to get system level tinkering.

More and more of ubuntu seems to be switching over to python based apps. I can see a definite trend in the developers. 

As far as system level stuff goes, I think python is just fine for that. Maybe you mean something pretty obscure? In any case, the list of python modules on my machine is 5 pages long, and I didn't install anything but pygame and quickly.

Most of what goes on in a typical desktop app is less intensive than what is required in a game, and pygame works just fine.

---

### Post by Letrazzrot on 2010-02-23
> **kolaperumal said:**
> 
For ppl like programmers , they can easily manage to get the applications running up after some searching(for libraries) and tweaking but for general users who just want to get the app running it is really a head ache .we need make things more simpler for them so they can just start the app and run it no googling  or any other kind of things

I just want to point out that, since you seem to be comparing the situation to Windows, that deploying applications on that platform wasn't necessarily a picnic either.  At least in my (limited) experience, I've had to worry/fix numerous lib/dll problems when trying to deploy from Visual Studio (although my lack of experience probably contributed to this).

I'm very new to Linux, but is there generally an accepted issue with the end-user not being able to easily run applications?  And is this related to the language chosen for development?

To be honest, I'd guess that approximately zero programmers would ever want a de facto language, and this would probably never happen.  Visual Studio is a nice application, true, but C(++/#) are not the preferred languages of choice by everyone.

Different languages are different tools for different situations.  There is no one-size-fits-all language.

---

### Post by Barrucadu on 2010-02-23
> **Letrazzrot said:**
> To be honest, I'd guess that approximately zero programmers would ever want a de facto language, and this would probably never happen.

Nothing wrong with a *de facto* standard language. A *de jure* standard language, however&#8230;

---

### Post by slavik on 2010-02-23
1. Look into Perl
2. Look into CPAN (I can argue that it has more libraries than Java)
3. To everyone who says to write modules in C for Python: Have you ever written one?

---

### Post by CptPicard on 2010-02-23
> **slavik said:**
> 
3. To everyone who says to write modules in C for Python: Have you ever written one?

I have, I have! :)

While I fully respect the "in properly written Python the speed issue is spread over everywhere" counter-argument, it's doable. Either the module genuinely can be isolated into C function calls and the interface is clean and nice and simple, or alternatively you must understand CPython's internals a bit more in order to interact with the language elements in the C binding code so you can expose your own implementations more in terms of convenient language primitives. 

SWIG gives you a pretty good start for bindings, and then you just write specific code to transform between objects and possibly make sure you play nice with Python's reference counting mechanism. Here also Python's duck-typing comes in handy... it's always sufficient for an object to just respond appropriately to whatever is being called on it at runtime, so if you know you're going to need something at a certain point in your code, all you need to do is to just implement that behaviour...

---

### Post by TheStatsMan on 2010-02-23
I have as well although as I only work with numerical coding I tend to use Fortran for my extensions. Write the function or subroutine in Fortran, compile with f2py use from python, couldn't be easier. You can also use f2py to link to C routines, you just need a Fortran signature file. It is really pretty easy as well.

---

### Post by Dragonbite on 2010-02-23
> **kolaperumal said:**
> I do accept that but think how VB (visual basic ) revolutionized the desktop app development for windows which we cannot deny ....Server side development is something more different and it had its own breed of development in the past and even in the future .A single concentrated environment something similar to ms studio will develop a unified approach for linux app development making it easier for ppl to develop , to get support , to upgrade what not.Many of the open source projects are not unified and are just spread around the internet ..there is no sort of synchronization between them..I think u can understand what I meant, correct me if i am wrong!

With .NET, the line between VB.NET and C# for desktops, web and servers is technically blurring, though the stigma that VB is for desktop and newbies while C# is for "real" programmers is still there.

The advantage that .NET has is that you are able to run a number of different languages (IronPython, VB.NET, C#, IronPHP, etc.) and have them compile down to the "same" compiled code for the framework to use.  Mono is pretty much able to handle that compiled code but Monodevelop limits what they support, or support anywhere kinda like Visual Studio.

Now if I could run Visual Studio in Linux and debug and compile down to Mono runtimes which I can move to Linux (w/Mono), Windows (w/.NET) or even Mac (w/Mono) then I'd be all over that!  In fact, maybe work would be willing to change too!

---

### Post by Cracauer on 2010-02-23
> **kolaperumal said:**
> I have been browsing this forum for the past few days in search for the ultimate programing language for linux application development.I am not an expert in programming but i can understand the language of the geeks in the forum lol!

Coming back to the subject, there is no such defacto language for linux apps development.While many users suggest using python , i feel it cannot be used for performance intensive apps ...still many will suggest to optimize the code by using extension modules developed in C.

About C++, performance wise it is better than python but there are not many libraries like the ones developed for java.Even if one exists they are just scattered as projects around the internet which makes life difficult for an average programmer like me to produce some good apps.

Turning our attention to Java,just look at the size of the class libraries they have ....they are really good for developing server side apps and not cute looking GUI apps.Now some would say SWING is really cool but I personally dislike SWING as it takes time to load and the performance of the components make me to think ..Why did i develop my GUI in SWING..

I have discussed all prominent languages i guess,the point is we dont have single unified language IDE ,libraries ,adding new modules offering best performance (Execution speed)..like MS visual studio which provides all in one environment for windows app development.Unless we give a serious thinking in this direction we are not going to have newer breed of young , inexperienced yet creative programmers jumping to Linux world for developing Applications.

Pls note all the above text are my personal opinion and I want your views too..Do correct me if I am wrong and I am interested in learning things!:)

In general, the industry has spend 30 years preventing any good language from actually taking over. Sun's backstabbing of it's own Java is certainly the masterpiece of it all, allowing for C# to step in, leave Linux on C/C++ and prevent Apple from giving up on NeXT's Objective-C approach in favor of Java. We can be glad it even made it into the server-side code segment. Java performance claims are generally misleading and their language benchmarks not meaningful. In practice a good C, C++ or Common Lisp hacker's code can run circles around Java code, unless you are willing to make the Java code unmaintainable.  Performance-clumsy library design such as you experienced in Swing makes it worse and let's be honest - most Java libraries are naive like that in the performance department.

There is really no shortage of C/C++ libraries for Linux. As you say the major problem is general mess and getting them together, but there are several things you need to keep in mind:
[list]
[*]Your distribution does the collecting for you and you probably end up with a compatible set. If a library is too obscure to be in Debian or FreeBSD ports there is a high chance it sucks.  Doesn't have to be this way, but as a beginner you should probably concentrate on common libraries included with the distribution. Shallowly debugged and unmaintained libraries are generally worse than rolling your own.
[*]Many "C/C++" libraries are C, but to be honest there are so many different styles of C++ library design I often find this to be an advantage. I get the debugged algorithms and working system access layers in a C library. I then wrap it into C++ (or Objective-C) according to my own taste. Best of both worlds.
[/list]

Python is a mess of incompatible versions. I don't know how anybody can stand it. If you want a slow scripting language I'd use Ruby or Perl.  Perl is actually pretty cool now that it isn't that popular anymore. Most stuff you get from the library archive actually works now, there are libraries for exception handling etc. and the power at your fingertips is unmatched.  Ruby is annoying but at least somewhat predictable.

---

### Post by Dragonbite on 2010-02-23
Does anybody think that now that Sun is owned by Oracle, that Java could get the much-needed revisions to improve speed, interface and quality and make it a competitor for .NET/Objective-C/C/C++?

*Could* it become the de facto language for Linux?

---

### Post by CptPicard on 2010-02-23
No, because VM-based languages really can't become de facto languages on a system unless the VM has some fairly heavy integration into the operating system, even on a kernel level... at the very least you'd have to integrate the memory management systems of the OS and the various separate VM processes.

Mind you, I have nothing against VM-based languages in general... the abstracted machine is a very good idea.

---

### Post by Dragonbite on 2010-02-23
> **CptPicard said:**
> No, because VM-based languages really can't become de facto languages on a system unless the VM has some fairly heavy integration into the operating system, even on a kernel level... at the very least you'd have to integrate the memory management systems of the OS and the various separate VM processes.

Mind you, I have nothing against VM-based languages in general... the abstracted machine is a very good idea.

That makes sense that VM-based languages won't become the de facto, though it may become a leading application platform if the performance is good enough and the applications are quality.

---

### Post by Cracauer on 2010-02-23
> **Dragonbite said:**
> Does anybody think that now that Sun is owned by Oracle, that Java could get the much-needed revisions to improve speed, interface and quality and make it a competitor for .NET/Objective-C/C/C++?

*Could* it become the de facto language for Linux?

The language spec doesn't allow full speed no matter how good the compiler. Of course it is still much faster than any of the python/perl/ruby/go stuff, not to mention has SMP-capable threads.

As for making it big: too late.

All these Java libraries that people use have been written before important features came along, namely generics. There is no good way to mix a generics-style approach to algorithms writing with that lousy cast style thing.  In addition, Sun's insane licensing has prevented a good JVM to become standard on all OpenSource OS installations. To this day I have to retrieve parts of the JDK by hand when building from source. Insane.

Plus both generics and inner classes fell short of my expectations. First Sun kicks and screams that it's useless, then they give them when it's too late, and only half-baken. Good riddance.

Now it's too late. Microsoft has established C# pretty well for the Windows crowd. Linux people have forked out into a C/C++ crowd and a Python crowd, both producing code that's unreliable, or slow, breaks on updates, or all of the above. Apple made their pick staying with Objective-C.

Disgusted by all this the alternative language people (Common Lisp, various MLs, Haskell) also got a foot in the door, further diversifying things but lessening the pressure to use a clean language like Java. Clean language freaks just use one the alternative languages instead of teaching the community about clean languages. 

So the others stay clueless instead of everybody working together on a common language that has has reasonable everything (performance, cleanness support features, SMP threads).

Party over for Java.

---

### Post by CptPicard on 2010-02-23
> **Cracauer said:**
> 
Plus both generics and inner classes fell short of my expectations. First Sun kicks and screams that it's useless, then they give them when it's too late, and only half-baken. Good riddance.

This stuff really was a major nail in the coffin, and I'm really glad there are people who understand this (yeah, they're Lispers and such...) in particular the fact of not turning inner classes into proper closures as a matter of principle despite most smart Java coders turning their code into an inner-class-fest was big fail. It should have been ringing big bells...

> 
Now it's too late. Microsoft has established C# pretty well for the Windows crowd. Linux people have forked out into a C/C++ crowd and a Python crowd, both producing code that's unreliable, or slow, breaks on updates, or all of the above.

Well, at least the Linux crowd really do have a broad base of choice... it's as open a platform for "any language" as it gets, and if you really had more of a de facto language especially in direction of languages that rely on their own "platform" it would just restrict the others. Admittedly Microsoft may be onto something with their CLR -- something the JVM could have been.

> Clean language freaks just use one the alternative languages instead of teaching the community about clean languages. So the other stay clueless.

Well, we've tried hard here and it has resulted in some impressive flamewars... ;) Good to see you back around here btw.

---

