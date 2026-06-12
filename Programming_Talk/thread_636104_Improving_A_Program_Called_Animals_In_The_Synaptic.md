---
title: "Improving A Program Called Animals In The Synaptic Package Manager"
date: 2007-12-09
forum: Programming Talk
---

### Post by emergingtechnologies on 2007-12-09
It's already obvious that I am not a programmer but I am in love with how Ubuntu and open source works and so I want to join in in whatever small ways I might.

I have encountered a great little program through the Synaptic Package Manager Called Animals... (just search animals).

It is supposed to be something of a Twenty Questions about animals -- but it comes with ZERO items in the database.  The user is supposed to divine that he or she needs to "teach" the program from the very start.

It's an excellent Idea and I love it but even I, who know at least a little bit about how these things work, couldn't get the hang of it right away because there is no documentation as far as I can see.

The game is presently 100% text based.

I figure without too much programming skill I should be able to merge some ideas from KEduca-Editor into a version of this Animals application.  That's further down the road.

Right off the bat I would like some intelligent person who can figure these things out to tell me:

1. How can I simply gain access to the program's data base so that I can build the database in a text editor?

2.  How can I make a database that I create available to other people who might be interested in it?

I still consider myself new to the Ubuntu community even though I have installed version on about 10 systems (I'm a huge cheerleader for Ubuntu) -- that's child's play.  Getting in and actually participating seems like a big step.

I know Animals might strike some programmers has beneath their interest but it really is a great little program and a nice place for a new person like me to start seeing if there's more that I might contribute.  I hope some people will help me get started with some simple instruction.

Thanks for you kind guidance,
Chris

---

### Post by Wybiral on 2007-12-09
You can get the source using "sudo apt-get source animals"

It appears to be using its own database, so you'd have to study the code some to see whats going on.

This is actually a really simple program to design, just create a binary tree with either a question or an answer at each node and keep appending them as you go.

What exactly are you asking? Just to be able to see the database in a text editor?

---

### Post by emergingtechnologies on 2007-12-09
Thanks so much for the terminal command -- it did not even occur to me that the source would be so easily accessible -- I am in fact this new at this.

I managed to get the source and then view the directory where it was deposited.  This pretty much my exhausts my terminal skills:

dpkg-source: extracting animals in animals-20031130
dpkg-source: unpacking animals_20031130.orig.tar.gz
dpkg-source: applying ./animals_20031130-2.1.diff.gz
fifi@fifi:~$ cd animals-20031130
fifi@fifi:~/animals-20031130$ ls
Animal.h          db4.1++-stuff.cc  gdbm-stuff.cc  Question.h          tut.cc
animals.6         db4.1++-stuff.h   gdbm-stuff.h   Record.h            util.cc
build-stamp       db4++-stuff.cc    install-stamp  str-conversions.cc  util.h
db2++-stuff.cc    db4++-stuff.h     main.cc        str-conversions.h
db2++-stuff.h     db++-stuff.h      main.h         test.cc
db4.0++-stuff.cc  debian            Makefile       test-str-cvt.cc
fifi@fifi:~/animals-20031130$ 

The last time I needed to manipulate a program it was a perl database program and everything was in one file.  All I needed to do was view the file in a text editor and making changes was simple after I figured out what they were doing with the fields.

I must confess that I do not understand any of the above suffixes.  

I am gathering that this program does not function from a single file but uses a number of files that work together.  I hate to ask for so much hand holding but I promise that the help you give me will be given back to the community when I get the hang of things.

To answer your questions: "What exactly are you asking? Just to be able to see the database in a text editor?"

I guess my hope is to build a database for this program that hosts about fifty animals and fifty questions.  I then want to add my database to the package so that when people download it they can begin to actually "play" the game without having to figure out that they first have to build the database as they play.

My audience here is parents who know even less about Ubuntu and open source than do I.

So... may I ask a couple of related and possibly stupid questions that might help me with this:

Let's say I decided to just "play" the game and allow the database to be built the way it is set up to be created during the play.  Now... which of those files in the directory is the new information being saved in?

Any tips would be greatly appreciated.

Thanks again for your patience and encouragement.  I am in terra incognito.

-- Chris

---

### Post by pmasiar on 2007-12-09
> **emergingtechnologies said:**
>  This pretty much my exhausts my terminal skills:
...
I guess my hope is to build a database for this program that hosts about fifty animals and fifty questions.  I then want to add my database to the package so that when people download it they can begin to actually "play" the game without having to figure out that they first have to build the database as they play.
...
I am in terra incognito.

Welcome aboard!

You have many options how to help/contribute. Simplest is to find "upstream" developers responsible for this package and suggest/persuade them to make changes you want. It might not work tho - they may have different preferences.

Easiest (as: you are in control) would be to get involved in programming - you do have some Perl experience. This is trivial program to make (in fact, variant of it is a training task in LearnPython wiki), and it definitely does not have to be in C. I would suggest Python, most programmers can pick basics within hours. Then you can create new package working **exactly** as you want, and package it for distribution in ubuntu. One of forums here is for training such packagers (ubuntu calls them MOTU: Master of the universe).

---

### Post by ajm2005 on 2007-12-12
> **emergingtechnologies said:**
> Let's say I decided to just "play" the game and allow the database to be built the way it is set up to be created during the play.  Now... which of those files in the directory is the new information being saved in?


the database created and used by the animals program is called "animals.db" and it is stored in this location:
/var/games/animals/animals.db

I had a quick look at the database file, it doesn't appear to be easily editable as it contains characters that won't display properly in a text editor.

However, if you have built up a database of animals, you could make a copy of your database (it's at /var/games/animals/animals.db) and share it with other people. They would just have to copy it to the correct location on their own machine.

I agree the documentation for the program is rather skimpy. You can get a very brief description of the program by typing "man animals" from the command window. There is also a "read me" file that is placed at the following location when you install the animals program:
/usr/share/doc/animals/README.Debian

You can read the readme file by typing "more /usr/share/doc/animals/README.Debian" in a command window (or you can navigate to that location using the graphical file manager). Here is a bit from the animals readme file:

"animals for Debian
----------------------

Animals uses a binary-tree database to store questions (which are like lisp cons-cells) and animals (which are like lisp atoms).

I wrote this, it's the typical animals game where you think of an animal 
which is searched in a binary tree where non-leaf nodes are yes-or-no
questions and leaf nodes are animals.

Traditionally, all such animals games I ever saw always had an initial database as shown in the first tree above. My version is not traditional: there are NO animals and NO questions at all in the initial database. Hence, my databases tend to be more flexible."


Going by the above, the author seems to have intended the game to arrive without a database. However that wouldn't stop you from sharing your own animals.db file with others if you wanted to. The package was written for Debian. I guess an animals.db file could be in included in the Ubuntu distribution, I don't know what the process would be for proposing something like that though.

---

### Post by sloggerkhan on 2007-12-12
we had a java project that sounds like this in my class this semester, lol.
My instructor brought in some little electronic toy that supposedly guess what we were thinking in a 20 questions game. I think we picked bagpipes and it guessed electric guitar after 20 questions. It was pretty funny, if a slight waste of lecture time.

---

### Post by emergingtechnologies on 2007-12-14
Thanks ajm2005!  This is exactly the type of instruction that I was looking for.  I'm guessing that I will also find contact information for the author of this program when I check those readme files so I am just delighted!

Thanks for helping this newcomer carry on and hopefully add something to one of the many projects that serve Ubuntu.

---

### Post by emergingtechnologies on 2007-12-14
> **pmasiar said:**
>  One of forums here is for training such packagers (ubuntu calls them MOTU: Master of the universe).

This opens up a whole new world for me.  Thanks.

---

