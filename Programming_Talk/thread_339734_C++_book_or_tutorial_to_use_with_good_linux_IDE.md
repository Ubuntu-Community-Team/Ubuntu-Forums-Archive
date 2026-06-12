---
title: "C++ book or tutorial to use with good linux IDE?"
date: 2007-01-16
forum: Programming Talk
---

### Post by maksym on 2007-01-16
Hi, probably an old topic but I could not find satisfactory answer in the forums:

Background:

1. I have recently switched to ubuntu from windows and happy with that
2. I work in finance and used to do many small programs in VBA / Matlab to suite my needs
3. Open office supports VBA macros but it is not exactly the same experience, so I need a new language to for modelling
3. C/C++ seems to be the tool of choice since 
	a) there are a couple of free compilers 
	b) it seems to be least prone to major overhauls (look at the change of VB to
                    VB.net) so best time investment in the long run.
	c) is still very popular in financial industry
4. I have practically no experience in c/c++

Now, here comes my question: **are there any books/tutorials for c/c++ using linux based  IDEs? **I have seen many books around which teach you the language assuming some windows based IDE but none for linux. I am new to c/c++ so setting up a  
working programming environment in ubuntu is more challenge to me than actually understanding key concept c/c++.

Any ideas as to where to start would be very welcome!

---

### Post by Lord Illidan on 2007-01-16
As regards tools, anjuta is a very nice tool to work with c++/c. It is an IDE.

I also know about books regarding QT and GTK+, two of the main toolsets used in Linux.

Google is your friend, as always.

---

### Post by amo-ej1 on 2007-01-16
just as a side note, since you're proficient with matlab you might also consider gnu octave ([www.octave.org](www.octave.org)) as an option, this is an 'open' matlab implementation (matlab even works onder linux too). 

When working in finance i'd first say that C/C++ is more dangerous to use, since C/C++ lets you overflow values extremely easy when numbers get too huge ... (you don't like going you bank account from + a couple of million do - a couple of million ?). 

But if you still feel like learning c/c++ there are a loot of good books out there C++ primer and The C programming language will be some of the most standard works to learn there languages. But I'm sure all the other people here will have lots of other suggestions too ;)

---

### Post by Wybiral on 2007-01-16
This thread has some C++ tutorials on it: [http://ubuntuforums.org/showthread.php?t=333867](http://ubuntuforums.org/showthread.php?t=333867)

Also, there usually isn't a need for an IDE, especially when you're trying to learn the language, I would suggest using a text editor (like gnomes GEdit, comes with ubuntu) and the command line to compile.

IDE's usually aren't much help until later on, and even then a lot of people still don't use them.

BTW, most C++ tutorials, as long as they don't use any specific libraries will work on linux. Anything that uses standard C++ without any external lib's...

Good luck, btw!

---

### Post by maksym on 2007-01-16
Thanks everyone for the suggestions!

Concerning Octave - I have actually looked at it but it appeared on at first glance to provide console only interface. This is fine to compute ugly matrixes but is it possible to easily visualise my input/output data and build plots/histograms...? 

I would not be too concerned with overflows right now since my tasks are of not directly related with banks operations.

c++ seems a good choice since I can build a library at home in Linux environment and use it at work (Windows XP here) with Excel as front-end or as in Matlab. Speed of calculations is also important consideration. Both VBA and Matlab are very far from ideal when it comes to MonteCarlo simulations.

I wanted a tutorial with the use of IDE because I thought that IDE would provide a more efficient way of debugging. However when I open Anjuta or KDevelpe (remember I am complete novice :) ) the nice features and error messages which mean absolutely nothing to me are overwhelming :)  So as Wybiral suggested a simple text editor and GCC are probably the best alternative after all...

---

### Post by Wybiral on 2007-01-16
You can combine libraries... You might want a well equipped math library to handle the numbers, and a nice plotting library for graphs and stuff. Graphic libraries are easy to find, just use the data from the math library in the graphics library.

---

### Post by amo-ej1 on 2007-01-16
Octave offers a lot of visualisation using gnuplot (just try the plot command). The only negative thing is that there is indeed no fancy GUI like matlab.

If i recall correctly, there is some effort being put into a gui and things like that.

---

### Post by maksym on 2007-01-16
amo-ej1, actually I have downloaded the Octave for windows (at work) and gave it another look. I does seem to be very similar to MatLab and has very decent plotting capabilities. I might end up learning both c++ and Octave, LOL :mrgreen: Does anyone know how compatible both Matlab and Octave are?? E.g. I find a nice statistical distribution fitting routine written for Matlab - can use it in Octave as well ?

---

### Post by lloyd mcclendon on 2007-01-16
> **amo-ej1 said:**
> When working in finance i'd first say that C/C++ is more dangerous to use, since C/C++ lets you overflow values extremely easy when numbers get too huge

