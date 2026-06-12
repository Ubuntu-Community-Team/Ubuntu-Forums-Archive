---
title: "Is C# a good langauge?"
date: 2007-02-25
forum: Programming Talk
---

### Post by billdotson on 2007-02-25
I have heard that the C# language is "THE" new language to learn.

---

### Post by Choad on 2007-02-25
well it is good

as a language its very nice. very elegant. 

but it locks you down to just windows. mono is not so great, and you loose the main advantage of c# which is the integration with visual studio

---

### Post by Mirrorball on 2007-02-25
> **billdotson said:**
> I have heard that the C# language is "THE" new language to learn.
Probably by Windows users. Here you would be more likely to hear Python.

---

### Post by gh0st on 2007-02-25
> **Mirrorball said:**
> Probably by Windows users. Here you would be more likely to hear Python.

Yeah I'd agree, Python and Ruby are the hot languages to learn at the moment. C# isn't that great in my opinion, I was a Java developer and I tried C# when forced to use .NET for a job, I didn't like it. I actually ended up using VB.NET for .NET development. The guys who develop Mono are doing a great job but I still think you are really locking yourself into Microsoft land by choosing C#. Why not choose a language that has good support on a range of platforms, then you can happily develop for any of them.

Just my opinion :)

---

### Post by MadMan2k on 2007-02-25
sorry, Python is a nice scripting language but no real competition for C#. It is much slower and lacks some Design paradigms you want it that league. Java is the closest alternative you can get and since its OSS now it is probably also the most desirable one.
But be aware that C# still has some minor language(syntax) advantages over Java...

---

### Post by Note360 on 2007-02-25
C# is very nice, I like the syntax better than C++ (I like C) and I like OO so it is amazing for me and for what I have to do mono isnt very limited. THe only problem is you have to sift through all that .net crap to get to the mono docs.

---

### Post by pythonbite77 on 2007-02-25
From an employment perspective C# is Microsoft's dominant language for it's .NET framework, and since most application developer jobs are for the Windows platform, then it is the obvious choice. From the perspective of pure enjoyment, C++, Python and functional programming (Miranda, ML, Haskell) are streets ahead. As for Java, I try to avoid it as much as possible.

Although C++ is considered cumbersome and overtly complicated, the Standard Library is a thing of beauty and if you put the time and effort in, the rewards both financial and intrinsic can be great. Plus, there are as many C++ jobs available as C#, plus its cross platform.

---

### Post by Note360 on 2007-02-25
Personally I dont like C++.

C# is just as fun as any other language but the most enjoyable language for me is still Python or Ruby. Lisp is fun to.

However, C# is functional and syntaticaly nice.

---

### Post by pmasiar on 2007-02-25
> **billdotson said:**
> I have heard that the C# language is "THE" new language to learn.

You are missing some point. THE language for what? Linux kernel hacking? Writing drivers? Dynamic web-based application? Modeling AI (artificial intelligence)? Your selection of the best language for the job depends what the job is. Do you need .NET compatibility? 

C# is proprietary MS replacement of Java, when MS realized that they standard trick "embrace, enhance, choke" will not work with Java. It is supposed to be next best thing for .NET development, and looks like MS hired smart people so they learned a little from Java's shortcomings, but really it is language pretty like Java, no breakthroughs.

It is statically typed (like Java), so in raw computing speed might be slightly faster than dynamically typed languages like Python and Ruby. But because of static typing, development speed is much slower than when using dynamically typed languages. Of course if you never tasted the freedom what dynamically typed language gives you, you will never miss it. If you walk on the ground, you do not feel need for 3rd dimension - but once you tried it, walking will be 2D task for you.

So if you need safe career in a big corporation, Java or C# are pretty replaceable (but libraries are quite different in parts). If you want to hack on free software (free like freedom), you need free languages: C/C++ for tasks where you are willing to invest extra efforts to gain speed coming from static typing, and Python/Perl/PHP/Ruby for applications.

