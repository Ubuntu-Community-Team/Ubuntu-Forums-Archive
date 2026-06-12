---
title: "C# in Ubuntu"
date: 2012-02-15
forum: Programming Talk
---

### Post by Arukas on 2012-02-15
Is there any reason one would want to program in C# for ubuntu?  I don't see C# bring anything to the table when the OS is Linux.  C# seems to be optimize for taking advantage of the .NET framework and none of that is on the linux side, unless I am wrong.  (and this wouldn't be the first time)

I'm not asking which language is better.  I'm just trying to find if there are any benefits for using C#.  

-Arukas

---

### Post by FamousAmos on 2012-02-15
I don't know that there any benefits compared to C++, unless you're just more comfortable with C#.  I'm not a C# expert, there may be other benefits as well.  There is C# from MonoDevelop, which works on Linux while maintaining the C# API you'd have with .NET.

---

### Post by Arukas on 2012-02-15
I thought the .NET stuff didn't work in linux, or am I mistaken?

---

### Post by FamousAmos on 2012-02-15
It doesn't.  My understanding is that MonoDevelop for Linux is a port of the .NET API.

---

### Post by HotCupOfJava on 2012-02-16
The MonoDevelop project isn't the .NET framework per se, but it does act as a virtual machine on Linux for languages that normally run on .NET. It is a little behind current .NET implementations, though. 

I believe Tomboy Notes was written in C# using Mono, so it is viable for some practical application development.

But hey, why not just use Java? It is very similar to C#, but has fewer portability issues (not that I'm biased or anything):D.

---

### Post by nebukadnezzar on 2012-02-17
> **FamousAmos said:**
> It doesn't.  My understanding is that MonoDevelop for Linux is a port of the .NET API.

Not really. Mono is a total reimplementation of .NET **from scratch**, available for Windows, Mac and Linux.

---

### Post by qeemat on 2012-02-17
Advantages over C and C++
It is compiled to an intermediate language (CIL) indepently of the language it was developed or the target architecture and operating system
Automatic garbage collection
Pointers no longer needed (but optional)
Reflection capabilities
Don't need to worry about header files ".h"
Definition of classes and functions can be done in any order
Declaration of functions and classes not needed
Unexisting circular dependencies
Classes can be defined within classes
There are no global functions or variables, everything belongs to a class
All the variables are initialized to their default values before being used (this is automatic by default but can be done manually using static constructors)
You can't use non-boolean variables (integers, floats...) as conditions. This is much more clean and less error prone
Apps can be executed within a restricted sandbox

---

### Post by directhex on 2012-02-17
> **Arukas said:**
> Is there any reason one would want to program in C# for ubuntu?  I don't see C# bring anything to the table when the OS is Linux.  C# seems to be optimize for taking advantage of the .NET framework and none of that is on the linux side, unless I am wrong.  (and this wouldn't be the first time)

I'm not asking which language is better.  I'm just trying to find if there are any benefits for using C#.  

-Arukas

Why wouldn't you? It's a nice clean language, on top of a well-balanced framework. Performance is orders of magnitude better than Python, RAM usage is orders of magnitude lower than Java. Only political ******** from anti-Microsoft fanatics stopped it getting the popularity that it deserves, compared to toys like Vala

---

### Post by directhex on 2012-02-17
> **Arukas said:**
> I thought the .NET stuff didn't work in linux, or am I mistaken?

.NET stuff is bytecode based, like .class in Java.

Stuff compiled with Mono or with MS.NET produces the same bytecode. You can compile apps on MS.NET and run them on Ubuntu, and vice versa

---

### Post by Arukas on 2012-02-17
> **qeemat said:**
> Advantages over C and C++
It is compiled to an intermediate language (CIL) indepently of the language it was developed or the target architecture and operating system
Automatic garbage collection
Pointers no longer needed (but optional)
Reflection capabilities
Don't need to worry about header files ".h"
Definition of classes and functions can be done in any order
Declaration of functions and classes not needed
Unexisting circular dependencies
Classes can be defined within classes
There are no global functions or variables, everything belongs to a class
All the variables are initialized to their default values before being used (this is automatic by default but can be done manually using static constructors)
You can't use non-boolean variables (integers, floats...) as conditions. This is much more clean and less error prone
Apps can be executed within a restricted sandbox


I understand the differences between C and C#, but not what I am asking.  (Personally I don't like the hand holding but that's a different story)  The part I'm not clear about is does it lose functionality because its not in a windows environment. 

I could of asked my question like this, which is most worth while in Linux:  Java or C#?  I been reading C# books, and from my first impression C# doesn't seem to have a place in Linux.  




 

the part I'm not clear on is does it lose functionality when it comes over to the linux side.

---

