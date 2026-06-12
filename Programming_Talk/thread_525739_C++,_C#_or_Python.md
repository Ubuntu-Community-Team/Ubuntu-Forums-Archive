---
title: "C++, C# or Python"
date: 2007-08-14
forum: Programming Talk
---

### Post by SRX on 2007-08-14
Hi

I am looking into programming but I am stuck on which language to learn I want to be able to make gui's and I want a language that is very stable and portable for most platforms. 

Also if I do choose to learn C should I pick either C++ or C#

thank you 

sincerely

SR

---

### Post by kebes on 2007-08-14
> **SRX said:**
> I am looking into programming but I am stuck on which language to learn I want to be able to make gui's and I want a language that is very stable and portable for most platforms. 

Also if I do choose to learn C should I pick either C++ or C#

I think Python would be the best place for you to start. Python has very clean syntax (which is good for beginners) but is also a very elegant and powerful language (so that as learn more you won't feel constrained by the language).

Python has GUI toolkits and development environments, so no trouble there. In my experience Python code is portable than C++ code, so that's a bonus, too.


I've never used C#, so I can't comment on that one.  C++ is also a powerful language with lots of code and examples out there... but since you don't seem to have a preference for C++ or Python, my recommendation is Python.

---

### Post by SRX on 2007-08-14
Thanks for the help

---

### Post by aks44 on 2007-08-14
If you're new to programming, the trend around here seems to be learning Python (granted, C or C++ are quite hard for newcomers).

I guess I'll let pmasiar introduce you to Python. :p

> **SRX said:**
> Also if I do choose to learn C should I pick either C++ or C#

C# has nothing to do with the C and C++ family. It only borrows some syntax. It's... something else... that MSFT made up. 'nough said.

If you really want to learn the C/C++ family, I'd advise you to begin with C++, then C.

If you do the other way around you'll have to *totally* unlearn C when you learn C++, and I can assure you that you'll have hard times then...

---

### Post by Jessehk on 2007-08-14
> **aks44 said:**
> 

I guess I'll let pmasiar introduce you to Python. :p


I know. It's getting so old. ;)

> 
C# has nothing to do with the C and C++ family. It only borrows some syntax. It's... something else... that MSFT made up. 'nough said.


Without having any actual experience with C#, I  hear that it combined with .NET is a great platform. I wouldn't be so quick to dismiss it just because it's produced by Microsoft.

---

### Post by dragonfyre13 on 2007-08-14
Yeah, I'd definitely go with Python. Of course, realize that you are asking this in an ubuntu forum. Ubuntu :heart: python. 

Besides, I like python simply because it is very specifically portable across platforms. Technically, if you code very well, and focus on it, C/C++ is portable as well, but you run into all sorts of issues coding those languages with a UI and making it portable. UIs are inherently not portable, unless you use WXWindows. WXPython is much easier (IMHO) to write in than WXWindows, as is python in general.

End result, if you want portability with C/C++, plan to rewrite your UI for all platforms. If you want easier portability, write your code in Python to begin with.

---

### Post by kayvortex on 2007-08-14
I'd say Python to start with, then C++ after that. You can do it the other way around, but it makes more sense to start with a "simpler" language first.

---

### Post by LarsP on 2007-08-14
Yes, Python is a good language to start with. The reason is that it is more important to learn about how to program(rather than how to program in a specific language). Python has much less syntax than C/C++, so you can concentrate more on concepts.

If you want GUI portability, you can use something like Qt. Qt is C++ based, but there are bindings for Python(PyQt).

---

### Post by aks44 on 2007-08-14
> **Jessehk said:**
> I wouldn't be so quick to dismiss it just because it's produced by Microsoft.

Granted, my post gives that impression. My bad.

The "nuff said" statement referred to the "something else" part rather than the "Microsoft" part (as a "proof" I'll say that IMHO MSFT's VC8.0 compiler is one of the best C++ optimizing compilers out there, even though it doesn't fully respect the standards).

I just don't believe in JIT, be it .NET or Java or whatever else. In fact, the only languages I trust are the ones that are close to the metal.

MSFT went so far to make a full prototype OS out of C#, removing the hardware process isolation (GDTs / LDTs) in favor of application signing. And at the same time they fully removed shared libraries in favor of static ones, arguing that "this solves upgrade compatibility problems". How can anyone trust engineers with so little insight? (whether they belong to MSFT or not, that's not the point).

---

### Post by aks44 on 2007-08-14
> **dragonfyre13 said:**
> Technically, if you code very well, and focus on it, C/C++ is portable as well, but you run into all sorts of issues coding those languages with a UI and making it portable. UIs are inherently not portable, unless you use WXWindows.

I found Qt to be *very* cross-platform friendly (way more than wxWidgets). YMMV.

---

### Post by slavik on 2007-08-14
I'd sayd C -> C++ -> Python

that way, you understand how things are under the hood and give you an appreciation for the things you can easily do in Python that aren't easy in C.

Otherwise, you will see how difficult C is (from python standpoint) and never bother to learn it.

putting you question aside, algorithms and good practices are of very high importance. languages only allow you to express those.

---

### Post by aks44 on 2007-08-14
> **slavik said:**
> I'd sayd C -> C++ -> Python
[...]
putting you question aside, algorithms and good practices are of very high importance. languages only allow you to express those.

I fully agree with that, and that's the very reason why I'd advise the exact contrary : Python -> C++ -> C.

Knowing how things really work under the hood is worth nothing if one doesn't have a high level approach of his problem. Indeed, for beginners I believe (from both my experience and other people's experience) that heading first into low level details is the best way to f*** up.

---

### Post by LaRoza on 2007-08-14
Either, except C#.

My wiki has information (tutorials/books/programs) for many languages. It is the first link in my sig.

---

### Post by batrick on 2007-08-14
If he wants the program to be runnable cross platform it may be better to write it in Java depending on the type of GUI and userbase.

If you want to learn algorithms you should do it in C, if you want other people to do it for you then do it in C++, Python, etc.

---

### Post by LarsP on 2007-08-14
> **batrick said:**
> If you want to learn algorithms you should do it in C, if you want other people to do it for you then do it in C++, Python, etc.

Wouldn't a higher level language let him focus on the algorithm rather than the syntax?

---

### Post by LaRoza on 2007-08-14
> **LarsP said:**
> Wouldn't a higher level language let him focus on the algorithm rather than the syntax?

Learning one language doesn't exclude others, but learning Python might make learning C++ easier (and faster). I learned C++ first, so I can't really go against it, but I usually recommend Python or another interpreted language.

---

### Post by batrick on 2007-08-14
> **LarsP said:**
> Wouldn't a higher level language let him focus on the algorithm rather than the syntax?

Learning a data structure or algorithm is not about syntax, it's about implementation and use. Learning how to implement the algorithm/data structure (hopefully) implies learning how to use it.

A higher level language would just hand him some function that does all the work for him (various sort algorithms, dictionaries, stacks, linked lists, et cetera). I'm of the opinion most people using a data structure/algorithm should at least look at the pseudo code for it before use. Instead of "why is my application doing X incorrectly" errors, you get "why is my implementation of Y data structure" wrong (assuming they need to implement it).

---

### Post by aks44 on 2007-08-14
> **batrick said:**
> A higher level language would just hand him some function that does all the work for him (various sort algorithms, dictionaries, stacks, linked lists, et cetera). I'm of the opinion most people using a data structure/algorithm should at least look at the pseudo code for it before use. Instead of "why is my application doing X incorrectly" errors, you get "why is my implementation of Y data structure" wrong (assuming they need to implement it).

The whole top-down vs bottom-up argument... ;)

