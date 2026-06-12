---
title: "C/C++ Pseudo-Deprecated for Standard Application Development?"
date: 2008-04-27
forum: Programming Talk
---

### Post by JupiterV2 on 2008-04-27
After reading post after post about using Python I decided that, for educational growth at they very least, I must learn Python. C and C++ were the first languages I've learned. I'm starting with "Diving into Python" and am enjoying learning the language so far.

The main reason I've stuck with C and C++ is twofold: a) I come from a MS Windows (shudder) background where 100% of commercial and the majority of non-commercial software is C/C++/C#/,NET derived, and by extension; b) I've worked under the (likely misinformed) delusion that all programs must be in binary form.

A post on finding a python script to binary conversion program sparked the same dogma's engendered in me by MS: A "real" program must only be in binary/executable form (linked libraries and other resources aside)!

However, as most of you who patrol these boards know, this perhaps is not the case. A good number of programs have been written in python, perl, et al. "Diving into Python" will, I hope, finally break the yoke thrown over my back and allow me to stand tall and walk confidently under the new light we call...Ubuntu. :)

All this made me think though: Are the days of writing standard applications using C++ or C, bogging down development unnecessarily, numbered? Is using Python/Perl/etc to be the de-facto platform for developing applications?

I know, of course, that C/C++/etc isn't going to die out. The majority of operating systems are written in C-derived languages. It's the same why ASM hasn't died. They have their place. However, using an interpreted language seems to have all the speed and faster productivity when developing apps where the granularity of speed, that extra nano-second here and there, will make all the difference to the end user, is inconsequential in anything but kernel development or other such tasks.

What do you guys think? Is this even the case with Linux/Unix/Etc? Should binaries, for the most part, become extinct?

If not, what is the value in still using compiled languages where the end result is a binary?

---

### Post by Ferrat on 2008-04-27
The value is simple, higher performance some things just need the speed, also say you lose a few seconds here and there (on every program you have running), it adds up and why waste cpu power and memory etc, I'm a bit of a minimalist but to me the fact that many programmers don't even think in terms of making their programs more effective and as small / fast as possible is a waste. 

I agree that interpreter languages has their uses, for fast development etc but to replace compiled languages? I wouldn't want it anyway.

---

### Post by scourge on 2008-04-27
> **JupiterV2 said:**
> All this made me think though: Are the days of writing standard applications using C++ or C, bogging down development unnecessarily, numbered?

I don't think anyone can say that with a straight face, and at the same time use these great modern deskop apps like, well, most of what's included in a default Ubuntu installation.


> Is using Python/Perl/etc to be the de-facto platform for developing applications?

Python and Perl aren't in the same ballpark when it comes to developing for the desktop (you don't want to use Perl for that). Python will probably gain more popularity, and it probably should, but I don't think any language is ever going to be the best for everyone and everything.

---

### Post by samjh on 2008-04-27
> **JupiterV2 said:**
> The main reason I've stuck with C and C++ is twofold: a) I come from a MS Windows (shudder) background where 100% of commercial and the majority of non-commercial software is C/C++/C#/,NET derivedStatistically, Visual Basic is the most commonly used software for in-house business applications and some commercial ones. Perhaps that explains the ridiculously low standards of some in-house software, but I digress... ;)

> All this made me think though: Are the days of writing standard applications using C++ or C, bogging down development unnecessarily, numbered? Is using Python/Perl/etc to be the de-facto platform for developing applications?Nay.

C/C++ will take at least a decade or more to die out.  C++ will probably die out sooner than C, as evidenced by some statistics which show much sharper decline in C++ popularity than C.

Despite the proclamations about the obsolescence of C/C++, they still hold the edge in performance, executable size, and code security.

The most likely outcome is that scripting languages will be dominant for higher-level application programs like web applications, office applications, media software accessories, and for building extensions to software (ie. plugins).  However system software, operating system utilities, anti-virus/spyware, cryptographic software, and multimedia applications, are likely to continue using C/C++.

There is also uncertainty about the future of computing itself.  Web applications are on the rise at the moment, but I think in the 2010-2020 era, there will be marked increase in embedded computing.  More specifically "ubiquitous computing" will probably end up as a powerful force, and so we may actually see lower-level languages become more popular rather than less.  Or if not lower-level languages, then higher-level languages with embedded capabilities (eg. Lua).

