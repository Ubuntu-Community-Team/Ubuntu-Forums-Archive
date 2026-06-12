---
title: "C++ Finding next and previous sibling"
date: 2007-11-05
forum: Programming Talk
---

### Post by DesertRose on 2007-11-05
Hi and bye. there's no question anymore. ;)

---

### Post by Wybiral on 2007-11-05
What data structure are you asking about? An STL container?

---

### Post by aks44 on 2007-11-05
With so few indications it's hard to help. What do you want exactly? Some code (even if it is an incorrect "prototype") would definitely help...


As far as I can tell from the little information you gave, my best guess (provided you use a sanely designed library) would be something like:
```
Node* nextParentSibling = node->parent()->nextSibling();
Node* previousParentSibling = node->parent()->previousSibling();
// do whatever you want with those nodes
```

(yeah, that second paragraph is totally random :-\")

---

### Post by DesertRose on 2007-11-05
;) cheers

---

### Post by Wybiral on 2007-11-05
So it's a standard binary tree where each node looks like:

```

struct
{
    void *data;
    node* left, right;
} node;

```

Right? Or does it store its parent node? Or does it store any information on the levels? You need to give us more info, maybe some code. Not all binary trees are implemented the same.

---

### Post by DesertRose on 2007-11-06
;) cheers

---

