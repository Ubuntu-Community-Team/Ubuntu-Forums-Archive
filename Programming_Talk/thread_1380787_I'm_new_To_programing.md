---
title: "I'm new To programing"
date: 2010-01-14
forum: Programming Talk
---

### Post by renoman19 on 2010-01-14
Hello everyone, I'm new to this forum but not to ubuntu, i've been following ubuntu since version 6. something in order to replace windows on my desktop. I really want to contribute to this operating system because i think it is a great operating system. But here is the problem, i have never created a program, not even sure where to start. So any ideas. The programs i hope to make are, Games, Utilities, Multimedia Programs and maybe others. as i said earlier i am a new user to this forum, and i'm not even sure if i posted this in the right area. any help is greatly appreciated! Thanks

---

### Post by slooksterpsv on 2010-01-14
Word of advise - You may start small with simple boring programs, but they are very useful to learn. I remember the first game I had to make was Pong, a boring game, but there was a bit that went into it. It's helped for larger projects and that.

One of my favorite books is: C++ Programming for the Absolute Beginner. It's a great book and walks you through step by step. If you like games, it has you make a game at the end of each lesson - simple and boring yes - but strong fundamentals.

Once you learn C++, look into FLTK (Fast Light ToolKit) it's an easy IDE that uses C++ for the coding. Java is a great one (slow though). 

[php]
#include <iostream>

using namespace std;

int main()
{
 cout << "Hello World!" << endl;
 return 0;
}
[/php]

---

### Post by iponeverything on 2010-01-14
Download or buy a book on C++ or C programing and start working your way though it from the begining. If you decide to study comp-sci some point you will have good head start..

---

### Post by ronniestamps on 2010-01-14
```
#include <stdio.h>

main()
{
  for(;;)
      { 
          printf ("Hello World!\n");
      }
}

```

always a good start ;)

---

### Post by SunSpyda on 2010-01-14
First, pick your technique. Will you learn bottom-up, or top-down?

The former will mean that you learn ASM as your first language. Then you learn C, then higher, etc.

The latter will mean you learn a language like Ruby/Python/Perl then work your way down ->Java->C++->C->ASM.

A more rare way is to learn a functional language like Haskell first. IMO this encourages good practices, and will increase the chance of you thinking up ingenious solutions.

Also, be aware that a programmer usually ends up learning 9 languages (or something like that :) ), so don't be afraid about learning the 'wrong' language (like learning Perl if you want to be a professional game programmer.)

---

### Post by nmccrina on 2010-01-14
> **ronniestamps said:**
> ```
#include <stdio.h>

main()
{
  for(;;)
      { 
          printf ("Hello World!\n");
      }
}

```

always a good start ;)

My professor said, "There are two kinds of people: those who have written an endless loop, and those who will."

It's so true. :)

---

### Post by raydeen on 2010-01-14
> **nmccrina said:**
> My professor said, "There are two kinds of people: those who have written an endless loop, and those who will."

It's so true. :)

That was pretty much what any kid in the '80's did as their first program. Only it was more like

```

10 PRINT 'HELLO WORLD!'
20 GOTO 10

```

:)

---

### Post by nmccrina on 2010-01-14
> **raydeen said:**
> That was pretty much what any kid in the '80's did as their first program. Only it was more like

```

10 PRINT 'HELLO WORLD!'
20 GOTO 10

```

:)

I wish I was around in the '80s...The music and movies were better, and you could actually get caught up with the current state of computing relatively quickly (from what I can tell, lol). An undergraduate student can't develop a groundbreaking operating system anymore :(

---

### Post by raydeen on 2010-01-14
It really was a cool time especially if you were into computers. The big thing for us back then was running out to the newsstands once or twice a month to get the newest issue of Compute! or whatever computer magazine was tailored for your brand of computer. (Antic and A.N.A.L.O.G. for me) We'd run home, fire up the machine and start furiously typing in the programs from that issue and then spend the next week or two finding our errors and sometimes the errors of the author or publisher of the magazine. It really was the best way to learn programming. Of course, we've had to pretty much unlearn a lot of the methods that BASIC taught, but the fundamentals were there. Subroutines are now called functions. 99 GOTO 10 is now usually a while loop (that was the only time I ever used GOTO). Variables are still variables. Strings are still strings. 

As for movies, we had Tron. Today's kids have Avatar. It's all good. :)

---

### Post by lisati on 2010-01-14
> **nmccrina said:**
> My professor said, "There are two kinds of people: those who have written an endless loop, and those who will."

It's so true. :)

I was taught that the endless loop was something to be avoided, like the plague. 

