---
title: "threads malloc"
date: 2012-04-11
forum: Programming Talk
---

### Post by chmcy on 2012-04-11
hello, can somebody tell me what happens if i've got some threads and each thread creates a node using malloc (so that i have a list at the end)? i mean when a thread create a node can an other thread put a value in?

---

### Post by 3Miro on 2012-04-11
Sure, you just need to keep track of the pointers. You can make an array of pointers and have each thread allocate a node for each pointer. Then all other threads can put values in that node. Just be careful to sync the threads, you don't want anyone writing into unallocated space or two threads simultaneously trying to alter the content of the same node.

---

### Post by chmcy on 2012-04-11
okz thank u!! :))

---

