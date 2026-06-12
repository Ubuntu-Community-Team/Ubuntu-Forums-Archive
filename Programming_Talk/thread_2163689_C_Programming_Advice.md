---
title: "C Programming Advice"
date: 2013-07-19
forum: Programming Talk
---

### Post by drmrgd on 2013-07-19
Out of boredom and for fun, I would like to starting working with some low level programming.  The question is, which is a better path: C or C++?  I know the root of the answer always lies in 'what do you plan to do with the language', but not being a programmer for a living (I'm a biologist), it's a bit hard to answer.  For the majority of what I do, Perl and / or Python is more than sufficient, and my comfort level with those languages (more so Perl than Python) is high enough that I can usually cobble together a script to do whatever I need.  At this point, though, I'd like to start working with a low level language to do some more complex tasks and to handle the hardware a little more intimately as much of the data I process is very large (it's not uncommon to have to process files that are several GB in size).  To really benefit what I do, I probably should focus more on mastering Python and learning Javascript, Jquery, etc.  But, I kind of want to do something a little different and fun.

Many, many moons ago in college, I took an introductory course to C++, and looking over snippets on the web I do recognize a lot of the syntax, although I'm so rusty that starting over wouldn't be a big concern of mine.  I didn't realize there was such a big difference until I started digging in and learned that there are a lot more features and syntax differences in C++ that make it slightly (significantly?) different than straight up C (although I would imagine the transition is as minimal as American English to British English).
 
Probably 99% of the time I'm working in a Linux environment, and so portability is not a major concern.  However, I would like it (especially if I develop some really useful tools) to be able to run these programs in both a Linux and Windows environment.  I haven't researched this, but I have a feeling like this is a complete non-issue.  Any advice on that aspect? 

So, to the my esteemed colleagues, who know a lot more about the usefulness, elegance, etc of each, what do you recommend?  I don't mind (and probably plan) to learn both, but which would be a better starting point?  Would it make sense to start with C, since it came first, and then layer C++ on top of it, or is it better to learn one or the other to avoid syntactic confusion?

---

### Post by nvteighen on 2013-07-19
I'd go for C. I know C++ has exactly the same low-level capabilities C has, but it also has a lot of higher-level stuff that is actually considered to be part of "learning C++ correctly". In fact, in my opinion, to use only the low-level parts of C++ is pointless: for that, just use C (and you can make OOP in C, so C++ is not a must if you want it). Be aware that C++'s ABI is not even standarized, so if you're really interested in call conventions and stuff that is in the lowest level imaginable (e.g. ASM), C is your best option...

