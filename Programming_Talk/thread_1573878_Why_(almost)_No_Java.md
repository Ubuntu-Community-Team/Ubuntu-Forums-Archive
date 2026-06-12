---
title: "Why (almost) No Java?"
date: 2010-09-13
forum: Programming Talk
---

### Post by Majorix on 2010-09-13
It's a pretty popular language, and it is created with the idea of being redistributable among different operating systems.

However I only rarely see a programmer interested in Java on these forums.

Why is that?

---

### Post by borth92 on 2010-09-13
personally i have found java to be a bit of a limited and bloated language

---

### Post by simeon87 on 2010-09-13
It doesn't work too well either on Ubuntu, there's always something that's off.. buttons missing, half-displaying windows, no native controls, etc.

---

### Post by Simian Man on 2010-09-13
Java is a language that was designed for managers instead of programmers.  There are a lot more programmers in open source than managers.

---

### Post by dwhitney67 on 2010-09-13
> **Majorix said:**
> It's a pretty popular language, and it is created with the idea of being redistributable among different operating systems.

However I only rarely see a programmer interested in Java on these forums.

Why is that?

Because it is a fairly trivial language, that almost anyone with half-decent programming skills (and possibly a book) could pick up.

Which brings me to ask... do you have a Java programming question yourself?

