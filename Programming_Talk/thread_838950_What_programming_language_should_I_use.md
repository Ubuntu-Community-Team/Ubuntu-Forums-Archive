---
title: "What programming language should I use?"
date: 2008-06-24
forum: Programming Talk
---

### Post by IQAndreas on 2008-06-24
I have been programming for a few years with VB.net, and for my next large project I would like to move on to something that does not require Windows. I have also messed around with perl, a little java, java script, and HTML (which isn't really programming IMO).

I am converting the board game Twilight Imperium to a computer game, but I am not sure what programming language to use for this and future projects. There are so many out there that I don't know where to start, but I am quick to learn whichever one is best for my needs.

Primarily, I would like the language to be able to run on any platform, and even better would be to allow the programs to run without a platform, using a live CD to run the program. Best would be both options.

Second, I want it to be able to run without being dependent on runtime compilers. For example, perl (I believe) requires the user to have perl, and run it through that program every time they want to run it.
I want to be able to compile it once and then allow it to be used anywhere.

Third, I would like there to be a lot of people already using the software so I can get a lot of help and samples instead of writing pretty much everything from scratch.


What is Linux usually written in? Would that work for software as well?

I don't mind learning machine code if that is the best route and someone can point me in the right way. :)

---

### Post by Phenax on 2008-06-24
> **IqAndreas said:**
> 
Second, I want it to be able to run without being dependent on runtime compilers. For example, perl (I believe) requires the user to have perl, and run it through that program every time they want to run it.
I want to be able to compile it once and then allow it to be used anywhere.


That statement is (close to) contradictory. 

Interpreted (or byte-code compiled) languages depend on an interpreter to read the code and translate it into machine-readable code, and therefor you do not need multiple binaries for different platforms. Examples of these languages are Perl, Python, Ruby, Java, etc.

Compiled languages are turned into a native executable for the target system you are compiling for. Windows uses a different executable format than Linux therefor you must compile one copy for Windows and one for Linux and one for any other systems with different executable formats.


Although it's not exactly black-and-white. With most interpreted languages you can bundle the interpreter as well as your code into one executable package leaving no dependency and the user should not even know it's not a native binary.

You can use a cross-compiler for a compiled language to easily produce binaries for other platforms.


Most people tend to think that interpreted languages are easier to work with. I would suggest checking out Python or Ruby if you're looking for powerful but easily grasped languages. You can use programs to convert them to a bundled interpreter and your code for ease of distribution if needed. Java is also a good choice, as most people have it, and the intermediate byte-code format allows the .class/.jar files to be used with any compliant Java Virtual Machine. With C or other compiled languages, I'd make sure I have access to all of the platforms I'd be compiling my code on.


And of course, while most languages are cross-platform, your programs won't be cross-platform unless you do not use platform-specific libraries (like DirectSound on Win32 - use SDL or OpenAL instead!)

---

### Post by Can+~ on 2008-06-24
A+ to Phenax (whoops, wrong nick).

You may also want to check a list of [available game engines](http://en.wikipedia.org/wiki/List_of_game_engines) ([Also, "notable" game engines]("http://en.wikipedia.org/wiki/Game_engine#Notable_engines"), since the list is huge), so you don't have to start from scratch. Of course, keep with OpenGL, as directx is Microsoft only. Check also

---

### Post by ankursethi on 2008-06-24
I suppose OP means to say he doesn't want an interpreted language, but a compiled one.

It's true that you will have to compile a separate binary for every platform your application runs on, but usually you can have one for Linux, one for Windows and an archive containing the source code so people can compile the app for their own platforms.

You might want to consider C++ for writing your game. You will find ample documentation and sample code, since C++ seems to be the de facto language for writing games these days. If you detest C++, then D is an option. It's an emerging language that has all the features of C++ and more.

That said, it will be more productive to use an interpreted language. I personally like Python. It has a set of binding to SDL called PyGame which is insanely popular among hobbyists.

---

### Post by TenPlus1 on 2008-06-24
SDL Basic is a very simple programming language will a full online manual with examples...  You can also compile your programs with the interface provided to make a completely standalone program file...

Get here : [http://www.sdlbasic.altervista.org/main/](http://www.sdlbasic.altervista.org/main/)

---

### Post by pmasiar on 2008-06-24
Every language requires installing support libraries - including C#.NET and Java, you just don't see it if it is preinstalled on Windows. Python is installed in most Linux distros, and for Windows, it is single windows installer to run. 

You should be more concerned about your own developer's productivity: any game fun to play is huge - and you do not have team of couple of dozens full-time developers like professional games. Going with anything low-level like C, C++, or even mid-level like C# and Java, will substantially decrease your chance of ever finishing the project. And if you did not finished it, there is nothing for users to worry installing. :-)

---

### Post by Frak on 2008-06-24
Compile once and use everywhere, you have just told yourself to use Java (as it is their motto).

EDIT

I actually took the time to read it, and I would recommend writing it in C. Since the mass majority of gaming engines and peripheral code that helps to make a game is written in C more than any other language. (Quake I, II, and III are written in C, as is other engines such as the Savage engine.)

---

### Post by LaRoza on 2008-06-24
> **pmasiar said:**
> Every language requires installing support libraries - including C#.NET and Java, you just don't see it if it is preinstalled on Windows. Python is installed in most Linux distros, and for Windows, it is single windows installer to run. 


Java isn't preinstalled on Windows (neither is Flash), so that doesn't matter. HP and Compaq computers come with Python (and other OEM's put various things on)

> **Frak said:**
> Compile once and use everywhere, you have just told yourself to use Java (as it is their motto).

Java isn't the answer. It isn't on most live cd's and requires a JRE.

> 
Primarily, I would like the language to be able to run on any platform, and even better would be to allow the programs to run without a platform, using a live CD to run the program. Best would be both options.

Python and Perl are good things for this requirement.

> 
Second, I want it to be able to run without being dependent on runtime compilers. For example, perl (I believe) requires the user to have perl, and run it through that program every time they want to run it.
I want to be able to compile it once and then allow it to be used anywhere.

You can't compile something once and have it run everywhere without some sort of interpreter. 

For no preinstalled software, I would recommend C and a makefile. For run anywhere, Perl, Python and Java are good.

> 
Third, I would like there to be a lot of people already using the software so I can get a lot of help and samples instead of writing pretty much everything from scratch.

See above.

---

### Post by Frak on 2008-06-24
> **LaRoza said:**
> Java isn't the answer. It isn't on most live cd's and requires a JRE.

He did say compile once run anywhere...

---

### Post by IQAndreas on 2008-06-24
> **Phenax said:**
> Compiled languages are turned into a native executable for the target system you are compiling for. Windows uses a different executable format than Linux therefor you must compile one copy for Windows and one for Linux and one for any other systems with different executable formats.
Ah. I do not mind doing so as long as I am able to compile it into each of the different platforms and don't have to re-write everything in a different language to make it useable for a different platform.

> **Phenax said:**
> Most people tend to think that interpreted languages are easier to work with. I would suggest checking out Python or Ruby if you're looking for powerful but easily grasped languages.
I do not mind hard to grasp languages, as long as they are powerful enough. I have been programming for quite a while, so I know most basic concepts.

> **Phenax said:**
> Java is also a good choice, as most people have it, and the intermediate byte-code format allows the .class/.jar files to be used with any compliant Java Virtual Machine.
If I end up using Java, does each host computer have to have java installed on them for it to be able to run? What if that version of java has an error in it or is outdated?

Is there any site or anything that compares different major programming languages and gives detailed lists of the pros and cons? I have found sites that list a lot of programming languages, but don't really get into details about each one. I would like a smaller yet detailed list.

---

### Post by LaRoza on 2008-06-24
> **Frak said:**
> He did say compile once run anywhere...

AND no runtime required. There is nothing like that. They were together.

---

### Post by Greyed on 2008-06-24
Just as an aside I am curious why there is such a negative view on interpreted languages for this?

EvE-Online is written in (Stackless) Python.
Dungeons and Dragons Online and I believe Lord of the Rings Online use Python for portions of their client.
Vampire: Masquerade has portions of its logic written in Python
World of Warcraft implements its UI (and who knows what else?) in Lua.

All but one of those is an MMO and MMOs are one of the more complex class of games one can design and implement.  Interpreted languages are up to the task of handling that complexity *and* are available on many different platforms.  They have a proven track record both in portability and gaming.

---

### Post by IQAndreas on 2008-06-24
Just to clarify, this isn't your average game. It is only a board game, and I'm mainly looking for a programming language that I will use for all my future projects that can either be an OS or a program running inside another OS. Is this possible?

And, I do not mind compiling the same program into different types of executables for each OS, as long as I don't need to use different code and different compilers each time I update it.

Also, when I say I want it to run by live CD, I mean I want it to BE the live CD. I don't want it to be playable by LiveCD linux users, I want it to be able to run without being dependent on anything or at least able to run on a very light installation of Linux that users do not even know is running.

---

### Post by LaRoza on 2008-06-24
> **IqAndreas said:**
> Just to clarify, this isn't your average game. It is only a board game, and I'm mainly looking for a programming language that I will use for all my future projects that can either be an OS or a program running inside another OS. Is this possible?

And, I do not mind compiling the same program into different types of executables for each OS, as long as I don't need to use different code and different compilers each time I update it.

Also, when I say I want it to run by live CD, I mean I want it to BE the live CD. I don't want it to be playable by LiveCD linux users, I want it to be able to run without being dependent on anything or at least able to run on a very light installation of Linux that users do not even know is running.

You have to write an entire OS and all its drivers for this project then. It will take a highly skilled computer science major 6 months to get something (a minimal OS) almost working on one processor architecture. Good luck...

To make things easier...

You can make a custom Live disk and include the game. And assuming it is GPL'd, you could write the game in Python or Perl and have the Python/Perl installer for the various platforms.

---

### Post by CptPicard on 2008-06-24
> **IqAndreas said:**
> Ah. I do not mind doing so as long as I am able to compile it into each of the different platforms and don't have to re-write everything in a different language to make it useable for a different platform.

You're looking for a huge project then... maintaining a multiplatform cross-compiling environment for a single project is not something to be taken lightly :) I am not sure if I would even bother considering if it was just a hobby project.

> 
I do not mind hard to grasp languages, as long as they are powerful enough.

Here we come back to the interesting issue of hardness vs. power of language. We have been having these discussions over and over again. :)

What sort of things do you feel are included in the "powerfulness" of the language? There is this interesting concept floating around (mostly in the heads of more inexperienced programmers who like to think if they do more work, they're more leet) that says that a "hard" -- in the work and obtuseness sense -- language is more powerful.

Then there are those people -- in my opinion, the more experienced programmers -- who take the view that a language is powerful when 1) it gets out of the way and gets work done and 2) when it contains high-level features that are missing in lower-level languages, thus upping the expressive power of the language.

I tend to be in the latter camp, case 2 to be exact. An interesting point IMO is that case 2 in particular doesn't necessarily make a language "easier" at the outset -- Haskell for example can be hard for the uninitiated -- but it does make it much more powerful for the programmer once you really get it, and those higher-level features become such a natural part of your problem-solving arsenal that you start hating languages that don't have them.

An interesting point about languages like C++ is that while they can be somewhat more runtime-efficient in the constant factors sense, they can never transcend the fact that they are lower-level and require lots of programmer's (dumb, non-thinking) work to get things up and running. So, efficiency/hardness is not a trivial consideration :)


> 
If I end up using Java, does each host computer have to have java installed on them for it to be able to run? What if that version of java has an error in it or is outdated?

Yes. Latter is not much of a problem, most people have Java 1.5+ these days anyway. I can't remember the last time Java or its libs actually had a noteworthy bug the programmer had to be aware of.


EDIT: Oh, there was more stuff I wanted to respond to...

> **Greyed said:**
> Just as an aside I am curious why there is such a negative view on interpreted languages for this?

It's because a lot of beginners learn C and then when they grasp the concept of pointers and how it all translates to ASM, imagine that's all there is and that they are now leet. Add to this that yes, their factorial program runs faster in C than in Python, they take it as proof positive that C beats the pants off everything else in everything.

Also they like to think that doing a lot of low-level work translates to being a cool programmer. Then when they are faced with the prospect that perhaps it's actually useless and that they can do mind-blowing things (that they can't comprehend) in higher-level languages, their defense mechanisms kick in and they launch into pointless rants about how there is still a virtual machine underlying it all so you're not really coding for the computer etc etc...

> Interpreted languages are up to the task of handling that complexity *and* are available on many different platforms.  They have a proven track record both in portability and gaming.

+1 for noticing this. That, and they actually let you do more complex stuff more easily, which is great for scalability etc.

> **IqAndreas said:**
> Just to clarify, this isn't your average game. It is only a board game, and I'm mainly looking for a programming language that I will use for all my future projects that can either be an OS or a program running inside another OS. Is this possible?

Sounds like Lisp... I love the ability to code the live environment, which actually *was* an OS on Lisp machines.

---

### Post by Alasdair on 2008-06-24
I looked at the website for the boardgame you wanted to make, and I think Python + Pygame would be a good language/library choice. You can make your own liveCD distro specifically for the game, but since every user will have an OS already, it seems kinda pointless (although it would be cool).

---

### Post by pmasiar on 2008-06-24
> **IqAndreas said:**
> I do not mind hard to grasp languages, as long as they are powerful enough. I have been programming for quite a while, so I know most basic concepts.

Quite obviously you do not know most basic of all basic concepts: software development is engineering (so it means balancing of contradictory requirements) and CPU's time is cheap: it's developer's time what is expensive. 

You are not concerned about development time at all, it suggests to me that you are just a student/hobby hacker who did not developed and maintained any program larger than couple hundred lines - so your chance in succeeding in this project is small.

Powerful language is not the one creating most effective code for number-crunching, but allowing to create whole application in least amount of code and least amount of time. 

> Is there any site or anything that compares different major programming languages and gives detailed lists of the pros and cons?

wikipedia

---

### Post by Frak on 2008-06-24
> **IqAndreas said:**
> Just to clarify, this isn't your average game. It is only a board game, and I'm mainly looking for a programming language that I will use for all my future projects that can either be an OS or a program running inside another OS. Is this possible?

And, I do not mind compiling the same program into different types of executables for each OS, as long as I don't need to use different code and different compilers each time I update it.

Also, when I say I want it to run by live CD, I mean I want it to BE the live CD. I don't want it to be playable by LiveCD linux users, I want it to be able to run without being dependent on anything or at least able to run on a very light installation of Linux that users do not even know is running.
More power usually means less portability...

Whatever language you use, try as hard as you can to stick to the STANDARD HEADERS/LIBRARIES/ETC. This will make the program ultra portable, though, programming might be more difficult.

---

### Post by CptPicard on 2008-06-24
> **Frak said:**
> More power usually means less portability...

I suppose you mean "smaller runtime constants" means less portability.. ;)

