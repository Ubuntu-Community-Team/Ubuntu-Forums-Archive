---
title: "PPPPPPick up a Python Project"
date: 2006-12-11
forum: Programming Talk
---

### Post by Kieranties on 2006-12-11
SO!

After a long time telling myself I should be getting back into python, I have decided to spend my xmas hols away from work! YAY!

Heres the thing, I haven't programmed in python for about a year, and even then I had only toyed with it for a few months.

I am not the most imaginative person.  In some ways I am a bit of a code monkey.  I am not great at thinking about ideas, but if someone gives me a good suggestion I tend to do all they need, then add bells and whistles which I think make it better.

So, I am looking for some ideas.  Nothing too big mind, I want something to ease me back in!

The only thing I have been able to think of so far is an app which allows the order of windows displayed in the on screen panel to be re-ordered.  Like you can rearrange the tabs in firefox.  Of course, I have no idea how to do this at the moment and it may require more fiddling with gnome and gtk then python.  But who knows.

So people, I am open all ears.  I am going home on Saturday, I will make a decision on friday if there are a few, so please, get suggesting!!

ttfn
Kieranties


EDIT: Typical!  There is a thread already running this kind of topic [http://www.ubuntuforums.org/showthread.php?t=316090](http://www.ubuntuforums.org/showthread.php?t=316090)  I guess I shall be flicking through that one too :D

---

### Post by angustia on 2006-12-11
do you like tetris-like games?

if so, design a tetris-like game shell, so any token based game (classic tetris, columns, tetris-attack, bricks, etc.) can be programmed for this shell as a plugin. the shell gives you a menu to select what game you want to play and how many players will be.

the shell has to provide to the plugins: input, display, network access and scores
plugins have to provide game logic and graphics

it will be interesting if the shell let the games to use not only top-down gravity (bottom-up, diagonal, center-border, etc.).

---

### Post by pmasiar on 2006-12-14
Suggestion: create a program **free software activist** aiding people to convince companies to open their drivers.

Rationale: As we read about yet another [try to ban binary drivers]("http://lwn.net/Articles/213977/"), and recall recent controversy about including binary drivers in Ubuntu...

Something should be done to educate people using binary drivers. People want Linux to "just work" but also need to know that they are using binary drivers. I suggested at [Binary Driver Education]("https://wiki.ubuntu.com/BinaryDriverEducation") wiki page to create a program which analyses config files, detects drivers which have binary-only drivers and are "target for activism". Create a HTML page with info about user's hardware, and more free equivalents. Then, sugest to write email to companies, complaining abot the situation and *suggest which other products I will buy next time*. 

Point is, I cannot change my hardware now, but sure as hell, **I will not get fooled again, if**
[LIST]
[*]I know how I got fooled,  
[*]I know what to do (and what to buy) to not get fooled again.
[/LIST]

If program is considered useful, it even may get included in system menu. Now, how cool it would be?

program and supporting infrastructure would include: 
[LIST]
[*]parsing config files for drivers information
[*]looking for "bad apples" and "free replacement suggestions" in some kind of database
[*]generating output page with:
[*]links to wikipedia for more info, and links to some other wiki explaining activism
[*]links to address of targeted companies, and suggestions how to write a letter which may make impact
[/LIST]

Private message me if you (or anyone) are interested, I will help you with the wiki part and in any other way I could - this is important to me.

---

### Post by maddog39 on 2006-12-19
I think we should have a thread (or even make this thread) a thread where people can post python projects that need help. It's also probably best if the projects posted where owned/founded by the poster.

---

### Post by rekahsoft on 2006-12-19
You could assist the Listen project on Sourceforge. 
[http://listengnome.free.fr/](http://listengnome.free.fr/)

---

### Post by lazka on 2006-12-20
my suggestion: take a python program you use and like and try to fix some bugs

---

