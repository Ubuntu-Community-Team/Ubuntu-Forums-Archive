---
title: "Why Microsoft rocks my boat"
date: 2008-04-24
forum: Programming Talk
---

### Post by Lau_of_DK on 2008-04-24
Gents,

Before you close this thread LaRoza: Yes, I've read the stickies, I've been to Wikipedia, I still dont have an answer :)

Visual Studio can really speed up my coding with its fast Intellisense. Any class, whether it be on of Microsoft standards or its a custom class is fully supported and you get all your options listed within a second. Why is there no editor for C++ on Linux that supports this? I mean Eclipse and QDevelop both try, but they're not very successful. Many times Eclipse gets the wrong options or incomplete lists. 

In C# you could do this

int i = 5;
i = i.ToString().ToCharArray().EncryptedStream(). 

And get all the properties and methods relevant for an EncryptedStream - Why is this "simple" feature not found in any of the Linux IDEs ?

/Lau

---

### Post by lnostdal on 2008-04-24
i could see this coming based on your other silly thread(s) .. first of all, see this:
[http://yosefk.com/c++fqa/index.html](http://yosefk.com/c++fqa/index.html)

> Why is this "simple" feature not found in any of the Linux IDEs ?

because we do not use c++ or c# .. we use languages that have support for introspection/reflection built into the language itself instead .. so we get this feature both at "developer-time" and runtime

---

### Post by Lau_of_DK on 2008-04-24
> **lnostdal said:**
> i could see this coming based on your other silly thread(s) 

Come on man, give a newbie a break. I recently switched to Ubuntu, Im here to stay, but I need to start getting my creative urges out by some form of coding, and its not as easy to get started here, as it is in Windows. Sorry to say.

> **lnostdal said:**
> .. first of all, see this:
[http://yosefk.com/c++fqa/index.html](http://yosefk.com/c++fqa/index.html)


That link is evil. I dont have the stomach to read through the whole thing, but know this: Im not hooked on C++ or C#, Im just looking for a language that powerful and in which I feel comfortable. Nobody has shown me anything that has convinced me to forsake C++ (note: I will probably need to see something that actually compiles to native before I do)

> **lnostdal said:**
> 
because we do not use c++ or c# .. we use languages that have support for introspection/reflection built into the language itself instead .. so we get this feature both at "developer-time" and runtime

Could you elaborate, I dont quite follow.

---

### Post by skeeterbug on 2008-04-24
> **Lau_of_DK said:**
> Gents,

Before you close this thread LaRoza: Yes, I've read the stickies, I've been to Wikipedia, I still dont have an answer :)

Visual Studio can really speed up my coding with its fast Intellisense. Any class, whether it be on of Microsoft standards or its a custom class is fully supported and you get all your options listed within a second. Why is there no editor for C++ on Linux that supports this? I mean Eclipse and QDevelop both try, but they're not very successful. Many times Eclipse gets the wrong options or incomplete lists. 

In C# you could do this

int i = 5;
i = i.ToString().ToCharArray().EncryptedStream(). 

And get all the properties and methods relevant for an EncryptedStream - Why is this "simple" feature not found in any of the Linux IDEs ?

/Lau

I used to wonder the same thing. However, intell-sense only speeds up the typing. There are a lot of good python editors that can handle refactoring and formatting. Also, the Python API docs are pretty decent (With .NET you always end up going to MSDN2 to see code examples/usage anyways right?).

---

### Post by Lau_of_DK on 2008-04-24
> **skeeterbug said:**
> I used to wonder the same thing. However, intell-sense only speeds up the typing. There are a lot of good python editors that can handle refactoring and formatting. Also, the Python API docs are pretty decent (With .NET you always end up going to MSDN2 to see code examples/usage anyways right?).

Yes in Visual C++ youre absolutely right, in C# not so much. I would say though tht speeding up the typing is (at least in my experiences) pretty helpful when it comes to productivity.

Are there any plans for making Python compile to native, or is the plan to keep it at the .pyc scripting level ?

/Lau

---

### Post by LaRoza on 2008-04-24
> **Lau_of_DK said:**
> Come on man, give a newbie a break. I recently switched to Ubuntu, Im here to stay, but I need to start getting my creative urges out by some form of coding, and its not as easy to get started here, as it is in Windows. Sorry to say.


If you want to be creative, use tools that assist you in this. C++, C# and Java seem to try to make things difficult for the programmer.

Try Lisp, Perl, Python, Ruby, or even C if you need it.

C++ and C# are usable on Linux, but they are rarely the language of choice.

It is very easy to get started on Linux. Open a terminal, type "python" and you are set to fiddle. Use Gedit (get the plugins for the best experience) and you will have an editor that can do everything that a programmer needs.

C# is a Windows oriented language, although it is available for Linux. If you want to use it in Linux, it is there, but I wouldn't think it is the language fulfilling "creative urges".

---

### Post by lnostdal on 2008-04-24
> **Lau_of_DK said:**
> Come on man, give a newbie a break. I recently switched to Ubuntu, Im here to stay, but I need to start getting my creative urges out by some form of coding, and its not as easy to get started here, as it is in Windows. Sorry to say.

well, in time you will realize you where wrong 

> **Lau_of_DK]
That link is evil. I dont have the stomach to read through the whole thing, but know this: Im not hooked on C++ or C#, Im just looking for a language that powerful and in which I feel comfortable. Nobody has shown me anything that has convinced me to forsake C++ (note: I will probably need to see something that actually compiles to native before I do)
[/quote]

Common Lisp .. SBCL said:**
> 
Could you elaborate, I dont quite follow.

no .. and i did not expect you to .. change your subject line and i might consider answering your questions

---

### Post by Lau_of_DK on 2008-04-24
> **LaRoza said:**
> 
It is very easy to get started on Linux. Open a terminal, type "python" and you are set to fiddle. Use Gedit (get the plugins for the best experience) and you will have an editor that can do everything that a programmer needs.


The problem I have with fiddling in Python is that I dont know all the tools that are available. If anything Intellisense puts all properties and methods on display, so you know that ToString() is an option forinstances, saves you alot of time searching through the documentation right? Thats really the type of accessability Im looking for. Well, that... And then something that compiles.

But thanks for your suggestions, I've already looked into Lisp a little bit, but that'll take some time to learn I think :)

/Lau

---

### Post by tseliot on 2008-04-24
> **LaRoza said:**
> C++ and C# are usable on Linux, but they are rarely the language of choice
C++ is used for KDE but not only, thanks to QT4. Replacing the standard library with QT4 will make you feel much more comfortable in C++, especially if you're used to coding in Python (which is and remains my favourite language).

Lau_of_DK: have you tried Kdevelop and Geany?

EDIT: you can try Eric4 for Python

---

### Post by skeeterbug on 2008-04-24
> **Lau_of_DK said:**
> The problem I have with fiddling in Python is that I dont know all the tools that are available. If anything Intellisense puts all properties and methods on display, so you know that ToString() is an option forinstances, saves you alot of time searching through the documentation right? ..

```
python>> i = 5
5
python>> dir(i)
```

The editor I use for larger Python projects is called PyDev (Eclipse plugin). It will intelli-sense libraries on your python path.

---

### Post by LaRoza on 2008-04-24
> **Lau_of_DK said:**
> The problem I have with fiddling in Python is that I dont know all the tools that are available. If anything Intellisense puts all properties and methods on display, so you know that ToString() is an option forinstances, saves you alot of time searching through the documentation right? Thats really the type of accessability Im looking for. Well, that... And then something that compiles.

But thanks for your suggestions, I've already looked into Lisp a little bit, but that'll take some time to learn I think :)

/Lau

See the Python docs, they are available for download and online reading.

See my wiki, you'll get a quick reference link for Python (handy PDF document)

For Python, str() is the function for converting to a string. In Python, str(), len(), int(), etc take an argument to convert and they are easily overloaded in classes.

---

### Post by Lau_of_DK on 2008-04-24
> **tseliot said:**
> C++ is used for KDE but not only, thanks to QT4. Replacing the standard library with QT4 will make you feel much more comfortable in C++, especially if you're used to coding in Python (which is and remains my favourite language).

Lau_of_DK: have you tried Kdevelop and Geany?

EDIT: you can try Eric4 for Python

I tried KDeveltop straight off when I first installed Ubuntu but I had some problems just getting it running after the package installation - Perhaps i should try again now that I actually know my way around Ubuntu. Do yo know if it integrates with Qt4 ?

And in regards to Geany: Ive never heard of it, does it come with your recommendation?

/Lau

---

### Post by kragen on 2008-04-24
> **lnostdal said:**
> we do not use c++ or c# .. we use languages that have support for introspection/reflection built into the language itself instead .. so we get this feature both at "developer-time" and runtime

What, you mean like [Reflection]("http://msdn2.microsoft.com/en-us/library/cxz4wk15.aspx")? :)

Intellisense does way more than just "speed up the typing" - it reduces typos, and its pretty much a replacement for documentation.

If there arent any current "intellisense-like" projects out there - are there any that could be considered a work in progress? 
You really cant underestimate how useful it is until you try and live without it! :)

---

### Post by tseliot on 2008-04-24
> **Lau_of_DK said:**
> I tried KDeveltop straight off when I first installed Ubuntu but I had some problems just getting it running after the package installation - Perhaps i should try again now that I actually know my way around Ubuntu. Do yo know if it integrates with Qt4 ?
Of course it does ;)

> **Lau_of_DK said:**
> And in regards to Geany: Ive never heard of it, does it come with your recommendation?
I can't recommend it for code completion but it supports many languages and makes compilation easier.

---

### Post by Lau_of_DK on 2008-04-24
> **LaRoza said:**
> See the Python docs, they are available for download and online reading.

See my wiki, you'll get a quick reference link for Python (handy PDF document)