---

### Post by pmasiar on 2008-04-27
There is no reason to C to die out, exactly as ASM never died out. It is just not used as often as a generation (of programmers - 25 years) ago, because speed/effectiveness gained by it's use is not worth the complexity anymore. So will be with C: Instead of writing whole app in C, you do prototype in Python and recode 5% of time critical code as C library, easily linked to Python.

So instead C being tool of first choice, Python (or other dynamically typed language) will replace it, and C will become weapon of last resort.

---

### Post by Wybiral on 2008-04-28
C should remain as the language of kernels-hacking and library writing, but C++... C++ doesn't do well for interfacing with other languages and offers no speed increase over C. So much software is built upon C that it's safe for a long time (unless a better, simple, low-level language ever comes along), but C++ is on the line. It doesn't fill any real gap of necessity and isn't as firmly rooted in most systems... Hopefully it will die quietly soon :)

---

### Post by vexorian on 2008-04-28
C++ and C are mostly the same thing only that C++ reduces some issues, new beats malloc all day. As a matter of fact, C is mostly a subset of C++ , so if one remains popular the other will as well.

So go ahead and stick to C(++), C for libraries and C++ for apps, you'll be fine. The big corps wants every programmer outside an elite to go towards other languages that are not as powerful under the promises that they are friendlier or that they make development time faster, the reason is that they'll want a monopoly on core stuff, however, after ages of trying to remove C(++) and replace them with toy languages, they have failed.

C++ has survived Java, .net, python, many others and countless of "polls" in which it is apparently less popular. I really see unlikely that it will go away anytime soon, and even calling it pseudo-deprecated is an over-statement. Besides, the C++0x standard is coming ... It is just C with more abstraction capabilities anyways, the best of both worlds.

Anyways, look at the apps included in ubuntu, besides of the few Novell and Microsoft's love children that are made in .net, everything else is in one C or the other.

---

### Post by Wybiral on 2008-04-28
> **vexorian said:**
> C++ and C are mostly the same thing only that C++ reduces some issues, new beats malloc all day. As a matter of fact, C is mostly a subset of C++ , so if one remains popular the other will as well.

So go ahead and stick to C(++), C for libraries and C++ for apps, you'll be fine. The big corps wants every programmer outside an elite to go towards other languages that are not as powerful under the promises that they are friendlier or that they make development time faster, the reason is that they'll want a monopoly on core stuff, however, after ages of trying to remove C(++) and replace them with toy languages, they have failed.

C++ has survived Java, .net, python, many others and countless of "polls" in which it is apparently less popular. I really see unlikely that it will go away anytime soon, and even calling it pseudo-deprecated is an over-statement. Besides, the C++0x standard is coming ... It is just C with more abstraction capabilities anyways, the best of both worlds.

Corporate conspiracies? Well established languages like Python/Lisp/Ruby/Java are just "toy languages"? Really? 

The C++0x standard looks ... interesting ... but it's all just fixing problems that the language itself is causing (and not fixing the big, obvious problems which are too core to the language). I see no point...

Either you need kernel/library level, fast binary code (in which case C is the standard choice, you generally don't need the rest of the C++ baggage at that level and C++ doesn't play well with others in terms of interfacing), or you need lightning-fast development speed... In which case dozens of other languages are better than C or C++ (Python, Lisp, Ruby, heck... even allows Java removes more headaches than C++).

If you need both, you use both (write C modules for your higher-level languages), but C++ is the worst of both worlds, not the best ;)

---

### Post by Natr0n on 2008-04-28
> **vexorian said:**
> ...new beats malloc all day.
Why?
> The big corps wants every programmer outside an elite to go towards other languages that are not as powerful...
How are the "other languages" less "powerful"?

---