IMHO knowing how/when to *use* specific data structures or algorithms is way more important than how to implement them.

I'm not saying you should not bother with their implementation, just that it should not be your priority.


Just an architect's two cents though... (I know, I'm biased ;))

---

### Post by AlexThomson_NZ on 2007-08-14
My 2c...

I'd learn either C or Python.  gtkmm  and libglademm is a bit dodgy with C++ (Won't go into here- have been plenty of posts on this).

As I have mentioned before, by the time you get to coding gtk apps, the complexity shifts towards the gtk implementation rather than syntax, ie. you have to understand callbacks, events, etc.  I would personally advise against using Glade at first, until you understand how to control widgets, etc. on a lower level.

I tend to disagree with the people here who say all beginner programmers should start with Python to learn programming structure, etc.  If you want to be a C/C++ programmer, start with C/C++, don't start with Python (unless you want to be a Python programmer).  Some here like to portray C is not some horrible language only old unix grey-beards and kernel hackers understand, but have a look for yourself and make up your own mind.

Ok pmasier, your turn... ;)

---

### Post by LarsP on 2007-08-14
> **batrick said:**
> 
A higher level language would just hand him some function that does all the work for him (various sort algorithms, dictionaries, stacks, linked lists, et cetera). I'm of the opinion most people using a data structure/algorithm should at least look at the pseudo code for it before use. Instead of "why is my application doing X incorrectly" errors, you get "why is my implementation of Y data structure" wrong (assuming they need to implement it).
Is it more likely that an algorithm is found in the standard library of a high level language than a low level language?