I'll get right on it. While Im reading, could you prepare a compiler for Python so I scrap the interpreter? :)  (seriously: I will read up on Python)

> **skeeterbug said:**
> ```
python>> i = 5
5
python>> dir(i)
```

The editor I use for larger Python projects is called PyDev (Eclipse plugin). It will intelli-sense libraries on your python path.

Thats the ticket, that was exactly the type of thing Im looking for! Thanks alot.

> **kragen said:**
> 
You really cant underestimate how useful it is until you try and live without it! :)

A fellow addict - This man knows the withdrawal pains Im going through.

> **tseliot said:**
> Of course it does ;)


I'll look into it ASAP, thanks alot for the heads up.

---

### Post by LaRoza on 2008-04-24
> **tseliot said:**
> 
I can't recommend it for code completion but it supports many languages and makes compilation easier.

I opened Geany (although I don't use it, I have a bunch of things installed I never use but so I can't provide support...) and it does do completion for C (at least, I didn't try anything else) and it gives you the prototype for the function.

---

### Post by phuocle on 2008-04-24
> **lnostdal said:**
> no .. and i did not expect you to .. change your subject line and i might consider answering your questions

I'm sorry to say, but elitist attitudes like this are one of the things that turns people away Linux.

Who really gives a flying fig what his subject line is?  I didn't read the other threads the OP posted, but his questions here seemed relevant to me and were politely asked.  Just because he may not know better or simply just disagrees, this crap really bugs me.

If you don't want to answer, it's better to just shut your mouth.  If you were to ask a question in my area of expertise, I most definitely would not answer in such a stupid manner.

---

### Post by LaRoza on 2008-04-24
> **Lau_of_DK said:**
> I'll get right on it. While Im reading, could you prepare a compiler for Python so I scrap the interpreter? :)  (seriously: I will read up on Python)


No, you are missing the point...

The speed of development is more important than speed of execuation. Python is written in some very heavy duty C code, and is more than fast enough for most tasks. Even large commercial games and google use it.

If you want, you can create a .exe for Windows from a Python program using Freeze or Py2exe, but you don't use those during development.

---

### Post by LaRoza on 2008-04-24
> **phuocle said:**
> I'm sorry to say, but elitist attitudes like this are one of the things that turns people away Linux.

Who really gives a flying fig what his subject line is?  I didn't read the other threads the OP posted, but his questions here seemed relevant to me and were politely asked.  Just because he may not know better or simply just disagrees, this crap really bugs me.


It isn't elitist.

Everyone on this forum. The Title of a thread is the most important thing. This thread has a title that severely reduces the likelyhood of good communication.

---

### Post by y6FgBn)~v on 2008-04-24
An interestng read;

[http://www.ddj.com/development-tools/207401593?cid=RSSfeed_DDJ_All](http://www.ddj.com/development-tools/207401593?cid=RSSfeed_DDJ_All)

---

### Post by Lau_of_DK on 2008-04-24
> **LaRoza said:**
> It isn't elitist.

Everyone on this forum. The Title of a thread is the most important thing. This thread has a title that severely reduces the likelyhood of good communication.

I've sent an appology to lnostdal, explaining that the topic was not meant as an offense - Perhaps I should have written "A feature I would like ported to Linux" instead, I'll remember that.

> **LaRoza said:**
> No, you are missing the point...

The speed of development is more important than speed of execuation. Python is written in some very heavy duty C code, and is more than fast enough for most tasks. Even large commercial games and google use it.

If you want, you can create a .exe for Windows from a Python program using Freeze or Py2exe, but you don't use those during development.

Yes, youre probably right - Im the conservative type and I dont feel like Im actually programming if it doesn't compile to native, but its a feeling, I'll let it go. On a side note: Your website gives a very good overview I think, so I'll have a deeper look into the world of Python in the days to come.

---

### Post by CptPicard on 2008-04-24
> Why is this "simple" feature not found in any of the Linux IDEs ?

Because it's not such a "simple" feature necessarily, and implementing an IDE with that is both a big and sort of "boring" task... I can't imagine a lot of extremely skilled FOSS hackers spending their days implementhing something like that. You scratch an itch, and they probably don't have the itch for it.

If you really want it, you can always contribute a project that would benefit of it. :)

Of course having a language that has good introspection/reflection capabilities like Java helps. Eclipse's Java "IntelliSense" is great (and IDEA's Java stuff is Great).

> **skeeterbug said:**
> However, intell-sense only speeds up the typing. There are a lot of good python editors that can handle refactoring and formatting.

Well.. it's not quite like that. I do find that IntelliSense is a great memory aid, and in particular, makes new libraries much more discoverable.

A lot of people say that Python's dir() function does the same thing, but it doesn't. I never code in the Python shell, and none of the editors I actually write Python in (Kate and Emacs) are able to inspect anything while I write, so in that sense there is no "programmer-time" help from anything, and there is no source-visible type information either... which of course would both make tools possible and required. So it's an interesting tradeoff really. You really need tools where they are possible, and where you don't need them as much they are not possible as type information is runtime (or would at least be very hard to deduce, would require sort of running the code backwards to see where your "x" came from)...

Lisp's REPL in something like SLIME is of course a completely different animal, it needs to be experienced to be understood... you genuinely both have very good introspection capability while you write and the immediate ability to run what you just wrote, even in pieces...

> 
Are there any plans for making Python compile to native, or is the plan to keep it at the .pyc scripting level ?

One wonders how you're so good at tossing near-flamebaits.. ;)

There's nothing wrong with bytecode... just another form of abstraction of computing. So is CLI if you like C#. It is by no means a "goal" of all programming languages to aim to be native-compiled...

---

### Post by LaRoza on 2008-04-24
> **Lau_of_DK said:**
> 
Yes, youre probably right - Im the conservative type and I dont feel like Im actually programming if it doesn't compile to native, but its a feeling, I'll let it go. On a side note: Your website gives a very good overview I think, so I'll have a deeper look into the world of Python in the days to come.

[http://www.tcl.tk/doc/scripting.html](http://www.tcl.tk/doc/scripting.html)

For the mindset you have, this article will do you good. [http://www.paulgraham.com/avg.html](http://www.paulgraham.com/avg.html)

Don't be a Blub programmer ;)

---

### Post by Lau_of_DK on 2008-04-24
> **LaRoza said:**
> [http://www.tcl.tk/doc/scripting.html](http://www.tcl.tk/doc/scripting.html)

For the mindset you have, this article will do you good. [http://www.paulgraham.com/avg.html](http://www.paulgraham.com/avg.html)

Don't be a Blub programmer ;)

I'm stilling looking at the scripting article, I'll have to finish it on the other side of my upgrade to 8.04.

Regarding the "Beating the competetion": WOW - This article is a must read. Im starting on Lisp asap! :)

---

### Post by pmasiar on 2008-04-24
OP: You make me laugh when you ask for Python compiler. Python already compiles your code, it is not as painful as with MSFT commandline tools, so you completely missed it.

You seems to me like "free range chicken": chicken closed to huge hangar (MSFT IDE), with small open door to open range. No chicken ever leave there, because it is scary, smells differently, and there is high blue ceiling instead of good old familiar neon tubes like in hangar.

Static typing is like life in the "safe" hangar. Dynamic typing is like free blue sky outside. Run!

IDE is good for generating many lines of code in a statically typed language, while you don't know library yet. Universal editors are excellent for refactoring, are highly customizable, and you can keep your customizations as you move from one language to another. I never seen any IDE which had half of the timesaving features of MultiEdit.

OK, here is quote from your favorite philosopher, William H. Gates:

"Measuring programmer's productivity in lines of code is like measuring progress of airplane design by the weight". Or something like that :-)

Enjoy!

This thread is completely useless, should be moved to "recurring discussions" or closed before it descends in the flames.

---

### Post by Wybiral on 2008-04-24
The only reason you need those features is because you're using languages that require unusable amounts of code to do simple little tasks that the language should do for you. Not to mention lacking static types also makes it easier to reuse your own code (reducing the bloat that you seem to be suffering from). Get rid of the bloat, don't find new features to make it more palatable.

And if you find that something like Eclipse doesn't have all the features you need, maybe you should stop crying to us and go out there and apply your leet-skills to making that feature a possibility. Why isn't it already there? Obviously because not many people find it necessary :) As mentioned above, open source works by the "itch and scratch" development model... If something hasn't been scratched, it probably wasn't an itch to begin with.

---

### Post by Lau_of_DK on 2008-04-24
> **Wybiral said:**
> The only reason you need those features is because you're using languages that require unusable amounts of code to do simple little tasks that the language should do for you. Not to mention lacking static types also makes it easier to reuse your own code (reducing the bloat that you seem to be suffering from). Get rid of the bloat, don't find new features to make it more palatable.


Not quite true on the first bit. I need it also as a handy replace for the documentation, to discover the classes quickly - although Im starting to see that theres some truth in the statements regarding C++ not being the chief of all programming languages.

Regarding the bloat - what do you mean?

> And if you find that something like Eclipse doesn't have all the features you need, maybe you should stop crying to us and go out there and apply your leet-skills to making that feature a possibility. Why isn't it already there? Obviously because not many people find it necessary :) As mentioned above, open source works by the "itch and scratch" development model... If something hasn't been scratched, it probably wasn't an itch to begin with.

I dont really understand why the tone is so harsh in this forum. Ive never pretended to be elite and I dont consider this type of request -crying-. I was looking for a quick way into faster development on this new platform. I agree that I could have formulated the thread-topic alot more elegantly and lfnostdal has been kind enough to send me some suggestions on how to improve, so point taken. 


/Lau

---

### Post by Can+~ on 2008-04-24
Python + Editra:

[IMG]http://img.photobucket.com/albums/v517/CanXp/python/screenshot2.png[/IMG]

