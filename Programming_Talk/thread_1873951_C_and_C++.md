---
title: "C and C++"
date: 2011-11-02
forum: Programming Talk
---

### Post by Drenriza on 2011-11-02
Hi all.

I'am wondering if i wanna get into one of these languages. But i need more info :)

Do you see any reason, that C will be killed / sourced out in the future? As i understand it's a legacy language?

Can C++ be run native on linux? I have used some time on C# but this cannot run native :(!!! on linux and i have had problems with mono on the 4.0 / 4.5 of the .NET framework. Where mono does not support the newer functions.

If you want to develop programs for linux, windows AND os x can u use C or C++ native on all of those? When i think programs i think in monitoring programs and such, not games.
Programs to delete files, and call functions to edit databases and so on in that regards. System administration really.

Is it "hard" to go from C# to C or C++? I know that both C# and C++ is object orientated. And i like this, C is structure based? What does this mean?

I would also like to get into Linux kernel work at sometime, is this ONLY C or does it also use some C++?

P.S
I think it's a damn shame that Ubuntu docent incorporate mono directly into the OS on both the Desktop and Server edition. Where as this can get upgraded with apt-get, like any other package. Since i really like C#

Thanks all on advance.
Kind regards.

---

### Post by WasMeHere on 2011-11-02
Good luck with C and C++, Drenriza,

I think they will survive, particularly for tasks that need fast execution, because it makes compiled code (not interpreting high level code).

But I think that there are convenient tools for many simple tasks, that can be done with shellscripts, but will be more user friendly with a GUI. One such tool is *KDialog*, that can be used to show nice dialog boxes from shell scripts. Install it with
```
sudo apt-get update
sudo apt-get install kdebase-bin
```

Have fun finding out :-)
Olle

---

### Post by karlson on 2011-11-02
> **Drenriza said:**
> Hi all.

I'am wondering if i wanna get into one of these languages. But i need more info :)

Do you see any reason, that C will be killed / sourced out in the future? As i understand it's a legacy language?

C will still be around active in the foreseeable future.

> 
Can C++ be run native on linux? I have used some time on C# but this cannot run native :(!!! on linux and i have had problems with mono on the 4.0 / 4.5 of the .NET framework. Where mono does not support the newer functions.


What do you mean by "native"?  C++ just like C# is compiled into machine code which runs native in the architecture it is compiled for.  The OS the program is compiled on determines the executable format and you can specify libraries linked at that time as well (like .NET framework).

> 
If you want to develop programs for linux, windows AND os x can u use C or C++ native on all of those? When i think programs i think in monitoring programs and such, not games.
Programs to delete files, and call functions to edit databases and so on in that regards. System administration really.


C and C++ can be compiled on any OS for which C and/or C++ compilers exist.

> 
Is it "hard" to go from C# to C or C++?

C might be harder then C++....
> I know that both C# and C++ is object orientated. And i like this, C is structure based? What does this mean?

It means that in C++ and C# you are thinking in terms of objects or classes, so an object which is a collection of data has certain methods(interface) exposed to its user which you can call.  The encapsulation basically hides the details of how the object is laid out and internal manipulation functionality from the objects user.
C doesn't give you that...  Data for one has to be passed to the function that will manipulate it and any function declared can be called from any other function as long as declaration has been made available prior to the call.

> 
I would also like to get into Linux kernel work at sometime, is this ONLY C or does it also use some C++?

C last I checked.

> 
P.S
I think it's a damn shame that Ubuntu docent incorporate mono directly into the OS on both the Desktop and Server edition.
Where as this can get upgraded with apt-get, like any other package. Since i really like C#


Create yourself a custom build which you can deploy which will include C# and you can deploy it as needed.  Since most libraries in Linux have been written in C or C++ I don't see any reason for Mono to be in as a default installation.

---

### Post by 3Miro on 2011-11-02
> **Drenriza said:**
> 
Do you see any reason, that C will be killed / sourced out in the future? As i understand it's a legacy language?

You understand wrong. Every OS currently on the market is written primarily in C (which includes Windows, Linux and OSX). At the present moment, there is no language capable of replacing C.

Don't get so much into the hype of C#, Java and Python. Those are great languages, however, they are rather task specific. At their core, C#, Java and Python are actually written in C (incidentally C is also written in C).

> 
Can C++ be run native on linux? I have used some time on C# but this cannot run native :(!!! on linux and i have had problems with mono on the 4.0 / 4.5 of the .NET framework. Where mono does not support the newer functions.

C++ is an extension of C. C++ gives you objects like in C#, in terms of syntax C++ and C# are similar, although they are quite a bit different. Most applications in the Ubuntu Software center are written in C++, it is as native as it gets.

> 
If you want to develop programs for linux, windows AND os x can u use C or C++ native on all of those? When i think programs i think in monitoring programs and such, not games.
Programs to delete files, and call functions to edit databases and so on in that regards. System administration really.

As I said, Windows, Linux and OSX are all written in C. You can make C applications to do administration on all three systems, however, the way you interact with the OS can be different in all cases. You can write system tools for all 3 OS, however, you will probably be unable to use the code directly. At the very least, you will have to recompile your code and quite a bit of it will have to be different in each case.

The preferred language for system administration under Linux is Bash. It is much easier to work with. OSX supports bash, although I am not sure if it is their default. I don't think you can use Bash under Windows (with cygwin maybe, be this is not what you want to do for real system administration).

