---
title: "Python vs C++ - standard libraries and speed"
date: 2008-12-23
forum: Programming Talk
---

### Post by giuspen on 2008-12-23
Hi, I work at job in C and little C++, during spare time instead in Python and GTK.
I like Python but I'm worried about how much you can lose in performance when compared to C++, about C++ instead I worry because I'm not able to find standard libraries comparable to Python ones, also documentation talking.
Does anybody can give an idea of the difference of performance between Python and C++?
Does anybody knows if it's possible to find similar powerful standard libraries for C++?

---

### Post by dribeas on 2008-12-23
There is no way that you can get a good answer to the question you propose. It fully depends on what you are coding for. Is your application performance critical? Use C++. If not, python will be faster to code, and if the speed difference during execution is not critical it might be the best choice.

Language decisions cannot be made out of thin air, first you need to consider the problem at hand.

C++ is way faster, probably the ratio is about 1:6

---

### Post by mike_g on 2008-12-23
As said, it really depends on what you are doing. Theres C++ wrappers about for Gtk if you want to use them; however, if you are only using it for the GUI elements then I'd recommend Python w/ PyGtk as you can forget about so much tedious code and the performance is not really an issue. Once you go beyond calling a few instructions now and again I find Python gets slow fast. To me it seems as if Python is quite a lot more than 6 times slower than C++ (dont know that for a fact, just observation) I guess that largely depends on what you ar doing.

---

### Post by pmasiar on 2008-12-23
Even if Python is 20 times slower, it might not make too much difference - it depends on your app. Ie if you program web frontend for a database, most of the time is wasted in web server and database server, completely out of your control regardless of the language. So if 90% of time is there, you have control on 10% of the time, and even fastest C++ code would be only 10% faster than average Python. See?

Better approach (and the one Python was designed and optimized for) is to write everything in pure Python first, make it work correctly, and then profile and find the bottleneck. Solve it by adjusting algorithms first, and when optimal, by coding that one function call in C.

Python has plenty of C-based libraries for numerical computing, where instead of looping through huge data structures you use C libraries calls.

When optimizing: don't guess - measure! Premature optimization is root of all evil.

---

### Post by CptPicard on 2008-12-23
Interestingly, one of the reasons why Python has such great libs is exactly because it is a higher level language. You can abstract so much better in them. Of course the converse of this is that you will take a performance hit. You are in some sense looking at contrasting requirements...

---

### Post by monkeyking on 2008-12-23
check this if you want to compare speeds
[http://shootout.alioth.debian.org/](http://shootout.alioth.debian.org/)

---

### Post by mike_g on 2008-12-23
> Interestingly, one of the reasons why Python has such great libs is exactly because it is a higher level language. You can abstract so much better in them. Of course the converse of this is that you will take a performance hit. You are in some sense looking at contrasting requirements...
You have a point, but I don't think that that in always a good thing. Me and a friend are looking at making a game (if we ever get enough time for it). The original plan was to use python with OGRE and ODE. While the python wrappers hide a lot of the verbose code, it can also complicate things. For example theres a function to load a heightmap into your environment. The python version conveniently hid where the mesh data was being stored, but this would be needed to pass to the physics engine. We found how to get it in the end, but it took quite a lot of time going through unclear docs. In C we would not have these problems. Also, while in Python you may not need to know how the internals work, if you want to do anything out of the ordinary you are going to have to dig into the libraries anyway. So, in some ways I have my doubts as to whether focusing on python will be all that more productive for this situation.

---

### Post by samjh on 2008-12-23
> **mike_g said:**
> So, in some ways I have my doubts as to whether focusing on python will be all that more productive for this situation.

It's a good approach in theory, but putting into practice is not so simple.  Think of it as a marketing line - take it with a grain of salt and evaluate it carefully for your situation.

Sometimes you might find it's better to do it the opposite way: write the core components using C or C++, and then embed Python for components that are not speed-critical.  This is the approach taken by some game companies, like DICE (maker of Battlefield 2 and 2142): they develop the engine and other resource-critical code in C++, and then use embedded Python to write level logic.

---

### Post by nvteighen on 2008-12-24
> **mike_g said:**
> You have a point, but I don't think that that in always a good thing. Me and a friend are looking at making a game (if we ever get enough time for it). The original plan was to use python with OGRE and ODE. While the python wrappers hide a lot of the verbose code, it can also complicate things. For example theres a function to load a heightmap into your environment. The python version conveniently hid where the mesh data was being stored, but this would be needed to pass to the physics engine. We found how to get it in the end, but it took quite a lot of time going through unclear docs. In C we would not have these problems. Also, while in Python you may not need to know how the internals work, if you want to do anything out of the ordinary you are going to have to dig into the libraries anyway. So, in some ways I have my doubts as to whether focusing on python will be all that more productive for this situation.

Well, an unsolved issue in programming languages seems to be the ability to scale down to a lowest level of abstraction. We can easily climb higher, but lower is not quite easy. C++ attempted this with results that don't satisfy all people... Python has a sort of pointers (id's) that are absolutely useless... Perl's references are much like Python's id's and don't count on Lisp for this.

