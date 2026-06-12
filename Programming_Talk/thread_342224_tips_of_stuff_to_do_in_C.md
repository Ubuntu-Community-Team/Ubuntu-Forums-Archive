---
title: "tips of stuff to do in C"
date: 2007-01-19
forum: Programming Talk
---

### Post by durus on 2007-01-19
Hi
I'm taking a course in C and wants tips for programs to do in C. I have programmed C++ some years ago, but i do not remember much, and i have done heaps / queues in python in another course.
So i did heaps / queues in C today.
```

#ifndef __NODE__H__
#define __NODE__H__

typedef struct Node Node;struct Node{
  char *data;
  Node *next;
};

#endif //__NODE__H__

```
```
#ifndef __QUEUE__H__
#define __QUEUE__H__

#include <stdlib.h>
#include "node.h"
// #define QUEUE_DEBUG(x) printf("  QUEUE_DEBUG\t%s\n",x)
#define QUEUE_DEBUG(x)


typedef struct{
  Node *front;
  Node *back;
}Queue;

void QueueInit(Queue *queue){
  queue -> front = NULL; 
  queue -> back = NULL;
  void (*func)(int, int, int); 
}

char QueueIsEmpty(Queue *queue){
  if(queue ->front == NULL)
    return 1;
  else
    return 0;
}

void QueuePut(Queue *queue, char *data){
  Node *node = malloc(sizeof(Node));
  node -> data = data;
  node -> next = NULL;
  if(QueueIsEmpty(queue)){
    queue -> back = node;
    queue -> front = node;
    QUEUE_DEBUG("Första noden tillagd");
  }else{
    queue -> back -> next = node;
    queue -> back = node;
    QUEUE_DEBUG("Till nod tillagd");
  }
}

char* QueueGet(Queue *queue){
  if(QueueIsEmpty(queue) == 0){
    Node *p = queue -> front;
    queue -> front = p -> next;
    char *temp = p -> data;
    free(p);
    return temp;
  }
}
#endif //__QUEUE__H__

```

```
#ifndef __HEAP__H__
#define __HEAP__H__

#include <stdlib.h>
#include "node.h"

// #define HEAP_DEBUG(x) printf("  DEBUG\t%s\n",x)
#define HEAP_DEBUG(x)
typedef struct{
  Node *front;
}Heap;


void HeapInit(Heap *heap);
char HeapIsEmpty(Heap *heap);
void HeapPut(Heap *heap, char *data);
char* HeapGet(Heap *heap);

void HeapInit(Heap *heap){
  heap -> front = NULL;
}
char HeapIsEmpty(Heap *heap){
  if(heap -> front == NULL)
    return 1;
  else 
    return 0;
}
void HeapPut(Heap *heap, char *data){
  Node *node = malloc(sizeof(Node));
  node -> data = data;  
  if(HeapIsEmpty(heap)){
    node -> next = NULL;
    heap -> front = node;
    HEAP_DEBUG("first Node added");
  }else{
    node -> next = heap -> front;
    heap -> front = node;
    HEAP_DEBUG("More node added");
  }
}
char *HeapGet(Heap *heap){
  HEAP_DEBUG("Running 'HeapGet()'");
  if(HeapIsEmpty(heap) == 0){
    HEAP_DEBUG("Node poped");
    char *data = heap -> front -> data;
    Node *node = heap -> front;
    heap -> front = node -> next;
    free(node);
    return data;
  }
  HEAP_DEBUG("Heap NOT POPED");
}

#endif //__HEAP__H__

```

Can you give me tips on some fun things to do that should be a little bit harder than this, and do you also have tips on free online books in C ?

And I'm glad if you give me tips on how i can improve the code above, or if i'm doing stuff in some "wrong/bad" way

---

### Post by Wybiral on 2007-01-19
Cool, I actually just got done writing a binary tree in C++ for a project. I'm using to avoid repeat information in a list.

Binary trees are similar to linked list's, except each node as two children. A left child and a right child. When you append a value to them, if the value is less than that of the current node, you move to the left child of that node. If the value is greater than that of the current node... You move to the right. Using this similar to a linked list you can create organized data, so when you need to search for something, you can use the left/right to navigate.

Such is the case for why I am using one... I need to avoid adding repeats to a list, so instead of having to traverse the entire list to check if the value is there, I can do an orderly search that is much faster.

Maybe you should try to write a simple binary tree yourself, they are very handy.

You can also use them to alphabetize something by using the character value to determine the left/right placement, and when you need to search for a word, it's easy to traverse the tree (otherwise you would have to traverse an list of entire words... Not very fast!)

---

### Post by durus on 2007-01-20
thx for the tips, i done this in python before, but it was i bit harder to do it in C. Can you see if my code is good ? Couse i think that my BinTree struct is unnecessary, but don't know how to do it so that all BinTree stuff should get same prefix. I'm gonna add a function that remove words from tree later today. You can see my code below.