= Auto-completion


And I agree with the one who said pydev with Eclipse. It's great.

To the OP, your post seems totally offensive, in the sense of "Omg, microsoft is so awesome, it does X, Y and Z, linux does not have that! And I like turtles". Better way: "Can you point me to an IDE that does this ____ as visual studio on windows? kthxbye"

---

### Post by kragen on 2008-04-24
> **Wybiral said:**
> The only reason you need those features is because you're using languages that require unusable amounts of code to do simple little tasks that the language should do for you. Not to mention lacking static types also makes it easier to reuse your own code.

[Why doesn't C# support #define macros?]("http://blogs.msdn.com/csharpfaq/archive/2004/03/09/86979.aspx")

C# doesn't support macros (I assume thats what you mean by "static" types) or the like because they make the code less readable. The same argument (readability) is also the reason why its more verbose. In my experience it helps loads - if your looking at code which is unfamiliar to you macros and abbreviated names are your two worst enemies!

If a project like this doesn't already exist I'd be interested in starting one - this is definitely an itch for me!

---

### Post by LaRoza on 2008-04-24
> **kragen said:**
> [Why doesn't C# support #define macros?]("http://blogs.msdn.com/csharpfaq/archive/2004/03/09/86979.aspx")

C# doesn't support macros (I assume thats what you mean by "static" types) or the like because they make the code less readable. The same argument (readability) is also the reason why its more verbose. In my experience it helps loads - if your looking at code which is unfamiliar to you macros and abbreviated names are your two worst enemies!

If a project like this doesn't already exist I'd be interested in starting one - this is definitely an itch for me!

No, wybiral meant static typing as in "int myVariable; char myChar;". When such strictness isn't needed, it is faster to let the computer (compiler, interpreter) deal with that. C# isn't C either, #define is used by the cpp, so it doesn't make sense to have it in C# (although it would be rather easy to do I would think)

---

### Post by Wybiral on 2008-04-24
> **Lau_of_DK said:**
> Not quite true on the first bit. I need it also as a handy replace for the documentation, to discover the classes quickly - although Im starting to see that theres some truth in the statements regarding C++ not being the chief of all programming languages.

Regarding the bloat - what do you mean?


If documentation is all you need, open up a Python terminal and try:
```

import math
help(math)
help(math.cos)

```
No need for a bulky IDE when your language supports doc-strings :)

Most people use IDEs like that because their code gets too large to manage, so they need all of those features to lug it all around. That's what I meant by "bloat". But if you just need documentation, that's why some languages have a REPL, and doc-strings too :)


> **Lau_of_DK said:**
> I dont really understand why the tone is so harsh in this forum. Ive never pretended to be elite and I dont consider this type of request -crying-. I was looking for a quick way into faster development on this new platform. I agree that I could have formulated the thread-topic alot more elegantly and lfnostdal has been kind enough to send me some suggestions on how to improve, so point taken. 


/Lau

When people say stuff like "Why Microsoft rocks my boat" on a Linux forum, and complain about Linux development tools not having enough features, 99% of the time they are trolling (stick around, it's a common theme).

[quote=kragen]I assume thats what you mean by "static" types[/quote]
No, it's not. I meant that the languages that use those IDEs are usually statically typed (as opposed to dynamically typed). Google it and come back to us. :)

---

### Post by LaRoza on 2008-04-24
> **Lau_of_DK said:**
> 
I dont really understand why the tone is so harsh in this forum. Ive never pretended to be elite and I dont consider this type of request -crying-. I was looking for a quick way into faster development on this new platform. I agree that I could have formulated the thread-topic alot more elegantly and lfnostdal has been kind enough to send me some suggestions on how to improve, so point taken. 


You are (probably) not in touch with the "culture" of this forum. I don't go on PS forums and ask why they don't have Halo for PS2, and that they should have Halo for PS2 because it is the best game in the FPS genre. (That isn't true, Goldeneye and Perfect dark are the best FPS, but Halo (2) are the next generation best)

If you stick around, you'll see it. You will also start to see the same things over and over again. The first time you see it (say, a "what IDE do I use" thread) you don't think anything of it, but if you see a bunch of them constantly, they get really old and you start repsonding differently.

---

### Post by Wybiral on 2008-04-24
> **LaRoza said:**
> If you stick around, you'll see it. You will also start to see the same things over and over again. The first time you see it (say, a "what IDE do I use" thread) you don't think anything of it, but if you see a bunch of them constantly, they get really old and you start repsonding differently.

Exactly, I don't mean to sound as harsh as I probably do... But search around, you'll see why.

---

### Post by LaRoza on 2008-04-24
> **Wybiral said:**
> Exactly, I don't mean to sound as harsh as I probably do... But search around, you'll see why.

Neither do I (although I may seem a little soft spoken, I am not as soft spoken as I should be). It is a result of the same stuff [noparse]for(;;)[/noparse].

---

### Post by kragen on 2008-04-24
> No, it's not. I meant that the languages that use those IDEs are usually statically typed (as opposed to dynamically typed). Google it and come back to us. :)

Ah - Wikipedia to the rescue :)
C# has static typing and I've come to hate languages that don't! :P

> **Wybiral said:**
> If documentation is all you need, open up a Python terminal and try:
```

import math
help(math)
help(math.cos)

```
No need for a bulky IDE when your language supports doc-strings :)

Yeah, features like that are really handy - I hate to go on about Microsoft's IDE's, but Visual Studio does takes it one step further - 

[IMG]http://www.activewin.com/reviews/software/devl/vsnet2003/images/figure_24.gif[/IMG]

Xml-Based documentation appears in tool tips as you type, showing you the name and type of inputs for every overload, plus any inline documentation it can find, all without compiling a thing.

I've been having a quick think about how to create a library to do something like this - I think it should be relatively easy to come up with a re-usable framework for something like this, the difficult bit would be supporting all the different languages.
Once a language is supported though, it would mean any IDE could use this sort of thing with very little effort, although whether they would or not is another matter!

---

### Post by samjh on 2008-04-24
> **Lau_of_DK said:**
> I dont really understand why the tone is so harsh in this forum. Ive never pretended to be elite and I dont consider this type of request -crying-. I was looking for a quick way into faster development on this new platform. I agree that I could have formulated the thread-topic alot more elegantly and lfnostdal has been kind enough to send me some suggestions on how to improve, so point taken. 

"Why Microsoft rocks my boat", in any Linux-related discussion board, is like going to an animal-rights discussion board and posting, "Why Chicken-fights rocks my boat". ;)

> Visual Studio can really speed up my coding with its fast Intellisense. Any class, whether it be on of Microsoft standards or its a custom class is fully supported and you get all your options listed within a second. Why is there no editor for C++ on Linux that supports this? I mean Eclipse and QDevelop both try, but they're not very successful. Many times Eclipse gets the wrong options or incomplete lists.Visual Studio really excels with Intellisense.  Perhaps one of the best innovations ever made by Microsoft in its software development tools.

On Linux, several IDEs have various forms of code-completion.
Eclipse
Code::Blocks
MonoDevelop

The final one, MonoDevelop has features very similar to Intellisense.  However I don't think any Linux-compatible IDE shows pop-up documentation for C++.  I know that both Eclipse and Netbeans can show method/class/property documentation as pop-ups for Java language, but not C++.

---

### Post by LaRoza on 2008-04-24
> **samjh said:**
> "Why Microsoft rocks my boat", in any Linux-related discussion board, is like going to an animal-rights discussion board and posting, "Why Chicken-fights rocks my boat". ;)

Unless the boat is capsized because of the rocking, it won't work well.

---

### Post by Wybiral on 2008-04-24
> **kragen said:**
> Ah - Wikipedia to the rescue :)
C# has static typing and I've come to hate languages that don't! :P

Really? I always thought it was strictly statically typed... How does that work?


> **kragen said:**
> Xml-Based documentation appears in tool tips as you type, showing you the name and type of inputs for every overload, plus any inline documentation it can find, all without compiling a thing.

I've been having a quick think about how to create a library to do something like this - I think it should be relatively easy to come up with a re-usable framework for something like this, the difficult bit would be supporting all the different languages.
Once a language is supported though, it would mean any IDE could use this sort of thing with very little effort, although whether they would or not is another matter!

I just keep a terminal open with the Python console and use "dir" and "help" when needed. It seems to work well enough for me. It's actually annoying, IMO, when the IDE goes into that "suggest everything" mode.

---

### Post by LaRoza on 2008-04-24
> **Wybiral said:**
> I just keep a terminal open with the Python console and use "dir" and "help" when needed. It seems to work well enough for me. It's actually annoying, IMO, when the IDE goes into that "suggest everything" mode.

I saw this animation of Vim with a ascii art paperclip offering suggestions. I wish I could find it!

---

### Post by LaRoza on 2008-04-24
> **LaRoza said:**
> I saw this animation of Vim with a ascii art paperclip offering suggestions. I wish I could find it!
Here it is:
[img]http://blogs.sun.com/marigan/resource/vim.gif[/img]

---

### Post by kragen on 2008-04-24
C# **is** statically typed - I've come to like it that way. My experience with dynamically typed languages (this is where wikipedia makes me sound knowledgeable :)) has been languages like JavaScript - dynamic types just makes things a pain to debug.

Admittedly, it is less flexible, but .Net 2.0 introduced generics, which makes re-use a whole lot easier and keeps debugging nice and straightforward.

Having said that, I really like python, and thats dynamically typed (according to wikipedia! :))...

> I saw this animation of Vim with a ascii art paperclip offering suggestions. I wish I could find it! 

Believe it or not, intellisense is genuinely not annoying, definitely nowhere near as annoying as "clippy"! :P

---