The current solution would be to use a low-level language to do that stuff and use a higher-level one to do the rest... and combine them. But it would be interesting to see a language that is capable to do that combination by itself in a clean way, not recurring to an external language (but I guess the trade-off would be against simplicity...)

---

### Post by jimi_hendrix on 2008-12-24
the speed wont matter unless your making some huge app or fallout 4

---

### Post by dribeas on 2008-12-24
> **nvteighen said:**
> Well, an unsolved issue in programming languages seems to be the ability to scale down to a lowest level of abstraction. We can easily climb higher, but lower is not quite easy. C++ attempted this with results that don't satisfy all people... Python has a sort of pointers (id's) that are absolutely useless... Perl's references are much like Python's id's and don't count on Lisp for this.

The current solution would be to use a low-level language to do that stuff and use a higher-level one to do the rest... and combine them. But it would be interesting to see a language that is capable to do that combination by itself in a clean way, not recurring to an external language (but I guess the trade-off would be against simplicity...)

You are right. That is something that is being tackled with C++, but as you mention there are many complaints. There will always be. If you use higher level idioms in C++ it is not so different to other languages like Java or C#. Now the language also allows the user to get deeper into lower levels, and that is what many people complain about.

To most people C++ is bad because it allows you to get to a low enough level that you can shoot yourself (and as many say, in the most efficient way with the greatest gun), but that same people will never try the higher level features of the language. 

Of course, this makes the language more complex, it has many features and some problems can even be tackled from different angles in the same language. That implies a steper learning curve. It is much harder to get to know a way of doing things than distinguishing which of three ways is the best for a particular problem.

In the project I am working, time requirements are critical and C++ was the language of choice (the client requested it). The way it is coded there is no single delete instruction in the whole system and no resource is leaked. The only disadvantage from using python would be that the set of libraries as a more complex API with finer control over how things are done with the implied cost of learning how each parameter affects the result even if you don't care in many cases.

On the other hand, I have had experience programming for Symbian smartphones in C++ and to a lesser extent in python. The complexity of the data structures in (the limited) C++ for that particular operating system made coding in python easier and faster even when I had never coded python before. But then again, Symbian has a strange memory control system and while it is said to be C++ it is just a small low level subset of it (no STL, bad support for exceptions...)

---

### Post by dribeas on 2008-12-24
> **jimi_hendrix said:**
> the speed wont matter unless your making some huge app or fallout 4

Or some small app that requires RT or near RT, or control some hardware system with strong constraints, or have many simultaneous users, or has NP-complete problems to resolve...

It will never be important with UIs since there is a single user and the user is way slower than the system no matter how slow the system is (to some extent), if you just shuffle data from one place to another or make simple tasks that depend on much work from slower systems (database access, remote servers...)

---

### Post by monkeyking on 2008-12-24
> **jimi_hendrix said:**
> the speed wont matter unless your making some huge app or fallout 4