Some of us here, myself included, first learned programming on computers where it was common to punch up your program on [punched cards]("http://en.wikipedia.org/wiki/Punched_card"), submit them to the computer centre, and wait for what seemed like an eternity for the printout to come back. If the program got stuck in an infinite loop, the programmer often had no way of doing the equivalent of hitting Ctrl+C.

---

### Post by nmccrina on 2010-01-14
> **lisati said:**
> I was taught that the endless loop was something to be avoided, like the plague. 

Some of us here, myself included, first learned programming on computers where it was common to punch up your program on [punched cards]("http://en.wikipedia.org/wiki/Punched_card"), submit them to the computer centre, and wait for what seemed like an eternity for the printout to come back. If the program got stuck in an infinite loop, the programmer often had no way of doing the equivalent of hitting Ctrl+C.

He wasn't advocating endless loops, he meant it like, "Face it, at some point you're going to forget to increment your counter or something and you're going to be waiting a while."

So, if you didn't have Ctrl+C, was the only recourse just shutting the machine off?

---

### Post by nmccrina on 2010-01-14
> **raydeen said:**
> 

As for movies, we had Tron. Today's kids have Avatar. It's all good. :)

I was thinking of Bladerunner, Indiana Jones, Star Wars, Ferris Bueller's Day Off, etc. Those have some undefinable 'X' factor that I haven't seen in most of today's movies, even in the later additions to those series.

I haven't seen Tron. :)

Edit: I'm looking at it on Wikipedia, and it seems like The Matrix pretty much ripped it off completely. O.o

---

### Post by Senesence on 2010-01-14
> **SunSpyda said:**
> First, pick your technique. Will you learn bottom-up, or top-down?

My view on that subject is as follows:

**Top down:**

Top-down approaches are more likely to keep you programming, because you'll be able to put together fairly complex applications quickly, and this will keep you from getting bored/frustrated by the boilerplate details of lower level languages.

The down side? -> You won't really get to understand lower level concepts, and that lack of understanding will hurt you, especially when you consider that the majority of really popular/high-performance software is written in C/C++.

As someone who started his programming adventures in a very high-level language like Python, I can tell you: Having to manage your own memory, and worry about types, especially when these things were never even an issue in your previous experience; that can be a real pain.

**Bottom up:**

I don't think one has to start with ASM, but C is definitely the "lingua-franca" as far as programming languages are concerned. Also, if you ever plan to program a piece of hardware directly, your board will probably come with a C compiler.

Overall, you'll just have more options, and then if you want to learn higher-level languages, it should be a fairly straightforward process.

However, this is assuming that you can spend months writing terminal programs in C, rather than making a game in Python, using something like PyGame.

When you're just starting out, C is not a very fun language (mainly because things are moving so slow), so many people who start out with C tend to quit soon after (especially if they're learning on their own).

---

### Post by lisati on 2010-01-14
> **nmccrina said:**
> He wasn't advocating endless loops, he meant it like, "Face it, at some point you're going to forget to increment your counter or something and you're going to be waiting a while."

So, if you didn't have Ctrl+C, was the only recourse just shutting the machine off?

When I was learning programming, first-year students got nowhere near the computer. There were options for cancelling a program that got stuck, but these usually involved going through people who were actually authorised to have access to the computer.

I was taught that doing something like **while(1)** or **[noparse]for (;;)[/noparse]** was a no-no. It kind of defeats the purpose of having a condition there, you'd be better off using "goto" and jumping out of the loop with an "if" statement.

---

### Post by CptPicard on 2010-01-14
> **Senesence said:**
> 
The down side? -> You won't really get to understand lower level concepts, and that lack of understanding will hurt you, ...


The issue with the lower level is that there really aren't much concepts, and those concepts that do exist, are pretty much contained in one form or the other in higher-level languages. Compare loops to Scheme tail-call recursion which is a more general formulation of the same thing...

There are *specifics* (that just need to be "memorized") but not much that you wouldn't conceptually *understand* by having had prior exposure to a higher-level language. Even the pet example, the pointer, is nothing but a typed indirect reference that is also quite understandable as just an array index... 

> Having to manage your own memory

It's just a tedious, repetitive resource-management problem... perfectly doable for someone who knows how to program; not really anything that in itself is particularly demanding except in effort invested (which is also why it would hold back a learner).

> and worry about types

Well, in Python your program will crash just the same if it's got a wrong type somewhere, it's not as if Python is any more forgiving of such errors. The difference is having to satisfy the compiler at compile-time with a (supposed subsequent) reduction of type errors at runtime -- especially in a language like C++ this requires a lot of "type system design" beforehand while Python just takes the approach that it assumes that things will work, that is, your interfaces in particular are "implicit" and not explicitly given. 

