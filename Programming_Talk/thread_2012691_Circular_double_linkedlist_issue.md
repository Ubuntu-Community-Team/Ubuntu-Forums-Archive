---
title: "Circular double linkedlist issue"
date: 2012-06-29
forum: Programming Talk
---

### Post by spanlength1 on 2012-06-29
Hi , I am implementing a circular linkedlist. I have got all the basic functions working but facing some issue in the ringMove function. Eventhough it is working fine ,I am getting valgrind error.Please see if there is some error.

```

#ifndef TKK_AS_C_RINGLIST_H
#define TKK_AS_C_RINGLIST_H

#include <stddef.h>

// TODO: RingNode definition
// Required variables:
// - data: array of 101 characters (max. 100 + terminating NUL)
// - prev and next: pointers to previous/next nodes
typedef struct RingNode_s {
    char data[101];
    struct RingNode_s *next;
    struct RingNode_s *prev;
}RingNode;

/** Construct a new node.
* @param pos if NULL, a new ring is created, otherwise the new node is inserted after node pos.
* @param data a C string used to initialize the data (undefined behavior for strings longer than 100 characters).
* @return the new node (connected to the old ring if pos was provided).
**/

RingNode* ringAdd(RingNode* pos, char const* data);

/** Move a set of nodes to another position. O(1).
* Takes a range of nodes [first, last] and moves them to a new position. The new
* position may be within another ring or in the same ring as the range, but the
* behavior is undefined if the destination is within the range to be moved.
* @param first the first node to move.
* @param last the last node to move.
* @param pos the destination: the moved nodes are inserted after node pos.
* @return first
**/

RingNode* ringMove(RingNode* first, RingNode* last, RingNode* pos);

#endif

```

```

#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include "ringlist.h"

RingNode* ringAdd(RingNode* pos, char const* data) {
    RingNode *newring = malloc(sizeof (RingNode));
    strcpy(newring->data, data);
    if (pos) {
        newring->prev = pos;
        newring->next = pos->next;
        pos->next = newring;
        (newring->next)->prev = newring;
    } else {
        newring->next = newring;
        newring->prev = newring;
    }
    return newring;
}

RingNode* ringMove(RingNode* first, RingNode* last, RingNode* pos) {

    RingNode *item = first;
    RingNode *final = last;
    while (item->next != final) // valgrind error Invalid read of                                        size 8 
    {
        item = item->next;
        if (item == pos)
            return first;
    }
    (first->prev)->next = last->next;
    (last->next)->prev = first->prev;
    last->next = pos->next;
    (pos->next)->prev = last;
    pos->next = first;
    first->prev = pos;
    return first;
}

```

```

#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include "ringlist.h"

int main() {


    RingNode* ringitem1 = ringAdd(NULL, "ringitem1");
    RingNode* ringitem2 = ringAdd(ringitem1, "ringitem2");
    RingNode* ringitem3 = ringAdd(ringitem2, "ringitem3");
    RingNode* ringitem4 = ringAdd(ringitem3, "ringitem4");
    RingNode* ringitem5 = ringAdd(ringitem4, "ringitem5");
    RingNode* ringitem6 = ringAdd(ringitem5, "ringitem6");
    RingNode* ringitem7 = ringAdd(ringitem6, "ringitem7");
    RingNode* ringitem8 = ringAdd(ringitem7, "ringitem8");
    RingNode* ringitem9 = ringAdd(ringitem8, "ringitem9");

    ringMove(ringitem5, ringitem8, ringitem9);

    return 0;
}

```

Please sujjest what might be the issue. For clarity and simplicity i have not added the ringDestroy function which does cleanup.

---

### Post by ofnuts on 2012-07-01
It could be useful to post the valgrind report as well.

---

### Post by dwhitney67 on 2012-07-01
> **spanlength1 said:**
> Hi , I am implementing a circular linkedlist. I have got all the basic functions working 

I can see an issue within RingMove() (the while loop condition is incorrect), however what confuses me more are the comments that you have given for the function.

You indicate that the function "Takes a range of nodes [first, last] and moves them to a new position.".  However with the return statement in the while loop, I don't see anything that indicates that you are moving anything anywhere.

So, if you could please clarify what is the intent of the method (it does not seem like a normal public interface for a circular list), then I or someone else may be able to help you better.

P.S.  There are lot more error checking that needs to be performed within RingMove(), that I question whether you should offer this public function at all.  For instance, you assume that 'first' comes before 'last', and that all of the parameters are non-NULL.

---

