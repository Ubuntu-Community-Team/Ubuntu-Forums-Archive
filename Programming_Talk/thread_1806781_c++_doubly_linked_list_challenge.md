---
title: "c++ doubly linked list challenge"
date: 2011-07-18
forum: Programming Talk
---

### Post by potaters on 2011-07-18
Hey guys, this is my first post on ubuntu forums. I'm really glad to be here!
 
Anyways, here's a c++ challenge I read somewhere a long time ago:
 
Write a doubly linked list class with all the normal functions:
 
```

void AddNodeToBeginning(NodeType NodeValue); //adds the node to the beginning
void AddNodeToEnd(NodeType NodeValue); // adds node to end of list
void PrintList(); // prints the linked list values
int searchList(NodeType NodeValue); //searches the list and returns found index or -1

```
 
But here's the twist, You need to add a function to* reverse the list*, and it has to be of order o(1) (Meaning the function needs to have a constatnt number of statements, you can't loop over the list and do something, cause then it would depend on the number of elements on the list).
 
```

void reverseList();

```
 
Yeah that's it for now, enjoy!
cheers.

---

### Post by dwhitney67 on 2011-07-18
Nice try, but this seems like a twist on asking for assistance in doing one's homework.

---

### Post by NovaAesa on 2011-07-18
I agree, this smells of homework. Btw, reversing the list should be extremely easy to do in O(1) considering that it's doubly linked...

---

### Post by Tony Flury on 2011-07-18
NovaAesa : I agree - if anything the list reversal is probably the easiest bit, and yes - it does smell of homework.

---

### Post by potaters on 2011-07-18
It's not homework. And my approach of the solution was adding a boolean variable *isReversed*, which will be set to false for all class instances, and then for the reverseList() function , we do:
 
```

isReversed = !isReversed;
node *temp = first;
first = last;
last = temp 
//reverse the first and last pointers

```
 
And then we make a check for all the other functions, say for print , if *isReversed* is true, we traverse the list with the *Back* pointer, rather than front.
 
cheers.

---

### Post by schauerlich on 2011-07-18
That's what I'd do.

EDIT: One way to avoid a bunch of

```
if (isReversed) {
  foo = node->prev;
}
else {
  foo = node->next;
}
...
```

is to have ListNode have a two element array of pointers instead of a separate prev and next, and use (int)isReversed to decide which one to use. Then you can do something like

```
node.neighbors[!isReversed]
```

Assuming the convention that neighbors[0] is the "left" neighbor, and neighbor[1] is the "right", then that line above will always yield the "next" depending on if you're moving left-to-right or right-to-left.

---

### Post by potaters on 2011-07-19
Elegant solution, schauerlich, deffinetely "cleaner" than mine. 
 
I'm just curious though, how can we reverse a *normal* linked list? Can it be done in O(1) efficiency? (I don't think so!) 
 
The only way I can think of is traversing the whole list and changing all the '*next' *pointers to the previous node.

---

### Post by dwhitney67 on 2011-07-19
> **potaters said:**
> Elegant solution, schauerlich, deffinetely "cleaner" than mine. 
 
I'm just curious though, how can we reverse a *normal* linked list? Can it be done in O(1) efficiency? (I don't think so!) 
 
The only way I can think of is traversing the whole list and changing all the '*next' *pointers to the previous node.

One should be able to insert new elements into a linked list either at the beginning, the end, or somewhere in the middle.

Thus to reverse an existing list, create a new list using the contents of the original list.  This will require only one traversal of the original list, thus O(1) efficiency.  Refer to the documentation on the [STL list]("http://www.cplusplus.com/reference/stl/list/") for more insight/ideas (hint:  push_back() and push_front() functions).

---

### Post by johnl on 2011-07-19
> **dwhitney67 said:**
> One should be able to insert new elements into a linked list either at the beginning, the end, or somewhere in the middle.

Thus to reverse an existing list, create a new list using the contents of the original list.  This will require only one traversal of the original list, thus O(1) efficiency.  Refer to the documentation on the [STL list]("http://www.cplusplus.com/reference/stl/list/") for more insight/ideas (hint:  push_back() and push_front() functions).

I think you're mistaken; traversing the list means that the time to run is dependent on the number of items in the list -- i.e., O(n)?

---

### Post by dwhitney67 on 2011-07-19
> **johnl said:**
> I think you're mistaken; traversing the list means that the time to run is dependent on the number of items in the list -- i.e., O(n)?

Dooh!  You're right.

---

