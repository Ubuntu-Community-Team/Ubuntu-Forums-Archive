---
title: "Hackers and Common Lisp"
date: 2009-06-17
forum: Programming Talk
---

### Post by sam191 on 2009-06-17
Hey,

I was wondering how many of you guys use Common Lisp, or any dialect of Lisp for that matter? 

I have just read the book, "Hackers and Painters" by Paul Graham, and he made some really interesting points about programming languages. What I think he said was that Lisp is the most powerful language, and that new programming languages are getting closer and closer to Lisp. 

This book really got me thinking. What do hackers (not crackers) use as their tools? I have read they often choose languages like Perl/Python/Ruby and Linux as their main OS.

I have been using windows for the past 9 years (I'm still in high school)  and when I was young I used to think that "windows + C++ = hacker" :D. Now, I am slowly switching over to Ubuntu. And I really like to work in Python.

What do you guys think about the book and Graham's ideas? What languages and operating systems do you like to work with and why?

---

### Post by CptPicard on 2009-06-17
It is late here so this post will be shorter than it probably should be...

First of all, this is going to touch off on some long-running "intense discussions" we have had on this forum regarding high and low-level languages and their relative "power"... search for the "high vs. low-level megathread" for example.

IMO a hacker is a person who likes to understand how things work and play with things. Linux, because of its openness, is a natural good fit for your typical computer hacker.

When it comes to programming... I can certainly see the value in knowing how to work close to the hardware if need be, but personally I am much more interested in "hacking" not so much with the computer per se, but with the problems I am solving. For this kind of stuff higher-level languages can be very useful and sometimes even provide insight to what you're working with...

The reason why Lisp is great is that it combines two things -- it is fundamentally very *simple* (there is not all that much *technical detail* to master -- in particular the syntax of a simple lisp like Scheme is near trivial) yet the pieces it is made of can be combined in various ways to pretty much create anything, producing a lot of conceptual richness. That is, Lisp has all you need and nothing more. Most other programming languages end up feeling like specialized syntactic sugar on top of stuff you could fairly straightforwardly implement in Lisp, after you get into it...

---

### Post by sam191 on 2009-06-17
I know what you mean. I think it is necessary for a hacker to have knowledge of lower level languages and such, but when it comes to software the users don't see the code. All they care about is if they like it and if it works well. (Excluding open source projects, of course) 

The reason I asked about the book is that while everyone else is saying, it doesn't matter, or all languages are the same. Graham has very strong opinions and believes that programming languages do matter and that one is better than the other. I have never encountered these ideas before, and that is why they stuck with me.

---

### Post by Can+~ on 2009-06-17
> **sam191 said:**
> I know what you mean. I think it is necessary for a hacker to have knowledge of lower level languages and such, but when it comes to software the users don't see the code.

That does not only apply to computer languages, it applies to almost every field that human develops into.

This is known as the holistic viewpoint, in which you not only understand how a system can be used, but also know how it works internally, it's a deeper level of understanding that improves how you understand things externally.

For example, I used to be very careless when disconnecting pen drives, because I didn't understand what was the difference between unplugging them "safely". When I first learned C, and discovered that a file is not necessary written immediately (fclose() experiences), but sometimes stored in a cache waiting the processor to be free and write the file.

However, going back to the original topic: I don't think that the language actually matters when it comes to solve a problem, just when it's time to implement it. When you learn languages, you're not just learning it's syntax, but you're also learning it's Paradigm. 

Paradigms are mostly overlooked by new programmers, but you'll learn that each paradigm offers a different viewpoint about the same subject and offering new ways to solve the same problem. Learning new paradigms trains your brain in solving problems different ways, in other words, you're teaching yourself how to think.

Some languages (C for example) are very limited, but you feel that this limitation means that you're reusing the same structures over and over again. I think people love LISP by similar reasons, plus it's a dozen steps higher on the abstraction scale (from C). I also love python for the same reasons, a string can be chopped and inverted just playing with the [start:end:step] operator.

On the other hand, you got those languages that try to invent the solution to every possible problem, which is not a bad approach, but it becomes restrictive when you have to dip into documentation so frequently that you spend 55% looking at docs and 40% actually programming (the other 5% is spent cursing why it doesn't f***ing work).

(I think I went overboard with the answer, but I have a lot going through my mind lately)

---

### Post by monraaf on 2009-06-17
> **sam191 said:**
> The reason I asked about the book is that while everyone else is saying, it doesn't matter, or all languages are the same. Graham has very strong opinions and believes that programming languages do matter and that one is better than the other.

That's like saying that a hammer is better than a screwdriver. You just pick the right tool for the right job. I'm sure that Common Lisp is a great language and has it's own niche, but I'm also pretty sure that Python blows it away when it comes to the amount of libraries that are available to the programmer.

---

### Post by CptPicard on 2009-06-17
> **sam191 said:**
> I think it is necessary for a hacker to have knowledge of lower level languages and such, but when it comes to software the users don't see the code.

It's not just the end user perspective, it's also the "how it feels like to work in some language" issue from the developer's point of view. Believe it or not, different languages make you think differently about things. Some people would disagree, but I usually get the impression that they are the types who never really did much outside of some C-derivative language.

As Eric Raymond says, Lisp is worth learning just because it makes you a better programmer for the rest of your days even if you did not use it much... it is about "exposure" to different "views" to how some program would be constructed.

It is very instructive to consider that all the brightest, most insightful hackers I know are Lispers first and foremost -- and can handle pretty much anything at ease too, mind you...

> 
The reason I asked about the book is that while everyone else is saying, it doesn't matter, or all languages are the same. Graham has very strong opinions and believes that programming languages do matter and that one is better than the other.

Theoretically you can write an interpreter for any Turing-complete language in any other Turing-complete language. This does not however mean that coding in raw binary would be preferable to coding in a more abstract language... you can extrapolate from there :)

---

### Post by sam191 on 2009-06-17
Some really good replies! 

I used to believe that if one did not code low level, (eg C/C++) Then that meant that they were not hardcore enough, or not real hackers. Now I think the complete opposite! A hacker must use the best tool at hand, and why go low if a program does not require the efficiency? What will happen in 20 years? Will low level languages still be around? (of course they will, but will they be in practical use? Other than for legacy code.)

> 
It is very instructive to consider that all the brightest, most insightful hackers I know are Lispers first and foremost -- and can handle pretty much anything at ease too, mind you...


...Makes me wonder, are they good hackers because they use Lisp, or do they use Lisp because they are good hackers? I'm always wondering what expert hackers are using and why.

I've done some research (aka went to google) and found out about programming paradigms.Now I think it would be pointless to learn numerous programing languages of the same paradigm all at once, so I would like to learn a language from each paradigm (too ambitious?) to get my brain running. What are some useful languages of different paradigms?

---

### Post by jpkotta on 2009-06-17
I don't know too many languages myself, but I would recommend at least 3 broad classes to learn to get started.  Low level languages like C or C++, higher level languages like Perl or Python or Octave/Matlab, and functional style languages like Haskell or Mathematica.  The main thing is to learn several different languages *thoroughly*, i.e. well enough to appreciate the differences.

---

### Post by CptPicard on 2009-06-18
> **sam191 said:**
> 
I used to believe that if one did not code low level, (eg C/C++) Then that meant that they were not hardcore enough, or not real hackers.

Don't worry, that fixation on the machine level view is rather common. I frankly find it a little bit intellectually dull... bit pushing is bit pushing, no matter how high you pile it ;)

> 
 Now I think the complete opposite! A hacker must use the best tool at hand, and why go low if a program does not require the efficiency?

And, one should also understand what concepts have been introduced in other languages and why. There is often more thought there than immediately meets the eye. For example I didn't quite "get" Python's pervasive "genericness" for a while; but it's actually very elegant...

> 
 What will happen in 20 years? Will low level languages still be around? (of course they will, but will they be in practical use? Other than for legacy code.)

The very low machine level languages won't go anywhere, but those have been meant to be written by compilers anyway. Virtual machines and operating systems will probably converge somehow.

As an interesting aside, did you know that Lisp, originally invented in 1958, actually had hardware back in the day that actually ran Lisp? It's been all downhill from there...

> 
...Makes me wonder, are they good hackers because they use Lisp, or do they use Lisp because they are good hackers? I'm always wondering what expert hackers are using and why.

Both. They have the good sense to understand that life is short and you want to be using the most flexible tool available to you, and they have become good hackers because they actually understand what kind of building blocks fundamentally matter in a programming language, and how one puts them together... 

> Now I think it would be pointless to learn numerous programing languages of the same paradigm all at once, so I would like to learn a language from each paradigm (too ambitious?) to get my brain running.

Good idea. You want to learn languages that are different enough so that you get a broad exposure to different ideas... in particular syntactic details, differences and such as rather uninteresting. 

> 
 What are some useful languages of different paradigms?


Python to start with -- duck typing, genericness, generally great language to get your first exposure. Ruby might be an alternative, but it's way more OOP-obsessed :)

C - small, low-level procedural, exposes some of the machine, not particularly interesting on the "big ideas" front otherwise
 -> as an aside, you may want to consider taking a peek at what C compiles into, the assembler

Either Java, C# or C++ for typical static-typed OOP-language. C++ is a fairly big beast to master, I wouldn't suggest it but it nevertheless is in the same camp

Scheme for a lisp -- it's more "educational" than Common Lisp. Also lets you play with functional programming although Lisp definitely is "multiparadigm"... for a "hardcore" functional-programming language, see Haskell, it's quite popular in some quarters these days

For something completely different, try Prolog for logic programming, or Forth for a combination of high and low level approaches.

---

### Post by jacksaff on 2009-06-18
> **Can+~ said:**
> 
Some languages (C for example) are very limited, but you feel that this limitation means that you're reusing the same structures over and over again. I think people love LISP by similar reasons, ***plus it's a dozen steps higher on the abstraction scale (from C)***. I also love python for the same reasons, a string can be chopped and inverted just playing with the [start:end:step] operator.


I think the key to lisp isn't that it's high level, but that it's the same at every level. Whatever level of abstraction you are using in lisp, the code always looks the same. 

You want to push a number around in memory you write a list with a command and a bunch of data. You want to strip some info out of a gui widget, use it to muck around with a database, get some result that you use to draw some 3d thing somewhere and play a mooing sound, you write a list, with a command and a bunch of data. A lot more might happen when the list is evaluated, but the code is much the same. 

You could write very low level code in lisp if you wanted to, but with such simple syntax you don't need to learn much to do abstract away the repetitive low-level stuff, so why would you? Going the other way, your high level lisp program gets broken down into much simpler bits (which use exactly the same syntax) when run, and you can tinker with that if you want aswell. 

And if you don't like the syntax or it's not convenient for the job at hand, you can write macros that change it to whatever it is you want.

---

### Post by sam191 on 2009-06-18
> **CptPicard said:**
> 

Python to start with -- duck typing, genericness, generally great language to get your first exposure. Ruby might be an alternative, but it's way more OOP-obsessed :)

C - small, low-level procedural, exposes some of the machine, not particularly interesting on the "big ideas" front otherwise
 -> as an aside, you may want to consider taking a peek at what C compiles into, the assembler

Either Java, C# or C++ for typical static-typed OOP-language. C++ is a fairly big beast to master, I wouldn't suggest it but it nevertheless is in the same camp

Scheme for a lisp -- it's more "educational" than Common Lisp. Also lets you play with functional programming although Lisp definitely is "multiparadigm"... for a "hardcore" functional-programming language, see Haskell, it's quite popular in some quarters these days

For something completely different, try Prolog for logic programming, or Forth for a combination of high and low level approaches.

This is exactly what I was looking for. Thank you so much! Since the university uses C, C++ and Java, I will have to learn those. I wish I could go to MIT, where they teach Python -> Scheme. I might even meet some hackers there... sigh, oh well.  

One thing I am wondering about is, how did Graham make web apps with Lisp? I know you have to have a framework to work with, eg Django, ruby on rails, etc. Is there another way to do this?

This might be a dumb question because I'm not familiar with web development at all, but does this mean that any language can be used for web development?

---

### Post by CptPicard on 2009-06-18
"Web frameworks" are just sort of "libraries" of web application related code and tools, you don't necessarily "need" one, but of course generally you'll prefer one, as web apps can be messy things without.

Yes, you can technically write web apps in any language as long as you can hook it up to a web server... you can even write your own web server as long as you have a socket interface. Google for "SymbolicWeb" for a Common Lisp web framework project by one of my favourite Lisp gurus...

---

### Post by CptPicard on 2009-06-18
> **jacksaff said:**
> I think the key to lisp isn't that it's high level, but that it's the same at every level. Whatever level of abstraction you are using in lisp, the code always looks the same. 

Yes, consistency is one of the strongest points of the language... and particularly the fact that [Lisp code is Lisp data]("http://en.wikipedia.org/wiki/Homoiconicity").

You can still move rather freely between highly abstract and rather down to the hardware and still remain the model... with SBCL you can tune the generated assembly by just writing more imperative code, for example...

---

### Post by nvteighen on 2009-06-18
The issue is that programming languages are artificial languages and as such, they are designed to fulfill some specific purpose. If two artificial languages share the same purpose, then you can compare them and judge which fulfills it better. That's why you can compare programming languages, though always with respect to some task.

As programming languages are designed to fit some task, their **semantic** system is biased towards its desired task(s). So, when working **in** a certain programming language, you agree to work inside a certain semantic system and to model some reality using that particular way to "see the world" that language has.

That's why programming languages do condition the way we think. In natural languages, this a bit discussed, as they lack that "design principle"... The goal of natural languages is to communicate realities by abstracting them into concepts... but by experience, all natural languages fulfill that task perfectly.

---

### Post by Nemooo on 2009-06-18
I'd definately recommend Lisp, though go with Scheme at first. I tried starting out with Common Lisp along with [Practical Common Lisp]("http://gigamonkeys.com/book/"), and it was too much format syntax for my head combined with learning something very different from my first programming language, C.

Since then I tried [Arc]("http://arclanguage.org/"), by going through the tutorial. While it was much more pleasant and intuitive than CL, I didn't really use the language to its fullest, because I was still influenced by C and stuck in my imperative mindset. The real eye opener for me was [SICP]("http://mitpress.mit.edu/sicp/"), which introduced a more functional approach. Unlike Practical CL it doesn't seek to be practical, but is more theoretically focused, which was what I was seeking. And discovering the "purity" of functional programming and just being at a higher level was a huge advantage, because I felt that I was focusing more on the problem and less on the implementation and the language.

Now when I occasionally program in C, I always find myself thinking how much easier it would've been in Lisp and how much I miss lists.

---

### Post by nvteighen on 2009-06-18
> **Nemooo said:**
> 
Now when I occasionally program in C, I always find myself thinking how much easier it would've been in Lisp and how much I miss lists.

Me too... and not only in C, but in Python too :p

For that reason, even though it has been much more difficult and it's still in a very pre-alpha state, I'm fonder of my FreeTruco Scheme project than anything else :)

