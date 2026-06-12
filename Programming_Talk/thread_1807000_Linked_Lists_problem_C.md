---
title: "Linked Lists problem C"
date: 2011-07-18
forum: Programming Talk
---

### Post by stamatiou on 2011-07-18
Hey guys, I would like to experiment with linked lists.It just prints the list backward and forward:. Here's the code:

```
#include <stdio.h>
#include <stdlib.h> 
 
struct node { 
       int data; 
       struct node *next; 
       struct node *previous; 
}; 
main() 
{   
    struct node *list = (struct node *)calloc(1,sizeof(struct node)); 
    struct node *new = (struct node *)calloc(1,sizeof(struct node)); 
    struct node *dummy; 
    struct node *bdummy; 
    bdummy = new; 
    list->data = 20; 
    list->next = new; 
    list->previous = NULL; 
    new->previous = list; 
    new->data = 83; 
    new->next = NULL; 
    dummy = list; 
    while(dummy->next != NULL) 
    { 
        printf("Forward : %d\n",dummy->data);
    dummy = dummy -> next; 
    } 
    while(bdummy->previous != NULL) 
    { 
        printf("Backward: %d\n",bdummy->data);
    dummy = dummy->previous; 
    } 
}
```
It compiles fine but when I execute it I take:
```
Forward : 20
Backward: 83
Backward: 83
Backward: 83
Segmentation fault

```

---

### Post by MadCow108 on 2011-07-18
you need to check dummy and not dummy->next in the while loop
same problem for the backward iteration and you also assign the wrong variable (dummy instead of bdummy)

---

### Post by Barrucadu on 2011-07-18
It's not working because your loops are wrong. Additionally, you are not giving main a return type, not returning anything, not using a valid function prototype, and not freeing the nodes after use.

```
#include <stdio.h>
#include <stdlib.h>

struct node
{
  int data;
  struct node *next;
  struct node *previous;
};

int
main (void)
{
  struct node *list = (struct node *) calloc (1, sizeof (struct node));
  struct node *new  = (struct node *) calloc (1, sizeof (struct node));
  struct node *dummy;
  struct node *bdummy;

  list->data     = 20;
  list->next     = new;
  list->previous = NULL;

  new->previous = list;
  new->data     = 83;
  new->next     = NULL;

  dummy  = list;
  bdummy = new;

  /* Whilst we have a valid node ... */
  while (dummy != NULL)
    {
      /* Print the node data and advance to the next */
      printf ("Forward : %d\n", dummy->data);
      dummy = dummy->next;
    }

  /* Whilst we have a valid node ... */
  while (bdummy != NULL)
    {
      /* Print the node data and go to the previous */
      printf ("Backward: %d\n", bdummy->data);
      bdummy = bdummy->previous;
    }

  /* Free nodes after we are done using them
   * to avoid a memory leak */
  free (new);
  free (list);

  return 0;
}

```

---

### Post by dwhitney67 on 2011-07-18
I could point out exactly where the issue is with your program, but instead I will offer some constructive criticism.

Why not define functions such as insertData() and destroyList()?  Something like:
```

#include <stdbool.h>
#include <stdlib.h>
#include <stdio.h>

typedef struct Node
{
   int          data;
   struct Node* next;
   struct Node* previous;
} Node;

Node* insertData(Node* list, const int data)
{
   /* always create new node */
   Node* node     = malloc(sizeof(Node));
   node->data     = data;
   node->next     = NULL;
   node->previous = NULL;

   if (list != NULL)
   {
      /* list is not empty */
      list->previous = node;
      node->next     = list;
   }

   list = node;

   return list;
}

void destroyList(Node* list)
{
   /* iterate from beginning to the end, and free each Node */
   /* TODO (left as an exercise) */
}

void printList(const Node* list, bool reverse)
{
   if (reverse)
   {
      /* TODO (left an an exercise) */
   }
   else
   {
      for (const Node* node = list; node != NULL; node = node->next)
      {
         printf("%d ", node->data);
      }
   }
   printf("\n");
}

int main()
{
   Node* list = insertData(NULL, 10);
         list = insertData(list, 20);
         list = insertData(list, 30);

   printList(list, false);
   printList(list, true);

   destroyList(list);

   return 0;
}

```
The rationale for implementing functions is to simplify the maintenance of the code, and to aide in the effort of troubleshooting for bugs.  And this leads to your question, which with the code above, should hopefully make it easier for you to troubleshoot on your own.

---

