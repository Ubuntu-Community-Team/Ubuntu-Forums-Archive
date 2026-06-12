---
title: "New to C and programming"
date: 2007-03-28
forum: Programming Talk
---

### Post by TreeFinger on 2007-03-28
I am trying to learn C computer language. I have just started and I am trying to compile a basic program. When I type into terminal

```

treefingers@treefingers-desk:~$ gcc tiny.c


```

I get an error message. 

```

/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
treefingers@treefingers-desk:~$ 

```


I do have KDevelop installed on my system, but I am not sure where to start with it.

---

### Post by lnostdal on 2007-03-28
i think you need:
```
sudo aptitude install build-essential
```

---

### Post by pmasiar on 2007-03-28
> **TreeFinger said:**
> I am trying to learn C computer language.

Maybe you have your special reason to start with C as first language. maybe not. Python is widely suggested as simpler to beginners and as first language than C, espcially for self-learners without a teacher. There is a sticky with links - how to start.

---

### Post by TreeFinger on 2007-03-28
> **lnostdal said:**
> i think you need:
```
sudo aptitude install build-essential
```


Thank you. That was the trick :guitar: 

[QUOTE=pmasiar]Maybe you have your special reason to start with C as first language. maybe not. Python is widely suggested as simpler to beginners and as first language than C, espacielly for self-learners without a teacher. There is a sticky with links - how to strart.[/QUOTE]

I was doing some tutorials on python but I already have ideas for some programs I'd like to make but I don't think I can do it with python.. plus I was going through a python tutorial and the next day when I wanted to continue it, the page went down, so that upset me a lot because it was a great tutorial.

---

### Post by pmasiar on 2007-03-28
> **TreeFinger said:**
> I already have ideas for some programs I'd like to make but I don't think I can do it with python.
just curious, what are you think is possible in C, and not possible in python (maybe with help from some little custom C library)?

---

### Post by TreeFinger on 2007-03-28
Well this may seem stupid but in all the tutorials on python I got in to there was never anything about saving your work.. I want to be able to make a program and save it for later use. Also I want to have a program that is able to save data that is entered by the user.

---

### Post by Wybiral on 2007-03-28
> **TreeFinger said:**
> Well this may seem stupid but in all the tutorials on python I got in to there was never anything about saving your work.. I want to be able to make a program and save it for later use. Also I want to have a program that is able to save data that is entered by the user.

You can save python programs, and you can save data with python.

But C is still a good language... It's up to you really.

(pmasiar is a python addict, so he's probably going to try to sway you that way)

:)

---

### Post by TreeFinger on 2007-03-28
Well I can't say I am brand new to programming.
I have dabbled with HTML for many years. I have also learned a little CSS.

A few years ago when I was a college freshman I took my first programming course in C++. I did not take it very seriously, I wish I did.
I still remember some things from that class.. very basic things so I believe I will keep trying to learn C.

---

### Post by jvc26 on 2007-03-28
If by saving for later you mean that the tutorials you were using were using the python shell, then you can save for later you can just save them as a .py script which you run with
```

python scriptname.py

```
You can also save the data from such a script in text files/dbs and the like. Anyhew, have fun with C - never got very far myself (got converted to python ;)),
Il

---

### Post by pmasiar on 2007-03-28
> **TreeFinger said:**
> Well this may seem stupid but in all the tutorials on python I got in to there was never anything about saving your work.. I want to be able to make a program and save it for later use. Also I want to have a program that is able to save data that is entered by the user.

Maybe you did not used good enough tutorials. [this one](http://hkn.eecs.berkeley.edu/~dyoo/python/idle_intro/) starts with saving your code snippet.

I am aware that there are many many Python tutorials on the 'net, some decent, some not. Thats why I maintain a wiki with good links: [http://learnpython.pbwiki.com/HowToStart](http://learnpython.pbwiki.com/HowToStart)

1) edit .py file with any editor and save it - you just saved your python program. :-)

2) save data entered by user: collect enterd info somewhere, when done, open a file and print saved data there

@Wybiral: it's not that I am Python addict - in my experience and best professional opinion Python is easier to learn for beginners. Why struggle with C++ if there is easier way? *After* beginner understands basic, and feels urge to learn other languages - I have no problems with that.

---

### Post by Wybiral on 2007-03-28
> **pmasiar said:**
> Why struggle with C++ if there is easier way?

He said C, not C++. Personally I think C is easier.

Why struggle with C? It teaches you how to manage data on your own. It's more transparent in terms of what it going on.

Do you really know how most of the python keywords and functions work internally (actually, you'd have to study the source, which was written in C)? Probably not... But with C it is very low level and transparent, allowing you to understand the code much more clearly.

I think a lot of people get stuck in HLL's and never look down at the lower level level stuff, and they have no idea what they are standing on. How are you supposed to write efficient code if you don't know what's really going on?

So yeah... I think it's worth the "struggle" to learn C. And I don't think it's that much of a struggle, especially if you aren't spoiled by HLL's to begin with.


If he wants to take the high level approach, fine... That's great. But learning a HLL will not teach you how to write efficient low level code. Might teach you some OOP, but not much further then that.

If he wants to take the low level approach, that is also fine. And what he learns there can carry on to any language afterwards because he will have an understanding of how the machine works and how code is processed. Then if he decides to learn a HLL later on, he will better understand how that languages handles his data and will write better code as a result.

---

### Post by pmasiar on 2007-03-28
> **Wybiral said:**
> Why struggle with C? ..., allowing you to understand the code much more clearly(....)I think a lot of people get stuck in HLL's and never look down at the lower level level stuff, and they have no idea what they are standing on. How are you supposed to write efficient code if you don't know what's really going on? ...learning a HLL will not teach you how to write efficient low level code....an understanding of how the machine works and how code is processed. Then if he decides to learn a HLL later on, he will better understand how that languages handles his data and will write better code as a result.

I agree with you that understanding how machine works is important.

I just disagree with order in which to learn it. I suggest first to learn basics of programming in Python (variables, arrays, loops, functions, parameters). Learn how to solve problems: design data structures, algorithms, split problems to smaller parts, join them together for solution.

With this knowledge student will be able create basic programs to solve basic problems. Yes, solutions might be less effective - but if it works, it is much better then if it does not :-)

When this knowledge is digested, and student is interested, it is possible to dig deeper: static typing, real understanding of memory management, cost of library call etc. C or even assembler. But at that stage, student has understanding *why* we need static typing and what it gives us. BTW I learned assembler first, and when learning C it was just like some supersmart macros - you can "feel" what assembly it generates. And then you forgot about worrying about low level - you have whole huge system to design and implement. :-)

Too many details too soon (C) does not make learning easier - just the opposite. IMHO, YMMV.

---

### Post by rplantz on 2007-03-28
I'll start by saying that I've only played with python a bit, so I can't really comment on learning it as the first language.

I started teaching CS (university level) in 1983. We used Pascal, which was supposed to teach students the basics along with good programming habits.

A few years later we decided to switch our beginning programming class to C, and I was the first person to teach it. It was a four (semester) unit class that included a three-hour lab. Many of our Pascal students wanted to learn C, so I also taught a two-unit class in C for those who had already learned how to program in Pascal.

I used the same book for both classes. (I think it was "C How to Program" by Deitel & Deitel.) My plan was that the beginning students would have to cover the first part of the book in detail, probably not getting all the way through the book. And I assumed that the students who had already learned Pascal could zoom through the C syntax in a couple of weeks, then move on to the more interesting material in the last parts of the book.

WRONG!! I had to completely change my plans in the two-unit C class. I think that C is very similar to Pascal, but my students did not see it that way. About the only area where they were ahead of the beginning students was that they already knew how to use an editor, compile, etc. I ended up giving the same assignments and exams in both classes.

This certainly was not a scientific study. But I've pretty much concluded that you have to learn at least 2 - 3 different languages before you begin to get a good understanding of programming. In my initial plans for the classes, I did not think about the fact that I had two decades of experience programming in several different languages, including half a dozen assembly languages. One of the challenges of teaching is recalling what it was like when I was a beginner.

---

### Post by califman831 on 2007-03-28
Pascal is better for beginners

