---
title: "Pretty good at 2 languages or really good at 1?"
date: 2008-11-30
forum: Programming Talk
---

### Post by e^(i*pi) on 2008-11-30
I am entering my last semester of college (computer science) and getting ready to head out into the working world. At this point I am reasonably competent in C++ and Java, but better at Java.  What I wonder is this: Would I fare better in the job hunt if I worked from here on out to get both languages up to around the same decently respectable level, or shoudl I really work on my Java and sell myself as an excellent Java programmer.  For the record, I am totally down with expanding my horizons and learning a new language every year and all of that, and I plan on doing that once I am comfortably employed, so this question is pertaining only to the short term goal of getting a job.

---

### Post by slavik on 2008-11-30
depends on where you want to work. some prefer better single language knowledge than others.

---

### Post by CptPicard on 2008-11-30
Now, to answer your short term goal question specifically -- I do believe you need to focus on your Java, knowing the class library and all that. You are much better off, right now, to be an excellent Java coder than an average Java coder and an even worse C++ coder.

C++ is a language that really takes quite a lot of practice to get up to genuinely "decent" professional standard, despite seeming superficial similarities with Java. Worse yet, from an "intellectual" standpoint, I do not believe learning C++ at this point would necessarily help you become a better *programmer* in general, also in the sense that would help your approaches to problems when using Java.

I would suggest that if you want to broaden your horizons, you might want to take a look at Python. It's fast to get started with, quite pleasurable to use, gives you a good "scripting" tool (something Java is awful at), and also introduces you to new concepts that do not exist in either Java or C++. As an added bonus there's Jython that runs on the JVM and interfaces with Java code.

---

### Post by Greyed on 2008-11-30
In all honesty, don't worry about it.  Learn what you learn and run with that.

In my years looking for employment as anything from a technical customer service rep to a programmer I have encountered two types of prospective employers:

1: The pie-in-the-sky.  They want you to know 20-30 of the hottest latest technologies with years of experience in each.  C++, C#, Java, XML, HTML (with CSS!), SQL (both Microsoft and My with some Postgres thrown in), blah, blah, blah, blah, BLAHdiblahblah, and 5 years in them all please!

2: The realist: Needs an experienced X programmer where X is the in house language of choice.

The problem is you will never **ever** satisfy the first and the latter is a crap shoot.  You choose to focus on Java, they want C++.  You focus on C++, they want Java.  But the good news is if you have some of both (or more) and demonstrate that generally the 2nd will pick you up.

So focus on what you want and let the PHBs do their own dance.

---

### Post by e^(i*pi) on 2008-12-01
Thanks for the responses, they are very helpful.  CptPicard: I didn't mention it in my original post but I also know Python pretty well (at least as well as Java) and I like it a lot.  I use to Jython all of the time to interactively test Java classes that I write.  I guess I didn't mention it because I don't think of it as being a really "in demand" language like Java or C++, although I hear that is changing to some degree.  My next new language that I am going to tackle is Lisp.  I learned just enough of it in my programming languages course to get really excited about it, but again, that will be a time-consuming endeavor and it can wait until I have a check coming in. Thanks again for responding, I appreciate the advice.

---

### Post by CptPicard on 2008-12-01
> **e^(i*pi) said:**
> My next new language that I am going to tackle is Lisp.

Now we're talking. :) That one really works your brain in a good way, and gives you more of a different perspective than imperative, static-typed OOP languages like Java or C++ do. It is interesting how much you can cover (essentially, all the other languages, in a sense) with so little fundamental syntax...

---

### Post by mbsullivan on 2008-12-01
> Would I fare better in the job hunt if I worked from here on out to get both languages up to around the same decently respectable level, or shoudl I really work on my Java and sell myself as an excellent Java programmer.

I agree with the previous answers... work on your Java! Once you come to fully understand the uses for polymorphism and other object-oriented features, you'll have a much better time improving your C++.

