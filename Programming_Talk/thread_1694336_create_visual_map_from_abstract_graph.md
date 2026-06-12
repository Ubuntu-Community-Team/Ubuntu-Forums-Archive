---
title: "create visual map from abstract graph"
date: 2011-02-24
forum: Programming Talk
---

### Post by ornages on 2011-02-24
Hi!

Are there any existing algorithms or even complete programs that can draw a visual representation from a graph-datastructure?

In detail: I have an adjacency list which describes territories in a world map. As always, the territories are the vertices of the graph, the borders between them are the edges.

The difficult part is that I don't want to draw a simple graph with vertices and edges but I want to create a realistic world map from that. So the challenge is to draw the graph in a way that neighbors are actually touching each other. In other words: the graph's edges must be translated into the maps borders.

Now I was wondering if anybody knew any existing piece of software that solves this or a similar problem. Or even better, some code since I want to integrate it into my program ultimately.

Any comments and suggestions appreciated!

---

### Post by PaulM1985 on 2011-02-24
If the nodes represent territories and edges represent the borders between them, then why not plot the nodes as normal, then for the borders, draw the prependicular line to each edge which passes through the edges centre point?

I have attached a really basic PNG file which hopefully makes what I am trying to describe clearer.

Paul

---

### Post by ornages on 2011-02-24
Thanks for your input, Paul! After doing some research, I just found exactly what I needed. I didn't find a complete algorithm but actually I sort of expected that. If anyone's interested: [http://www.cs.arizona.edu/~kobourov/PROJECTS/maps.html](http://www.cs.arizona.edu/~kobourov/PROJECTS/maps.html) and [http://arxiv.org/abs/0907.2585](http://arxiv.org/abs/0907.2585)

---

### Post by MadCow108 on 2011-02-24
[http://www.graphviz.org/](http://www.graphviz.org/)

---