Speed matters,
so does size.

---

### Post by pmasiar on 2008-12-24
> **nvteighen said:**
> The current solution would be to use a low-level language to do that stuff and use a higher-level one to do the rest... and combine them. But it would be interesting to see a language that is capable to do that combination by itself in a clean way, not recurring to an external language (but I guess the trade-off would be against simplicity...)

There are two ways to solve this problem: adding complexity like C++ does, or adding limits to programming language. 

[http://en.wikipedia.org/wiki/Cython](http://en.wikipedia.org/wiki/Cython) is interesting compromise, because it has simple syntax of Python, but effectiveness of C code (it compiles to C). So you can program all in Python, then convert bottleneck code to Cython.

> **monkeyking said:**
> Speed matters,
so does size.

unless they don't :twisted: Remember that premature optimization is root af all evil.

---

### Post by CptPicard on 2008-12-24
Hmmh... my own feelings regarding C++ disagree rather strongly with this viewpoint, which seems to just assume that people are complaining because C++ doesn't "restrict" them, that is, that they are implicitly too stupid to use C++... ;)


> **dribeas said:**
> If you use higher level idioms in C++ it is not so different to other languages like Java or C#.

... and one needs to point out that Java and C# are not really conceptually all that wonderful either, and C++ is in the same crowd. OOP is not such a big deal as far as languages go; it's just a way to package data and code and to do a single-dispatch on first implicit parameter of function (the implicit "this" pointer).

> 
 Now the language also allows the user to get deeper into lower levels, and that is what many people complain about.

It's not that it's wrong to let that happen, but if the language itself becomes messy to use, then it can be a problem. Lisp has nice foreign function interfaces, and just over Christmas holidays here I'm hacking on an AVL-tree implementation in C which is full of void*'s, with Python handling the high-level "driving" of the code plus type checking. It's really clean and nice with clean separation of abstraction levels, and in C++ it would be messy as I would be having to manage low-level and the high-level in the same language, with the coexistence being harder to manage as my high-level abstractions will constantly need to be very aware of their low-level implementation...


> 
To most people C++ is bad because it allows you to get to a low enough level that you can shoot yourself (and as many say, in the most efficient way with the greatest gun), but that same people will never try the higher level features of the language. 

No, to me it's bad because C++ is as a language too big for its own good and is just slow and messy to write. It's hard to put my finger on it, but writing C++ tends to be a fight where it shouldn't, and I actually dare say so as I have enough languages under my belt ;)

I am not also very sure what is meant by the high-level features of the language... I mean... as I said, static-typed OOP is not yet awfully beneficial, and to support OOP-design at C++'s chosen level of abstraction (or lack thereof) requires a lot of low-level support mechanisms that need to be managed by the programmer.

For me, high level features mean closures, lambdas, first-class functions, multiple dispatch, multimethods, eval, continuations, algebraic datatypes and pattern matching, list comprehensions (map/filter/reduce), duck typing....


> It is much harder to get to know a way of doing things than distinguishing which of three ways is the best for a particular problem.

Yet, it doesn't even support functional programming which is such a nice paradigm to design stuff in...

---

### Post by s3gfault on 2008-12-24
> **monkeyking said:**
> Speed matters,
so does size.

> **pmasiar said:**
> unless they don't :twisted: Remember that premature optimization is root af all evil.

I have to say that I really don't agree with your axiom.  Speed and size both matter, if you've got a simple algorithm that does its job in O(2^n) when another algorithm exists that does the same thing in O(n), then the first one is stupid and wrong.

Computer Science is not supposed to be experimental, lol.

---

### Post by CptPicard on 2008-12-24
segfault, lurk a little before lecturing on the obvious. ;)

Your example would be just simply plain wrong design, not "lack of premature optimization". Premature optimization in the saying pmasiar refers to generally here means resorting to low-level optimization strategies that typically result in constant factor improvements to runtime before it is known that such drastic action is actually required -- and that you can't get any better by, say, switching algorithms.

---

