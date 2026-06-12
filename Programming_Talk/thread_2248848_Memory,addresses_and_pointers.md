---
title: "Memory,addresses and pointers"
date: 2014-10-17
forum: Programming Talk
---

### Post by spacerocket on 2014-10-17
Hello,

I am only a novice programmer and recently gained interest in memory, addresses, pointers and free store allocation. I have only a basic understanding of variables, operators and program structure ( I have written some simple programs).

If I want to learn about those mentioned above, what should I master before them? Classes? Or/and something else?

---

### Post by papibe on 2014-10-17
Hi spacerocket.

It's been a long time since I learned that, but they go together with "Data Structures and Algorithms".

The basic data structures (or 'objects') that benefit from dynamic allocations are: lists, stacks and trees.

I would start with either lists, or stacks. First**[COLOR="#FF0000"]*[/COLOR]** you create the data structure, then the basic procedures like 'init', 'add', 'remove', 'search', etc.

Just some thoughts. Hope it helps.
Regards.

[COLOR="#FF0000"]*****[/COLOR] alternatively, with OOP in mind, you can create the classes and its methods.

---

### Post by ofnuts on 2014-10-17
Wikipedia to the rescue: 
 
[LIST]
[*][http://en.wikipedia.org/wiki/Pointer_%28computer_programming%29](http://en.wikipedia.org/wiki/Pointer_%28computer_programming%29) 
[*][http://en.wikipedia.org/wiki/Data_structure (and follow links)]("http://en.wikipedia.org/wiki/Data_structure") 
[/LIST]

---

### Post by dataformsaction on 2014-10-18
Even the simplest of programs written in C will use most of these concepts, so I'd start with some simple C tutorials.

And since you're on Linux, you have 2 excellent c compilers to choose from, clang or gcc.

PS what on earth is 'free store allocation' ?

---

### Post by Steven_Williams on 2014-10-22
This is another good resource for dealing with pointers.[http://cslibrary.stanford.edu/102/](http://cslibrary.stanford.edu/102/)

As has been said data structures are a great way to get familiar with pointers. Simple lists that can grow and shrink are a very good exercise. A great tool to track down memory leaks is valgrind.

---

### Post by trent.josephsen on 2014-10-23
> **dataformsaction said:**
> PS what on earth is 'free store allocation' ?

"Free store" is sometimes used as a synonym for "heap". In C++, I understand it refers specifically to the memory space used for allocation with new/delete, as opposed to the heap which is used by malloc/free, but don't quote me on that. It's the same memory either way.

---

### Post by spacerocket on 2014-11-06
Ok,

I`m generally interested in board games, and datastructures like bitsets come in handy for those. In my book there was a some chapters about bits, but not really much. I have tried to search for online documentation and so on but I have to say that I 

understand relatively little how to use shifting operators with board games (diatgonal and horizontal search, how to use & operator with >>). Is there any book/documentation for more about that?

---

### Post by papibe on 2014-11-06
Since bit sets/arrays are a complete different concern, I'd recommend opening a new thread about that specific topic.

Regards.

---

