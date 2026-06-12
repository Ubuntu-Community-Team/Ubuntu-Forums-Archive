---
title: "posibblility of os in jpython java python c"
date: 2007-08-09
forum: Programming Talk
---

### Post by bribaetz on 2007-08-09
would it be possible to make an os in one  2 or any combination or all of these languages

---

### Post by pmasiar on 2007-08-09
Linux kernel is in C :-)
neither Python, Java, or Jython were designed for programming OS (why - everybody knows we have C for that!)

You need to stop trying to start new projects and become if not expert, at least skilled coder in *any one* language. In the process, you will learn so much that you will be able to answer to many questions you are asking yourself.

Trust me, there are no shortcuts. It there could be, someone would tell you. There are none. Get a book, sit, read, learn. Don't waste your time, and our time :-)

---

### Post by slavik on 2007-08-09
umm, I remember reading about an OS written in Java (compiled to native code of course).

anything that uses C/C++ for the interpreter (eve you call it a virtual machine) can be compiled into native code and ran. :)

---

### Post by bribaetz on 2007-08-09
> **pmasiar said:**
> Linux kernel is in C :-)
neither Python, Java, or Jython were designed for programming OS (why - everybody knows we have C for that!)

You need to stop trying to start new projects and become if not expert, at least skilled coder in *any one* language. In the process, you will learn so much that you will be able to answer to many questions you are asking yourself.

Trust me, there are no shortcuts. It there could be, someone would tell you. There are none. Get a book, sit, read, learn. Don't waste your time, and our time :-)

im not trying to start a project especially one like that i was just curios i also didnt ask whether they were built for it but i have hear the use of multiple lesser languages being combined with a big language could make a powerful os python j python i have heard can be used to tie multiple languages together

---

### Post by bribaetz on 2007-08-09
> **slavik said:**
> umm, I remember reading about an OS written in Java (compiled to native code of course).

anything that uses C/C++ for the interpreter (eve you call it a virtual machine) can be compiled into native code and ran. :)

thanks

---

### Post by Wybiral on 2007-08-10
> **bribaetz said:**
> would it be possible to make an os in one  2 or any combination or all of these languages

Even if you could VIA interpreted... It wouldn't be worth it. Use C and assembly.

---

### Post by slavik on 2007-08-10
> **Wybiral said:**
> Even if you could VIA interpreted... It wouldn't be worth it. Use C and assembly.
*whine* but computers are cheap *whine* ... get it? ;)

---

### Post by Tepidbroth on 2007-08-10
> **slavik said:**
> umm, I remember reading about an OS written in Java (compiled to native code of course).

anything that uses C/C++ for the interpreter (eve you call it a virtual machine) can be compiled into native code and ran. :)

Solaris 10's entire desktop manager was written in Java (I think it's called Java Desktop Environment or something similar).  That's about the only OS I know of that uses Java (note: it's only the desktop that uses Java, the Kernel will be C/C++ as it's Unix).

---

### Post by Lster on 2007-08-10
I am programming an OS right now and am using assembly and C. I can't see how you could communicate with the hardware with java. It may be possible, but probably not worth it...

---

### Post by [h2o] on 2007-08-10
> **Lster said:**
> I am programming an OS right now and am using assembly and C. I can't see how you could communicate with the hardware with java. It may be possible, but probably not worth it...
You use specialized hardware ;)

---

### Post by Lster on 2007-08-10
Would that be like the processor being a JRE. I think I have heard of that...

---

### Post by [h2o] on 2007-08-10
> **Lster said:**
> Would that be like the processor being a JRE. I think I have heard of that...
I don't know, but I have heard something similar, and I don't see why it wouldn't be possible.

---

### Post by pmasiar on 2007-08-10
> **Tepidbroth said:**
> Solaris 10's entire desktop manager was written in Java 

Desktop is different - it is not as time critical as say process scheduler or filesystem.

"One laptop per child" project has desktop (Sugar) written in Python.

---

### Post by slavik on 2007-08-10
> **pmasiar said:**
> Desktop is different - it is not as time critical as say process scheduler or filesystem.

