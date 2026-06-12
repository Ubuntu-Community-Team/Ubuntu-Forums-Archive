---
title: "Writing a game engine"
date: 2008-01-21
forum: Programming Talk
---

### Post by Peter1234123 on 2008-01-21
I want to write a game engine, and in the end, write a fully playable MMORPG, I have some knowledge of C/C++  and HTML/PHP/JS, what I was thinking of doing is making central databases, with MySQL, and writing a game with good graphics that can communicate with them, but also writing one in PHP, or maybe Flash or Java, and allowing it to communicate with the databases. I feel..this would help the game get a good player base, cause if someone's on vacation or something, or they don't have the best computer they can still play the game like anyone else can. My question is..how hard would it be to write this game?

---

### Post by aks44 on 2008-01-21
> **Peter1234123 said:**
> I want to write a game engine, and in the end, write a fully playable MMORPG,
[...]
how hard would it be to write this game?


I don't mean to discourage you, but since you wanna know... ;)

[http://sol.gfxile.net/mmorpg.html](http://sol.gfxile.net/mmorpg.html)> **So you want to make your own MMORPG..**
[...]
MMORPGs are huge projects. You can drop 3-4 quakes into one MMORPG. And even a quake clone is too much for majority of people.

  Realistically speaking you need a team of 10 or more developers for about four years, full time. And those 10 people had better know what they're doing to begin with.

(better read the whole article, it will give you a clearer idea)


Good luck. :)

---

### Post by pmasiar on 2008-01-21
best suggestion from the article is: join WorldForge. They have playable prototype, working on it since at least [Nov 2003](http://slashdot.org/games/98/11/03/102224.shtml) 

BTW WorldForge code is GPLed

from WF: unless you are God, "takes a lot longer than 7 days to create a world." :-)

---

### Post by kragen on 2008-01-21
> **Peter1234123 said:**
> writing a game with good graphics

If you mean "good" as in "3D", then my advice is the same as those before me - I know that if you have an idea, it can be hard to scale it back, but even producing a browser-based MMO, or a very simple 3D game, are very challenging and time consuming projects in themsvles. Don't forget that even once you've gotten past the coding stage, you have to come up with all the graphics, sounds, game content and ballancing before your finished game is going to be any fun to play. 

One idea is to look at getting involved in a larger project, but personally, large projects never really appealed, so my advice would be keep things simple until you've gotten to the stage where you think you could really contribute to a larger project, either with friends, or over the internet.

Don't underestimate the time and effort needed to produce polised games - even the really simple ones. I spent weeks making tetris, and still never got it to the point where I was really happy with the sounds, graphics, menus, and subtle things, like the change in speed per level, or the way that the controls work. (If you dont believe me, try it yourself :P). At the same time, in that week I learnt shedloads from the experience.

---

### Post by RIchard James13 on 2008-01-22
> **Peter1234123 said:**
>  My question is..how hard would it be to write this game?

MMORPG = millions of dollars of development costs.
Drop an M so you end up with Multiplayer Online Role Playing Game. Aim for something like 16 players, quite doable for a single person over a few years, depending on how much time you apply to it.

Smaller games cost less to run. Compare a sixteen player game that runs on one server as opposed to say Second Life which runs on 2000 debian servers.

There are more smaller games out there so to distinguish yourself you need to innovate more which is a good thing.

for a list of multiplayer games see [http://www.mpogd.com/]("http://www.mpogd.com/")

---

### Post by clasificado on 2008-01-22
Some very realistic comments :D

From the beggining, only the logic of a simple game is very problematic for the average object-oriented programmer.

From there, the sync in real-time with a very variable database is simply a killer feature. If you reach the point where your character has "lag" you can die with a place in heaven.

And im not talking about the screen representation :D

But is fun! you should try it! Also, you can join an existing mmorpg open source project, and learn a lot

clasificado

---

### Post by Paul Miller on 2008-01-22
Others have pretty well covered the fact that a 3D MMOG engine is really not a feasible project for a solo developer.  What nobody's mentioned so far though is that a 2D, single-player engine definitely *is* feasible.  

However, before writing an "engine" of any sort, I'd go and make a few standalone games, first, using libraries that are already available.  Then, use the "once, twice, abstract" pattern: the first time you need to do something, just do it (preferably in the simplest way that could possibly work).  The second time, adapt what you did the previous time to your current project.  The third time, you should consider abstracting that functionality into a library.

---

