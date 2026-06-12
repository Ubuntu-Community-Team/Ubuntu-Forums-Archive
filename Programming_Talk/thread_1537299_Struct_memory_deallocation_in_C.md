---
title: "Struct memory deallocation in C"
date: 2010-07-23
forum: Programming Talk
---

### Post by xefix on 2010-07-23
Hey, everyone

I am writing a program in C that uses structs in a linked list to store some data. Each node I make contains both data and pointers to more data (strings, other structs, and the next/prev pointers that I use to maintain the linked lists). When I want to delete such a node, is it enough to simply say free(nodeptr)? Will this also free the memory from all the pointers in the node?

---

### Post by Bachstelze on 2010-07-23
> **xefix said:**
> When I want to delete such a node, is it enough to simply say free(nodeptr)? Will this also free the memory from all the pointers in the node?

No, you have to free() them as well.  Just make a helper function like

```
void free_node(node* p)
{
        free(p->somepointer);
        free(p->otherpointer);
        free(p);
}
```

---

### Post by nvteighen on 2010-07-23
> **xefix said:**
> Hey, everyone

I am writing a program in C that uses structs in a linked list to store some data. Each node I make contains both data and pointers to more data (strings, other structs, and the next/prev pointers that I use to maintain the linked lists). When I want to delete such a node, is it enough to simply say free(nodeptr)? Will this also free the memory from all the pointers in the node?

Rule of thumb: For each malloc(), you need a corresponding free().

So yes: free() won't traverse the list, though you could easily write one that does.

---

### Post by xefix on 2010-07-26
Thanks for the responses!

---