### Post by doobrie on 2012-02-17
> **Arukas said:**
> I understand the differences between C and C#, but not what I am asking.  (Personally I don't like the hand holding but that's a different story)  The part I'm not clear about is does it lose functionality because its not in a windows environment. 

I could of asked my question like this, which is most worth while in Linux:  Java or C#?  I been reading C# books, and from my first impression C# doesn't seem to have a place in Linux.  
 

the part I'm not clear on is does it lose functionality when it comes over to the linux side.

I don't see why C# shouldn't have a place on Linux.  If you're familiar with C# programming, then why should you be restricted to programming on Windows?

I agree there aren't many books teaching you how to program in C# on Ubuntu, but I don't think this should stop you developing C# on Ubuntu if that's what you like.

---

### Post by JDShu on 2012-02-17
> **directhex said:**
> .NET stuff is bytecode based, like .class in Java.


This is probably the most technically interesting answer. VMs are useful, and right now the only two significant VMs are the JVM and the CLR. C# is also a more powerful language than Java, which gives it an edge.

---

### Post by Arukas on 2012-02-17
> **doobrie said:**
> I don't see why C# shouldn't have a place on Linux.  If you're familiar with C# programming, then why should you be restricted to programming on Windows?

I agree there aren't many books teaching you how to program in C# on Ubuntu, but I don't think this should stop you developing C# on Ubuntu if that's what you like.

From reading the books, C# seems to be designed to work on window devices.  While that includes many devices, Linux isn't windows.  This is where I get the impression that it wouldn't work as good in Linux.  

While I am well versed in C++, I'm still learning the C# and I don't get the jargon. 

The reason, I asked the question is I wanted to know if C# was worth pursuing in Linux, and it looks like it is worthwhile.  

-Thanks

---

### Post by Dragonbite on 2012-02-17
All things considered, C# and Java both have the advantage of being (true) cross-platform.  (*I say "true" cross-platform because it includes Windows, Mac and Linux. Microsoft and Apple use "cross platform" meaning Windows and Macs only.*)  I think they can also both go onto smartphones.

I can't speak of the technical advantages but I do notice that C# (Mono) applications look better in Gnome than Java applications I have come across.  I think this is due to the Gtk#.

To see some of the C# (Mono) applications for Linux you can look at Banshee, Tomboy, F-Spot, Gnome-do and [s]some "brainy" game[/s] gBrainy.

C# has and the familiarity advantage for me, but that isn't a technical benefit and it doesn't matter to anybody but myself.

---

### Post by HotCupOfJava on 2012-02-17
> VMs are useful, and right now the only two significant VMs are the JVM and the CLR. C# is also a more powerful language than Java, which gives it an edge. 

OK, I admit I'm Java-biased (see handle), but I must take issue with a couple of things here:

-The C# virtual machine on Ubuntu is NOT the CLR, and the Mono environment is NOT up-to-speed with the current .NET framework.

-For a language that is so similar to Java, I must wonder how one thinks C# is more powerful, hmm? Power can mean many things, of course...

-Perhaps I should point out that Scala and Clojure also run on the JVM and can easily integrate with existing Java classes. If anyone reading this is a Java programmer and you haven't looked into these two languages yet, I strongly encourage you to do so. Scala's handling of concurrent threads is superb, and Clojure's meta-programming abilities will blow your mind. Both languages' handling of collections and/or sequences are a vast improvement over the Java/C#-style collections.

---

### Post by Simian Man on 2012-02-17
> **HotCupOfJava said:**
> -The C# virtual machine on Ubuntu is NOT the CLR, and the Mono environment is NOT up-to-speed with the current .NET framework.
That is not really true.  Mono is quite up to date with the .NET framework.  There are some small things that are missing, but there are also libraries you can use on Linux with Mono that you can't use on Windows with .NET.  I'm sick of people just repeating this nonsense that Mono is behind or crippled in some way.  It's a great programming environment on any platform and anyone who's used it at all would know that.

> **HotCupOfJava said:**
> -For a language that is so similar to Java, I must wonder how one thinks C# is more powerful, hmm? Power can mean many things, of course...
It has many more language features: unsigned numbers, stack types, tuples, properties, operator overloading, delegates and more.

> **HotCupOfJava said:**
> -Perhaps I should point out that Scala and Clojure also run on the JVM and can easily integrate with existing Java classes...
He didn't say anything about Scala or Clojure.  Mono and .Net also have other more advanced  languages targeting it such as F#, Nemerle, Boo etc.  That's irrelevant to the discussion of Java vs. C#.

---

### Post by CryptAck on 2012-02-17
> **HotCupOfJava said:**
> 

-For a language that is so similar to Java, I must wonder how one thinks C# is more powerful, hmm? Power can mean many things, of course...