### Post by LaRoza on 2008-04-24
> **kragen said:**
> C# **is** statically typed - I've come to like it that way. My experience with dynamically typed languages (this is where wikipedia makes me sound knowledgeable :)) has been languages like JavaScript - dynamic types just makes things a pain to debug.

Admittedly, it is less flexible, but .Net 2.0 introduced generics, which makes re-use a whole lot easier and keeps debugging nice and straightforward.

Having said that, I really like python, and thats dynamically typed (according to wikipedia! :))...

Believe it or not, intellisense is genuinely not annoying, definitely nowhere near as annoying as "clippy"! :P

ECMAScript (and Perl) have weak typing, where the types are silently converted and weird things happen. That is a real pain. Python, on the other hand, will enforce types. So in ECMAScript: 

[php]
var x = 2 + "2";
[/php]

Works (Perl also). In Python, it throws an error.

---

### Post by Wybiral on 2008-04-24
> **kragen said:**
> C# **is** statically typed - I've come to like it that way. My experience with dynamically typed languages (this is where wikipedia makes me sound knowledgeable :)) has been languages like JavaScript - dynamic types just makes things a pain to debug.

Admittedly, it is less flexible, but .Net 2.0 introduced generics, which makes re-use a whole lot easier and keeps debugging nice and straightforward.

Having said that, I really like python, and thats dynamically typed (according to wikipedia! :))...



Believe it or not, intellisense is genuinely not annoying, definitely nowhere near as annoying as "clippy"! :P

Oh, lol, I was so thrown off by your excitement that I though you meant "dynamically typed" :)

Why is dynamic typing a pain to debug (Javascript is, but not dynamically typed languages in general)?

Python is dynamically typed, and it's a beautiful thing. You can write WAY more reusable and flexible code that way.

---

### Post by LaRoza on 2008-04-24
> **Wybiral said:**
> 

Why is dynamic typing a pain to debug (Javascript is, but not dynamically typed languages in general)?



Weak typing (C, ECMAScript, etc) is a pain, dynamic isn't.

---

### Post by kragen on 2008-04-24
> **Wybiral said:**
> Oh, lol, I was so thrown off by your excitement that I though you meant "dynamically typed" :)

Why is dynamic typing a pain to debug (Javascript is, but not dynamically typed languages in general)?

Python is dynamically typed, and it's a beautiful thing. You can write WAY more reusable and flexible code that way.

I just couldn't work out what all the JavaScript object were! It was hard enough when debugging - without support for a simple .GetType() or equivalent (or at least not that I could see), I had a hard time working out whether an object was a var, piece of the DOM or a JavaScript object.

If I'm trying to understand some JavaScript and I'm not debugging it things are even worse! I would come across pieces of code like:

```
var enabled;
```

And there would be no pointers whether id was a boolean, string (taking values like "enabled", "disabled", "menuOnly" or other equally cryptic values), or even an int.

In truth I don't use JavaScript that much - I expect that if your used to it, you get used to figuring things like that out.

---

### Post by kragen on 2008-04-24
I've only just fired Ubuntu up for the first time in over a year, so I'm quite looking forward to having another go with Python :). I think this comic sums python up perfectly!

[IMG]http://imgs.xkcd.com/comics/python.png[/IMG]

---

### Post by LaRoza on 2008-04-24
> **kragen said:**
> I just couldn't work out what all the JavaScript object were! It was hard enough when debugging - without support for a simple .GetType() or equivalent (or at least not that I could see), I had a hard time working out whether an object was a var, piece of the DOM or a JavaScript object.

If I'm trying to understand some JavaScript and I'm not debugging it things are even worse! I would come across pieces of code like:

In truth I don't use JavaScript that much - I expect that if your used to it, you get used to figuring things like that out.

Sorry, it is easy:
```

type(<object>)

```

Good design goes a long way with languages like ECMAScript, Perl, and PHP. They get out of hand fast if you are not careful, but they can be quite powerful.

---

### Post by CptPicard on 2008-04-24
> **kragen said:**
> 
Admittedly, it is less flexible, but .Net 2.0 introduced generics, which makes re-use a whole lot easier and keeps debugging nice and straightforward.


If they are anything like Java's generics... well, those were pretty much the last straw for me with Java. They just shackle you even more and make you fight to make it work, because the generics type system just won't let you do what you want to, you need to jump through hoops first to keep the compiler happy.

(W00t, 1k posts. \\:D/ )

---

### Post by LaRoza on 2008-04-24
> **CptPicard said:**
> 
(W00t, 1k posts. \\:D/ )

It is so tempting to move this thread to the Recurring Discussions as suggested earlier...

(You'd lose the beans you got in this thread. So would I, but that is small potatoes to me)

---

### Post by Wybiral on 2008-04-24
> **kragen said:**
> And there would be no pointers whether id was a boolean, string (taking values like "enabled", "disabled", "menuOnly" or other equally cryptic values), or even an int.

In truth I don't use JavaScript that much - I expect that if your used to it, you get used to figuring things like that out.

The thing is that with good dynamic code you shouldn't have to care what type a variable is. And with a good dynamic language, you have introspection to make that a non-issue.

In Python I can say:

```

def add(x, y):
    return x + y

```

And not care if they are strings, floats, ints, etc. In fact, I'm glad I don't have to care, because the same function can be used for all of them (hence why it's good for code reuse). That's a trivial example, and any template/generic supporting language can do it, but there are many more examples that aren't as trivial to implement in a statically typed language.

---

### Post by Can+~ on 2008-04-24
> **kragen said:**
> I've only just fired Ubuntu up for the first time in over a year, so I'm quite looking forward to having another go with Python :). I think this comic sums python up perfectly!

[IMG]http://imgs.xkcd.com/comics/python.png[/IMG]

The guy from xkcd went bananas with python, he has 2 strips with it (3 if we count the one above):

"[import soul](http://www.xkcd.com/413/)"
"[from c to python](http://www.xkcd.com/409/)"

---

### Post by LaRoza on 2008-04-24
> **Can+~ said:**
> The guy from xkcd went bananas with python, he has 2 strips with it (3 if we count the one above):

"[import soul](http://www.xkcd.com/413/)"
"[from c to python](http://www.xkcd.com/409/)"

He also has several Lisp and Perl references, I wouldn't say he went bananas with any of them. He just recognized good languages.

Lisp: [http://xkcd.com/297/](http://xkcd.com/297/)
Perl: [http://xkcd.com/208/](http://xkcd.com/208/)

---

### Post by Wybiral on 2008-04-24
> **LaRoza said:**
> He also has several Lisp and Perl references, I wouldn't say he went bananas with any of them. He just recognized good languages.

import soul

:)

---

### Post by pmasiar on 2008-04-24
to compare apples to apples, we need to distinguish between weak typing, like in JS and Perl, which tries to guess conversion, and late binding (AKA dynamic typing), where variable name is bound to type at runtime.

- C++, C#, Java are strictly statically typed
- Perl is weakly dynamically typed (and needs more than 100 operators)
- Python is strictly dynamically typed

Then, there are macros/lambdas, which can generate  blobs of code on runtime, and that is especially powerful in dynamically typed languages like Lisp and Python. In them, you can put together data structure at runtime (list in lisp, string in Python) which defines a function, compile it into code at runtime, and assign it to a name. And voila! You can use it exactly like any other function. Together with introspection, you can write frameworks which generate code for you.

See also [http://en.wikipedia.org/wiki/Greenspun's_Tenth_Rule](http://en.wikipedia.org/wiki/Greenspun's_Tenth_Rule) and definition of 'Blub programmer' in [http://www.paulgraham.com/avg.html](http://www.paulgraham.com/avg.html) :-)

Of course dynamic typing feels weird to you - advanced features of higher languages always do so to blub programmers (for any value of blub). It is normal - it is just sign that you need to learn.

---

### Post by jespdj on 2008-04-25
But Eclipse does this just as well as MS Visual Studio.

[IMG]http://home.deds.nl/~jesper/eclipse-autocomplete.jpg[/IMG]

---

### Post by ricegf on 2008-04-25
> **kragen said:**
> 
Xml-Based documentation appears in tool tips as you type, showing you the name and type of inputs for every overload, plus any inline documentation it can find, all without compiling a thing.


Your statement above suggests that you haven't "gotten" the power of dynamic typing yet. The "type" of a Python input is "whatever objects have the same methods and attributes as I use with this input". This is sometimes called "duck typing" - another Wikipedia opportunity! :)

The author may have an *idea* of what types she's supporting in writing a method, but in actual practice, types invented years later will work just fine as long as they match the method and attribute signatures used by the method.

I came to Python from Ada (one of the most strictly typed, I believe), and you simply can't imagine my astonishment at how much I could accomplish in  just a few lines of highly reusable code - and without even noticing I was *writing* reusable code!

---

### Post by LaRoza on 2008-04-25
> **ricegf said:**
> 
I came to Python from Ada (one of the most strictly typed, I believe), and you simply can't imagine my astonishment at how much I could accomplish in  just a few lines of highly reusable code - and without even noticing I was *writing* reusable code!

That is a certainly a big contrast! I used Ada a bit.

---

### Post by Zugzwang on 2008-04-25
> **jespdj said:**
> But Eclipse does this just as well as MS Visual Studio.

But this is first of all Java ;-) and secondly not precisely the same! As you have seen, in the Visual Studio case, you also got a list of pages explaining the stuff further and containing examples. In your case you just get a description of what the method does. In general, however, you have a clear idea of *what* you are trying to accomplish, not exactly *how* you do it, so you are often rather looking for examples & explanations on solving the overall problem and not just one method or class.

This is however a big feature of Java (and all other language with a big user base). If for example I want to manipulate some pixels of the image in Java, I use a sufficiently good search string in google and search for some examples. Then I know what classes to use and then I can easily look it up.

---

### Post by hyper_ch on 2008-04-25
> **kragen said:**
> I've only just fired Ubuntu up for the first time in over a year, so I'm quite looking forward to having another go with Python :). I think this comic sums python up perfectly!

Well, with regards to editors you must not forget this one here:
[IMG]http://imgs.xkcd.com/comics/real_programmers.png[/IMG]

---

### Post by Lau_of_DK on 2008-04-25
In closing.

This has been an interesting thread from my POV giving some new insights into the Linux community.

One thing has changed since the beginning: Im going to get really serious about learning Lisp, then Python. ( Lisp compiles right? :) )