As an example, say that you are making an image processing application. For this application you have to implement the fft-algorithm ([http://en.wikipedia.org/wiki/Fft](http://en.wikipedia.org/wiki/Fft)). In a high level language you can focus on the mathematics/algorithm, without having to think too much about memory organization, variable typec etc.. 

High level language is not the same as large standard library.

The "algorithms and data structures"-course at my school uses Python exclusively in examples.

---

### Post by AlexThomson_NZ on 2007-08-14
BTW, so you can do your own comparisons:

[http://www.pygtk.org/pygtk2tutorial/index.html](http://www.pygtk.org/pygtk2tutorial/index.html)
[http://www.gtk.org/tutorial/](http://www.gtk.org/tutorial/)

These are two mirrors of tutorials- one for python and one for C.  Maybe I've been using C too long, but to me one doesn't look particularly easier than the other

---

### Post by samjh on 2007-08-14
To the original poster:

Depends on your focus.

I'll use a car analogy.

If you're the type of person who is only interested in getting from point A to point B without learning anything else about cars or driving: you learn to drive a car with automatic transmission, get the minimum number of lesson and just pass the test.
ie. you learn **Python**.

If you're the type of person who is interested in driving with finesse and skill, know how to change your oil, tyres, fan belt, diagnose routine problems: you learn to drive a car with manual transmission, take a short course on vehicle maintenance, and a couple of defensive driving courses.
ie. you learn **C** or **C++**.

If you're somewhere in between, then learn C# or Java.

The analogy is a bit extreme, but that's the general idea.

---

### Post by RedSquirrel on 2007-08-14
In my view, the best way to learn algorithms is with pseudocode and some diagrams. You can't go wrong with a good book, a pencil, and some paper. Coding algorithms (in an actual programming language) before you understand them is a bad habit to get into. It makes you lazy (in a bad way, not the 'enlightened' way) because you rely on recompiling your program and running it to see what's going on rather than understanding *in your mind* what is going on.

With regard to the OP's question, around here, Python will be the standard recommendation (as you can see :)). Bear in mind that there is little harm in trying out C or C++. It's not like you'll have to face a firing squad if they seem too difficult for you. I no longer have any recommendation for which should be learned first, C or C++. I used to think it would be better to learn C first, but at the moment I don't think it really matters. And I don't know enough about C# to really make a recommendation.

---

### Post by bread eyes on 2007-08-14
I don't think it really matters.

---

### Post by pmasiar on 2007-08-14
OK everyone waits until I say my word "learn Python" - but I repeated this advice so often here that most arguments for python were mentioned already. Well done guys :-D

Yes, C#/Java are used more often. One of the reasons is, big companies spent millions of dollars promoting them (Python got only recently support from ... Google), and C#/Java are often used in projects where [PHB](http://en.wikipedia.org/wiki/Pointy_Haired_Boss) picks the language, many smar hackers prefer Python) 

But all of this does not mean anything to you. IMHO *the* most important argument for beginner's language is: "How many pages has book 'language X in a nutshell' ". And you need to consider not only syntax of language itself (because there are exotic funny languages with only dozen of symbols - and *not* easy to use, syntax of [Scheme](http://en.wikipedia.org/wiki/Scheme_%28programming_language%29) has about a page, Forth has less than half-page), but also size of the language standard library. Big library is good (you have many modules ready), but too big libary is hard to learn: [Java In A Nutshell, 5th Edition](http://www.amazon.com/exec/obidos/ASIN/0596007736/interactiveda490-20) has 1252 pages of bigger format: Shipping Weight: 3.4 pounds :-)

[Python Pocket Reference](http://www.oreilly.com/catalog/pythonpr3/) is 158 pages of pocket format, best $10 value in language reference. And has everything you will need for at least a year.

Programming is not easy. Syntax of programming language is about 10% of the problem: much bigger part is designing program structure (modules/packages, and objects/classes), data structures, designing way to build and test and debug your code. Comparing with these problems, when experienced programmer is learning new language, syntax is almost trivial. 

But you are not experienced programmer yet, so it would be wise to start with language which works hard to make programming intuitive and obvious - Python.

After you learn basics of programming, data structures (which are so much easier to build in Python), and debugging, you may decide to learn more "enterprise-ready" languages, like C family (including Java). If you are so inclined, I would recommend C: simpler, and closer to the metal. Or you might decide that Python is enough for you, and use it for everything, like many people increasingly do these days. Heck, even Microsoft released version of Python for .NET - [IronPython](http://en.wikipedia.org/wiki/Ironpython) - under open-source license, no kidding!

Don't let people put you into a box "java programmer" "C programmer". If you become programmer, chances are, you will learn many languages during your long career, so better get ready to be flexible.

But I would strongly recommend to start with Python. In wiki in my sig you will find many links, including training tasks to solve. 

Good luck!

---

### Post by slavik on 2007-08-15
imo, it's better to go from lower level language to higher level language, this way you gain appreciation of the higher level language.

example:
C -> Perl
"Cool, no need to worry about data types or memory"

Perl -> C
"No automatic memory handling? and wtf is up with these datatypes? this sucks"

How many people do you know that drive automatic, that can switch to manual? How many people that drive manual can switch to automatic?

another thing in java:
string str;
for(int i = 0; i < 1000; i++) {
  str += i.toString();
}

notice any problems? probably not, but the problem is that at the end, the code will use n^2 memory (if i.tostring()always returns the same size string) because when java appends to a string, it creates an entirely new object. and garbage collection is on the lazy evaluation scheme, not right away as most programmers would probably do if they managed the memory themselves.

---

### Post by Wybiral on 2007-08-15
I vote C or Python as well.

And between those two...

It depends on the person. Some people are interested in how cars work and eager to get under the hood and screw with their parts (C) while some people simply want to get behind the wheel and drive really fast (Python).

Neither is bad since either of them will eventually lead you to a decent understanding. Python gets you going somewhere quicker, but may leave you stranded in certain instances if you don't have a solid understanding of how things really work. C will teach you more about data types, memory, and how your program works... But you will likely spend a lot of time in the garage :)

My ultimate advice is to learn both, you just have to choose which end you want to attack it from.

---

### Post by RawMustard on 2007-08-15
Pythons nice, quick and easy to learn, but how do you protect it from theft?  I know we're on linux here and we all follow foss, but not all apps are suitable for release under an open source licence.  Particularly when you're making software for morons that want to steal and lock away anything they can.  Does anyone have any tips on protecting python code in such a situation.

Please excuse my ignorance if this is a dumb question, as I'm only learning to program and have just completed a special purpose program in an industrial application.  It was mostly all done in python.

---

### Post by LaRoza on 2007-08-15
> **RawMustard said:**
> Pythons nice, quick and easy to learn, but how do you protect it from theft?  I know we're on linux here and we all follow foss, but not all apps are suitable for release under an open source licence.  Particularly when you're making software for morons that want to steal and lock away anything they can.  Does anyone have any tips on protecting python code in such a situation.

Please excuse my ignorance if this is a dumb question, as I'm only learning to program and have just completed a special purpose program in an industrial application.  It was mostly all done in python.

You could compile it, if that is what you are asking.

---

### Post by RawMustard on 2007-08-15
Yeah I did that to byte code you mean? 

If so, a decompiler is just an apt-get install decompyle it's in the repos :(

---

### Post by Wybiral on 2007-08-15
> **RawMustard said:**
> Yeah I did that to byte code you mean? 

If so, a decompiler is just an apt-get install decompyle it's in the repos :(

I can reverse engineer programs written in C too... Mwa ha ha...

Then again... Anyone with a decent knowledge of assembly and a disassembler can. There is no way to 100% protect source code, but compiling makes it very hard to understand. I doubt the python bytecode still has meaningful labels (meaning it will be just as hard to read as disassembled C)...

I might be wrong, I've never messed with python bytecode (but I assume for the sake of program size that the labels are removed when compiled).

---

### Post by LaRoza on 2007-08-15
> **RawMustard said:**
> Yeah I did that to byte code you mean? 

If so, a decompiler is just an apt-get install decompyle it's in the repos :(

There is a way to compile it into an binary, but why are you so concerned about people seeing the source? Any one interested in looking at the code is more likely to improve it, rather than steal it. Actually, if they wanted to steal it, they would copy the program, with out caring about the source.

---

### Post by Hairy_Palms on 2007-08-15
yea but the point he was making is that the Boss doesnt always care about the source being improved, he just wants more cash, and the competition to not be able to look at it.

---

### Post by LaRoza on 2007-08-15
> **Hairy_Palms said:**
> yea but the point he was making is that the Boss doesnt always care about the source being improved, he just wants more cash, and the competition to not be able to look at it.

The competition would make less money trying to steal code than writing it. It is not worth the time and effort to crack others code. By the time they got it, they would be behind you, YOU WANT THEM TRYING TO STEAL YOUR CODE! 

Read: "The Cathedral and the Bazaar"

I am reminded of a Dilbert cartoon, which showed how ridiculous "the competition" is, they are just as clueless as your company.

---

### Post by batrick on 2007-08-15
> **aks44 said:**
> The whole top-down vs bottom-up argument... ;)

IMHO knowing how/when to *use* specific data structures or algorithms is way more important than how to implement them.

I'm not saying you should not bother with their implementation, just that it should not be your priority.


Just an architect's two cents though... (I know, I'm biased ;))

Implementation exposes misunderstanding.

---

### Post by jaybee99 on 2007-08-15
I don't know if the OP is listening but...I think python is a pretty good place to start (and definitely preferable to C++ or C# which will waste your time and damage your brain) but I'll put my two pennorth in and say you should consider scheme or another lisp. One of the main things that makes this a good idea is that it is truly multi-paradigm - you can write Object Oriented code, imperative style, functional style, learn about closures and continuations, "real" macros etc etc. A lot of this is not really possible, at least not in an elegant way, in python, c++ or c#. 

There are masses of great resources around to help with this, start at [www.drscheme.org](www.drscheme.org), and you'll learn a different way of looking at programming which to my mind is much more flexible and powerful than the typical imperative approach. You can move on from there to python/whatever later. Good luck!

---

### Post by pmasiar on 2007-08-15
> **jaybee99 said:**
> I don't know if the OP is listening but...I think python is a pretty good place to start (and definitely preferable to C++ or C# which will waste your time and damage your brain)

I agree that Python is good start, but disagree what C++/C# damages your brain - C++/C# are just *much* more pain to learn, so you will struggle unnecessary, and could burn out before learning to love programming (because time to develop anything in C++ will be 10 times of time in Python, especiall for a beginner).
 
> consider scheme or another lisp. One of the main things that makes this a good idea is that it is truly multi-paradigm - you can write Object Oriented code, imperative style, functional style, learn about closures and continuations, "real" macros etc etc. A lot of this is not really possible, at least not in an elegant way, in python, c++ or c#. 

Again I agree what C++/C# cannot do such things, but **Python can!**. You can use OOP, imperative and functional paradigm, has closures, all in much more understandable (readable and obvious) way than Lisp.

---

### Post by adityakavoor on 2007-08-15
python

---

### Post by SRX on 2007-08-15
Thanks for all of your guys advice

much appreciated

sincerly 

SR

---

### Post by bmeyer on 2007-08-15
> **jaybee99 said:**
> There are masses of great resources around to help with this, start at [www.drscheme.org](www.drscheme.org), and you'll learn a different way of looking at programming which to my mind is much more flexible and powerful than the typical imperative approach. You can move on from there to python/whatever later. Good luck!

Heh, I agree that Scheme is indeed powerful, but LISP languages for a beginner?!  ;)

The first post mentioned wanting to make GUIs.  I'd suggest trying Python with Tk -- Tk is relatively simple and seems to be a decent foundation for GUI coding.  Here's Python.org's guide to Tkinter:
[http://wiki.python.org/moin/TkInter]("http://wiki.python.org/moin/TkInter")

You might also try Perl with Tk...

---

### Post by tpg on 2007-08-15
I think I'll go against the trend here and recommend C/C++. C++ was my first language, and I have found it to be the most useful. I've found that most libraries are written with C/C++ in mind, and so tend to be easiest to use with those languages. While there are often wrappers for Python, you often have to "translate" the documentation from C to the equivalent python code(which I suppose means you would have to understand C to use that library with python).

The code can be portable (so long as the libraries are portable), but obviously you have to recompile the code on every platform you want to run the program on (Python clearly has an advantage here). I've dabbled with Python, admittedly not very much, but I just prefer C! :)

---

### Post by LaRoza on 2007-08-15
> **tpg said:**
> I think I'll go against the trend here and recommend C/C++. C++ was my first language, and I have found it to be the most useful. I've found that most libraries are written with C/C++ in mind, and so tend to be easiest to use with those languages. While there are often wrappers for Python, you often have to "translate" the documentation from C to the equivalent python code(which I suppose means you would have to understand C to use that library with python).

The code can be portable (so long as the libraries are portable), but obviously you have to recompile the code on every platform you want to run the program on (Python clearly has an advantage here). I've dabbled with Python, admittedly not very much, but I just prefer C! :)

I like/know C\C++ also, C++ was my first language. Learning Python first (just the basics) might have helped me, so learning both is a better end goal than one.

---

### Post by pmasiar on 2007-08-15
> **tpg said:**
> While there are often wrappers for Python, you often have to "translate" the documentation from C to the equivalent python code(which I suppose means you would have to understand C to use that library with python).

While you have valid point that most libraries are in C/C++, I bet that all libraries any beginner would like to use during her 1st year with Python have native ports with good documentation: [http://docs.python.org/lib/](http://docs.python.org/lib/) and [http://docs.python.org/modindex.html](http://docs.python.org/modindex.html) so your disclaimer does not apply for a beginner - ie you are saying this not from point of first-hand information, but as prejudice ;-D Or is any important library missing?

And many libraries have *much* simplified API thanks to Python's flexibility: ie [ElementTree](http://docs.python.org/lib/module-xml.etree.ElementTree.html) is *far* superior to any XML parser for 90% of work you may want to do.

---

### Post by sphim on 2007-08-15
I like C++ first because it's easier than C in the beginning, but it helps you learn C eventually. Also, its a lot easier to go from C++ to python than it is the other way around. Python is so nice and simple you get used to it, and don't learn all the annoying gotcha's in C++. Python is more forgiving than C++, so if you want it to be easy, start with Python, but if you want to be more versatile, start with C++.

---

### Post by NeillHog on 2007-08-15
Now that all the experts have had their say ...

Years ago I programmed in C on DOS
I tried C++ but gave up because it was WAY too complicated for my brain.

Four weeks ago I changed from Windows to Linux.
Last week I realised that a needed utility (wrapper for GPSBabel) was missing in Linux.
24 hours later I had the utility written and working nearly as I wanted. 

I used Python (out of the box on Kubuntu) to write a command line version and then Qt designer to create a GUI.

I am not sure if Qt reduces my portabilty (although I THINK that any one wanting to run my program would need it installed - I will be glad if some one can tell me I am wrong) but at the end of the day 24 hours to "learn" Python and Qt Designer and get the utility running is pretty impressive.

So my vote is for Python.

Neill

---

### Post by jaybee99 on 2007-08-15
> **pmasiar said:**
> I 
[...]
Again I agree what C++/C# cannot do such things, but **Python can!**. You can use OOP, imperative and functional paradigm, has closures, all in much more understandable (readable and obvious) way than Lisp.
What about macros? Also, a paradigm that can't be expressed in python is FP - having map, filter and list comprehensions doesn't cut it, there's more to FP than that.

---

### Post by jaybee99 on 2007-08-15
> **bmeyer said:**
> Heh, I agree that Scheme is indeed powerful, but LISP languages for a beginner?!  ;)

The first post mentioned wanting to make GUIs.  I'd suggest trying Python with Tk -- Tk is relatively simple and seems to be a decent foundation for GUI coding.  Here's Python.org's guide to Tkinter:
[http://wiki.python.org/moin/TkInter]("http://wiki.python.org/moin/TkInter")

You might also try Perl with Tk...

Perl, for a beginner? You're evil :)

---

### Post by slavik on 2007-08-15
> **LarsP said:**
> In a high level language you can focus on the mathematics/algorithm, without having to think too much about memory organization, variable typec etc.. 

and then it comes back to bite you in the ***. I know afellow student who implemented grover's algorithm in haskel that eats 4GB of RAM on a dual dualcore xeon system (with no way of freeing it in the middle of the program, since there is no memory) and a prof who is trying to parallelize his sudoku solver (also in haskel).

here are 2 examples, 1 in python, other in perl, I dare anyone tell me that perl is unreadable:

PERL:
```

use Math::BigInt;
$s = new Math::BigInt(1);
for $i(1..1000) { $s *= $i; }
print $s."\n";

```

PYTHON:
```

s = 1
for i in range(1,1000,1): s *= i
print s

```

---

### Post by pmasiar on 2007-08-15
> **jaybee99 said:**
> What about macros? Also, a paradigm that can't be expressed in python is FP - having map, filter and list comprehensions doesn't cut it, there's more to FP than that.

Well, of course it is not Lisp-like FP. But with python, beginner  also doesn't have to fight car/cdr, and finish code with exactly seven closing parentheses :-D.

Seriously, I let anyone write simple program to parse a data file: read file, ignore lines beginning with a '#', find ID part, data part, do some calculations. Simple in Python. Now do  same in Lisp.

---

### Post by slavik on 2007-08-15
now try to write AI code in python that can modify itself.

while we're at it, why not have a web server written in BASIC?

maybe even an OS written in haskel?

---

### Post by A-Sylum on 2007-08-16
I highly reccomend C++ for anything :D!! and for guis in C++ i use QT4 check out this site for graphical programming tips and tutorials

> [http://ubuntu-gamedev.wikispaces.com/](http://ubuntu-gamedev.wikispaces.com/)

it has a great QT4 tutorial which uses a gui and the C++ programming language in unison!!

---

### Post by pmasiar on 2007-08-16
> **slavik said:**
> now try to write AI code in python that can modify itself.

It is trivial, function reference is first-class object, you can pass it and assign it. Duck-typing helps too - important is not inheriting from special class, but presence of required method. And yes you can add attributes and methods on the runtime.

---

### Post by jaybee99 on 2007-08-16
> **slavik said:**
> now try to write AI code in python that can modify itself.

while we're at it, why not have a web server written in BASIC?

maybe even an OS written in haskel?
There is one, it's called House.

---

### Post by RawMustard on 2007-08-16
> **LaRoza said:**
> The competition would make less money trying to steal code than writing it. It is not worth the time and effort to crack others code. By the time they got it, they would be behind you, YOU WANT THEM TRYING TO STEAL YOUR CODE! 

WRONG!  In this case, the competition would make plenty of money without having to lift a finger.  The program in question is for a very specific niche market.  Others have tried to do what I have done but have not succeeded.  If I were to release my code open, I wouldn't see a dime for all my hard work and it is my living.

I don't care if someone looks at my program working and then copies it by writing something similar, then they have done some hard work, but to just grab the source and sell it on without my knowledge isn't going to happen easy I can give you the tip!

Like I said, not everything is suitable to be open sourced.
Also understand, that I do believe in FOSS greatly, but I'm also a realist!

---

### Post by LaRoza on 2007-08-16
> **RawMustard said:**
> WRONG!  In this case, the competition would make plenty of money without having to lift a finger.  The program in question is for a very specific niche market.  Others have tried to do what I have done but have not succeeded.  If I were to release my code open, I wouldn't see a dime for all my hard work and it is my living.

**I don't care if someone looks at my program working and then copies it by writing something similar**, then they have done some hard work, but to just grab the source and sell it on without my knowledge isn't going to happen easy I can give you the tip!

Like I said, not everything is suitable to be open sourced.
Also understand, that I do believe in FOSS greatly, but I'm also a realist!

Well, if you are not worried about them using the code by writing something similar, your argument doesn't make sense.

Binaries are just as easy to copy as source. You say you don't mind them using the source to write something similar, but mind them selling it as is, which doesn't require the source.

I am not saying you are wrong in your decision, or that you should do anything else, but that is how I (and others, far greater than I) see things.

---

### Post by RawMustard on 2007-08-16
I think you have missunderstod what I said or perhaps my writing wasn't clear enough.

If someone looks at my compiled working program as in when the user is using it and then goes off and tries to make a similar program, then good for them.  But I'm not going to make it easy for them by allowing them to see the source code to see how it works.  And I'm certainly not going to leave the source to my code on the machine so they can just copy as in copy and paste my own code and sell it on.

Does that make more sense? :)

This program does not run on a standard computer, it's in a machine and controlls the machines functions.

---

### Post by LaRoza on 2007-08-16
> **RawMustard said:**
> I think you have missunderstod what I said or perhaps my writing wasn't clear enough.

If someone looks at my compiled working program as in when the user is using it and then goes off and tries to make a similar program, then good for them.  But I'm not going to make it easy for them by allowing them to see the source code to see how it works.  And I'm certainly not going to leave the source to my code on the machine so they can just copy as in copy and paste my own code and sell it on.

Does that make more sense? :)

This program does not run on a standard computer, it's in a machine and controlls the machines functions.

I see now, I misinterpreted what you said. Thanks for clarifing. 

What does it do? (If you can tell me)

-EDIT This may help [http://effbot.org/pyfaq/how-can-i-create-a-stand-alone-binary-from-a-python-script.htm](http://effbot.org/pyfaq/how-can-i-create-a-stand-alone-binary-from-a-python-script.htm)

---

### Post by RawMustard on 2007-08-16
> **LaRoza said:**
> I see now, I misinterpreted what you said. Thanks for clarifing. 

What does it do? (If you can tell me)

-EDIT This may help [http://effbot.org/pyfaq/how-can-i-create-a-stand-alone-binary-from-a-python-script.htm](http://effbot.org/pyfaq/how-can-i-create-a-stand-alone-binary-from-a-python-script.htm)

Yeah sure, it's a HMI running under Ubuntu Feisty server to control the stitch settings on a carpet tufting machine.  The operator can create different patterns, run them and then save them for later use.  It controls 6 servo driven motors to control the stitch heights and rates.

Ubuntu will soon be making carpet for your home or whatever :)

---

### Post by LaRoza on 2007-08-16
> **RawMustard said:**
> Yeah sure, it's a HMI running under Ubuntu Feisty server to control the stitch settings on a carpet tufting machine.  The operator can create different patterns, run them and then save them for later use.  It controls 6 servo driven motors to control the stitch heights and rates.

Ubuntu will soon be making carpet for your home or whatever :)

Cool.

Is the carpet in the repos, or do you have to get it elsewhere :D.

---

### Post by RawMustard on 2007-08-16
Hehehe!

Wouldn't that be cool, apt-get install charcole-carpet-lounge :)

Now if I could just figure out why Ubuntu server won't let me execute pyc files :(

---

### Post by LaRoza on 2007-08-16
> **RawMustard said:**
> Hehehe!

Wouldn't that be cool, apt-get install charcole-carpet-lounge :)

Now if I could just figure out why Ubuntu server won't let me execute pyc files :(

Are they marked as executable, does the server know that .pyc are to be opened with python?

---

### Post by RawMustard on 2007-08-16
> **LaRoza said:**
> Are they marked as executable

yes.

> does the server know that .pyc are to be opened with python?

Ahah, how would I check that?  I just naturally assumed it would?

see this thread for more info.
[http://ubuntuforums.org/showthread.php?t=526865]("http://ubuntuforums.org/showthread.php?t=526865")

---

### Post by pmasiar on 2007-08-16
guys stop hijacking this thread, switch to proper thread

---

### Post by emperon on 2007-08-16
Learn Boo.

1-) It works on mono. And mono is default installed in gnome 
2-) Its syntax is pythonic
3-) It supports both dynamic and static typing. Best of both worlds!
4-) It supports macros. This makes boo even more powerful than ruby
5-) You have the full power of .NET framework. You can develop ASP.NET applications , Distributed Applications via SOAP and remoting. Windows Forms applicaitions with full portability.
6-) You can use full persistence layers like db4o and NHibernate.
7-) You can use unit testing frameworks nunit and mock objects library like rhinomocks.
8-) It can cooperate with any .net language
9-) You also have full power of all java frameworks via IKVM.
10-) Your applications will work out of box on windows and gnome based distros. Without any extra runtime installed.
11-) .NET can languages can use P/Invoke , meaning you can call your native compiled code if necessary

