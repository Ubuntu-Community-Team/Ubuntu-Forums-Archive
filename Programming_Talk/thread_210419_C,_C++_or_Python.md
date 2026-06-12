---
title: "C, C++ or Python?"
date: 2006-07-06
forum: Programming Talk
---

### Post by Randomskk on 2006-07-06
Heya
I've got a whole load of free time coming up, about 6 weeks free, as school just ended for the holidays, and I figured I may as well do something productive.
Anyway, I decided on learning a new language, since PHP isn't much use besides web pages :P

I've thought about three, basically: C, C++ and Python.
Now, Python I've used a little, and can do some basic things in, plus I've figured out how to get it to bind to a Qt window, with PyQt, so I can make fun GUIs that way.
C I have a small book on, but I don't know how useful it'd be since it's a pretty old book, and C++ I've heard nothing about.

Which language would you recommend, and why? I've heard C++ is harder than C, and I know Python's easier and similar to PHP, but I don't really know which would be better.

Being able to have the applications work with some sort of GUI would make it fun, too - do C and C++ handle this fairly well?

Also, I'll probably just use Kate or something for writing the code, unless you think it's a really good idea to use an IDE while starting out.

Thanks for any help

---

### Post by DirtDawg on 2006-07-06
If you're just doing it for fun, I say just go for Python. Unless you're planning on doing some heavy duty coding.

---

### Post by Note360 on 2006-07-06
Python is good for learning. I am gonna say Perl and Ruby are also really nice languages, so is C# (When running on Mono). (Why's Poigant Guide to Ruby is a really good free full featured book)

---

### Post by Daverz on 2006-07-06
There's really no reason not to learn both Python and C; they compliment eachother nicely.

---

### Post by LordHunter317 on 2006-07-06
If you're going to insist on learning one of these three languages, then I'd recommend C++ simply because the learning material for it is far superior than the other two.  It will teach the language and basic underlying theory of computation and programming.  Most of the python material I've read fails to delve into really deep detail on the latter part.

---

### Post by Wallakoala on 2006-07-06
Python is really great. Learning the basics might only take a day or two depending on how computer-literate you are. But the great thing is there is so much more you can learn after the basics. The possibilities are endless.

---

### Post by Max Luebbe on 2006-07-06
i would definately pick python of the three you mentioned.
Build up your programming chops with it, then tackle C at a later date if you feel like systems programming or have a sudden need to squeeze every drop of performance out of a program.

I know all of the three, and given the choice to pick one for a making generic ubuntu app xyz, id pick python in a second.

---

### Post by ifokkema on 2006-07-08
Hi,

> **Randomskk said:**
> Anyway, I decided on learning a new language, since PHP isn't much use besides web pages :P
Hmm.... I wouldn't use the wording 'much use' here since you CAN use PHP for lots of stuff. I've written a backup script, a PDF creator, a mass mailer, a graphical counter script, a download script, a reminder service and several scripts analyzing various data. You can even create GTK GUIs with PHP. Whether or not PHP would be the best choice for all of this, is open for discussion :)

> **Randomskk said:**
> I've thought about three, basically: C, C++ and Python.
Python is a scripting language, C and C++ are programming languages. Programming languages in general take longer to learn, and it takes longer to code a similar app. However, it will run much faster then when the app is written in a scripting language. When it's running speed you need, go for C++. If you just want to have some fun and quickly create graphical apps, use Python (or PHP, :)).

---

### Post by DolphinWeb on 2006-07-08
Python, python, python. Just for a quick-n-easy program, and you're not worried about speed, Python is perfect. It's syntax is close to PHP - it helps. C/C++ are more machine-level than human-understandable, but they're lightining fast. C++, in my opinion, is the fastest (no test actually done, just observation).

Python - easy syntax
C - average
C++ - VERY fast

I'd still choose Python, then move onto C for Python modules, and any time you want more spped. ;)