> 
Is it "hard" to go from C# to C or C++? I know that both C# and C++ is object orientated. And i like this, C is structure based? What does this mean?

Coming from C#, C++ would be easier. Starting from scratch, I think C is easier.

C++ and C# use objects, that encapsulate data structures and functions together. C++ and C# enforce a style of programming. You can do "object oriented programming" under C, without the use of classes, just data structures. You can view C as being "less restrictive" in that way, although that can be seen as both good and bad.

> 
I would also like to get into Linux kernel work at sometime, is this ONLY C or does it also use some C++?

C only. At such a low level, all OS are C only.

> 
P.S
I think it's a damn shame that Ubuntu docent incorporate mono directly into the OS on both the Desktop and Server edition. Where as this can get upgraded with apt-get, like any other package. Since i really like C#

Thanks all on advance.
Kind regards.
I thought mono was available in the Software Center. It is not installed by default since there are so few applications written in C# for Linux. In the Linux world, Python is more popular and it is installed by default.

---

### Post by trent.josephsen on 2011-11-02
Personally I'd say C has (if anything) more future than C++ at this point.  The benefits of C++ for applications programming can be better implemented in a language that doesn't try to be simultaneously backwards-compatible with C.  And when you strip C++ down to what makes it best for low level stuff, you basically get C.

That said, there is a HUGE amount of code written in C++ and none of it is going to spontaneously disappear.  Even if it goes the way of COBOL, that probably means job security for upwards of 50 years (especially once all the script kiddies and incompetent CS1 students have moved on to some other language).  And that's an extreme case.

Why is it so important that what you want be "native"?  System administrators IRL typically use scripting languages like Perl or Python, and if you're writing something to automate away mundane tasks, one of those is probably a much better option.

---

### Post by 11jmb on 2011-11-02
> **trent.josephsen said:**
>  System administrators IRL typically use scripting languages like Perl or Python, and if you're writing something to automate away mundane tasks, one of those is probably a much better option.

OP mentioned kernel development, so it would be better to stick to C to reach that goal.

If you have any decent programming experience, learning a new language should not be too much of a challenge. You should know going in that C# is a much gentler language than C or C++. When programming in C/C++ you will have to manage memory instead of relying on garbage collection, and there will be many other small things that C# takes care of that you will now have to handle.

---

### Post by Drenriza on 2011-11-02
> Why is it so important that what you want be "native"? System administrators IRL typically use scripting languages like Perl or Python

I also use bash, awk and sed (in a combo) to get what i want from scripting. But in the current company i work, i do not get the option to install libraries on live systems, for the cause that the R&D are afraid of resource shortage. Don't ask me why, since the system utilization is no way near max at any times (unless a program facks up) and then its through the roof.

> Create yourself a custom build which you can deploy which will include C#
Can u explain this? Since i'am not 100% sure how one would do such a thing :p

Also, i can get a lot of things done in bash/sed/awk but i would like to advance and get to the next level of programming. Where i have used C# before, to get an understanding of object orientated programming.

---

### Post by Fallen_Demon on 2011-11-02
> **Drenriza said:**
> 
Do you see any reason, that C will be killed / sourced out in the future? As i understand it's a legacy language?

Bust out the Linux kernel source. Pretty much everything is C and assembler

> **Drenriza said:**
> 
Can C++ be run native on linux? I have used some time on C# but this cannot run native :(!!! on linux and i have had problems with mono on the 4.0 / 4.5 of the .NET framework. Where mono does not support the newer functions.

C++ compiles to run natively on *NIX, yes. Use the g++ compiler

> **Drenriza said:**
> 
If you want to develop programs for linux, windows AND os x can u use C or C++ native on all of those? When i think programs i think in monitoring programs and such, not games.
Programs to delete files, and call functions to edit databases and so on in that regards. System administration really.

Don't use C or C++ if you want to move across all three. You're best off using a higher level language like Python, Ruby or Java. All of those have a proven track record in cross platform compatibility, and believe me, it'll be less hassle to do what you need to 

> **Drenriza said:**
> 
Is it "hard" to go from C# to C or C++? I know that both C# and C++ is object orientated. And i like this, C is structure based? What does this mean?

Syntax-wise: No.
Everything else-wise: Yes
C and C++ will force you to learn how to control your memory allocation. I love C and the 'enough rope to hang yourself and everyone else on your block' mentality, but pointers are damn confusing when you first come across them. Just remember to always free up your memory and reap old processes and you'll be ok after some practice

> **Drenriza said:**
> 
I would also like to get into Linux kernel work at sometime, is this ONLY C or does it also use some C++?

C++ doesn't give the hard timing guarantees required by the kernel, not to mention certain functions like delete need OS support and some of the weird tricks during compilation that you just can't do in kernel space. However, the kernel does provide some nice libraries for you to do most simple things in C without too much trouble, along with some nice data structures. 

I started off with the networking stack and USB video drivers if you want a good launching point ;)
> **Drenriza said:**
> 
P.S
I think it's a damn shame that Ubuntu docent incorporate mono directly into the OS on both the Desktop and Server edition. Where as this can get upgraded with apt-get, like any other package. Since i really like C#

