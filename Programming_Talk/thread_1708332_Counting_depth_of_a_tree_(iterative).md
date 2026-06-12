---
title: "Counting depth of a tree (iterative)"
date: 2011-03-16
forum: Programming Talk
---

### Post by AlGorism on 2011-03-16
Hi people.

I'm trying to count the depth of a tree. Here is the recursive one in C:

[PHP]
typedef struct tree* tree_ptr;
typedef struct tree {
    tree_ptr leftchild;
    tree_ptr rightchild;
    char data;
};
int depth( tree_ptr L) {
    int left,right;
    if (L) {
       left=depth(L->leftchild);
       right=depth(L->rightchild);
       return (left<right ? right : left) +1;
    }
    return 0;
}[/PHP]

I tried to find the iterative one, but it seems hard. 
Thanks.

---

### Post by Arndt on 2011-03-16
> **AlGorism said:**
> Hi people.

I'm trying to count the depth of a tree. Here is the recursive one in C:

[PHP]
typedef struct tree* tree_ptr;
typedef struct tree {
    tree_ptr leftchild;
    tree_ptr rightchild;
    char data;
};
int depth( tree_ptr L) {
    int left,right;
    if (L) {
       left=depth(L->leftchild);
       right=depth(L->rightchild);
       return (left<right ? right : left) +1;
    }
    return 0;
}[/PHP]

I tried to find the iterative one, but it seems hard. 
Thanks.

Are you allowed to modify the tree while doing this?

---

### Post by AlGorism on 2011-03-16
No. As in the example, only the pointer of root node is sent to the function. And we can't change the content of the *tree* struct.

---

### Post by Some Penguin on 2011-03-16
Doable with storage linear in the maximum number of nodes in any level in the tree, and time proportional in the number of nodes.  Figuring out how is pretty obviously the point of the homework, however.

---

### Post by schauerlich on 2011-03-16
> **Some Penguin said:**
> Doable with storage linear in the maximum number of nodes in any level in the tree, and time proportional in the number of nodes.  Figuring out how is pretty obviously the point of the homework, however.

Here's another hint: The recursive version the OP posted also takes linear space, but it uses the call stack instead of having an explicit stack variable. Your iterative version can use a stack in a more explicit manner to achieve the same results.

---

