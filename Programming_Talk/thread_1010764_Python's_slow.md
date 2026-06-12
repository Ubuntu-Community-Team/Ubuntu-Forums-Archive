---
title: "Python's slow"
date: 2008-12-14
forum: Programming Talk
---

### Post by 7raTEYdCql on 2008-12-14
I have heard that python is one of the slowest languages out there. Is that true. Then why is it that in ubuntuforums and everywhere there is always a propogation of this language as the easiest, most useful ...

---

### Post by CptPicard on 2008-12-14
... could it possibly be because speed isn't everything?

---

### Post by Bichromat on 2008-12-14
i.mehrzad: So, what you are saying is that a language cannot be easy/useful if it is slow? :confused:

---

### Post by roelpeeters on 2008-12-14
In my opinion it all depends on what you have to do. In the case of scientific algorithms or certain types of applications Python might be slower than C++, but it still depends on the implementation. The only way to make a statement on this is to take an example case, write an implementation in Python and C++ (or any other language of reference) and measure the performance of each implementation. Then for that particular case you can say whether Python is slower or faster than C++. 

Another example is GUIs. Writing user interface applications on Linux might be much easier using Python than for instance C++. In the case of user interfaces, performance is usually not a big issue, since the computer most of the time is waiting for you - the user. But the speed-up in development can be a lot!

The main reason it is propagated on the ubuntu-forums is that it is an easy language to learn and you can get quick results.

---

### Post by mentallaxative on 2008-12-14
Python is easy to use and learn and most of the time the speed will not be important to you anyway.

---

### Post by 7raTEYdCql on 2008-12-14
I will stand on every one's side as far as ease of use is concerned. Honestly i studied "C" and am bored with it. Took up Python and am waiting to get bored. 

And anyway "Who cares about speed." Atlest I don't. But still, was Just asking.


[Hope i didn't hurt any feelings.]

---

### Post by wmcbrine on 2008-12-14
My first computer ran a BASIC interpreter, and it was fast enough for most purposes. Although slow enough that it made me learn assembly... But the computer I'm using now is literally thousands of times as fast as that one. So Python now is probably faster than assembly was then.

There is still a place for C, and even for assembly, but the domain where you *need* them is shrinking.

---

### Post by nvteighen on 2008-12-14
My question: who of us is doing such time-critical stuff that Python's slowness (just some tenths of a second) may be relevant?

As ol' pmasiar *will* say, the most serious bottlenecks are related to I/O operations which are not language-related.

---

### Post by jimi_hendrix on 2008-12-14
lets all use binary because its fastest ;)

---

### Post by jimi_hendrix on 2008-12-14
> **wmcbrine said:**
> There is still a place for C, and even for assembly, but the domain where you *need* them is shrinking.

well proffesional games running on a console with realistic graphics probably would need C/C++...but i doubt any of use are writing those games...

---

### Post by nvteighen on 2008-12-14
> **jimi_hendrix said:**
> well proffesional games running on a console with realistic graphics probably would need C/C++...but i doubt any of use are writing those games...
Nope, we're coding Tic-Tac-Toe and a strange Scheme experiment... ;)

---

### Post by pmasiar on 2008-12-14
> **i.mehrzad said:**
> I have heard that python is one of the slowest languages out there. Is that true. 

It's complete lie: Python is one of tha fastes language to give you a solution.

Just yesterday, I was deleting some lines in a big log file. I realized that it's boring, wrote a simple program to parse file and ignore some, and it run at first try. I was done in less than 5 minutes. Using any of so called "fast" languages like C, it would take me much longer.

The most important speed is **speed to the market** or to get the working solution.

OP: take note who gives you such misleading advice ("Python is worthless because is slow") and make sure ignore advice from those people, they have no clue and just repeat soundbites they overheard somewhere.

---

### Post by mssever on 2008-12-14
> **i.mehrzad said:**
> I have heard that python is one of the slowest languages out there. Is that true.
Ruby 1.8 is a lot slower than Python. Even still, I like Ruby a lot. If Ruby had the library support Python does, I'd likely ignore Python. (I end up writing more and more Python, however, because Python has so much better libraries.)

---

### Post by pp. on 2008-12-14
> **pmasiar said:**
> It's complete lie (...)  The most important speed is **speed to the market** or to get the working solution.

These are half-truths and quite a bit misleading.

It is quite true that for many kinds of applications the speed of execution will be noticeably slower for programs written in Python than for programs written in other languages.

Whether the loss of speed matters or not can be only decided in the context of the application. Chances are that for the OP as beginning programmer the advantages of the language will outweigh the lack of execution speed.

There are projects where the time to market is of overriding importance while in other project that time is of subordinate importance. Again, for a beginning programmer the time to completion might be more important than the speed of execution.

This does not, hovewer, imply that speed of execution is unimportant for all kinds of problems or that time to completion is more important than execution speed in every circumstance.

It has become a bit of a fashion (the last 30 years or so) to deride a bit people who favor speed of execution. At the same time, many bemoan sluggishly performing GUIs and glacial web servers which are to an impressive degree due to languages which are faster to market but slower to run.

Lastly, most performance problems are probably not due to slowly running languages but due to ineptly selected or implemented algorithms.

---

### Post by curvedinfinity on 2008-12-14
A quick way of making any python app faster:

In a terminal:
```

sudo apt-get install python-psyco

```

Then after all of the import statements in your code (being after all of the imports is important):
```

import psyco
psyco.full()

```

Psyco is a JIT(Just In Time) compiler. It will compile parts of your app into platform-specific language. Its similar to what newer versions of java run. Results vary drastically, but in most cases, it will speed Python up to almost as fast as Java -- that ends up being around 1.5x to 8x faster. Its not like its hard to use, so I always use it. :)

---

### Post by curvedinfinity on 2008-12-14
Also, being a long time C++ user, Python is better from a programming standpoint. I'd say the biggest advantages come in a larger project, however. Down the line, all code eventually gets messy. Python is easier to read than C, and has some features with great syntax. Those facts make things cleaner, which makes it easier to maintain old code.

