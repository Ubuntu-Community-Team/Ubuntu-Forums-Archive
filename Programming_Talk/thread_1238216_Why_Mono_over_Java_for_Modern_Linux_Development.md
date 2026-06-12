---
title: "Why Mono over Java for Modern Linux Development?"
date: 2009-08-12
forum: Programming Talk
---

### Post by SunSpyda on 2009-08-12
I performed a quick search and didn't find anything, so I think this shouldn't be a dupe thread.

So I have been using C# and MS VS Pro '08 on Windows for quick Windows-only programs for quite a while, but for any "real" high-level app I write, I use Java.

So, it seems after reading around that Mono C# might become the next "higher level language" of Linux, since many people don't want to use C++ when higher level languages are available.

So why are we embracing Mono C#, when Java has provided the high level environment with the vast array of libraries that we already need? Not to mention OpenJDK which is open, ofc.

I'm not taking this as a opportunity to insult Mono C# (There are enough threads for that), I simply want to know why C# has become so popular, when Java can basically offer the same thing but with more cross-platform libraries. I know Mono is a little easier to get working, but even so....

I have noticed that C# has a slightly better syntax and ways of doing things in a few areas to Java, but not enough to make it a "better" Java. In fact, I think Java is the better option, since, from what I can see, Java has more cross-platform libraries and more mature.

Is there something I completely missing here?

---

### Post by froggyswamp on 2009-08-12
[http://ubuntuforums.org/showthread.php?t=1193143](http://ubuntuforums.org/showthread.php?t=1193143)

---

### Post by SunSpyda on 2009-08-12
Thabks for the link. Sorry about that - I don't get it - I put "Mono" and "Java" in the search terms... it should have came up. Sorry again.

---

### Post by directhex on 2009-08-12
> **SunSpyda said:**
> I performed a quick search and didn't find anything, so I think this shouldn't be a dupe thread.

So I have been using C# and MS VS Pro '08 on Windows for quick Windows-only programs for quite a while, but for any "real" high-level app I write, I use Java.

So, it seems after reading around that Mono C# might become the next "higher level language" of Linux, since many people don't want to use C++ when higher level languages are available.

So why are we embracing Mono C#, when Java has provided the high level environment with the vast array of libraries that we already need? Not to mention OpenJDK which is open, ofc.

I'm not taking this as a opportunity to insult Mono C# (There are enough threads for that), I simply want to know why C# has become so popular, when Java can basically offer the same thing but with more cross-platform libraries. I know Mono is a little easier to get working, but even so....

I have noticed that C# has a slightly better syntax and ways of doing things in a few areas to Java, but not enough to make it a "better" Java. In fact, I think Java is the better option, since, from what I can see, Java has more cross-platform libraries and more mature.

Is there something I completely missing here?

As I said in the other thread, there are three core points (ignoring ALL arguments regarding java versus C# as languages - which may be a mistake to ignore). Hopefully I won't be called ignorant for my willful use of reality again.

**_1) Age._**

OpenJDK is from 2007. Mono is from 2002. Any app older than May 2007 would need to have either targeted a non-Sun Java (e.g. GCJ), or proprietary Sun Java. This is an inertia issue, since Java's been effectively ignored by developers (at Stallman's recommendation) for those 5 years between the two. F-Spot is from 2004, Tomboy from 2006 - you do the math!

**_2) Disk Bloat._**

I'll be jumped on for this again, but it's simply fact as it relates to desktop Linux development. If you want to run "hello world" on OpenJDK, you need about 90 meg of disk space. This cannot effectively be split between "important" and "rarely-used cruft" because the Java class library is incredibly intertwined. As a result, you need to find that much space on disk (or in a distro's case, on the install CD) before you can even get started. Sure, it comes with the kitchen sink - e.g. Swing - but Swing sticks out like a sore thumb anyway and is NOT an asset in this case.

So, how about Mono? 10 meg for a barebones install (actually, less in Karmic). That gets you enough runtime to run a "hello world" app on Ubuntu. Add a little more space for more features - as a result, remember our 90 meg figure for "just" OpenJDK? Tomboy, F-Spot, their translated manuals full of images, all weigh in WITH enough Mono to run them, at 54 meg. That's combines for both apps AND the runtime AND the libs AND the GUI bindings to make them feel as native as any other app (which leads on to point 3)

**_3) JNI._**

Java is unquestionably terrible at leveraging existing C libraries on a system. JNI is effectively the only reason .NET (and hence Mono) even exists, it's unfriendly and unwieldy in the extreme. Conversely, using a C library in a Mono app is literally only 1 extra line compared to using a C# library. No JNI stub invocation, no C compiler nonsense, just add the word "extern" to the method declaration, and shove a [DllImport("foo.so")] above it. As a result, someone making an app with Mono can really really easily leverage all the existing "good stuff" on their system. Might they want to replace those C calls with more portable C# at some point? Sure. But they have the freedom to use the existing libs easily - hence apps like Banshee leveraging things like GStreamer. Writing apps "in general" is fine with Java, but writing "Linux apps", which use Linux libraries, Mono is simply easier due to JNI sucking compared to P/Invoke.

