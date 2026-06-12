---
title: "one-directional linked list help needed"
date: 2009-01-27
forum: Programming Talk
---

### Post by cybo on 2009-01-27
I'm reading a book "Mastering Algorithms with C". There is a chapter on linked lists there. I'm having problems understanding list_rem_next function. Specifically why do I have to pass a double pointer, void **data, why can't it be just void *data?

I tried rewriting the function with void *data, but it caused problems with the linked list

Can someone help?

```

/**********************************************
*  Define a structure for linked list elements.
***********************************************/

typedef struct ListElmt_ {
void               *data;
struct ListElmt_   *next;
} ListElmt;

/**************************************
*  Define a structure for linked lists.                                      
***************************************/

typedef struct List_ {
int                size;

int                (*match)(const void *key1, const void *key2);
void               (*destroy)(void *data);

ListElmt           *head;
ListElmt           *tail;

} List;

/*****************************************************************************
* Return Value

* 0 if removing the element is successful, or -1 otherwise.

* Description

* Removes the element just after element from the linked list specified by * list. If element is NULL, the element at the head of the list is removed. * Upon return, data points to the data stored in the element that was 
* removed. It is the responsibility of the caller to manage the storage 
* associated with the data.

*****************************************************************************/
int list_rem_next(List *list, ListElmt *element, void **data) {

ListElmt           *old_element;

/*****************************************************************************
*  Do not allow removal from an empty list.
*****************************************************************************/

if (list_size(list) == 0)
   return -1;

/*****************************************************************************
*  Remove the element from the list.
*****************************************************************************/

if (element == NULL) {

   /**************************************************************************
   *  Handle removal from the head of the list.
   **************************************************************************/

   *data = list->head->data;
   old_element = list->head;
   list->head = list->head->next;

   if (list_size(list) == 1)
      list->tail = NULL;

   }

else {

   /**************************************************************************
    Handle removal from somewhere other than the head.
   **************************************************************************/

   if (element->next == NULL)
      return -1;

   *data = element->next->data;
   old_element = element->next;
   element->next = element->next->next;

   if (element->next == NULL)
      list->tail = element;

}

/*****************************************************************************
*  Free the storage allocated by the abstract datatype.
*****************************************************************************/
free(old_element);

```

---

### Post by nvteighen on 2009-01-27
A linked list is just:
```

struct LIST
{
    /* stuff */
    struct LIST *next;
};

```

Using a void pointer is a way to have a generic linked list of arbitrary data, but of course, that leads into the usual pointer mess. 

IMO, the whole thing there is just overkill: you don't need to manage the whole list as an object; by keeping the reference to the first element you are able to traverse the whole list linearly. Think what C does with arrays: an array is just a pointer to a[0] (so, a[0] is *a)... so, to get a[9] what you do is *(a + 9).

---

### Post by cybo on 2009-01-27
Oh I know that this code is a VERY BIG overkill. But I just don't understand why to use a double pointer. The only case I ever had to use it was with strings.

> **nvteighen said:**
> A linked list is just:
```

struct LIST
{
    /* stuff */
    struct LIST *next;
};

```

Using a void pointer is a way to have a generic linked list of arbitrary data, but of course, that leads into the usual pointer mess. 

IMO, the whole thing there is just overkill: you don't need to manage the whole list as an object; by keeping the reference to the first element you are able to traverse the whole list linearly. Think what C does with arrays: an array is just a pointer to a[0] (so, a[0] is *a)... so, to get a[9] what you do is *(a + 9).

---

### Post by nvteighen on 2009-01-27
> **cybo said:**
> Oh I know that this code is a VERY BIG overkill. But I just don't understand why to use a double pointer. The only case I ever had to use it was with strings.

Ok, the code is really weird in what's it's trying to do (keep a reference to the deleted elements so you can be sure to deallocate them if necessary).

You need a double pointer because he needs to assign a value to a pointer from one function to another. If you just used (void *) data, then you would lose the reference when the function returns (as its stack will be deallocated). But with a double pointer, it is the (void **) data pointer which will be lost, but the changes you do to *data will remain.

Of course, the whole thing is absurd... you could just make the function return the pointer and everything would be much easier; and in case of error, return NULL.

---

### Post by cybo on 2009-01-27
thnx nvteighen. i appreciate the help

---