> Python is a scripting language, C and C++ are programming languages. Programming languages in general take longer to learn, and it takes longer to code a similar app. However, it will run much faster then when the app is written in a scripting language
Right! Speed VS Ease-of-use.
Really, it depends on what you're going to do. Big project for the boss? C/C++. Simple app for fun? Python. Each is good in it's own way.

---

### Post by Randomskk on 2006-07-08
How big is the speed difference between python and C++, then?
That seems to be what everyone's saying, but how complex does a program need to be before you start seeing a difference?

---

### Post by JDD on 2006-07-08
Needs to be gigantic frankly. From what i can tell your a hobbiest, so i'd go with python, since you would see little to no difference in speed, and python syntax is much easier to grasp then C/C++'s.

To whoever posted above, Python is NOT a scripting language, yes, it's used quite a bit for scripting, but it isn't constricted solely to it. More advanced python is actually OO.

Just my 2 cents :)

---

### Post by LordHunter317 on 2006-07-08
[QUOTE=ifokkema]Python is a scripting language, C and C++ are programming languages.[/quote]No, all 3 are programming languages.  All 3 are touring-complete.

Definition of a scripting language is a touch hard too.  C can be interpreted, though it's pretty rare to see that actually occur.

> However, it will run much faster then when the app is written in a scripting language.That's not necessarily true either.

---

### Post by LordHunter317 on 2006-07-08
[QUOTE=DolphinWeb]It's syntax is close to PHP - it helps.[/quote]Only in the same way assembly and C are close, which is to say, not really at all.

[quote=Randomskk]How big is the speed difference between python and C++, then?[/quote]Massive.

> That seems to be what everyone's saying, but how complex does a program need to be before you start seeing a difference?If you use threads, you may notice it immediately because Python's interpreter is not thread-safe. 

If you're doing anything CPU-bound, you'll notice it immediately generally and it'll be rather apparent.  There are some exceptions to this, but they require really careful programming.

[quote=JDD]To whoever posted above, Python is NOT a scripting language, yes, it's used quite a bit for scripting, but it isn't constricted solely to it. More advanced python is actually OO.[/quote]Scripting and OO are completely orthogonal concepts.  Javascript is only seen in the wild as a scripted language, yet it is OO.

---

### Post by Jessehk on 2006-07-08
I personally quite like Ruby. Features don't feel "tacked-on" like I sometimes feel they are in Python. Furthermore, it is a much more pure language. 

I also recognize that Python is probably easier for the beginner. Furthermore, it is better suited to graphical games, and GUI's due to _current_ limitations of speed in Ruby (a byte-compiler called YARV is in the works).

---

### Post by Ubuntist on 2006-07-20
> **Randomskk said:**
> How big is the speed difference between python and C++, then?
That seems to be what everyone's saying, but how complex does a program need to be before you start seeing a difference?

