---
title: "Best way to begin to learn programming."
date: 2009-06-17
forum: Programming Talk
---

### Post by themusicalduck on 2009-06-17
I'm sure this has probably been discussed to death before somewhere.. but I'm looking into properly learning at least a basic understanding of programming, but I feel a bit lost with the number of options around and have been unable to really properly dedicate myself to it yet.

I'd like to learn using Ubuntu ideally. My main questions are: where to start? Which language? Which IDE? Is there a good place where there are some easy to follow tutorials, preferably using that IDE? I'm aware that there is comprehensive information on programming on the web, but it makes more sense to me to find opinions on the best place to start as a beginner. 

I'm guessing that C is the best language to learn first since a lot of languages seem to be similar to it and it is a good comprehensive language to learn. As far as I know. Also, I did a module this year at university on programming and C was the language we used so it makes sense to continue this. We used xcode on OS X and it was great, but I want to use linux when learning on my own time.

The easiest IDE I've tried so far is monodevelop. It seems to be fairly clear without being overly simple and I like the fact that it has a built in GTK interface designer. (although only for C# it seems) I've also tried Eclipse, but that seems to be very heavily focused on java and not on C.

As you can probably tell I'm a bit of an utter noob when it comes to this but I want to find out the best way to go about this in case I end up going in the wrong direction and find I've been completely barking up the wrong tree learning the wrong language and software.

Thanks in advance for help.

---

### Post by Mirge on 2009-06-17
I would honestly learn a bit more "friendly" of a language than C to start, just to grasp the concepts of programming in general. I'm sure Python will be one of the most recommended, but I've no experience with it personally. Seems neat though.

Once you have an idea of what sort of programming you want to do, then you can narrow in on a specific language and fine-tune your skills with it.

---

### Post by OutOfReach on 2009-06-17
> **Mirge said:**
> I would honestly learn a bit more "friendly" of a language than C to start, just to grasp the concepts of programming in general. I'm sure Python will be one of the most recommended, but I've no experience with it personally. Seems neat though.

Once you have an idea of what sort of programming you want to do, then you can narrow in on a specific language and fine-tune your skills with it.

Why not C?
C easier than most people says it is (but of course its not as easy as Python), I think that C is a great language for a beginner

---

### Post by Java Geek on 2009-06-18
> **OutOfReach said:**
> Why not C?
C easier than most people says it is (but of course its not as easy as Python), I think that C is a great language for a beginner

I started on C...It was hard to grasp at first but I figured it out sooner or later.

---

### Post by cph05a on 2009-06-18
I think C is a good place to start because it is a very simple language. I think it's important to have a feel for a procedural language before learning about Object Oriented programming. 

One thing is for sure though, no matter what language you learn, the best way to program is by actually programming, and being both curious and creative. You'll never learn by simply going to a class and listening to a teacher unless you actually apply it.

---

### Post by sam191 on 2009-06-18
themusicalduck, I know exactly what you're going through, I was in your position a couple of months ago. 

I highly recommend Python, and I'll tell you why. 

I started with Python as my first language, so I might be a bit biased, but I always found myself coming back to Python. What I mean is, I started with Python and "language hopped" a lot. But I always got stuck. When I came back to Python, everything came into place. 

There is no correct way to start. My advice would be to do what you like, because then you will learn the most and will have fun. And always be curious!

---

### Post by jacensolo on 2009-06-18
I also recommend C. If you start thinking on the level of C it will be easier to move to other languages (such as python, ruby, or Lua) than move from one of those to C.

---

### Post by sam191 on 2009-06-18
I would like to add a few things I forgot to mention. 

With a bunch of mixed answers and opinions, you will leave these forums in the same position you came in. (Also a big problem I had)

One thing I want to ask you is why do you want to program, and what do you want to program? When you answer these questions, then you can decide where to start.

If you are comfortable with C and want to learn it, then by all means go ahead. But I have tell you, when I started out I thought I would get an amazing foundation in programming if I start "correctly", but everywhere I went I was given different answers. This left me confused for a long time. 

