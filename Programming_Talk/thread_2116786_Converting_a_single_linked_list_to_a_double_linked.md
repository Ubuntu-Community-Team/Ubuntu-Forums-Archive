---
title: "Converting a single linked list to a double linked list"
date: 2013-02-16
forum: Programming Talk
---

### Post by Amulon on 2013-02-16
I have created a single linked list that has integers from a file. How do I copy the nodes in the single linked list to a double linked list?

Thanks!

---

### Post by TheFu on 2013-02-16
I'd suggest that you draw a picture to work this out.
Oh and which language are you using?

---

### Post by Amulon on 2013-02-16
Oh sorry, I forgot to put that. C++.  Like... I know the concept of how to do it. I just can't make it work. It is something like this, right?

p->next = q->next;
p->back = q;
q->next->back = p;
q->next = p;

---

### Post by TheFu on 2013-02-17
> **Amulon said:**
> Oh sorry, I forgot to put that. C++.  Like... I know the concept of how to do it. I just can't make it work. It is something like this, right?

p->next = q->next;
p->back = q;
q->next->back = p;
q->next = p;

If you are using C++, then shouldn't a class be involved?  Perhaps something called "Node?"

```
Class Node
{
  public:
        Node();
        Node(Node* pPrev, Node* pNext=NULL);   
        ~Node();
        SetNext(Node*);
        SetPrev(Node*);
  private:
    Data mWhateverYouLike;
    Node* mpNext;
    Node* mpPrev;
};
```It has been awhile (10+ yrs) since I wrote any C++, but that should get you started.  It is doubtful that class is syntactically correct.

I would also ensure that any member pointers were initialized to NULL and judicious checking for NULL at every step is used to ensure pointers were not overwritten or not deleted[] as necessary.

Hopefully, you have a Node class already for your single linked-list ... that has "Data" and a pointer to next already.  Heck, there must be a template that already does this data structure. In my day, we'd use a RogueWave class - templates have completely replaced those commercial libraries now.

Anyway, that should get you started.

---

### Post by dwhitney67 on 2013-02-17
> **TheFu said:**
>  In my day, we'd use a RogueWave class...

I left a project not too long ago that still employed the use of RogueWave classes.  Indeed it is old technology, yet still in use today.

The OP should be using the [STL list]("http://www.cplusplus.com/reference/list/list/"), unless of course he is tackling a school-work assignment.

---

### Post by Linteg on 2013-02-17
> **Amulon said:**
> Oh sorry, I forgot to put that. C++.  Like... I know the concept of how to do it. I just can't make it work. It is something like this, right?

p->next = q->next;
p->back = q;
q->next->back = p;
q->next = p;
Assuming the original list is P->Q->R that will create Q<->P<->R.

---

