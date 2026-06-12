---
title: "a little help on a c++ program"
date: 2007-02-05
forum: Programming Talk
---

### Post by onewaytrip on 2007-02-05
i ve always been terrible with pointers and i have an assignment which has to do with pointer and its killing me. well any let me just show the code and example.

To insert, you are given a reference to the list pointer, representing the head (front) of the list. Remember, that if the list is currently empty, this pointer will be NULL! You'll have to check for that as a special case. You are also given the integer to be stored in the new node. 

    DoubleLinkedList* dl_insert( DoubleLinkedList*& list, int id )
    {
       DoubleLinkedList* link = new DoubleLinkedList( id );
       /*
        * TODO: insert the new link onto the list
        */
       return link;
    }
The given code allocates a new list node for you, and already initializes it with the integer. You just have to link it into the existing list (if any), and initialize its next and previous pointers properly. Then, return the new link pointer.

i have tried so many different combination with no good result its just killing, can any of you more experience programmer explain and help me out because im totally burned out.

thanks in advance.

---

### Post by Wybiral on 2007-02-05
You should post the rest of the "DoubleLinkedList" struct/class so we can see what it looks like.

Generally, they look like this...
```

struct Node {
   int key;
   Node* last;
   Node* next;
};

```

Is that what this one looks like?

---

### Post by onewaytrip on 2007-02-05
ok here is the struct definition:

  struct DoubleLinkedList
    {
       int id;
       DoubleLinkedList* prev;
       DoubleLinkedList* next;
       DoubleLinkedList( int id );
    };

    DoubleLinkedList* dl_insert( DoubleLinkedList*&, int );

---

### Post by onewaytrip on 2007-02-05
ive been working on this for the past couple of hours and its just killing me. if anyone can break down circular double linked list for me would be great. i guess somewhere along the way i miss some key concepts.

---

### Post by Wybiral on 2007-02-05
But you understand linear singly linked list's... Right?

---

### Post by onewaytrip on 2007-02-06
yeah i understand how linked list work in general but this program is just kill me.

ok for the insert function i under stand that,

first list is set to 0(null) so i did a check for that:

  if( ! list )
     {
      list = link; // list is no longer null.
      link->next = list; //sets the next to point to list.
      link->prev = list; // sets the prev to point to list.
     }

from what i understand that should work right?

if any of ya see something way out of line let me know, explain if you can thanks.

---

### Post by Wybiral on 2007-02-06
Well, for a circular doubly linked list... They have to connect in a circle (I'm sure you already knew that)... But when you add an object, you have to insert it between the first and last (that's usually where they go).

Naturally... The "prev" pointer should point to the previous object and the "next" to the next (once again... pretty obvious).

I would help a little more... But I don't know how you are supposed to solve it (using a loop, recursion?)

I also am not entirely sure why it is returning a pointer to the list when a reference is passed (since it will already alter the object which is the functions argument because it's a reference... Why is it returning it?)

To illustrate... The left value is the prev pointer, the right is the next pointer and the middle is itself (so I can illustrate this)

(c, a, b)->(a, b, c)->(b, c, a)

So if you were to insert... Say... d after c, it would have to look like this...

(d, a, b)->(a, b, c)->(b, c, d)->(c, d, a)

Do you see what I mean? At any object in a doubly linked list, you can always use the prev/next pointers to move either direction... And since it's circular the last and first objects are connected.

EDIT:

As long as you don't need it done tonight, I can probably help you tomorrow with it if you PM me all the code you have so far (unfortunately I have to get to bed soon... Job hunting tomorrow, early morning... YUCK, but afterwards I'll be pretty much free)

Also, [http://en.wikipedia.org/wiki/Linked_list](http://en.wikipedia.org/wiki/Linked_list) you can probably find a lot of info online if you google it.

---

### Post by Peti29 on 2007-02-06
Using the given code parts I think:

```
DoubleLinkedList* dl_insert( DoubleLinkedList*& list, int id )
{
 DoubleLinkedList* link = new DoubleLinkedList( id );

 if( ! list )
 {
  list = link; // list is no longer null.
  link->next = list; //sets the next to point to list.
  link->prev = list; // sets the prev to point to list.
 } else {
  list->prev->next = link;
  link->next = list;
  link->prev = list->prev;
  list->prev = link;
 }
 return link;
}
```

---

### Post by onewaytrip on 2007-02-06
thanks for all the help, and especially to the dude that posted the exam with the "(a, b, c)", it really helped me out. anyways i figured out what i was doing wrong and i got my code working. 

here is what did just incase anyone else with a similar problem should happen to run across this post.

ok insertion code:

DoubleLinkedList* dl_insert( DoubleLinkedList*& list, int id )
{
   DoubleLinkedList* link = new DoubleLinkedList( id )

    if(!list)
        {
        list = link;
        list->prev = link;
        list->next = link;
        }
    else
        {
        link->next = list;
        link->next = list->next;
        list->next->prev = link;
        list->next = link;
        }    
    
   return link;
}
////////////////////////////////////////////////////////////////////////
removal code:

void dl_remove( DoubleLinkedList*& list )
{  
    if(list->next == list && list->next->prev == list)
        {
        list = 0;
        }
    else
        {
        list->prev->next = list->next;
        list->next->prev = list->prev;
        }
   delete list;
   list = 0;
}

also can anyone direct me to a place where i can get some good exercises on pointer and linked lists. i wanna lean more about these concepts so i can avoid this problem in the future. yet again thanks for all the help.

---

### Post by Peti29 on 2007-02-07
This is bad. 

```

        link->next = list;               // You overwrite this value on the next line
        link->next = list->next;
        list->next->prev = link;
        list->next = link;

```

You leave link->prev undefined.
I didn't take a look on the removal part.

Edit: CODE instead of QUOTE

---

### Post by onewaytrip on 2007-02-07
i see that now but my code still worked. i think it because of the removal code, which re-links the next and prev for list and if the list is pointing to itself, sets list back to 0(null).

---

