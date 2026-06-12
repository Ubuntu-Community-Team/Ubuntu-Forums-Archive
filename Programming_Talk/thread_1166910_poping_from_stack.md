---
title: "poping from stack"
date: 2009-05-22
forum: Programming Talk
---

### Post by csstudent on 2009-05-22
When popping an element from a linked list implemented stack
we use ```
top=top->next
```
Does this free the memory held by the previous
top could someone explain exactly how this freeing of memory is controlled?

---

### Post by PmDematagoda on 2009-05-22
This looks a lot like a homework question. Please understand that homework questions are not allowed here. 

This thread is closed.

---

### Post by PmDematagoda on 2009-05-22
After talking with the OP, I have decided to reopen the thread.

---

### Post by smartbei on 2009-05-23
Memory is freed when a call is made to the function 'free' with the pointer at hand.
For example, if I execute:
[php]
char * my_pointer = malloc(10);
[/php]
Then my_pointer now points to a buffer of ten bytes. In order to free this buffer (that is, mark it unused so that the operating system can give it to someone else who wants it), I would:
[php]
free(my_pointer);
[/php]
The above examples were for C. In C++ you would see 'new' instead of malloc:
[php]
char * my_pointer = new char[10];
[/php]
And delete instead of free:
[php]
delete [] my_pointer;
[/php]

Now to your question:
I assume you meant "top = top->next", because that makes more sense. In this case, if we have a linked list that looks like so:
```

top -> A -> B -> C

```
top->next is equal to A. Therefor, after execution of top = top->next, our list would look like:
```

top (A) -> B -> C

```
So we have successfully popped the top of the list, but we haven't freed the memory. In order to do that, we probably should do something more like:
[php]
old_top = top // save the pointer to the head of the list for later
top = top->next // pop the top element
free(old_top); // free the memory.
[/php]

I hope that cleared things up some... post again if not :-)

---

