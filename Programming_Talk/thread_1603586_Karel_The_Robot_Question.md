---
title: "Karel The Robot Question"
date: 2010-10-22
forum: Programming Talk
---

### Post by zackj3 on 2010-10-22
I'm very new to programming / C++, and I have stumbled on this problem for a few hours now and was curious if someone can help.

Assume Karel is on a street corner, and he needs to check the 4 adjacent street corners around him (north, south, east, west). It is guaranteed that one and ONLY one of these adjacent corners contain a random number of beepers. 

My problem is just to get Karel to check each corner and return back to the original street he starts on.

Also, there is the possibility that his front is blocked by a wall

if (frontIsClear)
   Move();
   if (nextToABeeper) 
   count the beepers (i have a function already for this)
else
   TurnLeft();
   TurnLeft();
   Move();

this isn't right though. any suggestions?

---

### Post by Some Penguin on 2010-10-23
*shrug*  How did Hans and Gretel plan on finding their way back through the forest?

---

