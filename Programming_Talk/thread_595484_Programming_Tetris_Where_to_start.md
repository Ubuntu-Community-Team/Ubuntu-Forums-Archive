---
title: "Programming Tetris: Where to start?"
date: 2007-10-28
forum: Programming Talk
---

### Post by japtar10101 on 2007-10-28
First of all, I'm a Computer Science student in college with big dreams and little motivation, but I hope this goal would help me out: I want to program a tetris clone.  

Now, I've seen a few people who've tried this task with Java and C++,  but with terrible outcomes such as blocks going through each other, and inability to turn blocks before the blocks spazzes out and freezes the game.  Long story short, I know it's a hard game to program, and I'm practically stuck at even planning how to begin programming it (do I start with a 2-D array?  what programming language should I use?  what about image uploading?).  Any help on this rather naive (not to mention, very cliched) "project"?

By the way, I'm quite knowledgeable in Ruby and Java.  I'm currently learning Perl, and I'm trying to improve on C and C++ (and Assembly, too).  I plan to look into Python (I've tried learning Pygame, but to no success), Lua, and Tcl/Tk (for GUI programming) in the future.  I wanted to know if any of these languages are "better" at game programming.

---

### Post by slavik on 2007-10-29
anything with OpenGL bindings will suffice (C, C++, Perl, Python, Ruby, many others)

then you want to read up on colision detection and handling it.

tetris isn't very difficult. if you want a simpler starting task, try making a 2player pong clone (no AI)

edit: you could make a 2D array for your game field, it would help you solve some problems you might be having)

---

### Post by japtar10101 on 2007-10-29
> **slavik said:**
> anything with OpenGL bindings will suffice (C, C++, Perl, Python, Ruby, many others)

then you want to read up on colision detection and handling it.

tetris isn't very difficult. if you want a simpler starting task, try making a 2player pong clone (no AI)

edit: you could make a 2D array for your game field, it would help you solve some problems you might be having)

Err...Pong is really easy.  I can literally visualize it now: make the field a xy-plane.  Increment x-variable.  Decrement it if it hits the right paddle.  Increment it if it hits the left paddle.  increment y-variable.  Decrement if it hits the bottom wall.  Increment if it hits the bottom wall.  Stop the game if it hits left and right wall.

Ugh, even a caveman could do that.
Anyway, thanks for your support!  It made me feel a little more confident.

---

### Post by Wybiral on 2007-10-29
SDL would be a really good library for this. OpenGL is good, but might be a bit too deep to dive into for a simple 2d game like this (but if you plan to develop 3d applications, it's a must).

PyGame, as you've mentioned, is also a good library for this. What were you having trouble with getting into PyGame? It's basically a simplified interface to SDL.

---

### Post by pmasiar on 2007-10-29
I would suggest Pygame for games - what was the problem first time?

And I would strongly suggest joining existing project before starting new one. And before going to games with graphics and GUI, start with plain old text games and programs. Wiki in my sig has many links.

---

### Post by Ramses de Norre on 2007-10-29
I've made something of the same difficulty at college after two months of java lessons (it was some kind of maze in which you needed to find a treasure).
The only hard thing will be to draw the blocks and such using swing/awt.

And I would never use an array to store the game field... I'd make a coordinate and a "field entity" class and use a hashmap with the first as keys and the second as values.

If you use the OOP principles good, this wont be too hard.

---

### Post by japtar10101 on 2007-10-29
Thanks for all of your replies.  To be quite frank, the only reason I've never understood Pygame is merely because I don't have much time.  And I don't have much time working on this tetris game, either (although, I meant to try it merely for experience).  Once the winter vacation starts, I think I've got several good headways into it.

Now, something that caught my eye:
> **Ramses de Norre said:**
> I've made something of the same difficulty at college after two months of java lessons (it was some kind of maze in which you needed to find a treasure).
The only hard thing will be to draw the blocks and such using swing/awt.

And I would never use an array to store the game field... I'd make a coordinate and a "field entity" class and use a hashmap with the first as keys and the second as values.

If you use the OOP principles good, this wont be too hard.
I'm not exactly sure how a hash would help coordinate a field.  Either the keys or values would have to be coordinates, if anything.

Also, I was curious about creating smoother animation.  Whereas tetris blocks falls in spazzy increments, I wanted it to fall in a constant speed.  How would I simulate this?  As in, how would I store the current block formation at the bottom of the screen, while at the same time, render a "smooth falling" block?  I eventually want to give tetris attack, meteos, and lumines a try as well (although that's obviously too much from where I'm beginning).

---

### Post by evymetal on 2007-10-31
> **japtar10101 said:**
> Err...Pong is really easy.  I can literally visualize it now: make the field a xy-plane.  Increment x-variable.  Decrement it if it hits the right paddle.  Increment it if it hits the left paddle.  increment y-variable.  Decrement if it hits the bottom wall.  Increment if it hits the bottom wall.  Stop the game if it hits left and right wall.

Ugh, even a caveman could do that.
Anyway, thanks for your support!  It made me feel a little more confident.

Sounds like you know how to do graphics well enough (if not, I suggest Pygame - read the tutorials on the website).

Never written Tetris, but I'd suggest using an array/list to store a block, i.e.

[[0,1,1],
[0,1,0],
[1,1,0]] would be the wavy shaped block (you could use colours instead of 1).

Now implement matrices for the rotation operations.

Store the fixed blocks at the bottom in an array, and do colision detection on the non-zero entries of the block.

Other technicalities should work themselves out (you've got me interested in doing something like this now, if only I had time :-)

---

### Post by wolfbone on 2007-10-31
> **japtar10101 said:**
> 
Now, I've seen a few people who've tried this task with Java and C++,  but with terrible outcomes such as blocks going through each other, and inability to turn blocks before the blocks spazzes out and freezes the game.  Long story short, I know it's a hard game to program...


If Tetris is a hard game to program, perhaps it would help to study someone else's implementation:

[[IMG]http://img228.imageshack.us/img228/5521/screenshotjx0.th.png[/IMG]](http://img228.imageshack.us/my.php?image=screenshotjx0.png)

(yes - I am crap at playing it)

It isn't a very large program:

[source]( http://cvs.savannah.gnu.org/viewvc/emacs/emacs/lisp/play/tetris.el?revision=1.22&view=markup)

---

### Post by stinger30au on 2007-10-31
it would be so easy if we had a program like [dark basic for linux]("http://darkbasic.thegamecreators.com/")



or [game maker]("http://www.yoyogames.com/gamemaker") for linux

that way more non-programmers like me can make games for linux

---

### Post by japtar10101 on 2007-11-04
> **stinger30au said:**
> it would be so easy if we had a program like [dark basic for linux]("http://darkbasic.thegamecreators.com/")



or [game maker]("http://www.yoyogames.com/gamemaker") for linux

that way more non-programmers like me can make games for linux
Those programs are usually full of flaws and glitches.  It's normally preferred if you hard code it instead: if you find a glitch or a problem in it, you're more likely to be able to fix it.

While it ALWAYS helps to learn mid-level language like C, C++, and Java first, high level languages like Python and Ruby (both for free, see synaptics) are easier to learn, and less work to do in game programming.  Try them out first.  Don't lose your cool!

---

