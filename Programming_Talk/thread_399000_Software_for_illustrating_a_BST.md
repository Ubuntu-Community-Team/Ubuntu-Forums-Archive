---
title: "Software for illustrating a BST"
date: 2007-04-01
forum: Programming Talk
---

### Post by greenmaze on 2007-04-01
I have a project I'm working on that requires me to illustrate some binary search trees and red-black trees. I've done a lot of searching, but I can't seem to find a piece of software that can do the drawing for me. Mainly something that can place the nodes of the tree in a presentable manner (i.e. does all the measuring and placement for you). I'm not looking for something to figure out the manipulation of the trees, just something to assist me in drawing it.

Thanks

---

### Post by WW on 2007-04-01
The **graphviz** package provides some tools that might be useful.  For example, this file
```


/* tree.dot */

digraph tree {
   "1" -> "2";
   "1" -> "3";
   "2" -> "4";
   "3" -> "5";
   "3" -> "6";
}

```
can be processed by the **dot** command like this:
```

$ dot -Tpng tree.dot -o tree.png

```
to create the attached png file.

---

