---
title: "What programming language to choose?"
date: 2007-03-21
forum: Programming Talk
---

### Post by ronald_stall on 2007-03-21
I want to get back into programming, I never really got into it heavy but did some light programming years ago with VB, basic, and perl. 

Not sure what I want to do yet but I want to get into learning what is new out there. Any suggestions?

---

### Post by mac.ryan on 2007-03-21
This is the typical question for holy wars! ;)

Anyhow, as a matter of facts, on the ubuntu website (in the section on "participation") they advice you to start from phython. There is a nice, plain, enjoyable book that guides you through learning it.

Of course as soon as I shared this with my geek friends, each of them came up with different recommendations... yet, I found interesting ubuntu "sponsors" this as entry-point into development.

(I tried to find the page again for you, but I can't find it anymore in the new structure of the website...)

---

### Post by ciscosurfer on 2007-03-21
I agree with the previous poster.  At the same time, it really depends on what you want to use it for.  In other words, certain languages are better for Web programming, others are more suited for core system development.  Some are easy to pickup if you have prior experience, others are more difficult (more of a learning curve...of course, this is subjective, but from my experience, it holds true).

My personal favorites (in no particular order or used for any particular function):
[LIST]
[*]Python
[*]Perl
[*]PHP
[*]C#
[*]Ruby (on Rails)
[*]Java (for it's versatility)[/LIST]

---

### Post by thumper on 2007-03-21
I also suggest starting with python.

I wish I had known about it earlier.  I've been using python for around six years now and it really is great.  Most of that was part time along side my primary language at the time which was Java and C++.

I have been doing python full time for the last year, and I don't really miss C++ like I did when I was doing Java.

---

### Post by Wybiral on 2007-03-21
Python, C++, then C...

OR, whatever language you want!

---

### Post by raja on 2007-03-21
Python any day !

---

### Post by ronald_stall on 2007-03-21
Ok, ok I get it. It seems Python is well liked. How about resources? Thanks guys

---

### Post by pmasiar on 2007-03-21
> **ronald_stall said:**
>  How about resources? 

[http://learnpython.pbwiki.com/HowToStart](http://learnpython.pbwiki.com/HowToStart), also see sticky for this forum

---

### Post by thumper on 2007-03-21
[www.python.org](www.python.org) is the central place for all things pythonic.

I installed the python docs and refer to those through a bookmark.  They are very good.

---

### Post by raja on 2007-03-22
I find [this]("http://rgruet.free.fr/PQR24/PQR2.4.html") very handy as a quick reference.

---

### Post by Frosty Cold Drink on 2007-03-22
Python is good when you want to start programming. C is good when you want to start programming well.

---

### Post by pmasiar on 2007-03-22
> **Frosty Cold Drink said:**
> Python is good when you want to start programming. C is good when you want to start programming well.

I agree with first sentence, but how you define "well" in the second? Is raw speed overhelming criteria for "well"? I know many situation where Python is "good enough" solution, is good enough "well"? If not, why not?

---

### Post by Frosty Cold Drink on 2007-03-22
> **pmasiar said:**
> I agree with first sentence, but how you define "well" in the second? Is raw speed overhelming criteria for "well"? I know many situation where Python is "good enough" solution, is good enough "well"? If not, why not?

First, Python is great, and I won't knock it.

People who only know dynamically typed, forgiving languages *can* be excellent programmers, but I find that nothing compares to having to do the ugly stuff yourself.

When you have to manage your memory the hard way on your own, and deal with fun things like data structures without the aid of built-in hash tables and collections, casting, buffer fun, and other issues that newer lanaguages do for you, one tends to understand what is happening in the background elsewhere. The more you understand what is going on, the better you can exploit that. Spoiled programmers have a hard time becoming great, IMO.

Of course, assemly programmers think C programmers are spoiled too.

---

### Post by hanzz on 2007-03-22
Am I wrong when making the distinction that Python is rather a scripting than a programming language?

Anyway - I have been working with Java for the last 6-7 years and still loving it. One major advantage you shouldn't forget is its platform independency!

At least the new Java 5 release made a lot of things easier. You could try to jumpstart development with Java on Ubuntu by installation the java and netbeans IDE or eclipse packages.

hanzz

---

### Post by hod139 on 2007-03-22
> **hanzz said:**
> Am I wrong when making the distinction that Python is rather a scripting than a programming language?

Yes, you would be wrong.

> 
Anyway - I have been working with Java for the last 6-7 years and still loving it. One major advantage you shouldn't forget is its platform independency!

Only on platforms with a JVM.

> 
At least the new Java 5 release made a lot of things easier. You could try to jumpstart development with Java on Ubuntu by installation the java and netbeans IDE or eclipse packages.

The new Java release is [Java 6]("http://java.sun.com/javase/6/"), not Java 5.

---

### Post by Frosty Cold Drink on 2007-03-22
> **hanzz said:**
> Am I wrong when making the distinction that Python is rather a scripting than a programming language?

Anyway - I have been working with Java for the last 6-7 years and still loving it. One major advantage you shouldn't forget is its platform independency!

At least the new Java 5 release made a lot of things easier. You could try to jumpstart development with Java on Ubuntu by installation the java and netbeans IDE or eclipse packages.

hanzz

Programming language vs scripting is largely a semantic debate these days, and an unimportant one. Both are going to typically require run-times (consider MSVCRT, or even libc (yes I know I know)), both will be compiled, both can be run on multiple platforms (if you do things the right way, and/or use a cross-platform GUI toolkit).

---

### Post by pmasiar on 2007-03-22
> **hanzz said:**
> Am I wrong when making the distinction that Python is rather a scripting than a programming language?

I am wrong when i assume that java is the only language you know? :-)  (as I did even before reading rest of your post)? 

How you distinguish "scripting" from "programming"? Is a language used to write a commercial game (like [galcon](http://www.imitationpickles.org/galcon/index.html) ) still scripting? Why "scripting" is bad? Where you paint the line? FYI Python is compiled to bytecode and can be compiled further to binaries.

> Anyway - I have been working with Java for the last 6-7 years and still loving it. One major advantage you shouldn't forget is its platform independency!

I am forced (in work) to move to java after happily programming for 6 years in Perl and then Python, and it is *very* painfull to *me*. IMHO Java is too independent - uses own java-only solutions where existing and better solutions are available. Don't get me started with java's insistence on own terminology influenced by needs of marketing and not by technological issues - only MS world is worse. Also, some people do have problems with different quirks of different JVM (especially on embedded platforms) - and Perl/python is rather platform independent too. About as independent as java.

> At least the new Java 5 release made a lot of things easier. You could try to jumpstart development with Java on Ubuntu by installation the java and netbeans IDE or eclipse packages.

IMHO Java's generics is admission that dynamic typing and late binding is a good thing which was lacking in java - but if you want them, you may IMHO as well write code in Python and abandon ie. java's static exceptions and other quirks. :-)

Only after you know and used more languages, you can distinguish what part of your thinking about programming  is language dependent: like if something is hard to do or impossible in some language, and you know only that one, you do not appreciate other languages where that thing is possible, because your thinking  does not need it and you do not miss it. But even if learning a new language is not hard, becoming experienced programmer in it, knowing idioms and expertly using them is hard (takes couple years unless you are a genius).

When advocating a language, I always ask: language best for what task?

---

### Post by hanzz on 2007-03-22
> **hod139 said:**
> Yes, you would be wrong.
ok, my fault.

> **hod139 said:**
> 
Only on platforms with a JVM.

Oh thank you for that, obviously I forgot about that fact.

> **hod139 said:**
> 
The new Java release is [Java 6]("http://java.sun.com/javase/6/"), not Java 5.

I'd say that Java 5 is not to be mentioned as "old" release yet. Btw most of the "ease of development" stuff was introduced in Java 5, not 6. That's why I referred to 5.

---

### Post by hod139 on 2007-03-22
> **hanzz said:**
> 
I'd say that Java 5 is not to be mentioned as "old" release yet. Btw most of the "ease of development" stuff was introduced in Java 5, not 6. That's why I referred to 5.
True, I see how I mis-interpreted your sentence.

---

### Post by Ubuntist on 2007-03-23
> **ronald_stall said:**
> I want to get back into programming, I never really got into it heavy but did some light programming years ago with VB, basic, and perl. 

Not sure what I want to do yet but I want to get into learning what is new out there. Any suggestions?

Exactly the situation I was in a few months ago.  I used to program a lot in FORTRAN and wanted to find out what better ways of programming had appeared since then.

The answer probably depends on whether you are programming because you're interested in computers themselves or because you want to use computers predict the stock market or design spacecraft or something like that.

If it's computers themselves that you're interested in, I would guess that Java, C++ and, for anyone using Ubuntu, Python are good candidates.  They seem to be the languages used an all kinds of systems programming.

On the other hand, although I find computers interesting in their own right, most of my programming isn't about computers.  I want to analyze data; I don't particularly want to learn how to allocate memory with maximum efficiency.  So I had a look at the languages available and decided to investigate Python, Ruby, Scheme and Common Lisp closely.

If you want to stretch your brain out and really see programming from a new angle, try Scheme.  It is beautiful and powerful, and the free on-line textbook, [*Structure and Interpretation of Computer Programs*]("http://mitpress.mit.edu/sicp/full-text/book/book.html")*,* is great.  In a typical introductory programming book, by the end you'll be writing code to manipulate databases or something mundane like that.  At the end of *SICP,* you're writing a compiler.  That tells you something about the quality of the book and the power of the language.  I wish I'd learned Scheme as a first programming language.

The trouble with standard Scheme is that it's more of a theoretician's language.  For example, you can do object-oriented programming in either the message-passing or generic-function paradigms, but in either case you  have to roll your own implementation.  Still, it's great fun and a real mind-opener.

Python is nice, but IMHO it's a lot more like computer programming as you used to know it.  Having to type all those underscores drives me slightly up the wall.  It is a good language, though, and it is well supported by libraries and so on.

IMHO Ruby, though having much in common with Python, is more innovative.  Python seems to be based, at its core, on the imperative programming languages that were around in the 1980s.  Ruby, in contrast, was born in the object-oriented 1990s and borrows from diverse sources, including Smalltalk and Lisp.  I prefer Ruby to Python for its flexibility, although I can imagine that for large, formal projects Python's broader support and greater maturity make it a winner over Ruby.

I'm still getting to grips with Common Lisp.  I'm a bit put off by the historical baggage it carries, but it is definitely an industrial-strength language with lots of power and flexibility.  For the time being I've not adopted it as my major idiom, but I'm still looking into it and expect that over the next year I may transition to it.

---

### Post by Mathiasdm on 2007-03-23
> **pmasiar said:**
> I agree with first sentence, but how you define "well" in the second? Is raw speed overhelming criteria for "well"? I know many situation where Python is "good enough" solution, is good enough "well"? If not, why not?
C allows you (or even forces you) to take care of memory yourself, and learns you not to waste memory, code...
Same thing with Assembly, though I wouldn't advise that language unless you want to go REALLY low-level. It can be pretty fun though: trying to get execution time from 2 seconds to 1.2 seconds by hand-optimising is highly interesting!

To be honest, I think any language is good to get started (my first experience was with Java), but it's very interesting to understand the underlying ideas.

---

### Post by pmasiar on 2007-03-23
I agree with you 90%, but...

> **Mathiasdm said:**
> C allows you (or even forces you) to take care of memory yourself, and learns you not to waste memory, code...

C does not waste memory (and CPU cycles), sure yes. As everything in life, it comes with price: it takes long time to make C code work. Python does not waste your (developer's) time.

Python allows many people (who are not deeply interested in optimizing program usage of memory and CPU cycles) to solve real-life problems. You as developer as just making **different compromises**. You pay CPU cycles to save your own time. In some situations it is good trade, in others (like kernel) it is not, and it makes sense to optimize for CPU cycles. There is no silver bullet.

> To be honest, I think any language is good to get started (my first experience was with Java), but it's very interesting to understand the underlying ideas.

Any language is good to get started, but not all languages are equally suited to get you started. It also depends if you have someone around to help you (like teacher in your case I assume).

I read article at Salon [Why Johnny can't code](http://www.salon.com/tech/feature/2006/09/14/basic/index_np.html) (sorry you need to click through ad to access it). Author complains: "BASIC used to be on every computer a child touched -- but today there's no easy way for kids to get hooked on programming. ". Because Java or C# is not as easy to start hacking it as it was ROM BASIC 25 years ago. BTW author ended up buing for his son old Atari or something on eBay.

I have no problem with people using C or Java. Everyone has different priorities and needs - optimizing CPU and memory might be what you love to do, or your app requires, but  it is not the only measure of "good". **Speed to market** is another, extremely important measure, even (and especially) in for-profit applications.

---

