---
title: "FAQ: I want to start my own project, how long it will take?"
date: 2008-02-06
forum: Programming Talk
---

### Post by RIchard James13 on 2008-02-06
The answer to the question is complicated because many factors can affect the time taken to finish the project.

**The most important factor however is the *focus* required to keep going at a project even when it seems that it is boring. If you lack that focus your project will *never* get finished!**

Some factors to take into account
[LIST]
[*]Have you undertaken and completed a project before?
[*]Have you written a similar program before?
[*]Are you familiar with the language/tools/libraries you will be using?
[*]How much time can you personally allocate to the project per week?
[*]How many projects at once are you working on?
[*]Do you have other commitments such as family, job, sport, etc?
[*]Do you have any other people helping you with the project?
[*]Does your project depend on someone else's project being completed first?
[*]Are you familiar with using Source Code Management tools?
[*]Are you familiar with project management?
[/LIST]

It is very hard to give accurate time estimates unless you have done the work before and know how long it will take you. Even in the large companies making software there are problems with estimation.

Of course the biggest factor in any project is "Complexity"

The more features your project has the more complex it is. The less you understand about the problem you are trying to solve the more complex it is.

Simple programs take less time to complete.
Complex programs take more time to complete.

In general I find most people underestimate the time it takes to complete a project.

Some sample estimates from my point of view are (which is limited mainly to game programming) these are times I believe it would take me to complete each task. Assuming I worked approx 18 hours per week.

Tic Tac Toe -> hours
Breakout -> weeks
Tetris -> weeks
Space Invaders -> a few months
Shoot em up like R-type -> 6 - 18 months
Pacman type game -> weeks
2D Platform game -> 6 months
Nethack Style RPG game -> months
simple 2D RPG game -> 1 - 2 years
simple 3D RPG game -> more than 2 years
simple Multiplayer 2D RPG -> 1 - 3 years
very simple 3D shooter -> 1 year - 2 years
3D shooter on par with Quake -> 5 years
3D shooter on par with Quake 4 -> 10 years
3D shooter on par with Crysis -> 50 years
MMORPG like World of Warcraft -> 200 years

---

### Post by pmasiar on 2008-02-06
Thanks, Richard, You are the first! 
I added your post to [FAQ portal page](http://ubuntuforums.org/showthread.php?p=4274830)

I would recommend to add FAQ to the title, so it will be more obvious that your post is FAQ candidate (to be linked to the portal), not genuine question as I thought before and almost ignored it.

Ind it would be waste of good work.

Thanks again!

---

### Post by Acglaphotis on 2008-02-06
Uhm... I think i read somewhere that a MMORPG could be made in 4 years by a 10 man team, so i think 200 (and 50 years for Crysis) years is a little exaggerated.

---

### Post by skeeterbug on 2008-02-06
> **Acglaphotis said:**
> Uhm... I think i read somewhere that a MMORPG could be made in 4 years by a 10 man team, so i think 200 (and 50 years for Crysis) years is a little exaggerated.

Not really. He is figuring a single person only working 18 hours per week.  4 people working an 8-10 hour day is double than what he would put in for a week.

---

### Post by RIchard James13 on 2008-02-06
With Crysis on a rethink it might be more like 20-25 years. Because it is basically space invaders with very advanced graphics. If I did a similar game using only ASCII graphics it could be done in less than a year. In this case graphical complexity is the problem.

With the MMORPG I say like World of Warcraft. WOW has exceeded 10million subscribers [http://www.gamasutra.com/php-bin/news_index.php?story=17062]("http://www.gamasutra.com/php-bin/news_index.php?story=17062")
Therefore one might deduce that the "game" has to handle at least 1 million people playing it at the same time. If you cut the graphics out and had say only a text MUD interface you might cut 10 years of development time on the client, maybe another 10 on the server. But you still have to cope with the data of 10million subscribers and the possibility that 1/10th of them might play at the same time.

Linden Labs uses over 2000 servers to run Second Life. But they cheat because the game is not distributed. If many people show up on one location then one server takes a hit and slows that location down. WOW is distributed AFAIK.

So to build something like WOW I need to
[LIST]
[*]Write a database that can handle in excess of 10 million players and all their stats.
[*]Write a distributed system that spreads that load, not just across one server farm but across server farms in different continents.
[*]Somehow write a game system running on the system that can concurrently deal with millions of player interactions.
[*]Build the world itself
[*]Watch out for people trying to hack it at all levels, the game, the servers, message boards etc
[*]Write a scripting language that makes it easy to add things to the world
[*]Write the scripts that make the entire game world seem like a living entity
[*]I could go on but just thinking about all the steps required to make that game makes my head hurt
[/LIST]

An example of the problem might be say player X gives player Y a gold coin. Now the system needs to extract the database record of player X and player Y and update that. That is pretty easy unless the records are held on a different continent. So you end up needing databases to talk to each other, probably through the game engine. Or you need to make one database and make it distributed across all those servers. Now with 1 million people playing there might be 100,000 such transactions going on each second. That is not too bad until you realise the system is working in real time so if player X gives something to player Y and player Z tries to steal it off player X at the same time. What happens?

Don't even get me to think about collision detection between 1 million players in 3D distributed across the globe in real time. I think I'll go and program Naughts and Crosses.

*EDIT*
Of course the point of this thread is not to argue how long it would take to make such a program but rather to point out that more complex programming projects take more time. Also some problems seem simple on the surface but as you begin to study how to solve them you realise that they are much more complicated than you first thought.

---

### Post by Sam on 2008-02-06
Should be stickied !

---

### Post by Daveski on 2008-02-06
> **RIchard James13 said:**
> Don't even get me to think about collision detection between 1 million players in 3D distributed across the globe in real time. I think I'll go and program Naughts and Crosses.

Only a problem if all 1 million were in the same location. Surely this would be partitioned, and I even think that the central engine really only needs to look out for the roughest of likely collisions as the clients themselves could do the fine detail work. Let's face it, as a player, your PC is not being sent the location details of all 1 million players, it only has to render in 3D the players that are 'in range'.

---

### Post by LaRoza on 2008-02-06
Added to a current sticky.

---

### Post by aks44 on 2008-02-06
> **Daveski said:**
> Only a problem if all 1 million were in the same location. Surely this would be partitioned, and I even think that the central engine really only needs to look out for the roughest of likely collisions as the clients themselves could do the fine detail work. Let's face it, as a player, your PC is not being sent the location details of all 1 million players, it only has to render in 3D the players that are 'in range'.

IMHO you're making the very same point RIchard James13 was making: what you suggest (which is quite close to reality) adds even more complexity to the code (compared to Richard's description), hence increasing again the development time. :)