However, saying its faster is silly. C is on average 10-100x faster. Period. End of story.

If speed isn't so important -- which is more often than most people think -- Python is better.

---

### Post by OutOfReach on 2008-12-14
I agree with most of your guys's posts. Just yesterday I coded a simple Python program to help with some simple file operations (changing the WM/DE in $HOME/.xinitrc), it was easy. It took me maybe 10 minutes to complete everything (including arguement parsing, and some other small features) and it took maybe some 30 minutes to make the GUI (for fun, i don't really intend on using the GUI).
If I were to do this in C (the language of which I have learned the basics of) it would have made this simple task such a pain. Even though C would be faster, I like ease of development especially for those simple tasks.

---

### Post by wmcbrine on 2008-12-14
Unfortunately psyco only works on i386 (x86-32).

---

### Post by samjh on 2008-12-14
> **i.mehrzad said:**
> I have heard that python is one of the slowest languages out there. Is that true.In terms of execution speed, yes it is true.

> **i.mehrzad said:**
> Then why is it that in ubuntuforums and everywhere there is always a propogation of this language as the easiest, most useful ...Only on Ubuntuforums and some other places.  I frequent quite a lot of programming forums, and very rarely see as much glowing praise about Python as here.

Python IS easy to learn.

Python IS useful for programs where execution speed or memory usage is not important.

Python IS NOT useful for everything, or even a lot of things.


As for the comment about speed to market being most important, that is not even a generally-applicable statement.  Speed to market will mean jack all if the client is LOSING man hours because of a slow app.  Oh yes, I've seen it happen.  My former employer ditched a vendor because their application was causing a bottleneck (our network and data server were both found to be more than fast enough) in our administration work flow - nearly half the time spent on entering a record was spent waiting for the application to respond!

You need balance.

---

### Post by jimi_hendrix on 2008-12-14
i love C++ for somethings and python for others...

C++ for games and python for interfacing with other things (files, IRC, etc)

but basically unless your calculating the googleth iteration of pi i dont think you need C speed

---

### Post by jimi_hendrix on 2008-12-14
> **wmcbrine said:**
> Unfortunately psyco only works on i386 (x86-32).

what happens on x86_64?

---

### Post by pp. on 2008-12-15
> **jimi_hendrix said:**
> i love C++ for somethings and python for others...

C++ for games and python for interfacing with other things (files, IRC, etc)

but basically unless your calculating the googleth iteration of pi i dont think you need C speed

I take it, then, that Open Office and the GIMP are written in Python?:p

---

### Post by Greyed on 2008-12-15
> **pp. said:**
> I take it, then, that Open Office and the GIMP are written in Python?:p

OOo is written in, I believe, Java and GIMP is C?  GTK is C, QT is C++ if memory serves.  However both implement Python as a scripting language.

More telling, however, is that [EVE-Online is written in Python]("http://www.eve-online.com/faq/faq_07.asp").

The position of the Python community has always been that it is better to prototype or primarily code in Python, identify bottlenecks and *if needed* drop down to C to speed up those portions.  This approach gives you the rapid development of Python with the speed of C in the areas where it is really needed.

---

### Post by CptPicard on 2008-12-15
> **Greyed said:**
> OOo is written in, I believe, Java

C++. There are some bits and pieces of Java somewhere, IIRC in the database connection code if memory serves.

---

### Post by Greyed on 2008-12-15
Well, it feels like Java sometimes.  :-\"

---

### Post by SeanHodges on 2008-12-15
> **Greyed said:**
> More telling, however, is that [EVE-Online is written in Python]("http://www.eve-online.com/faq/faq_07.asp").

If I had a penny for every time EVE-Online was used as a poster child for Python...

---

### Post by Greyed on 2008-12-15
You still wouldn't be able to have enough money to hire people to invalidate the fact that it refutes the notion C++ is the only language in which to program games, amen?  

But you're right.  If only someone else would develop a game in Python *cough*[FretsonFire]("http://fretsonfire.sourceforge.net/")*cough* or used Python extensively *cough*[Vampires: Bloodlines]("http://www.gamespot.com/pc/rpg/vtmb/index.html")*cough*hack*[Tabula Rasa]("http://www.playtr.com/index.html")*wheeze* we could let EVE Online off the hook a tad, right?  :D

---

### Post by ufis on 2008-12-15
> **i.mehrzad said:**
> I have heard that python is one of the slowest languages out there. Is that true. Then why is it that in ubuntuforums and everywhere there is always a propogation of this language as the easiest, most useful ...

I do not know Python, but I have had this type of discussion many times before, only for other languages.

When looking at speed you have to look at two things: Speed of development vs Speed of execution.
(Generalisation)c++ will run faster than Python in most cases. But Python will develop faster than c++. (Going by all the posts of how easy a language it is to pick up and use)

So lets say you want to write a simple calculator application. And lets assume that Python takes you 1 hour to develop said application. c++ takes you 2 hours. Now c++ calculates your sums 1/10th of a second faster. 

That means that you will have to make 36000 calculations on your calculator before you are losing time. Meaning you can almost do 100 calculations a day for a whole year before you have lost the 1 hour you gained by using Python instead of c++

This is just a (very) simple (and generalised) example to illustrate the basics of speed and programming.

---

### Post by Wybiral on 2008-12-15
> **SeanHodges said:**
> If I had a penny for every time EVE-Online was used as a poster child for Python...

Well, it's a good poster child because it counters several common misconceptions people have about Python. For instance, people think CPython IS Python, but really Python is a language, and CPython is just the most popular implementation (there's cpython/jython/ironpython/stackless python...)

But, as far as performance in Python goes... If you've got some code where you're profiled it, exhausted all chance of clean algorithmic optimization, and the thing still wont perform fast enough... Just write that tiny chunk in a compiled language and import it into Python. Writing a module in C is just as easy as compiling a DLL (any shared library can be FFI-loaded with the ctypes module and painlessly wrapped in Python objects for convenience). You can also take the PyRex and cython approach that find a sort of middle grounds between C and Python to make writing fast modules easier. And this, of course, is still just CPython, IronPython can leverage .NET libraries, Jython can leverage Java libraries...

