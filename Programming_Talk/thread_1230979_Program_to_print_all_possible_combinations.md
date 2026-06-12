---
title: "Program to print all possible combinations?"
date: 2009-08-04
forum: Programming Talk
---

### Post by dE_logics on 2009-08-04
Given any number of places.

For instance the same program should print all possible combinations of 3 digits and if its 4...then also it should print all possible combinations of 4 digits...same with 5,6,7 etc...

I'm having a very bad time making it.

Can openoffice calc do it?

---

### Post by dE_logics on 2009-08-04
In C

And yes, one more thing (the most important one)...you are not allowed to compute the total number of possible combination...for instance for 4 digits its 4!...so this information is not to be used here.

Actually I was wondering about a program to print all possible combinations with exceptions...by exceptions I mean...for e.g 4 cannot be admitted to the first place...etc...multiple exceptions.

---

### Post by PandaGoat on 2009-08-04
First, a combination is a list where order is not important; that is (1 2 3) is the same as (3 2 1).  However, you want to find all permutations.  Therefore, I will use the term permutation instead of combination; I suggest you do the same.

When I first read this, the first algorithm that came to mind is of the divide and conquer variety.  Let's say you have the list (3 2 1).  To extract all permuations, you really look at each element and append to it all permutaions of the other elemenents.  

Let's say we have a procedure, called **perms**, that takes, as input, an initial list of numbers and outputs a list of permutaions--a list of lists.  This method will go through every element in the input list and recursively call itself on the input list *minus* the current element.  The procedure ceases and returns NULL (or an empty list) when the list passed to it is NULL (or an empty list); otherwise it appends the value of the current iterate to every permutaion returned by the recursive call. Finally combine all the lists (of lists) formed by the appension and return the combination. 

Returning to the earlier, hopefully not wasted, example list, (3 2 1), here is what the procedure's actions on this list would look like as a tree.  I will use a lisp like syntax for procedure calls:

=> refers to the return
- refers to level of recursion (height of the tree)
# refers to the value in the list of the current iterate when the procedure is called, and #:# refers to the complexity that recursion introduces

```

(perm (3 2 1))      => ((3 2 1) (3 1 2) (2 3 1) (2 1 3) (1 3 2) (1 2 3))

3 -(perms (2 1))    => ((2 1) (1 2))
3:2 --(perms (1))   => ((1))
3:2:1 ---(perms ()) => ()
3:1 --(perms (2))   => ((2))
3:1:2 ---(perms ()) => ()

2 -(perms (3 1))    => ((3 1) (1 3))
2:3 --(perms (1))   => ((1))
2:3:1 ---(perms ()) => ()
2:1 --(perms (3))   => ((3))
2:1:3 ---(perms ()) => ()

1 -(perms (3 2))    => ((3 2) (2 3))
1:3  --(perms (2))  => ((2))
1:3:2 ---(perms ()) => ()
1:2 --(perms (3))   => ((3))
1:2:3 ---(perms ()) => ()

```

I hope you can understand what I wrote; I'm rather tired and am not the best at explaining, especially with ASCII trees.

If you wish to write exceptions into this implentation, it is as simple as 'if the value of the current iterate is the exception, return NULL (or an empty list).'

---

### Post by cariboo on 2009-08-04
This looks suspiciously like a homework question. This thread is closed.

---

