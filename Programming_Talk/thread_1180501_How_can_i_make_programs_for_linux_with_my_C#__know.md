---
title: "How can i make programs for linux with my C#  knowledge?"
date: 2009-06-06
forum: Programming Talk
---

### Post by xZachtmx on 2009-06-06
Ok i jsut got ubuntu 9.04 and its amazing! and id love to develop software for it.  I have a c# knowledge and i was just wondering if there was an equivalent of microsoft's visual C# express for linux?

---

### Post by incubii on 2009-06-07
Hi xZachtmx, I would suggest you take a look at [Monodevelop](http://monodevelop.com/). It is a C#/Mono IDE you can use to develop your .NET applications for Linux.

> 
MonoDevelop is an IDE primarily designed for C# and other .NET languages. MonoDevelop enables developers to quickly write desktop and ASP.NET Web applications on Linux. MonoDevelop makes it easy for developers to port .NET applications created with Visual Studio to Linux and to maintain a single code base for all platforms.


---

### Post by directhex on 2009-06-07
C# knowledge allows you to be a productive & valuable Free Software developer. For a couple of example apps, look at F-Spot, Banshee, Tomboy, GNOME Do.

You want to install the monodevelop package, which is an IDE. It should pull in mono-devel automatically, which has things like the compiler (gmcs) in it. MonoDevelop has an integrated GUI designer, for GTK# (not WinForms).

And the thing you're gonna ask, before you ask it: because GTK is container based, not pixel based. You need to use container widgets (HBox, VBox, Table, etc) and place widgets like buttons inside the containers. Think <table> on a web page.

---

### Post by xZachtmx on 2009-06-07
ok i got monodevelop (automaticly installed when i clicked the ubuntu download.) now where do i find it? :D  dosent seem to be on a menu

---

### Post by fr4nko on 2009-06-07
If you have installed monodevelop correctly you should see it under Applications -> Programming, it is not so difficult.

Otherwise, talking about C# development, Tomboy is a good example of what you can have with C#, a bloated programs that use tons of memory to do a very simple task. I've uninstalled this program and forget about it a long time ago.

Your C# knowledge is what Microsoft want you to learn as programmer.

I'm happy that KDE and Gnome are not built with C# otherwise it will be a nightmare in terms of memory usage, slowness and startup time. Learn C and C++, it is much more useful. As higher level programming language you can learn Python or if you are versed for mathematics you will love OCaml.

Francesco

---

### Post by xZachtmx on 2009-06-07
i know pytyhon as well :) i just like c#

---

### Post by directhex on 2009-06-07
> **fr4nko said:**
> If you have installed monodevelop correctly you should see it under Applications -> Programming, it is not so difficult.

Otherwise, talking about C# development, Tomboy is a good example of what you can have with C#, a bloated programs that use tons of memory to do a very simple task. I've uninstalled this program and forget about it a long time ago.

Your C# knowledge is what Microsoft want you to learn as programmer.

I'm happy that KDE and Gnome are not built with C# otherwise it will be a nightmare in terms of memory usage, slowness and startup time. Learn C and C++, it is much more useful. As higher level programming language you can learn Python or if you are versed for mathematics you will love OCaml.

Francesco

I love how people always recommend Python, despite it being up to 60x slower, and usually much more RAM-hungry, than Mono

---

### Post by fr4nko on 2009-06-07
I've recommended python ***and*** C/C++ because I know that python is slow. Python will always be slow because is interpreted and everything is determined at run-time including the type of any object.

I guess mono is faster because is compiled and is a typed programming language.

In any case I don't want to be misunderstood, I don't mean that C# is bad. I simply mean that I don't like the idea (a java like programming language) and it is not among the tool of choice for my developments. I plan to try C# to see how it works but I guess I will never adopt this programming language and the mono environment in general.

So, don't be angry with me :-)

Francesco

---

### Post by ajackson on 2009-06-07
> **fr4nko said:**
> I plan to try C# to see how it works but I guess I will never adopt this programming language and the mono environment in general.
If you try something with the attitude that you won't like it then chances are you won't like it, no matter how good it may/may not be. If you go with an open mind then you will give the language a fair chance of appealing.

> **fr4nko said:**
> So, don't be angry with me :-)
You have a pre-conceived idea of what a language can do, you've damned it before trying and now are giving ill-informed opinions to someone asking a genuine question.

---

### Post by Yacoby on 2009-06-07
> **directhex said:**
> I love how people always recommend Python, despite it being up to 60x slower, and usually much more RAM-hungry, than MonoBecause when looking at a language to chose for a task the only thing I am interested in is RAM usage and speed.

Not much can beat C/C++ in terms of speed and memory usage but 95% of the time it [C++] is the wrong language for the application. It is just too slow ,[and] too complex to develop with.

Regarding language choice, 99% of the time I found python was fast enough and its memory usage wasn't a concern. The other 1% of the time I was using C++, because C# would have been to slow as well.

From my perspective, Python looks a much nicer language to get started with compared to something like C#, which is why I will continue to recommend it over C# and my current language interest.



Having said that, ignoring MS issues (lets not go there), C# is a great language, is fast enough for 99% of tasks. Bashing a language without any reasoning, understanding isn't a good thing to do, especially when it is unrelated to the question itself.

> a java like programming language
C++ is fairly Java like, yet you recommend that. Arguably C++ is far worse a language to program in than Java and C#

---

### Post by leblancmeneses on 2009-06-07
>Not much can beat C/C++ in terms of speed and memory usage but 95% of the time it is the wrong language for the application. It is just too slow, too complex to develop with.

