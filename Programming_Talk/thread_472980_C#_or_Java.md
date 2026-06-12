---
title: "C# or Java"
date: 2007-06-13
forum: Programming Talk
---

### Post by visionaire on 2007-06-13
I can't make up my mind, what of this 2 PL would you recommend me, i program in Powerbuilder in my job, and python for fun, but i want to learn another major language, i already know C a little

Cheers

---

### Post by beatlesfan124 on 2007-06-13
well, i personally don't like java, but thats just me. i think its not fast enough because of the jvm (java virtual machine) and i hate the amount of declarations that it needs. its more for enterprise level projects where restriction is important. it is a programming language to learn still if you want to work on open source projects such as in linux. C# is microsoft's proprietary language and is seen a lot in windows now such as vista. the declarations for C# though are very similar to java, so after learning one, you could easily switch to another. you would just need to understand their differences and not need to learn what seems like learning an actual language. hope some of this helps.

---

### Post by rekahsoft on 2007-06-13
like beatlesfan said, java and C# look the same...once you understand the concepts you could make the switch from on to the other...i started with java, then moved to C++ and now am looking at C#. BTW remeber that C# is a language spec/platform and that it is not owned by M$ (or i would not touch it); there is a great opensource implementation of the .NET platform (mono) and it works good in linux as well.

---

### Post by Skardal on 2007-06-13
As beatlesfan124 says, if you know one of them, it's no big problem to switch! I've been using both languages for a while, and I can't either decide which one I prefer most :P 
But again, if you want to be cross-platform, Java is the best choice I guess....though [Mono]("http://mono-project.net") has become pretty good! 

Maybe you should just give 'em both a try, and hopefully you'll quickly discover what you prefer :)

Edit: rekahsoft, you "won" :-\" ;)

---

### Post by Cows on 2007-06-13
If you want to learn something thats extremely portable then you should learn C. Although I don't like C. I program in C++. IMO though C is much faster , and java , C# are extremely slow languages. It all depends on what you feel comfortable with, but also remember this: High Level Languages are always slower. High Level meaning how easy the language is. C and C++ are mid-level. ASM is Low-Level. C# , Java is High Level. Correct me if I'm wrong.

---

### Post by Skardal on 2007-06-13
And of course; which language to learn also depends on what you want to program.

---