---

### Post by Tuna-Fish on 2008-12-15
> **Greyed said:**
> You still wouldn't be able to have enough money to hire people to invalidate the fact that it refutes the notion C++ is the only language in which to program games, amen?  

But you're right.  If only someone else would develop a game in Python *cough*[FretsonFire]("http://fretsonfire.sourceforge.net/")*cough* or used Python extensively *cough*[Vampires: Bloodlines]("http://www.gamespot.com/pc/rpg/vtmb/index.html")*cough*hack*[Tabula Rasa]("http://www.playtr.com/index.html")*wheeze* we could let EVE Online off the hook a tad, right?  :D

Also, Civilization 4 and Oblivion (likely Fallout 3 too).

Those are just the ones I've noticed.

---

### Post by nvteighen on 2008-12-15
> **samjh said:**
> 
As for the comment about speed to market being most important, that is not even a generally-applicable statement.  Speed to market will mean jack all if the client is LOSING man hours because of a slow app.  Oh yes, I've seen it happen.  My former employer ditched a vendor because their application was causing a bottleneck (our network and data server were both found to be more than fast enough) in our administration work flow - nearly half the time spent on entering a record was spent waiting for the application to respond!

You need balance.

Of course: your last phrase summarizes it all. The best tool for the right task...

What I don't get why some think that praising Python immediately means to ditch C and C++? I guess the reasons why Python is that present at these forums are many (Ubuntu using lot of Python, that lots of beginners visit these forums...).

---

### Post by jimi_hendrix on 2008-12-15
does anyone else feel like people either love or hate python

---

### Post by pp. on 2008-12-15
> **jimi_hendrix said:**
> does anyone else feel like people either love or hate python

I don't.

---

### Post by jimi_hendrix on 2008-12-15
@people listing games

wikipedia does not mention any of those

[here]("http://en.wikipedia.org/wiki/Python_software#Video_games")

---

### Post by wmcbrine on 2008-12-15
> **jimi_hendrix said:**
> what happens [with psyco] on x86_64?Nothing. It's not available.

---

### Post by jimi_hendrix on 2008-12-15
> **wmcbrine said:**
> Nothing. It's not available.

i mean does an error happen or does it do nothing

---

### Post by Smygis on 2008-12-15
> **Tuna-Fish said:**
> Also, Civilization 4 and Oblivion (likely Fallout 3 too).

Those are just the ones I've noticed.

There is some python in Battlefield 2 also. Dont remember exactly what it does tho. And i belive World in conflict makes extensive use of python.

---

### Post by estyles on 2008-12-15
> **ufis said:**
> So lets say you want to write a simple calculator application. And lets assume that Python takes you 1 hour to develop said application. c++ takes you 2 hours. Now c++ calculates your sums 1/10th of a second faster. 

That means that you will have to make 36000 calculations on your calculator before you are losing time. Meaning you can almost do 100 calculations a day for a whole year before you have lost the 1 hour you gained by using Python instead of c++

This is just a (very) simple (and generalised) example to illustrate the basics of speed and programming.

Thanks for the huge oversimplification.  

(rant mode on) This isn't entirely directed at you, but...  I'm kinda sick of programmers who code sloppily because "speed doesn't matter" or because processor cycles are cheap, or whatever other reason.  Usually, it's more of an issue with bad algorithms, poor garbage cleanup (heck, everyone has 1GB of RAM, so if my crappy little text-viewer program uses up 100MB of it, no big deal, right?), and such than a question of which programming language they use.  Ever play a lot of flash games in Linux?  Yeah, flash is implemented poorly for Linux, but on top of that, most coders of little flash games don't care to optimize for performance so that tiny little shoot-em-up uses as much processor time as the latest 3D FPS's - it's crazy.  And the solution is "get a better CPU or video card".  That's like Atari games telling you that you need a bigger TV.

But in addition to poor coding, using an interpreted language when a compiled language would be faster makes using your program a hassle.  If you're writing it mostly for yourself, and "hey maybe someone else could use this", then it's no big deal.  Write it however you want, and if people think your program is too slow, then they can compile it for themselves.  But if your goal is to get users and you're doing text matching or database queries or file-searching, then that extra 1/10th of a second per operation is huge.  It can mean the difference between a query taking 10 seconds and 10 minutes, easy.

---

### Post by jimi_hendrix on 2008-12-15
> **estyles said:**
> Thanks for the huge oversimplification.  

(rant mode on) This isn't entirely directed at you, but...  I'm kinda sick of programmers who code sloppily because "speed doesn't matter" or because processor cycles are cheap, or whatever other reason.  Usually, it's more of an issue with bad algorithms, poor garbage cleanup (heck, everyone has 1GB of RAM, so if my crappy little text-viewer program uses up 100MB of it, no big deal, right?), and such than a question of which programming language they use.  Ever play a lot of flash games in Linux?  Yeah, flash is implemented poorly for Linux, but on top of that, most coders of little flash games don't care to optimize for performance so that tiny little shoot-em-up uses as much processor time as the latest 3D FPS's - it's crazy.  And the solution is "get a better CPU or video card".  That's like Atari games telling you that you need a bigger TV.

But in addition to poor coding, using an interpreted language when a compiled language would be faster makes using your program a hassle.  If you're writing it mostly for yourself, and "hey maybe someone else could use this", then it's no big deal.  Write it however you want, and if people think your program is too slow, then they can compile it for themselves.  But if your goal is to get users and you're doing text matching or database queries or file-searching, then that extra 1/10th of a second per operation is huge.  It can mean the difference between a query taking 10 seconds and 10 minutes, easy.

+1

i have a problem every 2 or 3 years where i have to stop buying computer games because my computer cant take them...

paritially its because of technology, but i think code contributes too...

memeory used to be expensive, so people used it wisely...

now when you can get a decked out computer for relatively little money...

its such a pain...

---