### Post by s3gfault on 2008-12-24
> **CptPicard said:**
> segfault, lurk a little before lecturing on the obvious. ;)

Your example would be just simply plain wrong design, not "lack of premature optimization". Premature optimization in the saying pmasiar refers to generally here means resorting to low-level optimization strategies that typically result in constant factor improvements to runtime before it is known that such drastic action is actually required -- and that you can't get any better by, say, switching algorithms.

oh, well that makes sense i suppose.:(

---

### Post by samjh on 2008-12-24
> **CptPicard said:**
> It's hard to put my finger on it, but writing C++ tends to be a fight where it shouldn't, and I actually dare say so as I have enough languages under my belt ;)

CptPicard, although I don't doubt your broad experience with programming languages, but your assertion that you shouldn't have to feel C++ programming as a fight just because you have "enough" languages under your belt is absurd.

One can shoot a handgun, submachine gun, automatic rifle, and shotgun, and still be a bad shot at any one or all of them.  If you feel that shooting a an automatic rifle at a target within its range is a struggle, then the issue is your competence with the weapon, not the weapon itself.  If your competence is good enough but it's still a struggle, then the problem is the range of the target.  Any other reason is just subjective personal preference.

Do you try to use C++ like C++, or do you try to use C++ like Lisp or some other language you prefer, in order to solve a problem that is better solved using a language other than C++? ;)  Or perhaps your brain just doesn't jive with C++.

I never liked C++ until I had to use it for Qt.  Now it's tolerable (but still doesn't jive with me). :p

---

### Post by CptPicard on 2008-12-24
samjh,

You're pretty much correct. I am quite willing to admit that a lot of it probably *is* about my lack of competence regarding C++ because of course I know a lot of stuff is indeed being written in C++ by a lot of people (I do not for example list C++ on my resume although I know a lot of less competent people do). The C++ gurus are *very* good at using C++, but from my perspective, the fact that we get these humongously long and detailed technical explanations about why and how you do "something fairly simple" in C++ is symptomatic, regardless of how much competence there is in the guy doing the writeup on "how to do it right in C++" :)

And yes, most other languages do fit my brain better... and interestingly, a lot of those "other" languages have also taught me some language-independent truths and design patterns and strategies that have actually shown me why certain things work the way they do in C++-ish languages like, uh, C++, and Java, and how to emulate or reproduce these strategies in those languages (and when I have not been able to, it has been instructive to see, why). It is interesting that it was other languages that taught me how to code C++, for what my C++ coding is worth. After that, it's been about learning the language-specific tactics of achieving certain goals, of which there are a lot in C++... ;)

So I would say that although I indeed sort-of suck at C++, because other stuff just works so much more nicely, it leaves me with this nagging feeling that this particular emperor might not actually have all of his clothes on...

