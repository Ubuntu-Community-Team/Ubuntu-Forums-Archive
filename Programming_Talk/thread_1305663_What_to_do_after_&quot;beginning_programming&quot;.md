---
title: "What to do after &quot;beginning programming&quot;?"
date: 2009-10-30
forum: Programming Talk
---

### Post by dylbud on 2009-10-30
I skimmed the sticky threads and didn't see anything specifically addressing my question --- so here goes:

I've been dabbling with learning programming...Javascript, PHP, C, C++, and Python are the languages I've dealt with so far. I've taken a few classes at the community college, and done quite a few online video tutorials.

The thing is, all these classes and tutorials are *beginning* programming. As I try to figure out my next step, I am finding either of the following: 

(1) more beginning programming, or
(2) stuff that is totally and completely beyond me

Is there a middle ground? Can anyone suggest a next step for *intermediate* programming? Resources, websites, approaches, etc?

---

### Post by McDarling on 2009-10-30
Well, at my school, we have a class called Object Oriented programming that is intended to be taken after Programming 1, both of which are in C++. Maybe you have something similar, if you have something analogous to our Programming 1. We also have some specialized programming classes, like Intro to Scientific Computing (in Fortran), and classes similar to the two C++ classes but with Java.

---

### Post by whirlwind on 2009-10-30
If you haven't already in your CC classes, I suggest fully examining data structures and lower systems level Unix programming (operating systems/assembly code).  This is probably the next step in your CC classes if you haven't done it yet.  Keep on taking the CC classes would be my suggestion...

whirlwind

---

### Post by diesch on 2009-10-30
[LIST]
[*]Some algorithm and data structure lecture is always a good thing. As is something about parsing, state machines and such.
[*]Read and try to understand code written by others.
[*]Most important: Write code. Makes mistakes and learn from them.
[/LIST]

---

### Post by whirlwind on 2009-10-30
> **diesch said:**
> 
[LIST]
[*]Most important: Write code. Makes mistakes and learn from them.
[/LIST]


I don't mean to hijack dylbud's thread, but this has always been the hardest part for me when not writing assignments for school: what kind of program should I write?  I would love to work on some sort of opensource project, but don't really know if my skills are mature enough to do so.

---

### Post by vamped on 2009-10-30
> **whirlwind said:**
> I would love to work on some sort of opensource project, but don't really know if my skills are mature enough to do so.

Same here. CC courses not available to me right now, but I keep reading reading reading - and sometimes programming when I need to make a utility. I'm hoping that some day I'll get good enough to contribute.

Data structures sounds like a good read. Will google.

---

### Post by diesch on 2009-10-30
> **whirlwind said:**
> I don't mean to hijack dylbud's thread, but this has always been the hardest part for me when not writing assignments for school: what kind of program should I write?  


Is there something boring you are doing over and over again? Some command line program you always wanted to have a GUI for? Some web site you want to extract something from?

When I was in school I had to conduct an experiment for the physics class and evaluate the results. To save me some time I wrote a program that calculated to results, added a random 10% error and created the needed charts from it.  ... ;-)

> **whirlwind said:**
> 
I would love to work on some sort of opensource project, but don't really know if my skills are mature enough to do so.

I think it's a good idea to start with your own small project so you can try things and learn how to use tools without causing problems to others. 

If you want to join other projects submitting bug fixes is often a good first step.

---