nough said...

---

### Post by vexorian on 2007-08-16
> Without having any actual experience with C#, I hear that it combined with .NET is a great platform. I wouldn't be so quick to dismiss it just because it's produced by Microsoft.

I would.

Do you know what happens with MONO? Everytime someone makes a C# program with mono he is using open source and all, but he is also promoting MS' platform.

This causes other people to use MS' platform... But what's the problem there? C# and .net 2.0 are full of other features that MONO is years away of implementing. So most users will get advertised to stay on .net and the advertiser would be MONO.

And what's wrong with .net ? Microsoft's .net only works correctly on windows.

And provided MONO finally implemented 2.0 correctly, MS will only have to release a new version, and if MONO got so good it always implemented things as fast, MS can just drop the 'promise not to sue' and screw all MONO projects.

---

So:
C++ : A lot of concepts that might help you later (regarding memory usage and strings mainly).
Python : you instantly begin to program, but it gets a problem it will make it very hard to learn other languages later.

so the question is, do you want to learn to program or to begin to code?

In my opinion you shouldn't begin with **a** language, you should try learning plenty of languages at the same time (aka don't wait to finish learning a language before starting to learn another)

---

### Post by emperon on 2007-08-16
> **vexorian said:**
> 

Do you know what happens with MONO? Everytime someone makes a C# program with mono he is using open source and all, but he is also promoting MS' platform.