---

### Post by sam191 on 2009-06-18
Looks like I have a long way to go! So many new things to explore and I am really interested in learning Lisp now after reading about it.

---

### Post by fr4nko on 2009-06-18
> **sam191 said:**
> I was wondering how many of you guys use Common Lisp, or any dialect of Lisp for that matter?
I was tempted to learn lisp of schema in the past but I never really get into this business. Looking at that backward I don't have any regret. While common lisp or scheme can be used as an embedded programming language - most popular examples are emacs and jed - there are no modern successful project that use lisp as far as I know. I've seen also un unsuccessful office suite that was using lisp as scripting language. At the opposite side python and [lua]("http://www.lua.org") are gaining more and more popularity like embedded or stand-alone scripting language and many programs now have bindings for python.

We can ask what is the reason of the decline of lisp since it is a really powerful programming language. I think one of the main reason is the awful syntax with tons of parenthesis that make it difficult to read for most 'normal' people. It seems to me that lisp is mostly a write-only programming language because of the difficult to read and easily understand the code. In the other side python comes with a clear excellent syntax and is almost as powerful as lisp, I believe.

Of course lisp has many appealing, powerful concepts like functional programming (closures) and high-level commodities like lists and similar high-level structures. Other kind of high-level interpreted languages now provides the same kind of functionalities with much more clear syntax. There are also some very powerful pure functional programming languages with some excellent implementations like OCaml and Haskell. Personally I love ocaml, I think that all the other existing languages are far behind it. If you try to program in ocaml the compiler will catch ***all*** your programming errors thanks to the powerful typing systems. Once your program compiles all the errors that remains are simply errors in the logic of you program. So you get rid of all the sort of stupid low level errors, like side effects, buffer overflows, "tuple expected got string" and things like that. Also ocaml can compile your code in machine code that run almost as fast as C.