### Post by nitro_n2o on 2007-06-13
Well... yes Java is SLOW.. but so what???? you are not programming a rocket? are you? Although i prefer c/c++ bu go with Java.. It has so many advantages, unless you plan to be a professional programmer:
- portable (no worries works, with all operating systems and you don't need to modify anything in most cases)
- web apps 
- easy (you can't do something wrong in Java) 
- well supported 
- relatively easy GUIs 
- Eclipse (a great IDE that can do everything for you) 
- well documented 
- you can find almost everything written for you from Sun
- and it teaches some programming concepts

---

### Post by kknd on 2007-06-13
> **visionaire said:**
> I can't make up my mind, what of this 2 PL would you recommend me, i program in Powerbuilder in my job, and python for fun, but i want to learn another major language, i already know C a little

Cheers

Java!!!

Java is way more mature, but Sun still work on it.
There are a lot of open source libraries and tools for Java. In fact, the best tools for Java are open-source, and the virtual machine and standard libraries are being "opened" now (you can download its source and compile it now).

---

### Post by kknd on 2007-06-13
Hi, I disagree with you, IMHO:

> **Cows said:**
> If you want to learn something thats extremely portable then you should learn C. 

True, C itself is very portable. Try doing a real project that require multimedia and other libraries and see what amount of work you will need. Or learn Java.

> **Cows said:**
> 
Although I don't like C. I program in C++. IMO though C is much faster , and java , C# are extremely slow languages.


40% more slow is much? There are a plenty of application that do some heavy mathematics in Java.

> **Cows said:**
> 
 It all depends on what you feel comfortable with, but also remember this: High Level Languages are always slower. High Level meaning how easy the language is. C and C++ are mid-level. ASM is Low-Level. C# , Java is High Level. Correct me if I'm wrong.

Hight level languages are now always slower (yes, you can always make it faster in low-level languages if you put effort in it), because a high level language compiler/interpreter can do some serious optimizations, generating machine code with comparable performance to low-level languages like C. Look at PyPy and real Java applications (not just 5sec benchmarks0.

---

### Post by pmasiar on 2007-06-13
What is your goal when learning new language? Improve your career? Enhance your understanding of programming? Learn new area? Have fun?

And which new area: web apps? parallel systems?

C# is just MS Java, difference is in libraries - and incompatibilities are deliberate. :-( Both languages are rather boring.

---

### Post by samjh on 2007-06-13
Java is my pick.  Now almost FOSS, well-established, safe, and efficient to program in (relatively speaking).  It has a massive standard API that will let you accomplish 90% of programming you will ever do.  Now that it has been open-sourced while still being developed and supported by Sun, it will only improve faster.

C# is a good language, but it, like Java, depends on its libraries.  Microsoft rules the roost at the moment with .NET, and there are a lot of patents associated with that.  Mono is the FOSS version, but it includes some important compatibility layers that are vulnerable to Microsoft's patent action, such as ASP.NET and WinForms.  So beware.

---

### Post by metalkr on 2007-06-18
C#

---

### Post by ankursethi on 2007-06-18
C# is a nice bet. I find it faster than Java. And with Mono coming along pretty well, I wouldn't be surprised to see quite a number of libraries and toolkits for C#.

---

### Post by dustman on 2008-05-15
man, i'm using Ubuntu cause i wanted to escape from microsoft and all it's bullsh*t. Since c# is copied after Java, i don't see why i should use ANY of microsoft's technologies (taking into consideration that windows itself was copied after Mac OS). So go with open source, go with Java, go with Linux!


Cheers!

Radu

---

### Post by vexorian on 2008-05-15
Go with [Vala](http://freshmeat.net/redir/vala/65428/url_homepage/Vala)

I wish for an alternative for these things that would compile something that doesn't require any silly runtime. GCJ actually does that and is very nice, but the problem is that Sun's Java is way stronger and people don't think of using it. Would be nice, one day to see a C# alternative that didn't require runtimes, Vala does that job but the problem is that it is focused on gnome.

Both Java and .net are platforms, so thinking that you can actually use them to make programs that run on Linux is, far-fetched, all you can do is target Java or .net  and hope they will have versions that will run on the platform you actually intended.

---

### Post by Delever on 2008-05-15
Well, in Microsoft camp there is a joke that C# is Java done right - and there is a lot of truth to that.

Monodevelop is nice IDE if you have enough RAM, and given the choice from only C# and Java, I would choose C# (I did more than few lines with both in past).

However, there may be big political reasons to avoid C# because of some huge name behind it :lolflag:

---

### Post by CptPicard on 2008-05-15
> **vexorian said:**
> GCJ actually does that and is very nice

GCJ's binaries still require a big library to be present IIRC, so there is not that much of a benefit really...

---

### Post by dustman on 2008-05-15
> **Delever said:**
> Well, in Microsoft camp there is a joke that C# is Java done right - and there is a lot of truth to that.

Monodevelop is nice IDE if you have enough RAM, and given the choice from only C# and Java, I would choose C# (I did more than few lines with both in past).

However, there may be big political reasons to avoid C# because of some huge name behind it :lolflag:

i don't have enough room to tell you here about my "terrific" experience with c#. I'm a CS student and i had to work with c#, and it's amazingly....BAD. Once i had to write a simple socket application. Everything was working just fine (because c# is so similar to Java - it's curious that c# appeared after Java), and suddenly the data that i was sending through a socket didn't reach the other end...I overlooked the code, and everything was fine...for Pete's sake, it was working 2 minutes ago!!! So i didn't modify anything, and went to sleep. The next morning, when i ran the application...it was working again! Why was that? Of course microsoft lovers might say that it was something wrong with my machine...but this is just one of the many cases c# proved to be "just another microsoft application". So again, go with open source, go with Java, go with Linux! Of course there are many good programming languages to use (maybe Vala ;), and for certain PHP) but anyways, Java rullz! :D

---

### Post by ivze on 2008-05-15
Either java, or C# are made so that the language make software more stabile (e.g. no direct memory management). 
The languages shall not be blamed for being slower (by the rate of 2-4 compared to C++, not 100-1000 times as Python). Write the same application in c++, and you will have a nice programm, that runs faster (just 4 times), but with lots of (---)8< in it =).

---

### Post by achelis on 2008-05-15
Personally I wouldn't code C# even if I was paid for it - but I guess that's mostly because I'm politically biased.

A great plus for Java however is it has Eclipse, I'm not aware of any C# IDEs coming even close to that.

As for the languages themselves - semantics/syntax - they are so similar that if you learn one you've pretty much learned the other as well by default.

---

### Post by vexorian on 2008-05-15
> **ivze said:**
> Either java, or C# are made so that the language make software more stabile (e.g. no direct memory management). 
The languages shall not be blamed for being slower (by the rate of 2-4 compared to C++, not 100-1000 times as Python). Write the same application in c++, and you will have a nice programm, that runs faster (just 4 times), but with lots of (---)8< in it =).
If a self proclaimed programmer can't really code in C/C++ without introducing bugs thanks for the lack of a GC (cause there IS memory management) , then he will be able just as easily to introduce bugs in Java and C#.

---

### Post by LaRoza on 2008-05-15
> **vexorian said:**
> If a self proclaimed programmer can't really code in C/C++ without introducing bugs thanks for the lack of a GC (cause there IS memory management) , then he will be able just as easily to introduce bugs in Java and C#.

Memory management can introduce problems for any programmer. To say that the lack of a GC shouldn't have any effect on bugs is strange. It is another thing for the programmer to track, and therefore, make mistakes.

---

### Post by Delever on 2008-05-15
> **dustman said:**
> i don't have enough room to tell you here about my "terrific" experience with c#. I'm a CS student and i had to work with c#, and it's amazingly....BAD. Once i had to write a simple socket application. Everything was working just fine (because c# is so similar to Java - it's curious that c# appeared after Java), and suddenly the data that i was sending through a socket didn't reach the other end...I overlooked the code, and everything was fine...for Pete's sake, it was working 2 minutes ago!!! So i didn't modify anything, and went to sleep. The next morning, when i ran the application...it was working again! Why was that? Of course microsoft lovers might say that it was something wrong with my machine...but this is just one of the many cases c# proved to be "just another microsoft application". So again, go with open source, go with Java, go with Linux! Of course there are many good programming languages to use (maybe Vala ;), and for certain PHP) but anyways, Java rullz! :D

Well - C# sockets are just direct wrappers around... guess what - winsock :D. I could not dare to touch them, just used WCF when I needed some simple network communication.

BTW, from your explanation it seems that it started working after restart - so maybe you just forgot to close socket properly.

---

### Post by Can+~ on 2008-05-15
> **dustman said:**
> man, i'm using Ubuntu cause i wanted to escape from microsoft and all it's bullsh*t. Since c# is copied after Java, i don't see why i should use ANY of microsoft's technologies (taking into consideration that windows itself was copied after Mac OS). So go with open source, go with Java, go with Linux!


Cheers!

Radu

Last post:
**June 18th, 2007**

Anyway, I prefer java :).

---

### Post by Delever on 2008-05-15
It's strange, although I said that I prefer C# as language, I would choose either of them depending of job, for example:

(if there is no requirement which one to use)

**Applets** - the only choice is Java

**Business application with centralized database** - if target platform is windows, I would prefer C# just because of streamlined IDE. However, there is the cost if you would want to use full version of MS SQL server. MySQL, however, is also possible. If you want to be portable, then Java. I used Interbase and MySQL with Java, and saw Oracle working successfully too.
Speed is also quite trivial in such applications.
Mono may prove to be useful there. However, you can't use any assembly (.Net dll) witch begins with "Microsoft.*", like, Enterprise Library or Smart Client.
Java wins in portability.

**Web** - Lots of "technology" is coming for .Net here. They call "technology" any new piece of crap which is supposed to solve every problem. Basically, in .Net, if you write single line of code, it is wrong way of doing it, because probably Microsoft already created component for that. All you need to do, is to download new free code, edit few dozens of configuration files correctly, create aspx templates correctly, and you have it! Everything just... works? Nope. You end up writing code which makes it work. Invoking private functions of those components using replication. Nasty work, and no freedom. And good luck hosting it on server with .Net framework 3. Of course, you can use generic handlers to write web server output (HTML) directly, and no way of reusing ASP.NET components in them, because ASP.NET can only be used with ASPX form templates.
I am not very familiar with Java side, but there you have almost the same story: you can write handlers, or, possibly, use Java Server Pages (JSP). However, you have hosting on Apache with Tomcat - with much lower costs.
So - what I would choose for web programming? PHP :D.... erm... from those two - .... (thinking) ... ok. Java.

**Game programming** - Again, like with any other choice (possible exception - simple applications), mono is not really a choice yet if you want portability. You can use XNA for game programming with C#, or managed DirectX. XNA is really easy, C# proves to be fast there (you can do enough things even every frame), it requires at least pixel shader 2.0, and everything is done using shaders (HLSL). Managed DirectX is not maintained enough, and year ago there were rumours it may be canceled.
Java, however, can work with OpenGL, and I guess it would be much more portable solution (I have not tried it yet).
So, if I need some accelerated rendering and target platform is Windows, I would go with Xna, otherwise - I would check Java (more likely python or C++).

**Network tools** - Again, better tools in C# (like WCF), require .Net3, and that means it's unportable (mono still in progress). Java there seems much more stable and consistent across platforms (I would hope).

Ok, I guess it is enough - this is very biased review based on my subjective experience. If you want more information about some things (I may know about Java servlets/Xna/.Net3/ASP.NET) just ask.

So, after this review, it seems that Java actually have more possibilities on GNU/Linux. Of course.

I hope someone will find something useful in this post.

---

### Post by jespdj on 2008-05-16
This is already an old post, but I see a lot of FUD and nonsense about both Java and C# here:

> **beatlesfan124 said:**
> well, i personally don't like java, but thats just me. i think its not fast enough because of the jvm (java virtual machine) and ...
Which version of Java are you using? GCJ (GNU Java)? Yes, that's slow. Use Sun Java 6 instead - it is very fast, the JVM is a very sophisticated piece of software that compiles Java bytecode to native machine code on the fly, and so it runs quite fast - not much slower than C++.

Note that C# is also compiled to bytecode, which runs on the .NET (Windows) or Mono (Linux) [CLR](http://en.wikipedia.org/wiki/Common_Language_Runtime). The CLR is a virtual machine, exactly the same concept as the Java VM.

> **Cows said:**
> ... java , C# are extremely slow languages. It all depends on what you feel comfortable with, but also remember this: High Level Languages are always slower. High Level meaning how easy the language is. C and C++ are mid-level. ASM is Low-Level. C# , Java is High Level. Correct me if I'm wrong.
Ok, I'll correct you. See above about the JVM. When a language is a high-level language, it does not automatically mean that it's slow. That depends on the compiler and the runtime environment. And Java isn't that much higher-level than C++.

> **nitro_n2o said:**
> Well... yes Java is SLOW..
It is not. Some implementations (such as GNU Java) are slow, but Sun's Java is not slow at all. There's no fundamental problem with the Java programming language that makes it slow.

Programming in Java is my job. Java is a very good and solid programming language that scales well to large and complicated projects. But it wouldn't be my first choice for writing small to mid-size desktop applications for Ubuntu - a language like Python would be more suitable for that. C# is almost the same as Java - the same concepts, the same kind of runtime environment etc.

---

### Post by hermes0710 on 2008-05-16
I think java is the way to go..........................................
.......................................................................
.......................................................................

---

### Post by LaRoza on 2008-05-16
> **Delever said:**
> 

**Applets** - the only choice is Java



**Applets** - You can use Tcl (Tclets) and you can use Python on the Java platform, even to make applets.

---

### Post by pmasiar on 2008-05-16
> **ivze said:**
> Either java, or C# are made so that the language make software more stabile (e.g. no direct memory management). 
The languages shall not be blamed for being slower (by the rate of 2-4 compared to C++, not 100-1000 times as Python). Write the same application in c++, and you will have a nice programm, that runs faster (just 4 times), but with lots of (---)8< in it =).