I think that actually starting is the hardest part. But once you've started it is easy to continue. I am currently learning C after starting with Python, and it is a hell of a lot easier to understand now. I'm soon going to go for C++ and Java, because the Computer Science curriculum use them, but I would never program in them if I had the choice (also depending on what I'm making), I would probably use Python 90% of the time.  

What I'm trying to get at in this long post is that, I know exactly where you're coming from, and that you should start with the language you most want to learn. Don't get me wrong here, you should eventually learn many others, but I think your first should be able to give you tangible results and provoke your thoughts (solving the problem vs fighting syntax errors). 

Long story short, figure out what you want to do, start doing it, and remember to have fun! (Thought this post would never end :D)

---

### Post by Cyanidepoison on 2009-06-18
If you want to study computer science and learn about your machine in general, pick C.  C will teach you everything you need to know.  You can do object-oriented programming in C if you want, too, so don't let people try to confuse you into thinking that you need some  bloated language to make a class.  The void* in the most powerful thing you have at your disposal.  You can learn about data structures (and write your own implementations, which really helps you get the important bits) such as linked lists, dictionaries, stacks, etc.

If you just want to be practical and get some simple automation work going, use Python or something easy like that.

---

### Post by CptPicard on 2009-06-18
*Sigh*... here we go again. I guess this stuff needs to be rehashed with all newcomers to the forum ;)

First of all, I would certainly tell a beginner to start with Python. It is both easy and approachable and will go a long way, and in addition teaches you a lot of important concepts straight away along a pedagogically meaningful learning curve. "Easy to play with" is a really important quality in a teaching tool.

Now, I do agree that C has one thing going for it -- that it's rudimentary. At least it's a small language (at least you're not suggesting C++), and it teaches you some *very* basic stuff easily (because that's all it has), but you really can go only that far with a few loops, functions and conditionals.

> **jacensolo said:**
> If you start thinking on the level of C it will be easier to move to other languages 
(such as python, ruby, or Lua) than move from one of those to C.

I never understood this argument. I have a strange hunch that some people consider C "hard enough" that it somehow "forces" you to "implement everything from scratch", but it really is not as if a beginner is going to be able to do that, or should do it, or should discover how to do it in C "out of nothing". Instead, they'll be segfaulting (which is completely uninformative) while they could actually be learning how to put functions, assignments, conditionals etc together, in an interactive REPL in Python no less...

I would rather say it's totally the opposite -- moving from Python or Ruby to C is a trivial migration -- after all, all control constructs of C are essentially present in higher-level languages, and by then you already actually understand what you're doing, and how to possibly emulate in C, using those rudimentary control constructs, what you used to do in the higher-level language. You will already know what you want in your program, so you know what you will be writing.


> **Cyanidepoison said:**
> If you want to study computer science and learn about your machine in general, pick C.  C will teach you everything you need to know.

Of course, most CS is totally language-independent (I actually rarely programmed anything for my degree, it was 95% math, algorithms, pencil and paper), but ... how does it teach me what I need to know? How does it teach you what objects are? Higher-order functions? Closures? Basics of data structures? (Yes, you'll want to implement them eventually, but let's just use them for now)... there's lots of stuff out there you honestly will never learn from C, but will have to learn from somewhere else first before you know what you want to do in C, if you need to do it in C.

> 
  You can do object-oriented programming in C if you want, too, so don't let people try to confuse you into thinking that you need some  bloated language to make a class.

Yes, but but you won't know how to do your method dispatching, or what it even is, if you've never actually written any object-oriented code anywhere. You really need to learn the concepts from somewhere before you can hack up an OOP-language emulation in C.

> 
  The void* in the most powerful thing you have at your disposal.

I wouldn't get too excited over something that is just an untyped "indirect value"... reference types and array indices carry the idea just fine in other languages. That is, pointers are not computationally "necessary" for a language, but just happen to be present in the more machine-level context.

> 
You can learn about data structures (and write your own implementations, which really helps you get the important bits) such as linked lists, dictionaries, stacks, etc.


Writing any of these in Python is actually just as informative from the conceptual point of view, nothing of the understanding of how they work is lost.

> 
If you just want to be practical and get some simple automation work going, use Python or something easy like that.

