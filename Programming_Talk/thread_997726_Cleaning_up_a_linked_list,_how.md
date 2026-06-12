---
title: "Cleaning up a linked list, how?"
date: 2008-11-30
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-11-30
If I want to free every node of a linked list, and then the list structure itself, how would I do that?

Can I just free the list structure, without worrying about the nodes, or will the old nodes still exist?

Or do I have to loop trough the list and free every node on the way?

---

### Post by pp. on 2008-11-30
How did you obtain the memory for the nodes?

---

### Post by crazyfuturamanoob on 2008-11-30
Here you go:
```

/* creates a new polygon but doesn't link */
struct node *new_node( )
{
    struct node *p;
    p = malloc( sizeof(struct node) );
    
    if ( p == NULL )
        return NULL;
    
    memset( p, 0, sizeof(struct node) );
    
    return p;
}

```

---

### Post by hessiess on 2008-11-30
Iliterate over the list running free() on every item in the list.

---

### Post by crazyfuturamanoob on 2008-11-30
> **hessiess said:**
> Iliterate over the list running free() on every item in the list.

Iterating over a linked list goes like this as I have learned:
```

struct node *n;
for(n=list->head; n; n=n->next)
{
    // do stuff with n
}

```
So if I do free() for n, the loop breaks. That's the problem.

---

### Post by pp. on 2008-11-30
> **crazyfuturamanoob said:**
> Iterating over a linked list goes like this as I have learned:
```

struct node *n;
for(n=list->head; n; n=n->next)
{
    // do stuff with n
}

```
So if I do free() for n, the loop breaks. That's the problem.

Copy the link to the next node before discarding the current one.

---

### Post by crazyfuturamanoob on 2008-11-30
> **pp. said:**
> Copy the link to the next node before discarding the current one.

Correct?
```

struct node *n;
struct node *n2;
for(n=list->head; n; n=n->next)
{
    n2 = n;
    free(n2);
}
free(n);

```

---

### Post by pp. on 2008-11-30
No.

The '***current***' node contains a link to the ***next*** node.

How do you find the ***next*** node when you kill the ***current*** node which holds the ***pointer to the next*** one?

---

### Post by nvteighen on 2008-11-30
Forget this post

---

### Post by crazyfuturamanoob on 2008-11-30
> **nvteighen said:**
> Forget this post

I didn't even read it.

> **pp. said:**
> No.

The '***current***' node contains a link to the ***next*** node.

How do you find the ***next*** node when you kill the ***current*** node which holds the ***pointer to the next*** one?

I don't get it.

---

### Post by geirha on 2008-11-30
This is a pseudo code of what you are currently doing
```

current= list->head
while current is not null
    free(current)
    current= current->next   //This will fail since we just freed current, so current->next does not exist anymore

```

Pseudu code of what pp. means
```

current= list->head
while current is not null
    next= current->next    // save the pointer to the next node before we free the current
    free(current)          // free the current node
    current= next          // move to next node

```

---

### Post by crazyfuturamanoob on 2008-11-30
> **geirha said:**
> This is a pseudo code of what you are currently doing
```

current= list->head
while current is not null
    free(current)
    current= current->next   //This will fail since we just freed current, so current->next does not exist anymore

```

Pseudu code of what pp. means
```

current= list->head
while current is not null
    next= current->next    // save the pointer to the next node before we free the current
    free(current)          // free the current node
    current= next          // move to next node

```

Looks smart. 

Edit:

Here's the complete C code:
```

void clean_list( struct list *l )
{
    if (list != NULL && list->nodes != NULL)
    {
        struct node *current = l->nodes;
        struct node *next;
        while (current != NULL )
        {
            next = current->next;
            free(current);
            current = next;
        }
    }
}

```

---