### Post by samjh on 2008-12-15
> **nvteighen said:**
> What I don't get why some think that praising Python immediately means to ditch C and C++?That's because many Python promoters over-push Python.  It's irritating, like how high-pressure sales people are irritating.

It's not just Python.  It's C and C++ as well.  Same for Java.  People tend to over-push whatever language takes their fancy, and it gives a false impression that the language being promoted is the ONLY language you should ever use (even if the promoter includes qualifying statements, like "you should choose the right tool for the right job").

If anyone wants to give advice on the choice of programming languages, that person needs to be a consultant, not a sales person.

---

### Post by pmasiar on 2008-12-15
> **estyles said:**
> that extra 1/10th of a second per operation is huge.  It can mean the difference between a query taking 10 seconds and 10 minutes, easy.

You obviously have little experience or understanding how I/O **really** works. Both Python and C call **exactly** the same library (written in C) and that 0.1 sec is just that: 0.1 sec. Can you explain how it gets conveted to 10 minutes? Did you ever wrote a SQL statement which runs for more than 10 minutes on your databse?

---

### Post by slavik on 2008-12-15
I know of cases where a long running SQL caused a site outage and stuck threads in the JVMs ;) (cyber monday, one of the clients I support).

---

### Post by jimi_hendrix on 2008-12-15
cyber monday?

---

### Post by Greyed on 2008-12-16
> **jimi_hendrix said:**
> @people listing games

wikipedia does not mention any of those

[here]("http://en.wikipedia.org/wiki/Python_software#Video_games")

Wikipedia also shun just listing out every instance where something is mentioned or used.  They prefer such details either be worked into the main article or left out.  [Here]("http://en.wikipedia.org/wiki/Wikipedia:Trivia_sections") is the relevant policy.  So Wikipedia not listing something does not mean it is not present.

I would link to a screen shot I had of a listing of Tabula Rasa's directory but I believe I deleted it a day or two ago and, frankly, I'm in no mood to dig up my CDs and reinstall.  Needless to say I know TR uses Python because the Python DLL was in the game's directory structure.

Vampire: Bloodlines was even better.  Their NPC AI was coded in Python and the files were shipped as py files instead of pyc files.  So an enterprising modder could modify the behavior of the enemies if they were so inclined.  Again, not installed currently and I think the original media is long gone (at least 2 moves since I had it installed).

> **samjh said:**
> That's because many Python promoters over-push Python. It's irritating, like how high-pressure sales people are irritating.

I don't believe I am over-pushing Python.  I don't go into topics not marked for Python to talk about it.  With two exceptions.  Those being topics marked as "script" since it could mean Python and those asking "what would be a good language".  IE, pretty much every topic I mention Python I am doing so at someone's invitation.  Furthermore when the "script" marked topics don't mean Python in almost all cases I stay out unless it looks like the person is struggling with the foibles of shell which don't exist in Python.  I then offer the alternative and head on out.

You'll find that most cases where I could be charitably called as "pushing" Python is when people post something negative about Python that is inaccurate.  The "C++ for gaming" fallacy being the chief example.  The fact that it has been done and that other languages in the similar class as Python have been used to make games, and not trivial games, means that statement is false, plain and simple.  So if correcting bad information is "pushing" the language, guilty as charged.

Finally, I haven't see people who have said that Python is the only choice.  If they did I would correct them, as well.  While I am a fan of Python I do know its limitations and appropriateness.  I have never hidden the fact that sometimes when you're coding in Python you will need to drop down to C to get speed.  In fact I explicitly mention that time and again.  This is different than the people who push the point that a person should program everything in C (or C++, or what have you) and exclude Python solely based on the dubious notion of speed-at-all-costs.

> If anyone wants to give advice on the choice of programming languages, that person needs to be a consultant, not a sales person.

Exactly.  However I think you have them backwards.  A sales person is the one that will shift his responses to sell you something.  He'll push the best product for his interests and, barring you being aminable to that, go with what you say to get some sale.  A consultant, at least one worth paying, will tell you when your solution is wrong and present the correct view in spite of your objections.  

Or, to put it another way, if you were coding something and for some reason wanted the entire project in Brainfuck he might try to push his solution but in the end, if you were adament, would agree with you just to make the sale.  The consultant would just tell you you're wrong and offer viable alternatives.

---

### Post by jimi_hendrix on 2008-12-16
> **Greyed said:**
> The "C++ for gaming" fallacy being the chief example.  The fact that it has been done and that other languages in the similar class as Python have been used to make games, and not trivial games, means that statement is false, plain and simple.

this comes from the fact that if you make real, proffesional games, you will, for the most part, touch C or C++ somewhere...even if its in the engine that you write your script for...

---

### Post by iQuizzle on 2008-12-16
it is ill-informed to claim that python is slow. here's why:

1. if you use python packages properly, you get huge speed increases. why? because the modules have been compiled and run from C libraries. matrix/array operations are very fast under the numpy package.

2. it is much faster to develop and maintain in python because the syntax is easy and neat even for a high level language. furthermore, there's no need to compile before testing your code. additionally python has an interactive shell where you can test out things if you aren't sure they'll work...if things are documented well, you can print the doc strings directly to your screen and figure out how to use the functions.

3. python was written to interact easily with C/C++. if you have a huge iterative loop that takes lots of time in python, write a few lines of code in C and #include the "Python.h" package. a few extra lines of C code and you can now import your function directly into python. all the power of C and C++ when you need it without having to make a mess of your code.

it's that easy. the combination of python and C/C++ extensions can solve just about any 'speed' problems you'll ever encounter. if you think python is hyped, there's a reason for it. people who use it love it. :)

---

### Post by Greyed on 2008-12-16
> **jimi_hendrix said:**
> this comes from the fact that if you make real, proffesional games, you will, for the most part, touch C or C++ somewhere...even if its in the engine that you write your script for...

Which was never claimed not to be the case.  But note that most times C/C++ is mentioned it is to the *exclusion* of Python.  IE people have said that you might as well not touch Python and just to everything in C++ because you'll have to touch it.  The Pythonistas, at least this one, have never excluded C/C++ from the process.  The frankly state that for those portions where Python may be too slow it is best to code in C at that time.