### Post by grayrainbow on 2009-10-30
The first and most importand thing in todays software after good understadning of basic principles of programming(and some math) is to be familiar with others peoples code. No one write programms alone anymore, more programms that could be written by single programmer are already written. So, go and find open source project you like, you could be of help not only by writing code, but with debugging also(which is very helpfull to understanding how code work). If you want big challange...try implement face regognition application, not full blown just enough to recognize the people from your family(assuming it's not 100 member family :) ). And ofcourse find friends to do it with you :)

---

### Post by dwhitney67 on 2009-10-30
> **grayrainbow said:**
> The first and most importand thing in todays software after good understadning of basic principles of programming(and some math) is to be familiar with others peoples code. No one write programms alone anymore, more programms that could be written by single programmer are already written. So, go and find open source project you like, you could be of help not only by writing code, but with debugging also(which is very helpfull to understanding how code work). If you want big challange...try implement face regognition application, not full blown just enough to recognize the people from your family(assuming it's not 100 member family :) ). And ofcourse find friends to do it with you :)

+1.

Also, another facet of s/w development is the testing phase.  This involves writing test plans for full-scope testing to ensure that the s/w is bug-free, and that it is worthy of being used in a critical system.  Most s/w apps don't fall under this umbrella, thus the reason why many s/w apps are shoddy.  God forbid the "blue screen of death" shows up on a medical device, or the flight console of an aircraft.

---

### Post by A_Fiachra on 2009-10-30
Solve a problem.


It doesn't have to be unique or pretty ... but if you look around, you'll see computing problems all over the place.

E.g.  Write a C++ program to check spelling on a web page.

Yes, it's been done. but you can learn a lot from doing it yourself.

You'll have to figure out how to pull a web page, parse the html, get the raw text data and check it against a dictionary.  Figure out how to do it then figure out how to do it optimally.  Remember Knuth's warning -- premature optimization is the root of all evil!

---

### Post by cdiem on 2009-10-30
@ A_Fiachra - I find your idea really useful - I was looking for something  like that myself, in order to try my luck with languages new to me. So, just thanks! (btw I find the whole thread extremely useful - as to me, it could be sticky as well).

---

### Post by kavon89 on 2009-10-30
This is the description of the intermediate programming course I am taking next semester at my university. The language is C++.

> Intermediate Programming - Object-oriented programming, recursion, fundamental data structures (including stacks, queues, linked lists, hash tables, trees, and graphs), the basics of algorithmic analysis, and an introduction to the principles of language translation.

Other than learning those topics, the best thing you could do is start a project and just code away at something challenging.

---

### Post by Penguin Guy on 2009-10-30
Steps to mastering any programming language:
[LIST=1]
[*]Read through a beginners tutorial (experiment during the tutorial)
[*]**Make some programs (doesn't matter if they're completely useless)**
[*]Read/edit other's code
[/LIST]
Remember that [google]("http://www.google.com/codesearch") is your friend.

---

### Post by dylbud on 2009-10-30
Wow, thanks for all the responses, everyone. That's more responses than I've ever got on this forum...and in less than 24 hours!!

Anyway, let me ask another question focusing in on one suggestion in particular that several of you gave. Namely, reading other people's code. Seems like everyone agrees that's a good way keep learning.

But my problem is finding code to read that is even remotely in my realm of understanding. Like I mention in my original post, everything I find online tends to be basic beginner stuff, or super-major-advanced out-of-this-world stuff. My struggle is bridging the gap between the beginning level stuff that I know, and the advanced level stuff that I'm seeing out there. 

Any good libraries of medium-to-advanced example code out there that I can study?

Thanks again for all suggestions.

---

### Post by nvteighen on 2009-10-31
I'd start coding something... well, don't desperate if you don't find something to do; inspiration needs time to arrive on your head. Meanwhile, take a look at popular project hosting sites and search projects that you might be interested at.

1) [http://sourceforge.net](http://sourceforge.net)
2) [http://launchpad.net](http://launchpad.net)
3) [http://gitorius.org](http://gitorius.org)
4) [http://savannah.gnu.org](http://savannah.gnu.org)

Also learn some popular frameworks and libraries used in the languages you know. For example, you say you know C and C++... well, why don't you try GTK+ and Qt, respectively? Compare the feel of C GTK+ with PyGtk's... Or learn how to interface with CUPS (libcups is a quite easy library to use)... etc.

---

### Post by RichardUK on 2009-10-31
Something I did many moons ago ( 28 years! ) was to try to copy one aspect or effect games I was playing. Now that was not so hard to do in the days of z80 and a choice of asm or basic. Today that may be a lot harder. But a lot of the clones of the simple phones games would be a good start. But even if delving into graphics is a bit far to start a text base game would be a good start.

So for example, connect 4. You enter the column number a chip is placed the it responds with the column number that it wants to go in.

I did a connect 4 game quite a few times over the years, it's always fun when your running the code in your head at the same time and it makes a move you do not expect, emergent behaviour. :D

Then the cool bit, ask a relative to play against your program.

---

### Post by nvteighen on 2009-11-01
> **RichardUK said:**
> 
I did a connect 4 game quite a few times over the years, it's always fun when your running the code in your head at the same time and it makes a move you do not expect, emergent behaviour. :D

Then the cool bit, ask a relative to play against your program.

AI even as simple as a negamax search w/alpha-beta pruning for Connect-4 may not be something easy to think about... I'm coding a Connect-4 client (see PycTacToe in my sig) and I haven't even thought on an AI for it because I just don't "see" the evaluator part of it.

---

### Post by RichardUK on 2009-11-02
> **nvteighen said:**
> AI even as simple as a negamax search w/alpha-beta pruning for Connect-4 may not be something easy to think about... I'm coding a Connect-4 client (see PycTacToe in my sig) and I haven't even thought on an AI for it because I just don't "see" the evaluator part of it.

Ok, I have no idea of what you said there, my connect 4 (I was just learning) progs were just a load of "if's" and for loops to scan for shapes and to do a stock response to that. I guess your prog would have whipped mine. ;)

---

### Post by nvteighen on 2009-11-02
> **RichardUK said:**
> Ok, I have no idea of what you said there, my connect 4 (I was just learning) progs were just a load of "if's" and for loops to scan for shapes and to do a stock response to that. I guess your prog would have whipped mine. ;)
Look at: [http://en.wikipedia.org/wiki/Alpha_beta_pruning](http://en.wikipedia.org/wiki/Alpha_beta_pruning) :)

In AI the problem is the evaluator, not the search. Writing a good evaluator requires to create a good vmodel that assigns a "reasonable" value to each situation... You know, computers can't think so you have to give them predefined thoughts they can apply to. In Tic-Tac-Toe, this is trivial...

That's why I think an AI project may be unsuited :P

---

### Post by froggyswamp on 2009-11-02
> **dylbud said:**
> 
Can anyone suggest a next step for *intermediate* programming? Resources, websites, approaches, etc?
Next step create a private implementation of the AI.

---

### Post by terry_a_g on 2009-11-02
Like other's have pointed out, traditionally Data Structures and Algorithms is the next step.  You'll learn how to implement things like hash tables, red-black trees, quicksort, and a ton of other stuff that will come in handy some day.  I'd also recommend learning Boolean Algebra and how to analyze the runtime performance of algorithms at this point if you haven't already.  Googling "Big O notation" should lead you to some sites discussing algorithm anaylsis.

---

### Post by StunnerAlpha on 2009-11-03
> **terry_a_g said:**
> Like other's have pointed out, traditionally Data Structures and Algorithms is the next step.  You'll learn how to implement things like hash tables, red-black trees, quicksort, and a ton of other stuff that will come in handy some day.  I'd also recommend learning Boolean Algebra and how to analyze the runtime performance of algorithms at this point if you haven't already.  Googling "Big O notation" should lead you to some sites discussing algorithm anaylsis.

Agreed. This is the route I took in uni. Although you may find it boring, I recommend doing it.

---

### Post by grayrainbow on 2009-11-03
> **terry_a_g said:**
> Like other's have pointed out, traditionally Data Structures and Algorithms is the next step.  You'll learn how to implement things like hash tables, red-black trees, quicksort, and a ton of other stuff that will come in handy some day.  I'd also recommend learning Boolean Algebra and how to analyze the runtime performance of algorithms at this point if you haven't already.  Googling "Big O notation" should lead you to some sites discussing algorithm anaylsis.
I personally find Set theory much more useful than Boolean Algebra in respect to programming, but usually more math knowledge never hurt :)

---

