---
title: "Why don't more people use Jython?"
date: 2008-01-13
forum: Programming Talk
---

### Post by jacensolo on 2008-01-13
I haven't been using it long enough to make a final decision, but Jython seems to be great. It's Python with all of the Java classes! 

Actually I've just been using the command line so I have a few questions.

[LIST=1]
[*]Jython compiles to Java byte code and can use the same classes, so it is the same as Java, besides syntax?
[*]If the above is true then why don't more people use it?
[*]OR, for some odd reason is Jython not a good idea for fairly large applications? I mean Jython only, no Java.
[/LIST]

Basically I don't understand how it is a scripting language but is compiled into byte code. Before someone tries it, I do understand how Java compiles and how JVM works.

Thanks ahead of time for any responses. :)

---

### Post by LaRoza on 2008-01-13
> **jacensolo said:**
> 
[LIST=1]
[*]Jython compiles to Java byte code and can use the same classes, so it is the same as Java, besides syntax?
[*]If the above is true then why don't more people use it?
[*]OR, for some odd reason is Jython not a good idea for fairly large applications? I mean Jython only, no Java.
[/LIST]

Basically I don't understand how it is a scripting language but is compiled into byte code. Before someone tries it, I do understand how Java compiles and how JVM works.

Thanks ahead of time for any responses. :)

1. It is the same, you can even write applets with it

2. If they don't use Java already, why would they use it? If they do use Java, why learn another language/syntax? 

3. I don't know.

Python also compiles to byte code (and to binary executables). "Scripting" language is not really technical. C can be interpreted (with tcc, a great compiler/interpreter) and compiled.

---

### Post by CptPicard on 2008-01-13
> **LaRoza said:**
> 
2. If they don't use Java already, why would they use it? If they do use Java, why learn another language/syntax? 


Actually there is a really good reason, and that is why I am currently looking at integrating Jython with the Java toolkit I develop as my main line of business. Python is much more RAD than Java, and lets you really quickly code the non-performance intensive bits or those ones that can make do with a looser architecture. 

Then again, I might not actually want to distribute the toolkit in a form that requires both Java and Python to be present, not to mention the work that would go into all the process I/O I'd have to somehow use to glue the bits and pieces together. Being able to distribute just Java bytecode plus dependency jars is thus great.

---

### Post by LaRoza on 2008-01-13
> **CptPicard said:**
> Actually there is a really good reason, and that is why I am currently looking at integrating Jython with the Java toolkit I develop as my main line of business. Python is much more RAD than Java, and lets you really quickly code the non-performance intensive bits or those ones that can make do with a looser architecture. 

Then again, I might not actually want to distribute the toolkit in a form that requires both Java and Python to be present, not to mention the work that would go into all the process I/O I'd have to somehow use to glue the bits and pieces together. Being able to distribute just Java bytecode plus dependency jars is thus great.

Yes, I know there is a good reason. I was putting it from their perspective. There isn't a NEED for it. It is most likely known and used by those who like Python, but need Java. 

It is like C with Python syntax, it would be a good idea, and make C possibly easier to use, but there is no need for it. If there is a project like this, I never heard of it.

---

### Post by Wybiral on 2008-01-13
> **LaRoza said:**
> It is like C with Python syntax, it would be a good idea, and make C possibly easier to use, but there is no need for it. If there is a project like this, I never heard of it.

[PyRex]("http://www.cosc.canterbury.ac.nz/greg.ewing/python/Pyrex/")! In fact, I use PyRex myself from time-to-time.