Thanks all on advance.
Kind regards.
Nah, you don't need mono. Ubuntu server is basically a drop-and-configure type thing. You will generally run it headless. I remember one server I set up I connected a screen to it once, and that was to set up the NIC so I could SSH into it. If you're doing vanilla-ish stuff like hosting a website (C# is great and all, but the only reason I'd use it is if I needed to be talking to an MS SQL DB), routing or using it as a mail server, you probably won't need to install anything other than what's on the CD

> 
Can u explain this? Since i'am not 100% sure how one would do such a thing 

Custom builds are kind of like Windows images if you've ever used them. Basically (nowadays, anyway), you get a distro building tool like SUSE Studio or the SLAX builder (not sure if there's an Ubuntu equivalent, never needed it), select your packages, press a button and BOOM. You're done. SUSE studio is an online one, and you can keep your distro up to date pretty easily :)

> 

I also use bash, awk and sed (in a combo) to get what i want from scripting. But in the current company i work, i do not get the option to install libraries on live systems, for the cause that the R&D are afraid of resource shortage. Don't ask me why, since the system utilization is no way near max at any times (unless a program facks up) and then its through the roof.


Those are some pretty core utilities. They should be there

> 

I thought mono was available in the Software Center. It is not installed by default since there are so few applications written in C# for Linux. In the Linux world, Python is more popular and it is installed by default.

Banshee is written in C#.... Gwibber is as well, I think...

---

### Post by karlson on 2011-11-02
> **Drenriza said:**
> 
Can u explain this? Since i'am not 100% sure how one would do such a thing :p

The easiest would be:
[LIST]
[*]Build base system
[*]Install all packages that you would like to see
[*]On any system that you want to have this list deployed run: dpkg --set-selections < list ; apt-get dselect-upgrade
[*]Use it in Orchestra as needed.
[/LIST]
The model is similar to RedHat's Kickstart or Solaris' Jumpstart.

---

### Post by trent.josephsen on 2011-11-02
> **11jmb said:**
> OP mentioned kernel development, so it would be better to stick to C to reach that goal.

OP mentioned wanting to *eventually* get into kernel development.  I was addressing "monitoring programs and such".  These are two very different applications that OP **should** use different languages for (unless there's a **very** compelling reason to do otherwise).

---

### Post by 11jmb on 2011-11-02
> **trent.josephsen said:**
> OP mentioned wanting to *eventually* get into kernel development.  I was addressing "monitoring programs and such".  These are two very different applications that OP **should** use different languages for (unless there's a **very** compelling reason to do otherwise).

Of course. People would be a lot better of in general if they thought of their language choice in terms of "what problem do I want/need to solve?" 

my recommendations
kernel devel->c
monitoring programs and such->bash or python

---

### Post by 3Miro on 2011-11-02
> **11jmb said:**
> Of course. People would be a lot better of in general if they thought of their language choice in terms of "what problem do I want/need to solve?" 

my recommendations
kernel devel->c
monitoring programs and such->bash or python

I agree. There are so many languages for a reason. There are problems that are best solved by some languages and not others. 

In genera, people put too much emphasis on "what language should I learn" as opposed to "learn how to program". I think C and C++ are the best languages to learn how to program in general. Once you understand those two (and the general idea behind programming), you can switch to a new language in a week.

---

### Post by Vaphell on 2011-11-02
true but not entirely, functional languages will make your mind boggle :)

---

### Post by akvino on 2011-11-02
Why do you think C or C++ will disappear? 

Do you have a car, a cell phone, router, firewall, fridge with the temperature regulator, oven with digital display, one of those latest LCD/LED TV's, game system, computer... They all depend on C++. 

And if you manage to study, and get some experience under your belt check out job listings:

[http://www.simplyhired.com/a/jobs/list/q-c%2B%2B+linux](http://www.simplyhired.com/a/jobs/list/q-c%2B%2B+linux)

---

### Post by karlson on 2011-11-02
> **Vaphell said:**
> true but not entirely, functional languages will make your mind boggle :)

Nah... just takes a couple of days of getting used to.:)

---

### Post by cgroza on 2011-11-02
> **Vaphell said:**
> true but not entirely, functional languages will make your mind boggle :)
Only on the first days, it takes time to get used to recursive thinking :D.

---

### Post by Drenriza on 2011-11-03
It's always interesting to start a thread like this, since you get a lot of info.

So for the sake of argument. IF! i would write a console program in C# 4.0 / 4.5, what would i need to install on a debian system to make it work? Here i think in the form of libraries.

Since from what i can understand on some of the posts (maybe i am wrong) you don't need to install the entire mono package?

---

### Post by karlson on 2011-11-03
> **Drenriza said:**
> 
So for the sake of argument. IF! i would write a console program in C# 4.0 / 4.5, what would i need to install on a debian system to make it work? Here i think in the form of libraries.

Since from what i can understand on some of the posts (maybe i am wrong) you don't need to install the entire mono package?

If you don't have Mono how would you compile your C# program?

---

### Post by 11jmb on 2011-11-03
> **Drenriza said:**
> It's always interesting to start a thread like this, since you get a lot of info.

So for the sake of argument. IF! i would write a console program in C# 4.0 / 4.5, what would i need to install on a debian system to make it work? Here i think in the form of libraries.

Since from what i can understand on some of the posts (maybe i am wrong) you don't need to install the entire mono package?

You will need mono to compile.

I don't think 4.5 is supported by mono yet, though.

---

### Post by CptPicard on 2011-11-03
> **3Miro said:**
> 
In genera, people put too much emphasis on "what language should I learn" as opposed to "learn how to program". I think C and C++ are the best languages to learn how to program in general. Once you understand those two (and the general idea behind programming), you can switch to a new language in a week.