Yes, I said it and yes am that old to remember it LOL

<takes his Geritol>

---

### Post by MathiasT on 2008-02-06
Sorry if this is a littli newbish but I am totally new to programming. I am not so very known whit ubuntu either but I want to start programming! can someone tell me what is the easiest to start with?
thanks:D

---

### Post by aks44 on 2008-02-06
> **MathiasT said:**
> Sorry if this is a littli newbish but I am totally new to programming. I am not so very known whit ubuntu either but I want to start programming! can someone tell me what is the easiest to start with?
thanks:D

Read [the]("http://ubuntuforums.org/showthread.php?t=667422") [sticky]("http://ubuntuforums.org/showthread.php?t=554070") [threads]("http://ubuntuforums.org/showthread.php?t=606009"), and [this]("http://ubuntuforums.org/showthread.php?t=688554") wannabe sticky thread. They probably have answers to most of your questions. :)

---

### Post by Wybiral on 2008-02-07
> **Wybiral said:**
> He said C, not C++. Personally I think C is easier.

Why struggle with C? It teaches you how to manage data on your own. It's more transparent in terms of what it going on.

Do you really know how most of the python keywords and functions work internally (actually, you'd have to study the source, which was written in C)? Probably not... But with C it is very low level and transparent, allowing you to understand the code much more clearly.

I think a lot of people get stuck in HLL's and never look down at the lower level level stuff, and they have no idea what they are standing on. How are you supposed to write efficient code if you don't know what's really going on?

So yeah... I think it's worth the "struggle" to learn C. And I don't think it's that much of a struggle, especially if you aren't spoiled by HLL's to begin with.


If he wants to take the high level approach, fine... That's great. But learning a HLL will not teach you how to write efficient low level code. Might teach you some OOP, but not much further then that.

If he wants to take the low level approach, that is also fine. And what he learns there can carry on to any language afterwards because he will have an understanding of how the machine works and how code is processed. Then if he decides to learn a HLL later on, he will better understand how that languages handles his data and will write better code as a result.

Hello pre-python Wybiral :) You have much to learn. Programming isn't all about pushing bits around and writing **operationally** efficient code. Those details change all the time with hardware architecture and microcode implementations of machine codes and all the levels of abstraction that you low-level addicts (such as yourself) seem to ignore. It's not like you need to understand microcode to understand machine code, or machine code to use assembly.

More important than low-level efficiency is high-level algorithmic efficiency. Your work is futile if you spend all of your time trying to shave off tiny operations here-and-there, your time is much better spent trying to improve your algorithm. Changing something from an O(n^2) to an O(n) is where you'll notice the biggest difference in terms of efficiency and your code will be much more maintainable too (because you wont have to resort to assembly or unreadable C optimizations).

Leave the low-level code to people like Linus Torvalds and all those other kernel hackers out there. The rest of us rarely have to mess with that crap. Your time is better spent learning design patterns and how to optimize your algorithms to scale effectively than learning how to shave off one or two opcodes from your program.

I'm done talking to past versions of myself now...

---

### Post by lnostdal on 2008-02-07
ok, that was hilarious, wyb .. hehe :)

but really .. when talking to newbies i often feel like i'm talking to previous versions of myself .. it's kinda weird -- because sometimes it's like i'm yelling at myself in frustration while trying to explain something (like, to myself :confused:) .. it's like getting back into a previous mindset that one might have worked very hard to get out of .. x)

---

### Post by scourge on 2008-02-07
> **pmasiar said:**
> just curious, what are you think is possible in C, and not possible in python (maybe with help from some little custom C library)?

I think it's more about what's acceptable than what's possible. In the world of software engineering there are often performance and memory requirements that Python simply cannot meet. For example I've made a not that complex application that manipulates 3D objects which are stored in .obj format. I first wrote it in Python, and it worked great with small files. But it also had to be able to handle huge, over 100MB files. So I switched to C++, using almost exactly the same object-oriented design, and as a result memory consumption was reduced to 1/7 of the Python version, and speed was 22 times better. And this is just basic desktop software we're talking about, not serious number crunching.

In my university the Basics of Programming course is in C, and people learn it just fine.

---

### Post by pmasiar on 2008-02-07
> **scourge said:**
> I think it's more about what's acceptable than what's possible. In the world of software engineering there are often performance and memory requirements that Python simply cannot meet. 

Yes, but why to go there if you are new to programming? In my professional opinion, learn to walk before running, and learn basics of programming before trying optimize your code for specific purposes. YMMV.

---

### Post by stevescripts on 2008-02-07
> **pmasiar said:**
> Yes, but why to go there if you are new to programming? In my professional opinion, learn to walk before running, and learn basics of programming before trying optimize your code for specific purposes. YMMV.

Well said!

Premature optimization should be avoided (IMHO, at least)

Steve

---

### Post by Wybiral on 2008-02-07
> **scourge said:**
> ... So I switched to C++, using almost exactly the same object-oriented design ...

That's where your problem is. If your Python code is ANYTHING like your C++ code, then you aren't taking advantage of Python. People often try to write C code in Python and wonder why it isn't as fast as C, they don't use Python correctly. There are tons of tricks to optimize Python code and most of it involves getting familiar with the standard library and learning to write Pythonic code.

I was about to write a C module for a Python program of mine the other day because it was running sluggishly. Instead, I went over my code and realized a few places where I could use generators instead of building lists and replace some of my code with standard library functionality. I ended up not needing the C module at all. Sure, this wont work for EVERY case, but I would advise trying to improve your Python code before doing a total rewrite in another language. And if the total rewrite is easy to do, then you didn't use Python properly.

---

### Post by pmasiar on 2008-02-07
> **scourge said:**
> And this is just basic desktop software we're talking about, not serious number crunching.

Not sure if in desktop development user will notice 0.2 sec difference between Python and C program. Are you aware that many desktop GUI programs in ubuntu are written in Python?

OTOH, number crunching in Python with numpy uses the same library smart C hacker would use, with almost the same speed. :-)

---

### Post by ghostdog74 on 2008-02-07
> **TreeFinger said:**
> very basic things so I believe I will keep trying to learn C.
good for you. Enjoy the learning process and don't give up halfway
also , remember, before there's Python,perl, etc, there's C.

---

### Post by slavik on 2008-02-08
> **pmasiar said:**
> just curious, what are you think is possible in C, and not possible in python (maybe with help from some little custom C library)?
wait, are you suggesting that the OP write a C library to use in his Python learning? (usually that is what 'custom' means to me).

---

### Post by pmasiar on 2008-02-08
> **slavik said:**
> wait, are you suggesting that the OP write a C library to use in his Python learning? (usually that is what 'custom' means to me).

Not so.

I suggest that everything what beginner learning programming may ever think of, is easier to done in Python. No exceptions.

And vast majority of what experienced programmer (not beginner) may ever want to do, can be done with Python with possible custom C library. It will still be simpler to write in C just small library part than whole enchilada.

I was trying to pry out of OP what s/he is afraid is not possible in Python, because it seemed to be based on uninformed prejudice and no real understanding. So far no luck.

Do you know about some exceptions, where Python will be not the simplest tool, for beginner-level learning programming?

---

### Post by Wybiral on 2008-02-08
> **ghostdog74 said:**
> good for you. Enjoy the learning process and don't give up halfway
also , remember, before there's Python,perl, etc, there's C.

Don't stop there... Before there was C there was assembly. And before there was assembly there was machine code (there was even punch-cards at some point). If the OP wants to learn C, that's fine, but I don't want them to think it's essential for their understanding of programming. Programming is more than pointers and segfaults, there's design and algorithms, things that make more sense at a higher level.

---

### Post by ghostdog74 on 2008-02-08
> **Wybiral said:**
> but I don't want them to think it's essential for their understanding of programming.

why not? its essential if they want to know about pointers and such..
> 
 Programming is more than pointers and segfaults, there's design and algorithms, things that make more sense at a higher level.
How do you define higher level? I don't really agree with the "things that make more sense at a higher level" statement. If its about design of algorithms, which is often related to writing efficient code, using a lower level language ( such as assembly) will enable the programmer to appreciate how his hardware work.