You can have a look at [http://shootout.alioth.debian.org/]("http://shootout.alioth.debian.org/")
to see execution times of numerous benchmarks under numerous languages, including Python and C++.

Execution time is only part of the total time.  This report compares the times needed to code, debug and execute a particular task among several languages, including Python and C++:
[http://page.mi.fu-berlin.de/~prechelt/Biblio/jccpprtTR.pdf]("http://page.mi.fu-berlin.de/~prechelt/Biblio/jccpprtTR.pdf")

It's also possible to embed C code directly in Python for those parts that are really computationally intensive.

---

### Post by RAOF on 2006-07-21
Python.  It's easy, it's quick, and it's got a nice unittesting framework :)

Many of the Ubuntu tools are written in python.  Unless you're doing anything heavily computational, python is perfectly fine (and if you **are** doing something heavily computational, generally you can just put the critical section in a python-extension library written in C, and call it from python).

For examples of python programs, check out Listen (audio player), Gnome-app-install (also known as "Add/Remove Programs"), bazaar-ng (distributed source-control program), to name a few.

In short, don't worry about how much slower python is.  Computer science in general* doesn't care - see how the trend is for higher-level, interpreted languages like Java and C#.  Yes, they're slower than C, but most of the time, even if they're 100 times slower than equivalent C code the trade off is well worth it.  Computers are ridiculously fast.  Your time is much more valuable than CPU time :).

Interpreted stuff tends to be easier to debug too.  In python, for example, I've never got an error that didn't give me **some** sort of indication of where I should start looking.  If you write C, you'll need to fire up the debugger to work out where your program is segfaulting :).

* - Yes, I aknowledge that there are particular cases where you want to use a low-level language.  The kernel, big, important system libraries, Xorg.  Almost all programming can be done more effectively in a higher level language, though.

---

### Post by LordHunter317 on 2006-07-21
> **RAOF said:**
> .In short, don't worry about how much slower python is.  Computer science in general* doesn't care - see how the trend is for higher-level, interpreted languages like Java and C#.Urr, umm, no.  Computer Science is intimiately involved in how fast things are.  However, the reality is that language choice and hardware choice only make a few small orders of magnitude difference (let's say ~1000x at best for argument's sake).  Proper algorithm choice and program design make a difference of several orders of magnitude higher (say 1,000,000 or more, trivally).

Computer scientists usually express things in big-O notation, which is a mathmatical notation for bounded complexity of an expression.  So they're interested in speed, but not the nitty-gritty details.  The heart of applied CS is essentially doing more with less by being smart.

Java and C# aren't interpreted either, or remotely close.  

> Interpreted stuff tends to be easier to debug too.  In python, for example, I've never got an error that didn't give me **some** sort of indication of where I should start looking. Err, you will with a sufficently  If you write C, you'll need to fire up the debugger to work out where your program is segfaulting :).You shouldn't apply C's inadequacies to everyone.  It's not nice.  C++ doesn't have this problem necessarily, though most implementations don't give as clear exeception output as other languages.

---

### Post by jordilin on 2006-07-21
I'm a python fan. I learned C at the University, and to be sincere, you can do complex things with python in an easy manner. C with its pointers are a nightmare. Python is a complete, full featured programming language, object oriented, has a very clear syntax and very powerful. We, with Linux, can take profit of python and our very advanced operating system to do amazing things.
Go for python!!! It's very cool 8)

---

### Post by JDD on 2006-07-21
> **jordilin said:**
> I'm a python fan. I learned C at the University, and to be sincere, you can do complex things with python in an easy manner. C with its pointers are a nightmare. Python is a complete, full featured programming language, object oriented, has a very clear syntax and very powerful. We, with Linux, can take profit of python and our very advanced operating system to do amazing things.
Go for python!!! It's very cool 8)

I agree and disagree with jord. Sure you can do complex things with python in an easy manner, but it wouldn't be near as efficient as doing complex things with C. Sure, when your doing something simplistic you might as well go with Python since its going to run fast either way, and with Python you'd have less coding time. 

So unless your doing some heavy systems programming or the like, Python should fit you well :) 

My 2 cents :o

---

### Post by Van_Gogh on 2006-07-21
> **JDD said:**
> I agree and disagree with jord. Sure you can do complex things with python in an easy manner, but it wouldn't be near as efficient as doing complex things with C. Sure, when your doing something simplistic you might as well go with Python since its going to run fast either way, and with Python you'd have less coding time. 

So unless your doing some heavy systems programming or the like, Python should fit you well :) 

My 2 cents :o

I agree and disagree with JDD :), because it certainly is possible to do non-simplistic things with Python. And I agree with most of the guys here: Learn Python first, it's mush easier. Though you want to pick up other languages later on too, especially ones that are more CPU-efficient.

---

### Post by xtacocorex on 2006-07-21
If you got the time and understand programming already, all you're learning is syntax and therefore you should dabble in at least two of the three. I'd pick C++ and Python and that's not because I'm currently using both for a project of mine which has Python doing all the basic stuff of GUI setup and that sort and using C++ for the actual computation and piping data back and forth.

