---
title: "C - double circular linked list"
date: 2008-11-03
forum: Programming Talk
---

### Post by themis on 2008-11-03
Hello everyone,
This is the part where I try to insert a node to a circular double linked list.
**my struct is**
```
struct doubleList{
    int id;
    struct doubleList *prev;
    struct doubleList *next;
};
typedef struct doubleList DoubleList;
typedef DoubleList *DoubleListPtr;
```

I get a SEGME at line 26.
I can you give the whole file, if you would like to try running it.
But I would be grateful mostly if I understood where the problem is!

Do you see something that i dont??
Thanks in advance..! 
```
/*********************************************/
1void init(DoubleListPtr start, int *id){
2    start->prev = start;
3    start->id = *id;
4    start->next = start;
5}
6
7/*********************************************/
8void DL_insert(DoubleListPtr startPtr, int *id){
9    DoubleListPtr new_node, current;
10
11    new_node = malloc(sizeof(DoubleList));
12    if ( new_node != NULL ){  
13        init( new_node, id);
14        printf("tha valoume to new_node->id : %d\n ", new_node->id);
15        current = startPtr;
16        printf("lLLLLLLLLLLLLLLLLLLLLLLLL **current->id: %d\n", current->id);
17        printf("3\n");
18        while( (current->next != startPtr) && (*id > current->id) && (current->id != NULL) ){  /* find where the new node gets in*/
19            printf("Node comes after **current->id: %d\n", current->id);
20            current = current->next;
21        }
22        printf("4\n");
23        new_node->next = current->next;     /* Start is being copied */
24        printf("5\n");
25      
26           (current->next)->prev = new_node;
27        printf("6\n");
28        
29              current->next = new_node;
30        printf("7\n");
31
32                new_node->prev = current;
33        printf("8\n");
34
35    }else{
36        printf("Problem with malloc, func DL_insert() \n");
37    }
38    printf("--please print my id %d\n",new_node->id);
39}
```

---

### Post by whoelse on 2008-11-03
Are you sure that (current->next)->prev is working? Perhaps you just predefine a temporary node as current->next and then use temp_node->prev.

---

### Post by themis on 2008-11-03
Nop!

Still doesnt work
I get the same segmentation fault

...I can't understand!

---

### Post by cknoblock on 2008-11-03
My C is really really rusty, but I thought the -> operator was a dereferencing operator, thus the end result is not a pointer.  So perhaps you need a different combination of -> and . for that struct element?

---

### Post by dribeas on 2008-11-03
> **themis said:**
> This is the part where I try to insert a node to a circular double linked list.

```
/*********************************************/
1void init(DoubleListPtr start, int *id){
//...
7/*********************************************/
//...
8void DL_insert(DoubleListPtr startPtr, int *id){
//...
39}
```

How is the start DoubleListPtr initialized before the first call to DL_insert? Does it have allocated memory, is it correctly initialized?

---

### Post by dwhitney67 on 2008-11-03
Initially the DL list is empty; why is this case not handled in the DL_insert() function?  You probably should merge the init() function and the DL_insert() function.  In your main(), something like this should function properly:

[php]
// Accept the address of 'list' so that if memory is assigned to it, the
// callee will see the change.
void DL_insert(DoubleListPtr* list, int id)
{
  if (*list == 0)
  {
    // new list... set up for first entry
    *list = malloc(sizeof(DoubleListPtr));

    (*list)->id   = id;
    (*list)->prev = 0;
    (*list)->next = 0;
  }
  else
  {
    ...
  }
}

int main()
{
  DoubleListPtr list = 0;
  int           id   = 10;

  DL_insert(&list, id);
  ...
}
[/php]

This is not related to the problem at hand, but I changed the function definition of DL_insert() to accept 'id' as an integer  There is no point (no pun!) of storing an atomical data type by its pointer.

---

