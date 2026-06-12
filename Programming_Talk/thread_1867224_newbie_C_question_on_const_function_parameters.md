---
title: "newbie C question on const function parameters"
date: 2011-10-22
forum: Programming Talk
---

### Post by V for Vincent on 2011-10-22
Hi,

I'm learning C for an embedded systems course and I thought I'd check out some generic data structures to really get the hang of runtime memory allocation, pointer indirection and the likes. So I checked out the O'Reilly book "Mastering Algorithms with C". It contains an implementation of a singly-linked list and there is one thing about the reference implementation that bothers me. The author's interface to the insert method is:

```
int list_ins_next(List *list, ListElmt *element, const void *data);
```

meanwhile, the ListElmt data type looks like this:

```

typedef struct ListElmt_ {
    void               *data;
    struct ListElmt_   *next;
} ListElmt;

```

Isn't it a bad idea to ask for a pointer to a const data type and then to store it as a regular pointer? I would probably leave the 'const' out of the function signature. Any idea why the author thought it was better to put it in?

---

### Post by cgroza on 2011-10-22
No. By declaring a parameter const, you promise not to modify it and the compiler will spit out an error if you try to.
So that function declaration tells you that it won't modify the data pointed by *data.

---

### Post by gnometorule on 2011-10-22
The const in the prototype is a reminder that the function call should not change the data. The data is obviously variable and you can change it at any time, but while storing it into the list element, it should not be changed, and this provides a means to the compiler to perform some basic safety checks. When you look at man pages for c lib functions such as strcmp, you will notice a similar semantic.

---

### Post by V for Vincent on 2011-10-22
I see. In the function gcc tells me 

"list.c: In function &#8216;list_ins_next&#8217;:
list.c:34:20: warning: assignment discards &#8216;const&#8217; qualifier from pointer target type [enabled by default]" 

when I assign the "data" parameter to newelement->data.

Is the compiler warning me based on the assumption that I might use newelement->data to change the value of the referenced variable *while I'm still inside the list_ins_next function*?

---

### Post by Arndt on 2011-10-23
> **V for Vincent said:**
> I see. In the function gcc tells me 

"list.c: In function ‘list_ins_next’:
list.c:34:20: warning: assignment discards ‘const’ qualifier from pointer target type [enabled by default]" 

when I assign the "data" parameter to newelement->data.

Is the compiler warning me based on the assumption that I might use newelement->data to change the value of the referenced variable *while I'm still inside the list_ins_next function*?

If I understand this correctly, if you want to have 'const' in the signature but keep it as non-const inside (because it will be returned to the user at some point), you should cast away the 'const', preferably just before storing the pointer as non-const.

---

### Post by V for Vincent on 2011-10-23
That's right. The cast followed by an assignment is what generates the gcc warning. What I'm mostly interested in is whether the warning is relevant if I don't modify the data from within the insert function.

---

### Post by Arndt on 2011-10-23
> **V for Vincent said:**
> That's right. The cast followed by an assignment is what generates the gcc warning. What I'm mostly interested in is whether the warning is relevant if I don't modify the data from within the insert function.

I meant that if you do newelement->data = (const void *) data, you shouldn't get a warning.

Warnings are for getting your attention. The warning is relevant insofar as it is true, it is irrelevant insofar as you know what the should and shouldn't do.

---

### Post by V for Vincent on 2011-10-23
Turns out the cast is there in the reference implementation, but I left it out, precisely because I wasn't sure it was safe. But I feel I've really gained some insight now. You've been of great help. Thanks.

---