EDIT:
This gets back to why EVE-Online is held up as the poster of a Game written in Python.  It is written in Stackless Python.  There is no doubt they are dropping to C for things like the graphic engine.  But they state boldly that the client and server are written primarily in Stackless Python.  This is exactly the paradigm that many Python proponents are pointing out as viable that other people are ignoring in the C++ and nothing argument.  The telling point of EVE-Online is that, as pmasiar stated, often times it is the database access which is the bottleneck.  EVE-Online handles more simultanious connections than any other MMO, ever.  CCP has stated that whenever they gain speed increases in terms of overall lag it is in the area of database access, not overcoming slowness in Python.

---

### Post by pp. on 2008-12-16
> **pmasiar said:**
> You obviously have little experience or understanding how I/O **really** works. Both Python and C call **exactly** the same library (written in C) and that 0.1 sec is just that: 0.1 sec. Can you explain how it gets conveted to 10 minutes? Did you ever wrote a SQL statement which runs for more than 10 minutes on your databse?

The post you're referring to says that there are settings where the python program runs slower ***by a factor of 60*** than an equivalent program written in other languages. No need to get your feathers ruffled.

> **iQuizzle said:**
> it is ill-informed to claim that python is slow. here's why:

... if you have a huge iterative loop that takes lots of time in python, write a few lines of code in C and #include the "Python.h" package. a few extra lines of C code and you can now import your function directly into python. all the power of C and C++ when you need it without having to make a mess of your code.

If the claim that python is slow is false, there can be no "huge iterative loop that takes lots of time in python". There are program parts written in python involving a great number of iterations which take much longer than equivalent code written in other languages. Therefore "the claim that python is slow is false" is false.

What you're saying is that in some circumstances the marked lack of speed of python programs can be circumvented by implementing parts of the program in languages other than python. 

That has been said several times over. It does not make python any faster. It reduces the problem of python being slow in some cases.

---

### Post by Greyed on 2008-12-16
> **pp. said:**
> The post you're referring to says that there are settings where the python program runs slower ***by a factor of 60*** than an equivalent program written in other languages. No need to get your feathers ruffled.

Yes, because unsubstantiated, wildly inaccurate negative claims never ruffled any feathers.

---

### Post by iQuizzle on 2008-12-16
well if that's the case then you have to claim C is slow..because python is written in C. all i'm driving at is that python is made to work with C and _every function called from python_ is actually C code in some form. ever notice the ".pyc" files that get created when you run a python program?? you aren't circumventing anything by compiling a C function and using it in python. that **is** how the language inherently works and in fact most "python" modules are compiled from C for use inside the python environment.

by creating a python extension in C you are using the language the way it already gets used...you just never notice it because you don't have to do any actual C coding. extensions aren't "work arounds" just because they are more advanced methods of using python.

---

### Post by Greyed on 2008-12-16
Erm, IQuizzle, pyc has nothing to do with C code.  Really.

---

### Post by Tuna-Fish on 2008-12-16
> **jimi_hendrix said:**
> @people listing games

wikipedia does not mention any of those


And?

You can bring up a python REPL in Oblivion, and anyone who has ever modded civ 4 instantly realizes it's python.


> **estyles said:**
> I'm kinda sick of programmers who code sloppily because "speed doesn't matter" or because processor cycles are cheap, or whatever other reason. 


> **jimi_hendrix said:**
> 
paritially its because of technology, but i think code contributes too...

memeory used to be expensive, so people used it wisely...


People do not code sloppily just because they are lazy - coding so that you count every bit takes so much more time than "sloppy coding" that it's not even funny. It can be the difference of a project costing a M€ to complete and a project that would cost 10-20 M€ to complete, that is if it ever would be started.

Sloppy coding made the software you are using feasible to implement.

---

### Post by iQuizzle on 2008-12-16
> **Greyed said:**
> Erm, IQuizzle, pyc has nothing to do with C code.  Really.

yeah, you're technically right. it's really the CPython byte-compilation...so you wouldn't actually be able to read anything from it.



it really boils down to semantics to say python is slow because it's inseparable from C. i'm just trying to offer real-world solutions instead of engaging in petty arguments because in my experience it's easy to adapt python to most any situation(with the special case exception of coding that is heavily dense with nested loops, i.e. scientific numerical computation).

i've written tens of thousands of lines of "pure python" code with merely 200 lines of python extension/C code to run a scanning tunneling microscope with microsecond precision. yes, you have to know some C in order to do anything and everything with python at blazing speeds but you can't hardly consider that a deficiency of the language since it's practically built in (as an alternative you can actually import C libraries _directly_ with **zero** C code using the python-ctypes module and attain similar speeds). and, in fact the ctypes module ships in the python standard package. (pp., i would moew consider ctypes a work-around, but it does work quite effectively).

---

### Post by pp. on 2008-12-16
Just to make sure:

Programs written in pure Python can be orders of magnitude slower than programs written in languages which are closer to the hardware architecture. This has nothing whatsoever to do with the algorithms employed but is an immediate consequence of the nature of Python.

In some (but by no means very many) instances this lack of speed makes the programs not useful enough.

Where the lack of speed becomes an issue, there are several strategies available to boost the performance of the offending program. You can replace all or parts of the program by parts written in other languages. You can employ compilers which make the program run more efficiently. There are more strategies which I don't think are useful to name here.

Stating that a Python program executes the same kinds of instructions than any other program is not very helpful in that context, since the number of instructions executed is at issue, not any kind of quality of those instructions.

---

### Post by nvteighen on 2008-12-16
Get the Facts... :D

0. Any interpreted language will be slower than a native-compiled langauge because of the interpreter that sits in the middle.
1. It will be faster to develop in any high-level language than any low-level language because you need less lines and less abstraction-steps to achieve the same.