Once you learn one language, picking up another isn't too hard, unless you were taught non object oriented programming like I was. I've been programming for about 7 years now and have attempted OOP a couple of times and I finally understood it with Python a couple of months ago. This is exciting because I use FORTRAN a lot and the new standard, 2003, is OOP.

---

### Post by RAOF on 2006-07-22
> **LordHunter317 said:**
> Urr, umm, no.  Computer Science is intimiately involved in how fast things are.  However, the reality is that language choice and hardware choice only make a few small orders of magnitude difference (let's say ~1000x at best for argument's sake).  Proper algorithm choice and program design make a difference of several orders of magnitude higher (say 1,000,000 or more, trivally).

Computer scientists usually express things in big-O notation, which is a mathmatical notation for bounded complexity of an expression.  So they're interested in speed, but not the nitty-gritty details.  The heart of applied CS is essentially doing more with less by being smart.
...
Thank you for explaining more fully what I meant.  That's exactly it.  It's possible to write slow programs no matter **what** language you use, and the most important factor in program speed is the algorithms/data structures you use.

I'll just add:
> 
Laziness is the highest virtue in a programmer.


---

### Post by IYY on 2006-07-22
C. It's a very important language, and you need to know it anyway if you want to learn C++.

---

### Post by LordHunter317 on 2006-07-22
Err, no, it isn't.  In fact, learning C before learning C++ is generally just a good way to learn bad habits in C++.  Good C is bad C++.  Good C++ is simply impossible in C.

Don't believe me?  Write a program in C to correctly read a string from a user, concatonate it with another string, and print the result to a user.  You cannot leak any memory and must handle all potential input cases without creating any security risks.  You may not also just crash under OOM condition.

Then write the same thing in C++.  The difference pretty thoroughly proves my point.

---

### Post by ProjectGod on 2006-07-22
hiya! i think python. 

i was bored... believe it or not on this very saturday night. i had installed python (free download) quite some weeks ago but never touched it... in under 30 minutes i've written a program that asks for user input to calculating the volume of a prism / cube. neat huh? you should know i've NEVER done programming in my life before. believe me. in the spirit of open source... here's the code! hopefully i'll keep learning and write something neat to share with everyone.

-------------------------------------

# calculate the volume of a cube
# asks for user input first and then calculates volume

# first define all of the variables and functions

print "volume = height x breadth x width"
height = input("what is the height?")
breadth = input("what is the breadth?")
width = input("what is the width?")
volume = height * breadth * width

# second do the calculations
question = raw_input("do you with to view the volume of your cube? y/n")
if question == "y": print volume
else: print ""

-------------------------------------

---

### Post by jordilin on 2006-07-22
> **JDD said:**
> I agree and disagree with jord. Sure you can do complex things with python in an easy manner, but it wouldn't be near as efficient as doing complex things with C. Sure, when your doing something simplistic you might as well go with Python since its going to run fast either way, and with Python you'd have less coding time. 

So unless your doing some heavy systems programming or the like, Python should fit you well :) 