and this is only a bad thing in the finance industry?  



for an IDE you definately want eclipse with the CDT plugin set.  eclipse is great, hands down the best IDE out no doubt.  [www.yoxos.com/ondemand](www.yoxos.com/ondemand)

a text editor and the command line is ok but once  you get more than 3 files in a project you start to be less productive.  and eclipse's debugger is pure sex.

---

### Post by ohgod on 2007-01-16
For books, I'd recommend "Thinking in C++"....

---

### Post by Wybiral on 2007-01-16
> a text editor and the command line is ok but once you get more than 3 files in a project you start to be less productive. and eclipse's debugger is pure sex.

I'm going to disagree. It really depends on the person, and the persons computer. I can't program quickly in eclipse because my computer freaks out every time I open it (eclipse is quite the memory muncher)

Also, I can see more code in Gedit, which means I can remember more before and after the chunk I cam working on.

And, for anyone who knows their language well enough, they shouldn't need a super debugger to figure out a problem... Generally with C++ the gcc compiler response is enough for me to tell whats wrong.


BUT, like I said... It's really a personal preference.

(as far as files go... You can only work on so many at one time, a text editors tabs should be more than enough, and for compiling... use a makefile...)

---

### Post by tpg on 2007-01-16
Regarding GUI programming, I found the free Qt 3 book/pdf ("C++ GUI Programming with Qt 3") really useful, and the Qt 4 book is now being sold. These books teach Qt by coding user interfaces manually, and by using the Qt form designer. I also found KDevelop fairly easy to pick up after reading through the first couple of chapters of the Qt 3 book.

If you want to learn Qt, then I'd recommend the first (free) book.

---

### Post by jblebrun on 2007-01-16
> **Wybiral said:**
> I'm going to disagree. It really depends on the person, and the persons computer. I can't program quickly in eclipse because my computer freaks out every time I open it (eclipse is quite the memory muncher)

Also, I can see more code in Gedit, which means I can remember more before and after the chunk I cam working on.

And, for anyone who knows their language well enough, they shouldn't need a super debugger to figure out a problem... Generally with C++ the gcc compiler response is enough for me to tell whats wrong.


BUT, like I said... It's really a personal preference.

(as far as files go... You can only work on so many at one time, a text editors tabs should be more than enough, and for compiling... use a makefile...)

Not all bugs produce compiler errors or warnings... the compiler isn't going to be much help when your program segfaults. :-)

I do agree that Eclipse is ridiculously resource intensive for what you get. Gvim has served me well for quite a few years now.

---

### Post by Unterseeboot_234 on 2007-01-16
The bulk of my academic work was C++, but at the time that language wasn't well suited to GUI and linking. I took up Java and never looked back. However, QT4 took my breath away. It is almost everything java but very, very fast with very nice graphics. If they ever make a plug-in for C/C++/C# then java will have some competition.  For cool C++ check out 

