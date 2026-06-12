---
title: "[SOLVED] Can't get linked lists working in C"
date: 2008-11-11
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-11-11
I tried to make as simple linked list as possible in C.
Here's what I got, exactly. Nothing removed, nothing edited, this is the original file as it is:
```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

struct node
{
    
    struct node *next;
    
    char name[80];
    
    int value;
    
}

struct list
{
    struct node *nodes;
}

struct list *init_list()
{
    struct list *L;
    L = malloc( sizeof(struct list) );
    L->nodes = NULL;
    return L;
}

struct node *create_node( char name[80], int value )
{
    struct node *n;
    n = malloc( sizeof(struct node) );
    
    if ( n == NULL )
        return NULL;
    
    memset( n, 0, sizeof(struct node) );
    
    n->name = name;
    n->value = value;
    
    return n;
}

void add_node( struct list *L, struct node *N )
{
    N->next = L->nodes;
    L->nodes = N;
}

void destroy_node( struct node *N )
{
    free(N);
}

void looptrough( struct list *L )
{
    struct node *N;
    for (N=L->nodes; N; N=N->next)
        printf("Name: \"%s\"\nValue: %i\n", N->name, N->value);
}

int main()
{
    /* do stuff */
    return 0;
}
```
But when I try to compile it:
> arho@ohra-laptop:~/Työpöytä/C/teststuff/linkedlist$ gcc -o list list.c
list.c:21: error: two or more data types in declaration specifiers
list.c:21: error: two or more data types in declaration specifiers
list.c: In function ‘init_list’:
list.c:26: warning: return from incompatible pointer type
list.c: In function ‘create_node’:
list.c:39: error: incompatible types in assignment
arho@ohra-laptop:~/Työpöytä/C/teststuff/linkedlist$ 

Can't get further. I need help. I'm a total noob in C, and I got no idea what might it be.

---

### Post by Cracauer on 2008-11-11
Missing semicolons;

---

### Post by mvs1207 on 2008-11-11
missing ';' for struct definitions.

---

### Post by crazyfuturamanoob on 2008-11-11
Where do I have to put semicolons?

Edit: Figured out with reference manual.

---

### Post by Sinkingships7 on 2008-11-11
> **crazyfuturamanoob said:**
> Where do I have to put semicolons?

After the closing brace of struct definitions. Example:
[php]
struct node{
    struct node *next;
};
[/php]
You can also write it like this:
[php]
struct{
    struct node *next;
}node;
[/php]
but I personally don't prefer it...

---

### Post by Sinkingships7 on 2008-11-11
double post

---

