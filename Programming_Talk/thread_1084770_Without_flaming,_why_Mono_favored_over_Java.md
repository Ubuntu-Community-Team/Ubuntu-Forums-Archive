---
title: "Without flaming, why Mono favored over Java?"
date: 2009-03-02
forum: Programming Talk
---

### Post by jsmidt on 2009-03-02
Java has been open sourced with official GTK bindings.  Mono's legality is in question in some areas.  However, many more gtk-minded develpers seem to be choosing to program in Mono over Java. 

I was just wondering if anyone had any intelligent reasons why, without flaming.  It isn't a question of "Why is mono/C# better then Java", it is the question "Why has the gtk community adopted Mono/C# over Java"?  If anyone knows.

---

### Post by directhex on 2009-03-02
> **jsmidt said:**
> Java has been open sourced with official GTK bindings.  Mono's legality is in question in some areas.  However, many more gtk-minded develpers seem to be choosing to program in Mono over Java. 

I was just wondering if anyone had any intelligent reasons why, without flaming.  It isn't a question of "Why is mono/C# better then Java", it is the question "Why has the gtk community adopted Mono/C# over Java"?  If anyone knows.

A few points:

[LIST]
[*]Java sucks badly at some common things. A good example here is JNI, the Java mechanism allowing you to leverage existing C libraries. The GTK ecosystem has LOADS of quality libraries available for use, and using them in Java is......... well, JNI being a monstrous piece of doodie is the reason C# was created in the first place. If you wanted to use one function in an existing library, and had the option between writing 1 line of C#, or ~40 lines of Java and non-portable C, to use that lib... which would YOU pick?
[*]Java is bloated compared to Mono. People often try to claim otherwise, however, the sad fact is that Java is huge. Part of this is a design problem - Java's many libraries are completely interdependent, so you can't effectively split the "core" parts from the "useful" parts. As a result, even the simplest of apps requires over 100 meg of Java on disk - comparatively, Tomboy (which includes nearly 10 meg of docs) and its entire Mono-related dependency chain come to between 30 and 40 meg on Jaunty - and that dependency chain obviously matters less the more apps you have. Java should be in a position to shrink if the promised reoganization in Java 7 happens. Java's enormous RAM consumption compared to Mono also doesn't help matters.
[*]Development environments for GTK on Java are lacking. Monodevelop makes it very easy to use clicky design using its integrated Stetic designer, or you can use cross-platform .glade XML files just as easily. Designing a GTK GUI on Java is unpleasant manual work.
[*]Years of hindsight. Java is a "mature" platform, more or less the first of its kind - which unfortunately means Sun were in a position to make a lot of first-time errors. C# and the Common Language Infrastructure have a number of advantages over Java thanks to the ability to "fix" Java design flaws (both the language and the framework) - the simplest two being that Generics support in Java is very weak (a compiler trick), and that Java's bytecode (.class files) is NOT designed for use with non-Java languages. Conversely, CLI was designed from day 1 to be multi-language, and its generics support is much more powerful. You can even write using the Java language, on Mono, if you want to (ikvm package)
[/LIST]

---

### Post by jimi_hendrix on 2009-03-02
personally, i prefer C# over Java as a language and .Net over the java libraries

---

### Post by ajackson on 2009-03-02
> **jsmidt said:**
> Java has been open sourced with official GTK bindings.
The question is why Sun went down that root, they obviously have concerns over the popularity of C# (both Mono and the MS version).

> Mono's legality is in question in some areas.
Sabre rattling by Microsoft is often just that, sabre rattling. Mono isn't the only open source solution that Microsoft are claiming patent violations about and if they were so certain of violations wouldn't the sensible thing to do be to defend those patents (i.e. legal action), good old MS blows out a lot of hot air.

> However, many more gtk-minded develpers seem to be choosing to program in Mono over Java.
Could be because Mono got there first or it could be because there is a de jure standard. From a Ubuntu point of view, because of it's Debian roots I would guess that what was a closed source language wouldn't be that high up the picking list for languages to use.

> If anyone knows.
People, like me, will have opinions (and remember opinions are like backsides, everyone has one) but I doubt if anyone knows for sure (I doubt there was a big meeting where use of Java was ruled out).

---

### Post by Cracauer on 2009-03-02
> **jsmidt said:**
> However, many more gtk-minded develpers seem to be choosing to program in Mono over Java. 


The same person that started GNOME started Mono. He must be right, so the sheep follow.

In the Windoze world, Sun's behavior over the better part of Java's existence has alienated a majority of programmer who would use one of these medium-level languages. Sun's behavior and willingness to just give Java people what they want only improved when C# had taken off. Too late.

Since .net is much more popular on Windows it makes sense that people on Linux follow.

These users of medium-level languages usually aren't hardcore in any way. They want to get work done and they want to keep their options open, and many want to improve their chances of scoring Windoze programming jobs. They rather deal with some imperfections in Mono than with Sun's arrogant behavior.

---

### Post by wrtpeeps on 2009-03-02
C# is the language of the future.

Someone write a machine code compiler (whatever it's called, so the runtime isn't needed) and watch it leave the world in its wake!

---

### Post by days_of_ruin on 2009-03-02
> **wrtpeeps said:**
> C# is the language of the future.

Someone write a machine code compiler (whatever it's called, so the runtime isn't needed) and watch it leave the world in its wake!