(bah, badly structured rant but I'm tired... need sleep)

---

### Post by pmasiar on 2008-12-25
> **s3gfault said:**
> Speed and size both matter, if you've got a simple algorithm that does its job in O(2^n) when another algorithm exists that does the same thing in O(n), then the first one is stupid and wrong.

... and if you are writing program which you will run on this file exactly once, neither speed or size matters: the only thing what matter is to write it under 15 minutes, with no errors, so it runs from first try. And if you never used simple language like Python, you don't have such experience, so you cannot even compare.

---

### Post by Cracauer on 2008-12-25
> **giuspen said:**
> Hi, I work at job in C and little C++, during spare time instead in Python and GTK.
I like Python but I'm worried about how much you can lose in performance when compared to C++, about C++ instead I worry because I'm not able to find standard libraries comparable to Python ones, also documentation talking.
Does anybody can give an idea of the difference of performance between Python and C++?
Does anybody knows if it's possible to find similar powerful standard libraries for C++?

There is no good answer for this.

At the very least you need to understand the concept of what is a system call and what kind of waiting on user, disk and network is involved. You also need to understand that some critical code in Python is actually running in C, namely regular expressions. Then there's the issue of programs that are "fluffy", use lots of listsm allocate a lot and generally aren't tight to get best performance. These don't perform well in C++ either and although Python will be even slower the difference isn't that large.

Once you are outside of that and have code written with performance in mind Python is about 10-100 times slower. Most people rarely use constructs that meet all these conditions, though, so Python is fast enough for them at the time.

The problem is that once you have a large codebase you can't switch languages, so you get along with your scripting language fine for 3 years and then somebody makes a requirement that pushes one subsystem into this zone. Then you can be screwed. Using foreign code, loading C code, for these subsystems only works in about half of the cases, in the other half the overhead of converting data and calling in and out of C eats up the advantage.

I don't think there's any library that doesn't have something available for C++, with the notable exception of Twisted.

"Powerful" libraries, what exactly do you mean. Of course the API for C++ libraries is usually the opposite of elegant and provides real puzzles as opposed to the straightforward (and slow) interfaces you usually find in Python.

---

### Post by samjh on 2008-12-25
Back to the OP:

> **giuspen said:**
> Does anybody can give an idea of the difference of performance between Python and C++?This is a very simplistic example.  For a selection sort of 10000 random integers, Python is 78 times slower than C++.  This is just pure Python vs C++.

In another example, Matrix multiplication involving 1 million elements, with Python using the numpy library (implemented in C), all are single-threaded:
Python + numpy (C-optimised numerics library) = 12.611s
C++ (naive, unoptimised) = 12.437s
C++ (as above, compiled with -O2) = 9.570s
C (algorithmic optimisation and -O3) = 3.906s

> **giuspen said:**
> Does anybody knows if it's possible to find similar powerful standard libraries for C++?There are lots of multi-purpose libraries for C++, but none of them are "standard".  The only standard libraries for C++ is the language itself, the C library, and STL.

GLib, Qt, Boost, and others are all multi-purpose libraries for C++ or have C++ bindings (GLib has GLibmm).

---

### Post by giuspen on 2008-12-26
I explain better my "powerful standard libraries for C++":
for instance:
1)I have to call for a shell command, there is the weel documented subprocess module:
[PHP]subprocess.call(string, shell=True)[/PHP]
2) I have to walk through directories:
[PHP]for dirpath, dirnames, filenames in os.walk(source_path):
   for filename in filenames:
      source_size += os.path.getsize(os.path.join(dirpath, filename))[/PHP]
3) check if a path exists, if it's a dirtectory:
[PHP]if os.path.exists(destination_path):