sorry you also have to consider speed to develop of an application also. A program written in c# with visual studio can be completed is a shorter period of time then with traditional c/c++ tools.

Also mono compiler has switches which allow the application to be compile to elf executable rather than running in CLI-compliant vm's.

I couldn't find Miguel's post on the topic but here is one of the switches [I]--aot 
which creates a shared library .so

if you're interested research [/I]Cecil.FlowAnalysis  and compiler backend because i've seen videos on creating elf format.

[http://tirania.org/blog/archive/2008/Nov-03.html](http://tirania.org/blog/archive/2008/Nov-03.html)  gives speed comparison and cutting edge topics.

so c/c++ speed is a dying myth.

---

### Post by ajackson on 2009-06-07
> **leblancmeneses said:**
> >Not much can beat C/C++ in terms of speed and memory usage but 95% of the time it is the wrong language for the application. It is just too slow, too complex to develop with.

sorry you also have to consider speed to develop of an application also.
Read the bit you quoted (preceded with a > ) then read the bit I quoted, see if you can spot the mistake :)

Speed is relative and subjective, something require quick processing speeds, some don't. If application *A* runs 2 times faster than application *B* but takes twice as long to develop, which is faster? Many would argue *A* but if it took 6 months to develop *B* and runs in 4 seconds, would people wait for *A* to be developed?

---

### Post by Yacoby on 2009-06-07
> **leblancmeneses said:**
> sorry you also have to consider speed to develop of an application also. A program written in c# with visual studio can be completed is a shorter period of time then with traditional c/c++ tools.
That was covered with the "[C++ is 95% of the time] Too slow, too complex to develop with [to make the possible speed increase worth it]" bit. (Square brackets added to clarify meaning)

> **leblancmeneses said:**
> so c/c++ speed is a dying myth.
Last time I checked, C/C++ was still up at the top as far as speed goes. It will be interesting to see when it is beaten.(Notice how most major game engines are still written in C++). 

You have to know what you are doing much more to get a fast C/C++ code as well, and as mentioned, 95% of programs I write don't have enough of a speed difference between C++/C/C#/Java/Python/Lisp/Haskell for the speed to make any difference to my choice in language.


The comparison you linked to unfortunately doesn't seem to compare a C# SIMD version to a C++ SIMD version, which makes the benchmarks very questionable in regards to speed comparisons. (But interesting none the less)

---

### Post by fr4nko on 2009-06-07
> **Yacoby said:**
> C++ is fairly Java like, yet you recommend that. Arguably C++ is far worse a language to program in than Java and C#

Well, you are touching a sensitive point. You're saying that C++ is a Java like programming language. This is not really true IMHO because in C++ you can have many different way of programming. You can use it just like an improved procedural language of you can use object-orientation but in many different flavors. To be more clear, you can use (or not):

[LIST]
[*]virtual methods against ordinary methods
[*]virtual base classes (to define interfaces like in java, for example)
[*]multiple inheritance
[*]templates
[/LIST]
Also C++ is basically different from Java because it compiles directly to machine code and no garbage collection is made by default. So in C++ you can write programs that executes very fast with a small memory footprint.
For the other side, I've to say that I don't specially like C++. I like a lot C because of its simplicity and because it gives full control on every detail. My feeling with C++ is that it does have too much features and some are designed the wrong way. For example multiple inheritance is a nightmare in term of implementation and understanding, you can have something better with Objective C or Java by using simple inheritance and protocol/interfaces (whatever name you prefer). By the way I believe that's the same choice that has been made with C#.
In many cases with C++ is very difficult to guess what the compiler does with a given statement because of operator and function overloading, default parameters, automatic constructor invocations, etc. etc.

So, I've made a small digression, but I love to talk about this kind of subject :-)

Francesco

---

### Post by phrostbyte on 2009-06-08
Try the language Boo also. It's like Python for .NET programmers. It's very good, and in my opinion better then C# (more concise). It runs on Mono/CLR.

---

### Post by johnhlong on 2009-06-16
I'm new to Linux so my question may seem strange.
 
Will MonoDevelop compile C# to a program that will run nativaly under ubuntu?
 
It may not be the best choice but I have some personal C# programs that I would like to run nativally under ubuntu.
 
 
Thanks,
John

---

### Post by Zugzwang on 2009-06-16
> **johnhlong said:**
> Will MonoDevelop compile C# to a program that will run nativaly under ubuntu?


Depending on what you consider to be "running natively", the answer is likely to be "no". But that applies to Windows as well!

.net framework programs are always interpreted or compiled on-the-fly at runtime. Under Windows, you just don't see it because there's a Windows-only stub in each compiled file automatically starting the .net environment if needed. Under linux, type "mono <yourexe.exe>" to run the program. But this is really not a problem.

---

### Post by directhex on 2009-06-16
> **johnhlong said:**
> I'm new to Linux so my question may seem strange.
 
Will MonoDevelop compile C# to a program that will run nativaly under ubuntu?
 
It may not be the best choice but I have some personal C# programs that I would like to run nativally under ubuntu.
 
 
Thanks,
John

You don't actually need to even recompile, assuming you don't have any silly P/Invokes. CIL code (.NET exe files) are cross-platform, and will run on any CLR (framework, e.g. Mono or Microsoft.NET) that has the libraries you reference. This includes WinForms apps - they look like crap, but they'll run as "natively" as F-Spot does, directly via Mono.

---

