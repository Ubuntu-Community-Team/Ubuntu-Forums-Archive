---
title: "C list element swapping"
date: 2012-12-14
forum: Programming Talk
---

### Post by Odexios on 2012-12-14
Hello everyone!

I'm following a basic programming class and one of the assignments I had to solve was to write a C procedure which orders a linked list using Insertion Sort.

The actual sorting is pretty simple, but I had some issues with swapping two elements of a list.

While the code I came up with works (as far as I see), it's kind of ugly, and I'm sure it can be done with fewer lines and cases. I'm not really concerned with efficiency, but I'd like to see how I can make it more compact.

Here's the structures I need to use:

[php]struct el
{
  int info;
  struct el *next;
};
typedef struct el Element;
typedef Element *List;[/php]

And here's the code I wrote for swapping two elements:

[php]int swap(List *first_address,
         List *second_address)
{
  if (*first_address == NULL || *second_address == NULL)
    return 1;
  else if (*first_address == *second_address)
    return 0; /*nothing to be done*/
  else
  {

    if ((*second_address)->next == *first_address)
    /*just to be sure that if the two elements are adjacent
      the first one comes before the second one*/
    {
      List *temp;
      temp = second_address;
      second_address = first_address;
      first_address = temp;
    }

    if ((*first_address)->next == *second_address)
    /*the two elements are adjacent*/
    {
      List temp;
      temp = *second_address;
      (*first_address)->next = (*second_address)->next;
      temp->next = *first_address;
      *first_address = temp;
      return 0;
    }
    else
    {
    /*there's at least one element between the two*/
      List temp;
      temp = (*first_address)->next;
      (*first_address)->next = (*second_address)->next;
      (*second_address)->next = temp;
      temp = *first_address;
      *first_address = *second_address;
      *second_address = temp;
      return 0;
    }
  }
}
[/php]

Example of execution:
[php]int main()
{
  List test;
  int dim;
  dim = 5;
  create_random_list(&test, dim);
  print_list(test);
  swap(&test, &(test->next));
  print_list(test);
  swap(&test, &(test->next->next));
  print_list;
}
[/php]
```
0 -> 8 -> 7 -> 5 -> 7 -> //
8 -> 0 -> 7 -> 5 -> 7 -> //
7 -> 0 -> 8 -> 5 -> 7 -> //

```
For instance, do I really need to consider separately the case in which the two elements are adjacent? I wasn't able to come up with a general solution.

Any comment is appreciated, even if not directly related with what I asked; pointers in the right direction are more appreciated than an explicit better solution.

---

### Post by trent.josephsen on 2012-12-14
```
int swap(List *first_address,
         List *second_address)
```
What are you swapping? Lists? I find that hiding the indirection makes the algorithm less clear, which is the opposite of what a typedef should do.

I don't like the exposed interface of this one, either. To make it work you have to pass the address of the "next" member of the *previous element in the struct*. That is, given e1 -> e2 -> e3 -> e4 -> e5, to swap e2 and e5 you must call swap(&e1.next, &e4.next). That's just confusing. There are two ways I'd consider solving this problem:

1) Swap the values, not the pointers. In your case each node only stores an int. You'd save a lot of time, both development and machine, if you just leave the nodes in place and exchange the values they contain.

2) Swap by indexes. Pass "swap" the address of the head, plus the indexes of the 2 elements you want to swap. Then it's easy to find all 4 nodes you need to modify without having to pass weird values.

Since you have to traverse the list (at least in part), method 2 will be slower with long lists that contain simple data, whereas method 1 will be slower when copying the data takes a long time as compared to walking down the list.

(Obviously a doubly-linked list would not suffer these problems, at the expense of more complication.)

As for your question about there being a more efficient way without doing as many checks, yep, there is one. It might help to draw a picture and list the assignments that have to happen. (There are 4 of them, although some might change the same value twice in certain cases.) If you give up, Google for "swap nodes singly linked list" or some such. It's a simple solution but I always found it hard to visualize.

---

### Post by spjackson on 2012-12-14
> **Odexios said:**
> I'm following a basic programming class and one of the assignments I had to solve was to write a C procedure which orders a linked list using Insertion Sort.

The actual sorting is pretty simple, but I had some issues with swapping two elements of a list.

While many sorting algorithms involve swapping elements, I don't understand how Insertion Sort requires a swap.

---

### Post by lisati on 2012-12-14
> **spjackson said:**
> While many sorting algorithms involve swapping elements, I don't understand how Insertion Sort requires a swap.

Although "swapping" might not be the best word to describe how the insertion sort works, my understanding is that depending on how you implement it, there can be a fair bit of moving things around involved.

A nice animation of one possible implementation can be found at [Wikipedia]("http://en.wikipedia.org/wiki/Insertion_sort").

---

### Post by trent.josephsen on 2012-12-14
> **lisati said:**
> Although "swapping" might not be the best word to describe how the insertion sort works, my understanding is that depending on how you implement it, there can be a fair bit of moving things around involved.
Not with a linked list, though, since you don't have to move items around to insert an item into the middle of the sorted list.

Selection sort is one that would require a lot of swapping no matter how you slice it... I think.

Edit: I'm wrong. You can still do selection sort on a linked list without swapping; Wikipedia even describes how.

---

### Post by Impavidus on 2012-12-15
I don't think linked listst ever require swapping of elements when sorting, just cutting from one location and inserting at another. This is very nice if you frequently delete/add elements, especially if the elements are huge structs. (I like linked lists too if I want a list to be sorted in different ways at the same time. I find them easier to manage than pointer arrays). When working with linked lists I prefer merge sorts or insert sorts on double linked lists (very efficient if already nearly sorted), but an insert sort on a single linked list works as well using a little bit of pointer wizardry:
[PHP]Element *item1, *item2, *pointer_to_first_element;

/* Move the element after item1 to the start of the list */
insert(&pointer_to_first_element, &(item1->next));

/* Insert the element after item1 after item2 */
insert(&(item2->next), &(item1->next));

/* Function to insert source at dest */
void insert(Element **dest, Element **source)
{
    Element *temp;

    /* Cut element */
    temp=*source;
    *source=temp->next;

    /* Insert element */
    temp->next=*dest;
    *dest=temp;
}[/PHP]It even works when source==dest. How to find out which element to insert where I leave to you. You may want to use a double while loop. The basic idea of how to cut and insert an element must be clear from this example (but of course, I encourage you to write your own code).

Oh, and you might want to try your hand on a double linked list. It's often more efficient (depending on the amount of entropy in the list), but requires some modifications.

---

### Post by ofnuts on 2012-12-15
> **Odexios said:**
> I'm following a basic programming class and one of the assignments I had to solve was to write a C procedure which orders a linked list using Insertion Sort.

The actual sorting is pretty simple, but I had some issues with swapping two elements of a list.
You don't swap elements in an insertion sort?  In the insertion sort, you navigate down the list, and if you find that element N+1 is smaller than element N, you cut it from the list and insert  it at the right place between elements 1 and N.

---

### Post by Impavidus on 2012-12-15
> **ofnuts said:**
> You don't swap elements in an insertion sort?  In the insertion sort, you navigate down the list, and if you find that element N+1 is smaller than element N, you cut it from the list and insert  it at the right place between elements 1 and N.
Indeed, you cut and insert, without moving any other elements. Swapping elements is what you usually do in in-place sorting algorithms on arrays (like quicksort, heap sort, bubble sort, ...).

---

