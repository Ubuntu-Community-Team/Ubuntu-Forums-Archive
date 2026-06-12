---
title: "Good game-development kit/engine for a programmer with no time?"
date: 2008-10-08
forum: Programming Talk
---

### Post by Sydius on 2008-10-08
I consider myself "above average" at C/C++, and have no trouble making simple 2D games from scratch.  Well, except that I spend all my time making engines and not making games, mostly because "my time" is about an hour a day at best.

I've spent a lot of my time scoffing at the use of game kits/engines for simple 2D games, but I think I've become wise enough to know that a finished game is better than an unfinished game, no matter how it's made.

Coming to the point, I want to make a Mega Man-like game/clone.  I don't want 3D graphics.  The ideal starting point to me would be a C++ engine specifically made for 2D platform games, but after much searching, it seems a lot of programmers try to make such a thing but kinda' give up half-way and I'm having a hard time sifting through the clutter on the web.

So I'm wondering if anybody has heard of something similar to what I'm looking for, or something close enough that I could adapt it (I prefer GPL/otherwise open-source solutions, by far).

I just want to make a silly little open-source Mega Man clone (preferably in C/C++) that runs on Linux, and would like a good start/jumping-off point if possible.  I'm even happy using clicky drag/drop kind of tools if available (I won't be picky).  Not trying to be pro.

---

### Post by wrtpeeps on 2008-10-09
Slightly OT in that it's really no use to you, but I am studying XNA at the moment and it really is impressive.

---

### Post by rnodal on 2008-10-09
Hey Sydius,

Even though my project is in the very early stage of the development I was wondering if you mind giving my project a try just to get some feedback from you. It comes with a sample game, 4 demos and the source code for all the demos and engine. It also comes with a sample Codeblocks project file that allows you to open the project file and code away as long as you have the C++ compiler in Linux(G++) and Windows(Mingw). You also need the SDL, SDL_Image and SDL_Mixer. Like I said, the project is in still in planning but I released pretty much what I did for my school project that's why is called "Graduation". I would really appreciate your feedback so I can improve upon them. Thanks.

-r

---

### Post by pmasiar on 2008-10-10
IMHO you don't use C++ if you don't have time :-) If you are competent programmer, you can learn Python over a weekend, and Pygame is excellent game library. As most python libraries, is simplified compared to underlying C libraries, and easier to use. (Disclaimer: I never had time to master "proper" game library in C++).

Just a thought. In my experience, development in Python is 3-10 times faster compared to any project in C++ or or Java or other statically typed language, and so much better when programmer's productivity is the main goal.

---

### Post by Paul Miller on 2008-10-10
Let me suggest in addition to PyGame, you might check out Pyglet.  Generally speaking, when I see Python game libraries mentioned, and 3D isn't a requirement, these two are the first two on the list.

---

### Post by rnodal on 2008-10-10
> **pmasiar said:**
> IMHO you don't use C++ if you don't have time :-) If you are competent programmer, you can learn Python over a weekend, and Pygame is excellent game library. As most python libraries, is simplified compared to underlying C libraries, and easier to use. (Disclaimer: I never had time to master "proper" game library in C++).

Just a thought. In my experience, development in Python is 3-10 times faster compared to any project in C++ or or Java or other statically typed language, and so much better when programmer's productivity is the main goal.

I was about to jump on you again since the OP prefers something in C/C++ but the OP goals are well met with your suggestions :). 

Let me go ahead and warning you though, if you are planning on making in the future that if you are going to be building something more than just a clone of the game mentioned, in other words, it will require more performance you may want to then move out to some better for the job (The authors of pygame even admit it). 

So yea I do agree that pygame is a good suggestion but please if you do have the time to give it a shot to my project that would be nice just so I can hear your opinion that's all.

-r

---