---

### Post by Wybiral on 2008-02-08
> **ghostdog74 said:**
> How do you define higher level? I don't really agree with the "things that make more sense at a higher level" statement. If its about design of algorithms, which is often related to writing efficient code, using a lower level language ( such as assembly) will enable the programmer to appreciate how his hardware work.

More abstraction. You seem to be suggesting that writing processor-efficient code means writing efficient algorithms... It doesn't always work like that. Algorithmic efficiency is almost always more important. You can futilely optimize "f" to be the most efficient function around (for that processor), or you can optimize your entire algorithm to call "f" O(log n) times instead of O(n).

Some programmers get stuck in this mindset that its more important to optimize everything and program in low-level languages so that you have more control over the machine (I used to be that way). They often don't realize that the machine has levels of abstraction for a reason. If you suggest someone learn C because it's low-level and more optimized, why not suggest assembly? Why even use the abstraction of an assembler that's going to change some of your code and build executable headers for you? It will be more efficient to do yourself, so just use raw machine code and a hex editor. In fact, machine code is silly since processors these days are almost always implemented in microcode. Then again, why use microcode when you can just design your own circuits... Now THAT'S efficient But only when you know how those transistors work will you ever REALLY understand it all. In fact, you might want to study electrons while you're at it (along with wave-particle duality and all the mathematics behind that).

Those levels of abstraction are all interesting stuff to know. But it's hardly a prerequisite for programming (and I'm not talking about people who plan to design computers or write operating systems or compilers). Those abstraction levels exist for a good reason... They make our lives easier and give us time to get out and have a life instead of designing low-level circuits all day. Another interesting thing is that the low-level programmer spends her time optimizing the low-level operations. As I stated before, it's nice for those to be efficient (when they need to be) but it's MORE efficient to optimize the algorithm at a high-level and reduce its complexity. You can do that in C... But after you write your hashing functions for your custom associative arrays and write an efficient dynamic list implementation, you could have probably learned Python, Perl, AND Ruby... Which would be a much better use of your time.

---

### Post by ghostdog74 on 2008-02-08
> **Wybiral said:**
> More abstraction. You seem to be suggesting that writing processor-efficient code means writing efficient algorithms... It doesn't always work like that. Algorithmic efficiency is almost always more important. You can futilely optimize "f" to be the most efficient function around (for that processor), or you can optimize your entire algorithm to call "f" O(log n) times instead of O(n).


no, you misunderstood me. let me quote you again
[quote=Wybiral]
Programming is more than pointers and segfaults, there's design and algorithms, things that make more sense at a higher level. 
[/quote]
How do you reckon designs and algorithms make more sense at a higher level? for example,  a programmer writes some code in Python, and due to speed problems, he had to implement some C code to help "optimize" his program. So if this programmer only sees things at a higher level, how can he write this C code in an "optimized" way that makes his program run faster? I may not be the king of explanation, hope you understand where i come from. If not, just treat my posts till now as garbage. :) since its also going OT

---

### Post by hod139 on 2008-02-08
> **ghostdog74 said:**
> 
How do you reckon designs and algorithms make more sense at a higher level? for example,  a programmer writes some code in Python, and due to speed problems, he had to implement some C code to help "optimize" his program. So if this programmer only sees things at a higher level, how can he write this C code in an "optimized" way that makes his program run faster? 

Let me try a simple example to help explain.  You are told that you have a collection of items that you will be searching over.  You can write a C program that uses an array representation and makes sure that when iterating over the array you use pointers and are as fast as possible.  Searching this array will have little language overhead, but will still require searching all the elements of the array in the worst case.

Alternatively, you could use a balanced-tree representation (e.g. std::map) to store the items.  Now searching for an item in the worst case only requires searching log (base 2) of all the elements in the list.  

There is no tree structure in C, so you the programmer will have to write it (and debug it) yourself.  Or you can use a higher level language providing this data-structure for you and have a much faster run time, even if the implementation language isn't as "efficient".  It is true that you could write this structure in C, but it will take you time and not be as debugged as the language's library version.  It also required stepping back and looking at the bigger picture and not focusing on low level optimizations.

---

### Post by pmasiar on 2008-02-08
> since its also going OT

I think refuting fears that something special (sadly, OP never told us what, and forgot about the thread) cannot possibly be done in Python is very on-topic, IMHO.

You guys can argue 'till cows come home, without OP's input we can only try WAGs.

@ghostdog74: IIUC, you assume that newbie who cannot decide (and has no clue) which part of his/her design needs be highly optimized, and how to do it, will be better off by writing whole thing in low-level language? And will be able to write efficient code, creating custom solutions matching those from libraries? And, applying your's standards you yourself, can you substantiate such claim? 

I cannot prove it, but my feeling is that such unskilled person is due to make many wrong decisions, writing highly unefficient code - and those mistakes will be well-hidden in piles of low-level code. High level language will shield newbie from all those decisions (decisions are made for her, and correctly) and will do right thing: call proper libraries, handle memory correctly etc.

I understand high-level language as optimized for developer's performance, and low-level languages as optimized for CPU performance. Maybe this is the main difference?

---

### Post by ghostdog74 on 2008-02-08
> **pmasiar said:**
> 

@ghostdog74: IIUC, you assume that newbie who cannot decide (and has no clue) which part of his/her design needs be highly optimized, and how to do it, will be better off by writing whole thing in low-level language? 

nope. I have explained my point in my previous post to Wy. Its not the best explanation to put my point across, so I digress.

---

### Post by pmasiar on 2008-02-08
> **ghostdog74 said:**
> nope. I have explained my point in my previous post to Wy. Its not the best explanation to put my point across, so I digress.

I somehow do not understand your explanation. :-(

Seems like we should agree to disagree :-) and let OP to decide which definition of "high level" makes more sense, and if s/he prefers languages optimized for performance of the CPU, or the performance of the programmer using that CPU. :-)

---

### Post by Wybiral on 2008-02-08
> **ghostdog74 said:**
> How do you reckon designs and algorithms make more sense at a higher level? for example,  a programmer writes some code in Python, and due to speed problems, he had to implement some C code to help "optimize" his program. So if this programmer only sees things at a higher level, how can he write this C code in an "optimized" way that makes his program run faster? I may not be the king of explanation, hope you understand where i come from. If not, just treat my posts till now as garbage. :) since its also going OT

Writing the C module is the last resort. I rarely find myself needing C code to speed up my Python code because Python gives me tools to solve the problem better, algorithmically (similar to what [hod139 explained]("http://ubuntuforums.org/showpost.php?p=4293385&postcount=31")).

When the NEW PROGRAMMER, who has learned algorithm design and how to actually PROGRAM (as opposed to learning how to live with a languages shortcomings) hits a problem that requires the speed of C and doesn't leave much room for algorithmic optimization, then they can learn some C (or C++) to speed things up. But only for those tiny bottlenecks in the program that require it, after it has been properly profiled and the clean (algorithmic) solutions have hit their limit.

And before you totally misunderstand what I'm saying... I'm NOT saying they should just ignore other languages because they will never need them. I'm just saying that it's more valuable to learn to deal with problems from a higher level and learn as much as they can about algorithms before they go around trying to trim off operations at a lower-level (I've been there, it doesn't help that much).

---

### Post by GSF1200S on 2008-02-08
As  a complete noob to programming, Ill add my 2 cents. I started by trying C, and while I moved along allright, I fealt overloaded by the language in general. Compiling and debugging was foreign and uncomfortable to me.

I know that C and C++ offer lower level control and that Linux uses it extensively, but that is not helping me any.

So, I grabbed IDLE and spent maybe 3 hours, and I could do FAR MORE than I could with C even having spent a day on it. The syntax is very clean. The concept of space makes the code clean to see and easy to understand flow. The commands themselves make perfect sense. It really walked my mind into what programming is, vs how its done.

Now, Im certainly not resolved to Python alone. Once I understand the jist of things, I will certainly move on to C++ and C for the lower level aspect of control should I need it. Thats another great thing about python- you can still use C and C++ modules for elements where lower-level is important, and use Python for smaller projects or even GUI's etc for big projects.

