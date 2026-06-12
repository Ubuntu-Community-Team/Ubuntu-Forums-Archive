---
title: "Beyond loops."
date: 2008-12-24
forum: Programming Talk
---

### Post by Zargoon on 2008-12-24
I'm a highschool student.  The unfortunate thing about my school is that their technology department is sevearly limited in their technology department.  Like the peak of their tech class are "How to use MS Word".

Well, a long story short, I created a club where we meet after school and then do some programming.  What ended up happening is that I just started teaching everyone the little bit a know.  Which is not much mind you just stuff I've pick up on the internet.

So were using python because that seems like a good starting point.  We've done loops and if statements and made some little text based combat and adventure games.

The issue is now I've hit a road block.  I really have no idea where to go next after simple stuff like loops and what not.  Objects?  That sounds kinda advanced.  I don't really know what the natural progression is, and I also have a hard time finding things because the tutorials that I've found are either redundant or to advanced.

So I was wondering if there are any tutorials and resources that you guys would recommend?  I'm okay with ordering a book off of amazon if need be.  The information is scattered enough that I figured I could save some time by asking first.

Thanks in advance!

---

### Post by pmasiar on 2008-12-24
Wiki in my sig has plenty links. 

You need to solve many problems (also linked), but don't get bogged by OOP design at the begining: using existing objects is just fine, and when you will learn how to use them, designing your own will make much more sense. Until then, dictionaries will serve as your 'poor man' objects just fine.

Also, consider avoiding GUI - it is lots of work for little gain (except it looks pretty). There is another way to share your applications: make then web-hosted using Google App Engine. It is also hard, like GUI is, but IMHO more useful skill to learn. But stay in commandline as long as you can.

O'Reilly's book are almost all of high quality if you want to invest money. Pygame is nice and relatively simple game library. EasyGUI is the easiest GUI is you must have it.

---

### Post by CptPicard on 2008-12-24
Well, learning to use lists, tuples and dicts and how to write functions? :)

IMO writing simple classes of your own wouldn't be too hard, after all, everything in Python is an object... why not make your own.

One important topic you may be able to tackle now is recursion (after you've been defining functions). For example, riddle me this... how do you sum the first n integers without either using the "sum" built-in or using a loop? (Hint, it's an application of function calling itself)...

---

### Post by s3gfault on 2008-12-24
Programming club sounds like a great idea!  It sounds like you've covered syntax for your language and are ready to move on to meatier subjects.  You'll want to explore Algorithms and Data Structures.  Are you guys using C?  Should consider using C if you're not.

Start by learning and loving the Linked List.  After that most books move on to Stacks and Queues.  Learn about Binary Trees and more advanced graphs.  For beginner algorithms, look to mathematical formulas, like fibonacci, for problems.  Explore recursion.

There are alot of good books out there, my alma mater uses Data Structures and Algorithms in C++
[http://www.amazon.com/Data-Structures-Algorithms-Michael-Goodrich/dp/0471202088/ref=sr_1_2?ie=UTF8&s=books&qid=1230152387&sr=1-2](http://www.amazon.com/Data-Structures-Algorithms-Michael-Goodrich/dp/0471202088/ref=sr_1_2?ie=UTF8&s=books&qid=1230152387&sr=1-2)

---

### Post by catchmeifyoutry on 2008-12-24
Good for you guys to learn some programming your selfs. I remember the same point where I wasn't sure what to do, everything is too simple (explaining the same basic syntax) or to advanced (talking about concepts i didn't know or cared about).
However, I can't name an exact action/lesson that got me out of that situation, I just tried stuff like playing around with classes and inheritance and then didn't do anything with it because there was no need in my simple code. But at least I got familiar with some concepts. At the same time I learned about other computer stuff, and programming libraries, and that also introduced new concepts I got to understand. With time, stuff got connected in my head and now I have a pretty good idea how to approach what problem and why. Ok, so far my story of frustration.

Anyway, you're never going to learn the details and uses of any language (even natural languages like spanish, french, whatever!) if you don't have an objective (like go to the bakery in spain, or program tetris). Also, coding is all about using data structures, defining new ones, and control the program flow between them with loops and if statements. Knowing when to use a list, and when a dictionary (or even a set() ) is part of the higher level knowledge you're looking for.

So, why don't you try to make a nice game? Don't abandon the command line, but see if you can make a checkers game, for example (for 2 human players).
If you do want some graphical stuff to keep you excited, try the pygame library. The website has many tutorials and explanations how to get started: [http://www.pygame.org/news.html](http://www.pygame.org/news.html)
In ubuntu it can be installed with: sudo aptitude install python-pygame
Keep playing ( = programming) and at a certain moment you realize life would be easier if you had something like those "classes" you read about before.

Good luck and have fun!

---

### Post by Zargoon on 2008-12-24
Haha wow thanks for quick responses.  I'm definetally going to check all that stuff out.  As for languages the reason we did python was because it just seemed easy to start with and it also seemed like it would at like a stepping stone to harder languages (we want to reach some C++ before the end of the year).

As for what we were going to develope we were thinking along the lines of a simple game that our math teacher suggested.  You have a bunch of hexagonal bubbles all on a grid and you have to make a line across the paper, without getting blocked off by the other person.  I'll get a copy of the paper and upload when I get the chance cause' I know I'm not doing a very good idea of describing it.  The checkers sounds like a good idea too.  A lot of the guys there really want to do game stuff but that's REALLY complicated.  We've done some playing around with blender and 3DSMAX but that stuff is crazy.  So I like the idea of getting familiar with simple objects and going more gradually into that kind of stuff.  Maybe that will curb their impatience :-)

Thanks again for the help!

---

### Post by s3gfault on 2008-12-24
as far as games go, i cut my programming teeth on MUDs.  This something well worth looking in for.  Check out the source code for Rom 2.4.  you really need a *nix to run it from, mac would probably work.

---

### Post by monkeyking on 2008-12-25
I would go for a larger project.

I remember when i was a first year cs student,
we had to implement the basic math operations (+,-,*,/),
for unbound integers.

It was a really good project that spanned many areas,
but still the programming was very basic,
or could at least be implemented in a basic fashion :)

Which way to represent the data internally?
Arrays, lists, vectors?
Which base to use?
binary? decimal?
Should the lists be reversed?

You start all(not div) math ops, with the least significant cipher.

You can fairly fast get a working implmentation running.
All these basic operations are just variants of addition.
subtraction is just a negative addition.
multiplication is just a lot of additions.

But after you have implemented this you can optimize.
Basicly you can use the table system you have learned in school. with carreyins.

This is rather easy for most people.
Still it takes some time to check for correctness.
------------------------------------------
But integer division proved to be quite more difficult to implement. beware.
------------------------------------------

When we had this basic math calculator, we testet it,
with the rsa cryptography.
This meant decrypting the first rsa coded message ever made.
quite funny actually.

I'm here not talking about hacking or cracking but coding and decoding.

rsa is just multiplication of numbers. Some exponent and a lot of moduli.

I can really recommend this project.
Even though you won't actually decode the rsa,
It's surely been very rewarding for everyone.

---

