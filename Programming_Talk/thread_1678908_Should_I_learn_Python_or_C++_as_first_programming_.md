---
title: "Should I learn Python or C++ as first programming language?"
date: 2011-01-31
forum: Programming Talk
---

### Post by tuahaa on 2011-01-31
First of all, I have NO EXPERIENCE in programming. At all. I want to learn a programming language- and I was going to learn C++ (started with the "hello world" bit) but I just read that Python is much simpler and good for people who are total noobs.

In the end, I'd like to be able to make complex 2d games for linux- I understand that might take years to learn it all and make something good. I want programming as a hobby and not as a carreer. I also won't have too much time to spend on it as I'm 15 and studies are bound to get tougher.

So, do you suggest Python?

---

### Post by CaptainMark on 2011-01-31
I found python so easy to pick up, i learnt from this book [http://www.amazon.com/Python-Programming-Absolute-Beginner-3rd/dp/1435455002/ref=sr_1_3?ie=UTF8&qid=1296474366&sr=8-3](http://www.amazon.com/Python-Programming-Absolute-Beginner-3rd/dp/1435455002/ref=sr_1_3?ie=UTF8&qid=1296474366&sr=8-3)3 once youve learnt the theories and ideas from python then i found it really easy to pick up c and java because the basics are the same you just have to learn the syntax

---

### Post by fct on 2011-01-31
Yeah, easier than C++ and hence better to learn programming.

I learnt with Pascal, which I really enjoyed and was designed for students. Unfortunately it's not as extended as Python nowadays.

---

### Post by giowck on 2011-01-31
Go with Python... It's awesome for hobby-style programming :)

I personally love C++, it's powerful and flexibe but the learning curve is very long.

---

### Post by Nytram on 2011-01-31
For writing a game I'd personally go with C++ for its speed.

---

### Post by Simian Man on 2011-01-31
> **tuahaa said:**
> So, do you suggest Python?
Yes, and once you're comfortable with it, I suggest [PyGame]("http://www.pygame.org").

> **giowck said:**
> I personally love C++, it's powerful and flexibe but the learning curve is very long.
How is C++ more powerful and flexible than Python???  That's the polar opposite of how I'd compare these two languages!

> **Nytram said:**
> For writing a game I'd personally go with C++ for its speed.
With a game, almost all of the time will be spent in library code: graphics, audio, networking etc.  And almost all Python libraries are written (mostly) in C.  So using Python for the game code doesn't hurt performance much and increases programmer efficiency.  Besides it doesn't sound like he's going after a AAA next-gen blockbuster does it?

---

### Post by Zugzwang on 2011-01-31
> **Simian Man said:**
> How is C++ more powerful and flexible than Python???  That's the polar opposite of how I'd compare these two languages!

Note that giowck didn't write that Python is *more* powerful or *more* flexible than Python. He just wrote that C++ is powerful and flexible, without any comparison. And depending on the type of projects you are doing, that is a valid point.

---

### Post by V for Vincent on 2011-01-31
The speed thing isn't quite as relevant as it might seem. There are engines out there (e.g. Panda3D) made for Python scripting.

I'm currently picking up Python myself and, while I have my doubts about certain aspects of the language, I would certainly suggest it over C++.

---

### Post by Nytram on 2011-01-31
> **Simian Man said:**
> Yes, and once you're comfortable with it, I suggest [PyGame]("http://www.pygame.org").


Have you seen games that use pygame, or have you written one yourself?

I've done both, and the results aren't very impressive. Sure my code was inefficient and it was run on a low spec netbook, but it was a simple platform game and yet I was getting speed issues. I'm pretty sure it wouldn't have happened in C++.

> **Simian Man said:**
> 
With a game, almost all of the time will be spent in library code: graphics, audio, networking etc.  And almost all Python libraries are written (mostly) in C.  So using Python for the game code doesn't hurt performance much and increases programmer efficiency.  Besides it doesn't sound like he's going after a AAA next-gen blockbuster does it?

It's very possible that after writing a 2D game, the OP will think about something more ambitious and try 3D, in which case knowing C++ will serve him/her well.

Can you give me some examples of complex games (not necessarily 3D) that are written in Python?

---

### Post by Simian Man on 2011-01-31
> **Nytram said:**
> Have you seen games that use pygame, or have you written one yourself?

I've done both, and the results aren't very impressive. Sure my code was inefficient and it was run on a low spec netbook, but it was a simple platform game and yet I was getting speed issues. I'm pretty sure it wouldn't have happened in C++.
I haven't used PyGame for a serious game, just played around with it.  Though Frets on Fire uses it and it runs pretty well.  With programming a game, you will always have to be careful to program efficiently.  This is easier to do with a language you know well, so maybe that has something to do with it.

> **Nytram said:**
> Can you give me some examples of complex games (not necessarily 3D) that are written in Python?

[Yes :).]("http://wiki.python.org/moin/PythonGames")

