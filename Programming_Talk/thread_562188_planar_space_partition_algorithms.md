---
title: "planar space partition algorithms?"
date: 2007-09-28
forum: Programming Talk
---

### Post by aks44 on 2007-09-28
Hi there...


Out of curiosity, I'm currently digging into planar space partitioning, namely the good old "*given a set of points on a plane, find all the points within a certain distance of a specific point*" (efficiently, of course ;)).

I'm aware of Delaunay triangulation (and Voronoi diagram), but I couldn't find anything really relevant besides that (plus, I'm still struggling at fully understanding it).


So I was wondering if any of you know any other decent plane partition algorithms, even if they are not as efficient as Delaunay (from what I read, Delaunay seems to be one of the most efficients, but too hard for me yet :(). I'm pretty sure I will use Delaunay at the end, but that's just a toy project so I want to be able to grasp what's involved under the hood...


The idea I have in mind would be some kind of simulation involving moving points, and range-constrained broadcasted messages between the points. The whole thing would be just a framework, with points behaviour (ie. moving, message sending & reactions to messages) fully scriptable.


Any ideas / comments? :)

---

### Post by hod139 on 2007-09-28
I'm not 100% sure what you are looking for, but some common planar space partitioning schemes are: quadtree (2d version of an octree), BSP, or 2D kd-tree.

---

### Post by aks44 on 2007-09-28
> **hod139 said:**
> some common planar space partitioning schemes are: quadtree (2d version of an octree), BSP, or 2D kd-tree.

Don't know how I managed to overlook the wikipedia "Space partitioning" article, which mentions them all... :-| Thanks for the pointers, I'm looking into it!

FWIW I'm trying to understand space partitioning algorithms from the ground up (and more precisely, how to solve that "proximity" problem I mentionned), for the sake of it.
When I'm done with it, I may (or may not) write that simulation I talked about. I have a few interesting ideas about it, I only fear that I'll lack the time to do it.

---

### Post by CptPicard on 2007-09-28
In all of the search structures that immediately spring to mind, your problem is the fact that your points are moving about. Typical search/partition structures are trees you build once and assume conditions don't change...

I was initially at a loss of why you are looking at Delaunay triangulation, but thanks for the heads-up about that.. I don't think I've ever really thought of things from that perspective :) To me it would seem like a good bet because your data is dynamic. You certainly don't want to be rebuilding your trees all the time.

Another possibility is putting together some sort of neighbourhood lists you update as you go, but I'm not quite sure how practical that would be (or that it wouldn't break under some conditions)...

---

### Post by aks44 on 2007-09-28
> **CptPicard said:**
> Typical search/partition structures are trees you build once and assume conditions don't change...

I was initially at a loss of why you are looking at Delaunay triangulation [...] To me it would seem like a good bet because your data is dynamic. You certainly don't want to be rebuilding your trees all the time.

Indeed, even though I'm primarily just trying to understand how computers can "grasp" this proximity problem, I'm trying to do it in a dynamic context.

However IIRC Delaunay updating is at best n.log(n) while kd-tree updating is only log(n). BSP and quadtree don't seem to fit well in that context. But again, I don't understand yet how those algorithms really work, so I may well be off the tracks.


One more precondition I forgot to mention: two points can't share the same location/coordinates (which should simplify a bit the algorithm).


FWIW that simulation I mentioned would be some kind of enhanced "[game of life]("http://en.wikipedia.org/wiki/Conway's_Game_of_Life")" including sight range, scriptable behaviour and so on...

I think that with such a basic mechanism as range-constrained message broadcasts we should be able to model environment awareness (yet at a very basic level). That's not really AI per-se, but it kinda looks like it anyway. :D



Who said I should be looking for a pure research job? :p Too bad I don't have the required level...

---

### Post by hod139 on 2007-09-28
Another fun spacial tree: [Interval trees]("http://en.wikipedia.org/wiki/Interval_tree").

You can also see if your library has this book: 
"[Design and analysis of spatial data structures]("http://www.amazon.com/Analysis-Spatial-Structures-Addison-Wesley-computer/dp/0201502550")"

---

### Post by CptPicard on 2007-09-28
> **aks44 said:**
> 
However IIRC Delaunay updating is at best n.log(n) while kd-tree updating is only log(n). BSP and quadtree don't seem to fit well in that context.

Yeah, building the whole thing is n log n... I actually thought you have come across with some faster local update mechanism that allows you to avoid constructing the triangulation from scratch (having thought about it more, local updates are probably impossible without forcing complete reconstruction of the triangulation)... and as I suppose most of your points move during a "round", updates are a bit of a moot point. 

