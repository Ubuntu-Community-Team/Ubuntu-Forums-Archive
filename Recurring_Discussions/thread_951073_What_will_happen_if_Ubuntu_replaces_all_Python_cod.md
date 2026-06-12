---
title: "What will happen if Ubuntu replaces all Python code with C/C++ code?"
date: 2008-10-17
forum: Recurring Discussions
---

### Post by verb3k on 2008-10-17
The use of Python in ubuntu is beyond any question. Will any software engineer opt to use a scripting language in a serious and demanding platform?

---

### Post by gletob on 2008-10-17
My answer:
Whatever as long as it works for me.

---

### Post by LaRoza on 2008-10-17
Speed isn't the issue.

It would be a stupid move. The elements that are using Python are using it for a reason.

Anyone who voted for the first option has no understanding of the topic (if they are programmers, they are [speed kiddies](http://en.wikipedia.org/wiki/Speed_kiddie)).

Might as well ask what it would be like if all the C parts were written in assembly.

---

### Post by snova on 2008-10-17
What question would that be? :x

Absolutely.

In response to your ridiculous subject, here's what would happen. First all the developers would be told to rewrite the massive Python infrastructure in horrible, difficult, complex languages. Then Ubuntu would delay the next release by, oh, say, two years? What do you think? Then none of it would work right, so that'd take longer! Then it'd be hard to maintain, so everybody would leave.

Launchpad is written in Python (AFAIK). Besides, how much of the system is even written in Python, anyway?

---

### Post by LaRoza on 2008-10-17
> **snova said:**
> 
Launchpad is written in Python (AFAIK). Besides, how much of the system is even written in Python, anyway?

Many apps are written in Python, however, the "speed" isn't an issue. Most apps sit there waiting for user interaction, and have the parts that need to be optimized written in C. 

The Ubuntu installer is written in Python for example.

---

### Post by cardinals_fan on 2008-10-17
In general, I have found pure C apps to be more carefully designed and lighter.  However, there is no reason Python produces bad code in and of itself.  All languages are merely tools for programmers.  A good programmer produces good code.

In other words, this whole premise is absurd.

---

### Post by MaxIBoy on 2008-10-17
Speaking as a programmer, I am a believer in optimization, but more than that I am a believer in minimalism and maintainability. 

Python is a joy to use. I know Python and C++, and I mostly use Python. As far as I'm concerned, a good, well-designed algorithm can be expressed readably in any language, and runs fast *before* optimization. Python is a good test of whether or not an algorithm is a good one.

I've fallen prey to premature optimization, and I refuse to do so again. Premature optimization resulted in me needing to rewrite entire projects, and tended to hide poor algorithms behind a facade of false confidence. 

As far as I'm concerned, rewriting in low-level languages and optimization should NOT take place until the entire thing is FINISHED, GUARANTEED STABLE, and LIKELY TO NEVER NEED TO BE MODIFIED. For a project like Ubuntu, almost NOTHING qualifies for this.

My focus is on game engines/rendering, so I have different requirements than most, but even so, I only ever rewrite something in C++ after a major release (every compiled version is essentially a fork,) and since none of my projects have thus far gotten out of the pre-alpha stage, I've only done this a few times. However, when I am writing one of these versions, readability goes out the window and I try to improve performance as much as possible, with language-specific features and goto statements should that be needed.

---

### Post by Calmatory on 2008-10-17
How Ubuntu isn't fast? Most of the time the bottleneck lies somewhere else than the CPU which is crunching the instructions. 

More Python please! More Perl! More RUBY! More shell scripts! ...as long as everything is stable and speed is no concern.

---

### Post by cardinals_fan on 2008-10-17
> **Calmatory said:**
> More RUBY!
Quoted for truth.  Of all the languages I've scripted in, Ruby is the most natural.  It flows almost like a real (non-coding) language.

---

### Post by MaxIBoy on 2008-10-17
More so than Python? 

Now I'm interested.

---

### Post by cardinals_fan on 2008-10-17
> **MaxIBoy said:**
> More so than Python? 

Now I'm interested.
I recognize that Python is the darling of the coding world at the moment, but I was never taken with it.  Somehow, it just seemed very unnatural in its syntax.  How I could tolerate Perl instead, I'll never know.

Anyway, Ruby is a bit different.  The [About Ruby]("http://www.ruby-lang.org/en/about/") page is a good intro.  This quote sums up a lot of what I like about Ruby:

> Ruby is a language of careful balance. Its creator, Yukihiro &#8220;matz&#8221; Matsumoto, blended parts of his favorite languages (Perl, Smalltalk, Eiffel, Ada, and Lisp) to form a new language that balanced functional programming with imperative programming.

He has often said that he is &#8220;trying to make Ruby natural, not simple,&#8221; in a way that mirrors life.

Building on this, he adds:

    [QUOTE]Ruby is simple in appearance, but is very complex inside, just like our human body.[/QUOTE]
Before you take all my word as truth (after all, who wouldn't ;)), let me append a warning:  I am a fairly proficient scripter, in that I write a number of scripts in varying languages to automate common tasks in my computing life.  However, I have no real experience with major projects, so perhaps your needs are different.

EDIT: You might want to read [http://www.ruby-lang.org/en/documentation/ruby-from-other-languages/to-ruby-from-python/](http://www.ruby-lang.org/en/documentation/ruby-from-other-languages/to-ruby-from-python/)

---

### Post by LaRoza on 2008-10-17
> **cardinals_fan said:**
> In general, I have found pure C apps to be more carefully designed and lighter.  However, there is no reason Python produces bad code in and of itself.  All languages are merely tools for programmers.  A good programmer produces good code.


Python is written in C

---

### Post by MaxIBoy on 2008-10-17
Not necessarily. No language is actually written in another language. The compiler/interpreter is just implementation. Jython is just as much Python as cPython is.

---

### Post by cardinals_fan on 2008-10-17
> **LaRoza said:**
> Python is written in C
...which is my point.  I was saying that the language used is not the determining factor in the quality or performance of an application.

---

### Post by MaxIBoy on 2008-10-17
Also my point. I'm sure it's possible to have a PCI-E hardware Python interpreter that runs blazingly fast. Actually, that would be awesome. I'd never need a compiled language again.

---

### Post by xebian on 2008-10-17
> **LaRoza said:**
> 
Might as well ask what it would be like if all the C parts were written in assembly.

C/C++ compilers are now so advanced the resulting machine code will be the same.:)

---

### Post by snova on 2008-10-17
Python is too dynamic to compile well. There's simply too much that must be decided at runtime. Although a good optimizer (and well written code) could probably hack it down fairly well...

I'm only just starting Ruby. I find some of its syntax strange, but mostly it just feels messy under the fingers. A bit like Perl, actually- a kind of disordered, messy, hacky feeling that won't go away. Python feels sleek, and C impresses on something raw, cold and hard.

It's strangeness does empower certain features that I find really neat, though. Like being able to pass blocks of code as function parameters in such a way that you can almost create new... what are they called... well, in the same family as "if", "while", and so on.

---

### Post by LaRoza on 2008-10-17
> **MaxIBoy said:**
> Not necessarily. No language is actually written in another language. The compiler/interpreter is just implementation. Jython is just as much Python as cPython is.

I know. The Python on Ubuntu is the question here, and that is CPython.

---

### Post by MaxIBoy on 2008-10-17
> **snova said:**
> Python is too dynamic to compile well. There's simply too much that must be decided at runtime. Although a good optimizer (and well written code) could probably hack it down fairly well...

I'm only just starting Ruby. I find some of its syntax strange, but mostly it just feels messy under the fingers. A bit like Perl, actually- a kind of disordered, messy, hacky feeling that won't go away. Python feels sleek, and C impresses on something raw, cold and hard.

It's strangeness does empower certain features that I find really neat, though. Like being able to pass blocks of code as function parameters in such a way that you can almost create new... what are they called... well, in the same family as "if", "while", and so on.

Control structures? 

I do know exactly what you mean. It's easy to get carried away with that kind of power, though. I wouldn't attempt something like that unless I had a VERY good reason, even though I admit that it's quite tempting.

> **LaRoza said:**
> I know. The Python on Ubuntu is the question here, and that is CPython.
Touché.

---

### Post by cardinals_fan on 2008-10-17
> **snova said:**
> 
I'm only just starting Ruby. I find some of its syntax strange, but mostly it just feels messy under the fingers. A bit like Perl, actually- a kind of disordered, messy, hacky feeling that won't go away. Python feels sleek, and C impresses on something raw, cold and hard.

It's strangeness does empower certain features that I find really neat, though. Like being able to pass blocks of code as function parameters in such a way that you can almost create new... what are they called... well, in the same family as "if", "while", and so on.
I started with Perl, and it remains my favorite.  Nothing scripts better :)

---

### Post by MaxIBoy on 2008-10-17
Bah. My personal favorite is BASH and Python intermingled in the same script (looks even uglier than it sounds like it would.) :)

---

### Post by cardinals_fan on 2008-10-17
> **MaxIBoy said:**
> Bah. My personal favorite is BASH and Python intermingled in the same script (looks even uglier than it sounds like it would.) :)
I mix Perl and Zsh sometimes.  It works pretty well.