Learning each new language gets easier, so it's better to work to become as good of a programmer as possible. Learn specific languages when you get a job using them. The syntax of C++ is much less regular than that of Java, anyway, so working in it would probably rot your brain and probably make you dumber :)

> My next new language that I am going to tackle is Lisp.

Functional programming is a different paradigm, so it's probably good to throw at least one FP language into the mix. Better to get at least some of that in your brain before you become completely entrenched in imperative languages. However, don't expect to run out and find any old job using Lisp :)

Another programming paradigm that you might find useful down the road would be to get used to some basic SIMD/vectorized extensions. Maybe consider trying some SSE instructions, or if you have a new graphics card, you could work on SIMD-style data parallel programming using [CUDA]("http://en.wikipedia.org/wiki/CUDA") (NVidia) or AMD's [Stream processing SDK]("http://ati.amd.com/technology/streamcomputing/sdkdwnld.html") (ATI).

Mike

---

### Post by pmasiar on 2008-12-01
> **e^(i*pi) said:**
> I use to Jython all of the time to interactively test Java classes that I write.  I guess I didn't mention it because I don't think of it as being a really "in demand" language like Java or C++,

I did not bothered to reply at first because your first post looked like something from run-of-the-mill code monkey with no deep interest in programming (having programming as vocation, not as job/hobby), but I am glad I was wrong.

Of course Python is not in demand - because only smart companies are looking for it, and as Sturgeon's law says, 80% of everything (ie companies) is crap. You want to work only in smart companies. And Python jobs are often not posted at job boards for code monkeys, but on Python-jobs mailing list or announced at planetpython blogs.

You are young, consider joining a startup or two while you don't have strict obligations. Plenty startups are looking for experts in agile languages like Python.

You should spend couple hours reading Spolsky's and Paul Graham blogs, to learn from successfull programmer millionaires (you cannot become Bill Gates anymore - market is too mature for that).

There are 3 application stacks: Java, .NET and FOSS LAMP. Picking one is a crapshot, but you need years to master either one so you have to choose. And language is not the only choice you have to place your bet on: there are also application frameworks. Learning one means you did not spent year learning another. Smart company realizes you can learn the other one fast, stupid company - you don't want to work there anyway, so don't worry about that.

Go with opportunities, and try not get stuck with dead-end projects and technologies. Become expert in some problem/application area, because technologies change all the time but problems remain.

---

### Post by Cracauer on 2008-12-01
If your goal is job hunt, you go better with a strong preference for one language. If they decide to grill you a bit on interview day you don't want to end up getting interrogated about your second best language and it's not much better if you know two languages halfway.

In practice, Java is pretty useless as a sole language as it manages to be worse at scripting that C is and scripting is very useful. But many people in job interviews don't take that into consideration.

Knowing some Python to Java or C++ in addition is a good thing.

Naming yourself a C++ expert can backfire big time if you couldn't dedicate the time required.

And who's doing functional programming in Lisp, anyway? :)

---

### Post by jimi_hendrix on 2008-12-01
from what ive heard java...big industry right now...

you might want to take a little peak at C# too...ive heard its growing in the job area...its similar to java with different standard class names and they call booleans bools (the extra -ean always bugs me)

---

### Post by Mickeysofine1972 on 2008-12-01
Ok here's my 2p

I think you should definatley go with the C++ and learn it a well as you able.

LISP? hell yeah! I have never heard anyone say they wish they hadnt messed with lisp and alot of people actually belive it made them a better programmer.

Java in lots of ways is like C++ anyway so it wouldnt hurt you to do C++ and do as much as you have time for with Java.

After some time you will probably meet the same opinion that most well heeled programmers have. Its all very much the same thing anyway and there are only a few different things to keep in mind when switching between the other languages like PHP, C, C++, Java, Javascript, c# or any other 'C family' type languages.

Well thats what i have experience anyway.

I also agree with the post earlier about 2 different types of employers, thats always been my experience.

Mike

---