I have always been so much in agreement with the first sentiment, but very much in disagreement with the resultant suggestion. ;) We have had a lot of discussion about this "programming in general" subject, how it is important, and which languages are most beneficial for the learning curve. Search for the "high vs. low level language megathread" for a big discussion on this, for example.

IMO in particular C++ just has way too much C++-specific stuff to it for it to be a good "general" learning tool. Languages like Python that take out a lot of the boring drudgery, don't have "sharp edges" and expose you to a lot of different paradigms and programming ideas quickly, present a far nicer learning curve. Also, I still have not managed to understand how a language like C in particular helps you to learn any of the more different-paradigm languages... it might help you understand a C-derived imperative language, but that's it.

---

### Post by trent.josephsen on 2011-11-03
CptPicard has the right idea.

---

### Post by 3Miro on 2011-11-03
> **CptPicard said:**
> I have always been so much in agreement with the first sentiment, but very much in disagreement with the resultant suggestion. ;) We have had a lot of discussion about this "programming in general" subject, how it is important, and which languages are most beneficial for the learning curve. Search for the "high vs. low level language megathread" for a big discussion on this, for example.

IMO in particular C++ just has way too much C++-specific stuff to it for it to be a good "general" learning tool. Languages like Python that take out a lot of the boring drudgery, don't have "sharp edges" and expose you to a lot of different paradigms and programming ideas quickly, present a far nicer learning curve. Also, I still have not managed to understand how a language like C in particular helps you to learn any of the more different-paradigm languages... it might help you understand a C-derived imperative language, but that's it.

And I think that if a person doesn't understand how to manage dynamic memory, they don't know how computers work. Another thing that is bad for learning is how scripting languages can have a variables that switch from int to double and back.

Creating a program is about putting together a series of logical and mathematical statements that interface with the hardware and produce a desired result. Languages like Python and Java take out the whole hardware aspect and put you on rails in terms of programming with classes. You still keep the logic, but even the mathematical part is obscured by removing the distinctions between float and double and introducing higher level structures like rational numbers (floats and doubles are native to the hardware, rational numbers are not).

I learned how to program on Pascal/Delphi. No objects, no classes, just functions and data structures (the I moved to C and C++). Sure it was hard in the beginning and it took awhile to get be able to do fancy and exciting graphics, but going from that to classes (C++) took couple of weeks. Knowing good C++ programming, I managed to learn Python in 2 days, since all I had to do is learn the few new syntax quirks. Logic is the same, object oriented programming is the same and everything is the same, except you can be lazy about memory management. I wonder how many people that have first learned Java or Python can then say that going into C++ was trivial.

---

### Post by karlson on 2011-11-03
> **3Miro said:**
> And I think that if a person doesn't understand how to manage dynamic memory, they don't know how computers work. Another thing that is bad for learning is how scripting languages can have a variables that switch from int to double and back.

[snip]

I learned how to program on Pascal/Delphi. No objects, no classes, just functions and data structures (the I moved to C and C++). Sure it was hard in the beginning and it took awhile to get be able to do fancy and exciting graphics, but going from that to classes (C++) took couple of weeks. Knowing good C++ programming, I managed to learn Python in 2 days, since all I had to do is learn the few new syntax quirks. Logic is the same, object oriented programming is the same and everything is the same, except you can be lazy about memory management. I wonder how many people that have first learned Java or Python can then say that going into C++ was trivial.

I understand your point but you would have to agree that the lion's share of the software developers will not see or develop anything that will require performance requirements that will require understanding of memory management that C++ and more importantly C will require.  Most others will write software that whose performance will be solved by the rapidly commoditized fast hardware.

You're right learning Python and Java after C++ is much easier then the other way around.  But me being a selfish SOB that I am I don't want more competition in my field so if a person wants to learn Java or Python I'd say let them, those who actually do want to understand how stuff works and develop software that performs will get where they need to be even if it takes them a long time to do it.

---

### Post by 3Miro on 2011-11-03
> **karlson said:**
> I understand your point but you would have to agree that the lion's share of the software developers will not see or develop anything that will require performance requirements that will require understanding of memory management that C++ and more importantly C will require.  Most others will write software that whose performance will be solved by the rapidly commoditized fast hardware.

You're right learning Python and Java after C++ is much easier then the other way around.  But me being a selfish SOB that I am I don't want more competition in my field so if a person wants to learn Java or Python I'd say let them, those who actually do want to understand how stuff works and develop software that performs will get where they need to be even if it takes them a long time to do it.

There are the two general schools of thought: let me learn something quick so I can quickly find a job and make money vs putting years of hard work to gain more theoretical knowledge even it lacks direct application. Contrary to popular belief, the second one pays a lot more over the long run (although it is harder in the beginning).

One of the most useful classes that I ever took was in assembler, I have never written a single line of assembler ever since, but what I learned in that class, I am using every day.

I find it appalling how people can get Computer Science degrees and not understand pointers, although I also like your argument about the competition; maybe I shouldn't feel that bad about it.

---

### Post by 11jmb on 2011-11-03
> **3Miro said:**
> And I think that if a person doesn't understand how to manage dynamic memory, they don't know how computers work. Another thing that is bad for learning is how scripting languages can have a variables that switch from int to double and back.

Creating a program is about putting together a series of logical and mathematical statements that interface with the hardware and produce a desired result. Languages like Python and Java take out the whole hardware aspect and put you on rails in terms of programming with classes. You still keep the logic, but even the mathematical part is obscured by removing the distinctions between float and double and introducing higher level structures like rational numbers (floats and doubles are native to the hardware, rational numbers are not).

