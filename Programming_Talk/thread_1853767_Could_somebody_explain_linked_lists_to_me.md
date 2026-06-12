---
title: "Could somebody explain linked lists to me?"
date: 2011-10-02
forum: Programming Talk
---

### Post by w007 on 2011-10-02
So I was reading a tutorial at cprogramming.com and I got this far before I lost my keen understanding. I've read [this]("http://www.cprogramming.com/tutorial/lesson15.html") several times and it still has me baffled. 
Basically, what I'm failing to understand is what order the nodes are pointed to and why conductor and root are set to point to two things at once.

---

### Post by ofnuts on 2011-10-03
> **w007 said:**
> So I was reading a tutorial at cprogramming.com and I got this far before I lost my keen understanding. I've read [this]("http://www.cprogramming.com/tutorial/lesson15.html") several times and it still has me baffled. 
Basically, what I'm failing to understand is what order the nodes are pointed to and why conductor and root are set to point to two things at once.

Look at some generic explanation that doesn't refer to some programming language, and uses some nice schemas, for instance [http://en.wikipedia.org/wiki/Linked_lists](http://en.wikipedia.org/wiki/Linked_lists)

---

### Post by akvino on 2011-10-03
> **w007 said:**
> So I was reading a tutorial at cprogramming.com and I got this far before I lost my keen understanding. I've read [this]("http://www.cprogramming.com/tutorial/lesson15.html") several times and it still has me baffled. 
Basically, what I'm failing to understand is what order the nodes are pointed to and why conductor and root are set to point to two things at once.

Linked list is crucial to understand properly if you're ever to understand data structures.

First you need to know thing or two about pointers - so read quick explanation about pointers on cplusplus.com. 

Second you need to understand how structure or class works - not everything is important, just basics.

Now lets talk memory. 
When you create an object (which is done when constructor is called), that object will take a certain location in memory, say memory address 'A' (simplistic terms, I wont use real hex values). The length of the object does not matter, but do have in mind that the object will take enough space in memory to accommodate all its members, starting with the address 'A'. This means if the object or a struct has two 'int' members it will be at least two int's in size, meaning if int = 4 bytes, then 2xint = 8 bytes. So for two int it will be at least 8 but can be more. 


Now back to Linked List. For basic linked list you need 2 things, to know where the beginning is (root), and to know when you reached the end. In concept you will create first node (an object), which will have few member variables to tell us where to find the next node, what the value you store in the linked list is, and in double linked list it could hold the pointer to the previous node as well. 

Linked List node (an object/ or a struct) has a member pointer called 'next'. This pointer holds the address to the next object/struct. So if you're first node is at the memory location 'A', the next pointer will hold the memory location of the next object which we will call 'D' (I am calling it 'D' and not 'B' since this memory location can be anywhere, it is not sequential and do not assume sequential memory locations). If the 'next' pointer is equal to 0, then you know you reached the end.

Think of the Linked list as a train where your train engine is the root, and in order to get to the last carriage you have to go through each carriage and check if there is another one behind it.

For programming tips on Linked List:
[http://www.fredosaurus.com/notes-cpp/ds-lists/list-ex1a.html](http://www.fredosaurus.com/notes-cpp/ds-lists/list-ex1a.html)

---

### Post by samjh on 2011-10-04
> **w007 said:**
> what order the nodes are pointed to
Each node points to another node.  That is all.

In the simplest terms, a node consists of two values: one is the value carried by the node, and the other is the value of the location of the next node in the list.  So the "order" of a list is just whatever each node points to.

If a linked list is not implemented correctly, this can have some funny - or disasterous, depending on how you look at it - results.

> why conductor and root are set to point to two things at once.

Not sure what you mean by this.

When a linked list is first created, the root just points to a location in memory where the list will start.  Like a vine growing from the ground, the root is where the list begins.  But when a list begins to grow, the root must also know where the next element will be.

The so-called "conductor" is just a thing that traverses the list.  It starts at the root, and goes up and down the list as required, to read values, or whatever.

There are a many types of linked lists, but this is not the place to discuss them all.  The Wikipedia page linked by *ofnuts* is good.

---