It really is mostly a difference in amount of editing of source you must do, as again, maintenance of the type information is also pretty much busy-work -- after all, a machine is capable of telling you stuff is being wrong somewhere, and you are just annotating into the source *things you already know* in order to satisfy the compiler. I do not quite see how this makes you getting better at knowing how the types must work in the correct program to begin with.  Also consider how a lot of modern compilers are capable of inferring most types even in static-typed languages, and how good IDEs are guessing what should go where... the vast majority of that type information is genuinely superfluous.

> Overall, you'll just have more options, and then if you want to learn higher-level languages, it should be a fairly straightforward process.

I am not sure I've ever understood where these "options" are... they mostly just mean reimplementation of a lot of stuff.

I have actually found that a lot of programmers whose exposure is only to your typical imperative programming language in the C/C#/Java/C++ general family actually have big issues bending their mind around the stuff in higher-level languages. This is yet another reason to favour starting directly in HLLs -- you avoid having your mind "stuck" in the way low-level languages pretty much by necessity do things, and a lot of solution approaches become second nature as they simply are more accessible in HLLs...

---

### Post by wmcbrine on 2010-01-14
> **nmccrina said:**
> I wish I was around in the '80s...The music and movies were better, and you could actually get caught up with the current state of computing relatively quickly (from what I can tell, lol). An undergraduate student can't develop a groundbreaking operating system anymore :(It was an interesting time, but, trust me -- today is better. :D For a start, you have practically the whole of human knowledge at your fingertips. In the 80's, if we wanted to know something, we had to spend hours in the library... and often still end up frustrated. And we were all like, "Any day, there's gonna be a nuclear war, and we'll all die." It's hard to express the impact that the fall of the Berlin wall had on us. Plus, the computer I'm typing this on is literally thousands of times faster than the ones I had then, with one *million* times the RAM of my first computer (a ZX81). I'm not exaggerating. Secondary storage was screechy noises on a cassette tape, or if you were rich, a 360K (not G, not M, but K) floppy.

Nostalgia is a crock.

---

### Post by Senesence on 2010-01-14
> **CptPicard said:**
> The issue with the lower level is that there really aren't much concepts, and those concepts that do exist, are pretty much contained in one form or the other in higher-level languages. Compare loops to Scheme tail-call recursion which is a more general formulation of the same thing...

There are *specifics* (that just need to be "memorized") but not much that you wouldn't conceptually *understand* by having had prior exposure to a higher-level language.

Yes, "concepts" was the wrong word to use, and now that you mentioned it, "specifics" was really what I was thinking of.

Thanks.

About the other points you made:

Yes, I would agree that there is nothing more "intellectually challenging" about lower-level languages. I was in fact referring to the "effort involved" in doing tedious, repetitive resource management.

And in the options department: I'm just trying to say that a lot of projects are C/C++ based; a lot of really big projects, like the Linux kernel. Also, if you're going to interact with the hardware directly, C seems to be the way it's done in an overwhelming number of cases.

Now, I'm not saying that Python experience would be irrelevant in the scope of a C/C++ project, but the fact that you can't simply do my_string = "Hello World!" would be quite irritating, and then even more so when you discover that the alternative is char *my_string = "Hello World!", or char my_string[] = "Hello World!".

And then, rather than being able to do something like my_list.append(arbitrary_object), you have to do something like object *object_array = (object*)malloc(sizeof(object)*element_count), and then populate that with a for loop or something like that (I'm not sure, since I'm new to C).

In either case, it's not as trivial as you make it sound (at least for mere mortals like myself).

[quote=wmcbrine]Nostalgia is a crock.[/quote]

:)

---

### Post by lisati on 2010-01-14
> **wmcbrine said:**
>  I'm not exaggerating. Secondary storage was screechy noises on a cassette tape, or if you were rich, a 360K (not G, not M, but K) floppy.

Nostalgia is a crock.
And the floppies on some machines were physically larger but with a smaller storage capacity. I recall seeing one machine (circa 1987 or [noparse]1988[/noparse]) which took 8" disks - it was a bit of a dinosaur even then.

---

### Post by grayrainbow on 2010-01-14
> **Senesence said:**
> My view on that subject is as follows:

**Top down:**

Top-down approaches are more likely to keep you programming, because you'll be able to put together fairly complex applications quickly, and this will keep you from getting bored/frustrated by the boilerplate details of lower level languages.

