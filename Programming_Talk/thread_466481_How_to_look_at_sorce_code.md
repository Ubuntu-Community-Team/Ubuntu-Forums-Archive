---
title: "How to look at sorce code"
date: 2007-06-06
forum: Programming Talk
---

### Post by microsoft92sucks on 2007-06-06
I've been learning to program in python and once I get a lot better I want to make some game (along with other things). And I've heard a good way to learn how to program is looking at coding. so where can I go to download some games that were written in python and once I do that how would I look at all the coding?

---

### Post by microsoft92sucks on 2007-06-06
I need GNU,Open source games of course.

---

### Post by Auria on 2007-06-06
For learning, I dont recommend looking at existing games at all - their source code will probably be very big and intimidating to you...

you better read books and tutorials - you say "a good way to learn how to program is looking at coding"... this is right, but, and especially for a beginner, small examples. digging into the code of a big project can be very intimidating even for experienced programmers (or just look at very small games ;) i don't know any )

i think you can ind good resources here [http://www.pygame.org/wiki/tutorials](http://www.pygame.org/wiki/tutorials)

building along tutorials will be more rewarding than getting lost in files of code.

unless I misundertsood your current level and you're no beginner

---

### Post by jfinkels on 2007-06-06
Don't look at source code for large programs, that won't do you any good. I suggest thinking up a small application that might be useful to you and writing it! You can do pretty much anything you can dream up :D

---

### Post by microsoft92sucks on 2007-06-06
Thanks and i'm still very much a noob I'm reading a online book right now to learn I'm about half way through it.

---

### Post by Lord Illidan on 2007-06-06
Aye, I tried looking at programs once, and I gave up immediately..books are the  way to go.

---

### Post by microsoft92sucks on 2007-06-06
I still want to know how do I look at the source code of stuff like for all the GNU software that I have most if not all my software is GNU so how would I look at the code on any of it?

---

### Post by microsoft92sucks on 2007-06-06
Sorry for my bad gramer.

---

### Post by Feba on 2007-06-06
While you should listen to their advice, if you want to look at source code, look up "svn".

---

### Post by microsoft92sucks on 2007-06-07
I am listing to them but I've always wanted to know how to look at source code.And I'll try looking up svn. Thanks

---

### Post by microsoft92sucks on 2007-06-07
Looking up svn is'ent helping can you be more pacific.

---

### Post by WW on 2007-06-07
Take a look at the games and demos at [pygame.org]("http://www.pygame.org/").

---

### Post by ankursethi on 2007-06-07
There's a book which has some tips on reading source code called "Code Reading : The Open Source Perspective" which starts from basic UNIX apps like echo and goes up to the X server. You might find it helpful, though most of the examples in it are in C.

---

### Post by pmasiar on 2007-06-07
After reading intro book, start with simple programs. Real programs (with GUI and error handling) might be too complicated for a beginner. After couple months, when you wrote and debug your own 500 line program, reading code of other people will suddenly become much easier. You will be able to see "patterns" and distinguish bigger chunks of the code.

But really deeply reading and understanding code of other people is hard, reading code is always slower that reading ie. sci-fi novel :-)

---

### Post by ssam on 2007-06-07
to get the source code to any program in ubuntu you can run

```
apt-get source program_name
```

to get a list of all the ubuntu packages using pygame

```
apt-cache rdepends python-pygame
```

so pick one of those and run, for example

```
apt-get source singularity
```

---

### Post by cunawarit on 2007-06-07
> **microsoft92sucks said:**
> Looking up svn is'ent helping can you be more pacific.

svn is the client for Subversion. 

Subversion is version control system, it is open source and just about everyone uses it (yep, even Microsoft heavy companies do). Many open source projects will tell you the URL for their repositories so you can download the source.

---

### Post by microsoft92sucks on 2007-06-07
Thanks ssam now I get how this all work's.

---

### Post by microsoft92sucks on 2007-06-08
> **WW said:**
> Take a look at the games and demos at [pygame.org]("http://www.pygame.org/").
Thanks for this site there's lot's of Python source code here.

---

