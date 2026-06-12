---
title: "Python and Java gaming"
date: 2007-03-13
forum: Programming Talk
---

### Post by Gannin on 2007-03-13
In the professional market, Java is used for gaming much more than Python is.  It wasn't until recently, with Battlefield 2142, that I saw Python used professionally at all.  However, in the homebrew market, Python is used much more than Java is.  Why is that?

---

### Post by Ramses de Norre on 2007-03-13
Because python is easier and faster in development? The big difference is python being dynamically typed and java being statically typed which makes java harder to learn and slower to develop apps with. Which doesn't mean there aren't disadvantages with python (but talking about them here will probably start an endless discussion...).

---

### Post by Frosty Cold Drink on 2007-03-13
All things considered, Python requires less sit-ups than Java. As a result, its a lot easier to get in to for most people. Then there is the issue of fads. There was a Java fad a while ago. Now its Python and most recently, Ruby.

---

### Post by Tuna-Fish on 2007-03-14
Actually, I think python is used quite a lot in professional games, it just can be hidden under the bonnet well enough people hardly ever see it. A few mmorpgs spring to mind that use stackless python for guaranteeing concurrency.

---

### Post by Gannin on 2007-03-14
It would seem to me you would also have less files to distribute if you used Python because, even though Java is GPL now, if you want to distribute the JRE with a program, you still have to distribute almost the whole thing, and I think the amount of Python files you have to distribute with a Python project are much smaller.

---

### Post by pmasiar on 2007-03-14
You may not see the Python, but it might be used behind the sceen. A while ago there was presentation about using Python to compile world descriptions for some RPG used to train soldiers for Iraq. They used whatever engine they had to run the worlds, but instead of editing worlds by hand, they generated them. Also, in many places they use Jython (which integrates seamlessly with java including inheriting from it) to script dynamic parts of the Java code. Like  [Industrial Light & Magic](http://www.python.org/about/success/ilm/) and [many more](http://www.python.org/about/success/)

Untill recently Java was "the enterprisey" fad language and doing anything in Java was supposed to add bragging rights before investors, so many companies did and java had more exposure as result. Python was little scripting language used to glue whings together - like nobody mentions using bash script on Linux, why would they, it is a given.

Ruby got popularity from Rails and Rails is Rubys most popular use. At the time (04-05), Rails was the fastest and simples web app framework: Python guys thought it is enough being more agile than Java and cleaner than PHP -- Rails was wake-up call. It is actually funny story: on PyCon 2005 when asked about web apps situation Guido said he does know web apps and not care about them. Google hired him soon after (giving him 50% of time to work on Python development) and first task to do was - web application! So Guido got involved with web apps :-) Since that Pycon, 2 or 3 Python frameworks like Rails (Django, Turbogears, Pylons) emerged in Python too, and meta-framework to integrate web frameworks (WSGI) is becoming Python 2.5 standard library.

---

### Post by nihilocrat on 2007-03-14
Python is an excellent language for rapidly developing things (like Perl) which you and other people will be able to read the code for (unlike Perl) afterwards. Compared to the other alternatives in the open source scripting languages arena, though, it's slow and it's dynamic typing ('duck' typing) can be really annoying. In most cases, you're actually going to have to worry about what types your variables are and you will often need to explicitly cast them or do other such shenanigans or else your program will have buggy output or some function will complain about the types of its arguments at runtime. You end up having to either a) rethink the way your program is working or b) do data validation, which feels to me like a hackish chore where a statically typed language would do it automatically. It's also a little annoying for me to run into all of my errors at runtime, but that's something true of all scripted languages.

If you are working on a large project using OO, however, you can benefit from duck typing. If you design your class hierarchies correctly, you can call class methods that exist in base classes without any thought into what particular subclass you are calling from. Not worring about the particular type of your class instances is a huge time saver and headache-avoider.

