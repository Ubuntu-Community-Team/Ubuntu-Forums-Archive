---
title: "Linked list in two directions, in C, how? BTW I like milk chocolate :P"
date: 2008-11-22
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-11-22
How could I possibly make a linked list in two directions?

Tried google but couldn't find any good tutorials, they were all for one directional lists.

And I have already experience of one-directional list. 


Thanks.

---

### Post by raf_kig on 2008-11-22
If you already had 'experience of one-directional list' you probably wouldn't be asking this question.

A google search for 'doubly linked list c' returns tons of examples and tutorials, so maybe just give it a try ;-)

Regards

raf

/e typos

---

### Post by Idefix82 on 2008-11-22
You do it just like with the one-directional list: have a class (or struct) which stores the information you need plus two pointers, one forward and one backward. eg
```
struct my_data_set{
  my_data_set* next;
  my_data_set* prev;
  data...

```
When you create the first data set, A, say, it's 'prev' and 'next' pointers are set to NULL. When you append a new data set, B, say, you set A's 'next' pointer to the address of B, B's 'prev' pointer to the address of A and B's 'next' pointer to NULL until you again append a new set, at which point you set B's 'next' pointer to the address of this new set and the new set's 'prev' pointer to B, and so on.

---

### Post by crazyfuturamanoob on 2008-11-22
> **Idefix82 said:**
> You do it just like with the one-directional list: have a class (or struct) which stores the information you need plus two pointers, one forward and one backward. eg
```
struct my_data_set{
  my_data_set* next;
  my_data_set* prev;
  data...

```
When you create the first data set, A, say, it's 'prev' and 'next' pointers are set to NULL. When you append a new data set, B, say, you set A's 'next' pointer to the address of B, B's 'prev' pointer to the address of A and B's 'next' pointer to NULL until you again append a new set, at which point you set B's 'next' pointer to the address of this new set and the new set's 'prev' pointer to B, and so on.

Of course I know it's like that, but when creating new nodes, how to link them backwards then? :O

---

### Post by Idefix82 on 2008-11-22
I don't understand your problem. When you create a new data set, you need to access the set which was the last in the list because you want it to point to the new set. So if you can do that, what's the problem with assigning the new set's 'prev' pointer the address of the last one?

To make it explicit, if the variable "last_set" points to the last set in the sequence then you do something like

```
last_set->next = new my_data_set;
last_set->next->prev = last_set;
```

although this may be C++ rather than C (I'm not much of a C programmer) so you might want to do the same but in C style.

---

### Post by raf_kig on 2008-11-22
> **Idefix82 said:**
> I don't understand your problem.

I do understand it perfectly well. He didn't even bother to google once, otherwise the first hit he would have gotten would have been an example of a doubly linked list coded in c and that would have answered all of his questions...

Regards

raf

---

### Post by nvteighen on 2008-11-22
Hmm... Use paper and pencil and do the following:
0. Draw each node as a box... let's say horizontally just for convenience in this post.
1. To each box, draw two arrows one pointing to left and another to right. Label the left arrow as 'prev' and the right as 'next'.
2. The root node's 'prev' and the last node's 'next' should point to NULL.
3. NULLs are also boxes.
4. Ok. Now try to prepend ("append backwards") a node wherever. Draw a box somewhere simbolizing that new node... So, the idea is to move the arrows that way that you **never break** the chain. Write the algorithm.

Translate it into C by using: arrows = pointers; boxes = data.

You'll see it's trivial (**but do it!**...), but the issue is that human mind sometimes needs spatial relationships to understand concepts and processes...

---

### Post by crazyfuturamanoob on 2008-11-22
Last two post explained it pretty well. I'll try to write a test program.

---

