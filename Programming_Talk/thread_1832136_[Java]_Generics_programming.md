---
title: "[Java] Generics programming"
date: 2011-08-24
forum: Programming Talk
---

### Post by alexmoca on 2011-08-24
Hi everyone :) I am not sure how to accomplish what I am trying.

```
public class Graph<T extends Comparable> implements Comparable<Graph>
```

This is my class. Basically, each node will contain a precise <T extends Comparable> object and each Graph will be able to be compared with another Graph.

What I want to do is enforce the user to choose a particular type when instantiating this class and not leave the type empty.

For example this should be valid:
```
Graph<String> stringGraph = new Graph<String>();
```
because it doesn't allow things like
```
stringGraph.addNode(new Integer(2));
```

whereas this should be invalid:
```
Graph g = new Graph();
```
since it allows both
```

g.addNode("bla bla");
g.addNode(new Integer(3));
```

Is there any way I can do this?

---