### Post by jespdj on 2008-04-28
> **vexorian said:**
> C++ and C are mostly the same thing only that C++ reduces some issues,
And [adds a whole bunch](http://www.yosefk.com/c++fqa/?r=t) of new issues...

> **vexorian said:**
> new beats malloc all day.
Really? How?

> **vexorian said:**
> So go ahead and stick to C(++), C for libraries and C++ for apps, you'll be fine. The big corps wants every programmer outside an elite to go towards other languages that are not as powerful under the promises that they are friendlier or that they make development time faster, the reason is that they'll want a monopoly on core stuff, however, after ages of trying to remove C(++) and replace them with toy languages, they have failed.
A corparate conspiracy theory? What nonsense. Especially if you're a software developer I'd expect you to think in a more rational way. The simple fact is that time is money, and software development is expensive because it costs a lot of time. If you can write software in a different language than C++ so that it costs much less time to write and works just as well, then it's obvious that you'd use that other language.

And calling other languages such as C#, Java, Python or Ruby "toy languages" shows that you don't have a very realistic view of software development in the real world.

I agree that C is certainly not going to go away anytime soon. It will remain the most important lower-level programming language for many years to come. I don't know about C++. It probably won't disappear soon, but it has many clear disadvantages compared to more modern object-oriented programming languages, of which speed of development is only one.

---

### Post by JupiterV2 on 2008-04-28
You guys are really starting to hit a key point I was trying to explore with this thread. For a long time I have labored under the idea that C and C++ were the only "real" languages to learn and the rest were just "filler," or perhaps tools suited only to specific jobs (like web-development).

Generally, all I'd ever read was that C++ was C but better! After perusing through many threads on these forums, this one included, and reading a few essays on the pitfalls of C++ I'm starting to realize my faith may have been misplaced in the language. I know I've learned something from it and that I'm coming away with something but I definitely feel a little disillusioned. It was when I began to learn GTK+ that I began to wonder why it was ever written, and persists to be, in C rather than C++. (Yes, I know there are C++ bindings via GTKmm).

As I continue to learn Python I'm starting to find that I wish I'd learned it from the beginning. As I continue to learn and grow (Let's be honest, I'm still a novice) I find more and more things to continue learning. I'm writing a "flash card" styled vocabulary builder to help increase vocabulary in foreign languages. As I continue to try and solve problems I find better and better tools to use, like using an XML format for data storage rather than parsing plain text (not that CSV doesn't still have its place), or Python for the main program and using pyGTK for the interface, or even using Glade to build the interface and inserting the resources into the project, or better yet using GNU auto-tools for compiling/packaging my program. All these tools have made my life easier and easier.

I've now written a road map of things/languages I'd like to learn to increase my arsenal for solving problems in the most efficient way. Meanwhile, I'm going to keep plugging away.

However, back to where we started. There seems to be some definite value in continuing to grow with C for writing libraries and other play-nice code. There also seems to be real value in learning other languages like Python, Lisp, and XML (its a markup language rather than a programming language, I know). The real question then, is there any value with continuing to write programs in C++? 

C clearly has its use, but does C++? Are there situations where C++ would be better than C, Python, or any other language?

---

### Post by henchman on 2008-04-28
Do you think that D will play any role in the 'programming languages battle'?

What i've read so far sais that D is as fast as c++ while it looks (at least to me) like a modern programming language like c# or so...

---

### Post by LaRoza on 2008-04-28
> **henchman said:**
> Do you think that D will play any role in the 'programming languages battle'?

What i've read so far sais that D is as fast as c++ while it looks (at least to me) like a modern programming language like c# or so...

D looks like it will continue to grow. It seems to be what C++ should have been.

It is #12: [http://www.tiobe.com/index.php/content/paperinfo/tpci/index.html](http://www.tiobe.com/index.php/content/paperinfo/tpci/index.html)

---

### Post by pmasiar on 2008-04-28
XML is not a solution - it is another problem :-)
Try YAML for notation as readable as Python.

I don't know how complicated structure you have, but plain text/tab delim is often all what is needed. Or just use list of dict literals for your data.

---

### Post by mssever on 2008-04-28
> **JupiterV2 said:**
> like using an XML format for data storage
I very much prefer [YAML]("http://yaml.org") over XML except in cases where YAML is inadequate (there aren't many of those). Note that YAML's homepage is formatted as YAML, and yet it's perfectly readable.

---

### Post by CptPicard on 2008-04-28
> **Ferrat said:**
> I'm a bit of a minimalist but to me the fact that many programmers don't even think in terms of making their programs more effective and as small / fast as possible is a waste. 


Oh, I think of that all the time. The art and science I use to do that is called Algorithmics, as small constant factors are beat by algorithmic solutions any day :)

HLLs just make those considerations so much easier, and even give you elements you would have hard pressed to get or code yourself in C.

