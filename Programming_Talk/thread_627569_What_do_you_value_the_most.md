---
title: "What do you value the most?"
date: 2007-11-30
forum: Programming Talk
---

### Post by Wybiral on 2007-11-30
As we all know, every project you work on is likely to have a different set of goals. Often times your programming strategy (and sometimes your language set) must change to better meet your goal. Sometimes it even comes down to a trade-off of a few measures where you have to pick the measure you need the most. My question to all of you is which of the following measure do you typically find your project to require the most of:

[LIST=1]
[*]Security
[*]Runtime speed
[*]Memory efficiency
[*]Readability / Manageability
[*]Development speed
[/LIST]

I'm also curious why, and what kind of projects you are working on that merit the particular functionality that you often require? Not factoring in the functionality requirements of the libraries you need to use, just the code that you actually spend time developing.

---

### Post by pmasiar on 2007-11-30
Which you value more: your left eye, right eye, any of your hands, or head? :-)

I tend to prefer **both** 4 and 5, assuming that 1, 2, 3 are withing limits of "tolerable".

Programming is engineering discipline, whole point is balancing contradictory requirements to accomplish the goal. For each project, balance might be different.

---

### Post by tyoc on 2007-11-30
I value more a good design and the time spend on it, also openess to change the code for a best design (if it requires factoring or a whole reengeenering).

Also this days I love that there will be a nice way to integrate things in my code, where I work now there is a way that I dont like, where I need to modify some part of the code Im merging (a bad design for integration in my POV, because I need to spend some time instead of copy&paste the new code or do some includes, hope to change that in near future after I terminate my first project here, and hope to change whole POV of the design process and work).

From the list I value 5, 4, 2 == 3 and 1. Thought what you mean by "security"? encription, protection of data??, security in term that it will work OK?? (hehe).

---

### Post by Vadi on 2007-11-30
Security. Just reading about the storm botnet gave me the chills 'till I read it's for Windows only (seriously. When AV companies are admitting they cannot stop something that's been out for a year, you aren't going to be happy).

---

### Post by Wybiral on 2007-11-30
> **pmasiar said:**
> Which you value more: your left eye, right eye, any of your hands, or head? :-)

I tend to prefer **both** 4 and 5, assuming that 1, 2, 3 are withing limits of "tolerable".

Programming is engineering discipline, whole point is balancing contradictory requirements to accomplish the goal. For each project, balance might be different.

Exactly. All of them are important at some point, this is more of a question of what types of projects you work on that justify your concern for a particular measure. For me it's manageability because I'm getting much more into web development (where the code you write will almost definitely need to be read again). Second would definitely be development speed (because it's a fast paced industry we're in).

But when I used to write 3d games and optimized libraries, I cared more about runtime efficiency than development time. I'm mostly curious what kind of projects everyone is working on, and why you value the measures that you do. Vote for the most important one that you find you care about the most.

---

### Post by xtacocorex on 2007-11-30
I don't think that any of the 5 fit my development style Wybiral.  Mainly I just want to get something working because my programs usually are meant to solve a single problem.  Guess that's what I get for not writing programs similar to everyone else.

---

### Post by CptPicard on 2007-11-30
They're all important, some things more important than others depending on your project. When it comes down to actually doing business though, I tend to believe that development time is the crucial factor, hopefully without sacrificing the other ones.

For me, raw speed tends to be of most concern as my main "product" is a number-crunching library that is used by just one guy and is developed by just me, in tight collaboration with him so that I know his needs 100%. I should probably invest more into readability though, the other day I went to modify my core algorithm after having not touched it much for a year or so... took the whole day to figure out what the unholy mess is doing, and how to modify it safely so that I don't introduce subtle breakage that catches me by surprise...

---

### Post by Lster on 2007-11-30
I think security (and accuracy) are paramount. I program by the philosophy that software is only as good as it's worst case.

So my list goes:

Security, runtime speed, memory efficiency, readability/ manageability and least development speed.

---

### Post by aks44 on 2007-11-30
I'm pretty surprised you didn't even mention correctness... ;)

As far as I'm concerned, correctness, stability and security are the bare minimum (so I voted security). Next comes scalability and code maintainability, then only runtime speed (if the customer complains).