[http://www.trolltech.com/](http://www.trolltech.com/)

just for the QT4 demos alone. Real-time OpenGL (whew).

---

### Post by maksym on 2007-01-16
I have downloaded "C++ GUI Programming with Qt 3" and ""Thinking in C++". Guess that will keep my evenings busy for a while. Concerning the IDEs as I was afraid too many opinions :mrgreen:  So I will have to try them out one by one :)  

I was a bit confused with Gvim but this, I suppose, is a matter of habit. Strangly that some very simple "Hello world" examples which i got from tutorials turn out to run in IDEs which use g++ but produce errors when I just create cpp file in text editor and compile in command line gcc..

Anyway the math part of my problem is probably safe with Octave. Btw - is it possible to: 
1. c++:   develop apps with qt which can be later install on windows?
2. Octave:   use toolboxes developed for Matlab (like the econometrics one by LeSage) in Octave?
3. use functions developed in Octave in C++?

Thanks to all !

---

### Post by phossal on 2007-01-16
> **Wybiral said:**
> I can't program quickly in eclipse because my computer freaks out every time I open it (eclipse is quite the memory muncher)

I've seen a comment like this from you before. I had similar troubles with eclipse in Ubuntu, which is why I started installing the 32Bit packages of the current JDK and eclipse right from their respective sources. The performance rivals Windows on my box. If you were willing to take 10 minutes to try my [recommendation for installing the JDK and eclipse]("http://ubuntuforums.org/showthread.php?t=332674"), I would be surprised if you didn't find the performance was noticeably better. 

Like you said, though, to each his own.

[Edit] For .c and .cpp, I use gedit with the external tools plug-in, tabbed command line, etc. External tools lets you set up compiler instructions to be executed with a function key.

---

### Post by ZylGadis on 2007-01-16
> **lloyd mcclendon said:**
> for an IDE you definately want eclipse with the CDT plugin set.  eclipse is great, hands down the best IDE out no doubt.  [www.yoxos.com/ondemand](www.yoxos.com/ondemand)

a text editor and the command line is ok but once  you get more than 3 files in a project you start to be less productive.  and eclipse's debugger is pure sex.

I consider Eclipse to be far less than "best." Please refrain from imposing unfounded opinions upon others.
Learning a new language should happen in a simple text editor with the help of command-line tools. An IDE should only be used to help *experienced* programmers automate repetitive tasks, because they already know how to do those tasks themselves.

---

### Post by lloyd mcclendon on 2007-01-16
i disagree i've always used an ide but recently had a fling with the command line, and while it was kind of fun, it's more of a pain in the *** than an ide is. if you use workspaces well and get a rythm going it's cool, but the directory changing was too much for me (java packages)

eclipse runs fantastic on this laptop with a 1.7 ghz, gig of ram and 7200 rpm hd.  it's very zippy, starts in about 10 seconds.  it's not without the occasional crash though, definately not perfect software yet.

i'd draw the analogy that eclipse is to air tools and a lift as makefile is to a being on your back with a ratchet.

---

### Post by ZylGadis on 2007-01-17
You may disagree *and provide arguments for your reasons.* You may not talk as if you are the ultimate authority in programming.

Eclipse is bad because it uses SWT internally. SWT, unlike Swing, is a set of GUI libraries that tries to call the native GUI functions of the system it is running on. SWT, unlike Swing, is slow and buggy on GNU/Linux, because the people who develop it use Windows.
Netbeans, on the other hand, uses just plain Java, which means it uses Swing. With JDK6 out, Swing is a bit faster (not to mention stable) on GNU/Linux than Windows.
There are other IDEs that use Swing, too - I believe IDEA is one.

The moral of the story is: do not talk about things you do not understand.

The argument of IDEs in general versus the command line goes like this:
If the person wants to learn, he should start with the command line and gradually move to automating what he does with an IDE. If the person is fine with "I know nothing more than when I press this button, that happens," he should be fine with starting with an IDE, too. But then that person would not be a programmer in the end - he would be an IDE user.

---

### Post by Grey on 2007-01-17
Hey guys, lets all just be excellent to eachother okay?  Everyone has their own software preferences and choices.  We all do things a little differently from one another, and we have different priorities on our tastes.  Can't we just accept that, and move on?

I think in the interest of answers the original question, we should just present a few IDEs, and give the pros/cons of each.  I've only used Eclipse and Anjuta.

Eclipse: I never got it working satisfactorily.  Importing existing code into a project seemed tedious and akward.  Java is a slow resource hog.  When it IS working properly, it works fairly well.

Anjuta: Takes a bit of work to get set up, but once it's up and running, its fairly pleasant to use.  You can freely switch between the Anjuta IDE, and a text editor/terminal as you please.

kDevelop: I used it once or twice.  Seemed to be more or less a free version of Visual Studio.  Not my thing, don't know a lot about it.

Code::Blocks: I hear good things about this constantly, but I've never used it myself.

---

### Post by Wybiral on 2007-01-17
Personally, with C++ I think non-IDE compiling is better to learn with. It teaches you how to compile things properly... If you just use the build button in an IDE, you have no clue what the IDE is doing to build it... This is a bad thing. I think you really gain a lot from having to find your own errors too, you will have to learn to type out the entire command instead of waiting for an auto-complete...

But, I just think it's easier to learn C++ and know C++ than to learn an IDE and C++ at the same time... Then you become confused as to what C++ is. I see a lot of people who think Code::Blocks and DevC++ are compilers, simply because that's the only way they know how to compile.

If you need to work on large projects, use makefiles or compile scripts... Its very simple. I don't think most IDE's are even that helpful if you already know C++ and how to compile properly... I will take the trade-off of having to type "make" every now-and-then for the memory that isn't being tied up by an IDE.

---

### Post by Lord Illidan on 2007-01-17
> **ZylGadis said:**
> I consider Eclipse to be far less than "best." Please refrain from imposing unfounded opinions upon others.
Learning a new language should happen in a simple text editor with the help of command-line tools. An IDE should only be used to help *experienced* programmers automate repetitive tasks, because they already know how to do those tasks themselves.

That is your opinion. Everyone has a right to say his own opinion. I learned Turbo Pascal with the help of the TP IDE, without it I wouldn't have learned it.

---

### Post by maksym on 2007-01-17
> **Wybiral said:**
> Personally, with C++ I think non-IDE compiling is better to learn with. It teaches you how to compile things properly... If you just use the build button in an IDE, you have no clue what the IDE is doing to build it... This is a bad thing. I think you really gain a lot from having to find your own errors too, you will have to learn to type out the entire command instead of waiting for an auto-complete...

But, I just think it's easier to learn C++ and know C++ than to learn an IDE and C++ at the same time... Then you become confused as to what C++ is. I see a lot of people who think Code::Blocks and DevC++ are compilers, simply because that's the only way they know how to compile.

If you need to work on large projects, use makefiles or compile scripts... Its very simple. I don't think most IDE's are even that helpful if you already know C++ and how to compile properly... I will take the trade-off of having to type "make" every now-and-then for the memory that isn't being tied up by an IDE.

I would probaby agree with that. Since I have very limited idea about c/c++ I  was overwhelmed with what to do and where to start when I open a nice and shiny IDE... That was actually why I asked for help. It appears that as long as I learn (contrary to work) I would be better off with simple things.

However, in my experience in VBA and Matlab IDEs (and some plug-ins to those), once you know the language, were very helpful in debuggin code fast and great time savers. So I guess - start with console and look for IDE later when really necessary?

---

### Post by lloyd mcclendon on 2007-01-18
> **ZylGadis said:**
> You may disagree *and provide arguments for your reasons.* You may not talk as if you are the ultimate authority in programming.

The moral of the story is: do not talk about things you do not understand.

i will do whatever i please.  swt is just fine with me, no need to understand it. i guess i must have a bad *** computer.  but at least i do understand that the astetics of an IDE do not get me a bigger paycheck.   i try not to worry about what OS the devs for the IDEs toolkit use and focus on delivering quality software quickly.  eclipse definately helps at that tremendously and that's why i'm such a zealot.  the more i use it, the more it makes sense.  it's like a crack pipe.

i have evaluated netbeans 4 times now and each time it wasn't my cup of tea - that doesn't mean it's bad.  i haven't looked at idea yet, but i've read mixed reviews.  some say it fits like a glove, i'd say the same for eclipse.  it's all a matter of preference.

OP - you owe it to yourself to read a few eclipse tutorials.  spend a good hour or two getting it setup correctly, and another hour or two learning how to leverage it to make your life easier.  

as far as the "start with a command line" argument, it's the same thing as doing long division by hand vs. using a calculator.  is it nice to know? sure.  is it necessary?  absolutely not.  once you get more than a certain number of digits (artifacts), it becomes necessary to use a modern tool to solve the problem instead of wasting time with an obselete approach.


and those of you still hanging around in 1978 using Makefiles need to look at ANT.   ant is the best, remember i am the ultimate authority on this stuff.

---

### Post by Wybiral on 2007-01-18
I am in no way saying that IDEs are bad... It's just my personal experience and opinion that I, being myself, learn a language much faster when I have to think about the keywords and syntax while I am learning... I personally feel that learning from an IDE distracts you from this because it offers too much assistance.

With that said... IDEs can be useful for certain things like making sure you close your quotes and brackets and such... But Gedit does that too, and I do feel that it is more important to understand your compiler than an IDE wrapped around your compiler. So makefiles and command line compiling is more of a "getting to know your compiler" thing than a comfort thing.

But, as it's already been said, to each his own... I don't like IDEs, they're distracting to me and too CPU intensive (especially since I need to test my programs at the same time, and I do a lot of 3d and math related stuff, so the memory is more valuable), but it's understandable why others use them.

I don't mean to downplay anyone... IDE/text editor... It all accomplishes the same thing, which is code... Thats what's important. So use what is easy for you to learn with and suites your needs.

---

### Post by amo-ej1 on 2007-01-18
i kinda agree with Wybiral on somethings, in the end you'll gain much more understanding from API's, your application in general and the language you're using when _not_ using an IDE. 
A stupid example, eclipse has the feature to automatically add 'import' when using certain classes, but in the end when you only use eclipses feature you won't know where that certain class is located, you only know that it's "out there". 
Nevertheless the greatest value an IDE has to offer is integrated documentation. I would do anything for a C++ IDE which magically parses my doxygen comments and makes them tooltip wise accesible and has the same support for all STL wizardy but until that emacs it will be ;)

---

### Post by ZylGadis on 2007-01-18
> **lloyd mcclendon said:**
> swt is just fine with me, no need to understand it.

Power to the masses.

> **lloyd mcclendon said:**
> but at least i do understand that the astetics of an IDE do not get me a bigger paycheck.

And their priorities.

---

### Post by lloyd mcclendon on 2007-01-18
at least i can support my argument

so far all you have brought to the conversation is "eclipse sucks because the swt devs use windows."

you may not post again in this thread.

---

### Post by maksym on 2007-01-23
Moving slovly now in c++ :rolleyes: 
Is it possible to convert my octave code in c++ source code and complie ? I know that matlab offerce such a compiler but it is commercial. Any free ones? 

Thanks!

---