Ok, the question is... how much applications are actually that time-critical that writing them on C and C++ will be the only way to achieve a human-appreciable speed increase? Honestly, I guess there are and 3D games are the examples most usually given. But, if I were in such a situation, I'd resort to use C or C++ as the last speed-optimization alternative... and if locally restricted to the time-critical part. So you get the best of both worlds, specially when you're using a language like Python that allows to do that interfacing.

---

### Post by SeanHodges on 2008-12-16
> **Greyed said:**
> You still wouldn't be able to have enough money to hire people to invalidate the fact that it refutes the notion C++ is the only language in which to program games, amen?  

But you're right.  If only someone else would develop a game in Python *cough*[FretsonFire]("http://fretsonfire.sourceforge.net/")*cough* or used Python extensively *cough*[Vampires: Bloodlines]("http://www.gamespot.com/pc/rpg/vtmb/index.html")*cough*hack*[Tabula Rasa]("http://www.playtr.com/index.html")*wheeze* we could let EVE Online off the hook a tad, right?  :D

Wow, you got all that from my post?! :)

Python is one of my favourite languages to use (as are C++ and Java). My point was that every time someone challenges Python's performance (which is often indisputable), the knee-jerk response is ALWAYS "Yeah, but EVE Online uses Python!". 

It uses Stackless Python for it's game logic. Many other games use Python too, but neither of these facts indicate that Python is as fast or faster than some other languages. It is relatively slow, but whilst speed is not it's strength; it has many other strengths that make it a powerful tool in development.

---

### Post by CptPicard on 2008-12-16
> **iQuizzle said:**
> 
it really boils down to semantics to say python is slow because it's inseparable from C.

I don't get it... Python is just a language, you can implement it on top of a lot of stuff, for example the Java VM (Jython) or the CLR...

If you mean that in the end the CPU is running machine code instructions, then you're right. But C, too, is just a language...

---

### Post by Greyed on 2008-12-16
> **SeanHodges said:**
> Python is one of my favourite languages to use (as are C++ and Java). My point was that every time someone challenges Python's performance (which is often indisputable), the knee-jerk response is ALWAYS "Yeah, but EVE Online uses Python!". 

However if you read carefully that isn't what I did.  Someone generally excludes Python from game development because of its speed saying it is *impossible* for Python to be fast enough to code games in.  The fact it *has already been done* makes that point moot.  So any time someone excludes Python from that arena based on it is speed it is entirely appropriate to remind those people they are wrong.  Plain as that.  If they didn't exclude Python because of their outdated bias then there would be no need for those who know better to point out the folly of their words.

---

### Post by SeanHodges on 2008-12-16
> **Greyed said:**
> Someone generally excludes Python from game development because of its speed saying it is *impossible* for Python to be fast enough to code games in.  The fact it *has already been done* makes that point moot.

That is an oxymoron. People don't "generally" exclude Python when developing games, you've already provided a list of games to prove that.

> **Greyed said:**
> So any time someone excludes Python from that arena based on it is speed it is entirely appropriate to remind those people they are wrong.  Plain as that.  If they didn't exclude Python because of their outdated bias then there would be no need for those who know better to point out the folly of their words.

No'one had mentioned games at that point, you started that. The OP was referring to the general performance of Python, not it's applicability to gaming, and pp's post that you quoted mentioned the Gimp and OOo, but made no reference to game development.

I see the point you're trying to make, but I don't think it applies. Also, my original comment that Eve Online is often treated as a poster child for Python stands correct for the same reason.

---

### Post by pmasiar on 2008-12-16
> **samjh said:**
> That's because many Python promoters over-push Python.  It's irritating, like how high-pressure sales people are irritating.

It's not just Python.  It's C and C++ as well.  Same for Java.  People tend to over-push whatever language takes their fancy,

I have rather strong opinion that beginners are much better served by Python than by C, Java or C++. I do not promote Python for everything - but Python **is** IMNSHO best solution for most problems beginners post in this forum.

And I feel i need to push back because so many posts by people with obviously little experience (not you!) who just repeat misinformation they picked from they equally misinformed peers, spreading the fallacies around.

Most beginners are not aware that opinions are not counted but evaluated, so for every misinformation there has to be 2 posts pushing back, to make impression on those young minds ;-)

Possibly because when they are not beginners, they stop asking those trivial questions :twisted:

---

### Post by Greyed on 2008-12-16
> **SeanHodges said:**
> That is an oxymoron. People don't "generally" exclude Python when developing games, you've already provided a list of games to prove that.

I meant on the boards.


> No'one had mentioned games at that point, you started that.


.... uh, you're wrong.

> The OP was referring to the general performance of Python, not it's applicability to gaming, and pp's post that you quoted mentioned the Gimp and OOo, but made no reference to game development.

Yes, but what post was he replying to?

> **jimi_hendrix said:**
> i love C++ for somethings and python for others...

C++ for games and python for interfacing with other things (files, IRC, etc)

but basically unless your calculating the googleth iteration of pi i dont think you need C speed

pp.'s response quoted that in its entirety.  UF automatically strips nested quotes so my response to pp. excluded his quote of jimi's post.

Jimi posted about games and excluded Python in favor of C++.

So, as I said, you're wrong.  Someone did mention games.  Someone did exclude Python.  And I was replying to those points.  If you ever have any doubts as to what someone says they are doing it would behoove you to check the chain back a bit.  While webforums are notoriously hideous for this UF is decent in that every quote has a link back to the parent which, in turn, also has a link back to its parent and so on.  Of course that was hardly needed in this case since they were on the same page and had no other posts between them, but I digress.

---

### Post by pmasiar on 2008-12-16
> **jimi_hendrix said:**
> this comes from the fact that if you make real, proffesional games, you will, for the most part, touch C or C++ somewhere...even if its in the engine that you write your script for...

Real professional games have for sure small parts in ASM. Does it mean that whole thing has to be done in ASM? If not, why not?

It's really funny how people now replay the big discussion from 40 years ago when issue of ASM versus "high level languages (like Fortran, Algol and Cobol) were discussed... 