---

### Post by samjh on 2008-04-29
> **JupiterV2 said:**
> C clearly has its use, but does C++? Are there situations where C++ would be better than C, Python, or any other language?

C++ is still very relevant if you want to produce executable code that runs and conserves resources almost as well as C, while allowing the use of higher-level abstractions.  Games are the most visible examples of this demand (I'm talking commercial AAA titles, not hobbyist creations), as it is the kind of programming where object-oriented abstraction is ideal.

At the moment, a lot of game companies use C++ to write performance-intensive engines for their games, balancing execution performance with development speed provided by higher-level data structures and objects.  Then they implement designs that do not have stringent performance requirements (maps, campaigns, dialogues, user-interface, etc.) using scripting languages - most popular being Lua, with a handful using Python.

---

### Post by pmasiar on 2008-04-29
Another use of C++ I know about is automatic trading on Wall Street: analyze data stream in real time and give orders, and you want to beat other guys (analyzing same data) by ten miliseconds. Not a job for Java, but they use Python and Ruby for QA/testing.

---

### Post by stratavarious on 2008-05-02
.

---

### Post by scourge on 2008-05-02
> **stratavarious said:**
> So what?  C++ is a very relevant language and I would dare say most programmers will at the very least want to be somewhat acquainted with it.

You can be sure that C++ is not going away any time soon.

That's pretty much how I feel. People tend to think that there are two kinds of applications: those that need high performance (use C), and those that need a high level of abstraction (use Python). But one often needs both, and that's when C++ becomes a good choice. It's not always trivial to just write the performance-critical parts in C and the rest in Python, especially when you have a heavily object-oriented design and complex data structures.

With that said, I wish I could use Objective-C instead of C++. IMO it's what C++ should've been. If wxWidgets or QT4 ever get objc bindings, I'm never going to write my own projects in C++ again.

---

### Post by LaRoza on 2008-05-02
> **scourge said:**
> That's pretty much how I feel. People tend to think that there are two kinds of applications: those that need high performance (use C), and those that need a high level of abstraction (use Python). But one often needs both, and that's when C++ becomes a good choice. It's not always trivial to just write the performance-critical parts in C and the rest in Python, especially when you have a heavily object-oriented design and complex data structures.

With that said, I wish I could use Objective-C instead of C++. IMO it's what C++ should've been. If wxWidgets or QT4 ever get objc bindings, I'm never going to write my own projects in C++ again.

Or C and Python ;)

---

### Post by scourge on 2008-05-02
> **LaRoza said:**
> Or C and Python ;)

Yes, I did mention that possibility, and it's fine if you can isolate the performance-critical parts, and they are not too many. Writing a couple of Python wrappers in C is not too much work, but what if you had to write 50 of them just because you insist on using Python for the 30% of code that don't need to be optimized?

---

### Post by LaRoza on 2008-05-02
> **scourge said:**
> Yes, I did mention that possibility, and it's fine if you can isolate the performance-critical parts, and they are not too many. Writing a couple of Python wrappers in C is not too much work, but what if you had to write 50 of them just because you insist on using Python for the 30% of code that don't need to be optimized?

Well, Oblivion, a very large RPG find using Python to be useful (and C)

---

### Post by pmasiar on 2008-05-02
> **scourge said:**
> insist on using Python for the 30% of code that don't need to be optimized?

90% of the code does not need to be optimized.

Edit: It is consequence of fundamental rule of the Universe: 90% of anything is crap. And it is fine, world runs like that with no problems.

---

### Post by Wybiral on 2008-05-02
> **scourge said:**
> Yes, I did mention that possibility, and it's fine if you can isolate the performance-critical parts, and they are not too many. Writing a couple of Python wrappers in C is not too much work, but what if you had to write 50 of them just because you insist on using Python for the 30% of code that don't need to be optimized?

You don't have to "write" wrappers, there are tools that do that magically (like SWIG). And most likely, you'll throw all your C code in one or two modules and have SWIG wrap it all in a nice package.

---

### Post by Alasdair on 2008-05-02
> **LaRoza said:**
> Well, Oblivion, a very large RPG find using Python to be useful (and C)
IIRC Oblivion is almost entirely C++ (using [gamebryo]("http://en.wikipedia.org/wiki/Gamebryo")), except for gameplay scripts which are written in an incredibly simple basic-like scripting language. EVE online would be an example of major title that uses python.