Memory efficiency? Buy more RAM. :p
Development speed? I'll see what I can do, but don't expect miracles... :-\"


Doing back-office stuff here (dedicated WinNT-based servers).

---

### Post by Wybiral on 2007-11-30
> **aks44 said:**
>  ... 

I would hope correctness / stability are always in mind when writing any programs, but I guess you never know... Damn, I should have put scalability on there. Ironically this poll doesn't scale very well with new options :)

---

### Post by CptPicard on 2007-11-30
Buying more RAM is great advice. Memory efficiency is such a non-issue today, although of course being outright wasteful is another matter (Firefox caching, I'm thinking of you)...

In my number-crunchers, I trade space for time whenever I can. Actually, my most intense algorithm is very, very much data driven in the sense that it pushes anything it can into RAM for later reuse. I tend to do this up to the point when actual memory access time starts to become a bottleneck... then it's time to reconsider the implementation strategy.

---

### Post by aks44 on 2007-11-30
> **Wybiral said:**
> I would hope correctness / stability are always in mind when writing any programs, but I guess you never know...
Unfortunately this is not always the case.
I remember that guy who declared a **wchar_t fileName[100];** to hold a file name... on NT (where a file name can be up to 256 characters IIRC not sure though since nowadays I always use dynamic allocation so I don't have to bother with that). Plus it was prone to buffer overflow (he didn't check the length before copying the string). His argument when I pointed this out was like "*oh well noone sane will ever use such a long file name anyway, why bother now that it's done?*". Lucky him, I was in a good mood that day, he's still alive... :-\"


> **CptPicard said:**
> Buying more RAM is great advice. Memory efficiency is such a non-issue today, although of course being outright wasteful is another matter (Firefox caching, I'm thinking of you)...
Well, on dedicated enterprise servers you can easily argue to the customer that he must buy some more RAM. Now when it comes to desktop applications, I guess that requiring at least 2GB of RAM is not the way to go. :p

---

### Post by samjh on 2007-12-01
In general, I put 4 as the top priority: readability and manageability.

The reason is simple: code that is easy to read and manage are usually easier to optimise, easier to secure, and faster to develop, than code that is difficult to read and manage. :)

But as with all things, "it depends". ;)

Hmmm... forgot to answer the other part of the question...

My past projects have mostly been firmware and low-level application software, involving signal interpretation and encoding/decoding.  Memory and processor efficiency were obviously important, but I found that optimisation was a lot easier if the code itself could be [relatively] easily understood.  I tend to write code in the most readable and "correct" manner, and then optimise them by modifying incrementally, amending comments after each modification.

---

### Post by de_valentin on 2007-12-01
Hard to say all of them are actuallymy  reasons for not going back to windows, that and the fact that it's not free and becoming more and more like spyware.

---

### Post by jespdj on 2007-12-04
Your poll is not very meaningfull...

When you are participating in commercial software development projects, like I am in my day job, then there's always a triangle of three things that you have to keep in mind: time, money and quality. You'll have to know where the balance between these three has to be for that particular project.

For some clients, a fast time to market is very important, so for them the factor time is more important than money or quality. For other clients, quality is very important and time or money are less important. And for some, money might be the most important factor above time and quality.

So what you spend most of your attention to depends on the requirements and situation of the client. There's not a single aspect that is most important in all projects.

The same thing can be said for your poll options. Security is probably very important for web stores that deal with people's money, credit card numbers and personal information, but it is totally irrelevant for simple desktop applications that don't connect to Internet. Likewise, runtime speed, memory efficiency, readability and development speed each have different levels of importance depending on what software you are writing and for whom.

---

### Post by Auria on 2007-12-04
I value getting the work done :)

This question is rather limited, if I make a FPS I will value performance, if I make a small comand-line utility i won't mind performance and will much more care about ease of use

---

### Post by Wybiral on 2007-12-04
> **Auria said:**
> I value getting the work done :)

This question is rather limited, if I make a FPS I will value performance, if I make a small comand-line utility i won't mind performance and will much more care about ease of use

Pay careful attention to the paragraph at the bottom of the first post. I'm curious which projects require what and who is working on them.

---