---

### Post by worksofcraft on 2011-01-31
Python would have been ideal for learning to program computers, but sadly a lot of confusion was recently introduced with the  switch to version 3 of the Python language: It is **not** being backward compatible with version 2 :(

Thus you will find many tutorials and also software libraries that you try to use simply don't work and if you are just starting then that can soon become very disappointing and frustrating.

The biggest difference between Python and C++ is that Python is an interpreted language while C++ is a compiled language. What that means is:

[LIST=1]
[*]with Python the computer works out what to do as it reads the actual program that you typed in.
[*]C++ programs first need to be converted into native machine instructions by a separate compilation stage to produce a binary or *executable* program that you can run. 
[/LIST]

I think both have their advantages and disadvantages so you might best just have a go at each and see which one suits you ;)

---

### Post by Nytram on 2011-01-31
> **Simian Man said:**
> I haven't used PyGame for a serious game, just played around with it.  Though Frets on Fire uses it and it runs pretty well.  With programming a game, you will always have to be careful to program efficiently.  This is easier to do with a language you know well, so maybe that has something to do with it.


You've not actually written a game in pygame and yet you're telling me how to use it?

Like I said in my last post it was a simple platformer and I wouldn't have had speed issues with C++.

> **Simian Man said:**
> 
[Yes :).]("http://wiki.python.org/moin/PythonGames")

This list includes snake and solitaire?

By complex my meaning was CPU/GPU intensive, ie requiring a fast language.

---

### Post by MadCow108 on 2011-01-31
> **Nytram said:**
> You've not actually written a game in pygame and yet you're telling me how to use it?

Like I said in my last post it was a simple platformer and I wouldn't have had speed issues with C++.

This list includes snake and solitaire?

By complex my meaning was CPU/GPU intensive, ie requiring a fast language.

pygame is largely implemented in C so its quite fast.
python is mainly used to glue the components together.
I guess your program was just written badly in this respect.

Almost all performance critical modules in python are not implemented in python itself.

I also recommend python over C++ as you will get nice results really fast. In C++ you spend literally years learning all the inconsistencies until you can really do really useful stuff. The new standard on the horizon isn't going to make learning easier too.
But on the long run you should learn a high performance compiled language, be it C,C++, Objective C or even something new like D or Go.

---

### Post by Simian Man on 2011-01-31
> **Nytram said:**
> You've not actually written a game in pygame and yet you're telling me how to use it?
I have written a game in Python, just not with PyGame.  Since he wanted 2D, I recommend PyGame.  I was just pointing out that it's easier to write bad code in a language you don't know well, so maybe that's where your poor results came from.


> **Nytram said:**
> 
This list includes snake and solitaire?

By complex my meaning was CPU/GPU intensive, ie requiring a fast language.

Uh, did you see the games on that list?  Are EVE Online and Civ IV not good enough?

They say that there is an 80-20 rule in programming: 80% of the time is spent in 20% of the code.  That may be true in some domains, but in game dev, it's likely closer to 95-5.  With a Python engine written in C or C++, you get the best of both worlds.

---

### Post by Nytram on 2011-01-31
Yes my code was badly written as I said in an earlier post, but my point is, I don't believe the same algorithms would have caused speed issues in C++.

Anyway, if you guys want to try writing complex games in Python then good luck to you.

In my original post I said I *personally* would use C++ to write games because of its speed, and I stand by that.

---