---

### Post by LaRoza on 2008-05-02
> **Alasdair said:**
> IIRC Oblivion is almost entirely C++ (using [gamebryo]("http://en.wikipedia.org/wiki/Gamebryo")), except for gameplay scripts which are written in an incredibly simple basic-like scripting language. EVE online would be an example of major title that uses python.

I don't play such games, but I do know that some large commercial games use Python.

---

### Post by scourge on 2008-05-02
> **pmasiar said:**
> 90% of the code does not need to be optimized.

You don't think it depends on the application even a little? For example, take a look at this chess engine I wrote, called [Sloppy]("http://koti.mbnet.fi/~ilaripih/sloppy/"). Try replacing 90% of the code with something slow like Python, and see what happens to performance. I'd say that more than 50% of the code is performance-critical.

---

### Post by scourge on 2008-05-02
> **Wybiral said:**
> You don't have to "write" wrappers, there are tools that do that magically (like SWIG). And most likely, you'll throw all your C code in one or two modules and have SWIG wrap it all in a nice package.

Thanks, I wasn't aware of SWIG, I'll have to give it a try.

---

### Post by Asham on 2008-05-03
For applications like Gedit or Kate (not the heaviest apps) would their performance be noticeably slower had they been programmed in Python? Does this performance loss just affect startup times or GUI responsiveness too?

---

### Post by LaRoza on 2008-05-03
> **Asham said:**
> For applications like Gedit or Kate (not the heaviest apps) would their performance be noticeably slower had they been programmed in Python? Does this performance loss just affect startup times or GUI responsiveness too?

They are not very graphical, and the differences would be little I think for the most part.

The plugins are in Python.

IDLE is written in Python, and has no noticable speed issues, although tkinter isn't that pretty.

---

### Post by kknd on 2008-05-03
> **Asham said:**
> For applications like Gedit or Kate (not the heaviest apps) would their performance be noticeably slower had they been programmed in Python? Does this performance loss just affect startup times or GUI responsiveness too?

There would be a higher memory usage, but the responsiveness would be equal, since the GUI hard job would be done by GTK+ / QT.

---

### Post by Asham on 2008-05-03
I was afraid Python would suffer from drawbacks similar to Java on the desktop. Startup time and desktop integration with, eh, the desktop environment, is not quite there yet. Performance is good though but if the user experience fails to deliver many would prefer a better looking application. I know I would.

Thanks both for your replies.

---

### Post by dempl_dempl on 2008-05-03
LaRoza : Why is this thread still here?  For all of those having a bad day, they should go to **holy wars** section...

LaRoza, no matter what you say, deep down, you like the flaming, don't you ? :D  

Because I've had a very nice day, I'll be neutral today by not showing what you can do in C++ and you can't in Python  :) 
[for example decent version of **Visitor pattern** :P ] .



I'll quote Erick Bern:
> 
This is one of those things where all of those saying they're neutral, very soon show on which side they're neutral . 



Cheers!

---

### Post by Can+~ on 2008-05-03
> **dempl_dempl said:**
> Because I've had a very nice day, I'll be neutral today by not showing what you can do in C++ and you can't in Python  :).

I'm pretty sure there's a lot of things that you can do in C++ that you can't do on Python. As I'm pretty sure there's a lot of things that you can do in Python that you can't do in C++.

Assuming that your language can do everything, is simply wrong. It's like trying to say that my hammer can chop wood, so I don't need a saw. There's a tool for everything, and sticking to one means that you'll probably try to build a house just with a hammer; you will probably have a house, but everything smashed into place.

So instead of saying that "Oh, my language is superior since it has the _________ thing that is great.". I just go "I think I will use this language because it has ___________ that works in my case".