Let Python teach you to program, at which point you will easily pick up in this case C, and then youll have both working for you...

**EDIT** Its also really important to add the awesomeness that is the interpreter.. the way it informs you of where your problems are, and all without compiling a thing.

---

### Post by slavik on 2008-02-09
> **pmasiar said:**
> Not so.

I suggest that everything what beginner learning programming may ever think of, is easier to done in Python. No exceptions.

And vast majority of what experienced programmer (not beginner) may ever want to do, can be done with Python with possible custom C library. It will still be simpler to write in C just small library part than whole enchilada.

I was trying to pry out of OP what s/he is afraid is not possible in Python, because it seemed to be based on uninformed prejudice and no real understanding. So far no luck.

Do you know about some exceptions, where Python will be not the simplest tool, for beginner-level learning programming?
easy, teaching the usefulness of pointers and nice things you can do with them :)

as for someone experienced ... is there a Python module for MPI?

---

### Post by pmasiar on 2008-02-09
> **slavik said:**
> easy, teaching the usefulness of pointers and nice things you can do with them :)

I am interested to learn details. AFAIK, Python does have references, and you can do with them all useful things you can with pointers, and none of the nasty stuff. Am I mistaken? Always ready to learn some obscure trick from a Perl master! :-)

---

### Post by scourge on 2008-02-09
> **Wybiral said:**
> That's where your problem is. If your Python code is ANYTHING like your C++ code, then you aren't taking advantage of Python. People often try to write C code in Python and wonder why it isn't as fast as C, they don't use Python correctly. There are tons of tricks to optimize Python code and most of it involves getting familiar with the standard library and learning to write Pythonic code

I didn't write C code in Python. My example was object-oriented Python versus object-oriented C++. Why shouldn't the design be similar? Both C++ and Python are fully OOP languages with classes, inheritance, polymorphism, etc.


> Premature optimization should be avoided (IMHO, at least)

So coding in C++ is now called premature optimization?


> Not sure if in desktop development user will notice 0.2 sec difference between Python and C program.

No, but he will notice when loading a 100MB file takes 2 minutes of time and 3GB of RAM, as opposed to 5 seconds and 0.5GB of RAM. Maybe with some serious optimization and C libraries I could have improved the efficiency, but that would've taken more time and been more difficult that just doing it in C++.


> Are you aware that many desktop GUI programs in ubuntu are written in Python?

Yes. I write a lot of stuff in Python myself, and I like it. I just don't try to use it for every task.

---

### Post by stevescripts on 2008-02-09
> **scourge said:**
> 
So coding in C++ is now called premature optimization?


Absolutely not.  Again (IMHO) the last thing a new programmer needs to worry about is optimization.

Well documented code, using good coding practices, is far more important to learn from the beginning.

Steve

---

### Post by pmasiar on 2008-02-09
> **scourge said:**
> No, but he will notice when loading a 100MB file takes 2 minutes of time and 3GB of RAM, as opposed to 5 seconds and 0.5GB of RAM. Maybe with some serious optimization and C libraries I could have improved the efficiency, but that would've taken more time and been more difficult that just doing it in C++.

Is this pure FUD, or you have real test case, with code?

---

### Post by Lster on 2008-02-09
[QUOTE=pmasiar]Is this pure FUD, or you have real test case, with code?[/QUOTE]

