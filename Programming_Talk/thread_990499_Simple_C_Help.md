---
title: "Simple C Help"
date: 2008-11-22
forum: Programming Talk
---

### Post by lems on 2008-11-22
I'm trying to make a binary search tree/tree insert function and I'm getting a segment fault error. This is my first time coding in C.

```
#include <stdio.h>
#include <stdlib.h>

typedef struct tree_node {
  int val;
  struct tree_node *left;
  struct tree_node *right;
} tree_node;

tree_node* tree_insert(tree_node *root, int n){
	tree_node *node;
	
	node->val = n;

	if(root == NULL){
		return node;
	}
	
	else if(n < root->val)
		return root->left = tree_insert(root->left, n);
	else{
		return root->right = tree_insert(root->right, n);
	}
	
}
```

here's my main:

```
#include <stdio.h>

typedef struct tree_node {
  int val;
  struct tree_node *left;
  struct tree_node *right;
} tree_node;


tree_node* tree_insert(tree_node*, int);
int tree_sum(tree_node*);
main() {
  
	tree_node *root;
	int n = 0;

 
	do{
		printf("Enter an integer (type 0 to quit): ");
		scanf("%d", &n);
		root = tree_insert(root, n);
	} while(n != 0);
}

```

---

### Post by WW on 2008-11-22
You are not allocating any memory for the tree_node structures.  The first time your program executes "node->val = n" in tree_insert(), it will crash, because node does not point to memory containing a tree_node structure.

---

### Post by Mr.Macdonald on 2008-11-22
why are you returning the tree below. heres pseudo-ish code for insert

[PHP]char insert(tree**, val) {
	if (*tree == 0) {
		*tree = mk_tree();
		(*tree)->val = val;
		return 1;
	}
	if (val < tree.val && tree.less != 0) {
		insert(&(*tree)->less, val);
		return 1;
	}
	else if (val > tree.val && tree.less != 0) {
		insert(&(*tree)->more, val);
		return 1;
	}
	
	if (val < tree.val && (*tree)->less == 0) {
		(*tree)->less = mk_tree();
		(*tree)->less->val = val
		return 1;
	}
	else if (val > tree.val && (*tree)->more == 0) {
		(*tree)->less = mk_tree();
		(*tree)->less->val = val
		return 1;
	}
	return 0;
}[/PHP]

First Implement in python and then try in C, It helps me!

---

### Post by nitro_n2o on 2008-11-22
whenever you create a pointer like tree_node *node you'll have to malloc it .. 

change it to something like: 

tree_nodo *node = (tree_node *)malloc(sizeof(tree_node));

---

