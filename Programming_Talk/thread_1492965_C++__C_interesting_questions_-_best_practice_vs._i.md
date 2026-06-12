---
title: "C++ / C interesting questions - best practice vs. inovation vs. brainstorming"
date: 2010-05-25
forum: Programming Talk
---

### Post by akvino on 2010-05-25
1) Which data structure would you use to store 1000000 intigers?
2) Which data structure would you use to store 10 000 000 telephone numbers?
3) What search algorithm would you implement for fastest search on 10 000 000 telephone numbers?
4) If you had a C++ program that needs to process and load a lot of information into the memory, and you run out of memory, how would you modify the program? 
5) What are best practices to avoid running out of memory when processing large data sets?
6) How would you best, most efficiently, fastest, sort 1 000 000 000 integers?

:popcorn:

---

### Post by MadCow108 on 2010-05-25
this forum is not for answering homework questions...
if this is not homework, please provide some context to persuade me you don't just want others do do your work.

---

### Post by trent.josephsen on 2010-05-25
1) Depends on usage patterns.
2 and 3) Sounds like a job for a relational database.
4 and 5) None of my real-world experience is applicable.
6) sort -n

---

### Post by akvino on 2010-05-25
> **MadCow108 said:**
> this forum is not for answering homework questions...
if this is not homework, please provide some context to persuade me you don't just want others do do your work.

It is not homework. I don't want others to do my work. As it happens I am going over Data Structures, and am interesting what you guys think, since there is some good talent here. I am especially interested in optimization techniques which would allow C++ processing of large data sets without flooding the memory... Why does everything have to be homework?!

---

### Post by akvino on 2010-05-25
> **trent.josephsen said:**
> 1) Depends on usage patterns.
2 and 3) Sounds like a job for a relational database.
4 and 5) None of my real-world experience is applicable.
6) sort -n

Well, even if it is work for relational database, let's say you had to use a data structure? Which one and why?

---

### Post by lisati on 2010-05-25
3) Sorted or unsorted?

---

### Post by uOpt on 2010-05-25
You don't give enough context.

For all the search stuff we need to know at least the rate of updates on the number set, the expected frequency and nature of the search, the expected range of numbers (if any) and how much memory you are willing to trade for search and/or update speed.

For sorting, likewise, the range is important, the update rate is important and maybe the lists are usually almost-sorted when they come in.

Out of memory means virtual or physical memory in your question?

---

### Post by akvino on 2010-05-25
> **lisati said:**
> 3) Sorted or unsorted?

Questions 2 and 3 are related. If you have 10 000 000 telephone numbers you have to store them in a data structure that is going to enable fast search, and we would assume if you have to name data structure and load them into data structure, then they would be sorted.

---

### Post by lisati on 2010-05-25
> **akvino said:**
> Questions 2 and 3 are related. If you have 10 000 000 telephone numbers you have to store them in a data structure that is going to enable fast search, and we would assume if you have to name data structure and load them into data structure, then they would be sorted.

True: the first thing that came to my mind when reading the question was "binary search", which works best with sorted data.

---

### Post by akvino on 2010-05-25
> **uOpt said:**
> You don't give enough context.

For all the search stuff we need to know at least the rate of updates on the number set, the expected frequency and nature of the search, the expected range of numbers (if any) and how much memory you are willing to trade for search and/or update speed.

For sorting, likewise, the range is important, the update rate is important and maybe the lists are usually almost-sorted when they come in.

Out of memory means virtual or physical memory in your question?
Thanks for the reply and let me answer with a question if you don't mind.

Search is going to be often, update - rare, but if it was not rare would it change your choosing?

Sorting question 6 only pertains to list of integers that are not sorted, range can be anything, so would you implement different approaches if the range exceeded unsigned long vs. range within unsigned long?

Out of memory means out of physical and virtual.

---

### Post by akvino on 2010-05-25
> **lisati said:**
> True: the first thing that came to my mind when reading the question was "binary search", which works best with sorted data.

I also think Binary Tree would be the best.. I am interested if anyone has different opinion, or specific type of Binary Tree they would use - and why?

---

### Post by lostinxlation on 2010-05-25
> **akvino said:**
>  
Out of memory means out of physical and virtual.
If virtual memory runs out, it's beyond the capability of your computer. To avoid memory exhaustion on physical memory, put as many data into a single page as possible and use fewer pages, which means you should allocate continuous locations to all the data upfront. I don't know the details of C/C++ compiler, but array might work.

---

### Post by Tony Flury on 2010-05-25
Or even better - use the right tools for the job - like a file based database system - and only put into memory (physical or virtual) the data you actually need to process at the time.

---

### Post by trent.josephsen on 2010-05-25
There's a problem with 2 and 3 in that telephone numbers by themselves are not very useful.  What can you do with a list of telephone numbers if you don't have associated addresses, names, or at least employee ID numbers?  I can tell if a telephone number is connected or not just by picking up the phone and dialing it.  If you want to store telephone numbers, I assume there is other information that you want to associate with it.  That's why I would suggest a relational database.

Database design is an entire topic to itself.  How you retrieve that data in your program is determined by what database engine you use, what library you use to access it, and what functions you use.  Read up on the Perl DBI if you're interested in seeing one way to do it.  But how you deal with that information on the code level just depends.  I can think of a few dozen different approaches to the telephone number problem; depending on how you approach it, your solution will most likely be different from mine.

BTW, binary search is an algorithm for finding an element of a sorted array.  Binary trees are data structures that work best when the data is initially unsorted.  They share log(n) search complexity, but that's about it.

I think the answer to all your questions is, "avoid storing thousands (let alone millions) of records in memory at once."  Process records one at a time; don't ever try to load an entire database into memory unless its size is known to be small.  But, again, it all depends.  You won't get a hard and fast answer, or even a rule of thumb, for any of your questions because they could apply to any of millions of different situations, and any situation could require a unique solution.

---

### Post by lisati on 2010-05-25
> **trent.josephsen said:**
> 
Database design is an entire topic to itself.  How you retrieve that data in your program is determined by what database engine you use, what library you use to access it, and what functions you use.  Read up on the Perl DBI if you're interested in seeing one way to do it.  But how you deal with that information on the code level just depends.  I can think of a few dozen different approaches to the telephone number problem; depending on how you approach it, your solution will most likely be different from mine.
Books can and have been written about databases by people more skilled and knowledgable in the topic than myself. One or two ideas come to mind here too.
> **trent.josephsen said:**
> 
BTW, binary search is an algorithm for finding an element of a sorted array.  Binary trees are data structures that work best when the data is initially unsorted.  They share log(n) search complexity, but that's about it.

Nicely said. I'd spotted this, but got distracted by something else before coming up with a suitable comment about the difference between binary searches and binary trees. I haven't read much about the topic in recent years, but do recall reading something about balancing binary trees, which is a topic unto itself.

---

### Post by hyperAura on 2010-05-25
5) by designing a garbage collector like the one which is built-in in java.. lets say as soon as you reach a critical amount of memory, then make a test to get rid off those objects which are not used..

---