"One laptop per child" project has desktop (Sugar) written in Python.
umm, except the schedule should cater to ME instead of the apache server I have in the background. this is the reason one of the kernel devs left (forget his name already :()

nice -19: schedular and things that MUST get done for system to be stable
nice -18: INTERACTIVE USER
nice -17 to +19: everything else

scheduling and such cannot be avoided, but the interactive user is something that you should attend to right this moment and get rid of him, then you can go about all other tasks.

here's a scenario:
you are carrying a large object and your child is next to you. child falls and scrapes his knee or hurts himself, whatever (pouint is you need to attent to him).

here's the typical parent reaction:
- put down the heavy object
- take gloves off
- attend to the child
- go on with rest of the stuff ...

if your child would hurt himself while you are getting change from the cashier, would you ask your child to wait while you put money away properly (file system stuff?) or do you somehow throw it in your pocket (to be sorted later), or even ask the cashier to hold on for some time and attend to your child?

the dev's argument was that apache has the same priority to the system as an interactive user and even though throughput is high, the system feels slow (because isntead of opening a 5kb file you want, the system decides to open the 5gb file apache wants) or something similar.

---

### Post by pmasiar on 2007-08-10
> **slavik said:**
> umm, except the schedule should cater to ME instead of the apache server I have in the background. this is the reason one of the kernel devs left (forget his name already :()
...
the dev's argument was that apache has the same priority to the system as an interactive user and even though throughput is high, the system feels slow (because isntead of opening a 5kb file you want, the system decides to open the 5gb file apache wants) or something similar.

I cannot see through your analogy. If you need fast desktop, why would you run apache, and the one opening 5GB files? Or if you do, why not change apache priority?

I still cannot see how your example is relevant and what it proves. In desktop, flexibility of use is of most importance (with decent speed), IMHO.

Anyway, those are engineering decisions, about priorities, preferences, and cutting different corners. Use the one which suits your needs best.

---

### Post by bribaetz on 2007-08-10
what about C#

---

### Post by giganerd on 2007-08-10
The idea that anyone would use any language other than C (maybe C++) and assembly to write an operating system (read: kernel) is ridiculous to me.  C compiles pretty directly to assembly and machine code and has been around for awhile, so you know gcc (and other C compilers) are very well optimized.  C gives you that low-level hardware interaction that the kernel needs and allows you to link and write inline assembly when you have to (and you will).  I don't know if languages like Java and Python allow you to do inline assembly (my instinct says no) and I doubt native compilers for them create as nice of machine code as good ol' gcc does.

In essence, brush up on computer architecture and you'll start to understand why trying to code a kernel in languages like Java and Python is just plain silly.

---

### Post by Tepidbroth on 2007-08-10
> **bribaetz said:**
> what about C#

C# is Microsoft's copy of Java basically.  Microsoft needed a language for their .NET platform (distributed computing basically).  Java was designed, originally, to create software for Sun's set top box project in the early 90's.  The set top box project failed but Java took off anyway because it was designed to be platform independent and great for programming over networks (applets were popular in the late 90's).  

C# is Microsoft's version of Java because they got sued by Sun Microsystems for trying to copy it or something.  So they made their own distributed computing language.  

Both Java and C# are good for distributed software and embedded systems, but you couldn't really design an operating system with them.  The reason is that they compile to bytecode (in C#'s case it compiles to CLI or Common Language Runtime) which is then interpreted to machine code (thus taking longer than C/C++ to run which are compiled straight to machine code).  

In order to design and implement an OS you'd need to use a language that could directly interface with hardware.  For example, both Java and C# don't allow the programmer to use pointers (direct references to memory locations).  You'd need to manage memory directly if you were designing an OS.

Disclaimer: I'm still learning about programming (primarily Java and C just now) so I may have some of the above details wrong.

---

### Post by slavik on 2007-08-10
> **giganerd said:**
> The idea that anyone would use any language other than C (maybe C++) and assembly to write an operating system (read: kernel) is ridiculous to me.  C compiles pretty directly to assembly and machine code and has been around for awhile, so you know gcc (and other C compilers) are very well optimized.  C gives you that low-level hardware interaction that the kernel needs and allows you to link and write inline assembly when you have to (and you will).  I don't know if languages like Java and Python allow you to do inline assembly (my instinct says no) and I doubt native compilers for them create as nice of machine code as good ol' gcc does.

In essence, brush up on computer architecture and you'll start to understand why trying to code a kernel in languages like Java and Python is just plain silly.
in 1980's, there used to be LISP machines which had the hardware to perform every LISP instruction. :)

---

### Post by bread eyes on 2007-08-10
You can make an OS out of any complete language; You just need the right compiler.

---

### Post by xtacocorex on 2007-08-10
> **Tepidbroth said:**
> C# is Microsoft's copy of Java basically.  Microsoft needed a language for their .NET platform
C# is an international standard, Microsoft has taken it and put in their .NET API.  Because C# is an international standard, anyone can make an interpretor or whatever C# uses to run.  I've never used the language and never will.

---

### Post by slavik on 2007-08-10
> **xtacocorex said:**
> C# is an international standard, Microsoft has taken it and put in their .NET API.  Because C# is an international standard, anyone can make an interpretor or whatever C# uses to run.  I've never used the language and never will.
except sun provides more support for java, than mcirosoft does for .net :)

---

### Post by pmasiar on 2007-08-10
> **xtacocorex said:**
> C# is an international standard, Microsoft has taken it and put in their .NET API.  Because C# is an international standard, anyone can make an interpretor or whatever C# uses to run.  

Danger is not in language itself, but in libraries. Language without libraries is useless. Free libraries have to reimplement .NET, where MSFT claims to have patented tricks. Patent is very strange beast, you are not allowed to reinvent it yourself, even if it is obvious. Well, if it is obvious patent should not be granted, but if it was, it is about your budget for lawyers against MSFT budget, not about truth or fairness.

BTW do you know folks that William H Gates III studied in Harvard to become lawyer like his dad? And it shows.

---

### Post by xtacocorex on 2007-08-10
But .NET is not part of the C# standard; therefore, you could have a pure language without it.

People get caught up in the fact that C# is actually a Microsoft language, but it is an ISO standard; they just implemented it first and threw in their own pieces, just like Visual C++ has it's own non standard C++ syntax.

Why try to reimplement .NET in Linux?  From my standpoint, it's a fairly worthless library.

---

### Post by pmasiar on 2007-08-11
> **xtacocorex said:**
> But .NET is not part of the C# standard; therefore, you could have a pure language without it.
...
Why try to reimplement .NET in Linux?  .

hmmm let me see why would anyone use C#? maybe to run same apps on windows and Linux, why else? Could be hard without the .NET libraries tho... :-)

---

### Post by bribaetz on 2007-08-11
well on another note how do you get graphics and buttons in python

---

### Post by slavik on 2007-08-12
> **bribaetz said:**
> well on another note how do you get graphics and buttons in python

by using a toolkit library. python has bindings to gtk, tk and wxwidgets I believe (don't know about qt)

---

### Post by ssam on 2007-08-12
> **pmasiar said:**
> Desktop is different - it is not as time critical as say process scheduler or filesystem.

"One laptop per child" project has desktop (Sugar) written in Python.

more than that.

> 
The solution is python, everything we can reasonably implement on python on this machine will be implemented in python and I really mean almost everything, we're talking GUI, window manager, presence, communications, system boots, init daemons, security service, platform crypto, filesystem, search, basically almost anything that transforms user space and can be done in python, will be done in python. There are exceptions of course, we're not going to be re-implementing X.org in python as fun as that would sound, the avahi demon is not something we really want to re-implement, the way we do sound, the way our system bus IPC works, these are the things which are going to stay pretty much intact and we are not going to be re-implementing them.

And when I run through the list of the stuff that we want to implement in python, I sort of mentioned file system in quotes and you know, people usually go "hunh?" you're going to write the filesystem in python. The answer is yeah. We're trying to do something pretty different here. We're creating a centralized storage for user documents on the machine, that's essentially a big object store. And if you do this, you get some pretty incredible things that then the operating system can do for your documents, you get version control on all of the user documents that you have on the machine. You get efficient n-way synchronization and you can get delta compression and track all the metadata. Really, its like putting your entire machine under very advanced version control that can do the right thing. and in addition to this you get sort filtering, timeline, of things that are happening on your machine, you can ask the machine, show me everything that I did yesterday, which you cant really easily do on your computer.

[http://www.olpctalks.com/ivan_krsti/ivan_krstic_at_google.html](http://www.olpctalks.com/ivan_krsti/ivan_krstic_at_google.html)

but still i think on normal CPUs you would need a kernel and python interpreter in something that can be compile into a native binary.

there are processors that run java [http://en.wikipedia.org/wiki/Java_processor](http://en.wikipedia.org/wiki/Java_processor) . so it probably possible run a java os on one of those. i found [http://cjos.sourceforge.net/archive/](http://cjos.sourceforge.net/archive/) with a bit of searching.

---

### Post by bribaetz on 2007-08-12
java still would not be good for wide  use C++ seems much better and eisier.

---

### Post by CptPicard on 2007-08-13
> **bribaetz said:**
> java still would not be good for wide  use C++ seems much better and eisier.

I would really want to hear some of your wisdom about that... how so?

I write Java stuff professionally myself, and am fairly "fluent" in C++. Frankly, C/C++ have their place when required, but especially in C++, the added complexity is just a bit much. And no, this is not a C++-hating statement, I'm just saying that if you can get away with a garbage-collected language that lets you manipulate just general references to all objects that aren't primitives on stack, I say go for it...

---

### Post by bribaetz on 2007-08-13
java seems to be about as hard as CPP but not as good and my sentence was meant for java processor  and java os

---

### Post by pmasiar on 2007-08-13
> **CptPicard said:**
> I would really want to hear some of your wisdom about that... how so?

can get away with a garbage-collected language that lets you manipulate just general references to all objects that aren't primitives on stack, I say go for it...


CptPicard, in case you missed it so far, bribaetz is perfect example of "One fool can ask more questions in a minute than twelve wise men can answer in an hour."  [Most recent example](http://ubuntuforums.org/showpost.php?p=3184484&postcount=8)

Bonus link: [more good quotes](http://www.creativequotations.com/tqs/tq-wisdom.htm) about fools and wise men, see #19 :-)

I doubt bribaetz can tell "stack" from "garbage collector", now bribaetz can you? Maybe garbage can get into stack? If not, why not? :-)

> **bribaetz said:**
> java seems to be about as hard as CPP but not as good 

bribaetz: why so? How C++ differs from Java, in your POV? Show us you learned something as you promised.

---

### Post by CptPicard on 2007-08-13
I am fully aware that he is a ... uhm.. "funny guy" as someone pointed out. And because I am a patient Jedi Master and want to see if our children is learning, I'm asking him to provide some grounds for his ideas. :)

---

### Post by pmasiar on 2007-08-13
> **CptPicard said:**
> I am fully aware that he is a ... uhm.. "funny guy" as someone pointed out. And because I am a patient Jedi Master and want to see if our children is learning, I'm asking him to provide some grounds for his ideas. :)

me too, hehehehe :-)

Just the word "wisdom" in your reply confused me, all clear now :-D

Now it becomes interesting.... Let's sit and watch. Google and wikipedia are allowed, I guess.

---

### Post by Wybiral on 2007-08-13
```
.  !  ?  ,  "  ()
```

Please use them, it is very hard to read what you write (and thus give an appropriate response).

Also... Firefox has a built in option you can enable that will underline misspelled words as you type. It's very handy.

---

### Post by pmasiar on 2007-08-16
bump.

bribaetz, still reading? :-)

---

### Post by bribaetz on 2007-08-17
> **pmasiar said:**
> CptPicard, in case you missed it so far, bribaetz is perfect example of "One fool can ask more questions in a minute than twelve wise men can answer in an hour."  [Most recent example](http://ubuntuforums.org/showpost.php?p=3184484&postcount=8)

Bonus link: [more good quotes](http://www.creativequotations.com/tqs/tq-wisdom.htm) about fools and wise men, see #19 :-)

I doubt bribaetz can tell "stack" from "garbage collector", now bribaetz can you? Maybe garbage can get into stack? If not, why not? :-)



bribaetz: why so? How C++ differs from Java, in your POV? Show us you learned something as you promised.

did you call me a fool hey buddy i just started programming maybe i am a fool but it takes one to know one

---

### Post by AnRa on 2007-08-17
> **bribaetz said:**
> what about C#[Singularity](http://en.wikipedia.org/wiki/Singularity_%28operating_system%29)

---

### Post by bribaetz on 2007-10-28
now i do believe i know why most of those languages can not right an os, but wouldn't it be possible to right a desktop environment on top of the operating system so that the language would be integrated into the os but still act as part of it but not literally be a part of it?

---

### Post by Mathiasdm on 2007-10-28
> **bribaetz said:**
> now i do believe i know why most of those languages can not right an os, but wouldn't it be possible to right a desktop environment on top of the operating system so that the language would be integrated into the os but still act as part of it but not literally be a part of it?

Can you describe that a bit more clearly?

I understand your text as: write the OS in C, and write a desktop environment in another language.

---

### Post by bribaetz on 2007-10-28
yeah thats about it i mean wouldn't that make the whole thing more light wait

---

### Post by Mathiasdm on 2007-10-28
A way to make it 'light weight' would be to write both the OS and the desktop environment in a language like C, but that would also take lots of development time.

A desktop environment in a higher-level language would be 'heavier', but take less time to create.

It depends on your needs ;-)

---

### Post by Ramses de Norre on 2007-10-29
Many mobile phones, mp3 players, ... have an OS written in Java, but they don't have x86 processors, their processors are embedded JRE's (the mobile version, a full one would be quite big for those devices).
I don't think you can circumvent assembly and C on an x86 processor.

---

### Post by pmasiar on 2007-10-29
Using Forth, is is easy (and trivial) to write self-hosting OS, even I was able to do it! :-)

Forth is excellent for embedded systems, it is [Raison d'être](http://en.wikipedia.org/wiki/Raison_d'%C3%AAtre) of Forth. Code cannot get any more compact than Forth does it, and it is almost as fast as ASM (code is compiled, no run-time interpreter). If you are interested in embedded systems, take a look and check if you have what it takes to handle the sharp and dangerous toll as Forth without question is. It is not as simple as Java, but it is ahhh so much more compact and powerfull!

---

