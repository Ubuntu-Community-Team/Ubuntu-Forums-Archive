---
title: "Basic GUI game design?"
date: 2006-05-14
forum: Programming Talk
---

### Post by tht00 on 2006-05-14
Alright.

So... I've played some of the asteroid games for Linux, and I haven't been all that impressed (KAsteroids and such).  Sure, they have nice sprite graphics and what-not, but they really don't have a decent feel of how asteroids should be and they don't do the game justice.  Maybe I'm just picky (I was a Subspace/Continuum player, FYI ;) ).

Anyway, I've been thinking about making my own.  I did make an asteroids game in HS programming a couple years back, and I very much enjoyed doing it, though, it could definitely use improvements... I used what I had learned on, which was VB6 (no classes :( ), but it was fairly easy to design, especially in the early stages.  I used an image box to draw lines and circles in (which was the ship, asteroids, and bullets), and I was able to just spew some debugging info into some labels, which would be cleaned up later.  So, I got it working, got a good grade, and put it on the shelf until a later project where I revamped it a couple times.  At one time, I did implement a design playing with sprites (bitblt), but it never got too far.

Launch forwards a couple years.  Now I'm a student at Purdue, going towards a computer science major.  I've been through a Java course (with some GUI design... that's a headache compared to the VB days) and I also discovered and have become hooked on Linux. :D But, alas, I've yet to find an asteroids game that I've truely enjoyed.  So, I'd like to start developing one -- partially to fill this void, but also to get some experience with general development on Linux.

So, I'm wondering what language would fit this best.  Cross-platform would be nice, but not a requirement.  To start with, I'd like to develop something just using basic drawing commands (lines, circles), but have the ability to use sprites later.  I've been impressed with MonoDevelop and C#, though, I haven't gotten far with figuring out how to draw crap.  Object-Oriented is a requirement, so C++ might work (I've had some experience with it in HS on command-line stuff).  I'd rather not use Java, though I guess I could.  I think I've seen enough of it lately (sick of it)... though, it *might* just be the best choice... and I am used to it for the time being.  Oh, and I'd like something with a C-style syntax.  That doesn't leave many languages left... C++, C#, Java... any others?

Any thoughts on where to start?  This isn't something I'll do overnight... probably be on-going for several years if it ever gets off the ground, working on it when I've got some extra time and feel like coding.

---

### Post by kb3hkg on 2006-05-15
It sounds like you have already narrowed down your options, but if you did like VB you might want to take a look at Gambas.

---

### Post by Gustav on 2006-05-15
I and a friend did a networked Astroids in a networking course about a year ago. We did it in Java but that was mainly because the course staff wanted that. If we had done it today we would probably have used Python or C.

Python with PyGame is really easy to use.

---

### Post by tht00 on 2006-05-15
[QUOTE=kb3hkg]It sounds like you have already narrowed down your options, but if you did like VB you might want to take a look at Gambas.[/QUOTE]

I've looked at Gambas before, and though it looks decent, I think I'll stay away from a BASIC-related language for now.

[QUOTE=Gustav]I and a friend did a networked Astroids in a networking course about a year ago. We did it in Java but that was mainly because the course staff wanted that. If we had done it today we would probably have used Python or C.

Python with PyGame is really easy to use.[/QUOTE]

Hmm... I've never really messed with python, though, I don't care for the looks of it's syntax, from what I've seen.  I keep hearing about how good of a language it is... so I might look into it.  It's OO, right?

Java might still be my best bet.

---

### Post by Revert on 2006-05-15
It supports OO (not strictly that paradigm, though).

PyGame really is a blast to mess around with.  Their [site]("http://www.pygame.org/projects/6") has a bunch of user created sample games, tutorials, and the like if you feel like looking more into it.  There're a few versions of Asteroids there, too.

---

### Post by sparklehorse on 2006-05-16
Hi there,

[QUOTE=tht00]
So, I'm wondering what language would fit this best.  Cross-platform would be nice, but not a requirement.  To start with, I'd like to develop something just using basic drawing commands (lines, circles), but have the ability to use sprites later.  I've been impressed with MonoDevelop and C#, though, I haven't gotten far with figuring out how to draw crap.  Object-Oriented is a requirement, so C++ might work (I've had some experience with it in HS on command-line stuff).  I'd rather not use Java, though I guess I could.  I think I've seen enough of it lately (sick of it)... though, it *might* just be the best choice... and I am used to it for the time being.  Oh, and I'd like something with a C-style syntax.  That doesn't leave many languages left... C++, C#, Java... any others?

Any thoughts on where to start?  This isn't something I'll do overnight... probably be on-going for several years if it ever gets off the ground, working on it when I've got some extra time and feel like coding.[/QUOTE]

in view of your wishes/requirements, I'd suggest you try qt/c++ and use opengl to do the drawing (using the opengl classes provided by qt). that'll give you cross-plattform too, plus there's plenty of reading material, tutorials, etc. 

though i haven't programmed any games, i did an application for my thesis using that setup, and got off to a rather speedy start.

---

### Post by Grey on 2006-05-16
Count another vote for some sort of Python.  Syntax is very much like C, and is quite easy to develop in.  Get used to the fact that white space matters really early on, and pretty soon you won't even miss braces anymore.  ;)

---

### Post by tht00 on 2006-05-17
[QUOTE=Revert]It supports OO (not strictly that paradigm, though).[/quote]

Similar to how C++ supports OO, but technically isn't OO in and of itself (ie Java)?

[QUOTE=Revert]PyGame really is a blast to mess around with.  Their [site]("http://www.pygame.org/projects/6") has a bunch of user created sample games, tutorials, and the like if you feel like looking more into it.  There're a few versions of Asteroids there, too.[/QUOTE]

Looks interesting, though, do you know of projects like this focused around C++ or C#?

[QUOTE=sparklehorse]Hi there,

in view of your wishes/requirements, I'd suggest you try qt/c++ and use opengl to do the drawing (using the opengl classes provided by qt). that'll give you cross-plattform too, plus there's plenty of reading material, tutorials, etc. [/quote]

I was thinking qt was used to build KDE apps?

[QUOTE=Grey]Count another vote for some sort of Python.  Syntax is very much like C, and is quite easy to develop in.  Get used to the fact that white space matters really early on, and pretty soon you won't even miss braces anymore.  ;)[/QUOTE]

I took a look at Python, but I don't think I want to make the change and start learning that *yet*.

---

### Post by Revert on 2006-05-17
[QUOTE=tht00]Similar to how C++ supports OO, but technically isn't OO in and of itself (ie Java)?[/QUOTE]

I'm not very familiar with C++, but from what I've heard, it is similar.

[QUOTE=tht00]Looks interesting, though, do you know of projects like this focused around C++ or C#?[/QUOTE]

Most other projects I know of are based more around specific libraries and aren't language specific.  [Example.]("http://www.ubuntuforums.org/showthread.php?t=127121&highlight=game+competition")

---

### Post by tht00 on 2006-05-19
[QUOTE=Revert]Most other projects I know of are based more around specific libraries and aren't language specific.  [Example.]("http://www.ubuntuforums.org/showthread.php?t=127121&highlight=game+competition")[/QUOTE]

Allegro looks great.  Any other suggestions?

Thanks. :D

---

### Post by tht00 on 2006-05-19
I think I might end up going with C++ and SDL.  Thoughts?

---

### Post by fct on 2006-05-20
SDL with C++ is nice, but SDL is so low level that it doesn't include a GUI toolkit to draw buttons, menus, etc. Fortunately, there are third party libraries like guichan that fill that void.

But SDL is worth it, specially because it allows you to use OpenGL for 3D games. I suggest you look at the SuperTux code to get the grasp of programming 2D games using 3D acceleration (it's basically applying textures over rectangles to make sprites, if I remember correctly).

Some other people have suggested using QT. Although QT is a very nice toolkit library, I recall it has some licensing problems for Mac OS and Windows ports. I'm not sure if those problems are still around, so if you go for QT you'll have to investigate that.

---