I learned how to program on Pascal/Delphi. No objects, no classes, just functions and data structures (the I moved to C and C++). Sure it was hard in the beginning and it took awhile to get be able to do fancy and exciting graphics, but going from that to classes (C++) took couple of weeks. Knowing good C++ programming, I managed to learn Python in 2 days, since all I had to do is learn the few new syntax quirks. Logic is the same, object oriented programming is the same and everything is the same, except you can be lazy about memory management. I wonder how many people that have first learned Java or Python can then say that going into C++ was trivial.

In my experience trying to teach people how to program, (not too much, tutor in undergrad, TA, mentoring), students can almost always be put into two general models: the theoretician and the engineer. They are just two different intrinsic mindsets. I personally fall into the engineer model.

The theoretician will see lisp or python as more simple, because they allow for high-level thinking to easily manifest itself.

The engineer will find c to be more simple because it does not hide much, and allows more freedom and does not obfuscate memory management and data typing (an engineer will not be satisfied with an explanation of dynamic typing and garbage collection until he/she has programmed in a statically typed language and handled dynamic memory)

It seems to me that these arguments are more clashes between the two mindsets and are fairly pointless.

[http://www.smbc-comics.com/index.php?db=comics&id=2192#comic](http://www.smbc-comics.com/index.php?db=comics&id=2192#comic)

It would just be better to point people towards the best tool for the job (and pick out a better job than "learn to program") rather than argue about what we are sure is the right way to learn.

</rant>

---

### Post by karlson on 2011-11-03
> **3Miro said:**
> There are the two general schools of thought: let me learn something quick so I can quickly find a job and make money vs putting years of hard work to gain more theoretical knowledge even it lacks direct application. Contrary to popular belief, the second one pays a lot more over the long run (although it is harder in the beginning).


I know but being the selfish SOB that I am ....

> 
One of the most useful classes that I ever took was in assembler, I have never written a single line of assembler ever since, but what I learned in that class, I am using every day.


No argument there.

> 
I find it appalling how people can get Computer Science degrees and not understand pointers, although I also like your argument about the competition; maybe I shouldn't feel that bad about it.

You shouldn't feel bad because most software developers today don't graduate from Computer Science departments, it's now Information Systems or Information Technologies.  The CompSci is still as it was with may be a few additions but it's damn hard just take a look at some of the better schools curriculum.

---

### Post by karlson on 2011-11-03
> **11jmb said:**
> In my experience trying to teach people how to program, (not too much, tutor in undergrad, TA, mentoring), students can almost always be put into two general models: the theoretician and the engineer. They are just two different intrinsic mindsets. I personally fall into the engineer model.

The theoretician will see lisp or python as more simple, because they allow for high-level thinking to easily manifest itself.

The engineer will find c to be more simple because it does not hide much, and allows more freedom and does not obfuscate memory management and data typing (an engineer will not be satisfied with an explanation of dynamic typing and garbage collection until he/she has programmed in a statically typed language and handled dynamic memory)

It seems to me that these arguments are more clashes between the two mindsets and are fairly pointless.


I think you're right about the pointlessness but I think you are wrong about the languages.  Theoreticians(Donald Knuth) use English, Engineers use whatever tool fits the problem best.

---

### Post by 11jmb on 2011-11-03
> **karlson said:**
> I think you're right about the pointlessness but I think you are wrong about the languages.  Theoreticians(Donald Knuth) use English, Engineers use whatever tool fits the problem best.

Agreed. I just meant to point out that simplicity is not black and white, and different learning methods are good for different people.

---

### Post by CptPicard on 2011-11-03
First of all, I really recommend reading at least the "megathread" should you find it in the search results; this has all been talked about repeatedly here, at length.

Second, it should be pointed out that this is of interest to me exactly because we're discussing the ways to get well versed in *general* programming in the sense that you're then able to fluently think in terms of various ways of expressing your problem in different languages... this has nothing to do with, say, specifically handling the particulars of a given hardware architecture.

That said...

> **3Miro said:**
> And I think that if a person doesn't understand how to manage dynamic memory, they don't know how computers work.

Manual memory management is mostly a boring bookkeeping task that produces lots of intellectually uninteresting bugs. If one wants to learn to solve similar problems, it's doable in higher-level languages.

> Another thing that is bad for learning is how scripting languages can have a variables that switch from int to double and back.

Loose typing is bad, agreed, as the actual type changes. Most decent dynamically typed languages also are typed strongly though, so this is a non-issue there. The implicit type conversions, where they are specifically implemented, just generally make sense.

> 
Creating a program is about putting together a series of logical and mathematical statements that interface with the hardware and produce a desired result.

Here's a somewhat different take -- I'd say programming is about using a formal language in a certain class of languages in order to express some solution to a problem. All of those languages are guaranteed to be mechanistically computable, regardless of the actual physical device doing the computation. 

Therefore, the actual architecture is irrelevant, as the translation from the language to the architecture is something that is doable by machine and can be solved once *for all problems* for a language-machine pair. It is important to notice that the compiler/interpreter itself does not really contain anything problem-specific in its construction; it just maps from one equivalent representation to another.

It follows that we're free to choose a representation that best suits the purpose by fitting our mental model of the situation. At this point it's pretty easy to see that the choice between a string of ones and zeroes is a lesser choice than a language that actually contains abstract building blocks you can use to express yourself...

And because we're talking about developing mental models about programming in a most efficient manner, I'd offer that making use of higher-level languages builds this kind of a toolkit faster. Anything else is in the domain that is specific to the hardware part of the general translation problem, not in the domain of general programming.

>  Languages like Python and Java take out the whole hardware aspect and put you on rails in terms of programming with classes.

The hardware aspect is completely overrated, unless you're specifically programming with hardware. All the issues you have to deal with in hardware are analogues to abstract problems that you'll meet anyway programming in higher-level languages, and they are not in any sense more fundamental than others; it's just that they specifically get in the way more programming on the lower level.

I find it a bit odd that you'd specifically mention classes as the culprit... there is so much other stuff in other programming languages; yet I guess classes are the first thing that a programmer meets after coming from something like C.

But in defense of classes; it's good to have an extensible type system. It is the single-dispatch model of Simula-style programming languages (Java and C++) that is the original sin. Try Common Lisp's multiple dispatch for matching your datatypes to operator functions instead. ;)