The down side? -> You won't really get to understand lower level concepts, and that lack of understanding will hurt you, especially when you consider that the majority of really popular/high-performance software is written in C/C++.

As someone who started his programming adventures in a very high-level language like Python, I can tell you: Having to manage your own memory, and worry about types, especially when these things were never even an issue in your previous experience; that can be a real pain.

**Bottom up:**

I don't think one has to start with ASM, but C is definitely the "lingua-franca" as far as programming languages are concerned. Also, if you ever plan to program a piece of hardware directly, your board will probably come with a C compiler.

Overall, you'll just have more options, and then if you want to learn higher-level languages, it should be a fairly straightforward process.

However, this is assuming that you can spend months writing terminal programs in C, rather than making a game in Python, using something like PyGame.

When you're just starting out, C is not a very fun language (mainly because things are moving so slow), so many people who start out with C tend to quit soon after (especially if they're learning on their own).
I would say that C++ was the funniest learning experience in programming languages I had. But I used to consider making 'data base' holding info for my class mates a fun thing to do(B-trees are such a nice creatures!), so maybe my opinion on fun part does not matter :).

>  I'm new To programing
Good Luck! Follow your hard, 'n happy coding(uhm, learning :) )!

P.S.
> When I was learning programming, first-year students got nowhere near the computer.
I here of some theory that beginning programmers shouldn't be allow to access computers and all their programs should be just in papers, and that will make them really thing how the program work, not just to adjust it and make it with bad logical flow full of stupid 'hacks'.

---

### Post by CptPicard on 2010-01-14
> **Senesence said:**
> Yes, "concepts" was the wrong word to use, and now that you mentioned it, "specifics" was really what I was thinking of.

Having read your post I guess we're mostly in agreement here, just to mention it... there is occasionally a "low-level crowd" around that is very vocal and categorical about the denial of "concepts" in HLLs -- ideas that are rather dear to me as a theoretically-minded CS type -- so I may have given you the usual treatment -- apologies if it came off a bit confrontational :p (to me that sort of an ideological view just seems to be a tell of a relatively immature programmer...)

I do not deny the need to actually have to understand the language you have to use, when you have to use it ;) -- my views have more to do with the general applicability of the stuff present in various kinds of languages.

> 
And in the options department: I'm just trying to say that a lot of projects are C/C++ based; a lot of really big projects, like the Linux kernel. Also, if you're going to interact with the hardware directly, C seems to be the way it's done in an overwhelming number of cases.

Sure. Practical considerations will mean you use the language you need to use. Agreed. I am not a practical guy in first instance, even though I do appreciate the "ease" introduced by HLL-programming (just means I can get hacked more on the algorithm...) :p

> 
Now, I'm not saying that Python experience would be irrelevant in the scope of a C/C++ project ... In either case, it's not as trivial as you make it sound (at least for mere mortals like myself).

I am not disagreeing per se... in particular C++ requires quite a bit of "learning how to use C++, and use it right". This part of C++ is certainly non-trivial. C is a far smaller, conceptually simpler language. Purely on the "need to get a C++ project written" front, you are correct in the pure language-usage sense, which your examples illustrate. My issues tend to be mostly with claims that confuse these (often non-trivial, but still tedious and so on) "language-specifics" (say, how to *exactly* work with a string) with more overarching ideas and principles, that, I would say, often find much better expression in HLLs. It is the understanding of this sort of "abstraction" the low-level language types are often almost creepily, actively hostile towards. I would force them take a Lisp class if I could :)

---

### Post by lisati on 2010-01-14
> **grayrainbow said:**
> I here of some theory that beginning programmers shouldn't be allow to access computers and all their programs should be just in papers, and that will make them really thing how the program work, not just to adjust it and make it with bad logical flow full of stupid 'hacks'.

Good idea! :)

Random musing: I've probably got more computing power sitting here in the corner of the room than the whole computer centre had back in my student days. [citation and research needed]

---

### Post by renoman19 on 2010-01-14
Thank you everyone for all the help, as i see it i have a lot of reading and learning to do, i now know which direction to go, i figure i will start learning the C language and work my way up from then. 
thanks!

---

### Post by nmccrina on 2010-01-14
> **renoman19 said:**
> Thank you everyone for all the help, as i see it i have a lot of reading and learning to do, i now know which direction to go, i figure i will start learning the C language and work my way up from then. 
thanks!

Good luck, and remember to **have fun**! :)

---