[http://shootout.alioth.debian.org/gp4/benchmark.php?test=all&lang=python&lang2=gcc](http://shootout.alioth.debian.org/gp4/benchmark.php?test=all&lang=python&lang2=gcc)

That seems to imply that Python is very slow in comparison to C. That doesn't mean C is a good language to teach however (although I think it teaches some valuable things that should be learned eventually). Python is great to learn, but C is just way faster, really.

---

### Post by pmasiar on 2008-02-09
> **Lster said:**
> [url]Python is very slow in comparison to C. ... Python is great to learn, but C is just way faster, really.

I do not dispute that C is faster in raw CPU power number-crunching tasks - of course it is! C forces programmer to handle many more details which Python handles for you (for the price: but the price is not that high, AFAIK).

For numeric calculation, numpy is good library to use.

But scourge claimed he has some specific test case:

> loading a 100MB file takes 2 minutes of time and 3GB of RAM, as opposed to 5 seconds and 0.5GB of RAM.

I was curious what it was, maybe his code is doing something wrong? Storing 100MB in 3GB seems wrong.

---

### Post by Lster on 2008-02-09
I reckon that case could exist. Looking at the comparison that I posted, I myself think that that case is possible.

[QUOTE=pmasiar]C forces programmer to handle many more details which Python handles for you (for the price: but the price is not that high, AFAIK).[/QUOTE]

I'm haven't fully learned Python yet but the little I do know I must say I love what I have seen. Most specifically, it seems like the first language (at least that I've found) that I can think "this is a developer's language". Other languages feel like they are "a computer's language".

I think that is why people are, forgive me, obsessed with it. ;) Maybe that will be me later, but I can't see me giving up C.

---

### Post by pmasiar on 2008-02-09
> **Lster said:**
> I'm haven't fully learned Python yet but the little I do know I must say I love what I have seen. Most specifically, it seems like the first language (at least that I've found) that I can think "this is a developer's language". Other languages feel like they are "a computer's language".

I think that is why people are, forgive me, obsessed with it. ;) Maybe that will be me later, but I can't see me giving up C.

You are right. Python's priority is to use** code as a medium to communicate between humans**, and **code is read more often than written**. So priority is code readable by humans, even if less efficient when executing on CPU.

And sure keep your C, you can easily write your own extension libraries - this **extendability by C was one of main goals of Python**. Just with Python, you can do 100% of prototype and 95% of production code much faster than in C, and later solve bottleneck with fast C code (after profiling of course).

---

### Post by scourge on 2008-02-10
> **pmasiar said:**
> Is this pure FUD, or you have real test case, with code?

Those numbers aren't completely accurate, because I never dared to even try opening such huge files with the Python version, after seeing how much RAM it consumed even with small files. It's not FUD though. Here's the relevant code, in both C++ and Python. Perhaps you can show me how the Python version can be made as efficient as the C++ version.

C++:
```

#include <cstdio>
#include <cctype>
#include <iostream>
#include <cassert>
#include <sys/timeb.h>
using namespace std;

#define MAX_BUF 256

class Pnode
{
	public:
		Pnode(Pnode *_parent, const char *_line);
		~Pnode(void);
		Pnode * create(const char *_line);
		void print_node(int level=-1);
		bool read_file(const char *filename);
		char *line;
		Pnode *parent;
		Pnode *first;
		Pnode *last;
		Pnode *previous;
		Pnode *next;
		static int get_nnodes(void);
	protected:
		void kill_children(void);
		static int nnodes;
		static int nprinted;
};


int Pnode::nnodes = 0;
int Pnode::nprinted = 0;

Pnode::Pnode(Pnode *_parent, const char *_line)
{
	assert(_line != NULL);

	parent = _parent;
	first = NULL;
	last = NULL;
	next = NULL;

	line = new char[strlen(_line) + 1];
	strcpy(line, _line);

	if (parent != NULL) {
		previous = parent->last;
		parent->last = this;
		if (parent->first == NULL)
			parent->first = this;
		else
			previous->next = this;
	} else 
		previous = NULL;
	
	nnodes++;
}

Pnode * Pnode::create(const char *_line)
{
	return new Pnode(this, _line);
}

Pnode::~Pnode(void)
{
	if (parent != NULL) {
		if (previous == NULL)
			parent->first = next;
		else
			previous->next = next;
		if (next == NULL)
			parent->last = previous;
		else
			next->previous = previous;
	}
		
	while (first != NULL)
		delete first;

	assert(line != NULL);
	nnodes--;
	assert(parent != NULL || nnodes == 0);
	delete [] line;
}

void Pnode::kill_children(void)
{
	while (first != NULL)
		delete first;
	first = NULL;
	last = NULL;
}

void Pnode::print_node(int level)
{
	int i;
	bool at_root;
	
	assert(level >= -1);
	
	at_root = (level == -1);
	if (at_root)
		nprinted = 0;
	if (++nprinted > 32)
		return;
	
	if (!at_root) {
		for (i = 0; i < level; i++)
			printf("\t");
		printf("%s\n", line);
	}
	if (first != NULL) {
		for (i = 0; i < level + 1; i++)
			printf("\t");
		printf("{\n");
		first->print_node(level + 1);
	}
	if (next != NULL && !at_root)
		next->print_node(level);
	else if (!at_root) {
		for (i = 0; i < level; i++)
			printf("\t");
		printf("}\n");
	}
}

bool Pnode::read_file(const char *filename)
{
	FILE *fp;
	char tmp_line[MAX_BUF];
	int c;
	int i = 0;
	int level = 0;
	bool in_quotes = false;
	bool trail = true;
	Pnode *node;
	
	assert(filename != NULL);
	
	if ((fp = fopen(filename, "r")) == NULL) {
		printf("Can't open file %s\n", filename);
		return false;
	}

	node = this;
	while ((c = fgetc(fp)) != EOF) {
		switch (c) {
		case '\n': case '\r':
			if (i > 0) {
				if (!trail)
					tmp_line[i++] = '\0';
				else
					tmp_line[i - 1] = '\0';
				node->create(tmp_line);
			}
			trail = true;
			i = 0;
			break;
		case ' ': case '\t':
			c = ' ';
			if (!trail) {
				tmp_line[i++] = c;
				if (!in_quotes)
					trail = true;
			}
			break;
		case '\"':
			tmp_line[i++] = c;
			trail = false;
			in_quotes = !in_quotes;
			break;
		case '{':
			level++;
			if (node->last != NULL)
				node = node->last;
			break;
		case '}':
			level--;
			if (level < 0) {
				fclose(fp);
				kill_children();
				return false;
			}
			if (node->parent != NULL)
				node = node->parent;
			break;
		default:
			if (level <= 0 || !isprint(c)) {
				fclose(fp);
				kill_children();
				return false;
			}
			tmp_line[i++] = c;
			trail = false;
			break;
		}
		
	}
	fclose(fp);

	if (level != 0) {
		kill_children();
		return false;
	}
	return true;
}

int Pnode::get_nnodes(void)
{
	return nnodes;
}

/* Returns the time in milliseconds since Jan 01, 1970.  */
long long get_ms(void)
{
	struct timeb time_buf;
	ftime(&time_buf);

	return ((long long)time_buf.time * 1000) + time_buf.millitm;
}

int main(void)
{
	char c;
	int nnodes;
	long long timer;
	Pnode *root = new Pnode(NULL, "ROOT");
	
	timer = get_ms();
	if (!root->read_file("input.txt"))
		printf("Can't read file\n");
	else {
		timer = get_ms() - timer;
		nnodes = root->get_nnodes();
		printf("Created %d nodes in %.2f seconds\n",
		       nnodes, (double)timer / 1000.0);
		//root->print_node();
		printf("Enter something\n");
		scanf("%c", &c);
	}

	delete root;

	return 0;
}

```

Python:
```

import time

nnodes = 0
nprinted = 0

class PNode:

    def __init__(self, parent, line):
        global nnodes
        self.line = line
        self.parent = parent
        self.first = None
        self.last = None
        self.next = None
        
        if self.parent != None:
            self.previous = self.parent.last
            self.parent.last = self
            if self.parent.first == None:
                self.parent.first = self
            else:
                self.previous.next = self
        else:
            self.previous = None
        nnodes += 1

    def create(self, line):
        return PNode(self, line)

    def print_node(self, level = -1):
        global nprinted
        nprinted += 1
        if nprinted > 32:
            return
        
        if level > -1:
            print '\t' * level + self.line
        if self.first != None:
            print '\t' * (level + 1) + '{'
            self.first.print_node(level + 1)
        if self.next != None and level > -1:
            self.next.print_node(level)
        elif level > -1:
            print '\t' * level + '}'

    def read_file(self, filename):
        level = 0
        node = self
        fp = open(filename, 'rU')

        for line in fp:
            if line.isspace():
                continue
            line = line.strip()

            if line == '{':
                level += 1
                if node.last != None:
                    node = node.last
            elif line == '}':
                level -= 1
                if level < 0:
                    fp.close()
                    return False
                if node.parent != None:
                    node = node.parent
            else:
                node.create(line)
        fp.close()
        if level != 0:
            return False
        return True

root = PNode(None, 'ROOT')
now = time.time()
root.read_file('input.txt')
print 'Created ' + str(nnodes) + ' nodes in ' + str(round(time.time() - now, 2)) + ' seconds'
raw_input('Enter something')
#root.print_node()

```

The program reads text files in this format:
```

{
parent_node
	{
	first kid
	second kid
		{
		second kid's child
		}
	third kid
	}
another_parent
third_parent
}

```

At this point it doesn't matter what the text is, as long as the braces match and there's no text before the first opening brace. Obviously I can't send you my test files because they're huge, but you can easily create a big (> 10 MB) file in that format to test.

Here are the results on my PC, using a 11.2 MB test file:
Python: 700 MB of RAM, 10.22 sec
C++ 32-bit: 31.3 MB of RAM, 0.37 sec
C++ 64-bit: 56.5 MB of RAM, 0.32 sec

Based on this I would estimate that opening a 100MB file (which aren't uncommon for my app to handle) would take over 6GB of RAM, and God knows how much time, due to swapping.


Btw, I think my example shows pretty clearly both the strengths and weaknesses of Python: fewer code lines, more powerful default libraries, garbage collection, but also slower speed and bigger memory footprint. I have not yet found any language that is as suitable for handling lots of objects as C++.

---

### Post by Lster on 2008-02-10
Is those codes optimal (performance wise) for each language?

---

### Post by scourge on 2008-02-10
> **Lster said:**
> Is those codes optimal (performance wise) for each language?

I'm very happy with the C++ version, but I haven't really done anything to optimize it. I guess I write fast code naturally. Same for the Python version. In this case memory consumption is more important than the algorithms used, and I don't understand how the objects in the Python version can be so big.

For the C++ version it makes sense:
A node has the pointers previous, next, first, last, and parent. On a 64-bit system that's 8 bytes each and 40 bytes total. The average size of a node is 98 bytes, so the text data + padding + whatever takes an average of 58 bytes per node.

The Python version manages to waste more than a kilobyte per node, which is ridiculous. And as you can see, the nodes in both versions have exactly the same contents: links to previous, next, first, last, and parent node, and text data.

---

### Post by thijs on 2008-02-10
just a sec.

[PHP]apt-get install gcc g++ (gjc java)[/PHP].

---

### Post by hod139 on 2008-02-10
> **thijs said:**
> just a sec.

[php]apt-get install gcc g++ (gjc java)[/php].
I really don't understand your post.  What are you trying to contribute?

If you want to install gcc and g++ use
```

sudo apt-get install build-essential

```Don't do what you posted.

---

### Post by popch on 2008-02-10
> **scourge said:**
> I'm very happy with the C++ version, but I haven't really done anything to optimize it. I guess I write fast code naturally. Same for the Python version. In this case memory consumption is more important than the algorithms used, and I don't understand how the objects in the Python version can be so big.

For the C++ version it makes sense:
A node has the pointers previous, next, first, last, and parent. On a 64-bit system that's 8 bytes each and 40 bytes total. The average size of a node is 98 bytes, so the text data + padding + whatever takes an average of 58 bytes per node.

The Python version manages to waste more than a kilobyte per node, which is ridiculous. And as you can see, the nodes in both versions have exactly the same contents: links to previous, next, first, last, and parent node, and text data.

You have not really provided sufficient data for an in depth analysis of what is going on in your program. However, a few things come to my mind which you might not have thought of. Please bear in mind that I am proficient neither in C nor in Python. I have used other programming languages, both OO and otherwise, and therefore believe that I can contribute anyway.

Memory usage:

You give no indication of having closely looked at where the 700MB of RAM have gone which the Python program has consumed. How much RAM does the program occupy when there is a very small number of nodes to process? Your program does not appear to initiate any garbage collection before counting the amount of RAM occupied. Hence, it is quite possible that the Python environment simply filled available RAM because there was no other process which demanded RAM.

You should expect the Python version of your program to produce garbage of at least roughly the size of your data file because you trim each line after reading. Strings are immutable in Python, and therefore each call to trim() will put the untrimmed string into the garbage pool.

Also, you have to expect that in Python an object occupies a bit more RAM than does a similar object in C-like languages. Being dynamically typed and having automatic memory management, Python must add a bit of overhead to each single object. Things added to each object are at least a pointer to its class and presumably some accounting information for the garbage collector. 

Processor time:

Besides the obvious overhead of languages which are either interpreted or compiled on execution, you should bear a few facts in mind. It is quite impossible that for the problem and the algrithm you gave us the python program will ever run as fast as the C one.

Firstly, Python is dynamically typed. That means that upon execution each time a variable is being used for something, it has to be tested for its type. Your C program does not do any type testing at all.

Further, you directly access variables of one instance from within code of another instance. This should about double the number of type verifications needed. Put this in contrast with the simple address arithmetic done in your C program, and you see where part of the difference in speed comes from.

Then there's object creation which presumably runs slower in Python. Add the time neded for garbage collection which occurs in Python and not in your C program, you can see quite a few reasons why the Python variant is much slower than the C variant.

I agree that the difference in speed appears to be a bit drastic in the case of your example. Without more detailled knowledge about Python and your test data it's a bit difficult to be more specific. I trust that you will see the reason for part of the difference nonetheless.

---

### Post by scourge on 2008-02-10
> How much RAM does the program occupy when there is a very small number of nodes to process?

I tried with a 750KB file, and it took 48 MB of RAM, which is pretty much the same efficiency that I got with the bigger file.

> Your program does not appear to initiate any garbage collection before counting the amount of RAM occupied. Hence, it is quite possible that the Python environment simply filled available RAM because there was no other process which demanded RAM.

This makes a lot of sense, and indeed I have 2 GB of RAM, which was enough for opening the 11.2 MB file. So I tried a 22.2 MB file to see what would happen: the program ate all the RAM I had left (about 1.3 GB), and instead of collecting the garbage it filled my Swap partition as well. And when programs need Swap, I have a problem.

> I agree that the difference in speed appears to be a bit drastic in the case of your example. Without more detailled knowledge about Python and your test data it's a bit difficult to be more specific. I trust that you will see the reason for part of the difference nonetheless.

Your post was very enlightening for sure, and it made me understand Python better. It probably won't help me optimize my program, but then again my interest was purely academic anyway, since I had already found C++ to be perfect for this particular job.

---

### Post by Wybiral on 2008-02-10
I agree with you that file parsing is an example of a problem that is hard to improve algorithmically. There's not much room for reduction when you have to go over the entire file. I'm not sure what you're getting to though... Nobody is debating whether C++ performs better than Python or not. In fact, I can write a more efficient version of your parser in C, and an even more efficient one in assembly. This comparing X language to Y for efficiency stuff doesn't prove or disprove anything when it comes to practicality.

If I knew that I needed to parse files that are several hundred megabytes long in a really short amount of time, then I might not write my parser in Python. Of course, that doesn't mean I can't write the rest of my program (the bulk of my program) in Python, just the file parser (I would use either C or C++, and SWIG to create a Python module, maybe even PyRex to write the entire module). However, if I knew that my files would be small (such as your example file) then I would go ahead and do it in Python. The 0.1 second difference isn't going to matter.

If this is somehow related to the conversation about new programmers, I don't exactly see how it applies. When someone is learning to program they aren't going to need to parse several hundreds of megabytes of a special file format.

---

### Post by popch on 2008-02-11
> **Wybiral said:**
> 
If this is somehow related to the conversation about new programmers, I don't exactly see how it applies. When someone is learning to program they aren't going to need to parse several hundreds of megabytes of a special file format.

As I already mentioned in another thread, I firmly believe that higher level languages exhibit as one particular problem that their behaviour is not immediately obvious to programmers, especially ones new to a language. The case just discussed illustrates that quite nicely.

I have taken the stance that in order to produce good programs in a high level language you have to understand the code produced by that language in lower level terms as well. I then suggested that it might be a good idea to start learning how to program with a simple lower-level language. I used Pascal as an example.

---

### Post by scourge on 2008-02-11
> **Wybiral said:**
> I'm not sure what you're getting to though... Nobody is debating whether C++ performs better than Python or not.

Well, I was asked to post my case and some code, so I did.

> If I knew that I needed to parse files that are several hundred megabytes long in a really short amount of time, then I might not write my parser in Python.

Speed isn't actually the biggest issue here. Memory use is what made Python a totally unacceptable choice.

> Of course, that doesn't mean I can't write the rest of my program (the bulk of my program) in Python, just the file parser (I would use either C or C++, and SWIG to create a Python module, maybe even PyRex to write the entire module).

To me it's just easier to write the whole thing in C++. And writing a faster parser isn't going to help if I still need to use the same data structure that I'm using. The whole PNode class would have to be in C++ to keep memory use down.

> If this is somehow related to the conversation about new programmers, I don't exactly see how it applies. When someone is learning to program they aren't going to need to parse several hundreds of megabytes of a special file format.

This discussion drifted all over the place a long time ago. And I don't see how knowing a programming language's limitations can be bad for a new programmer.

---

### Post by pmasiar on 2008-02-11
> **scourge said:**
> Based on this I would estimate that opening a 100MB file (which aren't uncommon for my app to handle) would take over 6GB of RAM, and God knows how much time, due to swapping.

I didn't need to create that many objects, so I don't personally know how to improve that code. My first guess would be using tuples instead of objects (which are hash-based). But tuples are immutable.

If you are interested, you may post this question at python mailing list, best experts will look at it and may suggest ways to speed it up and decrease memory usage if at all possible.

If you decide to do it, please let us know if it is possible to improve memory usage, and how.

---

### Post by pmasiar on 2008-02-11
> **popch said:**
> I have taken the stance that in order to produce good programs in a high level language you have to understand the code produced by that language in lower level terms as well. I then suggested that it might be a good idea to start learning how to program with a simple lower-level language. I used Pascal as an example.

You are mixing apples and oranges again. :-)

**When you start learning programming, ** you don't care about efficient code, so high-level language like Python is the best.

Later, **when (and IF) you want to write efficient code** ("good programs" - how you define "good"?), of course learning some low-level language is expected. I would not suggest wasting time with nice but obsolete language like Pascal. If you are already half-competent programmer in Python, learning C would not be that hard, or that  harder compared to Pascal. And C you can use directly from Python to gain efficiency.

But many professionals don't care about efficiency at all - computer is idling on their table anyway, getting data processed **without wasting time to explain career programmer** what is in the data is the **most efficient use of their personal time** - even if not CPU cycles. :-)

---

### Post by ruy_lopez on 2008-02-11
> **pmasiar said:**
> 
**When you start learning programming, ** you don't care about efficient code, so high-level language like Python is the best.

What if you are learning to code because you want to manipulate low level interfaces? Say you want to write a device driver, or you have built a data acquisition card with a USB interface.

The idea that everyone should learn programming the same way is ridiculous. People are aiming to achieve different ends with their programs.

---

### Post by pmasiar on 2008-02-11
> **ruy_lopez said:**
> What if you are learning to code because you want to manipulate low level interfaces? Say you want to write a device driver, or you have built a data acquisition card with a USB interface.

The idea that everyone should learn programming the same way is ridiculous. People are aiming to achieve different ends with their programs.

Yes, I admit that 0.1% of people who wants hack on bits and nothing else might skip high-level programming. But IMHO it will make them **worse programmers** in general if they never learn also high-level (and more productive) language - and experiments with students shows, will take them longer to learn how to program.

Of course not all people will learn programming in the same way. If you want to hack on bytes, and you have someone to guide you, dive in, and enjoy the pain. But for 99% of the people who try to learn by themselves, or in school, but without close contact to expert, learning high level language like Python is better, faster, less painful way to learn programming.

---

### Post by Lster on 2008-02-11
[QUOTE=pmasiar]Yes, I admit that 0.1% of people who wants hack on bits and nothing else might skip high-level programming. But IMHO it will make them **worse programmers** in general if they never learn also high-level (and more productive) language - and experiments with students shows, will take them longer to learn how to program.[/QUOTE]

Can you justify why they would be "worse programmers"? I think Python is a good first language for many, but I think C is also. I think it works more the other way, "worse programmers" generally don't know low level languages (that is not to say that one is a worse programmer for not knowing a low level language).

---

### Post by pmasiar on 2008-02-11
> **Lster said:**
> Can you justify why they would be "worse programmers"? 

I said:
> it will make them worse programmers in general if they never learn also high-level (and more productive) language

In short, programmer who knows "only C and nothing more" is worse programmer who knows "C and Python".

> good first language for many, but I think C is also

I am not sure how many times I need to repeat that strict typing of C and need to manage memory is confusing to beginners and completely distracting from task of learning of basics of programming. Funny that every time someone else comes around and repeats the same arguments, and then someone else is offended that I disagree with that with the same arguments all the time. But for same argument, same response?

Or do you think that learning 3 things (programming+types+memory management) is simpler than just learning programming? I said  many times that **after** learning basics of programming I recommend to anyone who cares about how CPU does it, and cares about effective CPU usage, to learn also C, my preferred low-level language. 

But you are forgetting that many people who program do not care about CPU time - they care about own time. Of course, if you are just a student of CompSci with no real-life experience, you did not met yet  many professionals (scientists and all) who  use little programming to help solving big problems they have. Last thing they worry about is effective use of CPU. If they need something effective, they hire C hacker, but most of the time they don't have need, time and budget to do that.

> I think it works more the other way, "worse programmers" generally don't know low level languages (that is not to say that one is a worse programmer for not knowing a low level language).

Not all people who use programming to solve own problems are career programmers. In fact, most people are not. For them, learning C or other low-level language is waste of time.

And let me tell you that those professionals are able to solve problems which "career programmers" are not able to solve, or will take them inordinate amount of time, because career programmers don't have specialized knowledge of those professionals. Are they "worse" programmers? Why should they waste time by optimizing code for CPU? Why not use CPU time to optimize their own time?

And if these professionals need to learn low-level languages, they are able to learn that too, with no problems, as I've seen multiple times. CompSci education is highly overrated, IMHO. Most of smart professionals are able to become quite competent programmers, if they need to. It is much harder for a CompSci student to learn enough science or any other problem area to be capable of solving interesting problems (and not only solve whatever s/he is told to solve).

BTW I am career programmer with CompSci education, working for biologists, medical researchers etc, so I know it firsthand.

---

### Post by Lster on 2008-02-11
[QUOTE=pmasiar]I am not sure how many times I need to repeat that strict typing of C and need to manage memory is confusing to beginners and completely distracting from task of learning of basics of programming. Funny that every time someone else comes around and repeats the same arguments, and then someone else is offended that I disagree with that with the same arguments all the time. But for same argument, same response?[/QUOTE]

Well, after just a short time C became clear to me. Before that I had learned Java, BASIC and JavaScript, but once I learned C everything kind of clicked. I think for someone like me, C would have been the best first language. Others Python might be, but I doubt Python is the best for "99%" (even if it's still the majority).

It's also not about performance, although I think that it is an important topic. As for fast development, I find development in C to be quick and I don't know Python well enough to compare them. I'm *guessing* Python is quicker.

[QUOTE=pmasiar]In short, programmer who knows "only C and nothing more" is worse programmer who knows "C and Python".[/QUOTE]
Can you justify why this would be?

---

### Post by CptPicard on 2008-02-11
> **Lster said:**
> Can you justify why they would be "worse programmers"? 

Programming is always more about expressing computational concepts and solutions in abstract terms than knowing how to push some certain bits around in the context of some given hardware/platform/API... IMO it's the difference between someone who knows how to make the computer do anything and a code monkey.. :)

---

### Post by pmasiar on 2008-02-11
> **Lster said:**
> I don't know Python well enough to compare them. I'm *guessing* Python is quicker.

If you started with this one, all your comments would be understood as they are: as making judgments about a language you do not know enough to make competent judgment. Try Python first. Write couple programs in it. Then, you will be able to justify for yourself what you as me to do for you now.

Let me remind you that I do know C well enough to compare it with Python, even if I haven't used C for 15 years or so.

---

### Post by Lster on 2008-02-11
I still don't see how not learning a high level language makes you a worse programmer. Am I missing the point? :)

---

### Post by CptPicard on 2008-02-11
Learn Lisp and write a few parsers and AI programs. Then, we will talk. :)

---

### Post by Lster on 2008-02-11
Are AI programs in C close enough? :) And what type?

---

### Post by CptPicard on 2008-02-11
The whole point is that my favourite intellectual activity related to "coding" is reading textbooks/articles, staring at the wall, doodling by pencil and paper, and then, maybe, taking some expressive high-level language and putting my thoughts into actual code.

It's all in the abstractions you express, not how you do it, and low-level languages force you to spend way too much time and effort actually pushing the bits. It does not advance the level of your thinking, your understanding of your problem or how you create an algorithm to solve it.

I know that when one is younger there is a certain coolness factor to low-level coding such as C, but the more you get to know computing, the more you appreciate the beauty to be found on the very high level...

[http://www.gnu.org/fun/jokes/eternal-flame.html](http://www.gnu.org/fun/jokes/eternal-flame.html)

(Do I sound old or what... :mad: )

---

### Post by pmasiar on 2008-02-11
> **Lster said:**
> I still don't see how not learning a high level language makes you a worse programmer. Am I missing the point? :)

When your mind is not occupied by juggling low-level problems, you can really start think about the task you are trying to solve.

It is well known fact that human mind can best handle 7+-2 items at a time. The more slots you occupy by low-level details, the less is left for real task. People can in general remember about 2 pages of code in detail. The more you can accomplish in those two pages of code, the more productive are you.

Exactly like when you program, you don't put all your code into one chunk, but create functions. High-level language have more abstractions like that. As you learn more languages, you realize that programming is not only about pushing bits around.

This discussion is really funny, I remember old discussion when some people argued against using "high-level languages" like PL/1, Algol and C, they preferred to do everything in assembler, to really understand what is happening. When I was learning programming, it was of course joke. But in 60ties, "Assembly-only" programmers did not understand why learning Algol, Fortran, PL/1 (C was not invented yet) will make them better programmers - because those languages are translated to asm anyway, so what is the difference? I wonder when the time comes for Python and friends to step aside for even higher-level languages? :-)

[Beating the averages](http://www.paulgraham.com/avg.html) is famous article describing why programmers have hard time comparing languages with features they did not learned to use yet.

---

### Post by Lster on 2008-02-11
I had a look at Lisp. Urghhh! Are all those brackets necessary? ;)

I do love the abstraction of Python and its elegance but will maintain there are some people (including me) who lower level languages suit better. As I have said before, Python really is such a nice language but I wouldn't say you are worse for programming in other languages.

I would personally love a CPU that can decode a specific language such as Python. I think that would really rock!

Anyway, I thank you pmasiar and CptPicard; this has been very interesting. You guys are a better education than my computer science class. :)