Those who cannot learn from history are forced to repeat it. Only that second time it is a farce: Knowledgeable people can see exactly what arguments are replayed, and what the solution would be after the dust settles :-) So we can just set back and enjoy the show :-)

---

### Post by pmasiar on 2008-12-16
> **pp. said:**
> No need to get your feathers ruffled.

I don't have feathers so your claim is patently false! :twisted:

When i have time to post (like this morning) I sometime respond to strong false claim in a strong language. I am afraid that subtlety is lost on many posters - not you, but many.

Also, it's more fun that way ;-)

---

### Post by SeanHodges on 2008-12-16
> **Greyed said:**
> I meant on the boards.

Fair enough, I must have taken you out of context there.

> **Greyed said:**
> Jimi posted about games and excluded Python in favor of C++.

So, as I said, you're wrong.  Someone did mention games.  Someone did exclude Python.  And I was replying to those points. 

OK, so lets just break down jimi's post then shall we?

> i love C++ for somethings and python for others...

C++ for games and python for interfacing with other things (files, IRC, etc)

Cool, so he loves using C++ for games, and Python for integration work. Perhaps you're suggesting that I should read between the lines?

> but basically unless your calculating the googleth iteration of pi i dont think you need C speed

Well this doesn't seem to be dismissing Python for games at all, in fact if anything this sentence could be construed as *supporting* languages other than C for games development.

> **Greyed said:**
> If you ever have any doubts as to what someone says they are doing it would behoove you to check the chain back a bit.  While webforums are notoriously hideous for this UF is decent in that every quote has a link back to the parent which, in turn, also has a link back to its parent and so on.  Of course that was hardly needed in this case since they were on the same page and had no other posts between them, but I digress.

Thanks for your tip on Web forums usage, that particular function I was well aware of, but it's always worth it to assume the least of someone :)

Don't get me wrong, I'm not usually keen on arguing off-topic, but the context of your arguments are missing the big picture. In the real world languages are not chosen because they are the "fastest", regardless of domain. They are chosen because they best meet a set of criteria, and are "fast enough".

---

### Post by iQuizzle on 2008-12-16
> **CptPicard said:**
> I don't get it... Python is just a language, you can implement it on top of a lot of stuff, for example the Java VM (Jython) or the CLR...

If you mean that in the end the CPU is running machine code instructions, then you're right. But C, too, is just a language...


yes, i agree. my point is just that if you open up python and run the print command, it is a function that has been compiled in C.

you could say that matrix operations are slow in python because running loops with lists is slow...but then if you import and use functions of the numpy package all the sudden python is fast again. why? because numpy contains C compiled functions to do matrix operations. so in the end it's just an issue of semantics because depending on how you use python it can be either fast or slow...which is no different than C. if your code runs slow, it's really just a sign that you need to go back and use a compiled function.

it would be fair to say that python has more overhead associated with function calls. of course python will run slow if you set it to make a ton of function calls...i just don't think it's fair to say that you can write something directly in C and then write the same thing in python and it's 60 times slower...specifically because python as a high-level language is not meant to be used the same way C is. it's like saying "check it out, if i use really poor programming techniques in python it runs much slower than it does in C". when in reality, if you actually learn how to program in the language (god forbid) all things become equal again.

example:
say for instance there is 1 microsecond of overhead for python to call a function from a C library. when run one time, it's practically just as fast as C and you won't even notice the difference. now suppose you loop that call one million times. this causes a full second of additional run-time over C because you have made repetitive calls on something that has a fixed overhead associated with it. of course if you're smart you can reduce this unnecessary overhead back to 1 microsecond if you loop the function you want to call in C, compile it and call it one time in python. the limitation of the language isn't speed. it can run for practical purposes as fast as C if you want it to. the downfall occurs when people don't understand how the language works and incorrectly assume that all of their programming styles from C should directly carry over into python.

---

### Post by mssever on 2008-12-16
> **iQuizzle said:**
> well if that's the case then you have to claim C is slow..because python is written in C. all i'm driving at is that python is made to work with C and _every function called from python_ is actually C code in some form.

> **iQuizzle said:**
> yes, i agree. my point is just that if you open up python and run the print command, it is a function that has been compiled in C.
Not necessarily. Ever heard of Jython? or PyPy? There's absolutely no requirement that any part of Python be implemented in C. The fact that the most widespread implementation, CPython, is written in C doesn't change anything. Theoretically, it's possible to implement Python in Whitespace, though only an insane person would try something like that.

Furthermore, when you compile a C program, you no longer have C. You have machine code. That's why it's fast. If you kept the code in a form recognizable as C, you'd have to use an interpreter and pay a speed penalty.

---

### Post by pp. on 2008-12-16
> **iQuizzle said:**
> i just don't think it's fair to say that you can write something directly in C and then write the same thing in python and it's 60 times slower... (...) of course if you're smart you can reduce this unnecessary overhead back to 1 microsecond if you loop the function you want to call in C, compile it and call it one time in python. the limitation of the language isn't speed. it can run for practical purposes as fast as C if you want it to. the downfall occurs when people don't understand how the language works 

It is neither fair nor unfair to state that interpreted late-binding languages have an inherent lower execution speed than - say - assembly. It's just a fact. 

The difference in speed varies and can range from negligible to rather more than three orders of magnitude. Just one of these weeks there was a thread in this forum which discussed a Python-to-C converter which resulted in programs running thousands of times faster than the original Python programs.

The difference in speed depends, of course, on the kind of thing the program does. Strangely enough, heavy number crunching can be expected to perform in Python nearly as well as in C.

However, consider some program which does a large number of array accesses such as a table sort.

In a language close to the machine architecture, adressing an element within an array involves doing a sum: base address of table plus offset of element within table. Depending on the processor's architecture the processor does it all for you in the course of one single instruction. 

In a language with properties such as those of Python you will fetch the index from a variable, ascertain the data type of the index, compute the actual address of the desired list element in RAM and then fetch the element from RAM. Please note that even fetching the index from a variable might involve a hash table lookup because variables might be identified by name and scope and not by a simple offset within a frame on the stack. I would assume that to be the case with Python for the single reason that variables are not declared beforehand.