Python speed is a strawman. I just yesterday needed to analyze huge table for duplicities. SQL was not flexible enough, so I ended up doing part of processing in SQL, extracting report of results, and analyzing it in Python. Writing Python program took me about 10 minutes, it run once in seconds, and saved me couple hours of fighting with SQL. Writing such analyzing code in C or C++ would take substantially longer than 10 minutes, and resulting difference in running time is meaningless.

Python is fast enough for most tasks you will use it, because most task are IO bound: limit of speed are IO operations, database, user input, and not processing. And if you need to process big numerical tables, numpy uses exactly the same C libraries, just getting your code to work is 100 times simpler in Python.

I noticed slight variation of "script kiddies" - "speed kiddies". Kids without real life development experience, obsessed with the speed the program will run, without concern about how long it will take to develop the code and make inevitable changes in the future.

---

### Post by CptPicard on 2008-05-16
> **jespdj said:**
> JVM is a very sophisticated piece of software that compiles Java bytecode to native machine code on the fly, and so it runs quite fast - not much slower than C++.

+1 for this. I just today was experimenting again with some fairly intense numerical code... my Common Lisp implementation on SBCL, cool as it was (and as much as I tried to tune it), was like 2-3x slower than the Java one, and the Java one on the other hand has typically proven to be actually close to unoptimized gcc output in speed.