Why? Because it allows for super-fast Python modules without hassling with the Python-C API (which is a pain, as anyone who's ever messed with it would know) or code in raw C at all for that matter. There's also [TinyPy]("http://www.philhassey.com/blog/2007/12/22/64k-version-of-python-is-4234x-faster-than-c-python/"), but I believe the developer is considering writing a VM for it instead of compiling directly to C.

---

### Post by pmasiar on 2008-01-13
> **jacensolo said:**
> 
Jython compiles to Java byte code and can use the same classes, so it is the same as Java, besides syntax?

No, it is **better** than Java: you have dynamic typing, list comprehension and all the Python goodies. Including inheriting from Java objects.

> If the above is true then why don't more people use it?

Because clueless Sun's marketoids are brain-dead promoting Java "brand" even in places where it does not make any sense, like "Java Desktop"?

Jython was created 10 years ago, and Sun ignored it, and let MSFT snatch lead developer to create competing product, IronPython (Python for .NET, on top of C#). Now they realized the mistake, but **still** cannot confess they were wrong, so they promote (and support development of)  JRuby, but not Jython.

One can tell that MSFT are software development company, some top people **do** have a clue: best way to develop apps is to glue libraries (written for speed in statically typed language like C# or C) using some dynamically typed language, like Python, Perl, or Ruby. Java tries to be both, and fails. And .NET VM is being optimized to run dynamically typed languages, so it would beat JVM in both run speed and development speed. Now Sun is scared and tries to save what it can, but might be too late.

Of course Java will stay with us for 30 more years, but it will cease to be intellectual leader, like some COBOL++. 

Another reason is that Java is used in "enterprise" software - IOW clueless PHB decided what to use, as he overheard at this golf match. He never heard of Jython - so it is forbidden to be used. (Happens to me all the time).

IMHO, YMMV. :-)

> OR, for some odd reason is Jython not a good idea for fairly large applications? I mean Jython only, no Java.

No, Python/Jython is IMHO **better** choice for big applications, even over Java. The only problem is, Jython is not developed as intensively as it deserves - and it is entirely Sun's brain dead policies.

But it picked speed again, was included in Summer of Code, and they prepare Jython 2.5 release in 2008 IIRC.

> Basically I don't understand how it is a scripting language but is compiled into byte code. Before someone tries it, I do understand how Java compiles and how JVM works.

Python runs dynamically typed code on top of statically typed C code. Same in Jython. Instead of compiler resolving binding method name with executable code address, Python/Jython does it at the runtime.

---

### Post by kevykev on 2008-01-13
> No, it is **better** than Java: you have dynamic typing

Dynamic typing isn't necessarily better than static typing. Check out the first presentation on this page:

[http://www.javalobby.org/java/forums/t105120.html]("http://www.javalobby.org/java/forums/t105120.html")

Significant available type information is what makes good IDE auto-completion possible (the kind of thing you see in eclipse and netbeans), It also allows more errors to be caught at compile time. It enables several technologies like GWT and automatic bug pattern detection.

Of course, dynamic typing has advantages over static typing too. Just wouldn't say that one technology is better than the other.

---

### Post by Jessehk on 2008-01-13
```

$ pacman -Ss python | wc -l
338
$ pacman -Ss jython | wc -l
0

```

;)

---

### Post by CptPicard on 2008-01-13
On the other hand, auto-completion type information is what you need when you can potentially have serious type conflicts, which statically typed languages produce more than dynamically typed ones. So it solves the problem that is partially caused by being in the environment for that problem in the first place.

Interestingly, in Java coding, you are seeing more and more the idea of programming to interfaces instead of extending classes. This is in some sense a move towards duck typing. There is merely an external contract over behaviour instead of actual hard-coded behaviour behind the contract that you would reuse.

Java is in some sense an odd bird that would have a lot of potential if made use of properly, and a lot of this has to do with the typing system tradeoff. I have a strong suspicion that whenever you move away from static typing to higher level constructs, you just have to essentially up the abstraction of your virtual machine, which has serious repercussions to the speed of your code. Java as it is is, properly coded, not too far from C++ in speed -- at least not if you also consider the speed of development in relation to speed of the result. But, unfortunately, it also falls short on some really key aspects that even higher-level languages provide -- I am such a sucker for functional programming that my code is strewn with anonymous inner classes pretending to be closures, and "final" wrappers supporting those.

Give me a language that compiles to something close to Java's speed and has proper closures (which enable a lot of other interesting structures), and I'm sold... I'm not sure if that is doable, though.

---

### Post by kevykev on 2008-01-13
> ...my code is strewn with anonymous inner classes pretending to be closures, and "final" wrappers supporting those.

Give me a language that compiles to something close to Java's speed and has proper closures (which enable a lot of other interesting structures), and I'm sold... I'm not sure if that is doable, though.

I couldn't agree more! 

I think closures are being considered as an enhancement for Java 7 :-)

---

### Post by Jessehk on 2008-01-13
> Give me a language that compiles to something close to Java's speed and has proper closures (which enable a lot of other interesting structures), and I'm sold... I'm not sure if that is doable, though.

D? It has full closure support and compiles to native code.

---

### Post by pmasiar on 2008-01-14
> **kevykev said:**
> Significant available type information is what makes good IDE auto-completion possible (the kind of thing you see in eclipse and netbeans), It also allows more errors to be caught at compile time. It enables several technologies like GWT and automatic bug pattern detection.


(BTW I qualified my opinion with "IMHO", you probably replied to first draft save of my comments)

As CptPicard said previously, Java needs IDE with auto-completion because if has thousands of classes which no human can remember. Sometimes I feel like we just replaced spaghetti code with a **ravioli code** - hundreds and thousands of small little bite-size object, and you need to consume them one by one, checking what filling they have :-)

