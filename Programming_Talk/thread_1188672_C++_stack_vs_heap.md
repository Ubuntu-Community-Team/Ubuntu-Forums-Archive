---
title: "C++ stack vs heap"
date: 2009-06-15
forum: Programming Talk
---

### Post by Mirge on 2009-06-15
So, I'm reading about dynamically allocating memory via "new" keyword in C++ (with its counterpart "delete" to free up that memory).

It's my understanding that using new/delete allocates memory from the heap, rather than from the stack. Anything allocated from the heap must be explicitly freed... is there any advantage to using new/delete?

I'm just curious because I constantly ran into pointers in my Qt4 book (C++ GUI Programming with Qt 4)... and I didn't really know if that was necessary or not. I've google'd around and people say it's useful for persistant data, and I've heard "performance" bounced around... but I just still have a hard time following. What are the advantages?

Thanks as always folks... sincerely appreciated.

---

### Post by Can+~ on 2009-06-15
Stack variables (or just local variables) can be defined statically defined and typed during compile time only, dynamic allocation does exactly what it says, it allows you to allocate memory during runtime.

You haven't got to the point when it's useful, for example, can you create a list of integers?  A list that let's you append() or remove() elements from it?

---

### Post by Mirge on 2009-06-16
> **Can+~ said:**
> Stack variables (or just local variables) can be defined statically defined and typed during compile time only, dynamic allocation does exactly what it says, it allows you to allocate memory during runtime.

** You haven't got to the point when it's useful**, for example, can you create a list of integers?  A list that let's you append() or remove() elements from it?

Ah, makes sense (see bold).

By list, do you mean list<int> ? I would imagine that would HAVE to be dynamically allocated, since you can use the .erase() and .push_back() methods to change the size of the list at run-time. Thanks for helping clarify :). I still don't quite understand the benefit of Qt4 using them like crazy though... maybe just so it's only allocating memory as needed, rather than allocating a ton right off the bat?

---

### Post by Can+~ on 2009-06-16
> **Mirge said:**
> Ah, makes sense (see bold).

By list, do you mean list<int> ? I would imagine that would HAVE to be dynamically allocated, since you can use the .erase() and .push_back() methods to change the size of the list at run-time.

This is the reason why I never suggest C++ as a first language; It demands knowledge on dynamic allocation, yet it has some classes that hide it entirely, thus giving the student a hard time figuring why some things are that way. list<int> is acting as a wrapper for an underlying dynamic allocation, each time you push a new element it's being dynamically inserted into the list.

> Thanks for helping clarify :). I still don't quite understand the benefit of Qt4 using them like crazy though... maybe just so it's only allocating memory as needed, rather than allocating a ton right off the bat?

So let's say you create a window inside a { }, would it make sense that as soon as you finish a function, namespace, w/e the window automatically vanishes?

I will soon post a dynamic allocation in C as an example.

---

### Post by Mirge on 2009-06-16
Awesome, can't thank ya enough for sharing your insight with me... tremendous help!

---

### Post by Can+~ on 2009-06-16
[PHP]/*
 * dynlist.c
 *
 *  Created on: Jun 16, 2009
 *      Author: canxp
 */

#include <stdio.h>
#include <stdlib.h>

/* Define a single element of a list called a "node".
 * It stores the value and a pointer to the next node.
 * */
typedef struct TNODE
{
	int value;
	struct TNODE *next;
}node;

/* Define a special type of node called "list" that acts as
 * a reference to the start of the list. Allows to insert directly in the end.
 * */
typedef struct
{
	int length;
	node* head;
	node* tail;
}list;


node *new_node(int value)
{
	/* Creates a new node
	 * 
	 * args:
	 * 	value: number to be stored
	 * 
	 * returns: pointer to the new node.
	 */
	
	// Allocate N = (sizeof(node)) bytes and cast it.
	node* nnode = malloc(sizeof(node));
	
	nnode->value = value;
	nnode->next = NULL;
	
	return nnode;
}

list *new_list()
{
	/* Creates a new list
	 * 
	 * args: none
	 * 
	 * returns: pointer to the new list.
	 */
	
	// Allocate N = (sizeof(list)) bytes and cast it.
	list* nlist = malloc(sizeof(list));
	
	nlist->length = 0;
	nlist->head = NULL;
	nlist->tail = NULL;
	
	return nlist;
}

node *append(list *alist, int value)
{
	/* Appends a new integer to a list.
	 * 
	 * args:
	 * 	alist: the list to do an append operation.
	 * 	value: value to be stored.
	 * 
	 * returns: pointer to the new node (optional)
	 */
	
	node *nnode = new_node(value); 
	
	if (alist->length == 0)
	{
		// It's empty, it's both the head and the tail.
		alist->head = nnode;
		alist->tail = nnode;
	}else{
		// It's not empty, append to the end.
		alist->tail->next = nnode;
		alist->tail = nnode;
	}
	
	alist->length++;
	
	printf(" List: Appended element %d\n", value);
	
	return nnode;
}

void printlist(list *alist)
{
	/* Prints the contents of a list.
	 * 
	 * args: 
	 * 	alist: the list containing the data.
	 * 
	 * returns: nothing.
	 */
	
	node *iter;
	
	if (alist->length == 0)
	{
		printf("Empty list.\n");
		return;
	}
	
	printf("[");
	for (iter=alist->head; iter; iter=iter->next)
	{
		printf("%d, ", iter->value);
	}
	printf("] (length:%d)\n", alist->length);	
}

void freelist(list *alist)
{
	/* Destroys a list and frees its memory.
	 * 
	 * args: 
	 * 	alist: the list containing the data.
	 * 
	 * returns: nothing.
	 */
	
	int totalsize = alist->length;
	node *iter, *killiter;
	
	// Loop and free every node
	while (iter)
	{
		killiter = iter;
		iter=iter->next;
		
		free(killiter);
	}
	
	// Free the last element
	free(killiter);
	
	// Free the list
	free(alist);
	
	printf(" List: freed %d [Bytes]", totalsize*sizeof(node) + sizeof(list));
}

int main()
{
	list *mylist = new_list();
	
	printlist(mylist);
	
	// Add some stuff
	append(mylist, 10);
	append(mylist, 18);
	append(mylist, 0);
	append(mylist, -7);
	
	printlist(mylist);
	
	freelist(mylist);
	
	return 0;
}[/PHP]

Not sure if it's very "stable" but that's the basic idea.

Testing it:
```
Empty list.
 List: Appended element 10
 List: Appended element 18
 List: Appended element 0
 List: Appended element -7
[10, 18, 0, -7, ] (length:4)
 List: freed 44 [Bytes]
```

---