So, I don't use lisp and I don't regret it, I prefer to use other programming languages :-)

Francesco

---

### Post by arcdrag on 2009-06-19
> **sam191 said:**
> Looks like I have a long way to go! So many new things to explore and I am really interested in learning Lisp now after reading about it.

That feeling will go away shortly after you start working with it.  Then you'll start having nightmares where all you see is ((((()))((())))))))))))(((()))))))))))))))))()()())))))))(((((((((((((())))))))))))))(((((((((((()))))))()()())))))))))()))))))))))

Lisp can solve some pretty intense problems with only a few lines of code...but sometimes it can take quite a long time to get a single line of code working as intended with it...especially when you're just learning.

---

### Post by nmaster on 2009-06-19
> **sam191 said:**
>  I wish I could go to MIT, where they teach Python

"Structure and Interpretation of Computer Programs" (Abelson, Sussman, and Sussman) is a very famous textbook/course that originated at MIT and that class is taught in Scheme.  Its important to realize that the idea of a CS course is not to learn a language but to learn theory.  At places like Berkeley that still use SICP as the introductory course, the focus of the curriculum is theory.  MIT has recently chosen to move to an "applications first" style of teaching that integrates some of the EE courses with CS to show students how they can actually do things.  The idea is to get students hooked so that they can then learn more theory as they go.  In some ways, its a political decision.  These teaching styles have been studied and have been shown effect when targeting certain groups that are underrepresented in engineering fields.