I dont think that these strictly high-level languages are the end of all programming, I simple wouldn't want to put myself in a position where I couldnt do the low-level stuff myself, which would put me 100% at the mercies of the libraries. But on the other hand, Im comitted to not being (continuing to be) a Blub programmer.

Last night I upgraded from 7.10 => 8.04 which complete destroyed by installation causing kernel panics, and since the Ubuntu servers are so slow ATM it will be a while before I have an installation again.

To those of you who provided valuable insights and helpful links: Thanks alot. 

/Lau

---

### Post by Wybiral on 2008-04-25
You're overlooking something here... Python and C are good friends. You can easily write a library in C, then use either [ctypes]("http://docs.python.org/lib/module-ctypes.html"), [SWIG]("http://www.swig.org/"), or [PyRex]("http://www.cosc.canterbury.ac.nz/greg.ewing/python/Pyrex/") to make it a Python module. So when you need that low-level interfacing, it's there with little extra work. If it's just speed you want, high-level languages are capable of JIT compiling. Python, for instance, has [psyco]("http://psyco.sourceforge.net/").

---

### Post by Lau_of_DK on 2008-04-25
> **Wybiral said:**
> You're overlooking something here... Python and C are good friends. You can easily write a library in C, then use either [ctypes]("http://docs.python.org/lib/module-ctypes.html"), [SWIG]("http://www.swig.org/"), or [PyRex]("http://www.cosc.canterbury.ac.nz/greg.ewing/python/Pyrex/") to make it a Python module. So when you need that low-level interfacing, it's there with little extra work. If it's just speed you want, high-level languages are capable of JIT compiling. Python, for instance, has [psyco]("http://psyco.sourceforge.net/").

Well - That great, I'll be looking into those tools. It does not change my oppinion though, because my concern is that in a few years we will have a fleet of programmers who can only use high-level languages, because they never bother to go down low. I suppose in a sense thats why Ive tried to keep myself in C++, to avoid loosing touch with this type of programming. 

My own situation: I will most definately be looking at Python and integrating C modules.

---

### Post by lnostdal on 2008-04-25
yeah, using C as a sort of portable ASM for whatever language you are using is a great idea

practically all languages can communicate with C since it has a well defined ABI etc. .. this is often not the case with C++ by the way, but i hope i don't have to rant more about C++ for a while now .. lol

here is how you do it in lisp:

* [http://www.sbcl.org/manual/Foreign-Function-Interface.html](http://www.sbcl.org/manual/Foreign-Function-Interface.html)
..or..
* [http://common-lisp.net/project/cffi/manual/html_node/index.html](http://common-lisp.net/project/cffi/manual/html_node/index.html)

..it is easy and downright fun to test/debug/play with C libraries this way.. =) (edit: as in; from a high-level interactive language+environment)

---

### Post by skeeterbug on 2008-04-25
[IMG]http://img245.imageshack.us/img245/57/pydevyf1.jpg[/IMG]

This is the PyDev plugin for Eclipse. Note the SomeMethod method in the user class, and how intelli-sense picks it up along with the parameter and the documentation string.

---

### Post by CptPicard on 2008-04-25
> **Lau_of_DK said:**
> ...in a few years we will have a fleet of programmers who can only use high-level languages, because they never bother to go down low.

Gah... I am a high-level algorithmics geek -- high-level in the pencil and paper and maths and "drawing pictures of my algorithms to figure them out" sense... you know, opinions like that are always a bit of a slap in the face for me, because just because I don't bother using C (although I can), it doesn't make me any less competent -- and I would WANT our new programmers to approach their field from a completely different direction than pointer arithmetic and bit pushing...  ;)

C is just one kind of "virtual machine" you can code on. I mean, modern CPUs just fake x86 anyway for compatibility! It could just as well be a "Java VM CPU" or a Lisp machine. Or some kind of Haskell interpreter... now that would let you focus on the problem, and REALLY see if you've got the mind for it! :)

Honestly, you can do stuff in HLLs [that blow your mind]("http://ubuntuforums.org/showthread.php?t=749965") in comparison to what LLLs bind you to.

I'm not going to repeat myself, I just refer you to [this thread]("http://ubuntuforums.org/showthread.php?t=745599") and read my exchange with Shining Arcanine...

---

### Post by pmasiar on 2008-04-25
> **Zugzwang said:**
> in the Visual Studio case, you also got a list of pages explaining the stuff further and containing examples....
This is however a big feature of Java (and all other language with a big user base).

Wrong. This is feature of a language with rich company who can finance thousand of writers to sit down is a cubicle and write all that boring stuff. :-) If abundant presence of boring stuff is your only important criteria when picking a language, Free software will never be your choice. In Free software, docs is written until is good enough, then left to be improved by others. In proprietary software, you pay (through your nose) for that boring stuff. Free software instead provides forums, wikis, recipe repositories, created by enthusiastic community, where anyone can participate and help others. 

My personal experience with Free vs proprietary docs is mostly in databases, and let me tell you that MySQL beats Oracle in this. Well paid Oracle experts do not waste time helping beginners in forums, but hoard precious knowledge they know and rack money. Even access to Oracle help system is for (free) registered users. MySQL even lets users to comment on docs pages, and often I found that if docs were not clear enough, someone asked, and someone else answered my question.

---

### Post by rangalo on 2008-04-25
Hi,

It is not good to ask somebody to change the language if he finds a feature or two missing in the IDE.

I think eclipse (CDT) tries to provide a similar functionality. But if you are not satisfied with it, you can modify the eclipse cdt plugin. That's how free software works. You are a programmer, you can do it and make it better than ms visual studio. (May be you will need to learn Java)

Have a good time with reinstall/upgrade !

regards,
rangalo

---

### Post by Lau_of_DK on 2008-04-25
> **pmasiar said:**
> Wrong. This is feature of a language with rich company who can finance thousand of writers to sit down is a cubicle and write all that boring stuff. :-) If abundant presence of boring stuff is your only important criteria when picking a language, Free software will never be your choice. 

Now please: Dont take offense! But I think that this kind of mentality definately scares people away from Unix/Linux/OpenSource and everything in between. When I first made this thread I was hoping that somebody would step up and say -Well, if MS can do it, we can do it- or maybe -We've had those features for ages-. This mentality that -everything that comes from MS is evil and stupid- and what this community has to offer -is waaaay better (even though its not)- is silly and unhelpful to people looking to migrate to new platforms. The work that Microsoft has put into MSDN and the likes is actually an incredible feat which daily helps/assists many many developers across the globe. To write it off as -just boring stuff- is not the best way to go. IMHO :)

Why are so many people in this thread offended that Microsoft is actually one step ahead of the opensources community in regards to creating development enviroments? Being offended produces nothing. An attitude of 'we know they've got these things, but we can do something similar/better' would be alot more productive.

> **CptPicard said:**
>  you know, opinions like that are always a bit of a slap in the face for me, because just because I don't bother using C (although I can)

You know, before I joined this forum I considered myself quite gifted within communications - now: maybe not so much. Im really sorry if you took my statement as a slap in the face, it was not meant to be anything other than me raising a concern and primarily a concern in regards to myself: I do not want to loose touch with lowlevel programming. Im not saying that a man such as yourself is not competent, if anything I consider you much more competent and intelligent than myself, but this was not the subject I was touching on. Hope this clears up the slap - There was no harm intended.

Regarding your thread on BLOW YOUR MIND - Im absolutely struggling to understand the concept and the code that is discussed - I might return with (many) questions.

---

### Post by lnostdal on 2008-04-25
here is a screenshot of Slime (a Common Lisp IDE or GUI or whatever) .. it looks very simple, but has many somewhat "hidden" features 

.. i've bound auto-completion to tab, for instance "(m-v-b" expands to "(multiple-value-bind" .. at the bottom you will always see the arguments for the function/macro/code you are currently working with ..etc.

[img]http://nostdal.org/~lnostdal/gfx/screenshot-slime-describe-symbol.png[/img]

---

### Post by pmasiar on 2008-04-25
> **Lau_of_DK said:**
> my concern is that in a few years we will have a fleet of programmers who can only use high-level languages, because they never bother to go down low.

This is **exactly** the arguments used 20 years ago to argue that C is bad and real programmers should code in ASM. :-)

Moore's law continues to add more CPU power, imagine the power what will be idling on your desktop 20 years from now.

[http://paulgraham.com/hundred.html](http://paulgraham.com/hundred.html)

---

### Post by Lau_of_DK on 2008-04-25
> **rangalo said:**
> Hi,

It is not good to ask somebody to change the language if he finds a feature or two missing in the IDE.

I think eclipse (CDT) tries to provide a similar functionality. But if you are not satisfied with it, you can modify the eclipse cdt plugin. That's how free software works. You are a programmer, you can do it and make it better than ms visual studio. (May be you will need to learn Java)

Have a good time with reinstall/upgrade !

regards,
rangalo

I think youre right :)

Thanks alot.

(ps: deBootstrap has run for 2 hours now and is up to packages starting with "l" - could somebody hurry up these servers??? zzzZZZ)

---

### Post by Wybiral on 2008-04-25
> **Lau_of_DK said:**
> Why are so many people in this thread offended that Microsoft is actually one step ahead of the opensources community in regards to creating development enviroments? Being offended produces nothing. An attitude of 'we know they've got these things, but we can do something similar/better' would be alot more productive.