> You still keep the logic, but even the mathematical part is obscured by removing the distinctions between float and double and introducing higher level structures like rational numbers (floats and doubles are native to the hardware, rational numbers are not).

It's the logic that is all important in programming, not some hardware-level detail. IMO that sounds like such a remarkably minor complaint in comparison to what I'd want to see a programming learner to actually be learning... kind of a case of "can't see forest for the trees".

If you want to implement your own rational number class as some kind of a homework exercise, nothing stops you, though. It's the rational math that is interesting anyway. But here we're talking implemented libraries already, it's not really in the domain of the fundamental core language design.

> 
I learned how to program on Pascal/Delphi. No objects, no classes, just functions and data structures (the I moved to C and C++).

BASIC, Pascal, C to begin with here, from the mid-80s... but have got to say the higher-order language-independent thinking about programming that I value in myself these days didn't really develop until having messed with dozens of languages and starting to see the big picture after being exposed to things like Scheme and having written some interpreters in it (it's a remarkably useful exercise, highly recommended)... that's when all the cruft just disappears and you can see the really important ideas that are left. 

Most languages just tend to occupy some kind of a niche where they've made some kinds of decisions and left others out; then you'll just have to map your mental idea of what you're doing to that language and emulate the rest.

"Just functions and data structures" is a nice description of functional programming, btw. I'm glad it's making a comeback. Thinking about stuff in terms of just transforming data using functions is a useful model, in particular in our modern parallel, distributed world...

> Sure it was hard in the beginning and it took awhile to get be able to do fancy and exciting graphics, but going from that to classes (C++) took couple of weeks.

C++ is not just classes. It's a rather big language with lots of "incidental complexity" when you put stuff together that trips up in particular a beginner for no good reason IMO... I consider myself fairly fluent in C++, but frankly I just can't be bothered with it if I mustn't :p

> 
Knowing good C++ programming, I managed to learn Python in 2 days, since all I had to do is learn the few new syntax quirks. Logic is the same, object oriented programming is the same and everything is the same, 

It's easy to take a superficial look at Python and not to really appreciate everything it's got -- IMO 2 days is not enough. The dynamically-typed OOP, higher-order functions, generators...

But, of course the entire point of my argument is that Python is easy to get started with (and to continue with); regardless of whether you're coming from C++ or not. And by the way, the "logic is the same" kind of arguments work the other way as well. This is better seen when comparing Python and C -- C is mostly basic logic building blocks; Python gives you those just as well, and then some.

> except you can be lazy about memory management.

Which is a very good thing, as memory management is conceptually such a stupid, boring problem :p

> I wonder how many people that have first learned Java or Python can then say that going into C++ was trivial.

If someone has already learned Python or Java, they already have a really good start to their programming mindset. The issues with C++ that make it "harder" are mostly about C++ itself really, not because C++ somehow would represent some kind of superior, naturally harder representation of programming.

In the end, when looking for the most efficient learning curve, finding the "hardest" (maybe even in the "hard in a stupid sense as in it makes you do a lot of stupid work" way) language doesn't really sound sensible, even though it may give a person some bragging rights.

> **karlson said:**
>  Most others will write software that whose performance will be solved by the rapidly commoditized fast hardware.

Or, the choice of appropriate algorithm... it's just simply a specific requirement to operate closer to the hardware sometimes, and then you're making use of similar programming skills you would have learned from elsewhere; and it's not as if memory management is any kind of magic a person who learned to program already *couldn't* do. The converse is not true; managing memory does not magically confer superior programming ability in other scenarios.

> **3Miro said:**
> There are the two general schools of thought: let me learn something quick so I can quickly find a job and make money vs putting years of hard work to gain more theoretical knowledge even it lacks direct application. Contrary to popular belief, the second one pays a lot more over the long run (although it is harder in the beginning).

I could easily say exactly the same things, but from my perspective. I honestly do not consider lower-level languages to be particularly "theoretical" or to yield theoretical insight particularly well... they are too stuck to the imperative-programming mindset. Lisp may lack immediate practical application and it does not pay too well, but boy, does it open you up to looking at things differently.

If you want theory, I'd suggest you start working on your Haskell skills. ;)

> 
One of the most useful classes that I ever took was in assembler, I have never written a single line of assembler ever since, but what I learned in that class, I am using every day.

Well, same... but IMO imperative state changes by small operations is just one way of looking at it. There's nothing "special" to it.