If you don't, I believe Ubuntu Forums has a discussion board, which IMO, this thread should be tossed over there.  In fact, here's one site: [http://ubuntuforums.org/forumdisplay.php?f=11](http://ubuntuforums.org/forumdisplay.php?f=11)

---

### Post by endotherm on 2010-09-13
Java was closed-source until about 2 years ago, and the open alternatives prior to iced tea (blackdown for instance) didn't really work right to support apps written against the JRE and vice versa. 

java has been declining for some time, especially in relation to uptake of C# (which i describe as "java but with hindsight", or "java, but rational"). 
java is popular with business programmers (as is C#), but because of the interpreted runtime components, isn't really popular with the more systems oriented programmers that would frequent this locale.

---

### Post by KdotJ on 2010-09-13
Just to say, I'm a java programmer and there are occasionally a few java based threads on here. But remember ubuntu is mainly python orientated, and lower level Linux stuff is popularly done in a language like C

---

### Post by juancarlospaco on 2010-09-13
> **endotherm said:**
> Java was closed-source until about 2 years ago

java has been declining for some time

Dont worry Oracle will help on that.

---

### Post by Some Penguin on 2010-09-13
People are unlikely to be able to grok Java with as little effort as they might take up Bash or Python.  This forum is heavy in people at the level of "spot the syntax error" or "spot my failure to actually initialize my variables", not "how do I guard access to this structure with maximum concurrency" or "how do I interrogate this object to identify which method to invoke on a variable-sized array of parameters" or so forth.

---

### Post by r-senior on 2010-09-13
Java works perfectly well on Ubuntu and other Linux distributions. What is lacking is an attractive and accurate look & feel for the Swing APIs which provide the cross-platform GUI. If you are prepared to compromise on "write once, run anywhere", there are alternatives such as SWT (Eclipse IDE is written with Java and SWT for example) or the excellent but as yet incomplete [Java-Gnome bindings](http://java-gnome.sourceforge.net/).

Java is not an interpreted language. Java JIT compilation is different from the traditional compile/link model, happening dynamically as the program runs:

[Just-in-time_compilation]("http://en.wikipedia.org/wiki/Just-in-time_compilation")

I'd disagree that Java is a trivial language. The strength of Java comes from a higher level of abstraction and building on sophisticated APIs like the Servlet API for web applications and EJB/Spring for "back-office" functionality. You cannot write device drivers and operating systems in Java but it remains a popular choice for large-scale, complex, enterprise applications that require distributed transactions, message queues, clustering, massive scalability and so on.

At the other end of the scale, it's standing up to Apple and Microsoft's domination as the language for the Android mobile platform.

It's certainly not a popular choice for an individual writing GUI programs for Gnome, or someone who wants to hack around with device drivers and system software. But that doesn't mean it's not a useful language.

---

### Post by spjackson on 2010-09-13
> **juancarlospaco said:**
> 
[QUOTE=endotherm][I]Java was closed-source until about 2 years ago

java has been declining for some time[/I]

Dont worry Oracle will help on that.[/QUOTE]Do you mean that Oracle will help the decline, i.e. cause it to decline further?

---

### Post by KdotJ on 2010-09-13
> **r-senior said:**
> Java works perfectly well on Ubuntu and other Linux distributions. What is lacking is an attractive and accurate look & feel for the Swing APIs which provide the cross-platform GUI. If you are prepared to compromise on "write once, run anywhere", there are alternatives such as SWT (Eclipse IDE is written with Java and SWT for example) or the excellent but as yet incomplete [Java-Gnome bindings](http://java-gnome.sourceforge.net/).

Java is not an interpreted language. Java JIT compilation is different from the traditional compile/link model, happening dynamically as the program runs:

[Just-in-time_compilation]("http://en.wikipedia.org/wiki/Just-in-time_compilation")

I'd disagree that Java is a trivial language. The strength of Java comes from a higher level of abstraction and building on sophisticated APIs like the Servlet API for web applications and EJB/Spring for "back-office" functionality. You cannot write device drivers and operating systems in Java but it remains a popular choice for large-scale, complex, enterprise applications that require distributed transactions, message queues, clustering, massive scalability and so on.

At the other end of the scale, it's standing up to Apple and Microsoft's domination as the language for the Android mobile platform.

It's certainly not a popular choice for an individual writing GUI programs for Gnome, or someone who wants to hack around with device drivers and system software. But that doesn't mean it's not a useful language.

This.

Just as a note, the Gtk LookAndFeel of Java swing is not actually too bad. I have tried it under the default luicd theme and under the elementary theme, both look good to be honest (although it requires playing with component sizes a bit). Plus, Nimbus LookAndFeel is nice too.

---

### Post by CptPicard on 2010-09-13
I guess it mostly boils to the fact that Java is not particularly suitable for a lot of the "fun stuff" or your typical desktop app stuff, and the libraries used for enterprise applications are numerous and huge... and most hobbyists don't really write enterprise apps.

As a language, Java is just a little bit dull, that's all. It's your archetypical static-typed OOP language that forces the paradigm quite a bit on you, and doesn't have any of the higher-level features you typically find in post-Java HLLs. Even closures are crippled out of the language, as a matter of design decision!

I'd take some issue with the systems-programming point of view; there are quite a bit of HLL geeks, Lispers/pythonistas and such around here who do not really elevate systems programming on a pedestal and do not look down on Java for the classical "it lacks pointers" reasons. For me, although I actually work for a living with Java right now, it's actually not high level enough to be interesting :)

That said, Java is most certainly not declining anywhere; the architecture stacks (that run anywhere, not just on Windows) are going to be very, very hard to best in C#. A lot of infrastructure runs on Java even though the end-user rarely sees any of it.

---

### Post by GeneralZod on 2010-09-13
Re: popularity of Java in industry: I'm not sure how much credence to give it, but this site gives some very interesting information about the number of Java jobs available in the UK:

[http://www.itjobswatch.co.uk/jobs/uk/java.do](http://www.itjobswatch.co.uk/jobs/uk/java.do)

It shows a very steep drop in relative popularity from ~Jan '07 to ~Jan '09, followed by an almost equally steep rise from then until now, during which it claws back a lot of its losses.  Very odd - I wonder what drove this increase?

---

### Post by juancarlospaco on 2010-09-13
> **spjackson said:**
> Do you mean that Oracle will help the decline, i.e. cause it to decline further?

Ask to Google...

---

### Post by spjackson on 2010-09-13
> **juancarlospaco said:**
> Ask to Google...
You expressed an opinion. I was not clear about what you meant. Google will not clarify your meaning.

If you wish to remain cryptic, that's fine by me.

---

### Post by juancarlospaco on 2010-09-13
This place IS to write opinions.

*Google get on problems for using Oracle Java.*

---

### Post by GeneralZod on 2010-09-13
> **spjackson said:**
> You expressed an opinion. I was not clear about what you meant. Google will not clarify your meaning.

If you wish to remain cryptic, that's fine by me.

He's referring to this:

[http://en.wikipedia.org/wiki/Java_applet#The_2010_Oracle_-_Google_lawsuit](http://en.wikipedia.org/wiki/Java_applet#The_2010_Oracle_-_Google_lawsuit)

---

### Post by r-senior on 2010-09-13
I asked Google and it said ...

"[Oracle] takes on the new role as steward of Java technology with a relentless commitment to fostering a community of participation and transparency".

and then it said ...

"Oracle filed a patent infringement lawsuit against Google ...".

](*,)

---

### Post by juancarlospaco on 2010-09-13
Common sense Win

---

### Post by Some Penguin on 2010-09-13
There actually IS the ability to do some ahead-of-time compilation of Java.   The Excalibur JET system is one I've experimented with some time ago (roughly a year, IIRC); it takes Java code and class files, analyzes it, and produces native-code binaries.  I doubt that they're the only AOT compiler.

However, I'm not aware of any free AOT Java compilers, and generally speaking most people looking for performance improvements will find more significant gains with re-architecting or the like, or other more readily accessible optimizations.

---

### Post by maximinus_uk on 2010-09-14
> **GeneralZod said:**
> Re: popularity of Java in industry: I'm not sure how much credence to give it, but this site gives some very interesting information about the number of Java jobs available in the UK:

[http://www.itjobswatch.co.uk/jobs/uk/java.do](http://www.itjobswatch.co.uk/jobs/uk/java.do)

It shows a very steep drop in relative popularity from ~Jan '07 to ~Jan '09, followed by an almost equally steep rise from then until now, during which it claws back a lot of its losses.  Very odd - I wonder what drove this increase?

We had a recession

---

