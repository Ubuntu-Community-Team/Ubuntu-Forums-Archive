---
title: "Trees"
date: 2008-08-15
forum: Programming Talk
---

### Post by lordhaworth on 2008-08-15
Hey all

Me again, I've only recently been programming with pointers and have realised how useful they can be by improving some old programs using linked lists etc and creating some new programs i never could before. 
However, although I understand what it is, im having trouble constructing a tree. Ive searched a fair bit and not really found any tutorials on how to construct a tree - only on how to search them (which isnt very useful when i cant build one). 

A lot of tutorials tell you how to build linked lists and then kind of go "this is a tree, you can build it in pretty much the same way" which makes me think itll prob be easy but Im having trouble!
This is in fortran90 again, direction to tutorials or advice would be much appreciated. Using a tree recursively will probably be the next big useful thing for me so Im hoping to get this nailed!

Cheers

Tom

---

### Post by lordhaworth on 2008-08-15
To specify my trouble a bit. Im having a bit of a problem with the tree as it gets bigger. Am I going to have to come up with some kind of traversal condition and then when I get to a node that has null Left and Right pointers come up with some criteria as to which to add the next node to?

---

### Post by nvteighen on 2008-08-15
> **lordhaworth said:**
> To specify my trouble a bit. Im having a bit of a problem with the tree as it gets bigger. Am I going to have to come up with some kind of traversal condition and then when I get to a node that has null Left and Right pointers come up with some criteria as to which to add the next node to?
Yes.

---

### Post by mike_g on 2008-08-15
> To specify my trouble a bit. Im having a bit of a problem with the tree as it gets bigger. Am I going to have to come up with some kind of traversal condition and then when I get to a node that has null Left and Right pointers come up with some criteria as to which to add the next node to? 
In an unbalanced tree you always follow the path until you reach a null node then add your new node there. Theres a little extra complexity when nodes have equal values.

Heres a good tutorial on binary trees: [http://eternallyconfuzzled.com/tuts/datastructures/jsw_tut_bst1.aspx](http://eternallyconfuzzled.com/tuts/datastructures/jsw_tut_bst1.aspx)

The code examples are in C, but it explains the concepts well. Such as how to delete nodes and create balanced trees.

---

### Post by lordhaworth on 2008-08-15
Cheers C and Fortran are similar enough for it to be useful! Shows what I mean about a lack of info about it online though I had a fair look!

---

### Post by mike_g on 2008-08-15
No worries, that site is hard enough to find through google even when you're explicitly searching for it ;)

---

