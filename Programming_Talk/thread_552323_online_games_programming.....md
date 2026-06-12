---
title: "online games programming...."
date: 2007-09-16
forum: Programming Talk
---

### Post by hockey97 on 2007-09-16
Hi, I want to make a web game well I decided to make a game that you would have to download the files from my website and install it on the user's computer, but the whole game is online, like their is no other option to play just online.

I already know c++ and some python, I know the basic elements of programming like what functions do ect basic stuff.

I am advance in C++, meaning I mostly know that lang then any other.

well I still can't decided to either have it installed on the user's computer or have it on my server, so they don't need to install it.
but the thing is that my server's memory is no that great to handle it.

is python better to make games with?? this game is going to just be a network game.

---

### Post by nonewmsgs on 2007-09-16
what i would do is to find an open source game similar (same genre) to what your idea is, and to give you an idea about what's going on.

---

### Post by pmasiar on 2007-09-16
twisted is python framework to write such games. 
But nonewmsgs advice above is right, look at some existing project, I would even advice you to participate in it for a year, so you will learn what (right decisions) work for them, and when you will know what to do differently, you may start your own project. But don't start project right now, your skills are likely not up to speed, you will make many wrong decisions, and will struggle to fix them. Learn from existing code first.

---

### Post by Vadi on 2007-09-16
IMHO, what you want is java, unless I understand you wrong.

---

### Post by Wybiral on 2007-09-16
C++ or Python would both work great, go with whatever one you're more comfortable with.

If this is your first game... Aim low. Make a simple 2d game with basic networking, don't expect to pump out a big 3d MMO. Build up.

Also, if you've never worked on a game... Do that first, then work on a networked game. There are some rules that change between them, simple offline games are much easier.

---

### Post by dugh on 2007-09-16
Python isn't a good choice for online web-based games.  Such games are usually created in either flash or java.  Since flash is not open source, on ubuntu java is a better option.  See the Netbeans IDE (now GPL), which supports development in java, javafx (an easier to use language), as well as ruby.

---

### Post by Wybiral on 2007-09-16
> **dugh said:**
> Python isn't a good choice for online web-based games.  Such games are usually created in either flash or java.  Since flash is not open source, on ubuntu java is a better option.  See the Netbeans IDE (now GPL), which supports development in java, javafx (an easier to use language), as well as ruby.

I don't think the OP meant browser embedded online games, just multiplayer networked games...

OP:
> 
I decided to make a game that you would have to download the files from my website and install it on the user's computer


So Python would actually be a pretty good choice. Since he/she knows C++ and Python, I'd say both are pretty good for game development and they both have tons of networking libraries available.

---

### Post by pmasiar on 2007-09-17
> **dugh said:**
> Python isn't a good choice for online web-based games.  Such games are usually created in either flash or java.

If you want to run game as applet (without downloading the client), yes. But then you restrict yourself to whatever browser lets you to do. Much better idea is what OP wanted: write your own client. Python is very good for that, see ie [http://www.eve-online.com/](http://www.eve-online.com/)

---