Fact: Ubuntu already has mono installed by default. When you write a C# program you don't promote MS. You are just using an open source framework.
In your case, when people use java they promote SUN and when they use QT they promote Trolltech. We discuss the technology here. And MS has nothing to do with this.

> **vexorian said:**
> 
This causes other people to use MS' platform... But what's the problem there? C# and .net 2.0 are full of other features that MONO is years away of implementing. So most users will get advertised to stay on .net and the advertiser would be MONO.


Don't spread FUD for the stuff that you don't know. Mono is not years away from .net

FACT: ASP.NET 2.0 100% implemented except Web Parts
FACT: Windows Forms 1.1 100% implmented
FACT: Windows Forms 2.0 is mostly implemented
FACT: .NET framework 2.0 including generics is all implemented except File.Security and CAS stuff
FACT: C# 3.0 is implemented on mono except LINQ (there is a test release of LINQ built in 2006)

> **vexorian said:**
> 
And what's wrong with .net ? Microsoft's .net only works correctly on windows.


FACT: .NET Applications work perfectly on Linux, Mac and windows. (Except some windows forms 2.0 applications can have glitches).
PROOF: The following frameworks/applications are not designed for  linux but they are complex and yet they work on mono flawlessly: NHibernate, Castle Project, ASP.NET, NUNIT, DB4O , Reflector (Windows forms with minor glitches), log4net, Rhino Mocks