### Post by unknownPoster on 2011-01-31
> **Nytram said:**
> Yes my code was badly written as I said in an earlier post, but my point is, I don't believe the same algorithms would have caused speed issues in C++.

Anyway, if you guys want to try writing complex games in Python then good luck to you.

In my original post I said I *personally* would use C++ to write games because of its speed, and I stand by that.

I'd like to reiterate the point that EVE Online is written in Python. 

This isn't an insult to you, but if you're experience bad performance in PyGame it's probably because of poorly designed and/or written algorithms. 

Switching to C++ wouldn't automatically fix those problems, especially since you then introduce manual memory management among other things.

If you're switching to C++ in hopes of making your poorly written code faster, you really need to reinvestigate your path into programming.

---

### Post by Nytram on 2011-01-31
> **unknownPoster said:**
> I'd like to reiterate the point that EVE Online is written in Python. 

This isn't an insult to you, but if you're experience bad performance in PyGame it's probably because of poorly designed and/or written algorithms. 

Switching to C++ wouldn't automatically fix those problems, especially since you then introduce manual memory management among other things.

If you're switching to C++ in hopes of making your poorly written code faster, you really need to reinvestigate your path into programming.

This isn't an insult to you either, but you seem to be making a lot of assumptions there, all of which are wrong.

I'm tired of repeating myself, and I'm not spending all day arguing on here.

---

### Post by unknownPoster on 2011-01-31
> **Nytram said:**
> This isn't an insult to you either, but you seem to be making a lot of assumptions there, all of which are wrong.

I'm tired of repeating myself, and I'm not spending all day arguing on here.

You yourself said the following:

> 
Yes my code was badly written as I said in an earlier post, but my point is, I don't believe the same algorithms would have caused speed issues in C++.

I'm not assuming anything you haven't already said.

Your argument that C++ is superior to Python is invalid because you claim it makes bad algorithms faster.

---

### Post by tuahaa on 2011-01-31
Thanks for replies everyone.

I tried Python and found a very comprehensive and noob friendly tutorial and it's great! It's much easier than C++!

I'd like to dedicate some time to this on the weekends.

---

### Post by nvteighen on 2011-01-31
> **tuahaa said:**
> Thanks for replies everyone.

I tried Python and found a very comprehensive and noob friendly tutorial and it's great! It's much easier than C++!

I'd like to dedicate some time to this on the weekends.

Nice to know your decision. And I also think it's the right one: Python is a dynamic language with a very clean set of built-in features that makes it quite ideal to learn the basics of programming.

But, if you're going to be serious about programming, never forget that you'll have to learn other languages in the future. Don't you ever think that just knowing Python will be enough! (And IMO, that's a great thing: there's so much to learn! :D).

---

### Post by tuahaa on 2011-01-31
> **nvteighen said:**
> Nice to know your decision. And I also think it's the right one: Python is a dynamic language with a very clean set of built-in features that makes it quite ideal to learn the basics of programming.

But, if you're going to be serious about programming, never forget that you'll have to learn other languages in the future. Don't you ever think that just knowing Python will be enough! (And IMO, that's a great thing: there's so much to learn! :D).

Yes, I'll won't forget, and I'll keep it as a hobby! Hopefully I can contribute something useful to the relatively small collection of linux software available today.

---

### Post by CptPicard on 2011-01-31
This is a very old topic, but let's reiterate.. ;)

Python, certainly. It teaches many (most?) of the major programming patterns/paradigms in the same compactly designed language that has a very comfortable learning curve. After Python the beginner already has a very broad-based mindset... a toolkit for all kinds of programmatic solutions.

C++ on the other hand forces a much slower learning process with a more limited set of ideas as the end product.

Speed of native-compiled code is overrated. It's the abstract structure of the problem and thus the structure of the program that describes it that a programmer needs to develop understanding on. I've seen enough C++/Java-types have their mind blown by Lispish languages that I'm pretty confident in stating which way the more beneficial learning direction goes (I was one of these folks, mind you - there is a lot to "unlearn" after static-typed imperative programming becomes too ingrained).

---

