---
title: "Shell Scripting: RPG Style."
date: 2010-01-20
forum: Programming Talk
---

### Post by Tp2357 on 2010-01-20
Hi. I've been thinking about creating a RPG by bash Shell Scripting... Anyone interested in helping? I'll need some room descriptions, and the like. The game structure would probably follow the tales of a criminal in the old west, or something similar. Of course, including different possible endings, NPC raids, and the like. (we'll see what we feel like adding. :) )

Most likely a "rouge-like" game ([http://en.wikipedia.org/wiki/Roguelike](http://en.wikipedia.org/wiki/Roguelike)). I might use python.. might be a lot longer, though, as I have very little previous experience. But the main structure of the program would have folders for each "level" and text files for each room, describing things to be picked up, ect.

**Not necessarily  Prompt Based, now, that We're using Python. (that mean that we might need some icons. Get that GIMP going!)

PS, Google Wave might work nicely for this, too. Have 8 invites left. :P

---

### Post by deer dance on 2010-01-20
If you could be more specific about the game and what needs to be done, I may be more interested.

---

### Post by nvteighen on 2010-01-21
Hm... My spidey senses tell me bash may harden this project a lot, but I may be proven wrong.

---

### Post by deer dance on 2010-01-21
> **nvteighen said:**
> Hm... My spidey senses tell me bash may harden this project a lot, but I may be proven wrong.

Not necessarily.

I've seen people on Windows use Batch scripts to create a full text-based RPG without much difficulty.

And if it's so simple accomplish of Windows with Batch, imagine how easy it would be with Bash on a *NIX?

---

### Post by nvteighen on 2010-01-21
> **deer dance said:**
> Not necessarily.

I've seen people on Windows use Batch scripts to create a full text-based RPG without much difficulty.

And if it's so simple accomplish of Windows with Batch, imagine how easy it would be with Bash on a *NIX?

Hm... never seen any, but I'd like to see how this advances.

---

### Post by deer dance on 2010-01-21
Plus, shell languages are great for making a game open source (really they're more or less forced to), anyone can easily add to, or modify a game to make new reditions of it.

---

### Post by Bios Element on 2010-01-21
Why not use python so you don't have to rely on bash? Then it'd be cross-platform + somewhat future proof.

---

### Post by deer dance on 2010-01-21
O_o

What other platforms do people use?

---

### Post by OgreProgrammer on 2010-01-21
I remember that the first Wing Commander game for dos came with a text adventure made with batch. Even back then I was into snooping through folders.

---

### Post by Tp2357 on 2010-01-22
Hey, Bios, I do believe that you Play SWC... I'm Jad Quelben :P
Anyways, I've updated the first post.

---

### Post by wmcbrine on 2010-01-22
The only reason I can see to do something like this in shell script is to prove that It Can Be Done. Python should be much easier, even factoring in your learning time.

---

### Post by Tp2357 on 2010-01-22
Alright, I'll prolly do that. PS, here's a B/W tree  made in gimp for this... let me know.

---

### Post by growlf on 2010-01-22
Python is my choice...   then if you progress nicely in the object based code for the textual portion, check out [PyGame]("http://pygame.org/").  Very easy, very cool - and lots of helpful folx there.  ..not to mention several metric killatonnes of examples are available. Books too.  Be sure to check out the online [PyGame Cookbook]("http://www.pygame.org/wiki/CookBook"). :popcorn:  Lots of recipes to start out with.

Now, if you want 3D, there is also [PySoy]("http://www.pysoy.org/") and another library from Disney Studios (but I forgot it's name).  If you want to really jump in deep water - try Torque, ***extremely*** nice stuff there from the folx at [Garage Games]("http://www.torquepowered.com/"), who are also extremely nice and helpful.  There is an example of an MORPG built in Python and Torque from [Prairie Games]("http://prairiegames.com/").  Check them out - it open source and a great forum to get your feet wet if you choose to delve that deep.

---

### Post by Tp2357 on 2010-01-22
Hmm... Never really thought about getting into 3d. I might get started with pygame (actually found it earlier today :P) Is the pygame Cookbook online, or is it a book I have to buy? Is it easier to write a terminal version, then progress to a gnome/KDE module? (sorry for all the questions... a little young to be programming this seriously.)

---

### Post by growlf on 2010-01-22
The PyGame Cookbook is linked in my earlier post - incase you missed it: [http://www.pygame.org/wiki/CookBook](http://www.pygame.org/wiki/CookBook).  It is online, and free.  3d is way fun.  But if you are just beginning... I would suggest that you start with where you are comfortable.  3D game development requires several other disciplines (such as 3D modeling and physics) that may slow you down initially.  I find that when I teach teenagers how to develop software, that slow downs can cause derailment.   I don't know if that applies to everyone, but I *have* noticed that it also applies to myself.  :)

As far as starting with textual vs graphic, I think that PyGame is a fine place to start.  Like I said - LOTS of examples and helpful people.  Also?  There are several things that are pre-done in the engine to make rapid progress a guarantee.  You can have a basic game with some very limited AI and user interaction in a single night.   ...and networking the following night :)

---

### Post by Tp2357 on 2010-01-23
Thanks growlf, I'll check that out.

---

### Post by growlf on 2010-01-27
I just remembered a note in a podcast that I listened to a few weeks back that mentioned a site on exactly this topic.  Check out [http://www.gamedev.net/reference/articles/article2259.asp](http://www.gamedev.net/reference/articles/article2259.asp).  Jay builds an entire RPG in Python/PyGame in a ***single*** week.  Now - keep in  mind that Jay is a _very_ accomplished developer and he did dedicate an _entire_ work week to this with no distractions - so mileage may vary. 

However, the work week was defined as 40 hours max - so no "time-packing" with 20 hour days as we devs tend to do.  He also produced a very playable game - better than you might expect with no prep time or planning/design time in advance.

The concept still stands on it's own, and he discusses the processes he used and methods to accomplish each task in the process. He even lists all the free resources that he found while building it.  A very good article.

[SIDE NOTE] I forgot to mention... Jay did not know PyGame in advance, but in fact learned it while implementing it in that 40 hour span.  It really is that easy.

---

### Post by lisati on 2010-01-27
<off topic>Please excuse me doing a rant, I'm slightly distracted by a meaning of "RPG" described here: [http://en.wikipedia.org/wiki/Report_program_generator](http://en.wikipedia.org/wiki/Report_program_generator) </off topic>

---

### Post by Tp2357 on 2010-02-12
I mean Role playing game... lol

---

### Post by growlf on 2010-02-12
Side note.. my son and I are currently doing a project together with Panda 3D and Python as he learns programming in Python the fun way. 

It is a very easy to use game engine from Walt Disney Studios and Carnegie Mellon - free to use and distribute, under a modified BSD license. [http://www.panda3d.org/](http://www.panda3d.org/)

I was amazed at how much faster he took to it than he did with PyGame.  It might have been the 3D part, and that he can export from his copy of Daz Carrara directly to the game.  Makes it much more fun when you can rapidly "see" that you have done something cool in #D that is entirely your own. 

Easy pipeline there :)  It will cleanly take several COMMON 3d model formats and animations.  That was always an issue with several other 3D rendering or game engines I have tried - unless you want to take on learning Blender as well (NOT for the average beginner)

---

