---
title: "C#? Mono??? .Net in linux? What a world!"
date: 2006-07-16
forum: Programming Talk
---

### Post by Nexusx6 on 2006-07-16
Hello :) 

I come to you oh Programming Talk forums for some much needed help :( 

I am an ex-visual basic, ex-windows user who's recently switched to Ubuntu (and loving it) and really itching into getting back to programing; So I do my homework and I'm thinking Python is the language for me until I run across a thread that talks about C# and some weird little thing call Mono.

"C#, in Linux? .NET? Huh??" I'm rather confused by this but as the posts go on it really seems like C# and 'Mono' are becoming the new things in Linux, and sounds like a great portable language (My WinXP friends have yet to see the light).

But like I said, I'm throughly confused. Does Mono mean that I can go to Barnes and Nobles and pick up any Learn C# book and have the same code in that book work in Linux? Does using Mono need its own 'How-to' booklet? In VB, making a GUI app was childs play.. is it difficult in C#? Is C# in general a pretty hard language to learn like C++?

I apreciate all reply's and help b(^^)

---

### Post by Daverz on 2006-07-16
I think you're going to be disappointed if you're expecting anything like the VB environment.  

As for C# books, just avoid Visual .NET specific ones.  Also, Gtk# is the default toolkit for mono development on Linux (as opposed to WinForms).  It can be used from any of the mono languages (which, BTW, includes IronPython, an implementation of Python).  This book

[http://www.amazon.com/gp/product/0596007922](http://www.amazon.com/gp/product/0596007922)

has an intro to Gtk#.  Of course, you can also use Gtk from "regular" Python.

---

### Post by Note360 on 2006-07-16
Visual Basic is also supported by Mono though not completely. Most C# books only concern dotNet but the basics are the same most of the GUI stuff is different. Here is my suggestion
[URL="http://www.mono-project.com/Main_Page"]
Go here [/URL] and read on mono.

Then go to Synaptic and download Mono and MonoDevelop (the IDE)

Next, find a tutorial or book.
Here is a list of books with a review: [http://lists.ximian.com/pipermail/mono-list/2003-January/011066.html](http://lists.ximian.com/pipermail/mono-list/2003-January/011066.html)

---

### Post by Oler1s on 2006-07-17
> Is C# in general a pretty hard language to learn like C++? 
It makes boring tasks easier. C++ is hard because you have to work with everything. GUI gets even worse.

C# takes care of all the annoying details, and allows you to focus on writing the meat of the application. I found learning C# easier than C++.

---

### Post by mostwanted on 2006-07-17
C# feels like a revised Java where all the obsolete junk collected over time is thrown out and classes have been renamed to make it more in tune with other languages.

Monodevelop comes with a visual GUI builder (Gtk#-based) which is very alpha at the moment, but it's there nonetheless. When Monodevelop some day becomes less buggy, maybe it will be a piece of cake. You can also use Glade which is a largely language independant GUI builder (also Gtk+ which = Gtk# when used in conjunction with Mono).

---

### Post by LordHunter317 on 2006-07-17
> **Oler1s said:**
> It makes boring tasks easier.Not really.  It makes some boring tasks eaiser.  The problem is that the .NET framework is so poor that when you want to do a boring task it doesn't cover, it becomes order-of-magnitude harder to do.

You have to design your application to the framework in a lot of situations, which is just a really poor state to be in.

> C++ is hard because you have to work with everything.I'm not sure what you mean.

>  GUI gets even worse.Not really, if you're using a good toolkit.

[quote=mostwanted]C# feels like a revised Java where all the obsolete junk collected over time is thrown out and classes have been renamed to make it more in tune with other languages.[/quote]Well, yes and no.  MS did crib from Java in several ways, there's little question about that.  The problem with C# is that the /language/ is superior in many ways to Java (and actually inferior in a few others), but the basic library is incredibly inferior.

---

### Post by mostwanted on 2006-07-17
Well, I disagree :)

---

### Post by GeoMX on 2006-07-17
I'm learning C++ (I've been programming with C) and wxWidgets, but wanted to take a look at C# + Mono.

I installed monodevelop (from the repositories), and compiled the simple console application (the one monodevelop creates automatically), but when adding **using System.Drawing;** I got this compiler error:

> 
[Task:File=~/Projects/monotest/monotest/Main.cs, Line=3, Column=1, Type=Error, Description=The type or namespace name `System.Drawing' could not be found. Are you missing a using directive or an assembly reference?(CS0246)


Do you know what do I need to do in order to make mono recognize the System.Drawing namespace? Do I need to install another package?

Thanks for your help.

---

### Post by LordHunter317 on 2006-07-17
> **mostwanted said:**
> Well, I disagree :)Go look at System.Collections vs. the JCF and get back to me on that.

---

### Post by LordHunter317 on 2006-07-17
As for GeoMX's problem, you probably need to add '/r:System.Drawing.dll' to the command line.  System.Drawing is in a seperate library, and you have to tell the compiler to link to it.

---

### Post by Oler1s on 2006-07-17
> Not really.  It makes some boring tasks eaiser.  The problem is that the .NET framework is so poor that when you want to do a boring task it doesn't cover, it becomes order-of-magnitude harder to do.

What sort of boring task are you referring to? I think the .NET framework is excellent.

> You have to design your application to the framework in a lot of situations, which is just a really poor state to be in.

Why is that? How is this different from C++, where you have to design your application to the standardised STL, Boost, or some other non standardised library? How is this different where you have to conform with a toolkit?

Designing an application to a framework can actually be beneficial. Because the framework is standardised, you know what to expect when looking at someone else's C# code.

> I'm not sure what you mean.

Memory has to be properly allocated and deallocated. Unicode is a mess. The same can be said for strings.

> Not really, if you're using a good toolkit.

Fair enough. Although, it seems odd to complain about conforming to the .NET framework, and then espouse a toolkit.

> MS did crib from Java in several ways, there's little question about that.  The problem with C# is that the /language/ is superior in many ways to Java (and actually inferior in a few others), but the basic library is incredibly inferior.

More like MS took the best of Java, C++, added features, and ended up with C#. Thankfully, we also have the Mono project.

So your issue with C# is the basic library (read: .NET framework)? Well, that's an interesting topic for another thread ^_^

---

### Post by GeoMX on 2006-07-17
> **LordHunter317 said:**
> As for GeoMX's problem, you probably need to add '/r:System.Drawing.dll' to the command line.  System.Drawing is in a seperate library, and you have to tell the compiler to link to it.
Thanks for the answer, it works. Also, you can use -r: instead of /r: :). I had to compile the file from the command line, I can't find an option in monodevelop to add this instruction when calling the compiler (I guess it should do it automatically, but it's not doing so).

Regards,
JJ (GeoMX).

---

### Post by LordHunter317 on 2006-07-17
> **Oler1s said:**
> What sort of boring task are you referring to? I think the .NET framework is excellent.Any task related to collections that doesn't involve enumeration.  The collections are so fundamentally broken you have to recode everything.

They didn't go back and actually use generic where appropriate (even if they kept the old methods).  Virtually all my ASP.NET code is litered with 2/3 assigments at the start of every method to cast things to the correct type.

The ASP.NET membership stuff, if you need to extend it, is a bloody nightmare.


> How is this different from C++, where you have to design your application to the standardised STL, Boost, or some other non standardised library?By and large, most of the constraints the STL puts on you are invariants: you'd have to met them no matter what.  That's not to say there aren't annoying limitations in C++, they're just less common.  

> Memory has to be properly allocated and deallocated.Resource have to still be allocated and deallocated in C#, which is just as (if not more) important and still dealt with in essentially the same ways.

> Although, it seems odd to complain about conforming to the .NET framework, and then espouse a toolkit.The point is, the good GUI toolkits for C++ are of better quality and far less limiting in nature than SWF.

> More like MS took the best of Java, C++,They didn't take a single thing from C++ Java hadn't already.

> So your issue with C# is the basic library (read: .NET framework)?Yes, the issue is principally with the library.

---

### Post by GeoMX on 2006-07-18
> **GeoMX said:**
> Thanks for the answer, it works. Also, you can use -r: instead of /r: :). I had to compile the file from the command line, I can't find an option in monodevelop to add this instruction when calling the compiler (I guess it should do it automatically, but it's not doing so).

In the solution explorer, right click and select Edit References..., sorry for not seeing it before :P.

Regards,
JJ (GeoMX).

---

### Post by HolyJoe on 2006-07-19
oh, c# is elgant and simpler than c++, and more like java.

If u want to learn c#, u can download ECMA-334 to getting start.

---

### Post by cruizer on 2006-07-19
well Java doesn't have pointers and operator overloading. The latter is available in C# and pointers can be used in "unsafe" or "unmanaged" code sections.

.NET also introduced innovations that Java didn't have before (and they're including them now).

of course it doesn't mean that since it's there you have to use it. but it sure feels good that i can use it should i have the need to do so in the future...

---

### Post by LordHunter317 on 2006-07-19
> **cruizer said:**
> well Java doesn't have pointersYes, it does.  Java "references" are pointers.  They behave like pointers and have pointer semantics.  

> The latter is available in C# and pointers can be used in "unsafe" or "unmanaged" code sections.ITYM "former", but unmanaged C# pointers are different.

C# also has and strictly uses pointers for all non-value types.

---