My 2 cents :o
You can do very nice things in python. Take a look at this app made in python an pygtk. Discussed in the forums in [http://www.ubuntuforums.org/showthread.php?t=126080&highlight=listen](http://www.ubuntuforums.org/showthread.php?t=126080&highlight=listen)
web page:
[http://listengnome.free.fr/](http://listengnome.free.fr/)
It's a music player made with python. Amazing, eh? Don't underestimate the power of python :cool:

---

### Post by JDD on 2006-07-22
> **jordilin said:**
> You can do very nice things in python. Take a look at this app made in python an pygtk. Discussed in the forums in [http://www.ubuntuforums.org/showthread.php?t=126080&highlight=listen](http://www.ubuntuforums.org/showthread.php?t=126080&highlight=listen)
web page:
[http://listengnome.free.fr/](http://listengnome.free.fr/)
It's a music player made with python. Amazing, eh? Don't underestimate the power of python :cool:

It's not that i underestimate it, i just know say... a 200kloc (thousand lines of code) program would more then likely run faster in C, then the same program in Python.

:eek:

---

### Post by LordHunter317 on 2006-07-22
But you don't until you've proven that.

---

### Post by JDD on 2006-07-22
> **LordHunter317 said:**
> But you don't until you've proven that.

[http://shootout.alioth.debian.org/gp4/](http://shootout.alioth.debian.org/gp4/)

They have -.-.

---

### Post by thumper on 2006-07-22
> **JDD said:**
> It's not that i underestimate it, i just know say... a 200kloc (thousand lines of code) program would more then likely run faster in C, then the same program in Python.

:eek:

But to be realistic, 200kloc of C will be nothing near 200kloc of python for functionality :)

---

### Post by JDD on 2006-07-22
> **thumper said:**
> But to be realistic, 200kloc of C will be nothing near 200kloc of python for functionality :)

Since when are we realistic? :D

---

### Post by LordHunter317 on 2006-07-22
> **JDD said:**
> [http://shootout.alioth.debian.org/gp4/](http://shootout.alioth.debian.org/gp4/)

They have -.-.Umm no, they have not.  Those benchmarks aren't even indicative of most code run, and they're still irrelevant.  

Why?  Because no one cares who's fastest.  We only care who's fast enough, and benchmarks of that sort don't tell us that.

---

### Post by JDD on 2006-07-22
> **LordHunter317 said:**
> Umm no, they have not.  Those benchmarks aren't even indicative of most code run, and they're still irrelevant.  

Why?  Because no one cares who's fastest.  We only care who's fast enough, and benchmarks of that sort don't tell us that.

[QUOTE=JDD]Sure you can do complex things with python in an easy manner, but it wouldn't be near as efficient as doing complex things with C[/QUOTE]

I didn't say it wasn't fast enough, i said it was slower then C. Lots of people care who's faster, some of the times its the deciding factor in what program/application you may use.

This isn't meant to be an argument, i was just adding my 2 cents.
:rolleyes:

---

### Post by Randomskk on 2006-07-22
I've been keeping track of the thread, and it's pretty insightful - practically everyone's said python, although a few people have also said learning C/C++ as well would be a good idea.
It's interesting to note that many people who said python know C(++) *and* python, yet still say definitely go for python.

The PDF someone linked on the differences between scripted and non-scripted was interesting reading, saying that basically scripts took half as long to write, using up half the amount of code, and running (roughly) half as fast (in their test case).

Anyway, what I've decided to do is learn C++ first, writing a small program that I've wanted to make for a while in it (with a Qt GUI), going through the books "C++ For Dummies" and then "Accelerated C++".

After that, I'll pick up O'Reilly's "Learning Python" book from a friend, and depending on how good it is I'll see about getting a second book as well. I don't know what I'll make yet in python though >_>

I decided on this for a few reasons... if nothing else, I'd like to have a hard, compiled language learnt for when I do want something CPU efficient, plus it seems most of the people here know C++ as well anyway.
Plus, I can use it to build python modules, so it won't go to waste even if I do just use Python.
Also, it'l be nice to know how much better python is, at the least :P

So, one last question I guess: what python books are good?
Assuming I'll know some C++ at that point, but very little python.

Feel free to keep on arguing about whether scripts or compiled programs go faster too, it's interesting reading :D

---

### Post by tseliot on 2006-07-22
> **Randomskk said:**
> So, one last question I guess: what python books are good?
Assuming I'll know some C++ at that point, but very little python.

I'm currently using “Beginning Python: From Novice to Professional” by M.L. Hetland. I bought it on amazon.

I'm not a programmer, I'm learning Python in my spare time. I only knew a few of Bash before. 

That book is really nice and easy to follow even if you have never tried to program before.

---

