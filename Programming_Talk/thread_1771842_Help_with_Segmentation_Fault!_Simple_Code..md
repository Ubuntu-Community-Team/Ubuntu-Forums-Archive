---
title: "Help with Segmentation Fault! Simple Code."
date: 2011-05-30
forum: Programming Talk
---

### Post by ragedmonkey on 2011-05-30
Hello, this is my simple attempt to start implementing Linked List.
I am getting a Segmentation Fault at 
Line:
     newNode->item =d;  

Does anyone know why?

```

#include <assert.h>
#include <sys/types.h>
#include <stdio.h>

struct node{
    int item;
    struct node *next;    
};

struct node* createNode(int d){
    struct node *newNode;
    newNode->item = d;
    //newNode->next = NULL;
    return newNode;
}

int main(){
    struct node *new = createNode(10);
    //int x=0;
    //printf("%d\n",new->item);
    return 0;
}

```

---

### Post by slavik on 2011-05-30
because new node is being allocated on the stack of the createNode function, read about malloc() and don't miss class.

---

### Post by ragedmonkey on 2011-05-30
Thanks for your response!.Problem Solved.

---

