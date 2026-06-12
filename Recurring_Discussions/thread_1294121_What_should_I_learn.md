---
title: "What should I learn?"
date: 2009-10-17
forum: Recurring Discussions
---

### Post by Devon64327 on 2009-10-17
Should I learn C or Python first?

---

### Post by dominiquec on 2009-10-17
If you're a first-time programmer, I'd say go for Python: lightweight, easier learning curve, less setup and overhead necessary.  

You should also consider getting a friendly IDE to ease you into the process.  Geany is a good candidate.

---

### Post by houbysoft.xf.cz on 2009-10-17
C : harder to learn than Python but it is more powerful and faster than Python since it's compiled and low-level compared to python and therefore you'll understand how the computer works more than if you only learn Python.

Python : very easy to learn but slower since it's interpreted, also higher level so you learn less about the internals of for example how memory works etc.

Good luck

---

### Post by Devon64327 on 2009-10-17
alright... 
where can i grab Geany?

---

### Post by houbysoft.xf.cz on 2009-10-17
```

sudo apt-get install geany

```

---

### Post by dominiquec on 2009-10-17
It's available in the repositories.  From the terminal:

sudo apt-get install geany

---

### Post by Devon64327 on 2009-10-17
Cool thank you.

---

### Post by Simian Man on 2009-10-17
> **houbysoft.xf.cz said:**
> C : harder to learn than Python but it is more powerful and faster than Python since it's compiled and low-level compared to python and therefore you'll understand how the computer works more than if you only learn Python.

Python : very easy to learn but slower since it's interpreted, also higher level so you learn less about the internals of for example how memory works etc.

Choosing C over Python because you want to learn about how computers work is like choosing to live in New York over Chicago because it's closer to London.

For a beginning programmer, there is no reason to choose C at all.  And I know C better than any other language and work with it every day :).

---

### Post by vipulkelkar on 2009-10-17
Even ERIC is a good IDE for python..
try it

sudo apt-get install eric

good luck

---

### Post by matthew.ball on 2009-10-18
> **Simian Man said:**
> Choosing C over Python because you want to learn about how computers work is like choosing to live in New York over Chicago because it's closer to London.

For a beginning programmer, there is no reason to choose C at all.  And I know C better than any other language and work with it every day :).
C is pretty good because it's still fairly low-level, you learn to appreciate abstraction more, it teaches you a valuable concept (memory management) perhaps it's not so important, but it's an interesting area which comes up a fair bit in programming.

I didn't learn C first, but I wish I did. Most other languages essentially build off C, and clean up the murky parts which people may have found confusing. It's a small language so it's fairly easy to recognise the syntax (which is then employed in your next language [more than likely...]), it might take a little bit longer to fully appreciate C, but it's going to help ten fold in the next endeavour.

I also recommend using a [basic] text-editor and a command-line compiler to start off with, after a while you'll learn what's going on; it makes an IDE that much more attractive.

---

### Post by nvteighen on 2009-10-18
> **matthew.ball said:**
> C is pretty good because it's still fairly low-level, you learn to appreciate abstraction more, it teaches you a valuable concept (memory management) perhaps it's not so important, but it's an interesting area which comes up a fair bit in programming.

Hm... I think that depends more on what kind of learning guide you're using... You can learn to appreciate abstraction with any language or with none. C forces you to abstract and if you pretend to be a competent programmer, you need to know how to abstract things. But, along with C, other languages also forces you to abstract and they're not precisely low-level languages: Scheme, for example, is a high-level language but its minimalist philosophy makes you implement things on your own.

The "issue" with Python is that its basic constructs are so good and well planned that make it unnecessary to start with abstraction... In some way, it's a good idea because it makes you first learn the very basic constructs (loops, lists, conditionals, etc.) without making you immediately implement something without any programming knowledge... On the other hand, I do recognize that it confuses the beginner when suddenly he needs to take off after all the time just dealing with built-in data structures... And then, the doubts on OOP and bad interface design habits pop up in these forums...

That's why I'm seriously considering that, maybe, Scheme (with SICP as tutorial) should be more recommended...

> 
I didn't learn C first, but I wish I did. Most other languages essentially build off C, and clean up the murky parts which people may have found confusing. It's a small language so it's fairly easy to recognise the syntax (which is then employed in your next language [more than likely...]), it might take a little bit longer to fully appreciate C, but it's going to help ten fold in the next endeavour.


The syntax issue is more about familiarity than anything else. I don't see syntax as a major obstacle in learning a programming language. Familiarity may help, but it also may be counterproductive... where you expected X because the "parent" language does it, you may get Y. That's what usually happens in Perl with people coming from C-like languages.

---

### Post by steeleyuk on 2009-10-18
C or Python is a good start. They both have their benefits and drawbacks (I recommend Python but have a look at the tutorials for both and see which suits you).

One thing I would say is don't learn C because its 'faster'. The speed gains from compiled vs interpreted at this point are irrelevant and in most cases Python can be as fast as C. Learning the skills that can be transferred to other languages are whats important.

---