I finished reading the text about the guy that started [his own company with LISP](http://www.paulgraham.com/avg.html). And it's quite true. People just stick to a language, they were born and taught to eat C++ and it is the only thing, when there are other tools out there. You could take the speed of development as a huge plus in a competitive industry, rather than basing all on the speed of the application. Developing something faster is sometimes better than having an application that works fast, as users may never notice the difference, specially with modern hardware..

---

### Post by Wybiral on 2008-05-03
> **dempl_dempl said:**
> [for example decent version of **Visitor pattern** :P ]

Why do you think the visitor pattern isn't possible in Python?

---

### Post by LaRoza on 2008-05-03
> **dempl_dempl said:**
> LaRoza : Why is this thread still here?  For all of those having a bad day, they should go to **holy wars** section...

LaRoza, no matter what you say, deep down, you like the flaming, don't you ? :D  



It wasn't reported.

No, I don't like flaming.

---

### Post by dempl_dempl on 2008-05-03
> **Wybiral said:**
> Why do you think the visitor pattern isn't possible in Python?

There are few version of that pattern. Some are better than the others. 

The better ones , the ones which are more flexible and scalable, are only available in C++  . 

Check out the Book "Modern C++ design, Generic programming and design patterns applied" . I believe it's 10th chapter. Standard visitor has a bunch of flaws , hence it was always a subject to controversy . In this book you can see some new ideas ( the cool stuff ) about making it better. 
Book itself is not C++ - only book , everyone can learn something from reading it. 

You can find it here: 
[http://alas.matf.bg.ac.yu/~mr06184/stosha.net/doc/modern-c++.tar.gz](http://alas.matf.bg.ac.yu/~mr06184/stosha.net/doc/modern-c++.tar.gz)

Btw, I'm maybe bit on the C++ side, but I am really starting to like this Python. 

My job ( mostly ) is made of Data Mining and some pretty nice Search algorithms , and I use CLucene framework for some of the things. 

CLucene is port of Java's [Lucene ]("http://lucene.apache.org/java/docs/index.html")search engine framework. We use C++ version because it is , as you can guess, enough times faster :)  . 

But , the thing is, that PyLucene ( the port for guess-which-language ) , is actually faster than original Java version, although Python folks have a smaller team, and their primary concern is not speed , rather the compatibility with the original. I didn't believed in that , until I've checked that for myself.  I'll post benchmarking results soon enough. 
I'm pretty interested to see those things when I actually compile 
Python version ( is that possible? ) .

---

### Post by dempl_dempl on 2008-05-03
> **LaRoza said:**
> 

No, I don't like flaming.

Yeah , I know   .  I was just kidding  :) .

---

### Post by LaRoza on 2008-05-03
> **dempl_dempl said:**
> Yeah , I know   .  I was just kidding  :) .

So was I...

---

### Post by Wybiral on 2008-05-03
> **dempl_dempl said:**
> There are few version of that pattern. Some are better than the others. 

The better ones , the ones which are more flexible and scalable, are only available in C++  . 



Most implementations of the visitor pattern only require some sort of type dispatching system, which Python is fully capable of. But, this kind of design isn't as much of an issue in Python, since it's so dynamic. If I want an object to have a method it doesn't have, I'll just put it there, and if I want to get rid of it, I'll take it off. I don't have to devise some elaborate system to work around this.

```

from new import instancemethod

class Object:

    def __init__(self, data):
        self.data = data

obj = Object("some data here")
print dir(obj) # Before method

obj.get_data = instancemethod(lambda self: self.data, obj)
print dir(obj) # With method
print "Data is : '%s'" % obj.get_data()

del obj.get_data
print dir(obj) # After method is deleted

```

---

### Post by dempl_dempl on 2008-05-03
> **Wybiral said:**
> Most implementations of the visitor pattern only require some sort of type dispatching system, which Python is fully capable of. But, this kind of design isn't as much of an issue in Python, since it's so dynamic. If I want an object to have a method it doesn't have, I'll just put it there, and if I want to get rid of it, I'll take it off. I don't have to devise some elaborate system to work around this.

```

from new import instancemethod

class Object:

    def __init__(self, data):
        self.data = data

obj = Object("some data here")
print dir(obj) # Before method

obj.get_data = instancemethod(lambda self: self.data, obj)
print dir(obj) # With method
print "Data is : '%s'" % obj.get_data()

del obj.get_data
print dir(obj) # After method is deleted

```

It would be good idea reading the chapter I've suggested . 
 
You can't get the point if you don't . I'm fully aware of Python's dynamic types and stuff .  Python is our friend :D . 

And , as I've said, book I've suggested is not good only for C++ programmers. It's like Art of Programming, something for everyone, but no-one in particular ( or was that Eclipse :) ?  ).

---

