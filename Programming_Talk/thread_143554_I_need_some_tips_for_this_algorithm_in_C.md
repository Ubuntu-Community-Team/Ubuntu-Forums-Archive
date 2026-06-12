---
title: "I need some tips for this algorithm in C"
date: 2006-03-12
forum: Programming Talk
---

### Post by Mykas0 on 2006-03-12
First, I will read an "unsigned int" from stdin, which I will here call X.

Then, I need to get a way of storing X elements of type "unsigned int", what's the best way to do it? I thought about simply creating a vector of usigned int's (as "unsigned int name [X]"), but would that work any good? **1)**

Now, I read X values and store them in the place I've just said, but then I have to read another "unsigned int", which I will here call Y.

Finally, I have to output the largest amount of numbers separated by Y. For example, {1, 2, 2, 3, 4, 5 , 6 , 7} with Y == 3 would return 4 (for the sequence "1 2 2 3"). Any ideas on the best way to do this? **2)**


(I need your opinions with steps 1 and 2...)

---

### Post by Lux Perpetua on 2006-03-12
[QUOTE=Mykas0]First, I will read an "unsigned int" from stdin, which I will here call X.

Then, I need to get a way of storing X elements of type "unsigned int", what's the best way to do it? I thought about simply creating a vector of usigned int's (as "unsigned int name [X]"), but would that work any good? **1)**[/quote]Not in C. In C, you have to use explicit dynamic allocation, for example, using "name = (unsigned int *)malloc(sizeof(unsigned int)*X)". 

[quote=Mykas0]Now, I read X values and store them in the place I've just said, but then I have to read another "unsigned int", which I will here call Y.

Finally, I have to output the largest amount of numbers separated by Y. For example, {1, 2, 2, 3, 4, 5 , 6 , 7} with Y == 3 would return 4 (for the sequence "1 2 2 3"). Any ideas on the best way to do this? **2)**[/quote]Try rephrasing this. I don't know what you're asking.

---

### Post by rplantz on 2006-03-12
[QUOTE=Mykas0]Finally, I have to output the largest amount of numbers separated by Y. For example, {1, 2, 2, 3, 4, 5 , 6 , 7} with Y == 3 would return 4 (for the sequence "1 2 2 3"). Any ideas on the best way to do this? **2)**
[/QUOTE]

I concur with Lux Perpetua. From your description, I would say that the answer is 5 -- for the sequence "2 2 3 4 5". It's very important to have a complete description of the problem, and to understand how to solve it, before starting to write the code.

---

### Post by Mykas0 on 2006-03-12
Sorry about that, and thanks for the answer in the first question.

As for the second one, "Y" can be interpreted as the maximum amount of DIFFERENT numbers in the sequence.
For example, Y = 3 could be the following sub-sequences:
{1,2,3} --> returns 3
{1,1,1,1,1,2,3} --> returns 7
[1,1,2,2,3,3} ---> returns 6

In the example from before, we had:
{1, 2, 2, 3, 4, 5 , 6 , 7} with Y == 3
With 3 different consecutive numbers, we could have:
{1,2,2,3}
{2,2,3,4}
{3,4,5}
{4,5,6}
{5,6,7}
Since {1,2,2,3} is the biggest one (ties don't matter, so we can ignore {2,2,3,4}), the function would return 4.

Did you understand it this time? Now, my problem is creating an algorithm for this, so I was hoping someone could give me some tips.

---