Lisp is extremely powerful, it's also very portable...

---

### Post by Frak on 2008-06-24
> **CptPicard said:**
> I suppose you mean "smaller runtime constants" means less portability.. ;)

Lisp is extremely powerful, it's also very portable...
What I meant was, portability without modification.

---

### Post by IQAndreas on 2008-06-24
> **LaRoza said:**
> You have to write an entire OS and all its drivers for this project then. It will take a highly skilled computer science major 6 months to get something (a minimal OS) almost working on one processor architecture. Good luck...
Is there any way to have an operating system "shell" which loads all the drivers and everything, and then continue from there custom making the desktop environment and such?


And no, this is no small time project. I plan on working full time developing this over a course of maybe two years and keep expanding on it for years to come.

Even though it would be relatively simple to just make the board game, I am going ions further with this, so this will be no ordinary game, adding features not possible on a table or even in most games seen already. The biggest feature I will be implementing is creating my own relatively simple "programming language" to allow users to create their own action cards, strategy cards, etc.

This is not my first time programming. I have been creating medium sized applications for use in office environments (as well as entertainment) for several years, but I wanted to get out of VB.Net and the Microsoft stranglehold.


What I mean by difficult languages, is I don't mind learning entirely new code such as (just a sample that probably doesn't even exist, but as you can see it is influenced a tad by java):
sys.outln.print(config.usrfont,prompt.release{'/"Hello#CHR{23}World/"},debug={'no'});
I don't mind complicated coding or language. I am not limited to only learning BASIC commands.

What I mean by powerful languages is, I once used TrueBASIC in my early years, and although the language was very simple and easy to learn you were greatly limited to what you could do. Probably the most powerful feature was using a library to make your sound card play MIDI music. Or some languages might be limited to only allowing you display things on the screen and will not allow you to actually do anything to the actual computer. I want something than is more powerful than these two examples. Near full control would be the best.

I would just like some programming language where I have FULL control and am not limited by interpreters, other software, required libraries, or even limited by the operating system.

---

### Post by LaRoza on 2008-06-24
> **IqAndreas said:**
> Is there any way to have an operating system "shell" which loads all the drivers and everything, and then continue from there custom making the desktop environment and such?

I would just like some programming language where I have FULL control and am not limited by interpreters, other software, required libraries, or even limited by the operating system.

Yes, you can use Linux as the base (think: GParted Live CD) and only have the apps you want loaded. It would be light, portable, and rather easy (not much harder than just writing the program in any language, Python + PyGame might be worth checking)

For the programming language, you will be limited by hardware, and those limitations will be more shocking. The reason compilers and interpreters exist is to abstract the hardware away. So, for writing a program in Java or Python, it will run anywhere the runtime is found. For C, it will be able to be compiled anywhere there is a compiler available. For assembly, it will only work on the architecture it was written for. If you go lower, you are even more restrained by the hardware. That is what the kernel does for you, it handles all that (as opposed to an embedded program in a device, which only has to deal with one set of hardware)

---

### Post by CptPicard on 2008-06-24
IMO you are just jumping in at the deep end before *really* knowing how to swim. That you are concerned of vague hypothetical limitations which you can't probably even properly pin down before you actually meet them in your real project (if you ever do), is a big flashing warning sign.


> **IqAndreas said:**
> Is there any way to have an operating system "shell" which loads all the drivers and everything, and then continue from there custom making the desktop environment and such?

Probably this would mean writing a Linux LiveCD that fires up your app after boot. But this is a very very specific need, and there is a reason why most apps do not work this way.

> And no, this is no small time project. I plan on working full time developing this over a course of maybe two years and keep expanding on it for years to come.

Full time for two years? Did you win the lottery or something or are you already retired, because this does not really sound like a financially profitable project, looking at the way you plan on going about it? :)

> 
Even though it would be relatively simple to just make the board game, I am going ions further with this, so this will be no ordinary game, adding features not possible on a table or even in most games seen already.

I do not really understand how doing away with libraries, dependencies, interpreters, even the operating system is going to help you create some vague vaporware unforeseen features that haven't been possible before. You're far better off writing on top of existing stuff, or you really are some super-genius... or alternatively you're just full of it ;)

> The biggest feature I will be implementing is creating my own relatively simple "programming language" to allow users to create their own action cards, strategy cards, etc.

Why not write this in something like Python then, which would be readily extensible by your users... in Python?

> 
What I mean by difficult languages, is I don't mind learning entirely new code such as (just a sample that probably doesn't even exist, but as you can see it is influenced a tad by java):
sys.outln.print(config.usrfont,prompt.release{'/"Hello#CHR{23}World/"},debug={'no'});

You do realize that this is a complete triviality? No coder worth his salt is going to be without the ability to absorb new syntax.

> 
I don't mind complicated coding or language. I am not limited to only learning BASIC commands.

You should. Useless complexity is bad. Expressiveness is good. "Not being limited to BASIC" is... not much.



> What I mean by powerful languages is, I once used TrueBASIC ...  I want something than is more powerful than these two examples. Near full control would be the best.

Sorry, but this is what shows you're clueless. :) You just need a proper general-purpose programming language and to really properly code in it to be able to answer your own questions. Until you can do that, there is no way we can convince you that you don't need to learn assembler to code the whole full stack straight on top of the CPU.

> I would just like some programming language where I have FULL control and am not limited by interpreters, other software, required libraries, or even limited by the operating system.

This is the typical speed-kiddy "full control" myth. Could you give me a proper example of what you are worried about with these supposedly limiting OSes and libs and intepreters? (In particular when it comes to the OS, please consider that *all* apps you are using in Linux for example seem to work just great despite being crippled by the operating system...)

---

### Post by Frak on 2008-06-24
What it sounds like is a program that needs no external info files, nor libraries or kernel. As if the Kernel is the program you want to run.

---

### Post by pmasiar on 2008-06-24
> **IqAndreas said:**
> I have been creating medium sized applications for use in office environments (as well as entertainment) for several years,...
I once used TrueBASIC in my early years, ...programming language where I have FULL control and am not limited by interpreters, other software, required libraries, or even limited by the operating system.

You are limited by your experience, which is clearly limited to couple dozens/hundreds lines of VB/VBA.

The more control you have, the more responsibility, more hard work, and more chances to make really big mistakes. What you want (to be productive) is a language what makes lots of decisions for you, and tracks lots of details, without limiting your creativity - like Python. You quite obviously are not familiar with any of RAD languages.

You should also read Brooks "Mythical man-month" (which you obviously did not yet), to recognize what you want is syndrome of the [http://en.wikipedia.org/wiki/Second-system_effect](http://en.wikipedia.org/wiki/Second-system_effect) 

You clearly never managed 2 year project (and yours is two year hobby project, not 2 yr FT). Solve couple dozen problems from EulerProject, then join existing FOSS game project to learn the ropes. Jumping into deep end like you do will end up disaster and you will learn nothing.

Answer to bunch of questions like yours is: "if you have to ask for answer, you are not ready to solve it yet".

Of course do whatever you want in your own free time. For me it would be easier just to ignore you, and not waste 15 minutes to advise you. Maybe I will help you from disappointment, and prevent waste of your valiant efforts. Then, maybe not :-) 

Good luck, you will need it!

---

### Post by NathanB on 2008-06-24
> **IqAndreas said:**
> I have been programming for a few years with VB.net, and for my next large project I would like to move on to something that does not require Windows. I have also messed around with perl, a little java, java script, and HTML (which isn't really programming IMO).

I am converting the board game Twilight Imperium to a computer game, but I am not sure what programming language to use for this and future projects. There are so many out there that I don't know where to start, but I am quick to learn whichever one is best for my needs.

Primarily, I would like the language to be able to run on any platform, and even better would be to allow the programs to run without a platform, using a live CD to run the program. Best would be both options.

Second, I want it to be able to run without being dependent on runtime compilers. For example, perl (I believe) requires the user to have perl, and run it through that program every time they want to run it.
I want to be able to compile it once and then allow it to be used anywhere.

Third, I would like there to be a lot of people already using the software so I can get a lot of help and samples instead of writing pretty much everything from scratch.


What is Linux usually written in? Would that work for software as well?

I don't mind learning machine code if that is the best route and someone can point me in the right way. :)


It is pretty obvious that the only thing that meets all of your criteria is a Web-based application.  You already know most of what you need to create this thing.  But if you'd like to use this time to learn something new, then here are a few options:

Java Applets
[http://java.sun.com/applets/](http://java.sun.com/applets/)

Google App Engine
[http://code.google.com/appengine/](http://code.google.com/appengine/)

Flash
[http://www.adobe.com/products/flash/](http://www.adobe.com/products/flash/)

Those are from just the top of my head... others here can probably suggest more options. For a 'board game' I think the Google App Engine would be a good fit.

Nathan.

---

### Post by slavik on 2008-06-24
> **pmasiar said:**
> Quite obviously you do not know most basic of all basic concepts: software development is engineering (so it means balancing of contradictory requirements) and CPU's time is cheap: it's developer's time what is expensive. 
sometimes developer time is much much cheaper than the CPU time (look at anything that needs a cluster/grid to calculate), scientific computations usually use straightforward algorithms (word count on all internet text), but it will still take 2000 nodes a few hours to run. I can easily come up with interesting problems that will take more engineering time than actual development, and CPU time will overtake both put together.

> 
You are not concerned about development time at all, it suggests to me that you are just a student/hobby hacker who did not developed and maintained any program larger than couple hundred lines - so your chance in succeeding in this project is small.

Powerful language is not the one creating most effective code for number-crunching, but allowing to create whole application in least amount of code and least amount of time. 



wikipedia
umm, if you say you have programmed for as long as you have you should know that each language has its application, there is a reason Haskell is making great inroads into scientific computation. Like I said before, 10% performance penalty for an application is acceptable, 10% for a system is not. I would like to add to that, sometimes 10% is a measure done in weeks and maybe even months.

---

### Post by LaRoza on 2008-06-24
> **slavik said:**
> sometimes developer time is much much cheaper than the CPU time (look at anything that needs a cluster/grid to calculate), scientific computations usually use straightforward algorithms (word count on all internet text), but it will still take 2000 nodes a few hours to run. I can easily come up with interesting problems that will take more engineering time than actual development, and CPU time will overtake both put together.


But this is a board game!

---

### Post by slavik on 2008-06-24
> **LaRoza said:**
> But this is a board game!

which is exactly why they are fun on a cluster ... please note that BlueGenieL (the one that beat Kasparov at chess) had a team of CS and Chess Grandmasters working on it. Say whatever you want about developer time, but the actual supercomputer is very expensive to construct and operate (power and power for the cooling system), hence CPU time becomes expensive. Another thing to note is that BlueGenieL was able to play with Kasparov at pretty much his level (it won by a point, I think). Also, take into consideration that there is almost no calculations done in the beginning (the chess engine uses opening books) and at the end (there isn't much to compute). A chess game where both players have made 50 moves is considered a very long game (most games end before move 40), thus you don't need to calculate the first 5-10 moves, and the last 5-10 moves, which leaves you about 20-30 to compute and BlueGenieL could compute all possible (all possible meaning decent-good moves) combinations 15 moves ahead.

---

### Post by pmasiar on 2008-06-24
> **slavik said:**
> 10% performance penalty for an application is acceptable, 10% for a system is not.

... and the game OP proposed is an app, not a cluster program or operating system utility, so I do not see where we disagree, if any.

---

### Post by slavik on 2008-06-24
> **pmasiar said:**
> ... and the game OP proposed is an app, not a cluster program or operating system utility, so I do not see where we disagree, if any.
it's on the point of what being a "powerful language" means ...

---

### Post by LaRoza on 2008-06-24
> **slavik said:**
> which is exactly why they are fun on a cluster ... please note that BlueGenieL (the one that beat Kasparov at chess) had a team of CS and Chess Grandmasters working on it. Say whatever you want about developer time, but the actual supercomputer is very expensive to construct and operate (power and power for the cooling system), hence CPU time becomes expensive. Another thing to note is that BlueGenieL was able to play with Kasparov at pretty much his level (it won by a point, I think). Also, take into consideration that there is almost no calculations done in the beginning (the chess engine uses opening books) and at the end (there isn't much to compute). A chess game where both players have made 50 moves is considered a very long game (most games end before move 40), thus you don't need to calculate the first 5-10 moves, and the last 5-10 moves, which leaves you about 20-30 to compute and BlueGenieL could compute all possible (all possible meaning decent-good moves) combinations 15 moves ahead.

That is nothing special...the average person can't beat GNU chess ;)

The difference between computers and humans playing chess is that computers don't rip your arms off when they lose. (Or something like that)

> **slavik said:**
> it's on the point of what being a "powerful language" means ...

Give you the control you need without getting in the way?

---

### Post by slavik on 2008-06-24
> **LaRoza said:**
> That is nothing special...the average person can't beat GNU chess ;)

The difference between computers and humans playing chess is that computers don't rip your arms off when they lose. (Or something like that)



Give you the control you need without getting in the way?

heh, point taken about chess.

as for giving control, this is where it becomes interesting ... a computationally inclined language is very difficult to do UI with, and a language which is UI inclined is very difficult to do heavy computations with.

---

### Post by LaRoza on 2008-06-24
> **slavik said:**
> 
as for giving control, this is where it becomes interesting ... a computationally inclined language is very difficult to do UI with, and a language which is UI inclined is very difficult to do heavy computations with.

That is why you do the UI in a browser and the computations on a server.

Would you consider Perl or Python UI inclined? I don't think there is a real split in languages that way, now that things like Glade and such exist.

---

### Post by Can+~ on 2008-06-24
Did I just woke up in Opposite day?

1. 2 years of development
2. It's a ******* board game
3. Use a live CD to boot into game, how many games have done that? Oh right, none (unless you count console games as "Live CDs" (seriously, I don't)).
4. It should be multiplatform, but compiled, but it can't be interpreted, but it must be powerful... Which brings me back to number 2: It's a ******* board game.
5. Developing your own drivers / OS? Your own language?
6. Let me guess that you'll make your own soundtracks, your own animations, your own artwork.
7. It's a ******* board game.

(btw, the *******'s are not F-words)

I want to stab something in my face, now.

---

### Post by LaRoza on 2008-06-24
> **Can+~ said:**
> 
3. Use a live CD to boot into game, how many games have done that? Oh right, none (unless you count console games as "Live CDs" (seriously, I don't)).

They aren't, they do have an underlying operating system.

> 
I want to stab something in my face, now.
/me dons purple shirt

---

### Post by tinny on 2008-06-25
JAVA!!!

I have written a few applications in Java that run on Linux, Windows and Mac. I have to say it was a very nice experience!

There is an amazing tool set available for Java and if you get good at it you will have a job for life. Also there are HEAPS of open source libs available for Java development.

For games have a look at this [http://www.jmonkeyengine.com/]("http://www.jmonkeyengine.com/")

---

### Post by LaRoza on 2008-06-25
> **tinny said:**
> JAVA!!!

I have written a few applications in Java that run on Linux, Windows and Mac. I have to say it was a very nice experience!

There is an amazing tool set available for Java and if you get good at it you will have a job for life. Also there are HEAPS of open source libs available for Java development.

For games have a look at this [http://www.jmonkeyengine.com/]("http://www.jmonkeyengine.com/")

Um, I would suggest you read the thread ;)

(Also, your arguments in favour of Java apply to many languages)

---

### Post by Can+~ on 2008-06-25
> **LaRoza said:**
> They aren't, they do have an underlying operating system.

Thanks, that skipped my mind entirely while writing.

Now that I have a grip of myself, let's do a more reasonable speech, dear OP: 
-Most of your problems have been already solved. If we, humans, would reinvent the wheel each time we want to make a car, we would be still in the freaking stone age.

-Compiled language are translated to bytecode, which will run on the platform targeted of the compiling, therefore, you can compile for multiple platforms if you are in possession of said tools. Interpreted language, on the other hand, just need the interpreter there and are compiled at runtime (and in the case of python, stored as bytecode). The benefits of interpreted is that it solves a lot of issues like memory management (which, may be faster in CPU to write down your own management, but it's 10x your time, a free for each malloc).

-Learning the language is not the hard task, in fact, it's the most trivial part. It's like saying you're a painter just because you know how to move it over the canvas. Wrong. The most difficult part is the implementation of algorithms and data structures (or making in case they don't exist). How would you store the score? In a tree? Stack? Queue?, How to sort it? Quicksort? Heapsort? Insertion-sort for regular updates?

-Building your own OS demands knowledge on the most low levels you could get access to. And if you could do it, would your implementation be better than anyone else's? Why not just work with what is working now?

-Power / difficulty. Could you get me a chart that correlates the two of them? There's no such thing as power-difficulty. The most used things in your life are the ones you learn during your first years: how to speak, how to walk, how to eat, how to breath... But without them, we're screwed.

During my newbie days I used to think I could practically come up with something that's better than anything created for ____. Later you meet reality, and those ideas go away.

In conclusion, learn an existing language, preferably interpreted, and use SDL, don't try to reinvent the whole world.

---

### Post by Can+~ on 2008-06-25
> **tinny said:**
> java!!!

I Have Written A Few Applications In Java That Run On Linux, Windows And Mac. I Have To Say It Was A Very Nice Experience!

There Is An Amazing Tool Set Available For Java And If You Get Good At It You Will Have A Job For Life. Also There Are Heaps Of Open Source Libs Available For Java Development.

For Games Have A Look At This [http://www.jmonkeyengine.com/]("http://www.jmonkeyengine.com/")

Holy Crap It Has [Heaps](http://en.wikipedia.org/wiki/Heap_(data_structure))!

---

### Post by tinny on 2008-06-25
> 
Um, I would suggest you read the thread


Um, I did...?

> 
(Also, your arguments in favour of Java apply to many languages) 


Yes but Java is the best example of these advantages (This is my opinion having developed in C#, C, VB, Delphi and Java).

FYI:

[http://www.google.com/trends?q=java%2C+c%23%2C+python&ctab=0&geo=all&date=all&sort=0]("http://www.google.com/trends?q=java%2C+c%23%2C+python&ctab=0&geo=all&date=all&sort=0")

---

### Post by pmasiar on 2008-06-25
> **slavik said:**
> which is exactly why they are fun on a cluster ... please note that BlueGenieL (the one that beat Kasparov at chess)

IIRC it was [http://en.wikipedia.org/wiki/Blue_Gene](http://en.wikipedia.org/wiki/Blue_Gene) and  chess was side job: main focus was calculate protein folding (hence the "Gene").

Obviously in such expensive machines you need to take into account CPU time - but those are outliers, not relevant to OP question.

BTW you might be surprised that on biggest cluster on the planet (Google), even if C++ and Java is used for search and custom file system, deployment and management of all those servers is done in Python.

---

### Post by tinny on 2008-06-25
> **Can+~ said:**
> Holy Crap It Has [Heaps](http://en.wikipedia.org/wiki/Heap_(data_structure))!

Thanks for the [ThreadDeath]("http://java.sun.com/j2se/1.5.0/docs/api/java/lang/ThreadDeath.html") Can+~

---

### Post by pmasiar on 2008-06-25
> **tinny said:**
> Yes but Java is the best example of these advantages (This is my opinion having developed in C#, C, VB, Delphi and Java).

FYI:

[http://www.google.com/trends?q=java%2C+c%23%2C+python&ctab=0&geo=all&date=all&sort=0]("http://www.google.com/trends?q=java%2C+c%23%2C+python&ctab=0&geo=all&date=all&sort=0")

Your experience sadly lack any agile/dynamic language (Perl/Python/Ruby/Lisp/...). Even if Java is new COBOL, it does not make Java any more agile.

---

### Post by LaRoza on 2008-06-25
> **tinny said:**
> 
Yes but Java is the best example of these advantages (This is my opinion having developed in C#, C, VB, Delphi and Java).


No offense, but those languages are not a wide spectrum (except for C) they are all "blubbish".

If you compare something like Perl to Java, you'll see that Java isn't the best example.

[http://www.paulgraham.com/avg.html](http://www.paulgraham.com/avg.html)

---

### Post by CptPicard on 2008-06-25
> **LaRoza said:**
> No offense, but those languages are not a wide spectrum (except for C) they are all "blubbish".

Hey! I make 80% of my living in Java and I'm not blub... :)

Java has a bad rap for some strange reason which I do not completely understand. It's not remarkably marvelous, but it's not hideously awful either... I might actually even suggest the OP to look into Java for his cross-platform needs if he wasn't so far in outer space otherwise.

---

### Post by tinny on 2008-06-25
> **pmasiar said:**
> Your experience sadly lack any agile/dynamic language (Perl/Python/Ruby/Lisp/...). Even if Java is new COBOL, it does not make Java any more agile.

Not sure what your interpretation of Agile is? Are you talking about languages that make Agile software development easier?

Java has many tools to help refactor, test and perform continuous integration. The tools are amazing! I have done alot of agile software development quite happily. ;)

Hahah, a discussion like this is always going to be like talking about religion.

---

### Post by LaRoza on 2008-06-25
> **CptPicard said:**
> Hey! I make 80% of my living in Java and I'm not blub... :)

Java has a bad rap for some strange reason which I do not completely understand. It's not remarkably marvelous, but it's not hideously awful either... I might actually even suggest the OP to look into Java for his cross-platform needs if he wasn't so far in outer space otherwise.

But you have experience outside of it don't you? Your numbers are screwy, I recall you give a percentage of income from another source, and if added to this figure will result in over 100%...

I did recommend Java (along with Python and Perl, then C), but I was merely pointing out the good points about Java apply to other languages. C#, Java, Delphia etc isn't a broad range to draw such conclusions.

---

### Post by tinny on 2008-06-25
> **CptPicard said:**
> Hey! I make 80% of my living in Java and I'm not blub... :)

Java has a bad rap for some strange reason which I do not completely understand. It's not remarkably marvelous, but it's not hideously awful either... I might actually even suggest the OP to look into Java for his cross-platform needs if he wasn't so far in outer space otherwise.

Yeah in the Linux world Java does seem to have a bit of a bad name. I think its because all the Linux guys think they are too smart to use a main stream programming language.

I guess the main point I am trying to make is that the tool set for Java is fantastic! Also the availability of Jobs in Java cant be disputed.

---

### Post by CptPicard on 2008-06-25
I guess the point is that some languages are even more agile than others. While I do use Java professionally, I also agree with the statement that it is less agile than something like Python or Lisp.

> **tinny said:**
> 
Java has many tools to help refactor, test and perform continuous integration. The tools are amazing! I have done alot of agile software development quite happily.

Interestingly, the tools are mostly there to work around the language so that you can develop in an agile fashion. In other languages you don't need the tools because you don't have the problems you need the tools for in Java.

In particular refactoring is the automation of code alterations which tend to mostly arise from object oriented design and its limitations... taking one "this is how we work around the language to achieve this" state and transforming it, hopefully mostly automatically, into some "this is how we work around..." other state.

In more dynamic languages, refactorings are much easier because abstractions are generic and stuff tends to be written "right" and without Gang-of-Four Jumping-Through-Burning-Hoop Patterns...


> Hahah, a discussion like this is always going to be like talking about religion.


It really isn't, we have had a lot of interesting discussions on this exact topic here and IMO they are not flamewars although some people want to try to make them look like they are (mostly those who run out of arguments really).

---

### Post by LaRoza on 2008-06-25
> **tinny said:**
> Yeah in the Linux world Java does seem to have a bit of a bad name. I think its because all the Linux guys think they are too smart to use a main stream programming language.

Why is Java "mainstream"? Because of corporate pushing, which affects Linux less ;)

By itself, Java is nothing special on the desktop (devices another story)

---

### Post by tinny on 2008-06-25
> 
Interestingly, the tools are mostly there to work around the language so that you can develop in an agile fashion. In other languages you don't need the tools because you don't have the problems you need the tools for in Java.


Tools / Language, it doesn't matter. Its all about the end game.

---

### Post by CptPicard on 2008-06-25
> **tinny said:**
> Tools / Language, it doesn't matter. Its all about the end game.

Yeah, and in totality, Java is more unwieldy than, say, Python. There's just more "stuff" to work on/with/against.

---

### Post by tinny on 2008-06-25
> **LaRoza said:**
> Why is Java "mainstream"? Because of corporate pushing, which affects Linux less ;)

By itself, Java is nothing special on the desktop (devices another story)

This is what I mean by main stream (I can only comment on what ive seen in my home country of New Zealand).

About 80% of the coding at universities is done in Java.
Over half the coding jobs advertised here are Java.
4 of the 5 big banks in New Zealand basically run on J2EE. (Im involved in this industry). I see Java everywhere.

---

### Post by LaRoza on 2008-06-25
> **tinny said:**
> This is what I mean by main stream (I can only comment on what ive seen in my home country of New Zealand).

About 80% of the coding at universities is done in Java.
Over half the coding jobs advertised here are Java.
4 of the 5 big banks in New Zealand basically run on J2EE. (Im involved in this industry). I see Java everywhere.

Then that is true. Also, Britney Spears is "mainstream", but that doesn't make it good music ;)

It is pushed by companies, it is pushed in the corporate world, it is pushed in universities, and is popular because of it. 

In the free world, where corporate pushing is less prevalent, languages like C, Perl, and Python are used because the are better for the job at hand. There is rarely a case where "This looks like a job for Java!" can't be replaced with another language to increase development speed. Check out the link in my sig, and read the article about scripting.

---

### Post by CptPicard on 2008-06-25
> **tinny said:**
> 
4 of the 5 big banks in New Zealand basically run on J2EE. (Im involved in this industry). I see Java everywhere.

J2EE is indeed Java's strong point... when you are running a big bank.

Most people aren't. ;)

---

### Post by LaRoza on 2008-06-25
> **CptPicard said:**
> J2EE is indeed Java's strong point... when you are running a big bank.

Most people aren't. ;)

Do heists count? I could be in the "banking business"...

---

### Post by Yudraciell on 2008-06-25
> **Can+~ said:**
> A+ to Phenax (whoops, wrong nick).

You may also want to check a list of [available game engines](http://en.wikipedia.org/wiki/List_of_game_engines) ([Also, "notable" game engines]("http://en.wikipedia.org/wiki/Game_engine#Notable_engines"), since the list is huge), so you don't have to start from scratch. Of course, keep with OpenGL, as direct x is Microsoft only. Check also

OpenGL 3.0 is in development right now when it is released it will be able to clone if not surpass direct x 9.0c+ :popcorn:

---

### Post by slavik on 2008-06-25
> **Yudraciell said:**
> OpenGL 3.0 is in development right now when it is released it will be able to clone if not surpass direct x 9.0c+ :popcorn:

OGL2 already has everything needed as far as DX9 feature set is concerned ...

OGL3 will be OGL2 using OO.

---

### Post by tinny on 2008-06-25
> **CptPicard said:**
> J2EE is indeed Java's strong point... when you are running a big bank.

Most people aren't. ;)

Yeah but what about the volume of coding. E.g. Server Side vs Desktop???

---

### Post by CptPicard on 2008-06-25
> **tinny said:**
> Yeah but what about the volume of coding. E.g. Server Side vs Desktop???

I am not really sure I understand what you mean. In J2EE apps you have a very specific need for an enterprise stack with stuff like distributed transactions... there's way too much coding in Java anyway (tools are there partly to mitigate the verbosity) :)

Btw, the OP's plan of going about building his board game for some reason reminded me of this...

[http://en.wikipedia.org/wiki/Not_even_wrong](http://en.wikipedia.org/wiki/Not_even_wrong)

---

### Post by Frak on 2008-06-25
> **tinny said:**
> Yeah but what about the volume of coding. E.g. Server Side vs Desktop???
1. Java
2. It's really a tie between C/C++ and C#, and no, I'm not kidding
3. Visual Basic
4. Python
5. Ruby

It's from some O'Reilly book I just bought.

---

### Post by tinny on 2008-06-25
> 
Then that is true. Also, Britney Spears is "mainstream", but that doesn't make it good music ;)

Haha, nice.

> 
In the free world, where corporate pushing is less prevalent, languages like C, Perl, and Python are used because the are better for the job at hand. There is rarely a case where "This looks like a job for Java!"

There is a lot of open source Java code out there (including the HotSpot VM).

Also, what if I wanted to write a piece of software once and run it anywhere? Or if I wanted to tap into a large market of developers. Or use tools that had solid support behind them.

What about a performance comparison between Java and say Python

[http://mrpointy.wordpress.com/2007/11/06/java-vs-python-performance/]("http://mrpointy.wordpress.com/2007/11/06/java-vs-python-performance/")

These are massive ticks in the box for me.

I just have this over welling feeling that if I do it in Java It will get done.
> 
Check out the link in my sig, and read the article about scripting.

Will do.

---

### Post by LaRoza on 2008-06-25
> **tinny said:**
> 
There is a lot of open source Java code out there (including the HotSpot VM).

What about a performance comparison between Java and say Python

[http://mrpointy.wordpress.com/2007/11/06/java-vs-python-performance/]("http://mrpointy.wordpress.com/2007/11/06/java-vs-python-performance/")


I am not saying Java is useless, just over hyped. 

There is also open source C# code, but the majority of it isn't.

Performance is something that is specific to the task and purpose.

---

### Post by tinny on 2008-06-25
> 
I am not really sure I understand what you mean.


Ill rephrase. (I got a little lazy)

You said that most people aren't running a bank, true. But most people do benefit from a technology like J2EE. People get at least as much benefit from content delivered over the web as they do from their desktop applications.

We have to take into account all areas of software development when rating a language (server and desktop) (rating the technology is probably more important).

Opps, I seem to have hijacked this thread and moved away from the much more interesting topic of board games. :)

---

### Post by tinny on 2008-06-25
> **LaRoza said:**
> I am not saying Java is useless, just over hyped. 

There is also open source C# code, but the majority of it isn't.

Performance is something that is specific to the task and purpose.

C#, now theres a useless language ;)

---

### Post by CptPicard on 2008-06-25
> **tinny said:**
> 
You said that most people aren't running a bank, true. But most people do benefit from a technology like J2EE. People get at least as much benefit from content delivered over the web as they do from their desktop applications.

No, they honestly don't. In particular in writing normal, non-J2EE web apps, Java is an awful web development language. It's remarkably weak on that count. Trust me, I did Java web apps for a few years and then just gave up in disgust because of the unneccessary complexity.

See Python's TurboGears for a much nicer framework to work with.

---

### Post by LaRoza on 2008-06-25
> **tinny said:**
> C#, now theres a useless language ;)

Built to compete with Java, and is an improvement on Java in many opinions.

---

### Post by tinny on 2008-06-25
> **CptPicard said:**
> No, they honestly don't. In particular in writing normal, non-J2EE web apps, Java is an awful web development language. It's remarkably weak on that count. Trust me, I did Java web apps for a few years and then just gave up in disgust because of the unneccessary complexity.

See Python's TurboGears for a much nicer framework to work with.

I agree that JSP etc sucks. 

But J2EE is great! EJB's, JPA, JMS etc...

If you think you dont benefit from Java then I guess you dont have a bank account, insurance policy or use a credit card. Even though you may think these things are in someway freedom hating you still need them to buy food so you can live.

---

### Post by tinny on 2008-06-25
> **LaRoza said:**
> Built to compete with Java, and is an improvement on Java in many opinions.

I was a C# .Net developer for 1 year.

Worst year of my professional life!!! I don't know about Mono but C# .Net just wraps you in bubble wrap.

If you are happy solving problems the way you are told to, then great. Once again this is the technology not the language im talking about.

I believe the technology is more important than the syntax.

---

### Post by LaRoza on 2008-06-25
> **tinny said:**
> 
If you are happy solving problems the way you are told to, then great. Once again this is the technology not the language im talking about.

I believe the technology is more important than the syntax.

C# is the best language.

(If technology is what is important, use Python on Java ;) Jython)

---

### Post by tinny on 2008-06-25
> **LaRoza said:**
> C# is the best language.

(If technology is what is important, use Python on Java ;) Jython)

Java

I though you didnt like the bloated syntax and strict typing of Java, C# just builds on that (Name spaces, Properties etc...). 

Also good luck selling a Mono application to anyone.

---

### Post by LaRoza on 2008-06-25
> **tinny said:**
> java

I Though You Didnt Like The Bloated Syntax And Strict Typing Of Java, C# Just Builds On That (name Spaces, Properties Etc...). 

Also Good Luck Selling A Mono Application To Anyone.

C# Ftw. It is the language of the future. We should all use it.

(This is fun)

---

### Post by henchman on 2008-06-25
C# ist the best, agree... all the .net framework has "some" cool functions, too

And... C# has the best editor :P

but I personally think mono is not on this stage that you could say that .net is a crossplatform technology (when i tried it with some of my programs ~1 year ago, perhaps they improved a lot)

---

### Post by tinny on 2008-06-25
One thing we know for sure is that all these programming languages / technologies run best on Ubuntu Linux ;)

---

### Post by CptPicard on 2008-06-25
> **tinny said:**
> 
But J2EE is great! EJB's, JPA, JMS etc...

If you think you dont benefit from Java then I guess you dont have a bank account, insurance policy or use a credit card.

As I said, when you are running a bank or something then you need something like J2EE. Most of us aren't, and therefore it's way overkill, and it's horribly, horribly complex, at least the last time I looked at it. They say EJB3 is better, and that it's taken some cues from Spring... hopefully so.

But yeah, LaRoza is right, it's great that Microsoft gave us C#.

---

### Post by tinny on 2008-06-25
> 
They say EJB3 is better, and that it's taken some cues from Spring... hopefully so.


YES absolutely. In enterprise systems we still tend to use Spring, the Spring MVC framework is quite nice. EJB3 is good but still sucks when you try to bolt your front end on.

BTW I should have mentioned that many J2EE technologies can be used in Java desktop applications. I had a lot of fun building an application that used JPA > Hibernate > Derby DB (all in a desktop application). I just cant understand why more developers dont try and do this stuff. And yes people are buying this application, it runs on Linux, Windows and Mac!

---

### Post by pmasiar on 2008-06-25
> **tinny said:**
> Not sure what your interpretation of Agile is? Are you talking about languages that make Agile software development easier?

Java has many tools to help refactor, test and perform continuous integration. The tools are amazing! I have done alot of agile software development quite happily. ;)

"agility" had a meaning even before it was used for marketing purposes by sellers of java development tools and methodologies :-)

But I really think this discussion about java is wasted here, if you want to do it right, you should start "Why I love/hate Java" thread, and stop hijacking this one.

Also, to be more relevant, it would be helpful if you had some (or a lot) experience with dynamically typed languages, so you would know what are you arguing against. Surely Sun has enough money to promote the koolaid they sell :-) 

Your other comments suggests that most of your experience outside of Java is C#/.NET, which might be painful for you: language almost the same (no new useful features to make differences worth) and library painfully different. 

If you do want to start that discussion about java, start with reading [Execution in the Kingdom of Nouns](http://steve-yegge.blogspot.com/2006/03/execution-in-kingdom-of-nouns.html) and [Dynamic Languages Strike Back](http://steve-yegge.blogspot.com/2008/05/dynamic-languages-strike-back.html) - and blog of world Java expert [Bruce Eckel](http://www.mindviewinc.com/Index.php) why he moved to dynamically typed languages.

---

### Post by pmasiar on 2008-06-25
> **tinny said:**
> What about a performance comparison between Java and say Python

[http://mrpointy.wordpress.com/2007/11/06/java-vs-python-performance/]("http://mrpointy.wordpress.com/2007/11/06/java-vs-python-performance/")


Comparing apples to oranges, like other speed kiddies. 

1) Python can be compiled too - and should, if comparison claims any validity
2) most apps are limited not by speed of the app code, but by web server/DB server response time, IO, and stuff. So improving parts which are not critical makes little business sense.

---

### Post by Frak on 2008-06-25
> **pmasiar said:**
> 1) Python can be compiled too - and should, if comparison claims any validity

The latest GCC supports Python compilation into native binary. From my end, it is slightly faster.

---

### Post by nvteighen on 2008-06-25
> **Frak said:**
> The latest GCC supports Python compilation into native binary. From my end, it is slightly faster.
Really!? That's a nice one that will shut the whole Python vs. C++ discussion up. Which is the GCC version that supports it?

---

### Post by Lster on 2008-06-25
[QUOTE=Frak]The latest GCC supports Python compilation into native binary. From my end, it is slightly faster.
[/QUOTE]

[QUOTE=nvteighen]Really!? That's a nice one that will shut the whole Python vs. C++ discussion up. Which is the GCC version that supports it? [/QUOTE]

That would really rock. I'm up for some experimenting! ;)

---

### Post by IQAndreas on 2008-06-25
> **Can+~ said:**
> Did I just woke up in Opposite day?

1. 2 years of development
2. It's a ******* board game
3. Use a live CD to boot into game, how many games have done that? Oh right, none (unless you count console games as "Live CDs" (seriously, I don't)).
4. It should be multiplatform, but compiled, but it can't be interpreted, but it must be powerful... Which brings me back to number 2: It's a ******* board game.
5. Developing your own drivers / OS? Your own language?
6. Let me guess that you'll make your own soundtracks, your own animations, your own artwork.
7. It's a ******* board game.

(btw, the *******'s are not F-words)

I want to stab something in my face, now.

Will everyone stop thinking of it as just a board game!!
That will  be the crown of my achievements, but I am looking for a programming language to switch to for all my future projects.

> **Can+~ said:**
> 6. Let me guess that you'll make your own soundtracks, your own animations, your own artwork.
Actually, no. I'll be delegating that as well as some of the programming to other people, many of them friends of mine. However, I will be working on the main code to ensure that everything turns out just right. If you have 4 or 5 programmers working on the same application, there is a much higher chance of errors ocurring.

However, non-code related items will be handled by other people whenever possible.

---

### Post by IQAndreas on 2008-06-25
Wow. This thread became filled quick...

Thanks for some of the advice, and I hate to throw a wrench in the whole thing... The programming software has to be free or near free and allow people to make money off of the programs you sell.

I think Visual Studio Express Editions have some sort of rule that does not allow people to make a profit off of the software they create using their free editor and compiler.

It seems like many agree that C# would be the way to go. Are there any good editors for it? I have a Microsoft C# editor, but I think you are only able to run the compiled executable on windows computers.

---

### Post by pmasiar on 2008-06-25
> **IqAndreas said:**
> I am looking for a programming language to switch to for all my future projects.

...one language to rule them all! Of course it has to be C#, from MSFT, who gave us Vista, Outlook, IIS, and so many other gems.

---

### Post by Frak on 2008-06-25
> **nvteighen said:**
> really!? That's A Nice One That Will Shut The Whole Python Vs. C++ Discussion Up. Which Is The Gcc Version That Supports It?
Gcc 4.1.2

---

### Post by LaRoza on 2008-06-25
> **IqAndreas said:**
> 
It seems like many agree that C# would be the way to go. Are there any good editors for it? I have a Microsoft C# editor, but I think you are only able to run the compiled executable on windows computers.

In case people missed it, I was joking (as was CptPicard)

I think you should back up...You can use any editor, it is the compiler that matters.

C# is even worse for your goals.

---

### Post by tinny on 2008-06-25
> **LaRoza said:**
> In case people missed it, I was joking (as was CptPicard)

I think you should back up...You can use any editor, it is the compiler that matters.

C# is even worse for your goals.

YES!!!

> 
Thanks for some of the advice, and I hate to throw a wrench in the whole thing... The programming software has to be free or near free and allow people to make money off of the programs you sell.


Java, class library is open source and the runtime is open source. And you can make money from it!

> 
think Visual Studio Express Editions have some sort of rule that does not allow people to make a profit off of the software they create using their free editor and compiler.

It seems like many agree that C# would be the way to go. Are there any good editors for it? I have a Microsoft C# editor, but I think you are only able to run the compiled executable on windows computers.


If you where unfortunate enough to have to use C#

[SharpDevelop]("http://sharpdevelop.net/OpenSource/SD/")


Or [MonoDevelop]("http://www.monodevelop.com/Main_Page")

Also, I have NEVER had to pay for any Java development tools or technologies. Why does everyone think Java is plagued with commercial hooks??? Because people can actually make a living from it?

Here are two FREE Java editors you should look at:

[NetBeans]("http://www.netbeans.org/")
[Eclipse]("http://www.eclipse.org/")

C# Mono, beware of submarine patents!

> 
But I really think this discussion about java is wasted here, if you want to do it right, you should start "Why I love/hate Java" thread, and stop hijacking this one.


The thread creator doesn't seem to mind. Being the most popular programming language in the world I think it is completely relevant to talk about Java when trying the answer the question "What programming language should I use?".

> 
Also, to be more relevant, it would be helpful if you had some (or a lot) experience with dynamically typed languages, so you would know what are you arguing against. Surely Sun has enough money to promote the koolaid they sell  


Yep I would love too. But who is going to employ me at the end of it?

---

### Post by pmasiar on 2008-06-25
> **tinny said:**
> 
Java, class library is open source and the runtime is open source. And you can make money from it!

Same is true with python - and because you are 10 times as productive in Python, you may even make 10 times the money :-)

---

### Post by Lster on 2008-06-25
[QUOTE=Frak]Gcc 4.1.2[/QUOTE]

Sorry to be a little of topic, but would you mind posting a little example of how I would compile something. That would be ever so useful if you have the time! Thanks. :)

---

### Post by Frak on 2008-06-25
> **IqAndreas said:**
> I think Visual Studio Express Editions have some sort of rule that does not allow people to make a profit off of the software they create using their free editor and compiler.

There are no restrictions for making a profit.

> [7]("http://www.microsoft.com/express/support/faq/") Can I use Express Editions for commercial use?

Yes, there are no licensing restrictions for applications built using Visual Studio Express Editions.

---

### Post by CptPicard on 2008-06-25
> **tinny said:**
> Yep I would love too. But who is going to employ me at the end of it?

Oh, that's not a problem. Dynamically typed languages are very good for a lot of stuff, and there's this one guy who used to hang around here who codes professionally in Common Lisp pretty much exclusively, and loves it more than life itself. In particular, web apps are a great example of where *not* to use Java. Even in fairly enterprisey systems, you can just use the database as your focal point and then connect whatever systems to it (I never was a huge believer in doing everything through the Java stack, although that approach has its benefits -- that way Java "owns your project" a bit too much).

I use Java when I must, other languages whenever I can. Same applies to C pretty much. Frankly, as pmasiar said, you really need to know what you're talking about before mouthing off... before that, you're just blub:

[http://www.paulgraham.com/avg.html](http://www.paulgraham.com/avg.html)

By the way, if you want a cool dynamic language on top of the JVM which interfaces nicely to existing Java classes, look at Clojure. I'm trying to switch to it almost completely for situations where there is no need to use raw Java. It's just ... way superior.

---

### Post by LaRoza on 2008-06-25
> **CptPicard said:**
> Oh, that's not a problem. Dynamically typed languages are very good for a lot of stuff, and there's this one guy who used to hang around here who codes professionally in Common Lisp pretty much exclusively, and loves it more than life itself. In particular, web apps are a great example of where *not* to use Java. Even in fairly enterprisey systems, you can just use the database as your focal point and then connect whatever systems to it (I never was a huge believer in doing everything through the Java stack, although that approach has its benefits -- that way Java "owns your project" a bit too much).


It would be fun to have lars in here occasionally :evil:

> 
I use Java when I must, other languages whenever I can. Same applies to C pretty much. Frankly, as pmasiar said, you really need to know what you're talking about before mouthing off... before that, you're just blub:

[http://www.paulgraham.com/avg.html](http://www.paulgraham.com/avg.html)
I already pointed that out, but it never hurts to read it again.

---

### Post by pmasiar on 2008-06-25
> **tinny said:**
> The thread creator doesn't seem to mind. Being the most popular programming language in the world I think it is completely relevant to talk about Java when trying the answer the question "What programming language should I use?".

yes, but discussions about specifics of certain language are better kept in "love/hate" thread so they don't have to be repeated every time "which language" is started (about bi-weekly BTW).

> But who is going to employ me at the end of it?

Guys who sold YouTube (programmed in Python) to Google do not worry about being employed anymore. :-)

---

### Post by Can+~ on 2008-06-26
> **tinny said:**
> [http://mrpointy.wordpress.com/2007/11/06/java-vs-python-performance/]("http://mrpointy.wordpress.com/2007/11/06/java-vs-python-performance/")

The same page you posted links to the test site:
[http://www.twistedmatrix.com/~glyph/rant/python-vs-java.html](http://www.twistedmatrix.com/~glyph/rant/python-vs-java.html)

First, it starts like this:
"This paper is subjective, and as such,** is not meant to be a serious technical discussion of the various merits of these languages**. It is my own personal opinion, and we all know what opinions are like. "

Second, the same webpage eximplifies where the beauty of python is:
> [IMG]http://img.photobucket.com/albums/v517/CanXp/screenshot2-2.png[/IMG]

Please compare left-side vs right-side space used. We give two craps if Java does things 0.00001x or 4x times faster than python (or inverted), the thing we praise is on the code alone. You probably won't notice the extra milliseconds your processor will shoot if working with one or other language, but you'll clearly notice your extra hours it takes to build an application, when you could use a more **Expressive Language**.

Even if you wanted raw speed, just #include <Python.h> and start hacking in C.

But it doesn't matter, you're a speed kiddie, right? Or a Blub? It's hard to tell.

---

### Post by tinny on 2008-06-26
> 
But it doesn't matter, you're a speed kiddie, right? Or a Blub? It's hard to tell. 


I think thats the 4th time ive been called a blub.

> **tinny said:**
> 
I believe the technology is more important than the syntax.


Anyway its been fun guys. :-)

---

### Post by CptPicard on 2008-06-26
> **tinny said:**
> I think thats the 4th time ive been called a blub.

Well, you are very clear on not having experience on what you criticize, and thus it's hard to tell if you actually would feel differently if you did... :)

I use Java too and don't "hate" it as viscerally as some people around here (they are guilty of a sort of inverse irrational fanboyism), but it's hardly perfect. It often gets the job done, but that's the boring, uninteresting part... using Java is such a huge, brain-numbing slog :)

That "technology is more important than syntax" is only sort of partially true. Syntax of no fundamental importance, but as it expresses concepts we have in our mind about the problem we're solving, it and the associated semantics are important at our brain-code interface, not as much at the computer-code interface.

As far as the language itself is malleable and expressive enough, the technology can be just developed... it just follows. You can easily see that when given a good language people will run away with it and create interesting technologies. *Technology is an after-effect of language*.

Java's "techonology" is monumental, but that it is so in size is because of the static typing of the language. That creates an explosion of types and the code needed to handle the types plus the encapsulation requirement through all kinds of "design patterns".

Languages like Lisp for example are extensible by design, and this one Lars guy I mentioned for example is creating a really really cool web framework based on Lisp's abilities. It's concise, it's elegant, and it does some remarkable stuff. I can't even being to think of how to do it within the rigidity imposed by Java.

I guess we're just trying to show you that there is a reason *why* a lot of very competent people have come to the conclusions they are expressing here. :)

EDIT: just read this... all C++ weenies, check this out

[QUOTE=Bjarne Stroustrup]
 Convincing the systems programming community of the value of type checking was surprisingly hard. The idea of checking function arguments against a function declaration was fiercely resisted by many - at least until C adopted the idea from C with Classes.[/quote]

The C guys originally had it right... but were then lured to the dark side. ;) (Yes, I know that the right way to do it is still with strict typing..)

---

### Post by tinny on 2008-06-26
LaRoza, I just did your Language Selector questionnaire

Im going to learn Assembly! :eek:

---

### Post by nvteighen on 2008-06-26
> **Lster said:**
> Sorry to be a little of topic, but would you mind posting a little example of how I would compile something. That would be ever so useful if you have the time! Thanks. :)

While the rest discussed again the same things as always, we're actually concerned on something slightly more serious :)

It seems you'll have to build gcc from source with a custom --enable-languages flag? In a Terminal, type:
```

gcc -v

```

That will show you how your gcc was built.

---

### Post by Lster on 2008-06-26
Looks like I would need to recompile GCC myself. I have no idea how this could be done.

---

### Post by LaRoza on 2008-06-26
> **tinny said:**
> LaRoza, I just did your Language Selector questionnaire

Im going to learn Assembly! :eek:

Have fun. Assembly was fun to learn.

---

### Post by slavik on 2008-06-26
> **pmasiar said:**
> yes, but discussions about specifics of certain language are better kept in "love/hate" thread so they don't have to be repeated every time "which language" is started (about bi-weekly BTW).



Guys who sold YouTube (programmed in Python) to Google do not worry about being employed anymore. :-)

I am missing the point about YouTube, because I am sure that Google buying YouTube had nothing to do with the fact that YouTube uses Python (it's a page with a flash video player that fetches videos from a content server, not very complicated from my point of view which involves very little web development knowledge) but with the fact that it was unique and almost nobody used Google videos.

---

### Post by lunarcloud on 2008-06-26
[http://cartan.cas.suffolk.edu/oopdocbook/opensource/](http://cartan.cas.suffolk.edu/oopdocbook/opensource/)

C++ and Qt should be good if you've got a java background and want crossplatforming.

---

### Post by pmasiar on 2008-06-27
> **slavik said:**
> I am missing the point about YouTube, because I am sure that Google buying YouTube had nothing to do with the fact that YouTube uses Python (it's a page with a flash video player that fetches videos from a content server, not very complicated from my point of view which involves very little web development knowledge) but with the fact that it was unique and almost nobody used Google videos.

They developed YouTube specifically to be bought by Google, and using technology Google likes.

And don't say that technology used by acquired company has no effect on buying decision: when products are under single roof, they have to be compatible, and team skills transferable.

---

### Post by molotov00 on 2008-06-27
Have you considered making it a web-based game? I'm unfamiliar with the game you want to make but for simple turn-based games the web works well. PHP would be the obvious choice there -- it's what most of those types of games are coded in.

I've recently learned Python which is an interesting language. But it's not a good first language to learn IMO. It all depends on what you want to achieve. PHP can get the job done but you aren't going to become a good programmer because the language is not very strict. Something like C or Java will make sure you become a better programmer but it'll take longer to learn.

Python is on my mind now because I like it's versatility but I wouldn't code anything serious in it. I mainly use it to automate tasks and grab stuff from websites. There are a lot of modules out there that will cut down the development time also.

Only you can decide. But hopefully the posts here have given you some idea about what to look at.

---

### Post by rnodal on 2008-07-08
Instead of recommending what to do I will let you know what I'm doing, what my goals are and you judge for yourself if it applies to you.

What I'm doing:
2D Game engine that runs on popular platforms (Linux, Windows Mac, etc) that handles input, sound, video, physics, scripting, etc with minimal dependencies so the developer does not have to worry that much about the user having 3000 libraries installed. For that I'm using C++, SDL, OpenGL. Note that SDL is a "for now" solution. 

My code so far can compile, in Linux and Windows without changing one line of code. I don't have a Mac machine so I can't report about that.

My Goals:

Reduce the dependencies only to C++ standard library, my engine and OpenGL. All the developer would have to do is to code his game in his favourite platform, compile the other versions in the corresponding platforms and ship the game. The use, well just double clicks the executable and plays.

It will be a long road but that is ok. 

Good luck in whatever you decide to do.

-r

---

### Post by pmasiar on 2008-07-08
> **rnodal said:**
> What I'm doing:
2D Game engine that runs on popular platforms (Linux, Windows Mac, etc) that handles input, sound, video, physics, scripting,

How is your engine different/better than pygame? I don't know, your engine might be better, but it's long time to get there, right?

---

### Post by rnodal on 2008-07-08
I have not used pygame. It is my senior project so I had to do it any ways. But you are right it is a long term project. For my senior project goals I'm done 65% done. The other goals that I mention are long term goals that I plan on implementing on my free time. So once I submit my senior project I will make it public. :)

This is some comparison to what is written in pygame website.

> Python is actually quite capable at running games. It will likely even surprise you how much is possible in under 30 milliseconds. Still, it is not hard to reach the ceiling once your game begins to get more complex. Any game running in realtime will be making full use of the computer.

This is why I chose C++, and I do plan on providing ASM optimizations but as a long term goal (in other words as something to do once I submit my senior project for grading :)).

> Over the past several years there has been an interesting trend in game development, the move towards higher level languages. Usually a game is split into two major parts. The game engine, which must be as fast as possible, and the game logic, which makes the engine actually do something. It wasn't long ago when the engine of game was written in assembly, with portions written in C. Nowadays, C has moved to the game engine, while often the game itself is written in higher level scripting languages. Games like Quake3 and Unreal run these scripts as portable bytecode. 

I do plan on adding scripting support but still provide the old way of doing things if the developer prefers to go that way. This is future thing since it is not part of my senior project requierments.

> It is impressive how well both Python and SDL work on multiple platforms. For example, in May of 2001 I released my own full Pygame project, SolarWolf, an arcade style action game. One thing that has surprised me is that one year later there has been no need for any patches, bug fixes, or updates. The game was developed entirely on windows, but runs on Linux, Mac OSX, and many Unixes without any extra work on my end.
 

My engine will take care of the dirty details so you code once also but you do have to recompile ofcourse.


> Still, there are very clear limitations. The best way to manage hardware accelerated graphics is not always the way to get fastest results from software rendering. Hardware support is not available on all platforms. When a game gets more complex, it often must commit to one or the other. SDL has some other design limitations, things like full screen scrolling graphics can quickly bring your game down to unplayable speeds.
 
My engine does not use SDL for rendering at least not when OpenGL is available. I guess a down side of my engine will be that it is aimed at people with OpenGL support. But we'll see what happens.


> Pygame is faily low level when it comes to writing games. You'll quickly find yourself needing to wrap common functions into your own game environment. The great thing abuot this is there is nothing inside pygame to get in your way. Your program is in full control of everything. The side effect of that is you will find yourself borrowing a lot of code to get a more advanced framework put together. You'll need a better understanding of what you are doing.

My engine aims to provide high level functions. (At least to me :)) without removing the possibility for the developer to add in whatever he feels like.



I don't consider my engine to be the best or anything(it is not even done yet). I'm actually molding it to my likes and if it is useful to someone else great, if not then I apologize from the bottom of my heart.


-r

---