I personally prefer the SICP approach.  Any application that you learn about now will be outdated in a matter of years.  Theory, on the other hand, lays a good foundation so that learning applications comes naturally.

To answer the original question of the poster, I like Scheme.  Its elegant and very easy to use.  I'm doing research for a professor (in the EE division at UCB) and when I need to write something quickly to help me solve a problem, I'll often use Scheme.  Its never efficient, but I can produce things to help me and thats what matters.  Even if I optimized my code by using the appropriate data structures (I sometimes use lists so that I can car/cdr even when a vector would be better) and using better algorithms it wouldn't be as efficient as C, but for my purposes it doesn't matter.

Sorry for being longwinded, but I think its cool that people like this enjoy these discussions. :D

---

### Post by nmaster on 2009-06-19
And another thing (lol),  while LISP is not often used in industry, it is used quite a a bit in "rapid prototyping."  Writing in Lisp is very simple, so you can quickly finish a project to so a client.  You can go through several prototypes this way until the client is satisfied.  When you're finally done, you usually write the code in C to make it more efficient.

---

### Post by sujoy on 2009-06-19
and to all the people complaining about the parens and the awful syntax ...

[IMG]http://arch.har-ikkje.net/gfx/lisp.png[/IMG]

---

### Post by monraaf on 2009-06-19
Looks a lot like Script-Fu from The Gimp. Thank god there's now also Python-Fu, so us mere mortals can also script the The Gimp :D

