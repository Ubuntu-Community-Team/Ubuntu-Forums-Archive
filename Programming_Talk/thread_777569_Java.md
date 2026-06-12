---
title: "Java"
date: 2008-05-01
forum: Programming Talk
---

### Post by Helios1276 on 2008-05-01
Hey guys, Can someone tell me whats the advantage of using binary trees over arrays and linked lists?? thanks in advance :popcorn:

---

### Post by LaRoza on 2008-05-01
> **Helios1276 said:**
> Hey guys, Can someone tell me whats the advantage of using binary trees over arrays and linked lists?? thanks in advance :popcorn:

Faster searching I think. A linked list is not easily searched, you have to go over the entire list to get to one entry.

---

### Post by Npl on 2008-05-01
it has as much advantages as disadvantages.

Use Trees if you search for elements often and need to add remove elements.

use lists is you add/remove elements often.

use arrays if you read/search often, but write rarely. (Or if you have small amounts of entries)

---

### Post by xtal on 2008-05-01
Most of the advantage of binary trees over linked lists and arrays is in its search. Search of an element in arrays / lists takes O(n) while in binary trees its take O(Log N)! (if you dont know math, its MUCH better).

u can find more information about binary trees and binary search trees in the following links:

[http://en.wikipedia.org/wiki/Binary_tree](http://en.wikipedia.org/wiki/Binary_tree)
[http://en.wikipedia.org/wiki/Binary_search_trees](http://en.wikipedia.org/wiki/Binary_search_trees)

---

### Post by CptPicard on 2008-05-01
> **Npl said:**
> 
Use Trees if you search for elements often and need to add remove elements.

The benefit of using a tree is exactly the ability to get to the element in question faster than in the case of a list where you would have to search through the entire list from the beginning... so a search and a deletion from tree is O(log n) instead of a list's O(n).

Whether you have anything to gain in comparison with a list when you consider additions depends on whether you have a sorted or nonsorted list. In a sorted list, you have to find the place where to add in linear time. In a nonsorted list, you can just stick the item at the beginning of the list and be done with it.

> 
use lists is you add/remove elements often.

Untrue. Trees beat lists in deletion always, and in additions it depends on whether list is sorted or not.

> 
use arrays if you read/search often, but write rarely.

Arrays are good for random access of elements (the "getting to the element" part) *if you know the index of the item in advance*. Otherwise an array is not any better than a list -- you must search from the beginning for your item.

Deletions in arrays are particularly bothersome if you must move the rest of the items in the array back by 1 so that you don't leave holes in your array. Note that this would also shift indices that you use to find stuff in the array. Additions can be difficult for the same reason, if you must add into some specific place in the array -- and even the simple case of adding to the end of the array can force you to resize your array by reallocating and copying everything over.

> (Or if you have small amounts of entries)

Small lists perform similarly to small arrays...

---

### Post by mike_g on 2008-05-01
> Arrays are good for random access of elements (the "getting to the element" part) if you know the index of the item in advance. Otherwise an array is not any better than a list -- you must search from the beginning for your item.
Well you could write a binary search for an array, but only if its sorted. 

One point that has not been mentioned is that arrays also use less memory; especially compared to multiple indexed trees or lists. One annoying thing with arrays is that they cant be resized in java unless you use array slicing (AFAIK you cant reallocate it like in C).

---

### Post by LaRoza on 2008-05-01
Speaking of Java, the title of this thread is a little misleading...

---

### Post by Npl on 2008-05-01
> **CptPicard said:**
> ...

Untrue. Trees beat lists in deletion always, and in additions it depends on whether list is sorted or not.Always?? You mean if I delete the first/last n elements of a List it will be faster than traversing&fixing up up the Tree n times? What if youre dealing with a degenerated tree thats basically a list?
You are silently assuming I dont want to delete based on position. I dont know what use the OP had in mind.

> **CptPicard said:**
> Arrays are good for random access of elements (the "getting to the element" part) *if you know the index of the item in advance*. Otherwise an array is not any better than a list -- you must search from the beginning for your item.google up binary search. Also accessing them is more efficient than Lists (or trees if they are sorted - no pointer-chasing).

---

### Post by CptPicard on 2008-05-01
> **Npl said:**
> Always?? You mean if I delete the first/last n elements of a List it will be faster than traversing&fixing up up the Tree n times?

That's a strange special case that falls outside of what you usually analyze for... you just get "any" n items, and in data structures you generally assume you're after some particular item in the structure.

> What if youre dealing with a degenerated tree thats basically a list?

I'm assuming a proper balanced tree structure there of course, the degenerate corner case is not something you ever want to see when you've got a tree :)

> 
google up binary search.

Now *that* is a fair point, and mike_g got a thanks for it already :)

---

### Post by Npl on 2008-05-02
> **CptPicard said:**
> That's a strange special case that falls outside of what you usually analyze for... you just get "any" n items, and in data structures you generally assume you're after some particular item in the structure.I wouldnt call a Stack/Queue/Deque a strange special case :)
> **CptPicard said:**
> I'm assuming a proper balanced tree structure there of course, the degenerate corner case is not something you ever want to see when you've got a tree :)Nor do you want to search within lists often if you did your homework. I certainly dint said I`d use them if searching is required, maybe you addressed the OP more than me in your post - but you quoted me.

---

### Post by CptPicard on 2008-05-02
> **Npl said:**
> I wouldnt call a Stack/Queue/Deque a strange special case :)

Although implementation is/can be the same, at least in my book you consider Stacks/Queues/Deques specifically if you want to consider the performance considerations related to them.

FWIW my post relates to structures where they are general storage/lookup structures, as should be clear. Addition/deletion from end of structure is thus just one case of your analysis which happens to be good for lists.

> 
I certainly dint said I`d use them if searching is required

Yes, the problem is you didn't say much in your original post. It is rather vague when a lot of hidden assumptions are not clarified on. When they're not, one assumes the general case. But of course, bringing them in, you're making a lot more sense :p

> maybe you addressed the OP more than me in your post - but you quoted me.

At least the OP knows a bit more of what is involved and why/when he wants to for example "add/remove elements" with trees vs. with lists -- it's the search part that after all makes for the difference between trees and lists.

---

### Post by Npl on 2008-05-02
> **CptPicard said:**
> Although implementation is/can be the same, at least in my book you consider Stacks/Queues/Deques specifically if you want to consider the performance considerations related to them.As you should do with wathever else Datastructure. 
> **CptPicard said:**
> FWIW my post relates to structures where they are general storage/lookup structures, as should be clear. Addition/deletion from end of structure is thus just one case of your analysis which happens to be good for lists.I could think up more examples where lists beat trees. But youre right of course, just saying they have their place.
> **CptPicard said:**
> Yes, the problem is you didn't say much in your original post. It is rather vague when a lot of hidden assumptions are not clarified on. When they're not, one assumes the general case. But of course, bringing them in, you're making a lot more sense :pThe OP wasnt very clear what kind of information he needs either ;) . I rather elaborate points than posting essays noone reads or asked for.
> **CptPicard said:**
> At least the OP knows a bit more of what is involved and why/when he wants to for example "add/remove elements" with trees vs. with lists -- it's the search part that after all makes for the difference between trees and lists.I couldnt disagree with that.

---