Well, as I said before, there are loads of important *concepts* present in Python (and other high-level languages) that just are not there in C, and you will be learning them almost automatically as you go along, without specifically having to look them up. Seriously, I have never, ever met a C coder that wasn't "educated" by something like the concept of a closure -- that is, he would have "known" it beforehand from C. It just isn't on their radar.

Most people who dismiss higher-level languages as just simply "easy" just come across as people who haven't programmed all that much ;)

Here's a collection of thoughts from nvteighen that have been expressed here over the past year or two...

[http://lambdagrok.wikidot.com/articles:what-is-programming](http://lambdagrok.wikidot.com/articles:what-is-programming)

---

### Post by rjack on 2009-06-18
Books available online:

[How to Design Programs](http://www.htdp.org/)
[Structure and Interpretation of Computer Programs](http://mitpress.mit.edu/sicp/full-text/book/book.html)

---

### Post by chipppy on 2009-06-18
Good Evening

I am just a little step ahead of you on the same subject.

In the end I wrote down all the different languages that were recommendedto me by asking the same questions.  I then threw a dart at then bit of paper and hit one.  That is the one that i chose.

It just the jump in and learn to swim theory.  I have downloaded a couple of ebooks on my choosen language and started reading.  All is good so far.  I cannot help you chose but I can help in saying that it is hard to start with but once you get into it.

I am now onto the IDE choice step.  Your next step once you choose a language.  Do a search when you get to this step and hopefully you will find a post with lots of questions and answers about IDE's.  I know I am about to start asking a heap.

Good luck

Cheers
chipppy

---

### Post by monraaf on 2009-06-18
> **chipppy said:**
> I am now onto the IDE choice step.  Your next step once you choose a language.  Do a search when you get to this step and hopefully you will find a post with lots of questions and answers about IDE's.  I know I am about to start asking a heap.

Well, you don't really need an IDE. A good text editor with syntax highlighting and automatic indentation such as VIM will do just fine.

---

### Post by lisati on 2009-06-18
I just had a fit of nostalgia, and began to feel thankful that these days we don't have to be limited to punched cards (or "card images" stuck in a text file somewhere) The first bit of programming I tried my hand with used dialect of Fortran using punched cards where you poked out "chads" with a pen or paper clip - the cards had a habit of jamming in the card reader and random chads would sometimes drop out, confusing the compiler no end. Very frustrating.

---

### Post by stevescripts on 2009-06-18
@ lisati - hmm, yet another old FORTRANer ... ;)

OP - one more $.02 on the topic:

1. Pick a language to learn.

2. Find a decent book or tutorial.

3. Read code, write code, test code, edit code ....

4. Repeat #3 til done ...

Steve

---

### Post by NielsBhor on 2009-06-18
A very simple language is Basic. :D

---

### Post by themusicalduck on 2009-06-18
Wow, thanks for all the replies!

I've heard lots of good things about Python so it looks like a good place to start. I can probably apply my very basic understanding of C so far to it, and then vice versa later on (since I will probably be continuing in C on my course next year).

For now though I will focus on python and make a decision later on whether it's right for me. I'll look at some of the links posted here, find some ebooks and go from there. As for IDEs, a search on Add/Remove have come up with a few editors like Kate, Eric, Vim and Geany. So I have a few to give a try for now.

My aim with programming is primarily at software development, probably for linux or OS X more than Windows. Ultimately I have an interest in music production software (my course is in music tech) but it's probably a while before I have to think too much about that.

Thanks again for all the opinions and advice/experiences. It's nice to know it's not just me who has felt lost like this :p

---

### Post by Mirge on 2009-06-18
For those who asked why not C as a first language, I agree with what CptPicard said, though he went into a bit more detail than I would have lol!

I remember when I first started programming (I started with C--didn't get far until I learned other languages and came back to it)... I would get frustrated because while the C language itself has a relatively small syntax to learn/remember, the concepts can be a little overwhelming for a beginner. Because it's a "lower level" high level language, you have a lot more control. Sometimes that control is more than you really need when first starting out... mess up with an array or pointer and you can run into unexpected errors or segmentation faults. No fun.

Also it takes more generally to achieve the same result. People like instant gratification... it gives them motivation to continue learning. Sure, the syntax can be far different between languages (ie: Python vs C), but the programming concepts and practices can be applied if, afterwards, you decide that you need to use C. Because of your familiarity with programming concepts and practices, you'll be able to learn and make use of C much quicker, imo.

---

### Post by Can+~ on 2009-06-18
> **Cyanidepoison said:**
> If you want to study computer science and learn about your machine in general, pick C.  C will teach you everything you need to know. ** You can do object-oriented programming in C** if you want, too, so don't let people try to confuse you into thinking that you need some  bloated language to make a class.  **The void* in the most powerful thing you have at your disposal**.  You can learn about data structures **(and write your own implementations, which really helps you get the important bits)** such as linked lists, dictionaries, stacks, etc.

My blub-o-meter just exploded.

Funny that you mention void*, when, on the other hand, CPython's implementation of types uses a struct with a void* and a type identifier. Plus having a Garbage Collector; Does it make python the most powerful thing you have at your disposal? Probably not, but neither is C.

And then again, have you written a list of a few elements on a paper?

A, B, C, D...

The great idea of having an abstract "List" object is that you don't have to care on how it works internally. Learning how this things work is not a minus clearly, I would probably suggest it to everyone, except a beginner.

---

### Post by arcdrag on 2009-06-18
If you're learning on your own I would start off with something like Python.  I personally think it would be extremely difficult to learn complex data structures in C without taking classes.
Also, Python you can start off creating programs that are actually useful and/or have a pretty GUI which will keep things interesting.  

With C...your first few hundred hours of effort will be spent creating programs that output some text to the screen or a text file.  This extremely boring nature of a programmer's beginning burns out most people that are hoping to find a new hobby.

---

### Post by ranthal on 2009-06-18
Verilog, use Synplify, that Xilinx stuff is crap.

---

### Post by ranthal on 2009-06-18
Sorry, don't pay attention to that last post, it's getting to be towards the end of a long day.

If you want immediate results then Python.

If instead you're after the actual thought process behind programming then C++.

And use vim or some other text editor.  I saw some stuff about an IDE in some earlier posts and no offense to the poster but I noticed it was form one beginner to another, most of the guys I see posting a lot on this forum are backing up the text editor.

---

### Post by Mirge on 2009-06-18
> **ranthal said:**
> Sorry, don't pay attention to that last post, it's getting to be towards the end of a long day.

If you want immediate results then Python.

If instead you're after the actual thought process behind programming then C++.

And use vim or some other text editor.  I saw some stuff about an IDE in some earlier posts and no offense to the poster but I noticed it was form one beginner to another, most of the guys I see posting a lot on this forum are backing up the text editor.

Lotta beginners, specify :P

BTW, "Edit" button is awesome :).

---

### Post by simeon87 on 2009-06-18
> **ranthal said:**
> If instead you're after the actual thought process behind programming then C++.

Let's make that: if instead you're after the necessary evils of machine related problems then C++.

---

### Post by ranthal on 2009-06-18
> **Mirge said:**
> Lotta beginners, specify :P

BTW, "Edit" button is awesome :).

Eh, whole point was to not call out any specific person.

...and like I said, long day](*,)

