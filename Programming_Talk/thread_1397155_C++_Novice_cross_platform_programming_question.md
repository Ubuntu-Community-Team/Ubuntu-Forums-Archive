---
title: "C++ Novice cross platform programming question"
date: 2010-02-02
forum: Programming Talk
---

### Post by Jonas thomas on 2010-02-02
I'm taking a C++ class.  The class uses visual studio, but the instructor a windows guy but is open to us downing our homework using Gcc and Linux.

On principle, I want to be able to able to run my code  either Windows or Linux.

At this point, our projects to be submitted as a single .cpp file (no headers)

I'm getting hung up with the clearing the terminal screen and the system pause and think it would be able to compile the .cpp file without modification either in windows or Linux.

**_Windows_** 
system("cls");//clear the screen in windows:
system("pause");// pause to keep the terminal open

**_Linux_**
#include <"stdlib.h"> // Apparently not required 
                      //with windows to call system
system ("tput clear");
// pause is not an issue on Linux on return from main();

---------------
'I suppose I need some sort of pre-processer directive to figure out how to return the OS that I'm compiling in and then to figure to throw in some sort of and selective #define either  "pause" or "tput clear"? Is that how its done?

Sorry about the babbling... Looking for info on C++ on the net is like walking through a dense forest.  I'm not asking for an answer, just the appropriate search terms or a link to recommended Tutorial discussing cross-platform issues for novice C++ programmers?  I'm running into a bit of a deadline here and if I'm not careful I'm going to get hoisted up by my own [petard]("http://en.wikipedia.org/wiki/Petard")s.

---