It's also a fantastic beginner's language. It has a BASIC-like syntax and dynamic typing style but doesn't encourage bad programming habits. The forced-indentation of Python may seem aesthetically restrictive, but any decent programmer would be indenting anyways, and it's only really a pain because you then have to worry about whether your tabs are actual tabs or a series of spaces. If you do all your editing in one editor, or configure all of your editors to convert tabs to an exact amount of spaces, this isn't a problem. For beginners, forced indentation is excellent, because it teaches good style: haven't you ever tutored CS 101 students and cringed when they decide to completely omit any indentation or readable style from their code?

But anyways, to get more to the point, in games I've seen it (namely, BF2 and 2142, as well as Civilization 4 and Mount&Blade) used as a 'generative' language that sits on top of fast C/C++ code. It seems to be used a lot for generating game content and game rulesets while leaving all of the frame-by-frame heavy lifting to the C/C++ libraries. Lots of games use Lua to do this sort of thing, but Python provides a more "complete" and powerful language to do this with, at the expense of speed (which for generating content on those "Loading" screens isn't a big deal).

I don't think Python is very 'faddish' at all, mainly because (as stated by other posters) it's used behind the scenes in a lot of big, professional systems instead of your dorm roomate's Web 2.0 digg clone site. I've been coding in Python since about 2001, and I've noticed it's taken a long while for Python to find its niche. I think this is also true of Ruby, which was practically unkown until RoR came out. Although I'm sure Ruby has many more uses, people will mainly think of it as a "web framework language" rather than a "rapid development glue language" like people are beginning to see Python as, or "blazing fast industry standard systems/game language" like C/C++ is. This makes Python more generically applicable in the eyes of developers, and thus more "survivable" and multipurpose, while the popularity of Ruby is currently directly proportional to the popularity of web frameworks. Until the big boys decide that Ruby has a larger niche that it is particularly suited for, I don't see this changing.

edit : Oh wait, I forgot that Python offers garbage collection/automatic memory management! I'm not sure if Java does this or not, but it's a huge plus because the worst bugs in C/C++ are memory leaks!

---

### Post by pmasiar on 2007-03-14
I agree with you almost 100%.

> **nihilocrat said:**
> Compared to the other alternatives in the open source scripting languages arena, though, it's slow 

IIRC Python is about as fast as other scripting languages. It is not C, or course, but... And you can even compile Python in couple different ways - psyco has JIT compiler which accumulates info abut actually used types, and changing code accordingly. Do you have any links to prove that other scripting languages are faster?

> and it's dynamic typing ('duck' typing) can be really annoying. In most cases, (...) need to explicitly cast them (...) or do data validation, which feels to me like a hackish chore where a statically typed language would do it automatically. It's also a little annoying for me to run into all of my errors at runtime, but that's something true of all scripted languages.

Not exactly... Possible solution is to use [test driven development](http://en.wikipedia.org/wiki/Test-driven_development): you start writing tests -- by checking for types/methods, way before production runtime. Error fires on runtime only once: before fixing it you write a test checking for it, and run tests after every commit or as needed.

Another huge userbase for Python is coming: Python is main development language for [One Laptop Per Child](http://en.wikipedia.org/wiki/Olpc) - in couple of years OLPC might be the most widely used Linux desktop, big part written in Python.

> Oh wait, I forgot that Python offers garbage collection/automatic memory management! I'm not sure if Java does this or not, but it's a huge plus because the worst bugs in C/C++ are memory leaks!

Java also has GC, but [garbage collection](http://en.wikipedia.org/wiki/Garbage_collection_%28computer_science%29) in java is "mark and sweep" which might cause slight delays, while Python uses reference counting.

---

### Post by Mirrorball on 2007-03-14
In the benchmarks I saw, Python was almost always faster than PHP and Ruby, sometimes A LOT faster.

---

### Post by Gannin on 2007-03-14
This is a very good discussion with a lot of interesting information.  Thanks for all the input :).

---