On Windows, I do believe C# to be superior. With C#, Microsoft had the ability to see what did and didn't work for Java.

Things I believe to be better, 
[list]
[*]Windows Presentation Foundation (WPF)
[*]Operator overloading 
[*]Ability to write "unsafe" code.
[/list]

Obviously, my points have nothing to do with performance. I've never actually compared the two. 

On Linux, I have limited knowledge on Mono. If I were going to write an application, I think I'd side with Java, just because I have the perception that it'd be better supported than C#.

---

### Post by HotCupOfJava on 2012-02-18
> **Simian Man said:**
> I'm sick of people just repeating this nonsense that Mono is behind or crippled in some way.  It's a great programming environment on any platform and anyone who's used it at all would know that.


Didn't say it was crippled - you'll notice in an earlier post I pointed out that Tomboy Notes was developed in C# and said that Mono was a viable development platform. Upon reflection I believe that portability issues between .NET and Mono were my frame of reference.

You ARE correct in that I have not used C# on .NET or Mono, so I cannot and do not speak from personal experience. That assumption I made regarding the implementation of Mono versus .NET is based entirely on reviews by people who have used C# on both. Like you, they noted that the most recent language features available on .NET have yet to be implemented on Mono. That stands to reason. Is that serious or significant? Probably not.

Apparently I am not familiar with the abstractions available to C# programmers. I had always assumed that it was just "Microsoft's Java". I did take into consideration that perhaps the poster was referring to higher-level abstractions when he mentioned C# being "more powerful". That is why I mentioned Scala and Clojure - because of the seamless integration with Java, they serve as much higher-level abstractions to the language - I would even suggest that they were developed to supply such features to frustrated Java programmers. But I am just trying to explain myself, not disagree with you.

If you perceived me as trying to poo-poo on C#, you have my apologies. I am NOT familiar enough with C# to critique it. And, I am painfully aware of Java's shortcomings - Scala and Clojure have been a breath of fresh air for me.

With regards to the other languages targeting .NET and Mono - I am not at all familiar with those. You have made me curious.....

---

### Post by directhex on 2012-02-18
> **HotCupOfJava said:**
> Like you, they noted that the most recent language features available on .NET have yet to be implemented on Mono.

The reverse is usually the case. Mono is typically ahead of .NET on language features. It's behind in library availability. e.g. Mono has supported compiler-as-a-service for years, but Microsoft aren't doing it until .NET 5.0 ships. Conversely, Mono has no WPF library which is part of .NET for a long time.

> Apparently I am not familiar with the abstractions available to C# programmers. I had always assumed that it was just "Microsoft's Java".

To an extent, it is - Java with hindsight. Java without any of Java's biggest legacy design errors. e.g. it actually has handling for ABI versioning, rather than Java's "shove everything in classpath, pray all the versions are compatible" nightmare

> With regards to the other languages targeting .NET and Mono - I am not at all familiar with those. You have made me curious.....

We have support for four major .NET languages in Ubuntu right now - C#, Visual Basic.NET, Boo (a Python-like scripting language) and Java (using IKVM.NET to write .NET apps and libs in Java). We have previously had, but don't have in Precise, IronPython, IronRuby, and Nemerle - these may return in the future now we have a volunteer to help fix the packaging problems we didn't have time to address.

---

### Post by Simian Man on 2012-02-18
> **HotCupOfJava said:**
> You ARE correct in that I have not used C# on .NET or Mono, so I cannot and do not speak from personal experience.
When enough people keep feeling the need to hate on Mono without actually knowing what they are talking about, it just adds to the FUD out there about it.

> **directhex said:**
> We have support for four major .NET languages in Ubuntu right now - C#, Visual Basic.NET, Boo (a Python-like scripting language) and Java (using IKVM.NET to write .NET apps and libs in Java). We have previously had, but don't have in Precise, IronPython, IronRuby, and Nemerle - these may return in the future now we have a volunteer to help fix the packaging problems we didn't have time to address.
I guess F# isn't packaged in Ubuntu, but it does work on Linux.  It is my favorite .NET language.  Very much recommended :).

---

### Post by HotCupOfJava on 2012-02-18
> **Simian Man said:**
> When enough people keep feeling the need to hate on Mono without actually knowing what they are talking about, it just adds to the FUD out there about it.


Point taken and assimilated

---

### Post by directhex on 2012-02-18
> **Simian Man said:**
> I guess F# isn't packaged in Ubuntu, but it does work on Linux.  It is my favorite .NET language.  Very much recommended :).

Same problem as with IronFoo - someone needs to volunteer to not only create a package, but create a legally redistributable .orig.tar.gz without any dubious binaries in it (just source code, and any Free binaries needed for bootstrapping if absolutely neccessary)

---

