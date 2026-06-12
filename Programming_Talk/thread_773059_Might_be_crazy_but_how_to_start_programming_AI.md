---
title: "Might be crazy but how to start programming AI?"
date: 2008-04-28
forum: Programming Talk
---

### Post by Melhisedek on 2008-04-28
Ok folks,
in short I'm lousy at programming, did a few courses here and there... VB, C++, Java. But doubt I could code a function now :) Although I think I would be able to read code okish. 

Anyway... I was watching some "speed runs" through games (am at sick leave and have nothing better to do). And noticed how enemies can be very, very stupid at how they react to player. So I started thinking of ways to improve on NPC (Non Playable Characters) thinking and reactions, and I had a few ideas....

Than I started thinking how I should go about to implement those ideas. I ended up with 100 lines of "if statements" and I don't think that is the best way to do it :)

Needless to say I've been thinking about AI for past 2 days. Just incredible amounts of thinking and planning. Probably junk most of it but fun nonetheless.

So my question is, any ideas where to start? Just simple stuff, game related AI. See something... shoot, move, shoot, reload and such :) I was thinking of chess or Sudoku solvers but that waaaaaay over my head for now :)

Any help is greatly appreciated!
Thank you for your time!

---

### Post by defmomo on 2008-04-28
I tried once for a school project, and failed miserably. I used lines and lines of IFs and ELSEIFs, and it did what it was programmed to do, but it didn't like the unexpected, and wasn't very intelligent...
So IMO, from my previous experiences, and some research I did afterwards, if you want to build a true AI, one way to do it would be to program into it some kind  of pattern recognition capabilities, and knowledge base, so it can react to those patterns.
I am really not a pro on AIs, just giving my two cents... Hope it helps.

---

### Post by LaRoza on 2008-04-28
Paradigms of Artificial Intelligence Programming: Case Studies in Common Lisp

by Peter Norvig 

I hear it is good for this.

---

### Post by Melhisedek on 2008-04-28
Gonna check it LaRoza... thanks mate!

I was also thinking it would be good if I could see an example of a game AI? Simple stuff, like in shooters or even Pacman damnit :)

---

### Post by RIchard James13 on 2008-04-28
> **Melhisedek said:**
> 
Anyway... I was watching some "speed runs" through games (am at sick leave and have nothing better to do). And noticed how enemies can be very, very stupid at how they react to player. So I started thinking of ways to improve on NPC (Non Playable Characters) thinking and reactions, and I had a few ideas....

Than I started thinking how I should go about to implement those ideas. I ended up with 100 lines of "if statements" and I don't think that is the best way to do it :)

> 
So my question is, any ideas where to start? Just simple stuff, game related AI. See something... shoot, move, shoot, reload and such :) I was thinking of chess or Sudoku solvers but that waaaaaay over my head for now :)

Perhaps the best way forward would be to write a small test game. Probably using 2D graphics. have the player walk through a map with some enemies that shoot back. Make the game as simple as possible, only include the player, enemies and cover. Use very simple graphics and don't worry about the look. You might be able to use an existing open source game for this but I can't think of any. The game doesn't even need to scroll the screen it can be on one screen. You probably only need to cover collisions with weapons and maybe with the enemies and cover.

After you have the simple game you can start tweaking the AI. Try making them react to the player in different ways. Try making them use cover as appropriate. Ask how does the computer know where cover is? Try making the enemies work as a group.

---

### Post by LaRoza on 2008-04-28
> **RIchard James13 said:**
> Perhaps the best way forward would be to write a small test game. Probably using 2D graphics. have the player walk through a map with some enemies that shoot back. Make the game as simple as possible, only include the player, enemies and cover. Use very simple graphics and don't worry about the look. You might be able to use an existing open source game for this but I can't think of any. The game doesn't even need to scroll the screen it can be on one screen. You probably only need to cover collisions with weapons and maybe with the enemies and cover.

After you have the simple game you can start tweaking the AI. Try making them react to the player in different ways. Try making them use cover as appropriate. Ask how does the computer know where cover is? Try making the enemies work as a group.

Try Doom.

---

