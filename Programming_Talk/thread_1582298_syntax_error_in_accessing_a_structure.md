---
title: "syntax error in accessing a structure"
date: 2010-09-26
forum: Programming Talk
---

### Post by jamesbon on 2010-09-26
I am writing a small program 
```

#include<stdio.h>
#include<stdlib.h>
struct node {
    struct node *left, *right;
    int data, color;
} *root;
int index=0;
typedef struct node tree;
void create_tree(int);
int main()
{
    int i, j, value;
    printf("enter value \n");
    scanf("%d", &value);
    create_tree(value);
}

void create_tree(int num)
{
    tree *temp;
    if (index == 0) {
        root = (tree *) malloc(sizeof(tree));
        root->data = num;
    }
    if(index>0){
    temp=(tree *) malloc(sizeof(tree));
        tree->data=num;

    }
    index++;
}

```

but I got following syntax error
```

tree.c:7: warning: built-in function ‘index’ declared as non-function
tree.c: In function ‘create_tree’:
tree.c:27: error: expected identifier or ‘(’ before ‘->’ token

```
What are these errors and why am I getting the above warnings?

---

### Post by GeneralZod on 2010-09-26
```

tree->data=num;

```

=>

```

temp->data=num;

```

Edit:

The warning is problem due to a name-clash with this:

[http://www.gnu.org/s/libc/manual/html_node/Search-Functions.html#index-index-565](http://www.gnu.org/s/libc/manual/html_node/Search-Functions.html#index-index-565)

---

### Post by jamesbon on 2010-09-26
Oh thanks
 I modified the code and now it gives a new warning
```

#include<stdio.h>
#include<stdlib.h>
struct node {
    struct node *left, *right;
    int data, color;
} *root;
int check=0;
typedef struct node tree;
tree * create_tree(int);
int main()
{
    int i, j, value;
    tree *nv;
    printf("enter value \n");
    scanf("%d", &value);
    nv=create_node(value);
}

tree * create_node(int num)
{
    tree *temp;
    if (check == 0) {
        root = (tree *) malloc(sizeof(tree));
        root->data = num;
    }
    if(check!=0){
    
    temp=(tree *) malloc(sizeof(tree));
        temp->data=num;

    }
    check++;
       return temp;
}
```
the warning is 
```

tree.c: In function ‘main’:
tree.c:16: warning: assignment makes pointer from integer without a cast
tree.c: At top level:
tree.c:19: error: conflicting types for ‘create_node’
tree.c:16: note: previous implicit declaration of ‘create_node’ was here

```
Why is this warning/error present and how can I overcome it?
I want to have tree as typedef to a pointer to a structure of type node.

---

### Post by GeneralZod on 2010-09-26
You have not declared create_node before you use it on line 16.

---