Hence, it is really, really true that programs written in Python execute more slowly than programs written in languages closer to the hardware architecture. 

It is also true that Python can be much more useful than the reputedly 'faster' languages for many programmers, for a number of reasons which have been stated over and over again.

---

### Post by iQuizzle on 2008-12-16
> **pp. said:**
> 
In a language with properties such as those of Python you will fetch the index from a variable, ascertain the data type of the index, compute the actual address of the desired list element in RAM and then fetch the element from RAM. Please note that even fetching the index from a variable might involve a hash table lookup because variables might be identified by name and scope and not by a simple offset within a frame on the stack. I would assume that to be the case with Python for the single reason that variables are not declared beforehand.


i could be wrong, by my understanding of this process is different. python doesn't 'fetch' anything because all variables are pass-by-reference. thus every variable doesn't have it's own object created or associated with it like C does...instead variables are more like pointers.

i don't disagree with you that python is slower than C (however minute the difference is), but i'm talking about real-world application...and for almost any application, there's not a big difference if the program runs microseconds longer than equivalent C code. my point is that if you're noticing very slow run-times, then you have done something in your code that is not kosher in python programming..and in my experience there has always been simple solutions.

---

### Post by pp. on 2008-12-16
> **iQuizzle said:**
> i could be wrong

Yes

> **iQuizzle said:**
> python doesn't 'fetch' anything because all variables are pass-by-reference. 

In order to add two numbers, the processor has to have the values or at least the addresses of the parts of RAM where the values are kept. 

The program source calls a variable something like "myVar". The process of finding the address or the value of a variable when you only have a name for that variable is what I was referring to in my post. 

Also, being late binding, the program must first check to see if the content of the variable "myVar" is indeed a number and is indeed of a type suitable for addressing an element within a list.

I won't mention checking the index range here because any program written in C ought to do that as well (and often fails to do so).

---

### Post by iQuizzle on 2008-12-16
> **iQuizzle said:**
> 
i don't disagree with you that python is slower than C (however minute the difference is), but i'm talking about real-world application...and for almost any application, there's not a big difference if the program runs microseconds longer than equivalent C code. my point is that if you're noticing very slow run-times, then you have done something in your code that is not kosher in python programming..and in my experience there has always been simple solutions.

when people say python is slower than C they're usually not referring to the things you're talking about because those happen pretty fast, even in loops. there's much greater overhead associated with calling python functions from out of the C library than what you're talking about.

---

### Post by Greyed on 2008-12-16
> **mssever said:**
> Furthermore, when you compile a C program, you no longer have C. You have machine code. That's why it's fast. If you kept the code in a form recognizable as C, you'd have to use an interpreter and pay a speed penalty.

[TCC]("http://bellard.org/tcc/") anyone?  :-\"

Kept that one in the back of my brain if there was ever a time I wanted to attempt C again.  Currently looking at D and OCaml for compiled languages though.

---

### Post by pmasiar on 2008-12-16
> **iQuizzle said:**
> when people say python is slower than C they're usually not referring to the things you're talking about because those happen pretty fast, even in loops.

Even if I agree with pp. on technical merit, I agree with iQuizzle in spirit.

In theory, there is no difference between the theory and practice. 
In practice, there is. :-)

1) Python is plenty fast for 90% of tasks OP will ever do.

2) Python is in 90% cases the quickest way to correct program - and if my program does not have to be correct, I can beat any of your super-fast C/C++ code with even faster NOP instruction :twisted:

3) Your CPU is idling anyway, we should worry how to improve our brain's productivity by burning cheap CPU cycles: [http://www.paulgraham.com/hundred.html](http://www.paulgraham.com/hundred.html) - "The Hundred-Year Language"

PS: And of course Python can be replaced by Ruby, Perl and such, when productivity matters.

---

### Post by pp. on 2008-12-16
> **pmasiar said:**
> we should worry how to improve our brain's productivity by burning cheap CPU cycles

We're on agreement on that point, too, together with most of the software industry. Most software manufacturers improve ***their own*** productivity by burning ***my*** CPU cycles which do not cost them anything at all.

With all that hoopla about time to completion vs execution time, one very special case hasn't been mentioned at all in this thread.

Consider the case where time to completion is roughly the same but the alternatives are assembly vs a high level language. There are problems where using the high level language will give you so much leverage that you end up with a much more sophisticated or complex solution which would not have been affordable in the lower level language, and which will solve the same problem in shorter time even while wasting a large percentage to the perceived overhead of the higher level language.

That kind of scenario is often seen in the brute force vs elegant solution discussions.

Hence, I stipulate that there will be cases where - given the same cost of development - the python solution will be faster than the C one.

---

### Post by mssever on 2008-12-16
> **Greyed said:**
> [TCC]("http://bellard.org/tcc/") anyone?  :-\"

Kept that one in the back of my brain if there was ever a time I wanted to attempt C again.  Currently looking at D and OCaml for compiled languages though.
That's good to know. Maybe one of these days I'll get sufficiently bored that I'll learn C.

---

### Post by pmasiar on 2008-12-16
> **pp. said:**
> there will be cases where - given the same cost of development - the python solution will be faster than the C one.

But of course!

As always in any project management:  Time (manpower), money (budget), bugs/features: pick any two! ;-)

---

### Post by slavik on 2008-12-16
> **pmasiar said:**
> But of course!

As always in any project management:  Time (manpower), money (budget), bugs/features: pick any two! ;-)
you forgot another thing: what people already know. because if you have 10 Perl devs and want a project in Python, they either need to learn enough Python to use it wisely or you risk spending more time supporting the app.

---

### Post by samjh on 2008-12-17
> **slavik said:**
> you forgot another thing: what people already know. because if you have 10 Perl devs and want a project in Python, they either need to learn enough Python to use it wisely or you risk spending more time supporting the app.

That would add onto time, money, and features/bugs.  In your case, the Python implementation will take more time, therefore more money, and have less features or more bugs. ;)

---