And remember - THE most important speed in your program is "speed to the market". If first version is fast enough to be usable, you can improve speed in next version. In Python, you can create correct application first, then profile speed bottleneck, reimplement 5% of critical code as C library, and link it together. As result, you have 80% of the speed of pure C program for 20% of the efforts.

MS knows this - and not many people are willing to use their programs before first service pack. And they hired one of Python gurus to implement Python fot .NET - IronPython. So with IronPython you can get access to .NET libraries and flexibility and development speed of dynamically typed language, if you need it.

---

### Post by kinson on 2007-02-26
If you just say "Is C# a good language to learn". 

In this case, I would say its probably good to learn, and easy to learn(if you're talking about a windows environment. I've never programmed for Linux yet). If you're using Visual studio, it'll be realli easy to pick up, what with the code completion and what not (its a bit pampering though). I managed to pick up the language without much fuss.

But in terms of cross platform, I'd still say something like c++ is probably much better.

If you're talking about "THE" language to learn as is upcoming and popular language, thats probably true, and lotsa companies(including mine) as looking for programmers with c# knowledge/experience.

So it really depends on what you're asking for :P

Cheers,
Kinson

---

### Post by Choad on 2007-02-26
> **pmasiar said:**
> You are missing some point. THE language for what? Linux kernel hacking? Writing drivers? Dynamic web-based application? Modeling AI (artificial intelligence)? Your selection of the best language for the job depends what the job is. Do you need .NET compatibility? 

C# is proprietary MS replacement of Java, when MS realized that they standard trick "embrace, enhance, choke" will not work with Java. It is supposed to be next best thing for .NET development, and looks like MS hired smart people so they learned a little from Java's shortcomings, but really it is language pretty like Java, no breakthroughs.

It is statically typed (like Java), so in raw computing speed might be slightly faster than dynamically typed languages like Python and Ruby. But because of static typing, development speed is much slower than when using dynamically typed languages. Of course if you never tasted the freedom what dynamically typed language gives you, you will never miss it. If you walk on the ground, you do not feel need for 3rd dimension - but once you tried it, walking will be 2D task for you.

So if you need safe career in a big corporation, Java or C# are pretty replaceable (but libraries are quite different in parts). If you want to hack on free software (free like freedom), you need free languages: C/C++ for tasks where you are willing to invest extra efforts to gain speed coming from static typing, and Python/Perl/PHP/Ruby for applications.

And remember - THE most important speed in your program is "speed to the market". If first version is fast enough to be usable, you can improve speed in next version. In Python, you can create correct application first, then profile speed bottleneck, reimplement 5% of critical code as C library, and link it together. As result, you have 80% of the speed of pure C program for 20% of the efforts.

MS knows this - and not many people are willing to use their programs before first service pack. And they hired one of Python gurus to implement Python fot .NET - IronPython. So with IronPython you can get access to .NET libraries and flexibility and development speed of dynamically typed language, if you need it.
qft

this dude really knows his ****

---

### Post by gh0st on 2007-02-26
> **Choad said:**
> qft

this dude really knows his ****

Yeah he certainly does, I'd 2nd that :) 

Is IronPython any good? Has anyone used it? I don't really do .NET development these days and it was a few years back when I did, unfortunately it was before IronPython had been created I think. I certainly didn't come across it at the time but then I was working for a Microsoft only shop and didn't have time to look :( 

Is it just Python with access to the .NET framework and Visual Studio support? :-k

---

### Post by Note360 on 2007-02-26
> **gh0st said:**
> Yeah he certainly does, I'd 2nd that :) 

Is IronPython any good? Has anyone used it? I don't really do .NET development these days and it was a few years back when I did, unfortunately it was before IronPython had been created I think. I certainly didn't come across it at the time but then I was working for a Microsoft only shop and didn't have time to look :( 

Is it just Python with access to the .NET framework and Visual Studio support? :-k