---

### Post by RIchard James13 on 2008-02-07
> **Daveski said:**
> ... I even think that the central engine really only needs to look out for the roughest of likely collisions as the clients themselves could do the fine detail work...

The clients should never have anything to do with the game logic, that way people can't alter their clients and cheat. The client program should display data and receive data. The game should run on the server.

I had to reply to this because I can remember several instances of games offloading work onto the clients only to have people use that to cheat. I don't want any one else to fall into the same trap. The most common place this occurs is in graphics rendering. Should the client code be able to decide what the player can see or not? Some people might rewrite the client so players can look through walls.

---

### Post by C0pac3t1c on 2009-01-18
Wonderful thread

---

### Post by Jacob_Hacker on 2009-10-22
Thank you for this I will post it on [http://cplusplus.com](http://cplusplus.com) :)


Some sample estimates from my point of view are (which is limited mainly to game programming) these are times I believe it would take me to complete each task. Assuming I worked approx 18 hours per week.

Tic Tac Toe -> hours
Breakout -> weeks
Tetris -> weeks
Space Invaders -> a few months
Shoot em up like R-type -> 6 - 18 months
Pacman type game -> weeks
2D Platform game -> 6 months
Nethack Style RPG game -> months
simple 2D RPG game -> 1 - 2 years
simple 3D RPG game -> more than 2 years
simple Multiplayer 2D RPG -> 1 - 3 years
very simple 3D shooter -> 1 year - 2 years
3D shooter on par with Quake -> 5 years
3D shooter on par with Quake 4 -> 10 years
3D shooter on par with Crysis -> 50 years
MMORPG like World of Warcraft -> 200 years


~RIchard James13

---

### Post by daasdingo on 2010-01-23
very nice; 
thank you that gives all these MMORPG-first game
people a bit of an overview ;)

well, we made the same mistake in believing we could do a 
very simple 3D-rpg in 1-2 years xD

opengl is a lot more complex than you would expect at first

---

### Post by vishurockssrivastava on 2013-01-16
My theory on this is that the person who is actually doing the project must do it for a good reason and time shouldn't be a constraint. You shouldn't do it just to do it or get it done. Do it because you like to do it.

---