Well, this is the opinion of another hobbyist programmer (I'm a linguist :) )

---

### Post by trent.josephsen on 2013-07-19
As another hobbyist, but a hardware engineer this time, it really doesn't matter which one you learn or (if you learn both) which one you learn first. What's important is to think of them not as different dialects of the same language, but as different languages with different strengths and different problem-solving strategies.

So as not to be repetitive, [here's a link to a post](http://ubuntuforums.org/showthread.php?t=2003553&p=12026382#post12026382) I made about practical considerations of C and C++ when the topic came up last year. There are some smart people in that thread too. In short, C++, despite being younger, hasn't aged as gracefully as C. (And that's saying something when you can call C99 "aging gracefully").

Since your stated goal is to learn more about low-level programming, I don't think C++ offers you any advantage over C, and since my own preference is for C, that's what I recommend. But choose wisely.

---

### Post by drmrgd on 2013-07-19
Thanks for the perspective!  I was already leaning more toward C, and I think you both seem to agree with that.  

Trent thanks for the link and the in depth insight!  I hesitated to describe C and C++ as more like two different languages based on what I had read up to that point, even though it seemed the case.  After reading through that thread, though, it seems that the both are indeed almost two separate languages.  I knew asking here was going to be beneficial!

One more question, apart from the K&R book, what other resources would you recommend to get started?  Like I said, although I'm not a programmer by trade, I'm not new to programming and comfortable with computer logic.  So, really I just need to learn the syntax and the unique elements of how things are done in that language.

---

### Post by trent.josephsen on 2013-07-19
Given that you already have programming experience including some Perl, I'm not sure I have any secondary recommendations after K&R. If you decide to get that book and work through it, doing the exercises as you go is a good idea. (Another book I've seen highly recommended, but haven't used myself, is C Primer Plus by Stephen Prata.)

The language has evolved somewhat beyond the book, though. Perhaps the best way to supplement any book is with live advice. I have been known to lurk comp.lang.c, where there is maybe a 70/30 split of experts to trolls, but in general has a very high rate of success in solving problems. Actually, even if you don't post, just lurking there while you learn is probably a good idea; it'll give you a feel for some rookie mistakes to avoid and maybe teach you more than you really wanted to know about the several versions of the C standard. Of course, you can always post here as well.

---

### Post by trent.josephsen on 2013-07-19
Oh, and as for the portability issue: if you use standard C and cross-platform libraries, it is pretty much a non-issue unless you write programs that use platform-specific behavior like endianness or integer representation. Usually you can tell whether a function/header/etc. is standard or not by reading the manpage (see the CONFORMING TO section) or by a quick Web search. Portability often depends on what kind of programs you write; there's no C standard networking stack or GUI toolkit, but number crunching and text I/O is essentially universal.

---

### Post by drmrgd on 2013-07-19
> **trent.josephsen said:**
> Given that you already have programming experience including some Perl, I'm not sure I have any secondary recommendations after K&R. If you decide to get that book and work through it, doing the exercises as you go is a good idea. (Another book I've seen highly recommended, but haven't used myself, is C Primer Plus by Stephen Prata.)

The language has evolved somewhat beyond the book, though. Perhaps the best way to supplement any book is with live advice. I have been known to lurk comp.lang.c, where there is maybe a 70/30 split of experts to trolls, but in general has a very high rate of success in solving problems. Actually, even if you don't post, just lurking there while you learn is probably a good idea; it'll give you a feel for some rookie mistakes to avoid and maybe teach you more than you really wanted to know about the several versions of the C standard. Of course, you can always post here as well.

Excellent!  I'm going to pick up K&R. I was happy to see that there were exercises in the book; the best way to learn is to do!  Thanks for all the advice.  If that use group is anything like Perl Monks, I'll bet I will find it very helpful.

> [COLOR=#000000]Oh, and as for the portability issue: if you use standard C and cross-platform libraries, it is pretty much a non-issue unless you write programs that use platform-specific behavior like endianness or integer representation. Usually you can tell whether a function/header/etc. is standard or not by reading the manpage (see the CONFORMING TO section) or by a quick Web search. Portability often depends on what kind of programs you write; there's no C standard networking stack or GUI toolkit, but number crunching and text I/O is essentially universal.

That's great to hear!  I think I'll primarily be doing number crunching and text I/O, so it sounds like I will be set.  

Time to get some materials and start reading!  Thanks again[/COLOR]:)

---

### Post by steeldriver on 2013-07-19
drmrgd, like you I am not a professional programmer (physical science / engineering) but I've programmed mostly numerical stuff in both C and C++ over the years - I still find myself dipping into K&R even though I have several other books - as K&R say in the intro "C is not a big language, and it is not well served by a big book."

If you're going to be doing a lot of number crunching then I've found the 'Numerical Recipes in C' books to be useful - even when I don't actually use their code, the discussions around each topic can steer you away from many pitfalls

---

### Post by drmrgd on 2013-07-20
> **steeldriver said:**
> drmrgd, like you I am not a professional programmer (physical science / engineering) but I've programmed mostly numerical stuff in both C and C++ over the years - I still find myself dipping into K&R even though I have several other books - as K&R say in the intro "C is not a big language, and it is not well served by a big book."

If you're going to be doing a lot of number crunching then I've found the 'Numerical Recipes in C' books to be useful - even when I don't actually use their code, the discussions around each topic can steer you away from many pitfalls

Thanks for the suggestion, steeldriver.  I think I may have a look at that book too once I get a little further.  Looks very informative.

---