if os.path.isdir(source_path):[/PHP]
4)to retrieve last editing time:
[PHP]time.ctime(os.path.getmtime(source_path)[/PHP]
thanks everybody.
regards,
giuseppe.

---

### Post by Cracauer on 2008-12-26
Mixing languages, writing the slow parts in a comfortable language and the speed-needy parts in C or C++, rarely works out.

In a complex application you have huge amounts of data in composite data types in collection classes, and in almost no languages you can actually share the same data between the two languages.  Most runtime systems require you to convert every time you access from one of the languages, and then the speed advantage is gone.

There are exceptions, such as the better Common Lisp compiler, which can generate Lisp machine code that directly accesses C data, and C collection classes such as arrays and lists.  Not that it's much needed since these generate pretty code machine code anyway.  But Python, Ruby, Perl and notably Java require actual translation of C data before messing with it in the main language. 

(which is, BTW, another one of those non-obvious reasons why Java always performs adequately in language benchmarks and comes up with horribly slow applications in real life - people assume they can just look at the profile and re-implement the top 10 functions in C. But things don't work that way)

---

### Post by CptPicard on 2008-12-26
Cracauer, that's a good point -- especially when performance-criticality is a sort of cross-cutting concern between modules and different high-level abstractions, you end up just having to "implement everything in C" to avoid data transfer across the interface.

However, if you're able to keep crossing the interface inside tight loops and such, it is a workable strategy. I am currently writing a prototype of an analysis toolkit of mine in which I essentially just write the toolkit as a C library which I will then "drive" from Python, and it looks pretty nicely doable. Essentially all the data is held in the C side, with "handles" exposed for Python. Because I can just "load data, compute and extract results", it works.

---

### Post by dribeas on 2008-12-27
> **CptPicard said:**
> Hmmh... my own feelings regarding C++ disagree rather strongly with this viewpoint, which seems to just assume that people are complaining because C++ doesn't "restrict" them, that is, that they are implicitly too stupid to use C++... ;)


I did not mean to imply that by any means. I believe that most text books and tutorials about C++ center on the lower levels of the language and forget the rest. 'Accelerated C++' is one of the clearest exceptions to that trend. Anyway, the fact is that many beginners are thrown directly into pointers, manual resource control (that could be handled by higher level constructs) and some of the basic building blocks and idioms that ease development are left behind.

Most texts will talk STL but only refer to containers, many will briefly mention iterators without explaining why they were introduced in the language and their power. I have many times read that iterators are just the same in C++ than they are in Java, and above the surface they may seem but they are very different in nature.

My complain is not about the capacity of the learners, but about the limitations of the teachers.

I am not defending C++ over any other language, just stating that it many of the complaints against it are not justified. I started to comment on your concepts for high vs. low level languages but at the end I decided to avoid the whole discussion. C++ is not the highest level language, but when most people (not you) consider other statically typed OO languages high level, C++ fits there. Your definition explicitly excludes static typed languages. C++ is statically typed. End of discussion.

---

### Post by dribeas on 2008-12-27
Boost is kind of the standard non-standard library source. In fact some of the standard TR1 libraries are either Boost libs or barely changed from boosts.

> **giuspen said:**
> I explain better my "powerful standard libraries for C++":
for instance:
1)I have to call for a shell command, there is the weel documented subprocess module:
[PHP]subprocess.call(string, shell=True)[/PHP]
2) I have to walk through directories:
[PHP]for dirpath, dirnames, filenames in os.walk(source_path):
   for filename in filenames:
      source_size += os.path.getsize(os.path.join(dirpath, filename))[/PHP]
3) check if a path exists, if it's a dirtectory:
[PHP]if os.path.exists(destination_path):

if os.path.isdir(source_path):[/PHP]
4)to retrieve last editing time:
[PHP]time.ctime(os.path.getmtime(source_path)[/PHP]
thanks everybody.
regards,
giuseppe.

1) system() in C will call exec a command in a shell

2,3,4) never needed it, but you could check the Boost::filesystem

From the four problems you provided it seems as if you are more interested in a scripting language than in a real programming language.

---

### Post by monkeyking on 2008-12-27
> **dribeas said:**
> 
From the four problems you provided it seems as if you are more interested in a scripting language than in a real programming language.

lol

---

### Post by monkeyking on 2008-12-27
> **Cracauer said:**
> 
The problem is that once you have a large codebase you can't switch languages, so you get along with your scripting language fine for 3 years and then somebody makes a requirement that pushes one subsystem into this zone. Then you can be screwed. Using foreign code, loading C code, for these subsystems only works in about half of the cases, in the other half the overhead of converting data and calling in and out of C eats up the advantage.

Excellent point,

---

### Post by giuspen on 2008-12-29
> **dribeas said:**
> Boost is kind of the standard non-standard library source. In fact some of the standard TR1 libraries are either Boost libs or barely changed from boosts.



1) system() in C will call exec a command in a shell

2,3,4) never needed it, but you could check the Boost::filesystem

From the four problems you provided it seems as if you are more interested in a scripting language than in a real programming language.

I don't know if I'm searching for a scripting language... I'm just finishing my first GTK application in PYGTK and I feel good programming this way but as I wrote in the beginning of this post I was trying to understand the loss of speed compared to C++ (that I use at my job together with C) and if there are good standard libraries someway comparable to python ones.
Probably I mistake but I think C++ could be good at higher levels too if supported by good standard libraries.
Thanks to everybody helped me in this post.
Regards,
Giuseppe.

---

