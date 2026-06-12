---
title: "Programming C# inLinux"
date: 2008-02-26
forum: Programming Talk
---

### Post by Havok_CR on 2008-02-26
:popcorn:
Hi there :D
I'm starting a new semester in the university: Now is time for C# ...
...
It gets even worst ... Developing specifications: Visual Studio 2005, Microsoft C# compiler, Windows.
...
My system: Dual boot Ubuntu/Vista.
 I just don't want to boot in Vista, I hate it, I just have It installed because I'll need it eventually for programming things... But I don't want to program a whole semester in Vista, again, I hate it!
Anyway... after a long long discussion with the teacher... others teachers... others free software defenders and after specking a while about the implications of been TOTALLY attached to Microsoft, in OS, Compiler and IDE, the teachers gave us the green light to program in an alternative - a platform-independent alternative -.
I'm assuming that the best option is MONO, maybe I'm wrong. 
So, I'm thinking to program in MonoDevelop (IDE), Mono C# compiler and Ubuntu Linux Gutsy.
But I'm a little bit lost... like everything in the open community I have a lot of options... I wish that all the programmers that have already have this experience, programming C# in Linux, that gave me some advice about limitations, recommendations, warnings, ideas, IDEs, etc.

More specifically, I have 3 questions.
1. What packages I need to install to enable C# compile? mono, mono-gmcs or mono-mcs? The 2.0 especification is ready? And what about the 3.0?
2. The versions are so different from the lasted releases. For example, mono is 1.2.6 now but the mono package is 1.2.4. MonoDevelop is 1.0 RC1 nos but the package still 0.14. So what I do? I don't like to install software from source because I can't update It and I don't know how to uninstall them.
3. The FAQ: This is ready? I mean... Mono C# is a full compiler? MonoDevelop is ready to be used (1)? This quotation (2) really scarred me.

Well, thanks in advance, any suggestion is highly appreciated. 

(1) "MonoDevelop 1.0 Release Candidate 1 has been released. This new release includes plenty of bug fixes, and it is the last step before the final release of MonoDevelop 1.0".

(2) "New in Mono 1.2.5
Some statistics:
    * 1,907 new methods have been implemented. "

---

### Post by LaRoza on 2008-02-26
Use the tools used in class.

Don't try to force Linux on yourself.

Mono seems very complete, it implements the ECMA standard, and things that are not part of the standard. It may not be suitable for a class geared towards Windows.

There is a Windows version, if you want to use that as well.

If it doesn't work out, don't make life hard on yourself and use VS.

---

### Post by jviscosi on 2008-02-26
A few months ago, Microsoft released the 2008 versions of their freeware Visual Studio Express products, including Visual C# 2008 Express Edition.  I've used it a little bit and it's not bad.

(Would Visual Studio Express editions exist if not for OSS?  Would SQL Server Express Edition exist if not for MySQL?  I think not!)

---

