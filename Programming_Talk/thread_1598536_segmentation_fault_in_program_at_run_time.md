---
title: "segmentation fault in program at run time"
date: 2010-10-16
forum: Programming Talk
---

### Post by jamesbon on 2010-10-16
I am making a program to do a breadth first search.
The code which I am posting here just makes a que of the nodes visited in a binary tree in inorder fashion,so this implementation is not yet complete.
While developing I got a segmentation fault which I was not able to understand why I am getting so I am posting since the tree of same program (without BFS) is working.
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
struct list {
    struct list *next;
    struct node *btree_node_ptr;    //btree_node_ptr stores the address of members of structure node 
} *que_start;
typedef struct list que;
tree *create_node(int);
void add_tree(int value, tree *);
void travel_tree(tree *);
void enque(tree *);
void travel_que(void);
void deque(tree *);
que *que_add_node(tree *);
que *tree_que;
int main()
{
    int i, j,value;
    tree *nv;
    root = NULL;
    que_start = NULL;
    value = 0;
    while (0) {
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
    printf("\n travelling in que \n");
    travel_que();    
}

tree *create_node(int num)
{
    tree *temp;

    temp = (tree *) malloc(sizeof(tree));
    temp->data = num;
    temp->left = NULL;
    temp->right = NULL;
    temp->color=2;
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

void travel_tree(tree *temp)
{
//      printf("\n inside travel_tree");

    if (temp->left != NULL)
        travel_tree(temp->left);
    printf(" \n %d ", temp->data);
    enque(temp);
    if (temp->right != NULL)
        travel_tree(temp->right);
    return;
}

que *que_add_node(tree * temp)
{
    que *b;
    b = (que *) malloc(sizeof(que));
    b->next = NULL;
    temp->color=1;
    b->btree_node_ptr = temp;
    return b;
}

void enque(tree *temp)
{
//to make a que of que
    tree_que=que_start;
    if (que_start == NULL) {
        que_start = que_add_node(temp);
        tree_que=que_start;
        return;
    }
    else
        {    while(tree_que->next!=NULL)
        {
        tree_que=tree_que->next;
        }
    tree_que->next=que_add_node(temp);
    }
     return;
}
void travel_que(void)
{
    tree_que=que_start;
    while (tree_que!=NULL)
        {
    printf("Data is %d color is %d\n",tree_que->btree_node_ptr->data,tree_que->btree_node_ptr->color);
    tree_que=tree_que->next;
    }
    return;
}
void deque (tree *temp)
{
 while (tree_que!=NULL)
     {
     tree_que=tree_que->next;

    }
    return;
}

```

---

### Post by spjackson on 2010-10-16
> **jamesbon said:**
> I am making a program to do a breadth first search.
The code which I am posting here just makes a que of the nodes visited in a binary tree in inorder fashion,so this implementation is not yet complete.
While developing I got a segmentation fault which I was not able to understand why I am getting so I am posting since the tree of same program (without BFS) is working.

It is very easy to find the cause using gdb.

In your main function, the while loop is not entered because it's
```

    while (0)

```Therefore when you get to travel_tree, root is still NULL. In travel_tree you dereference the NULL pointer which has been passed as the parameter. Boom!

---

### Post by jamesbon on 2010-10-17
Ok.

---