If you do benefit from having a partial update, a kd-tree might be interesting, but you're still updating in n log n time total if everything moves... didn't remember its running times off the top of my head, it's been years since my computational geometry class :) It all really depends on whether the Delaunay building algorithm is in absolute terms faster than a total update of the tree... IIRC the triangulation building is a pretty intensive process.

One idea that could be of interest is that once you've built the triangulation, you don't neccessarily have to discard it straight away. The proximity information contained in the triangulation degrades over time, but I'm pretty sure you don't need to recompute before errors become too great...

Also, you can always divide your plane into a grid of buckets, and just reduce the size of the n^2 bruteforcing you would have to do without anything fancier...

---

### Post by aks44 on 2007-09-28
> **CptPicard said:**
> as I suppose most of your points move during a "round", updates are a bit of a moot point.

You made a point here... I didn't think of it that way. I was only looking at the complexity of **one** point update. But since indeed most points will move during a "round", it **may** be cheaper to rebuild the whole thing.

The question I still have though, is that points won't move much each "round". So most of them will keep their **relative** positions (which Delaunay is all about if I understood correctly).


> **CptPicard said:**
> <snipped complexity considerations>

Unfortunately I'm not good at this kind of theory. Anyway, regarding whole Delaunay rebuilding,> **Wikipedia]The expected running time in two dimensions in this case is O(n^(3/2)) although the worst case continues to be O(n^2).[/QUOTE]Which would be much cheaper than n points * n.log(n) update.


Regarding kd-trees,[QUOTE=Wikipedia (again :p)]# Building a static kd-tree from n points takes O(n log n) time.
# Inserting a new point into a balanced kd-tree takes O(log n) time.
# Removing a point from a balanced kd-tree takes O(log n) time.[/QUOTE]
So whatever option I'd choose (either full rebuilding or point-per-point updates) I'd end up with n.log(n) anyway, if I understand correctly.


[QUOTE=CptPicard said:**
> One idea that could be of interest is that once you've built the triangulation, you don't neccessarily have to discard it straight away. The proximity information contained in the triangulation degrades over time, but I'm pretty sure you don't need to recompute before errors become too great...
Due to the nature of the intended simulation, it could indeed be interesting, as there's no need to be really *exact* (BTW this sort of looks like my above remark about points keeping their relative positions, maybe we're on something here?). Gotta think about that...

> **CptPicard said:**
> Also, you can always divide your plane into a grid of buckets
Already thought about that, but... how to cross "bucket" boundaries? Unless I can find a way to make them "overlap" when needed (but I have no clue how to do it).



Anyway thanks for your insight. Although I don't quite grasp the whole thing yet, I'm under the impression you have some very relevant points.
I'll have to "digest" all this information...

Keep it comin' ;)



@hod: sorry that's enough for today, I feel like my head's gonna explode, so I won't look into Interval Trees until tomorrow... ;) Oh well, I guess I just love hating maths... :p

---

### Post by CptPicard on 2007-09-29
> Unfortunately I'm not good at this kind of theory. Anyway, regarding whole Delaunay rebuilding,Which would be much cheaper than n points * n.log(n) update.

You probably typoed that one, but I'm sure you mean than "n points * log (n)" update. :)

> Regarding kd-trees,
So whatever option I'd choose (either full rebuilding or point-per-point updates) I'd end up with n.log(n) anyway, if I understand correctly.

Yes. Somehow I'm getting the distinct feeling you would gain very little in this problem by rebuilding your tree each round like that, because we're losing the all-important previous relative positional information -- trees aren't good at making use of that previous state...

> Due to the nature of the intended simulation, it could indeed be interesting, as there's no need to be really *exact* (BTW this sort of looks like my above remark about points keeping their relative positions, maybe we're on something here?). Gotta think about that...

Yeah, that is exactly what I meant... if you already have some sort of triangulation, it's probably 99% good for the next round too, so why waste time rebuilding from scratch? This in particular as you don't really need the Delaunay properties to hold, although it gives a pretty triangulation... *although* I have a nasty feeling that it's having the Delaunay triangulation, that is, the Voronoi tesselation, that actually helps us in making sure that the search recursion along the triangulation doesn't miss some of the neighbours you want as you advance along the edges (it could be that you end up outside of your circle of interest, but you should still go on back into it from there to get all the points).

I am really drawn to the Wikipedia bit about "retriangulation of affected parts of graph", but seriously, I think we're again coming to a problem that probably all parts of the graph eventually end up being "affected" because all points move, esp. when keeping hold of a strict Delaunay requirement...

Now, what I am thinking of is a kind of test after every round, starting from something like a Delaunay triangulation... suppose there is a triangle ABC, with A as our vertex of interest. Now, say that D is the vertex that is both a neighbour of B and C. Now if AD < AB+BD and AD < AC+CD, D is closer to A than going through its neighbours. Then, if it is also closer than k, your communication distance, you might want to consider adding it to A's neighbour list. Also, if D moves beyond k, you might no longer want to keep it in A's list.

