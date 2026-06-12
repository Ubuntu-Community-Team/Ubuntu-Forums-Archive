---
title: "[C]Why do we need double pointers for inserting in a link list"
date: 2009-09-15
forum: Programming Talk
---

### Post by Canis familiaris on 2009-09-15
I tried to code my Linked List program today.

The node was defined as follows:
```

typedef struct node
{
	int info;
	struct node *next;
} LLIST;

```

Next I tried to code inserting a new node at the beginning like this:

```

LLIST *insert_at_beginning(LLIST *p, int num)
{
	LLIST *newnode = (LLIST *)malloc(sizeof(LLIST));
	
	if(newnode==NULL)
		return NULL;  /* Resource not allocated */
		
	newnode->info = num;
	newnode->next = p;
	p = newnode;
	
	return p;
}

```

However with it apparently when I tried to display the entire linked list nothing got pushed.and It did NOT work.

However according to wikipedia page, they use linked list like this (using pointer to pointer)

```

LLIST *insert_at_beginning(LLIST **p, int num)
{
	LLIST *newnode = (LLIST *)malloc(sizeof(LLIST));
	
	if(newnode==NULL)
		return NULL;  /* Resource not allocated */
		
	newnode->info = num;
	newnode->next = *p;
	*p = newnode;
	
	return *p;
}

```

And that worked flawlessly, so my question is why do we need double pointers in this case?
On an algorithm I read on adding after the linked list, however it seemed to need only a single pointer.

Please Explain. :)

The Whole program just in case (with use of double pointers)
```

#include<stdio.h>
#include<stdlib.h>

typedef struct node
{
	int info;
	struct node *next;
} LLIST;

void display(LLIST *p);
LLIST *insert_at_beginning(LLIST **p, int num);

int main()
{
	LLIST *lnk = NULL;
	insert_at_beginning(&lnk, 23);
	insert_at_beginning(&lnk, 11);
	display(lnk);
	
	return 0;
}

void display(LLIST *p)
{
	if(p==NULL)
	{
		printf("List is Empty!\n");
	}
	
	while(p!=NULL)
	{
		printf("%d -> ", p->info);
		p = p->next;
	}
	printf("End\n");
}

LLIST *insert_at_beginning(LLIST **p, int num)
{
	LLIST *newnode = (LLIST *)malloc(sizeof(LLIST));
	
	if(newnode==NULL)
		return NULL;  /* Resource not allocated */
		
	newnode->info = num;
	newnode->next = *p;
	*p = newnode;
	
	return *p;
}

```

Wrong Program BTW:
```

#include<stdio.h>
#include<stdlib.h>

typedef struct node
{
	int info;
	struct node *next;
} LLIST;

void display(LLIST *p);
LLIST *insert_at_beginning(LLIST *p, int num);

int main()
{
	LLIST *lnk = NULL;
	insert_at_beginning(lnk, 23);
	insert_at_beginning(lnk, 11);
	display(lnk);
	
	return 0;
}

void display(LLIST *p)
{
	if(p==NULL)
	{
		printf("List is Empty!\n");
	}
	
	while(p!=NULL)
	{
		printf("%d -> ", p->info);
		p = p->next;
	}
	printf("End\n");
}

LLIST *insert_at_beginning(LLIST *p, int num)
{
	LLIST *newnode = (LLIST *)malloc(sizeof(LLIST));
	
	if(newnode==NULL)
		return NULL;  /* Resource not allocated */
		
	newnode->info = num;
	newnode->next = p;
	p = newnode;
	
	return p;
}

		
		

```

---

### Post by Sporkman on 2009-09-15
Your implementation of insert_at_beginning() is returning the new head of the list, whereas the wiki version just modifies the pointer you pass in.

So for your version, you should do something like:

lnk = insert_at_beginning(lnk, 23);

---

### Post by dwhitney67 on 2009-09-15
I did not peruse all of your code, but from the looks of it, you are using "apples" and "oranges".

The first function you provide (for inserting at the beginning) is correct, however you need to reassign the returned value to your list.  Something like:
```

LLIST* list = 0;

list = insert_at_beginning(list, 23);

```

If you declare insert_at_beginning() to return a void, ie nothing, then you would have to declare it as follows:
```

void insert_at_beginning(LLIST** list, int num);

```
Then its usage:
```

LLIST* list = 0;

insert_at_beginning(&list, 23);  // note that I'm passing the address of the local variable list

```

What you probably want is to combine the first example with the following (note, this is a personal opinion):
```

LLIST* insert(LLIST* list, int num)
{
   LLIST* elem = malloc(sizeof(LLIST));

   elem->info = num;
   elem->next = list;

   list = elem;

   return list;
}

```
Usage (to repeat what is above):
```

LLIST* list = 0;

list = insert(list, 23);
list = insert(list, 11);

...

```
The function above will insert new elements at the beginning of the list; I think this is what you wanted, right?

---

### Post by Can+~ on 2009-09-15
Pointer are just numbers, if you hand them to a function as arguments, they are also being treated as local variables.

An illustration with some random Hexs:

int x = 5;
int *p = &x;
int **q = &p;

```

Symbol | Location  |  Content
  'x'  | 0x0000004 |     5
  'p'  | 0x0000008 | 0x0000004
  'q'  | 0x000000C | 0x0000008
```

So you got 'x' that holds the data, 'p' that points to it, and 'q' that points to 'p'.

