---
title: "[SOLVED] Why is this segfaulting? I see no problem with it."
date: 2008-12-03
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-12-03
I got a function to link a new node into my linked list:
```

/* links an existing node */
void link_node( struct list *ls, struct node *n )
{
    n->next = ls->head;
    ls->head->prev = n; /* segfault with this line */
    ls->head = n;
}

```
It is supposed to link an existing node into the list.

If I remove that segfaulting line, everything works. If I don't, I get segfault.

What's wrong with it?

Node looks basically like this:
```

struct node
{
    int value;
    //some other stuff
    //...
    struct node *next;
    struct node *prev;
};
```

---

### Post by Zugzwang on 2008-12-03
So you did try using valgrind?

BTW: That might not work at the end or the beginning of the doubly-linked list.

---

### Post by crazyfuturamanoob on 2008-12-03
> **Zugzwang said:**
> So you did try using valgrind?

BTW: That might not work at the end or the beginning of the doubly-linked list.

What is valgrind?

And what it does is to add the node to the list's beginning:

1. Set **new node**'s **next** as list's **last added** (head)

2. Set list's **last added**'s **prev** to **new node** (segfault here, why?)

3. Set list's head pointing to the new node; set the **new node** as **last added**

I don't get it. What's the problem?

---

### Post by Kazade on 2008-12-03
> **crazyfuturamanoob said:**
> I got a function to link a new node into my linked list:
```

/* links an existing node */
void link_node( struct list *ls, struct node *n )
{
    n->next = ls->head;
    ls->head->prev = n; /* segfault with this line */
    ls->head = n;
}

```
It is supposed to link an existing node into the list.

If I remove that segfaulting line, everything works. If I don't, I get segfault.

What's wrong with it?

]

I would guess that ls->head is NULL or points to garbage.

Edit: I should probably elaborate...

"ls" is probably a valid pointer because you dereference it on the first line to get its "head" member. The second line the only thing you are accessing that could cause a segfault (going by the assumption "ls" is valid) is ls->head. When you try to access ls->head->prev either ls->head is NULL in which case you are dereferencing a NULL pointer, or it is pointing to memory that has: 
a.) been deleted
b.) never existed (it was never initialized to NULL so just points at some random place)

In short, there is nothing wrong with the code you just posted, but there is something wrong with the lists head.

---

### Post by dwhitney67 on 2008-12-03
> **Kazade said:**
> ...

In short, there is nothing wrong with the code you just posted, but there is something wrong with the lists head.

+1.

Initially the list contains no nodes;  upon inserting a new node (say the first node), the code needs to check if the head pointer is pointing to anything sane, or just pointing to null.

When the list is created (in the main function?), the head pointer should be set to null to indicate that the list is empty.

[php]
int main()
{
  struct list myList;
  myList.head = NULL;

  struct node* n = malloc(sizeof(struct node));
  // init node with whatever data it holds

  link_node(&myList, n);

  ...
}

void link_node(struct list* ls, struct node* node)
{
  assert(ls != NULL);
  assert(node != NULL);

  if (ls->head == NULL)
  {
    // add first node to list
    ls->head = node;
    ls->head->prev = NULL;
    ls->head->next = NULL;
  }
  else
  {
    // list exists; insert node at the beginning of the list
    node->next = ls->head;
    node->prev = ls->head->prev;   // will always be null
    ls->head   = node;
  }
}
[/php]

Unless you have a compelling reason to have a struct list, I would compose the "list" from using struct node elements.  That's really all you need.  Declare a head node, and set it equal to NULL.  Then pass that to link_node() in lieu of the struct list.

---

### Post by nvteighen on 2008-12-03
@dwhitney67: Just curious, why do you use assert()? Wouldn't it be better to check for NULLity and return an error code instead?

---

### Post by dwhitney67 on 2008-12-03
> **nvteighen said:**
> @dwhitney67: Just curious, why do you use assert()? Wouldn't it be better to check for NULLity and return an error code instead?

One can do whatever they please.  Though, I cannot think of why a null pointer would ever be passed to the function (what would be the point).  Thus once the code is out of the development test stage, and -DNDEBUG is passed via gcc, the assert() calls will no longer be made.

Wrt to memory allocations, as I have stated in other posts, if one fails to acquire the memory sought, then there are bigger issues that need to be addressed (i.e. perhaps the system does not have enough memory, or perhaps the s/w application has a memory leak).  Either way, IMO testing for null each an every time a node is inserted seems to be unnecessary, but nevertheless can be done if one wishes to do it.

---

### Post by crazyfuturamanoob on 2008-12-04
That works, although I only added the one line which checks for NULL head.

My node creating function sets next and prev to NULL by default so no need to worry about that.

Because head's prev is already NULL, then new node's prev will also be NULL.

BTW what does assert() do?

---

### Post by dwhitney67 on 2008-12-04
> **crazyfuturamanoob said:**
> ...
BTW what does assert() do?
assert() can be used to test an assertion that a variable has the value that the developer expects to "see" during run-time of the application.

To use assert(), you need to include <assert.h> (or for C++, <cassert> ).  If you define NDEBUG, the assert() function calls will behave as a no-op.  Thus it is safe to leave them in your code after testing is concluded.

Example:
[php]
int value = 5;

value *= 2;

assert(value == 10);    // ok
assert(value == 11);    // not true; hence the program will abort until you fix the issue
...
[/php]

---