And your argument about relying on compiler to find you errors is bogus, this approach is considered so '90. 

Today, [http://en.wikipedia.org/wiki/Test-driven_development](http://en.wikipedia.org/wiki/Test-driven_development) is widely considered next "paradigm shift", like OOP was in '80. Even world-known Java expert, Bruce Eckel (author of "Thinking in Java", today in 4th edition, which speaks for it's quality) considers TDD be superior paradigm compared with static type checking. After all, checking for type (or better and more flexible, for availability of methods) is just first and most trivial test you will write for your code.

I provided links in previous discussions about Python vs Java, if some good gnome would dig them out s/he will earn my thanks.

---

### Post by LaRoza on 2008-01-14
> **pmasiar said:**
> 
I provided links in previous discussions about Python vs Java, if some good gnome would dig them out s/he will earn my thanks.

> **pmasiar said:**
> 
Read [why hacker use python]("http://www2.linuxjournal.com/article/3882") [language for next 100 years]("http://www.paulgraham.com/hundred.html") [wikipedia entry for Python]("http://en.wikipedia.org/wiki/Python_%28programming_language%29") and [Comparison of programming languages]("http://en.wikipedia.org/wiki/Comparison_of_programming_languages#Expressiveness")


I am not a gnome, but a bot.

---

### Post by kevykev on 2008-01-14
> (BTW I qualified my opinion with "IMHO", you probably replied to first draft save of my comments)

Apologies, I did indeed.

> Java needs IDE with auto-completion because if has thousands of classes which no human can remember

If you program gtk in python, you also have a significant amount to remember. I know, I often write code for PyGTK and auto-completion would be a very useful tool for me indeed. PyGTK (QT/Python, WxPython etc) also have several thousand functions.

> And your argument about relying on compiler to find you errors is bogus, this approach is considered so '90.

This is not just my argument, but the opinion of several other experts.  For instance Joshua Bloch, the author of Effective Java. 

Here is the argument: Test driven development is great. Testing is a necessary but not sufficient method for proving programs are correct. The state space of any moderate program (class, function etc.) is generally exponentially large, thus not all cases can be tested, only a subset of significant cases and boundary conditions can be considered. As such, all additional automated bug checking is a good thing, it reduces the probability of an error by building robustness into the program. In a static typed language, a lot of this can be done by the compiler and external programs such as findbugs.

Generally I use unit-tests, along side static type checking + automated bug pattern testing to ensure maximum code robustness.

Anyway.. I'm not trying to say that static typing is better than dynamic typing. I'm just saying that they both have their advantages and disadvantages. It just upsets me when somebody says that static typing is obsolete as a matter of fact, myself and many experts believe that this is not the case.

---

### Post by Wybiral on 2008-01-14
As far as remembering Python module functionality, I've found the interactive console to be a lifesaver in this area. You can quickly test something and get instant feedback, especially the "dir" builtin... What a handy tool!

---

### Post by pmasiar on 2008-01-14
> **kevykev said:**
> 
Anyway.. I'm not trying to say that static typing is better than dynamic typing. I'm just saying that they both have their advantages and disadvantages. It just upsets me when somebody says that static typing is obsolete as a matter of fact, myself and many experts believe that this is not the case.

I agree with you. It just upsets **me** when someone (not you, but there are many of them) thinks that static typing is inherently better and less error prone than dynamic typing, without even bothering with tests. 

IMHO static typing has it place for low-level libraries where code effectiveness is crucial. For higher-level task, Dynamic typing is **safer** IMHO.

I do it all the time: store my objects in collection, then later get them back and cast them into a type. What if I miscast? OTOH in dynamic typing I don't fool  with instances like that, I let computer to remember proper type info and do the right thing for me.

Edit: BTW Re argument about [http://en.wikipedia.org/wiki/Joshua_Bloch](http://en.wikipedia.org/wiki/Joshua_Bloch). I am not sure what JB does for living, but I would be not surprised if he writes tools for statically typed languages like Java.

Compared to that Bruce Eckel consults and solves real-life problems. He was proponent of statically typed languages (C++ and Java), but later he realized that he does not need static type checks (he writes tests for it), and quite often types are just in the way when solving problems. 

Like one of the Java's problems: zillions of classes of slightly different flavors, compared with generic functions of Python. "x in Y" loops exactly same through lists, arrays, dictionaries, iterators, generators, and your own classes.

---

### Post by kevykev on 2008-01-14
> Edit: BTW Re argument about [http://en.wikipedia.org/wiki/Joshua_Bloch](http://en.wikipedia.org/wiki/Joshua_Bloch). I am not sure what JB does for living, but I would be not surprised if he writes tools for statically typed languages like Java.

Close enough ;-) He wrote a lot of the sun implementation of the java api (collections, concurrency etc.). He now works for google.

> Compared to that Bruce Eckel consults and solves real-life problems.

Well I wouldn't say that Josh Bloch doesn't solve real-life problems, but ok, i take your point. I would say, however, that *I* personally solve a variety of real life problems in my code. Granted, i often use python (i'm writing a python program as I write this email), however, I also use C++ and Java frequently. Remember that the backend to many python libs is written in C/C++ code. (so is the backend to the graphics libraries in Java actually). I sometimes need to develop this backend code (esp image processing stuff) and simply cant get the required performance in python (or java sometimes!), so i gotta use C++.

I know i'm re-iterating the old "right tool for the right job", but that's really what I think!

> .. "x in Y" loops exactly same through lists, arrays, dictionaries, iterators, generators, and your own classes.

Btw, you can do this in java for a while now
```

List<String> list = ...
for (String s : list) { ... }

```

Also works for maps, sets etc, anything that implements Iterable<T>. But nonetheless, I agree some of the syntax in Java is still a little cumbersome (esp. lack of closures). My only complaint about python syntax is having to type "self" all the frickin time ;-P

---

### Post by Wybiral on 2008-01-14
> **kevykev said:**
> My only complaint about python syntax is having to type "self" all the frickin time ;-P

It makes up for it by not having to type all of those brackets and type definitions :p

---

### Post by kevykev on 2008-01-14
> **Wybiral said:**
> It makes up for it by not having to type all of those brackets and type definitions :p

Heh, true. Though nowadays my IDE does most of that for me

---

### Post by LaRoza on 2008-01-14
> **kevykev said:**
>  My only complaint about python syntax is having to type "self" all the frickin time ;-P
You don't have to use 'self'.

---

### Post by pmasiar on 2008-01-14
> **kevykev said:**
> Close enough ;-) He wrote a lot of the sun implementation of the java api (collections, concurrency etc.). He now works for google.

This was also at the wikipedia page I linked, so yes I know. But hardly JB can pretend to be unbiased in his opinions about statically typed language like Java? Do you expect him to confess he wasted 15 years of life? Obviously not gonna happen, he is invested to prove Java.

> 
Well I wouldn't say that Josh Bloch doesn't solve real-life problems, but ok, i take your point. ...Remember that the backend to many python libs is written in C/C++ code. 

When you will be reading my older posts, you will see that I always reiterate Python for speed of development of high-level code and C for speed in libraries, you don't need to persuade **me**. :-)

---

### Post by kevykev on 2008-01-14
> **LaRoza said:**
> You don't have to use 'self'.

Ha ha, right you are! I never knew that was just convention! You've made my day :-D

---

### Post by LaRoza on 2008-01-14
> **kevykev said:**
> Ha ha, right you are! I never knew that was just convention! You've made my day :-D

Sarcasm? I can't tell...

Well, you can use anything you want. Most of the time self is used. I often have the feeling to use "this".

---

### Post by kevykev on 2008-01-14
> But hardly JB can pretend to be unbiased in his opinions

Yeah you're probably right there, that's why I said I take your point. I think i'm reasonably impartial myself though. 

> Do you expect him to confess he wasted 15 years of life?

Bit harsh mate. IMO core software engineering skills are language independent.

> When you will be reading my older posts, you will see that I always reiterate Python for speed of development of high-level code and C for speed in libraries, you don't need to persuade **me**.

Heh, ok, ok, i'll read the other posts :-P

---

### Post by Peyton on 2008-01-14
> **LaRoza said:**
> Sarcasm? I can't tell...

Well, you can use anything you want. Most of the time self is used. I often have the feeling to use "this".

Use *self*:

[http://www.python.org/dev/peps/pep-0008/](http://www.python.org/dev/peps/pep-0008/)

---

### Post by kevykev on 2008-01-14
> **LaRoza said:**
> Sarcasm? I can't tell....

No, honestly. Learn something new every day i guess

---

### Post by LaRoza on 2008-01-14
> **kevykev said:**
> No, honestly. Learn something new every day i guess

I don't recommend changing it to something else. It is an interesting feature of the language that is optional, but almost written in stone.

---

### Post by jacensolo on 2008-01-15
Well this thread went off-topic. 

I still couldn't find an answer. If I write Jython program x to do the same as Java program x, will it compile to the same byte code therefore being the same as Java (besides what you typed to make the program)? Does the JVM interpret it the same way? If it does then Jython programmers can make the exact same programs as Java programmers being more efficient. 

Someone said why program jython when you know python or Java. The reason I would think if my above question/statement is correct is that it will be able to go on smaller devices and you will have access to all of the  gui and other tools that Java has. Am I correct?

---

### Post by CptPicard on 2008-01-15
> **jacensolo said:**
> I still couldn't find an answer. If I write Jython program x to do the same as Java program x, will it compile to the same byte code therefore being the same as Java (besides what you typed to make the program)?

No, it doesn't. The bytecodes are not identical -- although of course both are valid Java bytecode -- as of course the languages are quite different, and in addition, Jython relies on its own external .jar to provide the Python standard library functionality and language you use from your Jython code. If you dump the Java source compiled from your Jython source, you see that it's essentially turned into kind of interpreted Python on top of the Jython library. Then, *that* is compiled into Java bytecode. It's much more indirect than "raw" Java.

> Does the JVM interpret it the same way?

Both being Java bytecode, yeah. But it's not the same bytecode, nor does it do the same thing although the outward semantics might be the same.

> If it does then Jython programmers can make the exact same programs as Java programmers being more efficient. 

More efficient as programmers, yes... more efficient as code, no.

> The reason I would think if my above question/statement is correct is that it will be able to go on smaller devices and you will have access to all of the  gui and other tools that Java has. Am I correct?

It goes the other way around. There is certainly a performance penalty to adding the layers of indirection Jython introduces. But it of course lets you use all the handy language features Jython has... it's a tradeoff.

---

### Post by pmasiar on 2008-01-15
As CptPicard said: Jython will be not the same binary (because of added layer of abstraction, to run Jython bytecode interpreted by JVM), but the same functionality. Including inheriting from Java classes.

Whole point is to let JVM to work harder for you, let Jython manage some tasks what are managed by programmer in plain Java (like dynamic typing).

---

### Post by tenmillionmilesaway on 2008-01-16
Why don't more people use Jython? - because there is [groovy]("http://groovy.codehaus.org/") instead.  Which has dynamic features and closures and such, but is 100% compatable with java.

---

### Post by jacensolo on 2008-01-16
> **CptPicard said:**
> No, it doesn't. The bytecodes are not identical -- although of course both are valid Java bytecode -- as of course the languages are quite different, and in addition, Jython relies on its own external .jar to provide the Python standard library functionality and language you use from your Jython code. If you dump the Java source compiled from your Jython source, you see that it's essentially turned into kind of interpreted Python on top of the Jython library. Then, *that* is compiled into Java bytecode. It's much more indirect than "raw" Java.



Both being Java bytecode, yeah. But it's not the same bytecode, nor does it do the same thing although the outward semantics might be the same.



More efficient as programmers, yes... more efficient as code, no.



It goes the other way around. There is certainly a performance penalty to adding the layers of indirection Jython introduces. But it of course lets you use all the handy language features Jython has... it's a tradeoff.

Finally, thanks!


> **tenmillionmilesaway said:**
> Why don't more people use Jython? - because there is [groovy]("http://groovy.codehaus.org/") instead.  Which has dynamic features and closures and such, but is 100% compatable with java.

As interesting as that looks (which is very interesting) I think I'll stick with Python. I'm taking a Java class this semester, so I have to learn that.

---

### Post by pmasiar on 2008-01-16
Jython community recently revived. One of comitters "complained" that community send him more patches than he can apply. They released long-delayed Jython 2.2, aim for Jython 2.5, and best of all, **Django on Jython** is almost ready! Only some obscure items, like order of the tests does not pass! 

Django on Jython will be most agile and productive web framework for JVM, and it is coming soon.

---

### Post by kevykev on 2008-01-16
> **tenmillionmilesaway said:**
> Why don't more people use Jython? - because there is [groovy]("http://groovy.codehaus.org/") instead.  Which has dynamic features and closures and such, but is 100% compatable with java.

That looks pretty cool! Actually, this got me looking into at other languages that compile to java byte code and i came across [Nice]("http://nice.sourceforge.net/"). It doesn't have dynamic types, but it does perform as fast as regular java (from what I read, and i hear groovy is about 10 times slower), and features some really nice (no pun intended) language features like anonymous functions, optional method parameters and methods that return tuples. Might just have to learn me a new language :-)

---

### Post by pmasiar on 2008-01-16
Groovy looks too verbose for a decent scripting language, IMHO.

Many people who are concerned about multithread programming on dozens of CPU cores which are coming soon, say that [Scala](http://en.wikipedia.org/wiki/Scala_%28programming_language%29) is the next high-level JVM language (Java having role of C).

---

### Post by kenshin1733 on 2012-12-20
> **Jessehk said:**
> D? It has full closure support and compiles to native code.


I have tried D and have never loved any language more than that. It is like best of everything put together to achieve something so powerful. 

Its like a gem waiting to be discovered by the world and gain mainstream acceptance. 

If someone could write a bytecode compiler for D? But then, that's not the topic of this thread.

---

### Post by Bachstelze on 2012-12-20
> **kenshin1733 said:**
> I have tried D and have never loved any language more than that. It is like best of everything put together to achieve something so powerful. 

Its like a gem waiting to be discovered by the world and gain mainstream acceptance.

I bet it would cure cancer and eliminate world hunger!

---

### Post by slavik on 2012-12-22
dead things stay dead.

---

