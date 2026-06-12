---
title: "Any C# programmers?"
date: 2007-09-17
forum: Programming Talk
---

### Post by Andrewie on 2007-09-17
I'm learning C# (part of school), and I'm wondering people's experience with it. 

P.S. what's a good C# compiler and/or IDE to use for Linux. Booting into windows hurts me :lolflag:

---

### Post by Wolki on 2007-09-17
Not me, sorry.

But for C# you should probably try Mono and the related IDE MonoDevelop. 

Two of Ubuntu's default programs are written with Mono, Tomboy and F-Spot, so you can take a look at their sources for inspiration

---

### Post by Andrewie on 2007-09-17
> **Wolki said:**
> Not me, sorry.

But for C# you should probably try Mono and the related IDE MonoDevelop. 

Two of Ubuntu's default programs are written with Mono, Tomboy and F-Spot, so you can take a look at their sources for inspiration

I heard MonoDevelop was buggy :( There was a few other C# compilers for Linux say a few on wikipedia, I have to try them out soon

---

### Post by luisromangz on 2007-09-17
I'm have been developing proffesionally in C# for a couple of years and I can say it's a great language. To develop with it in linux you should use Mono, and its IDE Monodevelop as was said before.

Monodevelop is compatible with VS solutions so you can use to open your school assignments easily.

I've got the latests (1.2.5) mono packages from this repository:

deb [http://www.viraptor.info/repo](http://www.viraptor.info/repo) feisty-custombackports contrib

 And the latest Monodevelop was installed from GetDeb:

deb [http://ubuntu.org.ua/](http://ubuntu.org.ua/) getdeb/

As for Monodevelop being buggy, well, it work flawlessly but for the integrated GTK# form editor. But I don't use it not because of that, but because I like the Glade approach better, linking the interface definition files at runtime rather than having code created by the form designer.

Bye!

---

### Post by Andrewie on 2007-09-17
> **luisromangz said:**
> I'm have been developing proffesionally in C# for a couple of years and I can say it's a great language. To develop with it in linux you should use Mono, and its IDE Monodevelop as was said before.

Monodevelop is compatible with VS solutions so you can use to open your school assignments easily.

I've got the latests (1.2.5) mono packages from this repository:

deb [http://www.viraptor.info/repo](http://www.viraptor.info/repo) feisty-custombackports contrib

 And the latest Monodevelop was installed from GetDeb:

deb [http://ubuntu.org.ua/](http://ubuntu.org.ua/) getdeb/

As for Monodevelop being buggy, well, it work flawlessly but for the integrated GTK# form editor. But I don't use it not because of that, but because I like the Glade approach better, linking the interface definition files at runtime rather than having code created by the form designer.

Bye!

I'll be sure to try it out then

---

### Post by forrestcupp on 2007-09-17
I did quite a bit with C# when I was in Windows.  I liked it a lot.  I haven't messed with Mono in Linux.

Don't listen to all of the anti-Mono trash that is talked around here.  C# is a great language.

---

### Post by Andrewie on 2007-09-17
> **forrestcupp said:**
> I did quite a bit with C# when I was in Windows.  I liked it a lot.  I haven't messed with Mono in Linux.

Don't listen to all of the anti-Mono trash that is talked around here.  C# is a great language.

don't worry I'm not listening to them

---

### Post by Spr0k3t on 2007-09-17
I've done some C# development.  However, there are many other languages that are suited better than C#.  I stopped C# development prior to moving back to Linux, so I can't help much in that area.

---

### Post by Montsegur87 on 2007-09-17
I work with C# , its nice. Visual Studio is better than MonoDevelop IMO.

I would focus on Java , Monodevelop/Mono is nothing compared to Java/Eclipse

---

### Post by drndrw on 2007-09-17
I thought C# was a Windows langauge... Anyways I started C#. I used MS Visual Studio. But since I'm trying to steer away from Windows, I no longer use this langauage now.

---

### Post by Andrewie on 2007-09-17
> **Montsegur87 said:**
> I work with C# , its nice. Visual Studio is better than MonoDevelop IMO.

I would focus on Java , Monodevelop/Mono is nothing compared to Java/Eclipse

my program is focusing on Java and C#

---

### Post by K.Mandla on 2007-09-17
Moved to Programming Talk.

---

### Post by Andrewie on 2007-09-17
> **K.Mandla said:**
> Moved to Programming Talk.

thanks

---

### Post by vexorian on 2007-09-17
For classes (as in studying ) you may need "interoperability" [size=1](to be locked-in)[/size] thus a virtual machine + visual studio should do good.

---

### Post by dhobbs on 2007-09-17
C# is a great language for developers who just want to quickly write an application.

I use it professionally and I can't say anything bad about it (expect that I must use it in a Windows environment).  That being said, I have yet to do any development with it in a *nix environment, though I would like to see how well the Mono team had done.

You'll enjoy C# and Java but I hope you get to dive into some C/C++ code because it's a slightly different world.  Anyway, enjoy.

---

### Post by Ozitraveller on 2007-09-18
I thought I'd add this in for interest.

A programmers comparison of C# versus Java
[http://www.theserverside.com/news/thread.tss?thread_id=10313](http://www.theserverside.com/news/thread.tss?thread_id=10313)

C#/Java Comparison, by Dare Obasanjo. 
[http://www.25hoursaday.com/CsharpVsJava.html](http://www.25hoursaday.com/CsharpVsJava.html)


Conclusion (2001)
Most developers, especially those with a background in C or C++, would probably agree that features like operator overloading, pointers, preprocessor directives, delegates and deterministic object cleanup make C# more expressive than Java in a number of cases. Similarly, Java developers who learn C# will be pleasantly surprised at features that are missing in Java that will seem glaring in their absence once one uses them in C#, such as boxing, enumerations and pass by reference. On the other hand the lack of checked exceptions, inner classes, cross platform portability or the fact that a class is not the smallest unit of distribution of code makes the choice of C# over Java not a clearcut case of choosing more language features without having to make any compromises.

It is my opinion that both languages are similar enough that they could be made to mirror each other without significant effort if so required by either user base. In this case, C# would have it easier than Java in that C# has less to borrow from Java than Java would have to borrow from C#. However, the true worth of a programming language that is intended for use outside of academia is how quickly the language evolves to adapt to the changing technological landscape and what kind of community surrounds the language. Some programming languages are akin to the French language under the Les Immortels of the Académie Française in France. Les immortels are charged with dictating what constitutes the official French language but they have been slow to adapt to the information age thus their edicts on what constitutes the proper French versions of new words, especially those related to technology, are usually ignored especially since they either conflict with what the general French public would rather call them and show up long after the unsanctioned words have already entered the lexicon. C++ is an example of a language that has undergone a process of balkanization closely resembling the French language under the Les Immortels of the Académie Française while Java under Sun Microsystems can be considered to be a language that has evolved with the times similar to how the English language has done.

Thus the question really becomes, which of these languages looks like it will evolve with the times and be easiest to adapt to new situations as they arise? So far, Sun has done a great job with Java although a lack of versioning support and the non-existence of a framework that enables extensibility of the language built into the platform makes drastic evolution difficult. C# with its support for versioning via the .NET framework and the existence of attributes which can be used to extend the features of the language looks like it would in the long run be the more adaptable language. Only time will tell however if this prediction is accurate.

Conclusion (2007)
As predicted in the original conclusion to this paper, a number of features have become common across both C# and Java since 2001. These features include generics, foreach loops, enumerations, boxing, variable length parameter lists and metadata annotations. However after years of convergence it seems that C# and Java are about to go in radically different directions. The current plans for C# 3.0 are highlighted in the Language Integrated Query (LINQ) Project which encompasses integrating a number of data oriented features including query, set operations, transformations and type inferencing directly into the C# language. In combination with some of C#'s existing features like anonymous methods and nullable types, the differences between C# and Java will become more stark over the next few years in contrast to the feature convergence that has been happening over the past few years. 


I've been a C# developer since the original beta. C# 3.0 will be out next year.

---

### Post by Coyote21 on 2007-09-18
There's also D (from Digital Mars, [http://www.digitalmars.com/d/index.html](http://www.digitalmars.com/d/index.html)), and you can also use it from linux ([http://packages.ubuntu.com/gutsy/virtual/gdc](http://packages.ubuntu.com/gutsy/virtual/gdc) you will need gcc version 4.1), D doesn't have an standard library like C# (particularly it doesn't have an gui), but it is quite similar to C#. You can see an comparison of it in [http://www.digitalmars.com/d/comparison.html](http://www.digitalmars.com/d/comparison.html).

---

### Post by pmasiar on 2007-09-18
> **dhobbs said:**
> C# is a great language for developers who just want to quickly write an application.... it's a slightly different world.

If you want "slightly different world" and "quickly write an application", try dynamically typed language like Python (or Ruby). Thats is about productivity, and freedom from hassle with dynamic typing blew my mind when I encountered it first time. :-)

---

### Post by Dragonbite on 2007-09-18
At work I've been using (*and sent to classes for *) VB.NET and ASP.NET.  I'm using a C# book and Monodevelop at home to teach myself C#.

So far Monodevelop has been alright for me. The thing I've had to get used to is that, and this is true in Visual Studio too, that C# does less hand-holding than VB.NET.  Simple case: VB isn't too concerned about case and will "fix" any case issues you run across.  C# doesn't intellisense (*auto-fill? don't remember the term*) unless you have at least the first word case-correct.

For more up-to-date Mono libraries I know there is [[COLOR="Blue"]Badgerports[/COLOR]]("http://directhex.mfgames.com/"), but is there any equivalent for Feisty or GG?

---

### Post by forrestcupp on 2007-09-18
> **pmasiar said:**
> If you want "slightly different world" and "quickly write an application", try dynamically typed language like Python (or Ruby). Thats is about productivity, and freedom from hassle with dynamic typing blew my mind when I encountered it first time. :-)

I have programmed with C# and Python, and I actually found C# even easier to use.  Especially for GUI stuff.  I don't know about Mono, but I think C# and .NET run somewhat faster than Python, too.  Python is a translated language that isn't compiled at all.  C# is compiled into a bytecode that is then quickly compiled before you run the program.  So it may be slightly slower to start up, but the actual running of the program doesn't take a huge hit.  But it's really dynamic, too.  You can run your program as you are working on it.  It doesn't have to be compiled first like C++ or C.

C# isn't as powerful as C++ or C, but it's pretty powerful.  When I was using Windows, I used C# to program a small 3D flight simulation game demo using straight DirectX with hardware acceleration.  So if it's possible to do that, it has to be fairly powerful.  It's a breeze to make simple GUI apps.

---

### Post by pmasiar on 2007-09-18
> **forrestcupp said:**
> Python ...isn't compiled at all.  C# is compiled into a bytecode that is then quickly compiled before you run the program. 

Of course. But C# is statically typed. Python is also compiled to bytecode, and **if desired** it can be compiled farther (there are compilers). Just nobody cares that much. One interesting compiler finds correct type info at runtime and compiles at runtime including proper type info. 

Simpler solution is to write it all in Python, profile it, and rewrite 5% of the code using 90% of the time as fast C library. So you optimize for speed only the part where it makes sense, **after** you measured it and you know how fast it needs to be.

>  I used C# to program a small 3D flight simulation game demo using straight DirectX with hardware acceleration. 

Of course. You would expect C# to have build-in libraries for those proprietary technologies. If not c#, the language MSFT used to write them, what other language would do it? :-)

Try C# to do something actually useful, like analyze your data using R libraries, or web front-end for a (free non-MSFT) database.

---

### Post by forrestcupp on 2007-09-18
> **pmasiar said:**
> 
Try C# to do something actually useful, like analyze your data using R libraries, or web front-end for a (free non-MSFT) database.

Well, I've done useful apps, too.  And it was pretty easy to do.  C# is made for programming  useful apps quickly.  I was merely pointing out that it is also powerful enough to do complex stuff that needs speed.

I don't have anything against Python.  I've used it and liked it.  I've programmed GUI apps with Python and PyGTK, and it was pretty easy to do.  But I have also used C# and .NET and it was easier.  It doesn't matter to me what anyone uses.  I now use C++ anyway.

---

### Post by vexorian on 2007-09-18
Since this already turned into a language flame war.

C#  is a language with the only purpose on destroying Java.

Why does MS hate Java? It is because its compile once run everywhere actually works. When a company develops in Java its software does work correctly everywhere without issues. And that's a problem that threatens to remove MS' auto monopoly.

So, they just made a Java clone, added nice stuff, etc, they made it heavily dependant on windows. Yes, they advertise .net as cross platform, etc but the truth is that it is not cross platform at all.

* Just for development you need visual studio which won't run everywhere.

* Most programmers lured into C# use system.windows.forms out of ignorance, that makes their programs heavily locked into windows.

* Yeah mono implements windows.forms but it does it in a Wine-like half-assed way that is not helpful.

* MS has promised they won't sue over current versions of .net EXCEPTING the implementations of windows.forms , (which means you really can't legfally use MONO's windows.forms implementation to run C# apps , which means C# isn't cross platform.

* MS' promise towards .net does not apply to later versions thus they got a remote off switch towards MONO they may use whenever they want to.

Enjoy.

There aren't really a lot of reasons to use C# over Java, both are heavy , slow languages with garbage constructs and some run time generics, etc. Either of them might be better than the other in certain aspects but in the end a pragmatic programmer should choose Java since it at least isn't tied to a single platform and is eventually becoming a GPL product which reduces any risks of lockage towards any program you make.

Java + GTK or QT becomes a good tool, [bias]of course nothing can beat over awesome C++[/bias] but if you have to choose between Java and .net , Java is simply a better option with less land mines.

C# is basically a Java clone with some extensions so learning any after the other is a trivial task...

---

### Post by Dragonbite on 2007-09-18
> **vexorian said:**
> Since this already turned into a language flame war.You figured you'd put a couple more logs on and stoke the ashes some, eh?

---

### Post by Andrewie on 2007-09-18
thanks for the information everyone

vexorian
thanks for the types I'll try and stay away from windows.forms.

I just have one more question, is their any QT/kdevelop for C#, or do I have to wait for KDE 4?

---

### Post by forrestcupp on 2007-09-18
> **vexorian said:**
> 
* Just for development you need visual studio which won't run everywhere.

Not true.  You know that you can program in C# in Linux with Mono.  You don't use Visual Studio for that.  But even in Windows using .NET, you can use an IDE called SharpDevelop which is free software.

> There aren't really a lot of reasons to use C# over Java,
Maybe there aren't a lot of reasons, but the ones there are are pretty important.  Like the fact that a lot of companies are requiring their programmers to use C#.  That's one you kind of can't get past.

If you are programming for Windows, it would be silly to not use System.Windows.Forms.  If you are programming only for Linux, you would be better off using another language altogether, unless you use C# for your job and that is all you are familiar with.  But I think if C# is all you are familiar with, you probably wouldn't have a programming job anyway.

---

### Post by Dragonbite on 2007-09-19
> **Andrewie said:**
> I just have one more question, is their any QT/kdevelop for C#, or do I have to wait for KDE 4?There are QT bindings for Mono called [[COLOR="Blue"]Qyoto[/COLOR]]("http://cougarpc.net/qyoto/").

I just read about this yesterday from [[COLOR="Blue"]Miguel de Icaza's blog regarding Qyoto[/COLOR]]("http://tirania.org/blog/archive/2007/Sep-18.html").

---

### Post by chrisfay on 2007-09-19
> I thought I'd add this in for interest.

A programmers comparison of C# versus Java
[http://www.theserverside.com/news/th...hread_id=10313](http://www.theserverside.com/news/th...hread_id=10313)

Interesting, although both have changed quite a bit in 6 years ;-)

---

### Post by pkid on 2007-12-03
I am starting to use MonoDevelop in Linux for my C# development and every night I cry myself to sleep because I miss Visual Studios 2005 so much.  It has to be the best IDE out there.  MonoDevelop looks like it has promise and looking at the changelogs it seems like the guys are doing a good job so all is not lost.

I just wish that Ubuntu would update the MonoDevelop package more often.  I am on 0.14 and there are already on BETA 2 which seems to have a few features that I would find useful.

---

### Post by pmasiar on 2007-12-03
It depends.

I had to use VS for one of my projects and I cried in frustration how clunky and non-intuitive it was. :-)

---

### Post by j_g on 2007-12-03
A poster asks about C# support in Linux, so he can work on his C# school assignments, and **as usual** (when the topic can be construed, or often misconstrued, by "linux fanboys" into being all about Microsoft), the thread degenerates into an argument about how people should be using Python or some other language (ostensibly not associated with Microsoft).

Typical.

Obviously, Ubuntu's forums are all about advocacy, and not about helping people with real information. And the moderators are clearly a large part of this situation, because their actions aid and abet it.

---

### Post by LaRoza on 2007-12-03
> **j_g said:**
> A poster asks about C# support in Linux, so he can work on his C# school assignments, and as usual, the thread degenerates into an argument about how people should be using Python or some other language (ostensibly not associated with Microsoft).


* Programming languages are tools
* Finding the best tool for the job is part of life
* C# has issues on Linux that Python doesn't
* C# is a good language, so is Python (Ruby, Perl, NASM, etc)
* Ubuntu development involved Python for many reasons, and this is an Ubuntu Forum
* IronPython is MS implementation of Python, and Python itself has MS specific libraries, so it isn't "anti-microsoft"

I have read the entire thread over again, and found a discussion of the various tools, experiences, and issues with using C# in Linux (very OT), a few alternatives (to be expected, read any thread on this forum), and one flamebait.

---

### Post by slavik on 2007-12-03
> **forrestcupp said:**
> I did quite a bit with C# when I was in Windows.  I liked it a lot.  I haven't messed with Mono in Linux.

Don't listen to all of the anti-Mono trash that is talked around here.  C# is a great language.

so is BASIC ;)

but in all honesty from my foray into C#, MonoDevelop was nice.

---

### Post by kvorion on 2007-12-04
I have been meaning to try out mono for quite a while, but somehow I never found a compelling enough reason to do so. As it is, C# doesn't have many takers in the Linux world, so when I code on the Linux platform, its either C or C++.

Inspite of what people say, C# is a great language, and it is so good because it is coupled so strongly with the .NET Framework and the Windows operating system. I have been developing using C# for over a year, and I am sure that there is nothing better than Visual Studio for a .NET language. So if you are really serious about C#, I suggest you move to using it on a windows platform, because of the framework class libraries that you can use.

---

### Post by emperon on 2007-12-04
I have developed  a HUGE asp.net application on linux/mono then ported to windows. I certainly am convinced you can do serious development with C# and Monodevelop. 
Finally considering .net the only windows specific part looks like windows forms. You can go do full development on C# with linux and in case you need to access system methods you can use P/Invoke which is great (though breaks cross platformity)

---

### Post by true_friend on 2008-06-13
It doesn't matter what is gui, it matters the code is same. Changing a few lines of code for corss-platformity is not bad et all. Mono does very good C# implementaiton in Linux.

---