There's a couple of reasons. You could ask some app developers for their thoughts if you like. The above certainly sums up my own thoughts, as someone with a bachelor's degree mostly from Java work.

---

### Post by SunSpyda on 2009-08-12
I see. Thanks for the points.

One of the reasons I embraced Java over Mono is due to the fact I hate "scavenger treasure hunts" for libraries over the net. And the fact it was all there is incredibly bloated, but very useful.

Is finding Mono C# libraries as difficult as people make out? For example, I use Swing, because it is present on nearly all Java implementations I have seen (I have seen a UNIX non-X version that didn't,) even if it looks obviously non-native.

Am I right in saying that GTK# will have a GTK dependency? Also, WPF isn't on Mono, right? So that leaves Windows Forms for Mono-compatible portable GUI that doesn't have dependencies?

You see, if I can find libraries for GUIs, socket programming, system tasks, and all the rest of it, I would consider Mono C# as a far more viable option. Of course, the libraries would have to be dependency free (On the client machine) and compatible with Mono and MS .NET.

You see, here is the problem. Getting Java to run on BSD is a pain quite often - not to mention the rest of the UNIX/UNIX-like OSes. Mono seems like quite a seamless install when I have tried it. Also, accessing C libs is something sorely missing from Java - not missing, but painful. So C# might be an option, if I can get a good selection of libraries.

So, what great libraries are there out there? A Google search would tell me, but I have a feeling that someone with experience with Mono C# would be able to explain better :)

---

