---
title: "Finding a team for a game project"
date: 2007-02-24
forum: Programming Talk
---

### Post by _Ozzi_ on 2007-02-24
Hi there!

I'm looking members to open source game project that I've started.

Project started allmost accidentally when I started to learn C++ / OpenGL and SDL programming eight months ago, so I'm not so high learned programmer -> this is very good project for programmers those wants to learn same things that I do ^^. 

Gurus are very welcomed too!! :D

The goal is 3rd person Multiplayer Online Role Play. Yes I know that everyone have same kinda project, but this is currently only "learning to program" - project.

You can find more info from: [HERE!]("http://freeworld.hopto.org/viewcvs/fwc/README?sortby=date&view=markup")

---

### Post by Wybiral on 2007-02-25
Why not... I'll help out.

Have you ever made an RPG before?

Have you ever made a networked game before?

If neither of these two, then I suggest you pick one to learn before jumping into both!

But, regardless, I'm decent with C++/OpenGL/SDL, I can write midi's... And I am OK at blender. So just PM me and I'll see if I can't pitch in some.

---

### Post by _Ozzi_ on 2007-02-26
> If neither of these two, then I suggest you pick one to learn before jumping into both!

Yes, I realize that. I thing that I'm feet on ground even I started this huge time eating project, and I really thing that I know my limits. And yes I'm really thinking that one piece in a time.

I'm planning this project so that in this point most important is an editor part. In this section that the game(client) is mostly for testing and base for an editor since editor uses same code than game part.

When the editor comes that point that it's possible somehow use for creating game maps, I'll change main focus for the game part and I leave the editor in a second place.

And finally when the game works alone, I'll start that server at full speed and the game gets a second place. In this point the editor should be "ready" and need very less time anymore.

Finally, after the years( ? ),  when the server side is working should the game client be very "ready".

I also realize that this is very huge project and sooner or later I need some partners. Sooner is of course better cause in this way everyone who are working with this project are very familiar with it when it's "ready".

I also understand that there is no very many skiller programmer/artist who want's to waste their time for a project in this state. There's thousands dead projects, similar of this, I know. That was another reason why I asked if there is anyone who is also learning same things as I.

But, back into this situation..

Now I'm stuck about choosing technic for terrain tile texturing. I'm trying to figure out how I do kinda base texture(grass, snow, sand, rock, etc.)  that smoothly changes to another and on those base textures should be "detail" textures as roads, fallen leaves, etc.

Any ideas?

---

### Post by Wybiral on 2007-02-26
Well... My point is that you should start smaller than that. Make a few networked games and a couple of RPG engines before you set sail on tackling them both.

Also, you never mentioned the method you are using to store/render the terrain or if you've used various types of 3d terrains before.

I also disagree with starting on the editor... If you do that, you will need to make a lot of assumptions on what your engine is capable of and since you may not be able to incorporate all of your original idea's, you will waste a lot of time writing an editor for them. My vote is that you start with a working game engine since that is the most important piece of the game. You need a strong networkable game engine capable of what you are trying to accomplish, which brings me to another point...

Maybe you should look into using another game engine. One that already exists. Otherwise you will spend so much time working on the engine that the game wont get very far at all. A good engine is a HUGE undertaking.

At any rate... The engine should probably come first. You can always write an editor to build levels for your engine... But it's harder to write an engine to keep up with the features you've already dedicated yourself to in the editor. Especially since the editor may need to run your engine in order to test the levels during editing (depending on what you have in mind for an editor)

---

### Post by pmasiar on 2007-02-26
> **_Ozzi_ said:**
> I also understand that there is no very many skiller programmer/artist who want's to waste their time for a project in this state. There's thousands dead projects, similar of this, (...)


... and there are projects like [http://www.worldforge.org/](http://www.worldforge.org/) which do most of you ever dream to do, in spades.

Sorry to wake you up from the dreaming - free software exist for a long time, thousands of extremely smart people spent hundreds of hours each to create excellent projects, and probability of a beginner like you making something usefull is *zero*. It is very, very hard to find a niche where is no existing free software project - usually there are more than one. So don't waste your and our time, join existing project, learn how stuff is done, learn from smart people. When you will know what they do wrong, what you can make differently, you can either suggest improvements or fork it. 

Untill then, your project is just a dreams of a random wannabe noob, and waste of perfectly good electrons.

I know you are afraid of jumping into existing big project and having to learn a lot before you can contribute - and yes it is true. But on the upside, you will learn from working code, with valid proven design, and you do not have to wait years untill your contribution will be noticed by others. If you can fix a bug, you will contribute right there. If you can think off a feature, or implement a suggestions of someone, we all free software users are even better off.

So don't start like a wannabe dreamer - start like a disciplined soldier of free software army :-)

---

### Post by _Ozzi_ on 2007-02-26
> Also, you never mentioned the method you are using to store/render the terrain or if you've used various types of 3d terrains before.
 
In this stage terrain is stored in heighmap array and engine uses geomipmapping for drawing. Another good and fast that I tested was ROAM, but I really didn't get how I ever do tile system on it. Geomipmapping is very fast and simple, and good looking enough for me, I tought. I also tested couble of my own technics with triangle strips and vertex arrays(and VBO's). I managed them really fast too, but no real time terrain geometry change was possible. Actually I really don't know Is there any reason to change terrain geometry anywhere than editor, but I wanted to keep that possibility with in the engine.

> The engine should probably come first.

Yes, It really should come first. In this case the editor uses same engine that game does. Of course the engine is most important. Everything runs on it, even my editor, it uses same core than game have. I'm trying keep things simple, clear and avoid double work and I thing that this way it's easy to test everything I do.

> Maybe you should look into using another game engine. One that already exists. Otherwise you will spend so much time working on the engine that the game wont get very far at all.

In a first point I really deep think that. I downloaded allmost every free engine that I found and tested them,  but there was couble reason why I choosed looong way, and most important was that I want to learn. I have no reason hurry to make game. I never get my livings from that project. It's a hobby.
Another reason was that I want keep count of extra libraries as less as possible.

---

### Post by Wybiral on 2007-02-26
> In a first point I really deep think that. I downloaded allmost every free engine that I found and tested them, but there was couble reason why I choosed looong way, and most important was that I want to learn.


You want to learn... Game making or engine writing? Believe me, they are two COMPLETELY different areas. If you haven't written an engine, I suggest not writing one WHILE you're writing a game. If you want to write a game, use an engine or a game maker. Most of the people that are actually writing the games and doing art for them don't touch the engine. That part is reserved for the programmers, not the game designers. Most people who write game engines don't make games... They're too busy working on perfecting the engine.

You may need to ask yourself if you are writing a game, or a game engine and adjust your plan accordingly, because they are both enormous task's to undertake and not something you will be able to learn as you go while working on both.

---

### Post by timjayko on 2007-02-27
Well.. I know nothing of programming.. but If possible I would love to assist with the ideas/story etc.  and I create music I would be honored to make music for the game.. here is a small library of music I have composed [www.stage.fm/timjayko](www.stage.fm/timjayko)

hope I can help

Tim

---

### Post by ssam on 2007-02-27
the linux games tome has a forum for games programmers/artists to get together.
[http://happypenguin.org/forums/viewforum.php?f=12&sid=f126e1afb5c80581c3c8372a1f074bf0](http://happypenguin.org/forums/viewforum.php?f=12&sid=f126e1afb5c80581c3c8372a1f074bf0)

---

