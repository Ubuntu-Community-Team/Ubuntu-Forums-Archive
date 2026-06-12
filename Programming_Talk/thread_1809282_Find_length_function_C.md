---
title: "Find_length function C"
date: 2011-07-21
forum: Programming Talk
---

### Post by stamatiou on 2011-07-21
Hey guys,
I am trying to do a function that gets the length of a singly linked list but it always tells me it is zero! Here's the code:

```
#include <stdio.h>
#include <stdlib.h>

typedef struct node
{
    struct node *next,*prev;
    int data;
}Node;

typedef struct list{
    Node *head,*tail;
    int len;
}List;

int find_len(List *list)
{
    int counter = 0;
    Node *dummy;
    dummy = (*list).head;
    while(dummy != NULL)
    {
        counter = counter + 1;
        dummy = dummy->next;
    }
    counter = list->len;
    return 0;
}

Node *new1,*new2,*new3;
    List list;
    
    new1 = malloc(sizeof(Node));
    new2 = malloc(sizeof(Node));
    new3 = malloc(sizeof(Node));
    
    new1->data = 26;
    new2->data = 12;
    new3->data = 45;
    
    list.head = new1;
    list.tail = new3;
    
    list.head->next = new2;
    new2->next = new3;
    
    new3->prev = new2;
    new2->prev = new1;
    
    find_len(&list);
    printf("LENGTH = %d",list.len);
    
    return 0;
}    

```

---

### Post by Bachstelze on 2011-07-21
Please be more careful when pasting code, it seems you missed a line or something. That being said, the error is probably

```
    counter = list->len;&#8217;
```

which should probably be the other way around.

---

### Post by stamatiou on 2011-07-21
> **Bachstelze said:**
> Please be more careful when pasting code, it seems you missed a line or something. That being said, the error is probably

```
    counter = list->len;’
```which should probably be the other way around.
:roll: Of course! That was stupid....
Ok I'll be more careful now....

---

### Post by PaulM1985 on 2011-07-21
Also, your find_len function returns 0.  This might be confusing for a user.  Since the function is returning an int, I would expect it to return the length of the list.  Or alternatively, the function should probably be set as void.

Paul

---