> I find it appalling how people can get Computer Science degrees and not understand pointers.

Hmm, I guess I could almost have got my CS MSc without touching pointers (it was mostly theoretical CS, algorithmics etc). Of course, conceptually we're talking of a kind of "indirection variable" -- you have one value that you use to get some other value from some abstract map. It's not some magic ingredient that makes everything else somehow tick.

> **11jmb said:**
> In my experience trying to teach people how to program, (not too much, tutor in undergrad, TA, mentoring), students can almost always be put into two general models: the theoretician and the engineer. They are just two different intrinsic mindsets. I personally fall into the engineer model.

Well, this much is probably true, I have noticed it myself as well. I guess I'm the theorist here ;)

---

### Post by CptPicard on 2011-11-03
> **11jmb said:**
> Agreed. I just meant to point out that simplicity is not black and white, and different learning methods are good for different people.

There's simplicity and then there's simplicity. Both Scheme and assembler are simple in the way that the languages' definitions are very small. The former is built of generic theoretically-minded abstractions, the other represents the hardware more directly (and this is not even quite true these days anymore). 

Of course, both really are equivalent, so the philosophical question is... does assembler somehow tell you something that Scheme does not, and does Scheme "hide" something, dumbing things down? Does Scheme's model contribute to your understanding of programmatic constructs in general better and faster than having to somehow figure out how to hack up an entire interpreter in assembler before you can be exposed to them (something I'd bet you wouldn't be doing especially when you're learning about things)...

In particular the "high-level languages hide things one needs to know" is IMO a flawed argument. The underlying machine really could be anything and we could never even tell, so really, you do not need to know as far as the big picture of programming is concerned.

---

### Post by 11jmb on 2011-11-03
> **CptPicard said:**
> Which is a very good thing, as memory management is conceptually such a stupid, boring problem :p
Says you :p. Doing ES development makes it a fun and interesting problem. But again, the theoretician will get nothing out of learning memory management.



> **CptPicard said:**
> 
Well, this much is probably true, I have noticed it myself as well. I guess I'm the theorist here ;)
We need one of those "celebrate diversity" posters that are in every office building in the world :)

---

### Post by CptPicard on 2011-11-03
> But again, the theoretician will get nothing out of learning memory management.

IMO what everyone would get out of learning memory management is learning how to work with one incarnation of a "reserve resources and remember to release them" kind of problem. My argument is not that one shouldn't learn memory management, it's just that it's not as special or "generally educational" as people make it seem like...

---

### Post by 11jmb on 2011-11-03
> **CptPicard said:**
> 
In particular the "high-level languages hide things one needs to know" is IMO a flawed argument. The underlying machine really could be anything and we could never even tell, so really, you do not need to know as far as the big picture of programming is concerned.

That depends on what you need to know.

From what I can infer from your posts, assembly is much less interesting to your work, where it is very important for my work (not programming in it directly, but an awareness). 

That is why i think "what language should I learn to program in" is a flawed question. It should be narrowed down to what the beginner wants to get out of programming, because there is plenty of choice there,.

---

### Post by 3Miro on 2011-11-03
@CptPicard: You would excuse me if I don't take the time to read a megathread and I would totally understand if you don't want to repeat arguments that you have already made. What I am saying is you don't have to respond or engage in a long argument if you don't want to.

I guess we have a rather different approach to the whole problem. I only got BS in CS before I went into Math. In my mind, algorithms are Mathematics and completely independent from Computer Language or Hardware. When I talk about CS I talk about the actual implementation of the algorithm in specific language AND hardware. I admit that I draw the line somewhat arbitrarily and if I try to think objectively, there is quite a bit of gray-area overlap between the CS and Math.

The types of problems that I am doing are incredibly demanding (think of Supercomputers). If I am not efficient in memory management then the program will simply fail. If I don't use native data types like double, then the program will fail. A custom (or from library) rational number class would theoretically produce the same result, but it will take too long to execute.

If you detach programming form the hardware, then in my view you are just doing Math. Not that there is anything wrong with that, I am a Mathematician, it is just that I think that a programmer should not only be able to code an algorithm, but also code it in a way that squeezes every once of power from the hardware. Java and Python don't let you do that. Only low level languages like C and assembler allow for this (I am not writing assembler, but I am linking to assembler optimized libraries form within C code i.e. BLAS).

I am not trying to dismiss high level languages either. They definitely have their use, for example I don't transform large text files with C I always go to Python for that. There are algorithms and Math problems that just cry for Lisp (luckily not in my field :) ). It is just that I think a good programmer should be able to do both high and low level programming.

---

### Post by CptPicard on 2011-11-03
> **11jmb said:**
> 
From what I can infer from your posts, assembly is much less interesting to your work, where it is very important for my work (not programming in it directly, but an awareness). 

Special domains are special domains, and there this argumentation is uninteresting. My actual work at the moment is about your typical (admittedly large-scale) enterprise application back-ends, and I wouldn't necessarily say that my ideas here have some particularly deep application in my current actual work. But it's all about how I "experience" the whole of programming, and how I come to view it over the years :)

> 
That is why i think "what language should I learn to program in" is a flawed question. It should be narrowed down to what the beginner wants to get out of programming, because there is plenty of choice there,.

