---
title: "Binary search tree, telephone directory. Multiple telephone numbers"
date: 2008-12-08
forum: Programming Talk
---

### Post by EvenStevens on 2008-12-08
C language, sorry didn't mention in topic title.

[http://pastebin.ca/1278874](http://pastebin.ca/1278874)

I've got this working so that you can enter a name, followed by white space, followed by a telephone number. When a "." is detected, the building of the tree stops and you can search for a name and the number would be output.
However, I'm not so sure how to get it so that if you input a name twice with different numbers each time, it will list the different numbers...

Any help? :-\

Thanks

---

### Post by pp. on 2008-12-08
Seeing the language your program is written in but without looking at your code, I'd separate the name nodes from the phone number nodes, make a linked list of phone number nodes and let each name node point to the linked list of phone number nodes.

---

### Post by dwhitney67 on 2008-12-08
As we know from looking through a typical telephone book, there can be more than one "John Smith", yet each with a unique telephone number (and address).

Your application should be augmented to handle this using a node that holds the name and also contains a list of sub-nodes for the telephone number(s).

Something like:
[php]
struct SubNode
{
  char number[31];
  struct SubNode* next;
};

struct Node
{
  char name[41];
  struct SubNode* numbers;

  struct Node* left;
  struct Node* right;
};
[/php]

---

### Post by EvenStevens on 2008-12-08
Thanks dwhitney, but that's not what my tech spec asks for (yeah, it's a project >_<).

I just need a little push in the right direction...

---

### Post by dribeas on 2008-12-08
> **EvenStevens said:**
> Thanks dwhitney, but that's not what my tech spec asks for (yeah, it's a project >_<).

I just need a little push in the right direction...

If you are not allowed to maintain a list of numbers associated to a single name (which to me would be the first option) then you must be able to store more than a node with the same key (name). You will have to modify your search algorithm so that it searches for the first element with the number that appears in your tree (not the first one you find, but the first one that is there). That will give you a pointer into the first pair <name,phone>. From then on, you can iterate over the tree up to the point where you find the first node that has a different name printing the numbers.

As it is for a project I will not go into more detail or provide code for the search, but it should not be that hard anyway.

---

### Post by phonelover143 on 2009-11-25
If you do not need to maintain a list of numbers on the right is not a unique name, the first option for me) will be (this is the same key (the name), and should be able to save more than one node There. cases, to change the algorithm to find the first number that appears in the tree (the first is to find the first here) is required. This provides a pointer to your first few <name,phone>. Therefore, the point where you can see the tree you can find the first node number that is printed a different name. 

Since the details of this project is not supported or not resources for research, or in any way is difficult.

I hope I am able to help even a little.

---