---

### Post by stevescripts on 2008-02-11
pmasiar - again thanks for the link. ;)

A link I often refer folks to is: [http://www.tcl.tk/doc/scripting.html](http://www.tcl.tk/doc/scripting.html)

Worth a read if you've never seen it!

Steve

(Yes, I use Tcl/Tk to do what most folks around here seem to do with Python)

---

### Post by pmasiar on 2008-02-11
> **Lster said:**
> I would personally love a CPU that can decode a specific language such as Python.

If you want high-level language hardwired in metal, you might be interested in [Forth](http://en.wikipedia.org/wiki/Forth_%28programming_language%29). It is high-level language, in which is very convenient to develop domain-specific languages (higher-level that traditional high-level general programing languages). Yet Forth allows you to manipulate stack and memory directly, if you want to, and you can freely mix defining new "functions" in either Forth, DSL, or ASM. Unlike other non-compiled HLL, Forth is very compact and very fast. And it was implemented in metal many times, and long time ago.

Be careful: your brains might boil when trying to learn Forth: everything is different (for a good reason) and unlike other languages, don't say I did not warned you. but if you are not afraid of being responsible for pushing bits around, you might like Forth. I know I did! Enjoy!

---

### Post by LaRoza on 2008-02-11
> **Lster said:**
> I had a look at Lisp. Urghhh! Are all those brackets necessary? ;)


Parentheses, and yes.

Lisp is very logical, and its not familiar syntax gets familiar quickly.

---

### Post by Wybiral on 2008-02-11
> **Lster said:**
> I had a look at Lisp. Urghhh! Are all those brackets necessary? ;)

