---
title: "[SOLVED] Linked-list type of array"
date: 2008-12-27
forum: Programming Talk
---

### Post by ProgramErgoSum on 2008-12-27
I am trying to understand arrays and linked lists. Can I have a linked-list which is similar to arrays when it comes to fetching data ?

Example : Suppose, if I have to access the fourth node of a list, then I would first navigate to the 'header node' address and then just add a constant value, etc. to get to the required node. Basically, I want to be able to use advantages of both list (delete, insert at middle, etc.) and array (random searching, contiguous memory, etc.)

---

### Post by monkeyking on 2008-12-27
I don't understand what you wan't.

Do you want the underlaying memorystructure to be the same,
or do you want them to share interface?

I think the overhead would be to big to gain anything,
what language are you using?

---

### Post by ProgramErgoSum on 2008-12-27
I want to use C.

I just want to use a linked-list type of data structure that does not force me to sequentially read through the nodes. I need to be able to go to a node directly using something like ```

start_address + (node_size) * (n-1)

```

The reason I am asking this is, when building the list would the address of the next node follow the above rule ?

Hope I am clearer now.

---

### Post by CptPicard on 2008-12-27
Well, the really simple answer is that you can't do it. That is the fundamental difference between lists and arrays, and both have their strong points, both of which you seem to understand. You just need to accept the tradeoff and choose your structure accordingly.

Now, trees are a structure that give you a bit of both worlds, with tradeoffs both in runtime speed and memory usage, but that is a somewhat offtopic answer already. Then there are skip lists etc...

---

### Post by ProgramErgoSum on 2008-12-27
ok...that saved some 'wild goose chase'. Thanks !

---