Well, a n00b will not know, and he's just getting started... and in the end, if he's going to be good, he should probably be capable of grabbing most programming languages and to use them. So we'll want to educate into him some kind of general understanding of how programming works, how to "think" about programmatic problems... first he will of course think "in terms of" his first language. Then over time he'll be exposed to more paradigms and so on, perhaps broadening his horizons as to how one might model the problems at hand. I'm just interested in figuring out what the most beneficial route to take is in this regard.

---

### Post by karlson on 2011-11-03
> **CptPicard said:**
> 
Or, the choice of appropriate algorithm...


In some cases it won't help you...  You can select the most appropriate algorithm out there but if you are processing real-time large stream of data you need to do this at near hardware speed.  Python and Java won't let you do it cause they are just not designed for it.

> it's just simply a specific requirement to operate closer to the hardware sometimes, and then you're making use of similar programming skills you would have learned from elsewhere; and it's not as if memory management is any kind of magic a person who learned to program already *couldn't* do.


Nothing in Computers is magic.  It's all deterministic, but the point was that most people stop when they have to try and understand pointers, pointer arithmetic, memory allocation and deletion, free lists and even such a concept as "placement new" in C++.

> 
The converse is not true; managing memory does not magically confer superior programming ability in other scenarios.


No single skill no matter how expert you are in it makes you a good or even decent developer.  But having it under your belt along with other things allows you to make software perform much better then the alternative.

> 
If you want theory, I'd suggest you start working on your Haskell skills. ;)


That still has practical applications :P

---

### Post by CptPicard on 2011-11-03
> **3Miro said:**
> @CptPicard: You would excuse me if I don't take the time to read a megathread and I would totally understand if you don't want to repeat arguments that you have already made. What I am saying is you don't have to respond or engage in a long argument if you don't want to.

I can't help it, it's such an interesting subject ;) But I do understand; it was just a hint that there's quite a lot of opinion on this already there. It is, after all, perhaps the most discussed topic in the history of the Programming Talk forum. It tends to divide people into the two camps we're seeing here...

Yes, you're correct we take somewhat different approaches to this.

> 
In my mind, algorithms are Mathematics and completely independent from Computer Language or Hardware.

They can be just pure math, but considering that we then want to give an expression to them that we know is computable, then we need some kind of a programming language. After all, Lisp was initially conceived for expressing computable functions in mathematics journals...

There is this area between algorithmics, math and language where my mind tends to like to play with programming languages and the kind of expression you can formulate with them. Therefore, for me, HLLs really are not just things that "hide the machine". They're not just a tool, they're a medium that actually shapes what you're working with, so therefore, it counts what gets taught first :)

> When I talk about CS I talk about the actual implementation of the algorithm in specific language AND hardware.

This is the classic question of how much engineering there is in CS...

> 
The types of problems that I am doing are incredibly demanding (think of Supercomputers). If I am not efficient in memory management then the program will simply fail. If I don't use native data types like double, then the program will fail. A custom (or from library) rational number class would theoretically produce the same result, but it will take too long to execute.

Yeah, and this really is a special domain... very much like embedded systems in nature, just on a bigger scale.

> If you detach programming form the hardware, then in my view you are just doing Math.

Well, yes. You're essentially defining functions in a certain class using a certain kind of formalism.

> There are algorithms and Math problems that just cry for Lisp (luckily not in my field :) ).

A fascinating aspect of Lisp that is often overlooked is its ability to be, in some sense, "closest" to all other programming languages -- it can be argued that if you've got a Lisp, you're the shortest possible implementation distance from all other programming languages -- the AST-like syntax, core language primitives and the macro compiler put together are like an interpreter/compiler toolkit at your disposal. This is one reason why I tend to recommend that new programmers do look at and try to understand the reasoning behind Lisp...

> It is just that I think a good programmer should be able to do both high and low level programming.

That much I can agree with, although the initial discussion was about suitable learning curve. The end result should be a well-rounded programmer.

---

### Post by WasMeHere on 2011-11-03
In this discussion you should probably classify me as an engineer or perhaps a teacher.

I think you should know enough about your field of work to select an appropriate tool for each task. Or to ask someone else to do it, if you think you can't do an efficient job. Obviously some people have to invent tools, but don't reinvent them!

Having fun finding out :-)
Olle

---

### Post by 11jmb on 2011-11-03
> **CptPicard said:**
> 
Well, a n00b will not know, and he's just getting started... and in the end, if he's going to be good, he should probably be capable of grabbing most programming languages and to use them. So we'll want to educate into him some kind of general understanding of how programming works, how to "think" about programmatic problems... first he will of course think "in terms of" his first language

I think that all of us have been guilty of the "golden hammer" fallacy at some point in our careers.

You aren't giving the n00bs enough credit here. While we may have to guide them towards verbalizing what they want, everybody has been led to programming through some other interest. We can use that interest to help point them towards good problems, and only then should we start suggesting languages.

---

### Post by karlson on 2011-11-03
> **CptPicard said:**
> 
Well, a n00b will not know, and he's just getting started... and in the end, if he's going to be good, he should probably be capable of grabbing most programming languages and to use them. So we'll want to educate into him some kind of general understanding of how programming works, how to "think" about programmatic problems... first he will of course think "in terms of" his first language.


Amen to that except the first language would be one of:
English, Russian, Swedish, Dutch, Danish, French, German, Spanish, Portuguese, Italian, ...... (sorry all there are too many), in which a n00b can describe a solution to the problem (s)he's trying to program and then it will get translated into a programming language for computers.  If he can't solve the problem in words it doesn't matter that (s)he knows syntax of Python or Perl or Java or C++....

---

