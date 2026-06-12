---
title: "[C++] Ordered Linked Lists"
date: 2010-10-13
forum: Programming Talk
---

### Post by xnerdx on 2010-10-13
I'm currently reading through the book _Practical C++ Programming_ and think I may have actually found an error in the code within the book (last time I thought this I caught myself as being wrong). This time I elaborated on the issue more than I did previously and want to confirm that my findings are accurate so that I don't teach myself the wrong things. The following is a code snippet from the book (I do not own the rights to any of the following code):
```

void linked_list::enter(int item):
{ 
    linked_list_item *before_ptr; // Insert after this element
    linked_list_item *after_ptr;  // Insert before this element

    /* 
     * Warning: This routine does not take 
     *   care of the case where the element is 
     *   inserted at the head of the list
     */

    after_ptr = first_ptr;
    while (true) { 
        before_ptr = after_ptr; 
        after_ptr = after_ptr->next_ptr; 

        // Did we hit the end of the list?
        if (after_ptr == NULL) 
            break; 

        // Did we find the place?
        if (item >= after_ptr->data) 
            break; 
    }

```
I know this is incomplete but the only relevant information about the rest of the classes is that the list starts at first_ptr and each element of the list stores its value in an int variable (data, I.E. after_ptr->data).

The issue with this code is that (at least for the following example) the data is put into the list at the wrong point. (The new data is inserted between before_ptr and after_ptr, and then obviously linked to the rest of the list). Here is the example:

[2]->[16]->[24] (where int item = 20) The following would happen:
(first_ptr points to [2]) after_ptr = [2], before_ptr = [2], after_ptr = [16]. Now the conditionals:
after_ptr != NULL (don't break). after_ptr->data = 16, (20 >= 16) is true, break.
Now the data [20] is going to be inserted, leaving the list looking like this:
[2]->[20]->[16]->[24]

I imagine the conditional should be:
if( item >= before_ptr->data && item <= after_ptr->data) break;

Is this the way that it should be done? Thanks in advance.

---

### Post by raf_kig on 2010-10-13
> **xnerdx said:**
> 
I imagine the conditional should be:
if( item >= before_ptr->data && item <= after_ptr->data) break;

Is this the way that it should be done? Thanks in advance.

Actually, comparing with the item which will be after your new item  is not necessary.
If item->next->data >= item->data for all items then the list is ordered.
So comparing with the new predecessor is necessary, the successor can be ignored.

/e: The other way around ;-)

I'd probably write the function like that:
```
don't look here, look at dwhitney67's code ;-)

```
But I'm not a C++ Programmer ;-)

---

### Post by spjackson on 2010-10-13
> **xnerdx said:**
> I'm currently reading through the book _Practical C++ Programming_ and think I may have actually found an error in the code within the book (last time I thought this I caught myself as being wrong). This time I elaborated on the issue more than I did previously and want to confirm that my findings are accurate so that I don't teach myself the wrong things.

Out of context, the code you gave is not good. Perhaps the author goes on to point out the deficiencies and corrects them later in the chapter... Hopefully he does, but I don't know.

I usually find the ACCU book reviews to be pretty reliable, and this book does not get a good rating. [http://accu.org/index.php?module=bookreviews&func=search&rid=1615](http://accu.org/index.php?module=bookreviews&func=search&rid=1615)

Nor do the author's two other books reviewed there.

---

### Post by dwhitney67 on 2010-10-13
> **raf_kig said:**
> 
But I'm not a C++ Programmer ;-)
This is not really a criteria needed to resolve the problem, although your code syntax looks ok.

What is wrong though, is that your code could possibly insert the new value in the wrong place.

If the list has values 10->20->30, and you attempt to insert the value 25, then the list would appear as 10->25->20->30.

I agree with the OP that something seems afoul with the code presented in the book, not that I agree with the author's or the OP's solution.

If the purpose is to do a sorted-insertion, then the "before" pointer is merely a place holder, whereas the "after" pointer should be used for the comparison.

Stealing your code:
```

linked_list_item* linked_list::enter(int item)
{
    linked_list_item *new_item = new linked_list_item(item);

    if (!first_ptr) {
        return first_ptr = new_item;
    }

    linked_list_item* current  = first_ptr;
    linked_list_item* previous = 0;

    do {
        previous = current;
        if (item < current->data)
            break;
    } while (current = current->next)

    tmp = previous->next;
    previous->next = new_item;
    new_item->next = tmp;
    return new_item;
}

```
P.S.  I'm not a compiler.  :-)

---

### Post by xnerdx on 2010-10-13
I understand the fact that the before_ptr is simply a place holder. It's more useful when it comes to adding the new item (instead of changing the position of after_ptr you just reference the before_ptr). From what I can see is that you would want to ensure that the after_ptr->data is >= item. In other words, would the simple revision of my previous revision be to only compare after_ptr->data to item to ensure after_ptr (more or less the current position) is greater than item?
```

void linked_list::enter(int item):
{ 
    linked_list_item *before_ptr; // Insert after this element
    linked_list_item *after_ptr;  // Insert before this element

    /* 
     * Warning: This routine does not take 
     *   care of the case where the element is 
     *   inserted at the head of the list
     */

    after_ptr = first_ptr;
    while (true) { 
        before_ptr = after_ptr; 
        after_ptr = after_ptr->next_ptr; 

        // Did we hit the end of the list?
        if (after_ptr == NULL) 
            break; 

        // Did we find the place?
        if (item <= after_ptr->data) 
            break; 
    }

```
The after_ptr and before_ptr are accessed to index the new location for the data (item)

---

### Post by raf_kig on 2010-10-13
> **dwhitney67 said:**
> What is wrong though, is that your code could possibly insert the new value in the wrong place.
To be precise, it will only by chance insert elements in an ordered way :-)

---

