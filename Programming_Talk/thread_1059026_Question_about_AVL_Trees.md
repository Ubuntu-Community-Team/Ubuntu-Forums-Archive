---
title: "Question about AVL Trees"
date: 2009-02-03
forum: Programming Talk
---

### Post by namegame on 2009-02-03
Today in my "Data Structures and Algorithms" class, we were discussing AVL Trees. 

The professor posed the following question, "If you had two AVL trees, the first with two million nodes, the second with six million nodes. How would you merge the two into one AVL tree?"

The only solution I can think of is to traverse the smaller tree using a postfix traversal and as the nodes are "removed," insert them into the larger AVL tree.

Is there a more efficient method to do this?

---

### Post by Npl on 2009-02-03
Sure, create a new tree with the amount of necessary nodes - simply do a "full" binary tree, where every level except the last one is full.
Then iterate all Trees inorder - "in1" iterates the first tree, "in2" the second, "out" the new tree.
In C++ Pseudocode:
> while( have_elements_in_both_input_trees)
{
 if( *in1 < *in2)
  *out++ = *in1++;
 else
  *out++ = *in2++;
}
// fillin the remaining elements if one input tree is not empty


Edit: Should add that you need to know the amount of nodes before.. which aint a given in Binary tree implementations.

---

### Post by namegame on 2009-02-03
> **Npl said:**
> Sure, create a new tree with the amount of necessary nodes - simply do a "full" binary tree, where every level except the last one is full.
Then iterate all Trees inorder - "in1" iterates the first tree, "in2" the second, "out" the new tree.
In C++ Pseudocode:


Edit: Should add that you need to know the amount of nodes before.. which aint a given in Binary tree implementations.

Well, if I have to count the nodes before I can do anything with them that seems fairly inefficient especially with trees with many nodes. That operation would be O(n). That seems counterintuitive to the point of an AVL tree with a worst case searching-scenario of O(log n).

---

### Post by Npl on 2009-02-03
> **namegame said:**
> Well, if I have to count the nodes before I can do anything with them that seems fairly inefficient especially with trees with many nodes. That operation would be O(n). That seems counterintuitive to the point of an AVL tree with a worst case searching-scenario of O(log n).

Yeah, if your implementation of AVL-Trees keeps track of number of the elements it would be easier. I dont know the exact context of the question.

If you know the amount of elements you can do as I said above. Given m,n are the number of Elements this results in a linear runtime m+n.
(Adding counting of Elements will result in 2*(m+n) runtime, which is the same as m+n in Big-O notation as you should know)

If you want to add Elements to the smaller Tree as you said, you also need to either count the Elements before - or compare the length of the longest branch to estimate the smaller one.
runtime will be ~ m*log(n), which is way worse than above (with or without counting elements) if m is about the same magnitude as n and big. i.e. O(m*log(n)) ~ O(n*log(n)) vs. O(n) ~ O(m+n)

If you dont have the size of a Tree available in your implementation you can also estimate the amount of Elements n upwards/downwards by calculating depth d of longest/shortest branch, then set n=2<<d.
After merging the 2 Trees into the newly allocated,  you then need to remove superflous Elements or add the remaining Elements "normally".

---

