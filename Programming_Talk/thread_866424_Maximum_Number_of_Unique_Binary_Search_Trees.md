---
title: "Maximum Number of Unique Binary Search Trees"
date: 2008-07-21
forum: Programming Talk
---

### Post by DBQ on 2008-07-21
Hey everybody.  I am developing something which relies on me calculating the number of unique binary search trees (BSTs) you can make given k unique integers.  

I think the formula for this is (2^k) - k where k is the number of integers (or nodes).  If you draw this out, you could see the pattern.  Can somebody please verify this? I tried this for k = 1, k = 2, and k = 3.  Trying anything bigger is probably not practical because the overall number of binary trees for say 4 is 4! = 24.

---

### Post by Npl on 2008-07-21
The solution to this are the Catalan numbers (google/wikipedia is your friend). Its been 2 years since I dealt with that stuff, but AFAR the Catalan numbers are the # of different binary trees with n **internal** nodes, but as the external nodes (=your numbers) are always 1 more, this should be no big problem for you.

---

### Post by DBQ on 2008-07-21
> **Npl said:**
> The solution to this are the Catalan numbers (google/wikipedia is your friend)

Yes, I am aware.  I have looked at the wikipedia for this.  I am interested in the BINARY SEARCH TREE not simply BINARY TREE.  Thank You.

---

### Post by matja on 2008-07-21
I count 14 different (unbalanced) binary search trees for k=4, using a pretty advanced method involving my fingers ;) I don't get why there should be 24 different binary trees for 4 nodes though, so maybe I've misunderstood something?

```

1       1      1      1     1       2       2
 2       2      4      4     3     1 3     1 4
  3       4    2      3     2 4       4     3
   4     3      3    2

```
these seven plus the seven symmetric ones (symmetric in shape, that is).

---

### Post by DBQ on 2008-07-21
> **matja said:**
> I count 14 different (unbalanced) binary search trees for k=4, using a pretty advanced method involving my fingers ;) I don't get why there should be 24 different binary trees for 4 nodes though, so maybe I've misunderstood something?

```

1       1      1      1     1       2       2
 2       2      4      4     3     1 3     1 4
  3       4    2      3     2 4       4     3
   4     3      3    2

```
these seven plus the seven symmetric ones (symmetric in shape, that is).

For the different number of binary trees I think its the permutation of all possible values from 1..k.  No?  I am actually interested in the BINARY SEARCH TREES.

---

### Post by WW on 2008-07-21
The number of binary search trees with n nodes, C(n), *is* the n*th* Catalan number.  Here's why:

Consider the integers 1, 2, ..., n.  The number of trees with root k is C(k-1)C(n-k), because there are k-1 integers below k and n-k above k. Then the total is found by adding these up for k from 1 to n:
[center]
C(n) = C(0)C(n-1) + C(1)C(n-2) + ... + C(n-1)C(0)
[/center]

with the trivial cases given by C(0)=1 and C(1)=1.  This is the same recurrence relation as given in the wikipedia article.

---

### Post by Npl on 2008-07-21
unless im missing something, # of binary trees = # of binary search trees?
You get every possibly BST if you take a BT and simply fill in the numbers "inorder" ( and theres only one way of doing this correctly).

What I dint think of though is that the Catalan numbers are for trees which only have nodes with 0 or 2 children.

---

### Post by DBQ on 2008-07-22
Thank you all!  You were very helpful.  You all get stars!

---

