---
title: "C Signle List function problem"
date: 2011-07-20
forum: Programming Talk
---

### Post by stamatiou on 2011-07-20
I have this function in C that will add a node at the end of the list, but I Have an error.

Here's the code:

```
Node *list_append_slow_by_value(Node *list,int value)
{
    Node *new = calloc(1,sizeof(Node));
    new->data = value;
    if(!*list)
    {
        list = new;
        exit(1);
    }
    
    while(list->next!=NULL)
    {
        list = list->next;
    }
    return list;    
}
```and the error:

```
error: wrong type argument to unary exclamation mark
```
Edit:the function must add to the beginning of the list

---

### Post by era86 on 2011-07-20
Try replace 

if(!*list)

with

if(!(*list))

---

### Post by stamatiou on 2011-07-20
> **era86 said:**
> Try replace 

if(!*list)

with

if(!(*list))
No it did not work...:(

---

### Post by dwhitney67 on 2011-07-20
Inserting at the end of the list is inefficient, unless you maintain a "tail" pointer.

Nevertheless, to get you on your way:
```

Node *list_append_slow_by_value(Node *list,int value)
{
    Node *new = calloc(1,sizeof(Node));
    new->data = value;
    if(**!list**)
    {
        list = new;
        **//exit(1);**
    }
[B]    else
    {
        Node* node = list;
        while(node->next)
        {
            node = node->next;
        }
        node->next = new;
    }[/B]
    return list;    
}

```

---

### Post by karlson on 2011-07-20
> **stamatiou said:**
> I have this function in C that will add a node at the end of the list, but I Have an error.

Here's the code:

```
Node *list_append_slow_by_value(Node *list,int value)
{
    Node *new = calloc(1,sizeof(Node));
    new->data = value;
    if(!*list)
    {
        list = new;
        exit(1);
    }
    
    while(list->next!=NULL)
    {
        list = list->next;
    }
    return list;    
}
```and the error:

```
error: wrong type argument to unary exclamation mark
```
Edit:the function must add to the beginning of the list

First off make up your mind if this is supposed to add a node to the beginning or the end of the list?

The error is actually very simple, and the reason is that you need to understand a difference between a pointer and a value stored at the address stored in the pointer variable.

so instead of:
```

if(!*list)

```

you want:
```

if(!list)

```

and my suggestion is that until you gain some more experience use code like this

```

if( NULL != list )

```

This way you would get a better description of the error.

---