ITs just Python for .NET its not much different than python. It also works with Mono

Just a fun fact, (from Wikipedia so it could be false) Miguel de Icaza the person behind GNOME and Mono was intervied a job at M$, in I think the IE ports department, previous to starting development on GNOME the same year. It seems that if M$ took him we may not have either and maybe have a bigger hold or he could have pushed them into some FLOSS stuff to.

---

### Post by Spr0k3t on 2007-02-26
> **pmasiar said:**
> 

There's no better way to put it than what pmasiar wrote.  Choose the language for the job... You don't write python scripts for a mainframe application and you don't build extensive j2ee applications for renaming files in a directory.  Each language has its strengths and weaknesses.  A good programmer will be able to tell you what language would work best for each task.

That said, I'm a Java C++ fan.  I had to code in C#... it was... nice... but I went back to Java for the final application.

If you want a good universal compilable language to learn, start with Java.  I picked up C++ in about a week or two of grunt coding and learning C#, I was thrown at the task I produced results about the same amount of time it took me to write the same in Java.  Java will just make the cross platform application development a tad bit easier and the syntax for C++, Java, and C# is very similar.

---

### Post by pmasiar on 2007-02-26
Many people seems to be obsessed by supposed speed gained by compilation. If your application is web-based frontend for a database, as most applications are now, at least 90% of runtime is in hands of database and web server. Even if runtime after compilation will be down to 0, you will gain 10% max. So chasing compilation speedup is a mirage, wake up. Dynamically typed language might add 3-5% of runtime, but improves your development speed and simplifies maintenance 1000%.

> **gh0st said:**
> Is IronPython any good? Has anyone used it? I don't really do .NET development these days and it was a few years back when I did, unfortunately it was before IronPython had been created I think. I certainly didn't come across it at the time but then I was working for a Microsoft only shop and didn't have time to look :( 

Is it just Python with access to the .NET framework and Visual Studio support? :-k