### Post by CptPicard on 2008-04-28
IMO before you can start properly with AI you need to have some grounding in typical classical algorithmics, in particular different kinds of searches. You have already come across with one really fundamental feature of AI... usually, explicitly hard-coding rules in if-then-else branches will not work. You need to be more general, and that requires analyzing the problem as it appears in each instance, and hard rules will be insufficient.

---

### Post by Melhisedek on 2008-04-28
Is there a source? Good idea nevertheless :P

---

### Post by CptPicard on 2008-04-28
Russell, Norvig: Artificial Intelligence, A Modern Approach

General algorithms book:

Cormen, Leiserson, Rivest, Stein: Introduction to Algorithms

---

### Post by Melhisedek on 2008-04-28
> **CptPicard said:**
> IMO before you can start properly with AI you need to have some grounding in typical classical algorithmics, in particular different kinds of searches. You have already come across with one really fundamental feature of AI... usually, explicitly hard-coding rules in if-then-else branches will not work. You need to be more general, and that requires analyzing the problem as it appears in each instance, and hard rules will be insufficient.

Yeah I noticed that when I started thinking about RTS games AI. I passed out ;) But it was such fun just making some basic rules. I'm so "pumped" about this right now, I can't sleep :P

---

### Post by pmasiar on 2008-04-28
First, you need to become decently skilled programmer. I recommend start with Python.
Then, learn the language of the project where you want hack AI. 
Alternative for un-patient: there are many frameworks to program your own 'AI bots' to compete against others.

---

### Post by RIchard James13 on 2008-04-28
Most simple games like pacman use very simple rules for their AI. As you get more complicated I believe that you need to add states to the AI. 

For instance in pacman the ghosts randomly choose which path to take. In space invaders and galaxian the aliens move in patterns pre-determined. In mario clones the enemies move backwards and forwards on the ground.

In some more complex games the bad guys try to move towards the player. But to make this not so obvious boundaries are placed on their movement, they may be able to only take certain paths (up,down,left,right), they may be restricted by speed. 

In FPS shooters there are many things to consider. Line of Sight for the weapon the enemy is holding. Amount of cover available. The players line of fire. Where can the AI move to? How does the AI know where the player is? Can the AI cheat and see through walls? Does it use sound cues? Can it communicate with others to determine the players position? What about the ability to crouch and lay prone?

Another thing to ask yourself is why is the player superior to an AI? When the player plays a game what clues do they use to get the best strategy? Has the level designer made it obvious that a certain room is safe but another room is dangerous and how do they convey that to the player?

---

### Post by coolkid5 on 2008-04-28
> **RIchard James13 said:**
> For instance in pacman the ghosts randomly choose which path to take.

Actually each of the ghosts behaves slightly differently, but they do pick paths which lead them closer to pacman. :)

---

### Post by RIchard James13 on 2008-04-29
> **coolkid5 said:**
> Actually each of the ghosts behaves slightly differently, but they do pick paths which lead them closer to pacman. :)

You are right. And they show behaviour states as well. If pacman is on the same line as them they move towards him. If he has eaten a power pill then then they will move away. Unfortunately I don't have a copy of pacman anywhere to see the actual behaviour but basically with a couple of simple rules they have a simple AI.

---

### Post by Melhisedek on 2008-04-29
Well I'm looking at Doom source code for the monsters:

P_enemy.c

And I'm overwhelmed :) Damn pointers :) So I think I'll have to start with waaaaay simpler stuff and build from there. Like someone said, I'll have to find some simple game with players and monsters, and see if I can figure out AI there. I thought about pacman similar AI last night. It is in fact very simple but as soon as you add maze, line of sight and ranged weapons it becomes much harder at least for me. 

Anyone knows of a simple open source game, similar to Pacman perhaps a bit more complicated. Maze, player and monsters moving in a grid. Think that is all that is needed for now...

---

### Post by Zugzwang on 2008-04-29
You could try RoboCode. This environment is designed for experiments in such a field. It's Java however and your task is to program some tank.

---

### Post by pmasiar on 2008-04-29
Game Maker has full clone (with sources) of Pacman, Invaders, and other games, and you can design your own games, including platform games. So you can look at the sources, see how it is done, and tweak it a little. 

GM is for Windows only, what's why we are making Linux clone, see my sig :-) Anyone is welcome to join.

---