You're looking at this wrong. I'm not offended... Because I don't actually believe that MS is one step ahead of us just because they have bloated, over-featured, development tools for crappy languages. I don't want half of that crap in my editor. So no, I'm not going to "step up" and write it myself. If you always need those kinds of features whenever you're developing, maybe your language is the culprit :) MS is one step _behind_ us, they just recently got their hands on Python (with IronPython), which we've had for years.

Remember the "itch and scratch" development model? You're the one with the itch, so why do you expect us to scratch it?

---

### Post by pmasiar on 2008-04-25
> **Lau_of_DK said:**
> I think that this kind of mentality definately scares people away from Unix/Linux/OpenSource and everything in between. When I first made this thread I was hoping that somebody would step up and say -Well, if MS can do it, we can do it- or maybe -We've had those features for ages-.

Why Free software needs to beat MSFT feature to feature? After I used MultiEdit for 10 years, I found VS very clunky and feature-poor. Notepad < VS < MEdit. Of course it took me years to become expert, and will take me years to become  such expert in vim, but it is just yet another reason pick tools carefully.

> This mentality that -everything that comes from MS is evil and stupid- and what this community has to offer -is waaaay better (even though its not)- .... The work that Microsoft has put into MSDN ... To write it off as -just boring stuff- ]

I never said MSFT is evil or stupid - they are clever in ways how to make money. Of course they put lot of work into MSDN - they paid lot of people to do stuff what noone is willing to do for free. Not even people like you who like it and need it: and yet you ask other people who don;t need it to do it for you, for free. How it does make sense?

> Why are so many people in this thread offended that Microsoft is actually one step ahead

MSFT is walking in different direction, using the fact that it can marshal thousand of doc writers to write docs in single repository and distribute it. Free software cannot compete there, obviously. Instead, we have zillions smaller repositories created by zillions volunteers, integrated by Google search.

BTW I am not sure why you think MSFT is ahead - Vista is a huge flop, while Free software is accelerating.

> 'we know they've got these things, but we can do something similar/better' would be alot more productive.

Who is 'we'? you? me? Linus?

It is your itch, you are responsible to fix what you want, not me. Or start a company and hire people to do it. Nobody owes you anything.

---

### Post by Lau_of_DK on 2008-04-25
> **rangalo said:**
> Hi,

It is not good to ask somebody to change the language if he finds a feature or two missing in the IDE.

I think eclipse (CDT) tries to provide a similar functionality. But if you are not satisfied with it, you can modify the eclipse cdt plugin. That's how free software works. You are a programmer, you can do it and make it better than ms visual studio. (May be you will need to learn Java)

Have a good time with reinstall/upgrade !

regards,
rangalo

I think youre right :)

Thanks alot.

(ps: deBootstrap has run for 2 hours now and is up to packages starting with "l" - could somebody hurry up these servers??? zzzZZZ)

---

### Post by lnostdal on 2008-04-25
> **Lau_of_DK said:**
> Now please: Dont take offense! But I think that this kind of mentality definately scares people away from Unix/Linux/OpenSource and everything in between. When I first made this thread I was hoping that somebody would step up and say -Well, if MS can do it, we can do it- or maybe -We've had those features for ages-. This mentality that -everything that comes from MS is evil and stupid- and what this community has to offer -is waaaay better (even though its not)- is silly and unhelpful to people looking to migrate to new platforms. The work that Microsoft has put into MSDN and the likes is actually an incredible feat which daily helps/assists many many developers across the globe. To write it off as -just boring stuff- is not the best way to go. IMHO :)


i'd like to know what you are looking for .. some concrete example instead of this sillyness .. for example, have you seen the man pages?

here is an online version of them:
[http://www.kernel.org/doc/man-pages/online_pages.html](http://www.kernel.org/doc/man-pages/online_pages.html)

..take socket stuff for instance .. here is an overview:
[http://www.kernel.org/doc/man-pages/online/pages/man7/socket.7.html](http://www.kernel.org/doc/man-pages/online/pages/man7/socket.7.html)
..and here is the socket function call..
[http://www.kernel.org/doc/man-pages/online/pages/man2/socket.2.html](http://www.kernel.org/doc/man-pages/online/pages/man2/socket.2.html)
..etc..

these are directly available in your terminal .. and also directly available in the editor/environment i'm using by a single keypress while editing code etc.

> **Lau_of_DK said:**
> 
Why are so many people in this thread offended that Microsoft is actually one step ahead of the opensources community in regards to creating development enviroments?


not really offended .. just annoyed and tired of this old not-true statement 

.. it is annoying to think that you think it is so - and that you almost "naturally" consider that everyone else(?) believes, or should know, it to be this way also

to be honest i wouldn't care if MS was in the lead in some places - and of course they already are .. but this is not the case here at all

---

### Post by CptPicard on 2008-04-25
> 
Why are so many people in this thread offended that Microsoft is actually one step ahead of the opensources community in regards to creating development enviroments?

As has been stated, no, it's not ahead. The scratches about dev environments have been scratched sufficiently, and I would say it has been done so that the need for the one IntelliSense example you stick to is irrelevant -- and that the existing implementations, where they are really needed because of the language, they are actually pretty good. It all really is as-is, and you do not have a warranty. If people want to use it, they use it. If they don't want to use it, they don't, or they get together to fix it. It's the morality of the community. Deal with it :)

Oh well, I am not repeating pmasiar and Wybiral above :p

> 
You know, before I joined this forum I considered myself quite gifted within communications - now: maybe not so much.

Helpful friendly hint -- you sound like a paid Microsoft shill who willfully doesn't have a clue... in a sort of Socratic sense though, I've got to give it to you ;)

> Im really sorry if you took my statement as a slap in the face

Nah, I didn't. But I want you to get the point why it can be construed as such, and why it provokes the responses it does from Lisp Gods like lnostdal who do not take insolence from mortals ;)

Whenever you're overlooking anything that isn't essentially C because people are, from your perspective, being just lazy losers and not in touch with the hardware, you *are* insinuating incompetence without demonstrating your own knowledge of what can actually be done with higher-level languages... quite the contrary, you seem ignorant. To prove your argument you'd have to essentially disprove the expressiveness of the high level, which seems like nonsense -- it is too restrictive an argument to be tenable. For people who *can do low level but won't because they know better from experience*, it does sound arrogant and it's like begging to be slapped.

The low-level is just a subset that is sometimes in practise called for. Otherwise, there is no need to go there as there is nothing intellectually special there, just needless, brainless manual labour that is better handled by the machine. That is what it is there for, so that you can actually make use of your mind where it is put to best use. Let the engineers figure out how to actually build hardware for your software -- it is not our problem ;)

> it was not meant to be anything other than me raising a concern and primarily a concern in regards to myself: I do not want to loose touch with lowlevel programming.

The low level is there when you need it. I was pretty much blown away when lnostdal showed me how SBCL can just disassemble a function into assembly straight into an Emacs buffer.

But I do not understand  what is so special with low level programming... it's just a very rudimentary register machine. Why do you like it? What is there that is intellectually interesting? What is there that lets you actually do something except write low level code as a matter of principle?

I mean... low level is simple... it is... but it's also a lot of work.

> Regarding your thread on BLOW YOUR MIND - Im absolutely struggling to understand the concept and the code that is discussed - I might return with (many) questions.

Yeah, exactly. I struggled getting it to work, too, more than I should have just for a single forum post. But it gives you a flavour of what is possible... 

A short explanation: This is co-operative multitasking with continuations passing execution to each other. A continuation is a sort of generalized return statement... you can repeatedly return to any point in code where you "save" a continuation (essentially an entire execution stack, from C perspective) by using call/cc. Continuations are a primitive that you shouldn't use all the time (and probably can't, if you're not a space alien) because of their obscurity, but... that can be very strong in select circumstances, when used carefully.

A call/cc just simply grabs your "program state" as far as your "stack" goes into a variable. You can have as many of them as you like, so essentially if you wanted to code this in C, you'd have to code a so called "spaghetti stack"... actual implementations do this by stack copying. In Scheme I was able to totally abstract co-operative multitasking and result "interweaving" by sticking it all in the print function... my trivial inorder recursion doesn't know *anything* of what is going on.

Try that in C, with similar level of modularity... you could simulate it with threads, admittedly... but it would involve a lot of synchronization. This code is actually single-threaded. And this is just a trivial example. And oh yeah, count the number of lines of code ;)

---

### Post by Lau_of_DK on 2008-04-25
> **pmasiar said:**
> 

I never said MSFT is evil or stupid - they are clever in ways how to make money. Of course they put lot of work into MSDN - they paid lot of people to do stuff what noone is willing to do for free. Not even people like you who like it and need it: and yet you ask other people who don;t need it to do it for you, for free. How it does make sense?


Well - I didnt really look at it like that :)

> **pmasiar said:**
> 
MSFT is walking in different direction, using the fact that it can marshal thousand of doc writers to write docs in single repository and distribute it. Free software cannot compete there, obviously. Instead, we have zillions smaller repositories created by zillions volunteers, integrated by Google search.

BTW I am not sure why you think MSFT is ahead - Vista is a huge flop, while Free software is accelerating.


I agree on Vista, I wouldnt install it even if they paid me. (depending on the fee of course). But my request wasnt for an OS, just an enviroment suite which provide as much support to the programmer as Visual Studio and in this regard, I do consider them a bit farther up the road than the opensource community.


> **pmasiar said:**
> 
Who is 'we'? you? me? Linus?

It is your itch, you are responsible to fix what you want, not me. Or start a company and hire people to do it. Nobody owes you anything.

I guess you and I understand the concept of a community a little differently. I never claimed anybody owes me anything, but Im looking at the task of getting more people to join the community by switched to Ubuntu/Linux. In this regard you and I are in the same boat, so to speak.


