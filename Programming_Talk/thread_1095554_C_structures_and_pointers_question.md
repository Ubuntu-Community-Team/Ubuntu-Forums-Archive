---
title: "C structures and pointers question"
date: 2009-03-13
forum: Programming Talk
---

### Post by Znupi on 2009-03-13
I learned C++ at school, but I want to learn plain C, too. A problem I bumped my head into was how to pass pointers by reference in C (I hope that's the right terminology). This is especially useful when working with linked lists and defining functions that have to change a pointer (e.g. functions that initialize / insert items in the list). In C++ I'd do this:
```

// *&p allows us to modify the address p points to.
void insert(node *&p, int value) {
   // If p was not initialize, do it now.
   if (p == NULL) {
      p = new node;
      p->value = value;
      p->next = NULL;
      return;
   }
   // Otherwise, insert a new item at the end of the list.
   node *q = p;
   while (q->next) q = q->next;
   q->next = new node;
   q = q->next;
   q->value = value;
   q->next = NULL;
}

```
I have tried similar solutions in C, but to no avail. Here's what I've tried:
```

#include <stdio.h>
#include <stdlib.h>

// Define list node structure
typedef struct struct_node {
	int value;
	struct struct_node *next;
} node;

void insert(node *&p, int value) {
	// List not initialized
	if (p == NULL) {
		p = malloc(sizeof(node));
		p->next = NULL;
		p->value = value;
		return;
	}
	// Insert at the end
	node *q = p;
	while (q->next) q = q->next;
	q->next = malloc(sizeof(node));
	q = q->next;
	q->next = NULL;
	q->value = value;
}

int main() {
	node *p = NULL;
	int x = 1;
	while (x) {
		printf("Insert new item: ");
		scanf("%i", &x);
		insert(p, x);
	}
	while (p) {
		printf("%i ", p->value);
		p = p->next;
	}
	return 0;
}

```
But that gives an error:
```
ref.c:10: error: expected ‘;’, ‘,’ or ‘)’ before ‘&’ token
```
Line 10 is the header of the insert() function.

The program works if I remove the ampersand (&) from the header of the insert() function and initialize the list with one node. But, that isn't always useful, for example when you create a function that inserts an element into a list, keeping the list ordered (it may have to insert the node at the beginning of the list).

How could I change *p in my function so that it changes in main(), too? Thanks.

---

### Post by Phristen on 2009-03-13
In the argument list, change *& to just &.

---

### Post by Znupi on 2009-03-13
> **Phristen said:**
> In the argument list, change *& to just &.
I get the same error.

---

### Post by WW on 2009-03-13
You can pass a pointer to the pointer (and adjust the rest of the code appropriately):
```

#include <stdio.h>
#include <stdlib.h>

// Define list node structure
typedef struct struct_node {
	int value;
	struct struct_node *next;
} node;

void insert(node **p, int value) {
	// List not initialized
	if (*p == NULL) {
		*p = malloc(sizeof(node));
		(*p)->next = NULL;
		(*p)->value = value;
		return;
	}
	// Insert at the end
	node *q = *p;
	while (q->next) q = q->next;
	q->next = malloc(sizeof(node));
	q = q->next;
	q->next = NULL;
	q->value = value;
}

int main() {
	node *p = NULL;
	int x = 1;
	while (x) {
		printf("Insert new item: ");
		scanf("%i", &x);
		insert(&p, x);
	}
	while (p) {
		printf("%i ", p->value);
		p = p->next;
	}
	return 0;
}

```
Note that one of the changes was the call to insert() in main():
```

		insert(&p, x);

```
So the address of p, not p, is passed to insert().

---

### Post by Znupi on 2009-03-13
Ahh, thanks! I -did- try insert(&p, x) but did not think of using **p in the argument list. It makes sense now. Thank you!

---

### Post by hanniph on 2009-03-14
C does not support passing arguments by reference. It only deals with pass by value but you can imitate pass by reference passing pointers to variables as shown before.

---

