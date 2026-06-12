---
title: "Delete Node function in C"
date: 2011-07-21
forum: Programming Talk
---

### Post by stamatiou on 2011-07-21
hey guys,
i know that I have made already many posts but this one is tough! I want to make a function that deletes the Node when it finds a specific value
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
    list->len = counter;
    return 0;
}

int del1st(List *list,int value)
{
    Node *dummy;
    dummy  = (*list).head;
    while(dummy != NULL)
    {
        if(dummy->data == value)
        {
            dummy->prev->next = dummy->next;
            free(dummy);
        }
        dummy = dummy -> next;
    }
    return 0;
}

int main()
{
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
    new3->next = NULL;
    
    new3->prev = new2;
    new2->prev = new1;
    
    find_len(&list);
    printf("LENGTH = %d\n",list.len);
    
    del1st(&list,12);
    
    printf("LENGTH = %d\n",list.len);
    
    return 0;
}    

```
I put in the find_len function to be easier to count the nodes.

---

### Post by Bachstelze on 2011-07-21
```
        if(dummy->data == value)
        {
            dummy->prev->next = dummy->next;
            free(dummy);
        }
        dummy = dummy -> next;
```

You cannot access dummy anymore after you free() it. ;)

---

### Post by stamatiou on 2011-07-21
> **Bachstelze said:**
> ```
        if(dummy->data == value)
        {
            dummy->prev->next = dummy->next;
            free(dummy);
        }
        dummy = dummy -> next;
```You cannot access dummy anymore after you free() it. ;)
So if I make a pointer to dummy->next and then assign dummy to the the pointer?

---

### Post by Bachstelze on 2011-07-21
> **stamatiou said:**
> So if I make a pointer to dummy->next and then assign dummy to the the pointer?

No, you cannot "make a pointer to dummy->next", because dummy does not point to anything anymore. What's that line for anyway? It doesn't seem to serve any purpose.

---

### Post by stamatiou on 2011-07-21
> **Bachstelze said:**
> No, you cannot make a pointer to dummy->next since dummy does not point to anything anymore. What's that line for anyway? It doesn't seem to serve any purpose.
I mean before I free dummy, something like this:```
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
    list->len = counter;
    return 0;
}

int del1st(List *list,int value)
{
    Node *dummy;
    Node *temp;
    dummy  = (*list).head;
    while(dummy != NULL)
    {
        if(dummy->data == value)
        {
            temp = dummy->next;
            free(dummy);
            dummy = temp;
        }
        dummy = dummy -> next;
    }
    return 0;
}

int main()
{
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
    new3->next = NULL;
    
    new3->prev = new2;
    new2->prev = new1;
    
    find_len(&list);
    printf("LENGTH = %d\n",list.len);
    
    del1st(&list,12);
    
    printf("LENGTH = %d\n",list.len);
    
    return 0;
}    

```

---

### Post by Bachstelze on 2011-07-21
You're making it more complicated than it needs to be. Just make the function return after it has deleted the node: 

```
int del1st(List *list,int value)
{
    Node *dummy;
    dummy = list->head;
    while(dummy != NULL)
    {
        if(dummy->data == value)
        {
            if (dummy->prev != NULL) {
                dummy->prev->next = dummy->next;
            }
            if (dummy->next != NULL) {
                dummy->next->prev = dummy->prev;
            }
            free(dummy);
            return 0;
        }
        dummy = dummy->next;
    }
    return 1; /* Return 1 if object not found */
 }
```

And if you want to "delete all nodes with value n", just do:

```
while (del1st(list, n) == 0)
    ;
```

---

### Post by stamatiou on 2011-07-21
> **Bachstelze said:**
> You're making it more complicated than it needs to be. Just make the function return after it has deleted the node: 

```
int del1st(List *list,int value)
{
    Node *dummy;
    dummy = list->head;
    while(dummy != NULL)
    {
        if(dummy->data == value)
        {
            if (dummy->prev != NULL) {
                dummy->prev->next = dummy->next;
            }
            if (dummy->next != NULL) {
                dummy->next->prev = dummy->prev;
            }
            free(dummy);
            return 0;
        }
        dummy = dummy->next;
    }
    return 1; /* Return 1 if object not found */
 }
```And if you want to "delete all nodes with value n", just do:

```
while (del1st(list, n) == 0)
    ;
```
Thank you very much but I am trying to do it like an exercize, is there a way to make the function that way that it does not need the while loop in main?

---

### Post by Bachstelze on 2011-07-21
Well, what is it exactly that you want to do, then? Your function is called del1st, which I assume means "delete the first node with the given value".. This is exactly what my function does. As I said, the while loop is if you want to delete *all* notes with that value.

---

### Post by stamatiou on 2011-07-21
The find_len function still says me that it did not delete anything....

---

### Post by stamatiou on 2011-07-21
So which is wrong, the del1st or the find_len?

---

### Post by Bachstelze on 2011-07-21
The problem is that you do not run find_len() after del1st(), so list.len never gets updated.

---

### Post by stamatiou on 2011-07-21
I think that I need many slaps!:roll:
Million Thanks!

---