Most Java code is slow because memory allocation is not paid attention to. You can't just constantly spam the garbage collector with thousands of little objects and expect it not to have an effect. The actual generated assembly from the JIT compiler isn't bad at all :)

If there is anything I dislike about Java is that it lacks a lot of really cool features you find in higher-level languages (I find myself constantly trying to emulate closures by anonymous inner classes).. Java is maybe a little boring but I suppose you can't have everything. :(

---

### Post by winch on 2008-05-16
> **pmasiar said:**
> Python speed is a strawman. I just yesterday needed to analyze huge table for duplicities. SQL was not flexible enough, so I ended up doing part of processing in SQL, extracting report of results, and analyzing it in Python. Writing Python program took me about 10 minutes, it run once in seconds, and saved me couple hours of fighting with SQL. Writing such analyzing code in C or C++ would take substantially longer than 10 minutes, and resulting difference in running time is meaningless.

Using that logic you can just as easily do this.

> Lower time to write programs in Python is a strawman. I just yesterday needed to perform some execution speed critical action. Python was too slow therefore the time saved writing in python is meaningless.

---

### Post by LaRoza on 2008-05-16
> **winch said:**
> Using that logic you can just as easily do this.

No, I think pmasiar was pointing out that there are two times that have to ba balanced. Programmer time, and processor time. Finding out which is more important is what is the issue. For many programming tasks, speed of coding is more important.