### Post by Vaphell on 2011-01-31
Python all the way. It's enjoyable from the start and you are amazed how simple is to do cool things in it, even as a noob. C++ on the other hand is rather unforgiving for beginners and you have to assimilate a lot of knowledge to do anything in it. In general it's risky to start programming adventure with C/C++, especially when you are not a stereotypical introverted nerdy geek type, because you can get discouraged easily and think that programming is not for normal people :). Good mood makes learning anything a breeze.

---

### Post by kurum! on 2011-01-31
> **tuahaa said:**
> Thanks for replies everyone.

I tried Python and found a very comprehensive and noob friendly tutorial and it's great! It's much easier than C++!

I'd like to dedicate some time to this on the weekends.

Learn [Ruby]("http://ruby-doc.org/docs/ProgrammingRuby/")

---

### Post by slavik on 2011-02-01
Awesome, yet another language flamewar.

1. C++ has a standard, Python doesn't. Python's "standard" is whatever CPython does.
2. C is faster than C++. Templates slow down C++ and add to the code.
3. Python's OpenGL library calls glError() after ever OpenGL call (not sure if this is the case with OpenGL 3.0+) which is a no-no according to the red book as it is a major slowdown (50% of C speed, where as without those calls you can do 99%).
4. Python 3 breaking backwards compatibility with Python 2.x is irrelevant.
5. Python is still strongly typed.

---

### Post by Simian Man on 2011-02-01
> **slavik said:**
> 2. C is faster than C++. Templates slow down C++ and add to the code.
The only things templates slow down is the compilation process.  They are implemented very quickly as they are fully resolved at compile time.  Things that slow down C++ are polymorphism (due to vtable lookups) and exception handling (due to stack unwinds).

> **slavik said:**
> 3. Python's OpenGL library calls glError() after ever OpenGL call (not sure if this is the case with OpenGL 3.0+) which is a no-no according to the red book as it is a major slowdown (50% of C speed, where as without those calls you can do 99%).
I haven't used that library, but that sucks.  Hopefully they can resolve that.

---

### Post by unknownPoster on 2011-02-01
> **slavik said:**
> Awesome, yet another language flamewar.

1. C++ has a standard, Python doesn't. Python's "standard" is whatever CPython does.


Currently, that's my least favorite thing about Python. I feel it is a true weakness/barrier the adoption of the the language. 

I know of several professors at my school that won't use or teach python b/c of the 2.X to 3.0 transition.

---

### Post by scott_tiger on 2011-02-01
Learn Python as it is easy..
For games see this [www.ogre3d.org](www.ogre3d.org).

---

### Post by worksofcraft on 2011-02-01
> **slavik said:**
> Awesome, yet another language flamewar.

1. C++ has a standard, Python doesn't. Python's "standard" is whatever CPython does.
2. C is faster than C++. Templates slow down C++ and add to the code.
3. Python's OpenGL library calls glError() after ever OpenGL call (not sure if this is the case with OpenGL 3.0+) which is a no-no according to the red book as it is a major slowdown (50% of C speed, where as without those calls you can do 99%).
4. Python 3 breaking backwards compatibility with Python 2.x is irrelevant.
5. Python is still strongly typed.

IDK, it didn't look like it had quite become a "flame war"... yet ;)

Incidentally, when used properly, templates can serve to gain major improvement of run time performance over traditional algorithmic coding:

Templates allow the compiler to optimize out all the compile time constant conditions and generate inline code that exactly matches the requirements in each situation instead of having to test them all at run time. It makes a huge difference when used inside tight loops, such as manipulating images at the pixel level like one might need to do in games.

---

### Post by dajomu on 2011-03-22
I am pretty much in the same shoes as the thread-starter, but I wonder if Genie / Vala would be a perfect fit?
Program syntax that is similar to python and speed like C, or am I wrong?
I also like that you compile it so no installation is required, just a any C program.

---

### Post by slavik on 2011-03-22
> **Simian Man said:**
> The only things templates slow down is the compilation process.  They are implemented very quickly as they are fully resolved at compile time.  Things that slow down C++ are polymorphism (due to vtable lookups) and exception handling (due to stack unwinds).


I haven't used that library, but that sucks.  Hopefully they can resolve that.

templates add to the code during runtime for all the abstraction you do.

no, "they" won't resolve it, because that's how it was written from the get go.

---