---

### Post by sam191 on 2009-06-19
> So, I don't use lisp and I don't regret it, I prefer to use other programming languages

What you're saying might hold some truth to it, but I'm not going to dismiss a language before trying it out for myself. There must be a reason why a lot of hackers use it.

> That feeling will go away shortly after you start working with it.

Couldn't this be solved with organizing your code better? Just because languages like C don't care about white space doesn't mean that I will write everything on one line. (A little over exaggerated, but you get my point.)

> When you're finally done, you usually write the code in C to make it more efficient. 

Is Lisp really that slow? How fast is it when compared to Python? 

I understand C's efficiency when programming OS's, Game engines, and drivers. But for web apps and desktop apps, is there really that big of a difference? If so, could you give me an example of a project that would require efficient code? 

Also, why is PHP so widely used on the web when I hear it is a "broken" language to begin with? (again sorry for the dumb question, I am completely new to the web development area.)

---

### Post by sujoy on 2009-06-19
I wouldnt say PHP is broken, but it allows and doesnt mind if you break your code inside out :P its popular because it works and the barrier of entry is low, and that almost all webhosts provides PHP.

As for lisp, try stumpwm(written in CL), its the improved version of ratpoison (written in C), by the same team infact. The author felt that he was recreating lispy codes in C so instead he just moved the whole project to lisp :)

---

### Post by nvteighen on 2009-06-19
> **fr4nko said:**
> 
We can ask what is the reason of the decline of lisp since it is a really powerful programming language. I think one of the main reason is the awful syntax with tons of parenthesis that make it difficult to read for most 'normal' people. It seems to me that lisp is mostly a write-only programming language because of the difficult to read and easily understand the code. In the other side python comes with a clear excellent syntax and is almost as powerful as lisp, I believe.


No, the decline of Lisp is related to the AI-crisis in the 80s. Lisp was the language of AI... but as that crashed, anything related to AI declined including, of course, the language.

The reason why Lisp isn't used is because lots of programmers stick to the idea that programming is just a practical task related to computers and forget that it is about creating theoric models about something. If your concern is about efficiency, creating some application and such, then Lisp is useless for you; if you want to explore how to model some reality in a clean formal language, Lisp is what you want.

---

### Post by sam191 on 2009-06-19
> **nvteighen said:**
> No, the decline of Lisp is related to the AI-crisis in the 80s. Lisp was the language of AI... but as that crashed, anything related to AI declined including, of course, the language.


Makes a lot of sense. This must be why it took me a whole year to find out about Lisp. I guess I must have been looking in the wrong places. :D

I also find it interesting that no other language has this much hype (be it, hidden hype) about it. I don't know any other programming language advocate that has as strong of an opinion as Lispers do.

---

### Post by fr4nko on 2009-06-19
> **neal.m.master said:**
> To answer the original question of the poster, I like Scheme.  Its elegant and very easy to use.  I'm doing research for a professor (in the EE division at UCB) and when I need to write something quickly to help me solve a problem, I'll often use Scheme.  Its never efficient, but I can produce things to help me and thats what matters.  Even if I optimized my code by using the appropriate data structures (I sometimes use lists so that I can car/cdr even when a vector would be better) and using better algorithms it wouldn't be as efficient as C, but for my purposes it doesn't matter.
For me is very much the same thing with python - it is elegant, it helps to quicly solve complex problems but it is never especially efficient. I'm using it at work to write one-task simple applications and it works really nicely. The code is elegant and compact, easy to read and to maintain. Probably I could do the same with Scheme - is just that I never learnt lisp.

But even if I'm using python in many cases, I know that in other cases I need C/C++ because execution speed is very important for some applications. For other applications like writing a compiler, or manipulates complex structures with high-level powerful constructs my preference is for ocaml. Also ocaml is amazingly good for the execution speed.

Sometimes people argues that nowdays execution speed is not important. I believe that this is pretty much false. What is true is that, for some kind of applications, execution speed is not important but in many domains it still important and will ever be.

Francesco

---

### Post by fr4nko on 2009-06-19
> **nvteighen said:**
> if you want to explore how to model some reality in a clean formal language, Lisp is what you want.
You are sure that you may not want Haskell or Ocaml for that ?

---

