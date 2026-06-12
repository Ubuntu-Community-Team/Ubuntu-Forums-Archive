---
title: "bipartite graph"
date: 2011-11-22
forum: Programming Talk
---

### Post by Mr.Pytagoras on 2011-11-22
Hi

I have a task which I can't solve

The problem is that we have N cites connected with M routes and I need to place a depo in those cites so than at each route there is max 1 depo.

So far I figured something like this:
Making the cites a vertex and the routes an edges I have to proof that the graph is a bipartite, in that case the graph's vertexes can be divided into 2 groups, one group has a depo and the another one hasn't and on each edge there is only one vertex with depo.

Is this right?

Can you advice me some algorithm how to do it?

EDIT:
Each route starts in one city and ends in another one, doesn't go through more cites

---

### Post by Arndt on 2011-11-22
> **Mr.Pytagoras said:**
> Hi

I have a task which I can't solve

The problem is that we have N cites connected with M routes and I need to place a depo in those cites so than at each route there is max 1 depo.

So far I figured something like this:
Making the cites a vertex and the routes an edges I have to proof that the graph is a bipartite, in that case the graph's vertexes can be divided into 2 groups, one group has a depo and the another one hasn't and on each edge there is only one vertex with depo.

Is this right?

Can you advice me some algorithm how to do it?

EDIT:
Each route starts in one city and ends in another one, doesn't go through more cites

But what if the graph isn't bipartite?

---

### Post by Mr.Pytagoras on 2011-11-22
In that case depots can not be placed at each edge max 1 time. (not sure:confused:)

How can I determine whether the graph is a bipartite? Is there some algorithm?

---

### Post by Bachstelze on 2011-11-22
> **Mr.Pytagoras said:**
> In that case depots can not be placed at each edge max 1 time. (not sure:confused:)

How can I determine whether the graph is a bipartite? Is there some algorithm?

One way is to take an arbitrary vertex v and perform a [BFS](http://en.wikipedia.org/wiki/Breadth-first_search) traversal of the graph starting at that vertex. Then check that each edge (of the original graph of course, not the BFS tree) connects a node of even depth (in the BFS tree) to a node of odd depth. If this is true, the graph is bipartite, and you can simply place depots at either all vertices of even depth or all vertices of odd depth.

---

### Post by Mr.Pytagoras on 2011-11-23
Thanks a lot

But I have actually figured it on my own.
After 2 hours of programming that task I have decided to take a new approach so I deleted the whole code and started from scratch, in about 15 minutes I finished the code and when I checked, it was generating correct output.

Anyway thanks.

---

