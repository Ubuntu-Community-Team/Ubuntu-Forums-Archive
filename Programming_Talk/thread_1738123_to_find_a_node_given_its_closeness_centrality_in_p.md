---
title: "to find a node given its closeness_centrality in python"
date: 2011-04-24
forum: Programming Talk
---

### Post by madhu91 on 2011-04-24
given a graph g, how to find a node via its closeness_centrality in python??

---

### Post by simeon87 on 2011-04-24
Ok, based on what I see on Wikipedia ( [http://en.wikipedia.org/wiki/Centrality#Closeness_centrality](http://en.wikipedia.org/wiki/Centrality#Closeness_centrality) ), compute the distance between that node and each of the reachable nodes (the lenghts of the paths) and then compute the value using that formula.

But what exactly do you need help with? Representing a graph, computing a shortest path, doing it efficiently, etc?

---

### Post by madhu91 on 2011-04-24
actually i am trying to find the path from a selected nodes as source and destination respectively having its closeness_centrality in mind. just wana compare that with dijstra's path.
i just wanted to know if there is any function in python which can help me out to find the node as i already have its closeness_centrality

---

### Post by simeon87 on 2011-04-24
There may very well be a graph library for Python that can perform such calculations but I don't think the default Python library has such a function.

If I understand correctly you're trying to find a node with a given closeness centrality? In that case you should compute the closeness centrality for a node and compare it with the given closeness centrality. Shortest paths can indeed be computed with Dijkstra's algorithm.

---

### Post by madhu91 on 2011-04-24
not actually!
i am just comparing if i traverse from a source to destination based on the closeness_centrality, do i get the same path as that of dijkstra's.

---