> **Wybiral said:**
> You're looking at this wrong. I'm not offended... Because I don't actually believe that MS is one step ahead of us just because they have bloated, over-featured, development tools for crappy languages.

Im getting the picture now: The languages arent top notch, I can ALMOST agree to that - but looking strictly at the enviroment VS provides, its in a league of its own. If you had a similar thing, as feature rich, as stable, as intuitively easy to use in Ubuntu, I think you would see hordes of developers switching.

> **Wybiral said:**
> 
Remember the "itch and scratch" development model? You're the one with the itch, so why do you expect us to scratch it?

I think there's a world of Windows developers itching, but maybe its just me. In that case I would still appreciate a little scratching :)

> **lnostdal said:**
> i'd like to know what you are looking for .. some concrete example instead of this sillyness .. for example, have you seen the man pages?


No - Not looking for more man pages. I was looking for a tool which in the blink of an eye could open up the classes of new languages to me, making them easily discoverable and easy to dive into. 


> **lnostdal said:**
> not really offended .. just annoyed and tired of this old not-true statement 

.. it is annoying to think that you think it is so - and that you almost "naturally" consider that everyone else(?) believes, or should know, it to be this way also


Now honestly and just between you, me and the forum: Youre not very experienced in developing in VS right? I dont mean this is a negative way, but you kinda give the impression that you dont know what youre talking about and now you've set up Microsoft as your target and are gunning for them. If that assumption is correct then you could benefit from either not engaging in discussions regarding Microsoft products, or alternatively (which I wouldnt recommend) start using them on a daily basis so you get to know them intimately. And again: This is spoken in a friendly tone, not to upset anyone.

/Lau

---

### Post by Lau_of_DK on 2008-04-25
> **CptPicard said:**
> 
Nah, I didn't. But I want you to get the point why it can be construed as such, and why it provokes the responses it does from Lisp Gods like lnostdal who do not take insolence from mortals ;)


Hmm, so youre saying that where arrogance reigns, humility is needed? Im all for that :)

> **CptPicard said:**
> Whenever you're overlooking anything that isn't essentially C because people are, from your perspective, being just lazy losers and not in touch with the hardware, you *are* insinuating incompetence without demonstrating your own knowledge of what can actually be done with higher-level languages... quite the contrary, you seem ignorant. 

I am ignorant - Im extremely ignorant. Reading many of the links that have been posted in this thread about Lisp, Python and Paul Graham as well as your wisdom and others Im realising how much Im missing out on by holding fast to this old C/C++ mentality. So Im reading up on Lisp as we speak!

> **CptPicard said:**
> 
The low-level is just a subset that is sometimes in practise called for. Otherwise, there is no need to go there as there is nothing intellectually special there, just needless, brainless manual labour that is better handled by the machine. That is what it is there for, so that you can actually make use of your mind where it is put to best use. Let the engineers figure out how to actually build hardware for your software -- it is not our problem ;)


Well - I agree and I dont, in a way. I have definately had my eyes opened to the fact that when programming in C++ you spend oceans on time on stuff that the language itself should just have given you as a free gift, and that realisation bugs me to pieces after having used C/C++ for almost 10 years! But I also imagine that people who only know hhl run into situations where they need special I/O functions or such to complete projects and they cant make these functions without the ability to do some low-level programming. I just dont want to be in that situation.

> **CptPicard said:**
> 
The low level is there when you need it. I was pretty much blown away when lnostdal showed me how SBCL can just disassemble a function into assembly straight into an Emacs buffer.


What? Link? I want to see :)


> **CptPicard said:**
> 
Yeah, exactly. I struggled getting it to work, too, more than I should have just for a single forum post. But it gives you a flavour of what is possible... 


Alright - after your explanation Im fully amazed. It does blow my mind. Making the maze come together in a stable form in C++ would have taken 50x times that code. Its amazing.

/Lau

---

### Post by Lster on 2008-04-25
Really, I must say I loved MS Visual Studio. Of course now I have switched to Python and GEdit which I am very happy with. But, I remember finding the intellisense feature extremely useful and it definitely speed up development for me.

The feature's usefulness is, of course, an opinion. The statement "Microsoft is technologically behind" (or "ahead") is so subjective that it's almost useless debating. ;)

My own opinion, as hinted at, is Microsoft are ahead on that front.

---

### Post by lnostdal on 2008-04-25
> **Lau_of_DK said:**
> 
No - Not looking for more man pages. I was looking for a tool which in the blink of an eye could open up the classes of new languages to me, making them easily discoverable and easy to dive into. 


I'm not sure what you mean, but I'm able to get the API information and other things I might need presented to me in various ways at rate that *by far* surpasses the rate in which I'm able to parse and understand it.

If you're somehow able to fully read and understand these things:

* [http://www.kernel.org/doc/man-pages/online/pages/man7/socket.7.html](http://www.kernel.org/doc/man-pages/online/pages/man7/socket.7.html)
* [http://www.kernel.org/doc/man-pages/online/pages/man2/socket.2.html](http://www.kernel.org/doc/man-pages/online/pages/man2/socket.2.html)
* ..and the things they link to that you might need..

..in a "blink of an eye" you cannot be human.

Others have talked about other languages and environments, so I will mention that via Slime (Common Lisp) I am also able to get context information, usually small reminders; all that is needed really, at the "blink of an eye". These things show up as I type, and more information is available at the press of a single key. I would _not_ want things to pop up totally automatic thus covering precious code context and screen space, but *if* I did I could configure my "IDE" so this would happen. If you want this, go find it or configure it yourself.

I also have:

* normal auto-completion

* fuzzy-completion and numerous other completion mechanisms

* form-completion (entire blocks of code are "completed" as small templates for me to fill in), 

* code folding (i never liked this, but never mind ..)

* definition lookup .. at the press of a single key i can navigate directly to the definition of a function, class, variable, method or even to a point of instantiation of a given instance .. i can keep pressing a key to navigate "further in" in nested functions that call other functions etc. .. with another key i navigate backwards in this "stack" of jumps inwards

* since the compiler and standard library itself is implemented by an open source, uh, implementation - i am able to do this with code that is part of the standard or implementation itself also

* i can browse and view class hierarchies

* i can with a single keypress get the ASM of any function or code presented to me

* i can expand macro calls, and if they in turn also contain calls to other macros i can expand them too and "further inwards" .. i can expand them inline flowing naturally with the "normal code", or have the expansion pop up in a new buffer

* i can determine who calls a function/method, who references a variable, who sets a variable, and what methods exists for a given class .. i get a navigable list with these things

* i can directly switch to a different currently running thread of execution and do all of these things there .. at runtime or compile-time, it doesn't matter

* i can profile already running code and get results presented to me in various ways .. time taken, %, number of calls, amount of memory "consed" while running said function .. etc.

* a whole bunch of other stuff i've forgotten now


..and I am able to do all of this with something that is running on some machine/server/whatever on the other side of the world -- and I do this *all the time*.


> **Lau_of_DK said:**
> 
Youre not very experienced in developing in VS right?


..and you're not very experienced in developing under a oss/gnu/linux environment, right?

I fly -- you drive.


[quote=Lau_of_DK]
I dont mean this is a negative way, but you kinda give the impression that you dont know what youre talking about and now you've set up Microsoft as your target and are gunning for them. If that assumption is correct then you could benefit from either not engaging in discussions regarding Microsoft products, or alternatively (which I wouldnt recommend) start using them on a daily basis so you get to know them intimately. And again: This is spoken in a friendly tone, not to upset anyone.
[/QUOTE]

This is just nonsense.

---

### Post by Lau_of_DK on 2008-04-25
> **lnostdal said:**
> 
* definition lookup .. at the press of a single key i can navigate directly to the definition of a function, class, variable, method or even to a point of instantiation of a given instance .. i can keep pressing a key to navigate "further in" in nested functions that call other functions etc. .. with another key i navigate backwards in this "stack" of jumps inwards


That sounds like sweet, I will be giving Slime a whirl once I get Ubuntu installed again.

> **lnostdal said:**
> 
* i can browse and view class hierarchies


As in you can also discover which classes/methods/properties are available at any given time for any given object?

> **lnostdal said:**
> 
* i can with a single keypress get the ASM of any function or code presented to me


How do you benefit from this exactly, how do you use it?

> **lnostdal said:**
> 
* i can profile already running code and get results presented to me in various ways .. time taken, %, number of calls, amount of memory "consed" while running said function .. etc.


And this is all Slime you say?


> **lnostdal said:**
> 
..and you're not very experienced in developing under a oss/gnu/linux environment, right?

I fly -- you drive.


Exactly right - the point is though: I wanna fly.

> **lnostdal said:**
> 
This is just nonsense.

Re-read it.

---

### Post by Wybiral on 2008-04-25
> **Lau_of_DK said:**
> I think there's a world of Windows developers itching, but maybe its just me. In that case I would still appreciate a little scratching :)

My point was why don't YOU take something like Eclipse and scratch your own itch from there. There is so much open code laying around, if you aren't satisfied, fix it...

---

### Post by skeeterbug on 2008-04-25
The more you do Python, the more you can't stand to do things in C#. At work we have this script that kicks us an email when a user views a flash movie we have on our site (it emails us their IP, the date they viewed it, and their name via querystring if the link was sent via email from our sales team). A manager wanted it modified so it automatically queries a WHOIS database, and puts that information in the email (saving a manual step). We are typically a C# shop, we have internal scripts running in python/perl, however. Anyways, within 5 minutes I had a proof-of-concept done:

```

import urllib
from HTMLParser import HTMLParser

class WHOISParser(HTMLParser):

    def __init__(self):
        HTMLParser.__init__(self)
        self.inPre = False
        self.preData = ""

    def handle_starttag(self, tag, attrs):
        if tag == "pre":
            self.inPre = True
            
    def handle_endtag(self, tag):
        if tag == "pre":
            self.inPre = False

    def handle_data(self, data):
        if self.inPre == True:
            self.preData += data

if __name__ == "__main__":
    param = urllib.urlencode({'queryinput' : '207.170.145.22'})
    opener = urllib.urlopen('http://ws.arin.net/whois', param)
    html = opener.read()
    parser = WHOISParser()
    parser.feed(html)
    parser.close()
    print parser.preData

```

This proof of concept was pretty much ready to go for the mod_python script. I had to make a few minor adjustments (get the IP from mod_ptyhon, added some basic exception handling). This all comes from the standard library. The script posts some data to a web form, and parses the <pre> tag for the results.

How would you do this so quickly in C#? It doesn't come with an HTML parser, and it's XML parser won't do the job.

```

WebClient client = new WebClient();
            client.QueryString.Add( "queryinput", "207.120.135.10" );
client.Headers.Add( "user-agent", "MSIE 7.0" ); 
            
StreamReader sreader = new StreamReader( client.OpenRead( "http://ws.arin.net/whois" ) );

//Head to google and start searching for an HTML parser

```

This is why Python rocks my boat. :)

---

### Post by Lau_of_DK on 2008-04-25
Man... Python just rocked my boat a little bit too.

Thank you for that very cool, easy to follow, example!

---

### Post by Can+~ on 2008-04-25
> **Lster said:**
> Really, I must say I loved MS Visual Studio. Of course now I have switched to Python and GEdit which I am very happy with. But, I remember finding the intellisense feature extremely useful and it definitely speed up development for me.

The feature's usefulness is, of course, an opinion. The statement "Microsoft is technologically behind" (or "ahead") is so subjective that it's almost useless debating. ;)

