---
title: "What's Good about Dynamic Typing?"
date: 2005-11-16
forum: Programming Talk
---

### Post by Ubuntist on 2005-11-16
An incorrect claim I made about Python not having type checking in another thread ([http://www.ubuntuforums.org/showthread.php?t=88859](http://www.ubuntuforums.org/showthread.php?t=88859)) lead several to point out that Python has dynamic typing.

As Van Gogh pointed out, Python's use dynamic typing makes it very slow for recursion.  And it seems to me that dynamic typing, by allowing "x=3" followed by "x='Fred'", doesn't flag errors that could be caught.

But there must be some advantages of dynamic typing.  What are they?

---

### Post by jrbj on 2005-11-16
> **Ubuntist]An incorrect claim I made about Python not having type checking in another thread ([http://www.ubuntuforums.org/showthread.php?t=88859](http://www.ubuntuforums.org/showthread.php?t=88859)) lead several to point out that Python has dynamic typing.

As Van Gogh pointed out, Python's use dynamic typing makes it very slow for recursion.  And it seems to me that dynamic typing, by allowing "x=3" followed by "x='Fred'", doesn't flag errors that could be caught.

But there must be some advantages of dynamic typing.  What are they?[/QUOTE]

The main advantage is productivity said:**
> http://www.mindview.net/WebLog/log-0025[/url]
[QUOTE=Bruce Eckel]
After I had worked with Python (free at [www.Python.org](www.Python.org)) for awhile &#8212; a language which can build large, complex systems &#8212; I began noticing that despite an apparent carelessness about type checking, Python programs seemed to work quite well without much effort, and without the kinds of problems you would expect from a language that doesn't have the strong, static type checking that we've all come to "know" is the only correct way of solving the programming problem.

This became a puzzle to me: if strong static type checking is so important, why are people able to build big, complex Python programs (with much shorter time and effort than the strong static counterparts) without the disaster that I was so sure would ensue? 

The answer here -- and I'm simplifying this quite a bit -- is that static typing is less important than strong testing. After all, static typing is basically a form of testing that happens at compile time.

Python allows programmers to rapidly build automated unit-tests that can exhaustively check the 'correctness' of the program. Again, this can be done quickly and with much less effort. The importance of this ease can't be emphasized enough.

---

### Post by Ubuntist on 2005-11-17
Thanks, that is very interesting.  I read Bruce Eckel's piece and another referenced within it.  I can believe now that I've overestimated the value of static typing, but I'm still not convinced that we're better off without it.  Don't we get the flexibility of dynamic typing and the added safety of static typing by simply allowing a generic type for those occasions when what we really want is dynamic typing?

---

### Post by dogen on 2005-11-17
> **jrbj]The main advantage is productivity said:**
> 
The answer here -- and I'm simplifying this quite a bit -- is that static typing is less important than strong testing. After all, static typing is basically a form of testing that happens at compile time.

This is a good point - static typing is a form of testing that happens at compile time. But.. Take that away and you shift the testing to post-compile - meaning you have to test the crap out of your program formally and informally if you're writing production code and not just a throw-away script. So I'm not sure the productivity boost really holds in real life. 

As much as I like Python, sometimes it's like programming in old VB with "Option Explicit" off. Every typo invisibly becomes a new variable. Does 3 / 4 = 0 or = 0.75? Ouch. "Agile" languages are cool and useful, but... keep it real.

---

### Post by gord on 2005-11-18
you don't _have_ to test everything though, python has great exepction handling so you can only test things when they are needed. which, most of the time, they are not.

i have to say, the main reason i beleve python does not have static typing is because it doesn't need to, its interpreted and they take advantage of that fact. it meens you can make more dynamic programs and code and not be restricted so much. allthough it does have its fair share of restrictions, its still a developing language. 

n about the 3/4 thing, in python any number without a decimal point is an integer number, put a decimal point in one and its a float and so the resulting number will be. 3/4 = 0. you have to learn a languages in's and outs before you can take real advantage ;) 

also, i apollogise for the typo's n stuff in this post, its very very very cold...

---

### Post by Van_Gogh on 2005-11-18
I have never experinced any problem using dynamic typing in Python, maybe partly because of the way I(and I think most people) program in Python - by running your program and see if everything works as planned. If something goes wrong, you always get a very(very!) nice error output that tells you what went wrong. No mysterious segmentation faults that just break your program, just a nice statement saying what went wrong. 

Also, segmentation faults overflows show that you in no way are safe, just because you use static typing: mistakes are an inherant property of all programming and you are not safe because you use tstic typing. However, a good, clean programming language makes it easy for you to correct your bugs, when they happen. Python does that, IMHO. 

Static typing is IMO more useful to the compiler than the programmer: it helps the compiler to arrange your code in a more efficient manner than is possible with dynamic typing and makes the code run faster. The programmer doesn't need it: if he's in doubt about an object's type, he just goes to the interactive promt and writes

type(object)

and you get the object's type. Easy as pie. If the object has a doc-string you can also do

object.__doc__

and you get human-readable text that explains what the object does. Pure bliss!

Oh, just fot the record: if I didn't mentioned it earlier: Python doc-strings rule:cool:

[QUOTE=dogen]This is a good point - static typing is a form of testing that happens at compile time. But.. Take that away and you shift the testing to post-compile - meaning you have to test the crap out of your program formally and informally if you're writing production code and not just a throw-away script. So I'm not sure the productivity boost really holds in real life. 
[/QUOTE]
And you don't test post-compile in compiled languages? Of course you do, there's not a difference there.

Oh, and you don't compile per se in Pyhon - that's one thing that makes it so great, no save-compile-run to test, just a faster save-run cycle. Agile development in its pure form. It's beautiful:-)


[QUOTE=dogen]
Does 3 / 4 = 0 or = 0.75? Ouch. "Agile" languages are cool and useful, but... keep it real.[/QUOTE]

3/4 = 0 because the equation only contains integers. Basic rule of Python. On the other hand, 3./4 = 0.75, (a float)because there's at least one float in the equation. Also basic rule of Python. Finally, it's always possible to do an conversion so: int(3./4) = 0, if that's what you want...

regards

---

### Post by Ubuntist on 2005-11-18
I think I'm just going to have to try using Python or Ruby for a sizeable (by my low standards, at least) project and see how well I do with dynamic typing.  For the moment I just can't see why I wouldn't miss static typing at least a little bit, but maybe I will be surprised.

By the way, why is there such a dichotomy between interpreted and compiled languages?  Could one not have a language that is both?  Code would usually be interpreted, but once it had been finalized, those parts which accounted for substantial portions of the execution time could be compiled.  That would give us the best of both worlds.  Python already goes part of the way with its ability to include code segments in other languages, which I presume are compiled.  And in the distant past I remember a Pascal under BSD Unix that allowed both interpretation and compilation.

---

### Post by Van_Gogh on 2005-11-18
[QUOTE=Ubuntist]I think I'm just going to have to try using Python or Ruby for a sizeable (by my low standards, at least) project and see how well I do with dynamic typing.  For the moment I just can't see why I wouldn't miss static typing at least a little bit, but maybe I will be surprised.[/QUOTE]

May I ask what you're planning on doing? I'm starting to get a little bit curious...

You seem a bit preoccupied with speed(depending on what you want to do, a valid concern with interpreted languages) and about dynamic typing(I don't think you need to worry abour it).

[QUOTE=Ubuntist]
By the way, why is there such a dichotomy between interpreted and compiled languages?  Could one not have a language that is both?  Code would usually be interpreted, but once it had been finalized, those parts which accounted for substantial portions of the execution time could be compiled.  That would give us the best of both worlds.  Python already goes part of the way with its ability to include code segments in other languages, which I presume are compiled.  And in the distant past I remember a Pascal under BSD Unix that allowed both interpretation and compilation.[/QUOTE]

In principle I think you could have a language that is both, but I think it would have to be statically typed to give the compiler a chance to do its thing.

BTW, if you are going to go with Python, I recommed iPython as your interactive promt(it's in the repositories). It's really great and is one of the reasons why I like Python so much...

---

### Post by LordHunter317 on 2005-11-19
> **jrbj]Python allows programmers to rapidly build automated unit-tests that can exhaustively check the 'correctness' of the program.[/quote]Testing via unit-test is much harder than via static-typing.  Compilers can be written to always give 100% assurance that the types are correct said:**
> Again, this can be done quickly and with much less effort. The importance of this ease can't be emphasized enough.It's never been shown to me or by anyone that it's demonstrably less than in a statically-typed language.

> **gord]t meens you can make more dynamic programs and code and not be restricted so much.[/quote]Static typing isn't a restriction though, not anymoreso than the rules of predicate logic or lambda calculus are in logic.

That's ignoring the fact most (All?) staticly-typed languages let you override the type system if you chose.

[quote=Van_Gogh]Also, segmentation faults overflows show that you in no way are safe, just because you use static typing: mistakes are an inherant property of all programming and you are not safe because you use tstic typing.[/quote]Too bad this response is a non-sequitur.  The fact that programs written in C can have buffer overflows has no relation to the fact they're statically typed.  It can't, by definition.

> Static typing is IMO more useful to the compiler than the programmer: it helps the compiler to arrange your code in a more efficient manner than is possible with dynamic typing and makes the code run faster.No, it doesn't.  C discards the type information completely said:**
> type(object)

and you get the object's type. Easy as pie. If the object has a doc-string you can also do

object.__doc__

and you get human-readable text that explains what the object does. Pure bliss!Neither of which are solely features of dynamically typed languages.

[quote=Ubuntist]By the way, why is there such a dichotomy between interpreted and compiled languages? Could one not have a language that is both? Code would usually be interpreted, but once it had been finalized, those parts which accounted for substantial portions of the execution time could be compiled.[/quote]Python is both.  Most functional languages are both.  C and Java are both, if you try hard enough.

[quote=Van_Gogh]In principle I think you could have a language that is both, but I think it would have to be statically typed to give the compiler a chance to do its thing.[/quote]This shows a grave misunderstanding about what compilers do.

---

### Post by Ubuntist on 2005-11-20
[QUOTE=Van_Gogh]May I ask what you're planning on doing? I'm starting to get a little bit curious...
[/QUOTE]
Nothing fantasically unusual.  For starters, I want to do some basic studies of single-stage-to-orbit launch vehicles and understand the trade-offs in their design.  That means integrating the equations of motion from the ground to orbit subject to boundary conditions.

> 
You seem a bit preoccupied with speed

I would guess that for what I'm doing in the short term, speed isn't going to be that much of an issue.  Certainly for some simulations I did in the distant past, though, it was a major issue.

---

