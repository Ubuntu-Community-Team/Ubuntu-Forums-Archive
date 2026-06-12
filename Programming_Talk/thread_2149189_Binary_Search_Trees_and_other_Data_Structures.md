---
title: "Binary Search Trees and other Data Structures"
date: 2013-05-28
forum: Programming Talk
---

### Post by WinterMadness on 2013-05-28
I am working on a project that uses a binary search tree. By that, I mean the standard BST: [http://en.wikipedia.org/wiki/Binary_search_tree](http://en.wikipedia.org/wiki/Binary_search_tree)

I have three questions:

After talking to some people, I was lead to believe that perhaps, these standard binary search trees are not often used, and instead things like red-black trees and AVL trees are used (among many others, if you notice one that should be stated, say it). Would you say this is correct?

The reason I ask, is because I asked some people "when to balance a BST" and they basically told me to look at other data structures. If you can answer when to balance a standard BST, that would be good as well.

Finally, what are the most commonly used data structures in the real world?

---

### Post by ofnuts on 2013-05-28
The "plain" binary tree is indeed not that much used when it contains non-trivial amount of data because constructing it can lead to pathological cases (for instance if your input is sorted you get something a linked list).

The AVL tree is really a binary tree, it just that the addition/deletion of nodes is using a less trivial algorithm that ensure that the tree remains reasonably balanced, so while being a tad slower in general, it doesn't exhibit pathological cases.

---

### Post by Leuchten on 2013-05-28
AVL and R&B trees are both self-balancing trees, that's why people are recommending them over the bog standard binary tree. If you solve the "when to balance a binary tree" problem, chances are you're going to end up implementing one of the self-balancing binary tree structures.

As for most commonly used, it really depends on what you are doing. For example, Binary trees are usually used for operations where you need to search and find values quickly, say in a map. Their main competitor in this realm are hash tables, which are faster at searching with an O(1) search time, but due to their implementation are theoretically more wasteful of memory than binary trees. Also, it is not as simple to traverse the set of elements in a hashmap as it is in a binary tree.

Linked lists and array-like structures are also commonly used. Linked lists, depending on whether they are singly or doubly linked have O(1) insertion time at the front of the list, O(n) instertion in the middle, O(1) or O(n) at the end of the list, and O(n) traversal time. Array-likes have O(n) for all insertion, an O(1) traversal. Depending on the characteristics of your language/environment, an array may beat out a linked list in speed most of the time, because the multiplicative factor of n in O(n) may be incredibly small. I believe this is why most people in java use ArrayList, which is actually an array with the operations for a list defined for it.

There are also more specialized data structures such as Tries, which are very good for stuff like auto-complete.

Some of these structures may not be appropriate to use despite their speed, depending on the situation your program is in. For example, a large linked list might make more sense on a memory constrained system since the elements of a linked list can more easily fit into fragmented memory than a large array which requires all elements be in sequential order in ram. Likewise, if you're dealing with concurrency a lot you may need an immutable datastructure, a hash table based map becomes difficult to write since most hash tables make use of destructive updates on an array for their speed, while a binary search tree is easily written to be immutable. Ditto for purely functional languages.

---

### Post by trent.josephsen on 2013-05-28
> **Leuchten said:**
> If you solve the "when to balance a binary tree" problem, chances are you're going to end up implementing one of the self-balancing binary tree structures.
This is true. If balancing is an issue for you at all, there's usually no reason not to use a self-balancing tree.

> hash tables [...] are theoretically more wasteful of memory than binary trees.

This is not true, although it may often turn out that way.

> Also, it is not as simple to traverse the set of elements in a hashmap as it is in a binary tree.
Not true. (To be fair, the obvious way to traverse a hash may be prohibitively slow for large, sparse hash tables.)

> Linked lists and array-like structures are also commonly used. Linked lists, depending on whether they are singly or doubly linked have O(1) insertion time at the front of the list, O(n) instertion in the middle, O(1) or O(n) at the end of the list, and O(n) traversal time.
True.

> Array-likes have O(n) for all insertion, an O(1) traversal.
Not true. Appending to the end or inserting at the beginning of an array can be O(1) ([s]or O(log(n)) amortized time[/s] *no, sorry, that is O(1) if you don't need to periodically reallocate the array, but can still be made O(1) amortized if you do*). All data structures have at least O(n) traversal, unless you're using some version of "traverse" that doesn't mean "enumerate the contents of". The metric you're missing is getting the nth element, which is O(n) for linked lists and O(1) for arrays.

---

### Post by Leuchten on 2013-05-29
> **trent.josephsen said:**
> 
This is not true, although it may often turn out that way.


Not true. (To be fair, the obvious way to traverse a hash may be prohibitively slow for large, sparse hash tables.)

Not true. Appending to the end or inserting at the beginning of an array can be O(1) ([s]or O(log(n)) amortized time[/s] *no, sorry, that is O(1) if you don't need to periodically reallocate the array, but can still be made O(1) amortized if you do*). All data structures have at least O(n) traversal, unless you're using some version of "traverse" that doesn't mean "enumerate the contents of". The metric you're missing is getting the nth element, which is O(n) for linked lists and O(1) for arrays.

I meant insertion as in adding elements to the datastructure. Arrays have all the elements they can have when they are allocated, so inserting a new element requires reallocation and copying. Uninitialized/unused elements in an array can be rewritten with O(1) time though. 

edit: Apparently there is an array type with worst-case O(1) append - [http://stackoverflow.com/a/4834508](http://stackoverflow.com/a/4834508) very interesting.

As for hash tables, I could've sworn most implementations rely on an array with more space allocated than is actually used by the elements in the table. That's what I meant by it being theoretically wasteful compared to a BST, since a BST generally only wastes space at leaf nodes.

Traversal is more difficult for a hash-table (especially in-order traversal) because you have to traverse the entire table and only return initialized elements, while a BST tree you just return every key/data pair in the tree.

---