### Post by Havok_CR on 2008-02-26
Thanks, but the problem is not if I need to choose Windows or Linux, this decision is already tacked. After all this "fight" (just talking :P) the teachers get very interested in Mono. Now, is official, I can present every program in the platform above mentioned, well... no I can... I must! Me, my partner and 4 others groups that were interested. The teacher saw the "Mono success stories" (1) and then he decided to try, C# still C#, even if we use other compiler. 
I've some experience with Visual Studio, but I want to learn something new :D
LaRoza, this class is not a Microsoft geared class, is a Data Structures class, all is theory, we never saw a piece of real code in class (the teacher write sometimes in C, others in Java, others in C++, others in C#, sometimes in something new that looks like C++ with Java... he a little bit crazy, for example .... cout>>"Something" and 3 lines after System.out.println("Something")... but everybody understood :D), but the homework need to be in some language, Python, Java, anyone, this doesn't matter, for this class, they choose C#. The teacher gave us this specifications, but after specking a while, the decided "why not, this is very interesting".
Anyway thanks for the reply.

(1) [http://www.mono-project.com/Companies_Using_Mono#Who_uses_Mono.3F](http://www.mono-project.com/Companies_Using_Mono#Who_uses_Mono.3F)

---

### Post by CptPicard on 2008-02-26
Uh... seriously, direct your FOSS advocacy efforts to singing the praises of success stories of a *complete and proper* FOSS stack instead of Linux plus some half-baked copy of a Microsoft technology.

Also, don't fight two fights at once; do not risk your class on insisting on using something that may not work or would work just barely, making you fight your tools when the point is to the passing the class, with good marks if possible...

The only saving grace I see here is that it's Data Structures, it will probably yield pretty well to code that can be "C# on any platform"...

---

### Post by Havok_CR on 2008-02-26
> **CptPicard said:**
> Uh... seriously, direct your FOSS advocacy efforts to singing the praises of success stories of a *complete and proper* FOSS stack instead of Linux plus some half-baked copy of a Microsoft technology.

Also, don't fight two fights at once; do not risk your class on insisting on using something that may not work or would work just barely, making you fight your tools when the point is to the passing the class, with good marks if possible...

The only saving grace I see here is that it's Data Structures, it will probably yield pretty well to code that can be "C# on any platform"...

Just passing the class... no... perhaps I'm an idealist... but my purpose and goal will never be "just to pass the class"... I'll do it, this is not the point, why is not the question, is how. If you don't have something concrete to say about the mono platform just ignore the thread, please. I have my reasons, I'm not here to discuss them, at least I wish to be understood :( .

I'm installing monodevelop and mono-gmcs, the repository versions. Wish me luck, because if I can program the QuickSort, MergeSort and others things for the next class I'll be installing those packages in my university Linux-based binaries server for my development projects.

---

### Post by CptPicard on 2008-02-26
> **Havok_CR said:**
> Just passing the class... no... perhaps I'm an idealist... but my purpose and goal will never be "just to pass the class"... I'll do it, this is not the point, why is not the question, is how.

"How" you should do it is to pass it with the best you can, of course, instead of giving you extra hindrances from the toolset. Put the extra effort into the actual classwork :)

---

### Post by Havok_CR on 2008-02-26
Sorry for my English, it's not my first language, I think I didn't express me right.
"Just passing the class... no... perhaps I'm an idealist... but my purpose and goal will never be "just to pass the class"... I'll (program C# in Linux), this is not the point, "why" is not the question, is "how"."

:P

The installation is done, I copied a 1000 lines VS C# program into MonoDevelop and it ran :D So far so good... it is doing well...

---

### Post by reverseblade on 2008-02-27
[B]1. What packages I need to install to enable C# compile? mono, mono-gmcs or mono-mcs? The 2.0 specification is ready? And what about the 3.0?
[/B]
- 2.0 and 3.0 specification is ready. To use it you need a version newer than 1.2.6 by default. if you are using 1.2.6 you can enable 3.0 specification by -langversion:linq option
[B]
2. The versions are so different from the lasted releases. For example, mono is 1.2.6 now but the mono package is 1.2.4. MonoDevelop is 1.0 RC1 nos but the package still 0.14. So what I do? I don't like to install software from source because I can't update It and I don't know how to uninstall them.[/B]

Do not uninstall any mono packages. Unfortunately ubuntu is a bit laggy on mono versions. Try to obtain packages from debian repos. It should work. 
[B]
3. The FAQ: This is ready? I mean... Mono C# is a full compiler? MonoDevelop is ready to be used (1)? This quotation (2) really scarred me.
[/B]
IMHO, mono is production ready. It has some bugs but mostly things go okay. For monodevelop, it's recent versions 0.18+ seems quite stable as well. But it is an RC anyway. The bad thing is MD does not support C# 3.0 syntax although the compiler supports

---

### Post by lnostdal on 2008-02-27
.. just a short note here .. 

i agree that installing software from source is a bad idea when you install it "globally as root" .. but, you can instead install software locally in your home folder .. that way it will be easy for you to "uninstall" it when you want to upgrade to a more recent version

i like your enthusiasm and the initiative btw. .. you should have no major problems pulling this off .. not at all

---

