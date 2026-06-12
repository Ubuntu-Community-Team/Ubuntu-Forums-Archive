---
title: "Boost graph library anyone?"
date: 2010-11-20
forum: Programming Talk
---

### Post by potpan on 2010-11-20
Anyone familiar with the boost graph library?  I am trying to build a directed graph but for each node of the directed graph I want to store pointers to different arrays of data.  I am new to the whole generic programming thing, and I am having a lot of trouble getting started using this library.  Any ideas?

---

### Post by worksofcraft on 2010-11-21
> **potpan said:**
> Anyone familiar with the boost graph library?  I am trying to build a directed graph but for each node of the directed graph I want to store pointers to different arrays of data.  I am new to the whole generic programming thing, and I am having a lot of trouble getting started using this library.  Any ideas?

I don't know boost, but by pure coincidence I recently programmed a generic base class for directed graph objects in C++. It is public domain and has both breadth-first and depth-first iterator classes. You can derive from them to add any attributes you like to the "edges" and "nodes" and it supports [double dispatch]("http://en.wikipedia.org/wiki/Double_dispatch") [vistor]("http://en.wikipedia.org/wiki/Visitor_pattern") algorithms.

The file is "cs_graph.h and cs_graph.cpp" currently in the cs_lib.tar file of my [nascent graphics project here]("http://code.google.com/p/schematrix/downloads/list"). I only wrote a little text file tutorial so far but if you did want to use it, I can give you lots of help... all I want to know is what users would like to see in a tutorial ;)

---