*edi1t: seams harder than i thought to fix a remove function, this should be fun.  *
*edit2: fixed a possible error in BinTreeTraverse. Added BinTreeSearch and BinTreeRemove.*
```
define __BINNODE__H__

#include <stdlib.h>

typedef struct BinNode BinNode;
struct BinNode{
  char *data;
  BinNode *left;
  BinNode *right;
};

#endif //__BINNODE__H__
``` 

```
#ifndef __CHARCMP__H__
#define __CHARCMP__H__

/* Returns 1 if a > b
**        -1 if a < b
**         0 if a == b
*/
char charCmp(char *a, char *b){
  if(*a == '\0' &&  *b == '\0')
    return 0;  
  else if (*a < *b)
    return -1;
  else if (*a > *b)
    return 1;
  return charCmp(a + sizeof(char),b + sizeof(char));
}
#endif //__CHARCMP__H__
```

```
#ifndef __BINTREE__H__
#define __BINTREE__H__

#include <stdio.h>
#include <stdlib.h>
#include "binNode.h"
#include "charCmp.h"
typedef struct{
  BinNode *father;
}BinTree;

void BinTreeInit(BinTree *binTree){
  binTree -> father = NULL;
}

char BinTreeSet(BinTree *binTree,char *data){
  if(binTree -> father == NULL){
    BinNode *binNode = malloc(sizeof(BinNode));
    binNode -> data = data;
    binNode -> left = NULL;
    binNode -> right = NULL;
    binTree -> father = binNode;
    return 1;
  }
  char cmp = charCmp(binTree -> father ->data,data);
  if(cmp == 1){
    BinTree tree;
    tree.father = binTree -> father -> right;
    cmp = BinTreeSet(&tree,data);
    binTree -> father -> right = tree.father;
    return cmp;
  }else if(cmp == -1){
    BinTree tree;
    tree.father = binTree -> father -> left;
    cmp = BinTreeSet(&tree,data);
    binTree -> father -> left = tree.father;
    return cmp;
  }else if(cmp == 0){
    return 0;
  }
}
void BinTreeTraverse(BinTree *binTree){
  if(binTree -> father == NULL)
    return;
  if(binTree -> father -> right != NULL){
    BinTree tree;
    tree.father = binTree -> father -> right;
    BinTreeTraverse(&tree);
  }
  printf("%s\n",binTree -> father -> data);
  if(binTree -> father -> left != NULL){
    BinTree tree;
    tree.father = binTree -> father -> left;
    BinTreeTraverse(&tree);
  }
}
char BinTreeRemove(BinTree *binTree,char *data){
  if(binTree -> father == NULL)
    return 0;
  char cmp = charCmp(binTree -> father -> data,data);
  if(cmp == 1){
    BinTree tree;
    tree.father = binTree -> father -> right;
    cmp = BinTreeRemove(&tree,data);
    binTree -> father -> right = tree.father;
    return cmp;
  }else if(cmp == -1){
    BinTree tree;
    tree.father = binTree -> father -> left;
    cmp = BinTreeRemove(&tree,data);
    binTree -> father -> right = tree.father;
    return cmp;
  }else if(cmp == 0){
    BinNode *holder = binTree -> father;
    if(holder -> right != NULL){
      binTree -> father = holder -> right;
      BinNode *temp;
      temp = binTree -> father;
      while(temp -> left != NULL){
	temp -> left = temp -> left -> left;
      }
      temp -> left = holder -> left;
    }else if(holder -> left != NULL){
      binTree -> father = holder -> left;
    }else{
       binTree -> father = NULL;
    }
    free(holder);
    return 1;
  }
}
char BinTreeSearch(BinTree *binTree,char *data){
  if(binTree -> father == NULL)
    return 0;
  char cmp = charCmp(binTree -> father -> data,data);
  if(cmp == 1){
    BinTree tree;
    tree.father = binTree -> father -> right;
    return BinTreeRemove(&tree,data);
  }else if(cmp == -1){
    BinTree tree;
    tree.father = binTree -> father -> left;
    return BinTreeRemove(&tree,data);
  }else if(cmp == 0){
    return 1;
  }
}
#endif //__BINTREE__H__


```
```
#include <stdio.h>
#include "binTree.h"

int main(int argc, char *argv[]){
  int i;
  BinTree binTree;
  BinTreeInit(&binTree);
  for(i = 1; i < argc; i++){
    printf("%d\n", BinTreeSet(&binTree,argv[i]));
  }
  BinTreeTraverse(&binTree);
  if(BinTreeSearch(&binTree,"olle") == 1)
    printf("hittade  olle\n");
  else
    printf("Hittade inte olle\n");
  if(BinTreeRemove(&binTree,"olle") == 1)
    printf("Tog bort olle\n");
  else
    printf("Hittade inte olle\n");
  printf("klar\n");
  BinTreeTraverse(&binTree);
  return 0;
}


```

---

