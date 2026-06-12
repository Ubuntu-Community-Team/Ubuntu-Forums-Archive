---
title: "Best language for me?"
date: 2008-12-12
forum: Programming Talk
---

### Post by timbim on 2008-12-12
I want to start programing on a linux system, and be able to produce programs able to run under linux.  I have had a look at the stickies, but thought it might just be a little easier to ask you knowledgeable lot rather than try to trawl through all the available languages to discover which ones meet my needs.

Basically, I've been programing in Just Basic, Liberty Basics smaller brother, and would like to stick to a language which uses similar syntax and language.  I also quite like the look of the VB design, especially with its powerful GUI controls outside the coding, so you don't have to write each feature of each control.  It needs to be able to fully address USB, serial and parallell ports, and needs to be able to have good sprite handling capabilities.

So hit me with some suggestions!

Thanks,
Tim

---

### Post by mssever on 2008-12-12
No language in the Basic family is in wide use in Linux. Plus, once you get more experience, you'll realize that syntax similarity is rather a minor issue. If you look at Glade, you'll find a GUI designer. But I'd strongly recommend that you stay away from GUIs until you've grasped the basics. A GUI should be just a layer on top of fully-working code.

This question is one that tends to start lots of flamewars--which is why the stickies exist. In terms of popularity, Python seems to be the most popular around here. While I like Python quite a lot, remember that popular doesn't necessarily mean best.

EDIT: One other thing: If you intend to advance in programming, you'll need to learn multiple languages eventually. So put LISP on your languages to learn eventually.

---

### Post by nvteighen on 2008-12-12
Read the stickies... you'll find anything there.

Just a note: as BASIC dialects are usually non-standarized proprietary languages, you won't find too much GNU/Linux support for them. Also, it's an obsolete language. Maybe, you could take a look at FreeBasic, but I'd recommend you to move to a more modern language.

---

### Post by Mr.Macdonald on 2008-12-12
Not to be angry, but if you ask this question then you are lazy and have no common sense, read stickies and google.

---

### Post by Sorivenul on 2008-12-12
You say you've read the stickies, people tell you to read the stickies. If you are new to this, it can seem like a daunting task to learn *any* programming language.

Now, the best language for you is the one that works best for you, just like the your favorite programs are the best programs for you, or like the Linux distribution you use is the best Linux distribution for you.  It really does come down to choice.

I have my own biases, but will bypass them, and simply list a couple that will get you will have plenty of help with around here:
Scheme - The book *[Structure and Interpretation of Computer Programs]("http://mitpress.mit.edu/sicp/full-text/book/book.html")* is a common reference, though many guides to the many dialects exist.
Python - [pmasiar's Wiki]("http://learnpython.pbwiki.com/HowToStart") is a good place to start.  The Python help on these forums is pretty outstanding.

---

### Post by mssever on 2008-12-12
> **Sorivenul said:**
> The Python help on these forums is pretty outstanding.
This brings up an important point. It's a good idea to choose a language that is known by the people you turn to for help. Around here, Python is your best bet by that measure--although there are several Java, C, and LISP fans around, too.

---

### Post by slavik on 2008-12-12
> **mssever said:**
> This brings up an important point. It's a good idea to choose a language that is known by the people you turn to for help. Around here, Python is your best bet by that measure--although there are several Java, C, and LISP fans around, too.
You forgot Perl (5 and 6). *sniff* *sniff* :(

---

### Post by Wybiral on 2008-12-12
> **slavik said:**
> You forgot Perl (5 and 6). *sniff* *sniff* :(

It's not forgotten, just willfully ignored :)

---

### Post by mssever on 2008-12-12
> **slavik said:**
> You forgot Perl (5 and 6). *sniff* *sniff* :(
Perl? What's Perl? :)

---

### Post by nvteighen on 2008-12-13
> **mssever said:**
> Perl? What's Perl? :)
```

ugi@UGI:~$ perl
use warnings;
use strict;
perl;
Bareword "perl" not allowed while "strict subs" in use at - line 3.
Execution of - aborted due to compilation errors.
ugi@UGI:~$ 

```

:D

---

### Post by crazyfuturamanoob on 2008-12-13
Try Python & PyGame.

PyGame does pretty much of sprite handling 
and other hard stuff, and Python is easy to learn.

Or maybe GTK instead of PyGame if you really need GUI buttons & things.

And its also possible to use OpenGL with PyGame.

---

