---
title: "[C++] binary trees.."
date: 2007-11-21
forum: Programming Talk
---

### Post by DesertRose on 2007-11-21
.

---

### Post by Vadi on 2007-11-21
Check for the value first in the tree before adding it. If it's already in the tree, then just don't add it :)

---

### Post by DesertRose on 2007-11-21
.

---

### Post by smartbei on 2007-11-21
No, I think that can be left as an exercise to the reader :). It isn't very difficult - just create a program that traverses the tree, each time checking if the current value is equal to the one you want to add.

If it is not, and the current number is smaller than the one you want to add, go left. If it is larger, go right. You can do this :).

---

### Post by DesertRose on 2007-11-21
.

---

### Post by DesertRose on 2007-11-21
.

---

### Post by CptPicard on 2007-11-21
Sorry to ask, but how did you get up to that data structures class without having prerequisites understood? :)

I'm getting the feeling that if people complete your homework here for the data structures class, the next thing we know, is that you're in some next class without understanding data structures and c++...

Is that particular integer you want to check against the key of the tree, in other words, is this supposed to be a binary search tree? If so, it really is that simple as suggested above.. in a binary search tree, the left-side branch contains all the values that are smaller than the one at the node; the right-side branch contains the values that are larger than the one at the node. If the value is the same at the node as the one you want to add, you just quit, as the value is already there.

If not, you either go left or right depending on where the value is supposed to be in relation to the node, and finally, when you find an empty branch to plug the value to, you do so.

You really *need* to be competent enough in C++ to implement that if you want to pass that class, you know.

---

### Post by DesertRose on 2007-11-21
I have just written so big explanation of the situation and everything, but it has disappeared :(:(:( it is so unfair :(

---

### Post by DesertRose on 2007-11-21
.

---

### Post by smartbei on 2007-11-21
Well! Come on, do you seriously think we don't want to help? [see your last thread as an example]. The fact is that we enjoy helping people learn, but we recognize the fact that many times it is better to learn by yourself even if it takes longer, and is harder. In the last thread, you posted code that did not work, and we helped you fix it so that you could use it, but the base was yours. Here, you are asking us to write the code... See the difference.

Besides, there is a general policy not to help out with homework too much, and it seemed (you say it isn't and I believe you) like this was another homework assignment which might be better off solved alone. That said, I find it odd that you were hurt by something someone said - it wasn't meant to be provocative or derisive. Regardless, good luck with your future endeavors (sp?) and if you do have a specific (prefferably non-homework :D) question, we will do our best to help you in the way **we** think is best, which may mean only advising you how it is done.

Note: I say 'we' in this post as if I am talking for the whole Programming Forum. I am not. I speak for myself, and my actions oin this forum are based on the general sentiment I get. I may be wrong.

---

### Post by CptPicard on 2007-11-21
> **DesertRose said:**
> ok, in few words. I got so far because I deserve it, because I am very responsible and stubborn and I never give up. I know what I want and what I need, and I go straight to it, no matter all the difficulties. 

Sometimes "going straight for it when you know you deserve it" just leads to shortcuts you need to backtrack on when you run out of competence you should already have.

> this one is not a homework. that's what I just want to know and understand. I know enough of theory, I need practical examples.


It sure looks like homework :) Anyway, you were given a complete explanation of the solution (twice), and considering that you already have code, it's such a simple modification it should be perfectly doable for someone in data structures class.

Just to add to my own explanation... if whatever you're adding to the tree is *not* the key, you pretty much don't have other options except recursively going through the whole tree and checking whether you've got the item already added in some node.

---

### Post by DesertRose on 2007-11-22
.

---

