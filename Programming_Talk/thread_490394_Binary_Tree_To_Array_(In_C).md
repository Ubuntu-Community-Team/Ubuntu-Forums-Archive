---
title: "Binary Tree To Array (In C)"
date: 2007-07-02
forum: Programming Talk
---

### Post by Lster on 2007-07-02
Hi everyone

I haven't learnt much on binary trees yet, so I decided to try it out. I understand how to make a binary tree out of an existing (sorted) array. I now want to convert back - how would I do that?

I have had no luck with either Ubuntu Forum, Google or Wikipedia searches and would really really appreciate if someone could show me how to do it... This is my start - as you'll see I haven't got very far!

```

...

```

I want to read the values in the binary tree from smallest to largest (ascending) into array named values. Just ask me if you need any other information.

I really appreciate,
Lster

---

### Post by Quikee on 2007-07-02
I don't want to spoil all the coding fun so I will only tell you the general idea in pseudo code:

```

void traverse(nodeNumber)

  if (tree[nodeNumber].left != -1 ) 
    traverse(tree[nodeNumber].left) /* recursively go to left because on the left all values are smaller  then current value*/

  addValueToArray(node[nodeNumber].value) /* when we deal with smaller numbers add current value to the array */

  if (tree[nodeNumber].right != -1 ) 
    traverse(tree[nodeNumber].right) /* the rest are bigger then current value */

```

---

### Post by hod139 on 2007-07-02
It looks like you are interested in the [Binary Heap]("http://en.wikipedia.org/wiki/Binary_heap") data structure.  In the underlying array representation of the tree, the root is at index 1 (index 0 is not used).  If a parent node has index i, then the left child is at index 2*i and the right child is at index 2*i+1.  For example, since the root has index 1, the left child of the root is at index 2 (2*1) and the right child is at index 3 (2*1+1).

---

### Post by Lster on 2007-07-02
Thank you loads, Quikee - that was all I need! Ubuntu Forums rock!

@ hod139:

I don't think I understand you - I'm interested, if you will explain again... As far as I can see, my way works - what does that method have over it?

Cheers,
Lster

---

### Post by hod139 on 2007-07-02
A binary heap is an array organized in such a way that you can perform tree like operations on it.  It has some properties that your randomly created array representation does not.  For example, you can create a binary heap in O(n) time.  Removing the max element is O(1).  All the leaf nodes are at indexes greater than n/2, etc.

---

### Post by Lux Perpetua on 2007-07-03
I think Lster wanted a sorted array, not a heap.

---

### Post by hod139 on 2007-07-03
> **Lux Perpetua said:**
> I think Lster wanted a sorted array, not a heap.

I think you are correct and I really misunderstood his original question.

---