### Post by raydeen on 2010-01-19
> **nmccrina said:**
> I was thinking of Bladerunner, Indiana Jones, Star Wars, Ferris Bueller's Day Off, etc. Those have some undefinable 'X' factor that I haven't seen in most of today's movies, even in the later additions to those series.

I haven't seen Tron. :)

Edit: I'm looking at it on Wikipedia, and it seems like The Matrix pretty much ripped it off completely. O.o

Bit of a derail here, but just in case anyone here hasn't seen this yet: Tron Legacy.

[http://www.youtube.com/watch?v=6HcsDc_9LX8](http://www.youtube.com/watch?v=6HcsDc_9LX8)

I am soooo stoked. And yes, Tron was pretty much the original Matrix. Still one of my favorite movies. The Lightcycles game was one of the first games I ever programmed on my Atari 400. I'm sure all of us in our 40's did something similar ;) So simple but so satisfying when you're 13.

---

### Post by slooksterpsv on 2010-01-19
C is a good language - when you learn C, you'll come to love C++. C will seem like a pain at first, then as you move up you'll find that things get easier for the programmer.

E.g. C, C++, etc. you have to allocate and dump your memory. Java has garbage collection - same with Objective-C, C#, VB.NET, etc.

Here's a simple C program to get you started:
[php]
#include <stdio.h>

int main()
{
 printf("Hello World!\n");
 return 0;
}
[/php]

---

### Post by MindSz on 2010-01-19
> **nmccrina said:**
> My professor said, "There are two kinds of people: those who have written an endless loop, and those who will."

It's so true. :)

My prof said: "There are 10 kinds of people. Those who get binary and those who don't".

---

### Post by nmccrina on 2010-01-19
> **MindSz said:**
> My prof said: "There are 10 kinds of people. Those who get binary and those who don't".

I have a sweatshirt that says that. Even one of the engineers I hung out with said that was the nerdiest shirt he'd ever seen. :lolflag:

---

### Post by Jonmarc on 2010-01-19
I was one of those who dove into C and got bored out of my mind at the pace of the learning curve and at the failures of my simple program attempts. 

_C for the absolute beginer_ is the book I used and it was great! I was the one lacking effort and patience.

Since then I have learned XHTML/CSS and moved up to java. Having a taste of c made java easy and fun. I plan on continuing on to learn php and mysql.

C is a great starter language because it teaches you how to translate complex ideas in to broken down logic. Which at time can be a true art.

---

### Post by CptPicard on 2010-01-19
> **Jonmarc said:**
> 
C is a great starter language because it teaches you how to translate complex ideas in to broken down logic. Which at time can be a true art.

A different and much-discussed other view on this is that you learn exactly the same kind of algorithmic breakdown in pretty much any language that allows for imperative programming, and get *other* important ideas that C doesn't contain in a much more easy to use (in the "pure work and effort" sense) package in a language like Python. There really is not much that comes to mind in C that you'd have to specifically learn from C, and it is interesting how hard it is for habituated imperative-programmers to for example get comfortable with functional programming, which IMO illuminates actual algorithmic structure often much more nicely than a "process description"...

---

### Post by 12_String on 2010-01-19
I am new , too, and think you have a lot of guts to want to start learnig to program...it looks so time-consuming and hard. I wish I had begun to learn programming years ago but now I don't have the time to devote to it. So, what I do is try to find a way around the problems I want to fix. For example: when I put guitar notes above the lyrics, and then post it on say wordpress or some other online place, their system seems to ignore the spacing between the guitar notes and they glump them all together on the left at the beginning of a line of lyrics. Nothing I have done fixes the notes above the word that occurs on the chord change. So my "fix" is to underscore the syllable that the change occurs at, and then all a viewer has to do is use their space bar to align the first note above the first underlined syllable, the second with the next and so forth. I was hoping there would be a better "fix" but nothing seems to work. (Note: Google Docs preserves them real good, but some of my friends' computers lock up when they try to view Google Docs, and that opens up a whole new can of problems to "fix". Shucky darn.)

---

### Post by 12_String on 2010-01-19
I volunteer at a local thrift store and the cutest t-shirt I've seen shows the AC / DC logo with the lightning bold in the center, but the letters said   AB / CD and was on a small child's tee.

---

### Post by iponeverything on 2010-01-20
I am not programer. I am a hack ;) I can throw together a php or perl program to do what I need. Programming in C or ASM for me is like going out into the parking lot and attempting to arrange a million tiny pebbles into a work of art.. 

So, I have no strong feelings about this. When was learning, I stated with mit-scheme to learn programing concepts and techniques then we moved on to C for data structures and algorithms and then to assembly to stress test my brain synapses.

---