### Post by sam191 on 2009-06-19
> **fr4nko said:**
> 
Sometimes people argues that nowdays execution speed is not important. I believe that this is pretty much false. What is true is that, for some kind of applications, execution speed is not important but in many domains it still important and will ever be.


How about when development time is more crucial than runtime? When it comes to working at companies, most of the time you don't have a choice. But if you're working on a project or even a startup company, (assuming that you are not writing device drivers or kernels.), I would worry more about the product and speed of development rather than how fast my program works (assuming it's not terribly slow).

I remember reading somewhere that premature optimization is the root of all evil ;)

I will definitely agree that efficiency is required in a lot of places and I am in no way dismissing other languages, but being the curious person that I am, I always like to explore untouched area. So I will definitely have to try Ocaml as well as Haskell in the future.

---

### Post by nvteighen on 2009-06-19
> **sam191 said:**
> 
I also find it interesting that no other language has this much hype (be it, hidden hype) about it. I don't know any other programming language advocate that has as strong of an opinion as Lispers do.

Well, C and C++ advocates sometimes also have very strong opinions...

> **fr4nko said:**
> You are sure that you may not want Haskell or Ocaml for that ?

Hmm... not sure... Lisp's homiconicity gives you the power to perform symbolic manipulation with Lisp itself. With that you can model the language itself, which is also part of the reality. Haskell can't do this, so it can't model Haskell in itself... thus not being able to render some part of the reality.

And modelling the language itself gives you the opportunity to change the language according to what is needed at any time...

---

### Post by mmix on 2009-06-19
PG mentioned 5 languages at least, which positioned differently.. to me, plan9 and linux, and c and asm, oh wait there is much more. :) BTW, arc3 released.

---

### Post by siman on 2009-06-19
> **jpkotta said:**
> I would recommend at least 3 broad classes to learn to get started.  Low level languages (...), higher level languages (...), and functional style languages (...)

+1 on that.

take for example functional programming. it's very different from what you usually do in C/java. most concepts seem extremly strange, but once you grasp them, it helps you be a better programmer in the "classical" languages, since you have a broader view of what is possible.