### Post by dribeas on 2008-12-29
> **giuspen said:**
> I don't know if I'm searching for a scripting language... I'm just finishing my first GTK application in PYGTK and I feel good programming this way but as I wrote in the beginning of this post I was trying to understand the loss of speed compared to C++ (that I use at my job together with C) and if there are good standard libraries someway comparable to python ones.
Probably I mistake but I think C++ could be good at higher levels too if supported by good standard libraries.
Thanks to everybody helped me in this post.
Regards,
Giuseppe.

From the questions it seemed as if you were looking for a way of checking files and then calling a bash script to be executed on them. If that was the intention, then a shell script would probably be faster to code and to test than any programming language (probably using find -exec ). Anyway, you can use C libs for all that data (man stat, fstat) or you can try Boost::filesystem that probably has a C++ friendly interface to the same data. Anyway I've never used it personally.

---

### Post by davoudi on 2010-03-08
It is matter of how you want to approach the machine. Closer the language is to you, more price machine has to pay. Farther it goes, you pay more. It is a sort of duality we can't avoid it. 

 I use python/root/octave... for small problem/calculation and I could have a nice figure at the end.

 For heavy, complex and huge model, I use c++. It takes my time, but it gives me freedom to build each piece and be sure that every little piece is as efficient as I want. Then I put things together and have my big toy completed. I can easily reuse it for other heavy problem.

---

### Post by CptPicard on 2010-03-08
> **davoudi said:**
> 
 For heavy, complex and huge model, I use c++.

Depends. One can also approach this with the idea that a larger problem can be tackled with a higher-level approach to make it more manageable. Otherwise you just have both a huge problem and and solution that requires a lot of work per unit of problem...

> I can easily reuse it for other heavy problem.

Can you really, when the language doesn't quite yield as well to general reuse (think building functional operators) as some other languages?

---

### Post by davoudi on 2010-03-08
Language is of curse is not the goal, but one has to be fluent with it. If you practice c++ well, then you can efficiently use c++ to divide a big problem to its abstract components. Efficiency is crucial for big projects, that of course you are going to use them much.

---

### Post by TheStatsMan on 2010-03-09
Lately, I use mostly python + fortran instead of C++. I think for many large problems python+fortran is competitive with C++ speed wise, however for smaller problems the overhead of Python makes it significantly slower. Sometimes the speed differential is important sometimes it is not. 

In my experience with numerical problems it is always clear what parts of the problem are speed critical.  These bits are coded in fortran and the majority of code is programmed in Python.  Python is really a lot better than C++ for generic coding. Whilst you can write fairly generic code in C++ it takes a lot of work and a really good understanding of templates. You have a moment you feel like you are the greatest programmer in the world only to realise seconds latter that you have just achieved what any idiot can do in Python. The other thing I don't really like about C++ is that good C++ code is very efficient. Whilst this may seem like a good thing in some sense you are optimising much of your code needlessly. In reality efficiency doesn't matter in the majority of the code I write and for that code the generic nature of Python seems highly advantagous to me over straight C++. Now if I had to choose between C++ and Python for the problems I do the only choice would be C++ as Python is far too slow on its own. Further if my choice was between C++,C and Fortran, I would definitely choose C++. However, the mixed language approach totally changes the equation though as you can really get the best of both worlds for many problems.

---

### Post by Cracauer on 2010-03-09
> **TheStatsMan said:**
> However, the mixed language approach totally changes the equation though as you can really get the best of both worlds for many problems.

The problem is that if you have a complex application with data structures that need to be shared field-by-field between the two languages you lose if translation between the two languages' data format is required. Anything copying will kill you. Mandatory function calls for translation functions will kill you.

In practice I have only found some Common Lisp implementations to be really capable of accessing C data at full speed. They accept untagged raw machines words as various data types and hence they can at least read C data without delay. Writing is fine as long as you don't create new data (that means mutating existing structures is fine).

But for languages like Python or Java you'll have to restrict usage of more complex data to one or the other language. That means you cannot -say- load the data and do some costly preparation in C and then run a complex algorithm in Java on that C data without slowing down severely or without having to copy the data first.

---