### Post by Jonas thomas on 2010-02-02
It think I found my answer here:
[http://www.computing.net/answers/programming/detecting-operating-system-in-c/8779.html]("http://www.computing.net/answers/programming/detecting-operating-system-in-c/8779.html")

I guess the magic search term I was looking for is "portable C++".
I'm some point I need to read through: [C++ Portability Guide]("https://developer.mozilla.org/en/C___Portability_Guide")

If think I found what I need, but if some what else has a really good link for C++ portability... feel free.

---

### Post by MadCow108 on 2010-02-03
system is a _very_ dangerous and non portable function.
you should basically never use it (except for convenience during development only, NEVER use it in production code)

To keep a terminal open there is an easy portable way:
require some input at the end of the program:
...
getchar()

clearing the terminal is of course not portable because its dependent on the terminal, but if you really require it you should use a terminal library like ncurses which is so far I know also ported to windows.

General rule write portable code:
stick to C/C++ standard code only and choose the standard on the age of systems you want to support (e.g. C89 or C99 etc)
C99 and C++98 have very good support in the major compilers nowadays (basically everything except c++'s broken-by-design export).
in gcc compile with -std=whatever -pedantic -ansi -Wall

Also remember to encapsulate carriage returns (\r\n) and directory separators (/ \), as they differ between windows and linux.

---

### Post by Jonas thomas on 2010-02-03
Very interesting comments...
Could you elaborate on instances where "system" is dangerous.

---

### Post by Zugzwang on 2010-02-03
System is a dangerous command in instances in which a program is run with more rights than the user of the system has. In some cases there is the possibility for the user to inject commands into calls to "system" and thus obtain more rights on the system. 

Furthermore, it is "dangerous" because it is non-portable, as you have also got to know. Even on different computers with the same operating system, you might run into problems as you normally cannot assume that user X has program Y installed *and* in the shell path.

---

### Post by Jonas thomas on 2010-02-03
> **Zugzwang said:**
> System is a dangerous command in instances in which a program is run with more rights than the user of the system has. In some cases there is the possibility for the user to inject commands into calls to "system" and thus obtain more rights on the system. 

Furthermore, it is "dangerous" because it is non-portable, as you have also got to know. Even on different computers with the same operating system, you might run into problems as you normally cannot assume that user X has program Y installed *and* in the shell path.

Very interesing...
I'm wish to develop good c++ programming habits from the get go so I'm loving these comments.  
Regarding "system" portability issues. Good point... At this point, I'm writing baby code that I want to run at home(Linux), or at school/work(Windows Vista(yech)/XP).  In the long run I should consider Mac and everyone else...

I think I should be able to come up with something universally portable for pausing the terminal using clearing out the input buffer using cin.ignore and getchar (I need to think on this a bit... No answers please).

What should be the general area I should look to make something universally portable to clear a screen without getting crazy with lots of code.  I don't suppose there is something easy.... Is there? (no direct answers please... just general direction to look.

---

### Post by dwhitney67 on 2010-02-03
> **Jonas thomas said:**
> 
What should be the general area I should look to make something universally portable to clear a screen without getting crazy with lots of code.  I don't suppose there is something easy.... Is there? (no direct answers please... just general direction to look.

Don't focus too much on user I/O from a terminal.  Most applications do don't utilize these.  Typically, C/C++ apps have GUI front-ends, and those that are used on embedded-systems, well many do not even have a terminal!

The C++ language is standardized, and as is the C library.  Stick to using these so that I will not matter which platform you use.  If you come across a C library function that is specific to GNU (Linux), weigh your options.

---

### Post by Maz_ on 2010-02-03
As a last restort you can consider writing some system specific pieces in different files. However for such subsystems it is often good to have common API. For example, if you really need a process management interface, you may want to do following setup:

A common interface for process management, no matter what underlying system is:
MyCreateProc( )
MyKillProc()
MySemaphoreCreate()
MySemaphoreWait()
MySemaphorePost()

etc.

write one common public header for these, and propably also one common C file with these functions.

Then write system specific files, which really implement these functionalities for each system. For example
MyProcMgmt_Linux.c
MyProcMgmt_Windows.c
MyProcMgmt_Mac.c

with functions like
MyCreateProc_imp()
MyKillProc_imp()
.
.
.

Then at compile time you can decide which files to take into compilation.

For small differences you can also use #ifdef, #ifndef and #if precompiler options to provide different code depending on defines passed. But this usually leads into few problems like:

1. How to guarantee that operation is same regardless the underlying system?
2. Harder maintenance / bug fixing
3. Messy code.

Usually these will however be needed in some places, when you write decent sized multiplatform SW in C/C++.

In general, before starting to write portable code, one should consider if the portability is REALLY needed. It is always way easier to write system specific code, which allows you to use all features the system's API allows. Selecting for example linux and windows to be supported, one will face problems when using sockets (basic things will succeed with very little troubles though), linux signals, linux "files", IPC mechanisms etc. And I do not even know what all cannot be used from windows world. Basically, writing portable SW is somewhat like making a house, when you need to start by cutting the wood from the forest all by yourself, compared to just obtaining large element blocks for walls.

---

### Post by akvino on 2010-02-03
I have a similar question:

> 
Don't focus too much on user I/O from a terminal. Most applications do don't utilize these. Typically, C/C++ apps have GUI front-ends, and those that are used on embedded-systems, well many do not even have a terminal!


I never worked as professional developer only as Linux/UNIX admin, although I am itching for turn in a career toward C++ development.

How does C++ professional development work - I never understood what is expected of C++ developer.

Does a C++ developer need to know Qt or GTK, is it more group oriented vs. individual oriented coding? How are distributed application done, is there GUI team (when I say team, I mean specialization), network/socket programming team, GUI team? What is the difference between Junior and Midlevel programmer? How good do you need to be with C libraries on Linux? 

Eh see where I'am going with this... :confused:

---

### Post by dwhitney67 on 2010-02-03
> **akvino said:**
> 
I never worked as professional developer only as Linux/UNIX admin, although I am itching for turn in a career toward C++ development.

Funny; I want to do the opposite.

> **akvino said:**
> 
How does C++ professional development work - I never understood what is expected of C++ developer.

It depends on the skill level of the programmer.  On some projects, there's a mix of junior-, mid-, and senior-level developers.  Generally the junior and mid level implement the code for a CSC (computer s/w component) that a senior developer has designed.  In some cases, the senior engineer writes code as well.

> **akvino said:**
> 
Does a C++ developer need to know Qt or GTK, is it more group oriented vs. individual oriented coding?

The more one knows, the better they are able to make wise decisions on the s/w architecting aspects of the project.

> **akvino said:**
> 
How are distributed application done, is there GUI team (when I say team, I mean specialization), network/socket programming team, GUI team?

It varies from one organization to another.

> **akvino said:**
> What is the difference between Junior and Midlevel programmer?

Most notably, the salary.  Another factor is experience -- basically knowing the best approach to solving a problem, or being familiar enough with the "tools" of the trade.  Most mid- and senior- level engineers can develop code without having to reference tutorials/manuals or even consulting amongst themselves.

> **akvino said:**
> How good do you need to be with C libraries on Linux?

It's just best to be familiar with it.  Don't try to be an expert in every possible nook/cranny of the libraries -- that might take a lifetime.

> **akvino said:**
> 
Eh see where I'am going with this... :confused:
At my current job, I'm always confused.  The s/w was written pre-1999, albeit in C++, by a bunch monkeys that had little experience with maintaining s/w.  I suppose they didn't give a damn that 10 years later, someone would have to maintain their 500K lines of crap, err.. code.

The team I work with consists strictly of senior developers; very rare to encounter this in the industry.  None of the developers know every aspect of the s/w.  Many times a simple question will draw blank stare from everyone.  Basically, if one wants to understand something, they must research the code themselves.

---

### Post by akvino on 2010-02-03
Thanks for the reply:

Here is some programming humor:

There are 10 types of people in this world.

Those who understand binary, and those who don't.
------------------------

DEBUGGING : Removing the needles from the haystack.
------------------------

"C makes it easy to shoot yourself in the foot. C++ makes it harder, but when you do, it blows away your whole leg."

- Bjarne Stroustrup
------------------------

Real programmers are surprised when the odometers in their cars don't turn from 99,999 to 99,99A.

------------------------

Programming is 10% science, 25% ingenuity and 65% getting the ingenuity to work with the science.

------------------------

The human mind ordinarily operates at only ten 10% of its capacity, the rest is overhead for the operating system.

------------------------

A computer scientist is someone who fixes things that aren't broken.
------------------------

The computer is mightier than the pen, the sword, and usually the programmer.

------------------------

Programming is an art form that fights back.
------------------------

If at first you don't succeed, you must be a programmer.
------------------------

If God had intended humans to program, we would be born with serial I/ O ports.

------------------------

Programming is a lot like sex. One mistake and you could have to support it the rest of your life.

---

### Post by Jonas thomas on 2010-02-03
> **dwhitney67 said:**
> Don't focus too much on user I/O from a terminal.  Most applications do don't utilize these.  Typically, C/C++ apps have GUI front-ends, and those that are used on embedded-systems, well many do not even have a terminal!

The C++ language is standardized, and as is the C library.  Stick to using these so that I will not matter which platform you use.  If you come across a C library function that is specific to GNU (Linux), weigh your options.
I've programmed alot in vb6 at work for internal use and I thought I could read a book watch a few videos and I'd be off an running writting C++ code.  I tried out gtk, gtkmm, qt and wxwidgets on my free time for my home use but I think I was biting off way too much to fast.  I took a beginners class to slow down and appreciate the nuances of the language.  For me at least I can't just read a book on C++ and code.  It's been very frustrating to me that I can write some very complex application in vb without thinking about it, but feel like a total Noob trying to do the most elemental things in C++

I suppose when I feel that I'm more proficient at C++ to use it work, I'll probably won't have the time or need to make it portable code on my work stuff.

The pace of class at the moment is such that I can ponder these esoteric questions for the moment. In the next week or so I will have Visual Studio installed on my work machine, but I really want to keep my home machine using Linux.  As near as I can tell the class will be using consul apps for a while, which why I'm interested in this stuff.  Will I use consul app's in a production environment... Heck no, but for now it's where I'm at.  Besides, those consul app's bring back fond memories of my dos days...

---

### Post by dwhitney67 on 2010-02-03
Be aware that many of the features of VC++ that enables one to develop a GUI are not portable.  The concepts are, just not the code.

Learning a programming language is important, however learning concepts is paramount to that.

In a work environment, oftentimes the platform is chosen much before the language is.  So I wouldn't sweat the portability issue too much.  But if you are interested in such, then stick to learning under Linux/Unix; they are more likely to be in tune with the standards than some money-grubbing firm like M$.

---

### Post by Jonas thomas on 2010-02-03
> **dwhitney67 said:**
> Be aware that many of the features of VC++ that enables one to develop a GUI are not portable.  The concepts are, just not the code.

I know a alot of people look down at vb6, but I love that IDE. I have a over a decade of code in that stuff.  I was so ticked that MS ended support for it. Yeh the code will still run but the IDE is no longer supported.  I made it my goal that if I was going to learn something new it wasn't going to be C# or VB.net.  
That lack of portability was one of things that intrigued me about QT and wxwidgets.  I started studying QT but I didn't think I could get work to buy a license (before trolltech made it LGPL) so I started checking Wxwidgets instead.  I was trying to soar before I was ready.. I hope to develop a coding style where I can strip the MS gui portions out if I ever choose to do that.
I was paging through the 20 chapter book the class is using: Starting out with C++ from Control Structure through Objects by Tony Gaddis(nice book but way too expensive) and as near as I can tell it's all console aps.  Vb6 has turned me into a bit of a guiholic so this will be interesting to me on many levels.
Any... need to finish my homework before class

---

