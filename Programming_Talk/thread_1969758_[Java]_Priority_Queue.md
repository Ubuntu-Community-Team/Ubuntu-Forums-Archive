---
title: "[Java] Priority Queue"
date: 2012-04-30
forum: Programming Talk
---

### Post by Royk14 on 2012-04-30
Hi,

i'm developing a project (i think it's called "Evolutionary Programming" in english) which has a class named "Individual", with an attribute named "confort".
I want my project to have a Top5 of the Individuals with higher confort. This Top5 must be refreshed frequently, and I must be able to access the one Individual with the higher confort.

I was thinking about implementing this as a PriorityQueue, exactly this one:
PriorityQueue(int initialCapacity, Comparator<? super E> comparator)
with initialCapacity = 5;

My question is: what happens if the Queue is full and I add another Individual? Does the Queue drop the Individual with lower confort? (I was hoping so...)
If this will not work, how do you suggest I do it?

Thanks in advance

---

### Post by mehaga on 2012-04-30
> **Royk14 said:**
> Hi,

i'm developing a project (i think it's called "Evolutionary Programming" in english) which has a class named "Individual", with an attribute named "confort".
I want my project to have a Top5 of the Individuals with higher confort. This Top5 must be refreshed frequently, and I must be able to access the one Individual with the higher confort.

I was thinking about implementing this as a PriorityQueue, exactly this one:
PriorityQueue(int initialCapacity, Comparator<? super E> comparator)
with initialCapacity = 5;

My question is: what happens if the Queue is full and I add another Individual? Does the Queue drop the Individual with lower confort? (I was hoping so...)
If this will not work, how do you suggest I do it?

Thanks in advance
[http://docs.oracle.com/javase/6/docs/api/java/util/PriorityQueue.html](http://docs.oracle.com/javase/6/docs/api/java/util/PriorityQueue.html)

"**A priority queue is unbounded**, but has an internal capacity governing the size of an array used to store the elements on the queue. It is always at least as large as the queue size. **As elements are added to a priority queue, its capacity grows automatically**. The details of the growth policy are not specified."

How can the queue get full?

---

### Post by 11jmb on 2012-04-30
I think you might just be better off maintaining a sorted list and looking at indexes 0:4 individually.

Remember you can only access the first (highest priority) item in a queue, so to get to Individual 1, you would need to remove Individual 0 from the queue, an so-on for 2, 3, and 4

---

### Post by Royk14 on 2012-04-30
Thank you both.

I'm sorry, I was actually reading that page, I just didn't read the initial paragraphs ;)

---

### Post by schauerlich on 2012-04-30
> **11jmb said:**
> I think you might just be better off maintaining a sorted list and looking at indexes 0:4 individually.

Remember you can only access the first (highest priority) item in a queue, so to get to Individual 1, you would need to remove Individual 0 from the queue, an so-on for 2, 3, and 4

> **Royk14 said:**
> This Top5 must be refreshed frequently, and I must be able to access the one Individual with the higher confort.

A sorted list is good for reading the top 5 in O(1) time, but is terrible if the list changes frequently. Inserting into a sorted array is O(logn + n) = O(n) (logn to find the right place in the array, plus n to shift potentially the whole array to the right/left). For any appreciably large n, it would be better to do 10*logn (5 pops and 5 inserts) every once in a while than a bunch of logn + n inserts. I would still recommend the priority queue in this case.

There's a more clever solution, though. Keep an array of 5 that's your top 5 people. Each time you add a new individual, see if they belong in the top 5. If so, place them there, and move the former #5 into a priority queue holding the rest of the population. If they don't belong in the top 5, put them straight in the priority queue. If you ever need to delete one of the top 5, pop from the priority queue to fill in the gap.

---