> **vexorian said:**
> 
And provided MONO finally implemented 2.0 correctly, MS will only have to release a new version, and if MONO got so good it always implemented things as fast, MS can just drop the 'promise not to sue' and screw all MONO projects.


FACT: C# is a ECMA Standard Language. Microsoft has no right to sue anyone for using C#. Because they don't own C#. They can only claim right on Windows Forms or windows specific stuff. As miguel explained if MS claims royalty for Windows Forms, Mono will drop the support for windows forms and yet it will still be a good project. 



I am using linux since 2000. And along with Python, I consider mono as one of the greatest things ever happened. The need for mono comes from miguel's explanation. He said evolution the email client on linux , it took 2 years to develop it. And at that time Python GTK bindings were not available.  And C/C++ bindings for GTK suck. This is why they considered Mono as an alternative.

You may like it. Or you don't like it. That's a personal taste. However one should first learn the FACTS before spreading FUD.  Otherwise he or she would be doing  more harm than good.

---

### Post by pmasiar on 2007-08-16
> **vexorian said:**
> And provided MONO finally implemented 2.0 correctly, MS will only have to release a new version,

MSFT already did released .NET 3.0: [http://en.wikipedia.org/wiki/.NET_Framework](http://en.wikipedia.org/wiki/.NET_Framework) even *before* Mono reimplemented full 2.0 :-)

> Python : you instantly begin to program, but it gets a problem it will make it very hard to learn other languages later.

Why hard? The only reason I can see is hard to understand why all other languages are so crufty and verbose and overcomplicated, hard to accomplish anything once you are spoiled by convenience of Python. 

It's not like with Python you learn some bad habits or anything. Python is just more helpful, and when coding in say C++ after Python, you have to handle in your code many minor and irritating details which python handles for you. Which gives you more opportunity to do it wrong, raising interesting bug, so you have more fun debugging it, and even more learning opportunities :-)

---

### Post by pmasiar on 2007-08-16
> **emperon said:**
> 
FACT: C# is a ECMA Standard Language. Microsoft has no right to sue anyone for using C#. Because they don't own C#. They can only claim right on Windows Forms or windows specific stuff. 

Patents might be not in C# compiler, but in library calls. Nobody knows and MSFT is not telling - patent FUD has goal to make Linux platform less certain.

As free software developer, you probably don't care - you are too small a fish, and too deep pockets to get any fine off you. Big companies, like Novell, have own patents to retaliate, just in case. Danger is for small for-profit companies, which might be either sued into oblivion, or sued and forced to sell cheaply to MSFT.

> You may like it. Or you don't like it. That's a personal taste. However one should first learn the FACTS before spreading FUD.  Otherwise he or she would be doing  more harm than good.

It is foolish to rely on programmer for law patent opinion, exactly as you wound not ask your lawyer for opinion on rapid web app development technology :-)

---