### Post by diafanos on 2009-10-18
I'm programming in Java for several years, and the last few days i came across with a python book, so I decided to give it a shot.

What really annoys me in python, is first that you don't have to define your variables and second is a dynamically typed language.

I know that for an experienced python programmer these two aspects of the language may be considered as merits of it, but a newbie programmer may have to spend a vast amount of time trying to find out why his program fails, only to find out later that he has just misspelled a variable's name.

My suggestion is to start with C (or java ;)) which will help you also grab the idea of programming in a better way, as python hides a lot of things that a new programmer should learn.

---

### Post by CptPicard on 2009-10-18
I'll just refer to the venerable megathread again..

[http://ubuntuforums.org/showthread.php?t=851794](http://ubuntuforums.org/showthread.php?t=851794)

The syntactic similarities between Algol-derivative languages really are a totally superficial matter and I would be surprised if anyone was actually "helped" in any meaningful way by the familiarity gained from C -- that stuff is close to trivial and the same familiarity is gained from any other language in the same family, which will then help learning C completely analogously.

While I am not a huge Java/C#-fanboi myself, I could for example make a claim that Java teaches you essentially C, plus typical static-typed OOP approach in an approachable package, which you can then emulate in your structs-and-function-pointers C. The issue with pointers and memory management is blown out of proportion as far its significance goes... the former are merely a typed indirect reference value, the latter is your regular resource management problem, which unfortunately gets early on in the way of a beginning programmer, RAM being such a common resource to be handled...

---

### Post by Simian Man on 2009-10-18
[QUOTE=matthew.ball]C is pretty good because it's still fairly low-level, you learn to appreciate abstraction more, it teaches you a valuable concept (memory management) perhaps it's not so important, but it's an interesting area which comes up a fair bit in programming.[/quote]
If you're designing a program of any complexity, with any language, you will *need* to abstract.  It's just that the phrase "of any complexity" has different meanings between C and Python.  In C a complex program is anything more than "guess the number" whereas in Python, complex programs tend to be more interesting.

[QUOTE=matthew.ball]I didn't learn C first, but I wish I did. Most other languages essentially build off C, and clean up the murky parts which people may have found confusing. It's a small language so it's fairly easy to recognise the syntax (which is then employed in your next language [more than likely...]), it might take a little bit longer to fully appreciate C, but it's going to help ten fold in the next endeavour.[/quote]
Learning syntax is the easiest part of learning a language.  Sure if you want to learn C++, C#, or Java knowing C will help, but it will still be faster to just learn the language you want to learn and start writing useful programs.

[QUOTE=matthew.ball]I also recommend using a [basic] text-editor and a command-line compiler to start off with, after a while you'll learn what's going on; it makes an IDE that much more attractive.[/QUOTE]
I agree with you there.

---

### Post by Devon64327 on 2009-10-18
0.0 
Uhh... I respect everyones opinions and I've decided on Python since I figured my school offers courses in C++(I don't know why) after i finish VB, advanced VB, Java, Advanced Java, then C++, and I THINK PERL.
Figure I'll just let a teacher show me right to my face.
Thank you for your help.

---

### Post by Can+~ on 2009-10-18
> **Devon64327 said:**
> 0.0 
Uhh... I respect everyones opinions and I've decided on Python...

It's just another day on the ubuntuforums:

1. OP: What should I learn?
2. High level: Because that's how you solve real problems, and not machine problems.
3. Low level: Learn how computers work, pointers durr, powerful!

:KS

---

### Post by nvteighen on 2009-10-18
> **Can+~ said:**
> It's just another day on the ubuntuforums:

1. OP: What should I learn?
2. High level: Because that's how you solve real problems, and not machine problems.
3. Low level: Learn how computers work, pointers durr, powerful!

:KS

You forgot:
4. Thread closed because of flamewar.

---

### Post by CptPicard on 2009-10-18
Meh, it's been totally boring in that regard for a long time now... either the warriors have left or are banned, and those who are left know how it goes already and can always refer to the megathread instead of retyping the whole thing ;)

---

### Post by ajackson on 2009-10-18
> **CptPicard said:**
> can always refer to the megathread instead of retyping the whole thing ;)
Ah but a "real"TM poster wouldn't use a third party thread and create their own. Swap the words poster and thread with programmer and library - I'm sure regular viewers can remember some of the threads (normally all in recurring discussions now) about such "issues".

Back OT - python gives you a good base to build on, the key to being a successful programmer is getting the right tool (language) for the task in hand.

---

### Post by ApEkV2 on 2009-10-18
> **nvteighen said:**
> You forgot:
4. Thread closed because of flamewar.

And.....
5. C is for cookie


If you go with C, here are some good books.
[http://www.borders.com/online/store/TitleDetail?sku=0131103628](http://www.borders.com/online/store/TitleDetail?sku=0131103628)
[http://www.borders.com/online/store/TitleDetail?sku=0596006977](http://www.borders.com/online/store/TitleDetail?sku=0596006977)

---

### Post by slavik on 2009-10-18
Moving to recurring discussions

---