### Post by pmasiar on 2008-05-03
> **dempl_dempl said:**
> Because I've had a very nice day, I'll be neutral today by not showing what you can do in C++ and you can't in Python  :) 
[for example decent version of **Visitor pattern** :P ] .

One view on patterns is that patterns are crutch which allows us to understand programs written by others. Dynamic languages use different kind of crutch.

I found [quite a few](http://www.google.com/search?q=visitor+pattern+python) articles about implementing Visitor in Python, each of them much shorter and easier to understand than C++ version in Wikipedia.

---

### Post by dempl_dempl on 2008-05-03
> **pmasiar said:**
> One view on patterns is that patterns are crutch which allows us to understand programs written by others. Dynamic languages use different kind of crutch.

I found [quite a few](http://www.google.com/search?q=visitor+pattern+python) articles about implementing Visitor in Python, each of them much shorter and easier to understand than C++ version in Wikipedia.

Yes .. if it's not in Wiki , it doesn't exists... ;)

Please read the book or some chapters regarding Visitor... I'm talking about pretty unseen stuff :)

Folks, I won't be coming back , I have a lot of work tonight .. 
Let's take the debate on some other occasion :)  . I believe somebody will post thread similiar to this by tomorrow ... and we'll go over again :)  .

Cheers!

---

### Post by Wybiral on 2008-05-03
> **dempl_dempl said:**
> Please read the book or some chapters regarding Visitor... I'm talking about pretty unseen stuff :)

The point is that there are certain patterns which are simply obsolete in one language and the only means of survival in another. Not long ago there was someone arguing about Python not having C++like "smart-pointers" :)

But, if you're talking about the general "visitor pattern", it is indeed possible, and not even difficult, in Python.

I read the chapter you mentioned, I'm not impressed. The need to add methods to a compiled library's objects (or just avoiding having to write the code in-place) is of no use in Python, it's not compiled :) and things can exist in an ad-hoc fashion.

---

### Post by JupiterV2 on 2008-05-04
I can't help but feel like this topic is getting a little...well...off-topic.

The point isn't whether or not which languages can, or can not, do something but whether they are still of use. I think the reality is that languages on a whole are evolving. I think the point is that I was mistaken and C and C++ are not, in fact, deprecated. I think the best example can be found in automobiles:

C is like a classic pick-up. It's a farm vehicle that takes a lick'n and keeps on tick'n. C++ a more modern pick-up. Its pretty, its flashy, has TONS of features but not exactly a vehicle you'd find many people using to haul hay or dirt.

Python and other interpretive languages are like SUV's. New, fun, sporty, and has all of the features of modern vehicles but that slightly rugged look of a pick-up. They continue to gain ground on those who have always bought pickups.

Different strokes for different folks. Pickups aren't going to get fazed out but they may loose popularity as rising costs of fuel and the practicality of having such a large vehicle wanes. However, we'll always need something to haul dirt and move hay. SUV's and other newer vehicles are more practical and better fuel efficiency.

A lot of people don't like C++ because while it offers a lot of features that C lacks it also gained a lot of baggage that doesn't make it the "best" language. Then again, Python isn't ideal for all tasks either. I don't see kernels being written in Python nor being used in other applications so close to "metal." I think I've learned the following from this, dare I say, very interesting thread which admittedly is looking more like the Holy Wars thread. ;)

C: Fastest, reliable, cumbersome. As close to the hardware as one can be without being an electron or using ASM. If you're a kernel or device driver hacker this will likely be the weapon of choice. Weakly and static-ly typed plus no OOP make it difficult to work with at times.

C++: Faster, cumbersome, OOP. Ideal for projects requiring speed and still utilize OOP style. Weakly and static-ly typed are one of its many faults but has features that make it easier to conceptualize real-world objects and better readability.

Python: Fast, easy, OOP. Awesome for quick development of every-day applications. Dynamic typing, white-space for code blocks and awesome data-types make it very productive and a treat to use. The fact that it relies on an interpreter make it slower by design but still fast-enough.

Ok, so WAY oversimplified, I know, but I've learned this: Know several languages and apply them to each situation. We will all likely favour one language over another but still need to accept that a particular language is ideal for certain tasks.

This is why I plan to continue learning C++ (going beyond stdc++), going back to C and beyond, and learning Python. I will likely continue learning new languages as I go too.

---