It already does have machine code compiling.[http://www.nuclex.org/pages/compiling-dotnet-to-machine-code]("http://www.nuclex.org/pages/compiling-dotnet-to-machine-code")

---

### Post by howlingmadhowie on 2009-03-02
> **jsmidt said:**
> Java has been open sourced with official GTK bindings.  Mono's legality is in question in some areas.  However, many more gtk-minded develpers seem to be choosing to program in Mono over Java. 

I was just wondering if anyone had any intelligent reasons why, without flaming.  It isn't a question of "Why is mono/C# better then Java", it is the question "Why has the gtk community adopted Mono/C# over Java"?  If anyone knows.

To continue the hyperbolic tone of the other contributors to this thread, Mono and C# are favoured over Java by people who have little regard for their freedom. Both have horribly dated language definitions. Both have large, complicated runtimes. C#/Mono has the added problem that at some stage in the future Microsoft will sue and close the project down. Programming for Mono is nothing short of idiotic.

---

### Post by Mr.Macdonald on 2009-03-02
> C# is the language of the future.

I would beg to differ, I feel that anything that comes from a priority back ground has no place in Unix. I feel that even Java (which is open source) is very un Unix like.

I feel that the languages of the future are the ones of the past: C, Lisp, Python (sort of old), C++. Nothing ever outdates C and Python is so general that just about anything is possible and easy to do. Lisp is in a class of its own, Lisp is older that C and still extremely powerful to those who know how to use it.

---

### Post by Sorivenul on 2009-03-02
> **howlingmadhowie said:**
> Programming for Mono is nothing short of idiotic.
What about programming *in* Mono/C#?
(Sorry, couldn't resist...)

Now, to address the topic:
directhex made a lot of good points. 

C# came after many of the design problems present in Java had become evident, and came up with solutions for many of them, while still retaining a few problems of its own, but no language is perfect.

From a personal perspective, I don't need a complicated IDE to write relatively intensive applications in Mono/C#. Even after 6 years writing in Java, I still feel the need to use NetBeans or some other IDE to help me cope with Java's library morass.

---

### Post by mpsii on 2009-03-02
> **Sorivenul said:**
> 
From a personal perspective, I don't need a complicated IDE to write relatively intensive applications in Mono/C#. Even after 6 years writing in Java, I still feel the need to use NetBeans or some other IDE to help me cope with Java's library morass.

Could you elaborate on this a bit more?

As someone who has dabbled in both C# (but not Mono) and Java, I have found trying to use anything other than Visual C# Express Edition to prove unwieldly. Also, I have used Oracle's JDeveloper (I HATE how it organizes files) and Eclipse. I find no IDE easier than another. Personally, I have to have APIs open in a browser window for either language. I have tried C# and Java using Notepad... again, I find both unwieldy.

I have tried Python, PHP, Ruby, and a couple of others. Again, I have not found a _great_ IDE for any use, but Python (at least) I can code in a text editor like I always did for HTML, Javascript, Basic, and Cobol (which I forgotten all but the green-lined paper).

---

### Post by wrtpeeps on 2009-03-02
> **Mr.Macdonald said:**
> I would beg to differ, I feel that anything that comes from a priority back ground has no place in Unix. I feel that even Java (which is open source) is very un Unix like.

I feel that the languages of the future are the ones of the past: C, Lisp, Python (sort of old), C++. Nothing ever outdates C and Python is so general that just about anything is possible and easy to do. Lisp is in a class of its own, Lisp is older that C and still extremely powerful to those who know how to use it.

Who cares if it has a place in Unix or not? Let's be honest here.

---

### Post by howlingmadhowie on 2009-03-02
> **Sorivenul said:**
> What about programming *in* Mono/C#?
(Sorry, couldn't resist...)

the way i understood it, mono is the runtime environment and compiler. C# is the language definition.

---

### Post by Sorivenul on 2009-03-02
> **mpsii said:**
> Could you elaborate on this a bit more?

If you do more than dabble in either, or both, you'll likely see what I mean more clearly. Most of, if not all of, this comes back to opinion and personal preference. What I find "easier" may not be for others, including yourself.

As far as the need for having APIs available while coding, I find myself browsing Mono/C# documentation much less than I rely on Java documentation and code completion via IDEs.  

IMO, C# generally makes many things easier, though easier does not always mean better. Multithreading in C# is, IMO, much nicer than in Java thanks to Monitor and Mutex. Interfaces in C# (mostly comparable to Vectors in Java) are "cleaner". There is also the possibility of operator overloading in C#, which was left out of Java, and is often a point of contention in this debate. Of course, one has to mention closures, which are arguably easier to achieve in C# without having to go through the extra work to "force" closures in Java with refactoring. In addition to closures, C# is capable of lambda functions and expression trees. Then comes the matter of exception handling, which is a fairly big point of contention between C# developers and Java developers in itself. 

Sorry if some of that was a bit of a tangent.

> **howlingmadhowie said:**
> the way i understood it, mono is the runtime environment and compiler. C# is the language definition.
True enough, but the important thing is, C# runs on Mono, which is the issue at hand here. It is nearly impossible to separate the two.

---

### Post by howlingmadhowie on 2009-03-03
> **Sorivenul said:**
> 
True enough, but the important thing is, C# runs on Mono, which is the issue at hand here. It is nearly impossible to separate the two.

the whole point of documenting the byte code which should be produced by a compiler is to allow the byte code to be run on various virtual machines. there is no standard for C byte code, there is however a standard for Java byte code (and i presume a standard for .NET byte code), otherwise the virtual machine would be unimplementable. 

no one seems to want to address the point that mono contains a lot of Microsoft's "intellectual property", apart from some hand-waving and saying "oh, Microsoft won't sue, they're just doing some good, old-fashioned sabre-rattling". this seems to me to be a rather wobbly rock upon which to build a project. 

there are enough languages which run on the jvm as well. it isn't as if you have to write java. you can write python, lisp, groovy, javafx and others too.

---

### Post by howlingmadhowie on 2009-03-03
> **Cracauer said:**
> The same person that started GNOME started Mono. He must be right, so the sheep follow.

In the Windoze world, Sun's behavior over the better part of Java's existence has alienated a majority of programmer who would use one of these medium-level languages. Sun's behavior and willingness to just give Java people what they want only improved when C# had taken off. Too late.

Since .net is much more popular on Windows it makes sense that people on Linux follow.

These users of medium-level languages usually aren't hardcore in any way. They want to get work done and they want to keep their options open, and many want to improve their chances of scoring Windoze programming jobs. They rather deal with some imperfections in Mono than with Sun's arrogant behavior.

you do know the story about Microsoft's sabotaging of java?

have a look [here]("http://www.usdoj.gov/atr/cases/f1700/1762.htm"), and search for the word java. one can understand sun being protective of java after microsoft behaved in this manner. you seem to have misinterpreted this as arrogance.

---

### Post by cb951303 on 2009-03-03
From an end-user point of view, mono applications looks better and feels faster. That pretty much covers why they prefer Mono over Java :popcorn:

---

### Post by directhex on 2009-03-03
> **howlingmadhowie said:**
> the whole point of documenting the byte code which should be produced by a compiler is to allow the byte code to be run on various virtual machines. there is no standard for C byte code, there is however a standard for Java byte code (and i presume a standard for .NET byte code), otherwise the virtual machine would be unimplementable. 

The standard you mention is ECMA-335, also ratified as ISO/IEC 23271:2006. There are four "major" implementations: Rotor is a proof-of-concept source-code release for Windows and BSD-like systems, by Microsoft (under a restrictive non-Free license); Microsoft.NET is the major closed source version for Windows only; DotGNU Portable.NET is a GNU-sponsored multi-arch multi-platform implementation under GPL and LGPL; Mono is the most popular multi-arch multi-platform implementation under GPL, LGPL, and MIT/X11.

It's worth noting that the "standard" for Java bytecode is not a standard any more than the "standard" for .doc files - Sun declined to spend time and effort (and risk allowing outside contribution) involved in submission to an international standards body

CIL bytecode can be executed on any framework implementing the required libraries, assuming the code itself wasn't written with false platform-specific assumptions (e.g. using methods in c:\windows\system32\gdi32.dll, or hard-coding paths with "\" in them instead of using the cross-platform-aware System.IO.Path.Combine())

> **howlingmadhowie said:**
> you do know the story about Microsoft's sabotaging of java?

have a look [here]("http://www.usdoj.gov/atr/cases/f1700/1762.htm"), and search for the word java. one can understand sun being protective of java after microsoft behaved in this manner. you seem to have misinterpreted this as arrogance.

See, the funny thing is, the "sabotage" is also part of  C#'s history. The sabotage in question is essentially two major features: a Windows-only GUI library for better OS integration (i.e. because Swing looks totally alien on Windows), and a non-crap replacement for JNI to make Java actually usable for "native" app development (by gaining the ability to leverage existing libraries without causing hernias).

.NET was born as a result of Sun's violent resistance to those changes - the end result was a non-Sun-controlled clone, fixing a bunch of design problems, and creating a proper ISO standard.

> **howlingmadhowie said:**
> To continue the hyperbolic tone of the other contributors to this thread, Mono and C# are favoured over Java by people who have little regard for their freedom. Both have horribly dated language definitions. Both have large, complicated runtimes. C#/Mono has the added problem that at some stage in the future Microsoft will sue and close the project down. Programming for Mono is nothing short of idiotic.

I hesitate to use the term, but here goes: braindead.

If, as seems to be the case right now, Microsoft go after someone (TomTom) for something in the Linux kernel, does that mean the entire kernel project is being closed down? REALLY? Can't hear you at the back.

Legal attacks need *specific* targets.

IF Microsoft decide they have more to gain than to lose by killing off .NET as a cross-platform framework
AND
IF they identify specific sections of Mono which infringe on MS patents they want to protect
AND
IF those sections cannot be re-worked and changed to avoid the patents (the way Freetype did to avoid Apple's patent lawyers)
AND
IF those patents cannot be invalidated by prior-art claims (typically from Sun, given the Java influences in .NET)
AND
IF those sections cannot be removed entirely, with apps reworked to bypass the problem areas
AND
IF an alternative framework cannot do the job - e.g. DotGNU Portable.NET, or even reworking the app with Vala
THEN, and only then, is there a real-world problem.

If you think people writing apps with Mono haven't weighed the pros and cons, then you're sorely mistaken

---

### Post by aquavitae on 2009-03-03
Sorry to bring another language into the discussion, but how about python?  I'll admit I haven't used either C# or java much, but from what I've seen there isn't any advantage of C# over python.  Both are cross-platform and use byte code.  Python also has a good IDE (e.g. Eric).  And the advantage is that python has smaller dependencies.

---

### Post by eye208 on 2009-03-03
> **jsmidt said:**
> Mono's legality is in question in some areas.
So is the legality of Linux, according to Steve Ballmer.

> However, many more gtk-minded develpers seem to be choosing to program in Mono over Java.
OpenJDK came to the party too late.

---

### Post by howlingmadhowie on 2009-03-03
> **directhex said:**
> 
It's worth noting that the "standard" for Java bytecode is not a standard any more than the "standard" for .doc files - Sun declined to spend time and effort (and risk allowing outside contribution) involved in submission to an international standards body

sun does not govern java, the java consortium governs java. seeing how iso has been bought by microsoft, i'd say that the java consortium has much more credibility as a standards committee

> 
See, the funny thing is, the "sabotage" is also part of  C#'s history. The sabotage in question is essentially two major features: a Windows-only GUI library for better OS integration (i.e. because Swing looks totally alien on Windows), and a non-crap replacement for JNI to make Java actually usable for "native" app development (by gaining the ability to leverage existing libraries without causing hernias).

.NET was born as a result of Sun's violent resistance to those changes - the end result was a non-Sun-controlled clone, fixing a bunch of design problems, and creating a proper ISO standard.

because the changes made programs compiled for microsoft's version of java dependent upon microsoft's version of java. this was totally against the "write once, run anywhere" idea behind java. microsoft sabotaged java in order to stop the spread of java technology. the courts agree with me here.

> 
If, as seems to be the case right now, Microsoft go after someone (TomTom) for something in the Linux kernel, does that mean the entire kernel project is being closed down? REALLY? Can't hear you at the back.


yes, it does, if TomTom doesn't have the money to fight the attack and microsoft decides to go after the next link in the chain. the linux kernel team has a lot of very powerful friends, so microsoft will think twice before doing so. mono on the other hand is at the moment utterly unimportant (fortunately). it is also controlled by novell, so don't expect any legal protection from that side. 

> 
Legal attacks need *specific* targets.

IF Microsoft decide they have more to gain than to lose by killing off .NET as a cross-platform framework
AND
IF they identify specific sections of Mono which infringe on MS patents they want to protect
AND
IF those sections cannot be re-worked and changed to avoid the patents (the way Freetype did to avoid Apple's patent lawyers)
AND
IF those patents cannot be invalidated by prior-art claims (typically from Sun, given the Java influences in .NET)
AND
IF those sections cannot be removed entirely, with apps reworked to bypass the problem areas
AND
IF an alternative framework cannot do the job - e.g. DotGNU Portable.NET, or even reworking the app with Vala
THEN, and only then, is there a real-world problem.

If you think people writing apps with Mono haven't weighed the pros and cons, then you're sorely mistaken

i imagine microsoft has already done the foot work for most of those steps. and even if they haven't, mono remains a risk. you can stick your head in the sand all you want, it won't change that fact.

---

### Post by directhex on 2009-03-03
> **aquavitae said:**
> Sorry to bring another language into the discussion, but how about python?  I'll admit I haven't used either C# or java much, but from what I've seen there isn't any advantage of C# over python.  Both are cross-platform and use byte code.  Python also has a good IDE (e.g. Eric).  And the advantage is that python has smaller dependencies.

Python's a very different topic, really

It's very popular because it allows for very very quick app development & prototyping.

One important difference to note here, however, is that C# is not Mono is not C# - the CLI allows multiple languages by design, and there's already a Python compiler for Mono in the archive (allowing you to, say, write F-Spot plugins in Python)

Plus points for (C)Python as an app development environment - quick & easy. Downsides - often breaks between versions, much much slower than Mono.

Personally, I think people should feel free to write in Python - part of Free Software is that people should be free to do as they please. If Python works best for them, then by all means. Ubuntu should be the best ******* computing platform out there - and it should help people to write whatever they want, however they want

---

### Post by eye208 on 2009-03-03
> **directhex said:**
> Swing looks totally alien on Windows
...unless you activate the system look & feel:
```
UIManager.setLookAndFeel(
    UIManager.getSystemLookAndFeelClassName()
);
```

---

### Post by directhex on 2009-03-03
> **eye208 said:**
> ...unless you activate the system look & feel:
```
UIManager.setLookAndFeel(
    UIManager.getSystemLookAndFeelClassName()
);
```

At which point it merely looks *partly* alien.

UIManager, especially when we're talking about here (~2000, 2001ish), simply does not look like the "real thing". These days it looks like a close approximation, sure.

---

### Post by jimi_hendrix on 2009-03-03
i learned programming in C#, so naturally i will favor it.  After C# i learned C++, and after a while java.  i dropped java quickly because it felt somewhat messy and a pain compared to C#

---

### Post by ajackson on 2009-03-03
> **howlingmadhowie said:**
> no one seems to want to address the point that mono contains a lot of Microsoft's "intellectual property", apart from some hand-waving and saying "oh, Microsoft won't sue, they're just doing some good, old-fashioned sabre-rattling". this seems to me to be a rather wobbly rock upon which to build a project.
Microsoft say that Mono contains their intellectual property, they can't provide examples (or have chosen not too). I seem to remember SCO making wild claims as well, last I heard they are losing/lost every legal claim they have taken out.

If you want to fall for Microsoft's scare tactics and not use Mono then by all means do so, you have freedom of choice, so do the people who use Mono (or Linux for that matter, another thing that Microsoft has made claims about). If it is proved that Mono does use Micrsofts IP then, and only then, will I cease making any use of it, or the parts in question. But as I said sabre rattling is often just sabre rattling, I'm not waving my hands about it and if I'm wrong then I'm wrong.

---

### Post by directhex on 2009-03-03
> **ajackson said:**
> Microsoft say that Mono contains their intellectual property, they can't provide examples (or have chosen not too). I seem to remember SCO making wild claims as well, last I heard they are losing/lost every legal claim they have taken out.

If you want to fall for Microsoft's scare tactics and not use Mono then by all means do so, you have freedom of choice, so do the people who use Mono (or Linux for that matter, another thing that Microsoft has made claims about). If it is proved that Mono does use Micrsofts IP then, and only then, will I cease making any use of it, or the parts in question. But as I said sabre rattling is often just sabre rattling, I'm not waving my hands about it and if I'm wrong then I'm wrong.

[img]http://www.camelspotting.com/FileUpload/pub/panic.gif[/img]

---

### Post by ajackson on 2009-03-03
> **directhex said:**
> [img]http://www.camelspotting.com/FileUpload/pub/panic.gif[/img]
Seems their scare tactics has worked on some people :(

---

### Post by ZuLuuuuuu on 2009-03-03
My humble opinion is that Mono is a magnificent project, in idea. However because Miguel de Icaza is tired of doing great projects and not getting any money, he turned this into an opportunity for him by choosing to use (or should I say "promote"?) a Microsoft technology, unfortunately costing a lot to free software world in long term.

**Just because .Net is good does not mean free software community should give up their philosophy and use it**. For long long years Microsoft has behaved to be a monopoly and Mono people just forget about that and help spreading this technology.

---

### Post by directhex on 2009-03-03
> **ZuLuuuuuu said:**
> My humble opinion is that Mono is a magnificent project, in idea. However because Miguel de Icaza is tired of doing great projects and not getting any money, he turned this into an opportunity for him by choosing to use (or should I say "promote"?) a Microsoft technology, unfortunately costing a lot to free software world in long term.

Mono started life when Miguel was still running Ximian. Are you suggesting there was some kind of secret deal between Ximian and Microsoft?

---

### Post by ZuLuuuuuu on 2009-03-03
> **directhex said:**
> Mono started life when Miguel was still running Ximian. Are you suggesting there was some kind of secret deal between Ximian and Microsoft?

No, I didn't understand what made you think of that from my message. I'm just talking about basic human desires...

---

### Post by ajackson on 2009-03-03
> **ZuLuuuuuu said:**
> However because Miguel de Icaza is tired of doing great projects and not getting any money, he turned this into an opportunity for him by choosing to use (or should I say "promote"?) a Microsoft technology
I'm intrigued where this speculation comes from, I know you say it is your opinion but does it have any basing in fact or is it pure speculation?

> **Just because .Net is good does not mean free software community should give up their philosophy and use it**. For long long years Microsoft has behaved to be a monopoly and Mono people just forget about that and help spreading this technology.
The open source community is based around choice, no one forces people to use Mono, sure parts of the Ubuntu OS is Mono-based but the choice still exists to use Ubuntu or to avoid the parts that are Mono based within it (where possible).

---

### Post by directhex on 2009-03-03
> **ZuLuuuuuu said:**
> No, I didn't understand what made you think of that from my message. I'm just talking about basic human desires...

"However because Miguel de Icaza is tired of doing great projects and not getting any money, he turned this into an opportunity for him by choosing to use (or should I say "promote"?) a Microsoft technology"

Miguel's never shied away from taking inspiration from technologies he likes - yes, that includes things like COM (CORBA) and OLE (Bonobo). In this instance, he saw a good Microsoft technology (.NET) beginning to appear, around the time that he realised what a complete mess writing big apps in C is (Evolution) - hence deciding to re-use Microsoft's R&D money by making an implementation of the new spec - to save time in developing Linux apps.

I'm not sure how 1) your quote can be interpreted as anything other than "Miguel made Mono to get MS money", and 2) How you feel it has any basis in documented reality

---

### Post by cb951303 on 2009-03-03
since it already turned into a yet another "mono is evil" thread may I ask what exactly MS has on mono? I mean, AFAIK, even if Novell and MS hadn't an agreement, reimplementing a MS technology wouldn't be illegal. Am I missing something? What makes Mono different than Wine or Samba? I think it even has an advantage considering C# is a standard now and free to implement. And implementing .NET libraries is just like Wine implementing Win32 libraries. Maybe there is something wrong (law wise) with Mono VM?

PS: I truly don't know the reason (if there is any). I don't mean to flame :)

---

### Post by Cracauer on 2009-03-03
> **howlingmadhowie said:**
> you do know the story about Microsoft's sabotaging of java?

have a look [here]("http://www.usdoj.gov/atr/cases/f1700/1762.htm"), and search for the word java. one can understand sun being protective of java after microsoft behaved in this manner. you seem to have misinterpreted this as arrogance.

I know all about it, but Sun just didn't play their hand right.

Java didn't do what people want, in particular lack of generics, any kind of compile-time computing and lack of printf or similar "get this done" format facility.

Microsoft successfully damaged by undermining Java's portability argument, but to be honest people just didn't care enough about Java as a language to raise a real stink about it.

---

### Post by ZuLuuuuuu on 2009-03-03
> **ajackson said:**
> I'm intrigued where this speculation comes from, I know you say it is your opinion but does it have any basing in fact or is it pure speculation?


Speculation has other meanings (it gives a meaning like conspiracy theory) :( I don't say "It is stated that..." or "Miguel's friend told me..." or "There are rumors about..." this is just an humble opinion of mine like I said.

> **directhex said:**
> I'm not sure how 1) your quote can be interpreted as anything other than "Miguel made Mono to get MS money", and 2) How you feel it has any basis in documented reality

I just can't understand why you think that I am claiming of having some knowledge about some secret fact. I don't claim anything. I added "My humble opinion" at the beginning of the sentence. Also I just said that, I think, Miguel decided to make some money and so he choose Microsoft technology; he doesn't need to do a secret deal with Microsoft to do that :S

> **directhex said:**
> Miguel's never shied away from taking inspiration from technologies he likes - yes, that includes things like COM (CORBA) and OLE (Bonobo). In this instance, he saw a good Microsoft technology (.NET) beginning to appear, around the time that he realised what a complete mess writing big apps in C is (Evolution) - hence deciding to re-use Microsoft's R&D money by making an implementation of the new spec - to save time in developing Linux apps.

He could base his workings on Python (which was already being popular in Linux application development) or Parrot VM (which was started before Mono project I guess and leaded by another free software hero, Larry Wall) if he wanted a general purpose virtual machine. Again this is just my opinion, I don't claim that he made a secret deal with Microsoft to use bytecode specification of .Net framework or that Miguel is actually the son of Bill Gates or any other conspiracy theory. I just think in that way...

---

### Post by ebichete on 2009-03-03
> **jsmidt said:**
> Java has been open sourced with official GTK bindings.  Mono's legality is in question in some areas.  However, many more gtk-minded develpers seem to be choosing to program in Mono over Java. 

I was just wondering if anyone had any intelligent reasons why, without flaming.  It isn't a question of "Why is mono/C# better then Java", it is the question "Why has the gtk community adopted Mono/C# over Java"?  If anyone knows.

GTK is written in C which is great for low-level stuff and providing libraries with good multi-language bindings. It is however tedious to write the GLib/GObject boilerplate in C. A few tools were created to do that for you automatically, but none of them really caught on. It is also convenient to have a language with an object-oriented syntax when writing GUI code.

Some groups tried using C++ (gtkmm notably), but faced pushback due to peoples' previous experiences with (and distaste for) C++. Perl was introduced and ignored by almost everyone. Python was pretty good but immature and spurred many language debates (the whitespace holywar). Java was still being jealously guarded by Sun. They had just killed off Microsoft's J++/WFC environment, so tangling with them was frightening; and any language that takes 6 versions to get enums right cannot be recommended. Vala was just beginning and nowhere close to ready.

When Miguel and his crack commando team bootstrapped Mono with C# (a really nice language) and churned out a couple of useful, funky new apps with pretty codebases, everyone took notice. There was an general anti-Microsoft backlash and later a more specific patent concern, but that didn't really matter. The direction of the Gnome platform is driven by the applications, contrasting with KDE which is more driven from the base library QT. It doesn't always work out well (the Evolution email client made people receptive to Bonobo/CORBA) but it seems "the way of Gnome". 

That's my opinion, consume with grain of salt.

- Edward -

---

### Post by howlingmadhowie on 2009-03-03
i've never used C#, and i have no intention of starting. friends of mine, who have used it, tell me the language definition is poor compared with languages such as python or ruby. python and ruby allow easy binding of C to do whatever heavy-lifting is needed as well, so speed isn't a problem. 

in the future i can see gnome solidifying around python wrappers to C libraries. i really can't see C# in gnome's future (fortunately).

---

### Post by wrtpeeps on 2009-03-03
> **ZuLuuuuuu said:**
> 

**Just because .Net is good does not mean free software community should give up their philosophy and use it**. For long long years Microsoft has behaved to be a monopoly and Mono people just forget about that and help spreading this technology.

Hold on, so you're saying, it's good, but don't use it, because big bad Microsoft are going to pocket all your monies??

Jesus Holy Christ.... :-({|=](*,)

---

### Post by Shin_Gouki2501 on 2009-03-03
of course it did turn into a flame war :D
Well i used .NET 1.0 and some 2.0 for my diploma, since then a lot changed.
I'm working now since 2 years with Java. And somehow, of course i got adicted...
C# is great! However the thing with mono is slightly diffrent. Sadly gnome supports C# far more than java.

Although these days you could create absolute nice looking Swing and SWT Apps which integrate very well in the Linux desktop ( via custom look & feels).

Despite that "disadvantage" of Java on the Linux desktop i do believe that the new open strategy regarding the jvm will bring usefull and interesting contributions to the Linux desktop. Via: Scala, Jython, JRuby, Groovy or even Clojure(ever wanted to write a GUI - App in LISP like syntax google some examples its fun ).

The new open and deversity concept of the jvm will break down some walls ( at least i hope so :))

below i link to java apps which i use quite often and i like it!

---

### Post by fevans on 2009-03-03
> **jsmidt said:**
> It isn't a question of "Why is mono/C# better then Java", it is the question "Why has the gtk community adopted Mono/C# over Java"?  If anyone knows.

I've had a lot of success using java in the Mono/Ikvm stack? Am I saying Ikvm runs java faster than sun's JRE? Of course not. Am I saying its more stable? Based on my experience, actually yes. This is a harsh bitter pill to swallow.

I don't know why java is failing. I don't know what Sun's malfunction is. I'm glad Mono exists, but the fact is, even if it didn't exist, I'd use C/C++, but not java. I've tried java. I gave it two years of my life. Maybe at some point in the future, if it survives, I'll give it another try.

In summary, its not so much that "mono" is favored. Its just that java is a pushy high-maintenance pseudo-intellectual college girl who won't put out. Mono watches "Fight Club" with you, and GET'S IT!!!!

---

### Post by Tibuda on 2009-03-04
> **ZuLuuuuuu said:**
> **Just because .Net is good does not mean free software community should give up their philosophy and use it**.How people give up free software philosophy by using Mono? It's released under LGPL.

---

### Post by cb951303 on 2009-03-04
> **danielrmt said:**
> How people give up free software philosophy by using Mono? It's released under LGPL.

+1, people tend to load new/untrue meanings to open source philosophy, when microsoft is the subject.

---

### Post by directhex on 2009-03-04
> **cb951303 said:**
> +1, people tend to load new/untrue meanings to open source philosophy, when microsoft is the subject.

The Archive Admins, however, are smarter than that. There is (c) Microsoft Free Software in the archive

---

### Post by nvteighen on 2009-03-04
The only issue I can see in Mono is a patent suit... but again, Microsoft doesn't seem to be willing to start one. No matter if there's a patent infringement or not by Mono, if the patent owner fails to defend its own rights by legal means, then the patent owner is almost surrendering its rights... and I can't believe Microsoft to be that stupid. So, it's most likely to be just a FUD campaign...

I wonder whether Mono could eventually sue Microsoft because of unfair competing. Just a thought.

---

### Post by cabalas on 2009-03-04
It is probably in Microsoft's best interest not to bring a lawsuit against mono, as mono gives them greater market penetration for less effort on their part.  If programmers are using mono then they are writing in a .Net language and if we are brutally honest Visual Studio is still the best .Net IDE out there (yes MonoDevelop is good, but it is just not that good yet) so programmers will keep using Visual Studio and by extension using windows with the reasonable assumption that the code they write will work (or work with a couple of minor modifications) on the different platforms that mono runs on.

---

### Post by arrancaru on 2009-03-04
Miguel de Icaza

---

### Post by orethrius on 2009-03-05
I refuse to get into the difference between software patents and copyrights, though I suspect someone else will explain it better than I ever could.

---

### Post by nvteighen on 2009-03-05
> **orethrius said:**
> I refuse to get into the difference between software patents and copyrights, though I suspect someone else will explain it better than I ever could.

Patents apply to ideas, where copyright applies to the way something is done (written, performed, whatever).

---

### Post by orethrius on 2009-03-05
> **nvteighen said:**
> Patents apply to ideas, where copyright applies to the way something is done (written, performed, whatever).

Right, but I was referring more to their practical applications as they pertain to Mono v Java.  I'm not going to get into that fight.

---

### Post by Keyper7 on 2009-03-05
Without even going into the patent issues, the main problem with Mono in my opinion is that it's always on a "catching up" state and it doesn't seem this is going to change any time soon. People who want to use the latest .NET 3.0 features can't do it and Moonlight just reached stable support of Silverlight 1.0.

---

### Post by orethrius on 2009-03-05
> **Keyper7 said:**
> Without even going into the patent issues, the main problem with Mono in my opinion is that it's always on a "catching up" state and it doesn't seem this is going to change any time soon. People who want to use the latest .NET 3.0 features can't do it and Moonlight just reached stable support of Silverlight 1.0.
Man, I *know* you're not citing catch-up between open standards and proprietary (closed) standards as a *fault*.  If anything, the closed standards created that problem.

---

### Post by directhex on 2009-03-05
> **Keyper7 said:**
> Without even going into the patent issues, the main problem with Mono in my opinion is that it's always on a "catching up" state and it doesn't seem this is going to change any time soon. People who want to use the latest .NET 3.0 features can't do it and Moonlight just reached stable support of Silverlight 1.0.

Which .NET features?

Mono contains all the *language* features (C# 3.0), and even features not yet found in MS.NET. The LIBRARIES is another matter - and frankly, one that makes **NO** difference to free software app development. We've had Linux-centric frameworks in Mono for YEARS, like GTK#. Nobody who develops Linux apps wants or cares about the extra libraries in .NET 3 and 3.5 - only the language features they already have.

The "playing catch-up" argument ONLY matters for people porting proprietary Windows apps to Linux (i.e. where a better, native GUI can't be injected), or for people using phantom arguments to attack a LINUX DEV PLATFORM. Mono was created to speed Linux app development, Windows compatibility is a secondary goal. Banshee or GNOME Do's devs don't give a crap whether they have access to WCF or whatever.

---

### Post by directhex on 2009-03-05
> **orethrius said:**
> Man, I *know* you're not citing catch-up between open standards and proprietary (closed) standards as a *fault*.  If anything, the closed standards created that problem.

[http://www.ecma-international.org/publications/standards/Ecma-335.htm](http://www.ecma-international.org/publications/standards/Ecma-335.htm)

There's the open standard Mono implements. Go nuts.

---

### Post by alternatealias on 2009-03-05
> **Keyper7 said:**
> Without even going into the patent issues, the main problem with Mono in my opinion is that it's always on a "catching up" state and it doesn't seem this is going to change any time soon. People who want to use the latest .NET 3.0 features can't do it and Moonlight just reached stable support of Silverlight 1.0.

By that argument, Java is (and always will be) playing "catch up" to .NET too (Java was late to the party adding Enum and Generics support, and are really late to the party adding closures). And Linux is playing "catch up" to Windows and MacOSX.

This is a pretty dumb argument.

---

### Post by alternatealias on 2009-03-05
> **ZuLuuuuuu said:**
> He could base his workings on Python (which was already being popular in Linux application development) or Parrot VM (which was started before Mono project I guess and leaded by another free software hero, Larry Wall) if he wanted a general purpose virtual machine.

Mono is several orders of magnitude faster than Python and the Parrot VM is not generic enough to be useful for much outside of Perl and Python (which are what it was designed for, because up until now Perl and Python have been using reference counted objects and fall flat on their faces when you have circular object refs).

The other problem with Python is that it is dynamically typed, which is great for prototyping, but horrible for writing final products in.

---

### Post by fevans on 2009-03-06
I don't think that Mono is favored. I think that C is favored, and for good reason. I think that Java has enjoyed a ten-year headstart, and has had ample opportunity to prove itself. So rather than being "against mono", Java proponents should simply focus on addressing the issues with java, and God forbid, maybe even learning from Mono. For example j/Invoke is a nice java/JNI replacement which borrows from .NET. 

Just to be clear, the above is not intended as a flame. Java isn't bad. In fact, its awesome.  But independent of any mono-discussion, java hasn't gained as much traction as one would expect for a stack that has so much potential.


Here's a nice blog from Linus about being "pro" versus "anti"
[http://torvalds-family.blogspot.com/2008/11/black-and-white.html](http://torvalds-family.blogspot.com/2008/11/black-and-white.html)


> **Keyper7 said:**
>   ... the main problem with Mono in my opinion is that it's always on a "catching up" ...

Keyper7, this is one of those universal truths, like "heavy things fall faster."  Might want to run a few tests to confirm it.

Based on 14 months of developing with mono, here's what I've found to be "not implemented".
========================================
1. System.Windows.Forms.WebBrowser: Technically this is implemented, but I don't have the gluzilla libraries. But a .NET developer wouldn't expect to worry about such things, so mono loses points on this one.

2. WWF (Windows Workflow Foundation). This isn't part of the ECMA standard. Still, it would be nice if it was cross-platform. The Olive project is a mono implementation, but it seems like its not moving forward as fast as the rest of mono.

3. Microsoft.DirectX.Direct3D.  Again not part of the standard. I don't even want to render anything. Just want to load meshes and DDS textures in linux and convert them. Oh well.

This is not the definitive list, but its what I've found in 14 months of development.

==========================
Trailing/Surging Ahead
==========================
People commonly mention the "trailing behind" objection. Its somewhat valid, but vastly exaggerated, and usually stated without an actual knowledge. But few people mention the "surge ahead" aspects of mono; specifically SIMD. Also, IKVM works with both .NET and Mono, but the Mono project gives it more importance.

---

### Post by ZuLuuuuuu on 2009-03-06
> **fevans said:**
> Here's a nice blog from Linus about being "pro" versus "anti"
[http://torvalds-family.blogspot.com/2008/11/black-and-white.html](http://torvalds-family.blogspot.com/2008/11/black-and-white.html)

Linus is probably the last person to tell us about being "pro" instead of "anti". He is always known of his "fanatical" opinions. Actually, he kinda admits it in the last paragraph. But it is never late for a change, hope he behaves like a pro after that entry :)

---

### Post by Keyper7 on 2009-03-06
**directhex** and **fevans**, thanks for the clarifications. I stand corrected.

And **alternatealias**,

> By that argument, Java is (and always will be) playing "catch up" to .NET too (Java was late to the party adding Enum and Generics support, and are really late to the party adding closures). And Linux is playing "catch up" to Windows and MacOSX.

This is a pretty dumb argument.

Java is not supposed to be a free implementation of .NET. Linux is not supposed to be a free implementation of Windows/OSX.

And that "dumb" was uncalled for.

Not only you didn't get my point, you were also rude without any reason. **directhex** and **fevans** understood what I meant, posted useful info and were *polite*. Learn from them.

---

### Post by orethrius on 2009-03-07
> **directhex said:**
> [http://www.ecma-international.org/publications/standards/Ecma-335.htm](http://www.ecma-international.org/publications/standards/Ecma-335.htm)

There's the open standard Mono implements. Go nuts.

Do not mistake my intent.  I don't believe he was comparing Java to Mono, but Mono to .NET.

[quote=Keyper7 (emphasis added)]Without even going into the patent issues, the main problem **with Mono** in my opinion is that **it's always on a "catching up" state** and it doesn't seem this is going to change any time soon. **People who want to use the latest .NET 3.0 features can't do it and Moonlight just reached stable support of Silverlight 1.0.**[/quote]

The self-defensive spin of "look how rude alternatealias is being" is a cute move though, I'll have to try it some time.

[quote=Keyper7]Java is not supposed to be a free implementation of .NET. Linux is not supposed to be a free implementation of Windows/OSX.[/quote]

Mono IS supposed to be a free implementation of .NET.  Linux IS supposed to be a free implementation of the WIMP-over-CLI model.  What's your argument, that alternatealias erred in his assessment of your point?

[quote=Keyper7]Not only you didn't get my point, you were also rude without any reason. directhex and fevans understood what I meant, posted useful info and were polite. Learn from them.[/quote]

I don't find it particularly cute that you acknowledge your supporters and discount your detractors.  From where I stand, he had a legitimate reason to make the Java connection; even if it isn't *your* point, you mustn't forget that it may well be *his* point.

---

### Post by Sorivenul on 2009-03-07
I enjoy the theoretical nature of this thread, and understand it can lead to points of contention, but, folks, we're flaming.

Debate is fine, but arguments and fingerpointing will get this thread closed, and I doubt we want that.

---

### Post by Keyper7 on 2009-03-07
> **orethrius said:**
> The self-defensive spin of "look how rude alternatealias is being" is a cute move though, I'll have to try it some time.

My main point was in the first sentence: "Java is not supposed to be a free implementation of .NET. Linux is not supposed to be a free implementation of Windows/OSX."

The rudeness part was an extra observation and not part of the argument. It seems you think I'm using the rudeness remark as an strategy because I have nothing better to say. However, the actual argument is there, in the first sentence, for everyone to see.

> **orethrius said:**
> Mono IS supposed to be a free implementation of .NET.  Linux IS supposed to be a free implementation of the WIMP-over-CLI model.  What's your argument, that alternatealias erred in his assessment of your point?

Precisely. Since Mono **is** supposed to be a free implementation of .NET, the "catching up" argument **makes** sense. Since Java is **not** supposed to be a free implementation of .NET, alternatealias' analogy does **not** make sense. And Linux is not supposed to be a free implementation of, specifically, **Windows or OSX**, so his analogy does not make sense in this case either.

> I don't find it particularly cute that you acknowledge your supporters and discount your detractors.

directhex and fevans both **said I was wrong**, so they are my "detractors" as well. That was precisely my point: you don't have to be rude to disagree with someone.

> From where I stand, he had a legitimate reason to make the Java connection; even if it isn't *your* point, you mustn't forget that it may well be *his* point.

I explained in the first sentence of my previous post, and above in this post, why the Java connection does not make sense and that my remark about the rudeness was unrelated to the point itself. I don't really see how I forgot from who was each point.

---

### Post by soltanis on 2009-03-07
BETTER QUESTION:

WHY DOES NO ONE APPRECIATE JAVASCRIPT?

I present to you exhibit (A), Rhino, which though it touts the ability to "compile" javascript into .class files, has the intended purpose of allowing embedding of js into java.

Exhibit (B), the Mono jscript compiler, which compiles jscript.net to the CIL.

Neither language gets much love (JScript.NET is mostly ignored and everyone seems to think that JavaScript/Rhino is only good for browsers/Java apps). Explain.

JavaScript has an excellent way to handle objects (functions are first-class objects, objects are prototyped not classed), anonymous functions (a page right out of Lisp), Regular Expressions (almost identical to Perl), and namespaces (although a namespace keyword might be nice).

With Java/.NET extensions JavaScript is a powerful language indeed. Screw C#. Why are we not using more J/Java/ECMA/Whatever you want to call it Script?

---

### Post by directhex on 2009-03-07
> **soltanis said:**
> BETTER QUESTION:

WHY DOES NO ONE APPRECIATE JAVASCRIPT?

I present to you exhibit (A), Rhino, which though it touts the ability to "compile" javascript into .class files, has the intended purpose of allowing embedding of js into java.

Exhibit (B), the Mono jscript compiler, which compiles jscript.net to the CIL.

Neither language gets much love (JScript.NET is mostly ignored and everyone seems to think that JavaScript/Rhino is only good for browsers/Java apps). Explain.

JavaScript has an excellent way to handle objects (functions are first-class objects, objects are prototyped not classed), anonymous functions (a page right out of Lisp), Regular Expressions (almost identical to Perl), and namespaces (although a namespace keyword might be nice).

With Java/.NET extensions JavaScript is a powerful language indeed. Screw C#. Why are we not using more J/Java/ECMA/Whatever you want to call it Script?

..................... so.................. Silverlight 1.0 then? :)

---

### Post by soltanis on 2009-03-07
That's not just JavaScript though, that's like all of .NET.

---

### Post by T.J. on 2009-03-07
The most obvious answer is that it lets Windows .NET programmers program Linux software.  There are a lot of Windows desktop programmers out there - given the extent of Microsoft's corporate culture - outnumbering Java ones, I'll risk as a guess. Microsoft developed C# after Java, so they tried to fix a few mistakes that they felt Java had in its design.

I think the biggest reason, (and this is not meant as a disparaging remark) is that part of the core team of GNOME are C# fans, particularly the well respected Miguel De Icaza (founder of GNOME). Mono, is of course, C#.  

I've programmed in both, and while they have nice semantics, I don't care for either. The point behind Java and C# is "compile once, run anywhere." The stated design purpose of both languages is all well and good, but seems pointless in an open source system.  

You don't need to write applications for a sluggish or buggy byte-code virtual machine when you have the original source code to compile for your native processor (or Ubuntu to do it for you).

---

### Post by directhex on 2009-03-07
> **soltanis said:**
> That's not just JavaScript though, that's like all of .NET.

Wrong.

SL1.0 really is just Javascript, used to mangle its own SVG-like layout system (XAML)

SL2.0 is .NETty

---

### Post by alternatealias on 2009-03-07
> **Keyper7 said:**
> My main point was in the first sentence: "Java is not supposed to be a free implementation of .NET. Linux is not supposed to be a free implementation of Windows/OSX."

The rudeness part was an extra observation and not part of the argument. It seems you think I'm using the rudeness remark as an strategy because I have nothing better to say. However, the actual argument is there, in the first sentence, for everyone to see.

My point was that it doesn't matter if Mono is behind .NET because the areas where Mono is behind don't prevent anyone from using Mono for its intended purpose.

Why does it matter if Mono's implementation of the Windows-only APIs is lagging? Do you need to use them? If so, how is Java any better?

Same goes for other languages like C or C++. Microsoft has a lot of useful libraries for those languages too, that Linux does not have. Does that mean that the C or C++ APIs available on Linux aren't useful?

Of course not.

Let's also note that Windows developers have been getting along just fine programming on Windows using .NET long before some of these latest .NET 3.5 libraries were written by Microsoft.

So obviously those libraries aren't required to write software. Thus your assertion that Mono is useless simply because it is lagging behind in a few areas is laughable at best.


> **Keyper7 said:**
> 
Precisely. Since Mono **is** supposed to be a free implementation of .NET, the "catching up" argument **makes** sense. Since Java is **not** supposed to be a free implementation of .NET, alternatealias' analogy does **not** make sense. And Linux is not supposed to be a free implementation of, specifically, **Windows or OSX**, so his analogy does not make sense in this case either.

Actually, my analogy DOES make sense.

Java has been playing catch-up to .NET the past few years by copying .NET's support for generics, closures, enums, etc.

If Mono is "playing catch-up" to .NET, then by your own argument, so is Java.

Besides, from what I've read, Mono's original intention is not to copy .NET fully, it was simply to make a usable cross platform VM for languages like C#. Copying all of the libraries that Microsoft adds on to .NET was never the objective AFAIK.

Mono is also ahead of .NET in areas like SIMD support (which is VERY important to a lot of developers) and their C# shell (which Microsoft will be copying for .NET 5.0).


In the end, developers should choose the language they feel best helps them to write the software they are working on. There is no one language to rule them all.

---

### Post by ajackson on 2009-03-08
> **T.J. said:**
> The point behind Java and C# is "compile once, run anywhere." The stated design purpose of both languages is all well and good, but seems pointless in an open source system.
Why is it pointless? Why should an open source system not benefit from cross platform capabilities of languages? Look at it another way, if good cross platform languages are available the the big software houses just might start making their apps available on linux, which in turn could help persuade some businesses to take up linux.
  
> You don't need to write applications for a sluggish or buggy byte-code virtual machine when you have the original source code to compile for your native processor (or Ubuntu to do it for you).
True you can compile it against sluggish and buggy libraries instead, libraries can contain bugs as easily as virtual machines can.

---

### Post by directhex on 2009-03-08
> **ajackson said:**
> Why is it pointless? Why should an open source system not benefit from cross platform capabilities of languages? Look at it another way, if good cross platform languages are available the the big software houses just might start making their apps available on linux, which in turn could help persuade some businesses to take up linux.
  

True you can compile it against sluggish and buggy libraries instead, libraries can contain bugs as easily as virtual machines can.

And Mono doesn't use a VM (I don't think Java does these days either), it uses a JITter

---

### Post by Asham on 2009-03-08
I know Java likes to use lots of RAM and since Mono/.NET runs on a platform similar to Java, does the same apply to Mono? 

No, let me paraphrase that: generally, performance wise, how does Mono compare to Java? Are there any tests floating around (that are not outdated)? /Adam

---

### Post by cb951303 on 2009-03-08
> **Asham said:**
> I know Java likes to use lots of RAM and since Mono/.NET runs on a platform similar to Java, does the same apply to Mono? 

No, let me paraphrase that: generally, performance wise, how does Mono compare to Java? Are there any tests floating around (that are not outdated)? /Adam

[http://shootout.alioth.debian.org/u32q/csharp.php](http://shootout.alioth.debian.org/u32q/csharp.php)
for the benchmarks they made java is 2-4 times faster but mono uses a lot less memory.

but I must add. when I use java application they don't feel as responsive/fast as mono. mono applications feels almost native fast to me.

---

### Post by Keyper7 on 2009-03-08
**alternatealias**,

It seems you are being too passionate in your replies and assuming I said things I didn't. Let me try to make things clear.

First of all, I **never, Never, NEVER, NEEEVEEER said Mono is useless or not enough to write software**. I just read my previous posts and I have absolutely no idea from where you got this from. My original post said "(...) the main problem with Mono in my opinion (...)". Put into the context of the thread: "why Mono favored over Java?". I gave **my personal personal reason why I prefer Java**. It was never my intention to claim Java is superior or to claim Mono is inferior. If you felt personally offended, and by the aggressivity and rude words in your posts I'd guess you did, I apologize.

Now let me explain my original point in details.

If I go to Mono's website, I read that its point is being an "open source implementation of Microsoft's .Net Framework". However, I believed that, compared to Microsoft's implementation of .Net, Mono was much less feature complete (Moonlight's support for Silverlight 2.0, for example). Therefore, if I have to choose between Mono and J2EE, I'd feel better in J2EE, where I'd be 100% sure that my applications would be completely portable.

**Before you reply to the previous paragraph**, let me make one thing clear: other posters already made me realise that the features Mono lacks are mostly irrelevant for Linux developers, so I already admit I'm wrong in this point.

So, as far as my original point goes, **the discussion is over and I was wrong.**

Now on to why your analogy didn't make sense.

The "catching up" argument I used for Mono refers to "something that's supposed to have the same set of features but currently does not". Java is **not** supposed to have the same set of features C# has. If they added features C# already had, it's because Sun thought they were worthy features, not simply "because C# has".

That's why your analogy didn't make sense, just like it wouldn't make sense to say that Java is catching up to Python because it does not have dynamic typing yet.

To make things even more clear: a valid analogy would be if there were no full implementation of the J2EE framework available for Linux. Then a developer could develop for J2EE without being 100% that his app would be portable. But having closures or not is irrelevant in this regard.

I hope this clarifies things.

---

### Post by igouy on 2009-03-08
> **cb951303 said:**
> [http://shootout.alioth.debian.org/u32q/csharp.php](http://shootout.alioth.debian.org/u32q/csharp.php)
for the benchmarks they made java is 2-4 times faster but mono uses a lot less memory.

but I must add. when I use java application they don't feel as responsive/fast as mono. mono applications feels almost native fast to me.

Note some of those Java programs are making use of more than one cpu core, [_here's a slightly different impression_]("http://shootout.alioth.debian.org/u32/csharp.php").

---

### Post by igouy on 2009-03-08
> **directhex said:**
> And Mono doesn't use a VM (I don't think Java does these days either), it uses a JITter

Is it possible that you are wrong about Mono?

["_Beyond the use of the Mono VM as Just-in-Time compiler_..."]("http://mono-project.com/Mono:Runtime")


And confused about what a VM is?

[_FOSDEM 2007 Java HotSpot Virtual Machine_ (pdf slides)]("http://openjdk.java.net/groups/hotspot/docs/FOSDEM-2007-HotSpot.pdf")

---

### Post by Simian Man on 2009-03-08
Simple.  Java is aimed at managers, not programmers.  C# is aimed at programmers.  There are very few managers in the Linux world, and a lot of programmers.

---

### Post by alternatealias on 2009-03-08
> **Keyper7 said:**
> **alternatealias**, ...

Keyper, apologies if you were offended; that was not my intention.

I guess in the meaning you were using "playing catch-up" it makes sense, but normally when people use that argument they mean "if it doesn't implement every last method that .NET has, it's not useful" or "if it's not bleeding edge, it's not useful". These arguments are clearly bogus.

I guess I read too much into what you were saying, assuming you meant it the same way most people who have used that argument in the past.

I'll be clear here and mention that I have used Java and have nothing against Java. I just prefer C# ;-)

---

### Post by Keyper7 on 2009-03-09
alternatealias, no hard feelings. I actually learned a lot from this thread. :)

I once used Java for almost everything. Nowadays I prefer using Python with C/C++ bindings for performance-critical parts.

I personally like this approach: SWIG can be a very powerful tool once you get used to it.

---

### Post by Shin_Gouki2501 on 2009-03-10
this is just a bit java/.Net related , well its Java related. I like very much how the speaker explains ( arround 30) how scala code is expanded into Java code. And then he decribes how good that workes with the Java JIT.


Just in case anyone here had doubts about the Java JIT ( i think i read somehting similar 2 or 3 pages ago)

[http://www.parleys.com/display/PARLEYS/Home#title=Scala;talk=10485769;slide=48](http://www.parleys.com/display/PARLEYS/Home#title=Scala;talk=10485769;slide=48)

---

### Post by DocForbin on 2009-03-10
> **Shin_Gouki2501 said:**
> [http://www.parleys.com/display/PARLEYS/Home#title=Scala;talk=10485769;slide=48](http://www.parleys.com/display/PARLEYS/Home#title=Scala;talk=10485769;slide=48)
Cool link, thanks.

---

### Post by jsmidt on 2009-04-12
Let's pretend I only use C#/Mono code/libraries/etc... which meet Debian's strong free licensing standards to do a project.  Is it theoretically possible to be sued by Microsoft?  Or would I have to dabble in the non-free stuff to get in trouble?

I guess another way to say it is: If I code using only Mono/C# code provided by Debian, could I theoretically get sued?

---

### Post by slavik on 2009-04-12
Tomcat, Jboss, WebSphere, WebLogic ...

---

### Post by Asham on 2009-04-13
> **slavik said:**
> Tomcat, Jboss, WebSphere, WebLogic ...

Do you mean to point something out by listing these Java applications? I don't quite see the point to be honset with you. :)

---

### Post by sakabato on 2009-04-13
> **Keyper7 said:**
> **alternatealias**,



If I go to Mono's website, I read that its point is being an "open source implementation of Microsoft's .Net Framework". However, I believed that, compared to Microsoft's implementation of .Net, Mono was much less feature complete (Moonlight's support for Silverlight 2.0, for example). Therefore, if I have to choose between Mono and J2EE, I'd feel better in J2EE, where I'd be 100% sure that my applications would be completely portable.
.

At least it runs on linux. Silverlight's counter part in java world , **JavaFX **totally ignores linux! How that sounds incomplete to you ?

---

### Post by directhex on 2009-04-13
> **jsmidt said:**
> Let's pretend I only use C#/Mono code/libraries/etc... which meet Debian's strong free licensing standards to do a project.  Is it theoretically possible to be sued by Microsoft?  Or would I have to dabble in the non-free stuff to get in trouble?

I guess another way to say it is: If I code using only Mono/C# code provided by Debian, could I theoretically get sued?

Could you? That depends on whether you worry about being sued by Microsoft for things like using Samba, GNOME, TCP/IP, and so on - i.e. "the risk is no higher than other things in Linux, and probably lower given the EMCA standardization process"

As smarter people than me have said, "you can't write more than 1000 lines of code without violating a software patent"

---

### Post by cb951303 on 2009-04-13
> **jsmidt said:**
> Let's pretend I only use C#/Mono code/libraries/etc... which meet Debian's strong free licensing standards to do a project.  Is it theoretically possible to be sued by Microsoft?  Or would I have to dabble in the non-free stuff to get in trouble?

I guess another way to say it is: If I code using only Mono/C# code provided by Debian, could I theoretically get sued?

You can't get sued! C# is an ECMA standard and the libraries you use are free. You don't even have to use standard .NET libraries. There is tons of Mono specific libraries + Glib which has probably everything you need.

---

### Post by pmasiar on 2009-04-13
> **cb951303 said:**
> You can't get sued! 

Yes, you can get sued by MSFT for most trivial things, like for using FAT file system. Check groklaw before dispensing free law advice.

---

### Post by alternatealias on 2009-04-13
> **jsmidt said:**
> Let's pretend I only use C#/Mono code/libraries/etc... which meet Debian's strong free licensing standards to do a project.  Is it theoretically possible to be sued by Microsoft?  Or would I have to dabble in the non-free stuff to get in trouble?

I guess another way to say it is: If I code using only Mono/C# code provided by Debian, could I theoretically get sued?

You could get sued for using any library as shipped by Debian over patents. It doesn't matter what programming language you use, be it C#, C, C++, Java, Perl, Python, LISP, Ruby, whatever.

If you stick to the ECMA portions of Mono, then you are safe from being sued by Microsoft (and Novell, Intel, HP, and a few others that offered their patents under RAND-Z for ECMA 334 and 335) for the usage of Mono.

HOWEVER!

1. The software *you* write might infringe on someone's patents if you write anything more complex than HelloWorld (doesn't matter what language you choose to use, this will always be true).

2. You are not safe from anyone else who may hold patents on algorithms used by Mono (or any other libraries you choose to use, no matter what language you choose to use).


For example, a few years ago Sun was sued by Kodak for infringing their patents in Java for $1 Billion. Kodak won. Sun paid up, but Java still infringes. Kodak can sue *anyone* that infringe those same patents (including developers using Java! They just can't sue Sun again.).


The end result is that if you are afraid of getting sued over patents, don't write or use software. Period.

The patent system is broken, but it is currently a fact of life in the US and some other countries where patents are valid.


Edit: I should note that it is extremely unlikely that any company would sue an individual such as yourself for infringing any of their patents because it would cost them far more than they'd get out of it, even if they won. Not to mention it'd make them look really pathetic to the public, and that would likely destroy them in the end.

---

### Post by slavik on 2009-04-13
> **Asham said:**
> Do you mean to point something out by listing these Java applications? I don't quite see the point to be honset with you. :)
They are java application containers/servers ... they even do clustering for your application automagically.

---

### Post by directhex on 2009-04-13
> **slavik said:**
> They are java application containers/servers ... they even do clustering for your application automagically.

And pretty much irrelevant in the context of the OP's question "Why has the gtk community adopted Mono/C# over Java"

At any rate, Tomcat was started in 1999 (Mono was started in 2002) and is largely Sun code, so no shocks there. The JBoss project also in 1999. Websphere in 1998. Weblogic in 1995. So I'm not convinced how much bearing a bunch of extremely mature webapp servers has on desktop development - nor why they used technology that actually existed when they began has any relationship to why they don't use Mono

---

### Post by slavik on 2009-04-13
> **directhex said:**
> And pretty much irrelevant in the context of the OP's question "Why has the gtk community adopted Mono/C# over Java"

At any rate, Tomcat was started in 1999 (Mono was started in 2002) and is largely Sun code, so no shocks there. The JBoss project also in 1999. Websphere in 1998. Weblogic in 1995. So I'm not convinced how much bearing a bunch of extremely mature webapp servers has on desktop development - nor why they used technology that actually existed when they began has any relationship to why they don't use Mono
My guess would be that there is no similar thing existing for languages other than Java. But anyway, this is turning into digression.

Back to topic ... OP, what makes you think that one is preferred over the other?

---

### Post by neighborlee on 2009-06-13
> **directhex said:**
> Could you? That depends on whether you worry about being sued by Microsoft for things like using Samba, GNOME, TCP/IP, and so on - i.e. "the risk is no higher than other things in Linux, and probably lower given the EMCA standardization process"

As smarter people than me have said, "you can't write more than 1000 lines of code without violating a software patent"

You consider the risk higher than other linux things, well thats a interesting take on the situation to be sure,   considering this :

[http://www.itwire.com/content/view/25215/1090/1/0/](http://www.itwire.com/content/view/25215/1090/1/0/)

I can't verfiy atm that a response was given, but after it is certainly a valid point in this topic.

and this:
[http://www.fsdaily.com/Legal/Patent_suit_tells_us_why_we_should_shun_Mono_Moonlight/related_links](http://www.fsdaily.com/Legal/Patent_suit_tells_us_why_we_should_shun_Mono_Moonlight/related_links)

SO its not  just a few fanatics worrying about this issue..unless one considers free software daily a radical jouranlist..dunno your call.

and then  we have this:
[http://nocturn.vsbnet.be/node/146](http://nocturn.vsbnet.be/node/146) < a free software enthusiast, love or hate him those are his views and he does seem to be a professional but then thats up to you to decide.

and here of course, feel free to mock it , but its valuable and credentials are more than tested:
[http://www.groklaw.net/article.php?story=20080528133529454](http://www.groklaw.net/article.php?story=20080528133529454) < and  she even < in case you think she's not to be trusted> even got a lawyer <  again, a professional > from: [http://www.softwarefreedom.org/](http://www.softwarefreedom.org/) < so I guess we can take this article with some deserved merit.

YOur choice as always to decide it yourself..but everyone no matter who they are deserve the facts, I hope everyone is in agreement with that ;)

I Hope this gives some more perspective to a sincere question someone had ;) There is no reason to fear truth .

cheers
nl

---

