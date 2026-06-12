---
title: "C++ Debug Help"
date: 2009-01-16
forum: Programming Talk
---

### Post by SullenGenie on 2009-01-16
I found the error.  It was elsewhere.  Stupid mistake.

I'm getting a scope error on a really simple piece of code, and I cannot for the life of me figure out what the problem is.

Here's the error:
```

decision_tree.cpp: In function ‘node* create_tree(int, int**)’:
decision_tree.cpp:152: error: ‘pos_child’ was not declared in this scope

```

And here's the troublesome code (both segments in the same file):

```

typedef struct tree_node_obj {
  struct tree_node_obj * neg_child;
  struct tree_node_obj * pos_child;
  int identifier;
} node;

...

node* tree_head = (node*) malloc(sizeof(node));
  
if (pos == 0 || neg == 0) {
  tree_head->identifier = -1;
  tree_head->pos_child = NULL;
  tree_head->neg_child = NULL;
  return tree_head;
}

```

It doesn't give any errors for identifier or neg_child.  I have a feeling this is a stupid fatigue-fueled error, but I really can't figure it out.

---