That's what I first said too. And with Python I though "significant whitespace... WHAT?". Now I look at C and think "I have to put a semicolon after every statement and enclose every block with a bracket???" :) lisp has some elegant solutions to problems, and the code usually ends up very small, and readable (provided you know lisp).

> **Lster said:**
> I do love the abstraction of Python and its elegance but will maintain there are some people (including me) who lower level languages suit better. As I have said before, Python really is such a nice language but I wouldn't say you are worse for programming in other languages.

I don't think they make you WORSE, but 80% of the low-level programmers I've talked to (including myself about a year or so ago) get stuck in the [blub]("http://en.wikipedia.org/wiki/Blub_(programming)") mindset. I never understood why languages like Python and Lisp were so powerful until I actually used them (and I mean, REALLY used them). I used to debate with pmasiar and lnostdal on this subject all the time. The only things assembly and C taught me were how to write for a specific platform and how to work around the missing features of low-level languages. You can learn about abstract problems in low-level languages, but you have to do so while battling pointers / memory management / strict types.

Not that C isn't a valuable skill to have... I just think it's more valuable to know how to program and think about problems abstractly than to learn how to live with a languages shortcomings (having to solve problems that don't exist, just because the language enforces them on you).

---

### Post by CptPicard on 2008-02-12
> **Lster said:**
> I had a look at Lisp. Urghhh! Are all those brackets necessary? ;)