---

### Post by MaxIBoy on 2008-10-17
I bet you I could intermingle BASH, DOS (WINE's implementation of cmd.exe,) <insert name of any other shell(s) here,> any language for which there is an interpreter (read: any language period,) AND some config files.

I shudder to think.

---

### Post by verb3k on 2008-10-18
If we compare Deluge with utorrent it surely makes sense to ditch Python.
Apart from the fact that utorrent uses minimal dependencies, it is exceedingly obvious that C++ has boosted the performance of utorrent by miles. It doesn't require a software guru to tell you that C++ is one of the fastest programming languages around. (C for OSs)

You won't know the difference until you try ubuntu on an old machine. The amount of time it takes to invoke the interpreter, read and analyze the code and determine variable types and execute the code is very high.

---

### Post by techmarks on 2008-10-18
I don't think this would make much sense.

Sure some programs would execute faster, but at what cost.

The Python code works now and gets the job done now.

If execution speed was the main concern, they should have thought of that before writing all the Python code.

At this stage it would be a large time consuming, error prone task, and all for what?

---

### Post by LaRoza on 2008-10-18
> **verb3k said:**
> If we compare Deluge with utorrent it surely makes sense to ditch Python.
This thread is a breeding ground for silliness.

I don't even know how to explain that.

Deluge and utorrent do two main things, wait, and download or upload. The low level features of both are written in C. (It is likely the GUI of Deluge that is mostly Python). 

> 
it is exceedingly obvious that C++ has boosted the performance of utorrent by miles. It doesn't require a software guru to tell you that C++ is one of the fastest programming languages around. (C for OSs)


[img]http://www.terminally-incoherent.com/img/facepalm.jpeg[/img]

---

### Post by MaxIBoy on 2008-10-18
Building a faster starter motor on a car does you no good, because that's not where the bottleneck is.

---

### Post by Canis familiaris on 2008-10-19
> **MaxIBoy said:**
> Building a faster starter motor on a car does you no good, because that's not where the bottleneck is.

EPIC Statement.

---

### Post by verb3k on 2008-10-19
> **LaRoza said:**
> This thread is a breeding ground for silliness.

I don't even know how to explain that.

Deluge and utorrent do two main things, wait, and download or upload. The low level features of both are written in C. (It is likely the GUI of Deluge that is mostly Python). 



[img]http://www.terminally-incoherent.com/img/facepalm.jpeg[/img]

Sir Admin, Were you not educated present your arguments in a respectable way?

>  (It is likely the GUI of Deluge that is mostly Python).

That's why it takes 15 seconds for the program to initialize the Deluge GUI on my rig, and that's why it takes 3 or 4 seconds to open a context menu. utorrent is much faster on the same machine even though it is being run under Wine.

Next time stop posting images and do speak sense, ok?

---

### Post by techmarks on 2008-10-20
I do think the OP had a point.

If you pay attention you'll notice it too.

The apps written in Python always have a delay to start up, some worse than others, and sometimes it's extremely noticeable.

---

### Post by LaRoza on 2008-10-20
> **verb3k said:**
> 
Apart from the fact that utorrent uses minimal dependencies, it is exceedingly obvious that C++ has boosted the performance of utorrent by miles. It doesn't require a software guru to tell you that C++ is one of the fastest programming languages around. (C for OSs)


> **verb3k said:**
> Sir Admin, Were you not educated present your arguments in a respectable way?

(Or madame)

Respectable, I can do. However, I cannot argue with the above quoted statement. It fails on so many levels it isn't even wrong.

> 
That's why it takes 15 seconds for the program to initialize the Deluge GUI on my rig, and that's why it takes 3 or 4 seconds to open a context menu. utorrent is much faster on the same machine even though it is being run under Wine.

Naturally, you decide to use this as a basis for saying it is Python's fault. Deluge doesn't take long to start or work on my machine. Does that mean it does this for all machines? Apparently, not. Neither should you assume everyone has the same experiences.

> 
Next time stop posting images and do speak sense, ok?

I'll stop posing images when other speak sense, ok?

---

### Post by saulgoode on 2008-10-20
> **LaRoza said:**
> Anyone who voted for the first option has no understanding of the topic (if they are programmers, they are [speed kiddies](http://en.wikipedia.org/wiki/Speed_kiddie)).

Might as well ask what it would be like if all the C parts were written in assembly.
No. The speed and resource benefits of coding in assembler versus coding in C come at a price of the code not running on different processors. No such loss of cross-platform capability would occur were programs written in interpreted Python source to be implemented in C.

---

### Post by verb3k on 2008-10-21
> **MaxIBoy said:**
> Building a faster starter motor on a car does you no good, because that's not where the bottleneck is.

Well, ubuntu has a lot of bottlenecks, among which is the extensive use of Python.

---

### Post by dracule on 2008-10-21
> **verb3k said:**
> Well, ubuntu has a lot of bottlenecks, among which is the extensive use of Python.

he is saying a bad algorithm is a bad algorithm. Changing the language wont help it at all.

---

### Post by verb3k on 2008-10-21
> **dracule said:**
> he is saying a bad algorithm is a bad algorithm. Changing the language wont help it at all.

A bad algorithm written in a compiled language is still faster than a bad algorithm written in an interpreted language.

---

### Post by LaRoza on 2008-10-21
> **verb3k said:**
> Well, ubuntu has a lot of bottlenecks, among which is the extensive use of Python.

No...

> **verb3k said:**
> A bad algorithm written in a compiled language is still faster than a bad algorithm written in an interpreted language.

Python isn't an interpreted language.

---

### Post by verb3k on 2008-10-22
> **LaRoza said:**
> No...



Python isn't an interpreted language.

*sigh*
[http://manpages.ubuntu.com/manpages/hardy/man1/python2.5.html](http://manpages.ubuntu.com/manpages/hardy/man1/python2.5.html)

---

### Post by Canis familiaris on 2008-10-22
> **verb3k said:**
> *sigh*
[http://manpages.ubuntu.com/manpages/hardy/man1/python2.5.html](http://manpages.ubuntu.com/manpages/hardy/man1/python2.5.html)

No not interpreted per se but the byte code produced is interpreted at runtime which is much faster...


BTW before bashing Python consider. have you ever programmed in Python? 
D'You know Ubiquity is written in Python? I doubt whether it will be faster with C or ASM since most of the time it waits for user input. There is Envy as well, and countless other open source projects written in Python too...

---

### Post by brunovecchi on 2008-10-22
I am not a programmer, but I do some amateur perl programming as a hobby. This discussion arose many times before, and I think that the key to the answer is taking into account development time.
Sure, you could write an application in C that runs an order or two of magnitude faster than one written in perl/python/ruby/etc. But what's more valuable? CPU time or manpower? Would you rather have your application run a fraction of a second faster but having to wait 5/6 years between releases, or wait that half a second more and have a six month release cycle with new features and an incredible development pace?

Perl, Python and Ruby (and other languages that I might not know of) are languages that fill a particular niche, and that niche appeared when programmers became more expensive than hardware. And I think that choosing Python over C is a wise choice for many of the projects of a distro developer.

---

### Post by LaRoza on 2008-10-22
> **verb3k said:**
> *sigh*
[http://manpages.ubuntu.com/manpages/hardy/man1/python2.5.html](http://manpages.ubuntu.com/manpages/hardy/man1/python2.5.html)

It is wrong, or at least, less accurate.

Python isn't executed line by line any more than C is. Python is compiled to an assembly code and executed. 

Before continuing, what is your programming experience? I'd hate to be arguing with someone with little knowledge, because it negates my knowledge.

---

### Post by verb3k on 2008-10-22
> **Anurag_panda said:**
> No not interpreted per se but the byte code produced is interpreted at runtime which is much faster...


D'You know Ubiquity is written in Python? I doubt whether it will be faster with C or ASM since most of the time it waits for user input. There is Envy as well, and countless other open source projects written in Python too...

Ubiquity and Envy are ok with Python because they are run once in an installation. You don't install ubuntu everyday on the same machine, or install video drivers everyday.

> BTW before bashing Python consider. have you ever programmed in Python? 

Yes.

---

### Post by LaRoza on 2008-10-22
> **verb3k said:**
> Ubiquity and Envy are ok with Python because they are run once in an installation. You don't install ubuntu everyday on the same machine, or install video drivers everyday.


That doesn't make sense.

---

### Post by verb3k on 2008-10-22
> **LaRoza said:**
> It is wrong, or at least, less accurate.

Python isn't executed line by line any more than C is. Python is compiled to an assembly code and executed. 


That's what I have been trying to tell you. The issue wasn't about terminology, rather it was about the fact that "Python is compiled to an assembly code and executed". It takes some time to compile and then execute. On some machines it's in milliseconds, on others it is way more than that. Pre-compiling Python surely speeds it up a bit, but still slower than compiled C.

> 
Before continuing, what is your programming experience? I'd hate to be arguing with someone with little knowledge, because it negates my knowledge.[

Thanks

---

### Post by LaRoza on 2008-10-22
> **verb3k said:**
> That's what I have been trying to tell you. The issue wasn't about terminology, rather it was about the fact that "Python is compiled to an assembly code and executed". It takes some time to compile and then execute. On some machines it's in milliseconds, on others it is way more than that. Pre-compiling Python surely speeds it up a bit, but still slower than compiled C.


It is only compiled once.

One can use C with Python quite easily.

---

### Post by david_lynch on 2008-10-22
> **techmarks said:**
> I do think the OP had a point.

If you pay attention you'll notice it too.

The apps written in Python always have a delay to start up, some worse than others, and sometimes it's extremely noticeable.I've noticed the same thing about python over the years. The python fans love it, but performance wise it's never impressed me. I know it's easier to script something in python than to write a proper c/c++ program, but graphical games written in python have always seemed a bit sluggish to me. And don't get me started on mailman. A few simple mailing lists in mailman would just hammer our mail server. I converted them all to postfix lists, and the load from the list traffic was undetectable from that point on.

Python has it's place - it can be useful as long as it's not in the fast path, not in a performance critical loop. System administration tools written in python are a good idea because it's a quick and easy way to code up a gui, and such functions are usually not at all performance intensive. 

For me, I could live without python, but if some people love it, more power to them.

---

### Post by david_lynch on 2008-10-22
> **LaRoza said:**
> That doesn't make sense.It makes perfect sense to me.

---

### Post by mentallaxative on 2008-10-25
So... exactly how much of and what in Ubuntu is written in Python?

Perhaps if you feel strongly enough about Python's lack of speed, you should submit this idea to Brainstorm and see what reaction it produces.

*hides under a rock*

---

### Post by BackwardsDown on 2008-10-25
If large parts of Ubuntu will be ported from Python to C/C++ the end result will be slower. Lots of parts of the system is being written by amateurs. Many of them are able to write clean, nice and fast algorithms in Python. But when you ask all of those programmers to write in C/C++ I bet their efficiency will drop amazingly fast and their code quality will be less stunning.

I think Python is great and should be used where it's logical to do, just as C/C++.

---

### Post by Alasdair on 2008-10-25
> **BackwardsDown said:**
> If large parts of Ubuntu will be ported from Python to C/C++ the end result will be slower. Lots of parts of the system is being written by amateurs. Many of them are able to write clean, nice and fast algorithms in Python. But when you ask all of those programmers to write in C/C++ I bet their efficiency will drop amazingly fast and their code quality will be less stunning.
This says a lot more about the quality of the C++ language than the quality of the average python programmer imho.

Personally I have have found that mature and well tested programs written in higher level languages are consistently more reliable and simpler than their C/C++ counterparts, which is certainly worth any minor trade offs in terms of execution speed.

---

### Post by bruce89 on 2008-10-25
Some places where I don't think Python should have been used:

system-config-printer (the applet especially)
update-manager (it uses huge amounts of memory for some reason)
ubuntu-system-service (it is a system tool)
deskbar (slows down GNOME start if used)

I think Python's fine for utilities that aren't used often, or testing purposes. However, system services or things that are always there (applets etc.) shouldn't be.

---

### Post by LaRoza on 2008-10-25
> **bruce89 said:**
> Some places where I don't think Python should have been used:

system-config-printer (the applet especially)
update-manager (it uses huge amounts of memory for some reason)
ubuntu-system-service (it is a system tool)
deskbar (slows down GNOME start if used)

I think Python's fine for utilities that aren't used often, or testing purposes. However, system services or things that are always there (applets etc.) shouldn't be.

Are you a programmer?

Pythn is perfect for some tasks, applets being one of them.

You'd need good reasons to say Python isn't used. You say it shouldn't be used for "system services", but not why...

---

### Post by verb3k on 2008-10-26
> **LaRoza said:**
> Are you a programmer?

Pythn is perfect for some tasks, applets being one of them.

You'd need good reasons to say Python isn't used. You say it shouldn't be used for "system services", but not why...

If the applet does something very important, and is used extensively and regularly, then writing it in Python is not a good choice. Why?
Because if a program is going to be used a lot, the programmer needs to make the the program run fast (I mean real fast). He needs to squeeze every bit of performance your machine can offer, and Python isn't the language of speed.

---

### Post by Sinkingships7 on 2008-10-26
> **LaRoza said:**
> This thread is a breeding ground for silliness.

I don't even know how to explain that.

Deluge and utorrent do two main things, wait, and download or upload. The low level features of both are written in C. (It is likely the GUI of Deluge that is mostly Python). 



[img]http://www.terminally-incoherent.com/img/facepalm.jpeg[/img]

I agree with this post.

---

### Post by Delever on 2008-10-26
What will happen if Ubuntu replaces all python code with C++?

It won't boot up.

What will happen if C++ programmers replace all python code with C++, **and keep quality up**?

It will be faster.

Yeah! I agree! Finally!

Now, who is going to rewrite? Fix bugs? Then, update?

Don't get me wrong, I would be glad if there would be enough people willing to do that.

---

### Post by LaRoza on 2008-10-26
> **verb3k said:**
> If the applet does something very important, and is used extensively and regularly, then writing it in Python is not a good choice. Why?

Bold statements.

> 
Because if a program is going to be used a lot, the programmer needs to make the the program run fast (I mean real fast). He needs to squeeze every bit of performance your machine can offer, 

No, that is absolutely false (and sexist). My most used application on the desktop is Opera. Opera is written in C++ mostly, however, most of the time, it is doing nothing or waiting for the network. Its rendering engine would needed to be snappy, and rendering engines are written in C or C++ usually, however, the browser itself could easily be written in Python.

> and Python isn't the language of speed.
Um... Yes it is. If you are going to be doing complex calculations, it may not be, but Python is quite fast, considering most of its modules are written in C.

Why is speed so critical? If an app is going to be doing constant complex calculations, yes, speed would be critical, most most apps that are open "all the time", it is usually just sitting there.

[http://en.wikipedia.org/wiki/Speed_kiddie](http://en.wikipedia.org/wiki/Speed_kiddie)

---

### Post by shadylookin on 2008-10-26
a lot of developer time would be wasted on unnecessarily rewriting things in C/C++ when it could have been used on adding new features. 

Premature optimization is the root of all evil

---