---

### Post by Can+~ on 2009-06-18
> **ranthal said:**
> If instead you're after the actual thought process behind programming then C++.

The actual thought process behind programming involves shooting yourself in the foot in a daily basis?

Never knew.

*waits for CptPicard to do a multi-quote response to ranthal*

---

### Post by ranthal on 2009-06-18
> **simeon87 said:**
> Let's make that: if instead you're after the [SIZE="4"]**necessary**[/SIZE] evils of machine related problems then C++.

IMO that's a huge part of SW that a lot of programmers can't handle where they should.  It would be great if SW were perfectly abstract and nobody ever needed to know the difference between 32 and 64 bit integers, network and host endianness, etc, but in the end the reality is that all SW is built on HW.

---

### Post by arcdrag on 2009-06-19
> **ranthal said:**
> IMO that's a huge part of SW that a lot of programmers can't handle where they should.  It would be great if SW were perfectly abstract and nobody ever needed to know the difference between 32 and 64 bit integers, network and host endianness, etc, but in the end the reality is that all SW is built on HW.

This is true, and everyone should dive into some lower level code at some point...but that point doesn't necessarily have to be day 1.  If you're dedicated to learning, it might be a good idea...but in an age where there's gui's for everything, creating programs that are hundreds of lines long that do a little bit of math and then output a few lines of text to a screen is probably pretty discouraging to a new programmer.