### Post by emperon on 2007-08-16
> **pmasiar said:**
> MSFT already did released .NET 3.0: [http://en.wikipedia.org/wiki/.NET_Framework](http://en.wikipedia.org/wiki/.NET_Framework) even *before* Mono reimplemented full 2.0 :-)


Then you should learn .NET 3.0 name is a marketing strategy that brings nothing to the table. Unlike .NET 1.1 and .NET 2.0 difference , .NET 3.0 does not make any change to runtime or compiler. The difference between .NET 3.0 and .NET 2.0 are the following addons: Windows Presentation Foundation (Available in Mono/olive)
Windows WorkFlows(Avaiabile in Olive) and Windows Communication Foundation (Available in Mono/Olive)

The link for Olive is : [http://www.mono-project.com/Olive](http://www.mono-project.com/Olive)

Apparently these are just some addons to .NET library. And yet they are not even widely used in windows world as well. Furthermore, Mono people consider  some of those libraries harmful as J2EE, so they avoid/don't hurry to implement it.

Finally the next real .NET version is .NET 3.5 which effectively changes the compiler (mostly using C# 3.0). And a I said C# 3.0 is already built in current mono releases

---

### Post by emperon on 2007-08-16
I may be a programmer but I can understand what I read. I needn't to be a lawyer.

Direct paste from :[http://www.mono-project.com/FAQ:_Licensing]("http://www.mono-project.com/FAQ:_Licensing")

 Patents
Could patents be used to completely disable Mono?

First some background information.

The .NET Framework is divided in two parts: the ECMA/ISO covered technologies and the other technologies developed on top of it like ADO.NET, ASP.NET and Windows.Forms.

Mono implements the ECMA/ISO covered parts, as well as being a project that aims to implement the higher level blocks like ASP.NET, ADO.NET and Windows.Forms.

The Mono project has gone beyond both of those components and has developed and integrated third party class libraries, the most important being: Debugging APIs, integration with the Gnome platform (Accessibility, Pango rendering, Gdk/Gtk, Glade, GnomeUI), Mozilla, OpenGL, extensive database support (Microsoft only supports a couple of providers out of the box, while Mono has support for 11 different providers), our POSIX integration libraries and finally the embedded API (used to add scripting to applications and host the CLI, or for example as an embedded runtime in Apache).

The core of the .NET Framework, and what has been patented by Microsoft falls under the ECMA/ISO submission. Jim Miller at Microsoft has made a statement on the patents covering ISO/ECMA, (he is one of the inventors listed in the patent): here ([http://web.archive.org/web/20030424174805/http://mailserver.di.unipi.it/pipermail/dotnet-sscli/msg00218.html](http://web.archive.org/web/20030424174805/http://mailserver.di.unipi.it/pipermail/dotnet-sscli/msg00218.html))

Basically a grant is given to anyone who want to implement those components for free and for any purpose.

For people who need full compatibility with the Windows platform, Mono's strategy for dealing with any potential issues that might arise with ASP.NET, ADO.NET or Windows.Forms is: (1) work around the patent by using a different implementation technique that retains the API, but changes the mechanism; if that is not possible, we would (2) remove the pieces of code that were covered by those patents, and also (3) find prior art that would render the patent useless.

Not providing a patented capability would weaken the interoperability, but it would still provide the free software / open source software community with good development tools, which is the primary reason for developing Mono.

The patents do not apply in countries where software patents are not allowed.

For Linux server and desktop development, we only need the ECMA components, and things that we have developed (like Gtk#) or Apache integration.
With the new Novell/Microsoft agreement, will the patent policy change?

Mono is a community project, and as such, we will continue to implement the policy of not integrating knowingly infringing code into Mono.

And we will continue to follow the steps outlined in the previous topic if code that potentially infringes is found: finding prior art, finding different implementation techniques, or if none of those are possible, removing the code from Mono.

---

### Post by motang on 2007-08-16
I would suggest C++ or Java but that is because that is what my school teaches, but I am interested in Python.

---

### Post by pmasiar on 2007-08-16
> **emperon said:**
> I may be a programmer but I can understand what I read. I needn't to be a lawyer.

As i said, self-help is OK for single open-source developer, but for a company it is *NOT* sufficient.


> And we will continue to follow the steps outlined in the previous topic if code that potentially infringes is found: finding prior art, finding different implementation techniques, or if none of those are possible, removing the code from Mono.

I am perfectly fine with that. It even admits that some features might have to be dropped, and everyone is fine with that.

But I am asking - "why C#/.NET? " Does it have something special which is missing in GNU/Linux world? Why I would want to waste years of my life learning intricacies of .NET libraries?

---

### Post by SRX on 2007-08-16
maybe we should create a poll and then we can see whether python or C++ is better when starting programming

---

### Post by Wybiral on 2007-08-16
> **SRX said:**
> maybe we should create a poll and then we can see whether python or C++ is better when starting programming

Python obviously :) (and I'm mainly a C++ programmer)

The real question is whether Python or C are better for a beginner.

But, I've said it before... It depends on the person and their intentions.

---

### Post by emperon on 2007-08-16
> **pmasiar said:**
> As i said, self-help is OK for single open-source developer, but for a company it is *NOT* sufficient.


But I am asking - "why C#/.NET? " Does it have something special which is missing in GNU/Linux world? Why I would want to waste years of my life learning intricacies of .NET libraries?

Appereantly if mono project is dropped, it won't be a big problem for GNU Linux community. But same is true for Python, Ruby and Java. I am well aware that there are tremendous amount of python applications and a lot of devs on that. But no! The core of linux is only C based programs alone.

For the answer of your question remember why mono emerged in the first case. There were no python GTK bindings, and C/C++ development sucks. (C++ although is a widely adopted industry standard, it is the most pointless lanaguage ever for me)..

Programming languages are tools. And they give us some abstraction level. I would classify :

Language....................... Abstraction Level

Machine Lang........................ 0
Assembly.............................. 1
C/C++  ................................... 2
Java/C# .................................3
Python, Ruby .........................4
LISP ...................................infinity

We choose a language according the to task and level of abstraction we require. Writing an operating system with LISP is pointless where as, writing an ERP with assembly is pointless as well.

Most Projects fall into the category between level 4 and 3. The main difference between level 4 and 3 is about statically typing or dynamic typing.

With statically typed languages you have compiler as a cop , that checks your code for preliminary compile time mistakes. This is more useful when the project is very large and iti hard to maintain and/or the developers are novice.

With dynamic languages, the language gives the developer more power (at the cost of Performance) , so it is more suitable for when developers are smarter and/or Project is not very large to maintain.

What .NET brings table, this is highly personal. Mono (and not .NET) is the best of the best of all development environments FOR ME. because of the following reasons:

1-) You have bunch of languages with dynamic and static typing that can interop: C#, VB.NET(it sucks I know), Boo (a statically typed language allowing dynamic typing), IronPyton, IronRuby(alpha available),Ruby.NET (Beta availbale), F# (first class functional language) and a lot of less popular ones like nemerle, lispdotnet, prolog.net...

2-) .NET framework is available in windows and gnome by default. Have you ever tried to deliver a python application to your customer who knows nothing about  computers ? You cannot instruct them to install python easily. Even if you can sometimes deployment of 1000 computers are problematic. Most XP and all Vista computers already has .NET framework so it is easier to deploy cross platform applications

3-) java is the most popular language now  according to TIOBE index: [http://www.tiobe.com/tpci.htm]("http://www.tiobe.com/tpci.htm") But popularity does not make a language good (For eg. VB). Although .NET especially c# is highly inspired of java ( the reason C# was born because sun sued Microsoft for Visual J++), for many years, Sun's over protective behavior of java, damaged java community a lot. If you check the bug list of java you will see there are 3 - 4 years standing bugs. GUI development with java sucks.Although Sun recenlty Open sourced java recently , as everything Sun did so far, it is too little and too late. Java is destined to go where PHP and Cobol lies now

4-) Web Development with mono is breeze. What other choices we have ? 
Java based framworks (look at item 3), PHP (is already dead), Ruby on Rails (this is a very nice framework but sorry not suitable for large applications, No unicode, no multithreading), Pythonic Frameworks like Django and Turbo Gears, these are also very nice but they are even worse than RoR. Still very nice for small to medium web development

5-) .NET library is large. Python library is also large, and available C librarires are huge. But with .NET you got all in one

6-) You've got the power of frameworks written for windows, like nhibernate, spring.net, db4o, nunit ...

7-) You've got the power of Java frameworks via IKVM. IKVM is a Java VM which can run on mono

8-) Although it is Alpha, we've got Silverlight/moonlight: [http://www.mono-project.com/Moonlight]("http://www.mono-project.com/Moonlight")

