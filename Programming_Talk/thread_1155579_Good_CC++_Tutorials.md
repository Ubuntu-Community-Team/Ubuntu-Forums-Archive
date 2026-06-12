---
title: "Good C/C++ Tutorials"
date: 2009-05-10
forum: Programming Talk
---

### Post by MechWarrior001 on 2009-05-10
Does anyone know a GOOD (not easy) C/C++ tutorial? And which should I learn first? C, or C++?

---

### Post by justin10ec on 2009-05-10
I am also interested in this. :)

---

### Post by Sinkingships7 on 2009-05-11
> **MechWarrior001 said:**
> And which should I learn first? C, or C++?

Out of curiosity, do you have any particular reason for limiting yourself to those two options?

---

### Post by MechWarrior001 on 2009-05-11
Not sure. Should I go with Python? Or maybe Ruby? Or I could learn Javascript...

But I want to start making games, and from my knowledge C/C++ are the two most efficient  coding languages for that.

---

### Post by Sinkingships7 on 2009-05-11
> **MechWarrior001 said:**
> Not sure. Should I go with Python? Or maybe Ruby? Or I could learn Javascript...

But I want to start making games, and from my knowledge C/C++ are the two most efficient  coding languages for that.

What kind of games are you looking into writing? Web/Flash based games, or just your standard running-off-the-os games?

If this is your first time coding, I'm going to recommend Python as your first language. Before you start doing something as complex as writing games, you should understand the logic behind programming.

If this is not your first time coding, and you're looking into writing games for the desktop, it's true that C++ is the most used language for this task. However, it is worth noting that this is changing with time. If your goal is to get something that works out there as quickly as possible, I still suggest using Python. It has many libraries for making games, and will make your task much easier is almost every regard.

---

### Post by MechWarrior001 on 2009-05-11
Hmm, well do you have any ideas for what my first app could be?

---

### Post by Sinkingships7 on 2009-05-11
> **MechWarrior001 said:**
> Hmm, well do you have any ideas for what my first app could be?

If your only goal really is games, then start with some simple command line games.

How about a "Guess the Number" game, where the computer randomly generates a number from 1 to 100 and the user attempts to guess it. If the users guess is higher than the computers number, then the computer spits out "Lower". You get the idea.

Afterward, you could try hacking together the game of War, usually played with cards. 

I've went as far as writing Tic-Tac-Toe, which you can find lurking around this forum somewhere.

A lot of people go on to suggest (once you're ready for graphical programming) Pong, followed by a simple 2D scrolling shooter. You can work your way up from there.

---

### Post by Sockerdrickan on 2009-05-11
I learnt C++ (which includes C many times) and then learnt stdlib.h etc. I recommend going for that order.

---

### Post by Jiraiya_sama on 2009-05-11
I liked C++ primer 4th edition. It's put me ahead of the rest of my class by a lot within 3 months.

---

### Post by eye208 on 2009-05-11
[http://www.icce.rug.nl/documents/cplusplus/](http://www.icce.rug.nl/documents/cplusplus/)

---

### Post by ajackson on 2009-05-11
For a good place to find information on a few languages head over to [Lambda: For those who Grok]("http://lambdagrok.wikidot.com/")

That site contains the following for [C]("http://lambdagrok.wikidot.com/learn:c") and [C++]("http://lambdagrok.wikidot.com/learn:cpp").

I highly recommend it for open-minded individuals (both novices and experts) who are interested in programming.

---

### Post by davidpeace on 2009-05-11
I'm learning C by using "C for Dummies". But I would also like something fun to learn with, like a game where the object is to use C code to do something. For example, Robocode is a game in which one programs a robot to kill other robots using Java. Is there something like this for C/C++?:popcorn:

---

### Post by ajackson on 2009-05-11
> **davidpeace said:**
> I'm learning C by using "C for Dummies". But I would also like something fun to learn with, like a game where the object is to use C code to do something. For example, Robocode is a game in which one programs a robot to kill other robots using Java. Is there something like this for C/C++?:popcorn:

Look for CRobots (it's even on wikipedia), a few links:

[http://crobots.deepthought.it/home.php]("http://crobots.deepthought.it/home.php")
[http://www.pinkandaint.com/oldhome/comp/crobots/index.html]("http://www.pinkandaint.com/oldhome/comp/crobots/index.html")
[http://www.gamerz.net/c++robots/]("http://www.gamerz.net/c++robots/")

---

### Post by davidpeace on 2009-05-15
Thanks. I downloaded it and am going to try it out this weekend.

---

### Post by mmix on 2009-05-15
advanced c :
[http://www.accu.informika.ru/accu/bookreviews/public/reviews/0sb/advanced_c.htm](http://www.accu.informika.ru/accu/bookreviews/public/reviews/0sb/advanced_c.htm)

advanced c++ :
[http://www.accu.informika.ru/accu/bookreviews/public/reviews/0sb/advanced_c__.htm](http://www.accu.informika.ru/accu/bookreviews/public/reviews/0sb/advanced_c__.htm)

etc:
Advanced Programming in the UNIX Environment, Second Edition (Addison-Wesley Professional Computing Series) (Paperback)

cs app [http://csapp.cs.cmu.edu/](http://csapp.cs.cmu.edu/)

Edit: typo

---

### Post by noerrorsfound on 2009-05-16
> **eye208 said:**
> [http://www.icce.rug.nl/documents/cplusplus/](http://www.icce.rug.nl/documents/cplusplus/)
That doesn't really help him since it's intended for people moving from C to C++.

---

### Post by Frak on 2009-05-16
Are you beginning to program? If so, I'd highly recommend you start off with a high level language (such as Python or Ruby first). I started with Ruby and moved to Python, then Java, then C++ and down to C. Ruby is very simple to comprehend as it comes very close to human speech, while it and Python share similarities, Python will serve you some more advanced concepts. Then Python will prepare you for Java, which comes closer to C++ which will ready you for dropping (true) OOP for C.

That was my course of study. Though, if you're looking to make games in C or C++ (and just starting with C/C++), then I recommend watching the VTC series on C. That will start you out with some footing. Then read a recipe book/bible/advanced C book until you become more comfortable. Finally, read some books over either a lightweight graphics library or something bigger such as OpenGL. Then read up on manipulating AI and you should be done.

My bookshelf:
VTC C
O'Reilly Cookbooks
AI for game developers
The OpenGL shading language 2nd edition

Though, you could also save yourself a lot of time and possibly do the same thing using Python and PyGame.

EDIT
The reason I say to watch the VTC series on C is because it really helps to watch a person make mistakes in front of you (and they do) and explain why something doesn't work. In a language as complicated as C, this can help enormously.

---

### Post by gmatt on 2009-05-17
In my humble opinion, 

[http://www.amazon.ca/Computer-Systems-Programmers-Randal-Bryant/dp/013034074X](http://www.amazon.ca/Computer-Systems-Programmers-Randal-Bryant/dp/013034074X)

is probably the most comprehensive and suprisingly easy to follow book on the topic of programming. Its extremely thorough and detailed and "looks under the hood". If you want to start hacking, this is a great place to start. Before you can hack away, you gotta know how stuff works, and documentation on linux is extremely poor, but this book covers almost all you need to know, not just about linux but about computers in general.

---