My own opinion, as hinted at, is Microsoft are ahead on that front.

And why not Eclipse with python, as someone posted? I've been trying it, although I'm not too fond of big-*** IDEs, I liked it.

---

### Post by Can+~ on 2008-04-25
> **Lau_of_DK said:**
> Man... Python just rocked my boat a little bit too.

Thank you for that very cool, easy to follow, example!

Another example, generator expressions:

[PHP]#!/usr/bin/env python

#sum of the squares of all odd integers to n

n = 5
nsum = sum(i*i for i in xrange(1, n+1, 2))

#n = 5 should produce 1^2 + 3^2 + 5^2 = 1 + 9 + 25 = 35
print nsum #returns 35[/PHP]

Why python rocks my boat:
-Garbage collection
-Generator expressions
-Custom iterators, or with yield statement.
-Decorators

But mostly, it must be the lightweight syntax, I don't like the something.something.something.doSomething(something);

---

### Post by Lau_of_DK on 2008-04-25
Powerfull stuff, pretty much a new way of thinking.

Anybody able to reproduce that last generator example in Lisp?

---

### Post by pmasiar on 2008-04-25
Lau, I am glad I was mistaken in you - originally I thought you are returning troll [?_?], flamewars with whom cost me some infraction points :-) but seems that you are different, you genuinely want to understand **how** Free software community is different, and **why**. So I'll give you couple links to read and enhance your understanding. 
> **Lau_of_DK said:**
> Well - I didnt really look at it like that :)

But the only way to look at software development is through money. Free and Proprietary software are fighting 'war' about which rules will govern [http://en.wikipedia.org/wiki/Noosphere](http://en.wikipedia.org/wiki/Noosphere) .

[rms ](http://en.wikipedia.org/wiki/Stallman) explained in in his [The Right to Read dystopia](http://www.gnu.org/philosophy/right-to-read.html). 
- **how** it works: [The Cathedral and the Bazaar](http://catb.org/~esr/writings/cathedral-bazaar/) - while there, read also about **why**: Homesteading the Noosphere and [http://en.wikipedia.org/wiki/Gift_economy](http://en.wikipedia.org/wiki/Gift_economy)

Of course to understand strategy of the struggle, [http://en.wikipedia.org/wiki/Sun_Tzu](http://en.wikipedia.org/wiki/Sun_Tzu) has it covered: victory is in attacking weakness of your opponent (while defending your weak point adequately). You cannot win by defending.

> you and I understand the concept of a community a little differently. I never claimed anybody owes me anything, but Im looking at the task of getting more people to join the community by switched to Ubuntu/Linux.

Yes, but we cannot win by providing the same, competing point to point in features like centralized docs, because doing that FOSS will attack strong points of MSFT with weak points of FOSS, and you cannot win doing that. There isn't one single centralized agency governing FOSS. Anyone can contribute, and best code wins. MSFT is intelligent design, FOSS is evolution.

> but looking strictly at the enviroment VS provides, ... as feature rich, as stable, as intuitively easy to use in Ubuntu, I think you would see hordes of developers switching.

No. 
1) knowledge of VS is not inborn. You have to learn it, and frankly for me, after using other richer editors, VS is painfully dull, and rather unintuitive.
Often I felt that developers decided 'this is good enough for those morons' or 'forget about it, that feature is too advanced and confusing for those morons' and they slacked. 
2) People who like VS and don't want learn and change will keep VS. Let them have it. No need to convert them, bring them kicking and screaming - MSFT can have those morons :-)
3) People who are willing to learn, (or start with Linux) will see improved productivity from using tools customized **to their own needs**, and will help others. Rest of them will pay MSFT tax until they die off or learn better. It is also about value of person's time: if someone can charge $500/hr, why waste 10 hours to learn Free software if you can upgrade for $100 - 6 minutes of billed time?

> I think there's a world of Windows developers itching, but maybe its just me. In that case I would still appreciate a little scratching :)

Then pick a project which is closest to what you like to have, get sources, and start adding what is missing. If it is good, it'll get accepted; if not, only your own time is wasted, but progress of the  rest of FOSS continues.

---

### Post by lnostdal on 2008-04-25
in lisp it could be anything you want .. like:

```

(sum-of (iterating :with i :from 1 :to 5 :stepping 2 :collecting (* i i)))
=> 35

```

..or instead of building up a list, then returning it to some function
that iterates it and sums up a result .. you can sum as you go:

```

(iterating :with i :from 1 :to 5 :stepping 2 :summing (* i i))
=> 35

```

don't like it? .. invent your own way of doing (edit: or _expressing_) this .. the language is programmable .. anything you want really

edit:
here is one using plain old loop:
```

(loop :for i :from 1 :to 5 :by 2 :summing (* i i))
=> 35

```

---

### Post by CptPicard on 2008-04-26
> **Lau_of_DK said:**
> 
Anybody able to reproduce that last generator example in Lisp?

Scheme, the "kind of minimalist Lisp" I wrote the continuations example in that I referred you to, has the "yield" as a built-in function (it can be done to implement what are called "lazy lists" that only evaluate the "rest of list" on demand as needed but not before). Interestingly, generators are just a sort of special case application of continuations -- you can write "yield" when you have continuations, although Python for example doesn't have real continuations, but has otherwise-implemented generators.

However, Common Lisp actually lacks continuations, and I have been a bit worried about that not because I would use continuations, but because it may imply the lack of generators... lnostdal, I haven't really come across a generator in CL yet... I suspect CL doesn't have yield and implements lazy lists as some kind of a generating closure object?

Also I have to warn that I may be totally wrong here and that yield can be implemented in terms of some kind of closure... which is probably the case, as Python does not support continuations and we could implement Python in CL and we'd have yield... and that the continuation implementation of yield is just another way to get the same effect.

---

### Post by Lau_of_DK on 2008-04-26
> **pmasiar said:**
> Lau, I am glad I was mistaken in you - originally I thought you are returning troll [?_?], flamewars with whom cost me some infraction points :-) 

PMAsiar - What an incredible interesting post. Took me a while to cover some of the material you posted though. The essay about the SPA was actually scary reading.

And you know - I think I was wrong about you too. Based on your statements and avatar I thought you were a Jedi turned Dark Side who was looking for my blood - I was wrong right? :)

Lastly. I think the depth of this community is quite and amazing and unique thing. Some time ago I spent many years studying Martial Arts, chinese in particular. And although I do not believe you will find 'all truth' in the eastern philosophies, youve definitely convinced me that there is no point in going toe-to-toe, feature-to-feature with Microsoft. That would be a step backwards and in the wrong direction.

Thank you for your post, it was great reading.

---

### Post by pmasiar on 2008-04-26
> **Lau_of_DK said:**
> Based on your statements and avatar I thought you were a Jedi turned Dark Side who was looking for my blood - I was wrong right? :)

My avatar means 'Python is your source of Jedi power' - I stole it from the cover of Turbogears book. :-)

> And although I do not believe you will find 'all truth' in the eastern philosophies

Of course not - but just one example, as I was rereading Sun Tzu yesterday: You never announce enemy about coming attack. This is what exactly was done in Iraq (in Falluja), and attack cost more than 100 US GI lives, and Falluja was completely destroyed (ppl live still in tents). Sun Tzu is REQUIRED READING for all officers, so now you can see what is their opinion on Rumsfield (who was Air officer, bomber pilot in Vietnam). One general told it succintly: "officers are trained to hit the target. Generals are trained to win the war". 

Sun Tzu said something like: 'Good general is liked in empire because he won great battles. Excellent general is not appreciated because he won too easy, without great battles.' :-)

Now imagine that Sun Tzu, wisdom of bronze age, is still not understood, even ignored, by the self-proclaimed "leader of the free world" in 21st century.

---

### Post by LaRoza on 2008-04-26
> **pmasiar said:**
> My avatar means 'Python is your source of Jedi power' - I stole it from the cover of Turbogears book. :-)

I never knew what it was. Now it makes so much sense...

---