Now, with the real problem:

[PHP]
void example(int *p, int size)
{
    p = malloc(sizeof(int)*size);
}
[/PHP]

Is it valid? Nope. After the call, p won't exist anymore (it's local), but the actual direction being pointed at (*p) still exists.

[PHP]
void example_good(int **p, int size)
{
    *p = malloc(sizeof(int)*size);
}
[/PHP]

Now, p points to a pointer. So it's basically telling "Change  this (p) pointer, so it points (*p) to the newly reserved space (**p)".

If it's still to difficult, stick to returning pointer directions.

---

### Post by Canis familiaris on 2009-09-15
Thanks dwhitney sporkman. Really appreciate.

So I understand that when the pointer is just passed, it's actually doesn't modify the pointer passed (similar to the case of passing in by value) and when the pointer to pointer is passed, it actually modifies the pointer.

So by the line:
list = insert(list, 23);

The head of the new pointer is returned as thus the new linked list with inserted node is returned.

Am I getting this right?

---

### Post by Sporkman on 2009-09-15
> **Canis familiaris said:**
> Thanks dwhitney sporkman. Really appreciate.

So I understand that when the pointer is just passed, it's actually doesn't modify the pointer passed (similar to the case of passing in by value) and when the pointer to pointer is passed, it actually modifies the pointer.

So by the line:
list = insert(list, 23);

The head of the new pointer is returned as thus the new linked list with inserted node is returned.

Am I getting this right?

Yes, a pointer to the new head of the list is returned.

---

### Post by Canis familiaris on 2009-09-15
> **Can+~ said:**
> 
Is it valid? Nope. After the call, p won't exist anymore (it's local), but the actual direction being pointed at (*p) still exists.

[PHP]
void example_good(int **p, int size)
{
    *p = malloc(sizeof(int)*size);
}
[/PHP]

Now, p points to a pointer. So it's basically telling "Change  this (p) pointer, so it points (*p) to the newly reserved space (**p)".

If it's still to difficult, stick to returning pointer directions.
So basically the value the pointer points to is stored and that pointer itself is local variable when passed as parameters across a function?

---

### Post by Can+~ on 2009-09-15
> **Canis familiaris said:**
> So basically the value the pointer points to is stored and that pointer itself is local variable when passed as parameters across a function?

Yup.

---

### Post by dribeas on 2009-09-16
> **Canis familiaris said:**
> So I understand that when the pointer is just passed, it's actually doesn't modify the pointer passed (similar to the case of passing in by value) and when the pointer to pointer is passed, it actually modifies the pointer.


In C you can only have pass-by-value semantics. Whatever the signature of the function takes is copied into a local variable of that type. Pass-by-reference is simulated by adding a level of indirection, you create a pointer into the element you want to change and pass that. The newly created pointer will be copied and assigned to a local variable of the function. The value that is copied is the address of the real data element that you want to change.

---

### Post by Canis familiaris on 2009-09-16
Thank you guys. Understood it perfectly.

Now when we have to insert into the end, however since we are not changing the original pointer but only the pointer link (which it it's member), so it does not require pointer to pointer or head of the new pointer. That's why it works. Right?
```

LLINK *insert_to_end(LLINK *p, int val)
{
	LLINK *t = p, *newnode = (LLINK*)malloc(sizeof(LLINK));
	
	if(newnode==NULL)
		return NULL;
	
	newnode->info = val;
	newnode->next = NULL;
	[B]
	if(t==NULL)
		t = newnode;
	else
	{
		while(t->next)
			t = t->next;
			
		t->next = newnode;
	}
[/B]
	
	return p;
}

```

Another quick question. (sorry if it's noobish :|)

Now at the bold part, I actually tried to move by

```

while(t!=NULL)
    t = t->next;
t = newnode;

```

However it did NOT work. What it seems that when t is itself transversed to the NULL pointer (the tail of the linked list), it does not then go on to point to the newnode and program does not work.
However when we reach to the second last pointer, then we can set the t->next, it seems to get pointed to newnode and works.

Can anyone shed light on this particular behaviour of NULL pointers?

---

### Post by Sporkman on 2009-09-16
Instead do:


```
LLINK *t_last = NULL;

while(t!=NULL)
{
   t_last = t;
   t = t->next;
}

t_last->next = newnode;
```

---

### Post by Sporkman on 2009-09-16
...or:

```
while(t->next!=NULL)
{
   t = t->next;
}

t->next = newnode;
```

---

### Post by dwhitney67 on 2009-09-16
Maintaining a pointer to the tail of the linked list would undoubtedly be more efficient than iterating node by node, until the end of the list is found.

Here's a basic example of using a tail pointer:
```

#include <stdlib.h>
#include <assert.h>

struct Node
{
   int          num;
   struct Node* next;
};

struct List
{
   struct Node* head;
   struct Node* tail;
};

void insert(struct List* list, int num)
{
   assert(list != 0);

   struct Node* elem = malloc(sizeof(struct Node));

   elem->num  = num;
   elem->next = 0;

   if (list->head == 0)
   {
      list->head = elem;
      list->tail = list->head;
   }
   else
   {
      list->tail->next = elem;
      list->tail = elem;
   }
}

int main()
{
   struct List list = {0, 0};

   insert(&list, 23);
   insert(&list, 11);
   insert(&list, 40);

   // ...

   return 0;
}

```

---