This task:
> 
I just yesterday needed to analyze huge table for duplicities


Doesn't seem like a candidate for spending a lot of time coding.

Read [http://www.tcl.tk/doc/scripting.html](http://www.tcl.tk/doc/scripting.html)

---

### Post by sakabato on 2008-05-16
> **Delever said:**
> It's strange, although I said that I prefer C# as language, I would choose either of them depending of job, for example:

(if there is no requirement which one to use)

**Applets** - the only choice is Java

[http://www.go-mono.com/moonlight/](http://www.go-mono.com/moonlight/)

> **Delever said:**
> 
**Business application with centralized database** - if target platform is windows, I would prefer C# just because of streamlined IDE. However, there is the cost if you would want to use full version of MS SQL server. MySQL, however, is also possible. If you want to be portable, then Java. I used Interbase and MySQL with Java, and saw Oracle working successfully too. 
Speed is also quite trivial in such applications.


[http://www.mono-project.com/Database_Access](http://www.mono-project.com/Database_Access)

> **Delever said:**
> 
Mono may prove to be useful there. However, you can't use any assembly (.Net dll) witch begins with "Microsoft.*", like, Enterprise Library or Smart Client.
Java wins in portability.


Because there are only few assemblies starting with Microsft and no one in the .net world even uses Enterprise Library anymore


> 
**Web** - Lots of "technology" is coming for .Net here. They call "technology" any new piece of crap which is supposed to solve every problem. Basically, in .Net, if you write single line of code, it is wrong way of doing it, because probably Microsoft already created component for that. All you need to do, is to download new free code, edit few dozens of configuration files correctly, create aspx templates correctly, and you have it! Everything just... works? Nope. You end up writing code which makes it work. Invoking private functions of those components using replication. Nasty work, and no freedom. And good luck hosting it on server with .Net framework 3. Of course, you can use generic handlers to write web server output (HTML) directly, and no way of reusing ASP.NET components in them, because ASP.NET can only be used with ASPX form templates.


Incorrect, ASP.NET is the general name for http pipeline technology. An alternative to aspx form templates is [http://www.castleproject.org]("http://www.castleproject.org")

> 
I am not very familiar with Java side, but there you have almost the same story: you can write handlers, or, possibly, use Java Server Pages (JSP). However, you have hosting on Apache with Tomcat - with much lower costs.
So - what I would choose for web programming? PHP :D.... erm... from those two - .... (thinking) ... ok. Java.


ASP.NET Applications work with Apache too:[http://www.mono-project.com/Mod_mono]("http://www.mono-project.com/Mod_mono")
> 
**Game programming** - Again, like with any other choice (possible exception - simple applications), mono is not really a choice yet if you want portability. You can use XNA for game programming with C#, or managed DirectX. XNA is really easy, C# proves to be fast there (you can do enough things even every frame), it requires at least pixel shader 2.0, and everything is done using shaders (HLSL). Managed DirectX is not maintained enough, and year ago there were rumours it may be canceled.
Java, however, can work with OpenGL, and I guess it would be much more portable solution (I have not tried it yet).
So, if I need some accelerated rendering and target platform is Windows, I would go with Xna, otherwise - I would check Java (more likely python or C++).


OpenGL , SDL framework for C#/mono/linux:[http://www.taoframework.com/]("http://www.taoframework.com/")

Cross platform 3-D engine working on mono: [http://axiomengine.sourceforge.net/wiki/index.php/Main_Page]("http://axiomengine.sourceforge.net/wiki/index.php/Main_Page")

> 
**Network tools** - Again, better tools in C# (like WCF), require .Net3, and that means it's unportable (mono still in progress). Java there seems much more stable and consistent across platforms (I would hope).


Incorrect! Here is WCF for mono:[http://www.mono-project.com/WCF]("http://www.mono-project.com/WCF")
Also another and better cross platform networking framework:
[http://www.indyproject.org/index.en.aspx]("http://www.indyproject.org/index.en.aspx")

> 

Ok, I guess it is enough - this is very biased review based on my subjective experience. If you want more information about some things (I may know about Java servlets/Xna/.Net3/ASP.NET) just ask.

So, after this review, it seems that Java actually have more possibilities on GNU/Linux. Of course.
 

please try to make more research. Here is the entire libraries supported by mono :

[http://www.mono-project.com/Libraries]("http://www.mono-project.com/Libraries")
I hope someone will find something useful in this post.[/QUOTE]

As a language there are better languages than C# for mono and .net 
like :
[http://boo.codehaus.org/]("http://boo.codehaus.org/")
[http://nemerle.org/Main_Page]("http://nemerle.org/Main_Page")

---

### Post by Delever on 2008-05-16
> **sakabato said:**
> [http://www.go-mono.com/moonlight/](http://www.go-mono.com/moonlight/)



[http://www.mono-project.com/Database_Access](http://www.mono-project.com/Database_Access)



Because there are only few assemblies starting with Microsft and no one in the .net world even uses Enterprise Library anymore




Incorrect, ASP.NET is the general name for http pipeline technology. An alternative to aspx form templates is [http://www.castleproject.com]("http://www.castleproject.com")



ASP.NET Applications work with Apache too:[http://www.mono-project.com/Mod_mono]("http://www.mono-project.com/Mod_mono")


OpenGL , SDL framework for C#/mono/linux:[http://www.taoframework.com/]("http://www.taoframework.com/")

Cross platform 3-D engine working on mono: [http://axiomengine.sourceforge.net/wiki/index.php/Main_Page]("http://axiomengine.sourceforge.net/wiki/index.php/Main_Page")



Incorrect! Here is WCF for mono:[http://www.mono-project.com/WCF]("http://www.mono-project.com/WCF")
Also another and better cross platform networking framework:
[http://www.indyproject.org/index.en.aspx]("http://www.indyproject.org/index.en.aspx")

 

please try to make more research. Here is the entire libraries supported by mono :

[http://www.mono-project.com/Libraries]("http://www.mono-project.com/Libraries")

As a language there are better languages than C# for mono and .net 
like :
[http://boo.codehaus.org/]("http://boo.codehaus.org/")
[http://nemerle.org/Main_Page]("http://nemerle.org/Main_Page")

You know your side of story, I know mine. I did not want to create language war.

---

### Post by claudio99 on 2008-05-18
If you like Free Software and Linux: Java, without a doubt.

Why?
- Java is **Free Software** (most of it already released under the GPL), while C#/.Net is in the hands of Microsoft and most of the libraries are covered by patents and other MS tricks. Mono is a nice copycat, but as a copycat completely dependent on the goodwill of Microsoft for their implementation. Do we really want to take that risk?
- You use Linux, clearly a minority OS. That's why it's not bad to know a **platform independent** language so your knowledgde is valid on e.g. Windows and Mac. Java is a true platform independent language while .Net is Windows only.
- A lot of open and commercial libraries exist for Java and [**netbeans**]("http://www.netbeans.org") is great  Free java IDE and there is a lot of **great documentation and books** to learn and use the language.

C.

PS: If you want to program gnome apps you should have a look at perl + gtk2-perl. If you throw glade into the mix it gets very easy to write small applications.

---

### Post by Frak on 2008-05-18
I would say both.

Java for its portability and ease of use.

C# as its also a very simple language and gaining more ground in general application and web markets.

EDIT
For XNA game studio (360 and Microsoft Zune products) C# is a MUST.

---

### Post by gareth_005 on 2008-05-18
I have worked with centura, cobol, basic, pascal, vb, c, c++, c# and some others.
I have only ever created one java app and did not like java so I will try not to compare the two.

I have found the C# language to be a very clear language compared to the other languages I have used.
If you take the time to read and follow the standards and best practices (Not only the microsoft ones) you can write very neat code in C#.

With large projects, it is very easy to split your code into separate libraries. Namespaces across libraries works well and is intuitive.
I have been using the open source SharpDevelop ide for the last 3 years. For forms applications it offers about the same functionality as Visual Studio (This is the only thing I still use WindowsXP in VirtualBox for).
I have started using MonoDevelop on and off for the last 2 months, yesterday I worked through some gtk tutorials for gtk forms and I may soon convert to using gtk forms in future.
I like win forms and have been using them for 10 years but I think that after I have learnt how to use gtk I will probably prefer them as the way they are designed seems clearer and neater (Still deciding).

I do not like most microsoft products but I think that they did a good thing with .net.
I have had a look over some of the libraries available with mono and I think that mono actually has a larger library base the the microsoft implementation.

From one of my simulation apps (((175000 lives * +-5 benefits each) * 3 random numbers per benefit) * 1000000 simulations) = about 4.5 hours on windows.
I have seen that mono on linux runs at about half of the speed of the same app running in xp.
The same app written in c++ running on windows was aiming for 20 hours (The random number generation is the killer in this app at 2,625,000,000,000 random doubles).

Whichever language you choose, have fun.

---