### Post by Reiger on 2009-08-12
In reverse order:
(3) 
You may want to take a look at JNA instead: [https://jna.dev.java.net/](https://jna.dev.java.net/)

But yes, Java out of the box isn't very well integrated with "the outside world".

Now I am not sufficiently knowledgeable with Mono to judge just yet. There are other things I would be interested to know:
On the other hand... does Mono have "native" support for things like accessing ZIP files, and remote data streams? In Java that is a JAR loader away. And how easy/difficult is it to embed script engines? In Java it is fairly trivial there is JSR spec which interpreters like Jython/Jaskell/Groovy/XSLT/Java/JavaScript support so you can pretty much plug in an additional library (the interpreter) and away you go. More complex set ups allow you to add app-level security mechanisms for controlling what scripts can and cannot do/access... I wonder whether Mono has that too (might then decide to code a couple of ideas I have in C# instead of Java to give it a spin).


(2) 
Something I disagree with you about, though is that Swing is not an asset. When I want a GUI app for something I make for myself I tend to want something just like Swing for the reason that I can have a more true write-once run-anywhere (I have only so many machines I want to run it on anyways) setup than I could hope to achieve with GTK# (simply because it means no extra dependency on my Windows box, or those of the incidental odd other person I share those throw-away apps with). 

[size="1"]Plus I think that Swing + Substance is better looking than GTK. (I happen to think GTK and GTK+ and GTKwhat-have-you all look ugly and no theme can remedy it: if you want something pretty you'd look at Qt). We two have been there before: about the look of Swing vs. the look of GTK, haven't we?[/size]

(1) Java is poorly packaged. Can't blame the package managers because Java has its own package format the JAR, which does not map cleanly to other formats. However a base installation would exist of JRE + java.lang support. That is enough for a CLI Hello world app, I think the thing is just that nobody bothers with CLI Hello world apps for Java so nobody bothers to package it that way either. But it is certainly possible to trim down Java installation size.

---

### Post by SunSpyda on 2009-08-12
Yeah I was thinking that as well - Swing looks ugly, but it does look half-decent considering its write-once run-everywhere talent, which GTK sorely lacks.

Thanks for the JNA link... looks less agonizing than JNI anyway :)

@ directhex - Why does Stallman tell people to ignore Java? :confused: He seems like the last person to wave the flag for a technology by MS. Unless he really thinks people will use C or Lisp forever... ofc I will use C with inline ASM for low level stuff, but it's too pedantic for high-level app development.

Oh, and if you have the link to where he said that, could you post it please? - it'll be an interesting read :)

---

### Post by Vadi on 2009-08-12
Probably because that's what students are taught in universities (C#) and is the only thing they know now. Go Vala here though :)

---

### Post by phrostbyte on 2009-08-12
This will be an epic thread. :)

This is my opinion:
I prefer C# the language over Java, but Java has more libraries by far. This is because Java has a bigger open source community around it and a community process that .NET lacks.

For desktop development Mono has a very nice integrated IDE called MonoDevelop. For GTK+ development this is an excellent choice. But Java has Qt/Jambi, which is an advanced solution for Qt development. Mono has Qyoto, but it is not officially supported by Nokia.

The main thing I miss in Java is the concept of properties. They are syntactic sugar over get'er ans set'er, but they make code look cleaner IMO. Java may be getting properties soon however.

---

### Post by directhex on 2009-08-12
> **SunSpyda said:**
> Am I right in saying that GTK# will have a GTK dependency? Also, WPF isn't on Mono, right? So that leaves Windows Forms for Mono-compatible portable GUI that doesn't have dependencies?

Correct. On Windows, a GTK# app requires installation of the GTK# redistributable. It's included with Mono on all platforms, or a standalone .msi

> So, what great libraries are there out there? A Google search would tell me, but I have a feeling that someone with experience with Mono C# would be able to explain better :)

I have no experience with the things you mention as wanting - I stick basically to the base class library and Novell.Directory.Ldap

---

### Post by directhex on 2009-08-12
> **Reiger said:**
> does Mono have "native" support for things like accessing ZIP files, and remote data streams? In Java that is a JAR loader away. And how easy/difficult is it to embed script engines? In Java it is fairly trivial there is JSR spec which interpreters like Jython/Jaskell/Groovy/XSLT/Java/JavaScript support so you can pretty much plug in an additional library (the interpreter) and away you go. More complex set ups allow you to add app-level security mechanisms for controlling what scripts can and cannot do/access... I wonder whether Mono has that too (might then decide to code a couple of ideas I have in C# instead of Java to give it a spin).

Zip support comes via the SharpZipLib library which is bundled with Mono and pretty much every app for MS.NET.

Scripting engines these days will likely layer on top of Microsoft's Dynamic Language Runtime, which is Free Software and works on Mono (IronPython and IronRuby use it), or may use other more traditional systems like System.Reflection.Emit (e.g. the Boo scripting language which Banshee supports). To an extent, the thing to bear in mind is that compiled CIL code for all .NET languages is completely interoperable - a library written in VB.NET can be used in an app written in C# can be leveraged inside an ASP.NET page written using IKVM (OpenJDK-on-Mono).

Security stuff... it's in MS.NET, but not in Mono yet (it's coming, Moonlight 2.0 is implementing it)

> [size="1"]Plus I think that Swing + Substance is better looking than GTK. (I happen to think GTK and GTK+ and GTKwhat-have-you all look ugly and no theme can remedy it: if you want something pretty you'd look at Qt). We two have been there before: about the look of Swing vs. the look of GTK, haven't we?[/size]

There's Qyoto. Done lots of work with the KDEBindings packagers to make that well-packaged. But it's less portable than GTK# since you need to worry about Qt libs and Smoke glue and so on.

> (1) Java is poorly packaged. Can't blame the package managers because Java has its own package format the JAR, which does not map cleanly to other formats. However a base installation would exist of JRE + java.lang support. That is enough for a CLI Hello world app, I think the thing is just that nobody bothers with CLI Hello world apps for Java so nobody bothers to package it that way either. But it is certainly possible to trim down Java installation size.

Java has no coherent way of tracking the dependencies, that's a large part of the problem. CLI assemblies have a name, version number, and list of dependent names/versions burned in, so you can see:

```
directhex@desire:/usr/lib/mono/2.0$ monodis --assemblyref mscorlib.dll 
AssemblyRef Table
```

Is the absolute root library, with no external deps, and
```
directhex@desire:/usr/lib/mono/2.0$ monodis --assemblyref ICSharpCode.SharpZipLib.dll 
AssemblyRef Table
1: Version=2.0.0.0
	Name=mscorlib
	Flags=0x00000000
	Public Key:
0x00000000: B7 7A 5C 56 19 34 E0 89 
2: Version=2.0.0.0
	Name=System
	Flags=0x00000000
	Public Key:
0x00000000: B7 7A 5C 56 19 34 E0 89 
```
needs the above library, plus the (almost root but not quite) System.dll - specific hard-coded versions (like SONAMEs). And even backward-compatibility tracking via Policy files. The whole infrastructure allows for chopping it into pieces.

---

### Post by SunSpyda on 2009-08-12
So what libraries can you be sure will be present on all .NET implementations (Especially MS .NET and Mono?)

I saw that System was available on all of them, but what others?

Basically, what I'm saying is, could I go out and write a app with networking, GUI, file compression, and other bits and bobs under Mono C# using only libraries found on all implementations of .NET? Or would I need to tack additional non-standard dependencies to it?

Because that is a absolute killer point for Java - Being able to write a full fledged app straight out the box with zero dependencies except JRE as a whole. If Mono C# is similar then that's Java's main advantage out the window.

---

### Post by directhex on 2009-08-12
> **SunSpyda said:**
> So what libraries can you be sure will be present on all .NET implementations (Especially MS .NET and Mono?)

I saw that System was available on all of them, but what others?

Basically, what I'm saying is, could I go out and write a app with networking, GUI, file compression, and other bits and bobs under Mono C# using only libraries found on all implementations of .NET? Or would I need to tack additional non-standard dependencies to it?

Because that is a absolute killer point for Java - Being able to write a full fledged app straight out the box with zero dependencies except JRE as a whole. If Mono C# is similar then that's Java's main advantage out the window.

[http://go-mono.com/status/](http://go-mono.com/status/) lists all namespaces & classes from MS.NET and whether Mono implements them

---