---

### Post by ksp1717 on 2009-06-24
I would recommend C. 

I have started programming with C and I find it easy. There are other languages that are based on C. 

I have very limited knowledge of python, started using it very recently.

Cheers
Shyam

---

### Post by CptPicard on 2009-06-24
> **Can+~ said:**
> 
*waits for CptPicard to do a multi-quote response to ranthal*

Uh, ok, if you insist ;)

> **ranthal said:**
> 
If instead you're after the actual thought process behind programming then C++.

If one is interested in learning C++ then one should learn C++. IMO the actual important structures, concepts and "thought process" behind programming is illustrated much more conveniently in a lot of other languages. C++ is a bit too complex for it to be particularly "clear" in that regard, and it actually lacks a couple of interesting things some other languages have (I always bring up proper higher-order functions and closures in this context), or alternatively using them is pretty hard (STL algorithms instead of list comprehensions, map/filter/reduce)...

> **ranthal said:**
> IMO that's a huge part of SW that a lot of programmers can't handle where they should.  It would be great if SW were perfectly abstract and nobody ever needed to know the difference between 32 and 64 bit integers, network and host endianness, etc, but in the end the reality is that all SW is built on HW.

I always felt like those details were somewhat uninformative in the big scheme of things... details you'll want to be aware of in some contexts of course, but that are (and should be) mostly handled by the compiler. Interestingly, all SW might eventually run on HW, but that, in the end, is just another Turing-complete computation formalism.. the program does not actually know, nor does it fundamentally care, whether it's a physical machine or not :)

> **arcdrag said:**
> If you're dedicated to learning, it might be a good idea...

Not that I am "opposed" to the idea of understanding low-level workings of the machine, but if you're dedicated to learning about the meaning of the abstractions of programming and how they can be put together, try some Lisp instead... 

This is actually a fairly deep philosophically divisive issue here... nothing wrong with the low level per se, it just never really felt like it actually taught me much about how to actually "think" about computation, programs, computable problems...

---

### Post by ranthal on 2009-06-24
> **CptPicard said:**
> This is actually a fairly deep philosophically divisive issue here...

+1 to that.  I mistakenly didn't choose some words carefully enough before I realized how many people would react to what I was posting (though that did make some things a lot more interesting ;)).

I think because my background is EE I enjoy understanding how some of the interactions mesh.  I also know plenty of people I work with who however feel like that is pure torture.   So hopefully the OP can read through the debate and figure out what suits him/her.

---

### Post by CptPicard on 2009-06-25
> **ranthal said:**
> 
I think because my background is EE I enjoy understanding how some of the interactions mesh.  I also know plenty of people I work with who however feel like that is pure torture.   So hopefully the OP can read through the debate and figure out what suits him/her.

Yeah, there seems to be some Engineering/CS distinction there that creates some of the sometimes rather profound difference in perspective. 

In a CS view though -- that starts to look at things at about the point where the engineer is able to hand over an instruction set, or perhaps even without a machine at all -- it is IMO hard to justify some special place to the hardware-level programming, especially when you can't even theoretically tell any of that apart from anything else. And in a lot of ways, assembly is just kind of so rudimentary it's outright conceptually boring although it might be just harder to get started with (and would be harder to hand-craft the stuff you write compilers for)

But anyway, I'm all for "understanding the interactions" you put it. There is this weird cult though, especially among the n00ber types, that likes to put low-level hacking on a pedestal even though I suspect those guys couldn't program their way out of a paper bag in a language like Haskell which doesn't (oh the horror)  even have raw pointers... :)

---

