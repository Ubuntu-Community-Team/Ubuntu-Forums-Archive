---
title: "find the number of nodes at a level in binary tree"
date: 2010-10-05
forum: Programming Talk
---

### Post by jamesbon on 2010-10-05
I am thinking on a logic to calculate the number of nodes in a binary tree.
Can some one help some idea.

---

### Post by schauerlich on 2010-10-05
Sounds like a [breadth-first traversal](http://en.wikipedia.org/wiki/Breadth-first_traversal).

---

### Post by Some Penguin on 2010-10-05
Also very much sounds like a basic homework question.

---

### Post by fatmarik on 2010-10-05
If you know the number of levels, you can figure out the number of nodes by using the following formula: (2^(level))-1

Since its a simple binary tree, it grows exponentially and the -1 takes care of the single root.

---

### Post by saulgoode on 2010-10-05
> **fatmarik said:**
> If you know the number of levels, you can figure out the number of nodes by using the following formula: (2^(level))-1

Assuming all branches extend to the specified level. ;)

---

### Post by worksofcraft on 2010-10-05
YOu could try the following:

[LIST]
[*]Create a static integer variable called *NodeCounter* set it to zero.
[*]Everytime a node constructor gets called you increment it
[*]Everytime a node destructor gets called you decrement it.
[*]Create your binary tree.
[*]Print the NodeCounter.
[/LIST]

---

### Post by jamesbon on 2010-10-06
> **Some Penguin said:**
> Also very much sounds like a basic homework question.
If that been the case the best thing I could do was to copy a program from my friend.
Should I make a digital signature
"This is not a home work problem.I have written my character device driver I am writing my malloc function so revising all the basics"

---

### Post by schauerlich on 2010-10-06
> **jamesbon said:**
> If that been the case the best thing I could do was to copy a program from my friend.
Should I make a digital signature
"This is not a home work problem.I have written my character device driver I am writing my malloc function so revising all the basics"

To count how many nodes there are at a given level, use a breadth-first traversal, or keep a vector of counts for each level. This requires some extra book keeping as you traverse the tree (ie keep track of your current level as you insert or delete) but will make the query O(1). To count how many there are overall, increment a counter as you insert or remove elements.

---

### Post by jamesbon on 2010-10-06
> **schauerlich said:**
> To count how many nodes there are at a given level, use a breadth-first traversal, or keep a vector of counts for each level. This requires some extra book keeping as you traverse the tree (ie keep track of your current level as you insert or delete) but will make the query O(1). To count how many there are overall, increment a counter as you insert or remove elements.

Ok this looks interesting.
I am explaining once more I am not counting total number of nodes in tree.
I am trying to find out number of nodes at each level.
So that if I have a tree and at a certain moment I want to print all those nodes that are at same level I shall be able to do so but only those nodes which are at same level not any other.

---

### Post by schauerlich on 2010-10-06
> **jamesbon said:**
> Ok this looks interesting.
I am explaining once more I am not counting total number of nodes in tree.
I am trying to find out number of nodes at each level.
So that if I have a tree and at a certain moment I want to print all those nodes that are at same level I shall be able to do so but only those nodes which are at same level not any other.

Okay. Do a breadth first traversal, but keep track of the level you're on and only print out those at the correct level. Or, if you're going to be doing this often, you may wish to make each level into a linked list. It might look like this:

```
                 6
                / \
               /   \
              /     \
             3 ----> 8 -> NULL
            / \       \
           /   \       \
          /     \       \
         2 ----> 4 ----> 9 -> NULL
```

Then, you simply need to go down the tree as far left as you can to the level you want to print, and walk across. Again, this requires some extra bookkeeping, but it's not unmanageable. You could even keep a record of the leftmost node at each level to speed up access, but that might be hairy to maintain on a chronically unbalanced tree.

EDIT: Or, ignore my overly complicated suggestions and just listen to CptPicard. :)

---

### Post by CptPicard on 2010-10-06
Well, just to get the nodes at a certain level, depth-first is certainly the most trivial way to do it...

---

### Post by jamesbon on 2010-10-08
Ok here is my code.

```

#include<stdio.h>
#include<stdlib.h>
struct node {
	struct node *left, *right;
	int data, color;
} *root;
//root is used to point to the root node of tree
int check = 0;
typedef struct node tree;
struct que {
	struct que *next;
	struct node *ald;	//ald stores the address of members of structure node 
} *que_begin;
typedef struct que linklist;
tree *create_node(int);
void add_tree(int value, tree *);
void travel_tree(tree *);
void enque(tree *);
linklist *que_node(tree *);
int main()
{
	int i, j,value;
	tree *nv;
	root = NULL;
	que_begin = NULL;
	value = 0;
	while (1 == 1) {
		printf("enter value \n");
		scanf("%d", &value);
		if (value == 1)
			break;
		if (root == NULL)
			root = create_node(value);
		else if (root != NULL) {
			//      nv = create_node(value);
			add_tree(value, root);
		}
	}
	travel_tree(root);
}

tree *create_node(int num)
{
	tree *temp;

	temp = (tree *) malloc(sizeof(tree));
	temp->data = num;
	temp->left = NULL;
	temp->right = NULL;
	return temp;

}

void add_tree(int v1, tree * node)
{

	if (v1 <= node->data) {
		if (node->left != NULL) {
			add_tree(v1, node->left);
		} else {
			node->left = create_node(v1);
		}
		return;
	}
	if (v1 > node->data) {
		if (node->right != NULL) {
			add_tree(v1, node->right);
		} else {
			node->right = create_node(v1);
		}
		return;
	}

}

void travel_tree(tree * temp)
{
//      printf("\n inside travel_tree");

	if (temp->left != NULL)
		travel_tree(temp->left);
	printf(" \n %d ", temp->data);
	if (temp->right != NULL)
		travel_tree(temp->right);
	return;
}

linklist *que_node(tree * temp)
{
	linklist *b;
	b = (linklist *) malloc(sizeof(linklist));
	b->next = NULL;
	b->ald = temp;
	return b;
}

void enque(tree *temp)
{
//to make a que of linklist
	linklist *list;
	list=que_begin;
	if (que_begin == NULL) {
		que_begin = que_node(temp);
		list=que_begin;
	}
	else
        {	while(list->next!=NULL)
		{
		list=list->next;
		}
	list->ald=temp;
	}
}
```
The above code creates a binary tree.
If I am correct then the enque function will enque a node if passed.
The BFS implemenation I was not able to do do.

---

### Post by schauerlich on 2010-10-08
I'd make the queue a doubly linked list with a pointer to head and tail. That way enqueueing is O(1), all you have to do is add a node after the tail pointer.

Anyways, you already have an insertion and inorder traversal for a BST there. Now, in order to print something at a given level N, all you need to do is add something along the lines of:

```
void print_at_level(tree *t, int n, int curr_level) {
  if (t && curr_level == n) {
	printf("%d ", t->data);
	return;
  }

  if (t) {
	if (t->left != NULL)
	  print_at_level(t->left, n, curr_level + 1);
	if (t->right != NULL)
	  print_at_level(t->right, n, curr_level + 1);
  }

}

```

And you'll be able to print everything on a given level.

```
int main(void) {
  tree *root = create_node(5);
  int ins[6] = {3, 2, 4, 7, 6, 8};
  int i;
  
  for(i = 0; i < 6; i++)
	add_tree(ins[i], root);

  print_at_level(root, 2, 0);

  return 0;
}

=> 2 4 6 8 

```

---

