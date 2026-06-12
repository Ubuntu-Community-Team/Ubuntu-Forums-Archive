---
title: "error: lvalue required as left operand of assignment-C"
date: 2011-07-20
forum: Programming Talk
---

### Post by stamatiou on 2011-07-20
Hey guys,
I am trying to make a function that prints a singly linked list with a for loop. Here's the loop:

```
for(list;list->next!=NULL;printf("%d\n",list->data) && list = list->next);
```
but I take the error:

```
lvalue required as left operand of assignment
```
What is wrong? Also I would like to ask if this is faster than the traditional way to print the list with printf and then assigning the pointer to the next node.

---

### Post by schauerlich on 2011-07-20
```
for (list = head; list; list = list->next) {
  printf("%d\n", list->data);
}
```

As far as the lvalue problem: && has higher priority than =, so your code evaluates the printf, ands that with list (yielding 0 or 1), and then tries to do

```
0 = list->next
```

(or 1 = ...)

Those aren't [lvalues](http://en.wikipedia.org/wiki/Value_(computer_science)), so it fails.

---

