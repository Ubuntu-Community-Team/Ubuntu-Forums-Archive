---
title: "[C] No graphs library??"
date: 2008-08-09
forum: Programming Talk
---

### Post by nvteighen on 2008-08-09
H
I'm playing around with trees and graphs for a time and have noticed that there's no [graphs]("http://en.wikipedia.org/wiki/Graph_(mathematics)") library for C (like the Boost Graph Lib for C++)... Am I wrong? The nearest I've found is a node data type in GLib (GNode), but it's designed for trees, not for graphs in general...

In short: I want to try reconverting my little "tree" application ([see this post]("http://ubuntuforums.org/showthread.php?p=5469976")) into a library, for learning purposes, hobby, nothing serious... but I want to see some other libraries' code. But, if it happens to be none out there... maybe have I found my first open source project??...

Thanks!

---

### Post by mike_g on 2008-08-09
IDK of any C graphs libraries, but I'm pretty sure it must have been done before. If you chose to make your own it sounds like a cool project.

Currently I'm working on a vector graphics library in C. THe drawing is performed on a buffer in RAM so its API/platform independant. Anyway, it can draw bezier curves / splines, which could be useful for graphs, and circle sectors useful for pie charts, as well as a load of other stuff. 

Its still a WIP, but if you like I could give you the source of what I have so far. Its not all that big yet. And, if you wanted to you could build a graph drawing layer that sits on top of it.

---

### Post by nvteighen on 2008-08-09
Hey, your sounds great! And useful, too...

I have to clarify: I'm on graphs, the data structure consisting in nodes connected, not on statistical graphs (I guess I wasn't clear enough)... For example, a binary tree is a specific type of graph. But we can also have cyclic graphs and whatever pattern you like. The theory behind is really simple: either intersection matrices (adjacency matrix, which I prefer) or interscetion vectors (adjacency lists). Up to know, I've seen code handling particular graphs, but none dealing with them in general.

What annoys me is that there is a very popular library to do this in C++, but it seems there's nothing for C I know of and possibly there isn't either. GLib's GNodes are good, but limited to trees, as I already said... and the node-wise approach is not optimal IMHO; I believe the graph should be accessed as a whole, that way, you don't have to hold an array with all nodes' addresses but have the graph variable handle all of them. 

Yes, quite OOP-ish: a graph "class". But who said OOP is not possible in C? :) 

Follow the link I gave in the first post to see the original "tree" program. Well, there, the "library" is built specifically according to the program's requirements: it reads from a file and only accepts integer values. It also includes some useless functions and lacks path searching capability (a vital point). Now, I want it to be as more independent as I can.

But, anyway, thanks! And good luck with your project!

---

