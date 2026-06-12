---
title: "How is the destination path calculated in strategy games? (Dijkstra's algorithm)"
date: 2012-09-04
forum: Programming Talk
---

### Post by hakermania on 2012-09-04
Most strategy games let you choose one or more characters and point with your mouse to a specific point. When you click at this point, then your character(s) move, taking the shortest possible path.

How is this implemented into games? I've thought of the Dijkstra's algorithm ([http://en.wikipedia.org/wiki/Dijkstra's_algorithm](http://en.wikipedia.org/wiki/Dijkstra's_algorithm)) but, then, there are maps out there that their grid points (in every strategy game your character moves into a grid) should exceed the million by far. So, including each of these points inside this algorithm should take ages to calculate the shortest distance. Consider your character(s) being on the one side of the map and you choose to move them to the other side. How many possible paths have to be calculated?

---

### Post by trent.josephsen on 2012-09-04
[NetHack's sources are available online](http://nethackwiki.com/wiki/Hack.c#findtravelpath), but I don't know whether that is any particular named algorithm (I only glanced through it). If memory serves, though, it's not truly shortest-path.

If I were asked to write such an algorithm, I'd probably try to guess my way through most of it. Perhaps if you broke the grid into chunks and tried to create a travel path through each chunk (basically running the same algorithm on the super-grid and then on each individual sub-grid within a chunk). It wouldn't be strictly shortest-path, but most maps exhibit patterns that would make it indistinguishable from a true shortest-path algorithm if you were merely casually examining it.

---

### Post by mehaga on 2012-09-05
Was it "A* algorithm"  or something like that?  Anyway, I don't think they calculate the entire path at once.

---

### Post by dagoth_pie on 2012-09-05
> **mehaga said:**
> Was it "A* algorithm"  or something like that?  Anyway, I don't think they calculate the entire path at once.

Yes, A* is right. Basically think of it as a the first best path. It doesn't calculate all possible paths, I think it calculates a certain number of possible paths, and goes with the shortest of those. 

Thinking back to a game like the original Age of Empires, I think this is how the "Advanced Pathfinding" option worked, just boosting the number of possble paths checked.

I would guess that Dijkstra's algorithm would give *THE* shortes route, at the cost of taking a lot longer.

---