this guy, for example, gives a very nice introduction to FP: [http://blip.tv/file/324976](http://blip.tv/file/324976)

edit: on a side note to this:

> **sam191 said:**
> Also, why is PHP so widely used on the web when I hear it is a "broken" language to begin with?

> **sujoy said:**
> I wouldnt say PHP is broken,

i would say php IS broken. in the sense that is has zero consistency (naming, parameter-order, etc). also see [http://www.bitstorm.org/edwin/en/php/](http://www.bitstorm.org/edwin/en/php/) , which has some very good points on that matter.

---

### Post by arcdrag on 2009-06-19
> **sam191 said:**
> 


Couldn't this be solved with organizing your code better? Just because languages like C don't care about white space doesn't mean that I will write everything on one line. (A little over exaggerated, but you get my point.)


Yeah, the hatred of lisp goes away as you gain skill and learn how to organize your code...but you can't deny it sucks pretty hard getting started with it.

---

### Post by curvedinfinity on 2009-06-19
I find that the language is kind of arbitrary. The majority of why I like one language over another is based on how easy the libraries of the language are to use. Generally each language has unspoken style guidelines of how a library is supposed to be structured.

Some styles are easier to use than others...

---

### Post by siman on 2009-06-19
> **curvedinfinity said:**
> I find that the language is kind of arbitrary. The majority of why I like one language over another is based on how easy the libraries of the language are to use. Generally each language has unspoken style guidelines of how a library is supposed to be structured.

Some styles are easier to use than others...

those library conventions are one thing, but they can vary within one paradigm. especially when it comes down to only using the most basic syntax the different concepts behind a paradigm shine.

take quicksort for example:

haskell
```

qsort []     = []
qsort (x:xs) = qsort (filter (< x) xs) ++ [x] ++ qsort (filter (>= x) xs)

```

javascript
```

function qsort(array, begin, end) {
  if(end-1>begin) {
    var pivot=begin+Math.floor(Math.random()*(end-begin));

    pivot=partition(array, begin, end, pivot);
    
    qsort(array, begin, pivot);
    qsort(array, pivot+1, end);
  }
}

```

differnt kind of beast :)

haskell solves the problem without ifs and never does a variable assignment. plenty of both in javascript.

---

### Post by soltanis on 2009-06-19
Just to throw in my 2 cents, I learned C first, so I am most at home with C syntax and C-similar languages.

Lisp was the first functional language that I learned, and it was a life-changing experience. It is perhaps the only language I have ever learned that intuitively expresses code. You just...think how YOU would do something, and writing it in Lisp is almost trivial. It is almost as if it is a language geared towards a human writing it -- as opposed to a language geared towards a machine running it.

---

### Post by CptPicard on 2009-06-20
Well, seriously, complaining about the Lisp parenthesis just tells me that this someone doesn't quite understand the point of why the parens are there in the first place.

The whole idea in Lisp is to express code in terms of abstract syntax trees written as Lisp list literals. It really is a beautifully elegant code-data duality that it's got going there, and leads to totally minimalist syntax. If you structure your code visually right, the parens actually almost disappear and you can just read the structure...

... which what leads to the effect soltanis is talking about in the previous post. Syntax has been abstracted away to the least minimum, and the language primitives that exist in the language are strong enough to allow for their recombination to achieve pretty much anything in conjunction with the macro compiler that can, in turn, mangle the minimalist syntax trees into any other syntax tree -- all the while using Lisp itself to do this!

---

### Post by fr4nko on 2009-06-20
> **CptPicard said:**
> Syntax has been abstracted away to the least minimum, and the language primitives that exist in the language are strong enough to allow for their recombination to achieve pretty much anything in conjunction with the macro compiler that can, in turn, mangle the minimalist syntax trees into any other syntax tree -- all the while using Lisp itself to do this!
Well, this seems to be a typical reason why lisp is appealing for academic or research community. Yet my remark was that lisp fails to be appealing in more real-world programming tasks. There is a very interesting [article]("http://www.paulgraham.com/popular.html") of Paul Graham, one of the most prominent lisp programmer, that explains very well why lisp is not popular and why he decided to start the Arc dialect of lisp. Among the weak points of lisp that he was raising:

[LIST]
[*]the lack of syntax, apart from the s-expressions expressed with parenthesis
[*]the lack of good libraries for many common real-world tasks
[/LIST]
He is also arguing that execution speed is not important but I does not agree with him, execution speed is important in many domains. I'm developing and maintaining a software that perform some complex numeric computations and I know that, while many parts of the software does not need so much speed, for the core engine execution speed is a key parameter. So I'm forced to write it in C/C++ and I've actually chosen C.

So, lisp users are saying that lisp is incredibly powerful but I'm wondering why we don't see any real-world application made in lisp and this programming language remains relegate to the academic or research community. I know a lot of programming languages that are incredibly powerful in theory but unfortunately it turns out that there is always a big gap between them and the real world so they remains in the world of theory.

Francesco

---

### Post by Reiger on 2009-06-20
> **CptPicard said:**
> Well, seriously, complaining about the Lisp parenthesis just tells me that this someone doesn't quite understand the point of why the parens are there in the first place.

The whole idea in Lisp is to express code in terms of abstract syntax trees written as Lisp list literals. It really is a beautifully elegant code-data duality that it's got going there, and leads to totally minimalist syntax. If you structure your code visually right, the parens actually almost disappear and you can just read the structure...

To add to this with a very wrong but effective comparison: think of Lisp syntax the same as you do of XML syntax. You write a document tree which so happens to contain `computable' statements, but for the purpose of writing a document tree that detail does not matter. There is no syntactic difference in writing:
```

<xsl:template match="*">
 <xsl:copy-of select="." />
</xsl:template>

```
and writing:
```

<template>
 <copy>
 </copy>
</template>

```
Or:```

<template>
 <copy></copy>
 <copy></copy>
 <copy></copy>
</template>

```

And you don't bother with contemplating removing the </template> or </copy> because they have meaning: they tell the parser where a particular sub-tree ends in the flattened representation that is the document.

Substitute with parentheses where necessary.

---

### Post by CptPicard on 2009-06-20
> **fr4nko said:**
>  Yet my remark was that lisp fails to be appealing in more real-world programming tasks.

IMO this is just a matter of "momentum". Most coders get their start in programming in your typical imperative language, and never move from there. Popularity breeds popularity you know... Lisp is a bit of a niche thing, but I always was a big fan of thinking a little bit off the beaten path -- the language needs to be considered on its merits, for what it is, instead of whether someone has used it for something.

> 
 There is a very interesting [article]("http://www.paulgraham.com/popular.html") of Paul Graham, one of the most prominent lisp programmer, that explains very well why lisp is not popular and why he decided to start the Arc dialect of lisp.

Yes, but he's still a lisper... a lisper enough to seek to improve on what is. And when it comes to the lack-of-syntax issue, at least he knows full well the reasons for the S-expression structure; I doubt he would ever actually disagree that homoiconicity is a very powerful property :)

> 
the lack of good libraries for many common real-world tasks


This is not something inherent to the language... it can be remedied by writing those libraries.

> He is also arguing that execution speed is not important but I does not agree with him, execution speed is important in many domains. I'm developing and maintaining a software that perform some complex numeric computations and I know that, while many parts of the software does not need so much speed, for the core engine execution speed is a key parameter.

Execution speed is important when it is important. I don't deny that. Actually, the SBCL compiler does an excellent job compiling highly performant code if you choose to write the speed-critical parts in a more imperative manner, with appropriate type declarations, and avoid consing like crazy.

Personally when considering the "philosophy" of programming languages, that is, how they choose to do things and how you make use of them etc., I prefer not to introduce the execution speed variable into the equation simply because if the "sometimes you need the speed" was an overriding concern, we'd write everything in C.

---

### Post by hessiess on 2009-06-20
Personally I find Lisp to be a beautiful language due to its extremely simple and consistent syntax and the speed which applications can be developed. Though I also find it to be of somewhat limited usefulness due to the lack of libraries available. For example, Lisp and web development seam to go together very nicely but the servers and frameworks available don't seam to have bean updated for some time i.e. I couldn't get portable allegroserve to work, and the last release was in 2004.

The only Lisp server that I managed to get(sort of) working was http.lisp, though again, this hasn't bean updated for a long time, and would need quite a lot of reworking to be of any use (HTML is old, and is hard coded in odd places and it cannot serve files).

> **fr4nko said:**
> Sometimes people argues that nowdays execution speed is not important. I believe that this is pretty much false. What is true is that, for some kind of applications, execution speed is not important but in many domains it still important and will ever be.

Most modern Lisp implementations compile to native machine code and have comparable execution speed to C.

As computers get more and more cores available, the advantage of pure functional/ partly functional languages will become more obvious. A pure functional program has no `state' so it is easy for the language runtime to scale it across as many cores as there are available.

---

### Post by CptPicard on 2009-06-20
> **hessiess said:**
>  For example, Lisp and web development seam to go together very nicely but the servers and frameworks available don't seam to have bean updated for some time i.e. I couldn't get portable allegroserve to work, and the last release was in 2004.

Google "SymbolicWeb"... it's a pretty impressive AJAX/Comet web app system in development that makes the browser completely transparent... it's developed by lnostdal of #ubuntu-programming.

> 
Most modern Lisp implementations compile to native machine code and have comparable execution speed to C.

Well, in all honesty, with reservations. If you create a lot of intermediate lists and map/filter/reduce them and all that, you unfortunately tend to spend a lot of time doing garbage collection... but yes, you can tune the important bits and then hide that behind macros.

> As computers get more and more cores available, the advantage of pure functional/ partly functional languages will become more obvious. A pure functional program has no `state' so it is easy for the language runtime to scale it across as many cores as there are available.

The problem here unfortunately is that pure-functionality tends to be a black and white proposition... lisp is not pure, and and as such it cannot give the guarantees that let pure-functional languages to be optimized/parallelized easily.

---

### Post by hessiess on 2009-06-20
> **CptPicard said:**
> Google "SymbolicWeb"... it's a pretty impressive AJAX/Comet web app system in development that makes the browser completely transparent... it's developed by lnostdal of #ubuntu-programming.


From the Wikipedia page it looks interesting, however  [http://groups.google.com/group/symbolicweb](http://groups.google.com/group/symbolicweb) doesn't seam to exist any more.

> 
The problem here unfortunately is that pure-functionality tends to be a black and white proposition... lisp is not pure, and and as such it cannot give the guarantees that let pure-functional languages to be optimized/parallelized easily


Lisp can be pure depending on the implementation, Scheme is more pure than CL for example. But you could say that any language which has IO has side effects, so even Haskell could be said to be non pure, even though it has no update operator, as it does have IO...

---

### Post by CptPicard on 2009-06-20
> **hessiess said:**
> 
Lisp can be pure depending on the implementation, Scheme is more pure than CL for example. But you could say that any language which has IO has side effects, so even Haskell could be said to be non pure, even though it has no update operator, as it does have IO...

No, I really really mean that a language either is pure or it is not. The sort of "Scheme is more pure than CL" is just a matter of style, but it does not mean that Scheme really *is* pure-functional up to the point where that feature of the language can actually be exploited. Scheme calls can produce side-effects somewhere, and they can't be ruled out, so you can't treat Scheme as a pure-functional language, although you may code in Scheme while trying to avoid side-effects.

Haskell, however, really is pure in the theory sense -- that is, it is guaranteed that as there are no side-effects anywhere (I/O excluded :) ), the purity can be systematically exploited by the compiler or some data-parallelism system.

---

### Post by Reiger on 2009-06-20
Actually in Haskell they got around the `dirty IO' issue by `locking IO away inside a monad'. This mechanism gives you a nice earmark for anything that may have side-effects upon the future result of some yet-to-be-evaluated expressions (and allows you to pretend to be still pure at heart). More importantly: it means that you *know* whether something *has* side effects. More important yet: monads operations are essentially transactions. 

Those two things combined give you a good abstraction mechanism for dealing with any shared resource (transactions), as well as let your compiler/interpreter know when it can go ahead and do as it pleases and when it must be rather more cautious.

---

### Post by CptPicard on 2009-06-20
+1 Reiger, I didn't feel like going into the details regading monads.. :) ... which I actually still am to totally "grasp", they are for some reason a remarkably hard topic for my puny brain :(

---