Yes, they are. If you look at Lisp even more you will actually find that Lisp's syntax is based on a single nested structure -- the S-expression -- that is essentially, as a Lisp data structure, a list. So Lisp code itself is nothing but nested Lisp lists, which just a lot of the time happen to have a function symbol at the head of the list, which is then applied to the rest of the list! So that's why Lisp looks the way it does.

A Lisp (actually, Scheme) interpreter, as described in *Abelson, Sussman: SICP*, is fundamentally just two procedures, *apply* and *eval*, first of which rewrites parameters to the function call and the latter then "runs" it (IIRC).

Incidentally, Lisp's awesomeness and multitude of delimiters has as a corollary the fact that Python's significant whitespace must be a bad thing.. ;)

> I do love the abstraction of Python and its elegance but will maintain there are some people (including me) who lower level languages suit better.

Probably not true. C suits you better because, uh, you're still quite a beginner and know C "well enough" in order to be comfortable. Intellectual inertia takes over from there. ;) Which is natural. As Wybiral said above, it's hard to discuss this topic without actually using higher-level languages... because there are some things you wouldn't even expect you could do, and that blow your mind while you meet them for the first time -- all the abstractions you can build with closures for example. Continuations are wild... and to imagine that Scheme actually can do *all* with such a minimal syntax, no need even for CL's syntactic sugar...

> I would personally love a CPU that can decode a specific language such as Python. I think that would really rock!

It's unneccessary. Just let those for whom low-level languages suit better code the interpreter, and focus on solving interesting problems using your high-level language. ;)

---

### Post by pmasiar on 2008-02-12
> **CptPicard said:**
> Incidentally, Lisp's awesomeness and multitude of delimiters has as a corollary the fact that Python's significant whitespace must be a bad thing.. ;)

I know it is a joke, but you have logical fallacy in it: **You assume that not being able to distinguish between program and data is a good thing**. Of course, from a false assumption you are able to prove the false statement as you did - awesomeness of Lisp. :-)

Of course all this are just jokes. I am fully aware that CptPicard knows that Python has eval and lambda statement and there is little possible in Lisp not possible in Python (with more readable code of course, even if you do evil tricks). Syntactic sugar, if used sparringly, improves taste without ruining the food :-D

For curious reader, there is yet another language where code looks like data: [XSLT](http://en.wikipedia.org/wiki/Xslt) and it is **much harder to read** than Lisp: it has all the additional ugliness of XML.

---

### Post by CptPicard on 2008-02-12
> **pmasiar said:**
> I am fully aware that CptPicard knows that Python has eval and lambda statement


Python has lambda *just barely* really... I get the feeling that Guido threw it in as a kind of act of mercy while holding his nose...

---

### Post by pmasiar on 2008-02-12
> **stevescripts said:**
> A link I often refer folks to is: [http://www.tcl.tk/doc/scripting.html](http://www.tcl.tk/doc/scripting.html)

Worth a read if you've never seen it!


Excellent link, thanks. Compares system programming languages and scripting languages (third group will be application programming languages) and how they relate to each other. Interesting statistics about productivity.

Even if article is 10 years old, when Python was still under the radar, comments about scripting languages are still valid. Thanks again!

One thing what was not obvious back then is difference between typing and binding: C is strongly statically typed early binding language. Perl is weakly dynamically typed late binding language. Python is strongly, but dynamically typed late binding language. BTW exact different is mentioned in footnotes, it is just then-common terminology.

---

### Post by Lster on 2008-02-12
[QUOTE=CptPicard]Probably not true. C suits you better because, uh, you're still quite a beginner and know C "well enough" in order to be comfortable. Intellectual inertia takes over from there. Which is natural. As Wybiral said above, it's hard to discuss this topic without actually using higher-level languages... because there are some things you wouldn't even expect you could do, and that blow your mind while you meet them for the first time -- all the abstractions you can build with closures for example. Continuations are wild... and to imagine that Scheme actually can do all with such a minimal syntax, no need even for CL's syntactic sugar...[/QUOTE]

Well I know many people on sites like OSDev and such that prefer C/ Assembly for even problems that high level languages address. These programmers are far from beginners. If you meant C would not suit *anyone* best I must disagree!

And I really do know C very well, actually. I've programmed most of the standard library from scratch for my OS whcih really does give me a good knowledge of everything. :)

---

### Post by pmasiar on 2008-02-12
> **Lster said:**
> These programmers are far from beginners. 

Having experience does not prevent one from becoming blub programmer. Read Tcl/Tk link above to see the difference.

Edit: in fact, having experience in single language only, and not willing to learn other languages, by definition makes programmer a blub programmer. :-)

---

### Post by CptPicard on 2008-02-12
> **Lster said:**
> 
And I really do know C very well, actually. I've programmed most of the standard library from scratch for my OS whcih really does give me a good knowledge of everything. :)

Okay, hat's off to you then. Sorry if it came off as condescending. :)

Now... you know that writing a Scheme interpreter is not all that difficult, because of the really strong generality of the language and powerful fundamental concepts? Why not build a Scheme shell for your OS and run everything else off that? It would be like Emacs, only better :-k

There were even Lisp machines a long time ago that actually ran Lisp on hardware...

---

### Post by Lster on 2008-02-12
[QUOTE=CptPicard]Okay, hat's off to you then. Sorry if it came off as condescending.

Now... you know that writing a Scheme interpreter is not all that difficult, because of the really strong generality of the language and powerful fundamental concepts? Why not build a Scheme shell for your OS and run everything else off that? It would be like Emacs, only better

There were even Lisp machines a long time ago that actually ran Lisp on hardware...[/QUOTE]

I wouldn't deny I'm a beginner, but my maths really helps me understand programming logic. :)

Well I haven't been programming my OS for a while. I really want to develop a 64 bit OS now which could then incorporate a little programming language (my 32 bit OS only had a little CLI with a few basic applications like a file reader and calculator etc...). Maybe Scheme. :)

---

### Post by CptPicard on 2008-02-12
Scheme really IS a "little" programming language as far as amount of primitives go, and Lisps in general are great at building abstractions on top of other abstractions, so it's would offer lots of opportunity for extension points on top of a really small "kernel" for running the base language. Read SICP :)

---