You get a sort of proximity graph where you try to maintain edges to all nodes that are closer than k... I'm not sure if this degenerates badly or has counter-examples, but is a possible candidate and it attempts to preserve proximity information from earlier rounds. :)

> Already thought about that, but... how to cross "bucket" boundaries?

The idea here would be that you have some limited range, say, k, and say your buckets are k units wide, so at worst you need to check in adjacent buckets to find neighbours. It really is the easiest way that comes to mind, and I'm almost sure that it's also the fastest if your buckets are small enough -- it of course has a really nasty worst case :) That, of course, you can handle by splitting your offending bucket into a smaller subgrid, and building a kind of tree out of those.


> Anyway thanks for your insight. Although I don't quite grasp the whole thing yet, I'm under the impression you have some very relevant points.
I'll have to "digest" all this information...

Glad I can try to help you with this, it sounds like an interesting problem and is close to the sort of stuff I actually did as a part of my Master's thesis -- there was this placement algorithm for mobile sensors in a network, and they need to find their neighbours for their ad hoc communication structure too.. :)

---

### Post by aks44 on 2007-09-30
Now that I understand a bit (but not much more...) how space partitioning works, I'm even more lost than before. :)


After thinking some more about that, I came up with the following requirements:
- as stated before, points will move but most of them will retain their relative positions.
- each and every point may query different ranges, depending on its (scripted) properties.


I guess that before attempting to optimize algorithms I don't fully grasp yet, I'll just use some stock algorithm (eg. one of CGAL's range searches) and rebuild the search tree each and every round for now. Properly encapsulated, it will be a breeze to replace the search backend later on anyway.

When I'll have something up and running I'll then be able to identify patterns more easily...


Again, thanks both of you for the pointers, it's been quite instructive. :)
I'll post again whenever I have something to show, or probably sooner when I'll need more help... :p

---

### Post by CptPicard on 2007-09-30
> **aks44 said:**
> 
- each and every point may query different ranges, depending on its (scripted) properties.

This makes it more difficult IMO. Having a fixed constant range restricts the problem nicely. :)

> Properly encapsulated, it will be a breeze to replace the search backend later on anyway.

If/when you get this done, would be cool to see the code -- this is, on the other hand, something I am bad at and could use a lesson in... I always couple things too tightly in designs like this :)

> I'll post again whenever I have something to show, or probably sooner when I'll need more help... :p

Waiting with interest. Using this kind of an agent platform it would be easy to for example demonstrate certain mobile sensor network node deployment algorithms... and some data aggregation/diffusion methods too. It could be used to implement emergent pack behaviour by diffusing observations throughout the population...

Btw, unless you're really interested in just doing this as a coding exercise; these kinds of frameworks exist already and are used in this kind of research...

---

### Post by aks44 on 2007-09-30
> **CptPicard said:**
> If/when you get this done, would be cool to see the code [...] Waiting with interest.

Stay tuned then. Just don't expect me to do it promptly, you've been warned... ;)


> **CptPicard said:**
> unless you're really interested in just doing this as a coding exercise

As I stated before, my primary goal is to understand how space partitioning works, especially "proximity awareness".
Since I have hard time understanding the naked theory, I guess I'll just have to dive in, in hope that I'll ultimately get it. :p

---

### Post by CptPicard on 2007-09-30
A good-looking survey paper for you:

[http://cis.poly.edu/chiang/cg-survey.ps.gz](http://cis.poly.edu/chiang/cg-survey.ps.gz)

Also at least scholar.google.com produces a great deal of interesting material with "dynamic voronoi diagram"... like

[ftp://ftp.inf.ethz.ch/pub/publications/papers/ti/grpw/KVD.ps](ftp://ftp.inf.ethz.ch/pub/publications/papers/ti/grpw/KVD.ps)

(Didn't actually read it yet but topic is aptly put "Dynamic Voronoi diagrams" which is exactly what we need here...

---

### Post by aks44 on 2007-10-01
Thanks for the links... though they are a bit too complex for me to understand it all. There are very interesting things in it anyway (especially the survey, as it is more general).


FWIW I settled for a range tree for now, at least BTrees are something I can understand easily. :p
Plus I'll have complete control upon the internals, which is good IMO during the initial development phase.



Now, another (kinda unrelated) question...
For convenience I was going to use boxed scalars, mostly to avoid overflow problems. In C++ this is not a problem, but what about handling those boxed types in a scripting language? (FWIW I'm planning to use Python at the beginning)

IOW is it easy to write OO bindings for Python?

Granted that's a bit far-sighted for now since I've written only a few headers, but I'd rather design that thing correctly...

---