Note that I am not claiming Mono is better than Python.
These are my opinions what for Mono brings to the table

---

### Post by slavik on 2007-08-16
> **emperon said:**
> ... And at that time Python GTK bindings were not available.  And C/C++ bindings for GTK suck. This is why they considered Mono as an alternative.

C bindings for GTK suck? (I will refrain from personal attacks)

---

### Post by gnuman on 2007-08-16
> **SRX said:**
> maybe we should create a poll and then we can see whether python or C++ is better when starting programming

Make sure to post the poll on some other forums, though--not just the Ubuntu forums. :)  This is probably a biased audience (myself included).

I switched to the Ubuntu distro because it is very Python-friendly (many distros don't have the latest version of Python).  

Well, for that reason and the Nelson Mandela video.....:popcorn:

---

### Post by pmasiar on 2007-08-16
> **SRX said:**
> maybe we should create a poll and then we can see whether python or C++ is better when starting programming

... giving exactly same amount of credibility to opinion of [world-famous language expert](http://en.wikipedia.org/wiki/Bruce_Eckel) and "wannabe experts" [like](http://ubuntuforums.org/showthread.php?t=523433)
[this](http://ubuntuforums.org/showthread.php?t=521908)?

No: this is not democracy, this is meritocracy. You need to earn the right to be listened to. You need to prove sound judgment, **then** we will listen.

Of course fools are free to listen to opinions of other fools :-)

---

### Post by pmasiar on 2007-08-16
I mostly agree with you. here are some differences:

> **emperon said:**
> 
LISP ...................................infinity

It is [well know fact](http://xkcd.com/224/) that real hacker hack in Perl :-)

> The main difference between level 4 and 3 is about statically typing or dynamic typing.

You miss garbage collection - in fact you are so used to it you forgot (or did not knew) how hard life was without GC.

You also missed coming paradigm shift in programming [agile](http://en.wikipedia.org/wiki/Agile_software_development) and [Test-driven development](http://en.wikipedia.org/wiki/Test-driven_development), where flexible dynamic "glue" language is used, and strong testing catches more errors than strong typing ever can.

> With dynamic languages, the language gives the developer more power (at the cost of Performance) , so it is more suitable for when developers are smarter and/or Project is not very large to maintain.

Some **very** big projects were made in Python. Some other languages have different quirks, like too eager type coercion: in Perl , "1" + 2 is valid, value is 3. Python is strictly typed and it is invalid. Java/C# errs to the other side :-)

> 1-) You have bunch of languages with dynamic and static typing that can interop: C#, VB.NET(it sucks I know), Boo (a statically typed language allowing dynamic typing), IronPyton, IronRuby(alpha available),Ruby.NET (Beta availbale), F# (first class functional language) and a lot of less popular ones like nemerle, lispdotnet, prolog.net...

Yup, I am afraid that MSFT is the only company which gets it: In the future, you need **seamless** integration between dynamically typed "glue" language to for flexible and [agile](http://en.wikipedia.org/wiki/Agile_software_development) application development, and strictly statically typed language for highly optimized libraries.

Sun certainly does not get it until recently: they allowed author of Jython (Python for JVM) be snatched by MSFT to work on IronPython.

> 2-) .NET framework is available in windows and gnome by default. Have you ever tried to deliver a python application to your customer who knows nothing about  computers ? You cannot instruct them to install python easily. 

Python is installed by default on Linux: installation is MSFT/windows problem ;-)

> 3) ...as everything Sun did so far, it is too little and too late. Java is destined to go where PHP and Cobol lies now

Yup, 100% agree. C# is what Java should have been.

> 4-) Web Development ... Django and Turbo Gears, these are also very nice but they are even worse than RoR. Still very nice for small to medium web development

TurboGears and especially Pylons (another framework) scales up very, very good. Much better than Ruby.
Why? because of many smart Python programmers have competing ideas, and with agile language it is easier to implement them and learn from mistakes (easier than ie Java: Struts is nightmare to learn, does not scale down at all).

> 5-) .NET library 6-) frameworks 

They are different, incompatible versions of what free software has. Even 30K MSFT programmers cannot beat creativity of free software developers.

fair opinion, .NET is neck-to-neck with other 2 platforms: Java and LAMP. Java looks like stumbled, but my bet will be on creativity of free software. 10 years from now, millions hackers raised by $100 laptop will be looking for opportunity - and they never touched windows-based PC. Most of the growth will be outside of the USA, that's why it is not visible yet. India has about 4 times USA population, China 6 times, and no legacy code to maintain.

---

### Post by slavik on 2007-08-16
> **pmasiar said:**
> 2-) .NET framework is available in windows and gnome by default. Have you ever tried to deliver a python application to your customer who knows nothing about  computers ? You cannot instruct them to install python easily.

.net != mono

as for installing python easily, if there is a python setup program that can do an unattended install (decent defaults and no prompts), then you can simply run it as part of your own install.

when I used gaim on windows, it would include the gtk+ as part of the install and promt me to install a newer version. you don't even need to do that (or something like,this program needs python to run, would you like to install it?)

look at some windows games that require directx ... they distribute directx along with their stuff and give an option to install it.

---

### Post by pmasiar on 2007-08-16
> **slavik said:**
> .net != mono

You quoted me as saying "2-) .NET framework...". Actualy, emperon said that and I forgot to quote him properly. It is fixed now. My bad.

> as for installing python easily, if there is a python setup program that can do an unattended install (decent defaults and no prompts), then you can simply run it as part of your own install.

I prefer developing and not installing so I am not installation expert... :-) But ie. Turbogears installs easily and unattended, new eggs format is IMHO very flexible.

> look at some windows games that require directx ... they distribute directx along with their stuff and give an option to install it.

I had my portion of Windows installing problems when I worked in PC support company: installing a program can overwrite version of DLL some other program depends on, so some error appears only if you install packages in a given order. No, thanks, I prefer dependency tracking like debian does.  It did not happened to you, you are the lucky one.

---

### Post by slavik on 2007-08-16
well, I never install directx (the reason that one was properly cut is because I went to advanced mode).

but the thing is, before gaim installs newer gtk, it run the uninstall of the older one. and if whatever you are installing/uninstalling (not your stuff, but stuff your stuff needs) is designed properly, there shouldn't be any problems, I've also had checkinstall generate packages that wanted to replace things like /usr/bin/ld ... (using the "proper" method generated a package that wanted to replace another file considered to be belonging to something under ubuntu-desktop umbrella)

---

