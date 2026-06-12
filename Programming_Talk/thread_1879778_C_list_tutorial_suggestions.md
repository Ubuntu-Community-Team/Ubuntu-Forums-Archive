---
title: "C list tutorial suggestions"
date: 2011-11-12
forum: Programming Talk
---

### Post by gameguy on 2011-11-12
I do not understand how to use lists in C, and couldn't find anything through googling for it. Does anyone know a good tutorial for lists / arrays in C? I found plenty on C# and some on C++, but couldn't seem to find any on C (which also seems to be the hardest for a python user).

Thanks

---

### Post by Barrucadu on 2011-11-12
I shall demonstrate with chars, but the principle is the same for any type:

Allocate:
```
char* list = malloc(size);
```

Resize:
```
char *newlist = realloc(list, newsize);
if (newlist != NULL) list = newlist;
```

Access:
```
char foo = list[x];
```

Modify:
```
list[x] = 'a';
```

Free:
```
free (list);
```

---

### Post by gameguy on 2011-11-12
How do you remove an item from a list?

---

### Post by Barrucadu on 2011-11-12
From the end of a list, you just shrink the list (with realloc), from somewhere in the middle of the list, you can either make a new list with all of the elements except the one you don't want, or just set it to some value which means "Nothing to see here".

For instance, in the char array I showed above, you could use the null character, '\0', as such a value.

**edit:**

Alternatively, you could use a linked list. Here is an (untested) example for chars:

```

/**
 * Data structure to represent a node in a linked list
 */
struct node
{
  char data;         /**< Data in this node */
  struct node* next; /**< Pointer to the next node */
}

/**
 * Get the value at a given position in the list
 *
 * @param list     The list to access
 * @param position Number of element (starting from zero)
 *
 * @return The value of list[position]
 */
char
list_get (struct node* list, unsigned int position)
{
  if (list == NULL) return '\0';

  return (position == 0) ? list->data : list_get (list->next, position - 1);
}

/**
 * Add a value to the end of the list
 *
 * @param list The list to modify
 * @param data The data to add
 */
void
list_add_at_end (struct node* list, char data)
{
  if (list == NULL) return;

  if (list->next == NULL)
    {
      list->next = malloc (struct Node);
      list->next->data = data;
      list->next->next = NULL;
    }
  else
    {
      list_add_at_end (list->next, data);
    }
}

/**
 * Change the value of a node
 *
 * @param list     The list to modify
 * @param position The number of the element to change
 * @param data     The new data
 */
void
list_change (struct node* list, unsigned int position, char data)
{
  if (list == NULL) return;

  if (position == 0)
    list->data = data;
  else
    list_change (list->next, position - 1, data);
}

/**
 * Delete a value from a list
 *
 * @param list     The list to access
 * @param position Number of element (starting from zero)
 *
 * @return A new list (old one gets clobbered)
 */
struct node*
list_delete (struct node* list, unsigned int position)
{
  if (list == NULL) return;

  struct node *out = list;

  if (position == 0)
    {
      struct node *oldnext = list->next;
      free (list);
      out = oldnext;
    }
  else
    {
      list->next = list_delete (list->next, position - 1);
    }

  return out;
}

/**
 * Free a list
 *
 * @param list List to free
 */
void
list_free (struct node* list)
{
  if (list == NULL) return;

  list_free (list->next);

  free (list);
}

```

---

### Post by MadCow108 on 2011-11-12
> **gameguy said:**
> I do not understand how to use lists in C, and couldn't find anything through googling for it. Does anyone know a good tutorial for lists / arrays in C? I found plenty on C# and some on C++, but couldn't seem to find any on C (which also seems to be the hardest for a python user).

Thanks

C has no builtin datastructures like list.
You only deal with blocks of memory and addresses to these.

With these you can implement lists in whatever way you like, depending on your requirements.
E.g. in cpython lists are implemented as continous memory blocks as barrucadu described, but usually when you talk about lists you mean seperated memory blocks connected by one or two pointers to a string of blocks:
```

struct list
{
void * datablock;
struct list * next_block;
struct list * prev_block;
};

// manually build a list, usually done via functions
struct list * block1 = malloc(sizeof(struct list));
struct list * block2 = malloc(sizeof(struct list));
struct list * block3 = malloc(sizeof(struct list));
block1->datablock = malloc(sizeof(int));
block2->datablock = malloc(sizeof(int));
block3->datablock = malloc(sizeof(int));

//put some data in
*(block1->datablock) = 5;
*(block2->datablock) = 6;
*(block3->datablock) = 7;

// link them, null denotes end of list
block1->prev_block = NULL
block1->next_block = block2
block1->prev_block = block2
block1->next_block = block3
block1->prev_block = block2
block1->next_block = NULL

// delete block2
block1->next_block = block3
block3->prev_block = block1
free(block2->datablock),
free(block2),


```

you have to write all the functions creating and managing these blocks yourself, or you use a library that provides this functionality (e.g. glib)

---