Some people are starting to use IronPython - you need to check [http://www.planetpython.org/](http://www.planetpython.org/) , IIRC voidspace guy is one of them.

Catch is, IronPython *IS* different from C-Python. Not all standard Linux C libraries are implemented in .NET, so some libraries are missing, and some will never be implemented (becuase cross-platfor is not a goal, it is designed to be restricted to .NET). A project to recode some libraries in pure python was started, because also Jython (Python on top of Java) needs them. Use common sense and due dilligence.

Now we have 4 independent implementation of Python: CPython, Jython, IronPython, and PyPy (Python in Python), slight under-documented implementation-specific issues started to buble up. Good thing is, Google hired lots of key Python hackers, so are paid to work on fixing these issues for Python 3K for all of us. Language for nex 100 years ( [http://www.paulgraham.com/hundred.html](http://www.paulgraham.com/hundred.html) )  is going to be available soon - first beta in 2007 :-)

But Python is so much more than access to .NET. With python, you have interacive shell. So instead of writing pages of scaffolding code to try out some objects, you can instantiate them in IronPython shell and try them out. I was told that dynamic nature of IP shell is the killer app for .NET developers - they have no other way to do it in .NET.

Because excellent CLR runtime of .NET, IronPython is sometimes faster than C-Python. MS is very rich company and it can afford to hire lots of smart people, who will work hard to make the best runtime for dynamic languages they can. They definitely want to beat java. I am not telling thay are winning, but they are not neither stupid or lazy - but MS has much more money in bank than Sun has, and can wait for 10 more years. And they are getting ready for dynamic languages too - are you?

> **Note360 said:**
> ITs just Python for .NET its not much different than python. It also works with Mono

Just a fun fact, (from Wikipedia so it could be false) Miguel de Icaza the person behind GNOME and Mono was intervied a job at M$, in I think the IE ports department, previous to starting development on GNOME the same year. It seems that if M$ took him we may not have either and maybe have a bigger hold or he could have pushed them into some FLOSS stuff to.

Your fear of Wikipedia facts is 100% unfounded. It took me about 1 minute to find the text  in linked article about Miguel here: [http://primates.ximian.com/~miguel/gnome-history.html](http://primates.ximian.com/~miguel/gnome-history.html) where Miguel himself says he in fact was interviewed in MS. Don't spread FUD about Wikipedia - read articles with open mind, and if you find an error, fix it. It is same as with free code.

---

### Post by gh0st on 2007-02-26
Thanks for the information pmasiar it's much appreciated. I will check out those links. I'm not really planning to do any .NET development any time soon but if by some chance I have to, it would be good to know this stuff.

Python works fine without .NET for me at the moment :)

---

### Post by juancarlospaco on 2010-08-23
You mean a gauge that meassure the lan?, or whats langauge?

---

### Post by matthew.ball on 2010-08-23
> **MadMan2k said:**
> sorry, Python is a nice scripting language but no real competition for C#. It is much slower and lacks some Design paradigms you want it that league. Java is the closest alternative you can get and since its OSS now it is probably also the most desirable one.
But be aware that C# still has some minor language(syntax) advantages over Java...
What are the advantages C# has over Python? Python has a richer support for the functional paradigm then C#, and it's object-oriented framework is just as good. I don't believe C# offers a declarative style (though I don't think Python does either), as far as I can tell, they're roughly equal in terms of what they offer.

If you're gonna use the whole "x is faster than y" you might aswell be an assembly programmer. Then you can literally look down on everyone else. In every other case, you really can't.

Sure, if you're a total IDE fanboy C# might be better, but in that case isn't it more accurate to say that Visual Studio is better? However (and perhaps this is only my experience) an IDE is completely arbitrary.

---

### Post by nvteighen on 2010-08-23
> **juancarlospaco said:**
> You mean a gauge that meassure the lan?, or whats langauge?

You made my day, sir. :lolflag:

---

### Post by goldfiction on 2013-04-22
I actually quite like C# myself. In fact it's my favourite language since the beginning of my computer days. I started qbasic, it was similar to turing I later encountered. They were both starter packs. Java was my Gr12 language. I liked it at the time, but OOP was new to me as a basic-er. I was too familiar to goto command which Java never had any. It was also my first time using recursive and iterative function and sub function to handle larger quests. But compare to JAVA, C# is much much easier. Sure, it does almost the same amount of features, I like how it is much easier to use with the help of VS. I learned C# in first year actually. Never stop playing with it ever since. Even later when I learned C++ in 2nd year, I didn't like C++ as much as C# mostly because of all the basic things are not really available from C++ as in C#. Or it takes too much effort to get to the starting point in C#. Using C# is like sleeping on a mattress while using C++ is like sleeping on the floor. Then of course I learned PHP and Javascript. I have to say I liked Javascript a lot after I learned the in and outs of callbacks and ajax. I had this great opportunity to learn node.js as the hosting language instead of apache and php. This was much better. So... If you want an application for a business, node.js+javascript+html is the future. Even the bigger companies start to follow this trend. But... I still like C# a lot. When I want to write a game, javascript and HTML just won't give me a good engine like XNA, bullet#... Plus, browser rendering really have a long way to go.

The idea .net is microsoft's pet is not really true. I built a server, installed ubuntu, installed wine and ran my .net app server on it just fine. What it really give me is a cheap way to deploy .net server apps on linux servers. The idea is that you want a non-graphic server to do the lifting and a nice graphic interface on the user end to deliver fancy stuff. So the server doesn't have to be on windows...

---

### Post by QIII on 2013-04-22
Thank you for sharing.

If a post is older than a year or so and hasn't had a new reply in that  time, instead of replying to it, create a new thread. In the software  world, a lot can change in a very short time, and doing things this way  makes it more likely that you will find the best information. You may  link to the original discussion in the new thread if you think it may be  helpful.

*Thread** Closed***

---

